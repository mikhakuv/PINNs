Доступная литература по операторам:  
1) **DeepONet:**: Идея от той же команды что создала PINN, есть реализация в [DeepXDE](https://deepxde.readthedocs.io/en/latest/demos/operator.html)[1]. Проверена на функциональных операторах и на простых дифференциальных уравнениях. Также есть модификация, позволяющая обучать оператор без входных данных с помощью идеи PINN - **PIDeepONet**[2].  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/operators_1.PNG">  

2) **NO:** Другая, более сложная конструкция основанная на идеи нахождения функции Грина в виде нейросети[3]. Проверена на малом числе простых дифференциальных уравнений. Есть модификации, такие как **FNO**[4] и **PINO**[5]. Большинство методов доступны в библиотеке [neuralop](https://neuraloperator.github.io/neuraloperator/dev/user_guide/quickstart.html).  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/operators_2.PNG">  

3) **PDEformer:** - сложно устроенная технология, но по сути оператор, по заявлениям решает любые двумерные задачи и делает это быстро [6].
---
[1] *Lu Lu, Pengzhan Jin, Guofei Pang, Zhongqiang Zhang & George Em Karniadakis* "Learning nonlinear operators via DeepONet based on the universal approximation theorem of operators" <https://www.researchgate.net/publication/350158010_Learning_nonlinear_operators_via_DeepONet_based_on_the_universal_approximation_theorem_of_operators/link/607e32a6907dcf667baf49fd/download>  
[2] *Somdatta Goswami, Aniruddha Bora, Yue Yu, George Em Karniadakis* "Physics-Informed Deep Neural Operator Networks" <https://arxiv.org/abs/2207.05748>  
[3] *Zongyi Li, Nikola Kovachki, Kamyar Azizzadenesheli, Burigede Liu, Kaushik Bhattacharya, Andrew Stuart, Anima Anandkumar* "Neural Operator: Graph Kernel Network for Partial Differential Equations" <https://arxiv.org/pdf/2003.03485>  
[4] *Zongyi Li and Nikola Kovachki and Kamyar Azizzadenesheli and Burigede Liu and Kaushik Bhattacharya and Andrew Stuart and Anima Anandkumar* "Fourier Neural Operator for Parametric Partial Differential Equations" <https://arxiv.org/pdf/2010.08895>  
[5] *Zongyi Li, Hongkai Zheng, Nikola Kovachki, David Jin, Haoxuan Chen, Burigede Liu, Kamyar Azizzadenesheli, Anima Anandkumar* "Physics-Informed Neural Operator for Learning Partial Differential Equations" <https://dl.acm.org/doi/pdf/10.1145/3648506>  
[6] *Zhanhong Ye, Xiang Huang, Leheng Chen, Hongsheng Liu, Zidong Wang, Bin Dong* "PDEformer: Towards a Foundation Model for One-Dimensional Partial Differential Equations" <https://arxiv.org/abs/2402.12652>  
