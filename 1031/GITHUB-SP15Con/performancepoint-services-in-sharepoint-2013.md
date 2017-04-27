---
title: PerformancePoint-Dienste in SharePoint 2013
keywords: accessing fco definitions in sharepoint 2013,bi in sharepoint 2013 using performancepoint services,business intelligence in sharepoint 2013,business intelligence using performancepoint services in sharepoint 2013,create scorecard transforms using performancepoint in sharepoint 2013,custom filter control in sharepoint 2013,custom performancepoint extensions,customize performancepoint in sharepoint,data source creation in sharepoint 2013,dlls used for performancepoint development,extending performancepoint services for sharepoint,fcos in sharepoint performancepoint,filter creation in sharepoint 2013,filters as fcos in pps performancepoint,getting started with performancepoint services,integration of performancepoint services in sharepoint,performancepoint assemblies used in development,performancepoint custom data sources,performancepoint custom filters,performancepoint custom reports,performancepoint custom scorecard transforms,performancepoint development scenarios,performancepoint services development,performancepoint services development scenarios,performancepoint services programming,performancepoint services sdk,pps custom dashboards in sharepoint 2013,pps development,pps programming,pps sdk,report creation in sharepoint 2013,report renderer in sharepoint 2013,SharePoint 2013 service application PerformancePoint
f1_keywords:
- accessing fco definitions in sharepoint 2013,bi in sharepoint 2013 using performancepoint services,business intelligence in sharepoint 2013,business intelligence using performancepoint services in sharepoint 2013,create scorecard transforms using performancepoint in sharepoint 2013,custom filter control in sharepoint 2013,custom performancepoint extensions,customize performancepoint in sharepoint,data source creation in sharepoint 2013,dlls used for performancepoint development,extending performancepoint services for sharepoint,fcos in sharepoint performancepoint,filter creation in sharepoint 2013,filters as fcos in pps performancepoint,getting started with performancepoint services,integration of performancepoint services in sharepoint,performancepoint assemblies used in development,performancepoint custom data sources,performancepoint custom filters,performancepoint custom reports,performancepoint custom scorecard transforms,performancepoint development scenarios,performancepoint services development,performancepoint services development scenarios,performancepoint services programming,performancepoint services sdk,pps custom dashboards in sharepoint 2013,pps development,pps programming,pps sdk,report creation in sharepoint 2013,report renderer in sharepoint 2013,SharePoint 2013 service application PerformancePoint
ms.prod: SHAREPOINT
ms.assetid: fb159708-d6b4-40c1-b5cc-4bb2071a7930
---



# PerformancePoint-Dienste in SharePoint 2013
Informationen Sie über unterstützte Entwicklungsszenarien und die der Erweiterbarkeitsarchitektur für PerformancePoint-Dienste in SharePoint Server 2013.
 * **Gilt für:*** 
  
    
    


