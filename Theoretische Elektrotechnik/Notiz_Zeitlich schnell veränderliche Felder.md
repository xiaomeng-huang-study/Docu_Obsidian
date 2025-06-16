# 1. Zeitlich schnell veränderliche Felder 
## 1.1 Maxwellsche Gleichungen für zeitlich schnell veränderliche Felder 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-28_21-08-02.png?raw=" width="80%" /> 

## 1.2 Energieerhaltungssatz 
- $-\frac{d}{d t}\left(W_{e}+W_{m}\right)=\underbrace{\unicode{x222F}_{F}(\vec{E} \times \vec{H}) \cdot d \vec{f}}_{P_{r}}+\underbrace{\iiint_{V} \vec{E} \cdot \vec{J} d v}_{P_{d}}-P_{s}$ 
	- $P_{r}$ : Durch die geschlossene Oberfläche abgestrahlte Leistung 
	- $P_d$ : Verlustleistung (Joule-Erwärmung) 
	- $P_{s}$ : Stromversorgung durch Fremdstromquellen 

### Poynting vector 
- $\vec{S}=\vec{E} \times \vec{H}$ ($[\vec{S}]=\frac{V}{m} \frac{A}{m}=\frac{W}{m^{2}}$) 

### Am Beispiel Strip Transmission Line 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-28_21-23-39.png?raw=" width="50%" /> 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-28_21-43-31.png?raw=" width="70%" /> 

#### Perfect Electric Conductor (PEC) ($\kappa = \infty$) 
- $\vec{E}_{l}=\frac{\vec{J}}{\kappa} \rightarrow 0$ $\Rightarrow$ $\vec{E}_{t} = \vec{E}$ 
- $\vec{S}=\vec{E}_{t} \times \vec{H}$  $\Rightarrow$ $\vec{S}_{l} = \vec{S}$ 
- $\begin{array}{l}P_{\text {load }}&= \unicode{x222F}_{F} \vec{S} \cdot d \vec{f} \\&= |\vec{S}_{l}|  \cdot ab \\ &= \mathrm{UI} \\\end{array}$ 

#### Metallic Conductor 
- $\vec{E} = \vec{E}_{t} + \vec{E}_{l}$ $\Rightarrow$ $\vec{E}_{t} < \vec{E}$ 
- $\vec{S}=\left(\vec{E}_{l}+\vec{E}_{t}\right) \times \vec{H}$ $\Rightarrow$ $\vec{S}_{l} < \vec{S}$ 
- $\begin{array}{l}P_{\text {load }}&= \unicode{x222F}_{F} \vec{S} \cdot d \vec{f} \\&= |\vec{S}_{l}|  \cdot ab \\&< \mathrm{UI} \\\end{array}$ 


## 1.3 Phasoren für zeitharmonische Felder 
- $\begin{array}{ll}\vec{E}(\vec{r}) &= x\cdot \vec{e}_x + y\cdot \vec{e}_y + z \cdot \vec{e}_z \\\vec{E}(\vec{r}, t) &= \vec{E}(\vec{r}) \cos \left(\omega t-\varphi\right) \\\vec{\underline{E}}(\vec{r}) &= \vec{E}(\vec{r}) e^{-j \varphi}  \\ \end{array}$ 


## 1.4 Maxwellsche Gleichungen in Phasorschreibweise 


## 1.5 Energieerhaltungssatz für komplexe Vektoren 


## 1.6 Wellengleichung 


## 1.7 Homogene ebene Welle (HEW) 
- Phasenfläche: die Fläche, auf der alle Punkte die **gleiche Phase** einer Welle besitzen. In einer ebenen Welle sind die Phasenflächen Ebenen, die senkrecht zur Ausbreitungsrichtung der Welle stehen. 
- Ebene Welle: eine Welle, deren Phasenflächen Ebenen sind. Die Wellenfronten sind also unendlich große, parallele Ebenen. Die Amplitude und Richtung der Welle ändern sich in der Ebene nicht, sondern nur in Ausbreitungsrichtung. 
- Homogene Ebene Welle: eine spezielle Form der ebenen Welle, bei der die Amplitude über die gesamte Phasenfläche konstant ist. Die Welle breitet sich ohne Dämpfung und ohne Richtungsänderung in einem homogenen Medium aus. 

