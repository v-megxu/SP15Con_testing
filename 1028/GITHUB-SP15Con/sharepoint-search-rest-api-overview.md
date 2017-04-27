---
title: SharePoint 搜尋 REST API 概觀
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# SharePoint 搜尋 REST API 概觀
使用 SharePoint Server 2013 中的搜尋 REST 服務以及任何支援 REST 網路要求的技術，來新增用戶端及行動應用程式的搜尋功能。
## 使用搜尋 REST 服務進行查詢
<a name="bk_queryrest"> </a>

在 SharePoint 2013 中搜尋 包含搜尋 REST 服務，您可以使用任何支援 REST Web 要求的技術，將搜尋功能加入至您的用戶端和行動裝置應用程式使用。您可以使用搜尋 REST 服務，在 SharePoint Add-ins、遠端用戶端應用程式、行動應用程式及其他應用程式中送出關鍵字查詢語言 (KQL) 或快速查詢語言 (FQL) 查詢。
  
    
    
搜尋 REST 服務同時支援 HTTP **POST** 和 HTTP **GET** 要求。
  
    
    

### GET 要求

建構 URI 以對搜尋 REST 服務提出查詢 **GET** 要求，如下所示：
  
    
    
 `/_api/search/query`
  
    
    
對於 **GET** 要求，在 URL 中指定查詢參數。您可用兩種方式建構 **GET** 要求 URL：
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### POST 要求

為搜尋 REST 服務建構查詢 **POST** 要求的 URI，如下所示：
  
    
    
 `/_api/search/postquery`
  
    
    
針對 **POST** 要求，以 JavaScript Object Notation (JSON) 格式在要求中傳遞查詢參數。
  
    
    
搜尋 REST 服務的 HTTP **POST** 版本，支援 HTTP **GET** 版本所支援的所有參數。不過，部份參數有不同的資料型別，如 表 1 所述。
  
    
    

**表 1。使用不同資料型別的 POST 要求查詢參數**


|**參數**|**資料型別**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HithighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Properties](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
下列情況適用 **POST** 要求：
  
    
    

- 使用 **GET** 要求會超過 URL 長度限制時。
    
  
- 無法以簡單 URL 指定查詢參數時。例如，如果您必須傳遞包含複雜型別陣列的參數值或以逗號分隔的字串，建構 **POST** 要求可以有更大的彈性。
    
  
- 使用  [ReorderingRules](#bk_ReorderingRules) 參數時 (因為只有 **POST** 要求支援此參數)。
    
  

## 在搜尋 REST 服務中使用查詢參數
<a name="bk_UsingQueryParams"> </a>

當您對搜尋 REST 服務進行呼叫時，必須在要求中指定查詢參數。在 SharePoint 2013 中搜尋 使用這些查詢參數來建構搜尋查詢。使用 **GET** 要求時，在 URL 中指定查詢參數。至於 **POST** 要求，則以 JavaScript Object Notation (JSON) 格式在內文中傳遞查詢參數。
  
    
    
下列章節將說明送出搜尋 REST 服務的搜尋查詢所用的查詢參數。
  
    
    

### QueryText 參數

字串，包含搜尋查詢的文字。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

字串，包含取代查詢文字的文字，做為查詢轉換的一部分。
  
    
    
 **範例 GET 要求**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:johndoe'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

布林值，指定結果區塊傳回的結果表格是否與原始查詢傳回的結果表格混合。
  
    
    
 **true** 表示混合 ResultTables；否則為 **false**。預設值為 **true**。
  
    
    
除非您想提供自己的交錯實作，否則不需變更此值。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

用來執行搜尋查詢的結果來源識別碼。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

用於查詢的排名模型識別碼。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

包含在傳回的搜尋結果第一列。當您想要對搜尋結果實作分頁時，可以使用這個參數。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

搜尋結果中傳回的整體資料列數目上限。相較於  _RowsPerPage_， _RowLimit_ 是整體傳回的資料列數目上限。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

每頁傳回的資料列數目上限。相較於  _RowLimit_， _RowsPerPage_ 是指每一頁傳回的資料列數目上限，主要用於對搜尋結果實作分頁時。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

搜尋結果中傳回的 Managed 屬性。若要傳回 Managed 屬性，請在搜尋結構描述中將屬性的擷取旗標設為 **true**。
  
    
    
若是 **GET** 要求，在包含逗號分隔清單的屬性字串中指定 _SelectProperties_ 參數。若是 **POST** 要求，則以字串陣列指定 _SelectProperties_ 參數。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SelectProperties' : {
    'results' : [
          'Title,
          Author'
          ]
}
}
```


### Culture
<a name="bk_Culture"> </a>

查詢的地區設定識別碼 (LCID) (請參閱 [Microsoft 指派的地區設定識別碼](http://msdn.microsoft.com/zh-tw/goglobal/bb964664.aspx))。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

發出細分查詢時使用的細分篩選條件集。若是 **GET** 要求，以 FQL 篩選條件指定 _RefinementFilters_ 參數。若是 **POST** 要求，則以 FQL 篩選條件陣列指定 _RefinementFilters_ 參數。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RefinementFilters' : {
'results' : ['fileExtension:equals("docx")']
}
}
```


