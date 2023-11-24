В этом эксперименте проводились те же опыты, что и в exp39, но при $\alpha=0$:  
<https://colab.research.google.com/drive/1SR0mp_tCfq4uHMb_Vgt5g20hG07kPQ2l?usp=sharing>  
При $\alpha=0$ начальные условия в виде солитонов действительно являются решениями и это заметно, MSE_u, MSE_v и MSE_q в соответствующих опытах заметно уменьшились.  
Более того, начальные условия $q(x,0)=(1-i)e^{-\frac{x}{2}^2}$ и $q(x,0)=e^{-\frac{x}{2}^2}$ начали задавать солитоноподобные решения.  
А вот что получилось при столкновении солитона с $k=1.4, w=1.8$ и решения для начального условия $q(x,0)=e^{-\frac{x}{2}^2}$:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp41_results.png">  

Точность: `MSE_f_u: 7.285696e-07, MSE_f_v: 7.731782e-07, First law mean/first_int(t=0): 13.90%, Second law mean/second_int(t=0): 15.10%`  
Модель именно этого опыта доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_41.pth)  
