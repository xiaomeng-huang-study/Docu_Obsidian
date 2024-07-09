# ML Verfahren 
## 1. Decision-Tree 

## 2. Sigmoid-Funktion 
- Formulierung: $\sigma(z) = \frac{1}{1+e^{-z}}$ 
- Anwendung 
	- in NN: Aktivierungsfunktion, um die nichtlinearen Zusammenhänge zu erlernen. 
	- in Logistische Regression: stetige Werte in Wahrscheinlichkeiten zwischen 0 und 1 umzuwandeln, was hilfreich ist, binäre Entscheidungen zu treffen. 

## 3. k-Means Verfahren 

## 4. Underfitting und Overfitting 
- Underfitting: Modell zu einfach, um die zugrunde liegenden Muster der Trainingsdaten zu erfassen 
- Overfitting: Modell zu komplex ist und sich zu sehr an die Trainingsdaten anpasst. 
- Visualisierung: [[Notiz_Underfitting_Overfitting#Underfitting_Overfitting|Underfitting und Overfitting]] 


# Bewertung 
## 3. Stratified Cross Validation 
- eine Technik der Kreuzvalidierung, bei der die Daten so in K-Falten aufgeteilt werden, dass jede Falte die gleiche proportionale Verteilung der Klassenlabels (Zielvariablen) wie der gesamte Datensatz aufweist. 


# Datenanalyse 
## Schritte zur Datenvorbereitung 
### Bereinigung 
- Fehlende Werte 
	- Fehl-Rate 
		```python
		df_missing_values = pd.DataFrame(columns=['col', 'percent_missing']).set_index('col') 
		for col in df.columns:
			df_missing_values.loc[col] = np.mean(df[col].isnull())
		```
	- Korrektur 
		- Mit einem Wert 
			- Mit Mittelwert 
				```python
				df['temperature'].fillna(df['temperature'].mean(numeric_only= True))
				```
			- Mit KNN-Imputer 
				```python
				df_numeric = df.select_dtypes(include=[np.number])
				imputer = KNNImputer(n_neighbors=2)
				imputed = imputer.fit_transform(df_numeric.iloc[:,10:20])
				```
		- Löschen 
- Ausreißer 
	- Prüfung & Korrektur 
		- Box-Plot 
			```python
			df['life_sq'].plot.box(figsize=(15,10), grid=True);
			mask = (df['life_sq']< 1000) | (df['life_sq'].isnull())
			df = df[mask]
			```
		- z-Value 
			```python
			df_numeric = df.select_dtypes(include=[np.number])
			df_zscore = df_numeric.apply(lambda x: np.abs(zscore(x)))
			threshold = 5
			(df_zscore>threshold).any(axis='columns')
			df = df[~(df_zscore>threshold).any(axis='columns')]
			```
- nicht aussagekräftige Infos 
	- columns 
		```python
		cnts = df.iloc[1].value_counts(dropna=False)
		cnst/num_rows 
		df.drop(columns=low_information_cols.keys()).head()
		```
	- rows 
		```python
		df.drop_duplicates(subset= df.columns.drop("id"))
		```
- Inkonsistenz 
	- Groß, klein - Schreibung 
		- `.str.lower()` , `.str.upper()` 
	- Format 
		- Datum 
			```python
			df["date"] = pd.to_datetime(df["date"])
			```
		- numeric 
			```python
			df["temperature"] = pd.to_numeric(df["temperature"])
			```
	- Tippfehler 
		- Mit Levenshtein-Distanz oder Spellchecker 

### Umwandlung 
- One-Hot-Encoding 
	```python
	oht = TransactionEncoder()
	oht_ary = oht.fit_transform(transactions)
	transactdf = pd.DataFrame(oht_ary, columns=oht.columns_)
	```
- Skalierung und Normalisierung 
	```python
	scaler = MinMaxScaler() df[['Temp', 'Max. Temp', 'Min. Temp']] = scaler.fit_transform(df[['Temp', 'Max. Temp', 'Min. Temp']])
	```

### Feature Engineering 

### Daten-Aufteilung 
```python
train, test = train_test_split(df, test_size=0.2, random_state=42)
```