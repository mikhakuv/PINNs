В этом эксперименте проводились эксперименты с FBPINNs - одним из усовершенствований технологии PINNs, [упомянутым](https://github.com/mikhakuv/PINNs/blob/main/proposals_for_PINNs.md) ранее.  
Производилось решение уравнения Шрёдингера с начальным условием в виде солитона, для которого решение известно. Были испробованы разные параметры разбиения на области, перекрытия областей, нормализации.
Наиболее удачные результаты приведены ниже:  
* разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.8)  
[таблица значений](https://drive.google.com/file/d/1Dk4CSxJGrjlirqV7sQpnBrEY_3PxrnkY/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_1.png">  

* разбитие на области: 40 по x, 10 по t; наезжание областей: 2.0; топология: (2, 8, 8, 2); денормализация: (0.0, 1.2)  
[таблица значений](https://drive.google.com/file/d/16tNRvqY5jZpwLJY9Tz3FiEeJ6NufuPVr/view?usp=sharing)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_2.png">  

<!---* разбитие на области: 40 по x, 10 по t; наезжание областей: 1.5; топология: (2, 5, 5, 2); денормализация: (0.0, 1.2)  
[таблица значений](https://github.com/mikhakuv/PINNs/blob/main/statistics/exp51_results_3.csv)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp51_charts_3.png">  ---!>
