# 1. Bestimmung der relativen Grade $\delta_i$ 
- Für jeden Ausgang $y_i$ (Zeile $i$ der Ausgangsmatrix $\underline{C}$) ($i \in \{1, ~2, ~3, ~\cdots,~ p\}$): 
	- Für jede Ordnung $k$ ($k \in \{0, ~1, ~2, ~3 ~\cdots\}$): 
		- Prüfe $\underline{C}_i \underline{A}^k \underline{B}$ 
		- Falls $\underline{C}_i \underline{A}^k \underline{B} \neq 0$ → $\delta_i = k+1$ 
		- Falls $\underline{C}_i \underline{A}^k \underline{B} = 0$ → weiter zu $k+1$ 


# 2. Entkoppelbarkeit 
- 0. Bedingung: Alle relativen Grade $\delta_i$ existieren (endlich sind) 
- 1. Bedingung: Summe der relativen Grade $\delta$  ≤ Systemordnung $n$ 
	- Summe der relativen Grade $\delta = \sum_{i}\delta_i$ 
- 2. Bedingung: Die Entkopplungsmatrix $\underline{D}^{\star}$ ist invertierbar ($\operatorname{det.}(\underline{D}^{\star}) \neq 0$) 
	- Entkopplungsmatrix: $\underline{D}^{\star} = \begin{bmatrix} \underline{C}_1 \underline{A}^{\delta_1-1} \underline{B} \\ \underline{C}_2 \underline{A}^{\delta_2-1} \underline{B} \\ \vdots \\ \underline{C}_p \underline{A}^{\delta_p-1} \underline{B} \end{bmatrix}$ 


# 3. Vorfilter $\underline{V}$ 
 - $\operatorname{inv}(\underline{D}^{\star}) = {\underline{D}^{\star}}^{-1}$ 
- $\underline{V} = {\underline{D}^{\star}}^{-1} \cdot \operatorname{diag.}(k_1, ~k_2, ~\cdots~, k_p)$ 


# 4. Rückführmatrix $\underline{R}$ 
- $\underline{R}={\underline{D}^{\star}}^{-1} \cdot \left[\begin{array}{c}\underline{C}_{1}^{T} \underline{A}^{\delta_{1}}+\sum_{k=0}^{\delta_{1}-1} q_{1, k} \underline{C}_{1}^{T} A^{k} \\\vdots \\\underline{C}_{p}^{T} \underline{A}^{\delta_{p}}+\sum_{k=0}^{\delta_{p}-1} q_{p, k} \underline{C}_{p}^{T} A^{k} \\\end{array}\right]$ 
	- Für $y_1 ~(i=1)$ : $s^{2} + q_{1,1}\cdot s + q_{1,0}$ 

