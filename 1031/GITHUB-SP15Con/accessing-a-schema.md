---
title: Zugreifen auf ein Schema
ms.prod: OFFICE365
ms.assetid: 02613912-36f6-4edc-a915-165d12e60bc8
---


# Zugreifen auf ein Schema

In diesem Thema zeigt ein Beispiel zum zugreifen und Anzeigen eines Schemas für den REST-Dienst in Excel Services. In diesem Thema wird davon ausgegangen, dass Sie  [Beispiel-URI für die REST-API in Excel Services](sample-uri-for-excel-services-rest-api.md).d gelesen haben.
  
    
    

 **Hinweis**: der Excel Services REST API gilt für SharePoint 2013 und SharePoint 2016 lokale. Verwenden Sie die Excel REST-APIs, die Teil des Endpunkts [Microsoft Graph](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/excel
) sind online Szenarios.
## Anzeigen eines Schemas

 Geben Sie in der Adressleiste des Browsers den URI zu einem ATOM-XML-Feed mithilfe des folgenden URI ein:
  
    
    

```

http://myserver/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|H3')?$format=atom
```

Klicken Sie mit der rechten Maustaste auf die Webseite, und klicken Sie dann auf **Quelltext anzeigen**.
  
    
    
Es sollte ein Schema ähnlich dem folgenden Beispiel angezeigt werden:
  
    
    



```XML
<?xml version="1.0" encoding="utf-8"?>
<entry xml:base="http://excel.live.com/REST" xmlns:x="http://schemas.microsoft.com/office/2008/07/excelservices/rest" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservice" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">
  <title type="text">Sheet1!A1:H3</title>
  <id>http://myserver/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1%7CH3')</id>
  <updated>2009-06-25T00:41:37Z</updated>
  <author>
    <name />
  </author>
  <link rel="self" href="http://myserver/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1%7CH3')?$format=atom" title="Sheet1!A1:H3" />
  <category term="ExcelServices.Range" scheme="http://schemas.microsoft.com/ado/2007/08/dataservices/scheme" />
  <content type="application/xml">
    <x:range name="Sheet1!A1:H3">
      <x:row>
        <x:c>
          <x:fv>Name </x:fv>
        </x:c>
        <x:c>
          <x:fv>Name </x:fv>
        </x:c>
        <x:c>
          <x:fv>Exchange  </x:fv>
        </x:c>
        <x:c>
          <x:fv>Symbol  </x:fv>
        </x:c>
        <x:c>
          <x:fv>Last Trade </x:fv>
        </x:c>
        <x:c />
        <x:c>
          <x:fv>Change </x:fv>
        </x:c>
        <x:c>
          <x:fv>Mkt Cap</x:fv>
        </x:c>
      </x:row>
      <x:row>
        <x:c>
          <x:fv>Microsoft Corporation </x:fv>
        </x:c>
        <x:c>
          <x:fv>Microsoft Corporation </x:fv>
        </x:c>
        <x:c>
          <x:fv> </x:fv>
        </x:c>
        <x:c>
          <x:fv>MSFT </x:fv>
        </x:c>
        <x:c>
          <x:v>26.25</x:v>
          <x:fv>26.25</x:fv>
        </x:c>
        <x:c />
        <x:c>
          <x:fv>-0.23 (-0.87%) </x:fv>
        </x:c>
        <x:c>
          <x:v>239670000000</x:v>
          <x:fv> $239,670,000,000 </x:fv>
        </x:c>
      </x:row>
      <x:row>
        <x:c />
        <x:c />
        <x:c>
          <x:fv> </x:fv>
        </x:c>
        <x:c />
        <x:c>
          <x:v>15.58</x:v>
          <x:fv>15.58</x:fv>
        </x:c>
        <x:c />
        <x:c>
          <x:fv>-1.38 (-8.14%) </x:fv>
        </x:c>
        <x:c>
          <x:v>21590000000</x:v>
          <x:fv> $21,590,000,000 </x:fv>
        </x:c>
      </x:row>
    </x:range>
  </content>
</entry>

```