### Refiners
<a name="bk_Refiners"> </a>

搜尋結果中傳回的精簡器集。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Refiners': {
'results' : ['author,size']
}
}
```


### HiddenConstraints
<a name="bk_HiddenConstraints"> </a>

附加至查詢的其他查詢字詞。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

搜尋結果排序所依據的屬性清單。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SortList' : 
{
    'results' : [
        {
                'Property':'Created',
                'Direction': '0'
        },
        {
                'Property':'FileExtension',
                'Direction': '1'
        }
    ]
}
}
```


### EnableStemming
<a name="bk_EnableStemming"> </a>

布林值，指定是否啟用相關字詞功能。
  
    
    
 **true** 為啟用相關字詞功能；否則為 **false**。預設值為 **true**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

布林值，指定是否從結果中移除重複的項目。
  
    
    
 **true** 為移除重複的項目；否則為 **false**。預設值為 **true**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

查詢要求逾時之前等候的時間量，以毫秒為單位。預設值為 30000。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

布林值，指定是否在搜尋查詢中使用精確字詞來尋找相符項目，或者也使用暱稱。
  
    
    
 **true** 為使用暱稱；否則為 **false**。預設值為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

布林值，指定是否使用查詢字詞的注音形式來尋找相符項目。
  
    
    
 **true** 為使用注音形式；否則為 **false**。預設值為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

布林值，指定查詢是否使用快速查詢語言 (FQL)。
  
    
    
 **true** 則查詢為 FQL 查詢；否則為 **false**。預設值為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HithighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

當屬性值符合使用者輸入的搜尋字詞時，要在搜尋結果摘要中醒目提示的屬性。若是 **GET** 要求，在包含逗號分隔清單的屬性字串中指定。若是 **POST** 要求，則以字串陣列指定。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlightedProperties' :  {
    'results' : [
         'Title'   
    ]
}
}
```


### BypassResultTypes
<a name="bk_BypassResultTypes"> </a>

布林值，指定是否對查詢執行結果類型處理。
  
    
    
 **true** 為執行結果類型處理；否則為 **false**。預設值為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

布林值，指定是否傳回查詢的首選結果。
  
    
    
 **true** 為傳回首選；否則為 **false**。只有在 **EnableQueryRules** 設為 **true** 才能使用此參數，否則會加以忽略。預設值為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessBestBets' : 'true',
'EnableQueryRules' : 'true'
}
```


### ClientType
<a name="bk_ClientType"> </a>

發出查詢的用戶端類型。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

送出搜尋查詢的使用者 GUID。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

搜尋結果頁面的 URL。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

識別查詢的自訂標記。您可以指定以分號隔開的多個查詢標記。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Properties
<a name="bk_Properties"> </a>

