# 1. Elektrische Felder stationärer Ströme 
## 1.2 Elektrische Stromdichte, Leitfähigkeit 
- Stromdichte: $\vec{J}=\rho_{V} \vec{v}_{D}=\rho_{V} b \vec{E}=\kappa \vec{E}$ 
- elektrische Leitfähigkeit: $\kappa=\rho_{V} b \quad[\kappa]=\frac{\mathrm{S}}{\mathrm{~m}}$ 

## 1.3 Ladungserhaltung 

## 1.4 Leistungsdichte im Strömungsfeld 
- Leistungsdichte: $p=\frac{d P}{d V}=\vec{E} \cdot \vec{J} \quad[p]=\frac{\mathrm{V}}{\mathrm{~m}} \frac{\mathrm{~A}}{\mathrm{~m}^{2}}=\frac{\mathrm{W}}{\mathrm{~m}^{3}}$ 

## 1.5 Joulsche Verlustleistung 

## 1.6 Der Ohmsche Widerstand 
- $R_{12}=\frac{l}{\kappa A}$ 

## 1.7 Grenzflächenbedingungen des stationären Strömungsfeldes 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-02_09-42-32.png?raw=" width="25%" /> 
- $\vec{J}_{n}$ stetig 

## 1.8 Brechungsgesetz der elektrischen Stromdichte 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-02_09-44-54.png?raw=" width="25%" /> 
- $\frac{\tan \left(\alpha_{1}\right)}{\tan \left(\alpha_{2}\right)}=\frac{\kappa_{1}}{\kappa_{2}}$ 

## 1.9 Analogie (Dualität) zwischen stationärem Strömungsfeld und Elektrostatik 
- $$\begin{array}{ccc}\text { Elektrostatik } & & \text { Strömungsfeld } \\\huge\unicode{x222F}_{F(V)} \vec{D} \cdot d \vec{f}=Q & \quad \vec{D} \longleftrightarrow \vec{J} \quad  & \huge\unicode{x222F}_{F(V)} \vec{J} \cdot d \vec{f}=0 \\\vec{D}=\varepsilon \vec{E} & \quad  \varepsilon \longleftrightarrow \kappa \quad  & \vec{J}=\kappa \vec{E} \\\operatorname{div} \vec{D}=\rho &  & \operatorname{div} \vec{J}=0 \\\end{array}$$ 
- $$\begin{array}{rl}\huge\unicode{x222F}_{F(v)} \vec{J} \cdot d \vec{f}+\frac{\partial}{\partial t} \iiint_{v} \rho d v & =0 \\\operatorname{div} \vec{J}+\frac{\partial}{\partial t} \rho &=0 \\\operatorname{div} \vec{J} &=0 \quad | ~ \frac{\partial}{\partial t} \rho = 0 \\\operatorname{div}(\kappa  \vec{E}) & =0 \quad | ~ \vec{J} = \kappa  \vec{E}\\-\kappa  \operatorname{div} \operatorname{grad} \phi & =0 \quad | ~ \vec{E} = -\operatorname{grad} \phi \\-\kappa  \Delta \phi & =0 \\\Delta \phi & =0 \\\end{array}$$ 
- $I=\iint \vec{J} \cdot d \vec{f}$ 
- $R = \frac{\Delta \phi}{I}$ 


## 1.10 Spiegelungsmethode für stationäre Strömungsfelder 
### Spiegelung an einer Ebene $\kappa \rightarrow \infty$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-03_15-04-59.png?raw=" width="30%" /> 

### Spiegelung an einer Ebene $\kappa = 0$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-03_15-08-43.png?raw=" width="70%" /> 


# 2. Magnetische Felder stationärer Ströme 
## 2.1 Maxwellsche Gleichungen fur¨ das zeitlich konstante Magnetfeld 

## 2.2 Das Durchflutungsgesetz 
- $\oint_{C(F)} \vec{H} \cdot d \vec{s}=\iint_{F} \vec{J} \cdot d \vec{f}$ 

## 2.3 Das magnetische Vektorpotential $\vec{A}$ und das Biot-Savartsche Gesetz 
### Vektorpotential 
- $\vec{A}(\vec{r})=\frac{\mu}{4 \pi} \iiint_{V^{\prime}} \frac{\vec{J}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\overrightarrow{r^{\prime}}\right|} d V^{\prime}$ 
- für linienförmige Leiter: $\vec{A}(\vec{r})=\frac{\mu I}{4 \pi} \int \frac{d \vec{s}^{\prime}}{\left|\vec{r}-\vec{r}^{\prime}\right|}$ 

### Das Biot-Savartsche Gesetz 
- allgemein: $\vec{B}=\frac{\mu}{4 \pi} \iiint \frac{\vec{J}\left(\vec{r}^{\prime}\right) \times\left(\vec{r}-\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|^{3}} d V^{\prime}$ 
- für dünne Leitbahn: $\vec{B}=\frac{\mu}{4 \pi} \iint \frac{\vec{J}_{F}\left(\vec{r}^{\prime}\right) \times\left(\vec{r}-\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|^{3}} d f^{\prime}$ 
- für linienförmige Leiter: $\vec{B}(\vec{r})=\frac{\mu I}{4 \pi} \int_{C} \frac{d \vec{s}^{\prime} \times\left(\vec{r}-\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|^{3}}$ 
- ($\vec{B}(\vec{r}) = \frac{\mu I}{2\pi R} \cdot \vec{e_{\varphi}}$) 

## 2.4 Kräfte im Magnetfeld 
### 1. Amperesches Gesetz 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-15_19-28-59.png?raw=" width="20%" /> 
- $\vec{F}=i \cdot(\vec{l} \times \vec{B})$ 

### 2. Lorentz-Kraft (auf bewegte Ladung) 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-15_19-29-41.png?raw=" width="20%" /> 
- $\vec{F}=Q(\vec{v} \times \vec{B})=Q(\vec{E}+\vec{v} \times \vec{B})$ 

### 3. Kraft auf $\vec{J}$ im $\vec{B}-Feld$ 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-05-15_19-30-25.png?raw=" width="20%" /> 
- $\vec{F}=\iiint_{V} \vec{f}(\vec{r}) d v=\iiint_{V}(\vec{J}(\vec{r}) \times \vec{B}(\vec{r})) d v$ 
- für linienförmige Leiter: $\vec{F}=\int_{C} i(d \vec{s} \times \vec{B}(\vec{r}))$ 
- Falls $\vec{J}$ und $\vec{B}$ homogen im Volumen $V$ sind: $\vec{F}=(\vec{J} \times \vec{B}) V$ 

