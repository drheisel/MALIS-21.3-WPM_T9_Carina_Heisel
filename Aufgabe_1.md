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

Eine potentielle Verbesserungsmöglichkeit für die Revisionslisten liegt im Format der bereitgestellten CSV-Datei. Die einzelnen Schritte beim Import in Excel ließen sich vermeiden, wenn die Werte der CSV tabulatorgetrennt wären, die führenden Leerzeichen vor Zahlenangaben (bei Vormerkungen und Ausleihzahlen) gar nicht erst da wären und die Zeichenkodierung so wäre, dass Excel sofort etwas damit anfangen kann.

Diese Punkte stehen auf der ToDo-Liste für das nächste zu programmierende Revisionslisten-Extraktionstool. Da die UB noch diesen Sommer von Aleph auf ALMA umsteigen wird, wird das aktuelle Tool nicht mehr angepasst werden.


### Kauf von eBooks und Neuauflagen aufgrund hoher Ausleihzahlen

##### Verbesserungsmöglichkeiten


### Aussondern von ungenutzter und inaktueller Literatur

##### Verbesserungsmöglichkeiten


## Etatlisten


### Hochrechnung von Fachbereichsetats

##### Verbesserungsmöglichkeiten
