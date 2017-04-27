---
title: Visio-Shapes in SharePoint Designer 2013 Eine Kurzübersicht (SharePoint 2010-Workflowplattform)
ms.prod: SHAREPOINT
ms.assetid: 51bc37fd-37de-4ad0-a75a-bdf7333bc80c
---



# Visio-Shapes in SharePoint Designer 2013: Eine Kurzübersicht (SharePoint 2010-Workflowplattform)
Sie können einen Workflow in Microsoft Visio Professional 2013 erstellen und diesen dann nach Microsoft SharePoint Designer 2013 exportieren. In diesem Handbuch sind die Visio-Shapes aufgeführt, die Sie zum Erstellen des Workflows verwenden.Verwenden Sie diesen Referenzartikel nur, wenn Sie in SharePoint Designer 2013 arbeiten, weiterhin jedoch die SharePoint 2010-Workflowplattform verwenden möchten.Die Shapes für die SharePoint 2010-Workflowplattform umfassen drei Schablonen: **Aktionen - SharePoint 2010-Workflow**, **Bedingungen - SharePoint 2010-Workflow** und **Abschlusszeichen - SharePoint 2010-Workflow**.
## Workflowaktionen
<a name="section1"> </a>

Workflowaktionen sind bestimmte Vorgänge, die ein Workflow durchführt. Jeder Workflow muss mindestens eine Aktion enthalten.
  
    
    
Die Aktionen in dieser Liste sind in Kategorien basierend auf ihrem Anwendungsbereich in einem Workflow organisiert. Beispielsweise werden die Aktionen, die Auswirkungen auf das Verhalten eines Listenelements haben, unter **Listenaktionen**, und Aktionen für Dokumentenmappen unter **Aktionen für die Dokumentenmappe** gruppiert. Die Kategorien für Aktionen sind:
  
    
    

-  [Hauptaktionen](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1a) Hierbei handelt es sich um die am häufigsten verwendeten Aktionen in einem Workflow.
    
  
-  [Aktionen für die Dokumentenmappe](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1e) Diese Aktionen werden normalerweise in Workflows verwendet, die einer Dokumentbibliothek oder dem Dokumentinhaltstyp zugeordnet sind.
    
  
-  [Listenaktionen](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1b) Diese Aktionen führen Operationen in Listenelementen aus.
    
  
-  [Relationale Aktionen](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1d) Die einzige Aktion in dieser Kategorie sucht nach dem Vorgesetzten eines Benutzers und speichert diese Informationen in einer Variablen.
    
  
-  [Aufgabenaktionen](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1c) Diese Aktionen sind Genehmigungs-, Feedback- und Formularvorgängen zugeordnet.
    
  

> **WICHTIG**
> Für die meisten Aktions-Shapes, die Sie in einen SharePoint-Workflow in Visio einfügen können, ist eine zusätzliche Konfiguration erforderlich, wenn der Workflow in SharePoint Designer importiert wird. Vergessen Sie in Visio nicht, die Kommentarfeatures jedes Aktions-Shapes zu verwenden, um die Einstellungen oder die Konfiguration der Aktion anzugeben. 
  
    
    


### Hauptaktionen
<a name="section1a"> </a>

Dies sind die am häufigsten verwendeten Aktionen, die in in jedem Workflowtyp oder -schritt verwendet werden können.
  
    
    

****


