# Где PINNs могут быть полезны
В статье [[1]](#источники) пришли к выводу, что PINNs в целом не могут превзойти численные методы там, где они и так хорошо работают. Но в некоторых специфичных случаях PINNs могут преуспеть:  
* В фильтрации сигналов или теории оптимального контроля появляются уравнения с большим числом размерностей, плохо решаемые классическими численными методами за счёт слишком большого числа узлов в сетке.
* Иногда нужно получить решение с очень высоким разрешением. PINNs позволяют получить его гораздо быстрее и сколь угодно сильно увеличивать детализацию, в то время как численные методы могут тратить на это много времени. Например, в предсказаниях погоды и климата используется численное решение уравнений Навье-Стокса, но сетка у такой схемы достаточно грубая(порядка километра между узлами) из-за размера области и недостатка данных. Как следствие, существует задача даунскейлинга, заключающаяся в увеличении разрешения полученной сетки на основании каких-то условий(ими могут быть физические законы) и можно попробовать применить для неё PINNs. 
* При решении комплексных уравнений появляется интересный эффект: PINNs получают более точное решение на действительной и комплексных частях по отдельности, но модуль решения у них менее точный, чем у численных решений. Это может служить мотивацией для применения PINNs, хотя в [[1]](#источники) был пример, в котором PINN не уловила эффект при больших t.
* Ещё оказалось, что PINNs легко приспособить к решению уравнений на различных поверхностях, в том числе неориентируемых: ленте Мёбиуса, бутылке Клейна, проективной плоскости(но я не успел это попробовать). Такие задачи решаются в математике, но некоторые из уравнений формально невозможно задать из-за неориентируемости соответствующих поверхностей.
# Как можно усовершенствовать PINNs
В статье [[1]](#источники) перечислено множество вариантов усовершенствования(я пока не успел все просмотреть):
* Conservative PINNs - [[2]](#источники)
* Extended PINNs - [[3]](#источники)
* Variational PINNS - [[4]](#источники)
* hp-VPINNs - [[5]](#источники)
* Bayesian PINNs - [[6]](#источники)
* Finite Basis PINNs - [[7]](#источники)
* Дополнительно: а что будет, если обучать нейросеть не с нуля, а переучивать из уже обученной на том же уравнении?

# Источники  
[1] *Tamara G. Grossmann, Urszula Julia Komorowska, Jonas Latz, Carola-Bibiane Schönlieb* "Can Physics-Informed Neural Networks beat the Finite Element Method?"  
[2] *A. D. Jagtap, E. Kharazmi, and G. E. Karniadakis* "Conservative physics-informed neural networks on discrete domains for conservation laws: Applications to forward and inverse problems."  
[3] *A. D. Jagtap and G. Em Karniadakis* " Extended Physics-Informed Neural Networks (XPINNs): A Generalized Space-Time Domain Decomposition Based Deep Learning Framework for Nonlinear Partial Differential Equations"  
[4] *E. Kharazmi, Z. Zhang, and G. E. Karniadakis* "Variational Physics-Informed Neural Networks For Solving Partial Differential Equations."  
[5] *E. Kharazmi, Z. Zhang, and G. E. Karniadakis* "hp-VPINNs: Variational physics-informed neural networks with domain decomposition."  
[6] *L. Yang, X. Meng, and G. E. Karniadakis* "B-PINNs: Bayesian physics-informed neural networks for forward and inverse PDE problems with noisy data."  
[7] *B. Moseley, A. Markham, and T. Nissen-Meye* "Finite Basis Physics-Informed Neural Networks(FBPINNs): a scalable domain decomposition approach for solving differential equations."  
