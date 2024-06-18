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
R_\text{direction\_toggle} = 
\left\{
\begin{array}{ll}
C_\text{direction\_toggle} & \text{ Wenn sich die Fahrtrichtung ändert} \\
0 & \text{sonst.} \\
\end{array}
\right.
$$

$$
R_t = 
\left\{
\begin{array}{lll}
R_\text{success} & = 100 - \beta & \text{wenn} ~~~~~~ S_t = S_\text{success} \\
R_\text{collision} & = -100 & \text{wenn} ~~~~~~ S_t = S_\text{collision} \\
R_\text{truncation} & = 0 & \text{wenn} ~~~~~~ S_t = S_\text{truncation} \\
R_1 + R_\text{direction\_toggle} & = R_\text{dist,gt} + R_\text{angle,gt} + R_\text{ori,gt} & + R_\text{direction\_toggle} \\
R_2 + R_\text{direction\_toggle} & = R_{dist,ot} & + R_\text{direction\_toggle} \\
R_3 + R_\text{direction\_toggle} & = R_\text{angle,ot} + R_\text{dist,gt} & + R_\text{direction\_toggle} \\
R_4 + R_\text{direction\_toggle} & = R_\text{dist,gt} + R_\text{angle,gt} + R_{ori,gt} & + R_\text{direction\_toggle} \\
\end{array}
\right.
$$

$$
S_{t} =
\left\{
\begin{array}{lll}
d_\text{gt} ~\leq~ 1m ~~ \text{und} ~~ \beta ~\leq~ 9^\circ &  \Rightarrow S_\text{success} & \\ 
\text{Berührung mit dem Hindernis} &  \Rightarrow S_\text{collision} & \\
\text{Überschreitung der zulässigen Dauer}  &  \Rightarrow S_\text{truncation} & \\
0 < d_{\text{ot}} \leq d_\text{soft\_margin} &
\left\{
\begin{array}{ll}
d_{\text{ot}}^2 + d_\text{gt}^2 > d_\text{go}^2 & \Rightarrow S_1 \\
d_{\text{ot}}^2 + d_\text{gt}^2 \leq d_\text{go}^2 & 
\left\{
\begin{array}{lr}
d_{\text{ot}} \leq d_\text{hard\_margin} & \Rightarrow S2 \\
d_{\text{ot}} > d_\text{hard\_margin} & \Rightarrow S3 \\
\end{array}
\right.
\end{array}
\right. \\
d_\text{soft\_margin} < d_{\text{ot}} & \Rightarrow S_4
\end{array}  
\right.
$$