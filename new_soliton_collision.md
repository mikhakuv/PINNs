Здесь описаны наиболее удачные эксперименты по столкновению солитонов с препятствиями.  
Используемые метрики:  
$$MSE_{f_u} = \frac{\sum\limits_{i=1}^n(f_{pred_u}(x_i,t_i))^2}{n}$$
$$MSE_{f_v} = \frac{\sum\limits_{i=1}^n(f_{pred_v}(x_i,t_i))^2}{n}$$
$$ErrFl = \frac{\sum\limits_{i=1}^N |\int\limits_{x_0}^{x_1} |q(x,t_i)|^2 dx - \int\limits_{x_0}^{x_1} |q(x,t_0)|^2 dx|}{N\cdot\int\limits_{x_0}^{x_1} |q(x,t_0)|^2 dx}\cdot100\\%$$
$$ErrSl = \frac{\sum\limits_{i=1}^N |\int\limits_{x_0}^{x_1} (v_x u - u_x v)(x,t_i)\ dx - \int\limits_{x_0}^{x_1} (v_x u - u_x v)(x,t_0)\ dx|}{N\cdot|\int\limits_{x_0}^{x_1} (v_x u - u_x v)(x,t_0)\ dx|}\cdot100\\%$$
# [Эксперимент 1](https://colab.research.google.com/drive/1MqNPmd4CWrGLLqPaZLk9sNnN1TU7IXwc#scrollTo=c3d-Gv_t-qEl)  
## (из [exp48](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp48.md))  
уравнение: $$iq_t + q_{xx} + |q|^2 q (1 - \alpha |q|^2 + \beta |q|^4) = 0$$
коэффициенты: $$\alpha=1,\quad \beta=0$$  
начальное условие: $$q(x,0)=\sum\limits_{i=1}^2\frac{(k_i^2-w_i)e^{\sqrt{k_i^2-w_i}(x-2k_it-x_{0_i})}*e^{i(k_ix-w_it+\theta_{0_i})}}{\frac{1}{16}+2(k_i^2-w_i)*e^{2\sqrt{k_i^2-w_i}(x-2k_it-x_{0_i})}}$$  
коэффициенты: $$k_1=1.4,\quad w_1=1.8,\quad x_{0_1}=-40,\quad \theta_{0_1}=0,\quad k_2=0.0,\quad w_2=-0.1,\quad x_{0_2}=0,\quad \theta_{0_2}=0$$  
график начального условия:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp48_ic_s.png">  

точность решения: $$MSE_{f_u}=1.395\cdot10^{-7},\quad MSE_{f_v}=1.366\cdot10^{-7},\quad ErrFl=1.24\\%,\quad ErrSl=1.88\\%$$  
график решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp48_heatmap_s.png">  

по срезам:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp48_slices_s.png">  

график соблюдения законов сохранения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp48_laws_s.png">  

