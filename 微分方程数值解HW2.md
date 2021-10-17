## <center>微分方程数值解HW2</center>

<center>苗泽亮 2200502177</center>

------



1. 证明下属格式是无条件稳定的.
$$
  y_{n+1}= y_n+h f(\frac{x_n+x_{n+1}}{2},\frac{y_n+y_{n+1}}
  {2})
$$
  证明：应用$y'=\lambda y$可得迭代格式为：

  ​			
$$
  y_{i+1}=y_i+hy'=y_i+h\lambda (\frac{x_n+x_{n+1}}{2},\frac{y_n+y_{n+1}}
  {2})=y_i+\frac{h}{2} \lambda (y_i+y_{i+1})
$$
  整理得：
$$
  （1-\frac{h\lambda}{2}）y_{i+1}=（1+\frac{h\lambda}{2}）y_{i}
$$
  即有：
$$
  y_{i+1}=\frac{\frac{1+h \lambda}{2}y_i}{1-\frac{h \lambda}{2}}=1+\frac{2h\lambda}{2-h \lambda}y_i
$$
  另第i步舍入误差为$\delta_i$，于是有$\tilde{y}-y=\delta_i$
$$
  \delta_{i+1}=\tilde{y_{i+1}}-y_{i+1}=1+\frac{2h\lambda}{2-h \lambda}(\tilde {y_i}-y_i)=(1+\frac{2h\lambda}{2-h \lambda}){\delta_i}=（1+\frac{2}{\frac{2}{h\lambda} -1}）\delta_i
$$
  由于$\frac{2}{h \lambda}$<0,因此$\frac{2}{\frac{2}{h\lambda} -1}$<0,于是$|\delta_{i+1}|<|\delta_i|$,因此该格式无条件稳定证得。

  

2. 利用Taylor 展开构造求下面问题近似解的2阶精度的数值格式：
$$
  y'=1+(t-y)^2, 2\leq t\leq 3, y(2)=1,h=0.5
$$
  解：
$$
  构造\phi_(x,y,h)=f(x,y)+\frac{h}{2}f^{(1)}(x,y)=f(x,y)+\frac{h}{2}(\frac{\partial f}{\partial t}+f\frac{\partial f}{\partial y})=1+(t-y)^2+\frac{h}{2}(2(t-y)+1+(t-y)^2·(-2)(t-y)
  =1+(t-y)^2+\frac{h}{2}(-2(t-y)^3)=1+(t-y)^2-h(t-y)^3
$$
  代入h=0.5,于是$\phi_(x,y,h)=1+(t-y)^2-\frac{(t-y)^3}{2}$

因此迭代格式为：$y_{n+1}=y_n+h(1+(t-y_n)^2-\frac{(t-y_n)^3}{2})=y_n+\frac{1}{2}(1+(t-y_n)^2-\frac{(t-y_n)^3}{2})$

