В этом эксперименте используется метод из эксперимента 2, но уже с sin в качестве функции активации: <https://colab.research.google.com/drive/1S0ReuWaef29iwZqfQxWAqSHsuQ0hhuhj?usp=sharing>  
Видно, что полученные результаты лучшие из всех экспериментов на области с 0<t<50. Если считать на всей области, разность модулей mse_q=7.547776e-03, а на если на срезах с шагом 10, то mse_q=4.914450e-03.

<img src="https://github.com/mikhakuv/PINNs/blob/main/exp6_results_u_0.PNG" width="450" height="800"> <img src="https://github.com/mikhakuv/PINNs/blob/main/exp6_results_v_0.PNG" width="450" height="800">

Но визуальная схожесть совсем не означает фактической схожести решений. Это видно на срезах:
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp6_results_u_1.PNG" width="900" height="800">
\
\
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp6_results_v_1.PNG" width="900" height="800">
