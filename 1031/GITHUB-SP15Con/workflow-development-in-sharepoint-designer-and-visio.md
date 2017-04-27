---
title: Workflowentwicklung in SharePoint Designer und Visio
ms.prod: SHAREPOINT
ms.assetid: 496780d5-47d6-4a43-bf14-70aefb8d820c
---


# Workflowentwicklung in SharePoint Designer und Visio
Hier erfahren Sie, wie Sie mit Visio 2013 und SharePoint Designer 2013 Workflows erstellen und auf einer SharePoint 2013-Website veröffentlichen, ohne dass Sie Code benötigen.
## Einführung
<a name="VSSPD_Intro"> </a>

Visio 2013 und SharePoint Designer 2013 machen es Geschäftsanalysten, Prozessberatern und IT-Experten einfach, zusammenzuarbeiten und -Workflows zu erstellen. Sowohl Visio Professional 2013 als auch der Visual Designer in SharePoint Designer 2013 bieten eine optionale Darstellung von Workflows in einem Format, das für Benutzer mit und ohne Programmierkenntnisse gleichermaßen verständlich ist.
  
    
    

> **HINWEIS**
> Hinweise zur Einrichtung und Konfiguration von SharePoint Server 2013 und dem Workflow-Manager-Server finden Sie unter  [Konfigurieren von Workflows in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj658586.aspx). 
  
    
    

Mithilfe von Visio 2013 können Sie einen SharePoint-Workflow visuell erstellen, den Workflow nach SharePoint Designer 2013 exportieren und diesen Workflow dann auf einer SharePoint-Website veröffentlichen. Nachdem ein Workflow in Visio 2013 erstellt wurde, muss er nach SharePoint Designer 2013 exportiert werden. Dann fügt ein SharePoint-Websiteeigentümer oder IT-Experte dem Workflow Parameter hinzu. Er verwendet dazu entweder den Workflow-Text-Editor oder den neuen Visual Workflow Designer. Dabei handelt es sich um ein Visio 2013-ActiveX-Steuerelement, das in SharePoint Designer 2013 gehostet wird. Nachdem der Workflow abgeschlossen wurde, kann er auf der SharePoint-Website veröffentlicht werden.
  
    
    
Dies ist ideal für Geschäftsanalysten und Prozessberater, die bereits mit Flussdiagrammen in Visio vertraut sind, da sie einen Workflow entwerfen können, der Geschäftslogik darstellt. Die Person, die den Workflow entwirft, kann sich voll und ganz auf die BI-spezifischen (Business Intelligence) Anforderungen des Workflows konzentrieren, ohne ein Experte für deklarative Workflows sein zu müssen.
  
    
    

## Info zur Erstellung von SharePoint-Workflows in Visio 2013 und SharePoint Designer 2013
<a name="VSSPD_About"> </a>

Visio 2013 enthält eine SharePoint 2013-Workflowvorlage, die zur Erstellung von SharePoint 2013-Workflows verwendet werden kann. Die SharePoint 2013-Workflowvorlage ist mit drei Vorlagen verknüpft: SharePoint 2013-Workflowaktionen, SharePoint 2013--Workflowbedingungen und SharePoint 2013-Workflow-Abschlusszeichen. Die Shapes in diesen Schablonen entsprechen den spezifischen Aktionen und Bedingungen, die in einem SharePoint 2013-Workflow verwendet werden können. Zur Erstellung eines Workflows müssen Sie nur Shapes in den Zeichenbereich in Visio 2013 ziehen, um die Geschäftslogik hinter dem Workflow zu modellieren.
  
    
    

### Phasen, Schleifen und Schritte

Bei Workflows in SharePoint Designer 2013 werden jetzt die Begriffe Phasen, Schleifen undSchritte verwendet. Workflowautoren können eine Reihe einzelner Aktionen und Bedingungen als einzelne Einheit gruppieren, um den Prozess klarer zu definieren. So könnte es z. B. eine Phase oder einen Schritt für die Genehmigung oder die Anforderung von Feedback geben. Diese Phase oder dieser Schritt würde alle Aktionen umfassen, die für diesen Prozess relevant sind. Die Phase oder der Schritt selbst kann ein Knoten eines längeren Workflows sein und würde einem Benutzer erlauben, anstatt einer Reihe einzelner Aktionen den Status dieser Phase als Ganzes anzuzeigen.
  
    
    
