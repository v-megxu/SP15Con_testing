---
title: Anpassen von Suchergebnissen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 1b30f6df-643a-4570-ae5c-d3d8df5609b8
---


# Anpassen von Suchergebnissen in SharePoint 2013
In diesem Artikel erfahren Sie, wie Sie in einem Suchergebnissatz in SharePoint Server 2013 ähnliche Elemente gruppieren oder doppelte Elemente entfernen, sodass die Ergebnisse übersichtlich und gut lesbar angezeigt werden.
In Suchergebnissen werden durch Gruppierung zwei oder mehr ähnliche Elemente in einem Suchergebnissatz reduziert, damit die Anzeige für den Benutzer besser lesbar ist. Das Entfernen von Duplikaten in Suchergebnissen ist ein Teil der Gruppierung; hierbei werden Elemente, die identisch oder fast identisch sind, aus dem Ergebnissatz entfernt. Abhängig von den Einstellungen, die vom SharePoint-Administrator festgelegt wurden, kann der Benutzer den Suchergebnissatz möglicherweise später erweitern und die einzelnen Ergebnisse anzeigen, die reduziert wurden.
  
    
    

Es folgen Beispiele von Methoden zum Gruppieren von Suchergebnissen:
- Duplikaterkennung - hierbei werden fast identische Dokumente aus dem Ergebnissatz entfernt.
    
  
- Websitereduzierung - hierbei wird nur das relevanteste Element jeder Website im Ergebnissatz angezeigt.
    
  
- Dokumentenmappenreduzierung - hierbei wird nur ein Treffer für jede Dokumentbibliothek in SharePoint angezeigt.
    
  
Sie können die Kriterien zum Reduzieren oder zum Entfernen von Duplikaten programmgesteuert mithilfe der folgenden  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) -Eigenschaften im Abfrageobjektmodell angeben:
-  [CollapseSpecification](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.CollapseSpecification.aspx)
    
  
-  [TrimDuplicates](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.TrimDuplicates.aspx)
    
  
-  [TrimDuplicatesOnProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesOnProperty.aspx)
    
  
-  [TrimDuplicatesKeepCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesKeepCount.aspx)
    
  
-  [TrimDuplicatesIncludeId](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesIncludeId.aspx)
    
  

## Reduzieren ähnlicher Suchergebnisse mithilfe der CollapseSpecification-Eigenschaft
<a name="bk_collapse_specification"> </a>

Die **CollapseSpecification**-Eigenschaft verwendet einen  _Spec_-Parameter, der mehrere durch ein Komma oder ein Leerzeichen getrennte Felder enthalten kann, die bei gemeinsamer Auswertung einen Satz von Kriterien für den Reduziervorgang angeben.
  
    
    
 **Syntax**
  
    
    
 `CollapseSpecification = Spec`
  
    
    
Die folgende Tabelle enthält die Felder des  _Spec_-Parameters.
  
    
    

**Tabelle 1. Felder des Spec-Parameters**


|**Element in Parameter**|**Beschreibung**|
|:-----|:-----|
| _Spec_ <br/> | `Subspec(<space>Subspec)*` <br/> |
| _Subspec_ <br/> | `Prop(','Prop)*[':'Dups]` <br/> |
| _Prop_ <br/> |Eine gültige verwaltete Eigenschaft oder ein Alias einer verwalteten Eigenschaft. Bei  _Prop_ wird die Groß-/Kleinschreibung nicht beachtet. Die verwaltete Eigenschaft muss abfragbar und entweder sortier- oder einschränkbar sein. <br/> |
| _Dups_ <br/> |Eine ganze Zahl, die die Anzahl der beizubehaltenden Elemente angibt. Der Standardwert ist 1.  <br/> |
| _<space>_ <br/> |Eigenschaften werden mit dem **OR**-Operator kombiniert.  <br/> |
| _,_ <br/> |Eigenschaften werden mit dem **AND**-Operator kombiniert.  <br/> |
| _*_ <br/> |Gibt mehr Elemente an.  <br/> |
| _() or []_ <br/> |Gibt optionale Elemente an.  <br/> |
   
