# SMO Algorithm

## Dual problem

We have a dual problem, for $\forall i=1...N$

$$
\begin{align}
maximize\quad &\sum^N_{i=1}\alpha_i - \frac{1}{2}\sum^N_{i=1}\sum^N_{j=1}\alpha_i\alpha_jy_iy_j\varphi(x_i)^T\varphi(x_j)\quad\quad\\
(maximize\quad &\sum^N_{i=1}\alpha_i - \frac{1}{2}\sum^N_{i=1}\sum^N_{j=1}\alpha_i\alpha_jy_iy_jK(x_i,x_j))\\
s.t.\quad &0\le \alpha_i \le c\\
&\sum^N_{i=1}\alpha_iy_i = 0
\end{align}\\
$$



let $\displaystyle\mathcal{L}(\alpha_i)=\sum^N_{i=1}\alpha_i-\frac{1}{2}\sum^N_{i=1}\sum^N_{j=1}\alpha_i\alpha_jy_iy_jK(x_i,x_j)$

$\textcircled{1}$ Let $\alpha_3, \alpha_4, ..., \alpha_N$ are constant, then

$$
\begin{align*}
\mathcal{L}(\alpha_1, \alpha_2) = \alpha_1 + \alpha_2 + \sum^N_{i=3}\alpha_i - \frac{1}{2}\Big[&\alpha_1^2y_1^2K(x_1, x_1)+\alpha_1\alpha_2y_1y_2K(x_1,x_2)+\alpha_1\sum^N_{j=3}\alpha_jy_1y_jK(x_1,x_j)\\
+&\alpha_2\alpha_1y_2y_1K(x_2,x_1)+\alpha_2^2y_1^2K(x_2,y_2)+\alpha_2\sum^N_{j=3}\alpha_jy_2y_jK(x_2,x_j)\\
+&\alpha_1\sum^N_{i=3}\alpha_iy_iy_1K(x_i,x_1)+\alpha_2\sum^N_{i=3}\alpha_iy_iy_2K(x_i,x_22)+\sum^N_{i=3}\sum^N_{j=3}\alpha_i\alpha_jy_iy_jK(x_i,x_j) \Big]\\
=(\alpha_1+\alpha_2)+\sum^N_{i=3}\alpha_i-\frac{1}{2}\Big[&\alpha_1^2y_1^2K(x_1,x_1)+2\alpha_1\alpha_2y_1y_2K(x_1,x_2)+2\alpha_1y_1\sum^N_{i=3}\alpha_iy_iK(x_i,x_1)\\
+&\alpha_2^2y_1^2K(x_2,x_2)+2\alpha_2y_2\sum^N_{i=3}\alpha_iy_iK(x_i,x_2)+\sum^N_{i=3}\sum^N_{j=3}\alpha_i\alpha_jy_iy_jK(x_i,x_j)\Big]\\
=\Big[\alpha_1 - \frac{1}{2}\alpha_1^2y_1^2K(x_1,x_1)-&\alpha_1y_1\sum^N_{i=3}\alpha_iy_iK(x_i,x_1) \Big]\\
-\alpha_1\alpha_2y_1y_2K(x_1,x_2)\;\;\;\;\;\\
+\Big[\alpha_2-\frac{1}{2}\alpha_2^2y_2^2K(x_2,x_2)-&\alpha_2y_2\sum^N_{i=3}\alpha_iy_iK(x_i,x_2) \Big]\\
+\Big[\sum^N_{i=3}\alpha_i - \frac{1}{2}\sum^N_{i=3}\sum^N_{j=3}\alpha_i\alpha_j&y_iy_jK(x_i,x_j) \Big]
\end{align*}
$$

To obtain $\mathcal{L}(\alpha_1, \alpha_2)$ $\iff$

$$
\begin{cases}\displaystyle\frac{\partial\mathcal{L}}{\partial\alpha_1}=0\\ 
\\
\displaystyle\frac{\partial\mathcal{L}}{\partial\alpha_2}=0\end{cases}
$$