查詢的其他屬性。 **GET** 要求僅支援字串值。 **POST** 要求支援所有型別的值。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Properties' : {
     'results' : [
          {
               'Name' : 'sampleBooleanProperty',
               'Value' :
               {
                    'BoolVal' : 'True',
                    'QueryPropertyValueTypeIndex' : 3
               }
          },
          {
               'Name' : 'sampleIntProperty',
               'Value' : 
               {
                    'IntVal' : '1234',
                    'QueryPropertyValueTypeIndex' : 2
               }
          }
     ]
}
}
```


> **注意事項**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) 指定屬性類型，每個類型都有特定的索引值。
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

布林值，指定是否對查詢啟用查詢規則。
  
    
    
 **true** 為啟用查詢規則；否則為 **false**。預設值為 **true**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

重新排列搜尋結果的特殊規則。這些規則可以指定符合特定條件的文件在結果中排名較高或較低。只有當搜尋結果是以排名排序時才適用這個屬性。這個屬性必須使用 **POST** 要求，無法用於 **GET** 要求。
  
    
    
在下列範例中， _MatchType_ 指的是 [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) 。在下列範例中， `'MatchType' : '0'` 指定 [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) 。
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ReorderingRules' :  {
    'results' : [
         {
             'MatchValue' : '<someValue>',
             'Boost' : '10',
             'MatchType' : '0'
         }
    ]
}
}
```


### ProcessPersonalFavorites
<a name="bk_ProcessPersonalFavorites"> </a>

布林值，指定是否在搜尋結果中傳回個人我的最愛。
  
    
    
 **true** 傳回個人我的最愛；否則為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

Queryparametertemplate.xml 檔案的位置。這個檔案用來啟用匿名使用者進行搜尋 REST 查詢。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

在搜尋結果中顯示命中項目醒目提示的屬性數目。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

布林值，指定是否可以排序命中項目醒目提示屬性。
  
    
    
 **true** 為啟用排序規則；否則為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

用來判斷如何摺疊個別搜尋結果的 Managed 屬性。如果結果符合任何一個摺疊規格則會摺疊成一個或指定數目的結果。在單一摺疊規格中，如果結果的屬性符合該摺疊規格的所有個別屬性，結果就會被摺疊。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

布林值，指定是否排序搜尋結果。
  
    
    
 **true** 為使用 _SortList_ 排序搜尋結果，如果 _SortList_ 是空的則依據排名。 **false** 則不排序結果。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

布林值，指定是否在交錯式結果表格的 **BlockRankLog** 屬性中傳回區塊排名記錄資訊。區塊排名記錄包含區塊分數的文字資訊以及已刪除重複項目的文件。
  
    
    
 **true** 傳回區塊排名記錄資訊；否則為 **false**。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

