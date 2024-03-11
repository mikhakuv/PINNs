В этом эксперименте проводились эксперименты с FBPINNs - одним из усовершенствований технологии PINNs, [упомянутым](https://github.com/mikhakuv/PINNs/blob/main/proposals_for_PINNs.md) ранее.  
Производилось решение уравнения Шрёдингера с начальным условием в виде солитона, для которого решение известно. Были испробованы разные параметры разбиения на области, перекрытия областей, нормализации.
Наиболее удачные результаты приведены ниже:  
1. разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.8); функция активации: $tanh(x)$  
[таблица значений](https://drive.google.com/file/d/1bKZMOGo5JP83qFLWyXXizFbqJlwtxLnk/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1_2.png">  

2. разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $tanh(x)$  
[таблица значений](https://drive.google.com/file/d/1boMzTIABIH_voAKmIt1CqPm3ghzu-zpT/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2_2.png">  

3. разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.2); функция активации: $tanh(x)$  
[таблица значений](https://drive.google.com/file/d/14eUGk8VbYc6uNHKfmdOlItmy-9-UL3nu/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_3_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_3_2.png">  

4. разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 5, 5, 2); денормализация: (0.0, 1.8); функция активации: $tanh(x)$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_4_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_4_2.png">

5. разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $sin(x)$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_5_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_5_2.png">

6. разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $c\cdot sin(o x)$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_6_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_6_2.png">

7. разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $sin(x)$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_7_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_7_2.png">  

---
опыты на большей области  
8. разбитие на области: 80 по x, 50 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $sin(x)$; число итераций: $10^{6}$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_8_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_8_2.png">  

9. разбитие на области: 80 по x, 50 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $sin(x)$ число итераций: $3\cdot 10^{6}$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_9_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_9_2.png">  


Статистику по точности проведённых экспериментов можно найти в таблице: [performance_table_fbpinns.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table_fbpinns.xlsx)  
Видно, что усиление наезжания областей даёт значительное повышение точности решения(порядка 6 раз), но что более важно - целевая метрика Rel_h больше не увеличивается с течением времени, особенно если взять функцию активации sin. Это можно объяснить тем, что значение в каждой точке получается как взвешенное среднее из нескольких нейросетей, то есть образуется что-то вроде ансамбля из нейросетей, который очевидно точнее если каждая из нейросетей по отдельности достаточно точна.
