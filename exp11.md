В этом эксперименте всё так же, как и в exp9, но использован метод балансировки SoftAdapt с тремя коэффициентами  (loss = lambda_in\*loss_in + lambda_b\*loss_b + lambda_f\*loss_f):
<https://colab.research.google.com/drive/1VSheui0465boMzqqJjo2SadU14WwnvER?usp=sharing>  
Получились следующие результаты:  

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
