### Прогресс:
* Проблема с z0 была в функции активации(была tanh, теперь будет sin)(см [exp3](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp3.md)), остальные изменения заметных положительных эффектов не дали(cм [exp4](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp4.md), [exp5](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp5.md)).
* Решение всё ещё плохо продолжается на большие t, а если и продолжается, то почему-то идёт ниже, чем нужно(см [exp6](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp6.md)).
* Soft Adapt тоже не очень помог, коэффициенты просто постепенно приравниваются(см [exp7](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp7.md)).
* Что интересно, при lr=1e-4 и ниже сеть вроде учится, loss уменьшается, но на выходе получается какая-то странная фигня, не похожая ни на константу ни на аналитическое решение(см [exp8](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp8.md)).
---
* Чтобы получить хорошие результаты нужно было поправить процесс обучения и использовать 100000 итераций оптимизатора ADAM с убывающим lr(см [exp9](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp9.md))
* Использование балансировки весов замедляет обучение, но в то же время улучшает стабильность уменьшения mse_q. Чем сильнее разбиение loss на части, тем сильнее эффект(см [exp10](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp10.md), [exp11](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp11.md),  [exp12](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp12.md),  [exp13](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp13.md))
---
* Память коэффициентов при балансировке весов улучшила результаты, но они всё ещё хуже, чем без балансировки вообще(см [exp14](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp14.md))
* Учёт порядка слагаемых loss при балансировке весов лишь ухудшил результаты(см [exp15](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp15.md))  
* Использование метода балансировки весов ReLoBRaLo дало существенное увеличение качества, но оно всё ещё хуже, чем без балансировки(см [exp16](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp16.md))
---
* Учёт соблюдения законов сохранения при обучении только ухудшает результаты, ведь задача повышения точности их соблюдения не совпадает с задачей понижения mse_q(см [exp17](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp17.md))
* При увеличении числа итераций в обучении до 300000 ReLoBRaLo показывает самые лучшие результаты. Остальные методы балансировки выдают результаты хуже, чем в опыте без балансировки вообще(см. [exp18](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp18.md), [exp19](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp19.md), [exp20](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp20.md),
[exp21](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp21.md), [exp22](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp22.md),
[exp23](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp23.md))
---
* Изучение взаимодействия двух солитонов при alpha=0 дало замечательные результаты: законы сохранения и уравнение выполняются при всех t(см. [exp24](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp24.md))
* Если же alpha=0.1, то начинаются проблемы: после пересечения солитоны распыляются, чего быть не должно. При этом полученное решение хуже удовлетворяет условиям уравнения, но лучше соответствует законам сохранения(см. [exp25](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp25.md))
* Как плавное, так и резкое изменение alpha в процессе обучения ничего не дало (см. [exp26](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp26.md), [exp27](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp27.md))
* Оказалось, проблема заключается в распылении каждого из солитонов при alpha=0.1(см. [exp28](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp28.md)). Но если уменьшить коэффициенты k в решении, то распыление прекратится и получатся вполне хорошие результаты(см. [exp29](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp29.md))
---
* Оказалось, что точность снижается при увеличении k и уменьшении w, а солитоны начинают распыляться при увеличении alpha.(см. [exp34](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp34.md))
* При этом компенсировать большой k большим w сложно, ведь k влияет на функцию сильнее w.(см. [exp31](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp31.md))
---
* Добавление Фурье слоёв иногда может увеличивать точность, но не решает проблему её снижения при увеличении k и не устраняет распыления солитонов(см. [exp35](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp35.md))
* Замена переменной, растягивающая оси и упрощающая аппроксимацию действительно увеличивает точность, но начальное условие перестаёт создавать солитон. Поэтому данный способ полностью бесполезен(см. [exp36](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp36.md))
---
* Если задавать в качестве начального условия функции вида $f(x)*e^{-\frac{x}{a}^2}$, то они будут распыляться или задавать солитоны, но они точно не будут оставаться постоянными во времени(см. [exp37](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp37.md))  
* Решение нелинейного уравнения Шрёдингера 4-го порядка показало, что PINN может решать его с высокой точностью, но только в случае ограниченности ожидаемого решения(см. [exp38](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp38.md))
---
* С достаточной точностью получены картины прохождения солитона через распыляющуюся экспоненту для разных начальных условий(см. [exp39](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp39.md) и [exp40](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp40.md))
---
* Были повторены exp39 и exp40, но для другого значения параметра alpha в уравнении($\alpha=0$) и попутно в одном из опытов получена наибольшая точность в решении данного уравнения, MSE_q~1e-8(см. [exp41](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp41.md) и [exp42](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp42.md))
* Получены картины столкновения солитонов с разными $k$ и $w$, но одинаковыми $\mu$(см. [exp43](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp43.md))
* Оказывается, обучение иметь тот же модуль, что и у солитона мешает учиться удовлетворять условиям уравнения (см. [exp44](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp44.md))
---
* Был обнаружен новый эффект при столкновении солитона с решением для начального условия в виде гауссианы(см. [exp45](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp45.md))
* Получена картина столкновения солитона с препятствием на большей области($t\in[0,100]$)(см. [exp46](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp46.md))
---
* Был проведён эксперимент с прохождением гауссианы через два параллельных солитона. И хотя его необходимо переделать, эффект изменения фазы наблюдается и тут(см. [exp47](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp47.md))
* Воспроизведены старые опыты(exp40, exp42) с новой визуализацией и видоизменённой метрикой для законов сохранения(см. [exp48](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp48.md), [exp49](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp49.md))
* Получены картины прохождения солитона с новым начальным условием(зависящим от $\alpha$) через различные гауссианы(см. [exp50](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp50.md))
---
* Проведены испытания метода FBPINNs для начального условия в виде солитона с известным решением и подобраны наиболее удачные параметры(см. [exp51](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp51.md))
* Подобранные на маленькой области параметры FBPINNs опробованы на больших областях(t<50)(см. [exp52](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp52.md))
* Хорошие результаты на больших областях позволили перейти к опытам на очень больших областях(t<100)(см. [exp53](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp53.md))
* Также проведены опыты для случаев с неизвестным точным решением($\alpha_0 \neq \alpha$) (см. [exp54](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp54.md))
---
* Был проведён эксперимент по улучшению с помощью transfer learning решения, полученного ранее c помощью FBPINNs (см. [exp55](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp55.md)). Дальнейшая работа по transfer learning была оформлена в [отдельный репозиторий](https://github.com/mikhakuv/PINNs_Transfer_Learning).
---
* Рассмотрено уравнение 6-го порядка: подвтерждена верность аналитического решения, получено решение с помошью классической PINN (см. [exp56](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp56.md))
* Изменены коэффициенты в уравнении для получения большей нелинейности, получены решения новой задачи с помощью PINN и FBPINN (см. [exp57](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp57.md))
* Использован новый способ генерации точек, опробован новый оптимизатор - NNCG (см. [exp58](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp58.md), [exp59](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp59.md))
* Реализована балансировка весов ReLoBRaLo и Causal Loss, дополнительно построены графики зависимости основных метрик от loss (см. [exp60](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp60.md))
* Реализована модель с новой топологией и сегментация области с возможностью повторного использования весов (см. [exp61](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp61.md))
* Изучено влияние повторного использования весов на точность, проведены опыты на больших областях (см. [exp62](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp62.md))
* Устранена причина некачественных результатов при использовании сегментации. Проведены новые опыты с одним и двумя солитонами (см. [exp63](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp63.md))
* Проведены опыты для случаев с неизвестным аналитическим решением (см. [exp64](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp64.md))
* Исследовано поведение решения для начального условия в виде гауссиан разной амплитуды. Реализован новый метод генерации точек (см. [exp65](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp65.md), [exp66](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp66.md))
* Проведено исследование нового метода генерации точек и сравнение его с другими существующими методами (см. [exp67](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp67.md))
* Получено качественное решение уравнения разностной схемой, проведено полное сравнение существующих методов генерации точек (см. [exp68](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp68.md))
* Найдены особенности работы численной схемы, предложен алгоритм оптимального подбора параметров сетки (см. [exp69](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp69.md))
---
Статистику обучения во всех успешных экспериментах и сравнительные графики можно найти в файле: [stats.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/stats.xlsx)    
Результаты можно найти в таблицах: [performance_table.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table.xlsx) или [performance_table_fbpinns.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table_fbpinns.xlsx)
