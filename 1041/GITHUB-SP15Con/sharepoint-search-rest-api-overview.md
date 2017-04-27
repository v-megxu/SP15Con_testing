---
title: SharePoint 検索 REST API の概要
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# SharePoint 検索 REST API の概要
SharePoint Server 2013 の検索 REST サービスと、REST Web 要求をサポートするテクノロジを使用してクライアント アプリケーションとモバイル アプリケーションに検索機能を追加します。
## 検索 REST サービスでクエリを実行する
<a name="bk_queryrest"> </a>

SharePoint 2013 の検索 には、REST Web 要求をサポートするテクノロジを使用して、クライアントとモバイル アプリケーションに検索機能を追加するのに使用できる検索 REST サービスがあります。検索 REST サービスを使用すると、SharePoint アドイン、リモート クライアント アプリケーション、モバイル アプリケーションなどのアプリケーションで、キーワード クエリ言語 (KQL) または FAST クエリ言語 (FQL) クエリを送信できます。
  
    
    
検索 REST サービスは、HTTP **POST** 要求と HTTP **GET** 要求の両方をサポートしています。
  
    
    

### GET 要求

検索 REST サービスに対するクエリ **GET** 要求の URI を次のように作成します。
  
    
    
 `/_api/search/query`
  
    
    
 **GET** 要求については、URL でクエリ パラメーターを指定します。 **GET** 要求 URL は、次の 2 つの方法で作成できます。
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### POST 要求

検索 REST サービスに対するクエリ **POST** 要求の URI を次のように作成します。
  
    
    
 `/_api/search/postquery`
  
    
    
 **POST** 要求について、要求のクエリ パラメーターを JavaScript Object Notation (JSON) 形式で渡します。
  
    
    
検索 REST サービスの HTTP **POST** バージョンの、HTTP **GET** バージョンでサポートされているすべてのパラメーターをサポートしています。ただし、一部のパラメーターは、表 1 のようにデータ型が異なります。
  
    
    

**表 1. POST 要求のデータ型が異なるクエリ パラメーター**


