# Reinforcement Learning 

## Begriffe 
- Epsilon-Greedy-Strategie 
	- Greedy-Strategie / Ausnutzung 
		- ein Algorithmusansatz, bei dem man bei jedem Schritt die beste lokale Entscheidung trifft, in der Hoffnung, dass dies zu einer global optimalen Lösung führt. 
		- aktuelles Wissen 
	- Erkundungsstrategie / Erkundung 
		- nach dem Zufallsprinzip 
	- Mit Wahrscheinlichkeit $\epsilon$ wird Erkundungsstrategie benutzt, mit $1-\epsilon$ wird Greedy-Strategie benutzt 
- Markov-Eigenschaft 
	- die zukünftige Entwicklung eines stochastischen Prozesses <u>nur von seinem aktuellen Zustand abhängt</u> und nicht von seiner Vergangenheit. 
- Policy $\pi$ 
	- eine Funktion, die einen Zustand auf eine Wahrscheinlichkeitsverteilung über die Menge der möglichen Aktionen in diesem Zustand abbildet 
	- optimale Policy: die Strategie, die die Belohnungen maximiert 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-03_18-14-28.png?raw=" width="600" /> 
- Wert-Funktion $V_{\pi}$ (engl. Value-Function) 
	- Funktionen, die einen Zustand auf den erwarteten Wert (die erwartete Belohnung) abbilden, wenn man sich in einem bestimmten Zustand befindet oder in einem bestimmten Zustand eine Aktion ausführt. 
- Aktion-Wert-Funktion $Q_{\pi}$ (engl. Q-Function) 
	- eine Funktion, ein State-Aktion-Paar auf den erwarteten Wert (die erwartete Belohnung) abbilden. 


Schaubild: 
<img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-03_18-11-22.png?raw=" width="500" /> 

