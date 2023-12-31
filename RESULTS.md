# Теория  
В данной работе применяется метод PINN для решения нелинейного дифференциального уравнения второго порядка, а полученный результат сравнивается с аналитическим решением. Исследуется влияение методов балансировки весов на качество обучения.
### Уравнение
Рассматривается обобщённое уравнение Шрёдингера в нелинейной среде (generalized Schrodinger equation with a dual-power law nonlinear medium):
$$iq_t + aq_{xx} + \alpha|q|^{2n}q - \beta|q|^{4n}q = 0$$
В [[1]](#обзор-литературы) найдено аналитическое решение такого уравнения:
$$q(x, t)=\left[\frac{4 \mu \mathrm{e}^{\left(x-2 a k t-z_0\right) \sqrt{\mu}}}{1+2 \lambda \mathrm{e}^{\left(x-2 a k t-z_0\right) \sqrt{\mu}}+\left(\lambda^2-4 \mu \nu\right) \mathrm{e}^{2\left(x-2 a k t-z_0\right) \sqrt{\mu}}}\right]^{\frac{1}{2 n}} \mathrm{e}^{i\left(k x-\omega t+\theta_0\right)},$$
$$где\quad \lambda=\frac{4 \alpha n^2}{a(1+n)},\quad \nu=\frac{4 \beta n^2}{a(1+2 n)},\quad \mu=\frac{4 n^2(\omega-a k^2)}{a} .$$
рассматривается  случай $\quad n = 1,\quad a = 1,\quad \alpha = 1,\quad \beta = 1,\quad$ при котором $\quad k = 1,\quad z_0 = 0,\quad \theta_0 = 0,\quad w = \frac{9}{8}.$
### PINN
Решение уравнения находится в виде нейросети. Это возможно потому, что нейросеть рассматривается как функция, а от функции можно считать производные разных порядков и из них составить исходное уравнение. Полученное уравнение будет использоваться как первое слагаемое `loss` (далее обозначается как `loss_f`). Задачей оптимизатора будет как можно сильнее уменьшить `loss`, а значит и заставить нейросеть удовлетворять уравнению. Чтобы в итоге не получалось тривиальное решение, вторым слагаемым `loss` будет ошибка выполнения начальных и граничных условий (далее обозначается как `loss_uv`). В данной работе начальное условие определяется как значения аналитического решения в $(x,t_0)$, а граничные условия считаются нулевыми в $(x_0,t)$ и $(x_1,t)$. В итоге минимизируется следующая функция: `loss = loss_f + loss_uv`. Весь процесс изображён на картинке:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/results_illustration.png">  
Такой подход называется **P**hysics **I**nformed **N**eural **N**etwork и был впервые представлен в [[2]](#обзор-литературы). Он существенно отличается от численных методов тем, что в итоге получается не массив чисел, а дифференцируемая функция.  
### Балансировка весов
Несмотря на то, что метод работает неплохо, есть много попыток улучшить его. Один из наиболее распространённых приёмов - динамическая балансировка весов, она используется не только в PINN, но и в других областях. Идея заключается в том, чтобы нейросеть одинаково хорошо училась удовлетворять всем условиям. Для этого при слагаемых `loss` добавляются коэффициенты и в итоге он имеет вид: $$loss = \sum_i lambda_i * loss_i$$ Есть несколько методов вычисления коэффициентов в процессе обучения, в данной работе изучается и совершенствуется метод SoftAdapt, предложенный в статье [[3]](#обзор-литературы). Изначально он применялся к задаче реконструкции изображений и использовал относительность прогресса в уменьшении составных частей loss. Обозначим как $loss_i(iter)$ значение $i$-того слагаемого `loss` на шаге $iter$. Тогда коэффициент $lambda_i$ при слагаемом $loss_i$ определяется по формуле: $$lambda_i = \frac{exp(\frac{loss_i(iter)}{loss_i(iter-1)})}{\sum_j exp(\frac{loss_j(iter)}{loss_j(iter-1)})}$$ Смысл такой формулы простой: во-первых коэффициент при $loss_i$ снижается, если он($loss_i$) уменьшился сильнее других и повышается в обратном случае, во-вторых сумма всех коэффициентов равна 1. Ясно, что на следующем шаге оптимизатору будет выгоднее снижать $loss_i$, у которого коэффициент $lambda_i$ больше и поэтому в процессе обучения все $loss_i$ будут снижены одинаково хорошо.  
Можно разбивать `loss` не только на 2, но и на большее число слагаемых за счёт разделения граничных и начальных условий, а также действительной и мнимой частей. В данной работе будет проверена работа метода SoftAdapt на 2, 3 и 6 слагаемых.  

Также можно усовершенствовать текущий метод, добавив ему память предыдущих итераций. Это можно сделать, если присваивать значения коэффициентов $lambda_i$ следующим образом: $$lambda_i = \tau*lambda_i(iter-1) + (1-\tau)*lambda_i(iter)$$ где $\tau \in[0,1]$ - коэффициент, обозначающий затухание. Чем ближе $\tau$ к 1, тем больше влияние предыдущих значений $lambda_i$.  

Ещё одним улучшением является метод ReLoBRaLo, предложенный в статье [[4]](#обзор-литературы). Он учитывает изменение `loss` не только по сравнению с предыдущим шагом, но и с самым началом обучения. У него также есть память предыдущих итераций, как в предыдущем методе. Коэффициенты определяются следующим образом: $$lambda_i = \tau*(\rho*lambda_i(iter-1) + (1-\rho) *\widehat{lambda_i}(iter)) + (1-\tau)*lambda_i(iter)$$ где $\tau \in[0,1]$ - коэффициент, обозначающий затухание, $\rho \in[0,1]$ - случайное число, генерируется каждую итерацию, $$\widehat{lambda_i} = \frac{exp(\frac{loss_i(iter)}{loss_i(0)})}{\sum_j exp(\frac{loss_j(iter)}{loss_j(0)})}$$
### Законы сохранения (!оказалось, что при обучении их использовать нет смысла)
Важным отличием PINN от численных методов является возможность наложения дополнительных условий на решение. Согласно теории [[1]](#обзор-литературы), в рассматриваемом уравнении решение должно подчиняться законам сохранения. Они имеют следующий вид:  
1. $P(t) = \int\limits_{-\infty}^{+\infty}{u(x,t)}^2+{v(x,t)}^2\ dx = const$  
2. $M(t) = \int\limits_{-\infty}^{+\infty}v_x(x,t)*u(x,t) - u_x(x,t)*v(x,t)\ dx = const$  
3. (не использовал) $H(t) = \int\limits_{-\infty}^{+\infty}\frac{\alpha{|q(x,t)|}^{2n+2}}{2n+2} - \frac{\beta{|q(x,t)|}^{4n+2}}{4n+2} - a|q_x|^2 \ dx \stackrel{n=1}{=} \int\limits_{-\infty}^{+\infty}\frac{\alpha{(u^2+v^2)}^{2}}{4} - \frac{\beta{(u^2+v^2)}^{3}}{6} - a(u_x^2+v_x^2) \ dx = const$

Чтобы при обучении учитывать эти условия, нужно добавить точность их соблюдения в `loss`, который будет иметь вид:  
`loss = loss_uv + loss_f + loss_fl + loss_sl`.
# Методика измерений и результаты  
### Параметры нейросети
В опытах использовалась нейросеть с топологией [2,100,100,100,100,2]: 2 входа - переменные $x$ и $t$; дальше идут 4 полносвязных слоя по 100 нейронов в каждом; 2 выхода - действительная($u$) и мнимая($v$) части. Обучение происходит в 2 этапа: сначала ~300000 итераций оптимизатора Adam, потом включается LBFGS. Функция активации нейронов - sin. Используемые параметры получены методом перебора как наиболее подходящие.
### Методика вычисления ошибок
Мерой успеха считалось значение функции $mse_q$ , вычисляемое как: $$mse_q=\frac{\sum_{1 \leq i \leq n}(\sqrt{u_{truth}(x_i,t_i)^2 +v_{truth}(x_i,t_i)^2} - \sqrt{u_{pred}(x_i,t_i)^2 +v_{pred}(x_i,t_i)^2})^2}{n}$$ где $n$ - количество рассматриваемых точек на области  
Также вычислялись $mse_u$, $mse_v$, $mse_{f_u}$, $mse_{f_v}$:
$$mse_u = \frac{\sum_{1 \leq i \leq n}(u_{truth}(x_i,t_i)-u_{pred}(x_i,t_i))^2}{n}$$
$$mse_v = \frac{\sum_{1 \leq i \leq n}(v_{truth}(x_i,t_i)-v_{pred}(x_i,t_i))^2}{n}$$
$$mse_{f_u} = \frac{\sum_{1 \leq i \leq n}(f_{pred_u}(x_i,t_i))^2}{n}$$
$$mse_{f_v} = \frac{\sum_{1 \leq i \leq n}(f_{pred_v}(x_i,t_i))^2}{n}$$
### Результаты
Опыты проводились на области $x \in [-85;85]$, $t \in [0;50]$. Был изучен каждый из предложенных методов балансировки весов:
* без балансировки - балансировка весов не используется
* 2 коэффициента, SoftAdapt - loss состоит из двух слагаемых, для нахождения коэффициентов при них используется метод SoftAdapt
* 3 коэффициента, SoftAdapt - loss состоит из трёх слагаемых, для нахождения коэффициентов при них используется метод SoftAdapt
* 3 случайных коэффициента - loss состоит из трёх слагаемых, коэффициенты при них генерируются случайным образом
* 3 коэффициента, SoftAdapt с памятью - loss состоит из трёх слагаемых, для нахождения коэффициентов при них используется усовершенствованный метод SoftAdapt с памятью предыдущих итераций
* 3 коэффициента, ReLoBRaLo - loss состоит из трёх слагаемых, для нахождения коэффициентов при них используется метод ReLoBRaLo

На графиках 1,2,3,4 изображены зависимости $mse_q(iter)$ для разных опытов, причём ось ординат представлена в логарифмическом масштабе:  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/results_chart1.PNG"></p>  

Из первого графика видно, что от увеличения числа коэффициентов метод SoftAdapt начинает работать всё хуже. Более того, кривая соответствующая опыту без балансировки коэффициентов проходит ниже, а значит SoftAdapt в данном случае только ухудшает обучение.  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/results_chart2.PNG"></p>  

Второй график подтверждает то, что SoftAdapt в данном случае мешает обучению, ведь опыт со случайными коэффициентами оказывается более успешным. В то же время незначительная модификация SoftAdapt даёт результаты ещё лучше.  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/results_chart3.PNG"></p>  

Третий график сравнивает лучшие кривые из графиков 1 и 2 с методом ReLoBRaLo. Отчётливо видно, что он обходит оба.  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/results_chart4.PNG"></p>  

На четвёртом графике собраны кривые со всех опытов.  

На графике 5 изображены $mse_q$ для каждого из опытов после окончания обучения:  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/results_chart5.PNG"></p>  

Из представленных выше графиков видно, что метод ReLoBRaLo с тремя коэффициентами позволяет получить наилучшие результаты. Ниже представлены результаты обучения нейросети таким методом:  
Метрики: $mse_u = 1.160926 *10^{-2}, mse_v = 1.160940 *10^{-2}, mse_q = 2.385358 *10^{-6}, mse_{f_u} = 5.229450 *10^{-9}, mse_{f_v} = 4.394714 *10^{-9}$  
Полученное решение(_pred) в сравнении с аналитическим(_truth):  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp23_results_u.png"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp23_results_v.png"></p>  

модули полученного и аналитического решений в срезах по $t$(красный и зелёный соответственно):  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp23_results_q.png"></p>  

разность модулей полученного и аналитического решений:  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp23_results_q_diff.png"></p>  

зависимость качества выполнения условий уравнения от $t$(чем ближе к 0, тем лучше):  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp23_results_mean.png"></p>  

зависимость качества выполнения законов сохранения от $t$(чем ближе к 0, тем лучше):  

<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp23_results_laws.png"></p>  

Как менялась выдача нейросети в процессе обучения:  
<p align="center"><img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/train_process.gif"></p>  

Статистика по всем проведённым экспериментам и данные для построения графиков находятся в файлах:
[performance_table.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table.xlsx),
[stats.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/stats.xlsx) (обсуждаемые в работе опыты имеют номера 18-23)  

### Вывод
В данной работе изучалась эффективность методов балансировки коэффициентов при решении обобщённого уравнения Шрёдингера в нелинейной среде. Проведённые эксперименты показали, что ни SoftAdapt ни его улучшенная версия не дают никакой выгоды, наоборот, они ухудшают результаты. В то же время метод ReLoBRaLo даёт некоторое преимущество и позволяет достигнуть очень высокой точности в решении рассмотренного уравнения.  
# Обзор Литературы  
1. вроде ещё неопубликованная статья *Nikolay A. Kudryashov, Daniil R. Nifontov* "Application of machine learning to construct solutions to non-integrable partial differential equations"
2. *Maziar Raissi, Paris Perdikaris, George Em Karniadakis* "Physics Informed Deep Learning (Part I): Data-driven Solutions of Nonlinear Partial Differential Equations"
3. *A. Ali Heydari, Craig A. Thompson, Asif Mehmood* "SoftAdapt: Techniques for Adaptive Loss Weighting of Neural Networks with Multi-Part Loss Functions"
4. *Rafael Bischof, Michael Kraus* "Multi-Objective Loss Balancing for Physics-Informed Deep Learning"
