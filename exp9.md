В этом эксперименте выбраны другие гиперпараметры, архитектура и использовано два оптимизатора:  
<https://colab.research.google.com/drive/1JkWOaK-RR_Q0ptb6nVSplzYbkNpDenoe?usp=sharing>  
Теперь z0=-55; -85<x<85 0<t<50; архитектура: [2,100,100,100,100,2]; каждые 10 итераций данные для обучения условиям уравнения перегенерируются: оптимизация происходит в два этапа:
сначала 100000 итераций adam с экспоненциальным уменьшением learning rate(lr=0.997*lr каждые 100 итераций) а потом lbfgs.  
Получились хорошие результаты:  
MSE_u: 1.160879e-02, MSE_v: 1.160933e-02, MSE_q: 1.935086e-05, MSE_f_u: 1.143437e-08, MSE_f_v: 9.929643e-09.   
Визуально решение похоже на аналитическое. Ниже приведены графики и статистика.  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_u_0.PNG" width="450" height="800">
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_v_0.PNG" width="450" height="800">  
срезы:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_u_1.PNG" width="1800" height="600">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_v_1.PNG" width="1800" height="600">  
кривая обучения(на графике не loss, а средний квадрат разности модулей MSE_q):  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_2.PNG" width="600" height="400">  
отклонение от аналитического решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_3.PNG" width="600" height="400">  
<img src="https://github.com/mikhakuv/PINNs/blob/main/exp9_results_4.PNG" width="600" height="400">  
