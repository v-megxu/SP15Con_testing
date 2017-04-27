---
title: SharePoint 2013 検索クエリ API を使用する
ms.prod: SHAREPOINT
ms.assetid: ae9d73ed-1140-430b-9287-01dbbe8ae7d1
---



# SharePoint 2013 検索クエリ API を使用する
SharePoint 2013 で提供されるクエリ API について説明します。クエリ API を使用すると検索機能をカスタム ソリューションやカスタム アプリケーションに追加することができます。 
## SharePoint 2013 クエリ API
<a name="bk_QueryAPIs"> </a>

SharePoint 2013 の検索 では、さまざまなクエリ API が利用でき、さまざまな方法で検索結果にアクセスすることができます。そのため、さまざまなカスタム ソリューション タイプで検索結果を返すことができます。
  
    
    
以前のバージョンの SharePoint で提供されていたサーバー オブジェクト モデルに加え、SharePoint 2013 の検索 では以下も利用できます。
  
    
    

- クライアント オブジェクト モデル (CSOM)
    
  
- JavaScript オブジェクト モデル (JSOM)
    
  
- REST (Representational State Transfer) サービス
    
  
表 1 に、検索クエリのプログラムに使用できる API およびサーバーのソース ファイルへのパスを示します。
  
    
    

**表 1. 検索 API**


|**API 名**|**クラス ライブラリまたはスキーマとパス**|
|:-----|:-----|
|.NET CSOM  <br/> |Microsoft.SharePoint.Client.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|Silverlight CSOM  <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|JavaScript CSOM  <br/> |SP.search.js          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|REST サービス エンドポイント  <br/> |http://server/_api/search/query          http://server/_api/search/suggest  <br/> |
|サーバー オブジェクト モデル  <br/> |Microsoft.Office.Server.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   
SharePoint 2013開発のベスト プラクティスとして、可能な限りクライアント API を使用してください。クライアント API には .NET、Silverlight、Phone、および JavaScript クライアント オブジェクト モデルと、REST サービスが含まれています。SharePoint 2013の API およびその使用に関する詳細については、 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)を参照してください。
  
    
    

### .NET クライアント オブジェクト モデルを使用したクエリ
<a name="bk_QueryNETcsom"> </a>

SharePoint 2013 の検索 オンライン、社内設置型、モバイル開発で検索結果にアクセスできるようにするクライアント オブジェクト モデル (CSOM) が含まれています。SharePoint 2013 の検索 の CSOM は SharePoint 2013 の CSOM 上に構築されます。そのため、クライアント コードは最初に SharePoint 2013 の CSOM にアクセスしてから、SharePoint 2013 の検索 の CSOM にアクセスする必要があります。SharePoint CSOM の詳細については、「 [マネージ クライアント オブジェクト モデル](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)」を参照してください。CSOM へのエントリ ポイントである  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) クラスの詳細については、「 [中心的オブジェクトであるクライアント コンテキスト](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)」を参照してください。
  
    
    
.NET マネージ CSOM の場合は、 **ClientContext** インスタンス (Microsoft.SharePoint.Client.dll の [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) 名前空間にある) を取得します。そして、Microsoft.SharePoint.Search.Client.dll の [Microsoft.SharePoint.Search.Client.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Search.Client.Query.aspx) 名前空間の中のオブジェクト モデルを使用します。
  
    
    
以下に基本的な例を示します。
  
    
    



```cs

using (ClientContext clientContext = new ClientContext("http://<serverName>/sites/<siteCollectionPath>"))
{
    KeywordQuery keywordQuery = new KeywordQuery(clientContext);
    keywordQuery.QueryText = "SharePoint";
    SearchExecutor searchExecutor = new SearchExecutor(clientContext);
    ClientResult<ResultTableCollection> results = searchExecutor.ExecuteQuery(keywordQuery);
    clientContext.ExecuteQuery();
}
```

