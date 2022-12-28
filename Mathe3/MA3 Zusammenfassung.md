[TOC]



<div style="page-break-after: always;"></div>

# ——————  A N W E N D U N G  ——————



# 1. Quellencodierung / Datenkomprimierung



## Häufigkeits-Codierung



## Huffman-Codierung

| Zeichen        | A    | B    | ...  | $Z_1$ | $Z_2$ | $Z_i$ |
| -------------- | ---- | ---- | ---- | ----- | ----- | ----- |
| **Wkt**        | 0.5  | 0.3  | ...  | $p_1$ | $p_2$ | $p_i$ |
| **Anzahl Bit** | 1    | 2    |      | $n_1$ | $n_2$ | $n_i$ |

| Mittlere Wortlänge                  | Entropie                                    |
| ----------------------------------- | ------------------------------------------- |
| $\displaystyle mWl=\sum_i\ n_i·p_i$ | $\displaystyle H=\sum_i-p_i·\text{ld}(p_i)$ |



## Burrows-Wheeler Transformation

| alphabetisch sortiert  /  Rosetta-Vektor                     | Beschreibung / Anleitung                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="../../Typora.assets/image-20201205075823707.png" alt="image-20201205075823707" style="zoom: 35%;" /> | 1. von Einsprungstelle aus wird linkes 'E' betrachtet<br />2. linkes 'E' ist 2. 'E' von oben → 2. 'E' rechts suchen    → **E**<br />3. von gefundenem rechten 'E' gerade nach links<br />4. 'L' wird auf rechter Seite gesucht    **→ L**<br />5. von gefundenem rechten 'L' gerade nach links<br />6. Links: 3. 'E' von Oben → 3. 'E' rechts wird gesucht    → **E**<br />7. horizontal nach links  ...       → Codewort: **E L E ...** |



## Move to Front Algrithmus





# 2. Markoffquellen





# 3. [Warteschlangen](https://www.youtube.com/watch?v=X7w5A1QFpG8) ([Website](https://www.bwl-lexikon.de/wiki/warteschlangentheorie/#berechnung-der-durchlaufzeit))



Anzahl Bedienstationen:	$n$			Ankunftsrate:	$\lambda$			Bearbeitungsrate:	$\mu$

Anzahl in Warteschlange:	$X$			Auslastungsgrad:	$\rho=\dfrac\lambda\mu$



|                                   | Begrenzt                                                     | Unbegrenzt                                                   |
| --------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Modell**                        | ![image-20201008124105075](../../Typora.assets/image-20201008124105075.png) | ![image-20201008123146473](../../Typora.assets/image-20201008123146473.png) |
| **stationäre Wkt**                | nur ein λ / µ:           mehrere λ~i~ / µ~i~:<br />$p_0=1-\rho\qquad\quad p_0=\dfrac1{1+\rho_1+\rho_1\rho_2~..} \\p_i=\rho^i·p_0\qquad\quad p_i=\rho_i·p_{i-1}\qquad\qquad$ | $1=p_0+p_1+p_2+…\\$<br />Mit geometrischer Reihe nach  $p_0$  auflösen |
| **Durchlauf-Zeit**                | $t=\frac1{p_0+p_1+\ ..}[t_0·p_0+t_1·p_1+\ ..]$               | $t=\sum_it_i·p_i$                                            |
| **Wkt, dass Warteschl. voll ist** | $p_{i,max}$                                                  | ————                                                         |
| **Erwartungswert**                | $E[X]=\dfrac1{\frac\mu\lambda-1}\quad=P_0·0+P_1·1+\ ..$      |                                                              |

n: Anzahl Bedienstationen	$\tau=\frac1\mu$: Bearbeitungszeit pro Bedienstation	x: Position in Warteschlange

| Auslastungsgrad         | Erwartungswert                                     | Wartezeit                                                    |
| ----------------------- | -------------------------------------------------- | ------------------------------------------------------------ |
| $\rho=\dfrac\lambda\mu$ | $E[X]=\dfrac1{\frac\mu\lambda-1}=P_0·0+P_1·1+\ ..$ | $t=\bigg\lfloor\dfrac{x}{n}\bigg\rfloor·\tau+\dfrac{x\mod n}{n+1}·\tau$ |

![image-20221029225505424](../../Typora.assets/image-20221029225505424.png)

 <div style="page-break-after: always;"></div>

# 4. Kongruenzen

## 4.1 [Euklidischer Algorithmus](https://www.youtube.com/watch?v=jZC7QqufD_0)



## 4.2 Lineare Kongruenz

$13x\equiv 5\mod 62\qquad\qquad ax\equiv b\mod m$  lösbar, wenn  $ggT(a,m)\mid b$

$\boxed{ggT(62,13)=\bold1}\mid5$

| a) ggT                                                       | b) Substitution                                              | c) Einsetzen                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $\begin{align}62&=4·13+\bold{10}\\13&=1·10+\bold3\\10&=3·3+\boxed{\bold1}\end{align}$ | $\begin{align}\bold1&=10-3·\bold3=10-3·(13-1·10)\\&=-3·13+4·\bold{10}=-3·13+4·(62-4·13)\\&=-19·13+4·62\quad\boxed{\equiv-19·13\mod62}\end{align}$ | $13·(-19)\equiv1\mod 62\\13·(-95)\equiv5\mod62\\ \boxed{x\equiv-95\equiv29\mod62}$ |



## 4.3  [Hashtabellen](https://www.youtube.com/watch?v=KyUTuwz_b7Q)

==fehlt==

## 4.4 Schnelle Potenzierung

==fehlt==

## 4.6 Fehlererkennung

==fehlt==



## 4.8 Kongruenzgenerator

