# Maxwelsche Gleichungen 
## 1. Erweitertes Durchflutungsgesetz 
- Das Flächenintegral über die Stromdichte $\vec{J}$ (d.h. der durch die Fläche tretende Gesamtstrom) ist gleich dem Umlaufintegral über die magnetische Feldstärke $\vec{H}$ längs der Berandung der Fläche $F$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_08-21-55.png?raw=" width="30%" />  
- in Form eines Integrals 
	- $\oint_{C(F)} \vec{H} \cdot d \vec{s}=\iint_{F}\left(\vec{J}+\frac{\partial}{\partial t} \vec{D}\right) \cdot d \vec{f}$ 
- in Differentialform 
	- $\operatorname{rot} \vec{H}=\vec{\nabla} \times \vec{H}=\vec{J}+\frac{\partial}{\partial t} \vec{D}$ 

## 2. Induktionsgesetz 
- Die negative zeitliche Änderung des magnetischen Flusses $\psi_{m}$ durch die Fläche $F$ ist gleich dem Umlaufintegral über die elektrische Feldstärke längs der Berandung der Fläche. 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_16-41-51.png?raw=" width="25%" /> 
- in Form eines Integrals 
	- $\oint_{C(F)} \vec{E} \cdot d \vec{s}=-\iint_{F} \frac{\partial}{\partial t} \vec{B} \cdot d \vec{f}$ 
- in Differentialform 
	- $\operatorname{rot} \vec{E}=\vec{\nabla} \times \vec{E}=-\frac{\partial}{\partial t} \vec{B}$ 

## 3. Gaußsches Gesetz 
- Der elektrische Fluss $\psi_{e}$ durch eine geschlossene Oberfläche ist gleich der gesamten darin eingeschlossenen Ladung $Q$. 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_16-46-34.png?raw=" width="35%" /> 
- in Form eines Integrals 
	- $\huge\unicode{x222F}_{F(V)} \vec{D} \cdot d \vec{f}=\iiint_{V} \rho d V$ 
- in Differentialform 
	- $\operatorname{div} \vec{D}=\vec{\nabla} \cdot \vec{D}=\rho$ 

## 4. Gaußsches Gesetz für Magnetfelder 
- Der magnetische Fluss $\psi_{m}$ durch eine geschlossene Oberfläche verschwindet. Die Summe der eintretenden und austretenden magnetischen Feldlinien ist also gleich, es existieren keine magnetischen Monopole. 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-04-18.png?raw=" width="35%" /> 
- in Form eines Integrals 
	- $\huge\unicode{x222F}_{F(V)} \vec{B} \cdot d \vec{f}=0$ 
- in Differentialform 
	- $\operatorname{div} \vec{B}=\vec{\nabla} \cdot \vec{B}=0$ 


# Randbedingungen des elektromagnetischen Feldes 
## 1. Randbedingung 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-26-51.png?raw=" width="60%" /> 
- $\vec{n} \times\left(\vec{H}_{1}-\vec{H}_{2}\right)=\left\{\begin{array}{l}0 \\\vec{J}_{F} \text{,  falls Oberflächenstrom in Grenzfläche. }\end{array}\right.$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-27-28.png?raw=" width="80%" /> 

## 2. Randbedingung 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-29-07.png?raw=" width="60%" /> 
- $\vec{n} \times\left(\vec{E}_{1}-\vec{E}_{2}\right)=0$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-31-03.png?raw=" width="80%" /> 

## 3. Randbedingung 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-32-08.png?raw=" width="60%" /> 
- $\vec{n} \cdot\left(\vec{D}_{1}-\vec{D}_{2}\right)=\left\{\begin{array}{l}0 \\\rho_{F} \text {,  falls Grenzfläche Oberflächenladung trägt }\end{array} \quad\right.$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-33-58.png?raw=" width="80%" /> 

## 4. Randbedingung 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-35-32.png?raw=" width="60%" /> 
- $\vec{n} \cdot\left(\vec{B}_{1}-\vec{B}_{2}\right)=0$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-04_17-34-34.png?raw=" width="80%" /> 

