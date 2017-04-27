---
title: Verwenden von OData-Quellen mit Business Connectivity Services in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7a87e5bf-4428-4055-b113-7665a93e7326
---


# Verwenden von OData-Quellen mit Business Connectivity Services in SharePoint 2013
Erfahren Sie mehr über die ersten Schritte bei der Erstellung externer Inhaltstypen auf der Basis von OData-Quellen und der Verwendung dieser Daten in SharePoint 2013- oder Office 2013-Komponenten.
## OData und der OData-Connector
<a name="SP15getstartedOdata_whatisodata"> </a>

Mit dem Open Data-Protokoll (OData) können Sie auf eine Datenquelle wie eine Datenbank zugreifen, indem Sie zu einer speziell zusammengesetzten URL browsen. Dies ermöglicht einen vereinfachten Ansatz für das Verbinden und Arbeiten mit Datenquellen, die in einer Organisation gehostet werden.
  
    
    
OData ist ein Protokoll, das HTTP, Atom und JavaScript Object Notation (JSON) verwendet, damit Entwickler Anwendungen schreiben können, die mit einer ständig wachsenden Anzahl von Datenquellen kommunizieren können. Microsoft unterstützt die Erstellung dieses Standards als Möglichkeit, den Austausch von Daten zwischen Anwendungen und Datenspeichern zu ermöglichen, auf die aus dem Internet zugegriffen werden kann.
  
    
    
Der neue OData-Connector ermöglicht SharePoint die Kommunikation mit OData-Anbietern.
  
    
    
In SharePoint 2013 kann Business Connectivity Services (BCS) mit OData-Quellen, oder Produzenten, ohne direkt an die OData-Quelle codieren zu müssen. Produzenten stellen ihre Daten auf eine strukturierte Weise über einen Webdienst zur Verfügung. Einige Produzenten lassen möglicherweise einige Aktualisierung der zugrunde liegenden Daten zu, andere möglicherweise nur einen schreibgeschützten Zugriff. Für Zwecke der Werbung, welche Vorgänge verfügbar sind, hat der Produzent ein Dienstdokument, das unter einem angegebenen URL-Endpunkt gefunden werden kann. SharePoint ist bereits ein OData-Produzent. SharePoint-Listendaten werden als OData-Quelle für alle Verbraucher zur Verfügung gestellt, die über die entsprechenden Rechte verfügen.
  
    
    

### Beispiele für OData-Produzenten
<a name="ExamplesOfODataProducers"> </a>

Im Folgenden finden Sie einige Beispiele für OData-Implementierungen. Diese Anwendungen und Dienste stellen ihre Daten über das OData-Protokoll zur Verfügung.
  
    
    

- SharePoint Foundation 2010
    
  
- SharePoint Server 2010
    
  
- SQL Azure
    
  
- Microsoft Azure Table Storage
    
  
- Microsoft Azure Marketplace
    
  
-  SQL Server Reporting Services
    
  
- Microsoft Dynamics CRM 2011
    
  
- Windows Live
    
  
Eine Liste der Produzenten von OData-Diensten finden Sie auf der  [Open Data Protocol-Website](http://www.odata.org/ecosystem).
  
    
    

## Voraussetzungen für das Arbeiten mit dem BCS-OData-Connector
<a name="SP15GetstartedOdata_prereq"> </a>

Zum Entwickeln von OData-basierten externen Inhaltstypen benötigen Sie Folgendes:
  
    
    

- Visual Studio 2012
    
  
- SharePoint 2013
    
  
- Office Developer Tools für Visual Studio 2012
    
  
Informationen zum Einrichten Ihrer Entwicklungsumgebung finden Sie unter  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

## Erstellen von externen Inhaltstypen für OData-Datenquellen
<a name="SP15GetstartedOdata_creatingECT"> </a>

Damit SharePoint die von einem bestimmten OData-Produzenten zur Verfügung gestellten Daten verwenden kann, muss ein externer Inhaltstyp in SharePoint erstellt werden. Wie bei allen externen SharePoint-Inhaltstypen enthält dieser alle Konnektivitätsinformationen, die für die Verbindung und Kommunikation mit dem externen System erforderlich sind.
  
    
    
Das Erstellen eines externen Inhaltstyps, der eine OData-Datenquelle verwendet, ähnelt der Erstellung beliebiger externer Inhaltstypen. Sie können Visual Studio 2012 verwenden, um automatisch externe OData-Inhaltstypen zu generieren. Sie stellen lediglich den REST-Endpunkt (Representational State Transfer) der OData-Quelle bereit, wenn Sie den externen Inhaltstyp erstellen. Weitere Informationen finden Sie unter  [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md).
  
    
    

## Inhalt dieses Abschnitts
<a name="SP15GetstartedOdata_inthissect"> </a>


-  [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen einer OData-Datendiensts zur Verwendung als einer externen BCS-System](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md)
    
  
-  [Vorgehensweise: Erstellen eine externe Liste mithilfe einer in SharePoint 2013 OData-Datenquelle](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md)
    
  

## Zusätzliche Ressourcen
<a name="SP15GetstartedOdata_addres"> </a>


-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [Was ist neu in Business Connectivity Services in SharePoint 2013](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Business Connectivity Services-Programmierreferenz für SharePoint 2013](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  

