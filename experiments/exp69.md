Рассматривается уравнение 6-го порядка с солитонным начальным условием:  
$$iq_t + ia_1q_x + a_2q_{xx} + ia_3q_{3x} + a_4q_{4x} + ia_5q_{5x} + a_6q_{6x} + q(b_1|q|^2 +b_2|q|^4 + b_3|q|^6)=0$$  
И следующими коэффициентами:  
$$a_1 = 1,\ a_2 = -1,\ a_3 = -2.8,\ a_4 = -0.3,\ a_5 = -0.6,\ a_6 = 0.1,\ b_1 = 6,\ b_2 = -1.525,\ b_3 = 0.113$$  

Были произведены дополнительные эксперименты с численной схемой Кранка-Николсона. Оказалось, что схема является более нестабильной чем считалось ранее: точность решения меняется не только при изменении области решения, но и при изменении начального условия. 
При $x_0=4$ решение выглядит так:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp68_chart_1.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp68_chart_2.png" width="1000" height="500">  

Но если немного сдвинуть начальное условие взяв $x_0=3$, то солитон начинает распыляться:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp69_chart_1.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp69_chart_2.png" width="1000" height="500">  

Если же сдвинуть начальное условие в другую сторону взяв $x_0=5$, то схема перестаёт быть стабильной:  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp69_chart_3.png" width="1000" height="500">  

<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/exp69_chart_4.png" width="1000" height="500">  
