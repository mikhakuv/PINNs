В этом эксперименте проводились опыты по столкновению двух солитонов с разными $k$ $w$, но одинаковыми $\mu$:  
<https://colab.research.google.com/drive/1AFXP7Rg11IHs-6lA9RqIupykFAZBrNrE?usp=sharing>  
Наиболее успешные опыты получились для начального условия: $$q(x, 0)=\frac{4(k^{2} - w)\cdot e^{i(kx - wt + \theta_{0})}}{\sqrt{k^2-w}*e^{\sqrt{k^{2} - w} (x - 2kt - x_0)} + 2\sqrt{k^{2}-w}*e^{-\sqrt{k^{2} - w} (x-2kt-x_0)}}$$
* солитон с $k=1.4, w=1.8$ и другой солитон с $k=-0.7, w=0.33$
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp43_results_1.png">  

Точность: `MSE_f_u: 1.214035e-06, MSE_f_v: 1.346597e-06, First law mean/first_int(t=0): 3.27%, Second law mean/second_int(t=0): 15.32%`  
Модель доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_43_1.pth)  

* солитон с $k=1.4, w=1.8$ и другой солитон с $k=-1.0, w=0.84$
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp43_results_2.png">

Точность: `MSE_f_u: 9.313288e-07, MSE_f_v: 8.771748e-07, First law mean/first_int(t=0): 4.33%, Second law mean/second_int(t=0): 20.63%`  
Модель доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_43_2.pth)  

Но также есть успешный опыт и для другого начального условия: $$q(x,0)=\frac{(k^2-w)e^{\sqrt{k^2-w}(x-2kt-x_0)}*e^{i(kx-wt+\theta_0)}}{\frac{1}{16}+2(k^2-w)*e^{2\sqrt{k^2-w}(x-2kt-x_0)}}$$  
* солитон с $k=1.4, w=1.8$ и другой солитон с $k=-1.0, w=0.84$
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp43_results_3.png">  

Точность: `MSE_f_u: 1.535311e-06, MSE_f_v: 1.550465e-06, First law mean/first_int(t=0): 6.06%, Second law mean/second_int(t=0): 42.00%`  
Модель доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_43_3.pth)  
