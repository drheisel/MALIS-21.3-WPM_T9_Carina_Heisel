# Beschreibung von datenintensiven und datenfokussierten Aktivitäten im eigenen Arbeitsalltag / in der eigenen Institution

*Carina Heisel, Kaiserslautern, Mai 2022*


## Überblick

In der Universitätsbibliothek (UB) der Technischen Universität Kaiserslautern (TUK) fallen an vielen Stellen Daten an, die aufgrund ihrer Menge und Komplexität idealerweise automatisiert mit Skripten o. ä. verarbeitet werden. Bei vielen dieser Daten geschieht dies bereits weitestgehend automatisiert. Klassische Beispiele für solche Prozesse sind z. B. der Betrieb und die Pflege zentraler Systeme wie **Bibliothekskatalog** (*Aleph*), **Discoverysystem** (*VuFind*)[^1], **Dokumentenserver** (*KLUEDO*)[^2] und **elektronische Tauschbörse** (*ELTAB*)[^3].

[^1]: https://kplus.ub.uni-kl.de
[^2]: https://kluedo.ub.uni-kl.de
[^3]: https://eltab.ub.uni-kl.de

An einigen Stellen ist trotz Teilautomatisierung noch einiges an "Handarbeit" notwendig.
Die IT-Abteilung der UB hat mehrere CronJobs (periodisch wiederkehrende Aufgaben/Prozesse) angelegt, die diverse Listen im CSV- oder HTML-Format erzeugen. Diese können dann von den Mitarbeitenden heruntergeladen und beliebig weiterbearbeitet werden.
- So wird immer am Monatsersten ein **Abgangsbuch** für den Vormonat erstellt.
- Jede Nacht wird eine tagesaktuelle **Revisionsliste** pro Signaturengruppe erzeugt.
- Außerdem werden einmal pro Nacht alle **Etatlisten** aktualisiert, sodass diese für jeden Etat tagesaktuell abrufbar sind.

In meinem Berufsalltag als Fachreferentin sind vor allem die Etat- und Revisionslisten ein wichtiges Werkzeug. Anhand der *Etatlisten* treffe ich **Kaufentscheidungen** und erstelle **Hochrechnungen** für die einzelnen Fachbereiche der TUK. Die *Revisionslisten* nutze ich vorrangig, um einen Überblick über **Ausleihzahlen** und **Aktualität** der Literatur zu bekommen. Daraus leite ich dann **Kaufentscheidungen** und **Aussonderungen** ab.


## Revisionslisten

Eine Revisionsliste ist eine vollständige Liste des aktuellen Bestandes. Sie enthält alle physischen Medien einer Signaturengruppe mit zahlreichen zugehörigen Informationen.\
Als wichtigste Informationen sind hier zu nennen:
- die eindeutige Signatur, die wie folgt aufgebaut ist: XXX aaa/bbb mit\
  XXX = Signaturengruppe (z. B. PHY für Physik)\
  aaa = Fachgruppe, Zahl zwischen 000 und 999\
	bbb = fortlaufende Nummer, Zahl zwischen 000 und 999
- Autor*in, Titel
- Auflage und ISBN
- Erscheinungsjahr und Jahr des Zugangs
- Vormerkungen (insgesamt und in den letzten beiden Jahren)
- Ausleihzahlen (insgesamt und in den letzten 1/2/5 Jahren)
- letztes Ausleih- und Rückgabedatum

Die Informationen werden als CSV-Datei zur Verfügung gestellt. Um Sortier-, Filter- und Rechenfunktionen auf die Daten anwenden zu können, importiere ich die CSV zunächst in eine Excel-Tabelle, wandle sie also in eine XLSX um.
Der Import erfordert einiges an Einstellungen und Nacharbeiten, um die Liste anschließend fehlerfrei weiterbearbeiten zu können. So sind die einzelnen Einträge z. B. nicht tabulatorgetrennt, sondern mit einer Tilde (~) separiert. Zudem sind Unmengen von Leerzeichen enthalten, die vorab entfernt werden müssen, da Zahlen ansonsten als Text fehlinterpretiert werden. Außerdem muss die Zeichenkodierung richtig eingestellt werden, um Umlaute korrekt wiederzugeben.

