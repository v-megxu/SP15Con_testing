---
title: Использование API поисковых запросов SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ae9d73ed-1140-430b-9287-01dbbe8ae7d1
---



# Использование API поисковых запросов SharePoint 2013
Узнайте, какие API-интерфейсов запросов в SharePoint 2013 позволяют добавлять возможности поиска в пользовательские решения и приложения. 
## API-интерфейсы запросов SharePoint 2013
<a name="bk_QueryAPIs"> </a>

Поиск в SharePoint 2013 предусматривает несколько интерфейсов API запроса, которые предоставляют множество способов доступа к результатам поиска, чтобы вы могли вернуть различные типы пользовательских решений.
  
    
    
Помимо серверной объектной модели, доступной в предыдущих версиях SharePoint, Поиск в SharePoint 2013 также предоставляет:
  
    
    

- клиентскую объектную модель (CSOM);
    
  
- объектную модель JavaScript (JSOM);
    
  
- службу передачи репрезентативного состояния (REST).
    
  
В таблице 1 приведены API-интерфейсы, которые можно использовать для программируемых запросов, а также путь к исходному файлу на сервере.
  
    
    

**Таблица 1. Поисковые интерфейсы API**


|**Имя API**|**Библиотека или схема классов и путь**|
|:-----|:-----|
|.NET CSOM  <br/> |Microsoft.SharePoint.Client.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|Silverlight CSOM  <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|JavaScript CSOM  <br/> |SP.search.js          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|Конечные точки службы REST  <br/> |http://server/_api/search/query          http://server/_api/search/suggest  <br/> |
|Серверная объектная модель.  <br/> |Microsoft.Office.Server.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   
Согласно передовой практике в разработке SharePoint 2013 используйте клиентские интерфейсы API, когда это возможно. Клиентские интерфейсы API включают клиентские объектные модели .NET, Silverlight, Phone и JavaScript и службу REST. Более подробную информацию об интерфейсах API в SharePoint 2013 и их использовании можно узнать в статье  [Выбор правильного набора API в SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

### Запросы с использованием клиентской объектной модели .NET
<a name="bk_QueryNETcsom"> </a>

В Поиск в SharePoint 2013 реализована клиентская объектная модель, предоставляющая доступ к результатам поиска для разработки веб-приложений, локальных и мобильных приложений. CSOM Поиск в SharePoint 2013 основана на CSOM SharePoint 2013. Поэтому клиентскому коду сначала нужно получить доступ к CSOM SharePoint 2013, а затем  к CSOM Поиск в SharePoint 2013. Дополнительные сведения о клиентской объектной модели SharePoint см. в статье  [Управляемая клиентская объектная модель](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Дополнительные сведения о классе  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) , который служит точкой входа в CSOM, см. в статье [Контекст клиента как центральный объект](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx).
  
    
    
При использовании управляемой CSOM .NET получите экземпляр **ClientContext** (расположен в пространстве имен [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) в библиотеке Microsoft.SharePoint.Client.dll). Затем используйте объектную модель в пространстве имен [Microsoft.SharePoint.Search.Client.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Search.Client.Query.aspx) из библиотеки Microsoft.SharePoint.Search.Client.dll.
  
    
    
Вот простой пример.
  
    
    



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

Чтобы скачать пример, изучите следующий пример кода, опубликованный  [Кори Ротом](http://mvp.microsoft.com/ru-ru/mvp/Corey%20Roth-4029260), специалистом MVP по SharePoint:  [SharePoint 2013: поисковый с помощью управляемой клиентской объектной модели](http://code.msdn.microsoft.com/Query-Search-with-the-649f1bc1).
  
    
    

### Запросы с использованием клиентской объектной модели JavaScript
<a name="bk_QueryJSOM"> </a>

Для клиентской объектной модели JavaScript получите экземпляр  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) , а затем используйте объектную модель в файле SP.Search.js.
  
    
    
Вот простой пример.
  
    
    



```

var clientContext = new SP.ClientContext("<serverRelativeUrl>");
var contextSite = clientContext.get_site();
var keywordQuery = new Microsoft.SharePoint.Client.Search.Query.KeywordQuery(clientContext); 
keywordQuery.set_queryText("SharePoint"); 
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(clientContext);  
var results = searchExecutor.executeQuery(keywordQuery); 
context.executeQueryAsync(onQuerySuccess, onQueryError);
```

Чтобы скачать пример, изучите следующий пример кода, опубликованный  [Кори Ротом](http://mvp.microsoft.com/ru-ru/mvp/Corey%20Roth-4029260), специалистом MVP по SharePoint:  [SharePoint 2013: поисковый запрос с помощью клиентской объектной модели JavaScript](http://code.msdn.microsoft.com/SharePoint-2013-Querying-a629b53b).
  
    
    

### Запросы с использованием службы REST
<a name="bk_QueryREST"> </a>

SharePoint 2013 предоставляет службу REST, которая позволяет удаленно выполнять запросы к службе поиска SharePoint 2013 из клиентских приложений, используя любые технологии, поддерживающие веб-запросы REST. Служба REST поиска предоставляет две конечных точки, **query** и **suggest**, и поддерживает операции **GET** и **POST**. Результаты возвращаются в формате XML или Нотация объектов JavaScript (JSON).
  
    
    
Далее показана точка доступа для службы:  `http://server/_api/search/`. Вы также можете указать сайт в URL-адресе следующим образом:  `http://server/site/_api/search/`. Служба поиска возвращает результаты из всего семейства веб-сайтов, поэтому для обоих методов доступа к службе возвращаются одинаковые результаты.
  
    
    
Подробнее см. в статьях  [Общие сведения об API службы поиска REST для SharePoint](sharepoint-search-rest-api-overview.md) и [Получение предложений запроса, с помощью службы Search REST](retrieving-query-suggestions-using-the-search-rest-service.md).
  
    
    

### Запросы с использованием серверной объектной модели .NET
<a name="bk_QuerySOM"> </a>

Приложения, использующие серверную объектную модель, должны выполняться непосредственно на сервере, где запущен SharePoint 2013. Серверная объектная модель поисковых запросов размещена в пространстве имен  [Microsoft.Office.Server.Search.Query](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.aspx) в библиотеке Microsoft.Office.Server.Search.dll.
  
    
    
Как и в SharePoint Server 2010, вы используете класс  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.KeywordQuery.aspx) , чтобы определить запрос, а затем вызываете метод [Execute()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.Execute.aspx) , чтобы отправить запрос. В SharePoint 2013 метод **Execute** по-прежнему работает, но считается устаревшим, поэтому следует использовать класс [SearchExecutor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.aspx) . Чтобы отправить запрос, вызовите метод [ExecuteQuery()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.ExecuteQuery.aspx) , передав экземпляр класса **KeywordQuery** в вызове.
  
    
    
Вот простой пример.
  
    
    



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

Чтобы скачать пример, изучите следующий пример кода, опубликованный  [Кори Ротом](http://mvp.microsoft.com/ru-ru/mvp/Corey%20Roth-4029260), специалистом MVP по SharePoint:  [SharePoint 2013: поисковый запрос с помощью класса KeywordQuery](http://code.msdn.microsoft.com/Query-Search-with-the-372139b5).
  
    
    

## Дополнительные ресурсы
<a name="bk_addresources"> </a>


-  [Построение запросов поиска в SharePoint 2013](building-search-queries-in-sharepoint-2013.md)
    
  
-  [Общие сведения об API службы поиска REST для SharePoint](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013: использование службы поиска REST в приложении для SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  

  
    
    
