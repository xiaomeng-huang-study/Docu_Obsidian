1) System-Matrix $\underline{A}$ in $\underline{A}_{11}$, $\underline{A}_{12}$, $\underline{A}_{21}$, $\underline{A}_{22}$ unterteilen; Eingangsmatrix $\underline{B}$ in $\underline{B}_1$, $\underline{B}_2$ unterteilen 
2) $\underline{A}_{BEO} = (\underline{A}_{22}- \underline{L} \cdot \underline{A}_{12})$ 
3) $\operatorname{det.} \left(s \cdot \underline{I} - \underline{A}_{BEO}\right)$ 
4) Polvergabe (z.B. Koeffizienten-Vergleich) $\Rightarrow$ $\underline{L}$ 
5) $\underline{A}_{BEO} = (\underline{A}_{22}- \underline{L} \cdot \underline{A}_{12})$ 
6) $\underline{H}= \underline{A}_{BEO} \cdot \underline{L} + \underline{A}_{21} - \underline{L} \cdot \underline{A}_{11}$ 
7) $\underline{B}_{BEO} = \underline{B}_{2} - \underline{L} \cdot \underline{B}_{1}$ 
8) $\left\{\begin{array}{ll}\underline{\dot{\rho}} &= \underline{A}_{BEO} \cdot \underline{\rho} + \underline{H} \cdot \underline{y} + \underline{B}_{BEO} \cdot \underline{u} \\\underline{r} &= \underline{\rho} + \underline{L} \cdot \underline{y} \\\end{array}\right.$ 