---
title: Erste Schritte mit den Business Connectivity Services in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c6bf3db0-db79-4b13-9834-891d24b2c9e5
---



# Erste Schritte mit den Business Connectivity Services in SharePoint 2013
Lernen Sie die Grundlagen dessen, was Business Connectivity Services (BCS) für Entwickler von SharePoint 2013-Lösungen bietet, sowie die ersten Schritte beim Verwenden von BCS in verschiedenen Arten von Lösungen.
## Was sind Business Connectivity Services?


|||
|:-----|:-----|
|Business Connectivity Services (BCS) wurde in SharePoint Server 2010 als eine Weiterentwicklung des in Office SharePoint Server 2007 veröffentlichten Geschäftsdatenkatalogs eingeführt. BSC ermöglicht SharePoint 2013 das Arbeiten mit extern gehosteten Daten. Mögliche Quellen können Datenbanken, Webdienste, Windows Communication Foundation (WCF)-Dienste, OData-Quellen und weitere proprietären Daten enthalten, auf die mithilfe der benutzerdefinierten .NET-Assemblys zugegriffen wird. [![Einrichten](images/mod_icon_getstartbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatDoYouNeed) [![Den Einstieg finden](images/mod_icon_dobox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatCanYouDo) [![Weitere Informationen](images/mod_icon_startbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_LearnMore)|
**Sehen Sie sich das Video an: Übersicht über SharePoint 2013 Business Connectivity Services und OData-Dienste**

  
    
    

  
    
    
![Videos](images/mod_icon_video.png)
  
    
    

  
    
    

  
    
    
|
   
In einer dynamischen Arbeitsumgebung benötigen Information-Worker Zugriff auf Daten, die in separater Software enthalten sind, z. B.:
  
    
    

- Strukturierte Daten in den Unternehmensanwendungen der Organisation, z. B. ERP- und CRM-Anwendungen
    
  
- Unstrukturierte Daten in Geschäftsproduktivitätsanwendungen, z. B. solche in Microsoft Office, in Team- und Zusammenarbeitsanwendungen wie SharePoint und in Web 2.0-Diensten wie Internetanwendungen, Wikis, Blogs und sozialen Netzwerken.
    
  
Obwohl die meisten Information-Worker die größte Zeit über innerhalb der Produktivitätsanwendungen arbeiten (z. B. der Microsoft Office-Umgebung, benötigen sie auch eine Möglichkeit zum Integrieren dieser Umgebung in die verwendeten Unternehmensanwendungen und Zusammenarbeitssoftware und Dienste. Der Geschäftsdatendatenkatalog stellt diese Funktion in SharePoint 2013 bereit.
  
    
    

## Erste Schritte mit Business Connectivity Services
<a name="SP15GettingStartedBCS_WhatDoYouNeed"> </a>

Sie benötigen zunächst Folgendes, um mit der Entwicklung mit Business Connectivity Services zu beginnen:
  
    
    

- SharePoint 2013
    
  
- Visual Studio
    
  
- Office Developer Tools für Visual Studio 2012
    
    oder
    
  
- SharePoint Designer
    
  
Informationen zum Einrichten Ihrer Entwicklungsumgebung finden Sie unter  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

### Grundlagen zu Business Connectivity Services

Die folgende Tabelle zeigt die Kernkonzepte, mit denen Sie sich vertraut machen müssen, bevor Sie mit der Entwicklung von BCS-Lösungen beginnen.
  
    
    

**Tabelle 1. Kernkonzepte zum Verständnis von BSC.**


|**Artikel**|**Beschreibung**|
|:-----|:-----|
| [Entity Data Model - Schlüsselkonzepte](http://msdn.microsoft.com/de-de/library/ee382840.aspx) <br/> |Das Entity Data Model (EDM) verwendet drei Schlüsselkonzepte zum Beschreiben der Datenstruktur: Entitätstyp, Zuordnungstyp und Eigenschaft. Dies sind die wichtigsten Konzepte beim Beschreiben der Datenstruktur in allen Implementierungen von EDM.  <br/> |
| [Grundlegende Sicherheitsmaßnahmen für Webanwendungen](http://msdn.microsoft.com/de-de/library/zdh19h94.aspx) <br/> |Das Erstellen sicherer Webanwendungen ist ein sehr umfangreiches Thema. Sie müssen sich auch mit den Sicherheitsfunktionen des Windows-Betriebssystems vertraut machen, .NET Framework und ASP.NET. Es ist wichtig, zu verstehen, wie diese Sicherheitsfunktionen zu verwenden sind, um Bedrohungen entgegenzuwirken.  <br/> |
| [WCF Data Services](http://msdn.microsoft.com/de-de/data/odata.aspx) <br/> |WCF Data Services, früher ADO.NET Data Services genannt, ermöglichen die Erstellung und Verarbeitung von OData-Diensten für das Web.  <br/> |
| [Open Data Protocol (OData)](http://www.odata.org) <br/> |OData ist ein Industriestandardprotokoll für den Zugriff auf Daten über URLs. Es befindet sich im Grunde über dem HTTP-Protokoll, um Funktionen mithilfe von vorhandenen HTTP-Verben zu lesen und zu schreiben.  <br/> |
| [Internetinformationsdienste](http://www.iis.net/) <br/> |Internetinformationsdienste (IIS) ist eine Plattform, auf der SharePoint ausgeführt wird. Sie müssen nachvollziehen können, wie Websites, virtuelle Verzeichnisse, Webdienste, URLs, Websicherheit und weitere mit IIS verwandte Technologien erstellt werden können.  <br/> |
| [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |Externe Inhaltstypen sind Beschreibungen externer Systeme, die sie darstellen. Sie können wiederverwendet werden, wenn sie in SharePoint importiert werden, und können zum Erstellen komplexer codefreier Lösungen mithilfe von SharePoint Designer 2013, Outlook 2013, Webparts, externen Listen und benutzerdefinierten Clientanwendungen verwendet werden.  <br/> |
| [Erste Schritte der Verwendung des Clientobjektmodells mit externen Daten in SharePoint 2013](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md) <br/> |SharePoint 2013bietet die Möglichkeit, auf alle Objekte über eine sorgfältig erstellte URL zuzugreifen. BCS wurde erweitert, um diese Funktionalität bereitzustellen.  <br/> |
   

## Welche Möglichkeiten bieten Business Connectivity Services?
<a name="SP15GettingStartedBCS_WhatCanYouDo"> </a>

Mit BCS können Sie Informationen aus verschiedenen Quellen zu SharePoint verschieben. Sie können beispielsweise Daten aus einer externen SQL Server-Datenbank, einem gewöhnlichen Webdienst, einem WCF-Dienst, aus proprietären Systemen und OData-Diensten zu SharePoint verschieben.
  
    
    

**Tabelle 2. Allgemeine Aufgaben beim Arbeiten mit Business Connectivity Services**


|**Aufgabe**|**Beschreibung**|
|:-----|:-----|
| [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |Informationen zum Erstellen von externen Business Connectivity Services (BCS)-Inhaltstypen.  <br/> |
| [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |Hier erhalten Sie Informationen zu den ersten Schritten bei der Erstellung von auf OData-Quellen basierenden externen Inhaltstypen und der Verwendung dieser Daten in SharePoint oder Office-Komponenten.  <br/> |
| [Vorgehensweise: Erstellen von externen Ereignisempfängern](how-to-create-external-event-receivers.md) <br/> |Informationen zu Konzepten hinter dem Erstellen von Ereignisempfängern, die externen Listen angefügt und ausgeführt werden, wenn die von dieser Liste dargestellten externen Daten aktualisiert werden.  <br/> |
| [Vorgehensweise: erstellen ein Add-in-bezogenen externes Inhaltstyps in SharePoint 2013](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md) <br/> |Erfahren Sie, wie Sie externe Inhaltstypen erstellen, die auf App-Ebene installiert oder vorhanden sind, und Entwicklern das Erstellen von Apps mit hohem Datenaufkommen mithilfe von externen Datenquellen ermöglichen.  <br/> |
| [Vorgehensweise: Verwenden Sie die Code-Clientbibliothek Zugriff auf externe Daten in SharePoint 2013](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |Erfahren Sie, wie Sie das SharePoint 2013-Clientobjektmodell für die Arbeit mit BCS in SharePoint 2013 verwenden.  <br/> |
   

## Weiterführendes: Weitere Informationen zu Business Connectivity Services
<a name="SP15GettingStartedBCS_LearnMore"> </a>

Wenn Sie die grundlegenden Konzepte von BCS beherrschen, können Sie erweiterte Funktionen zum Erstellen leistungsstarker Lösungen verwenden.
  
    
    

**Tabelle 3. Erweiterte Konzepte in BCS**


|**Thema**|**Beschreibung**|
|:-----|:-----|
| [Vorgehensweise: Erstellen einer OData-Datendiensts zur Verwendung als einer externen BCS-System](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md) <br/> |In diesem Artikel erfahren sie, wie Sie einen im Internet aufrufbaren WCF-Dienst erstellen, der OData zum Senden von Benachrichtigungen an SharePoint 2013 verwendet, wenn die zugrunde liegenden Daten geändert werden. Mithilfe dieser Benachrichtigungen werden Ereignisse ausgelöst, die mit externen Listen verknüpft sind.  <br/> |
| [BDC-Modell-Schemareferenz für SharePoint 2013](bdc-model-schema-reference-for-sharepoint-2013.md) <br/> |Hier finden Sie die Referenzdokumentation zum Schema des BDC-Modells.  <br/> |
| [BCS-Client-Objektmodellreferenz für SharePoint 2013](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |Zusammenfassung der für das Erstellen clientseitiger Skripts verfügbaren Objekte unter Verwendung des SharePoint 2013-Clientobjektmodells für den Zugriff auf externe von Business Connectivity Services (BCS) zur Verfügung gestellte Daten.  <br/> |
| [BCS-REST-API-Referenz für SharePoint 2013](bcs-rest-api-reference-for-sharepoint-2013.md) <br/> |Hier erhalten Sie Referenzinformationen für das Erstellen von REST-URIs, die für den Zugriff und die Manipulation von OData-Quellen verwendet werden.  <br/> |
   

## Weitere Ressourcen
<a name="SP15GettingStartedBCS_LearnMore"> </a>


-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Open Data Protocol-Website](http://www.odata.org/)
    
  
-  [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [Verwenden von OData-Quellen mit Business Connectivity Services in SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Externe Ereignisse und Warnungen in SharePoint 2013](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [Add-in-bezogenen externen Inhaltstypen in SharePoint 2013](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [Erste Schritte der Verwendung des Clientobjektmodells mit externen Daten in SharePoint 2013](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
