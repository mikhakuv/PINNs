Рассматривается всё то же уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И следующими коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  

Была найдена уязвимость метода генерации точек, предложенного в [предыдущем эксперименте](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp66.md), из-за неё некоторые точки могли оставаться неподвижными на протяжении всего процесса обучения:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp66_gif_2.gif" width="500" height="300">  

Для её исправления в знаменатель всех дробей была добавлена малая добавка. Далее приведены гифки для поведения точек в случае уравнения 6-го порядка (1000, 3000 и 5000 точек соответственно):

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp67_gif_1.gif" width="500" height="300">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp67_gif_2.gif" width="500" height="300">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp67_gif_3.gif" width="500" height="300">  

Также был произведён подбор гиперпараметров для упомянутого уравнения 6-го порядка на области $[0,0.1]$:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp67_chart_1.png" width="1000" height="500">  

Видно, что параметры $\tilde{\alpha}=0.038,\ \tilde{\beta}=0.025$ являются оптимальными. Другим соотношением оптимальных параметров является $\tilde{\alpha}=0.005,\ \tilde{\beta}=0.009$ (получено при другом подборе). Оптимальное количество точек равно $3000$.

Для области $x\in[-10,10], t\in[0,1]$ были проведены сравнения качества различных методов генерации точек. Результаты можно найти в [таблице](https://github.com/mikhakuv/PINNs/blob/main/statistics/methods_accuracy.xlsx).
