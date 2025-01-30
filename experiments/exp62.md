Рассматриваемая задача:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И такими же коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Области:  
* малая: $x\in[-20,20], t\in[0,0.5]$
* стандартная: $x\in[-10,10], t\in[0,1]$
* большая: $x\in[-20,20], t\in[0,1.5]$

На всех областях был оценён прирост точности от повторного использования весов в сегментационной модели (см [таблицу](https://github.com/mikhakuv/PINNs/blob/main/statistics/Seg_PINN.xlsx)):  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp62_charts_1.png" width="500" height="300">  

Также был сделан запуск с двумя солитонами, идущими друг за другом на большой области:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp62_charts_2.png" width="500" height="300">  

Модель с теми же параметрами решает задачу с одним солитоном следующим образом:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp62_charts_3.png" width="500" height="300">  
