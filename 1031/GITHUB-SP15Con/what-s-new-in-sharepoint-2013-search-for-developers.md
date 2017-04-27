---
title: What's new in SharePoint 2013-Suche für Entwickler
ms.prod: SHAREPOINT
ms.assetid: b8d69685-3612-421e-b011-50b4d580d461
---


# What's new in SharePoint 2013-Suche für Entwickler
Informationen Sie zu den neuen Features für Entwickler bei der Suche in SharePoint 2013.
## Search-Clientobjektmodell für den Zugriff auf die Funktionalität des Objektmodells für online Abfragen, lokalen und Mobilgeräte-Entwicklung
<a name="SPSearchnew_clientOM"> </a>

SharePoint 2013 Suche enthält ein Clientobjektmodell (CSOM), die Zugriff auf die Funktionalität des Abfrage-Objektmodells für die meisten online ermöglicht, lokalen und Mobilgeräte-Entwicklung. Dem Search-Clientobjektmodell können zum Erstellen von Clientanwendungen, die auf einem Computer ausgeführt werden, die keinen SharePoint 2013 installiert haben, um Suchergebnisse SharePoint 2013 zurückzugeben.
  
    
    
Die Suche CSOM besteht aus einem verwalteten Clientobjektmodell Microsoft .NET Framework und JavaScript-Objektmodell, und es basiert auf SharePoint 2013. Erstens greift Clientcode des SharePoint-CSOM auf. Klicken Sie dann auf Clientcode die Suche CSOM zugegriffen.
  
    
    
