В этом эксперименте находятся более точные решения для некоторых начальных условий из exp37, а также проводятся опыты с прохождением солитона сквозь заданные таким образом препятствия:
<https://colab.research.google.com/drive/1_dj__EbFA3vHLXWkEEVa4WmgloZSrZH0?usp=sharing>  
Проблема в том, что при начальном условии для солитона при $k=0.0, w=-0.5$ получается вовсе не солитон:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp39_results_1.png">  

При этом точность на уравнении и законах сохранения высокая: `MSE_f_u: 4.149019e-07, MSE_f_v: 4.643179e-07, First law mean/first_int(t=0): 0.95%, Second law mean/second_int(t=0): 30.60%`  
Такие результаты ставят под сомнение всё, что получено в этом эксперименте, ведь найденное решение строго говоря подходит, но при этом отличается от заведомо верного аналитического.
Тем не менее, в одном их экспериментов получилась неплохая картина прохождения солитона при $k=1.4, w=1.8$ сквозь препятствие $q(x,0)=e^{-\frac{x}{2}^2}$:
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp39_results_2.png">  

Точность: `MSE_f_u: 8.095225e-07, MSE_f_v: 9.746719e-07, First law mean/first_int(t=0): 2.40%, Second law mean/second_int(t=0): 1.67%`  
Модель именно этого опыта доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_39.pth)  
