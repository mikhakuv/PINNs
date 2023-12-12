В данном эксперименте проводились опыты с прохождением солитона через различные препятствия:  
<https://colab.research.google.com/drive/1Voj78wLD-hu2eeVSeD4_pT4mP3NCrzxH?usp=sharing>(k=1.4, w=1.8)  
<https://colab.research.google.com/drive/1IH9gyxRPYXZqmihGXD1sZ3t4rs6BEola?usp=sharing>(k=1.5, w=2.2)  
Причём солитон зависит от $\alpha$:  
$$q(x,0) = \sqrt{\frac{4(k^2-w)\cdot e^{2\sqrt{k^2-w}\cdot(x-2kt-x_0)}}{(1+\frac{1}{2}e^{2\sqrt{k^2-w}\cdot(x-2kt-x_0)})^2 - \frac{1}{3}(\alpha\cdot 4(k^2-w)\cdot e^{4\sqrt{k^2-w}\cdot(x-2kt-x_0)})}}\cdot e^{i\cdot (kx-wt-\theta_0)}$$
Хорошо получились эксперименты с прохождением через другой солитон(при k=1.4, w=1.8) и низкую гауссиану(при k=1.5, w=2.2).  
К сожалению, при вычислении ErrFl и ErrSl вылезли Nan, это исправлено для успешных опытов при оформлении в [new_soliton_collision](https://github.com/mikhakuv/PINNs/blob/main/new_soliton_collision.md).  
Наиболее успешные модели: [столкновение с другим солитоном](https://github.com/mikhakuv/PINNs/blob/main/models/model_50_s.pth), [столкновение с низкой гауссианой](https://github.com/mikhakuv/PINNs/blob/main/models/model_50_s.pth)