使用者介面的地區設定識別碼 (LCID) (請參閱 [Microsoft 指派的地區設定識別碼](http://msdn.microsoft.com/zh-tw/goglobal/bb964664.aspx))。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

要在搜尋結果產生的命中項目醒目提示摘要中顯示的慣用字元數。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

要在搜尋結果產生的命中項目醒目提示摘要中顯示的最大字元數。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

要在搜尋結果的結果摘要中顯示的字元數。
  
    
    
 **範例 GET 要求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **範例 POST 要求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## 啟用匿名搜尋 REST 查詢
<a name="bk_AnonymousREST"> </a>

您可以設定搜尋以支援來自匿名使用者的搜尋 REST 查詢。網站管理員可以使用 queryparametertemplate.xml 檔案，決定要公開哪些查詢參數給匿名使用者。本章節說明如何設定網站以啟用匿名存取，以及建立 queryparametertemplate.xml 檔案。
  
    
    

### 若要啟用匿名搜尋 REST 查詢


1. 在 Web 應用程式和發佈網站中啟用匿名存取。如需如何執行這項操作的詳細資訊，請參閱  [TechNet](http://technet.microsoft.com/zh-tw/) 上的 [在 SharePoint 2013 中管理 Web 應用程式的權限原則](http://technet.microsoft.com/zh-tw/library/ff608071.aspx)和 [在 SharePoint 2013 中規劃使用者驗證方法](http://technet.microsoft.com/zh-tw/library/cc262350.aspx)。
    
  
2. 新增名為 QueryPropertiesTemplate 的新文件庫至發佈網站。
    
  
3. 建立名為 queryparametertemplate.xml 的 XML 檔案，並將下列 XML 複製到檔案中。
    
  ```XML
  
<QueryPropertiesTemplate xmlns="http://www.microsoft.com/sharepoint/search/KnownTypes/2008/08" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <QueryProperties i:type="KeywordQueryProperties">
        <EnableStemming>true</EnableStemming>
        <FarmId>FarmID</FarmId>
        <IgnoreAllNoiseQuery>true</IgnoreAllNoiseQuery>
        <KeywordInclusion>AllKeywords</KeywordInclusion>
        <SiteId>SiteID</SiteId>
        <SummaryLength>180</SummaryLength>
        <TrimDuplicates>true</TrimDuplicates>
        <WcfTimeout>120000</WcfTimeout>
        <WebId>WebID</WebId>
        <Properties xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a:KeyValueOfstringanyType>
                <a:Key>_IsEntSearchLicensed</a:Key>
                <a:Value i:type="b:boolean" xmlns:b="http://www.w3.org/2001/XMLSchema">true</a:Value>
            </a:KeyValueOfstringanyType>
            <a:KeyValueOfstringanyType>
                <a:Key>EnableSorting</a:Key>
                <a:Value i:type="b:boolean" xmlns:b="http://www.w3.org/2001/XMLSchema">true</a:Value>
            </a:KeyValueOfstringanyType>
            <a:KeyValueOfstringanyType>
                <a:Key>MaxKeywordQueryTextLength</a:Key>
                <a:Value i:type="b:int" xmlns:b="http://www.w3.org/2001/XMLSchema">4096</a:Value>
            </a:KeyValueOfstringanyType>
            <a:KeyValueOfstringanyType>
                <a:Key>TryCache</a:Key>
                <a:Value i:type="b:boolean" xmlns:b="http://www.w3.org/2001/XMLSchema">true</a:Value>
            </a:KeyValueOfstringanyType>
        </Properties>
        <PropertiesContractVersion>15.0.0.0</PropertiesContractVersion>
        <EnableFQL>false</EnableFQL>
        <EnableSpellcheck>Suggest</EnableSpellcheck>
        <EnableUrlSmashing>true</EnableUrlSmashing>
        <IsCachable>false</IsCachable>
        <MaxShallowRefinementHits>100</MaxShallowRefinementHits>
        <MaxSummaryLength>185</MaxSummaryLength>
        <MaxUrlLength>2048</MaxUrlLength>
        <SimilarType>None</SimilarType>
        <SortSimilar>true</SortSimilar>
        <TrimDuplicatesIncludeId>0</TrimDuplicatesIncludeId>
        <TrimDuplicatesKeepCount>1</TrimDuplicatesKeepCount>
    </QueryProperties>
    <WhiteList xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a:string>RowLimit</a:string>
        <a:string>SortList</a:string>
        <a:string>StartRow</a:string>
        <a:string>RefinementFilters</a:string>
        <a:string>Culture</a:string>
        <a:string>RankingModelId</a:string>
        <a:string>TrimDuplicatesIncludeId</a:string>
        <a:string>ReorderingRules</a:string>
        <a:string>EnableQueryRules</a:string>
        <a:string>HiddenConstraints</a:string>
        <a:string>QueryText</a:string>
        <a:string>QueryTemplate</a:string>
    </WhiteList>
</QueryPropertiesTemplate>
  ```

4. 使用您伺服器陣列、網站及發佈網站集合的值，更新  _SiteId_、 _FarmId_ 和 _WebId_ 元素。
    
  
5. 儲存 queryparametertemplate.xml 至 QueryPropertiesTemplate 文件庫。
    
  
6. 新增  _QueryTemplatePropertiesUrl_ 參數至搜尋 REST 呼叫，指定spfile://webroot/queryparametertemplate.xml 為值。
    
  

### Queryparametertemplate.xml 檔案

Queryparametertemplate.xml 檔案中的主要元素為：
  
    
    

- **QueryProperties** 元素
  
    
    
包含序列化的  [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) 物件。
    
  
- **WhiteList** 元素
  
    
    
包含允許匿名使用者設定的查詢屬性清單。
    
  
送出匿名搜尋 REST 查詢時，會使用 **QueryProperties** 元素中指定的內容來建構查詢物件。然後從傳入查詢將 Whitelist 中列出的所有屬性複製至新建構的查詢物件。
  
    
    

## 在本章節中
<a name="bk_AnonymousREST"> </a>


-  [擷取使用搜尋 REST 服務的查詢建議](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## 其他資源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中搜尋](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013：從 SharePoint 相關應用程式使用搜尋 REST 服務](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [適用於開發人員的 SharePoint 2013 搜尋中新功能](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [使用 SharePoint 2013 其他服務的程式設計](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

