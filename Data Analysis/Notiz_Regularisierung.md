# Regularisierung 
- Modellkomplexität zu kontrollieren und Überanpassung (Overfitting) zu vermeiden 

## L1-Regularisierung (Lasso)
- $\operatorname{Loss}=\operatorname{Loss}+\lambda \sum_{j=1}^{p}\left|w_{j}\right|$ 
	- Loss die ursprüngliche Verlustfunktion ist 
	- $\lambda$ der Regularisierungsparameter ist 
	- $\omega_j$ die Modellkoeffizienten sind 
	- $p$ die Anzahl der Merkmale ist 

## L2-Regularisierung (Ridge) 
- $\operatorname{Loss}=\operatorname{Loss}+\lambda \sum_{j=1}^{p} w_{j}^{2}$ 
	- Loss die ursprüngliche Verlustfunktion ist 
	- $\lambda$ der Regularisierungsparameter ist 
	- $\omega_j$ die Modellkoeffizienten sind 
	- $p$ die Anzahl der Merkmale ist 

## in Scikit-learn 
- $C = \frac{1}{\lambda}$ 
	- größer C $\rightarrow$ schwächere Regularisierung 
