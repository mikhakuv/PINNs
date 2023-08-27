В этом эксперименте был повторён exp11, но количество итераций увеличено до 300000, а learning rate затухает по закону `lr=lr*0,999` каждые 100 итераций:  
<https://colab.research.google.com/drive/1d0AQ7IK0jOjpCnxJNpLL4G3qkw4PT1HH?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.155027e-02, MSE_v: 1.154920e-02, MSE_q: 2.724783e-04, MSE_f_u: 7.747857e-08, MSE_f_v: 7.712322e-08  
Графики можно найти в прогруженном ноутбуке: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp20.ipynb>  
