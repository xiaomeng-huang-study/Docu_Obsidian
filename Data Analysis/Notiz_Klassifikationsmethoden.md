# Klassifikationsmethoden 
- [[#Logistische Regression]] 
- [[#Softmax-Regression]] 


## Logistische Regression 
- Modellierung der Wahrscheinlichkeit eines **binären** Ergebnisses 
### Einfügung einer Aktivierungsfunktion 
- Funktion: kontinuierliche Werte in gewünschte diskrete Werte wandelt. 
- z.B. Step-Funktion, logistische Funktion (Sigmoid-Funktion $\sigma(z)=\frac{1}{1+e^{-z}}$) 
### Skalierung von Daten 
- Standarscaler $z=\frac{x-\operatorname{mean}(x)}{\operatorname{std}(x)}$ 
- MinMaxScaler $X_{\text {scaled }}=\frac{X-X_{\min }}{X_{\max }-X_{\min }}$ 
- RobustScaler $X_{\text {scaled }}=\frac{X-\operatorname{median}(X)}{\operatorname{IQR}(X)}$ 

## Softmax-Regression 
- multinomiale logistische Regression, um eine Wahrscheinlichkeitsverteilung über mehrere Klassen zu berechnen 
### Aktivierungsfunktion 
- Softmax-Funktion $\operatorname{softmax}\left(z_{i}\right)=\frac{e^{z_{i}}}{\sum_{j=1}^{K} e^{z_{j}}}$ 

