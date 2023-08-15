В этом эксперименте использовано всё то же, что и в exp9, но используется метод балансировки SoftAdapt с двумя коэффициентами (loss = lambda_uv\*loss_uv + lambda_f\*loss_f):  
<https://colab.research.google.com/drive/1JkWOaK-RR_Q0ptb6nVSplzYbkNpDenoe?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.139319e-02, MSE_v: 1.139416e-02, MSE_q: 4.298467e-04, MSE_f_u: 1.084106e-07, MSE_f_v: 1.099829e-07  
Решение всё ещё визуально похоже на аналитическое, но точность хуже(вероятно из-за того, что оптимизатор lbfgs почти сразу завершился)  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_u_0.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_v_0.PNG" width="450" height="800">  
срезы:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_u_1.PNG" width="1800" height="600">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_v_1.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_2.PNG" width="1200" height="400">  
коэффициенты lambda_uv и lambda_f(жёлтая и красная линии соответственно):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_3.PNG" width="600" height="400">  
отклонение от аналитического решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_4.PNG" width="600" height="400">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp10_results_5.PNG" width="600" height="400">  
