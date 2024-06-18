$$
\left\{
\begin{array}{lll}
R_{\text{success}} & = 100 & \text{wenn} ~~~~~~~~ S_t = S_\text{success} \\
R_{\text{collision}} & = -100 & \text{wenn} ~~~~~~~~ S_t = S_\text{collision} \\
R_{\text{truncation}} & = 0 & \text{wenn} ~~~~~~~~ S_t = S_\text{truncation} \\
R_4 & = R_{\text{dist,gt}} + R_{\text{angle,gt}} + R_{\text{ori,gt}} &
\left\{
\begin{array}{lll}
R_{\text{dist,gt}} & = C_\text{dist,gt} \cdot (d_\text{gt} - d_{\text{gt}, t - 1}) & \text{wenn} ~~~~~~ d_\text{gt} > d_{\text{gt}, t - 1} \\

\end{array}
\right. \\
R_2 & = 
\left\{
\begin{array}{ll}
\text{d\_hard\_margin} - \text{dot} & \text{// 1} \\
0 \\
\end{array}
\right. \\
R_3 & = R_{\text{angle.ot}} + R_{\text{dist.gt}} \\
R_4 & = R_{\text{dist.gt}} + R_{\text{angle.gt}} + R_{\text{ori.gt}} \\
\end{array}
\right.



$$