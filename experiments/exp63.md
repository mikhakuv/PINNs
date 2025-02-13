Рассматриваемая задача остаётся та же:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
Коэффициенты:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область:  средняя: $x\in[-20,20], t\in[0,1]$

Проблема с сегментацией оказалась в том, что площадь сегментов была слишком большая и из-за этого подобранные ранее коэффициенты не давали настолько же хороших результатов. При уменьшении площади сегментов до сопоставимой, получились следующие результаты:  

* Один солитон:  

Точности: `'Lw1_per_max': 2.202083833003037,  
 'Lw1_per_mean': 0.859222590510077,  
 'Lw2_per_max': 2.2265951145359493,  
 'Lw2_per_mean': 0.9431832563025244,  
 'Rel_h': 0.023279113719561772`

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp63_charts_1.png" width="500" height="300">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp63_charts_2.png" width="500" height="300">  

* Два солитона:  

Точности: `'Lw1_per_max': 2.997193855470598,  
'Lw1_per_mean': 1.1985204728129075,  
 'Lw2_per_max': 3.129263996263047,  
 'Lw2_per_mean': 1.240211054585871,  
 'Rel_h': 0.020880621613351615`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp63_charts_3.png" width="500" height="300">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp63_charts_4.png" width="500" height="300">  
