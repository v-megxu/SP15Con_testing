---
title: 使用 SharePoint 2013 搜索查询 API
ms.prod: SHAREPOINT
ms.assetid: ae9d73ed-1140-430b-9287-01dbbe8ae7d1
---



# 使用 SharePoint 2013 搜索查询 API
了解 SharePoint 2013 中提供的查询 API，此类 API 可让您向自定义解决方案和应用程序添加搜索功能。 
## SharePoint 2013 查询 API
<a name="bk_QueryAPIs"> </a>

SharePoint 2013 中的搜索功能 提供了几个查询 API，让您可以通过多种方式访问搜索结果，从而能够以各种自定义解决方案类型返回搜索结果。
  
    
    
除了 SharePoint 之前版本中提供的服务器对象模型，SharePoint 2013 中的搜索功能 还提供以下内容：
  
    
    

- 客户端对象模型 (CSOM)
    
  
- JavaScript 对象模型 (JSOM)
    
  
- 代表性状态传输 (REST) 服务
    
  
表 1 显示了用于对搜索查询进行编程的 API 以及服务器上源文件的路径。
  
    
    

**表 1. 搜索 API**


|**API 名称**|**类库或架构和路径**|
|:-----|:-----|
|.NET CSOM  <br/> |Microsoft.SharePoint.Client.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|Silverlight CSOM  <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|JavaScript CSOM  <br/> |SP.search.js          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|REST 服务终结点  <br/> |http://server/_api/search/query          http://server/_api/search/suggest  <br/> |
|服务器对象模型  <br/> |Microsoft.Office.Server.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   
作为 SharePoint 2013 开发中的最佳实践，在可能的时候使用客户端 API。客户端 API 包括 .NET、Silverlight、Phone 和 JavaScript 客户端对象模型，以及 REST 服务。有关 SharePoint 2013 中的 API 以及何时使用这些 API 的详细信息，请参阅 [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    

### 使用 .NET 客户端对象模型查询
<a name="bk_QueryNETcsom"> </a>

SharePoint 2013 中的搜索功能 包括一个客户端对象模型，可通过该模型访问搜索结果以进行联机、本地和移动开发。SharePoint 2013 中的搜索功能 CSOM 构建在 SharePoint 2013 CSOM 之上。因此，您的客户端代码首先需要访问 SharePoint 2013 CSOM，然后访问 SharePoint 2013 中的搜索功能 CSOM。有关 SharePoint CSOM 的详细信息，请参阅  [托管客户端对象模型](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)。有关作为 CSOM 的入口点的  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) 类的详细信息，请参阅 [作为中心对象的客户端上下文](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)。
  
    
    
对于 .NET 托管 CSOM，获取 **ClientContext** 实例（位于 Microsoft.SharePoint.Client.dll 中的 [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) 命名空间中）。然后使用 Microsoft.SharePoint.Search.Client.dll 中 [Microsoft.SharePoint.Search.Client.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Search.Client.Query.aspx) 命名空间中的对象模型。
  
    
    
以下是一个基本示例。
  
    
    



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

若要下载示例，请参阅 SharePoint MVP  [科里·罗斯](http://mvp.microsoft.com/zh-cn/mvp/Corey%20Roth-4029260)发布的以下代码示例： [SharePoint 2013：通过托管客户端对象模型查询搜索](http://code.msdn.microsoft.com/Query-Search-with-the-649f1bc1)。
  
    
    

### 使用 JavaScript 客户端对象模型查询
<a name="bk_QueryJSOM"> </a>

对于 JavaScript CSOM，获取一个  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) 实例，然后使用 SP.Search.js 文件中的对象模型。
  
    
    
以下是一个基本示例。
  
    
    



```

var clientContext = new SP.ClientContext("<serverRelativeUrl>");
var contextSite = clientContext.get_site();
var keywordQuery = new Microsoft.SharePoint.Client.Search.Query.KeywordQuery(clientContext); 
keywordQuery.set_queryText("SharePoint"); 
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(clientContext);  
var results = searchExecutor.executeQuery(keywordQuery); 
context.executeQueryAsync(onQuerySuccess, onQueryError);
```

若要下载示例，请参阅 SharePoint MVP  [科里·罗斯](http://mvp.microsoft.com/zh-cn/mvp/Corey%20Roth-4029260)发布的以下代码示例： [SharePoint 2013：通过 JavaScript 对象模型查询搜索](http://code.msdn.microsoft.com/SharePoint-2013-Querying-a629b53b)。
  
    
    

### 使用 REST 服务查询
<a name="bk_QueryREST"> </a>

SharePoint 2013 包括 REST 服务，使用该服务，您能够通过任何支持 REST Web 请求的技术从客户端应用程序对 SharePoint 2013 Search 服务执行查询。搜索 REST 服务公开两个端点： **query** 和 **suggest**，并将支持 **GET** 和 **POST** 操作。相关结果以 XML 或 JavaScript 对象表示法 (JSON) 格式返回。
  
    
    
以下是服务的访问点： `http://server/_api/search/`。您还可以以 URL 格式指定网站，格式如下： `http://server/site/_api/search/`。搜索服务从整个网站集返回结果，因此，通过这两种方法访问服务都将返回相同的结果。
  
    
    
有关详细信息，请参阅  [SharePoint Search REST API 概述](sharepoint-search-rest-api-overview.md)和 [使用搜索 REST 服务检索查询建议](retrieving-query-suggestions-using-the-search-rest-service.md)。
  
    
    

### 使用 .NET 服务器对象模型查询
<a name="bk_QuerySOM"> </a>

使用服务器对象模型的应用程序必须在运行 SharePoint 2013 的服务器上直接运行。搜索查询服务器对象模型驻留在位于 Microsoft.Office.Server.Search.dll 中的  [Microsoft.Office.Server.Search.Query](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.aspx) 命名空间中。
  
    
    
与 SharePoint Server 2010 中的情况相同，您使用  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.KeywordQuery.aspx) 类定义查询，然后调用 [Execute()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.Execute.aspx) 方法来提交查询。在 SharePoint 2013 中， **Execute** 方法已过时，尽管该方法仍然有效，但您也应该使用 [SearchExecutor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.aspx) 类来代替。若要提交查询，请调用 [ExecuteQuery()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.ExecuteQuery.aspx) 方法，在调用过程中传递 **KeywordQuery** 类的实例。
  
    
    
以下是一个基本示例。
  
    
    



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

若要下载示例，请参阅 SharePoint MVP  [科里·罗斯](http://mvp.microsoft.com/zh-cn/mvp/Corey%20Roth-4029260)发布的以下代码示例： [SharePoint 2013：使用 KeywordQuery 类查询搜索](http://code.msdn.microsoft.com/Query-Search-with-the-372139b5)。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中生成搜索查询](building-search-queries-in-sharepoint-2013.md)
    
  
-  [SharePoint Search REST API 概述](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013：从 SharePoint 相关应用程序使用搜索 REST 服务](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  

  
    
    
