---
title: Vorgehensweise erstellen ein Add-in-bezogenen externes Inhaltstyps in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: de4b50a3-84da-48ce-9ba0-fe06571e52a8
---


# Vorgehensweise: erstellen ein Add-in-bezogenen externes Inhaltstyps in SharePoint 2013
In diesem Artikel erfahren Sie, wie Sie externe Inhaltstypen erstellen, die in einer SharePoint-Add-In installiert, gesichert und verwendet werden können.
## Erforderliche Komponenten für die Entwicklung von add-in-bezogenen externen Inhaltstypen
<a name="bkmk_Prerequisites"> </a>

Wenn Sie die ersten Schritte beim Entwickeln von add-in-bezogenen externen Inhaltstypen, benötigen Sie Folgendes:
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools für Visual Studio 2012
    
  
- Einen veröffentlichten OData-Dienst, der über das Internet verfügbar ist
    
  
Informationen zum Einrichten einer SharePoint-Entwicklungsumgebung finden Sie unter  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

## Erstellen Sie einen Add-in-bezogenen externen Inhaltstyp
<a name="bkmk_CreateECT"> </a>

Die folgenden Schritte zeigen zum Erstellen eines externen Inhaltstyps basierend auf einer Open Data Protocol (OData) Datenquelle, und ändern sie Ihre SharePoint-Add-In zugewiesen werden.
  
    
    

### So erstellen Sie ein neues SharePoint-Add-In


1. Öffnen Sie Visual Studio 2012.
    
  
2. Erstellen Sie ein Projekt **-Add-in für SharePoint 2013**.
    
  
3. Geben Sie die Add-in-Einstellungen, einschließlich der Add-in-Name die URL der Website für das Debuggen des Add-Ins und wie Sie das Add-in (automatisch gehostet, vom Anbieter gehostete oder SharePoint-Hosting) hosten möchten. Weitere Informationen finden Sie unter  [Auswählen von Mustern für die Entwicklung und das Hosting Ihres Add-Ins für SharePoint](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx).
    
  
4. Wählen Sie auf **Fertig stellen**, um die app zu erstellen.
    
  
Führen Sie die Schritte zum Erstellen von SharePoint-Add-Ins finden Sie in der folgenden:
  
    
    

-  [Erste Schritte beim Erstellen von von einem Anbieter gehosteten SharePoint-Add-Ins](http://msdn.microsoft.com/library/3038dd73-41ee-436f-8c78-ef8e6869bf7b%28Office.15%29.aspx)
    
  
-  [So geht's: Erstellen einer einfachen automatisch gehosteten App für SharePoint](http://msdn.microsoft.com/library/0572894d-c437-4b7d-8ac6-8405496e2145%28Office.15%29.aspx)
    
  
-  [Erste Schritte beim Erstellen von von SharePoint gehosteten SharePoint-Add-Ins](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx)
    
  

### Um den externen Inhaltstyp zu generieren.


1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Hinzufügen** und **Inhaltstypen für externe Datenquelle** aus.
    
    Einen Assistenten, der können Sie die ausgewählten Datenquelle suchen und erstellen Sie das BDC-Modell, wird gestartet.
    
  
2. Geben Sie auf der Seite **Set OData Source** die URL des OData-Diensts, die Sie mit verbinden möchten. Die URL sollte etwa wie folgt aussehen: `http://services.odata.org/Northwind/Northwind.svc/`.
    
    Geben Sie einen Namen für die OData-Quelle.
    
    > **HINWEIS**
      > In diesem Beispiel verwenden Sie den Northwind-Dienst, der in der Hersteller-Liste, die sich nicht auf der  [Website Open Data Protocol](http://www.odata.org)verfügbar ist.
3. Eine Liste wird angezeigt, mit Datenentitäten, die vom OData Service verfügbar gemacht werden. Wählen Sie eine oder mehrere Entitäten, und wählen Sie **Fertig stellen**.
    
  

### Zum Bereitstellen von des Add-in-bezogenen externen Inhaltstyps


- Drücken Sie F5, um kompilieren Sie das Projekt, und laden die Projektdateien in SharePoint.
    
  

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Add-in-bezogenen externen Inhaltstypen in SharePoint 2013](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [Auswählen von Mustern für die Entwicklung und das Hosting Ihres Add-Ins für SharePoint](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
    
  
-  [SharePoint-Add-Ins](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [Erste Schritte mit den Business Connectivity Services in SharePoint 2013](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  

