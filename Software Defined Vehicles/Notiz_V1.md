# E/E Architekturen 
- Domänenbasierte Architektur 
	- Steuergeräte (ECUs) sind nach spezifischen Fahrzeugfunktionen gruppiert. 
	- Typische Domänen sind: 
		- Antriebsstrang (z. B. Motorsteuergerät) 
		- Fahrwerk & Fahrerassistenz (z. B. ESP-Steuergerät) 
		- Infotainment & Cockpit (z. B. Head-Unit) 
		- Karosserie & Komfort (z. B. Türsteuergeräte) 
- Zonenbasierte Architektur 
	- Das Fahrzeug wird in physische Zonen (z. B. vorne links, hinten rechts) unterteilt. In jeder Zone gibt es ein leistungsfähiges Zonensteuergerät (Zone Controller), das die Sensoren und Aktoren in diesem Bereich verwaltet. 

## Vergleich 
| Merkmal            | Domänenbasiert                     | Zonenbasiert                                |
| ------------------ | ---------------------------------- | ------------------------------------------- |
| **Organisation**   | Nach Funktion (z. B. Infotainment) | Nach Fahrzeugbereichen (z. B. Vorderachse)  |
| **Kommunikation**  | CAN, LIN, FlexRay                  | Ethernet (Backbone), CAN für lokale Aktoren |
| **Steuergeräte**   | Viele spezialisierte ECUs          | Wenige leistungsfähige Zonencontroller      |
| **Verkabelung**    | Hoch, komplex                      | Reduziert, effizient                        |
| **Skalierbarkeit** | Eingeschränkt                      | Hoch (OTA-Updates, neue Funktionen)         |

# Software 
## Kommunikation 
- Signalorientiert 
- Serviceorientiert 

## Software 
- Herausforderung: Performance vs. Echtzeitfähigkeit  (AUTOSAR vs. Linux) 

## Feature-Architektur 
- Feature Modell Beispiel 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_Software_Defined_Vehicle/refs/heads/main/Scrennshot_2025-03-25_10-23-00.png?raw=" width="60%" /> 

## Entwicklungsprozess 
- V-Modell 