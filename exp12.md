В этом эксперименте снова всё так же, как и в exp9, но использован метод балансировки SoftAdapt уже с шестью коэффициентами 
(loss = lambda_u_in\*loss_u_in + lambda_v_in\*loss_v_in + lambda_u_b\*loss_u_b + lambda_v_b\*loss_v_b + lambda_u_f\*loss_u_f + lambda_v_f\*loss_v_f):  
<https://colab.research.google.com/drive/1pn_vR3eC5TO0cg3hnMspFMLgdHqeVH3I?usp=sharing>  
Получились следующие результаты:  
MSE_u: 6.074734e-03, MSE_v: 6.050951e-03, MSE_q: 8.363874e-03, MSE_f_u: 4.822121e-06, MSE_f_v: 4.984156e-06  
Решение вышло хуже, чем при меньшем количестве коэффициентов и сеть явно недоучена. Тем не менее, mse_u и mse_v вышли даже меньше, а кривая mse_q(iter) стала ещё глаже.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_u_0.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_v_0.PNG" width="450" height="800">  
срезы:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_u_1.PNG" width="1800" height="600">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_v_1.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_2.PNG" width="1200" height="400">  
коэффициенты(жёлтая линия - при действительной части, красная - при мнимой):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_3.PNG" width="1800" height="300">  
отклонение от аналитического решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_4.PNG" width="500" height="400">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp12_results_5.PNG" width="500" height="400">