|||
|:-----|:-----|
|**In diesem Artikel**          [Benutzerdefinierte PerformancePoint-Dienste Berichte, Filter und tabellarische Datenquellen in SharePoint Server 2013](#bkmk_CreateCustomObjects)           [benutzerdefinierte scorecardtransformationen für PerformancePoint Services-Scorecards](#bkmk_CreateTransforms)           [Der Erweiterbarkeitsarchitektur für PerformancePoint-Dienste in SharePoint Server 2013](#bkmk_PerfPointArch)           [Zusätzliche Ressourcen](#bkmk_AdditionalResources) <br/> |
  
    
    
![Verwandte Codeausschnitte und Beispiel-Apps](images/mod_icon_links_samples.png)
  
    
    

  
    
    
 [PerformancePoint Services SDK Reference Sample](http://archive.msdn.microsoft.com/ppsSdkRefSample) <br/> |
   

PerformancePoint-Dienste ist eine SharePoint Server 2013-Dienstanwendung. Sie können Benutzer Business Intelligence (BI)-Dashboards erstellen, die einen Einblick in die Leistung einer Organisation bereitstellen. Sie können Erstellen benutzerdefinierter Berichte, Filter, tabellendatenquellen und scorecardtransformationen zum Erweitern der systemeigenen Funktionen von PerformancePoint-Dienste. Beispielsweise können Sie eine benutzerdefinierte berichtvisualisierung erstellen, die für die medizinische Branche optimiert ist und klicken Sie dann in eine wiederverwendbare vertikale Lösung integriert.
  
    
    


## Benutzerdefinierte PerformancePoint-Dienste Berichte, Filter und tabellarische Datenquellen in SharePoint Server 2013
<a name="bkmk_CreateCustomObjects"> </a>

Sie können systemeigene PerformancePoint-Dienste  [ReportView](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.ReportView.aspx) , [Filter](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Filter.aspx) und tabellarischen [DataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.aspx) Objekte erweitern, indem Sie benutzerdefinierte Werte für deren Eigenschaften definieren. Benutzerdefinierte Berichte, Filter und tabellarischen Datenquellenerweiterungen umfassen in der Regel drei Komponenten: ein Renderer oder Anbieter, ein Editor-Anwendung und Erweiterungsmetadaten.
  
    
    

### Renderer und Anbietern für PerformancePoint-Dienste-Erweiterungen

Der Typ des Objekts, die Sie erweitern bestimmt, ob es ein Renderer oder ein Anbieter verwendet wird. Berichts- und Erweiterungen Renderern verwenden, und Filtern und Datenquellenerweiterungen verwenden Anbieter.
  
    
    

- Bei Berichterweiterungen ist für die Berichtvisualisierung ein Renderer erforderlich.
    
  
- Filtererweiterungen erforderlich für das Steuerelement zur Auswahl ein Renderer. Renderer kann eines benutzerdefinierten Renderers oder einer systemeigenen PerformancePoint-Dienste Renderer sein. Wenn Sie einen PerformancePoint-Dienste Renderer verwenden, registrieren Sie einfach in der Erweiterung. Wenn Sie einen benutzerdefinierten Renderer verwenden, müssen Sie auch in der Erweiterung einbeziehen.
    
  
- Filtererweiterungen erfordern einen Verbindung mit der zugrunde liegenden Datenquelle Datenanbieter.
    
  
- Bei Datenquellenerweiterungen ist zum Herstellen der Verbindung mit der zugrunde liegenden Datenquelle ein Anbieter erforderlich.
    
  
Weitere Informationen finden Sie unter den folgenden Themen zum Erstellen von Renderern und Anbieter:
  
    
    

-  [Vorgehensweise: Erstellen von berichtsrenderern für PerformancePoint Services in SharePoint 2013](how-to-create-report-renderers-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen Filter von Datenanbietern für PerformancePoint Services in SharePoint 2013](how-to-create-filter-data-providers-for-performancepoint-services-in-sharepoint.md)
    
  
-  [Vorgehensweise: Erstellen von Anbietern für tabellarische Datenquellen für PerformancePoint Services in SharePoint 2013](how-to-create-tabular-data-source-providers-for-performancepoint-services-in-sha.md)
    
  

### Editor-Anwendungen für PerformancePoint-Dienste-Erweiterungen in SharePoint Server 2013

Benutzerdefinierte Editoren können Benutzer Eigenschaften für ein benutzerdefiniertes Objekt definieren, interagieren Sie mit Objekten im Repository und Endpunkte für benutzerdefinierte Berichte und Filter zu initialisieren. Editor sollte die Eigenschaften verfügbar machen, die Sie Aktivieren von Benutzern anzeigen und ändern möchten. Editoren können von Objekten in PerformancePoint Dashboard-Designer oder Elemente in der PerformancePoint-Inhaltsliste oder PerformancePoint-Datenverbindungsbibliothek geöffnet werden. Um in die für die Webseitenerstellung Dashboard-Designer integrieren, muss der Editor aus einen uniform Resource Identifier (URI) zu öffnen und der URI muss für die benutzerdefiniertes Objekt in der web.config-Datei PerformancePoint-Dienste registriert werden.
  
    
    
Weitere Informationen zum Erstellen von Editoren finden Sie unter den folgenden Themen:
  
    
    

-  [Vorgehensweise: erstellen Bericht-Editoren für PerformancePoint Services in SharePoint 2013](how-to-create-report-editors-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen Filter-Editoren für PerformancePoint Services in SharePoint 2013](how-to-create-filter-editors-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen tabellarische Datenquelle-Editoren für PerformancePoint Services in SharePoint 2013](how-to-create-tabular-data-source-editors-for-performancepoint-services-in-share.md)
    
  

> **HINWEIS**
> PerformancePoint Dashboard-Designer können erstellt und benutzerdefinierte Objekte löschen, damit Ihre Editor nicht notwendigerweise Logik zum Erstellen oder Löschen von Objekten bereitzustellen.
  
    
    


### Von Konfigurationsmetadaten für PerformancePoint-Dienste-Erweiterungen in SharePoint Server 2013

Sie müssen während des Installationsvorgangs Metadaten für die Erweiterung in der PerformancePoint-Dienste web.config-Datei angeben. Die Metadaten enthält **type**, **subType**, **RendererClass**, **EditorURI**und **Resources** Attribute.
  
    
    
Zum Erstellen eines benutzerdefinierten Objekts Dashboard-Designer Ruft Metadaten für das Objekt aus der PerformancePoint-Dienste web.config-Datei und dann das Objekt als einen Inhaltstyp im Repository Dashboard-Designer erstellt. Nach dem Erstellen des benutzerdefinierten Objekts zeigt Dashboard-Designer eine Verknüpfung zum-Editor.
  
    
    
For more information about extension metadata, see  [Gewusst wie: Manuelles Registrieren von PerformancePoint-Dienste-Erweiterungen](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx).
  
    
    

## Benutzerdefinierte Transformationen für Scorecards in SharePoint Server 2013PerformancePoint-Dienste
<a name="bkmk_CreateCustomObjects"> </a>

Transformationen Ändern der Darstellung, den Inhalt oder die Funktionalität der Scorecards vor Abfragen der Datenquelle nach Abfragen der Datenquelle oder vor dem Rendern der Scorecard im Webpart. Beispielsweise PerformancePoint-Dienste Transformationen verwendet, um verschiedene Vorgänge ausführen, vor dem Rendern einer Scorecardansicht, z. B. das benannte Mengen, erweitern computing Rollups und Netzwerke Aggregations. Diese Änderungen werden während der Laufzeit angewendet, und sie die Definition des scorecardobjekts nicht ändern.
  
    
    
For more information about scorecard transforms, see  [Vorgehensweise: Erstellen von scorecardtransformationen für PerformancePoint Services in SharePoint 2013](how-to-create-scorecard-transforms-for-performancepoint-services-in-sharepoint-2.md).
  
    
    

> **HINWEIS**
> Wenn eine Transformation die Datenwerte einer Scorecard ändert, werden die Änderungen direkt in Strategiekartenberichte eingefügt, die die Scorecard als Datenquelle verwenden. Darüber hinaus können sich Änderungen an Scorecards auf KPI-Detailberichte auswirken.
  
    
    


## Der Erweiterbarkeitsarchitektur für PerformancePoint-Dienste in SharePoint Server 2013
<a name="bkmk_PerfPointArch"> </a>

Unterstützte Anwendungserweiterungen führen innerhalb einer Anwendungsinstanz PerformancePoint-Dienste, auf dem Front-End-Webserver oder auf dem Anwendungsserver aus, wie in der folgenden Abbildung dargestellt.
  
    
    

**Abbildung 1. Erweiterbarkeitsarchitektur von PerformancePoint Services**

  
    
    

  
    
    
![Erweiterbarkeitspunkte der PerformancePoint-Dienste](images/SPS14_PerfPoint_ArchOverview.gif)
  
    
    

### Führen Sie auf dem Front-End-Webserver SharePoint Server 2013PerformancePoint-Dienste-Erweiterungen

Benutzerdefinierte Editoren (und andere unterstützten benutzerdefinierten Anwendungen) auf dem Front-End-Webserver in einer Instanz einer Anwendung PerformancePoint-Dienste ausführen. Editoren sind in der Regel als ASPX-Seiten bereitgestellt und in den Pfad  `%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS`installiert sind. Editoren rufen das  [BIMonitoringServiceApplicationProxy](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.BIMonitoringServiceApplicationProxy.aspx) oder [SPDataStore](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Store.SPDataStore.aspx) -Objekt für den Autor oder Prozesskonto Content wie folgt:
  
    
    

- Berichts- und Filterobjekte sollten  [SPDataStore](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Store.SPDataStore.aspx) für alle Repository-Vorgänge verwenden.
    
  
- Datenquellenobjekte sollten  [BIMonitoringServiceApplicationProxy](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.BIMonitoringServiceApplicationProxy.aspx) verwenden, um **Create** und **Update** Aufgaben ausführen, damit diese Aufgaben im Kontext der PerformancePoint-Dienste-Anwendung ausgeführt werden. **Read** (get) und **Delete** Aufgaben mithilfe von [BIMonitoringServiceApplicationProxy](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.BIMonitoringServiceApplicationProxy.aspx) oder [SPDataStore](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Store.SPDataStore.aspx) ausgeführt werden können. (Allerdings können benutzerdefinierte Datenquelle Anwendungen, die auf dem Anwendungsserver ausgeführt [SPDataStore](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Store.SPDataStore.aspx) direkt aufrufen.)
    
  

### Führen Sie auf dem Anwendungsserver SharePoint Server 2013PerformancePoint-Dienste-Erweiterungen

Benutzerdefinierte Renderer, Anbieter und scorecardtransformationen auf dem Anwendungsserver ausgeführt. Der Anwendungsserver gehostet wird, die Middle-Tier-Geschäftslogik für die PerformancePoint-Dienste-Instanz.
  
    
    

## Zusätzliche Ressourcen
<a name="bkmk_AdditionalResources"> </a>


-  [Grundlagen der PerformancePoint Services-Entwicklung](http://msdn.microsoft.com/library/5d2c183b-95f8-4930-b6d0-f3ffe1ee166e%28Office.15%29.aspx)
    
  
-  [Codebeispiele für PerformancePoint Services in SharePoint Server 2010](http://msdn.microsoft.com/library/97f0cbd4-03ef-44f8-9869-699df9d9c97f%28Office.15%29.aspx)
    
  
-  [Problembehandlung und FAQs für PerformancePoint Services-Entwicklung](http://msdn.microsoft.com/library/a90156e2-0522-46a1-9fc9-b6c8d2fffad7%28Office.15%29.aspx)
    
  
