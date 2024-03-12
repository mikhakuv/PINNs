В этом эксперименте проводились эксперименты с FBPINNs - одним из усовершенствований технологии PINNs, [упомянутым](https://github.com/mikhakuv/PINNs/blob/main/proposals_for_PINNs.md) ранее.  
Производилось решение уравнения Шрёдингера с начальным условием в виде солитона, для которого решение известно. Были испробованы разные параметры разбиения на области, перекрытия областей, нормализации.
Наиболее удачные результаты приведены ниже:  
1. разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.8); функция активации: $tanh(x)$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1_2.png">  

2. разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: $tanh(x)$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2_2.png">  

3. разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.2); функция активации: $tanh(x)$  
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
На основании проведённых опытов можно сказать, что:  
1) Нужно применять функцию активации $sin(x)$  
2) Широкое перекрытие областей(2.0) существенно повышает точность (это можно объяснить тем, что значение в каждой точке получается как взвешенное среднее из нескольких нейросетей, то есть образуется что-то вроде ансамбля из нейросетей, который очевидно точнее если каждая из нейросетей по отдельности достаточно точна)  
3) Если в каждом отдельном сегменте уравнение решается точно, то Rel_h не возрастает со временем(!!!)  
4) Для достижения этого нужно увеличивать топологию(в меньшей степени) и число итераций(в большей степени)  
5) Если масштабировать показавшиеся успешными на маленькой области параметры на большую область, то полученная модель будет учиться около суток  
6) Так и не удалось достигнуть точности $Rel_h<5\cdot 10^{-3}$ даже на маленькой области  