|**Visio-Aktions-Shapes**|**Entsprechende Aktion in SharePoint Designer**|**Aktionsbeschreibung**|
|:-----|:-----|:-----|
|![Hinzufügen eines Kommentars](images/spd15-addcomment-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Kommentar hinzufügen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Hinzufügen eines Kommentars](images/spd15-addcomment-txt.JPG)    > **HINWEIS**> Kommentare bleiben sichtbar, wenn der Workflow nach Visio exportiert wird.           |**Kommentar hinzufügen** <br/> Verwenden Sie diese Aktion, um informative Kommentare zu Referenzzwecken im Workflow-Designer zu hinterlassen. Dies ist besonders hilfreich, wenn es andere Benutzer gibt, die sich an der Erstellung von Workflows beteiligen. Wenn z. B. eine Variable im aktuellen Workflow keinen benutzerfreundlichen Namen aufweist, verwenden Sie diese Aktion zum Hinzufügen von Kommentaren, um anzugeben, welche Funktion die Variable im Workflow hat.  <br/> |
|![Zeit zum Datum hinzufügen](images/spd15-addtimetodate-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Zeit zum Datum hinzufügen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Zeit zum Datum hinzufügen](images/spd15-addtimetodate-txt.JPG)|**Zeit zum Datum hinzufügen** <br/> Mit dieser Aktion können Sie eine bestimmte Zeit in Minuten, Stunden, Tagen, Monaten oder Jahren zu einem Datum hinzufügen und den Ausgabewert als Variable speichern. Das Datum kann ein aktuelles Datum, ein bestimmtes Datum oder ein Nachschlagewert sein.  <br/> |
|![Durchführen der Berechnung](images/spd15-docalc-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Berechnung ausführen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Durchführen der Berechnung](images/spd15-docalc-txt.JPG)|**Berechnung ausführen** <br/> Verwenden Sie diese Aktion, um eine Berechnung durchzuführen, z. B. das Addieren, Subtrahieren, Multiplizieren oder Dividieren zweier Werte, und um den Ausgabewert in einer Variablen zu speichern.  <br/> |
|![Protokollieren in Verlaufsliste](images/spd15-LogHist-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Für die Verlaufsliste protokollieren** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Protokollieren In Verlaufsliste](images/spd15-LogHist-txt.JPG)|**Für die Verlaufsliste protokollieren** <br/> Verwenden Sie diese Aktion, um eine Nachricht zum Workflow in seiner Verlaufsliste zu protokollieren. Eine Nachricht kann eine Zusammenfassung eines Workflowereignisses oder etwas anderes wichtiges über den Workflow sein. Die Verlaufsliste des Workflows kann bei der Behandlung von Problemen mit dem Workflow hilfreich sein.  <br/> |
|![Für Dauer anhalten](images/spd15-PauseDuration-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Für Dauer anhalten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Für Dauer anhalten](images/spd15-PauseDuration-txt.JPG)|**Für Dauer anhalten** <br/> Verwenden Sie diese Aktion, um den Workflow für einen bestimmten Zeitraum in Tagen, Stunden oder Minuten anzuhalten.  <br/> > **HINWEIS**> Die Verzögerungszeit spiegelt das Zeitgeberauftragsintervall wider, das einen Standardwert von fünf Minuten hat.           |
|![Bis Datum anhalten](images/spd15-PauseDate-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Bis Datum anhalten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Bis Datum anhalten](images/spd15-PauseDate-txt.JPG)|**Bis Datum anhalten** <br/> Verwenden Sie diese Aktion, um den Workflow bis zu einem bestimmten Datum anzuhalten. Sie können das aktuelle Datum, ein bestimmtes Datum oder einen Nachschlagewert hinzufügen.  <br/> |
|![Festlegen des Zeitbereichs des Felds "Datum/Uhrzeit"](images/spd15-SetTimePortion-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Den Zeitbereich des Felds 'Datum/Uhrzeit' festlegen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Festlegen des Zeitbereichs des Felds "Datum/Uhrzeit"](images/spd15-SetTimePortion-txt.JPG)|**Den Zeitbereich des Felds 'Datum/Uhrzeit' festlegen** <br/> Verwenden Sie diese Aktion, um einen Zeitstempel zu erstellen und den Ausgabewert in einer Variablen zu speichern. Sie können die Uhrzeit in Stunden und Minuten festlegen und ein aktuelles Datum, ein bestimmtes Datum oder einen Nachschlagewert festlegen.  <br/> |
|![Festlegen des Workflowstatus](images/spd15-SetWFStatus-visio.JPG)| Diese Visio-Aktion ist identisch mit der Aktion **Workflowstatus festlegen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Festlegen des Workflowstatus](images/spd15-SetWFStatus-txt.JPG) Sie können einen Statuswert nicht umbenennen oder löschen, nachdem dieser erstellt wurde. Allerdings müssen Sie diesen nicht verwenden. <br/>  Ein benutzerdefinierter Status ist nur für den aktuellen Workflow anwendbar und kann nicht in einem anderen Workflow verwendet werden. <br/>  Ein Workflow kann benutzerdefinierte in der Aktion definierte Statuswerte nicht verwenden, wenn die Aktion in einem Identitätswechselschritt verwendet wird. <br/> |**Workflowstatus festlegen** <br/> Verwenden Sie diese Aktion, um den Status des Workflows festzulegen. Die Standardoptionen sind **Abgebrochen**, **Genehmigt** und **Abgelehnt**.  <br/> Sie können einen neuen Statuswert in der Dropdownliste in der Aktion eingeben. Sobald Sie einen Statuswert eingegeben haben, wird der Eintrag der Dropdownliste automatisch hinzugefügt.  <br/> Wenn die Aktion **Workflowstatus festlegen** der letzte Schritt in einem Workflow war, in der auch ein benutzerdefinierter Wert verwendet wurde, wird der benutzerdefinierte Wert in der Spalte **Status** in der Liste angezeigt, wenn der Workflow angehalten oder abgeschlossen ist. <br/> |
|![Festlegen der Workflowvariablen](images/spd15-SetWFVar-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Workflowvariable festlegen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Festlegen der Workflowvariablen](images/spd15-SetWFVar-txt.JPG)|**Workflowvariable festlegen** <br/> Verwenden Sie diese Aktion, um eine Workflowvariable auf einen Wert festzulegen. Verwenden Sie diese Aktion, wenn der Workflow einer Variablen Daten zuweisen soll.  <br/> |
|![Anhalten des Workflows](images/spd15-StopWF-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Workflow beenden** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Anhalten des Workflows](images/spd15-StopWF-txt.JPG)|**Workflow beenden** <br/> Verwenden Sie diese Aktion, um die aktuelle Instanz des Workflows zu stoppen und eine Nachricht in der Liste **Workflowverlauf** zu protokollieren. Die in der Aktion angegebene Nachricht wird in der Spalte **Beschreibung** im Workflowverlauf angezeigt, wenn der Workflow abgeschlossen wird. <br/> |
   

