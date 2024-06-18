$$
R_{t} =
    \left\{
    \begin{array}{ll}
        R_\text{success} & = & 100 & \text{wenn} ~~~~~~~~~~~~ S_t = S_\text{success} \\
        R_\text{collision} & = & -100 & \text{wenn} ~~~~~~~~~~~~  S_t = S_\text{collision} \\
        R_\text{truncation} & = & 0 & \text{wenn} ~~~~~~~~~~~~  S_t = S_\text{truncation} \\
        R_1 & = & R_\text{gt} + R_\text{angle,gt} + R_\text{ori,gt} &
            \left\{\begin{array}{}
				R_\text{gt} & = &
                    \left\{\begin{array}{}
                        C_\text{gt} \cdot (d_\text{gt} - d_{\text{gt}, t-1}) & \text{wenn} &  d_\text{gt} > d_{\text{gt}, t-1} \\
                        0 & \text{wenn} &  d_\text{gt} \leq d_{\text{gt}, t-1} \\
	                \end{array}\right. \\
                R_\text{angle, gt} & = & C_\text{angle,gt} \cdot  \alpha_\text{angle,gt} \\
                              R_\text{ori, gt} & = & C_\text{ori,gt} \cdot  \beta  \\
                       \end{array}
                       \right. & \\
        R_2 & = & 
        \end{array} 
    \right.


$$