Gegeben:	a, b, m, x(0)  *(zufälliger Startwert)*				$x_{n+1}\equiv a·x_n+b\mod m$

​	

## 4.9 Erzeugung von (Pseudo-)Primzahlen

| [**Rabin**](https://www.youtube.com/watch?v=qdylJqXCDGs) | Gegeben                                                      | Beschreibung                                                 |
| -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Eulersche Funktion**                                   | Menge aller Zahlen  $x$, deren  $ggT(x,n)=1$<br />Anzahl der Zahlen in Menge:  $\varphi(n)=\vert\Z_n'\vert\\$<br />$x\in\Z_n'\quad→\quad x^{\varphi(n)}\equiv1\mod n\qquad\qquad\\x\in\Z_p'\quad→\quad x^{p-1}\equiv1\mod p$ | ![image-20201204102143359](../../Typora.assets/image-20201204102143359.png) |
| **Fermat**                                               | geg.:   n (Primzahl),  a (Zeuge)                             | $a^{n-1}\mod n\ \bigg\{\begin{matrix}=1&\text{vrmtl. Primzahl}\\\ne1&\text{keine Primzahl}\end{matrix}$ |

$x^a\equiv1\mod b$	→	$x$  hat  $a.$  Ordnung Modulo  $b$ 

<div style="page-break-after: always;"></div>

# 5. Algorithmus konjugierter Gradient

[<img src="../../Typora.assets/image-20201027094840536.png" alt="image-20201027094840536" style="zoom:40%;" />](https://www.youtube.com/watch?v=H0NEInc6DB0)

| positiv definit   | negativ definit   | indefinit               | positiv semidefinit            |
| ----------------- | ----------------- | ----------------------- | ------------------------------ |
| $\lambda_{1,2}>0$ | $\lambda_{1,2}<0$ | $\lambda_1<0<\lambda_2$ | $\lambda_1>0\quad \lambda_2=0$ |

<img src="../../Typora.assets/image-20201030091804343.png" alt="image-20201030091804343" style="zoom: 50%;" />



## 5.2 Skalarprodukt / 5.3 LGS lösen

| Skalarprodukt                                                | [Orthogonalbasis (Gram-Schmidt)](https://www.youtube.com/watch?v=l6pr1W3MQoE&t=137s) |
| ------------------------------------------------------------ | :----------------------------------------------------------: |
| $\langle \vec x,\vec y\rangle_{\bold A}=\vec x·[\bold A\vec y]\\~$<br />**A**  ist symm. + pos. definit | $U=\{\vec v_1,\ \vec v_2,\ \vec v_3\}\qquad\vec b_1=\vec v_1\qquad\vec b_2=\vec v_2-\frac{\langle\vec v_2,\vec b_1\rangle}{\langle\vec b_1,\vec b_1\rangle}·\vec b_1\\\vec b_3=\vec v_3-\frac{\langle\vec v_3,\vec b_1\rangle}{\langle\vec b_1,\vec b_1\rangle}·\vec b_1-\frac{\langle\vec v_3,\vec b_2\rangle}{\langle\vec b_2,\vec b_2\rangle}·\vec b_2\\$ |
| **$\vec x,~\vec y$  konjugiert**                             | **LGS lösen**  $\bold{A}~\vec x=\vec b\qquad \bold{A}~\vec x_p\approx \vec b\qquad\vec x_p\in U$ |
| $\langle \vec x,\vec y\rangle_{\bold A}=\vec x·[\bold A\vec y]=\bold 0$ | $\vec x_p=\dfrac{\vec b·\vec b_1}{\vec b_1~[\bold A\vec b_1]}·\vec b_1+\dfrac{\vec b·\vec b_2}{\vec b_2~[\bold A\vec b_2]}·\vec b_2+~...$ |



## 5.3 Anwendung auf LGS (alter Stoff, ab WS22 nicht mehr in Klausur)

<u>Gegeben:</u>	$\bold A·\vec x=\vec b\quad,\qquad\vec x_0$

<u>Vorbereitung:</u>	$\vec p_0=\bold A·\vec x_0-\vec b\qquad=\vec r_0$	(Fehler)			$\bold{A}~\vec p_0$  (Nebenrechnung für später)

<u>1. Iteration:</u>

| a) Alpha bestimmen                                           | b) Neuer Vektor richtung Lsg          | c) Entfernung zu Lsg              | d) Gram Schmi==<u>d</u>==t                                   |
| ------------------------------------------------------------ | ------------------------------------- | --------------------------------- | ------------------------------------------------------------ |
| $\alpha_1=\dfrac{\vec b·\vec p_0}{\vec p_0·[\bold A\vec p_0]}$ | $\vec x_1=\vec x_0+\alpha_1·\vec p_0$ | $\vec r_1=\bold A\vec x_1-\vec b$ | $\vec p_1=\vec  r_1-\dfrac{\vec r_1·[\bold A\vec p_0]}{\vec p_0·[\bold A\vec p_0]}·\vec p_0$ |

| Aufhören, sobald  |  Ergebnis  |           Optimale Lösung in Richtung  $\vec p_0$            |
| :---------------: | :--------: | :----------------------------------------------------------: |
| $\vec r_i=\vec 0$ | $\vec x_i$ | $Lösung=\dfrac{\vec b·\vec p_0}{\vec p_0·[\bold A\vec p_0]}·\vec p_0$ |



## 5.4 Bezug zur quadratischen Optimierung

Matrix A:	positiv definit			→ Tiefpunkt gesucht

---