### Listenaktionen
<a name="section1b"> </a>

Diese Aktionen werden für Listenelemente verwendet.
  
    
    

****


|**VISIO-AKTIONS-SHAPE**|**ENTSPRECHENDE AKTION IN SHAREPOINT DESIGNER**|**AKTIONSBESCHREIBUNG**|
|:-----|:-----|:-----|
|![Hinzufügen von Berechtigungen für Listenelement](images/spd15-AddListItemPerms-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion ** Listenelementberechtigungen hinzufügen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Hinzufügen von Berechtigungen zum Element](images/spd15-AddListItemPerms-txt.JPG)    > **HINWEIS**> Diese Aktion ist nur in einem Identitätswechselschritt verfügbar.           |**Listenelementberechtigungen hinzufügen** <br/> Diese Aktion gewährt bestimmten Benutzern bestimmte Berechtigungsstufen für ein Element.  <br/> |
|![Einchecken eines Elements](images/spd15-CheckInItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Element einchecken** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Einchecken eines Elements](images/spd15-CheckInItem-txt.JPG)|**Element einchecken** <br/> Durch diese Aktion wird ein Element eingecheckt, das ausgecheckt ist.  <br/> > **HINWEIS**> Sie können nur Elemente aus einer Dokumentbibliothek einchecken.           |
|![Auschecken eines Elements](images/spd15-CheckOutItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Element auschecken** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Auschecken eines Elements](images/spd15-CheckOutItem-txt.JPG)|**Element auschecken** <br/> Verwenden Sie diese Aktion, um ein Element auszuchecken. Der Workflow überprüft, ob das Element eingecheckt ist, bevor ein Dokument ausgecheckt wird.  <br/> > **HINWEIS**> Sie können nur Elemente aus einer Bibliothek auf Ihrer Website auschecken.           |
|![Kopieren eines Listenelements](images/spd15-CopyListItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Listenelement kopieren** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Kopieren eines Listenelements](images/spd15-CopyListItem-txt.JPG)|**Listenelement kopieren** <br/> Verwenden Sie diese Aktion, um ein Listenelement in eine andere Liste zu kopieren. Wenn ein Dokument in dem Listenelement vorhanden ist, kopiert der Workflow auch das Dokument in die Zielliste.  <br/> > **WICHTIG**> Mindestens eine Spalte muss in der Quellliste und der Zielliste ähnlich sein.           |
|![Erstellen eines Listenelements](images/spd15-CreateListItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Listenelement erstellen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Erstellen eines Listenelements](images/spd15-CreateListItem-txt.JPG)|**Listenelement erstellen** <br/> Verwenden Sie diese Aktion, um ein neues Listenelement in der angegebenen Liste zu erstellen. Sie können die Felder und Werte in dem neuen Element angeben.  <br/> Sie können diese Aktion immer dann verwenden, wenn ein neues Element mit bestimmten Informationen erstellt werden soll.  <br/> > **HINWEIS**> Die Ausgabevariable ist die ID des in der Liste erstellten Elements.           |
|![Löschen eines Elements](images/spd15-DeleteItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Element löschen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Löschen eines Elements](images/spd15-DeleteItem-txt.JPG)|**Element löschen** <br/> Verwenden Sie diese Aktion, um ein Element zu löschen.  <br/> |
|![Auschecken des Elements verwerfen](images/spd15-DiscardItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Auschecken von Element verwerfen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Auschecken des Elements verwerfen](images/spd15-DiscardItem-txt.JPG)|**Auschecken von Element verwerfen** <br/> Verwenden Sie diese Aktion, wenn ein Element ausgecheckt ist, Änderungen daran vorgenommen wurden und Sie diese Änderungen verwerfen und das Element wieder einchecken möchten.  <br/> |
|![Erben von Listenelementberechtigungen](images/spd15-InheritListItemPerms-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Übergeordnete Listenelementberechtigungen erben** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Erben von Listenelementberechtigungen](images/spd15-InheritListItemPerms-txt.JPG)    > **HINWEIS**> Diese Aktion ist nur in einem Identitätswechselschritt verfügbar.           |**Übergeordnete Listenelementberechtigungen erben** <br/> Wenn das Element über eindeutige Berechtigungen verfügt, können Sie diese Aktion verwenden, damit das Element die übergeordneten Berechtigungen von der Liste erbt.  <br/> |
|![Entfernen von Listenelementberechtigungen](images/spd15-RmListItemPerms-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Listenelementberechtigungen entfernen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Entfernen von Listenelementberechtigungen](images/spd15-RmListItemPerms-txt.JPG)    > **HINWEIS**> Diese Aktion ist nur in einem Identitätswechselschritt verfügbar.           |**Listenelementberechtigungen hinzufügen** <br/> Durch diese Aktion werden Berechtigungen von einem Element für bestimmte Benutzer entzogen.  <br/> |
|![Ersetzen von Listenelementberechtigungen](images/spd15-ReplaceListItemPerms-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Listenelementberechtigungen ersetzen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Ersetzen von Listenelementberechtigungen](images/spd15-ReplaceListItemPerms-txt.JPG)    > **HINWEIS**> Diese Aktion ist nur in einem Identitätswechselschritt verfügbar.           |**Listenelementberechtigungen ersetzen** <br/> Dadurch werden die aktuellen Berechtigungen eines Elements durch die neuen Berechtigungen ersetzt, die Sie in der Aktion angeben.  <br/> |
|![Festlegen des Inhaltsgenehmigungsstatus](images/spd15-SetContentApprovalStatus-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Status für die Genehmigung von Inhalten festlegen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Festlegen des Inhaltsgenehmigungsstatus](images/spd15-SetContentApprovalStatus-txt.JPG)    > **HINWEIS**> Die Inhaltsgenehmigung muss in der Liste aktiviert werden, bevor Sie diese Aktion verwenden können.           
|**Status für die Genehmigung von Inhalten festlegen** <br/> Wenn Sie die Genehmigung von Inhalten in Ihrer Liste aktiviert haben, verwenden Sie diese Aktion, um das Statusfeld für die Inhaltsgehnemigung auf einen Wert wie "Genehmigt", "Abgelehnt" oder "Ausstehend" festzulegen. Sie können in der Aktion einen benutzerdefinierten Status eingeben.  <br/> > **HINWEIS**> Die Aktion **Status für die Genehmigung von Inhalten festlegen** verarbeitet das aktuelle Element, das derzeit vom Workflow verarbeitet wird, und steht daher in einem Websiteworkflow nicht zur Verfügung.          |
|![Festlegen von Feld in aktuellem Element](images/spd15-SetFieldCurrItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Feld im aktuellen Element festlegen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Festlegen von Feld in aktuellem Element](images/spd15-SetFieldCurrItem-txt.JPG)|**Feld im aktuellen Element festlegen** <br/> Verwenden Sie die Aktion, um ein Feld im aktuellen Element auf einen Wert festzulegen.  <br/> > **HINWEIS**> Wenn Sie den Workflow bis zur Änderung des Feldwerts anhalten möchten, verwenden Sie stattdessen die Aktion **Auf Feldänderung im aktuellen Element warten**.           Die Aktion **Feld im aktuellen Element festlegen** sollte nicht in einem Websiteworkflow verwendet werden. <br/> |
|![Aktualisieren des Listenelements](images/spd15-UpdateListItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Listenelement aktualisieren** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Aktualisieren des Listenelements](images/spd15-UpdateListItem-txt.JPG)|**Listenelement aktualisieren** <br/> Verwenden Sie diese Aktion, um ein Listenelement zu aktualisieren. Sie können die Felder und die neuen Werte in diesen Feldern angeben.  <br/> |
|![Warten auf Feldänderung in aktuellem Element](images/spd15-Wait4FieldChange-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Auf Feldänderung im aktuellen Element warten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Warten auf Feldänderung](images/spd15-Wait4FieldChange-txt.JPG)|**Auf Feldänderung im aktuellen Element warten** <br/> Durch diese Aktion wird der Workflow angehalten, bis das Feld im aktuellen Element auf einen neuen Wert geändert wurde.  <br/> > **HINWEIS**> Wenn der Workflow den Feldwert ändern soll, statt auf die Feldänderung zu warten, verwenden Sie stattdessen die Aktion **Feld im aktuellen Element festlegen**.           |
   

