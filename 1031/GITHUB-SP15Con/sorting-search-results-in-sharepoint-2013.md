---
title: Sortieren von Suchergebnissen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 66af835e-2c8f-405e-8bed-cb1e5436e190
---



# Sortieren von Suchergebnissen in SharePoint 2013

  
    
    
![Konzeptuelles Übersichtsthema](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
Suchergebnisse programmgesteuert sortieren - nach Rang, nach dem Wert einer verwalteten Eigenschaft, nach einem Formelausdruck oder in zufälliger Reihenfolge - mithilfe des **Query**-Objektmodells in SharePoint Server 2013. 
Sie können die Suchergebnisse für SharePoint Server 2013 auf vier Arten sortieren:
  
    
    


-  [Sortieren von Suchergebnissen nach Rang](#SP15_Sort_search_resuilts_by_rank): Ermöglicht die Sortierung des Suchergebnisses nach Relevanzrangfolge.
    
  
-  [Sortieren von Suchergebnissen nach dem Wert einer verwalteten Eigenschaft](#SP15_Sort_search_results_by_managed_property_value): Ermöglicht die Sortierung des Suchergebnisses basierend auf dem Wert mindestens einer verwalteten Eigenschaft.
    
  
-  [Sortieren von Suchergebnissen nach einem Formelausdruck](#SP15_Sort_search_results_by_formula): Ermöglicht die Sortierung des Suchergebnisses nach einer in der Abfrageanforderung angegebenen Formel.
    
  
-  [Sortieren von Suchergebnissen in zufälliger Reihenfolge](#SP15_Sort_search_results_in_random_order): Ermöglicht die Sortierung des Abfrageergebnisses in zufälliger Reihenfolge oder das Hinzufügen einer zufälligen Komponente zur Sortierreihenfolge.
    
  

In diesem Artikel wird nur die programmgesteuerte Sortierung von Suchergebnissen behandelt. Informationen zum Sortieren der Suchergebnisse mit SharePoint Server 2013-Abfrageregeln finden Sie in den folgenden Artikeln:
  
    
    


-  [„Ändern bewerteter Suchergebnisse" in „Verwalten von Abfrageregeln"](http://technet.microsoft.com/de-de/library/jj871676.aspx#BKMK_ChangeRankedSearchResults)
    
  
-  [„Ändern bewerteter Suchergebnisse" in „Erstellen von Abfrageregeln für das Web Content Management"](http://technet.microsoft.com/de-de/library/jj871014.aspx#BKMK_ChangeRankedSearchResults)
    
  

## Angeben der Sortierung in einer Abfrageanforderung
<a name="SP15_Specify_sorting_in_query_request"> </a>

Bei Verwendung des **Query**-Objektmodells können Sie die Sortierkriterien wählen, indem Sie über die  [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) -Eigenschaft der [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) -Klasse eine Sortierspezifikation angeben. Die [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) -Eigenschaft ist von Typ [SortCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortCollection.aspx) , der eine Auflistung von [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) -Objekten darstellt.
  
    
    
Ein  [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) -Objekt definiert eine Art der Sortierung von Suchergebnissen. Es besteht aus einem Wert, nach dem Sie Suchergebnisse sortieren möchten ( [Property](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Property.aspx) ), und einer Richtung der Sortierung ( [Direction](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Direction.aspx) ). Die Richtung ist vom Typ [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) und kann aufsteigend oder absteigend sein.
  
    
    
Wenn  [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) mehrere Werte enthält, erfolgt die Sortierung basierend auf der Reihenfolge, in der die Werte angezeigt werden. Dies bedeutet, dass jedes **Sort**-Objekt eine Ebene der Sortierreihenfolge darstellt. Eine nachfolgende Ebene ändert nicht die Reihenfolge der Ergebnisse, die von vorherigen Ebenen unterschieden wurden. Aber sie kann sich auf die interne Reihenfolge der Ergebnisse auswirken, die die gleichen Sortierwerte für die vorherigen Ebenen aufweisen.
  
    
    
Neben dem **Query**-Objektmodell bietet SharePoint Server 2013 einen REST-Suchdienst, mit dem Sie den Suchindex mit Ihren Clientanwendungen oder mobilen Anwendungen abfragen können. Der REST-Suchdienst unterstützt HTTP POST- und HTTP GET-Anforderungen. Weitere Informationen zum Erstellen von URIs für diese Anforderungen finden Sie unter  [Erstellen von Abfragen mit dem Search-REST-Dienst](sharepoint-search-rest-api-overview.md#bk_queryrest).
  
    
    

## Sortieren von Suchergebnissen nach Rang
<a name="SP15_Sort_search_resuilts_by_rank"> </a>

Standardmäßig werden die Suchergebnisse nach Relevanzrang sortiert. Dies bedeutet, dass SharePoint Server 2013 die relevantesten Ergebnisse oben in den Suchergebnissen platziert. Wenn Sie nach Rang sortieren, werden die Ergebnisse immer in absteigender Reihenfolge sortiert. Sie können die Sortierreihenfolge jedoch mithilfe von  [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) in aufsteigende Reihenfolge ändern.
  
    
    
Sie können zudem die Rangberechnung in der Abfragezeichenfolge auf zwei Arten beeinflussen:
  
    
    

- Mit dem **XRANK**-Operator in  [Syntaxreferenz für die Keyword Query Language (KQL)](keyword-query-language-kql-syntax-reference.md) und [Syntaxreferenz für FQL (FAST Query Language)](fast-query-language-fql-syntax-reference.md). Mit **XRANK** können Sie für den Fall, dass eine bestimmte Abfragebedingung erfüllt wird, eine bedingte Rangverstärkung anwenden.
    
  
- Durch Auswählen einer Relevanzgewichtung für eine dynamische Rangfolge. Bei Verwendung von FQL können Sie eine einzelne Relevanzgewichtung für jeden **STRING**-Operator angeben.
    
  

## Sortieren von Suchergebnissen nach dem Wert einer verwalteten Eigenschaft
<a name="SP15_Sort_search_results_by_managed_property_value"> </a>

Sie können die Sortierung der Suchergebnisse basierend auf dem Wert mindestens einer verwalteten Eigenschaft angeben. Dies bedeutet, dass SharePoint Server 2013 die Sortierung basierend auf allen Ergebnissen ausführt, die der Abfrage entsprechen.
  
    
    
Sie können basierend auf Texteigenschaften und numerischen Eigenschaften sortieren. Bei Texteigenschaften basiert die Sortierung auf der Standardsortierung von Textzeichenfolgen. Im Gegensatz dazu basiert die Sortierung für numerische Eigenschaften (z. B. verwaltete Eigenschaften vom Typ  [DateTime](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.DateTime.aspx) ), auf dem numerischen Wert.
  
    
    

### Beispiel

Das folgende Beispiel zeigt die Sortierung der Suchergebnisse mithilfe der verwalteten Eigenschaft **Size**.
  
    
    

```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("Size", SortDirection.Descending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"] + " Size:" + result["Size"]);
    }
}
```

Alternativ können Sie mit folgendem Aufruf die Such-REST-API zum Sortieren der Suchergebnisse nach der **Size**-Eigenschaft verwenden.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='size:descending'
```


## Sortieren von Suchergebnissen nach einem Formelausdruck
<a name="SP15_Sort_search_results_by_formula"> </a>

Sie können die Sortierung der Suchergebnisse basierend auf einer Sortierspezifikation angeben, die den Sortierwert nach einer mathematischen Formel berechnet.
  
    
    
Das Feature der Sortierung nach einer Formel ist eine Erweiterung der einstufigen und mehrstufigen Sortierfunktionalität für Suchergebnisse. Das Feature ermöglicht die Angabe einer Formel anstelle einer verwalteten Eigenschaft als Sortierkriterium. 
  
    
    
Mit dem Feature der Sortierung nach einer Formel können Sie mathematische Operationen auf den Wert von verwalteten Eigenschaften für jedes Element im Abfrageergebnis anwenden.
  
    
    
Im Folgenden finden Sie Beispiele, die mithilfe einer Formel für die Suchergebnissortierung implementiert werden können:
  
    
    

- K-Nächster-Nachbar-Algorithmus zur Klassifikation von Dokumenten
    
  
- Euklidischer Abstand oder Manhattan-Abstand zur Berechnung geographischer Entfernungen
    
  
- Bevorzugter Wert, z. B. zum Sortieren von Dokumenten basierend darauf, wie weit der Wert einer bestimmten verwalteten Eigenschaft von einem bevorzugten Wert entfernt ist.
    
  
Das Feature der Sortierung nach einer Formel umfasst keine Kontrolle über statistische dynamische Rangfolgenparameter, wie z. B. Häufigkeit von Begriffen und Nähe.
  
    
    
Die Formel wird von links nach rechts und mit der Standardrangfolge mathematischer Operatoren ausgewertet. D. h., zuerst werden Funktionen und Klammergruppen ausgewertet, dann werden Multiplikationen und Divisionen und schließlich Additionen und Subtraktionen ausgeführt.
  
    
    

> **WICHTIG**
> Das endgültige Ergebnis einer Formel muss im Wertebereich einer 32-Bit-Ganzzahl mit Vorzeichen liegen. Andernfalls ist die Sortierung möglicherweise falsch. 
  
    
    


### Angeben der Sortierformel in einer Abfrage

Sie können in der Sortierspezifikation der Abfrageanforderung eine Sortierformel anstelle einer verwalteten Eigenschaft angeben.
  
    
    
Die Sortierspezifikation hat folgendes Format:  `[formula:<sort-formula>]`
  
    
    
In dem Format ist  _<sort-formula>_ der Ausdruck für die Sortierformel.
  
    
    

> **HINWEIS**
> Die eckigen Klammern sind Teil der Syntax der Sortierspezifikation. 
  
    
    

Die Standardsortierreihenfolge ist absteigend. Sie können auch eine Formel verwenden, die nach aufsteigenden Werten sortiert, z. B. wenn die Formel eine geographische Entfernung angibt.
  
    
    
Das folgende Codebeispiel veranschaulicht die Sortierung nach einer Formel in aufsteigender Sortierreihenfolge mithilfe des **Query**-Objektmodells.
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(2000-size)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

Alternativ können Sie mit folgendem Aufruf die Such-REST-API zum Sortieren der Suchergebnisse nach der **Size**-Eigenschaft verwenden.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(2000-size)]:ascending'

```


### Verwenden von verwalteten Eigenschaften in der Sortierformel

Sie können eine Sortierformel auf den Wert verwalteter Eigenschaften vom Typ  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) , [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) und [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) anwenden. Sie müssen die Sortierung für die angegebene verwaltete Eigenschaft im Suchschema aktivieren.
  
    
    
Für weitere verwaltete Eigenschaften vom Typ  [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) wird der Wert vor der Formelauswertung mit 10^(Dezimalziffern) multipliziert.
  
    
    
Für verwaltete Eigenschaften vom Typ  [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) wird der Wert vor der Formelauswertung in die Anzahl von jeweils 100 Nanosekunden seit 1. Januar 29000 v. Chr. konvertiert. Das Jahr hat 366 Tage.
  
    
    

### Sortierformelausdrücke

In Tabelle 1 sind die Funktionen aufgelistet, die Sie im Sortierformelausdruck verwenden können. Der Ausdruck darf keine Leerzeichen enthalten.
  
    
    

**Tabelle 1. Funktionen für Sortierformelausdrücke**


|**Funktion**|**Beschreibung**|
|:-----|:-----|
|**+** <br/> |Gibt Addition an.  <br/> |
|**-** <br/> |Gibt Subtraktion an.  <br/> |
|* <br/> |Gibt Multiplikation an.  <br/> |
|**/** <br/> |Gibt Division an.  <br/> > **HINWEIS**> In der Standardeinstellung führt eine Division durch Null zu einer Ausnahme, und die Abfrage gibt einen Fehler zurück. Mit dem **errtolast**-Operator können Sie den Abfragefehler vermeiden und stattdessen die fehlerhaften Elemente am Ende des Resultsets platzieren.           |
|**rank** <br/> |Ein spezielles Schlüsselwort, das den dynamischen Rang eines Elements darstellt.  <br/> Beispiel:  `abs(rank-100)` verwendet den Abstand vom Rangwert 100 als Sortierkriterium. <br/> |
|**[0-9.]+** <br/> |Gibt an, dass die Zahlen als **integer**- oder **double**-Werte angegeben werden können.  <br/> Beispiele: 503; 3,14; 5,4352262  <br/> |
|**[a-z0-9]+]** <br/> |Gibt an, dass eine beliebige Zeichenfolge, die nicht als Funktionsname erkannt wird, als Name einer verwalteten Eigenschaft behandelt wird. Sie müssen die Sortierung für die angegebene verwaltete Eigenschaft im Suchschema aktivieren.  <br/> Beispiel: Sie können eine verwaltete Eigenschaft namens **height** mit aktivierter Sortierung definieren. Dies ermöglicht Ihnen, "height" als Ausdruck in der Formel zu verwenden. Die Formel verwendet dann den Wert der verwalteten Eigenschaft **height**.  <br/> |
|**( and )** <br/> |Verwendet zur Gruppierung von Berechnungen, um den richtigen Vorrang sicherzustellen.  <br/> Beispiel: 4*(3+2)  <br/> |
|**sqrt(n)** <br/> |Die Quadratwurzel von  _n_ <br/> |
|**exp(n)** <br/> |Die Exponentialfunktion, die  *pow(2.71828182846,n)*  entspricht. <br/> |
|**log(n)** <br/> |Der natürliche Logarithmus von _n_ <br/> |
|**abs(n)** <br/> |Der absolute Wert von  _n_ <br/> |
|**ceil(n)** <br/> |Die Obergrenze von  _n_. Das heißt, wenn  _n_ keine ganze Zahl ist, wird auf die nächste ganze Zahl aufgerundet. Wenn _n_ eine ganze Zahl ist, wird _n_ verwendet. <br/> |
|**floor(n)** <br/> |Die Untergrenze von  _n_. Das heißt, wenn  _n_ keine ganze Zahl ist, wird auf die nächste ganze Zahl abgerundet. Wenn _n_ eine ganze Zahl ist, wird _n_ verwendet. <br/> |
|**round(n)** <br/> |Die Rundung von  _n_ auf die nächstgelegene gerade ganze Zahl. Auch als „Bankers rounding" (mathematisches Runden) oder „Round half to even" bezeichnet. <br/> |
|**sin(n)** <br/> |Der Sinus von  _n_ Bogenmaß. <br/> |
|**cos(n)** <br/> |Der Kosinus von  _n_ Bogenmaß. <br/> |
|**tan(n)** <br/> |Die Tangente von  _n_Bogenmaß.  <br/> |
|**asin(n)** <br/> |Der Arcussinus von  _n_ in Bogenmaß. <br/> |
|**acos(n)** <br/> |Der Arcuskosinus von  _n_ in Bogenmaß. <br/> |
|**atan(n)** <br/> |Der Arcustangens von  _n_ in Bogenmaß. <br/> |
|**pow(x,y)** <br/> |Der Wert von  _x_ hoch _y_.  <br/> > **HINWEIS**> Der Wert von  _y_ muss eine reelle Zahl sein.          |
|**atan2(y,x)** <br/> |Ein Arcustangens (mit zwei Argumenten) des Winkels im Bogenmaß zwischen der positiven X-Achse und der angegebenen kartesischen Koordinate (x,y).  <br/> |
|**bucket(b,n1,n2,…)** <br/> |Ein Operator, der verwendet werden kann, um diskrete Werte für angegebene Werteverteilungsbereiche für einen Ausdruck anzugeben.  <br/> Der Ausdruck  _b_ kann eine verwaltete Eigenschaft oder ein anderer Formelausdruck sein. Die Argumente _n1, n2, …_ stellen numerische Schwellenwerte dar. Sie können eine beliebige Anzahl von Bucket-Schwellenwerten angeben. <br/> > **HINWEIS**> Sie müssen die Argumente  _n1, n2, n3, …_ in der folgenden Reihenfolge angeben: `n1 < n2 < n3 < ...` mit `n1 >= 0`.           Ein angegebener Wert für den Eingabeausdruck  _b_ wird zum nächstgelegenen angegebenen numerischen Schwellenwert abgerundet. Ist der Wert kleiner als der kleinste angegebene Schwellenwert, ist der Ergebniswert 0 (null). <br/> |
|**errtolast(x)** <br/> |Ein Operator zur Steuerung der Behandlung von Formelausnahmen.  _x_ kann ein beliebiger Formelausdruck sein. Führt die Berechnung des Formelausdrucks für ein Element im Resultset zu einer mathematischen Ausnahme, z. B. eine Division durch null, werden diese Elemente unabhängig von der angegebenen Sortierreihenfolge am Ende der Sortierliste angezeigt. <br/> |
   

### Leistungsmerkmale für das Sortieren nach einer Formel

Das Verwenden einer Sortierformel impliziert, dass die Formelberechnungen auf alle gefundenen Elemente im Resultset angewendet werden. Somit hängen die Auswirkungen der Abfrageleistung von der Anzahl der Elemente ab, die der Abfrage entsprechen.
  
    
    
Lange Formeln mit vielen Operatoren erfordern mehr Verarbeitungszeit als kurze Formeln.
  
    
    

### Verwenden der Sortierung nach einer Formel für geographische Entfernungen

Sie können mit einer Sortierformel eine Bewertung entsprechend der Entfernung anwenden. Dazu müssen Sie verwaltete Eigenschaften angeben, die die geografische Breite und Länge der einzelnen Elemente darstellen.
  
    
    
Beispielsweise können Sie eine der folgenden Standardformeln verwenden:
  
    
    

- Manhattan-Abstand
    
  
- Euklidischer Abstand (siehe Beispiel 2)
    
  
- Semiversus-Formel
    
  

> **WICHTIG**
> Verwenden Sie verwaltete Eigenschaften vom Typ **Decimal** oder **Float**, um die Werte für die geografische Breite und die geografische Länge anzugeben. 
  
    
    


### Beispiele

Die folgenden Beispielen zeigen, wie die Sortierformel mithilfe des **Query**-Objektmodells angegeben wird.
  
    
    
 **Beispiel 1.** Platzieren der Elemente, deren verwaltete Eigenschaft **height** am nächsten bei 20 liegt, am Anfang der Liste.
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(20-height)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

Alternativ könnten Sie die Such-REST-API verwenden, um die Elemente, deren verwaltete Eigenschaft **height** am nächsten bei 20 liegt, am Anfang der Ergebnisliste zu platzieren. Dazu verwenden Sie den folgenden Aufruf.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(20-height)]:ascending
```

 **Beispiel 2.** Sortieren nach dem echten dreidimensionalen euklidischen Abstand von einer gegebenen Position (z. B. der Position eines Benutzers). Dieser basiert auf Positionsinformationen, die in den verwalteten Eigenschaften **latitude**, **longitude** und **height** bereitgestellt werden. Die folgende Formel gibt den dreidimensionalen euklidischen Abstand an, unter der Voraussetzung, dass die Basisposition 50/100/200 (Breite/Länge/Höhe) ist.
  
    
    
 `sqrt(pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2))`
  
    
    
Wenn Sie entfernungsbasiert sortieren möchten (und nicht durch Kombination der Entfernung mit anderen Parametern in einer Formel), können Sie die  `sqrt()`-Komponente entfernen, da dadurch die Sortierreihenfolge nicht geändert wird. Dies verbessert die Abfrageleistung.
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

 **Beispiel 3.** Runden der Werte der Größe in Buckets, wobei Werte auf einen der folgenden Werte abgerundet werden: 0, 5, 15, 50, 100. Sortierung mit den größten Werten zuerst.
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:bucket(size,5,15,50,100)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## Sortieren von Suchergebnissen in zufälliger Reihenfolge
<a name="SP15_Sort_search_results_in_random_order"> </a>

Sie können Abfrageergebnisse zufällig sortieren oder der Ergebnissortierung eine zufällige Komponente hinzufügen.
  
    
    
Die Spezifikation der zufälligen Sortierung hat folgendes Format:  `[random:seed=<seed>:hashfield=<managed property>]`
  
    
    

> **HINWEIS**
> Die eckigen Klammern sind Teil der Syntax der Sortierspezifikation. 
  
    
    

Tabelle 2 erläutert die Parameter für die Spezifikation der zufälligen Sortierung.
  
    
    

**Tabelle 2. Parameter für die Spezifikation der zufälligen Sortierung**


|**Parameter**|**Beschreibung**|**Erforderlich**|
|:-----|:-----|:-----|
| _Seed_ <br/> |Der Startwert für die Generierung der Zufallswerte.  <br/> Der Startwert dient als Eingabe für eine Funktion, die eine Zufallszahl generiert. Diese Zufallszahl wird in der entgültigen Sortierung verwendet. Wird nur die  _seed_-Option verwendet, erhalten Sie ein zufällig sortiertes Abfrageresultset. Die Sortierreihenfolge für die gleiche Abfrage (mit demselben Startwert) kann nach einer Indexaktualisierung anders ausfallen.  <br/> |Ja  <br/> |
| _Hashfield_ <br/> |Eine verwaltete Eigenschaft, die als Hashwert für die zufällige Generierung verwendet wird. Sie können diesen Parameter verwenden, um sicherzustellen, dass die Sortierreihenfolge für die gleiche Abfrage (mit demselben Startwert) nach einer Indexaktualisierung unverändert bleibt.  <br/> Die verwaltete Eigenschaft muss vom Typ  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) sein und [Sortable()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.Sortable.aspx) sein. Sie können diese verwaltete Eigenschaft mit zufälligen oder eindeutigen Werten (z. B. einer von einer Elementverarbeitungsphase aufgefüllten Sequenznummer) belegen. <br/> |Nein  <br/> |
   
Wenn Sie für gleiche Abfragen denselben Startwert angeben, werden die Elemente in der gleichen Reihenfolge angezeigt. Dies ermöglicht Ihnen, die zufällige Reihenfolge beizubehalten, wenn Sie Suchergebnisse seitenweise anzeigen. Verwenden Sie den  _hashfield_-Parameter, wenn die zufällige Reihenfolge erhalten bleiben soll, falls zufällig zwischen den Abfragen eine Indexaktualisierung stattfindet.
  
    
    

### Beispiele

Die folgenden Beispiele zeigen, wie die zufällige Sortierung mithilfe des **Query**-Objektmodells angegeben wird.
  
    
    
 **Beispiel 1.** Das gesamte Resultset wird in zufälliger Reihenfolge sortiert.
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=5432]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

Alternativ können Sie mit folgendem Aufruf die Such-REST-API zum zufälligen Sortieren des gesamten Resultsets verwenden.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[random:seed=5432]:ascending
```

 **Beispiel 2.** Das gesamte Resultset wird in zufälliger Reihenfolge sortiert. Die gleiche zufällige Reihenfolge für die gleiche Abfrage wird mit demselben Startwert beibehalten, auch wenn ein Index umgeschaltet wird. Eine benutzerdefinierte verwaltete Eigenschaft namens **hashvalue** muss im Suchschema vorhanden sein. Sie muss mit zufälligen oder sequenziellen numerischen Werten für alle indizierten Elemente belegt sein.
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=6543:hashfield=hashvalue]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## Weitere Ressourcen
<a name="bk_addresources"> </a>


-  [Suche in SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [Syntaxreferenz für die Keyword Query Language (KQL)](keyword-query-language-kql-syntax-reference.md)
    
  
-  [Syntaxreferenz für FQL (FAST Query Language)](fast-query-language-fql-syntax-reference.md)
    
  
-  [Übersicht über die REST-API der SharePoint-Suche](sharepoint-search-rest-api-overview.md)
    
  
-  [Übersicht über durchforstete und verwaltete Eigenschaften in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj219630%28office.15%29.aspx)
    
  

  
    
    
