---
title: Zugreifen auf Bereiche mithilfe von ATOM-Feeds und HTML-Fragmenten
ms.prod: OFFICE365
ms.assetid: 45d4ef08-02d6-48dd-b0ef-a748db1a0c6a
---


# Zugreifen auf Bereiche mithilfe von ATOM-Feeds und HTML-Fragmenten

In diesem Thema werden die beiden Mechanismen ATOM-Feeds und HTML-Fragmente für den Zugriff auf Bereiche mithilfe der REST-API in Excel Services beschrieben.
  
    
    

 **Hinweis**: der Excel Services REST API gilt für SharePoint 2013 und SharePoint 2016 lokale. Verwenden Sie die Excel REST-APIs, die Teil des Endpunkts [Microsoft Graph](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/excel
) sind online Szenarios.
## Zugreifen auf Bereiche

Die REST-API in Excel Services unterstützt zwei Mechanismen für den Zugriff auf Bereiche. Mit dem ersten Mechanismus können Anwendungen in erster Linie auf die Rohdaten einer Arbeitsmappe zugreifen, d. h., die Rohzahlen oder -werte in einem Arbeitsblatt. Mit dem zweiten Mechanismus kann in einem Browser auf HTML-Fragmente zugegriffen werden.
  
    
    
Wie im Thema  [Ermittlung in der Excel Services-REST-API](discovery-in-excel-services-rest-api.md) beschrieben lautet die REST-URL zur Modellseite bei Verwendung der Ermittlung wie folgt:
  
    
    



```

http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>/model
```

Für eine Arbeitsmappe mit dem Dateinamen **sampleWorkbook.xlsx**, die im Ordner  `http://` _<ServerName>_ `/Docs/Documents/sampleWorkbook.xlsx` gespeichert ist, lautet der URI zur Modellseite wie folgt:
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model
```

Wenn Sie bei dem in  [Ermittlung in der Excel Services-REST-API](discovery-in-excel-services-rest-api.md) beschriebenen Ermittlungsmechanismus in der Modellseite auf dem Server auf den ATOM-Feed **Ranges** klicken ( `http://` _<ServerName>_ `/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model`), wird eine Seite mit allen benannten Bereichen in der Arbeitsmappe angezeigt. **sampleWorkbook.xlsx** enthält wie im folgenden Bildschirmfoto dargestellt den benannten Bereich **SampleNamedRange**:
  
    
    

> **WICHTIG**
> Sie können nicht nur die von der Ermittlung zurückgegebenen Bereiche, sondern auch beliebige Bereiche angeben. Ein Doppelpunkt (":") muss durch "|" ersetzt werden. Verwenden Sie z. B. "A1|G5" anstelle von "A1:G5".
  
    
    


> **HINWEIS**
> Zeichen wie "?" und "#" werden nicht unterstützt. Um ordnungsgemäß auf Blattnamen zu verweisen, die Sonderzeichen enthalten, gilt die Grundregel "Feststellen, was der Excel-Client macht", wenn Sie in einer Formel auf ein Blatt mit Sonderzeichen verweisen, und diesem Beispiel folgen.
  
    
    


**Ermittlung benannter Excel Services REST-Bereiche**

  
    
    

  
    
    
![Ermittlung benannter Excel Services REST-Bereiche](images/159f676e-421e-4190-94a6-cf311f7db2ca.gif)
  
    
    

### Zugreifen auf Bereiche mithilfe eines ATOM-Feeds

Wenn Sie auf der Bereichsermittlungsseite auf **SampleNamedRange** klicken, navigieren Sie zur folgenden URL:
  
    
    

```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('SampleNamedRange')?$format=atom
```

Beachten Sie, dass wie im folgenden Bildschirmfoto dargestellt die resultierende Seite in Internet Explorer fehlerhaft aussieht.
  
    
    

**Ermittlung von Excel Services REST-Bereichen mithilfe von ATOM**

  
    
    

  
    
    
![Ermittlung von Excel Services REST-Bereichen mithilfe von ATOM](images/2d011e17-953f-42b1-97d3-2525372296c1.gif)
  
    
    
In Internet Explorer kann ein ATOM-Feedelement mit einem einzelnen Eintrag nicht angezeigt werden. Beim Anzeigen des Quellcodes der Seite ist jedoch das XML des Feedelements sichtbar:
  
    
    



