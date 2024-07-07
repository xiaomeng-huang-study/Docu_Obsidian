# Regression_Bewertung 
- Mittlerer absoluter Fehler (engl. Mean Absolute Error, MAE) 
	- $\mathrm{MAE}=\frac{1}{n} \sum_{i=1}^{n}\left|y_{i}-\hat{y}_{i}\right|$ 
- Mittlerer quadratischer Fehler (engl. Mean Squared Error, MSE) 
	- $\operatorname{MSE}=\frac{1}{n} \sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}$ 
- Wurzel des mittleren quadratischen Fehlers (engl. Root Mean Squared Error, RMSE) 
	- $\mathrm{RMSE}=\sqrt{\frac{1}{n} \sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}}$ 
- Bestimmtheitsmaß ($R^{2}-Score$) 
	- ein Maß dafür, wie gut die beobachteten Ergebnisse durch das Modell erklärt werden. 
	- $R^{2}=1-\frac{\sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}}{\sum_{i=1}^{n}\left(y_{i}-\bar{y}\right)^{2}}$ 