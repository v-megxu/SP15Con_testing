---
title: BCS-REST-API-Referenz für SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 364fb8d7-87d9-4be7-affd-90caba3cd0c0
---



# BCS-REST-API-Referenz für SharePoint 2013

  
    
    
![Klassenbibliotheken und -verweise](images/mod_icon_badge_reference.png)
  
    
    

  
    
    

  
    
    
Enthält Referenzinformationen zum Erstellen von URLs zum Aufrufen und Bearbeiten von externen Datenquellen, die mit Business Connectivity Services (BCS) in SharePoint 2013 Representational State Transfer (REST).
## Mithilfe von Rest-APIs Zugriff auf externe Daten in SharePoint 2013
<a name="bkmk_Overview"> </a>

Die REST-Schnittstelle bereitgestellt von SharePoint 2013 können Sie die meisten SharePoint 2013 Ressourcen durch speziell gestalteten URLs zugreifen. Business Connectivity Services (BCS) verwendet diese Architektur für den Zugriff auf externe Daten.
  
    
    
Sie können externe Daten durch Erstellen URLs zugreifen, wie für den Zugriff Standardliste Elemente.
  
    
    

> **HINWEIS**
> Zugriff auf Entitäten über BDC direkt wird nicht bereitgestellt. Zum Arbeiten mit externen Daten müssen Sie eine externe Liste erstellen und verwenden die REST-URLs auf die Listenelemente in einer externen Liste zugreifen.
  
    
    

Die unterstützten HTTP-Verben für das Arbeiten mit externen Listen sind **GET**, **PUT**, **POST**und **DELETE**.
  
    
    
Im Gegensatz zu mit normalen Listen können nicht Sie eine externe Liste mithilfe von REST erstellen. Sie müssen dies tun, durch das Erstellen eines BDC-Modells und einer externen Liste mithilfe von Visual Studio 2012.
  
    
    
Die Informationen in Tabelle 1 veranschaulicht das Erstellen von Rest-URLs und die entsprechenden Client Objektmodellaufrufe und Bearbeiten von Daten aus externen Datenquellen zugreifen.
  
    
    

**In Tabelle 1. Rest-URL-Formate für den Zugriff auf externe Daten**


|**URL**|**Beschreibung**|**HTTP-Methode**|
|:-----|:-----|:-----|
| `http://[sharepointsite]/_api` <br/> |Die Basis des eine REST-Anforderung. Das virtuelle Verzeichnis _api zugeordnet ist, um Aufrufe client.svc, wo das Clientobjektmodell verwendet werden. <br/> |GET <br/> |
| `http://[sharepointsite]/_api/web/title` <br/> |Ruft den Titel des aktuellen Web ab. <br/> |GET <br/> |
| `http://[sharepointsite]/_api/lists` <br/> |Ruft alle Listen auf einer Website ab <br/> |GET <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')` <br/> |Ruft die Metadaten für eine angegebene Liste. <br/> |GET <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')/items` <br/> |Ruft die Listenelemente in einer angegebenen Liste ab. <br/> |GET <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')?select=Title` <br/> |Ruft den Titel einer bestimmten Liste ab. <br/> |GET <br/> |
   

## Erstellen von Abfragezeichenfolgen zum Filtern von Daten
<a name="bkmk_constructquery"> </a>

Um die zurückgegebene Datenmenge beschränken oder mehr Stellen für den Benutzer relevant die Filteroperationen gefunden in Tabelle 2 können Sie.
  
    
    

**In Tabelle 2. Operatoren zum Filtern von Daten**


|**Operator**||
|:-----|:-----|
|eq <br/> |Gleich <br/> > **HINWEIS**> Wenn Sie **EQ** zum Filtern verwenden, werden die Filterkriterien an das externe System übergeben, in dem Fall die Filterung auf dem Server.          |
|Gt <br/> |(größer als) <br/> > **HINWEIS**> Wenn Sie den Operator **GT** verwenden, wird nur clientseitige Filterung ausgeführt.> Beispiel:  `web/lists/getByTitle('ListName')/Items?$select=Title&amp;$filter=AverageRating gt 3` gibt alle Titel mit durchschnittlich Bewertung über 3 zurück.          |
   

> **HINWEIS**
> Zum Abrufen von Spalten, die Teil einer Zuordnung sind, müssen Sie explizit die Spalte in der URL **$select** in der Abfragezeichenfolge mit einbeziehen.
  
    
    


## Zusätzliche Ressourcen
<a name="bkmk_AdditionalResources"> </a>


-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Ausführen grundlegender Vorgänge unter Verwendung von SharePoint 2013-REST-Endpunkten](http://msdn.microsoft.com/library/e3000415-50a0-426e-b304-b7de18f2f7d9%28Office.15%29.aspx)
    
  
-  [Programmieren mit dem SharePoint 2013 REST-Dienst](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  
-  [SharePoint 2013: Durchführen grundlegender Datenzugriffsoperationen mit REST in Apps](http://code.msdn.microsoft.com/SharePoint-2013-Perform-335d925b)
    
  
-  [Auswählen des richtigen API-Satzes in SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [Ausführen grundlegender Vorgänge unter Verwendung von JavaScript-Bibliothekscode in SharePoint 2013](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
