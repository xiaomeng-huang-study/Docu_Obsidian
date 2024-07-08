# Klassifikation_Bewertung 
## Klassifikationsmetriken 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-07_13-25-00.png?raw=" width="40%" /> 
- Genauigkeit (engl. Accuracy) $=\frac{\sum \mathrm{TP}+\mathrm{TN}}{\sum \mathrm{TP}+\mathrm{FP}+\mathrm{FN}+\mathrm{TN}}$ 
- Präzision (engl. Precision) 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-07_13-34-11.png?raw=" width="40%" /> 
	- $=\frac{\sum \mathrm{TP}}{\sum \mathrm{TP}+\mathrm{FP}}$ 
- Sensitivität (engl. Recall) 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-07_13-34-10.png?raw=" width="40%" /> 
	- $=\frac{\sum \mathrm{TP}}{\sum \mathrm{TP}+\mathrm{FN}}$ 
- F1-Score 
	- ein harmonisches Mittel zwischen Precision und Recall 
	- $=2 \times \frac{\text { Precision } \times \text { Recall }}{\text { Precision }+ \text { Recall }}$ 
- AUC-ROC (Area Under the Receiver Operating Characteristic Curve) 
	- True Positive Rate (Recall) vs. False Positive Rate (FPR, $\frac{\sum \mathrm{FP}}{\sum \mathrm{FP} + \mathrm{TN}}$) 
- AUC-PR (Area Under the Precision-Recall Curve) 
	- Precision vs. Recall 

## Loss-Funktion 
- Kreuzentropie-Verlustfunktion (engl. Cross-Entropy-Loss) 