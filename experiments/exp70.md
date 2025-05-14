Рассматривается уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И следующими коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  

Были произведены эксперименты с параллельно идущими солитонами с целью нахождения минимального расстояния, на котором они будут проходить без взаимодействия:

* $\Delta x = 10$ - **распыления нет**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_1.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_2.png" width="1000" height="500">  

* $\Delta x = 9$ - **распыления нет**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_17.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_18.png" width="1000" height="500">  

* $\Delta x = 8$ - **распыления нет**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_3.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_4.png" width="1000" height="500">  

* $\Delta x = 7.9375$ - **распыляется только один солитон**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_11.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_12.png" width="1000" height="500">  

* $\Delta x = 7.875$ - **распыление есть**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_13.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_14.png" width="1000" height="500">  

* $\Delta x = 7.75$ - **распыляется только один солитон**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_15.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_16.png" width="1000" height="500">  

* $\Delta x = 7.5$ - **распыляется только один солитон**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_5.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_6.png" width="1000" height="500">  

* $\Delta x = 7$ - **распыление есть**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_7.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_8.png" width="1000" height="500">  

* $\Delta x = 6$ - **распыление есть**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_9.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_10.png" width="1000" height="500">  

---

Дополнительно была измерена полуширина солитона, в данном случае она равняется **~2.63565**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_20.png" width="500" height="500">  

---

**Итог: минимальное расстояние, на котором солитоны могут проходить без взаимодействия лежит в промежутке [7.937, 8.000], что составляет [3.011, 3.036] полуширин.**

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_19.png" width="800" height="300">  

---

Дополнительно: сравнение результатов для $\Delta x = 9$:

Модель, предсказавшая распыление:

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_35.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_21.png" width="600" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_22.png" width="600" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_23.png" width="500" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_24.png" width="500" height="500">  

Модель, предсказавшая устойчивость:

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_18.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_25.png" width="600" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_26.png" width="600" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_27.png" width="500" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_28.png" width="500" height="500">  

Разностная схема даёт противоречивые результаты:

При `nx = 770`, `nt = 2000`предсказывается устойчивость:  

`'Lw1_per_max': 1.2240598015569777,
 'Lw1_per_mean': 0.611592773293581,
 'Lw2_per_max': 0.20330019860638512,
 'Lw2_per_mean': 0.11112413399275119,
 'Rel_h': 0.03769559637054891`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_29.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_30.png" width="1000" height="500">  

При многих других сочетаниях предсказывается неустойчивость:  

`'Lw1_per_max': 1.0319866107970688,
 'Lw1_per_mean': 0.5058572693272787,
 'Lw2_per_max': 0.2608211747045256,
 'Lw2_per_mean': 0.06353678837696214,
 'Rel_h': 0.2885905825727266`  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_31.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_32.png" width="1000" height="500">  

Но такие схемы предсказывают её и тогда, когда никакого взаимодействия уже быть не должно (солитоны слишком далеко):  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp70_chart_33.png" width="1000" height="500">  
