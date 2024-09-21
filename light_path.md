В статье [[1]](https://www.nature.com/articles/s41598-023-49977-3) предложены новые идеи для применения PINN, в частности нахождение кратчайшего пути света в среде с переменным коэффициентом преломления $n(x,y)$. Для этого используется принцип Ферма, 
из которого можно получить задачу по минимизации параметра $T$ в уравнении:  
$$\left(\frac{1}{T}\cdot\frac{dx}{dt}\right)^2 + \left(\frac{1}{T}\cdot\frac{dy}{dt}\right)^2 - \left(\frac{c}{n(x,y)}\right)^2 = 0$$  
$x(t)$ и $y(t)$ неизвестны и находятся в виде PINN. Пример решения:  
<img src="https://github.com/mikhakuv/PINNs/blob/main/pictures/light_path_chart_1.png">  

В качестве развития этой идеи можно предложить определение $n(x,y)$ по уже заданной кривой или решение задач с учётом зависимости коэффициента преломления от длины волны $\lambda$ или температуры $T$.

[1]: **Jaemin Seo** Solving real‑world optimization tasks using physics‑informed neural computing
