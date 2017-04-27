---
title: SharePoint Search REST API 概述
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# SharePoint Search REST API 概述
使用 SharePoint Server 2013 中的搜索 REST 服务以及任何支持 REST web 请求的技术向客户端和移动应用程序添加搜索功能。
## 使用搜索 REST 服务进行查询
<a name="bk_queryrest"> </a>

SharePoint 2013 中的搜索功能包括一个搜索 REST 服务，可用于通过任何支持 REST Web 请求的技术向您的客户端和移动应用程序添加搜索功能。您可以使用搜索 REST 服务在 SharePoint 外接程序、远程客户端应用程序、移动应用程序以及其他应用程序中提交关键字查询语言 (KQL) 或 FAST 查询语言 (FQL) 查询。
  
    
    
搜索 REST 服务支持 HTTP **POST** 和 HTTP **GET** 请求。
  
    
    

### GET 请求

为针对搜索 REST 服务的查询 **GET** 请求构建 URI，如下所示：
  
    
    
 `/_api/search/query`
  
    
    
对于 **GET** 请求，您可以在 URL 中指定查询参数。您可以通过以下两种方式来构建 **GET** 请求 URL：
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### POST 请求

您可以针对搜索 REST 服务为查询 **POST** 请求构建 URI，如下所示：
  
    
    
 `/_api/search/postquery`
  
    
    
对于 **POST** 请求，您可以通过 JavaScript 对象表示法 (JSON) 格式来传递请求中的查询参数。
  
    
    
搜索 REST 服务的 HTTP **POST** 版本支持 HTTP **GET** 版本支持的所有参数。然而，有些参数具有不同的数据类型，如表 1 所述。
  
    
    

**表 1. 对于 POST 参数具有不同数据类型的查询参数**


