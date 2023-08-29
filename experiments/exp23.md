В этом эксперименте был повторён exp16, но количество итераций увеличено до 300000, а learning rate затухает по закону `lr=lr*0,999` каждые 100 итераций:  
<https://colab.research.google.com/drive/1o3g-Pin4xuItTisWz7KaEkTDVDoXiyhu?usp=sharing>  
Получились следующие результаты:  
MSE_u: 1.160926e-02, MSE_v: 1.160940e-02, MSE_q: 2.385358e-06, MSE_f_u: 5.229450e-09, MSE_f_v: 4.394714e-09  
Графики можно найти в прогруженном ноутбуке: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp23.ipynb>  
