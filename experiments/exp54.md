В этом эксперименте проводятся опыты с FBPINNs, для которых точное решение неизвестно. Общие гиперпараметры: $x \in [-70,230]$, $t \in [0,100]$, `x_parts=2000`, `t_parts=500`, `x_domains=60`, `t_domains=100`, `intersection = 2.0`, `unnorm=0.25`, `topology=(2,5,5,2)`, `activation=sin(x)`.
Результаты:

1. $\alpha=0.3,\ \alpha=0.35$, число итераций: $70\cdot 10^{6}$ , время обучения: $\sim 40h\ 27m$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp54_charts_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp54_charts_2.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp54_charts_3.png">  