- Wellenzahl: $$\begin{array}{l}k& =\frac{w}{v} \\& =\frac{2 \pi}{\lambda} \\& =k_{0} \sqrt{\varepsilon_{r} \mu_{r}} \quad |~~ k_{0}= \frac{w}{c_{0}} \\\end{array}$$ 
- Feldwellenwiderstand: $$\begin{array}{ll}Z& =\sqrt{\frac{\mu}{\varepsilon}}\\& =\sqrt{\frac{\mu_{r}}{\varepsilon_{r}}} Z_{0} \quad|~~ Z_0 = 120\pi \Omega\\\end{array}$$ 


### Fortschreitende Welle und Stehende Welle 
#### Fortschreitende Welle (Dielektrikum mit Open-End) 
- $\vec{E}(z)= \vec{e}_x E_{0} e^{-j k_1 z}$, $\vec{H}(z)=\vec{e}_y H_{0} e^{-j k_1 z}$ 
	- Amplituden: $E_0$, $H_0$ (konstant über $z$) 
	- Phase: linear fallend entlang der z-Achse, $\varphi = j \cdot (- k_1) z$ 
	- E- und H-Feld: Stehen **in Phase**. 
- Feldwellenimpedanzen $Z$ 
	- $Z=Z_{0} e^{j \phi}$ 
		- Amplituden: $Z_0$ 
		- Phase: $\phi = 0$ 
- Merkmalen 
	- Die Welle **bewegt sich durch den Raum**, transportiert also **Energie** von einem Ort zum anderen 


#### Stehende Welle (Dielektrikum mit elektrischem Ende) 
- $\vec{E}(z)=\vec{e}_x E_{0}\left(e^{-j k_1 z}-e^{j k_1 z}\right)=\vec{e}_x \cdot (-2) j E_{0} \sin (k_1 z)$, $\vec{H}(z)=\vec{e}_y \frac{E_{0}}{Z}\left(e^{-j k_1 z}+e^{j k_1 z}\right)=\vec{e}_x \cdot2 \frac{E_{0}}{Z} \cos (k_1 z)$ 
	- Amplituden: $2 E_{0}|\sin (k_1 z)|$, $2 H_{0}|\cos (k_1 z)|$ 
	- Phase: mit Phasenverschiebung $\frac{\pi}{2}$ 
	- $E(z)$: sinusförmiger Verlauf mit Knoten bei $E=0$, $H(z)$: cosinusförmig, mit Bäuchen dort, wo $E$ Knoten hat. $\Rightarrow$ **nicht in Phase** 
- Feldwellenimpedanzen $Z$ 
	- $Z=Z_{0} e^{j \phi}$ 
		- Amplituden: $Z_0$ 
		- Phase: $\phi = \pm \frac{\pi}{2}$ 
- Merkmalen 
	- Entsteht durch die **Überlagerung** zweier gegenläufiger, gleichartiger fortschreitender Wellen. 
	- Die Welle **bleibt räumlich fixiert**, schwingt aber zeitlich. 
	- Es entstehen feste Punkte, die **nicht schwingen** (Knoten), und Punkte mit **maximaler Auslenkung** (Bauch). 



## 1.8 HEW mit beliebiger Ausbreitungsrichtung 
- vereinfachte MWGs für HEW 
	- 1. MWG: $\vec{E} = - Z \cdot (\vec{n} \times \vec{H})$ 
	- 2. MWG: $\vec{H} = \frac{1}{Z} \cdot (\vec{n} \times \vec{E})$ 

