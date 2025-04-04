Рассматриваемая задача:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И такими же коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  
Область: $x\in[-10,10], t\in[0,1]$.  

1. Была реализована идея разделения нейросети на две части с топологиями [1,...,2k] и вычисления выхода как скалярного произведения k чётных элементов (действительная часть) и k нечётных элементов (мнимая часть).
Это должно было снизить вычислительные затраты: если сделать малой сеть, соответствующую входу координаты $x$, то производные высоких порядков по $x$ будут вычисляться легче(?). Эксперименты показали, что
на практике скорость обучения уменьшилась, а на размер сети появились ограничения: сети со слишком малым числом слагаемых (возникающих в скалярном произведении) имели видимые артефакты на выходе;
у слишком больших сетей мог сильно расти loss и дальнейшее обучение лишь снижало его до более ранних значений. Результаты можно увидеть в [таблице](https://github.com/mikhakuv/PINNs/blob/main/statistics/SP_PINN.xlsx).

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp61_charts_1.png" width="500" height="300">  

2. Также была реализована уже избитая идея с сегментацией, но с некоторыми нововведениями. Во-первых, результатом обучения становится не набор моделей, а одна модель, которая обучается на решениях, полученных в каждом из сегментов и уравнении.
Во-вторых, при обучении новой модели на новом сегменте, доступна возможность использования весов предыдущей модели, что ускоряет обучение. Эксперименты показали, что сегментация позволяет получить решения меньшего качества, но значительно быстрее
(см [другую таблицу](https://github.com/mikhakuv/PINNs/blob/main/statistics/Seg_PINN.xlsx)). Также сегментацию можно в будущем использовать для нахождения решения на больших областях.

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp61_charts_2.png" width="500" height="300">  
