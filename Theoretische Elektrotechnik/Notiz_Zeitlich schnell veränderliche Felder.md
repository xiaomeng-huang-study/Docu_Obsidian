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


## 1.4 Maxwellsche Gleichungen in Phasorschreibweise 


## 1.5 Energieerhaltungssatz für komplexe Vektoren 


## 1.7 Homogene ebene Welle (HEW) 
### Fortschreitende Welle (Dielektrikum mit Open-End) 
- $\vec{E}(z)= \vec{e}_x E_{0} e^{-j k_1 z}$, $\vec{H}(z)=\vec{e}_y H_{0} e^{-j k_1 z}$ 
- Amplituden: konstant über $z$ 
- Phase: linear fallend entlang der z-Achse, $\varphi = j \cdot (- k_1) z$ 
- Real- & Imaginärteil 
	- $\text{Re}\{E(z)\}$ ist eine laufende Sinuswelle, verschoben mit Ort und Zeit. 
	- $\text{Im}\{E(z)\}$ ist um 90° phasenverschoben. 
- E- und H-Feld: Stehen in Phase. 
- Die Welle bewegt sich durch den Raum, transportiert also Energie von einem Ort zum anderen 

### Stehende Welle (mit elektrischem Ende) 
- $\vec{E}(z)=\vec{e}_x E_{0}\left(e^{-j k_1 z}-e^{j k_1 z}\right)=\vec{e}_x \cdot (-2) j E_{0} \sin (k_1 z)$, $\vec{H}(z)=\vec{e}_y \frac{E_{0}}{Z}\left(e^{-j k_1 z}+e^{j k_1 z}\right)=\vec{e}_x \cdot2 \frac{E_{0}}{Z} \cos (k_1 z)$ 
- Amplituden 
	- $E(z)$: sinusförmiger Verlauf mit Knoten bei $E=0$. 
	- $H(z)$: cosinusförmig, mit Bäuchen dort, wo $E$ Knoten hat. 
- Phase: $E$ und $H$ sind 90° phasenverschoben im Ort (nicht in der Zeit!). 
- Real- & Imaginärteil: Beide oszillieren synchron, aber nicht wandernd – keine laufende Phase! 
- E- und H-Feld 
	- Im gleichen Ortspunkt: E und H nicht in Phase. 
