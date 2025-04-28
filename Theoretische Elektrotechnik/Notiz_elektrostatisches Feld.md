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
- Für Linienladung $\rho_{S}(\vec{r})$: $\phi(\vec{r})=\frac{1}{4 \pi \varepsilon_{0}} \int_{S} \frac{\rho_{S}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|} d S^{\prime}$ 
- Für Flächenladung $\rho_{F}(\vec{r})$: $\phi(\vec{r})=\frac{1}{4 \pi \varepsilon_{0}} \iint_{F} \frac{\rho_{F}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|} d F^{\prime}$ 
- Für Volumenladung $\rho_{V}(\vec{r})$: $\phi(\vec{r}) = \frac{1}{4 \pi \varepsilon_{0}} \iiint_{V} \frac{\rho_{V}\left(\vec{r}^{\prime}\right)}{\left|\vec{r}-\vec{r}^{\prime}\right|} d V^{\prime}$ 

### Überlagerungsprinzip 


## 2.4 Spiegelungsmethode 
### 2.4.1 Spiegelung an einer Ebene 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-16_12-46-07.png?raw=" width="40%" /> 
- $Q^{\prime}=-Q$ , $z=-z^{\prime}$ 

### 2.4.2 Spiegelung an einer Kugel 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Theoretische_Elektrotechnik/refs/heads/main/Scrennshot_2025-04-16_14-26-01.png?raw=" width="40%" /> 
- $p^{\prime}=\frac{a^{2}}{p} \quad$ 
- $Q^{\prime}=-\frac{a}{p} Q$ 

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
