1) $\underline{Q}_B = \left[\begin{array}{c}\underline{c}^{T} \\\underline{c}^{T} \underline{A} \\\vdots \\\underline{c}^{T} \underline{A}^{n-1}\end{array}\right]$ 
2) $\underline{Q}_B^{-1}$ 
3) $\underline{s}_1 =$ die letzte **Spalte** von $\underline{Q}_B^{-1}$ 
4) $\underline{A} \cdot \underline{s}_1$ ; ...; $\underline{A}^{n-1} \cdot \underline{s}_1$ 
5) $\left[\underline{s}_{1}, \underline{A} \underline{s}_{1}, \ldots, \underline{A}^{n-1} \underline{s}_{1}\right]$ 
6) $\underline{T}=\left[\underline{s}_{1}, \underline{A} \underline{s}_{1}, \ldots, \underline{A}^{n-1} \underline{s}_{1}\right]^{-1}$ (mit **Inverse**) 
7) $\underline{T}^{-1}$ 
8) $\left\{\begin{array}{ll}\underline{A}_B = \underline{T} \cdot \underline{A} \cdot \underline{T}^{-1} \\\underline{B}_B = \underline{T} \cdot \underline{B} \\ \underline{C}_B = \underline{C}^{T}\underline{T}^{-1} \\\underline{D}_B = \underline{D}  \\ \end{array}\right.$ 
9) $\left\{\begin{array}{ll}\underline{\dot{z}} = \underline{A}_B \cdot \underline{z} + \underline{B}_B \cdot \underline{u} \\\underline{y} = \underline{C}_B \cdot \underline{z} + \underline{D}_B \cdot \underline{u} \\\end{array}\right.$ 

<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Automatisierung_Technischer_Anlagen/refs/heads/main/Scrennshot_2025-06-18_23-48-17.png?raw=" width="100%" /> 