### Aufgabenaktionen
<a name="section1c"> </a>

Aktionen in dieser Kategorie beziehen sich auf Aufgabenelemente. Diese Aktionen gelten nur für SharePoint-Websites, auf denen SharePoint Server 2013 ausgeführt wird.
  
    
    

****


|**VISIO-AKTIONS-SHAPE**|**ENTSPRECHENDE AKTION IN SHAREPOINT DESIGNER**|**AKTIONSBESCHREIBUNG**|
|:-----|:-----|:-----|
|![Zuweisen eines Formulars zu einer Gruppe](images/spd15-AssignForm2Grp-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Formular einer Gruppe zuordnen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Zuweisen eines Formulars zu einer Gruppe](images/spd15-AssignForm2Grp-txt.JPG)|**Formular einer Gruppe zuordnen** <br/> Mithilfe dieser Aktion können Sie ein benutzerdefiniertes Aufgabenformular mit angepassten Feldern erstellen.  <br/> Sie können diese Aktion verwenden, um eine Aufgabe einem oder mehreren Teilnehmern bzw. einer oder mehreren Gruppen zuzuweisen und diese aufzufordern, ihre Aufgaben auszuführen. Teilnehmer geben ihre Antworten in die Felder des benutzerdefinierten Aufgabenformulars ein, wenn sie mit der Aufgabe fertig sind, und klicken in dem Formular auf **Aufgabe erledigen**.  <br/> |
|![Zuweisen eines Aufgabenelements](images/spd15-AssignToDoItem-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Aufgabe zuordnen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Zuweisen eines Aufgabenelements](images/spd15-AssignToDoItem-txt.JPG)|**Aufgabe zuordnen** <br/> Mit dieser Aktion können Sie jedem Teilnehmer eine Aufgabe zuordnen und ihn auffordern, seine Aufgaben zu erledigen und nach Abschluss auf die Schaltfläche **Aufgabe erledigen** im Aufgabenformular zu klicken. <br/> |
|![Sammeln von Daten von einem Benutzer](images/spd15-CollectDataFrUser-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Daten von einem Benutzer sammeln** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Sammeln von Daten von einem Benutzer](images/spd15-CollectDataFrUser-txt.JPG)|**Daten von einem Benutzer sammeln** <br/> Mit dieser Aktion können Sie einem Teilnehmer eine Aufgabe zuordnen, ihn auffordern, die erforderlichen Informationen in einem benutzerdefinierten Aufgabenformular anzugeben und dann auf die Schaltfläche **Aufgabe erledigen** im Aufgabenformular zu klicken. <br/> Diese Aktion hat eine OUTPUT-Klausel, d. h. der Workflow speichert die von dieser Aktion zurückgegebenen Informationen in einer entsprechenden Variablen. Die Listenelement-ID des abgeschlossenen Aufgabenelements der Aktion wird in der Sammelvariablen gespeichert.  <br/> |
|![Starten des Genehmigungsprozesses](images/spd15-StartApprovalProc-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Genehmigungsprozess starten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Starten des Genehmigungsprozesses für Dokumentensatz](images/spd15-StartApprovalProc-txt.JPG)|**Genehmigungsprozess starten** <br/> Verwenden Sie diese Aktion, um ein Dokument zur Genehmigung weiterzuleiten. Genehmigende Personen können das Dokument genehmigen oder zurückweisen , die Genehmigungsaufgabe erneut zuweisen oder Änderungen anfordern.  <br/> Sie können internen und externen Teilnehmern Aufgaben in der Aktion zuweisen. Ein externer Teilnehmer kann ein Mitarbeiter Ihres Unternehmens sein, der kein Benutzer in der Websitesammlung ist, oder jemand außerhalb Ihres Unternehmens.  <br/> |
|![Starten des Feedbackprozesses](images/spd15-StartFeedback-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Feedbackvorgang starten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Starten des Feedbackprozesses](images/spd15-StartFeedback-txt.JPG)|**Feedbackvorgang** <br/> Mit dieser Aktion können Sie Benutzern in einer bestimmten Reihenfolge Aufgabenelemente für ein Feedback zuweisen - seriell oder parallel. Der Standard ist parallel. Benutzer oder Teilnehmer an der Aufgabe können eine Aufgabe auch an andere Benutzer zuweisen. Wenn die Benutzer fertig sind, klicken sie auf die Schaltfläche **Feedback übermitteln**, um anzugeben, dass die Aufgabe abgeschlossen wurde.  <br/> Sie können internen und externen Teilnehmern Aufgaben in der Aktion zuweisen. Ein externer Teilnehmer kann ein Mitarbeiter Ihres Unternehmens sein, der kein Benutzer in der Websitesammlung ist, oder jemand außerhalb Ihres Unternehmens.  <br/> |
|![Starten des benutzerdefinierten Aufgabenprozesses](images/spd15-StartCustomTask-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Benutzerdefinierten Aufgabenprozess starten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Starten des benutzerdefinierten Aufgabenprozesses](images/spd15-StartCustomTask-txt.JPG)|**Benutzerdefinierten Aufgabenprozess starten** <br/> Die Aktion **Benutzerdefinierten Aufgabenprozess starten** ist eine Vorlage für einen Genehmigungsprozess, die Sie verwenden können, wenn andere Genehmigungsaktionen nicht Ihren Anforderungen entsprechen. <br/> |
   

