# Regression 
## Algorithmen 
- Schätzung stetiger Größen 
	- lineare Beziehung 
		- [[#Linear Regression]] 
	- nichtlineare Beziehung 
		- [[#Polynomiale Regression]] 
- Schätzung kategorialer Größen 
	- Binäre Klassifikation 
		- [[#Logistische Regression]] 
	- Mehrklassenklassifikation 
		- [[#Softmax-Regression]] 


## Algorithmen 
### Linear Regression 
#### mathematische Formulierung 
$\hat{y} = a + b \cdot x$ 
- $a$: Intercept 
- $b$: Coefficient 
#### Bewertung 
- Mittlerer absoluter Fehler (MAE) 
- Mittlerer quadratischer Fehler (MSE) 
- $R^{2}-Score$ 

### Polynomiale Regression 
- Regression mit Polynomen höheren Grades 
#### Bias und Variance 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-06_16-02-16.png?raw=" width="90%" /> 
- Bias (Verzerrung): Fehler, der durch die Annahmen im Modellierungsprozess eingeführt wird. 
	- hoher Bias $\rightarrow$ das Modell zu einfach ist und die zugrunde liegende Beziehung in den Daten nicht gut erfasst. 
- Variance (Varianz): wie stark die Modellvorhersagen für verschiedene Datensätze variieren. 
	- hohe Varianz: das Modell sehr empfindlich auf die Trainingsdaten reagiert und kleine Änderungen in den Daten zu großen Veränderungen in den Vorhersagen führen. 

---
### Logistische Regression 
#### Einfügung einer Aktivierungsfunktion 
- Funktion: kontinuierliche Werte in gewünschte diskrete Werte wandelt. 
- z.B. Step-Funktion, logistische Funktion (Sigmoid-Funktion $\sigma(z)=\frac{1}{1+e^{-z}}$) 
#### Skalierung von Daten 
- Standarscaler $z=\frac{x-\operatorname{mean}(x)}{\operatorname{std}(x)}$ 
- MinMaxScaler $X_{\text {scaled }}=\frac{X-X_{\min }}{X_{\max }-X_{\min }}$ 
- RobustScaler $X_{\text {scaled }}=\frac{X-\operatorname{median}(X)}{\operatorname{IQR}(X)}$ 

### Softmax-Regression 
- multinomiale logistische Regression 
#### Aktivierungsfunktion 
- Softmax-Funktion $\operatorname{softmax}\left(z_{i}\right)=\frac{e^{z_{i}}}{\sum_{j=1}^{K} e^{z_{j}}}$ 