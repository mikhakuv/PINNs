В этом эксперименте продолжены опыты с FBPINNs, но рассмотрены большие области. Общие гиперпараметры: $x \in [-100,100]$, `x_parts=6000`, `t_parts=500`, `x_domains=80`, `t_domains=(t_1-t_0)`, `intersection = 2.0`, `unnorm=1.2`, `topology=(2,8,8,2)`, `activation=sin(x)`.
Результаты:

1. $t \in [0,20]$, число итераций: $2\cdot 10^{6}$ , время обучения: $18h\ 38m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_10_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_10_2.png">  

2. $t \in [0,30]$, число итераций: $3\cdot 10^{6}$ , время обучения: $18h\ 38m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_11_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_11_2.png">  

3. $t \in [0,28]$, число итераций: $3.68\cdot 10^{6}$ , время обучения: $23h 30m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_12_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_12_2.png">  


Оказалось, что уменьшение количества точек коллокации (до `x_parts=2000`, `t_parts=500`) не сильно влияет на точность, но при этом существенно ускоряет процесс обучения. Это позволило провести опыты с большим числом итераций:  

4. $t \in [0,50]$, число итераций: $5\cdot 10^{6}$ , время обучения: $<6h$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_13_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_13_2.png">  

5. $t \in [0,50]$, число итераций: $10\cdot 10^{6}$ , время обучения: $11h 11m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_14_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp52_charts_14_2.png">  


Успешность последнего приведённого опыта позволила перейти к ещё большим областям.  
Статистику по точностям можно найти в таблице(exp10-exp14): [performance_table_fbpinns.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table_fbpinns.xlsx)  
