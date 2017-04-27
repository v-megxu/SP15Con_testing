---
title: Verwenden von OData mit Excel Services-REST in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8a20225a-323c-4420-bbb4-eef60aed4b42
---


# Verwenden von OData mit Excel Services-REST in SharePoint 2013
In SharePoint Server 2010 wurde die REST-API zum Abrufen und Festlegen von Informationen in Excel-Arbeitsmappen, die in SharePoint-Dokumentbibliotheken gespeichert sind, eingeführt. SharePoint Server 2013 verfügt nun über eine neue Möglichkeit, um Daten von Excel Services abzufragen, die das Open Data Protocol (OData) verwendet. Mit diesem Protokoll können Sie Informationen über Excel Services-Ressourcen abrufen. Dieser neue Diensts hängt stark von der vorhandenen Excel Services-REST-API ab.Dieses Thema bietet eine allgemeine Übersicht über für die Verwendung von OData in Excel Services.
> **HINWEIS**
> Die Excel Services-REST-API bezieht sich auf SharePoint 2013 und SharePoint 2016 (lokal). Für Office 365 Education-, Business- und Enterprise-Konten verwenden Sie die Excel-REST-APIs, die Bestandteil des  [Microsoft Graph](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/excel
)-Endpunkts sind. 
  
    
    


## Was ist OData?
<a name="xlsWhatIsOdata"> </a>

OData ist ein offenes Internet-Protokoll zum Abfragen und Aktualisieren von Daten. Es verwendet einen RESTful-Ansatz für die Rückgabe von Daten aus Ressourcen im Internet. Das heißt, Sie verwenden einen URI mit eingeschlossenen Abfrageparametern, um Informationen zu einer bestimmten Ressource zu erhalten.
  
    
    
Weitere Informationen zu OData finden Sie auf der Website für die  [Open Data Protocol-Spezifikation](http://www.odata.org).
  
    
    

## Wie verwenden Sie OData mit Excel Services?
<a name="xlsHowUseOdata"> </a>

Bei Excel Services verwenden Sie OData zum Abrufen von Informationen über Tabellen (einschließlich Abfragetabellen) in einer Arbeitsmappe, die in einer SharePoint-Bibliothek gespeichert ist. Der OData-Dienst gibt die angeforderten Daten im XML-Atom-Format zurück.
  
    
    

### Syntax für OData-Anforderungen an Excel Services
<a name="xlsOdataSyntax"> </a>

SharePoint macht jede Arbeitsmappe als separate Ressource verfügbar, aus der Sie Informationen abrufen können. In dieser Version von SharePoint Server können Sie nur Daten aus Tabellen in der Arbeitsmappe abrufen.
  
    
    
Zum Abrufen von Daten aus einer Excel-Arbeitsmappe müssen Sie eine URL erstellen, die auf die Arbeitsmappe verweist und die angibt, welche Daten Sie aus der Arbeitsmappe abrufen möchten und wie die Daten angeordnet werden sollen. Wenn Sie zum Beispiel Informationen zu Tabelle1 in einer Arbeitsmappe mit dem Namen "ProductSales.xlsx" abrufen möchten, die in einer SharePoint-Bibliothek in einem Ordner mit dem Namen "Documents" gespeichert ist, verwenden Sie die folgende URL.
  
    
    
http://<serverName>/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1
  
    
    
Weitere Informationen zur Verwendung von OData zum Abrufen von Informationen aus einer ExcelArbeitsmappe, die in SharePoint Server gespeichert ist, finden Sie unter  [Excel-Arbeitsmappendaten aus SharePoint Server mithilfe von OData anfordern](requesting-excel-workbook-data-from-sharepoint-server-using-odata.md).
  
    
    

## Von OData zurückgegebenen Daten
<a name="xlsOdataReturnData"> </a>

Wenn Sie eine OData-Anforderung an Excel Services stellen, werden die XML-Ergebnisse im Atom-Format zurückgegeben. Das Atom-Format ist das einzige unterstützte Format in der Excel Services-Implementierung von OData. Nachfolgend ist zum Beispiel eine OData-Anforderung für die erste Zeile in der ersten Tabelle (mit dem Namen "Tabelle1") in einer Arbeitsmappe mit dem Namen "WindowsPhoneComparison.xlsx" aufgeführt.
  
    
    
http://<serverName>/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/odata/Table1
  
    
    
Excel Services gibt dann die im folgenden Code dargestellte Atom-XML zurück.
  
    
    



```XML

<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<entry xml:base="http://{serverName}/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/OData" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" m:etag="W/&amp;quot;datetime'0001-01-01T00%3A00%3A00'&amp;quot;" xmlns="http://www.w3.org/2005/Atom">
  <id>http://{serverName}/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/OData/Table1(0)</id>
  <title type="text"></title>
  <updated>0001-01-01T00:00:00-08:00</updated>
  <author>
    <name />
  </author>
  <link rel="edit" title="Table1Item" href="/Table1(0)" />
  <category term="ExcelServices.Table1Item" scheme="http://schemas.microsoft.com/ado/2007/08/dataservices/scheme" />
  <content type="application/xml">
    <m:properties>
      <d:Phone>Samsung Focus</d:Phone>
      <d:sizeweight m:type="Edm.Double">4</d:sizeweight>
      <d:camera m:type="Edm.Double">2.5</d:camera>
      <d:battery m:type="Edm.Double">3</d:battery>
      <d:memory m:type="Edm.Double">3</d:memory>
      <d:speed m:type="Edm.Double">3</d:speed>
      <d:style m:type="Edm.Double">3</d:style>
      <d:callquality m:type="Edm.Double">3</d:callquality>
      <d:overall m:type="Edm.Double">3</d:overall>
      <d:excelRowID m:type="Edm.Int32">0</d:excelRowID>
    </m:properties>
  </content>
</entry>

```


## Schlussbemerkung
<a name="xlsOdataReturnData"> </a>

OData bietet eine einfache Möglichkeit zum Abrufen von Daten aus Excel-Arbeitsmappen, die in SharePoint gespeichert sind. Durch eine einfache Syntax, die auf Webstandards wie HTTP und REST basiert, können Sie mit OData schnell und einfach Daten aus Excel-Arbeitsmappen abrufen.
  
    
    

## Zusätzliche Ressourcen
<a name="xlsOdataAddRes"> </a>


-  [Was ist neu in Excel Services für Entwickler](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [Excel-Arbeitsmappendaten aus SharePoint Server mithilfe von OData anfordern](requesting-excel-workbook-data-from-sharepoint-server-using-odata.md)
    
  
-  [OData-Spezifikationsdokumentation](http://www.odata.org)
    
  

