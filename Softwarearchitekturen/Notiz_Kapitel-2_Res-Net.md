# Res-Net
- Problem zu lösen 
	- Bei sehr tiefen Netzwerken, insbesondere während des Trainings, können Gradienten entweder extrem klein werden (verschwindendes Gradientenproblem) oder extrem groß werden (explodierendes Gradientenproblem). Beide Phänomene können die Konvergenz des Trainingsprozesses beeinträchtigen.

- Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-21_17-13-54.png?raw=" width="1500" /> 
- Einführung 
	- "Residual Block" oder "Shortcut Connections". 
	- Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-21_17-06-21.png?raw=" width="200" /> 
	- Statt nur die Aktivierungen von einer Schicht zur nächsten zu übergeben, wird die Differenz zwischen den Eingabe- und Ausgabeaktivierungen als Residuum übergeben. 