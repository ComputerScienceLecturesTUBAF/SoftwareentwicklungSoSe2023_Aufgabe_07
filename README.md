# Softwareentwicklung SoSe2021 - Aufgabe 06

??

## Bearbeitungzeit

SWE: ?? 2021 (Mm, BWM, ROB, BAI, BGIP, BBWL, BBL, MGIN)

Einführung in SWE: ?? 2021 (KGB, BENG, VTC, MB)

## Entwicklung einer Mobilfunkinfrastruktur

Sie setzen im Auftrag eines Kommunikationsdienstleisters einen neuen `Kommunikationskoordinator` um, der die Interaktion mit unterschiedlichen Endgeräten realsiert. Dabei sollen die Endgeräten in einer Gesamtliste erfasst werden und verschiedene Services dafür abgebildet werden: 

| Konfiguration   | eingebundene Geräte                          |
|-----------------|----------------------------------------------|
| einzelnes Gerät | Auslösen eines Alarmklingelns, Lokalisierung | 
| Gerätepaar      | Sprachanruf                                  |

Dabei soll die Logik des `Kommunikationskoordinators` Fehler abfangen, wenn zum Beispiel eine Nummer nicht bekannt ist, ein Gerät deaktiviert ist oder eine nicht unterstützte Version des Betriebssystems ausführt. 

Da der Kunde Ihre Lösung nicht auf die realen Geräte seiner Nutzer "loslassen" möchte, werden Sie beauftragt die Leistungsfähigkeit des `Kommunikationskoordinator` zunächst in einer Simulationsumgebung zu zeigen. Diese liest Konfigurationsdateien ein und testet die angeführten Serviceanforderungen. In dieser Liste werden dann auch Serviceaufrufe realsiert, die einen Fehler generieren sollen (fehlendes Endgerät zu einer Rufnummer, ausgeschaltetes Gerät usw.) Der Kunde möchte am Ende eine Ergebnisliste erhalten, anhand derer die Funktionalität Ihrer Implementierung getestet werden kann. 

``` 
                            +----------------------------------------+
                            | ServicesTests.csv                      |
                            |  1 02234 ruft 23424                    |
                            |  2 02234 ruft 0000 (unbekannte Nummer) |
                            |  3 Alarmklingeln für 012332            |
                            |  4 Positionsinformation für 023432     |
                            +----------------------------------------+
                                                |
                                                v
 +----------------------+      +-----------------------------------+      +---------------+
 | SmartphoneData.csv   |      | MobilfunkSimulation               |      | Ergebnis.csv  |
 |  - Telefonnummer     |      |                                   |      | 1 erfolgreich |
 |  - Betriebssystem    | -->  |  +-----------------------------+  | -- > | 2 gescheitert |
 |  - Telefonstatus     |      |  | KommunikationsKoordinator   |  |      | 3 erfolgreich |
 |  - Verbindungsstatus |      |  |                             |  |      | 4 gescheitert |
 |  - Position          |      |  | SmartPhone Instanzen        |  |      +---------------+
 +----------------------+      |  +-----------------------------+  |
                               +-----------------------------------+
```

Setzen Sie die Aufgabe in drei Stufen um: 

1. Dafür entwirft zunächst der Senior Developer (und Projekt Maintainer) eine Klassenstruktur in UML mit PlantUML. Legen Sie das Diagramm als Bild im Issue "UML_Modell" ab, diskutieren Sie den Entwurf mit Ihrem Partner und verfeinern Sie diesen ggf.
2. Teilen Sie sich die Aufgaben auf ordnen Sie diese in Issues zu und implementieren Sie diese. 
3. Der Senior Developer entwirft variierende Implementierungen von `ServicesTests.csv` und `SmartphoneData.csv` und tauscht diese ggf. mit anderen Teams aus. Beide prüfen in den jeweiligen Verantwortlichkeiten, die Korrektheit der Ergebnisse und bessern ggf. nach.

## Hilfen 

+ Die beispielhafte Dateien für SmartphoneData.csv und ServicesTests.csv finden sich in Projektordner.
+ Das Einlesen von csv Inhalten wird in [DeserializationInCsharp](https://www.youtube.com/watch?v=kuOb8_U2jzE) erläutert.
