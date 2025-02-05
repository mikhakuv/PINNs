Examples of higher($\ge3$) dimensions equations, considered in literature on PINN:  
## [Can Physics-Informed Neural Networks beat the Finite Element Method?](https://arxiv.org/pdf/2302.04107)  
1. **3D Poisson**:
   
$$\begin{aligned}
\Delta u(x, y, z) & =-3 \pi^2 \sin (\pi x) \sin (\pi y) \sin (\pi z) \quad(x, y, z) \in(0,1)^3 \\
u(x, y, z) & =0 \quad(x, y, z) \in \partial(0,1)^3
\end{aligned}$$  

solution: $u = \text{sin}(\pi x)\text{sin}(\pi y)\text{sin}(\pi z)$  
methods: PINN, FEM  
result: FEM is better  

2. **(2+1)D Schrödinger**:
   
$$
\begin{array}{rlrl}
\mathrm{i} \frac{\partial h(t, x, y)}{\partial t} & =-0.5 \Delta h(t, x, y)-|h(t, x, y)|^2 h(t, x, y), & & x, y \in[-5,5], t \in[0, \pi / 2] \\
h(0, x, y) & =\text{sech}(x)+0.5 \text{sech}(y-2)+0.5 \text{sech}(y+2), & & x, y \in[-5,5] \\
h(t,-5, y) & =h(t, 5, y), & & t \in[0, \pi / 2], y \in[-5,5] \\
h(t, x,-5) & =h(t, x, 5), & & t \in[0, \pi / 2], x \in[-5,5] \\
\frac{\partial h(t,-5, y)}{\partial x} & =\frac{\partial h(t, 5, y)}{\partial x}, & & t \in[0, \pi / 2], y \in[-5,5] \\
\frac{\partial h(t, x,-5)}{\partial y} & =\frac{\partial h(t, x, 5)}{\partial y} & & t \in[0, \pi / 2], x \in[-5,5] .
\end{array}
$$

solution: no exact solution  
methods: PINN, FEM  
result: FEM is better  

## [Separable Physics-Informed Neural Networks](https://arxiv.org/pdf/2306.15969)  
1. **3D Helmholtz**:
   
$$\begin{array}{lr}
\Delta u+k^2 u=-((a_1 \pi)^2 + (a_2 \pi)^2 + (a_3 \pi)^2 - k^2)u, & x \in [-1,1]^3 \\
u(x)=0, & x \in \partial [-1,1]^3
\end{array}$$ 

solution: $u = \text{sin}(a_1 \pi x_1)\text{sin}(a_2 \pi x_2)\text{sin}(a_3 \pi x_3)$  
methods: PINN, SPINN  
result: SPINN is better  
