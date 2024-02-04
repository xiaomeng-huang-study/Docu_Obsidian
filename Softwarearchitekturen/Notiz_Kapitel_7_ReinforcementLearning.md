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

## Typen 
- Value-Based 
	- [[Notiz_Kapitel_7_ReinforcementLearning#Q-Learning|Q-Learning]] , [[Notiz_Kapitel_7_ReinforcementLearning#Deep Q-Learning|Deep Q-Learning]] 
- Policy-Based 
	- [[Notiz_Kapitel_7_ReinforcementLearning#Policy Gradient Methods|Policy Gradient Methods]] 
- Value-Based and Policy-Based Hybrid 
	- [[Notiz_Kapitel_7_ReinforcementLearning#Actor-Critic Method|Actor-Critic-Method]] 



## Q-Learning 
<img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_15-50-24.png?raw=" width="400" /> 
- ist eine Form des Reinforcement Learning, bei dem wir versuchen zu lernen, wie wir die erwarteten Belohnungen für jede Aktion in einem bestimmten Zustand vorhersagen können 
- $Q_i$ konvergiert zu $Q^{*}$ für $i ~ \rightarrow \infty$ 
- Problem 
	- wenn es zu viele State-Action gibt 
	- nur diskret, kann kontinuierlich 
	- Keine Fähigkeit zur Generalisierung auf neuen Staten 

### Deep Q-Learning 
<img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_16-01-22.png?raw=" width="600" /> 
- Funktion-Approximator -> tiefes neuronales Netz 
- $Q(s,a;\theta) \approx Q^{*}(s,a)$ 
	- $\theta$ : Gewicht für neuronales Netz 
- Zustandsraum: Gesamtheit aller möglichen Zustände, in denen sich die Umgebung befinden kann 
- Aktionsraum: Menge aller in einem bestimmten Zustand möglichen Aktionen 
- Zustandswert: die erwartete Summe der diskontierten Belohnungen für einen Zustand, wenn man eine bestimmte Policy verfolgen 
- Aktionswert: die erwartete Belohnung für die Durchführung einer Aktion in einem bestimmten Zustand 
- Policy-Funktion: eine Funktion, die Zustände auf Aktionen abbildet. 
- Q-Funktion: State-Action als Input, Aktionswert als Output 
- Off-Policy-Learning: eine Policy lernen, während man mit einer anderen Policy Daten sammeln 
- On-Policy-Learning: eine Policy lernen, dann gleichzeitig nutzen 
- katastrophales Vergessen: wenn man mit kleinen Datenmengen gleichzeitig trainiert, wobei die neu zu lernenden Daten die bereits gelernten alten Informationen löschen oder verfälschen 
- Memory Replay 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_16-38-01.png?raw=" width="600" /> 
	- ein Buffer, indem frühere Erfahrungen gespeichert werden und dann eine nach dem Zufallsprinzip ausgewählte Teilmenge (Batch) dieser Erfahrungen zur Aktualisierung des Q-Networks verwendet wird, anstatt nur die jüngste Erfahrung zu verwenden. 
- Target-Network 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_16-39-01.png?raw=" width="600" /> 
	- Kopie des Haupt-DQN -> Stabilisierung 


## Policy Gradient Methods 
<img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_18-45-21.png?raw=" width="800" /> 
- Problem bei Wahrscheinlichkeit: Surrogatziel $-\log \left(\pi_{\theta}(a \mid s)\right)$ verwenden 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_18-50-27.png?raw=" width="400" /> 
- Loss Funktion 


## Actor-Critic Method 
<img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-04_19-04-04.png?raw=" width="800" /> 
