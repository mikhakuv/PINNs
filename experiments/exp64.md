Рассматриваемое уравнение:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
Коэффициенты:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  

Для решения использовалась сегментационная модель с гиперпараметрами, которые показали хороший результат на случаях с известным решением.

* Солитон с $k=0$, $x_0=0$

Точности: `'Lw1_per_max': 0.4576935116230912,
 'Lw1_per_mean': 0.15984683810593966,
 'Lw2_per_max': 5.1004746387689176e+16,
 'Lw2_per_mean': 2.4066672028551364e+16`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_1.png" width="600" height="200">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_2.png" width="500" height="300">  

* Два солитона: один с $k=0$, $x_0=0$ и другой с $k=1$, $x_0=10$

Точности: `'Lw1_per_max': 0.6566198404961098,
 'Lw1_per_mean': 0.17496234565953364,
 'Lw2_per_max': 1.641455937548415,
 'Lw2_per_mean': 0.35108325677817787`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_3.png" width="600" height="200">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_4.png" width="500" height="300">  

* Гауссиана:  $y = 2\cdot e^{-x^2}$

Точности: `'Lw1_per_max': ,  
'Lw1_per_mean': ,
 'Lw2_per_max': ,
 'Lw2_per_mean': `  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_5.png" width="600" height="200">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_6.png" width="500" height="300">  

* Солитон с $k=1$, $x_0=6$ и гауссиана $y = 2\cdot e^{-(x-1)^2}$

Точности: `'Lw1_per_max': 2.9147265706910406,
 'Lw1_per_mean': 1.3347777626940296,
 'Lw2_per_max': 11.605852716992123,
 'Lw2_per_mean': 1.6455137142298057`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_7.png" width="600" height="200">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp64_charts_8.png" width="500" height="300">  
