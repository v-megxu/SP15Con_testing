---
title: Interaktive Excel-Ansicht entfernen aus einer Webseite
ms.prod: SHAREPOINT
ms.assetid: 407b3aa3-7286-462b-905f-811a3b7f3f1c
---


# Interaktive Excel-Ansicht entfernen aus einer Webseite

Das Feature für interaktive Excel-Ansicht wurde deaktiviert. Wenn Sie eine interaktive Excel-Ansicht in der Webseite eingefügt haben, können Sie ihn durch Entfernen der  `<script>` Tag und die Platzhalter `<a>` Tags für die Schaltfläche aus der HTML-Code der Webseite entfernen.
  
    
    

Entfernen Sie das  `<script>` -Tag, suchen und löschen den folgenden HTML-Code.


```HTML

<script src="http://r.office.microsoft.com/r/rlidExcelButton?v=1&amp;amp;kip=1" type="text/javascript"></script>
```

Wenn die Platzhalter  `<a>` Tags entfernen möchten, finden Sie < a >-Tags, die direkt vor dem < > Tabellenelemente in Ihre HTML-Seite befinden. Da < a >-Tags angepasst werden, analysieren Sie den HTML-Code für den ersten Teil der Zeichenfolge, um alle Instanzen der Schaltfläche Suchen.


```HTML
<a href="#" name="MicrosoftExcelButton" data-xl-tableTitle="" data-xl-buttonStyle="Standard" data-xl-fileName="Book1" data-xl-attribution="" ></a>
```


## Problemumgehungen

Wir empfehlen Ihnen zu  [Excel in Webseiten einbetten ](https://support.office.com/en-au/article/Share-it-Embed-an-Excel-workbook-on-your-blog-804e1845-5662-487e-9b38-f96307144081?ui=en-US&amp;rs=en-AU&amp;ad=AU) als Alternative.
  
    
    

## Zusätzliche Ressource
<a name="bk_addresources"> </a>


-  [Excel Services in SharePoint 2013](excel-services-in-sharepoint-2013.md)
    
  
-  [Einbetten einer Excel-Arbeitsmappe in Ihrem blog](https://support.office.com/en-au/article/Share-it-Embed-an-Excel-workbook-on-your-blog-804e1845-5662-487e-9b38-f96307144081?ui=en-US&amp;rs=en-AU&amp;ad=AU)
    
  

