В этом эксперименте были повторены опыты exp40, но при $\alpha=0$:  
<https://colab.research.google.com/drive/1lmq_xMlP5JbYjjT8ILzMgD9nGu5duKoh?usp=sharing>  
Заметно, что решения PINN для солитонов **очень** похожи на аналитические, в частности при $k=0.0, w=-0.1$ точность получается самая низкая из когда либо наблюдавшихся:  
`MSE_u: 2.186131e-08, MSE_v: 2.736096e-08, MSE_q: 1.901688e-08, MSE_f_u: 6.445730e-10, MSE_f_v: 4.273462e-10, First law mean/first_int(t=0): 0.06%, Second law mean: 5.583830e-06 (second_int(t=0)~0)`  
При столкновении двух солитонов с $k=1.4, w=1.8$ и  $k=0.0, w=-0.1$:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp42_results_1.png">  

Точность: `MSE_f_u: 7.450000e-07, MSE_f_v: 5.826565e-07, First law mean/first_int(t=0): 3.46%, Second law mean/second_int(t=0): 8.03%`  
Также хорошо получился опыт с прохождением солитона с $k=1.4, w=1.8$ через решение для начального условия $q(x,0)=e^{-\frac{x}{2}^2}$:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp42_results_2.png">  

Точность: `MSE_f_u: 8.026456e-07, MSE_f_v: 8.103217e-07, First law mean/first_int(t=0): 15.75%, Second law mean/second_int(t=0): 17.81%`
