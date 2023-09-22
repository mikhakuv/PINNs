В этом эксперименте были уменьшены скорости изменения вдоль x обоих солитонов(k_arr=[1.8,-1.6]), а начальные точки разнесены подальше(x0_arr=[-5.0,20.0]). Также была увеличена рассматриваемая область(-25<x<45, 0<t<10). При этом alpha=0.1:  
<https://colab.research.google.com/drive/1eiCCVgpThBgtmjM3zcEaPy_qpCUoUGCf?usp=sharing>  
Получились следующие результаты:  
MSE_f_u: 5.098589e-06, MSE_f_v: 6.323226e-06, MSE_fl: 8.194931e-02, MSE_sl: 2.184145e-01  
Предсказанное решение:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp29_results_uv.PNG">  
Модуль решения в срезе:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp29_results_q_abs.PNG">  
Ещё графики можно найти в прогруженном ноутбуке: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp29.ipynb>  