|**参数**|**数据类型**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HithighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Properties](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
在下列场景中使用 **POST** 请求：
  
    
    

- 当要超出 **GET** 请求的 URL 长度限制时。
    
  
- 无法指定简单 URL 中的查询参数时。例如，如果您必须传递包含一个复杂类型数组的参数值或者逗号分隔的字符串时，则在构建 **POST** 请求时，您会获得更高的灵活性。
    
  
- 当使用  [ReorderingRules](#bk_ReorderingRules) 参数时，因为只有 **POST** 请求支持它。
    
  

## 通过搜索 REST 服务使用查询参数
<a name="bk_UsingQueryParams"> </a>

当您调用搜索 REST 服务时，您会为请求指定查询参数。SharePoint 2013 中的搜索功能使用这些查询参数来构建搜索查询。对于 **GET** 请求，您可以在 URL 中指定查询参数。对于 **POST** 请求，您可以在正文中使用 JavaScript 对象表示法 (JSON) 格式传递查询参数。
  
    
    
以下各部分介绍了一些查询参数，您可以使用搜索 REST 服务通过它们来提交搜索查询。
  
    
    

### QueryText 参数

一个包含搜索查询文本的字符串。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

一个字符串，它包含可以替换查询文本的文本，是查询转换的一部分。
  
    
    
 **示例 GET 请求**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:johndoe'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

一个布尔值，它指定返回给结果块的结果表格中是否混有返回给原始查询的结果表格。
  
    
    
 **true** 表示混合 ResultTables；否则，为 **false**。默认值为 **true**。
  
    
    
只有当您要提供自己的隔行扫描实现时，才可更改此值。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

用于执行搜索查询的结果源 ID。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

用于查询的排名模型 ID。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

包含在返回的搜索结果中的第一行。当您想实现搜索结果分页时，可以使用此参数。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

搜索结果中返回的总体行数的最大值。相比于  _RowsPerPage_， _RowLimit_ 是返回的总体行数的最大值。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

每页返回行数的最大值。相比于  _RowLimit_， _RowsPerPage_ 指的是每页返回行数的最大值，在要实现搜索结果分页时常会用到它。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

在搜索结果中返回的托管属性。若要返回托管属性，请在搜索架构中将该属性的可检索标记设置为 **true**。
  
    
    
对于 **GET** 请求，可以在包含逗号分隔属性列表的字符串中指定 _SelectProperties_ 参数。对于 **POST** 请求，可以将 _SelectProperties_ 参数指定为一个字符串数组。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **示例 POST 请求**
  
    
    



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


### 区域性
<a name="bk_Culture"> </a>

查询的区域设置 ID (LCID)（请参阅  [Microsoft 分配的区域设置 ID](http://msdn.microsoft.com/zh-cn/goglobal/bb964664.aspx)）。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

发出细化查询时使用的一组细化筛选器。对于 **GET** 请求，会将 _RefinementFilters_ 参数指定为一个 FQL 筛选器。对于 **POST** 请求，会将 _RefinementFilters_ 参数指定为一个 FQL 筛选器数组。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **示例 POST 请求**
  
    
    



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

在搜索结果中返回的一组精简。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **示例 POST 请求**
  
    
    



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

查询中追加的附加查询词。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

属性列表，搜索结果据此进行排序。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **示例 POST 请求**
  
    
    



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

一个布尔值，它指定是否启用词干。
  
    
    
如果启用词干，在为 **true** enabled；否则，为 **false**。默认值是 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

一个布尔值，它指定是否将重复项从结果中删除。
  
    
    
 **true** 表示删除重复项；否则，为 **false**。默认值为 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

查询请求超时前的时长（以毫秒为单位）。默认值是 30000。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

一个布尔值，它指定是使用搜索查询中的精确条件来查找匹配，还是使用昵称。
  
    
    
如果使用昵称，则为 **true**；否则，为 **false**。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

一个布尔值，它指定是否使用查询词的语音形式来查找匹配。
  
    
    
如果使用语音形式，就为 **true**；否则，为 **false**。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

一个布尔值，它指定查询是否使用 FAST 查询语言 (FQL)。
  
    
    
如果查询是 FQL 查询，则为 **true**；否则，为 **false**。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HithighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

当属性值与用户输入的搜索条件匹配时要在搜索结果摘要中突出显示的属性。对于 **GET** 请求，可以在包含逗号分隔属性列表的字符串中指定。对于 **POST** 请求，可以指定为一个字符串数组。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **示例 POST 请求**
  
    
    



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

一个布尔值，它指定是否对查询执行结果类型处理。
  
    
    
 **true** 表示执行结果类型处理；否则，为 **false**。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

一个布尔值，它指定是否对查询返回最佳匹配结果。
  
    
    
 **true** 表示返回最佳匹配；否则，为 **false**。只有在 **EnableQueryRules** 设置为 **true** 时，才使用此参数；否则会忽略此参数。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **示例 POST 请求**
  
    
    



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

发出查询的客户端类型。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

提交搜索查询的用户对应的 GUID
  
    
    
 **示例 GET 请求**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

搜索结果页面的 URL。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

标识查询的自定义标签。您可以指定多个查询标签，用分号分隔。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Properties
<a name="bk_Properties"> </a>

其他用于查询的属性。 **GET** 请求仅支持字符串值。 **POST** 请求支持所有类型的值。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **示例 POST 请求**
  
    
    



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


> **注释**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) 指定属性的类型；每种类型均有特定的索引值。
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

一个布尔值，它指定是否对查询启用查询规则。
  
    
    
 **true** 表示启用查询规则；否则，为 **false**。默认值为 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

用于对搜索结果重新排序的特殊规则。这些规则可以指定匹配某些条件的文档在结果中排序的高低。此属性仅适用于搜索结果基于排名进行排序的情况。必须对此属性使用 **POST** 请求；该属性在 **GET** 请求中无效。
  
    
    
在下面的示例中， _MatchType_ 是指 [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) 。在下面的示例中， `'MatchType' : '0'` 指定 [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) 。
  
    
    
 **示例 POST 请求**
  
    
    



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

一个布尔值，它指定是否在搜索结果中返回个人收藏夹。
  
    
    
 **true** 表示返回个人收藏夹；否则，为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

queryparametertemplate.xml 文件的位置。此文件可用于使匿名用户进行搜索 REST 查询。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

在搜索结果中突出显示的属性数量。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

一个布尔值，它指定是否可对突出显示的属性进行排序。
  
    
    
 **true** 表示启用排序规则；否则，为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

用于确定如何折叠单个搜索结果的托管属性。如果它们与任意单个折叠规范匹配，搜索结果就会折叠为一个或指定数量的结果。在单个折叠规范中，如果结果属性与折叠规范中所有的单个属性匹配，则这些结果就会折叠起来。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

一个布尔值，它指定是否对搜索结果排序。
  
    
    
I **true** 表示使用 _SortList_ 对搜索结果排序，或者，如果 _SortList_ 为空，则按排名排序。 **false** 表示保持结果是无序状态。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

一个布尔值，它指定是否在隔行扫描结果表格的 **BlockRankLog** 属性中返回块排名日志信息。块排名日志中包含有关块分数和非重复文档的文字信息。
  
    
    
 **true** 表示返回块排名日志信息；否则，为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

用户界面的区域设置标识符 (LCID) （请参阅  [Microsoft 分配的区域设置 ID](http://msdn.microsoft.com/zh-cn/goglobal/bb964664)）。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

要显示在为搜索结果生成的突出显示摘要中的字符首选数量。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

要显示在为搜索结果生成的突出显示摘要中的字符最大数量。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

要显示在搜索结果的结果摘要中的字符的数量。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **示例 POST 请求**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## 启用匿名搜索 REST 查询
<a name="bk_AnonymousREST"> </a>

您可以将搜索配置为支持匿名用户的搜索 REST 查询。网站管理员可以使用 queryparametertemplate.xml 文件决定向匿名用户显示哪些查询参数。本节介绍如何将您的网站配置为启用匿名访问，以及如何创建 queryparametertemplate.xml 文件。
  
    
    

### 启用匿名搜索 REST 查询


1. 在 Web 应用程序和发布网站上启用匿名访问。有关如何操作的详细信息，请参阅  [TechNet](http://technet.microsoft.com/zh-cn/) 上的 [在 SharePoint 2013 中管理 Web 应用程序的权限策略](http://technet.microsoft.com/zh-cn/library/ff608071.aspx)和  [在 SharePoint 2013 中规划用户身份验证方法](http://technet.microsoft.com/zh-cn/library/cc262350.aspx)。
    
  
2. 将一个新的名为 QueryPropertiesTemplate 的文档库添加到发布网站上。
    
  
3. 创建一个名为 queryparametertemplate.xml 的 XML 文件，并将以下 XML 复制到文件中。
    
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

4. 使用您的场、网站和发布网站集的值更新  _SiteId_、 _FarmId_ 和 _WebId_ 元素。
    
  
5. 将 queryparametertemplate.xml 保存到 QueryPropertiesTemplate 文档库中。
    
  
6. 将  _QueryTemplatePropertiesUrl_ 参数添加到您的搜索 REST 调用中，将spfile://webroot/queryparametertemplate.xml 指定为值。
    
  

### queryparametertemplate.xml 文件

queryparametertemplate.xml 文件中的主要元素如下：
  
    
    

- **QueryProperties** 元素
  
    
    
包含一个序列化的  [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) 对象。
    
  
- **WhiteList** 元素
  
    
    
包含允许匿名用户设置的查询属性列表。
    
  
提交匿名搜索 REST 查询时，系统将使用 **QueryProperties** 元素中指定的内容构建查询对象。然后，允许名单中列出的所有属性将从传入查询复制到新构建的查询对象中。
  
    
    

## 本节内容
<a name="bk_AnonymousREST"> </a>


-  [使用搜索 REST 服务检索查询建议](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的搜索](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013：从 SharePoint 相关应用程序使用搜索 REST 服务](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [SharePoint 2013 搜索功能中面向开发人员的新增内容](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

