---
title: Grundlegende URI-Struktur und Pfad
ms.prod: SHAREPOINT
ms.assetid: d73cf6c2-0677-4726-8a3e-2ad130e1a12c
---


# Grundlegende URI-Struktur und Pfad

In diesem Thema wird erläutert, wie Sie die URI-Struktur und den Pfad für RESET-Dienstbefehle in Excel Services konstruieren.
  
    
    

 **Hinweis**: der Excel Services REST API gilt für SharePoint 2013 und SharePoint 2016 lokale. Verwenden Sie die Excel REST-APIs, die Teil des Endpunkts [Microsoft Graph](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/excel
) sind online Szenarios.

  
    
    


## Grundlegende URI-Struktur und Pfad

Die REST-API in Excel Services ermöglicht den Zugriff auf Ressourcen wie Diagramme, PivotTables, Tabellen und benannte Bereiche in einer Arbeitsmappe direkt über eine URL. Jede REST-URL in Excel Services besteht aus drei Teilen. Im Anschluss finden Sie die grundlegende Struktur der URL für den Zugriff auf die Ressourcen in der Arbeitsmappe:
  
    
    

1. **REST-URI zur "ASPX"-Seite** Der Einstiegspunkt zu einer **ASPX**-Seite
    
  
2. **Speicherort der Arbeitsmappe** Der Pfad zu der Arbeitsmappe
    
  
3. **Speicherort der Ressource** Der Pfad zu der angeforderten Ressource in der Arbeitsmappe
    
  
Im Anschluss finden Sie das Konstrukt für die REST-URL zu einem bestimmten Element in einer Arbeitsmappe:
  
    
    



```

http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>/<ResourceLocation>
```

Im Anschluss finden Sie ein Beispiel dafür, wie eine REST-URL in Excel Services aussieht, wenn alle drei Teile zusammengefügt sind. In diesem Beispiel greift die REST-URL auf eine Arbeitsmappe mit dem Namen **sampleWorkbook.xlsx** zu, die ein Diagramm mit dem Namen **SampleChart** enthält:
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('SampleChart')
```

Die Arbeitsmappe ist in einer Dokumentbibliothek gespeichert. Der vollständige Pfad zu der Arbeitsmappe lautet  `http://`_\<ServerName\>_`/Docs/Documents/sampleWorkbook.xlsx`.
  
    
    
Die drei Teile der REST-URL sind:
  
    
    

1. **REST-URI zur "ASPX"-Seite**: `http://`_\<ServerName\>_`/_vti_bin/ExcelRest.aspx`
    
  
2. **Speicherort der Arbeitsmappe**: `/Docs/Documents/sampleWorkbook.xlsx`
    
  
3. **Speicherort der Ressource**: `/model/Ranges('nameOfTheNamedRange')`
    
  

### Zugriff unter Verwendung der Discovery-Benutzeroberfläche

Sie können auf das Diagramm auch unter Verwendung der Discovery-Benutzeroberfläche zugreifen. Informationen dazu, wie Sie auf Ressourcen wie Diagramme, Tabellen, PivotTables und Bereiche unter Verwendung des im folgenden Screenshot dargestellten Ermittlungsmechanismus zugreifen, finden Sie unter  [Ermittlung in der Excel Services-REST-API](discovery-in-excel-services-rest-api.md).
  
    
    

  
    
    
![Excel Services REST-Modell-URL](images/SharePointServer14Con_XLSvcs_RESTModel.gif)
  
    
    

  
    
    

  
    
    

  
    
    

### Markierungspfad

Im Anschluss finden Sie die **ASPX**-Seite für den REST-Dienst in Excel Services:
  
    
    

```
http://<ServerName>/_vti_bin/ExcelRest.aspx
```

Um auf den REST-Dienst in Excel Services zugreifen zu können, müssen Sie der URL  `http://`_\<ServerName\>_`/_vti_bin/ExcelRest.aspx` voranstellen.
  
    
    

### Speicherort der Arbeitsmappe

Der Speicherort der Arbeitsmappe ist der relative Pfad zu der Arbeitsmappe, die die Ressourcen enthält, auf die Sie zugreifen möchten. Angenommen, Sie haben eine Arbeitsmappe mit dem Namen **sampleWorkbook.xlsx**, die in einer vertrauenswürdigen SharePoint-Dokumentbibliothek gespeichert ist. Für dieses Beispiel folgt im Anschluss der Pfad zu dem Speicherort von **sampleWorkbook.xlsx**:
  
    
    

```
http://<ServerName>/Docs/Documents/sampleWorkbook.xlsx
```

Sie nehmen den relativen Pfad zu der Arbeitsmappe ( `Docs/Documents/sampleWorkbook.xlsx`) und hängen diesen an den Markierungspfad an. Im Anschluss finden Sie die URL mit angehängtem Markierungspfad und angehängtem Speicherort der Arbeitsmappe:
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx
```


### Speicherort der Ressource

Der Speicherort der Ressource ist der Pfad innerhalb der Arbeitsmappe zu dem gewünschten Element. Wenn Sie beispielsweise auf ein Diagramm zugreifen möchten, würde der Speicherort der Ressource in etwa folgendermaßen aussehen:  `/model/Charts('Chart 1')`.
  
    
    
Um die vollständige URL zu erhalten, hängen Sie dieses an den Markierungspfad und den relativen Pfad zu der Arbeitsmappe an. Die vollständige Beispiel-URL sieht dann folgendermaßen aus: :
  
    
    



```

http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('Chart 1')

```


## Siehe auch


#### Konzepte


  
    
    
 [Ressourcen-URI für die REST API in Excel Services](resources-uri-for-excel-services-rest-api.md)
  
    
    
 [Ermittlung in der Excel Services-REST-API](discovery-in-excel-services-rest-api.md)
