# 1. Bestimmung der relativen Grade $\delta_i$ 
- Für jeden Ausgang $y_i$ (Zeile $i$ der Ausgangsmatrix C) ($i \in \{1, ~2, ~3, ~\cdots,~ p\}$): 
	- Für jede Ordnung $k$ ($k \in \{0, ~1, ~2, ~3 ~\cdots\}$): 
		- Prüfe $C_i A^k B$ 
		- Falls $C_i A^k B \neq 0$ → $\delta_i = k+1$ 
		- Falls $C_i A^k B = 0$ → weiter zu $k+1$ 


# 2. Entkoppelbarkeit 
- 0. Bedingung: Alle relativen Grade $\delta_i$ existieren (endlich sind) 
- 1. Bedingung: Summe der relativen Grade $\delta$  ≤ Systemordnung $n$ 
	- Summe der relativen Grade $\delta = \sum_{i}\delta_i$ 
- 2. Bedingung: Die Entkopplungsmatrix $\underline{D}^{\star}$ ist invertierbar ($\operatorname{det.}(\underline{D}^{\star}) \neq 0$) 
	- Entkopplungsmatrix: $\underline{D}^{\star} = \begin{bmatrix} C_1 A^{\delta_1-1} B \\ C_2 A^{\delta_2-1} B \\ \vdots \\ C_p A^{\delta_p-1} B \end{bmatrix}$ 


# 3. Vorfilter $\underline{V}$ 
 - $\operatorname{inv}(\underline{D}^{\star}) = {\underline{D}^{\star}}^{-1}$ 
- $\underline{V} = {\underline{D}^{\star}}^{-1} \cdot \operatorname{diag.}(k_1, ~k_2, ~\cdots~, k_p)$ 


# 4. Rückführmatrix $\underline{R}$ 
- $\underline{R}={\underline{D}^{\star}}^{-1} \cdot \left[\begin{array}{c}\underline{C}_{1}^{T} \underline{A}^{\delta_{1}}+\sum_{k=0}^{\delta_{1}-1} q_{1, k} \underline{C}_{1}^{T} A^{k} \\\vdots \\\underline{C}_{p}^{T} \underline{A}^{\delta_{p}}+\sum_{k=0}^{\delta_{p}-1} q_{p, k} \underline{C}_{p}^{T} A^{k} \\\end{array}\right]$ 
	- Für $y_1 ~(i=1)$ : $s^{2} + q_{1,1}\cdot s + q_{1,0}$ 

