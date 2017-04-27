---
title: Grundlegendes zu packen und POST von Workflows in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 545b4930-ac05-4c9d-9980-5818cb800cf1
---


# Grundlegendes zu packen und POST von Workflows in SharePoint 2013
Informationen Sie zum Verpacken und Bereitstellen eines Workflows in SharePoint Server 2013 mit SharePoint Designer 2013.
## Übersicht über die Verpackung Workflowfunktionen von SharePoint Designer 2013
<a name="section1"> </a>

SharePoint Designer 2013 bietet die Möglichkeit, einen Workflow als Vorlage speichern. Speichern ein Workflows als Vorlage wird auch als Workflow Packen bezeichnet. Nachdem der Workflow als Vorlage gespeichert wurde, kann es dann in anderen Umgebungen SharePoint Server 2013 importiert und verwendet, ohne die Notwendigkeit des Workflows Sicherheitsbasis. Nicht alle Workflowtypen können als Vorlage gespeichert werden. Die folgende Matrix zeigt die Workflowtypen, die als Vorlage gespeichert werden können.
  
    
    

**Unterstützung von Plattform für einen Workflow als Vorlage speichern**


|**Workflowtyp**|**SharePoint 2010 Workflow-Plattform**|**SharePoint 2013-Workflowplattform**|
|:-----|:-----|:-----|
|Listenworkflow <br/> |Nein <br/> |Ja <br/> |
|Website-Workflow <br/> |Nein <br/> |Ja <br/> |
|Wieder verwendbaren Workflows <br/> |Ja <br/> |Ja <br/> |
   

  
    
    

  
    
    

