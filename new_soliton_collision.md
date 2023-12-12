Здесь описаны наиболее удачные эксперименты по столкновению солитонов с препятствиями.  
Используемые метрики:  
$$MSE_{f_u} = \frac{\sum\limits_{i=1}^n(f_{pred_u}(x_i,t_i))^2}{n}$$
$$MSE_{f_v} = \frac{\sum\limits_{i=1}^n(f_{pred_v}(x_i,t_i))^2}{n}$$
$$ErrFl = \frac{\sum\limits_{i=1}^N |\int\limits_{x_0}^{x_1} |q^{pred}(x,t_i)|^2 dx - \int\limits_{x_0}^{x_1} |q^{truth}(x,t_0)|^2 dx|}{N\cdot\int\limits_{x_0}^{x_1} |q^{truth}(x,t_0)|^2 dx}\cdot100\\%$$
$$ErrSl = \frac{\sum\limits_{i=1}^N |\int\limits_{x_0}^{x_1} (v_x^{pred} u^{pred} - u_x^{pred} v^{pred})(x,t_i)\ dx - \int\limits_{x_0}^{x_1} (v_x^{truth} u^{truth} - u_x^{truth} v^{truth})(x,t_0)\ dx|}{N\cdot|\int\limits_{x_0}^{x_1} (v_x^{truth} u^{truth} - u_x^{truth} v^{truth})(x,t_0)\ dx|}\cdot100\\%$$
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

# [Эксперимент 2](https://colab.research.google.com/drive/1Voj78wLD-hu2eeVSeD4_pT4mP3NCrzxH#scrollTo=c3d-Gv_t-qEl)  
## (из [exp50](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp50.md))  
уравнение: $$iq_t + q_{xx} + |q|^2 q (1 - \alpha |q|^2 + \beta |q|^4) = 0$$
коэффициенты: $$\alpha=1,\quad \beta=0$$  
начальное условие: $$q(x,0)=\sqrt{\frac{4(k_1^2-w_1)\cdot e^{2\sqrt{k_1^2-w_1}\cdot(x-2k_1t-x_{0_1})}}{(1+\frac{1}{2}e^{2\sqrt{k_1^2-w_1}\cdot(x-2k_1t-x_{0_1})})^2 - \frac{1}{3}(\alpha\cdot 4(k_1^2-w_1)\cdot e^{4\sqrt{k_1^2-w_1}\cdot(x-2k_1t-x_{0_1})})}}\cdot e^{i\cdot (k_1x-w_1t-\theta_{0_1})}\quad+\quad\frac{(k_2^2-w_2)e^{\sqrt{k_2^2-w_2}(x-2k_2t-x_{0_2})}*e^{i(k_2x-w_2t+\theta_{0_2})}}{\frac{1}{16}+2(k_2^2-w_2)*e^{2\sqrt{k_2^2-w_2}(x-2k_2t-x_{0_2})}}$$  
коэффициенты: $$k_1=1.4,\quad w_1=1.8,\quad x_{0_1}=-40,\quad \theta_{0_1}=0,\quad k_2=0.0,\quad w_2=-0.1,\quad x_{0_2}=0,\quad \theta_{0_2}=0$$  
график начального условия:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_ic_s.png">  

точность решения: $$MSE_{f_u}=1.743\cdot10^{-7},\quad MSE_{f_v}=1.526\cdot10^{-7},\quad ErrFl=2.92\\%,\quad ErrSl=5.07\\%$$  
график решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_heatmap_s.png">  

по срезам:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_slices_s.png">  

график соблюдения законов сохранения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_laws_s.png">  

# [Эксперимент 3](https://colab.research.google.com/drive/1IH9gyxRPYXZqmihGXD1sZ3t4rs6BEola#scrollTo=equmSNU7m6x3)  
## (из [exp50](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp50.md))  
уравнение: $$iq_t + q_{xx} + |q|^2 q (1 - \alpha |q|^2 + \beta |q|^4) = 0$$
коэффициенты: $$\alpha=1,\quad \beta=0$$  
начальное условие: $$q(x,0)=\sqrt{\frac{4(k^2-w)\cdot e^{2\sqrt{k^2-w}\cdot(x-2kt-x_{0})}}{(1+\frac{1}{2}e^{2\sqrt{k^2-w}\cdot(x-2kt-x_{0})})^2 - \frac{1}{3}(\alpha\cdot 4(k^2-w)\cdot e^{4\sqrt{k^2-w}\cdot(x-2kt-x_{0})})}}\cdot e^{i\cdot (kx-wt-\theta_{0})}\quad+\quad\frac{1}{10}e^{-(\frac{x}{10})^2}$$  
коэффициенты: $$k=1.5,\quad w=2.2,\quad x_{0}=-40,\quad \theta_{0}=0$$  
график начального условия:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_ic_lg.png">  

точность решения: $$MSE_{f_u}=5.810\cdot10^{-8},\quad MSE_{f_v}=6.161\cdot10^{-8},\quad ErrFl=3.32\\%,\quad ErrSl=4.06\\%$$  
график решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_heatmap_lg.png">  

по срезам:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_slices_lg.png">  

график соблюдения законов сохранения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp50_laws_lg.png">  
