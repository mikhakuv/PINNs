В этом эксперименте проводились эксперименты с FBPINNs - одним из усовершенствований технологии PINNs, [упомянутым](https://github.com/mikhakuv/PINNs/blob/main/proposals_for_PINNs.md) ранее.  
Производилось решение уравнения Шрёдингера с начальным условием в виде солитона, для которого решение известно. Были испробованы разные параметры разбиения на области, перекрытия областей, нормализации.
Наиболее удачные результаты приведены ниже:  
* разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.8); функция активации: tanh  
[таблица значений](https://drive.google.com/file/d/1bKZMOGo5JP83qFLWyXXizFbqJlwtxLnk/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1_2.png">  

* разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: tanh  
[таблица значений](https://drive.google.com/file/d/1boMzTIABIH_voAKmIt1CqPm3ghzu-zpT/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2_2.png">  

* разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.2); функция активации: tanh  
[таблица значений](https://drive.google.com/file/d/14eUGk8VbYc6uNHKfmdOlItmy-9-UL3nu/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_3_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_3_2.png">  

* разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 5, 5, 2); денормализация: (0.0, 1.8); функция активации: tanh  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_4_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_4_2.png">

* разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2); функция активации: sin  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_5_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_5_2.png">  


Видно, что усиление наезжания областей даёт значительное повышение точности решения(порядка 10 раз). Это можно объяснить тем, что значение в каждой точке получается как взвешенное среднее из нескольких нейросетей, то есть образуется что-то вроде ансамбля из нейросетей, который очевидно точнее если каждая из нейросетей по отдельности достаточно точна.
