В этом эксперименте проводилось столкновение солитона с решением для начального условия в виде гауссианы:  
<https://colab.research.google.com/drive/1F49spr8G_Q1z05kgfdrEQTYUtEM2KLO-?usp=sharing>  
Опытным путём получено, что гауссиана должна быть широкой, чтобы быстро не затухнуть.  
Планировалось наблюдать полное сохранение солитона, но вместо этого во всех опытах(для $\alpha=0$, $\alpha=1$ и для гауссиан разных высот) получился другой эффект:
гауссиана имеющая только действительную часть после столкновения с солитоном обретает комплексную часть. При этом её модуль чётко сохраняется.  
Самый удачный эксперимент: солитон с $k=1.4, w=1.8$ и решение для начального условия $q(x,0)=\frac{1}{5}e^{-\frac{x}{10}^2}$ при $\alpha=1$  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp45_results_ic.png">  

Точность: `MSE_f_u: 6.772910e-08, MSE_f_v: 6.545782e-08, First law mean/first_int(t=0): 1.17%, Second law mean/second_int(t=0): 1.89%`  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp45_results_uv.png">  
Модель именно этого опыта доступна по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_45_a1_1.pth)  
Также есть другой успешный опыт с в 2 раза меньшей амплитудой. Его модель можно найти по [ссылке](https://github.com/mikhakuv/PINNs/blob/main/models/model_45_a1_2.pth)  