|**パラメーター**|**データ型**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HithighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Properties](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
次のシナリオで **POST** 要求を使用します。
  
    
    

- **GET** 要求で、URL の長さの上限を超える場合。
    
  
- 1 つの URL でクエリ パラメーターを指定できない場合。たとえば、複合型配列またはコンマ区切りの文字列を含むパラメーター値を渡す必要がある場合、 **POST** 要求を作成する際に柔軟に対応できます。
    
  
- **POST** 要求でのみサポートされるため、 [ReorderingRules](#bk_ReorderingRules) パラメーターを使用する場合。
    
  

## 検索 REST サービスでクエリ パラメーターを使用する
<a name="bk_UsingQueryParams"> </a>

検索 REST サービスを呼び出す場合、要求にクエリ パラメーターを指定します。SharePoint 2013 の検索は、このクエリパラメーターを使用して検索クエリを作成します。 **GET** 要求の場合、URL でクエリ パラメーターを指定します。 **POST** 要求の場合、本文でJavaScript Object Notation (JSON) 形式のクエリ パラメーターを渡します。
  
    
    
以下のセクションでは、検索 REST サービスで検索クエリを送信するときに使用できるクエリ パラメーターについて説明します。
  
    
    

### QueryText パラメーター

検索クエリのテキストを含む文字列。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

クエリ変換の一環として、クエリ テキストを置き換えるテキストを含む文字列。
  
    
    
 **GET 要求の例**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:johndoe'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

結果ブロックについて返される結果テーブルを、元のクエリに対して返される結果テーブルと混合するかどうかを指定するブール値。
  
    
    
ResultTables を混合する場合は **true**、それ以外の場合は **false** です。既定値は **true** です。
  
    
    
この値を変更するのは、独自のインターリーブ実装を指定する場合のみです。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

検索クエリを実行するために使用する検索先 ID。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

クエリに使用するランキング モデルの ID。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

返される検索結果に含まれる最初の行。検索結果のページングを実装するときに、このパラメーターを使用します。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

検索結果で返される行全体の最大数。 _RowsPerPage_ とは異なり、 _RowLimit_ は、返される全体の行の最大数です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

1 ページあたりの返される行の最大数。 _RowLimit_ とは異なり、 _RowsPerPage_ は 1 ページあたりの返される行の最大数を示し、主に検索結果についてページングを実装するときに使用されます。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

検索結果で返される管理プロパティ。管理プロパティを返すには、検索スキーマのプロパティの retrievable フラグを **true** に設定します。
  
    
    
 **GET** 要求の場合、コンマ区切りのプロパティ一覧を含む文字列で、 _SelectProperties_ パラメーターを指定します。 **POST** 要求の場合、文字列配列として _SelectProperties_ パラメーターを指定します。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **POST 要求の例**
  
    
    



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

クエリのロケール ID (LCID) (「 [Microsoft が割り当てているロケール ID](http://msdn.microsoft.com/ja-jp/goglobal/bb964664.aspx)」を参照してください)。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

絞り込みクエリを発行するときに使用される絞り込みフィルターのセット。 **GET** 要求の場合、FQL フィルターとして _RefinementFilters_ パラメーターを指定します。 **POST** 要求の場合、FQL フィルターの配列として _RefinementFilters_ パラメーターを指定します。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **POST 要求の例**
  
    
    



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

検索結果で返される絞り込み条件のセット。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **POST 要求の例**
  
    
    



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

クエリに付加する追加のクエリ語。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

検索結果の並べ替えに使用するプロパティの一覧。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **POST 要求の例**
  
    
    



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

ステミングを有効にするかどうかを指定するブール値。
  
    
    
ステミングを有効にする場合は **true**、それ以外の場合は **false** です。既定値は **true** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

重複する項目を結果から削除するかどうかを指定するブール値。
  
    
    
重複する項目を削除するには **true**、それ以外の場合は **false** です。既定値は **true** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

クエリ要求がタイムアウトするまでの時間 (ミリ秒)。既定値は 30000 です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

一致を検索するときに検索クエリの正確な用語を使用するか、またはニックネームも使用するかを指定するブール値。
  
    
    
ニックネームを使用する場合は **true**、それ以外の場合は **false** です。既定値は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

一致を検索するときにクエリ用語のふりがな形式を使用するかどうかを指定するブール値。
  
    
    
ふりがな形式を使用する場合は **true**、それ以外の場合は **false** です。既定値は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

クエリに FAST クエリ言語 (FQL) を使用するかどうかを指定するブール値。
  
    
    
クエリが FQL クエリの場合は **true**、それ以外の場合は **false** です。既定値は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HithighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

プロパティ値がユーザーの入力した検索用語と一致する場合、検索結果の概要で強調表示するプロパティ。 **GET** 要求の場合、コンマ区切りのプロパティ一覧を含む文字列で指定します。 **POST** 要求の場合、文字列の配列として指定します。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **POST 要求の例**
  
    
    



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

クエリに対して、結果の型処理を実行するかどうかを指定するブール値。
  
    
    
結果の型処理を実行する場合は **true**、それ以外の場合は **false** です。既定値は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

クエリのおすすめの結果を返すかどうかを指定するブール値。
  
    
    
おすすめを返す場合は **true**、それ以外の場合は **false** です。このパラメーターが使用されるのは、 **EnableQueryRules** が **true** に設定されている場合のみです。それ以外の場合は、無視されます。既定値は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **POST 要求の例**
  
    
    



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

クエリを発行したクライアントの種類。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

検索クエリを送信したユーザーの GUID。
  
    
    
 **GET 要求の例**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

検索結果ページの URL。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

クエリを識別するカスタム タグ。複数のクエリ タグがある場合は、セミコロン区切りで指定します。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Properties
<a name="bk_Properties"> </a>

クエリの追加プロパティ。 **GET** 要求は、文字列値のみをサポートします。 **POST** 要求は、任意の型の値をサポートします。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **POST 要求の例**
  
    
    



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


> **メモ**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) は、プロパティの種類を指定します。各種類には、特定のインデックス値があります。
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

クエリのクエリ ルールを有効にするかどうかを指定するブール値。
  
    
    
クエリ ルールを有効にする場合は **true**、それ以外の場合は **false** です。既定値は **true** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

検索結果を並べ替えるための特殊なルール。このルールを使用すると、特定の条件に一致するドキュメントについて、結果のランクを上下させることができます。このプロパティは検索結果がランキングに基づいて並べ替えられる時に限り適用されます。このプロパティには、 **POST** 要求を使用する必要があります。 **GET** 要求では機能しません。
  
    
    
次の例では、 _MatchType_ は [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) を参照します。次の例では、 `'MatchType' : '0'` は [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) を指定します。
  
    
    
 **POST 要求の例**
  
    
    



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

検索結果で個人のお気に入りを返すかどうかを指定するブール値。
  
    
    
個人のお気に入りを返す場合は **true**、それ以外の場合は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

queryparametertemplate.xml ファイルの場所。このファイルは、匿名ユーザーが検索 REST クエリを実行することを許可する場合に使用されます。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

検索結果でヒットを強調表示するプロパティの数。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

ヒットが強調表示されたプロパティを並べ替えることができるかどうかを指定するブール値。
  
    
    
並べ替えのルールを有効にする場合は **true**、それ以外の場合は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

個々の検索結果の折りたたみ方法を決定するのに使用される管理プロパティ。結果が個々の折りたたみの仕様に一致する場合、1 つまたは指定した数に折りたたまれます。結果のプロパティが折りたたみ仕様のすべての個々のプロパティと一致する場合、1 つの折りたたみの仕様に結果が折りたたまれます。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

検索結果を並べ替えるかどうかを指定するブール値。
  
    
    
 _SortList_ を使用して検索結果を並べ替える場合、またはランクで _SortList_ が空の場合は **true** です。結果を並べ替えない場合は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

インターリーブされた結果テーブルの **BlockRankLog** プロパティで、ブロック ランク ログ情報を返すかどうかを指定するブール値。ブロック ランク ログには、ブロック スコアに関するテキストの情報と、重複が除去されたドキュメントが含まれます。
  
    
    
ブロック ランク ログ情報を返す場合は **true**、それ以外の場合は **false** です。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

ユーザー インターフェイスのロケール識別子 (LCID) (「 [Microsoft が割り当てているロケール ID](http://msdn.microsoft.com/ja-jp/goglobal/bb964664)」を参照してください)。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

検索結果に対して生成される、ヒットが強調表示されたサマリーに表示する優先文字数。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

検索結果に対して生成される、ヒットが強調表示されたサマリーに表示する最大文字数。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

検索結果について、結果のサマリーに表示する文字数。
  
    
    
 **GET 要求の例**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **POST 要求の例**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## 匿名検索 REST クエリを有効にする
<a name="bk_AnonymousREST"> </a>

匿名ユーザーからの検索 REST クエリをサポートするように検索を構成できます。サイト管理者は、queryparametertemplate.xml ファイルを使用して、匿名ユーザーに公開するクエリ パラメーターを指定できます。ここでは、匿名アクセスを有効にするようにサイトを構成する方法と、queryparametertemplate.xml ファイルを作成する方法について説明します。
  
    
    

### 匿名検索 REST クエリを有効にするには


1. Web アプリケーションと発行サイトで匿名アクセスを有効にします。その方法の詳細については、「 [Web アプリケーションのアクセス許可ポリシーを管理する (SharePoint 2013)](http://technet.microsoft.com/ja-jp/library/ff608071.aspx)」と「 [SharePoint 2013 でユーザー認証方法を計画する](http://technet.microsoft.com/ja-jp/library/cc262350.aspx)」( [TechNet](http://technet.microsoft.com/ja-jp/)) を参照してください。
    
  
2. QueryPropertiesTemplate という新しいドキュメント ライブラリを発行サイトに追加します。
    
  
3. queryparametertemplate.xml という名前の XML ファイルを作成し、次の XML をファイルにコピーします。
    
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

4. ファーム、Web サイト、発行サイトのコレクションの値を使用して、 _SiteId_、 _FarmId_、および  _WebId_ の各要素を更新します。
    
  
5. queryparametertemplate.xml を QueryPropertiesTemplate ドキュメント ライブラリに保存します。
    
  
6.  _QueryTemplatePropertiesUrl_ パラメーターを検索 REST の呼び出しに追加し、値としてspfile://webroot/queryparametertemplate.xml を指定します。
    
  

### queryparametertemplate.xml ファイル

queryparametertemplate.xml ファイルの主な要素は次のとおりです。
  
    
    

- **QueryProperties** 要素
  
    
    
シリアル化された  [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) オブジェクトが含まれます。
    
  
- **WhiteList** 要素
  
    
    
匿名ユーザーが設定することを許可されているクエリ プロパティの一覧が含まれます。
    
  
匿名の検索 REST クエリを送信する場合、クエリ オブジェクトは、 **QueryProperties** 要素で指定した内容を使用して作成されます。その後、ホワイトリストに表示されるすべてのプロパティが、受け取ったクエリから新しく作成されるクエリ オブジェクトにコピーされます。
  
    
    

## このセクションの内容
<a name="bk_AnonymousREST"> </a>


-  [検索 REST サービスを使用したクエリ候補の取得](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 の検索](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013: SharePoint 用アプリケーションから検索 REST サービスを使用する](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [開発者向けの SharePoint 2013 検索の新機能](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