サンプルをダウンロードする場合は、SharePoint MVP である  [Corey Roth](http://mvp.microsoft.com/ja-jp/mvp/Corey%20Roth-4029260) 氏が投稿したコード サンプル: [SharePoint 2013: マネージ クライアント オブジェクト モデルを使用したクエリ検索](http://code.msdn.microsoft.com/Query-Search-with-the-649f1bc1) を参照してください。
  
    
    

### JavaScript クライアント オブジェクト モデルを使用したクエリ
<a name="bk_QueryJSOM"> </a>

JavaScript CSOM の場合は、 [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) インスタンスを取得し、SP.Search.js ファイル内のオブジェクト モデルを使用します。
  
    
    
以下に基本的な例を示します。
  
    
    



```

var clientContext = new SP.ClientContext("<serverRelativeUrl>");
var contextSite = clientContext.get_site();
var keywordQuery = new Microsoft.SharePoint.Client.Search.Query.KeywordQuery(clientContext); 
keywordQuery.set_queryText("SharePoint"); 
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(clientContext);  
var results = searchExecutor.executeQuery(keywordQuery); 
context.executeQueryAsync(onQuerySuccess, onQueryError);
```

サンプルをダウンロードする場合は、SharePoint MVP である  [Corey Roth](http://mvp.microsoft.com/ja-jp/mvp/Corey%20Roth-4029260) 氏が投稿したコード サンプル: [SharePoint 2013: JavaScript クライアント オブジェクト モデルを使用したクエリ検索](http://code.msdn.microsoft.com/SharePoint-2013-Querying-a629b53b) を参照してください。
  
    
    

### REST サービスを使用したクエリ
<a name="bk_QueryREST"> </a>

SharePoint 2013 には、REST Web 要求をサポートする任意の技術を使用して、クライアント アプリケーションから SharePoint 2013 検索サービスに対するクエリをリモートで実行できる REST サービスが含まれます。この検索 REST サービスでは 2 つのエンドポイント ( **query** と **suggest**) が公開され、 **GET** および **POST** 操作の両方がサポートされます。結果は XML または JavaScript Object Notation (JSON) 形式のどちらかで返されます。
  
    
    
このサービスのアクセス ポイントは  `http://server/_api/search/` です。また、 `http://server/site/_api/search/` のように URL 内でサイトを指定することもできます。検索サービスはサイト コレクション全体から結果を返すため、どちらの方法でサービスにアクセスしても同じ結果が返されます。
  
    
    
詳細については、「 [SharePoint 検索 REST API の概要](sharepoint-search-rest-api-overview.md)」および「 [検索 REST サービスを使用したクエリ候補の取得](retrieving-query-suggestions-using-the-search-rest-service.md)」を参照してください。
  
    
    

### .NET サーバー オブジェクト モデルを使用したクエリ
<a name="bk_QuerySOM"> </a>

サーバー オブジェクト モデルを使用するアプリケーションは、SharePoint 2013 を実行するサーバー上で直接実行される必要があります。検索クエリ サーバー オブジェクト モデルは  [Microsoft.Office.Server.Search.Query](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.aspx) 名前空間にあり、これは Microsoft.Office.Server.Search.dll にあります。
  
    
    
SharePoint Server 2010 では、 [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.KeywordQuery.aspx) クラスを使用してクエリを定義してから、 [Execute()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.Execute.aspx) メソッドを呼び出してクエリを送信していました。SharePoint 2013 では、 **Execute** メソッドが廃止されたため (引き続き使用することは可能)、代わりに [SearchExecutor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.aspx) クラスを使用する必要があります。クエリを送信するには、 [ExecuteQuery()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.ExecuteQuery.aspx) メソッドを呼び出して、その中で **KeywordQuery** クラスのインスタンスを渡します。
  
    
    
以下に基本的な例を示します。
  
    
    



```cs

using (SPSite siteCollection = new SPSite("<serverRelativeUrl>"))
{
    KeywordQuery keywordQuery = new KeywordQuery(siteCollection);
    keywordQuery.QueryText = "SharePoint";
    SearchExecutor searchExecutor = new SearchExecutor(); 
    ResultTableCollection resultTableCollection = searchExecutor.ExecuteQuery(keywordQuery); 
    resultTableCollection = resultTableCollection.Filter("TableType", KnownTableTypes.RelevantResults); 
    ResultTable resultTable = resultTableCollection.FirstOrDefault(); 
    DataTable dataTable = resultTable.Table; 
}
```

サンプルをダウンロードする場合は、SharePoint MVP である  [Corey Roth](http://mvp.microsoft.com/ja-jp/mvp/Corey%20Roth-4029260) 氏が投稿したコード サンプル: [SharePoint 2013: KeywordQuery クラスを使用したクエリ検索](http://code.msdn.microsoft.com/Query-Search-with-the-372139b5) を参照してください。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 で検索クエリを作成する](building-search-queries-in-sharepoint-2013.md)
    
  
-  [SharePoint 検索 REST API の概要](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013: SharePoint 用アプリから検索 REST サービスを使用する](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  

  
    
    
