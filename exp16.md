В этом эксперименте был применён метод ReLoBRaLo для балансировки трёх коэффициентов, теперь lambda определяется как: `lambda = 0.9*(p*old_lambda + (1-p)*compare_to_zero) + 0.1*compare_to_prev`.  
где p - случайная величина от 0 до 1, `old_lambda` - lambda на предыдущем шаге, `compare_to_zero` - насколько уменьшился loss в сравнении с началом обучения, `compare_to_prev` - насколько уменьшился 
loss в сравнении с предыдущим шагом:  
<https://colab.research.google.com/drive/1R3_7om2ABqcPVsqz5R0WM7tRRKCRODsT?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.160701e-02, MSE_v: 1.160617e-02, MSE_q: 4.154746e-05, MSE_f_u: 1.297050e-08, MSE_f_v: 1.175581e-08  
Результаты гораздо лучше, чем в экспериментах с SoftAdapt, но всё ещё хуже, чем в эксперименте без коэффициентов. Модуль решения перестал затухать и отставать от аналитического.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_u.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_v.PNG" width="450" height="800">  
в срезе:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_q.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_iter.PNG" width="1200" height="400">  
коэффициенты(красный - lambda_f, розовый - lambda_b, оранжевый - lambda_in):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_lambda.PNG" width="500" height="400">  
зависимость качества выполнения условий уравнения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_mean.PNG" width="1000" height="400">  
зависимость качества выполнения законов сохранения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp16_results_laws.PNG" width="1000" height="800">
