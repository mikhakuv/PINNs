В этом эксперименте проводятся те же опыты, что и в exp39, но используется другое аналитическое решение:  
<https://colab.research.google.com/drive/18KxANOxek6X0Lmfr3zRwjOPt17_tAH3Q?usp=sharing>  
Используемое решение имеет вид:  
$$q(x,t)=\frac{(k^2-w)e^{\sqrt{k^2-w}(x-2kt-x_0)}*e^{i(kx-wt+\theta_0)}}{\frac{1}{16}+2(k^2-w)*e^{2\sqrt{k^2-w}(x-2kt-x_0)}}$$  
(Невязка на нём тоже немаленькая, что подозрительно)  
Наиболее удачные результаты:  
* солитон при $k=1.4,\quad w=1.8$:  
невязка на аналитическом решении: `MSE_f_u: 1.745088e-05, MSE_f_v: 1.748705e-05, First law mean/first_int(t=0): 0.00%, Second law mean/second_int(t=0): 0.00%`  
невязка на нейросети: `MSE_f_u: 1.994509e-07, MSE_f_v: 2.265459e-07, First law mean/first_int(t=0): 3.89%, Second law mean/second_int(t=0): 5.02%`  
соответствие нейросети и аналитического решения:  `MSE_u: 4.261460e-03, MSE_v: 4.259078e-03, MSE_q: 1.030091e-03`  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp40_results_1.png">  

* солитон при $k=0.0,\quad w=-0.1$:  
невязка на аналитическом решении: `MSE_f_u: 1.979391e-06, MSE_f_v: 2.128459e-06, First law mean/first_int(t=0): 0.00%, Second law mean/second_int(t=0): inf%`(second_int(t=0)=0, из-за этого inf. Second law MSE: 1.143305e-17)  
невязка на нейросети: `MSE_f_u: 1.848115e-09, MSE_f_v: 1.683008e-09, First law mean/first_int(t=0): 0.03%, Second law mean/second_int(t=0): 73.00%`(second_int(t=0)->0, из-за этого такое большое значение. Second law MSE: 2.005546e-10)  
соответствие нейросети и аналитического решения: `MSE_u: 8.889163e-04, MSE_v: 4.927654e-04, MSE_q: 1.192059e-04`  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp40_results_2.png">  

* солитон с $k=1.4, w=1.8$ и другой солитон с $k=0.0, w=-0.1$:  
невязка на нейросети: `MSE_f_u: 1.614721e-07, MSE_f_v: 1.636114e-07, First law mean/first_int(t=0): 0.65%, Second law mean/second_int(t=0): 1.44%`  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp40_results_3.png">

Модель именно этого опыта доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_40.pth)  