$$
V=\dfrac12(ax^2+2bxy+cy^2)+dx+ey+f=\dfrac12(x,y)^T\begin{pmatrix}a&b\\b&c\end{pmatrix}\begin{pmatrix}x\\y\end{pmatrix}+dx+ey+f
\\~\\~\\\vec x_1=\vec x_0-\alpha\text{ grad}(V)\qquad\qquad\text{ grad}(V)=\begin{pmatrix}ax+by+d\\bx+cy+e\end{pmatrix}=\begin{pmatrix}a&b\\b&c\end{pmatrix}\begin{pmatrix}x\\y\end{pmatrix}+\begin{pmatrix}d\\e\end{pmatrix}\overset!=\vec0
$$

---





# 6. [Lineare Optimierung](https://www.matopt.de/werkzeuge/lineare-optimierung/simplexalgorithmus.html) (S)

x:	Anzahl Produkt 1			y:	Anzahl Produkt 2



## 6.2 Graphische Lösung

## 6.3 Rechnerische Lösung

==FEHLT==			Zielfunktion hat immer anderes Vorzeichen, als in Tabelle



## 6.5 Sonderfälle

| Minimierung                                                  | Größer gleich                                         | Gleich | keine x ≥ 0 -Bedingung                                       |
| ------------------------------------------------------------ | ----------------------------------------------------- | ------ | ------------------------------------------------------------ |
| Zielfunktion negieren, bei Endergebnis dann wieder Vorzeichen ändern | positive Überschuss-Variable wird eingeführt (z.B. t) | nichts | Bspw. x wird mit zwei positiven Variablen x' und t ausgedrückt und überall (x'-t) ersetzt |
| $\quad Z=~...~\overset!=min\\-Z=\bold{-}~...~\overset!=max$  | $x-y\ge 2\\x-y-t\le2$                                 | machen | $x=x'-t\qquad y=y'-t\\\ →\quad x',y',t\ge0$                  |

→ Einsetzen in Zielfunktion?	$Z=~...~-M·\underbrace{(2-x+y+t)}_{z_1}$	(bei größer gleich und gleich)

## 6.6 Tschebyscheff (Beiblatt)

<div style="page-break-after: always;"></div>

# 7. Dynamische Optimierung (D)

|      | search based                     | sampling based                   |
| ---- | -------------------------------- | -------------------------------- |
| bsp  | A*                               | RRT                              |
|      | Pixel Grid (gerad 10, schräg 14) | random punkte in restlichem feld |
|      | Dijkstra, Floyd-Warshall         |                                  |



## 7.1 Entfernungsproblem Dijkstra



## 7.2 [Entfernungsproblem Floyd-Warschall](https://youtu.be/oNI0rf2P9gE)

| Graph                                                        | Keine Umwege                                                 | Umwege über 1                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20210108115400460](../../Typora.assets/image-20210108115400460.png) | $\begin{array}{c|cccc}D^0&1&2&3&4\\\hline1&0&3&\infty&7\\2&8&0&2&\infty\\ 3&5&\infty&0&1\\4&2&\infty&\infty&0\end{array}$ | $\begin{array}{c|cccc}D^1&1&2&3&4\\\hline1&0&3&\infty&7\\2&8&0&&\\ 3&5&&0&\\4&2&&&0\end{array}$ |
|                                                              | $D^2(1,3)=min\{D^1(1,3),~D^1(1,2)+D^1(2,3)\}$                | Zeile und Spalte **1** bleiben stehen                        |



## 7.3 Vergleich von Strings

<div style="page-break-after: always;"></div>

## 7.4 [Faltungscodes](https://www.youtube.com/watch?v=kRIfpmiMCpU) 

<img src="../../Typora.assets/image-20201117104710395.png" alt="image-20201117104710395" width=45% />		<img src="../../Typora.assets/Inkedimage-20201117090025730_beschriftet_LI.jpg" alt="Inkedimage-20201117090025730_beschriftet_LI" width=25% />	  <img src="../../Typora.assets/image-20201117111809674.png" alt="image-20201117111809674" width=22% />

|        x[n]         |                S₁[n]    S₂[n]                |                      S₁[n+1]    S₂[n+1]                      |                        y₁[n]    y₂[n]                        |
| :-----------------: | :------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        Input        | Flip-Flop-Status<br />(<u>**Beispiele**</u>) | 1 späterer FF-Status<br />S₁[n+1] = x[n]<br />S₂[n+1] = S₁[n] | Output (XOR-Verknüpfung '⊕')<br />y₁[n] = x[n] ⊕ S₁[n] ⊕ S₂[n]<br />y₂[n] = x[n]               ⊕ S₂[n] |
| <u>**0**</u><br />1 |                <u>**0**</u> 0                |                   <u>**0 0**</u><br />1 0                    |                         0 0<br />1 1                         |
| 0<br /><u>**1**</u> |                <u>**1**</u> 0                |                   0 1<br /><u>**1 1**</u>                    |                         1 1<br />0 0                         |
|      0<br />1       |                     0 1                      |                         0 0<br />1 0                         |                         1 0<br />0 1                         |
|      0<br />1       |                     1 1                      |                         0 1<br />11                          |                         0 0<br />1 1                         |



| Generator-Polynom                               | 1. GP                                         | 2. GP                                            |
| :---------------------------------------------- | --------------------------------------------- | ------------------------------------------------ |
| Grad der Generator-Polynome = Anzahl Flip-Flops | g~1~(z) = 1 + z + z^3^ <br />g~1~ :   1 1 0 1 | g~2~(z) = 1 + z^2^ + z^3^ <br />g~2~ :   1 0 1 1 |
| **Ausgangssignal:**                             | y~1~ = x~1~ ⊕ s~1~ ⊕ s~3~                     | y~2~ = x~1~ ⊕ s~2~ ⊕ s~3~                        |

<div style="page-break-after: always;"></div>

s = s[n+1]			s' = s[n+1]			y = y[n]

