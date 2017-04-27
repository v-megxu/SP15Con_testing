---
title: Grundlegendes zu SharePoint 2013-Workflows
ms.prod: SHAREPOINT
ms.assetid: 1e622296-f78b-4e3a-a1e7-8effa24111a8
---


# Grundlegendes zu SharePoint 2013-Workflows
Bietet eine allgemeine Übersicht über die Workflowinfrastruktur in SharePoint 2013, einschließlich einer Sicht der Plattformarchitektur und der Workflow-Interopbrücke
## Übersicht über Workflows in SharePoint 2013
<a name="bkm_overview"> </a>

SharePoint 2013-Workflows werden von Windows Workflow Foundation 4 unterstützt, das in Vergleich zu früheren Versionen erheblich überarbeitet wurde. Windows Workflow Foundation (WF) basiert wiederum auf der von  [Windows Communication Foundation (WCF)](http://msdn.microsoft.com/de-de/library/vstudio/ms735119%28v=vs.90%29.aspx) bereitgestellten Messaging-Funktion.
  
    
    
Konzeptionell gesehen modellieren Workflows strukturierte Geschäftsprozesse. Daher sind Windows Workflow Foundation 4-Workflows eine strukturierte Sammlung von "Workflowaktivitäten", die jeweils eine funktionale Komponente eines Geschäftsprozesses darstellen.
  
    
    
Die Workflowplattform in SharePoint 2013 verwendet das Windows Workflow Foundation 4-Aktivitätsmodell, um einen SharePoint-basierten Geschäftsprozess darzustellen. Zusätzlich führt SharePoint 2013 ein allgemeineres Stage-Gate-Modell ein, auf dem Workflows erstellt werden.
  
    
    
Es ist wichtig, die Beziehung zwischen Workflowaktivitäten undSharePoint-Aktionen zu beachten. Workflowaktivitäten stellen die zugrunde liegenden verwalteten Objekte dar, deren Methoden Workflowverhalten steuern. Workflowaktionen stellen andererseits Wrapper dar, welche die zugrunde liegenden Aktivitäten kapseln und sie in benutzerfreundlicher Form in SharePoint Designer präsentieren. Workflowautoren interagieren mit den Workflowaktionen, wohingegen das Workflow-Ausführungsmodul die entsprechenden Aktivitäten verarbeitet.
  
    
    
Die Aktivitäten, die Implementierungen von Aktivitätsklassen darstellen, werden mithilfe von XAML deklarativ implementiert.
  
    
    
Workflowaktivitäten werden mithilfe locker gekoppelter Webdienste aufgerufen, die zum Kommunizieren mit SharePoint Messaging-APIs verwenden. Diese APIs basieren auf der von  [Windows Communication Foundation (WCF)](http://msdn.microsoft.com/de-de/library/vstudio/ms735119%28v=vs.90%29.aspx) bereitgestellten Messaging-Funktion.
  
    
    
Das Messaging-Framework ist sehr flexibel und unterstützt quasi jedes Messaging-Muster, das Sie benötigen. Beachten Sie, dass Windows Workflow Foundation und WCF in einer SharePoint 2013-Farm in Workflow-Manager-Client 1.0 gehostet werden.
  
    
    
Workflow-Manager-Client 1.0, SharePoint 2013 und SharePoint Designer 2013 stellen jeweils wesentliche Teile der neuen Infrastruktur bereit:
  
    
    

- **Workflow-Manager-Client 1.0** stellt das Management von Workflowdefinitionen bereit. Er hostet außerdem die Ausführungsprozesse für Workflowinstanzen.
    
  
- **SharePoint 2013** stellt das Framework für SharePoint-Workflows bereit, die SharePoint-basierte Geschäftsprozesse modellieren, welche SharePoint-Dokumente, -Listen, -Benutzer und -Aufgaben umfassen. Darüber hinaus werden SharePoint-Workflows, -Zuordnungen, -Aktivitäten und andere Workflowmetadaten in SharePoint 2013 gespeichert und verwaltet.
    
  
- **SharePoint Designer 2013** stellt, wie in früheren Versionen, das zentrale Geschäftsbenutzertool zur Erstellung von Workflowdefinitionen und deren Veröffentlichung dar. Es kann auch zum Verpacken einer Workflowdefinition mit oder ohne zugeordnete SharePoint-Komponenten verwendet werden.
    
  

## Plattformarchitektur
<a name="bkm_Architecture"> </a>

Abbildung 1 zeigt eine allgemeine Ansicht des SharePoint 2013-Workflow-Frameworks. Beachten Sie zunächst, wie die neue Workflowinfrastruktur Workflow-Manager-Client 1.0 als den neuen Workflowausführungshost einführt. Während die Workflowausführung in früheren Versionen in SharePoint selbst gehostet wurde, wurde dies in SharePoint 2013 geändert. Workflow-Manager-Client 1.0 befindet sich außerhalb von SharePoint und kommuniziert mithilfe allgemeiner Protokolle über den Microsoft Azure-Servicebus, vermittelt durch OAuth. Ansonsten enthält SharePoint die erwarteten Features: Inhaltselemente, Ereignisse, Apps usw. Beachten Sie allerdings, dass es für Abwärtskompatibilität auch eine Implementierung des SharePoint 2010-Workflow-Hosts (d. h. das Windows Workflow Foundation 3-Modul) gibt. Weitere Informationen dazu finden Sie unter  [Verwenden von Workflow-Interop für SharePoint 2013](use-workflow-interop-for-sharepoint-2013.md).
  
    
    

**Abbildung 1. Allgemeine Architektur der Workflowinfrastruktur**

  
    
    

  
    
    
![Allgemeine Workflowarchitektur](images/wfArchitecture1.png)
  
    
    
Workflow-Manager-Client 1.0 wird in SharePoint 2013 in der Form des Workflow-Manager-Client 1.0-Dienstanwendungsproxys dargestellt. Diese Komponente erlaubt SharePoint, mit dem Workflow-Manager-Client 1.0-Server zu kommunizieren und zu interagieren. Server-zu-Server-Authentifizierung wird mithilfe von OAuth bereitgestellt.
  
    
    
SharePoint-Ereignisse, die ein Workflow überwacht, wie **itemCreated**, **itemUpdated** usw., werden mithilfe des Microsoft Azure-Servicebus an Workflow-Manager-Client 1.0 weitergeleitet. Für den Weg zurück verwendet die Plattform die SharePoint-REST-API (Representational State Transfer), um einen Rückruf an SharePoint durchzuführen.
  
    
    
Außerdem wurde das SharePoint-Workflowobjektmodell, das zusammenfassend als der Workflow-Dienstemanager bezeichnet wird, ergänzt, sodass Sie Ihre Workflows und deren Ausführung verwalten und steuern können. Die Hauptinteraktionszonen für den Dienstemanager sind Bereitstellung, Messaging, Instanzensteuerung und (für Abwärtskompatibilität) Interoperabilität mit SharePoint 2010-Workflows.
  
    
    
Schließlich gibt es die Workflowerstellungskomponente. SharePoint Designer kann nun sowohl SharePoint 2010- als auch SharePoint 2013-Workflows erstellen und bereitstellen. Visual Studio 2012 bietet nicht nur eine Designeroberfläche zur Erstellung deklarativer Workflows, sonder kann auch SharePoint-Add-Ins und Lösungen erstellen, die Workflow-Manager-Client 1.0-Funktionen vollständig integrieren.
  
    
    

## Workflowabonnements und -zuordnungen
<a name="bkm_Subscriptions"> </a>

Da die wichtigste Änderung an SharePoint 2013-Workflows die Verschiebung der Workflowverarbeitung zu externen Workflow-Hosts wie Microsoft Azure darstellt, war es wichtig, dass SharePoint-Nachrichten und -Ereignisse eine Verbindung zur Workflowinfrastruktur in Microsoft Azure aufweisen. Zusätzlich war es erforderlich, dass Microsoft Azure die Infrastruktur mit Kundendaten verbindet. Workflowzuordnungen (die auf dem WF-Konzept von Abonnements basieren) stellen die SharePoint-Infrastrukturkomponenten dar, die diese Anforderungen unterstützen.
  
    
    

### Microsoft Azure-Veröffentlichungs-/Abonnementdienst

Bevor wir über Workflowverknüpfungen und -abonnements sprechen können, müssen wir uns den Microsoft Azure-Veröffentlichungs-/Abonnementdienst näher ansehen, der manchmal alspub/sub oder einfachPubSub bezeichnet wird. PubSub ist ein asynchrones Messaging-Framework. Nachrichtenabsender (Herausgeber) senden Nachrichten nicht direkt an Nachrichtenempfänger (Abonnenten). Stattdessen werden Nachrichten von Herausgebern als Klassen gerendert, die den Nachrichtenabonnenten nicht kennen. Abonnenten nutzen dann veröffentlichte Nachrichten, indem sie auf Basis der von ihnen erstellten Abonnements für sie relevante Nachrichten, unabhängig vom Herausgeber, identifizieren.
  
    
    
Diese Entkoppelung von Nachrichtenerstellung von der Nachrichtenverwendung ermöglicht Skalierbarkeit und Flexibilität. Sie erlaubt Multicast-Messaging seitens des Herausgebers und promiske Nutzung seitens des Abonnenten.
  
    
    

> **HINWEIS**
> Das PubSub-Feature ist Bestandteil des Microsoft Azure-Servicebus, der Konnektivitätsoptionen für WCF und andere Dienstendpunkte bereitstellt. Dazu zählen REST-Endpunkte, die sich hinter NAT-Grenzen (Network Address Translation) befinden können und/oder an sich häufig ändernde, dynamisch zugewiesene IP-Adressen gebunden sein können. Weitere Informationen zum Azure-Servicebus finden Sie unter  [Servicebus](http://msdn.microsoft.com/de-de/library/ee732537.aspx). 
  
    
    


### Workflowzuordnungen und Zuordnungsbereich

Workflowzuordnungen binden Workflowdefinitionen an einen bestimmten SharePoint-Bereich mit bestimmten Standardwerten. Diese Zuordnungen selbst stellen einen Satz von Abonnementregeln dar, die im Azure-Veröffentlichungs-/Abonnementdienst gespeichert werden und die eingehende Nachrichten verarbeiten, um sicherzustellen, dass sie von den entsprechenden (d. h. abonnierten) Workflowinstanzen verwendet werden.
  
    
    
Die Messaging-Infrastruktur unterstützt Workflows standardmäßig in den folgenden Bereichen:
  
    
    

-  [SPList](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPList.aspx) (für Listenworkflows)
    
  
-  [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) (für Websiteworkflows)
    
  
Im Gegensatz zu früheren Versionen unterstützt SharePoint 2013 keine Workflows, die einem Inhaltstyp ( [SPContentType](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPContentType.aspx) ) zugeordnet sind. Die Messaging-Infrastruktur ist allerdings erweiterbar, sodass sie jeden beliebigen Bereich unterstützen kann. Als Entwickler können Sie die [EventSourceId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscription.EventSourceId.aspx) -Eigenschaft auf einer bestimmten [WorkflowSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscription.aspx) -Instanz auf eine beliebige **guid** festlegen. Sie können diesen **EventSourceId**-Wert dann verwenden, um **PublishEvent(Guid, String, IDictionary<String, Object>)** aufzurufen, wodurch eine neue Workflowinstanz des angegebenen **WorkflowSubscription** ausgelöst wird.
  
    
    

### Workflowdienst in Microsoft Azure

Zuordnungen für SharePoint-Workflows werden in Microsoft Azure durch deren Workflowdienst dargestellt. Wenn eine Anwendung eine Workflowzuordnung und deren Daten abrufen muss, muss sie zuerst alle Workflowdienste abfragen, die in einem bestimmten Bereich verfügbar sind.
  
    
    
Auf ähnliche Weise bringen Workflowinstanzen zu ihrem entsprechenden Workflowdienst einen Verweis zurück. Anhand dieses Verweises wird deren korrekte Zuordnung ermittelt.
  
    
    

### Starten von Workflows

Workflows können manuell oder automatisch gestartet werden.
  
    
    
 **Manuelle Workflows**
  
    
    
Manuelle Workflows werden gestartet, wenn der PubSub-Dienst eine **StartWorkflow** -Nachricht erhält. Die Nachricht enthält die folgenden deskriptiven Informationen:
  
    
    

- Den Bezeichner für die Zuordnung (d. h. die **WorkflowSubscription**-Instanz).
    
  
- Die ID des Ursprungselementkontexts. Diese wird mit dem  _ItemId_-Parameter und der **EventSource**-Eigenschaft beim **PublishEvent**-Methodenaufruf übergeben.
    
  
- Den Ereignistyp für einen manuellen Start ( **WorkflowStart**).
    
  
- Ggf. zusätzliche Workflowinitiierungsparameter, entweder aus dem Abonnement oder dem **Init**-Formular. Für das Abonnement wäre dies die **CorrelationId**, und für das **Init**-Formular wäre dies die **WFInstanceId**.
    
  
 **Automatisch gestartete Workflows**
  
    
    
Automatisch gestartete Workflows werden mithilfe einer **Add**-Nachricht an den PubSub-Dienst initiiert. Die Nachricht enthält die folgenden deskriptiven Informationen:
  
    
    

- Die ID des Ursprungselementkontexts.
    
  
- Das Ereignis selbst ist ein normales SharePoint **Add**-Ereignis.
    
  
- Die Workflowinitiierungsparameter.
    
  

> **HINWEIS**
> Wenn ein Workflow für ein wiederholbares Ereignis (z. B. das **OnItemChanged**-Ereignis) automatisch startet, kann es erst dann einen anderen Workflow einer bestimmten Zuordnung starten, wenn die vorhandene ausgeführte Instanz des Workflows der Zuordnung abgeschlossen ist. 
  
    
    


### Workflowabonnements

Die natürliche Ergänzung zu Zuordnungen sind Abonnements, die dem Workflow erlauben, mit Zuordnungen zu interagieren. Der Workflow muss mithilfe von **create**- und **delete**-Methoden Abonnements auf dem Azure-Servicebus erstellen.
  
    
    
Die Signaturen der Methoden, die das Abonnement erstellen und den Workflow instanziieren, geben die - sowohl optionalen als auch erforderlichen - Parameter an. Die Liste der Parameter wird vom Workflowautor festgelegt, sodass sie von einer Workflowdefinition zur nächsten variieren können. Die Liste der Abonnementparameter wird als Metadaten der Workflowdefinitionen angegeben. Die Abonnementparameter werden bei Erstellung des Abonnements angegeben. Die Liste der Initialisierungsparameter wird in XAML als Bestandteil der Workflowdefinition angegeben. Die Initialisierungsparameter werden angegeben, wenn der Workflow instanziiert wird.
  
    
    
Abonnements sind an ein bestimmtes SharePoint-Objekt gebunden: entweder eine **SPList**-Instanz oder eine **SPWeb**-Instanz. Der Abonnementobjekttyp wird als Wert eines erforderlichen Parameters übergeben, wenn das Abonnement erstellt wird. Der Objekttyp definiert den Abonnementbereich, sodass ein Abonnement nur auf Ereignisse reagieren kann, die bei dem Objekt auftreten, das sie abonniert haben.
  
    
    

## SharePoint-Workflowinteroperabilität
<a name="bkm_InteropBridge"> </a>

SharePoint-Workflowinteroperabilität ermöglicht den Aufruf von SharePoint 2010-Workflows (die auf Windows Workflow Foundation 3 basieren) über SharePoint 2013-Workflows, die auf Windows Workflow Foundation 4 basieren. Dadurch können Sie 2010-Workflows innerhalb von 2013-Workflows ausführen.
  
    
    
Dies ist wichtig, weil Sie möglicherweise SharePoint 2010 haben, das Sie in Verbindung mit Ihren SharePoint 2013-Workflows verwenden möchten. Außerdem möchten Sie möglicherweise Aktivitäten oder Features aus SharePoint 2010 verwenden, die noch nicht in SharePoint 2013 implementiert sind.
  
    
    
Eine umfassende Erläuterung der SharePoint-Workflowinteroperabilität finden Sie unter  [Verwenden von Workflow-Interop für SharePoint 2013](use-workflow-interop-for-sharepoint-2013.md).
  
    
    

## Zusätzliche Ressourcen
<a name="bk_additional"> </a>


-  [Erste Schritte mit Workflows in SharePoint 2013](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [Workflowaktions- und -aktivitätenreferenz für SharePoint 2013](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [Entwickeln von SharePoint 2013-Workflows mit Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [Workflows in SharePoint 2013](workflows-in-sharepoint-2013.md)
    
  
-  [Verwenden von Workflow-Interop für SharePoint 2013](use-workflow-interop-for-sharepoint-2013.md)
    
  

