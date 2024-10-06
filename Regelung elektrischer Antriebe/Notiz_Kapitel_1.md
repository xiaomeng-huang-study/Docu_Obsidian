# Einfach Integrierendes System (EIS) 
- <img src="https://github.com/ICH-BIN-HXM/images_REA/blob/main/Scrennshot_2024-10-06_11-17-00.png?raw=" width="30%" /> 
- $\mathrm{F}_{0}(\mathrm{s})=\frac{1}{\mathrm{sT}_{0}}$ 
- $\mathrm{F}_{\mathrm{W}}(\mathrm{~s})=\frac{1}{1+\mathrm{sT}_{0}}$ 
## Nachteile 
- Stellglieder häufig mit Verzögerungsverhalten 
- ein Glättungsglied zur Aufbereitung des Istwertsignals und zur Unterdrückung von Störeinflüssen fehlt 

# EIS mit nichtkompensierbarem Glied 
## PT1-Glied 
- nichtkompensierbares Glied
	- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\frac{1}{1+\mathrm{sT}_{1}}$ 
- offener Regelkreis 
	- $\mathrm{F}_{0}(\mathrm{s})=\frac{1}{\mathrm{sT}_{0}} \cdot \frac{1}{1+\mathrm{sT}_{1}}$ 
- geschlossener Regelkreis 
	- $\mathrm{F}_{\mathrm{W}}(\mathrm{s})=\frac{1}{1+\mathrm{sT}_{0}+\mathrm{s}^{2} \mathrm{~T}_{0} \mathrm{~T}_{1}}$ 
## Totzeitglied 
- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\mathrm{e}^{-\mathrm{s} \mathrm{~T}_{\mathrm{t}}} \approx \frac{1}{1+\mathrm{sT}_{\mathrm{t}}}$ 
	- $\Rightarrow$ $T_{t}\approx T_{1} ~~\text{in PT1-Glied}$ 
## Allpassglied 
- $\mathrm{F}_{\mathrm{SNK}}(\mathrm{s})=\frac{1-\mathrm{sT}_{\mathrm{a}}}{1+\mathrm{sT}_{\mathrm{a}}} \approx \frac{1}{\left(1+\mathrm{sT}_{\mathrm{a}}\right)\left(1+\mathrm{sT}_{\mathrm{a}}\right)} \approx \frac{1}{1+\mathrm{s} \cdot 2 \mathrm{T}_{\mathrm{a}}}$ 
- 