## 1.9 Polarisation von HEW 
- $\begin{array}{ll}\underline{\vec{E}}(\vec{r}) & =\left(\underline{E}_{1} \vec{e}_{1}+\underline{E}_{2} \vec{e}_{2}\right) e^{-j \vec{k} \cdot \vec{r}} \\& =\left(\left|\underline{E}_{1}\right| e^{j \varphi_{1}} \vec{e}_{1}+\left|\underline{E}_{2}\right| e^{j \varphi_{2}} \vec{e}_{2}\right) e^{-j \vec{k} \cdot \vec{r}} \\\end{array}$ 
- Momentanwert: $\vec{E}(\vec{r}, t) = \operatorname{Re}\left\{\vec{\underline{E}}(\vec{r}) \cdot e^{j\omega t}\right\}$ 

1) linear polarisierte Welle ($\varphi_1 = \varphi_2$) 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-06-13_21-39-27.png?raw=" width="30%" /> 
	- $\underline{\vec{E}}(\vec{r})=\left(\left|\underline{E}_{1}\right| \vec{e}_{1}+\left|\underline{E}_{2}\right| \vec{e}_{2}\right) e^{j \varphi_{1}} e^{-j \vec{k} \cdot \vec{r}}$ 
2) $\varphi_{2}=\varphi_{1} \pm \frac{\pi}{2},\quad \left|E_{2}\right|=\left|E_{1}\right|$ 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-06-13_21-40-36.png?raw=" width="30%" /> 
	- $\begin{aligned}\vec{E}(\vec{r}, t) & =\operatorname{Re}\left\{\underline{\vec{E}}(\vec{r}) e^{j \omega t}\right\} \\& =\left|\underline{E}_{1}\right|\left(\operatorname{Re}\left\{e^{j\left(\varphi_{1}-\vec{k} \cdot \vec{r}+\omega t\right)}\right\} \vec{e}_{1} \pm \operatorname{Re}\left\{j e^{j\left(\varphi_{1}-\vec{k} \cdot \vec{r}+\omega t\right)}\right\} \vec{e}_{2}\right) \\& =\left|E_{1}\right|\left[\cos \left(\omega t-\vec{k} \cdot \vec{r}+\varphi_{1}\right) \vec{e}_{1} \mp \sin \left(\omega t-\vec{k} \cdot \vec{r}+\varphi_{1}\right) \vec{e}_{2}\right] \end{aligned}$ 
3) allgemeiner Fall: elliptisch polarisierte Welle 

## 7.10 Poynting-Vektor einer HEW 
- zeitlich gemittelter Poynting-Vektor: $\overline{\vec{S}}=\frac{1}{2} \operatorname{Re}\left\{\underline{\vec{E}} \times \underline{\vec{H}}^{*}\right\}$ 
	- für HEW: $\begin{array}{ll}\overline{\vec{S}}& =\frac{1}{2} \frac{|\vec{E}|^{2}}{Z} \cdot \vec{n} \\& =\frac{1}{2} |\vec{H}|^2 Z \cdot \vec{n} \\ \end{array}$ 
- Leistung $P$ 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-06-16_20-08-24.png?raw=" width="25%" /> 
	- $P=\iint_{F} \overline{\vec{S}} \cdot d \vec{f}$ 

## 7.11 HEW in speziellen Medien 
- komplexe Wellenzahl: $k=\beta - j\alpha$, $\vec{k}= \vec{k}^{\prime} - j \cdot \vec{k}^{\prime \prime}$ 
	- Phasenkonstante $\beta = |\vec{k}^{\prime}|$ 
	- Dämpfungskonstante $\alpha = |\vec{k}^{\prime \prime}|$ 
- $\begin{array}{ll}\vec{\underline{E}}(\vec{r}) &= \vec{E}(\vec{r}) e^{-j \vec{k} \cdot \vec{r}} \\&= \vec{E}(\vec{r}) e^{-j (\vec{k}^{\prime} - j\vec{k}^{\prime \prime}) \cdot \vec{r}} \\&= \vec{E}(\vec{r}) e^{-\vec{k}^{\prime \prime} \cdot \vec{r}} \cdot e^{-j \cdot \vec{k}^{\prime} \cdot \vec{r}} \\\end{array}$ 
	- Dämpfung: $e^{-\vec{k}^{\prime \prime} \cdot \vec{r}}$ 

