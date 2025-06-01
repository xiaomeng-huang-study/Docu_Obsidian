# Skalarprodukt und Vektorprodukt 
- Skalarprodukt $\vec{a} \cdot \vec{b}=|\vec{a}||\vec{b}| \cos \varphi$ 
- Vektorprodukt $\vec{c}=\vec{a} \times \vec{b}$ mit $|\vec{c}|=|\vec{a}||\vec{b}| \sin \varphi$ 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-03-24_21-50-47.png?raw=" width="30%" /> 



# Skalares Feld und Vektorfeld 
- Skalares Feld 
	- Jedem Punkt eines Raumes $\overrightarrow{r}$ wird eine reelle (oder komplexe) skalare Größe $\phi(\overrightarrow{r})$ zugeordnet. 
	- Zuordnung gegeben durch **skalare Feldfunktion**. 
- Vektorfeld 
	- Jedem Punkt eines Raumes $\overrightarrow{r}$ wird ein reeller (oder komplexer) Vektor skalare Größe $\overrightarrow{a}(\overrightarrow{r})$ zugeordnet. 
	- Zuordnung gegeben durch **vektorielle Feldfunktion** $\overrightarrow{a}$. 


# Koordinatensystem 
## Kartesisches Koordinatensystem 
- $(x, y, z)$ 

## Zylinderkoordinaten 
- $(\rho, \varphi, z)$  

## Kugelkoordinaten 
- $(r, \theta, \varphi)$ 


# Gradient, Divergenz, Rotation
## Gradient 
- Definition: Der Gradient ist eine <ins>vektorielle</ins> Ableitung einer skalaren Funktion. Er beschreibt die **Richtung** und die **Größe** der **stärksten Zunahme** dieser Funktion. 
- Mathematische Definition: $\operatorname{grad}f = \nabla f=\frac{\partial f}{\partial x}\vec{e}_x + \frac{\partial f}{\partial y}\vec{e}_y + \frac{\partial f}{\partial z}\vec{e}_z$ 
	- Bedeutung 
		- Der Gradient zeigt in die **Richtung**, in der die Funktion am stärksten wächst. 
		- Die Länge des Gradienten gibt die **Änderungsrate** der Funktion in diese Richtung an. 
- In kartesischen Koordinaten 
	- $\operatorname{grad} \phi(x, y, z)= \nabla \phi(x, y, z)= \frac{\partial \phi(x, y, z)}{\partial x} \vec{e}_x + \frac{\partial \phi(x, y, z)}{\partial y} \vec{e}_y + \frac{\partial \phi(x, y, z)}{\partial z} \vec{e}_z$ 

## Divergenz 
- Definition: Die Divergenz eines Vektorfeldes ist eine <ins>skalare Größe</ins>, die beschreibt, **wie stark** ein Vektorfeld an einem Punkt **eine Quelle** (Ausstrom) **oder** **eine Senke** (Einstrom) ist. 
- Mathematische Definition: $\operatorname{div} \mathbf{F}=\nabla \cdot \mathbf{F}=\frac{\partial F_{x}}{\partial x}+\frac{\partial F_{y}}{\partial y}+\frac{\partial F_{z}}{\partial z}$ 
	- Bedeutung 
		- **Positive** Divergenz bedeutet, dass das Vektorfeld an diesem Punkt eine **Quelle** ist, also „auseinanderströmt“ (z. B. eine Luftquelle). 
		- **Negative** Divergenz bedeutet, dass das Vektorfeld dort eine **Senke** ist, also „zusammenfließt“ (z. B. ein Abfluss). 
		- **Null** bedeutet, dass das Vektorfeld dort **quellenfrei** ist (z. B. ein inkompressibles Fluid wie Wasser). 
- In kartesischen Koordinaten 
	- $\operatorname{div} \vec{A}(x, y, z)= \nabla \cdot \vec{A}(x, y, z) = \frac{\partial A_{x}(x, y, z)}{\partial x}+\frac{\partial A_{y}(x, y, z)}{\partial y}+\frac{\partial A_{z}(x, y, z)}{\partial z}$ 

## Rotation 
- Definition: Die Rotation eines Vektorfeldes (auch Curl genannt) ist ein Maß für die lokale **Drehbewegung** des Feldes um einen Punkt. 
- Mathematische Definition: $\begin{array}{l}\operatorname{rot} \vec{F}(x, y, z) & = \nabla \times \mathbf{F} \\& = \left|\begin{array}{ccc}\vec{e}_{x} & \vec{e}_{y} & \vec{e}_{z} \\\frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\F_{x} & F_{y} & F_{z}\end{array}\right| \\&=\left(\begin{array}{l}\partial / \partial x \\\partial / \partial y \\\partial / \partial z\end{array}\right) \times\left(\begin{array}{l}x \\y \\z\end{array}\right)\\& = (\frac{\partial F_{z}}{\partial y}-\frac{\partial F_{y}}{\partial z}) \vec{e}_x+ (\frac{\partial F_{x}}{\partial z}-\frac{\partial F_{z}}{\partial x}) \vec{e}_y+ (\frac{\partial F_{y}}{\partial x}-\frac{\partial F_{x}}{\partial y})\vec{e}_z\end{array}$ 
	- Bedeutung 
		- **Null** bedeutet, dass das Vektorfeld **wirbelfrei** ist. 
- In kartesischen Koordinaten 
	- $\operatorname{rot} \vec{A}(x, y, z)=\nabla \times \vec{A}(x, y, z)=(\frac{\partial A_{z}}{\partial y}-\frac{\partial A_{y}}{\partial z})\vec{e}_x+(\frac{\partial A_{x}}{\partial z}-\frac{\partial A_{z}}{\partial x})\vec{e}_y+(\frac{\partial A_{y}}{\partial x}-\frac{\partial A_{x}}{\partial y})\vec{e}_z$ 

## Nabla-Operator $\nabla$ und Laplace-Operator $\Delta$ 
- Nabla-Operator $\nabla=\frac{\partial}{\partial x} \vec{e}_{x}+\frac{\partial}{\partial y} \vec{e}_{y}+\frac{\partial}{\partial z} \vec{e}_{z}$ 
- Laplace-Operator $\Delta=\nabla^{2}=\frac{\partial^{2}}{\partial x^{2}}+\frac{\partial^{2}}{\partial y^{2}}+\frac{\partial^{2}}{\partial z^{2}}$ 

