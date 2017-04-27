---
title: Benutzerdefinierte JavaScript-Funktionen (Übersicht)
ms.prod: SHAREPOINT
ms.assetid: fee38837-1985-4319-ba4e-b99c6ec66336
---



# Benutzerdefinierte JavaScript-Funktionen (Übersicht)
Benutzerdefinierte JavaScript-Funktionen (UDFs) sind neu in Excel Services in SharePoint Server 2013. Dieser Artikel enthält eine ausführliche Übersicht über JavaScript UDFs, einschließlich grundlegende Informationen zur Funktionsweise in Excel Services.
 * **Gilt für:*** 
  
    
    


|||
|:-----|:-----|
|**In diesem Artikel**          [Was sind UDFs?](javascript-user-defined-functions-overview.md#xlsWhatAreUdfs)           [JavaScript-UDFs](javascript-user-defined-functions-overview.md#xlsJsUDFs)           [Wo kann ich JavaScript UDFs verwenden?](javascript-user-defined-functions-overview.md#xlsWhereUseJsUdfs)           [Zusätzliche Ressourcen](#bk_addresources) <br/> ||
   

## Was sind UDFs?
<a name="xlsWhatAreUdfs"> </a>

Eine benutzerdefinierte Funktion (UDF) ist eine Funktion, die Sie selbst erstellen können, und fügen Sie der Liste der verfügbaren Funktionen in Excel beim Excel dem Typ der Funktion zur Verfügung steht, sofort einsetzbar werden soll.
  
    
    
Excel Services already allows you to create UDFs using managed code, so if you have worked with the existing Excel Services UDFs, JavaScript UDFs should look familiar to you. For more information about creating UDFs using managed code, see  [Excel Services User-Defined Functions](excel-services-user-defined-functions.md).
  
    
    

## JavaScript-UDFs
<a name="xlsJsUDFs"> </a>

JavaScript-UDFs sind UDFs, die auf einer Webseite im Browser ausgeführt werden, die eine Arbeitsmappe eingebettete Excel hat. Verwenden Sie die JavaScript UDF in die eingebettete Arbeitsmappe. Solange Sie mit der Arbeitsmappe im Browser arbeiten, können Sie die JavaScript UDF genau, wie Sie die integrierte Excel-Funktionen verwenden. Wenn die Webseite geschlossen wird, ist die JavaScript UDF nicht mehr verfügbar.
  
    
    

## Funktionsweise von JavaScript-UDFs
<a name="xlsJsUDFs"> </a>

Um eine JavaScript UDF zu verwenden, müssen Sie haben die Möglichkeit zum Ändern des Inhalts der Webseite, in dem Sie die Arbeitsmappe einbetten. Nachdem Sie die richtigen Excel Services JavaScript-Quelldatei verweisen möchten, fügen Sie Ihrer JavaScript UDF-Code auf der Seite. Darüber hinaus vor der Verwendung von JavaScript UDF müssen Sie zuerst die UDF-Datei mit der Dienste für Excel-Berechnungen zu registrieren. JavaScript UDF-API stellt Methoden zum Registrieren und Aufheben der Registrierung Ihrer JavaScript UDF bereit.
  
    
    
Wenn die Webseite mit den Excel Web Access-Webpart oder eingebetteten Arbeitsmappe gerendert wird, können Sie die JavaScript UDF in der Arbeitsmappe genau wie jede andere Excel Arbeitsmappe aufrufen.
  
    
    
Sie möglicherweise beispielsweise eine Funktion, die den aktuellen Aktienkurs für eine bestimmte Aktie abruft. Sie können die Webseite eine UDF JavaScript hinzufügen, die Ihre Excel-Arbeitsmappe (vorausgesetzt, dass Sie über Schreibrechte für die Webseite verfügen) gehostet wird, die JavaScript Code wie folgt verwendet.
  
    
    



```

function StockInfo(symbol, measure) {
  var req = new XMLHttpRequest();
  req.open('GET', 'http://www.contoso-stock-quotes.com/quote/' + symbol + '/' + measure, false); 
  req.send(null);
  if (req.status == 200) {
    return req.responseText;
  } else {
    throw new Error(ExcelCalcError.Value);
  }
 
ewa.BrowserUdfs.add("StockQuote",
                       StockInfo,
                       "Gets a stock quote given a security symbol and measure to return."
                       false,
                       false
                       );

```

Sie können die JavaScript UDF, StockInfo, klicken Sie dann in einer Formel aus einer Zelle innerhalb der Excel Online aufrufen.
  
    
    

**Abbildung 1. JavaScript UDF, die in Excel Online aufgerufen werden.**

  
    
    

  
    
    
![In Excel Online aufgerufene benutzerdefinierte JavaScript-Funktionen](images/SPS15CON_xls_JsUdfinWebApp.jpg)
  
    
    

  
    
    

  
    
    

## Wo kann ich JavaScript UDFs verwenden?
<a name="xlsWhereUseJsUdfs"> </a>

Sie können erstellen und Verwenden von JavaScript-UDFs Arbeitsmappen in SharePoint Server 2013 Excel Web Access-Webparts angezeigt oder auf einer Hostwebseite, die eine eingebettete Arbeitsmappe hat. Die Arbeitsmappe muss auf Microsoft OneDrive gespeichert werden. Der Hauptunterschied ist, dass die JavaScript-UDFs Excel Web Access-Webparts hinzugefügt einen SharePoint-Server benötigen. JavaScript-UDFs hinzugefügt Host von Webseiten, die Arbeitsmappen eingebettet haben muss nur auf OneDrive die Arbeitsmappe gespeichert werden.
  
    
    

## Wichtige Punkte
<a name="xlsWhereUseJsUdfs"> </a>


- JavaScript-UDFs live nur, solange die Webseite, die, der Sie auf, angezeigt wird. Sie nicht über die Lebensdauer der Webseite hinaus erhalten bleiben, in dem sie erstellt wurden.
    
  
- Sie können keine Excel Services JavaScript-Objektmodell aus in einer JavaScript UDF aufrufen.
    
  

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Excel Services in SharePoint 2013](excel-services-in-sharepoint-2013.md)
    
  
-  [Was ist neu in Excel Services für Entwickler](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [Benutzerdefinierte Funktionen von Excel Services](http://msdn.microsoft.com/en-us/library/ms493934)
    
  