Wenn die Felder in  _Spec_ durch Kommas getrennt sind, werden die Felder mit dem **AND**-Operator kombiniert. Wenn alle angegebenen Felder erfüllt sind, werden die Elemente reduziert.
  
    
    
Wenn hingegen die Felder in  _Spec_ durch Leerzeichen getrennt sind, werden die Felder (oder _Subspecs_) unter Verwendung einer Erweiterung kombiniert, die den **AND**-Operator und den **OR**-Operator enthält. Beispiel: Ein Ausdruck wie  `Category:3 Product:2` wird intern in den Ausdruck `(Category AND Product) OR (Category)` mit einem Zähler für jedes Element transformiert; hier ein Maximum von zwei für das erste und drei für das letzte Element. Elemente werden reduziert, wenn einige der angegebenen Felder erfüllt sind.
  
    
    

### Beispiele für die Verwendung von CollapseSpecification

Die folgende Tabelle enthält einen Produktkatalog der Firma Contoso. In den nächsten Beispielen wird anhand dieses Katalogs die Funktionsweise der **CollapseSpecification**-Eigenschaft veranschaulicht. 
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|Laptops  <br/> |WWI  <br/> |19W X0196 Black  <br/> |Computer 1  <br/> |
|Laptops  <br/> |Adventure Works  <br/> |12 M1201 Red  <br/> |Computer 2  <br/> |
|Laptops  <br/> |Adventure Works  <br/> |15.4W M1548 White  <br/> |Computer 3  <br/> |
|Laptops  <br/> |Proseware  <br/> |19 X910 Black  <br/> |Computer 4  <br/> |
|Laptops  <br/> |Proseware  <br/> |Laptop19 X910 Black  <br/> |Computer 5  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |2.33 XD233 Silver  <br/> |Computer 6  <br/> |
|Desktops  <br/> |WWI  <br/> |2.33 X2330 Black  <br/> |Computer 7  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |1.60 ED160 White  <br/> |Computer 8  <br/> |
|Desktops  <br/> |WWI  <br/> |3.0 M0300 Silver  <br/> |Computer 9  <br/> |
   

  
    
    

#### Beispiel: Gruppieren nach Category

Gruppieren Sie zunächst die Elemente nach **Category**, und zeigen Sie die zwei obersten für jede Gruppe an (also  `"Category:2"`). Zeigen Sie dann für jede **Category** eine entsprechende Anzahl eindeutiger **Products** an (also "Product:1").
  
    
    
 **Syntax**
  
    
    
 `CollapseSpecification="Category:2 Product:1"`
  
    
    
Die folgenden Ergebnisse sollten zurückgegeben werden.
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|Laptops  <br/> |WWI  <br/> |19W X0196 Black  <br/> |Computer 1  <br/> |
|Laptops  <br/> |Adventure  <br/> |12 M1201 Red  <br/> |Computer 2  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |2.33 XD233 Silver  <br/> |Computer 6  <br/> |
|Desktops  <br/> |WWI  <br/> |2.33 X2330 Black  <br/> |Computer 7  <br/> |
   
Verwenden Sie den folgenden Code, um die Suchergebnisse mithilfe der **CollapseSpecification**-Eigenschaft zu reduzieren.
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
        {
            QueryText = "Title:Computer",
            CollapseSpecification = "Category:3 Product:1",
        };

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    {
        Console.WriteLine(result["Title"]);
    }
}