> **HINWEIS**
> SharePoint Server 2013 enthält zwei unterschiedliche Workflow-Plattformen: der SharePoint 2010-Workflow-Plattform und der SharePoint 2013-Workflow-Plattform. Beide Plattformen sind in SharePoint Server 2013 verfügbar. Weitere Informationen zu den zwei Workflow finden Sie unter  [Getting started with SharePoint Server 2013 workflow.](http://msdn.microsoft.com/library/cc73be76-a329-449f-90ab-86822b1c2ee8.aspx)
  
    
    


## Packen eines Workflows mithilfe von SharePoint Designer 2013
<a name="section2"> </a>

Der Prozess für das Verpacken eines Workflows umfasst das Speichern des Workflows in eine Vorlagendatei mit SharePoint Designer 2013. Ein Workflow-Paket liegt in Form einer Datei Web Solution Package (WSP) und hat die Dateierweiterung WSP. Wenn Sie ein Paket ein Workflows gehen Sie folgendermaßen vor.
  
    
    

### Paket eines Workflows


1. Öffnen Sie einen vorhandenen Workflow oder entwickeln Sie neuen Workflow in SharePoint Designer 2013.
    
  
2. Klicken Sie auf der Registerkarte **Workfloweinstellungen** im Menüband auf die Schaltfläche **Speichern als Vorlage** im Abschnitt **Verwalten**, wie in der Abbildung dargestellt.
    
   **Abbildung: Speichern Sie Workflow als Vorlage.**

  

![Paketworkflow in SPD 2013](images/SPD15-PackagingWorkflow1.png)
  

  

  
3. Ein Dialogfeld mit Informationen wird angezeigt, damit Sie wissen, dass die Vorlage in der Bibliothek **Websiteobjekte** gespeichert wurde.
    
  
4. Klicken Sie auf der Bibliothek Websiteobjekte, um die Workflowvorlage anzuzeigen, wie in der Abbildung dargestellt.
    
   **Abbildung: Eine Workflowvorlage in Websiteobjekten**

  

![Workflowvorlage in Website-Objekten.](images/SPD15-PackagingWorkflow2.png)
  

  

  

  
    
    

> **TIPP**
> Eine Workflowvorlage speichert automatisch in der Bibliothek **Websiteobjekte** der Websitesammlung, in die sich der Workflow befindet.
  
    
    


## Bereitstellen von einem Workflow-Paket in SharePoint 2013
<a name="section3"> </a>

Sie können einem Workflow-Paket bereitstellen, zu einer SharePoint-Farm oder Website, die unterscheidet sich von der Farm oder Website entwickelt wurde. In der Reihenfolge für einen Workflow muss Bereitstellung erfolgreich zwei Elemente werden erfüllt sein:
  
    
    

- Alle Workflow Abhängigkeiten wie Listen, Bibliotheken, Spalten und Inhaltstypen müssen auf der neuen Website bereits vorhanden sein.
    
  
- Jede einzelne Abhängigkeit benötigen den genauen Namen der Quelle Abhängigkeit.
    
  
Wenn ein Workflow bereitgestellt wird und die genauen Abhängigkeiten sind nicht vorhanden wird das Ergebnis einen Fehler.
  
    
    
Bevor Sie einen Workflow bereitstellen können, müssen Sie zuerst die Workflowvorlage aus der quellfarm SharePoint Server 2013 exportieren. Verwenden Sie dieses Verfahren, um eine Workflowvorlage zu exportieren.
  
    
    

### Exportieren Sie eine Workflow-Vorlage


1. Öffnen Sie SharePoint Designer 2013, und navigieren Sie zu der Bibliothek Websiteobjekte, in die Vorlage gespeichert ist.
    
  
2. Wählen Sie die Workflowvorlage aus, den, die Sie durch Klicken auf exportieren möchten.
    
  
3. Klicken Sie auf die Schaltfläche **Datei exportieren**, um die Vorlagendatei an Ihrem lokalen Computer oder einem Netzlaufwerk zu speichern, wie in der Abbildung dargestellt.
    
   **Abbildung: Exportieren der Workflowvorlage aus SharePoint Designer 2013**

  

![Workflowdatei aus SPD exportieren.](images/SPD15-PackagingWorkflow3.png)
  

  

  
Zum Bereitstellen von einem Workflow-Paket verwenden Sie dieses Verfahren.
  
    
    

### Bereitstellen einer workflowlösung


1. Öffnen Sie Internet Explorer, und navigieren Sie zu der SharePoint Server 2013 Websitesammlung, in dem Sie den Workflow bereitstellen möchten.
    
  
2. Klicken Sie auf **Websiteaktionen**, und wählen Sie **Websiteeinstellungen** aus.
    
  
3. Klicken Sie im Abschnitt **Web-Design-Kataloge** auf **Lösungen**.
    
    > **HINWEIS**
      > Klicken Sie auf der Seite **Websiteeinstellungen** für die Websitesammlung muss, um **im Lösungskatalog** zu sehen. Die Seite **Websiteeinstellungen** für eine Unterwebsite **Klicken Sie dann im Lösungskatalog** ist nicht sichtbar, wenn Sie sich befinden.
4. Klicken Sie auf **Lösung hochladen**, um die Lösung hochladen, wie in der Abbildung dargestellt.
    
   **Abbildung: Lösungsschaltfläche hoch**

  

![Schaltfläche zum Hochladen einer Lösung.](images/SPD15-PackagingWorkflow4.png)
  

  

  
5. Aktivieren Sie die Lösung, indem Sie auf die Schaltfläche **Aktivieren**, wie in der Abbildung dargestellt.
    
   **Abbildung: Dialogfeld Lösung und die Schaltfläche aktivieren**

  

![Lösung nach Hochladen aktivieren.](images/SPD15-PackagingWorkflow5.png)
  

  

  
Nachdem eine workflowlösung für eine Websitesammlung aktiviert wurde, kann es als ein Feature für alle untergeordneten Websites verfügbar. Verwenden Sie dieses Verfahren, um das Workflowfeature für eine Unterwebsite zu aktivieren.
  
    
    

### Aktivieren des Workflowfeatures


1. Öffnen Sie die **Websiteeinstellungen** auf der Website, in dem Sie das Workflowfeature aktivieren möchten.
    
  
2. Klicken Sie in der Gruppe **Websiteaktionen** auf **Websitefeatures verwalten**.
    
  
3. Klicken Sie neben dem Workflowfeature auf **Aktivieren**, wie in der Abbildung dargestellt.
    
  

**Abbildung: Aktivieren Sie Workflowfeatures für Website**

  
    
    

  
    
    
![Website-Feature aktivieren.](images/SPD15-PackagingWorkflow6.png)
  
    
    

  
    
    

  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Workflow in SharePoint 2013 ](http://technet.microsoft.com/de-de/sharepoint/jj556245.aspx)
    
  
-  [What's new in workflow in SharePoint Server 2013](http://msdn.microsoft.com/library/6ab8a28b-fa2f-4530-8b55-a7f663bf15ea.aspx)
    
  
-  [Getting started with SharePoint Server 2013 workflow](http://msdn.microsoft.com/library/cc73be76-a329-449f-90ab-86822b1c2ee8.aspx)
    
  
-  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [Kurzübersicht zu Workflowaktionen (SharePoint 2013-Workflowplattform)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Blogartikel des SharePoint Designer-Teams: Verpackungs- und Bereitstellungsszenario für Workflows](http://blogs.msdn.com/b/sharepointdesigner/archive/2012/08/30/packaging-list-site-and-reusable-workflow-and-how-to-deploy-the-package.aspx)
    
  

