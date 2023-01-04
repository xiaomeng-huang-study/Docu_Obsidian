| Begriff                 | Bedeutung                                                 |
| ----------------------- | --------------------------------------------------------- |
| MIMO                    | Multiple Input, multiple Output  $\vec x$                 |
| SISO                    | Single Input, single Output  $x$                          |
| dynamisches System      | speichert Energie                                         |
| invertierbares System   | Eingangssignal kann wiederhergestellt werden              |
| stabiles System         | wird nach Störung in stationär eingehaltenen AP überführt |
| Zeitinvarianz           | Systemparameter / Koeffizienten zeitlich konstant         |
| Linearität              | Teil-ein/aus-gangssignale lassen sich addieren/skalieren  |
| Signal                  | physikalische Repräsentation von Information              |
| stationär / instationär | gleich, harmonisch, periodisch / zeitlich begrenzt        |
| Übertragungsfunktion    | Impulsantwort (G(s))                                      |

| Name                                                | Formel                         |
| --------------------------------------------------- | ------------------------------ |
| Reibbeiwert k                                       | $F_{max} = k·v_{max}^2$        |
| Zeitkonstante T                                     | $T=\dfrac{m·v_{max}}{F_{max}}$ |
| Konzentrationsänderung (kg/s)                       | $V·\dot C=\dot V·C=Q·C$        |
| Zulauf / Durchströmung Q (m^3^/s)                   | $Q=\dot V$                     |
| Drehmoment = Trägheitsmoment · Winkelbeschleunigung | $M=\Theta·\ddot \varphi$       |
| Translation → Rotation                              | $x=r·\varphi$                  |



# 1. Einführung

## 1.1 Systeme und Systemmodelle

| gerader/ungerader Anteil                                     | Periodische Wiederholung                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| $x(t)=x_g(t)+x_u(t)\\x_g(t)=\dfrac12(x(t)+x(-t))\\x_u(t)=\dfrac12(x(t)-x(-t))$ | $\displaystyle y(t)=\sum_{i=-\infty}^\infty x(t-i·\Delta T)$ |

<div style="page-break-after: always; break-after: page;"></div>

# 2. Beschreibung von Signalen und Systemen im Zeitbereich



## 2.1 Signale

| $z=a+j·b=\vert z\vert·e^{j\varphi}$      | $w=e^{j\alpha}=\cos(\alpha)+j·\sin(\alpha)$ | $\sin(\alpha)=\dfrac{e^{j\alpha}-e^{-j\alpha}}{2j}$ |
| ---------------------------------------- | ------------------------------------------- | --------------------------------------------------- |
| $\varphi=\arctan\left(\dfrac{b}a\right)$ |                                             | $\cos(\alpha)=\dfrac{e^{j\alpha}+e^{-j\alpha}}{2}$  |

| Addieren/Subtrahieren                                        | Mutiplizieren/Dividieren                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| $z=z_1+z_2=(a_1+a_2)+j(b_1+b_2)$                             | $z=z_1·z_2=\vert z_1·z_2\vert·e^{j(\varphi_1+\varphi_2)}$    |
| **Drehung**                                                  | $z+z^*=\vert z\vert(e^{j\varphi}+e^{-j\varphi})=2\vert z\vert\cos(\varphi)$ |
| $z·v=\vert z\vert· e^{j\varphi}·e^{j\alpha}=\vert z\vert·e^{j(\varphi+\alpha)}$ | $z·z^*=\vert z\vert·e^{j\varphi}·\vert z\vert e^{-j\varphi}=\vert z\vert^2$ |

