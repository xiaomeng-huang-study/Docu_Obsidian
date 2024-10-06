# Einfach Integrierendes System (EIS) 
- <img src="https://github.com/ICH-BIN-HXM/images_REA/blob/main/Scrennshot_2024-10-06_11-17-00.png?raw=" width="30%" /> 
- $\mathrm{F}_{0}(\mathrm{s})=\frac{1}{\mathrm{sT}_{0}}$ 
- $\mathrm{F}_{\mathrm{W}}(\mathrm{~s})=\frac{1}{1+\mathrm{sT}_{0}}$ 
## Nachteile 
- Stellglieder häufig mit Verzögerungsverhalten 
- ein Glättungsglied zur Aufbereitung des Istwertsignals und zur Unterdrückung von Störeinflüssen fehlt 

# EIS mit nichtkompensierbarem Glied 
## PT1-Glied als Referenzsystem 
- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\frac{1}{1+\mathrm{sT}_{1}}$ 
## Totzeitglied 
- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\mathrm{e}^{-\mathrm{s} \mathrm{~T}_{\mathrm{t}}} \approx \frac{1}{1+\mathrm{sT}_{\mathrm{t}}}$ 
## Allpassglied 
- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\frac{1-\mathrm{sT}_{\mathrm{a}}}{1+\mathrm{sT}_{\mathrm{a}}} \approx \frac{1}{\left(1+\mathrm{sT}_{\mathrm{a}}\right)\left(1+\mathrm{sT}_{\mathrm{a}}\right)} \approx \frac{1}{1+\mathrm{s} \cdot 2 \mathrm{T}_{\mathrm{a}}}$ 
## Allgemein 
<img src="https://github.com/ICH-BIN-HXM/images_REA/blob/main/Scrennshot_2024-10-06_15-50-23.png?raw=" width="50%" /> 
- nichtkompensierbares Glied 
	- $\begin{array}{l}\mathrm{F}_{\mathrm{SNK}}(\mathrm{s}) & =\frac{\mathrm{e}^{-\mathrm{sT}_{\mathrm{t}}}}{\left(1+\mathrm{sT}_{1}\right)\left(1+\mathrm{sT}_{2}\right)\left(1+\mathrm{sT}_{3}\right)} \cdot \frac{1-\mathrm{sT}_{\mathrm{a}}}{1+\mathrm{sT}_{\mathrm{a}}} \\& \approx \frac{1}{\left(1+\mathrm{sT}_{\mathrm{t}}\right)\left(1+\mathrm{sT}_{1}\right)\left(1+\mathrm{sT}_{2}\right)\left(1+\mathrm{sT}_{3}\right)\left(1+\mathrm{s} 2 \mathrm{~T}_{\mathrm{a}}\right)} \\ & \approx \frac{1}{1+\mathrm{sT}_{\sigma}} ~~ \text {mit} ~~\mathrm{T}_{\sigma}=\mathrm{T}_{\mathrm{t}}+\mathrm{T}_{1}+\mathrm{T}_{2}+\mathrm{T}_{3}+2 \mathrm{~T}_{\mathrm{a}}\end{array}$ 
- offener Regelkreis 
	- $\begin{array}{l}\mathrm{F}_{0}(\mathrm{s})& = \frac{1}{\mathrm{sT}_{0}} \cdot \mathrm{F}_{\mathrm{SNK}}(\mathrm{s}) \\& = \frac{1}{\mathrm{sT}_{0}} \cdot \frac{1}{1+\mathrm{sT}_{\sigma}}\end{array}$ 
- geschlossener Regelkreis 
	- $\begin{array}{l}\mathrm{F}_{\mathrm{W}}(\mathrm{s}) & = \frac{\mathrm{F}_{0}(\mathrm{s})}{1 + \mathrm{F}_{0}(\mathrm{s})} \\& = \frac{1}{1+\mathrm{sT}_{0}+\mathrm{s}^{2} \mathrm{~T}_{0} \mathrm{~T}_{\sigma}}\end{array}$ 
### Beziehung zwischen $T_0$ und $T_\sigma$ 
- Nach dem Betragsoptimum 
	- $d = 0.707$ 
		- $T_0 = 2 \cdot T_\sigma$ 
	- $d = 1$ 
		- $T_0 = 4 \cdot T_\sigma$ 
### Beziehung zwischen $T_0$ und $T_\sigma$ 
- Gleiches Verhalten bei Durchschnittsfrequenz $\omega_D$ 
	-  $\varphi_{0}\left(\omega_{D} = \frac{1}{T_{0}}\right)  \overset{!}{=} -\frac{\pi}{2}-\arctan \frac{T_{\sigma }}{T_{0}}$ 
### Charakteristische Größen 
<img src="https://github.com/ICH-BIN-HXM/images_REA/blob/main/Scrennshot_2024-10-06_15-49-03.png?raw=" width="70%" /> 
<img src="https://github.com/ICH-BIN-HXM/images_REA/blob/main/Scrennshot_2024-10-06_15-48-04.png?raw=" width="80%" /> 


# Zweifach integrierendes System (ZIS) 
<img src="https://github.com/ICH-BIN-HXM/images_REA/blob/main/Scrennshot_2024-10-06_16-23-30.png?raw=" width="50%" /> 
- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\frac{1}{1+\mathrm{sT}_{\sigma}}$ 
- $\mathrm{F}_{0}(\mathrm{s})=\frac{1+\mathrm{sT}_{02}}{\mathrm{~s}^{2} \mathrm{~T}_{01} \mathrm{~T}_{02}} \cdot \frac{1}{1+\mathrm{sT}_{\sigma}}$ 
- $\mathrm{F}_{\mathrm{W}}(\mathrm{s})=\frac{1+\mathrm{sT}_{02}}{1+\mathrm{sT}_{02}+\mathrm{s}^{2} \mathrm{~T}_{01} \mathrm{~T}_{02}+\mathrm{s}^{3} \mathrm{~T}_{01} \mathrm{~T}_{02} \mathrm{~T}_{\sigma}}$ 
## Beziehung zwischen $T_{01}, T_{02}$ und $T_\sigma$ 
- Nach dem Symmetrisches Optimum (SO) 
	- $T_{01}=2 \cdot T_{\sigma}$ 
	- $T_{02}=4 \cdot T_{\sigma}$ 