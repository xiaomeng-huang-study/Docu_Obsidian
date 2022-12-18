- Test auf lineare Abhängigkeit
	- Kovarianz-Matrix$$\left(
		\begin{array}{cc} 
		Var(X) & Cov(X,Y)\\
		Cov(X,Y) & Var(Y)
		\end{array}
		\right)$$
	- $Var(X)=E(X^2)-E(X)^2$ 
		- $E(X)=\sum\limits_{i_x=1}^{n_x}x_{i_x}\cdot(\sum\limits_{i_y=1}^{n_y}f(x,y))$ 
		- $E(X^2)=\sum\limits_{i_x=1}^{n_x}x_{i_x}^2\cdot(\sum\limits_{i_y=1}^{n_y}f(x,y))$ 
	- $Var(Y)=E(Y^2)-E(Y)^2$ 
		- $E(Y)=\sum\limits_{i_y=1}^{n_y}y_{i_y}\cdot(\sum\limits_{i_x=1}^{n_x}f(x,y))$ 
		- $E(Y^2)=\sum\limits_{i_y=1}^{n_y}y_{i_y}^2\cdot(\sum\limits_{i_x=1}^{n_x}f(x,y))$ 
	- $Cov(X,Y)=E(X⋅Y)−E(X)\cdot E(Y)$
- Korrelationskoeffizient
	- $r=\frac{Cov(X,Y)}{\sqrt{Var(X)\cdot Var(Y)}}$ 