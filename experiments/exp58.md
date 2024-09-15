Рассматривается уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И такими же коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область: $x\in[-10,10], t\in[0,1]$.  

Есть разные способы генерации точек, до сих пор использовался только метод **random**. По данным таблицы видно, что действительно снижают loss только **hl_2** и **hl_3**.

| points generation method | random    | hl_1      | hl_2      | hl_3       |
|--------------------------|-----------|-----------|-----------|------------|
| lambda_1                 | -         | 0         | 0.005     | -          |
| lambda_2                 | -         | -         | -         | 0.01       |
| generation_frequency     | 10        | 10        | 10        | 10         |
| Iterations               | 10000     | 10000     | 10000     | 10000      |
| Loss                     | 2.438e-02 | 4.299e-02 | 1.111e-02 | 2.136e-02  |
| MSE_q                    | 9.794e-02 | 1.050e-01 | 1.008e-01 | 1.027e-01  |
| Rel_h                    | 2.898e-01 | 3.010e-01 | 2.938e-01 | 2.948e-01  |
| Time                     | 43 min    | 44 min    | 47 min    | 45 min     |

На большем числе итераций был опробован [hl_3](https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp58.ipynb):  
$MSE_q$ = `8.256e-02`, $Rel_h$ = `2.835e-01`, считалось ~8 часов  
решение:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp58_charts_1.png">  

невязка:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp58_charts_2.png">  

<!--Также был опробован hl_2:  
$MSE_q$ = ``, $Rel_h$ = ``, считалось ~ часов  
решение:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp58_charts_3.png">  

невязка:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp58_charts_4.png">  -->

Также была попытка использовать другой оптимизатор, предложенный в [[1]](https://arxiv.org/abs/2402.01868). Он конфликтует с lbfgs, поэтому получается использовать его только вместе с adam. Пока результаты не очень удачные: оптимизатор работает слишком долго.

[1] *Pratik Rathore, Weimu Lei, Zachary Frangella, Lu Lu, Madeleine Udell* "Challenges in Training PINNs: A Loss Landscape Perspective"
