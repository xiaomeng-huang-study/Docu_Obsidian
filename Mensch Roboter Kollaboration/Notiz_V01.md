# Systemintegration 
## Begriffsklärung 

## Ablauf für neue Roboteranlagen 


# Inverkehrbringen von Roboteranlagen 
## Gesetzlicher Hintergrund 

## Risikobeurteilung und Gefährdungsbeurteilung 
### Risikobeurteilung 
- Durchführende 
	- **Roboterhersteller** bewertet **inhärente** Robotergefährdungen 
	- **Systemintegrator** bewertet Gefährdungen des **Gesamtsystems** 
- Konkrete Inhalte 
	- Bewertung der Risikostufen 
	- Entwicklung von Risikominderungsmaßnahmen 
- Rechtsgrundlagen 
	- Maschinenverordnung 
	- DIN EN ISO 12100 
- Ergebnis 
	- CE-Kennzeichnung und technische Dokumentation 

### Gefährdungsbeurteilung 
- Durchführende 
	- **Endkunde** bewertet konkrete Arbeitsplatzgefährdungen 
- Konkrete Inhalte 
	- Berücksichtigung von Betriebsumgebung, Mitarbeiterqualifikation, Arbeitsabläufen 
- Rechtsgrundlagen 
	- BetrSichV 
- Ergebnis 
	- Betriebsanweisungen und Mitarbeiterschulungen 

## Normen 
### Normenhierarchie 
- Typ A, B, C 
### Konkrete Normen 
#### DIN EN ISO 12100 (Typ A) 
- Dreistufige Risikominimierung 

#### DIN EN ISO 13849-1 (Typ B) 
- Kategorien (Gemäß Kanälen) 
	- B, 1, 2, 3, 4 
- Performance Level (Gemäß Schwere des Schadens, Häufigkeit, Möglichkeit zur Abwendung eines gefährlichen Ausfalls) 
	- a, b, c, d, e 

#### DIN EN ISO 10218 
- Kategorie 3 (Zweikanalig, mit Fehlererkennung) , PL d ($10^{-7}$ bis $10^{-6}$) 

##### DIN EN ISO 10218-1 Roboter 
- Not-Halt-Funktionen 
	- mindestens eine ist Kategorie 0 oder 1 
		- Kategorien: Kategorie 0: Energiezufuhr sofort getrennt; Kategorie 1: Sicherer Zustand, dann Energie getrennt; Kategorie 2: Sicherer Zustand, Energie nicht getrennt. 
- Betriebsarten 
	- Manuell mit reduzierter Geschwindigkeit (maximal 250 mm/s) 
	- Manuell mit hoher Geschwindigkeit 
	- Automatik 
- Dreistufige Zustimmungseinrichtung 
	- Ruhestellung 
	- Freigabestellung 
	- Panikstellung 

##### DIN EN ISO 10218-2 Robotersysteme und Integration 
###### Definition Integration 
- Einen Roboter mit anderen Maschinen zusammenzuführen, um ein Maschinesystem zu bilden. 

###### Kernprozess der Risikominderung: Gestaltung der Anordnung (Layout) 
- Berücksichtigung: Physikalische Grenzen der Zelle; Arbeitsräume, Zugänge, Freiräume usw. 
- Stoppfunktionen der **gesamten** Roboterzelle 
	- mindestens eine ist Kategorie 0 oder 1 
- Betriebsarten 
	- Manuell 
	- Automatik 
- Zustimmungseinrichtungen für **alle Personen**, die sich im geschützten Bereich aufhalten 

###### Äußere Schutzeinrichtungen 
- trennende Schutzeinrichtungen 
	- Schutzzäune (DIN EN ISO 13857): Fest eingebaut, Mindestsicherheitsabstände 
- nichttrennende Schutzeinrichtungen 
	- Lichtvorhänge (DIN EN ISO 13855): Nachlaufzeit und Annäherungsgeschwindigkeit 
- Türsysteme: Geschlossen $\rightarrow$ Automatikbetrieb möglich; Geöffnet $\rightarrow$ nur manueller Betrieb (Lockout-Tagout) 

