# Теория  
В данной работе применяется метод PINN для решения нелинейного дифференциального уравнения второго порядка, полученный результат сравнивается с аналитическим решением. 
### Уравнение
Рассматривается обобщённое уравнение Шрёдингера в нелинейной среде (как ещё перевести generalized Schrodinger equation with a dual-power law nonlinear medium?):
$$iq_t + aq_{xx} + \alpha|q|^{2n}q - \beta|q|^{4n}q = 0$$
В [[1]](#обзор-литературы) найдено аналитическое решение такого уравнения:
$$q(x, t)=\left[\frac{4 \mu \mathrm{e}^{\left(x-2 a k t-z_0\right) \sqrt{\mu}}}{1+2 \lambda \mathrm{e}^{\left(x-2 a k t-z_0\right) \sqrt{\mu}}+\left(\lambda^2-4 \mu \nu\right) \mathrm{e}^{2\left(x-2 a k t-z_0\right) \sqrt{\mu}}}\right]^{\frac{1}{2 n}} \mathrm{e}^{i\left(k x-\omega t+\theta_0\right)},$$
$$где\quad \lambda=\frac{4 \alpha n^2}{a(1+n)},\quad \nu=\frac{4 \beta n^2}{a(1+2 n)},\quad \mu=\frac{4 n^2(\omega-a k^2)}{a} .$$
рассматривается  случай $\quad n = 1,\quad a = 1,\quad \alpha = 1,\quad \beta = 1,\quad$ при котором $\quad k = 1,\quad z_0 = 0,\quad \theta_0 = 0,\quad w = \frac{9}{8}.$
### Метод

# Результаты  

# Обзор Литературы  
1. вроде ещё неопубликованная статья *Nikolay A. Kudryashov, Daniil R. Nifontov* "Application of machine learning to construct solutions to non-integrable partial differential equations"
