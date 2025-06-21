# 1. Potentialfunktion $\phi(\vec{r})$ 
- Für Punktladung $Q$ : $\phi(\vec{r})=\frac{1}{4 \pi \varepsilon_{0}}\frac{Q}{\left|\vec{r} - \vec{r}^{\prime}\right|}$ 


# 2. Methoden zur Berechnung elektrostatischer Felder 
## 2.1 Methode des Gaußschen Gesetzes 
- $\huge\unicode{x222F}_{F(V)} \vec{D} \cdot d \vec{f}=\iiint_{V} \rho \cdot dV$ 

## 2.2 Poisson- und Laplace-Gleichung 
- Für ein homogenes Material ($\varepsilon(\vec{r})=\mathrm{const}.$): **Poisson-Gleichung** $\Delta \phi(\vec{r})=-\frac{\rho(\vec{r})}{\varepsilon}$ 
- In einem ladungsfreien Gebiet ($\rho = 0$): **Laplace-Gleichung** $\Delta \phi(\vec{r})=0$ 

## 2.3 Coulombintegral-Methode/ Überlagerungsprinzip 
### Coulombintegral-Methode 
- Für Linienladung $\rho_{S}(\vec{r}^{\prime})$: $\phi(\vec{r})=\frac{1}{4 \pi \varepsilon_{0}} \int_{S} \frac{\rho_{S}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|} d S^{\prime}$ 
- Für Flächenladung $\rho_{F}(\vec{r}^{\prime})$: $\phi(\vec{r})=\frac{1}{4 \pi \varepsilon_{0}} \iint_{F} \frac{\rho_{F}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|} d F^{\prime}$ 
- Für Volumenladung $\rho_{V}(\vec{r}^{\prime})$: $\phi(\vec{r}) = \frac{1}{4 \pi \varepsilon_{0}} \iiint_{V} \frac{\rho_{V}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|} d V^{\prime}$ 

### Überlagerungsprinzip 
- $\phi(\vec{r})=\frac{1}{4 \pi \varepsilon_{0}} \sum_{i}  \frac{Q_i}{\left|\vec{r}-\vec{r_i}^{\prime}\right|}$ 
- $\begin{array}{l}\vec{E} & =- \text { grad } \phi \\& =\frac{1}{4 \pi \varepsilon_{0}} \sum_{i} Q_i \frac{\vec{r}-\vec{r}_{i}^{\prime}}{\left|\vec{r}-\vec{r}_{i}^{\prime}\right|^{3}}  \\\end{array}$ 

## 2.4 Spiegelungsmethode 
### 2.4.1 Spiegelung an einer Ebene 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-16_12-46-07.png?raw=" width="40%" /> 
- $Q^{\prime}=-Q$ , $z=-z^{\prime}$ 

### 2.4.2 Spiegelung an einer Kugel 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-16_14-26-01.png?raw=" width="40%" /> 
- $r_2^{\prime} \cdot {r_1^{\prime}} = r_0^{2}$ 
- $\begin{array}{ll}\frac{Q_2}{Q_1} & =-\frac{r_0}{r_1^{\prime}} \\& =-\frac{r_2^{\prime}}{r_0} \\\end{array}$ 

### 2.4.3 Spiegelung an einem Zylinder 

### 2.4.4 Spiegelung an der dielektrischen Ebenen 
- originale Anordnung 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-26_13-51-31.png?raw=" width="40%" /> 

#### Ersatzanordnung für Lösungsgebiet I 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-26_13-54-40.png?raw=" width="40%" /> 
- $Q^{\prime}=\frac{\varepsilon_{1}-\varepsilon_{2}}{\varepsilon_{1}+\varepsilon_{2}} \cdot Q$ 
- $d_{Q^{\prime}}=-d_{Q}$ 

#### Ersatzanordnung für Lösungsgebiet II 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-26_13-57-02.png?raw=" width="40%" /> 
- $Q^{\prime}=\frac{2\cdot\varepsilon_{2}}{\varepsilon_{1}+\varepsilon_{2}} \cdot Q$ 
- $d_{Q^{\prime}}=d_{Q}$ 


# 3. Kondensator und Kapazität 
- Kapazität: $C=\frac{\huge\unicode{x222F}_{A} \vec{D} \cdot d \vec{f}}{\int_{1}^{2} \vec{E} \cdot d \vec{s}}$ 
	- Sonderfall: $C=\frac{\varepsilon_{0} \varepsilon_{r} A}{d}$ 


# 4. Energie im elektrischen Feld 
- $W_{\mathrm{el}}=\iiint_{V} \frac{1}{2} \vec{E}(\vec{r}) \vec{D}(\vec{r}) d V$ 
- $W_{\mathrm{Kond}}=W_{\mathrm{el}}=\frac{1}{2} C U^{2}=\frac{1}{2} Q U=\frac{1}{2} \frac{1}{C} Q^{2}$ 


# Kräfte im elektrostatischen Feld 
- $d W_{\mathrm{el}}+\vec{F} \cdot d \vec{s}=0$ 