| stationär, harmonisch                                        | Exponential-Funktion                                         | Rechteck-Impuls                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $x(t)=\hat x·\cos(\omega t+\varphi_0)$                       | real:  $e^{\sigma t}\qquad$ komplex:  $e^{(\sigma+j\omega)t}+e^{(\sigma-j\omega)t}\\=2·e^{\sigma t}·\cos(\omega t)$ | $rect\left(\dfrac{t}{\Delta T}\right)$                       |
|                                                              | $\sigma<0$	→	stabiles System<br />$\sigma>0$	→	instabiles System | Amplitude:  $\dfrac{1\ sec}{\Delta T}$                       |
| $x(t)=\frac{\hat x}2(e^{j(\omega t+\varphi_0)}+e^{-j(\omega t+\varphi_0)})\\=\dfrac12(\hat xe^{j\varphi_0}\ e^{j\omega t}+\hat xe^{-j\varphi_0}\ e^{-j\omega t})\\=\dfrac12(\tilde x·e^{j\omega t}+\tilde x^*·e^{-j\omega t})$ | ![image-20201102165336483](../../Typora.assets/image-20201102165336483.png) | ![image-20201102165157437](../../Typora.assets/image-20201102165157437.png) |



## 2.2 Systeme

| Widerstand | Spule                                                        | Kondensator                                                  |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
|            | <img src="../../Typora.assets/image-20201016111119717.png" alt="image-20201016111119717" style="zoom: 33%;" /> | <img src="../../Typora.assets/image-20201016111149427.png" alt="image-20201016111149427" style="zoom: 33%;" /> |
| $u_R=i·R$  | $u_L=L·\dot i_L\qquad \tilde u=\tilde i·L·j\omega$           | $i_C=C·\dot u_C\qquad \tilde i=\tilde u·C·j\omega$           |

<div style="page-break-after: always; break-after: page;"></div>

| Allgemeine Herangehensweise                                  | Reihenschwingkreis                                   |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| - Summe mit Ausgangsgröße nach der<br />nicht gesucht ist (I/U) aufstellen<br />- Einzelne Summanden ausschließlich mit Ein-<br />/Ausgangsvariablen und Konstanten darstellen<br />- alles (mithilfe von Integralen) einsetzen und auflösen | - Summe mit Ein-/Ausgangsgröße aufstellen (u)<br />- |



| <img src="../../Typora.assets/image-20210129101446738.png" alt="image-20210129101446738" style="zoom: 25%;" />    <img src="../../Typora.assets/image-20210129110551557.png" alt="image-20210129110551557" style="zoom: 25%;" /> | $u_1=u_R+u_2=CR·\dot u_2+u_2\\~\\u_R=i·R\qquad i=C·\dot u_2$ |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="../../Typora.assets/image-20210129110721126.png" alt="image-20210129110721126" style="zoom: 33%;" /> | $i_1-i_2=i_C\qquad i_C=C·\dot u_2\\~\\i_1=\dfrac{u_1-u_2}{R_1}\qquad i_2=\dfrac{u_2}{R_2}\\~\\\dfrac{u_1}{R_1}-\dfrac{u_2}{R_1}-\dfrac{u_2}{R_2}=C·\dot u_2\\~\\~\\T~\dot u_2+u_2=V~u_1$ |
| <img src="../../Typora.assets/image-20210129112153067.png" alt="image-20210129112153067" style="zoom: 40%;" /> | $i_L=i_C+i_R=C~\dot u_2+\dfrac{u_2}R\\~\\\dot i_L=C~\ddot u_2+\dfrac{\dot u_2}R=\dfrac{u_1-u_2}L\\~\\LC~\ddot u_2+\dfrac LR~\dot u_2+u_2=u_1$ |
| <img src="../../Typora.assets/image-20210129113606323.png" alt="image-20210129113606323" style="zoom: 33%;" /> | $n=C~V\qquad \dot n=\dot C~V=C~Q\\~\\\dot n=\dot n_{in}-\dot n_{out}\\~\\V~\dot C=Q~C_0-Q~C$ |
| <img src="../../Typora.assets/image-20210129115429201.png" alt="image-20210129115429201" style="zoom:50%;" /> | $m·\ddot x=F_{mot}-F_W\\~\\F_W=k·v\\~\\m~\dot v+k~v=F_{mot}$ |

<div style="page-break-after: always; break-after: page;"></div>