```


#### Beispiel: Gruppieren nach Category und Product

Gruppieren Sie zunächst die Elemente nach **Category** und nach **Product**. Zeigen Sie anschließend jede eindeutige Kombination an.
  
    
    
 **Syntax**
  
    
    
 `CollapseSpecification="Category,Product:1"`
  
    
    
Die folgenden Ergebnisse sollten zurückgegeben werden.
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|Laptops  <br/> |WWI  <br/> |19W X0196 Black  <br/> |Computer 1  <br/> |
|Laptops  <br/> |Adventure Works  <br/> |12 M1201 Red  <br/> |Computer 2  <br/> |
|Laptops  <br/> |Proseware  <br/> |19 X910 Black  <br/> |Computer 4  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |2.33 XD233 Silver  <br/> |Computer 6  <br/> |
|Desktops  <br/> |WWI  <br/> |2.33 X2330 Black  <br/> |Computer 7  <br/> |
   

## Entfernen doppelter Suchergebnisse mithilfe der TrimDuplicates-Eigenschaft
<a name="bk_trim_duplicates"> </a>

Verwenden Sie **TrimDuplicates**, um anzugeben, ob die doppelten Suchergebnisse aus dem Suchergebnissatz entfernt werden sollen. **TrimDuplicates** ist standardmäßig auf **true** festgelegt.
  
    
    
Wenn Sie **TrimDuplicates** mit **TrimDuplicatesOnProperty** oder vorzugsweise mit **CollapseSpecification** verwenden, wird **TrimDuplicates** auf **false** festgelegt.
  
    
    
 **Syntax**
  
    
    
 `TrimDuplicates = <$true | $false>`
  
    
    

### Entfernen doppelter Suchergebnisse mithilfe der TrimDuplicatesOnProperty-Eigenschaft
<a name="bk_trim_duplicates_on_property"> </a>

Verwenden Sie **TrimDuplicatesOnProperty**, um anzugeben, ob eine nicht standardmäßige verwaltete Eigenschaft als Basis für das Entfernen von Duplikaten verwendet werden soll. Der Standardwert ist die verwaltete Eigenschaft **DocumentSignature**. Die verwaltete Eigenschaft muss den Typ **Integer** oder **String** aufweisen. Indem Sie eine verwaltete Eigenschaft verwenden, die eine Elementgruppe darstellt, können Sie dieses Feature zum Reduzieren von Feldern nutzen.
  
    
    
 **Syntax**
  
    
    
 `TrimDuplicatesOnProperty = <managed property>`
  
    
    

> **HINWEIS**
> Verwenden Sie in SharePoint Server 2013 nach Möglichkeit immer **CollapseSpecification**. **TrimDuplicatesOnProperty** steht nur aus Gründen der Abwärtskompatibilität zur Verfügung.
  
    
    


### Entfernen doppelter Suchergebnisse mithilfe der TrimDuplicatesKeepCount-Eigenschaft
<a name="bk_trim_duplicates_keep_count"> </a>

Verwenden Sie **TrimDuplicatesKeepCount**, um die Anzahl der beizubehaltenden Dokumente anzugeben, wenn **TrimDuplicates** auf **true** festgelegt ist. Wenn **TrimDuplicates** auf einer verwalteten Eigenschaft basiert, die als Gruppenbezeichner verwendet werden kann, z. B. eine Website-ID, können Sie steuern, wie viele Ergebnisse für jede Gruppe zurückgegeben werden. Zurückgegeben werden die Elemente mit dem höchsten dynamischen Rang in jeder Gruppe.
  
    
    
 **Syntax**
  
    
    
 `TrimDuplicatesKeepCount = <number>`
  
    
    

### Abrufen doppelter Suchergebnisse mithilfe der TrimDuplicatesIncludeId-Eigenschaft
<a name="bk_trim_duplicates_include_id"> </a>

Verwenden Sie **TrimDuplicatesIncludeId**, um die Duplikate eines Dokuments abzurufen, wenn **TrimDuplicates** auf **true** und **TrimDuplicatesOnProperty** oder **CollapseSpecification** auf **false** festgelegt ist.
  
    
    
Die Dokument-ID ( _docid_) wird zum Abrufen der Duplikate eines bestimmten Dokuments verwendet.
  
    
    
 **Syntax**
  
    
    
 `TrimDuplicatesIncludeId = <docid>`
  
    
    

> **HINWEIS**
> Die verwaltete Eigenschaft  _fcoid_ in FAST Search Server 2010 for SharePoint wurde durch die verwaltete Eigenschaft _docid_ in SharePoint Server 2013 ersetzt.
  
    
    


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx)
    
  
-  [Übersicht über das Suchschema in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj219669%28office.15%29.aspx)
    
  

  
    
    

