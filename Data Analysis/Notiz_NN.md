# Neural Network 

## Einzelne Neuronenschicht 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-07_17-23-00.png?raw=" width="90%" /> 
- $a^{1}=x$ 
- $a^{l}=\Phi\left(W^{l} a^{l-1}+b^{l}\right) \quad  \text{für} \quad l = 2,3, \ldots, L \quad  \text{bzw.}$ 
- Anzahl der Parameter 
	- $\begin{array}{cl} = & n_{a,l} \times n_{a, l - 1} + n_{a, l} \times 1 \\ = & n_{a, l} \times (n_{a, l-1} + 1)\end{array}$ 

## Mehrschichtige Netze 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-07_17-15-00.png?raw=" width="60%" /> 
- $a_{i}^{l}=\Phi\left(\sum_{j} w_{i j}^{l} a_{j}^{l-1}+b_{i}^{l}\right) \quad \text { für das } i \text {-te Neuron der Schicht}$ 