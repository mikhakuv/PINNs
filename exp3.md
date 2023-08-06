В этом эксперименте используется функция активации sin для обучения обычной сети 100\*100\*100, а граничные условия в xx2 и xx3 установлены равными 0: https://colab.research.google.com/drive/1MQo5PAhRZiFCnRDpWm20qSn-ReE457q6?usp=sharing  
Видно, что результат заметно лучше и при любых z0(пробовал -45, -40, 0, 40, 100, 200) решение всё ещё ищется, хоть и сдвигаясь(относительно аналитического), затухает с увеличением времени. Поэтому в последующих экспериментах будет использоваться такая же функция активации.

<img src="https://github.com/mikhakuv/PINNs/blob/main/exp3_results_u_0.PNG" width="450" height="800"> <b>u при z0=-45</b>
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp3_results_u_1.PNG" width="450" height="800"> <b>u при z0=0</b>
\
\
\
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp3_results_v_0.PNG" width="450" height="800"> <b>v при z0=-45</b>
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp3_results_v_1.PNG" width="450" height="800"> <b>v при z0=0</b>
