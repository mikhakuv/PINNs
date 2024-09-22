Рассматривается уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И такими же коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область: $x\in[-10,10], t\in[0,1]$.  

Вновь исследуются методы генерации точек, впервые рассмотренные в [exp58](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp58.md). В этот раз частота генерации значительно уменьшена, а также вычислены стандартизированные ошибки.

| points generation method | random | hl_1   | hl_2   | hl_3   |
|--------------------------|--------|--------|--------|--------|
| lambda_1                 | -      | 0      | 0.005  | -      |
| lambda_2                 | -      | -      | -      | 0.01   |
| generation_frequency     | 1000   | 1000   | 1000   | 1000   |
| Iterations               | 10000  | 10000  | 10000  | 10000  |
| Lw1_per_max              | 6,208  | 3,956  | 7,583  | 4,539  |
| Lw1_per_mean             | 4,340  | 2,880  | 5,175  | 3,441  |
| Lw2_per_max              | 7,777  | 4,187  | 8,842  | 4,795  |
| Lw2_per_mean             | 5,480  | 3,144  | 6,112  | 3,743  |
| Rel_h                    | 0,335  | 0,341  | 0,341  | 0,345  |
| Time                     | 44 min | 47 min | 46 min | 46min  |

Видно, что на Rel_h они почти не влияют, но немного снижают ошибки на законах.  
Также была попытка сделать больше итераций оптимизатором NNCG (100000 ADAM + 10000 LBFGS + 40000 NNCG):
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp59_charts_1.png">  

Видно, что большую часть работы сделал ADAM, а LBFGS и NNCG ничего заметного не достигли.  
Итоговый Loss: 0.0002351  
Ошибки:   `Lw1_per_max=1.038`, `Lw1_per_mean=0.966`, `Lw2_per_max=1.244`, `Lw2_per_mean=1.108`, `Rel_h=0.322`  
Решение:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp59_charts_2.png">  

Невязка:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp59_charts_3.png">  
