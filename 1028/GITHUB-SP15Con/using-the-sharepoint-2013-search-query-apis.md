---
title: 使用 SharePoint 2013 搜尋查詢 API
ms.prod: SHAREPOINT
ms.assetid: ae9d73ed-1140-430b-9287-01dbbe8ae7d1
---



# 使用 SharePoint 2013 搜尋查詢 API
了解 SharePoint 2013 所提供的查詢 API，可讓您將搜尋功能加入至自訂方案和應用程式中。 
## SharePoint 2013 查詢 API
<a name="bk_QueryAPIs"> </a>

在 SharePoint 2013 中搜尋 提供多個查詢 API，提供您許多存取搜尋結果的方法，讓您可以在各種自訂方案類型中傳回搜尋結果。
  
    
    
除了舊版 SharePoint 已提供的伺服器物件模型，在 SharePoint 2013 中搜尋 也提供下列方法：
  
    
    

- 用戶端物件模型 (CSOM)
    
  
- JavaScript 物件模型 (JSOM)
    
  
- 代表性狀態傳輸 (REST) 服務
    
  
表 1 顯示的 API 可用來以程式撰寫搜尋查詢以及伺服器上原始檔案的路徑。
  
    
    

**表 1。搜尋 API**


|**API 名稱**|**類別庫或結構描述和路徑**|
|:-----|:-----|
|.NET CSOM  <br/> |Microsoft.SharePoint.Client.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|Silverlight CSOM  <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|JavaScript CSOM  <br/> |SP.search.js          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|REST 服務端點  <br/> |http://server/_api/search/query          http://server/_api/search/suggest  <br/> |
|伺服器物件模型  <br/> |Microsoft.Office.Server.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   
以 SharePoint 2013 開發的最佳作法而言，請盡可能使用用戶端 API。用戶端 API 包括 .NET、Silverlight、Phone 和 JavaScript 用戶端物件模型，以及 REST 服務。如需 SharePoint 2013 中 API 的詳細資訊及其使用時機，請參閱 [選擇 [設定 SharePoint 2013 中的右 API](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    

### 使用 .NET 用戶端物件模型進行查詢
<a name="bk_QueryNETcsom"> </a>

在 SharePoint 2013 中搜尋 包含的用戶端物件模型可讓您存取線上、內部部署及行動應開發的搜尋結果。在 SharePoint 2013 中搜尋 CSOM 內建於 SharePoint 2013 CSOM 上。因此，您的用戶端程式碼首先需要存取 SharePoint 2013 CSOM，接著需存取 在 SharePoint 2013 中搜尋 CSOM。如需 SharePoint CSOM 的詳細資訊，請參閱  [SharePoint 2010 Client Object Model](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)。如需做為 CSOM 進入點之  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) 類別的詳細資訊，請參閱 [Client Context as Central Object](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)。
  
    
    
對於 .NET managed CSOM，請先取得 **ClientContext** 執行個體 (位於 Microsoft.SharePoint.Client.dll 的 [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) 命名空間)，接著使用 Microsoft.SharePoint.Search.Client.dll 之 [Microsoft.SharePoint.Search.Client.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Search.Client.Query.aspx) 命名空間中的物件模型。
  
    
    
以下是一個基本範例。
  
    
    



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

若要下載範例，請參閱 SharePoint MVP  [Corey Roth](http://mvp.microsoft.com/zh-tw/mvp/Corey%20Roth-4029260) 張貼的下列程式碼範例： [SharePoint 2013：使用受管理用戶端物件模型查詢搜尋](http://code.msdn.microsoft.com/Query-Search-with-the-649f1bc1)。
  
    
    

### 使用 JavaScript 用戶端物件模型進行查詢
<a name="bk_QueryJSOM"> </a>

對於 JavaScript CSOM，請先取得  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) 執行個體，然後使用 SP.Search.js 檔案中的物件模型。
  
    
    
以下是一個基本範例。
  
    
    



```

var clientContext = new SP.ClientContext("<serverRelativeUrl>");
var contextSite = clientContext.get_site();
var keywordQuery = new Microsoft.SharePoint.Client.Search.Query.KeywordQuery(clientContext); 
keywordQuery.set_queryText("SharePoint"); 
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(clientContext);  
var results = searchExecutor.executeQuery(keywordQuery); 
context.executeQueryAsync(onQuerySuccess, onQueryError);
```

若要下載範例，請參閱 SharePoint MVP  [Corey Roth](http://mvp.microsoft.com/zh-tw/mvp/Corey%20Roth-4029260) 張貼的下列程式碼範例： [SharePoint 2013：使用 JavaScript 用戶端物件模型查詢搜尋](http://code.msdn.microsoft.com/SharePoint-2013-Querying-a629b53b)。
  
    
    

### 使用 REST 服務進行查詢
<a name="bk_QueryREST"> </a>

SharePoint 2013 包含的 REST 服務可讓您使用支援 REST Web 要求的任何技術，從遠端用戶端應用程式對 SharePoint 2013 搜尋服務執行查詢。搜尋 REST 服務會公開兩個端點 **query** 和 **suggest**，並且支援 **GET** 和 **POST** 作業。結果會以 XML 或 JavaScript Object Notation (JSON) 格式傳回。
  
    
    
以下是服務的存取點： `http://server/_api/search/`。您也可以在網站中指定 URL，如下所示： `http://server/site/_api/search/`。搜尋服務會從整個網站集合傳回結果，因此存取服務的兩個方法會傳回相同的結果。
  
    
    
如需詳細資訊，請參閱  [SharePoint 搜尋 REST API 概觀](sharepoint-search-rest-api-overview.md)和 [擷取使用搜尋 REST 服務的查詢建議](retrieving-query-suggestions-using-the-search-rest-service.md)。
  
    
    

### 使用 .NET 伺服器物件模型進行查詢
<a name="bk_QuerySOM"> </a>

要使用伺服器物件模型的應用程式必須在執行 SharePoint 2013 的伺服器上直接執行。搜尋查詢伺服器物件模型位於 Microsoft.Office.Server.Search.dll 的  [Microsoft.Office.Server.Search.Query](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.aspx) 命名空間。
  
    
    
如同 SharePoint Server 2010，使用  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.KeywordQuery.aspx) 類別來定義查詢，然後再呼叫 [Execute()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.Execute.aspx) 方法來送出查詢。在 SharePoint 2013 中 **Execute** 方法已過時，雖然仍可運作，但您應改為使用 [SearchExecutor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.aspx) 類別。若要送出查詢，請呼叫 [ExecuteQuery()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.ExecuteQuery.aspx) 方法，並在呼叫中傳遞 **KeywordQuery** 類別的執行個體。
  
    
    
以下是一個基本範例。
  
    
    



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

若要下載範例，請參閱 SharePoint MVP  [Corey Roth](http://mvp.microsoft.com/zh-tw/mvp/Corey%20Roth-4029260) 張貼的下列程式碼範例： [SharePoint 2013：使用 KeywordQuery 類別查詢搜尋](http://code.msdn.microsoft.com/Query-Search-with-the-372139b5)。
  
    
    

## 其他資源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中建立搜尋查詢](building-search-queries-in-sharepoint-2013.md)
    
  
-  [SharePoint 搜尋 REST API 概觀](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013：從 SharePoint 相關應用程式使用搜尋 REST 服務](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  

  
    
    
