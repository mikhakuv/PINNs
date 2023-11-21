Здесь описаны наиболее удачные эксперименты по столкновению солитонов с препятствиями.  
Используемые метрики:  
$$MSE_{f_u} = \frac{\sum\limits_{i=1}^n(f_{pred_u}(x_i,t_i))^2}{n}$$
$$MSE_{f_v} = \frac{\sum\limits_{i=1}^n(f_{pred_v}(x_i,t_i))^2}{n}$$
$$MRF = \frac{\sum\limits_{i=1}^N |\int\limits_{x_0}^{x_1} |q(x,t_i)|^2 dx - \int\limits_{x_0}^{x_1} |q(x,t_0)|^2 dx|}{\int\limits_{x_0}^{x_1} |q(x,t_0)|^2 dx}\cdot100\\%$$
$$MRS = \frac{\sum\limits_{i=1}^N |\int\limits_{x_0}^{x_1} (v_x u - u_x v)(x,t_i)\ dx - \int\limits_{x_0}^{x_1} (v_x u - u_x v)(x,t_0)\ dx|}{|\int\limits_{x_0}^{x_1} (v_x u - u_x v)(x,t_0)\ dx|}\cdot100\\%$$
# эксперимент 1  
уравнение: $$iq_t + q_{xx} + |q|^2 q (1 - \alpha |q|^2 + \beta |q|^4) = 0$$
коэффициенты: $$\alpha=1,\quad \beta=0$$  
начальное условие: $$q(x, 0)=\frac{4(k^{2} - w)}{\sqrt{k^2-w}*e^{\sqrt{k^{2} - w} (x - 2kt - x_0)} + 2\sqrt{k^{2}-w}*e^{-\sqrt{k^{2} - w} (x-2kt-x_0)}} e^{i(kx - wt + \theta_{0})}\quad +\quad e^{-\frac{x}{2}^2}$$
коэффициенты: $$k=1.4,\quad w=1.8,\quad x_0=-40,\quad \theta_0=0$$  
график начального условия:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/collisions_ic_1.png">  

точность решения: $$MSE_{f_u}=8.095\cdot10^{-7},\quad MSE_{f_v}: 9.747\cdot10^{-7},\quad MRF=2.40\\%,\quad MRS=1.67\\%$$  
график решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/collisions_results_uv_1.png">  

график соблюдения законов сохранения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/collisions_results_laws_1.png">  

# Эксперимент 2  
уравнение: $$iq_t + q_{xx} + |q|^2 q (1 - \alpha |q|^2 + \beta |q|^4) = 0$$
коэффициенты: $$\alpha=1,\quad \beta=0$$  
начальное условие: $$q(x,0)=\sum\limits_{i=1}^2\frac{(k_i^2-w_i)e^{\sqrt{k_i^2-w_i}(x-2k_it-x_{0_i})}*e^{i(k_ix-w_it+\theta_{0_i})}}{\frac{1}{16}+2(k_i^2-w_i)*e^{2\sqrt{k_i^2-w_i}(x-2k_it-x_{0_i})}}$$  
коэффициенты: $$k_1=1.4,\quad w_1=1.8,\quad x_{0_1}=-40,\quad \theta_{0_1}=0,\quad k_2=0.0,\quad w_2=-0.1,\quad x_{0_2}=0,\quad \theta_{0_2}=0$$  
график начального условия:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/collisions_ic_2.png">  

точность решения: $$MSE_{f_u}=1.615\cdot10^{-7},\quad MSE_{f_v}: 1.636\cdot10^{-7},\quad MRF=0.65\\%,\quad MRS=1.44\\%$$  
график решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/collisions_results_uv_2.png">  

график соблюдения законов сохранения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/collisions_results_laws_2.png">  
