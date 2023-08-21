В этом эксперименте была попытка учесть естественные различия в порядках loss_uv и loss_f. Для этого в loss были добавлены дополнительные коэффициенты и теперь он имеет вид
`loss = 0.1*lambda_uv*loss_uv + 20*lambda_f*loss_f`:  
<https://colab.research.google.com/drive/1m4EOcwqjFxXoYMpspEAS9k2Q-6nHvx2r?usp=sharing>  
Получились следующие результаты:  
MSE_u: 9.631939e-03, MSE_v: 9.607878e-03, MSE_q: 2.056486e-03, MSE_f_u: 1.640185e-07, MSE_f_v: 1.558665e-07  
Как визуально, так и по MSE_q видно, что результат хуже, чем в других экспериментах с двумя коэффициентами. Возможно оптимизатор и нашёл решение дифференциального уравнения, но слабо учёл граничные и начальные условия.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_u.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_v.PNG" width="450" height="800">  
в срезе:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_q.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_iter.PNG" width="1200" height="400">  
коэффициенты(красный - lambda_f, оранжевый - lambda_uv):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_lambda.PNG" width="500" height="400">  
зависимость качества выполнения условий уравнения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_mean.PNG" width="1000" height="400">  
зависимость качества выполнения законов сохранения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp15_results_laws.PNG" width="1000" height="800">
