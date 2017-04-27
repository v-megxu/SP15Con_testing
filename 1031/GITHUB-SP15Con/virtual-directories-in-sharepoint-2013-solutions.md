---
title: Virtuelle Verzeichnisse in SharePoint 2013-Lösungen
ms.prod: SHAREPOINT
ms.assetid: c26c4160-31be-4358-89cf-082b8a1e6a6c
---


# Virtuelle Verzeichnisse in SharePoint 2013-Lösungen
Erfahren Sie, wie Änderungen im virtuellen Verzeichnissystem auswirken, wie Sie Farmlösungen in SharePoint 2013 erstellen.
## Stellen Sie Ihre Lösungen mit dem neuen Benutzeroberfläche Modus System kompatibel

Wenn Sie die Microsoft SharePoint 2010 Software Development Kit (SDK) verwenden, aber für SharePoint 2013 entwickeln, ist es eine Änderung im virtuellen Verzeichnissystem, das Sie während der Arbeit berücksichtigen müssen, an. Die Änderung erfolgt ist eine Auswirkung der neuen SharePoint 2013-Feature, mit dem eine Websitesammlung im entweder SharePoint 2010 oder SharePoint 2013 Modus ausgeführt. Die Modi werden manchmal Kompatibilität Ebenen oderBenutzeroberflächenversionenbezeichnet. SharePoint muss für die Dateien in die virtuelle Ordner  `_layouts` oder `_controltemplates`die Version der Dateien in %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ (den 15 Strukturbezeichnet) oder in den entsprechenden 14 Hive, je nach den Modus der Websitesammlung verwenden. Fügt SharePoint "/ 15" in den Pfad des virtuellen Verzeichnisses nach dem Namen des virtuellen Verzeichnisses zu signalisieren, dass die SharePoint 2013-Dateien verwendet werden soll. Keine zusätzlichen generiert gibt an, dass SharePoint 2010 Dateien verwendet werden soll.
  
    
    
Dieses neue System wirkt sich für Sie bei der Entwicklung SharePoint 2013 Lösungen und apps, insbesondere, wenn Sie die SharePoint 2010 SDK verwenden. In jeder SharePoint-Add-In (die nur im SharePoint 2013 Modus ausgeführt wird) und in jeder SharePoint-Lösung, die Ihnen bekannt ist nur in Websitesammlungen verwendet werden, die im SharePoint 2013 Modus ausgeführt werden soll, müssen Sie hinzufügen die "/ 15" sich auf alle  `_layouts` und `_controltemplates` virtuelle Pfade in Ihrer Lösung/App erstellen (es sei denn, Sie der Pfad zu einer ASPX-Datei zeigen) , obwohl diese Zeichenfolge nicht in eine beliebige Anweisungen angezeigt wird Sie in der SharePoint 2010 SDK gelesen. Beispielsweise wenn die SharePoint 2010 SDK Sie `~/_layouts/images/myimage.png`verwenden weist, sollten Sie  `~/_layouts/15/images/myimage.png` verwenden, bei der Entwicklung für SharePoint 2013.
  
    
    
Wenn Sie Ihre Lösung mit Websitesammlungen der beiden Modi kompatibel vornehmen müssen, müssen Sie bestimmen den Modus der aktuellen Websitesammlung und erstellen den virtuellen Pfad entsprechend Logik für die Verzweigung. Die  [CompatibilityLevel](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.CompatibilityLevel.aspx) -Eigenschaft, die in allen SharePoint-Clientobjektmodelle und der REST-Schnittstelle verfügbar ist, wird einer Stelle, wo der Code für den Modus überprüfen können. Die [SPUtility](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.aspx) -Klasse enthält auch mehrere neue Eigenschaften zur Unterstützung bei der Kompatibilitätsebene in Ihren Lösungen verwalten. Diese sind nicht in der Clientobjektmodelle verfügbar. Es gibt mehrere Steuerelemente in SharePoint, die eine **UIVersion** -Eigenschaft verfügbar, die Ihr Code auch verwenden machen, um den aktuellen Kompatibilitätsgrad finden.
  
    
    

> **HINWEIS**
> Wenn die Datei im virtuellen Pfad *.aspx ist, SharePoint automatisch erkennt den Modus der aktuellen Websitesammlung und die Datei aus dem entsprechenden Hive zurückgeben. Damit Sie nicht zum Einfügen der "/ 15" in den virtuellen Pfad.
  
    
    


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Erstellen von Farmlösungen in SharePoint 2013](build-farm-solutions-in-sharepoint-2013.md)
    
  
-  [Planen der Bereitstellung von Farmlösungen für SharePoint 2013](http://blogs.technet.com/b/mspfe/archive/2013/02/04/planning-deployment-of-farm-solutions-for-sharepoint-2013.aspx)
    
  
-  [SPUtility properties](http://msdn.microsoft.com/library/Properties.T:Microsoft.SharePoint.Utilities.SPUtility.aspx)
    
  

