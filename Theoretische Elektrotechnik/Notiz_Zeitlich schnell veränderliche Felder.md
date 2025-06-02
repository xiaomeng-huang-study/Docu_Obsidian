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