| s~1~  s~2~  s~3~ | x[n] = 0                           | x[n] = 0                           |
| ---------------- | ---------------------------------- | ---------------------------------- |
| Flip-Flop-Status | s~1~'  s~2~'  s~3~'  /  y~1~  y~2~ | s~1~'  s~2~'  s~3~'  /  y~1~  y~2~ |
| 000              | 000 / 00                           | 100 / 11                           |
| 001              | 000 / 11                           | 100 / 00                           |
| 010              | 001 / 01                           | 101 / 10                           |
| 011              | 001 / 10                           | 101 / 01                           |
| 100              | 010 / 10                           | 110 / 01                           |
| 101              | 010 / 01                           | 110 / 10                           |
| 110              | 011 / 11                           | 111 / 00                           |
| 111              | 011 / 00                           | 111 / 11                           |



## [Decodierung Viterby](https://youtu.be/dKIf6mQUfnY)  ([Deutsch](https://youtu.be/MXccfyEt4hA))

==Für Spracherkennung interessant==

Codieren

```mermaid
graph LR
N0[State]-- "x[n]<br />y[n]" -->N1[next State]
subgraph n=0
n0[000]
end
subgraph n=1
n1[100]
end
n0-- "1<br />11" -->n1
```

  

## 7.5 [Kaufmännische Probleme](https://youtu.be/vUQBz1phBsU)



## 7.6 [Statistische dynamische Optimierung](https://de.wikipedia.org/wiki/Wagner-Whitin-Algorithmus)

==Zugehöriges AB ( abl_dyn_kund.pdf ) nicht gleich wie AB in Video:	p=2/3  +  1200$==



<div style="page-break-after: always;"></div>

# 8. [Singulärwertzerlegung](https://youtu.be/bDV7Uxn9338) (S)



> Verwendung in Bildkomprimierung https://youtu.be/QQ8vxj-9OfQ
>
> LGS Ax=b leicht lösbar, wenn A quadratisch und A invertierbar (Determinante!=0)



<img src="../../Typora.assets/image-20201127121149488.png" alt="image-20201127121149488" style="zoom: 40%;" />		m × n:	Zeilen × Spalten (**Z**eilen **z**uerst, **S**palten **s**päter)



