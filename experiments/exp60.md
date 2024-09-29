Рассматривается всё то же уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И такими же коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область: $x\in[-10,10], t\in[0,1]$.  

Были реализованы технологии ReLoBRaLo [[1]](https://arxiv.org/abs/2110.09813) и Causal Loss [[2]](https://arxiv.org/abs/2203.07404), но пока они не особо хорошо работают.
Также были найдены зависимости ключевых метрик `Rel_h`, `Lw1_per_mean`, `Lw2_per_mean` от `Loss`:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp60_charts_1.PNG" width="500" height="300">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp60_charts_2.PNG" width="500" height="300">  

Полную информацию можно найти в [таблице](https://github.com/mikhakuv/PINNs/blob/main/statistics/loss_stats.xlsx)
