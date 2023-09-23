В этом эксперименте были уменьшены скорости изменения вдоль x обоих солитонов(k_arr=[1.8,-1.6]), а начальные точки разнесены подальше(x0_arr=[-5.0,20.0]). Также была увеличена рассматриваемая область(-25<x<45, 0<t<10). При этом alpha=0.1:  
<https://colab.research.google.com/drive/1eiCCVgpThBgtmjM3zcEaPy_qpCUoUGCf?usp=sharing>  
Получились следующие результаты:  
MSE_f_u: 2.763693e-06, MSE_f_v: 2.550728e-06, MSE_fl: 3.750363e-03, MSE_sl: 7.684185e-03  
Предсказанное решение:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp29_results_uv.png">  
Ещё графики можно найти в прогруженном ноутбуке: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp29.ipynb>  
Модель можно скачать по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_29.pth) и исследовать в [блокноте](https://colab.research.google.com/drive/1PGeRt-huLODfLSD-_PZaeBugljdYZdaQ?usp=sharing)
