---
title: Abrufen von Abfragevorschläge mithilfe des Suche REST-Diensts
ms.prod: SHAREPOINT
ms.assetid: a64c5bec-64a8-4752-9c72-433d1c864aed
---


# Abrufen von Abfragevorschläge mithilfe des Suche REST-Diensts
Hier erfahren Sie, wie Sie Abfragevorschläge aus Suche in SharePoint 2013 Abrufen des Search-REST-Diensts von Ihrer Client- und mobilen Anwendungen verwenden können.
Abfragevorschläge, auch bekannt als Suchvorschläge sind Ausdrücke, die Benutzer haben bereits gesucht und angezeigt oder "vorgeschlagen" können sie ihre Abfragen eingeben. Sie können Suche in SharePoint 2013 verwenden, um Vorschläge vor der Abfrage und nach der Abfrage zu aktivieren. Dieser Vorschläge in einer Liste unterhalb des Suchfelds angezeigt, wie ein Benutzer eine Abfrage eingibt. Weitere Informationen zu Abfragevorschläge und wie Sie diese aktivieren finden Sie unter  [Verwalten von abfragevorschlägen in SharePoint Server 2013](http://technet.microsoft.com/en-us/library/jj721441.aspx).
  
    
    


## Vorschlagen Sie Endpunkt im Search-REST-Dienst
<a name="bk_SuggestEndpoint"> </a>

Der Search-REST-Dienst enthält einen **Suggest** -Endpunkt, den Sie verwenden können, in jeder Technologie, die unterstützt der REST-Webanfragen Abfragevorschläge abgerufen, die das Suchsystem für eine Abfrage von Client oder mobilen Anwendungen generiert.
  
    
    
Der URI für **GET** Anforderungen an die Search-REST-Dienst **Suggest** Endpunkt ist:
  
    
    
 `/_api/search/suggest`
  
    
    
Die Abfrageparameter Vorschlag werden in der URL angegeben. Sie können die URL der Anforderung auf zwei Arten erstellen:
  
    
    


  
    
    
>  `http://server/_api/search/suggest?parameter=value&amp;parameter=value`
    
  

  
    
    
>  `http://server/_api/search/suggest(parameter=value&amp;parameter=value)`
    
  

> **HINWEIS**
> Der Search-REST-Dienst unterstützt keine anonyme Anfragen an den Endpunkt **Suggest**.
  
    
    


## Vorschlag Abfrageparameter
<a name="bk_SuggestParameters"> </a>

Den folgenden Abschnitten werden die Parameter, die Sie für den Endpunkt **Suggest** verwenden können.
  
    
    

### Abfragetext

Eine Zeichenfolge, die den Text für die Suchabfrage enthält
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint"
  
    
    

### iNumberOfQuerySuggestions

Die Anzahl der Abfragevorschläge abgerufen. Muss größer als 0 (null) sein. Der Standardwert ist 5.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Inumberofquerysuggestions = 3
  
    
    

### iNumberOfResultSuggestions

Die Anzahl der persönlichen Ergebnisse abgerufen. Muss größer als 0 (null) sein. Der Standardwert ist 5.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Inumberofresultsuggestions = 4
  
    
    

### fPreQuerySuggestions

Ein boolescher Wert, der angibt, ob Vorschläge vor der Abfrage oder nach der Abfrage abgerufen. **true** Vorschläge vor der Abfrage zurückzugebenden; andernfalls **false**. Der Standardwert ist **false**.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Fprequerysuggestions = True
  
    
    

### fHitHighlighting

Ein boolescher Wert, der angibt, ob Treffer hervorheben oder Abfragevorschläge fett formatiert. **true** fett formatiert die Ausdrücke in den zurückgegebenen Abfragevorschläge, die Ausdrücke in der angegebenen Abfrage übereinstimmen; andernfalls **false**. Der Standardwert ist **true**.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Fhithighlighting = False
  
    
    

### fCapitalizeFirstLetters

Ein boolescher Wert, der angibt, ob für die Großschreibung des ersten Buchstabens in jeden Ausdruck in der zurückgegebenen Abfragevorschläge. **true** für die Großschreibung des ersten Buchstabens in jeden Ausdruck; andernfalls **false**. Der Standardwert ist **false**.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Fcapitalizefirstletters = False
  
    
    

### Culture

Gebietsschema-ID (LCID) für die Abfrage (siehe  [Von Microsoft zugewiesene Gebietsschema-IDs](http://msdn.microsoft.com/de-de/goglobal/bb964664.aspx)).
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Culture = 1044
  
    
    

### EnableStemming

Ein boolescher Wert, der angibt, ob die wortstammerkennung aktiviert ist. **true** zum Aktivieren der wortstammerkennung; andernfalls **false**. Der Standardwert ist **true**.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Enablestemming = False
  
    
    

### ShowPeopleNameSuggestions

Ein boolescher Wert, der angibt, ob in der zurückgegebenen Abfragevorschläge Personennamen eingeschlossen. **true** Personennamen in der zurückgegebenen Abfragevorschläge enthalten; andernfalls **false**. Der Standardwert ist **true**.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Showpeoplenamesuggestions = False
  
    
    

### EnableQueryRules

Ein boolescher Wert, der angibt, ob Abfrageregeln für diese Abfrage zu aktivieren. **true** um Abfrageregeln zu aktivieren; andernfalls **false**. Der Standardwert ist **true**.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Enablequeryrules = False
  
    
    

### fPrefixMatchAllTerms

Ein boolescher Wert, der angibt, ob Abfragevorschläge zurückgegeben für Präfix übereinstimmt. **true** zurückzugebenden Abfragevorschläge basierend auf Präfix entspricht, andernfalls **false** beim Abfragevorschläge das vollständige Abfragewort übereinstimmen soll.
  
    
    
 **Beispiel für GET-Anforderung**
  
    
    
http:// _server_/_api/search/suggest?querytext = "Sharepoint" &amp; Fprefixmatchallterms = False
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Übersicht über die REST-API der SharePoint-Suche](sharepoint-search-rest-api-overview.md)
    
  
-  [Suche in SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013: Verwenden des Search-REST-Diensts über eine App für SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [What's new in SharePoint 2013-Suche für Entwickler](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [Programmieren mit dem SharePoint 2013 REST-Dienst](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

