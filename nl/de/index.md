---

copyright:
  years: 2016, 2018
lastupdated: "2018-4-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Einführung in DevOps Insights (Beta)
{: #gettingstarted}

{{site.data.keyword.DRA_full}} wendet Analysen für Entwickler, Teams und die Bereitstellung auf Ihre wichtigsten DevOps-Projekte an. Mithilfe dieser Komponente können Sie ermitteln, wie konform Ihr Team mit DevOps und Entwicklerverfahren arbeitet. Außerdem ist sie ideal für das Risikomanagement Ihrer Codebasis und die automatische Durchsetzung von Qualitätsstandards in Continuous Delivery-Projekten.
{:shortdesc}

**Hinweis**: {{site.data.keyword.DRA_short}} ist nur in der Region 'Vereinigte Staaten (Süden)' verfügbar.

{{site.data.keyword.DRA_short}} umfasst mehrere verschiedene Leistungsmerkmale:

   * Mit Developer Insights können Sie den Entwicklungsstand (Reife) Ihres Projekts umfassend untersuchen. Sie können fehleranfällige Dateien ermitteln und eine Konformitätsansicht des Projekts im Hinblick auf die Entwicklerverfahren erhalten.

   * Team verwendet soziale Codeanalysen, mit denen Sie feststellen können, wie gut Ihr Team zusammenarbeitet und wie diese Zusammenarbeit noch verbessert werden kann.

   * Deployment Risk fungiert als Sicherheitsnetz für Continuous Delivery. Die Komponente analysiert die Ergebnisse aus Komponententests, Funktionstests, Sicherheitsscans, Anwendungsscans und Codeabdeckungstools an bestimmten Gates in Ihrem Entwicklungsprozess und verhindert, dass riskante Änderungen freigegeben werden. Es werden Diagramme für Trends bei der Codeabdeckung, Builds und Bereitstellungen angezeigt.

Bei {{site.data.keyword.DRA_short}} handelt es sich um eine Integration mit dem offenen Toolchain-Katalog von Bluemix. Weitere Informationen zu Toolchains finden Sie in [Arbeiten mit Toolchains](/docs/services/ContinuousDelivery/toolchains_working.html).

Um {{site.data.keyword.DRA_short}} verwenden zu können, müssen Sie die Komponente zu einer Toolchain hinzufügen. Viele Toolchain-Vorlagen enthalten bereits {{site.data.keyword.DRA_short}}. [Fügen Sie die Komponenten außerdem unbedingt zu Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation als Service hinzu](/docs/services/reqnsi.html), damit Sie Informationen zu {{site.data.keyword.DRA_short}} anzeigen und über das {{site.data.keyword.Bluemix_notm}}-Dashboard auf einige der Toolchain-Vorlagen zugreifen können, die {{site.data.keyword.DRA_short}} enthalten.  

Darüber hinaus führt IBM Developer Insights und Team für eine Vielzahl der erfolgreichsten Open-Source-Projekte in GitHub aus. Rufen Sie [DevOpsInsights.io](http://devopsinsights.io/) auf, um die entsprechenden Entwicklungs- und Teamdaten anzuzeigen.

## DevOps Insights zu einer Toolchain hinzufügen
{: #catalog}

{{site.data.keyword.DRA_short}} steht über eine Integration mit Toolchains von
{{site.data.keyword.contdelivery_full}} zur
Verfügung. Sie können {{site.data.keyword.DRA_short}} zu jeder Toolchain hinzufügen, indem Sie die Komponente aus dem Toolintegrationskatalog auswählen.

{{site.data.keyword.DRA_short}} ist zudem in vielen Toolchain-Vorlagen enthalten. Wenn Sie eine Toolchain aus einer Vorlage erstellen, die {{site.data.keyword.DRA_short}} enthält, stellen Sie sicher, dass {{site.data.keyword.DRA_short}} auf **Erweitert** gesetzt ist. Erstellen Sie dann die Toolchain und fahren Sie mit dem Abschnitt [Insights verwenden](/docs/services/DevOpsInsights/index.html#using) fort.

Führen Sie die folgenden Schritte aus, um {{site.data.keyword.DRA_short}} zu einer Toolchain hinzuzufügen:

1. Klicken Sie auf **Tool hinzufügen**.

2. Klicken Sie auf **{{site.data.keyword.DRA_short}}**.

3. Klicken Sie auf **Integration erstellen**.

{{site.data.keyword.DRA_short}} ist nun auf der Übersichtsseite Ihrer Toolchain verfügbar. Das Repository und das Problemverfolgungssystem werden automatisch nach Daten durchsucht.

## DevOps Insights verwenden
{: #using}

Wenn Ihre Toolchain GitHub, GitLab oder JIRA enthält, stellt Ihnen {{site.data.keyword.DRA_short}} automatisch nach einer anfänglichen Datenerfassung und -analyse Informationen zu Ihrer Codebasis und Ihrem Team bereit. Wenn Ihre Toolchain keine dieser Integrationen umfasst, fügen Sie eine dieser Integrationen hinzu und führen Sie dann die folgenden Schritte aus:

1. Klicken Sie auf der Übersichtsseite der Toolchain auf **{{site.data.keyword.DRA_short}}**.

2. Klicken Sie auf **Team** oder **Developer Insights** und wählen Sie dann eine Datenkategorie aus.

3. Untersuchen Sie die Projektdaten, indem Sie die Dashboards in der Datenkategorie anzeigen. Wenn Sie mehr über ein Diagramm oder darüber wissen möchten, wie Sie die darin enthaltenen Informationen verarbeiten sollen, klicken Sie auf **Informationen** oder **Anweisungen**.

Konfigurieren Sie nach der Durchsicht von Team und Developer Insights [Deployment Risk](/docs/services/DevOpsInsights/about_risk.html), um Codequalität durchsetzen zu können. Deployment ist sowohl mit Delivery Pipeline for {{site.data.keyword.contdelivery_short}} als auch mit Jenkins kompatibel.
