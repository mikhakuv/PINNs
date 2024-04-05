В этом эксперименте продолжены опыты с FBPINNs, но рассмотрены области ещё больше. Общие гиперпараметры: $x \in [-70,230]$, `x_parts=2000`, `t_parts=500`, `intersection = 2.0`, `unnorm=1.2`, `topology=(2,8,8,2)`, `activation=sin(x)`.
Результаты:

1. $t \in [0,100]$, `x_domains=80`, `t_domains=50`, число итераций: $10\cdot 10^{6}$ , время обучения: $-$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_15_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_15_2.png">  

2. $t \in [0,100]$, `x_domains=120`, `t_domains=100`, число итераций: $20\cdot 10^{6}$ , время обучения: $12h\ 20m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_16_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_16_2.png">

3. $t \in [0,100]$, `x_domains=60`, `t_domains=50`, число итераций: $19,3\cdot 10^{6}$ , время обучения: $\sim 23h\ 30m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_17_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_17_2.png">  

4. $t \in [0,100]$, `x_domains=80`, `t_domains=50`, число итераций: $50\cdot 10^{6}$ , время обучения: $\sim 58h\ 39m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_18_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_18_2.png">  

5. $t \in [0,100]$, `x_domains=60`, `t_domains=100`, `unnorm=0.25`, `topology=(2,5,5,2)`, число итераций: $50\cdot 10^{6}$ , время обучения: $\sim 28h\ 40m$   
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_19_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp53_charts_19_2.png">  


Статистику по точностям можно найти в таблице(exp14-exp19): [performance_table_fbpinns.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table_fbpinns.xlsx)  
