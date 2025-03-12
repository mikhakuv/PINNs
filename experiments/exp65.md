Рассматриваемое уравнение:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
Коэффициенты:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  

Для решения использовалась сегментационная модель с гиперпараметрами, которые показали хороший результат на случаях с известным решением.

* Гауссиана:  $y = \frac{1}{2}\cdot e^{-x^2}$

Точности: `'Lw1_per_max': 7.252820548367566,
 'Lw1_per_mean': 2.7638973837427794,
 'Lw2_per_max': inf,
 'Lw2_per_mean': inf`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp65_charts_1.png" width="500" height="300">  

* Гауссиана:  $y = 1\cdot e^{-x^2}$

Точности: `'Lw1_per_max': 4.094128173204923,
 'Lw1_per_mean': 2.8928867014893416,
 'Lw2_per_max': inf,
 'Lw2_per_mean': inf`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp65_charts_2.png" width="500" height="300">  

* Гауссиана:  $y = 2\cdot e^{-x^2}$

Точности: `'Lw1_per_max': 2.3822917952751723,
'Lw1_per_mean': 1.530741449122327,
 'Lw2_per_max': inf,
 'Lw2_per_mean': inf`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp65_charts_3.png" width="500" height="300">  
