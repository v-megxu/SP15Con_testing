---
title: Excel-Arbeitsmappendaten aus SharePoint Server mithilfe von OData anfordern
ms.prod: SHAREPOINT
ms.assetid: 2f846e96-6c9e-4ed2-9602-4081ad0ab135
---



# Excel-Arbeitsmappendaten aus SharePoint Server mithilfe von OData anfordern

> **HINWEIS**
> Excel Services REST-API gilt für SharePoint 2013 und SharePoint 2016 lokale. Für Office 365 Education, Geschäfts- und Enterprise-Konten verwenden der Excel-REST-APIs, die Teil der sind die  [Microsoft Graph](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/excel
) Endpunkt.
  
    
    

OData verwendet URLs zum Anfordern von Informationen aus einer Ressource. Sie erstellen die URL auf eine bestimmte Weise Abfrageoptionen, die Informationen zurückgegeben, die Sie benötigen, verwenden. Die folgende URL zeigt, wie eine normale OData-Anforderung aussieht.
http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$top=20
  
    
    

In diesem Beispiel für OData-Anforderung ist so strukturiert, dass es Ruft die ersten 20 Zeilen aus einer Tabelle mit dem Namen Tabelle1 in der Arbeitsmappe ProductSales.xlsx der im Ordner "Dokumente" auf dem Server contoso1 gespeichert wird. Die URL verwendet das System Abfrage Option **$top**, um die Anzahl der zurückzugebenden Zeilen angeben.Betrachtung der URL, können Sie die drei Komponentenstruktur anzeigen: der Dienst Stamm-URI; der Pfad der Ressource; und die Abfrageoptionen.
## Stamm-URI-Service

Der erste Teil der URL das Stammverzeichnis Service aufgerufen und bleibt gleich für jede OData-Anforderung, die Sie an eine SharePoint 2013-Server mit Ausnahme der Name des Servers vornehmen. Sie enthält den Namen des SharePoint-Servers, auf dem die Arbeitsmappe gespeichert wird, und der Pfad, /_vti_bin/excelrest.aspx voranstellen, wie im folgenden Beispiel dargestellt.
  
    
    
http://contoso1/_vti_bin/ExcelRest.aspx
  
    
    

## Ressourcenpfad

Im zweite Teil der URL muss der Pfad zu der Excel-Arbeitsmappe und gibt an, dass dies ein OData-Anforderung ist.
  
    
    
/Documents/ProductSales.xlsx/OData
  
    
    

## System-Abfrageoptionen

Der dritte Teil der URL wird Abfrageoptionen für die Anforderung. Abfrageoptionen immer beginnen mit einem Dollarzeichen ($) und am Ende des URIS als Abfrageparameter angefügt sind. Anforderung ist in diesem Beispiel wird für die ersten 20 Zeilen in der Tabelle mit dem Namen Tabelle1.
  
    
    
/ Table1? $top = 20
  
    
    
System-Abfrageoptionen bieten eine Möglichkeit zum Abrufen von bestimmter Daten aus einer Ressource. Die Excel Services OData-Implementierung unterstützt eine Reihe von Abfrageoptionen für wie im folgenden Abschnitt aufgeführt.
  
    
    

## System-Abfrageoptionen
<a name="xlsSystemQueryOptions"> </a>

Die Excel Services-Implementierung der OData unterstützt eine Reihe von OData-System-Abfrage Standardoptionen. Diese Abfrageoptionen sind im Wesentlichen Anforderungen OData da Sie die Optionen zum angeben, welche Daten aus einer Ressource abgerufen werden soll. Die folgende Tabelle enthält die Abfrageoptionen System, die derzeit Excel Services-Implementierung von OData unterstützt.
  
    
    

**In Tabelle 1. Excel Services OData-System-Abfrageoptionen**