Die SharePoint 2013-Workflowvorlage, die in Visio 2013 enthalten ist, verwendet ebenfalls Phasen, Schleifen und Schritte als logische Bausteine zur Erstellung eines Workflows. 
  
    
    

> **WICHTIG**
> Aufgrund der zugrunde liegenden Unterschiede zwischen der Microsoft SharePoint 2010-Workflowvorlage und der SharePoint 2013-Workflowvorlage können Shapes aus einer Vorlage nicht in einem Diagramm des jeweils anderen Tools verwendet werden. Nur Shapes aus den Schablonen "SharePoint 2013- Workflowaktionen", "SharePoint 2013-Workflowbedingungen" und "SharePoint 2013-Workflow-Abschlusszeichen" können zur Erstellung eines SharePoint 2013-Workflows verwendet werden. 
  
    
    


### Phasen-Shapes

Eine Phase kann eine Reihe von Shapes und möglicherweise Verzweigungen enthalten. Allerdings kann es nur einen Pfad in eine Phase (und einen Schritt) und einen Pfad heraus geben. Alle Aktionen im Workflow müssen in einer Phase enthalten sein. Phasen-Shapes werden mithilfe von Container-Shapes visuell dargestellt. Bei einem Phasen-Shape müssen an den Rändern des Containers ein Eingangs- und Ausgangs-Shape hinzugefügt werden, um die Pfade zur und aus der Phase zu definieren. Visio 2013 und der Visual Designer in SharePoint Designer 2013 fügen die Eingangs- und Ausgangs-Shapes für Sie hinzu, wenn Sie den Container zum ersten Mal ablegen.
  
    
    
Für Phasen gelten außerdem die folgenden Regeln:
  
    
    

- Alle Diagramme müssen mindestens eine Phase aufweisen. Eine vollständige Phase mit Eingangs-, Ausgangs- und Start-Shapes ist als Teil einer SharePoint 2013-Standardworkflowvorlage vorhanden.
    
  
- Wenn Sie dem Zeichenbereich eine neue Phase hinzufügen, fügt Visio 2013 Start- und Ende-Konnektoren hinzu, wenn die Phase abgelegt wird.
    
  
- Bei Phasen können Konnektoren nur über die Eingangs- und Ausgangs-Shapes eingehen oder ausgehen.
    
  
- Phasen-Container können nicht verschachtelt werden. Wenn Sie einen anderen Unterprozess innerhalb einer Phase vernesteln möchten, verwenden Sie einen Schritt.
    
  
- Eine Phase kann Workflow-stoppen-Shapes enthalten.
    
  
- Für das gesamte Diagramm ist außerhalb der Phase ein explizites Start-Shape erforderlich. Ein explizites Terminieren-Shape ist außerhalb der Phase nicht erforderlich.
    
  
- Auf der obersten Ebene kann der Workflow nur Phasen, bedingte Shapes und Start- und Terminieren-Shapes enthalten. Alle anderen Shapes müssen in einer Phase enthalten sein.
    
  

### Schleifen-Shapes

Schleifen sind eine Reihe verbundener Shapes, die als Schleife ausgeführt werden, wobei so lange vom letzten Shape in der Reihe zum ersten Shape iteriert wird, bis eine Bedingung erfüllt ist. 
  
    
    
Wie Phasen werden Schleifen durch ein Container-Shape dargestellt, das ein Eingangs- und Ausgangs-Shape enthält (wird hinzugefügt, wenn das Shape im Zeichenbereich abgelegt wird). Auch bei einem Schleifen-Shape müssen an den Rändern des Containers ein Eingangs- und Ausgangs-Shape hinzugefügt werden, um die Pfade in die und aus der Schleife zu definieren.
  
    
    
Visio 2013 und SharePoint Designer 2013 unterstützen zwei Arten von Schleifen: Schleife  *n*  -mal ausführen und Schleife ausführen, bis *Wert1*  *Wert2*  entspricht.
  
    
    
Für Schleifen gelten außerdem die folgenden Regeln:
  
    
    

