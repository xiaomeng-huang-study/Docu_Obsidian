# Assoziationsanalyse 
## Assoziationsregel 
Implikationsausdruck der Form X $\rightarrow$ Y, wobei X und Y disjunkte Itemsets sind. 
- X steht für den Antecedent (Ursache) 
- Y für den Consequent (Folge) 

## Bewertung der Stärke der Implikation 

| Transactions |  Number   |
| :----------: | :-------: |
|    Total     | 3.000.000 |
|      B       |  300.000  |
|      W       |  500.000  |
|    B & W     |  150.000  |
Metrik 
- Support 
	- $\text{support}(A \rightarrow C)= \text{support}(A \cap C), \text { range: }[0,1]$ 
	- Es misst, wie oft das Itemset in den Daten vorkommt. 
		- hoher Wert $\rightarrow$ häufig 
	- Beispiel 
		$$
		\begin{aligned}
		\text{sup}(B) &= \frac{\text{B}}{\text{Total}} &= \frac{300.000}{3.000.000} &= 10\% \\
		\text{sup}(W \rightarrow B) &= \frac{\text{B \& W}}{\text{Total}} &= \frac{150.000}{3.000.000} &= 5\% \\
		\end{aligned}
		$$
- Confidence 
	- $\text { confidence }(A \rightarrow C)=\frac{\text{support}(A \cap C)}{\text{support}(A)}, \text { range: }[0,1]$ 
	- Es misst die Wahrscheinlichkeit, dass C in einer Transaktion erscheint, die A enthält. 
		- hoher Wert $\rightarrow$ Wenn A passiert, ist es sehr wahrscheinlich, dass C auch passiert. 
	- Beispiel 
		$$
		\begin{aligned}
		\text{conf}(W \rightarrow B) &= \frac{\text{B \& W}}{\text{W}} &= \frac{150.000}{500.000} &= 30\% \\
		\text{conf}(B \rightarrow W) &= \frac{\text{B \& W}}{\text{B}} &= \frac{150.000}{300.000} &= 50\%\\
		\end{aligned}
		$$
- Lift 
	- $\text{lift}(A \rightarrow C) = \frac{\text{support}(A \cap C)}{\text{support}(A) \times \text{support}(C)}, \text{range}: [0, \infty]$ 
	- das Verhältnis der tatsächlichen Häufigkeit des gemeinsamen Auftretens von A und C zu der erwarteten gemeinsamen Häufigkeit, wenn A und C unabhängig wären. 
	- Es misst die Stärke einer Regel im Vergleich zu einer Zufallsverteilung. 
		- $> 1$: A und C treten häufiger zusammen auf, als wenn sie unabhängig wären (positive Korrelation). 
		- $= 1$: A und C treten so oft zusammen auf, wie man es bei Unabhängigkeit erwarten würde (keine Korrelation). 
		- $< 1$: A und C treten seltener zusammen auf, als wenn sie unabhängig wären (negative Korrelation). 
	- Beispiel 
		$$
		\begin{array}{llll}
		\text{lift}(W \rightarrow B) &= \frac{\text{support}(W \cap B)}{\text{support}(W)\times\text{support}(B)} &= \frac{\frac{150.000}{3.000.000}}{\frac{500.000}{3.000.000} \cdot \frac{300.000}{3.000.000}} &= 3 \\
		\text{lift}(B \rightarrow W) &= \text{lift}(W \rightarrow B) & & \\
		\end{array}
		$$
- Levarage 
	- $\text { levarage }(A \rightarrow C)=\text{support}(A \cap C)-\text{support}(A) \times \text{support}(C), \text { range: }[-1,1]$ 
	- die Differenz zwischen der tatsächlichen Häufigkeit des gemeinsamen Auftretens von A und C und der erwarteten gemeinsamen Häufigkeit, wenn A und C unabhängig wären. 
		- $> 0$: A und C treten häufiger zusammen auf, als wenn sie unabhängig wären 
		- $= 0$: A und C treten so oft zusammen auf, wie man es bei Unabhängigkeit erwarten würde 
		- $< 0$: A und C treten seltener zusammen auf, als wenn sie unabhängig wären 
- Conviction 
	- $\operatorname{conviction}(A \rightarrow C)=\frac{1-\operatorname{support}(C)}{1-\operatorname{confidence}(A \rightarrow C)}, \text { range: }[0, \infty]$ 
	- das Verhältnis der erwarteten Häufigkeit, dass A ohne C auftritt, zur tatsächlichen Häufigkeit, dass A ohne C auftritt. 
	- Es misst, wie oft die Regel falsch wäre, wenn A auftritt, aber C nicht. 
		- hoher Wert: Die Regel ist zuverlässiger und tritt seltener falsch auf (starke Assoziation) 

## Arbeitsverlauf 
1. Auswahl der Frequent Itemsets mit einem $Min-Support$ 
2. Bestimmen der Assoziationsregeln basierend auf einer Confidence-Schwelle 
3. Auswertung der Regeln, z.B. Finden der Antecedents - Consequents mit dem höchsten $lift$ 
- Code-Beispiel 
	```python
	support_min = 0.01
	frequent_itemsets = apriori(transactdf, min_support= support_min, use_colnames= True)
	
	confidence_min = 0.5
	rules = association_rules(frequent_itemsets, metric= "confidence", min_threshold= confidence_min)
	
	mask = rules.loc[:, "antecedents"].apply(lambda x: x.issuperset({"Factorio"}))
	rules.loc[mask].sort_values("lift", ascending=False)[0: 5]
	```