|                                    |                              A                               |   A^+^    ([Pseudo-Inverse](https://youtu.be/PjeOmOz9jSY))   |
| ---------------------------------- | :----------------------------------------------------------: | :----------------------------------------------------------: |
| Singulärwertzerlegung              | $\underset{m×n}A=\underset{m×m}U·\underset{m×n}\Sigma·\underset{n×n}{V^T}$ | $\underset{n×m}{A^+}=\underset{n×n}V·\underset{n×m}{\Sigma^+}·\underset{m×m}{U^T}$ |
| Gleichung                          |                  $A·\vec v_i=s_i·\vec u_i$                   |             $A^+·\vec u_i=\dfrac1{s_i}·\vec v_i$             |
| A mit Summe berechnen              |    $\displaystyle A=\sum_{i=1}^r~s_i·\vec u_i·\vec v_i^T$    | $\displaystyle A^+=\sum_{i=1}^r~\dfrac1{s_i}·\vec v_i·\vec u_i^T$ |
| Sigma  *(gleiche Dimension wie A)* | $\Sigma=\begin{pmatrix}s_1&0&..\\0&s_2&..\\..\end{pmatrix}$  | $\Sigma^+=\begin{pmatrix}\dfrac1{s_1}&0&..\\0&\dfrac1{s_2}&..\end{pmatrix}$ |



|       | Berechnung                                                   | Ergebnis                                                    |
| ----- | ------------------------------------------------------------ | ----------------------------------------------------------- |
| **Σ** | $A^T·A=\underset{n×n}B$<br />$n$  Eigenwerte von B:  $\lambda_1,~\lambda_2,~..\\$<br />$r$  Singulärwerte (nicht Null, Größter zuerst):  $s_1=\sqrt{\lambda_1},\quad s_2=\sqrt{\lambda_2},~..$<br />*gleiche Dimension wie A* | $\Sigma=\begin{pmatrix}s_1&0&..\\0&s_2&..\\..\end{pmatrix}$ |
| **V** | Eigenvektoren von B:	$\lambda_1~→~\vec e_1~,\quad \lambda_2~→~\vec e_2\quad..\\$<br />EV [normieren](https://youtu.be/5GU-eElpHRo):	$\vec v_1=\dfrac1{\vert \vec e_1\vert}·\vec e_1$ | $V=\bigg(\vec v_1\quad\vec v_2\quad ..\bigg)$               |
| **U** | $\vec u_i=\dfrac1{\sqrt\lambda_i}·A·\vec v_i\qquad\qquad\vec u_1\perp\vec u_2\perp \vec u_3$	(sind automatisch normiert) | $U=\bigg(\vec u_1\quad\vec u_2\quad\vec u_3\bigg)$          |

<div style="page-break-after: always;"></div> 

# 9. Soft decision

| L-Wert                                             | Wkt                                                          |      |
| -------------------------------------------------- | ------------------------------------------------------------ | ---- |
| $L(y)=\ln\left(\dfrac{P(y|x=1)}{P(y|x=-1)}\right)$ | $P(y~|~x={\color{red}\pm}1)=\dfrac{e^{{\color{red}\pm}\frac{L(y)}2}}{e^{\frac{L(y)}2}+e^{-\frac{L(y)}2}}$<br />x:  was gesendet wurde |      |



| Störung        | Normalverteilung          |      |
| -------------- | ------------------------- | ---- |
| **Verteilung** | $\mathcal{N}(0,\sigma^2)$ |      |
| **L-Wert**     | $L(y)=\dfrac2{\sigma^2}y$ |      |



## 9.3 Soft-Viterbi Algorithmus





# 10. Graphentheorie





 <div style="page-break-after: always;"></div>

# ———————  S T A T I S T I K  ———————





# 1. Wahrscheinlichkeitsrechnung



## 1.1 [Kombinatorik](https://www.youtube.com/watch?v=1qWSxVm7Oak)

|                                       | Kombination<br /><span style="font-weight:normal">(Reihenfolge egal)</span> | Variation<br /><span style="font-weight:normal">(Mit Reihenfolge)</span> | Alles Anordnen              |
| ------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------- |
| **Ohne Wdh.**<br />(ohne Zurücklegen) | $\displaystyle\binom nk=\dfrac{n!}{k!·(n-k)!}$               | $\displaystyle\binom nk·k!=\dfrac{n!}{(n-k)!}$               | $n!$                        |
| **Mit Wdh.**<br />(mit Zurücklegen)   | $\displaystyle\binom{n+k-1}k$                                | $n^k$                                                        | $\dfrac{n!}{k_1!·k_2!\ ..}$ |



## 1.3 Grundlagen

$$
\array{&A&\overline A\\\hline B&P(A,B)&P(\overline A,B)&P(B)\\\overline B&P(A,\overline B)&P(\overline A,\overline B)&P(\overline B)\\\hline&P(A)&P(\overline A)&\Sigma}
$$



$P(A,B)$	Wahrscheinlichkeit, dass A und B eintreten.

$P(A|B)$	Wahrscheinlichkeit von A, falls B eingetreten ist	/	trifft B zu, so trifft mit ...% auch noch A zu



$P(A,B)=P(A|B)·P(B)$

$P(A|B)=\dfrac{P(A,b)}{P(B)}$

<div style="page-break-after: always;"></div>

## 1.5 Statistische Parameter – Ungruppiert

| Erwartungswert                      | α-Quantile                                                   | Varianz                                               | Standard-abweichung      |
| ----------------------------------- | ------------------------------------------------------------ | ----------------------------------------------------- | ------------------------ |
| $\displaystyle\mu=\frac1n\sum_ix_i$ | $x_\alpha=\bigg\{\begin{matrix}x_{\lceil n\alpha\rceil}& n\alpha\notin\Z\\\frac12(x_{n\alpha}+x_{n\alpha+1})&\text{sonst}\end{matrix}$ | $\displaystyle\sigma^2=\dfrac1n\sum_{i=1}(x_i-\mu)^2$ | $\sigma=\sqrt{\sigma^2}$ |

| Ausreißer - IQR                                   | untere Außreißergrenze | obere Außreißergrenze |
| ------------------------------------------------- | ---------------------- | --------------------- |
| $=x_{0,75}-x_{0,25}\\=ob.\ Quartil-unt.\ Quartil$ | $=x_{0,25}-1,5·IQR$    | $=x_{0,75}+1,5·IQR$   |

<img src="../../Typora.assets/boxplot.jpg" alt="boxplot" style="zoom:40%;" />					Variationskoeffizient:	$\dfrac\sigma\mu$



## 1.6 [Statistische Parameter – Gruppiert](https://de.wikipedia.org/wiki/Klasseneinteilung_(Statistik))

| Gruppen-Nr. $i$ | Gruppengrenzen                       | Gruppenmitte | Gruppenbreite | Gruppenhäufigkeit |
| --------------- | ------------------------------------ | ------------ | ------------- | ----------------- |
| $1$             | $0-4$                                | $3$          | $5$           | $3$               |
| $2$             | $5-9$                                | $8$          | $5$           | $2$               |
| $i$             | $\tilde x _{i,min}-\tilde x_{i,max}$ | $\tilde x_i$ | $\Delta x_i$  | $n_i$             |

| Erwartungswert                                 | Quantile                                                     | Varianz                                                      |
| ---------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $\displaystyle\mu=\frac1n\sum_i\tilde x_i·n_i$ | ${\scriptstyle Gruppenanfang}+\dfrac{\scriptstyle Pos.~in~Gruppe}{\scriptstyle \#~in~Gruppe}·{\scriptstyle Gruppenbreite}\\~\\=\tilde x_{i,min}+\dfrac{n\alpha-(n_0+..+n_{i-1})}{n_i}·\Delta x_i$ | $\displaystyle\sigma^2=\dfrac1n\sum_i(\tilde x_i-\mu)^2·n_i$ |
|                                                | Position:  $n·\alpha$	→	Gruppe:  $i$<br />→	Position in Gruppe:  $n\alpha-(n_0+..+n_{i-1})$ |                                                              |



<div style="page-break-after: always;"></div>

# 2. Diskrete Verteilung



Verteilung:	$F(x)=p_0·\varepsilon(x)+p_1·\varepsilon(x-1)+p_2·\varepsilon(x-2)\ ...$

$\mu=E(X)=\sum_ix_i·p_i$

$\sigma^2=Var(X)=\sum_i(x_i-\mu)^2·p_i$



$\sigma^2=Var(X)=E(X^2)-E(X)^2$



| Name                                    | Gegeben————————                                              | Formel                                                       |
| --------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Binomial-<br />Verteilung**           | p: Wkt für Erfolg<br />k: Anzahl Erfolge<br />n: Anzahl gesamt | $\displaystyle P(X=k)=\binom nk·p^k·q^{n-k}\\ E(X)=n·p\qquad \sigma(X)=\sqrt{n·p·q}$ |
| **Multinomial-<br />Verteilung**        | Ereignisse X~1~, X~2~ ... mit Wkt p~1~, p~2~ ...             | $P(X_1=k_1,X_2=k_2,..)=\dfrac{n!}{k_1!·k_2!·\ ..}·p_1^{k_1}·p_2^{k_2}·\ ..$ |
| **Geometrische Verteilung**             | k = konstant<br />n = veränderlich                           | $\displaystyle P(X=n)=\binom{n-1}{k-1}·p^k·(1-p)^{n-k}\\\displaystyle E(X)=\sum_n n·P(n)$ |
| **Hypergeo-<br />metrische Verteilung** | N: Anzahl gesamt<br />K: Anzahl  "Erfolg"<br />n: Anzahl gezogen | $P(X=k)=\dfrac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}n}\\ P(X_1=k_1,X_2=k_2,..)=\dfrac{\binom{K_1}{k_1}\binom{K_2}{k_2}·\ ..\ ·\binom{N-K_1-K_2...}{n-k_1-k_2...}}{\binom{N}n}$ |
| **Poisson Verteilung**                  | λ (=n·p): ∅-Wert (Ereignisse pro Zeiteinheit)<br />==X: # Ereignisse pro t== | $P(X=k)=\dfrac{\lambda^k}{k!}·e^{-\lambda}\qquad\sigma=\sqrt\lambda$ |

**[Vergleich Poisson vs Exponential](https://youtu.be/n7K8s4vryCQ)**



<div style="page-break-after: always;"></div>

# 3. Steige Zufallsvariable

|                            | ——————————                                          |                                                              |
| -------------------------- | --------------------------------------------------- | ------------------------------------------------------------ |
| **Exponential-Verteilung** | λ: Ereignisse pro Zeit<br />t: Zeit zw. Ereignissen | $F_X(t)=(1-e^{-\lambda t})\varepsilon(t)\qquad f_X(t)=\lambda e^{-\lambda t}·\varepsilon(t)$ |
| **Normal-Verteilung**      | µ: Erwartungswert<br />σ: Standardabweich.          | $\mathcal{N}(\mu,\sigma^2)=\phi(\frac{(x+0,5)-\mu}\sigma)-\phi(\frac{(x-0,5)-\mu}\sigma)\qquad \sigma^2=n·p·q$ |



| Dichte                                                      | Verteilung         | ==Erwartungswert==                                     | Varianz                  |
| ----------------------------------------------------------- | ------------------ | ------------------------------------------------------ | ------------------------ |
| $f_X(x)=F_X'(x)\\=\dfrac{F_X(x+\Delta x)-F_X(x)}{\Delta x}$ | $F_X(x)=P(X\le x)$ | $\displaystyle E(X)=\int_{-\infty}^\infty xf_X(x)\ dx$ | $\sigma^2=E(X^2)-E(X)^2$ |
| **α-Quantil**                                               |                    |                                                        |                          |
| $F_X(x)\overset!=\alpha$                                    |                    |                                                        |                          |


$$
\begin{array}~
P(a\le X\le b)&=&F_X(b)-F_X(a)&=&\int_a^b f_X(x)\ \text{dx}\\~\\
P(X\ge a)&=&1-F_X(a)&=&\int_a^\infty f_X(x)\ \text{dx}\\~\\
P(X\le b)&=&F_X(b)&=&\int_{-\infty}^b f_X(x)\ \text{dx}\end{array}
$$

---



## 3.2 Gleichverteilung

| Dichte                                                       | Verteilungsfunktion                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20201023124941366](../../Typora.assets/image-20201023124941366.png) | ![image-20201023124954774](../../Typora.assets/image-20201023124954774.png) |
| **Erwartungswert:**                                          | **Varianz**                                                  |
| $E(X)=\dfrac{a+b}2$                                          | $Var(X)=\dfrac{(b-a)^2}{12}$                                 |

<div style="page-break-after: always;"></div>

## 3.3 Die [Exponentialverteilung](https://www.youtube.com/watch?v=FLsAAbxzXR8&t=1224s)

X:	Ausfallzeitpunkt			1/λ = α :	Zeitabstand zwischen Ereignissen/Ausfällen

| Ausfall-Wkt. bis Zeitpunkt t              | Überlebens-Wkt. bis Zeitpunkt t                   | Ausfallrate                                                  |
| ----------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| $F_X(t)=P(X\le t)$                        | $R_X(t)=1-F_X(t)$                                 | $\lambda(t)=P(t\le X\le t+\Delta t\quad\vert\quad X\ge t)\\~\\=\dfrac{F_X(t+\Delta t)-F_X(t)}{1-F_X(t)}$ |
| **Exponentialverteilung**                 | **Erwartungswert / Standardabweichung**           | **β-Quantil**                                                |
| $F_X(t)=(1-e^{-\lambda t})\varepsilon(t)$ | $E(X)=\sigma(X)=\frac1\lambda\\\mu=\sigma=\alpha$ | $t_\beta=\dfrac{-\ln(1-\beta)}\lambda=\underbrace{-\ln(1-\beta)}_{Prozentsatz}·E(X)$ |





## 3.4 Die Weibull-Verteilung

| Dichte                                                       | Verteilung                                                   | Parameter                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $f_X(t)=\frac{\alpha·\beta}\gamma\left(\frac{t-t_0}\gamma\right)^{\beta-1}·e^{-\alpha(\frac{t-t_0}\gamma)^\beta}·\varepsilon(t)$ | $F_X(t)=\left(1-e^{-\alpha(\frac{t-t_0}\gamma)^\beta}\right)\varepsilon(t-t_0)$ | $t_0: Beginn\\\gamma: Gr\ddot oßenordnung$                   |
| **Parameter bestimmen:**  $\gamma:$  Zeitraum<br />$\gamma$  auch  $T=\dfrac1\lambda\qquad \beta$  auch  $\kappa$ | $\gamma_{neu}=\alpha^{-\frac1\beta}·\gamma_{alt}$            | β<1: früher Ausfall<br />β=1: zufäll. Ausfall<br />β>1: Verschleißausfall |



## 3.5 Die Normalverteilung

| Allgemeine Normalverteilung                                  | [Standardnormalverteilung](https://youtu.be/qTgKZ_RUxhc) | Verteilungsfunktion                                          |
| ------------------------------------------------------------ | -------------------------------------------------------- | ------------------------------------------------------------ |
| $f_X(x,\mu,\sigma)=\dfrac1\sigma·\phi(\frac{x-\mu}\sigma)\\~\\=\frac1{\sigma\sqrt{2\pi}}·e^{-\frac12\left(\frac{x-\mu}\sigma\right)^2}$ | $\phi(x)=f_X(x,0,1)=\frac1{\sqrt{2\pi}}·e^{-\frac12x^2}$ | $F(x)=\Phi(\frac{x-\mu}\sigma)=\int_{-\infty}^xf(x,\mu,\sigma)~dt$ |
| $\mathcal{N}(\mu,\sigma)\qquad\mathcal{N}(n\mu,\sqrt{n}\sigma)$ | $\mu:Erwartungswert\\\sigma:Standardabweich.$            | $\Phi(-z)=1-\Phi(z)$                                         |



<div style="page-break-after: always;"></div>

# 4. Zufallsgeometrie 



## 4.1 Diskrete Zufallsvektoren

|                  | Verteilung             | Dichte                    |
| ---------------- | ---------------------- | ------------------------- |
|                  | $f(x,y)=P(X=x,Y=y)$    | $F(x,y)=P(X\le x,Y\le y)$ |
| falls unabhängig | $f(x,y)=f_1(x)·f_2(y)$ | $F(x,y)=F_1(x)·F_2(y)$    |



$P(Z)=f_Z=f_X\circledast f_Y\quad⚬—\!•\quad \check f_X·\check f_Y$

```
Z = X + Y		0.6		0.3		0.1	 *	0.6		0.4			z  |  0		1	  2		3
				————————————————————————————————————		—————————————————————————————
						0.36	0.18	0.06				fz | 0.36  0.42  0.18  0.04
								0.24	0.12	0.04
				————————————————————————————————————			  z⁰	z¹	  z²	z³
						0.36	0.42	0.18	0.04
```



## 4.2 Diskrete Zufallsfunktion 

  

## 4.3 Stetige Zufallsvektoren

| Verteilung         | Dichte                                                       | Randverteilung                                               |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $f_{(X,Y)}(x,y)$   | $\displaystyle F(x;y)=\int_{x_1}^{x_2}\int_{y_1}^{y_2}f(x;y)\text{ dy dx}$ | $\displaystyle f_1(x)=\int_{-\infty}^\infty f(x,y)\text{ dy}$ |
|                    | $\displaystyle P(X\le x_0)=\int_{-\infty}^{x_0}\int_{-\infty}^{\infty}f(x;y)\text{ dy dx}$ | $\displaystyle f_2(y)=\int_{-\infty}^\infty f(x,y)\text{ dx}$ |
| **Erwartungswert** | $\displaystyle E(X-Y)=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}(x-y)·f(x;y)\text{ dy dx}$ |                                                              |



## 4.5 Stetige Zufallsfunktion

| Z = X + Y | Z = max( X , Y )                                             |
| --------- | ------------------------------------------------------------ |
|           | $\displaystyle F_Z(t)=P(X\le t,~Y\le t)=\int_0^t\int_0^tf_{X,Y}(t_1,t_2)dt_1dt_2$ |

$f_{X+Y}=f_X\circledast f_Y\quad⚬—\!•\quad \check f_X·\check f_Y\qquad\qquad F_{X+Y}(t)=X(t)\circledast Y(t)=\int_0^t X(t-t_2)·Y(t_2)dt_2$

<div style="page-break-after: always;"></div>

# 5. Die Grenzwertsätze



## 5.1 Bedingte Erwartung

$\displaystyle E(X~\vert~Y)=\sum_x~x·P(X=x~\vert~Y)\qquad\qquad\displaystyle E(X)=\sum_i~E(X\vert A_i)·P(A_i)$



## 5.2 Tschebyscheff Ungleichung

$P\big(\vert X-\mu\vert>\varepsilon\big)~\le~\dfrac{\sigma^2}{\varepsilon^2}\qquad \varepsilon=vorgegebene~Abweichung·\mu$

Falls Normalverteilung unterstellt:	$P(\mu-\mu\sigma\le X\le\mu+\mu\sigma)$



## 5.3 [Zentraler Grenzwertsatz](https://youtu.be/NvQTD4hlfCQ)

| Nur einzelnes X, μ und σ               | Mehrere X, μ und σ                                           |
| -------------------------------------- | ------------------------------------------------------------ |
| $\mathcal N(n\ \mu,\ \sqrt n\ \sigma)$ | $\mathcal N\big(~n·(\mu_1+\mu_2+…+\mu_n),~\sqrt n·(\sigma_1+\sigma_2+…+\sigma_n)~\big)$ |



## 5.4 Approximation anderer Verteilungen durch NV

|                         | Bedingung                   | Normalverteilung                    |
| ----------------------- | --------------------------- | ----------------------------------- |
| **Binomial-Verteilung** | $n>30\qquad 0,1\le p\le0,9$ | $\mathcal N(n~p,\ \sqrt{n~p~q}~)$   |
| **Poisson-Verteilung**  | $\lambda>10$), i            | $\mathcal N(\lambda,~\sqrt\lambda)$ |



<div style="page-break-after: always;"></div>

# 6. Schätzen und Testen



## 6.1 [Chi-Verteilung](https://youtu.be/oQVcepEviw4)

|    Praxis     |              A        !A              |                               |      | Theorie       | A        !A                           |              |
| :-----------: | :-----------------------------------: | ----------------------------- | ---- | ------------- | ------------------------------------- | ------------ |
| **B<br />!B** | p~1~       p~2~ <br />p~3~       p~4~ | p~1~ + p~2~ <br />p~3~ + p~4~ |      | **B<br />!B** | t~1~       t~2~ <br />t~3~       t~4~ |              |
|               |          p~1~ + p~3~    ...           | <u>Summe</u>                  |      |               |                                       | <u>Summe</u> |

$\chi^2=\sum\dfrac{(praxis.Wert-theor.Wert)^2}{theor.Wert}$			Freiheitsgrad:  $\nu=(m-1)(n-1)$	m: Zeilen, n: Spalten

| Anzahl Freiheitsgrade                         | 1    | 2    | 3     | 4     | 5     |
| --------------------------------------------- | ---- | ---- | ----- | ----- | ----- |
| **Signifikant**	           $\chi^2\ge95\%$ | 3,84 | 5,99 | 7,81  | 9,49  | 11,07 |
| **Hoch-Signifikant**	$\chi^2\ge 99\%$      | 6,63 | 9,21 | 11,34 | 13,28 | 15,09 |



## 6.2/3 [Erwartungswert / Anteil Schätzen](https://youtu.be/DdwTa28W4Os)

|                                                  | Große Stichprobe (n > 30)                                    | Kleine Stichprobe (n < 30)                                   |
| ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Erwartungswert**                               | $\mu\in\left[m-z·\dfrac{s}{\sqrt n}\quad;\quad m+z·\dfrac{s}{\sqrt n}\right]$ | $\mu\in\left[m-t·\dfrac{s}{\sqrt n}\quad;\quad m+t·\dfrac{s}{\sqrt n}\right]$ |
| **Anteil / Prozentsatz**                         | $\left[p-z·\sqrt{\dfrac{p~q}{n}}\quad;\quad p+z·\sqrt{\dfrac{p~q}{n}}\right]$ | $\left[p-t·\sqrt{\dfrac{p~q}{n}}\quad;\quad p+t·\sqrt{\dfrac{p~q}{n}}\right]$ |
| **Standard-abweichung**<br />(nicht KA-relevant) | $\left[s-z·\dfrac{s}{\sqrt{2n}}\quad;\quad s+z·\dfrac{s}{\sqrt{2n}}\right]$ | $\left[s\sqrt{\dfrac{n-1}{\chi^2_{0,995}}}\quad;\quad s\sqrt{\dfrac{n-1}{\chi^2_{0,005}}}\right]\quad(99\%)$ |

| Konfidenz                  | 90%        | 95%                                         | 99%              |
| -------------------------- | ---------- | ------------------------------------------- | ---------------- |
| **z - Werte**              | $z=1.65$   | $z=1.96$    (in Klausur reicht auch **2**)  | $z=2.58$         |
| **t - Werte**  ($\nu=n-1$) | $t_{0,95}$ | $t_{0,975}$                                 | $t_{0,995}$      |
| $\chi$-Werte               |            | $\chi^2_{0,975}=19\qquad\chi^2_{0,025}=2.7$ | $\chi^2_{0,005}$ |



## 6.4 Maximum Likelihood

<div style="page-break-after: always;"></div>

## 6.5 Bayes Schätzer

$\begin{array}{c|cc|c}&X&!X&In\\\hline Y\\!Y\\\hline Out&&&100\end{array}\qquad\qquad\begin{matrix}P(~X~\vert~ Y~)=\\P(~!X~\vert~!Y~)=\end{matrix}$			(Wahrscheinlichkeit Eingang)



## 6.7 Statistische Korrelation

| [Kovarianz](https://youtu.be/X7eeyRX35wM)                    | [Korrelationskoeffizient](https://youtu.be/hUmxhN5Uuqg)      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| $\displaystyle\text{Cov}(X,Y)=\sum_i(x_i-\overline x)(y_i-\overline y)=E(XY)-E(X)·E(Y)$ | $r=\dfrac{\text{Cov}(X,Y)}{\sigma(X)·\sigma(Y)}=1-\dfrac{\sum\vert x_i-y_i\vert}{n(n+1)}$ |
| **Varianz**                                                  | **Kovarianz-Matrix**                                         |
| $\text{Var}(X)~=~E(X^2)-E(X)^2\\\text{Var}(X+Y)~=~\text{Var}(X)+\text{Var}(Y)+2\text{Cov}(X,Y)$ | $\begin{pmatrix}Var(X)&Cov(X,Y)\\Cov(X,Y)&Var(Y)\end{pmatrix}$ |

wenn X und Y unabhängig sind, gilt Cov(X,Y) = 0



| Rang-Korrelation                                             | Rangkorrelationskoeffizient                 |
| ------------------------------------------------------------ | ------------------------------------------- |
| $\begin{array}{c|cccc}A&x_1&x_2&x_3&…\\\hline B&y_1&y_2&y_3&…\end{array}\qquad \begin{matrix}1\qquad2\qquad3\\x_2<x_3<x_1\\x_1=x_3<x_2\end{matrix}\qquad \begin{array}{c|ccc}A&3&1&2\\\hline B&1,5&3&1,5\\\hline\Delta r&1,5&2&0,5\end{array}$ | $1-\dfrac{6}{n(n^2-1)}·\sum \Delta {r_i}^2$ |

 





# ——————  W E R K Z E U G E  ———————



#### [Binomialkoeffizient](https://youtu.be/BDUJP9_dWEs?t=171)



| Geometrische Reihe                                           |
| ------------------------------------------------------------ |
| $1+x+x^2+x^3+\ ...\ =\dfrac1{1-x}\qquad,\text{wenn}\quad\vert x\vert<1$ |

 