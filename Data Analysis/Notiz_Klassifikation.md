# Klassifikation 
## Algorithmen 
- [[#Decision Trees]] 


## Algorithmen 
### Decision Trees 
#### Maß für die Unreinheit
- Entropie 
- Gini-Index 
	- kleinere GI $\rightarrow$ Knoten homogener 
#### Arbeitsverlauf 
1. Berechne die GI eines jeden Kindknotens bei einem möglichen Split 
2. Berechne die GI eines jeden Splits als den gewichteten mittleren GI der Kindknoten 
3. Wähle den Split mit dem kleinsten GI 
4. (Wiederholung bis kein Split mehr möglich) 