##### Verbesserungsmöglichkeiten

Eine potenzielle Verbesserungsmöglichkeit für die Revisionslisten liegt im Format der bereitgestellten CSV-Datei. Die einzelnen Schritte beim Import in Excel ließen sich vermeiden, wenn die Werte der CSV tabulatorgetrennt wären, die führenden Leerzeichen vor Zahlenangaben (bei Vormerkungen und Ausleihzahlen) gar nicht erst da wären und die Zeichenkodierung so wäre, dass Excel sofort etwas damit anfangen kann.

Diese Punkte stehen auf der ToDo-Liste für das nächste zu programmierende Revisionslisten-Extraktionstool. Da die UB noch diesen Sommer von Aleph auf ALMA umsteigen wird, wird das aktuelle Tool nicht mehr angepasst werden.


### Kauf von eBooks und Neuauflagen aufgrund hoher Ausleihzahlen

Wird ein Medium oft ausgeliehen oder ist es sogar ständig vergriffen und wird daher oft vorgemerkt, müssen weitere Exemplare angeschafft werden.

Wie finde ich das heraus?
- Anzahl der Vormerkungen in den letzten 2 Jahren
- Ausleihzahlen im letzten Jahr

Tendenz zu eBooks, da Digitalisierung

##### Verbesserungsmöglichkeiten

Zur Zeit überprüfe ich die Revisionsliste händisch auf "beliebte" Medien. Dabei wäre es möglich, diesen Prozess mit einer relativ einfachen Programmierung zu automatisieren.
- Schwelle für Ausleihen im letzten Jahr festlegen
- Schwelle für Vormerkungen (2J) festlegen
- Bei Überschreiten eines der Werte wird eine Markierung gesetzt (Excel) oder eine Ausgabe erzeugt (Shell)


### Aussondern von ungenutzter und inaktueller Literatur

Das Aussondern von ungenutzter und inaktueller Literatur ist etwas komplizierter gelagert als im Fall der beliebten Medien.\
Kriterien, die hierzu herangezogen werden, sind:
1. keine Ausleihen in den letzten 5 Jahren
2. keine Vormerkungen in den letzten 2 Jahren
3. letzte Rückgabe länger als 10 Jahre her
4. Medium älter als 20 Jahre oder Themengebiet ändert sich schnell (z. B. Informatikthemen)

Außerdem sind folgende Punkte zu beachten:
- Wie viele Exemplare haben wir mit der gleichen Signatur? Wie sind die Ausleihzahlen der anderen Medien?
- Welche Auflagen haben wir von dem Medium? Wie viele Jahre liegen zwischen der aktuellsten und den vorherigen Auflagen?
- Steht das Medium im Semesterapparat und ist deshalb auf jeden Fall vorzuhalten?

Bei der Aussonderung läuft es meist auf eine Individualentscheidung hinaus, in die zudem auch Erfahrungswissen und ggf. Rücksprachen mit Lehrstühlen einfließen. Hier ist eine Automatisierung schwer bis gar nicht umsetzbar.

##### Verbesserungsmöglichkeiten

Dennoch kann der Prozess auch hier vereinfacht oder abgekürzt werden. Anhand der oben genannten Kriterien Nr. 1 – 3 könnte eine Liste erstellt werden, die in bestimmten Zeitabständen überprüft und als Einstieg für Aussonderungsentscheidungen genutzt werden kann. Als Grundlage für die Programmierung kann eine angepasste Version der "beliebte Medien"-Liste dienen.


## Etatlisten


### Hochrechnung von Fachbereichsetats

##### Verbesserungsmöglichkeiten
