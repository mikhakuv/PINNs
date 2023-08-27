В этом эксперименте был повторён exp10, но количество итераций увеличено до 300000, а learning rate затухает по закону `lr=lr*0,999` каждые 100 итераций:  
<https://colab.research.google.com/drive/1uNns8KQZX3HoTZG6xDQNXO0FLokZwVbA?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.160524e-02, MSE_v: 1.160574e-02, MSE_q: 6.262412e-05, MSE_f_u: 2.453957e-08, MSE_f_v: 2.148443e-08  
Графики можно найти в прогруженном ноутбуке: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp19.ipynb>  
