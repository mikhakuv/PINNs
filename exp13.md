В этом эксперименте всё так же, как и в exp10 (loss = lambda_in\*loss_in + lambda_b\*loss_b + lambda_f\*loss_f), но коэффициенты генерируются случайным образом каждую итерацию:  
<https://colab.research.google.com/drive/1wGtplUm1XX3aA7BrZsNeQ7PoRShjUgBp?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.101067e-02, MSE_v: 1.101248e-02, MSE_q: 8.545287e-04, MSE_f_u: 2.385132e-07, MSE_f_v: 2.527417e-07  
Решение вышло лучше, чем в exp11, где тоже 3 коэффициента. Это значит, что SoftAdapt действительно замедляет обучение. Тем не менее, график mse_q показал резкие скачки, которых нету на графике mse_q в exp11.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_u_0.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_v_0.PNG" width="450" height="800">  
срезы:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_u_1.PNG" width="1800" height="600">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_v_1.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_2.PNG" width="1200" height="400">  
коэффициенты(видно, что они абсолютно случайно разбросаны):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_3.PNG" width="500" height="400">  
отклонение от аналитического решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_4.PNG" width="500" height="400">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp13_results_5.PNG" width="500" height="400">
