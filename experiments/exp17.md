В этом эксперименте в loss были добавлены loss_fl и loss_sl, отвечающие за соответствие нейросети законам сохранения(первому и второму), теперь loss имеет вид: `loss = loss_uv + loss_f + loss_fl + loss_sl`. Для увеличения скорости вычислений рассчёт loss_fl и loss_sl производился в тензорном виде:  
 
Получились следующие результаты:  
 

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp17_results_u.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp17_results_v.PNG" width="450" height="800">  
в срезе:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp17_results_q.PNG" width="1800" height="600">  
кривые обучения(loss - минимизируемая функция, mse_q - точность модели):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp17_results_iter.PNG" width="1200" height="400">  
зависимость качества выполнения условий уравнения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp17_results_mean.PNG" width="1000" height="400">  
зависимость качества выполнения законов сохранения от t(чем ближе к 0, тем лучше):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp17_results_laws.PNG" width="1000" height="800">
