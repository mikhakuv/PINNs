В этом эксперименте продолжены опыты с FBPINNs, но рассмотрены области ещё больше. Общие гиперпараметры: $x \in [-70,230]$, `x_parts=2000`, `t_parts=500`, `intersection = 2.0`, `unnorm=1.2`, `topology=(2,8,8,2)`, `activation=sin(x)`.
Результаты:

1. $t \in [0,100]$, `x_domains=80`, `t_domains=50`, число итераций: $10\cdot 10^{6}$ , время обучения: $$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_15_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_15_2.png">  

2. $t \in [0,100]$, `x_domains=120`, `t_domains=100`, число итераций: $20\cdot 10^{6}$ , время обучения: $$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_16_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_16_2.png">  

Статистику по точностям можно найти в таблице(exp14-): [performance_table_fbpinns.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table_fbpinns.xlsx)  
