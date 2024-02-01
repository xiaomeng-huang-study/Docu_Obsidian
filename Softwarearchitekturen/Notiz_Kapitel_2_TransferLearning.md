# TransferLearning 

- Schichten 
	- untere: generisch 
	- mittlere: Teile eines Objekts 
		- das rezeptives Feld noch nicht groß genug 
	- hohe: ganze Objekte 

- Einschub 
	- Nearest-Neighbours 
		- L1-Norm / Manhatten-Distance: $\sum_{i}\left|x_{i}-y_{i}\right|$ 
		- L2-Norm / Euclidian-Distance: $\sqrt{\sum_{i}\left(x_{i}-y_{i}\right)^{2}}$ 
		- mit jedem Bild in Datenbank vergleichen 

- Vorgehensweise 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-02_16-34-44.png?raw=" width="600" /> 
	- neue Datenmenge ist klein 
		- nur die letzte Schicht Finetuning 
		- andere Schichten freeze 
	- neue Datenmenge groß 
		- die FC finetuning 
		- die conv-Schichten freeze 
