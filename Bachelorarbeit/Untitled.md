$$
R_\text{dist,gt} = 
\left\{
\begin{array}{lll}
C_\text{dist,gt} \cdot (d_\text{gt} - d_{\text{gt},t-1}) & \text{wenn} & d_\text{gt} > d_{\text{gt},t-1}\\
0 & \text{sonst.} 
\end{array}
\right.
$$

$$
R_{\text{angle,gt}} = C_\text{angle,gt} \cdot \alpha_\text{gt}
$$

$$
R_\text{ori,gt} = C_\text{ori,gt} \cdot \beta
$$

$$
R_\text{dist, ot} = 
\left\{
\begin{array}{lll}
C_\text{dist,ot} - \left\lfloor \frac{d_\text{ot}}{1} \right\rfloor & \text{wenn} & d_\text{ot} < d_{\text{ot}, t-1} \\
0 & \text{sonst.} & \\
\end{array}
\right.
$$

$$
R_\text{angle,ot} = C_\text{angle,ot} \cdot (\alpha_{angle,ot} - 90^{\circ})
$$

$$
R_t = 
\left\{
\begin{array}{lll}
R_\text{success} & = 100 - \beta & \text{wenn} ~~~~~~ S_t = S_\text{success} \\
R_\text{collision} & = -100 & \text{wenn} ~~~~~~ S_t = S_\text{collision} \\
R_\text{truncation} & = 0 & \text{wenn} ~~~~~~ S_t = S_\text{truncation} \\
R_1 & = R_\text{dist,gt} + R_\text{angle,gt} + R_\text{ori,gt} & \\
R_2 & = R_{dist,ot} & & \\
R_3 & = R_\text{angle,ot} + R_\text{dist,gt} & \\
R_4 & = R_\text{dist,gt} + R_\text{angle,gt} + R_{ori,gt} & \\
\end{array}
\right.
$$