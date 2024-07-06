# Regressionsmethoden 
- lineare Beziehung 
	- [[#Linear Regression]] 
- nichtlineare Beziehung 
	- [[#Polynomiale Regression]] 


## Linear Regression 
- Modelliert eine lineare Beziehung zwischen den unabhängigen Variablen (Features) und der abhängigen Variablen (Ziel). 
### mathematische Formulierung 
$\hat{y} = a + b \cdot x$ 
- $a$: Intercept 
- $b$: Coefficient 

## Polynomiale Regression 
- Regression mit Polynomen höheren Grades 
### Bias und Variance 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-06_16-02-16.png?raw=" width="90%" /> 
- Bias (Verzerrung): Fehler, der durch die Annahmen im Modellierungsprozess eingeführt wird. 
	- hoher Bias $\rightarrow$ das Modell zu einfach ist und die zugrunde liegende Beziehung in den Daten nicht gut erfasst. 
- Variance (Varianz): wie stark die Modellvorhersagen für verschiedene Datensätze variieren. 
	- hohe Varianz: das Modell sehr empfindlich auf die Trainingsdaten reagiert und kleine Änderungen in den Daten zu großen Veränderungen in den Vorhersagen führen. 