### Relationale Aktionen
<a name="section1d"> </a>

Die einzige Aktion in dieser Kategorie sucht nach dem Vorgesetzten eines Benutzers und speichert diese Informationen in einer Variablen. Diese Aktion gilt nur für SharePoint-Websites, auf denen SharePoint Server 2013 ausgeführt wird.
  
    
    

****


|**VISIO-AKTIONS-SHAPE**|**ENTSPRECHENDE AKTION IN SHAREPOINT DESIGNER**|**AKTIONSBESCHREIBUNG**|
|:-----|:-----|:-----|
|![Nachschlagen des Managers eines Benutzers](images/spd15-LookupMgr4User-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Vorgesetzten eines Benutzers nachschlagen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Nachschlagen des Managers eines Benutzers](images/spd15-LookupMgr4User-txt.JPG)|**Vorgesetzten eines Benutzers nachschlagen** <br/> Verwenden Sie diese Aktion, um den Vorgesetzten eines Benutzers nachzuschlagen. Der Ausgabewert wird in einer Variablen gespeichert.  <br/> > **HINWEIS**> Damit diese Aktion ordnungsgemäß funktioniert, muss der Benutzerprofildienst in SharePoint ausgeführt werden.           |
   

### Aktionen für die Dokumentenmappe
<a name="section1e"> </a>

