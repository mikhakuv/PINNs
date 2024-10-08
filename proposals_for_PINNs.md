# Где PINNs могут быть полезны
В статье [[1]](#источники) пришли к выводу, что PINNs в целом не могут превзойти численные методы там, где они и так хорошо работают. Но в некоторых специфичных случаях PINNs могут преуспеть:  
* В фильтрации сигналов или теории оптимального контроля появляются уравнения с большим числом размерностей, плохо решаемые классическими численными методами за счёт слишком большого числа узлов в сетке.
* Иногда нужно получить решение с очень высоким разрешением. PINNs позволяют получить его гораздо быстрее и сколь угодно сильно увеличивать детализацию, в то время как численные методы могут тратить на это много времени. Например, в предсказаниях погоды и климата используется численное решение уравнений Навье-Стокса, но сетка у такой схемы достаточно грубая(порядка километра между узлами) из-за размера области и недостатка данных. Как следствие, существует задача даунскейлинга, заключающаяся в увеличении разрешения полученной сетки на основании каких-то условий(ими могут быть физические законы) и можно попробовать применить для неё PINNs. 
* При решении комплексных уравнений появляется интересный эффект: PINNs получают более точное решение на действительной и комплексных частях по отдельности, но модуль решения у них менее точный, чем у численных решений. Это может служить мотивацией для применения PINNs, хотя в [[1]](#источники) был пример, в котором PINN не уловила эффект при больших t.
* Ещё оказалось, что PINNs легко приспособить к решению уравнений на различных поверхностях, в том числе неориентируемых: ленте Мёбиуса, бутылке Клейна, проективной плоскости(но я не успел это попробовать). Такие задачи решаются в математике, но некоторые из уравнений формально невозможно задать из-за неориентируемости соответствующих поверхностей.
# Как можно усовершенствовать PINNs
В статье [[1]](#источники) перечислено множество вариантов усовершенствования(я пока не успел все просмотреть):
* Conservative PINNs[[2]](#источники):  
Предложено разделение исходной области на неравные части основываясь на виде решения. На каждой из частей учится отдельная нейросеть, причём от области к области гиперпараметры могут меняться. При этом условия на границах областей получаются "из экспериментов или численных симуляций", а в loss добавлены два новых слагаемых: точность совпадения решений из соседних областей и точность совпадения их потоков, где поток $f$ определён для уравнений вида $u_t+f=0$.
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/proposals_1.PNG">  

* Extended PINNs[[3]](#источники):  
Обобщение идеи cPINNs, применимое для произвольных дифференциальных уравнений. В отличие от предыдущего метода, в loss добавляются следующие слагаемые: точность совпадения решений из соседних областей, точность совпадения невязок этих решений, а также дополнительные краевые условия, зависящие от уравнения(например точность совпадения потоков или точность совпадения производных решений из соседних областей). В самой статье [[3]](#источники) бросаются в глаза некоторые опечатки(отсутствие Remark 1 и Remark 2, жёлтых точек на Figure 2), поэтому надо быть осторожнее с ней.
* Variational PINNs[[4]](#источники):  
По аналогии с методом Галёркина предложено модифицировать loss, вычисляя не невязку $Res(\vec{x})$ на уравнении, а среднее интегралов от произведения невязки на набор каких-то основных функций: $\frac{1}{N}\sum\limits_{k=1}^N\int{Res(\vec{x})\cdot \nu_{k}(\vec{x})d\vec{x}}$. Причём можно выбирать основные функции и функции активации так, чтобы этот интеграл аналитически(интегрированием по частям) преобразовывался во что-то с производными меньшего порядка и соответственно проще вычисляемое (к примеру можно взять основные функции с компактным носителем, а функции активации брать синусами, причём сеть рассматривать однослойной). Авторы указывают, что численное интегрирование будет вносить свою ошибку при обучении, а если брать слишком много основных функций, то задача оптимизации может не решиться.
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/proposals_2.PNG">  

* hp-VPINNs[[5]](#источники):  
Частный случай метода vPINNs, в котором в качестве основных функций берут набор функций с непересекающимися компактными носителями, объединение которых даёт всю исходную область. Опять же, есть возможность аналитически преобразовывать loss.
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/proposals_3.PNG">  

* Bayesian PINNs[[6]](#источники):  
По существу это объединение идеи Bayesian Neural Networks с методом PINNs. Веса и смещения нейросети не фиксированы, а берутся в виде распределения(распределение Гаусса вблизи какой-то точки) и в процессе обучения ошибка должна быть снижена на всём распределении, а не только на фиксированных коэффициентах. Выходом нейросети по итогу тоже будет определённое распределение, которое можно усреднить и получить привычный ответ. Полезно при заметно зашумлённых данных.
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/proposals_4.PNG">  

* Finite Basis PINNs[[7]](#источники):  
Достаточно избитая идея с разделением исходной области на области(без учёта особенностей решения) и обучением отдельной нейросети на каждой из областей. Новшество состоит в том, что полученные на отдельных областях решения собираются в одну функцию с помощью домножения каждого из решений на соответствующую функцию с компактным носителем и суммирования результатов. В итоге это даёт функцию, определённую на всей области, а также позволяет не добавлять в Loss всякие дополнительные слагаемые, как это сделано в cPINNs и XPINNs.
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/proposals_5.PNG">  

Дополнительно: а что будет, если обучать нейросеть не с нуля, а переучивать из уже обученной на том же уравнении? Такой подход в машинном обучении называется Transfer Learning и уже применялся к PINNs(вставить ссылки на статьи), но для нелинейного уравнения Шрёдингера пока такого не делали. Причём совсем необязательно переносить именно сами веса, можно учить нейросеть удовлетворять значениям выдаваемым предыдущей нейросетью, что гораздо быстрее, чем учить её уравнению. Причём ясно, что если новая нейросеть достаточно хорошо аппроксимирует решение старой, то и невязка у неё будет примерно такой же низкой и в процессе обучения станет только ниже. Более того, в данном направлении проявляется преимущество PINNs над обычными численными методами, которые неспособны использовать результаты предыдущих вычислений для ускорения последующих.  
Ещё появилась идея сделать что-то вроде градиентного бустинга для PINNs(раз ансамбль уже есть, то можно и дальше развивать идею принципа Кондорсе). Оказалось, это уже сделано в работе [[8]](#источники).

# Источники  
[1] *Tamara G. Grossmann, Urszula Julia Komorowska, Jonas Latz, Carola-Bibiane Schönlieb* "Can Physics-Informed Neural Networks beat the Finite Element Method?"  
[2] *A. D. Jagtap, E. Kharazmi, and G. E. Karniadakis* "Conservative physics-informed neural networks on discrete domains for conservation laws: Applications to forward and inverse problems."  
[3] *A. D. Jagtap and G. Em Karniadakis* " Extended Physics-Informed Neural Networks (XPINNs): A Generalized Space-Time Domain Decomposition Based Deep Learning Framework for Nonlinear Partial Differential Equations"  
[4] *E. Kharazmi, Z. Zhang, and G. E. Karniadakis* "Variational Physics-Informed Neural Networks For Solving Partial Differential Equations."  
[5] *E. Kharazmi, Z. Zhang, and G. E. Karniadakis* "hp-VPINNs: Variational physics-informed neural networks with domain decomposition."  
[6] *L. Yang, X. Meng, and G. E. Karniadakis* "B-PINNs: Bayesian physics-informed neural networks for forward and inverse PDE problems with noisy data."  
[7] *B. Moseley, A. Markham, and T. Nissen-Meye* "Finite Basis Physics-Informed Neural Networks(FBPINNs): a scalable domain decomposition approach for solving differential equations."  
[8] *Zhiwei Fang, Sifan Wang, Paris Perdikaris* "Ensemble learning for Physics Informed Neural Networks: a Gradient Boosting approach"
