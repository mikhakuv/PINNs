Рассматривается уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И такими же коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область: $x\in[-10,10], t\in[0,1]$.  

Был применён [новый способ](https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp58.ipynb) генерации точек, в котором вероятность включения точки в набор зависит от невязки в этой точке и значения модуля решения в ней:  
$MSE_q$ = `8.256e-02`, $Rel_h$ = `2.835e-01`, считалось ~8 часов  
решение:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp58_charts_1.png">  

невязка:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp58_charts_2.png">  

Также была попытка использовать другой оптимизатор, предложенный в [[1]](https://arxiv.org/abs/2402.01868). Он конфликтует с lbfgs, поэтому получается использовать его только вместе с adam. Возможно дело в параметрах, но пока у него не получается снижать loss.

[1] *Pratik Rathore, Weimu Lei, Zachary Frangella, Lu Lu, Madeleine Udell* "Challenges in Training PINNs: A Loss Landscape Perspective"
