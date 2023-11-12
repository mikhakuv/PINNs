В данном эксперименте определялось поведение решения при начальном условии, для которого аналитическое решение неизвестно:  
<https://colab.research.google.com/drive/1IDMlBQtXf-po7LZiIRgfTfbg4btTwMgB?usp=sharing>  
Чтобы была уверенность в том, что полученное с помощью PINN решение релевантно,
сначала при тех же значениях параметров уравнения: $\alpha = 1.0, \beta = 0.0$ было найдено решение для начального условия в виде солитона с известным аналитическим решением. Точность сопадения этого решения и решения, 
полученного PINN составила:  
`MSE_u: 4.824858e-03, MSE_v: 4.821468e-03, MSE_q: 1.065443e-03 MSE_f_u: 3.165004e-07, MSE_f_v: 2.835573e-07`  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_1.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_1.png">  
Далее в качестве начального условия использовались различные функции:  

*  $q=(1-i)e^{-x^2}$  
Точность полученного решения: `MSE_f_u: 3.344643e-05, MSE_f_v: 6.551591e-06` ${\color{green}(нормальная)}$  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_2.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_2.png">

*  $q(x,0)=(5-5i)xe^{-\frac{x}{5}^2}$  
Точность полученного решения: `MSE_f_u: 4.167099e-01, MSE_f_v: 2.456522e-01` ${\color{red}(низкая)}$  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_3.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_3.png">  

*  $q(x,0)=e^{ikx}*e^{-\frac{x}{2}^2}$  
Точность полученного решения: `MSE_f_u: 2.993682e-06, MSE_f_v: 1.770187e-06` ${\color{green}(нормальная)}$  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_4.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_4.png">  

*  $q=e^{-x^2}$  
Точность полученного решения: `MSE_f_u: 2.919786e-07, MSE_f_v: 3.177147e-07` ${\color{green}(нормальная)}$  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_5.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_5.png">  

*  $q(x,0)=(1-i)e^{-\frac{x-1}{2}^2} + (-1+i)e^{-\frac{x+1}{2}^2}$  
Точность полученного решения: `MSE_f_u: 1.346334e-06, MSE_f_v: 7.387038e-07` ${\color{green}(нормальная)}$  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_6.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_6.png">  

*  $q(x,0)=e^{3ix}*e^{-\frac{x}{2}^2}$  
Точность полученного решения: `MSE_f_u: 7.661237e-05, MSE_f_v: 6.618872e-05` ${\color{red}(низкая)}$  
Графики:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_ic_7.png">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp37_results_uv_7.png">

Возможно решения для некоторых начальный условий были найдены с недостаточной точностью(это может быть исправлено в следующих экспериментах), но то, что наблюдается здесь говорит об одном: начальные условия вида $f(x)*e^{-\frac{x}{a}^2}$
не задают постоянное во времени решение.  
Ноутбук можно скачать тут: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp37.ipynb>  
