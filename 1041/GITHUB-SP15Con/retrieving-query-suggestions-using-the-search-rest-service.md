---
title: 検索 REST サービスを使用したクエリ候補の取得
ms.prod: SHAREPOINT
ms.assetid: a64c5bec-64a8-4752-9c72-433d1c864aed
---


# 検索 REST サービスを使用したクエリ候補の取得
クライアントおよびモバイル アプリケーションから、検索 REST サービスを使用して、SharePoint 2013 の検索からクエリ候補を取得できる方法を説明します。
クエリ候補は、検索候補とも呼ばれ、ユーザーが既に検索したことがあり、クエリを入力すると表示される、つまり "提案される" 語句です。SharePoint 2013 の検索を使用して、クエリ前とクエリ後の候補を有効にすることができます。これらの候補は、ユーザーがクエリを入力すると、[検索] ボックスの下にリストで表示されます。クエリ候補の詳細とそれらを有効にする方法については、「 [SharePoint Server 2013 でクエリ候補を管理する](http://technet.microsoft.com/ja-jp/library/jj721441.aspx)」を参照してください。
  
    
    


## 検索 REST サービスの Suggest エンドポイント
<a name="bk_SuggestEndpoint"> </a>

検索 REST サービスには、 **Suggest** エンドポイントが含まれ、これは REST Web 要求をサポートする任意のテクノロジで使用でき、クライアントまたはモバイル アプリケーションから、検索システムによってクエリに対して生成されるクエリ候補を取得できます。
  
    
    
検索 REST サービスの **Suggest** エンドポイントへの **GET** 要求の URI は次のとおりです。
  
    
    
 `/_api/search/suggest`
  
    
    
クエリ候補パラメータは URL に指定します。要求 URL は次の 2 つの方法で作成できます。
  
    
    


  
    
    
>  `http://server/_api/search/suggest?parameter=value&amp;parameter=value`
    
  

  
    
    
>  `http://server/_api/search/suggest(parameter=value&amp;parameter=value)`
    
  

> **メモ**
> 検索 REST サービスでは、 **Suggest** エンドポイントへの匿名要求をサポートしていません。
  
    
    


## クエリ候補パラメーター
<a name="bk_SuggestParameters"> </a>

次のセクションで、 **Suggest** エンドポイントに使用できるパラメーターについて説明します。
  
    
    

### Querytext

検索クエリのテキストを含む文字列。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'
  
    
    

### iNumberOfQuerySuggestions

取得するクエリ候補の数。ゼロ (0) より大きい必要があります。既定値は 5 です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;inumberofquerysuggestions=3
  
    
    

### iNumberOfResultSuggestions

取得する個人用の結果の数。ゼロ (0) より大きい必要があります。既定値は 5 です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;inumberofresultsuggestions=4
  
    
    

### fPreQuerySuggestions

クエリ前候補を取得するか、クエリ後候補を取得するかを指定するブール値。クエリ前候補を返す場合は **true**、それ以外は **false** です。既定値は **false** です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fprequerysuggestions=true
  
    
    

### fHitHighlighting

ヒットしたクエリ候補をハイライト表示するか、太字で書式設定するかを指定するブール値。指定したクエリの用語に一致する、返されるクエリ候補の用語を太字で書式設定する場合は **true**、それ以外は **false** です。既定値は **true** です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fhithighlighting=false
  
    
    

### fCapitalizeFirstLetters

返されるクエリ候補の各用語の先頭の文字を大文字にするかどうかを指定するブール値。各用語の先頭の文字を大文字にする場合は **true**、それ以外は **false** です。既定値は **false** です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fcapitalizefirstletters=false
  
    
    

### カルチャ

クエリのロケール ID (LCID) ( [Microsoft によって割り当てられたロケール ID](http://msdn.microsoft.com/ja-jp/goglobal/bb964664.aspx) を参照してください)。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;culture=1044
  
    
    

### EnableStemming

ステミングを有効にするかどうかを指定するブール値。ステミングを有効にする場合は **true**、それ以外は **false**。既定値は **true** です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;enablestemming=false
  
    
    

### ShowPeopleNameSuggestions

返されるクエリ候補に人名を含めるかどうかを指定するブール値。返されるクエリ候補に人名を含める場合は **true**、それ以外は **false** です。既定値は **true** です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;showpeoplenamesuggestions=false
  
    
    

### EnableQueryRules

このクエリのクエリ ルールを有効にするかどうかを指定するブール値。クエリ ルールを有効にする場合は **true**、それ以外は **false** です。既定値は **true** です。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    

### fPrefixMatchAllTerms

前方一致のクエリ候補を返すかどうかを指定するブール値。前方一致に基づいてクエリ候補を返す場合は **true**、クエリ候補がクエリ全文に一致する必要がある場合は **false**。
  
    
    
 **サンプル GET 要求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fprefixmatchallterms=false
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 検索 REST API の概要](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013 の検索](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013: SharePoint 用アプリから検索 REST サービスを使用する](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [開発者向けの SharePoint 2013 検索の新機能](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