- Schleifen müssen sich innerhalb einer Phase befinden, und Phasen können sich nicht in einer Schleife befinden.
    
  
- Eine Schleife kann Schritte enthalten.
    
  
- Schleifen dürfen nur einen Eingangs- und einen Ausgangspunkt aufweisen.
    
  

### Schritt-Shapes

Schritte stellen eine gruppierte Reihe aufeinanderfolgender Aktionen dar. Schritte müssen in einer Phase enthalten sein. Ein Schritt-Shape muss auch ein Eingangs- und Ausgangs-Shape aufweisen, um die Pfade in das und aus dem Shape zu definieren. Beide Shapes werden standardmäßig hinzugefügt, wenn das Shape im Zeichenbereich abgelegt wird.
  
    
    

## Erstellen eines Workflows in Visio 2013
<a name="VSSPD_Creating"> </a>

Alle Master-Shapes in den SharePoint 2013-Workflowschablonen entsprechen den Aktionen, Bedingungen und anderen logischen Konstrukten innerhalb eines SharePoint 2013-Workflows. Zur Erstellung eines Workflows können Sie Shapes, wie in jedem anderen Flussdiagramm in Visio, in den Zeichenbereich ziehen. Wenn Sie mit der Erstellung des Workflows in Visio 2013 fertig sind, speichern Sie den Workflow, bevor SharePoint Designer 2013 ihn öffnen kann.
  
    
    
Gehen Sie folgendermaßen vor, um die SharePoint 2013-Workflowvorlage in Visio 2013 zu öffnen:
  
    
    

### So öffnen Sie die SharePoint 2013-Workflowvorlage in Visio 2013


1. Öffnen Sie Visio 2013.
    
  
2. Wählen Sie **Neu** aus.
    
  
3. Wählen Sie unter **Vorlagenkategorien** **Flussdiagramm** aus.
    
  
4. Wählen Sie unter **Vorlage auswählen** **SharePoint 2013 Workflow** und dann **Erstellen** aus.
    
    Die Vorlage wird geöffnet, und der Zeichenbereich wird mit Start- und Phasen-Shapes aufgefüllt. Das Phasen-Shape enthält ein Eingangs- und Ausgangs-Shape, verbunden durch einen einzelnen Konnektor.
    
  
Ziehen Sie, während die SharePoint 2013-Workflowvorlage geöffnet ist, Aktionen, Bedingungen und andere Shapes in den Zeichenbereich, um einen Workflow zu entwerfen. Weitere Informationen zu einzelnen Shapes und deren Bedeutung finden Sie im Artikel  [Shapes in der SharePoint Server-Workflowvorlage in Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md).
  
    
    

> **TIPP**
>  Berücksichtigen Sie beim Entwerfen eines Workflows zusätzlich Folgendes:>  Um schnell einen Workflow zu erstellen, legen Sie Aktions- und Bedingungs-Shapes auf dem internen Konnektor ab, der in neuen Phasen-Shapes enthalten ist. Visio 2013 teilt den Konnektor automatisch in zusätzliche Konnektoren auf, sodass der Workflow vom Eingangs- bis zum Ausgangs-Shape erhalten bleibt.>  Verwenden Sie keine Shapes aus anderen Schablonen als den Schablonen "SharePoint 2013-Workflowaktionen", "SharePoint 2013-Workflowbedingungen" und "SharePoint 2013-Workflow-Abschlusszeichen". Verwenden Sie nur das von der SharePoint 2013-Workflowvorlage bereitgestellte Konnektortool, um Verbindungen zwischen Shapes hinzuzufügen. Alle anderen Konnektor-Shapes sind in einem SharePoint 2013-Workflow nicht gültig.>  Aktions-Shapes, -Schritte und -Schleifen müssen immer in einem Phasen-Shape enthalten sein. Einige bedingte Shapes können sich außerhalb einer Phase befinden.>  Ein Phasen-Shape muss genau ein Eingangs-Shape und ein Ausgangs-Shape aufweisen. Der in der Phase enthaltene Unterprozess des Workflows muss mit dem Eingangs-Shape beginnen und mit dem Ausgangs-Shape enden.>  Ein Bedingungs-Shape muss zwei ausgehende Konnektoren aufweisen, einen mit der Bezeichnung "Ja" und den anderen mit der Bezeichnung "Nein". Sie können mit der rechten Maustaste auf einen Konnektor klicken und **Ja** oder **Nein** auswählen.>  Ein Workflow darf nur ein Start-Shape aufweisen. Das Start-Shape muss sich außerhalb einer Phase befinden.>  Wenn Sie Shapes im Workflow Text hinzufügen, hat der Shape-Text keine Auswirkung auf den Workflow.
  
    
    


  
    
    
Die Überprüfung des Workflows in Visio 2013 erfolgt wie bei jedem anderen verbundenen Diagramm: Visio prüft das Diagramm anhand einer Reihe von Regeln und gibt eine Liste mit Fehlern zurück, die im Diagramm gefunden wurden. Informationen dazu, wie Sie Validierungsprobleme beheben, finden Sie im Artikel  [Beheben von SharePoint Server 2013-Workflowvalidierungsfehlern in Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md).
  
    
    

