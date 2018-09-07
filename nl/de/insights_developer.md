---

copyright:
  years: 2016, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Developer Insights
{: #gettingstarted}

Mit {{site.data.keyword.DRA_full}} Developer Insights können Sie die Risiken bei der Entwicklung Ihres Projekts umfassend untersuchen. Sie können fehleranfällige Dateien ermitteln und eine Konformitätsansicht des Projekts im Hinblick auf die DevOps-Verfahren erhalten.
{:shortdesc}

Klicken Sie nach dem Öffnen von {{site.data.keyword.DRA_short}} über die Toolchain auf **Developer Insights**. Von hier aus können Sie eine Analysekategorie auswählen, um einen tieferen Einblick in die Codebasis Ihres Projekts zu erhalten. Was einzelne Datensätze aussagen, kann von Team zu Team unterschiedlich sein. Sie können daher für jede Visualisierung einen Drilldown durchführen, um eine weitere Orientierungshilfe zu erhalten. 

## Datenkategorien
Für die Daten, die von {{site.data.keyword.DRA_short}} zum Auffüllen der Dashboards verwendet wird, wird automatisch ein Mining aus dem Repository für die Quellcodeverwaltung des Teams durchgeführt. Weitere Informationen zur Bedeutung der Daten und zu Anwendungsmöglichkeiten für Ihr Projekt erhalten Sie durch Klicken auf **Informationen** oder **Anweisungen** in einem Diagramm.

### Bewährte Verfahren für Entwickler

Developer Insights stellt eine Reihe von Diagrammen bereit, anhand derer Sie Ihr Projekt gegenüber bewährten DevOps- und Entwicklerverfahren messen können. Verwenden Sie diese Kategorie, um eine übergeordnete Ansicht über den Reifegrad, den Zustand und die Effizienz Ihres Projekts zu erhalten. 

### Probleme

Die Kategorie 'Probleme' fasst alle Probleme bei der Leistungserfassung für Ihr Team zentral zusammen. Die Probleme werden automatisch nach Typ, Priorität und Tag gruppiert und können im Zeitverlauf angezeigt werden. 

Diese Problemgruppierungen können sich von Team zu Team in ihrer Bedeutung unterscheiden. Für ein Team könnte es beispielsweise interessant sein, ob die meisten mit Tags versehenen Elemente für ein bestimmtes Release geschlossen sind, während ein anderes Team Releases nicht mit Tags versieht und diese gemäß der Priorität der offenen Probleme verarbeitet.  

### Commits

Commits zeigen den Arbeitsumfang an, den Ihre Teammitglieder zur Codebasis beitragen. Untersuchen Sie Ihre Commitdaten, um zu verstehen, an welcher Stelle im Zeitverlauf gesehen ein großer Aufwand betrieben wird und wie Sie die Arbeitslasten Ihres Teams besser verteilen können. 

### Pull-Anforderungen

Mit Pull-Anforderungen kann der Code angezeigt werden, den Teammitglieder in einen anderen Zweig mergen.  Analysieren Sie die Pull-Anforderungsdaten, um die Risiken auszuwerten, die mit dem Hinzufügen von neuem Code in einen neuen Codezweig verbunden sind.

### Dateien

Die Kategorie 'Dateien' zeigt, welche Dateien in Ihrem Projekt am häufigsten verwendet werden. Ganz gleich, ob Sie Daten anhand der Anzahl der Zeilenänderungen, Commits, Autoren oder Fehler bewerten: Diese Daten verraten Ihnen, in welchen Bereichen Ihr Team besonders aktiv ist. Darüber hinaus können Sie das mit Ihren Dateien verbundene Risiko anzeigen, indem Sie die Registerkarte für die Fehleranfälligkeit von Dateien aufrufen.

Versuchen Sie allgemein sowohl die Anzahl der Mitglieder zu verringern, die eine Datei bearbeiten dürfen, als auch die Häufigkeit, mit der diese Datei geändert wird. Dieses Ziel kann jedoch für einige Dateien, wie allgemeine Konfigurationsdateien, unrealistisch sein. Jedoch sind für einzelne Dateien, an denen Entwickler gleichzeitig viele Änderungen vornehmen, Probleme vorprogrammiert. 

DevOps Insights ignoriert Dateien mit den folgenden Erweiterungen:
* .bin
* .cdr
* .jpeg
* .jpg
* .json
* .markdown
* .md
* .png
* .pyc
* .svg
* .text
* .yaml
* .yml
{: tip}