|****System-Abfrageoption****|****Beschreibung****|
|:-----|:-----|
|/<tableName> <br/> |Gibt alle Zeilen der Tabelle angegeben durch < TableName >, wobei < TableName > ist der Name einer Tabelle in einer Excel-Arbeitsmappe, die die Zeilen enthält, die Sie abrufen möchten. <br/> > **WICHTIG**> Dieses Formular von OData-Anforderung gibt nicht mehr als 500 Zeilen zu einem Zeitpunkt zurück. Jede Gruppe von 500 Zeilen ist eine Seite. Um die Zeilen in weitere Seiten in einer Tabelle abzurufen, die mehr als 500 Zeilen aufweist, verwenden Sie die Abfrageoption **$skiptoken** (siehe unten).          Im folgende Beispiel werden alle Zeilen bis zu den 500th Zeile in Tabelle1 in der ProductSales.xlsx Arbeitsmappe zurückgegeben. <br/> |
|**$metadata** <br/> |Alle verfügbaren Tabellen und den Typ von Informationen für alle Zeilen zurückgegeben in den einzelnen Tabellen in der angegebenen Arbeitsmappe. <br/> Das folgende Beispiel gibt die Tabellen und Typinformationen für die Tabellen in der Arbeitsmappe ProductSales.xlsx zurück. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/$metadata <br/> |
|**$orderby** <br/> |Gibt die Zeilen in der angegebenen Tabelle, sortiert nach von **$orderby**angegebenen Wert zurück. <br/> Das folgende Beispiel gibt alle Zeilen aus Tabelle 1, sortiert nach der Spalte Name in der Arbeitsmappe ProductSales.xlsx zurück. <br/> > **HINWEIS**> Der Standardwert für **$orderby** ist Aufsteigend.          http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$orderby=Name <br/> |
|**$top** <br/> |Gibt zurück N Zeilen aus der Tabelle, wobei N eine Zahl, die den Wert des **$top**angegeben. <br/> Das folgende Beispiel gibt die ersten 5 Zeilen from Tabelle1, sortiert nach der Spalte Name in der Arbeitsmappe ProductSales.xlsx. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$orderby=Name&amp;$top=5 <br/> |
|**$skip** <br/> |Überspringt N Zeilen, wobei N den Wert des **$skip**angegebene Nummer getestet werden, und gibt dann die restlichen Zeilen der Tabelle zurück. <br/> Das folgende Beispiel gibt alle verbleibende Zeilen nach der fünften Zeile from Tabelle1 in der Arbeitsmappe ProductSales.xlsx zurück. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skip=5 <br/> |
|**$skiptoken** <br/> |Der n-te Zeile, wobei N die Ordnungsposition Zeile durch den Wert des **$skiptoken**angegeben ist, sucht und gibt dann alle verbleibende Zeilen, beginnend bei Zeile N + 1 zurück. Die Auflistung ist nullbasiert, damit die zweite Zeile, beispielsweise durch $skiptoken angegebenen = 1. <br/> Das folgende Beispiel gibt alle verbleibende Zeilen nach der zweiten Zeile from Tabelle1 in der Arbeitsmappe ProductSales.xlsx zurück. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skiptoken=1 <br/> Sie können auch die Abfrageoption **$skiptoken** verwenden, Zeilen in Seiten nach der ersten Seite aus einer Tabelle abrufen, die mehr als 500 Zeilen enthält. Im folgenden Beispiel wird veranschaulicht, die 500th Zeile abgerufen und aus einer Tabelle mit mehr als 500 Zeilen höher. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skiptoken=499 <br/> |
|**$filter** <br/> |Gibt die Teilmenge der Zeilen, die den Wert der **$filter**angegebenen Bedingungen erfüllen. Weitere Informationen zu den Operatoren und einen Satz von Funktionen, die Sie mit **$filter**verwenden können, finden Sie unter das OData-  [Dokumentation](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/). <br/> Das folgende Beispiel gibt nur die Zeilen, wobei der Wert der Spalte Price größer als 100 ist. <br/> http://Contoso1/_vti_bin/ExcelRest.aspx/Documents/productsales.xlsx/OData/Table1?$ Filter = Preis Gt 100 <br/> |
|**$format** <br/> |Das Atom-XML-Format ist der einzige unterstützte Wert und ist die Standardeinstellung für die Abfrageoption **$format**. <br/> |
|**$select** <br/> |Gibt die Entität, die durch **$select**angegebenen zurück. <br/> Im folgende Beispiel werden die Spalte Name in der Arbeitsmappe ProductSales.xlsx from Tabelle1 markiert. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$select=Name <br/> |
|**$inlinecount** <br/> |Gibt die Anzahl der Zeilen in der angegebenen Tabelle zurück. <br/> $ **inlinecount** können nur 1 von 2 der folgenden Werte verwenden. <br/> **allpages** - zurückgegeben Anzahl die für alle Zeilen in der Tabelle. <br/> **none** - umfasst keine Anzahl der Zeilen in der Tabelle. <br/> Im folgende Beispiel werden die Anzahl für die Gesamtanzahl der Zeilen in Tabelle1 in der ProductSales.xlsx Arbeitsmappe zurückgegeben. <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$inlinecount=allpages <br/> |
   

## Zusätzliche Ressourcen
<a name="xlsAdditionalResources"> </a>


-  [Verwenden von OData mit Excel Services-REST in SharePoint 2013](using-odata-with-excel-services-rest-in-sharepoint-2013.md)
    
  
-  [Was ist neu in Excel Services für Entwickler](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [Dokumentation für OData-Spezifikation](http://www.odata.org)
    
  