### So überprüfen Sie einen SharePoint 2013-Workflow in Visio 2013


1. Wählen Sie auf der Registerkarte **Prozess** in der Gruppe **Diagrammüberprüfung** **Diagramm überprüfen** aus.
    
  
2. Wenn im Workflow Fehler gefunden werden, wird unter dem Diagramm der Bereich **Probleme** geöffnet. Wählen Sie in der Liste jedes Element aus, um das Shape im Diagramm auszuwählen, das den Fehler verursacht hat.
    
  
3. Beheben Sie jeden in der Liste **Probleme** aufgeführten Validierungsfehler. Nachdem alle Fehler behoben wurden, wählen Sie erneut **Diagramm überprüfen** aus. Weitere Informationen dazu, wie Sie Validierungsprobleme in Visio 2013 beheben, finden Sie im Artikel [Beheben von SharePoint Server 2013-Workflowvalidierungsfehlern in Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md).
    
  
4. Werden im Workflow keine Fehler gefunden, zeigt Visio die Meldung an, dass die Diagrammüberprüfung abgeschlossen wurde und keine Fehler gefunden wurden.
    
  
Nachdem der Workflow in Visio 2013 erfolgreich überprüft wurde, können Sie die Datei speichern und in SharePoint Designer 2013 importieren. Im Gegensatz zur Microsoft SharePoint 2010-Workflowvorlage können Sie eine Kopie des SharePoint 2013-Workflowdiagramms unter dem Visio 2013-Standarddateiformat (.vsdx) speichern, und SharePoint Designer 2013 kann die Datei öffnen. 
  
    
    
Verwenden Sie das folgende Verfahren, um einen SharePoint 2013-Workflow in Visio 2013 als Visio 2013-.vsdx-Datei zu speichern, die in SharePoint Designer 2013 geöffnet werden kann:
  
    
    

### So speichern Sie einen Workflow in Visio 2013


1. Wählen Sie **Datei** und dann **Speichern unter** aus.
    
  
2. Wählen Sie unter **Speichern unter** **Speichern** und dann **Navigieren** aus.
    
  
3. Wählen Sie im Dialogfeld **Speichern unter** einen Speicherort aus, um die Datei zu speichern, und geben Sie einen Namen für die Datei ein ("Mein SP-Workflow").
    
  
4. Wählen Sie **Speichern** aus.
    
  

## Anpassen und Veröffentlichen eines Workflows in SharePoint Designer 2013
<a name="VSSPD_Customizing"> </a>

Nachdem Sie die zugrunde liegende Geschäftslogik für einen SharePoint 2013-Workflow in Visio 2013 erstellt und das Diagramm gespeichert haben, können Sie die Visio-.vsdx-Datei in SharePoint Designer 2013 öffnen und damit beginnen, den Workflow an Ihre SharePoint 2013-Website anzupassen. Das .vsdx-Dateipaket enthält XML-Dokumente, die SharePoint Designer 2013 in Workflows übersetzen kann.
  
    
    
Verwenden Sie das folgende Verfahren, um eine SharePoint 2013-Website in SharePoint Designer 2013 zu öffnen:
  
    
    

### So öffnen Sie eine SharePoint 2013-Website in SharePoint Designer 2013


