# 1. Maxwellsche Gleichungen quasistationärer Felder 


# 2. Das Induktionsgesetz 
## 2.1 Induktionswirkung im bewegten Leiter 

## 2.2 Ruhende Leiterschleife 
- Lenzsche Regel: Das Magnetfeld des induzierten Stromes wirkt der Änderung des Originalfeldes entgegen. 
- $\begin{array}{l}u_{i n d}&=-\frac{d}{d t} \phi_{m} \\&=-\frac{d}{d t} \iint_{F} \vec{B} \cdot d \vec{f} ~~~~|~~ \phi_{m} = \iint_{F} \vec{B} \cdot d \vec{f} \\&=R \cdot i_{i n d}\\&=\oint_{C(F)} \vec{E}\cdot d \vec{s}\end{array}$ 

## 2.3 Bewegte Leiterschleife 
- $\begin{align}u_{i n d} & = -\iint_{A} \frac{\partial \vec{B}(\vec{r}, t)}{\partial t} \cdot d \vec{f} + \oint_{C(A)}(\vec{v} \times \vec{B}) \cdot d \vec{s} \\& = R \cdot i_{i n d} \\\end{align}$ 

### Falls Leiterschleife gebrochen 
- $\vec{J}=\kappa(\vec{E}+\vec{v} \times \vec{B})=0$ 
- $u = \int{\vec{E}\cdot d\vec{s}}$ 

## 2.4 Verlustleistung 
- Verlustleistungsdichte: $p(t)=\frac{1}{2} \vec{J} \cdot \vec{E}=\frac{1}{2} \kappa|\vec{E}|^{2}$ 
- Verlustleistung: $P_{v}(t)=\iiint \frac{1}{2} \vec{J} \cdot \vec{E} d v$ 
- zeitlich gemittelte Verlustleistung: $\bar{P}_{v}=\frac{1}{T} \int_{0}^{T} P_{v}(t) d t$ 

# 3. Induktionskoeffizienten 
- magnetische Feldenergie: $\begin{array}{l}W_{m}&=\frac{1}{2} \iiint_{V} \vec{A} \cdot \vec{J} ~ d V  \\&= \frac{1}{2} \iiint_{V} \vec{H} \cdot \vec{B} ~d V\\&= \frac{1}{2} L I^{2} \\\end{array}$ 
- Induktionskoeffizient: $\begin{array}{l}L &=\frac{\phi_{\mathrm{m}}}{I} = \frac{1}{I}\iint_{F} \vec{B}\left(\vec{r}\right) \cdot d \vec{f}\\&=\frac{2W_{m}}{I^2}\\\end{array}$ 

## Spezialfall: zwei verkoppelte Leiterschleifen 
- der magnetische Fluss, der von Leiterkreis 2 herrührend Leiterkreis 1 durchsetzt: $\phi_{\mathrm{m}, 12}=\iint_{F_{1}} \vec{B}_{2}\left(\vec{r}_{1}\right) \cdot d \vec{f}$ 
- $L_{12} =\frac{\phi_{\mathrm{m}, 12}}{I_{2}}$ 
- $W_{m}=\frac{1}{2}\left(L_{11} I_{1}^{2}+L_{22} I_{2}^{2}+2 L_{12} I_{1} I_{2}\right)$ 

