---
title: Grundlegendes zur Koordination Aktionen in SharePoint Designer 2013
ms.prod: SHAREPOINTDESIGNER
ms.assetid: 33fbcf91-0a5d-47ab-85a9-9d2d556a204d
---


# Grundlegendes zur Koordination Aktionen in SharePoint Designer 2013
Koordinationsaktionen in SharePoint Designer 2013 dienen zum Starten eines Workflows, die auf der SharePoint 2010-Workflow-Plattform von innerhalb eines Workflows auf der SharePoint 2013-Workflow-Plattform integriert.
||
|:-----|
||
   

## Koordinierungsaktionen in SharePoint Designer 2013
<a name="section1"> </a>

Es sind zwei Koordinationsaktionen in SharePoint Designer 2013 verfügbar. Beide Aktionen sind nur für die SharePoint 2013-Workflow-Plattform verfügbar. Diese Aktionen sind:
  
    
    

- Listenworkflow starten: zum Starten eines Workflows für eine bestimmte Liste entwickelt wurde.
    
  
- Starten Sie einen Website-Workflow: zum Starten eines Workflows für die Website entwickelt wurden.
    
  
Koordinierung Aktionen werden im Dropdown-Menü **Aktionen** angezeigt, bei der Erstellung eines Workflows basierend auf der SharePoint 2013-Workflow-Plattform, wie in der Abbildung dargestellt.
  
    
    

**Abbildung: Koordinierungsaktionen in SharePoint Designer**

  
    
    

  
    
    
![Koordinierungsaktionen in SharePoint Designer](images/SPD15-CoordinationActions.png)
  
    
    
Beide Aktionen dienen zum Starten eines Workflows, die auf der SharePoint 2010-Workflow-Plattform mithilfe eines Workflows auf der SharePoint 2013-Workflow-Plattform integriert.
  
    
    

    
> **WICHTIG**
> Die koordinationsaktionen unterstützen nur das Starten eines Workflows basierend auf der SharePoint 2010-Workflow-Plattform mithilfe eines Workflows basierend auf der SharePoint 2013 Workflow-Plattform. Starten eines Workflows auf der SharePoint 2013-Workflow-Plattform von innerhalb eines Workflows, die auf die gleiche Plattform integriert wird nicht unterstützt.
  
    
    


## Verwenden von Koordinationsaktionen
<a name="section2"> </a>

Es gibt eine Reihe von Aktionen, die in der SharePoint 2013 Workflow-Plattform veraltet sind. Legacy-Workflows zur Erfüllung können Sie Koordinationsaktionen verwenden. Koordinationsaktionen dienen zum Starten einer Listenworkflow oder Website-Workflow, der mithilfe der SharePoint 2010-Workflow-Plattform erstellt wurde.
  
    
    
Eine Aktion Koordinierung umfasst drei bearbeitbare Bereichen wie in der Abbildung dargestellt.
  
    
    

**Abbildung: Starten einer Listenworkflow-koordinierungsaktion**

  
    
    

  
    
    
![Starten einer Listenworkflow-Koordinierungsaktion](images/SPD15-CoordinationActions2.png)
  
    
    
Die drei bearbeitbaren Bereiche sind:
  
    
    

- **Workflow für SharePoint 2010** Wählen Sie den zu startenden Workflow 2010 aus.
    
  
- **Parameter** Parameter zum Senden an die 2010-Workflows.
    
  
- **dieses Element** Das Element der 2010-Workflows ausgeführt werden soll, klicken Sie auf.
    
  
Klicken Sie auf einen bearbeitbaren Link, um Informationen eingeben. Klicken Sie auf den Link **SharePoint 2010-Listenworkflow** beispielsweise markieren Sie den zu startenden Workflow 2010. Ein Dialogfeld angezeigt wird, wählen Sie den Workflow verwendet werden, wie in der Abbildung dargestellt.
  
    
    

**Abbildung: Auswählen eines Workflows basierend auf der 2010-Plattform**

  
    
    

  
    
    
![Auswählen eines Workflows basierend auf der 2010-Plattform](images/SPD15-CoordinationActions3.png)
  
    
    

  
    
    

  
    
    

  
    
    
SharePoint 2010-Workflow-Plattform Workflow-Instanzen, die innerhalb eines SharePoint 2013-Workflows aus koordiniert werden werden auf der Workflowstatusseite im Abschnitt Statusseite aufgelistet, wie in der Abbildung dargestellt.
  
    
    

**Abbildung: Workflow-Statusseite Listet die untergeordneten Workflows**

  
    
    

  
    
    
![Auf der Workflowstatusseite sind die Unterworkflows aufgeführt.](images/SPD15-CorrelationActions4.png)
  
    
    

  
    
    

  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [What's new in workflow in SharePoint Server 2013](http://msdn.microsoft.com/library/6ab8a28b-fa2f-4530-8b55-a7f663bf15ea.aspx)
    
  
-  [Getting started with SharePoint Server 2013 workflow](http://msdn.microsoft.com/library/cc73be76-a329-449f-90ab-86822b1c2ee8.aspx)
    
  
-  [Grundlegendes zu Wörterbuchaktionen in SharePoint Designer 2013](understanding-dictionary-actions-in-sharepoint-designer-2013.md)
    
  

  
    
    