Einige Workflowaktionen sind nur verfügbar, wenn der Workflow mit einer Dokumentbibliothek, z. B. freigegebene Dokumente, oder mit dem Dokumentinhaltstyp verknüpft ist.
  
    
    

****


|**VISIO-AKTIONS-SHAPE**|**ENTSPRECHENDE AKTION IN SHAREPOINT DESIGNER**|**AKTIONSBESCHREIBUNG**|
|:-----|:-----|:-----|
|![Senden der Genehmigung für Dokumentensatz](images/spd15-SendApproval4DocSet-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Genehmigungsvorgang für Dokumentenmappen starten** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Starten des Genehmigungsprozesses für Dokumentensatz](images/spd15-SendApproval4DocSet-txt.JPG)|**Genehmigungsvorgang für Dokumentenmappen starten** <br/> Verwenden Sie diese Aktion, um den Genehmigungsprozess für eine Dokumentenmappe zu beginnen.  <br/> |
|![Senden des Dokumentensatzes an Repository](images/spd15-SendDocSet2Repos-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Dokumentenmappe an Repository senden** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Senden des Dokumentensatzes an Repository](images/spd15-SendDocSet2Repos-txt.JPG)|**Dokumentenmappe an Repository senden** <br/> Mithilfe dieser Aktion können Sie die Dokumentenmappe in ein Dokumentrepository verschieben oder kopieren. Ein Dokumentrepository kann eine Bibliothek auf Ihrer SharePoint-Website oder eine eigene Website wie das Dokumentcenter sein, das Datensätze anhand der von Ihnen definierten Regeln an ein bestimmtes Ziel weiterleitet.  <br/> |
|![Senden des Dokuments an Repository](images/spd15-SendDoc2Repos-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Dokument an Repository senden** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Senden des Dokuments an Repository](images/spd15-SendDoc2Repos-txt.JPG)|**Dokument an Repository senden** <br/> Mithilfe dieser Aktion können Sie ein Dokument in ein Dokumentrepository verschieben oder kopieren. Ein Dokumentrepository kann eine Bibliothek auf Ihrer SharePoint-Website oder eine eigene Website wie das Dokumentcenter sein, das Datensätze anhand der von Ihnen definierten Regeln an ein bestimmtes Ziel weiterleitet.  <br/> |
|![Festlegen des Inhaltsgenehmigungsstatus für Dokumentensatz](images/spd15-SetContentApprStatus-visio.JPG)|Diese Visio-Aktion ist identisch mit der Aktion **Inhaltsgenehmigungsstatus für die Dokumentenmappe festlegen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Festlegen des Inhaltsgenehmigungsstatus für Dokumentensatz](images/spd15-SetContentApprStatus4DocSet-txt.JPG)|**Inhaltsgenehmigungsstatus für die Dokumentenmappe festlegen** <br/> Verwenden Sie diese Aktion, um den Inhaltsgenehmigungsstatus für eine Dokumentenmappe auf **Genehmigt**, **Abgelehnt** oder **Ausstehend** festzulegen. <br/> |
   

## Workflowbedingungen
<a name="section2"> </a>

Eine Workflowbedingung ist ein Verzweigungspunkt im Workflow. Die Workflowbedingung vergleicht die Eingabe mit einem angegebenen Wert. Stimmen sie überein, folgt der Workflow einer Verzweigung. Wenn dies nicht der Fall ist, folgt er der anderen Verzweigung.
  
    
    

> **WICHTIG**
> Für die meisten Bedingungs-Shapes, die Sie in einen SharePoint-Workflow in Visio einfügen können, ist eine zusätzliche Konfiguration erforderlich, wenn der Workflow in SharePoint Designer importiert wird. Vergessen Sie in Visio nicht, die Kommentarfeatures jedes Bedingungs-Shapes zu verwenden, um die Entscheidungskriterien der Bedingung anzugeben. 
  
    
    


### Allgemeine Bedingungen

In diesem Abschnitt werden die Bedingungen beschrieben, die in SharePoint Designer 2013 für Listen und wiederverwendbare Listenworkflows verfügbar sind, unabhängig davon, mit welchem Listen- oder Inhaltstyp der Workflow verküpft ist.
  
    
    

****


