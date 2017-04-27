---
title: Aktivität Workflowklassen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 70d5ca8d-520d-40a9-b24e-52bb31bd6c22
---


# Aktivität Workflowklassen in SharePoint 2013
Bietet eine Übersicht über die SharePoint-Workflow Aktivitätsklassen, die in SharePoint 2013 verfügbar sind.
Die Palette von Aktivitätsklassen wurde für SharePoint 2013 überarbeitet. Tabelle 1 werden den aktuellen Katalog 49 gruppiert nach ihren jeweiligen Kategorien verfügbaren Aktivitäten aufgelistet.
  
    
    


> **HINWEIS**
> In zukünftigen Versionen die Aktivitäten, die in dieser Tabelle aufgeführten Links zu den API-Referenzdokumentation für ihre jeweiligen verwalteten Klassen bieten.
  
    
    


## Workflow-Aktivitätsklassen in SharePoint 2013 verfügbar
<a name="bk_wfactivityclasses"> </a>


**In Tabelle 1. Workflow-Aktivitätsklassen**

||||
|:-----|:-----|:-----|
|**Aktivität** <br/> |**Kategorie** <br/> |**Beschreibung** <br/> |
|CreatedBy <br/> |Bedingung <br/> |Gibt zurück, ob das aktuelle Element von angegebenen Benutzer erstellt wurde. <br/> |
|CreatedInRange <br/> |Bedingung <br/> |Gibt zurück, ob der aktuelle Element in der angegebenen Datumsbereichs erstellt wurde. <br/> |
|ModifiedBy <br/> |Bedingung <br/> |Gibt zurück, ob das aktuelle Element vom angegebenen Benutzer geändert wurde. <br/> |
|ModifiedInRange <br/> |Bedingung <br/> |Gibt zurück, ob das aktuelle Element im angegebenen Zeitraum geändert wurde. <br/> |
|WordsInTitle <br/> |Bedingung <br/> |Gibt zurück, ob die angegebenen Schlüsselwörter in den Titel des aktuellen Elements vorhanden sind. <br/> |
|WorkflowInterop <br/> |Koordinierung <br/> |Startet einen Workflow SharePoint 2010 (Windows Workflow Foundation 3.5). <br/> |
|WaitForCustomEvent <br/> |Ereignis <br/> |Wartet auf ein benutzerdefiniertes Ereignis an den Workflow gesendet werden. <br/> |
|WaitForFieldChange <br/> |Ereignis <br/> |Wartet auf die angegebene Feld, in dem angegebenen Wert für das angegebene Listenelement zu ändern. <br/> |
|WaitForItemEvent <br/> |Ereignis <br/> |Wartet auf die angegebene Ereignis eintritt auf angegebenes Listenelement. <br/> |
|CheckInItem <br/> |Liste <br/> |Checkt das angegebene Listenelement. <br/> |
|CheckOutItem <br/> |Liste <br/> |Checkt das angegebene Listenelement. <br/> |
|CopyItem <br/> |Liste <br/> |Kopiert das angegebene Datei-Element in der angegebenen Dokumentbibliothek. Gilt nicht für nicht-Datei-Listenelemente. <br/> |
|CreateListItem <br/> |Liste <br/> |Erstellt ein Listenelement. <br/> |
|DeleteListItem <br/> |Liste <br/> |Löscht ein Listenelement. <br/> |
|LookupSPList <br/> |Liste <br/> |Gibt Informationen zu der Liste, die die angegebene Liste-ID entspricht. <br/> |
|LookupSPListItem <br/> |Liste <br/> |Eigenschaften für das angegebene Listenelement zurückgegeben. <br/> |
|LookupSPListItemBooleanProperty <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **Boolean**zurück. <br/> |
|LookupSPListItemDateTimeProperty <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **DateTime**zurück. <br/> |
|LookupSPListItemDoubleProperty <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **Double**zurück. <br/> |
|LookupSPListItemDynamicValueProperty <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **DynamicValue**zurück. <br/> |
|LookupSPListItemGuid <br/> |Liste <br/> |Gibt die GUID-Eigenschaft des ersten Listenelements, das mit der Eigenschaftenname und Wert-Eigenschaft angegebenen Filterkriterien übereinstimmt. <br/> |
|LookupSPListItemInt32Property <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **Int32**zurück. <br/> |
|LookupSPListItemProperty <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **Object**zurück. <br/> |
|LookupSPListItemStringProperty <br/> |Liste <br/> |Gibt den Wert der angegebenen Liste Item-Eigenschaft als **String**zurück. <br/> |
|LookupSPListProperty <br/> |Liste <br/> |Gibt auflisten Eigenschaften als **DynamicValue**. <br/> |
|UndoCheckOutItem <br/> |Liste <br/> |Widerruft Auschecken des Elements angegebene Liste. <br/> |
|UpdateListItem <br/> |Liste <br/> |Aktualisiert ein Listenelement. <br/> |
|CompositeTask <br/> |Aufgabe <br/> |Führt einen Aufgabenprozess - mehrere Personen in der Datenreihe oder Parallel, wartet Aufgaben abgeschlossen haben, mehrere Aufgaben zugewiesen und aggregierte Ergebnis berechnet. <br/> |
|SingleTask <br/> |Vorgang <br/> |Führt einen einfache Aufgabe-Prozess - eine Einzelperson oder eine Gruppe, wartet auf den Abschluss der Aufgabe eine einzelne Aufgabe zugewiesen. <br/> |
|ExpandGroupToUsers <br/> |Benutzer <br/> |Gibt eine Auflistung von LoginNames von Benutzern, die Mitglieder einer angegebenen Prinzipal der SharePoint-Gruppe sind. <br/> |
|IsValidUser <br/> |Benutzer <br/> |Überprüft, ob der angegebene Benutzer Prinzipal-ID einen gültigen SharePoint-Benutzer darstellt. <br/> |
|LookupSPGroup <br/> |Benutzer <br/> |Gibt Informationen zu einer SP-Gruppe, die entspricht der angegebenen Prinzipal-Id zurück. <br/> |
|LookupSPGroupMembers <br/> |Benutzer <br/> |Gibt die Auflistung von Informationen über jedes Mitglied einer Gruppe zurück. <br/> |
|LookupSPPrincipal <br/> |Benutzer <br/> |Gibt Informationen zu einer SP-Principal (Prinzipal stellt einen Benutzer oder eine Gruppe in SharePoint, die Berechtigungen zugewiesen werden kann). <br/> |
|LookupSPPrincipalId <br/> |Benutzer <br/> |Gibt Prinzipal-ID, die einen angegebenen Benutzernamen entspricht. <br/> |
|LookupSPPrincipalProperty <br/> |Benutzer <br/> |Gibt eine angegebene Eigenschaft von einem angegebenen SP Principal-Wert zurück. <br/> |
|LookupSPUser <br/> |Benutzer <br/> |Gibt Informationen zu einem Benutzer, der entspricht der angegebenen Prinzipal-ID. <br/> |
|LookupSPUserProperty <br/> |Benutzer <br/> |Gibt den Wert einer angegebenen Eigenschaft des Benutzers, den entspricht für angegebenen SP Principal zurück. <br/> |
|E-Mail <br/> |Dienstprogramm <br/> |Sendet eine e-Mail-Nachricht an die Benutzer der SharePoint-Website. <br/> |
|GetCurrentItemGuid <br/> |Dienstprogramm <br/> |Gibt die GUID-Eigenschaft des SharePoint-Listenelement auf dem die Workflowinstanz ausgeführt wird. <br/> |
|GetCurrentListId <br/> |Dienstprogramm <br/> |Gibt die ID-Eigenschaft des SharePoint-Liste auf dem die Workflowinstanz ausgeführt wird. <br/> |
|GetHistoryListId <br/> |Dienstprogramm <br/> |Gibt die ID der Verlaufsliste einer Workflowinstanz zurück, wenn eine Verlaufsliste für die workflowzuordnung angegeben ist. <br/> |
|GetTaskListId <br/> |Dienstprogramm <br/> |Gibt die ID der Vorgangsliste einer Workflowinstanz zurück, wenn eine Verlaufsliste für die workflowzuordnung angegeben ist. <br/> |
|LookupWorkflowContextProperty <br/> |Dienstprogramm <br/> |Wert der angegebenen Workflow Context-Eigenschaft zurückgegeben. <br/> |
|SetField <br/> |Dienstprogramm <br/> |Legt ein Feld im aktuellen Element fest. <br/> |
|SetWorkflowStatus <br/> |Dienstprogramm <br/> |Legt angegebenen Text als Status für das angegebene Feld aktuelle Listenelement. Ermöglicht den Workflow an, legen Sie den Wert eines zeichenfolgefelds eines Listenelements als "Workflowstatus". <br/> |
|TranslateDocument <br/> |Dienstprogramm <br/> |Erstellt eine übersetzte Kopie des angegebenen Dokuments in einer angegebenen Dokumentbibliothek mithilfe von SharePoint-Übersetzungsdienste. <br/> |
|WebUri <br/> |Dienstprogramm <br/> |Gibt die absoluten URI des SP-Webs, die den Workflow enthält. <br/> |
|WriteToHistory <br/> |Dienstprogramm <br/> |Schreibvorgänge angegebenen Kommentar Verlaufsliste. <br/> |
   

## Zusätzliche Ressourcen
<a name="bkm_addlresource"> </a>


-  [Workflowaktions- und -aktivitätenreferenz für SharePoint 2013](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [Entwickeln von SharePoint 2013-Workflows mit Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [Einrichten und Konfigurieren von SharePoint 2013-Workflow-Manager](set-up-and-configure-sharepoint-2013-workflow-manager.md)
    
  

