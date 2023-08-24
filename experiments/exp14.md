В этом экспеименте число итераций при обучении было увеличено до 130000, а также модифицирован метод SoftAdapt для трёх коэффициентов. Теперь lambda зависит не только 
от текущих показаний сети, но и от предыдущих lambda: `lambda=0.3*old_lambda+0.7*new_lambda`:  
<https://colab.research.google.com/drive/15je5COdPqAkcOam0U0hHfCtBMMpp927R?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.158619e-02, MSE_v: 1.158483e-02, MSE_q: 3.102907e-04, MSE_f_u: 5.798984e-08, MSE_f_v: 5.517501e-08  
Решение вышло лучше, чем в других опытах с тремя коэффициентами, но всё ещё хуже, чем без балансировки весов.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_u.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_v.PNG" width="450" height="800">  
в срезе:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_q.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_iter.PNG" width="1200" height="400">  
коэффициенты(красный - lambda_f, розовый - lambda_b, оранжевый - lambda_in):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_lambda.PNG" width="500" height="400">  
зависимость качества выполнения условий уравнения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_mean.PNG" width="1000" height="400">  
зависимость качества выполнения законов сохранения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp14_results_laws.PNG" width="1000" height="800">