1. Öffnen Sie SharePoint Designer 2013.
    
  
2. Wählen Sie unter **SharePoint-Website öffnen** **Website öffnen** aus.
    
  
3. Wählen Sie im Dialogfeld **Website öffnen** die Website aus, die Sie öffnen möchten.
    
  
4. Wählen Sie **Öffnen** aus.
    
  
Nachdem die SharePoint 2013-Website geöffnet wurde, können Sie das Visio 2013-.vsdx-Diagramm in SharePoint Designer 2013 öffnen.
  
    
    

### So öffnen Sie einen Visio Professional 2013-Workflow in SharePoint Designer 2013


1. Wählen Sie **Datei** und dann **Element hinzufügen** aus.
    
  
2. Gehen Sie folgendermaßen vor, um einen Listenworkflow zu erstellen:
    
1. Wählen Sie unter **Workflows** **Listenworkflow** aus.
    
  
2. Geben Sie im linken Bereich unter **Listenworkflow** einen Namen für Ihren Workflow ein (Mein erster SP2013-Workflow), und wählen Sie die Liste auf der Website aus, auf der Sie den Workflow veröffentlichen möchten.
    
  
3. Wählen Sie in der Liste **Workflowplattform für den neuen Workflow auswählen** **SharePoint 2013-Workflow** aus.
    
  
4. Wählen Sie **Erstellen** aus.
    
  
3. Gehen Sie folgendermaßen vor, um einen Websiteworkflow zu erstellen:
    
1. Wählen Sie unter **Workflows** **Websiteworkflow** aus.
    
  
2. Geben Sie im linken Bereich unter **Websiteworkflow** einen Namen für Ihren Workflow ein (Mein erster SP2013-Workflow).
    
  
3. Wählen Sie in der Liste **Workflowplattform für den neuen Workflow auswählen** **SharePoint 2013-Workflow** aus.
    
  
4. Wählen Sie **Erstellen** aus.
    
  
4. Wählen Sie auf der Registerkarte **Workflow** in der Gruppe **Verwalten** **Workfloweinstellungen** aus.
    
  
5. Wählen Sie auf der Registerkarte **Workfloweinstellungen** in der Gruppe **Verwalten** **Aus Visio importieren** aus.
    
  
6. Navigieren Sie im Dialogfeld **Workflow aus Visio-Zeichnung importieren** zum Speicherort der .vsdx-Datei.
    
  
7. Wählen Sie die Datei aus, die Sie öffnen möchten (Mein SP-Workflow), und wählen Sie dann **Öffnen** aus.
    
  
Wenn Sie eine .vsdx-Datei in SharePoint Designer 2013 öffnen, wird die Datei im Visual Designer, einem in SharePoint Designer gehosteten Visio-ActiveX-Steuerelement, angezeigt. Das Visio 2013-Diagramm enthält alle in Visio erstellten Shapes und sämtlichen Shape-Text. 
  
    
    

> **HINWEIS**
> Um zwischen dem Visual Designer und dem Declarative Designer in SharePoint Designer 2013 zu wechseln, wählen Sie auf der Registerkarte **Workflow** in der Gruppe **Verwalten** **Ansichten** aus. Dieser Vorgang kann einige Sekunden dauern, da SharePoint Designer 2013 den Workflow überprüft und die Workflowinformationen dann von einem Format in das andere konvertiert. Bei diesem Vorgang wird eine weitere Überprüfung auf Shape-Ebene durchgeführt. Falls im Diagramm Fehler entdeckt werden, werden diese in einem Fehlerbereich unten im Zeichenbereich (wie in Visio) angezeigt.
  
    
    

Die im Visual Designer angezeigten Shapes weisen auch Aktionstags auf (unten links im Shape durch ein Symbol des Typs Workfloweinstellungen dargestellt). Wenn Sie ein Aktionstag auswählen, zeigt ein Dropdownmenü die Attribute für diese Aktion oder Bedingung im Workflow und **Eigenschaften** an. Diese Eigenschaften definieren die Parameterwerte, die für diese Aktion verwendet werden sollen: aus welchen Listen Elemente abgerufen werden sollen, welcher Berechnungsoperator verwendet werden soll, oder an welche E-Mail-Adresse eine Nachricht gesendet werden soll. Wenn Sie eine in der Liste angezeigte Eigenschaft auswählen, wird ein Dialogfeld angezeigt, in dem Sie die Einstellungen für diese Eigenschaft anpassen können.
  
    
    
