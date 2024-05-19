В данной работе изучается эффективность применения методов Transfer Learning для PINNs в контексте решения нелинейного уравнения Шрёдингера.  
## Перенос весов модели
Обучив нейросеть на уравнении, можно сохранить её обучаемые параметры и при решении уравнения с другими коэффициентами загрузить их. Тогда будет происходить не обучение с нуля, а переучивание, которое может быть более простой задачей.
Применение такой идеи позволило увеличить точность на **47-91%**, причём пока разница в коэффициентах сравнительно небольшая, увеличение точности от неё практически не зависит(см график 1).  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/chart_1.PNG">  

(такая странная зависимость вызвана тем, что исходные опыты имеют сильный разброс по точности, в отличие от опытов с перенесёнными весами)  
## Перенос полученных значений  
Но в случае PINNs можно действовать другим способом. Так как задача оптимизации осложнена не высокой размерностью данных или большим их количеством, а видом функции потерь (которая содержит частные производные), упрощение вида функции потерь приведёт к существенному 
упрощению задачи оптимизации. Поэтому вместо переноса параметров модели можно обучить новую модель на решении, полученном ранее, причём процесс переноса не будет требовать много времени(в результате получилось 2-4 минуты). Применение этой идеи позволило с переменным 
успехом увеличить точность вплоть до **82%**, хотя результаты получились хаотичные(см график 2). Но возможно стоит не доучивать модель вовсе, а только переносить значения и показать, что точность почти не падает.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/chart_2.PNG">  

(опять же, хаотичность результатов вызвана хаотичностью исходных опытов)
## Улучшение ранее полученных результатов  
Рассмотрим задачу улучшения ранее полученных данных, когда полученный результат хорош, но есть потребность сделать его ещё лучше. Хотя видно, что перенос весов работает гораздо лучше переноса значений, он не всегда может быть реализован. Например если исходные данные получены методом FBPINNs, то можно получить веса, но это будет много весов от большого количества маленьких нейросетей, которые нельзя перенести в одну большую нейросеть. Поэтому в данном случае переносу значений нет альтернатив: нейросеть будет обучаться на данных, которые остались от FBPINN. Дополнительно можно оптимизировать этот процесс, избавившись от областей с околонулевыми значениями и разбив большой массив данных на последовательные части, на каждой из которых обучается отдельная нейросеть. Для данной задачи это приемлемо, ведь на выходе ожидается не нейросеть, а массив улучшенных данных.  
Рассмотрим пример работы данного подхода:  
1. Исходный результат:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/raw_1_fig.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/raw_1_amplitude.png">  

Разбиение данных:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_3_decomposition.png">  

Улучшенный результат:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_3_fig.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_3_amplitude.png">  

Rel_h уменьшилась на **38%**, ошибки на законах - более чем на **70%**  
Можно проделать те же самые действия и для полученных данных:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_3+_fig.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_3+_amplitude.png">  
Rel_h почему-то увеличился, но ошибки на законах дополнительно уменьшились более чем на **49%**  

2. Исходный результат:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/raw_2_fig.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/raw_2_amplitude.png">  

Разбиение данных:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_4_decomposition.png">  

Улучшенный результат:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_4_fig.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_4_amplitude.png">  

Rel_h уменьшилась на **--%**, ошибки на законах - более чем на **--%**  
Можно проделать те же самые действия и для полученных данных:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_4+_fig.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/transfer_learning/exp_4+_amplitude.png">  
Rel_h почему-то увеличился, но ошибки на законах дополнительно уменьшились более чем на **--%**  

Более подробная статистика доступна в файлах: [performance_table.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table_transfer_learning.xlsx), [enhancement_stats.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/enhancement_stats.xlsx)