```XML
<?xml version="1.0" encoding="utf-8"?>
<entry xmlns:x="http://schemas.microsoft.com/office/2008/07/excelservices/rest" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservice" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">
  <title type="text">SampleNamedRange</title>
  <id>http://ServerName/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('SampleNamedRange')</id>
  <updated>2010-01-20T21:28:10Z</updated>
  <author>
    <name />
  </author>
  <link rel="self" href="http://ServerName/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('SampleNamedRange')?$format=atom" title="SampleNamedRange" />
  <category term="ExcelServices.Range" scheme="http://schemas.microsoft.com/ado/2007/08/dataservices/scheme" />
  <content type="application/xml">
    <x:range name="SampleNamedRange">
      <x:row>
        <x:c>
          <x:fv>Performance</x:fv>
        </x:c>
        <x:c>
          <x:v>26</x:v>
          <x:fv>26</x:fv>
        </x:c>
        <x:c />
      </x:row>
      <x:row>
        <x:c>
          <x:fv>Employment</x:fv>
        </x:c>
        <x:c>
          <x:v>42</x:v>
          <x:fv>42</x:fv>
        </x:c>
        <x:c />
      </x:row>
      <x:row>
        <x:c>
          <x:fv>Earnings And Job Quality</x:fv>
        </x:c>
        <x:c>
          <x:v>22</x:v>
          <x:fv>22</x:fv>
        </x:c>
        <x:c />
      </x:row>
    ... XML truncated for brevity. 
      <x:row>
        <x:c>
          <x:fv>Innovation Assets</x:fv>
        </x:c>
        <x:c>
          <x:v>43</x:v>
          <x:fv>43</x:fv>
        </x:c>
        <x:c />
      </x:row>
      <x:row>
        <x:c />
        <x:c>
          <x:fv>State</x:fv>
        </x:c>
        <x:c />
      </x:row>
    </x:range>
  </content>
</entry>
```

Das Feedelement enthält XML für die Daten innerhalb des Bereichs. Die folgenden XML-Elemente sind interessant: 
  
    
    

- **<range>** Das Bereichselement. Stellt den Container des zurückgegebenen Bereichs dar.
    
  
- **<row>** Das Zeilenelement. Stellt die einzelnen Zeilen im Bereich dar.
    
  
- **<c>** Das Zellenelement. Stellt die einzelnen Zellen in einer Zeile dar.
    
  
- **<fv>** Das Element für den formatierten Wert. Stellt den von Excel formatierten Wert dar. Wenn dieser Wert in der Arbeitsmappe vom Typ **String** ist, ist das Element für den formatierten Wert das einzige Element in **<c>**.
    
  
- **<v>** Das Wertelement. Stellt einen Zahlenwert dar. Wenn der Wert in der Zelle keine Zeichenfolge, sondern eine Zahl ist, enthält das Wertelement diese Information.
    
  
Die Verwendung von XML stellt eine einfachere Möglichkeit für den Zugriff auf Daten in einem Excel-Bereich dar. Sie können diese Methode deshalb in Ihrer Anwendung verwenden.
  
    
    

### Zugreifen auf Bereiche mithilfe von HTML

Der letzte Teil der URL für den Zugriff auf einen benannten Bereich mithilfe eines ATOM-Feeds enthält den Parameter  `$format`, der auf  `atom` festgelegt ist. Dieser Parameter kann auch den Wert `html` aufweisen. Wenn Sie den `atom` in `html` ändern, gibt die URL ein HTML-Fragment anstelle eines ATOM-Feeds zurück. Es folgt ein Beispiel für die URL:
  
    
    

```

http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('SampleNamedRange')?$format=html
```

In Internet Explorer sieht die Seite ähnlich wie in der folgenden Abbildung aus.
  
    
    

> **HINWEIS**
> Dieser HTML-Code kann in einem **IFRAME**-Element direkt verwendet werden. Sie können ihn aber auch in JavaScript verwenden, um ein nahtloses Arbeiten zu ermöglichen.
  
    
    


  
    
    
![Ermittlung von Excel Services REST - Abrufen von Bereichen mithilfe von HTML](images/558e6305-5a42-4b5c-9a70-1116ddcf6637.gif)
  
    
    

  
    
    

  
    
    

## Siehe auch


#### Konzepte


  
    
    
 [Ressourcen-URI für die REST API in Excel Services](resources-uri-for-excel-services-rest-api.md)