| **Amplitudengang**  (Betrag komplex) | $\underline f(\omega)=\dfrac{a+jb}{c+jd}\quad→\quad\vert \underline f(\omega)\vert=\dfrac{\sqrt{a^2+b^2}}{\sqrt{c^2+d^2}}$ | $\vert H(e^{j\omega})\vert= \vert\dfrac1{e^{j\omega}}\vert= \vert\dfrac1{Re+Im}\vert\\ =\dfrac1{\sqrt{Re^2+Im^2}}$ |
| ------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Phasengang**                       | $arg\left(\underline f(\omega)\right)=\arctan\left(\dfrac ba\right)-\arctan\left(\dfrac dc\right)$ | $-\arctan\left(\dfrac{Im}{Re}\right)$                        |

### Beispiele DGL

| Homogen               | Inhomogen           | 2D System                                                    |
| --------------------- | ------------------- | ------------------------------------------------------------ |
| $T\ \dot y+y=0$       | $T\ \dot y+y=V\ x$  | $\begin{align}T\ \dot y_1+y_1&=k_1\ x+k_2\ y_2\\T\ \dot y_2+y_2&=y_1\end{align}$ |
| $y_h=c·e^{-\frac tT}$ | $y_s=V·x(t→\infty)$ | vor  $y_1/y_2$  muss immer Faktor 1 stehen                   |
|                       |                     |                                                              |



### 2.2.5 [Systeme 2. Ordnung](https://www.eit.hs-karlsruhe.de/mesysto/teil-a-zeitkontinuierliche-signale-und-systeme/uebertragungsglieder-der-regelungstechnik/elementare-uebertragungsglieder/proportionalglied.html)

