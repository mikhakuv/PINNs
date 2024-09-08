Рассматривается то же уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
Но коэффициенты другие для большей нелинейности:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область: $x\in[-10,10], t\in[0,1]$.  
Решение на области имеет вид:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp57_charts_1.png">  
Его невязка:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp57_charts_2.png">  

Применялось 2 способа для вычисления решения:  
* [**PINN**](https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp57_PINN.ipynb): $MSE_q$ = `7.959e-02`, $Rel_h$ = `2.801e-01`, считалось ~9 часов

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp57_charts_3.png">  

<!--
* [**FBPINN**](https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp57_FBPINN.ipynb): $MSE_q$ = ``, $Rel_h$ = ``, считалось ~ часов

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp56_charts_4.png">  
-->