As $\sum^N_{i=1}\alpha_iy_i=0$, i.e. $\alpha_1y_1 + \alpha_2y_2 +\sum^N_{i=3}\alpha_iy_i=0$, where $\sum^N_{i=3}\alpha_iy_i=C$ is a constant, so that

$$
\iff \alpha_1y_1 + \alpha_2y_2 = C\\
\iff \alpha_1 = y_1(C-\alpha_2y_2)

$$

(Note that $y_i^2=1$ for $\forall i=1..N$)

So the function $\mathcal{L}(\alpha_1, \alpha_2)$ becomes:

$$
\begin{align*}
\mathcal{L}(\alpha_1, \alpha_2) &= \mathcal{L}(\alpha_2)\\
&=y_1(C-\alpha_2y_2) - \frac{1}{2}(C-\alpha_2y_2)^2-(C-\alpha_2y_2)\sum^N_{i=3}\alpha_iy_iK_{i1}-\alpha_2(C-\alpha_2y_2)y_2K_{12}\\
&+\Big[\alpha_2-\frac{1}{2}\alpha_2^2-\alpha_2y_2\sum^N_{i=3}\alpha_iy_iK_{i2}\Big] + C'\\
&=y_1(C-\alpha_2y_2)+\alpha_2 - \frac{1}{2}\Big[(C-\alpha_2y_2)^2K_{11}+2(C-\alpha_2y_2)\alpha_2y_2K_{12}\\
&+\alpha^2_2K_{22}+2(C-\alpha_2y_2)\sum^N_{i=3}\alpha_iy_iK_{i1} +2\alpha_2y_2\sum^N_{i=3}\alpha_iy_iK_{i2}+C'\Big]\\
&=(1-y_1y_2+Cy_2K_{11}-Cy_2K_{12}+y_2\sum^N_{i=3}\alpha_iy_iK_{i2}-y_2\sum^N_{i=3}\alpha_iy_iK_{i2})\\
&+\alpha_2(-K_{11}+2K_{12}-K_{22})=0\\
\\
\alpha_2(K_{11}-2K_{12}+K_{22})&=1-y_1y_2+y_2K_{11}\sum^N_{i=3}\alpha_iy_i - y_2K_{12}\sum^N_{i=3}\alpha_iy_i+y_2\sum^N_{i=3}\alpha_iy_iK_{i1}-y_2\sum^N_{i=3}\alpha_iy_iK_{i2}\\
&=y_2(y_2-y_1+K_{11}C-K_{12}C+\sum^N_{i=3}\alpha_iy_iK_{i1}-\sum^N_{i=3}\alpha_iy_iK_{12})

\end{align*}
$$

Because $\alpha_1y_1+\alpha_2y_2=C$, or say $\alpha_1^{old}y_1+\alpha_2^{old}y_2=C$, i.e. $\alpha_1^oy_1+\alpha_2^oy_2=C$

so the $\alpha_2$ is updated with the equation above as:

$$
\alpha^{new}=\alpha^n=\frac{1}{K_{11}-2K_{12}+K_{22}}y_2(y_2-y_1+K_{11}+K(\alpha^o_1y_1 + \alpha^o_2y_2)-K_{12}(\alpha^o_1y_1+\alpha^o_2y_2)+\sum^N_{i=3}\alpha_iy_iK_{i1}-\sum^N_{i=3}\alpha_iy_iK_{i2})
$$

Remember that in the prime problem we have

$$
L(w) = \sum^N_{i=1}\alpha_i -\frac{1}{2}\sum^N_{i=1}\sum^N_{j=1}\alpha_i\alpha_jy_iy_jK(x_i,x_j)\\
where\quad \frac{\partial L}{\partial w}=0 \Rightarrow w=\sum^N_{i=1}\alpha_iy_ix_i
$$

so the hyperplane

$$
\begin{align*}
f(x)&=w^Tx+b\\
&=\sum^N_{i=1}\alpha_iy_ix_i^Tx + b\\
&= \alpha_1y_1x_1^Tx + \alpha_2y_2x^T_2x + \sum^N_{i=3}\alpha_iy_ix^T_ix + b
\end{align*}
$$

then for $f(x_1)$ we have

$$
\begin{align*}
f(x_1)&=\alpha_1y_1x^T_1x_1 + \alpha_2y_2x_2^Tx_1 + \sum^N_{i=3}\alpha_iy_ix^T_ix_1 +b \\
&=\alpha_1y_1K(x_1,x_1)\alpha_2y_2K(x_2,x_1)+\sum^N_{i=3}\alpha_iy_iK(x_i,x_1)+b\\
f(x_1)&=\alpha_1y_1K_{11}+\alpha_2y_2K_{21}+\sum^N_{i=3}\alpha_iy_iK_{i1}+b
\end{align*}
$$

simillarly, we can have

$$
f(x_2)=\alpha_1y_1K_{12}+\alpha_2y_2K_{22}+\sum^N_{i=3}\alpha_iy_iK_{i2} + b
$$

then from $f(x_1)-f(x_2)$ we can get

$$
\sum^N_{i=3}\alpha_iK_{i1}-\sum^N_{i=3}\alpha_iy_iK_{i2}= f(x_1)-f(x_2)-\alpha_1y_1K_{11}-\alpha_2y_2K_{21}+\alpha_1y_1K_{12}+\alpha_2y_2K_{22}
$$

take this into $\alpha_2^n$, then

$$
\begin{align*}
\alpha^n_2=\frac{1}{K_{11}-2K_{12}+K_{22}}y_2(&y_2-y_1 + \alpha^o_1y_1K_{11} + \alpha^o_2y_2K_{11}-\alpha^o_1y_1K_{12} - \alpha^o_2y_2K_{12}\\
&f(x_1)-f(x_2)-\alpha_1^oy_1K_{11}-\alpha_2^oy_2K_{21}+\alpha^o_1y_1K_{12}+\alpha^o_2y_2K_{22})
\end{align*}
$$

then

$$
\begin{align*}
\alpha_2^n&=\frac{1}{K_{11}-2K_{12}+K_{22}}y_2(y_2-y_1 + f(x_1)-f(x_2)+\alpha^o_2y_2K_{11}-2\alpha^o_2y_2K_{21}+\alpha^o_2y_2K_{22})\\
&=\frac{1}{K_{11}-2K_{12}+K_{22}}y_2\Big[(f(x_1)-y_1)-(f(x_2)-y_2) + \alpha^o_2y_2(K_{11}-2K_{12}+K_{22}) \Big]
\end{align*}
$$

Let $\epsilon = K_{11}-2K_{12}+K_{22}$, $E_1 = f(x_1)-y_1$, $E_2=f(x_2)-y_2$, then

$$
\alpha^n_2 =\frac{1}{\epsilon}y_2(E_1-E_2) + \alpha^o_2
$$

as $\alpha^o_1y_1 + \alpha^o_2y_2=C$

$$
\begin{align*}
\alpha^n_1=y_1(C-\alpha_1^ny_2)&=y_1(\alpha_1^oy_1 + \alpha^o_2y_2-\alpha^N_2y_2)\\
&=\alpha^o_1 + y1_y2(\alpha^o_2 - \alpha^n_2)\\
&=\alpha^o_1 + y_1y_2(-\frac{1}{\epsilon}y_2(E_1-E_2))\\
&=\alpha^o_1+\frac{y_1}{\epsilon}(E_2-E_1)
\end{align*}
$$

To the conclusion, the solution of $(\alpha_1, \alpha_2)$ is

$$
\begin{cases}
\displaystyle\alpha^n_1=\alpha^o_1+\frac{y_1}{\epsilon}(E_2-E_1)\\
\\
\displaystyle\alpha^n_2 = \alpha^o_2+\frac{y_2}{\epsilon}(E_1-E_2)
\end{cases}
$$

Afterwards, we can find the solution for the $\alpha_3, \alpha_4,...\alpha_N$ through same approach.
