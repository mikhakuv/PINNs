В этом эксперименте всё так же, как и в exp9, но использован метод балансировки SoftAdapt с тремя коэффициентами  
(loss = lambda_in\*loss_in + lambda_b\*loss_b + lambda_f\*loss_f):  
<https://colab.research.google.com/drive/1VSheui0465boMzqqJjo2SadU14WwnvER?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.072081e-02, MSE_v: 1.071946e-02, MSE_q: 1.292879e-03, MSE_f_u: 3.370290e-07, MSE_f_v: 2.950920e-07  
Решение получилось хуже, чем в предыдущих экспериментах, но если посмотреть на график mse_q(iter) и сравнить с такими же графиками из exp9 или exp10, то можно заметить, что он стал стабильнее. (Более того, оптимизатору adam могло просто не хватить шагов и качество такое низкое из-за этого)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_u_0.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_v_0.PNG" width="450" height="800">  
срезы:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_u_1.PNG" width="1800" height="600">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_v_1.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_2.PNG" width="1200" height="400">  
коэффициенты lambda_in, lambda_b и lambda_f(жёлтая, розовая и красная линии соответственно):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_3.PNG" width="600" height="400">  
отклонение от аналитического решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_4.PNG" width="600" height="400">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp11_results_5.PNG" width="600" height="400">