|                              | [Zeitbereich](https://www.eit.hs-karlsruhe.de/mesysto/teil-a-zeitkontinuierliche-signale-und-systeme/systeme-im-laplace-bereich/uebertragungsfunktion-linearer-zeitinvarianter-systeme/impuls-und-sprungantwort.html) |                                            | Frequenzbereich                          |
| ---------------------------- | ------------------------------------------------------------ | ------------------------------------------ | ---------------------------------------- |
| **Impuls**  $\delta(t)$      | [Impulsantwort](https://de.wikipedia.org/wiki/Impulsantwort)  $g(t)$ | $g(t)=\dot h(t)$                           | Übertragungsfkt.  $G(s)=F(s)=\ddot U(s)$ |
| **Sprung**  $\varepsilon(t)$ | [Sprungantwort](https://de.wikipedia.org/wiki/Sprungantwort)  $h(t)$ | $\displaystyle h(t)=\int_0^tg(\tau)~d\tau$ | $H(s)=G(s)·\dfrac1s$                     |

$\dfrac{d\ \varepsilon(t)}{dt}=\delta(t)$			Ableitung Sprungantwort ( · 1sec ) = Impulsantwort

| Name    | Symbol                                                       |                       Funktion                       |        Sprungantwort  $h(t)$        | Übertragungs-<br />funktion  $\ddot U(s)$ |
| ------- | ------------------------------------------------------------ | :--------------------------------------------------: | :---------------------------------: | :---------------------------------------: |
| `I`     | ![image-20201102122809883](../../Typora.assets/image-20201102122809883.png) | $\displaystyle y=\dfrac1{T_i}·\int_0^tx(\tau)~d\tau$ |   $\dfrac{t}{T_i}·\varepsilon(t)$   |              $\dfrac1{T_is}$              |
| `DT1`   | ![image-20210129110935834](../../Typora.assets/image-20210129110935834.png) |                    $y=T_D·\dot x$                    |           $T_D·\delta(t)$           |                  $T_D·s$                  |
| `Delay` | ![image-20201119190124539](../../Typora.assets/image-20201119190124539.png) |                     $y=x(t-T_T)$                     |        $\varepsilon(t-T_T)$         |               $e^{-s·T_T}$                |
| `PT1`   | ![image-20201102124033514](../../Typora.assets/image-20201102124033514.png?lastModify=1611913386) ![image-20201119185412076](../../Typora.assets/image-20201119185412076.png?lastModify=1611913386) |                   $T\ \dot y+y=Vx$                   | $V(1-e^{-\frac tT})·\varepsilon(t)$ |             $\dfrac{V}{Ts+1}$             |

<div style="page-break-after: always; break-after: page;"></div>

### 2.2.6 Schwingfähige Systeme 2. Ordnung (PT~2~)

$\dfrac1{\omega_0^2}~\ddot y+\dfrac{2D}{\omega_0}~\dot y+y=V·x$				<img src="../../Typora.assets/image-20201203115741498.png" alt="image-20201203115741498" style="zoom:40%;" />

| D____________________ | Eigenschaft                 | Eigenwerte                                                   | Beispiel                          |                                                              |
| --------------------- | --------------------------- | ------------------------------------------------------------ | --------------------------------- | ------------------------------------------------------------ |
| **( -∞ ; -1 ]**       | instabil<br />aperiodisch   | $s_{1,2}=-\omega_0D\pm \omega_0\sqrt{D^2-1}$                 | $s_{1,2}=+x~~\xcancel{+j·y}$      | ![image-20201205081809443](../../Typora.assets/image-20201205081809443.png) |
| **( -1 ; 0 ]**        | instabil<br />periodisch    | $s_{1,2}=-\omega_0D\pm j·\omega_0\sqrt{1-D^2}$               | $s_{1,2}=+x\pm j·y$               | ![image-20201205081755456](../../Typora.assets/image-20201205081755456.png) |
| **D = 0**             | grenzstabil<br />periodisch | $s_{1,2}=~\pm j·\omega_0\sqrt{1-D^2}$                        | $s_{1,2}=\xcancel{\pm x}~\pm j·y$ | ![image-20210129122943203](../../Typora.assets/image-20210129122943203.png) |
| **[ 0 ; 1 )**         | stabil<br />periodisch      | $s_{1,2}=-\omega_0D\pm j·\omega_0\sqrt{1-D^2}$               | $s_{1,2}=-x\pm j·y$               | ![image-20201205081844258](../../Typora.assets/image-20201205081844258.png) |
| **[ 1 ; ∞ )**         | stabil<br />aperiodisch     | $s_{1,2}=-\omega_0D\pm\omega_0\sqrt{D^2-1}=\dfrac1{T_{1,2}}$ | $s_{1,2}=-x~~\xcancel{+j·y}$      | ![image-20201205081558577](../../Typora.assets/image-20201205081558577.png) |

|           | Resonanzfrequenz    $\text{Im}\overset!=0~→~\omega_0$       | Dämpfung                                                   |
| --------- | ----------------------------------------------------------- | ---------------------------------------------------------- |
|           | $a\ddot x+b\dot x+cx=0\quad→\quad\omega_0=\sqrt{\dfrac ca}$ | $a\ddot x+b\dot x+cx=0\quad→\quad D=\dfrac{b}{2\sqrt{ac}}$ |
| **1 < D** | $T_1·T_2=\dfrac1{\omega_o^2}$                               | $T_1+T_2=\dfrac{2D}{\omega_0}$                             |



### 2.2.8 [Nichtlineare Systeme](https://www.youtube.com/watch?v=5gEattuH3tI)

| Beliebige Funktion                                           | Beispiel Funktion                                            | Multiplikation                                               |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20201109213347722](../../Typora.assets/image-20201109213347722.png) | ![image-20201115075158782](../../Typora.assets/image-20201115075158782.png) | ![image-20201217112347501](../../Typora.assets/image-20201217112347501.png) |
| $y=f(x)$                                                     | $y=\sqrt x$                                                  | $z=x·y$                                                      |
|                                                              | **Linearisierung:**                                          | $\Delta z=x_0~\Delta y+y_0~\Delta x$                         |



<div style="page-break-after: always; break-after: page;"></div>

## 3. Spektrale Eigenschaften von Systemen und Signalen

|                                                              |                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20200505145609699](../../Typora.assets/image-20200505145609699.png?lastModify=1610037915) | $\sin(\omega t)=\cos(\omega t-90°)\\~\\x(t)=\cos(2t)+2\sin(t)\\~\\ \sqrt5\cos(\omega t-63°)=\sqrt5\sin(\omega t+27°)\\~\\1-2j=\sqrt5/\underline{-63°}$ | $arg(z)=\varphi=\bigg\{\begin{matrix}\arctan(\frac yx)&x>0\\\pm90°&x=0\\\arctan(\frac yx)\pm180°&x<0\end{matrix}\\~\\~\\\cos(t)=\frac 12(e^{jt}+e^{-jt})\\\sin(t)=\frac 1{2j}(e^{jt}-e^{-jt})$ |



## 3.1 Stationäre Signale: Fourier-Reihe

| Fourrier-Reihe                                               | Gleichanteil                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| $\displaystyle y(t)=y_0+\sum_{k=1}^\infty\big(a_k·\cos(k\omega_0~t)+b_k·\sin(k\omega_0~t)\big)$ | $\displaystyle y_0=\dfrac1T\int_0^Ty(t)\text{ dt}$           |
| **cos-Anteil**                                               | **sin-Anteil**                                               |
| $\displaystyle a_k=\dfrac2T\int_0^Ty(t)·\cos(k\omega_0~t)\text{ dt}$ | $\displaystyle b_k=\dfrac2T\int_0^Ty(t)·\sin(k\omega_0~t)\text{ dt}$ |
| **Dirac-Puls-Reihe**                                         | **Fourrier-Koeffizient**                                     |
| $\displaystyle x(t)=1V·\sum_{k=-\infty}^\infty\delta(t-kT)$  | $\displaystyle \tilde x_k=\dfrac{2V~sec}T$                   |

| Fourrier-Reihe komplex                                       | komplexe Fourrier-Koeffizienten                              | Betragsspektrum       |
| ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------- |
| $\displaystyle x(t)=x_0+\dfrac12\sum_{k=-\infty\\k\ne0}^\infty \tilde x_k·e^{jk\omega_0t}$ | $\displaystyle \tilde x_k=\dfrac2T\int_T x(t)·e^{-jk\omega_0t}\text{ dt}=a_k-jb_k\\=\dfrac2T\int_T x(t)·\big(\cos(k\omega_0t)-j\sin(k\omega_0t) \big)\text{ dt}$ | $\tilde x_k=a_k-jb_k$ |

## 3.2 Instationäre Signale

| Transformation                   | FT                                                           | Inverse FT                                                   |
| -------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $y(t)\quad○—\!●\quad Y(j\omega)$ | $\displaystyle Y(j\omega)=\int_{-\infty}^{\infty}y(t)·e^{-j\omega t}\text{ dt}$ | $\displaystyle y(t)=\dfrac1{2\pi}\int_{-\infty}^\infty Y(j\omega)·e^{j\omega t}\text{ d}\omega$ |

| Rechteck                                                     | Transformierte                |
| ------------------------------------------------------------ | ----------------------------- |
| <img src="../../Typora.assets/image-20201205090438248.png" alt="image-20201205090438248" style="zoom:33%;" /> | $Y(j\omega)=F·si(\omega t_1)$ |

<div style="page-break-after: always; break-after: page;"></div>

|                                   |                    Transformations-Regel                     | Gegenstück                                                   |
| --------------------------------- | :----------------------------------------------------------: | ------------------------------------------------------------ |
| **Fourrier**                      |               $x(t)\quad○—\!●\quad X(j\omega)$               |                                                              |
| **Summe / Faktor**                |  $x_1(t)+x_2(t)\quad ○—\!●\quad X_1(j\omega)+X_2(j\omega)$   | $a·x(t)\quad ○—\!●\quad a·X(j\omega)$                        |
| **Verschiebung / Dämpfung**       |   $x(t-t_0)\quad ○—\!●\quad e^{-j\omega t_0}\ X(j\omega)$    | $X(j\omega-j\omega_0)\quad●—\!○\quad e^{j\omega_0t}\ x(t)$   |
| **Skalierung / Spiegelung**       | $x(at)\quad○—\!●\quad \dfrac1{\vert a\vert}\ X(j\frac\omega a)$ | $x(-t)\quad ○—\!●\quad X(-j\omega)=X(j\omega)^*$             |
| **Differentiation / Integration** |        $\dot x(t)\quad ○—\!●\quad j\omega·X(j\omega)$        | $\int x(t)~dt\quad ●—\!○\quad \dfrac1{j\omega}X(j\omega)$    |
| **Funktions-Paare**               |      $\varepsilon(t) \quad ○—\!●\quad \dfrac1{j\omega}$      | $t·\varepsilon(t) \quad ○—\!●\quad \dfrac1{(j\omega)^2}$     |
|                                   | $e^{-at}·\varepsilon(t),\quad _{a\gt0}\quad ○—\!●\quad \dfrac1{a+j\omega}$ | $t\ e^{-t}·\varepsilon(t) \quad ○—\!●\quad \dfrac1{(1+j\omega)^2}$ |
| **Delta / Rechteck**              | $\delta(t)\quad ○—\!●\quad 1~sec\\1\quad○—\!●\quad2\pi\ \delta(\omega)$ | $rect(\frac tT)\quad○—\!●\quad T\ si(\frac{\omega T}2)$      |
|                                   | $rect(\frac t{\Delta T})\quad○—\!●\quad 1sec·si(\pi f\Delta T)$ | $si(2\pi f_ct)\quad○—\!●\quad rect(\frac{f}{2f_c})$          |
|                                   | $2\cos(\omega_0t)\quad○—\!●\quad\delta\ (\omega-\omega_0)+\delta\ (\omega+\omega_0)$ | $2\sin(\omega_0t)\quad○—\!●\quad-j\delta\ (\omega-\omega_0)\\\qquad\qquad\qquad\quad+j\delta\ (\omega+\omega_0)$ |
| **Extra**                         | $Ш_T(t)\quad○—\!●\quad\dfrac{2\pi}TШ_{\frac{2\pi}T}(\omega)$ | $X(t)\ \big/\ \big(X(jt)\big)\quad ○—\!●\quad 2\pi\ x(-\omega)$ |
| **Faltungssatz**                  | $x(t)\circledast h(t)~~○—\!●~~ \int_{-\infty}^\infty x(\tau)h(t-\tau)\ d\tau$ | $x(t)h(t)~~○—\!●~~ \frac1{2\pi}\ X(j\omega)\circledast H(j\omega)$ |



#### 3.2.3 Laplace-Transformation

|                    | normal                                                    | invers                                                       |
| ------------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| $s=\sigma+j\omega$ | $\displaystyle Y(s)=\int_0^\infty y(t)·e^{-st}\text{ dt}$ | <img src="../../Typora.assets/image-20201205093748705.png" alt="image-20201205093748705" style="zoom: 50%;" /> |

| e-Funktion                                  | Sprungfunktion                          | Dirac-Impuls                     |
| ------------------------------------------- | --------------------------------------- | -------------------------------- |
| $K·e^{-t/T}\quad○—\!●\quad\dfrac{K}{s+1/T}$ | $\varepsilon(t)\quad○—\!●\quad\dfrac1s$ | $\delta(t)\quad○—\!●\quad 1~sec$ |

<div style="page-break-after: always; break-after: page;"></div>

## 3.3 Frequenzgang

| Frequenzgang                                                 | Betrag                                                   | Phase                                                        |                                                              |                                                              |
| ------------------------------------------------------------ | -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $F(j\omega)=\dfrac{\tilde y}{\tilde x}=\dfrac{Y(j\omega)}{X(j\omega)}$<br /><br />Verhältnis komplexer Zeiger | $\vert F(j\omega)\vert$<br /><br />Amplituden-Verhältnis | $\varphi=\underline{\big/ F(j\omega)}$<br /><br />Phasenver-schiebung | ![image-20201208120114851](../../Typora.assets/image-20201208120114851.png) | <img src="../../Typora.assets/image-20201208115530847.png" alt="image-20201208115530847" style="zoom: 50%;" /> |

<img src="../../Typora.assets/image-20201208120614408.png" alt="image-20201208120614408" style="zoom: 33%;" />			$x(t)\circledast h(t)\dfrac1{sec}=y(t)\qquad○—\!●\qquad X(j\omega)·H(j\omega)\dfrac1{sec}=Y(j\omega)\\~\\F(j\omega)=\dfrac1{sec}H(j\omega)=\dfrac{Y(j\omega)}{X(j\omega)}$

<img src="../../Typora.assets/image-20210115093831895.png" alt="image-20210115093831895" style="zoom:50%;" /> 

| Dreieck-Signal      | $\Lambda(t)=rect\left(\dfrac{t}{\Delta T/2}\right)\circledast rect\left(\dfrac{t}{\Delta T/2}\right)\dfrac{\Delta T}{2~sec^2}\quad○—\!●\quad\Lambda(j\omega)=\dfrac{\Delta T}2·si^2\left(\pi f\dfrac{\Delta T}2 \right)$ |
| :------------------ | :----------------------------------------------------------: |
| **Dirac-Puls**      | $y(t)=x(t)\circledast\delta(t-t_0)=x(t-t_0)·1sec\qquad○—\!●\qquad Y(j\omega)=X(j\omega)·e^{j\omega t_0}$ |
| **Dirac-Kamm**      | $Ш_{\Delta T}\quad○—\!●\quad\dfrac{1sec}{\Delta T}·Ш_{\frac1{\Delta T}}(j\omega)$ |
| **Multi-plikation** | $f_1(t)·f_2(t)\quad○—\!●\quad\dfrac1{2\pi}~F_1(\omega)\circledast F_2(\omega)$ |

<div style="page-break-after: always; break-after: page;"></div>

## 3.4 Übertragungsfunktion

| RC-Glied                                                     | PT~2~-Glied                                                  |      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| <img src="../../Typora.assets/image-20201208123903311.png" alt="image-20201208123903311" style="zoom:33%;" /> |                                                              |      |
| $T=RC\qquad F(S)=\dfrac{Ts}{Ts+1}$                           | $F(s)=\dfrac{V}{\frac1{\omega_0^2}s^2+\frac{2D}{\omega_0}s+1}$ |      |



| Bezeichnung        | Skizze                                                       | Formel                                       |
| ------------------ | ------------------------------------------------------------ | -------------------------------------------- |
| Einzeln            | <img src="../../Typora.assets/image-20201208124506123.png" alt="image-20201208124506123" style="zoom: 40%;" /> | $X(s)·F(s)=Y(s)$                             |
| Reihen-Schaltung   | ![image-20201208124626566](../../Typora.assets/image-20201208124626566.png) | $F(s)=F_1(s)·F_2(s)$                         |
| Parallel-Schaltung | <img src="../../Typora.assets/image-20201208124728478.png" alt="image-20201208124728478" style="zoom: 33%;" /> | $F(s)=F_1(s)+F_2(s)$                         |
| Gegenkopplung      | <img src="../../Typora.assets/image-20201208124919975.png" alt="image-20201208124919975" style="zoom:33%;" /> | $F_{geg}(s)=\dfrac{F_V(s)}{1+F_V(s)·F_R(s)}$ |
| Mitkopplung        | <img src="../../Typora.assets/image-20201208125110578.png" alt="image-20201208125110578" style="zoom:33%;" /> | $F_{mit}(s)=\dfrac{F_V(s)}{1-F_V(s)·F_R(s)}$ |

<div style="page-break-after: always; break-after: page;"></div>

## 3.5 Methoden zur Visualisierung von Systemeigenschaften



## 4.3 Diskrete Systeme

| Stetig      | $x(t),~y(t)$ | $dy$          | $dt$       |
| ----------- | ------------ | ------------- | ---------- |
| **Diskret** | $x[n],~y[n]$ | $y[n]-y[n-1]$ | $\Delta T$ |





# F E H L E R



### DGL aufstellen

- Grundform wie in Mathe: nicht  $\dot v=F-v$  sondern  $\dot v+v=F$  (alle Variablen auf eine Seite)



### Signalflussdiagramm Zeichnen

- DGL nach höchster Ableitung umstellen und wenn möglich ausklammern:  $m·\ddot x+c·x=c·y\quad\Rightarrow\quad m·\ddot x=c·(y-x)$



### System Beispiele

- Rührkessel:  V ist immer konstant → somit sind Q~in~ und Q~out~ immer gleich



