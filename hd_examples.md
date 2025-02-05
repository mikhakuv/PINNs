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

2. **(2+1)D Klein-Gordon**

$$
\begin{aligned}
&\begin{aligned}
& \partial_{t t} u-\Delta u+u^2=f,\ &&x \in [-1,1]^2, t \in [0,10], \\
& u(x, 0)=x_1+x_2,\ &&x \in [-1,1]^2, \\
& u(x, t)=u_{\mathrm{bc}}(x),\ &&x \in \partial [-1,1]^2, t \in [0,10]
\end{aligned}\\
\end{aligned}
$$

solution: $u = (x_1+x_2)\text{cos}(2t) + x_1x_2\text{sin}(2t)$  
methods: PINN, SPINN  
result: SPINN is better  

3. **(2+1)D  Diffusion**

$$\begin{array}{lr}
\partial_t u=\alpha\left(\|\nabla u\|^2+u \Delta u\right), & x \in [-1,1]^2, t \in [0,1], \\
u(x, 0)=u_{\mathrm{ic}}(x), & x \in [-1,1]^2, \\
u(x, t)=0, & x \in \partial [-1,1]^2, t \in [0,1], \\
\end{array}
$$
$$
\begin{aligned}
\text{where}\ u_{\text {ic }}(x, y)=0.25 \exp [-10 {(x-0.2)^2+(y-0.3)^2}] & +0.4 \exp [-15 {(x+0.1)^2+(y+0.5)^2}] \\
& +0.3 \exp [-20{(x+0.5)^2+y^2}]
\end{aligned}
$$

solution: no exact solution  
methods: PINN, SPINN  
result: PINN is almost equal to SPINN

4. **(2+1)D Flow Mixing Problem**

$$\frac{\partial u(t, x, y)}{\partial t}+a \frac{\partial u(t, x, y)}{\partial x}+b \frac{\partial u(t, x, y)}{\partial y}=0, \quad t \in[0,4], x \in[-4,4], y \in[-4,4]$$
$$
\begin{aligned}
\text{where}& a(x, y)=-\frac{v_t}{v_{t, \max }} \frac{y}{r} \\
& b(x, y)=\frac{v_t}{v_{t, \max }} \frac{x}{r} \\
& v_t=\text{sech}^2(r) \text{tanh} (r) \\
& r=\sqrt{x^2+y^2} \\
& v_{t, \max }=0.385
\end{aligned}
$$

solution: $u(t, x, y)=-\tanh \left(\frac{y}{2} \cos (\omega t)-\frac{x}{2} \sin (\omega t)\right),\ \text{where}\ w=\frac{1}{r}\frac{v_t}{v_{t, \max}}$  
methods: PINN, SPINN  
result: SPINN is better  

5. **(2+1)D Navier-Stokes**

$$
\begin{array}{lr}
\partial_t \omega+u \cdot \nabla \omega=\nu \Delta \omega, & x \in [0,2\pi]^2, t \in [0,1], \\
\nabla \cdot u=0, & x \in [0,2\pi]^2, t \in [0,1], \\
\omega(x, 0)=\omega_0(x), & x \in [0,2\pi]^2,\\
\text{where}\ \omega = \nabla\times u
\end{array}
$$

solution: no exact solution  
methods: PINN, causal PINN, SPINN  
result: SPINN is way better than others

6. **(3+1)D Navier-Stokes**

$$
\begin{array}{lr}
\partial_t \omega+(u \cdot \nabla) \omega=(\omega \cdot \nabla) u+\nu \Delta \omega+F, & x \in [0,2\pi]^3, t \in [0,5], \\
\nabla \cdot u=0, & x \in [0,2\pi]^3, t \in [0,5] \\
\omega(x, 0)=\omega_0(x), & x \in [0,2\pi]^3
\end{array}
$$

$$
\text{where}
\begin{aligned}
& F_x=-6 e^{-18 \nu t} \sin (4 y) \sin (2 z), \\
& F_y=-6 e^{-18 \nu t} \sin (4 x) \sin (2 z), \\
& F_z=6 e^{-18 \nu t} \sin (4 x) \sin (4 y) .
\end{aligned}
$$

solution:

$$
\begin{aligned}
u_x & =2 e^{-9 \nu t} \cos (2 x) \sin (2 y) \sin (z) \\
u_y & =-e^{-9 \nu t} \sin (2 x) \cos (2 y) \sin (z) \\
u_z & =-2 e^{-9 \nu t} \sin (2 x) \sin (2 y) \cos (z) \\
\omega_x & =-3 e^{-9 \nu t} \sin (2 x) \cos (2 y) \cos (z) \\
\omega_y & =6 e^{-9 \nu t} \cos (2 x) \sin (2 y) \cos (z) \\
\omega_z & =-6 e^{-9 \nu t} \cos (2 x) \cos (2 y) \sin (z), \\
\text{and}\ \nu = 0.05
\end{aligned}
$$

methods: SPINN  
result: SPINN achieves good result in less than 30 minutes

7. **(3+1)D Klein-Gordon**

$$
\begin{aligned}
&\begin{aligned}
& \partial_{t t} u-\Delta u+u^2=f,\ &&x \in [-1,1]^3, t \in [0,10], \\
& u(x, 0)=x_1+x_2,\ &&x \in [-1,1]^3, \\
& u(x, t)=u_{\mathrm{bc}}(x),\ &&x \in \partial [-1,1]^3, t \in [0,10]
\end{aligned}\\
\end{aligned}
$$

solution: $u = (x_1+x_2+x_3)\text{cos}(t) + x_1x_2x_3\text{sin}(t)$  
methods: PINN, SPINN  
result: SPINN is better  

8. **(5+1)D Diffusion**

$$\frac{\partial u(t, x)}{\partial t}=\Delta u(t, x), \quad x \in[-1,1]^5, t \in[0,1]$$

solution: $u = ||x||^2 + 10t$  
methods: SPINN  
result: SPINN achieves good results within 2 minutes
