$$
\left\{
\begin{array}{lll}
R_{\text{success}} & = 100 & \text{wenn} ~~~~~~~~ S_t = S_\text{success} \\
R_{\text{collision}} & = -100 & \text{wenn} ~~~~~~~~ S_t = S_\text{collision} \\
R_{\text{truncation}} & = 0 & \text{wenn} ~~~~~~~~ S_t = S_\text{truncation} \\
R_4 & = R_{\text{dist,gt}} + R_{\text{angle,gt}} + R_{\text{ori,gt}} &
\left\{
\begin{array}{lll}
R_{\text{dist,gt}} & = C_\text{dist,gt} \cdot (d_\text{gt} - d_{\text{gt}, t - 1}) & \text{wenn} ~~~~~~~~ d_\text{gt} > d_{\text{gt}, t - 1} \\
R_{\text{angle,gt}} & = C_\text{angle,gt} \cdot \alpha_\text{gt} & \\
R_\text{ori,gt} & = C_\text{ori,gt} \cdot \beta & \\
\end{array}
\right. \\
R_2 & = 
\left\{
\begin{array}{ll}
d_{\text{hard\_margin}} - \left\lfloor \frac{d_\text{ot}}{1} \right\rfloor & \text{wenn} ~~~~~~~~ d_\text{ot} < d_{\text{ot}, t-1} \\
0 & \text{wenn} ~~~~~~~~ d_\text{ot} \geq d_{\text{ot}, t-1} \\
\end{array}
\right. \\
R_3 & = R_{\text{angle,ot}} + R_{\text{dist,gt}}
\left\{
\begin{array}{ll}
R_{\text{angle,ot}} & = C_\text{angle,ot} \cdot (\alpha_\text{angle,ot} - 90^{\circ}) \\
R_{\text{dist,gt}} & = C_\text{dist,gt} \cdot (d_\text{gt} - d_{\text{gt}, t-1}) & ~~~~~~~~ \text{wenn} d_\text{gt} > d_{\text{gt},t-1} \\

\end{array}
\right. \\
R_4 & = R_{\text{dist.gt}} + R_{\text{angle.gt}} + R_{\text{ori.gt}} \\
\end{array}
\right.
$$

$$
R_\text{dist,gt} = 
\left\{
\begin{array}{lll}
C_\text{dist,gt} \cdot (d_\text{gt} - d_{\text{gt},t-1}) & \text{wenn} & d_\text{gt} > d_{\text{gt},t-1}\\
0 & \text{sonst.} 
\end{array}
\right.
$$