- Fourier Reihe
	- für stationäre Signale
	- reelle Schreibweise
		 $y(t)=y_0+\sum\limits_{k=1}^\infty\big(a_k·\cos(k\omega_0~t)+b_k·\sin(k\omega_0~t))$ 
		 - Gleichanteil
			 - $y_0= \frac{1}{T} \int_{0}^{T} y(t) \text{ dt}$ 
		 - cos-Anteil
			- $a_k=\frac{2}{T} \int_{0}^{T} \cos(k\omega_0~t)\text{ dt}$ 
		- sin-Anteil
			- $b_k=\frac{2}{T} \int_{0}^{T} \sin(k\omega_0~t)\text{ dt}$ 
	- komplexe Schreibweise
		- $x(t)=x_0 + \dfrac{1}{2} \sum\limits_{k=-\infty,k\ne0}^{\infty} \tilde {x_k}\cdot e^{jk\omega_0t}$ 
		- komplexe Fourier-Koeffizienten
			- $\begin{array}{r} \tilde {x_k} =\dfrac2T\int_T x(t)·e^{-jk\omega_0t}\text{ dt}=a_k-jb_k\\=\dfrac2T\int_T x(t)·\big(\cos(k\omega_0t)-j\sin(k\omega_0t) \big)\text{ dt}\end{array}$
			- $\begin{array}{r} 1.&Zeile \\ 2.&Zeile \end{array}$  