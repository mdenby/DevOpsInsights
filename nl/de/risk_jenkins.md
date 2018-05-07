---

copyright:
  years: 2016, 2018
lastupdated: "2018-3-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Integration mit unformatierten Jenkins-Projekten

Nach dem Hinzufügen von {{site.data.keyword.DRA_full}} zu einer offenen Toolchain und dem Definieren der von dieser Komponente überwachten Richtlinien können Sie sie mit Ihrem unformatierten Jenkins-Projekt integrieren. Unformatierte Jenkins-Projekte werden über die Jenkins-Webschnittstelle konfiguriert und verwaltet. 

Das IBM Cloud DevOps-Plug-in für Jenkins integriert Jenkins-Projekte mit Toolchains. Eine _Toolchain_ ist eine Gruppe von Toolintegrationen, die Entwicklungs-, Bereitstellungs- und Operationsaufgaben unterstützen. Das Gesamtpotenzial einer Toolchain ist größer als die Summe ihrer einzelnen Toolintegrationen. Offene Toolchains sind Teil des {{site.data.keyword.contdelivery_full}}-Service. Weitere Informationen zum {{site.data.keyword.contdelivery_short}}-Service finden Sie in der [entsprechenden Dokumentation](https://console.ng.bluemix.net/docs/services/ContinuousDelivery/cd_about.html).

Nach der Installation des IBM Cloud DevOps-Plug-ins können Sie Testergebnisse in {{site.data.keyword.DRA_short}} veröffentlichen, automatisierte Qualitätsgates hinzufügen und Ihre Bereitstellungsrisiken verfolgen. Außerdem können Sie Jobbenachrichtigungen an andere Tools, wie Slack und PagerDuty, in Ihrer Toolchain senden. Damit Sie Ihre Bereitstellungen besser überwachen können, können über die Toolchain Bereitstellungsnachrichten zu Git-Commits und deren zugehörige Git- oder JIRA-Probleme hinzugefügt werden. Zudem können Sie Ihre Bereitstellungen auf der Verbindungsseite der Toolchain anzeigen. 

Das Plug-in stellt Aktionen für den Buildabschluss sowie Befehlszeilenschnittstellen für die Unterstützung der Integration zur Verfügung. {{site.data.keyword.DRA_short}} aggregiert und analysiert die Ergebnisse aus Komponententests, Funktionstests, Codeabdeckungstools und dynamischen Sicherheitsscans, um zu bestimmen, ob Ihr Code an Gates in Ihrem Bereitstellungsprozess den vordefinierten Richtlinien entspricht. Entspricht Ihr Code keiner Richtlinie oder überschreitet Ihr Code eine Richtlinie, wird die Bereitstellung angehalten; dadurch wird verhindert, dass sicherheitsbedenkliche Änderungen freigegeben werden. Sie können {{site.data.keyword.DRA_short}} als Sicherheitsnetz für Ihre Continuous Delivery-Umgebung, als Möglichkeit der Implementierung und Verbesserung der Qualitätsstandards über einen Zeitraum hinweg sowie als Datenvisualisierungstool für Informationen zum Projektstatus verwenden.

## Voraussetzungen
{: #jenkins_prerequisites}

Sie müssen über Zugriff auf den Server verfügen, auf dem das Jenkins-Projekt ausgeführt wird.

## Eine Toolchain erstellen
{: #jenkins_create}

Bevor Sie {{site.data.keyword.DRA_short}} mit einem Jenkins-Projekt integrieren können, müssen Sie eine Toolchain erstellen. 

1. Rufen Sie zum Erstellen einer Toolchain die [Seite zum Erstellen einer Toolchain](https://console.ng.bluemix.net/devops/create) auf und befolgen Sie die Anweisungen auf dieser Seite. 

2. Nachdem Sie die Toolchain erstellt haben, fügen Sie {{site.data.keyword.DRA_short}} zu dieser Toolchain hinzu. Anweisungen hierzu finden Sie in der [{{site.data.keyword.DRA_short}}-Dokumentation](https://console.ng.bluemix.net/docs/services/DevOpsInsights/index.html). 

## Plug-in installieren
{: #jenkins_install}

Installieren Sie zuerst das Plug-in auf dem Jenkins-Server. Öffnen Sie die Serverschnittstelle und führen Sie dann die folgenden Schritte aus:

1. Klicken Sie auf **Jenkins verwalten**.
2. Klicken Sie auf **Plug-ins verwalten**. 
3. Klicken Sie auf die Registerkarte **Verfügbar**.
4. Filtern Sie nach `IBM Cloud DevOps`. 
5. Wählen Sie IBM Cloud DevOps aus.
6. Klicken Sie auf **Jetzt herunterladen und nach dem Neustart installieren**. 

Das Plug-in ist nach dem Neustart des Servers verfügbar.  

## Jenkins-Jobs für das Deployment Risk-Dashboard konfigurieren
{: #jenkins_configure}

Nachdem das Plug-in installiert wurde, können Sie {{site.data.keyword.DRA_short}} in Ihr Jenkins-Projekt integrieren. 

Führen Sie die folgenden Schritte aus, um Deployment Risk-Gates und das Deployment Risk-Dashboard mit Ihrem Projekt verwenden zu können.

1. Öffnen Sie die Konfiguration eines vorhandenen Jobs (z. B. Build, Test oder Bereitstellung).

2. Fügen Sie eine Buildabschlussaktion für den entsprechenden Typ hinzu:

   * Verwenden Sie für Build-Jobs den Typ **Publish build information to IBM Cloud DevOps**.
   
   * Verwenden Sie für Testjobs den Typ **Publish test result to IBM Cloud DevOps**.
   
   * Verwenden Sie für Bereitstellungsjobs den Typ **Publish deployment information to IBM Cloud DevOps**.
   
3. Füllen Sie die erforderlichen Felder aus. Diese können je nach Jobtyp anders sein. 

   * Wählen Sie aus der Liste **Credentials** Ihre {{site.data.keyword.Bluemix_notm}}-ID und Ihr Kennwort aus. Sind diese nicht in Jenkins gespeichert, klicken Sie auf die Option zum Hinzufügen, um sie hinzuzufügen und zu speichern. Testen Sie die Verbindung mit {{site.data.keyword.Bluemix_notm}}, indem Sie auf **Test Connection** klicken.
   
   * Geben Sie im Feld für den Namen des Build-Jobs den Namen Ihres Build-Jobs genau wie in Jenkins an. Lassen Sie dieses Feld leer, wenn der Build-Job zeitlich mit dem Testjob zusammenfällt. Wenn es außerhalb von Jenkins zu dem Build-Job kommt, aktivieren Sie das Kontrollkästchen **Builds are being done outside of Jenkins** und geben Sie die Buildnummer und die Build-URL an.
   
   * Wenn die Tests in der Umgebung in der Buildstufe ausgeführt werden, wählen Sie nur die Buildumgebung aus. Wenn die Tests in der Bereitstellungsstufe ausgeführt werden, wählen Sie die Bereitstellungsumgebung aus und geben Sie den Umgebungsnamen an. Es werden zwei Werte unterstützt: `STAGING` und `PRODUCTION`.
   
   * Geben Sie den Speicherort der Ergebnisdatei im entsprechenden Feld an. Wenn durch den Test keine Ergebnisdatei generiert wird, lassen Sie dieses Feld leer. Durch das Plug-in wird eine auf dem Status des aktuellen Testjobs basierende Standardergebnisdatei hochgeladen.

   Die nachfolgenden Abbildungen zeigen Beispielkonfigurationen:
   
   ![Buildinformationen hochladen](images/Upload-Build-Info.png "Buildinformationen in DRA veröffentlichen")
   _Buildinformationen veröffentlichen_
   
   ![Testergebnis hochladen](images/Upload-Test-Result.png "Testergebnis in DRA veröffentlichen")
   _Testergebnis veröffentlichen_
   
   ![Bereitstellungsinformationen hochladen](images/Upload-Deployment-Info.png "Bereitstellungsinformationen in DRA veröffentlichen")
   _Bereitstellungsinformationen veröffentlichen_

4. Wenn Sie {{site.data.keyword.DRA_short}}-Richtliniengates zum Steuern eines nachfolgenden Bereitstellungsjobs verwenden möchten, fügen Sie eine Buildabschlussaktion des Typs **IBM Cloud DevOps Gate** hinzu. Wählen Sie eine Richtlinie aus und geben Sie den Gültigkeitsbereich der Testergebnisse an. Damit Richtliniengates nachfolgende Bereitstellungen verhindern können, aktivieren Sie das Kontrollkästchen **Fail the build based on the policy rules**. Die folgende Abbildung zeigt eine Beispielkonfiguration:

    ![DevOps Insights-Gate](images/DRA-Gate.png "DevOps Insights-Gate")

5. Führen Sie den Jenkins-Build-Job aus.

6. Zeigen Sie das Deployment Risk-Dashboard an, indem Sie [{{site.data.keyword.Bluemix_notm}} DevOps](https://console.ng.bluemix.net/devops) aufrufen, Ihre Toolchain auswählen und auf **DevOps Insights** klicken.

Das Deployment Risk-Dashboard ist nach einem Staging-Bereitstellungsjob auf das Vorhandensein eines Gates angewiesen. Wenn Sie das Dashboard verwenden möchten, stellen Sie sicher, dass nach der Bereitstellung für eine Staging-Umgebung (jedoch vor der Bereitstellung für eine Produktionsumgebung) ein Gate vorhanden ist.
    
## Benachrichtigungen konfigurieren
{: #jenkins_notifications}

Sie können die Jenkins-Jobs so konfigurieren, dass Benachrichtigungen an Tools wie Slack oder PagerDuty gesendet werden, indem Sie die Anweisungen in der entsprechenden [{{site.data.keyword.Bluemix_notm}}-Dokumentation](https://console.ng.bluemix.net/docs/services/ContinuousDelivery/toolchains_integrations.html#jenkins) befolgen.