|**VISIO-BEDINGUNGS-SHAPE**|**ENTSPRECHENDE BEDINGUNG IN SHAREPOINT DESIGNER**|**BESCHREIBUNG DER BEDINGUNG**|
|:-----|:-----|:-----|
|![Vergleichen der Datenquelle](images/spd15-CompareDataSrc-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Wenn ein beliebiger Wert gleich dem Wert ist** in SharePoint Designer 2013 und wird angezeigt als: <br/>![If-Wert entspricht Wert](images/spd15-CompareDataSrc-txt.JPG)|**Datenquelle vergleichen** <br/> Diese Bedingung vergleicht zwei Werte. Sie können angeben, ob die Werte gleich oder nicht gleich sein sollen.  <br/> |
|![Vergleichen des Dokumentfelds](images/spd15-CompareDocField-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Wenn das aktuelle Elementfeld gleich Wert ist** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Wenn aktuelles Elementfeld dem Wert entspricht](images/spd15-CompareDocField-txt.JPG)|**Dokumentfeld vergleichen** <br/> Diese Bedingung vergleicht ein Feld mit einem Wert, den Sie angeben. Sie können angeben, ob die Werte gleich oder nicht gleich sein sollen.  <br/> |
|![Von einer bestimmten Person erstellt](images/spd15-CreatedBySpecPerson-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Erstellt von einer bestimmten Person** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Wenn von bestimmter Person erstellt](images/spd15-CreatedBySpecPerson-txt.JPG)|**Erstellt von einer bestimmten Person** <br/> Diese Bedingung überprüft, ob ein Element von einem bestimmten Benutzer erstellt wurde. Der Benutzer kann als E-Mail-Adresse, z. B. olivier@contoso.com, angegeben oder aus SharePoint-, Exchange- oder Active Directory-Benutzern ausgewählt werden.  <br/> > **HINWEIS**> Beim Benutzernamen und der E-Mail-Adresse wird die Groß-/Kleinschreibung berücksichtigt. Es wird empfohlen, dass Sie einen Benutzernamen oder eine E-Mail-Adresse auswählen, um sicherzustellen, dass Sie die richtge Schreibweise verwenden. Wenn Sie einen Benutzernamen oder eine E-Mail-Adresse eingeben, muss dies mit der Schreibweise des Kontos übereinstimmen. Wenn das Konto beispielsweise von "contoso\\molly" erstellt wurde, wird dies nicht als TRUE ausgewertet, wenn das Benutzerkonto "Contoso\\Molly" lautet.           |
|![In einem bestimmten Zeitabschnitt erstellt](images/spd15-CreatedInSpecDateSpan-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Erstellt in einer bestimmten Zeitspanne** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Wenn in einem bestimmten Zeitabschnitt erstellt](images/spd15-CreatedInSpecDateSpan-txt.JPG)|**Erstellt in einer bestimmten Zeitspanne** <br/> Diese Bedingung überprüft, ob das Element zwischen den Datumsangaben erstellt wurde. Sie können das aktuelle Datum, ein bestimmtes Datum oder einen Nachschlagewert verwenden.  <br/> |
|![Von einer bestimmten Person geändert](images/spd15-ModifiedBySpecPerson-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Geändert von einer bestimmten Person** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Wenn von einer bestimmten Person geändert](images/spd15-ModifiedBySpecPerson-txt.JPG)|**Geändert von einer bestimmten Person** <br/> Verwenden Sie diese Bedingung, um zu überprüfen, ob ein Element von einem bestimmten Benutzer geändert wurde. Der Benutzer kann als E-Mail-Adresse, z. B. olivier@contoso.com, angegeben oder aus SharePoint-, Exchange- oder Active Directory-Benutzern ausgewählt werden.  <br/> > **HINWEIS**> Beim Benutzernamen und der E-Mail-Adresse wird die Groß-/Kleinschreibung berücksichtigt. Es wird empfohlen, dass Sie einen Benutzernamen oder eine E-Mail-Adresse auswählen, um sicherzustellen, dass Sie die richtige Schreibweise verwenden. Wenn Sie einen Benutzernamen oder eine E-Mail-Adresse eingeben, muss dies mit der Schreibweise des Kontos übereinstimmen. Wenn das Konto beispielsweise von "contoso\\molly" geändert wurde, wird dies nicht als TRUE ausgewertet, wenn das Benutzerkonto "Contoso\\Molly" lautet.           |
|![In einem bestimmten Zeitabschnitt geändert](images/spd15-ModifiedInSpecDateSpan-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Geändert in einer bestimmten Zeitspanne** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Wenn in einem bestimmten Zeitabschnitt geändert](images/spd15-ModifiedInSpecDateSpan-txt.JPG)|**Geändert in einer bestimmten Zeitspanne** <br/> Diese Bedingung überprüft, ob ein Element zwischen den Datumsangaben geändert wurde. Sie können das aktuelle Datum, ein bestimmtes Datum oder einen Nachschlagewert verwenden.  <br/> |
|![Titelfeld enthält Stichwörter](images/spd15-TitleFieldKeywords-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Titelfeld enthält Schlüsselwörter** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Wenn Titelfeld Stichwörter enthält](images/spd15-TitleFieldKeywords-txt.JPG)|**Titelfeld enthält Schlüsselwörter** <br/> Diese Bedingung überprüft, ob das Feld **Titel** Feld für ein Element ein bestimmtes Wort enthält. Sie können entweder das Stichlwort im Zeichenfolgengenerator angeben - hierbei kann es sich um einen statischen Wert oder eine dynamische Zeichenfolge oder eine Kombination daraus handeln - oder fügen Sie eine Suche für ein Feld oder eine Variable ein. <br/> > **HINWEIS**> In der Bedingung **Titelfeld enthält Stichwörter** können Sie nach maximal einem Stichwort suchen. Sie können jedoch logische Operatoren wie**||**(oder) oder **&amp;&amp;** (und) verwenden.          |
   

### Bedingungen für Dokumentenmappen

Einige Workflowbedingungen sind nur verfügbar, wenn der Workflow mit einer Dokumentbibliothek, z. B. freigegebene Dokumente, oder mit dem Dokumentinhaltstyp verknüpft ist.
  
    
    


|**VISIO-BEDINGUNGS-SHAPE**|**ENTSPRECHENDE BEDINGUNG IN SHAREPOINT DESIGNER**|**BESCHREIBUNG DER BEDINGUNG**|
|:-----|:-----|:-----|
|![Dateigröße liegt in einem bestimmten Bereich](images/spd15-FileSzInSpecRange-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Die Dateigröße in einem bestimmten KB-Bereich** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Dateigröße liegt in einem bestimmten Bereich](images/spd15-FileSzInSpecRange-txt.JPG)|**Die Dateigröße in einem bestimmten KB-Bereich** <br/> Diese Bedingung überprüft, ob die Dateigröße eines Dokuments zwischen den angegebenen Größen liegt (in KB). Die Bedingung schließt die angegebenen Größenwerte nicht in die Auswertung mit ein. Sie können eine Zahl eingeben oder einen Nachschlagewert für die erste oder zweite Größe in der Bedingung verwenden.  <br/> |
|![Datei ist ein bestimmter Typ](images/spd15-FileIsSpecType-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Der Dateityp weist einen bestimmten Typ auf** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Datei ist ein bestimmter Typ](images/spd15-FileIsSpecType-txt.JPG)|**Der Dateityp weist einen bestimmten Typ auf** <br/> Diese Bedingung überprüft, ob der Dateityp des aktuellen Elements dem angegebenen Typ entspricht, z. B. DOCX. Sie können den Dateityp als Zeichenfolge eingeben oder einen Nachschlagewert verwenden.  <br/> |
   

### Listenbedingungen


  
    
    

****


|**VISIO-BEDINGUNGS-SHAPE**|**ENTSPRECHENDE BEDINGUNG IN SHAREPOINT DESIGNER**|**BESCHREIBUNG DER BEDINGUNG**|
|:-----|:-----|:-----|
|![Überprüfen genauer Benutzerberechtigungen](images/spd15-ChkExactUserPerms-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Listenelement-Berechtigungsstufen überprüfen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Überprüfen von Berechtigungsebenen für Listenelement](images/spd15-ChkExactUserPerms-txt.JPG)|**Exakte Benutzerberechtigungen überprüfen** <br/> Diese Bedingung überprüft, ob der angegebene Benutzer über die minimal erforderliche Berechtigungsstufe verfügt.  <br/> |
|![Überprüfen von Benutzerberechtigungen](images/spd15-ChkUserPerms-visio.JPG)|Diese Visio-Bedingung ist identisch mit der Bedingung **Listenelementberechtigungen überprüfen** in SharePoint Designer 2013 und wird angezeigt als: <br/>![Überprüfen von Listenelementberechtigungen](images/spd15-ChkUserPerms-txt.JPG)|**Benutzerberechtigung überprüfen** <br/> Diese Bedingung überprüft, ob der angegebene Benutzer über die minimal erforderlichen Berechtigungen verfügt.  <br/> |
   

## Workflowabschlusszeichen
<a name="section3"> </a>

In Visio muss jeder Workflow mit einem Start-Abschlusszeichen (
  
    
    
![Beginn](images/spd15-WFStart-icon.JPG)
  
    
    
) beginnen und mit einem Stop-Abschlusszeichen (
  
    
    
![Stopp](images/spd15-WFStop-icon.JPG)
  
    
    
) enden. In einem Workflow kann jeweils nur ein Typ von Abschlusszeichen verwendet werden. Abschlusszeichen sind erforderlich, wenn Sie einen SharePoint-Workflow in Visio erstellen, damit der Workflow die Validierung besteht und exportiert werden kann. Workflowabschlusszeichen werden in SharePoint Designer nicht verwendet.
  
    
    

## Weitere Ressourcen
<a name="bk_addresources"> </a>


-  [Neuerungen in Workflows für SharePoint 2013](what-s-new-in-workflows-for-sharepoint-2013.md)
    
  
-  [Erste Schritte mit Workflows in SharePoint 2013](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  

  
    
    