So sind z. B. mit dem Shape **E-Mail senden** zwei Eigenschaften verknüpft: **E-Mail erstellen** und **Eigenschaften**. Wenn Sie **E-Mail erstellen** auswählen, wird das Dialogfeld **E-Mail-Nachricht definieren** angezeigt, in dem Sie die Nachricht erstellen können, die durch die Aktion gesendet werden soll. Wenn Sie **Eigenschaften** auswählen, wird das Dialogfeld **E-Mail senden - Eigenschaften** angezeigt, das alle Parameter für die Aktion anzeigt.
  
    
    

> **HINWEIS**
> Weitere Informationen zu einzelnen Aktionen, Shapes und deren Eigenschaften finden Sie in den Artikeln  [Shapes in der SharePoint Server-Workflowvorlage in Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md) und [Kurzübersicht zu Workflowaktionen (SharePoint 2013-Workflowplattform)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md). 
  
    
    

Wenn Sie die Eigenschaften im Workflow festgelegt haben und zum Veröffentlichen bereit sind, müssen Sie den Workflow in SharePoint Designer 2013 zuerst auf Fehler prüfen. Wenn Sie im Menüband auf der Registerkarte **Visual Designer** **Veröffentlichen** auswählen, prüft SharePoint Designer 2013 den Workflow automatisch auf Fehler. Wenn Sie möchten, können Sie die Fehlerprüfung auch manuell auslösen.
  
    
    
Verwenden Sie das folgende Verfahren, um den SharePoint 2013-Workflow in SharePoint Designer 2013 zu überprüfen:
  
    
    

### So prüfen Sie einen Workflow in SharePoint Designer 2013 manuell auf Fehler


1. Wählen Sie auf der Registerkarte **Visual Designer** in der Gruppe **Speichern** **Auf Fehler überprüfen** aus.
    
  
2. Werden im Workflow Fehler gefunden, wird unter dem Zeichenbereich von Visual Designer der Bereich **Probleme** geöffnet. Wählen Sie jedes Element in der Liste aus, um die Aktion, die Bedingung, den Konnektor, das Abschlusszeichen oder den Container im Workflow auszuwählen, der den Fehler verursacht hat.
    
  
3. Beheben Sie jeden in der Liste **Probleme** aufgeführten Validierungsfehler. Nachdem alle Fehler behoben wurden, wählen Sie erneut **Auf Fehler überprüfen** aus.
    
  
4. Werden im Workflow keine Fehler gefunden, zeigtSharePoint Designer die Meldung an, dass im Workflow keine Fehler gefunden wurden.
    
  
Wenn der Workflow überprüft wurde und keine Fehler gefunden wurden, können Sie den Workflow in der SharePoint-Liste veröffentlichen. Um den Workflow in SharePoint Designer 2013 zu veröffentlichen, wählen Sie auf der Registerkarte **Visual Designer** in der Gruppe **Speichern** **Veröffentlichen** aus. Wenn während des Veröffentlichungsvorgangs Fehler auftreten, kehrt SharePoint Designer 2013 zum Visual Designer zurück und zeigt die Fehler im Bereich **Fehler** an.
  
    
    

## Zusätzliche Ressourcen
<a name="VSSPD_Additional"> </a>

Weitere Informationen finden Sie in den folgenden Ressourcen:
  
    
    

-  [Kurzübersicht zu Workflowaktionen (SharePoint 2013-Workflowplattform)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Shapes in der SharePoint Server-Workflowvorlage in Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)
    
  
-  [Beheben von SharePoint Server 2013-Workflowvalidierungsfehlern in Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)
    
  
-  [Erstellen, Importieren und Exportieren von SharePoint-Workflows in Visio](http://office.microsoft.com/de-de/visio-help/create-import-and-export-sharepoint-workflows-in-visio-HA101888007.aspx)
    
  
-  [SharePoint Developer Center](http://msdn.microsoft.com/de-de/sharepoint/default.aspx)
    
  
-  [Visio Developer Center](http://msdn.microsoft.com/de-de/office/aa905478)
    
  