Verwenden die Suche .NET Framework verwaltetes CSOM, Sie müssen eine  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) -Instanz (befindet sich im Namespace [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) in der Microsoft.SharePoint.Client.dll) abrufen. Klicken Sie dann mithilfe des-Objektmodells im [Microsoft.SharePoint.Client.Search.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.aspx) -Namespace in der Microsoft.Office.Server.Search.Client.dll. Weitere Informationen zu SharePoint-CSOM finden Sie unter [Verwaltetes Clientobjektmodell](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Weitere Informationen zum **ClientContext** -Objekt, das den Einstiegspunkt für das CSOM ist, finden Sie unter [Clientkontext als zentrales Objekt](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx).
  
    
    
Die Search-CSOM zurückgegeben Search Results Daten vom Server in JavaScript Object Notation (JSON). Für die Suche Ergebnisdaten die JSON enthält eine  [ResultTableCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.ResultTableCollection.aspx) -Auflistung zusammengesetzten von [ResultTable](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.ResultTable.aspx) -Objekten, die unterschiedliche Resultsets darstellen.
  
    
    

## Unterstützung für SQL-Syntax entfernt
<a name="SP15Searchnew_support"> </a>

 [SQL-Syntax](http://msdn.microsoft.com/en-us/library/ee558869)unterstützt benutzerdefinierte suchlösungen in SharePoint Server 2013 nicht. Suche in SharePoint 2013 unterstützt die FQL-Syntax und KQL-Syntax für benutzerdefinierte suchlösungen. SQL-Syntax der kann nicht benutzerdefinierte suchlösungen mit jeder Technologien, einschließlich des Serverobjektmodells Abfrage, das Clientobjektmodell und der Search REST-Dienst verwendet werden. Benutzerdefinierte suchlösungen, die SQL-Syntax mit der Abfrage Serverobjektmodell und den Query-Webdienst verwenden, die in früheren Versionen von SharePoint Server erstellt wurden, funktionieren nicht, während der Aktualisierung auf SharePoint Server 2013. Abfragen, die über diese Anwendungen übermittelt wird einen Fehler zurückgegeben. Weitere Informationen zur Verwendung von FQL-Syntax und KQL-Syntax finden Sie unter  [Syntaxreferenz für die Keyword Query Language (KQL)](keyword-query-language-kql-syntax-reference.md) und [Syntaxreferenz für FQL (FAST Query Language)](fast-query-language-fql-syntax-reference.md).
  
    
    

## Search REST-Dienst für die Remoteausführung von Abfragen von Clientanwendungen
<a name="SP15Searchnew_support"> </a>

SharePoint Server 2013 enthält den Representational State Transfer (REST)-Dienst, mit dem Sie Remoteausführung Abfragen für den Suchdienst SharePoint 2013 von Clientanwendungen mit jeder Technologie, die REST-Webanfragen unterstützt. Der Search-REST-Dienst stellt zwei Endpunkte, **query** und **suggest**und **GET** und **POST** Vorgänge unterstützt. Ergebnisse werden in XML oder JSON-Format zurückgegeben.
  
    
    
Dies ist der Zugriffspunkt für den Dienst:  `http://server/_api/search/`. Sie können die Website auch wie folgt in der URL angeben:  `http://server/site/_api/search/`. Der Suchdienst gibt Ergebnisse aus der gesamten Websitesammlung zurück. Es werden also die gleichen Ergebnisse bei beiden Arten des Zugriffs auf den Dienst zurückgegeben.
  
    
    
Sie können auch die URL, die Zugriff auf den Dienst wie folgt client.svc verweist:  `http://server/_vti_bin/client.svc/search/`. Die Verwendung von  `_api` ist jedoch die bevorzugte Konvention.
  
    
    
Verwenden Sie den folgenden Zugriffspunkt Zugriff auf die webdienstmetadaten:
  
    
    
 `http://server/_api/$metadata`
  
    
    
Allgemeine Informationen über den REST-Dienst in SharePoint 2013 finden Sie unter  [Programmieren mit dem SharePoint 2013 REST-Dienst](use-odata-query-operations-in-sharepoint-rest-requests.md).
  
    
    

## SharePoint-Suchabfrage-Webdienst ist veraltet.
<a name="SP15Searchnew_support"> </a>

Der Query-Webdienst (befindet sich in dem Pfad  `http://server/site/_vti_bin/search.asmx`) ist in SharePoint 2013 veraltet. Wenn Sie neue Anwendungen schreiben, vermeiden Sie die Verwendung dieses veralteten Features, und verwenden Sie stattdessen den neuen Abfrage CSOM oder Abfrage REST-Dienst. Wenn Sie vorhandene Anwendungen ändern, empfehlen wir dringend empfohlen, keine Abhängigkeit dieses Feature zu entfernen.
  
    
    

## SharePoint Search-Objektmodell Abfragevorgängen
<a name="SP15Searchnew_support"> </a>

Eigenschaften von Abfrage enthalten Informationen zu einer Suchabfrage. Eine Eigenschaftensammlung wurde in SharePoint 2013 suchen die Abfrage und Ergebnisse Klassen zum Aktivieren der benutzerdefinierte Abfrageeigenschaften hinzugefügt. Sie können vorhandene Abfrageeigenschaften über die Eigenschaft auf eine der Abfrageklassen wie folgt zugreifen:
  
    
    
 `KeywordQuery.EnableStemming`
  
    
    
Sie können auch den Eigenschaftenbehälter wie folgt:
  
    
    
 `KeywordQuery.Properties["EnableStemming"]`
  
    
    
Sie können benutzerdefinierte Eigenschaften zugreifen, nur mithilfe der Eigenschaftensammlung wie folgt:
  
    
    
 `KeywordQuery.Properties["UserDefinedProperty"]`
  
    
    
SharePoint 2013 Suche schließt Abfrageeigenschaften im Eigenschaftenbehälter, einschließlich der neuen Abfrageeigenschaften wie etwa:
  
    
    

- **BypassResultTypes** Gibt an, ob die Suche Ergebniselementtyp für den Abfrageergebnissen zurückgegeben wird. Geben Sie **true** zum Zurückgeben von kein Ergebnistyp. andernfalls **false**.
    
  
- **EnableInterleaving** Gibt an, ob die Ergebnissätze, die durch Ausführen von abfrageregelaktionen zum Hinzufügen eines ergebnisblocks generiert mit dem Resultset für die ursprüngliche Abfrage verwendet werden. Geben Sie **true**, um die generierte Ergebnismenge mit dem ursprünglichen Resultset mischen. andernfalls **false**.
    
  
- **EnableQueryRules** Gibt an, ob Abfrageregeln für diese Abfrage aktiviert sind. **true** zum Aktivieren von Abfrageregeln für die Abfrage angeben. andernfalls **false**.
    
  
Sie können eine beliebige Eigenschaft im Eigenschaftenbehälter, einschließlich der benutzerdefinierten Eigenschaften als abfrageregelbedingungen angeben. Verwenden Sie Abfrageregeln zum Anpassen des Suchvorgangs für die Arten von Abfragen, die für Ihre Benutzer wichtig sind. Wenn eine Abfrage in einer Abfrageregel angegebene Bedingungen entspricht, gibt die Regel Benutzeraktionen zum Verbessern der Relevanz der Suchergebnisse zugeordnet.
  
    
    

## Schlüsselwort Sprache Abfragevorgängen
<a name="SP15Searchnew_support"> </a>

SharePoint 2013 enthält Verbesserungen an der Schlüsselwort-Abfragesprache, die in diesem Abschnitt beschrieben werden.
  
    
    

### Verbesserte NEAR-operator

In SharePoint Server 2010 Operators **NEAR** impliziert einen token maximalen Abstand von **8** und die Reihenfolge der Eingabe Token beibehalten. In SharePoint 2013 behält der Operator **NEAR** nicht mehr die Reihenfolge der Token. Darüber hinaus erhält der Operator **NEAR** jetzt einen optionalen Parameter, der maximalen token Abstand angibt. Der Standardwert ist jedoch weiterhin **8**. Wenn Sie das vorherige Verhalten verwenden müssen, verwenden Sie stattdessen **ONEAR**.
  
    
    
Der **NEAR** -Operator kann in Eigenschaft Einschränkung Ausdrücken verwendet werden, wie im folgenden Beispiel dargestellt:
  
    
    
 `"acquisition" NEAR "debt"`
  
    
    
Diese Abfrage stimmt exakt mit Elementen, in dem das Token "Erwerb" und "Forderung" innerhalb desselben Dokuments, mit einer maximalen token Abstand von **8** angezeigt (der Standardwert der _n_ ist, wenn kein Wert angegeben ist). Die Reihenfolge der Token ist nicht von Bedeutung für die Übereinstimmung.
  
    
    
Wenn Sie einen geringeren token Abstand benötigen, können Sie es wie folgt angeben:
  
    
    
 `"acquisition" NEAR(n=3) "debt"`
  
    
    
Diese Abfrage stimmt exakt Elemente, in denen die beiden Token "Erwerb" und "Forderung" innerhalb desselben Dokuments, mit einer maximalen token Abstand von **3** angezeigt werden. Die Reihenfolge der Token ist nicht von Bedeutung für die Übereinstimmung.
  
    
    

### Neue ONEAR-operator

Der Operator **ONEAR** stellt in der Nähe geordnete Funktionalität bereit. Er empfängt optionalen Parameter, der maximalen token Abstand angibt. Der Standardwert ist **8**.
  
    
    
Der Operator **ONEAR** behält die Reihenfolge der Eingabe Ausdrücke. Verwenden Sie für ungeordnete Nähe **NEAR**.
  
    
    
Den Operator **ONEAR** können in Eigenschaft Einschränkung Ausdrücken wie im folgenden Beispiel dargestellt:
  
    
    
 `"acquisition" ONEAR "debt"`
  
    
    
Diese Abfrage stimmt exakt Elemente, in denen die beiden Token "Erwerb" und "Forderung" angezeigt werden, innerhalb desselben Dokuments, mit einer maximalen token Abstand von **8** (die den Standardwert _n_ ist, wenn kein Wert angegeben ist). Die Reihenfolge der Token muss für ein Element, das zurückgegeben werden übereinstimmen.
  
    
    
Wenn Sie einen geringeren token Abstand benötigen, können Sie es wie folgt angeben:
  
    
    
 `"acquisition" ONEAR(n=3) "debt"`
  
    
    
Diese Abfrage stimmt exakt Elemente, in denen die beiden Token "Erwerb" und "Forderung" innerhalb desselben Dokuments, mit einer maximalen token Abstand von **3** angezeigt werden. Die Reihenfolge der Token muss für ein Element, das zurückgegeben werden übereinstimmen.
  
    
    

### Neue XRANK-operator

In SharePoint Server 2010 war der **XRANK** Operator nur mit FAST Query Language (FQL) verfügbar. SharePoint 2013 führt einen neuen und leistungsstarken **XRANK** -Operator.
  
    
    
Der Operator **XRANK** bietet dynamische Steuerung der Rangordnung. Dieser Operator steigert die dynamische Rangfolge der Elemente, die auf Basis des Vorkommens bestimmter Angaben ohne Ändern der Elemente, die mit die Abfrage übereinstimmen.
  
    
    

## Rich-Ergebnis-Framework für das Anpassen der Benutzeroberfläche für Suchergebnisse
<a name="SP15Searchnew_support"> </a>

SharePoint 2013 Suche umfasst ein neue Framework Ergebnisse, das zum Anpassen der Darstellung (Aussehen und Verhalten) über die Search Results-Benutzeroberfläche (UI) erleichtert. Nun können Sie anstelle von Schreiben von benutzerdefiniertem XSLT zum Ändern der Anzeige von Suchergebnissen aus, die Darstellung der wichtige Typen von Ergebnissen mithilfe von Anzeigevorlagen und Ergebnistypen anpassen.
  
    
    

### Anzeigevorlagen

Anzeigevorlagen definieren das visuelle Layout und das Verhalten der einen Ergebnistyp mithilfe von HTML und CSS- JavaScript. Anpassen die vorhandenen Anzeigevorlagen oder Erstellen von Anzeigevorlagen mithilfe ein HTML-Editor, und Laden Sie sie in der Galerieansicht Vorlagen.
  
    
    

### Ergebnistypen

Ergebnistypen definieren, wie Sie eine Reihe von Suchergebnisse basierend auf einer der folgenden Auflistung anzuzeigen:
  
    
    

- **Regeln** Bestimmen Sie, wann einen Ergebnistyp basierend auf den angegebenen Bedingungen gelten. Regelbedingungen können mithilfe von Gleichheit, Vergleichsoperatoren und logischen Operatoren verknüpft werden.
    
  
- **Eigenschaften** Bestimmen Sie die Liste der verwalteten Eigenschaften für das Ergebnis. Sie müssen verwaltete Eigenschaften zur Liste hinzufügen, bevor Sie eine Anzeigevorlage die verwaltete Eigenschaft zuordnen.
    
  
- **Anzeigevorlagen** Definieren Sie das visuelle Layout des Ergebnistyps.
    
  
Administratoren können erstellen und Verwalten von Ergebnistypen auf Standortebene oder dienstanwendungsebene; keine benutzerdefinierte Codierung ist erforderlich.
  
    
    

## Connector-Framework-Verbesserungen
<a name="SP15Searchnew_support"> </a>

SharePoint 2013 Suchen können Sie abrufen Anspruchsinformationen für Inhalte, die in benutzerdefinierten externen Datenquellen, die mithilfe des Frameworks Connector gecrawlt werden.
  
    
    
Das konnektorframework bietet auch verbesserte Ausnahme erfassen und Protokollierung, um Ihnen bei der Problembehandlung für Fehler beim Crawlen von Inhaltsquellen mit benutzerdefinierten Connectors, die auf das konnektorframework aufbauen. Informationen über das konnektorframework finden Sie unter  [Connector Framework für die Suche in SharePoint 2013](search-connector-framework-in-sharepoint-2013.md).
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Durchsuchen neuer Inhalte mit SharePoint-Suche](searching-new-content-with-sharepoint-search.md)
    
  
-  [Konfigurieren der Suche in SharePoint 2013](configure-search-in-sharepoint-2013.md)
    
  
-  [Erstellen von Suchabfragen in SharePoint 2013](building-search-queries-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: verwenden ein benutzerdefinierten Security Trimmer für SharePoint Server-Suchergebnisse](how-to-use-a-custom-security-trimmer-for-sharepoint-server-search-results.md)
    
  

