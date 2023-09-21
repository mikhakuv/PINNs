В данном эксперименте `alpha` резко повышается от 0 до 0.1 при `iter = 150000`. При этом данные в процессе обучения записываются и в результате формируются в гифку:  
<https://colab.research.google.com/drive/1D6zZZfr9cTTQOHJ1Or41Ha3RIb9vfxNK?usp=sharing>  
Получились следующие результаты:  
MSE_f_u: 9.153842e-05, MSE_f_v: 9.572584e-05, MSE_fl: 2.154382e-03, MSE_sl: 2.929731e-02  
Процесс обучения(розовый слайд - момент изменения alpha):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp27_train_process.gif">  
Графики можно найти в прогруженном ноутбуке: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp27.ipynb>  
Модель можно скачать по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_27.pth) и исследовать в [блокноте](https://colab.research.google.com/drive/1PGeRt-huLODfLSD-_PZaeBugljdYZdaQ?usp=sharing)
