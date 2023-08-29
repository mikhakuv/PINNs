В этом эксперименте при обучении учитывались законы сохранения. На старте обучения loss вычислялся как обычно: `loss=loss_uv+loss_f`, но при `iter>50000` в loss добавлялась точность соблюдения законов сохранения: `loss=loss_uv+loss_f+loss+fl+loss+sl.:  
<https://colab.research.google.com/drive/1pNn2KMNgQhQ8ECku00b3IPGH342zkrP8?usp=sharing>  
Получились следующие результаты:  
MSE_u: 9.317195e-03, MSE_v: 8.925392e-03, MSE_q: 1.465884e-02, MSE_f_u: 3.663063e-05, MSE_f_v: 3.532440e-05  
Результаты плохие, это видно и по графикам и по MSE_q. Важно отметить, что не помогло ни постепенное расширение области, ни балансировка коэффициентов. И этому есть объяснение: на графике loss(iter) видно,
что после включения loss_fl и loss_sl в loss(iter=50000) оптимизатор способен снижать loss и тем самым решать задачу оптимизации. Но в то же время после iter=50000 mse_q не снижается, а только растёт.
Это значит, что задача снижения loss_fl и loss_sl не совпадает с задачей снижения mse_q. То есть точность соблюдения законов сохранения вообще не помогает соответствовать исходному уравнению и
нет смысла её учитывать при обучении.  
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
