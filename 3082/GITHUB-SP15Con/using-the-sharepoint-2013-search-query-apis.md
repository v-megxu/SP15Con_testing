---
title: Usar las API de consulta de búsqueda en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ae9d73ed-1140-430b-9287-01dbbe8ae7d1
---



# Usar las API de consulta de búsqueda en SharePoint 2013
Conozca las API de consulta disponibles en SharePoint 2013 que le permiten agregar funciones de búsqueda a las soluciones y aplicaciones personalizadas. 
## Las API de consulta de SharePoint 2013
<a name="bk_QueryAPIs"> </a>

Buscar en SharePoint 2013 tiene varias API de consulta, lo que le ofrece muchas formas de obtener acceso a los resultados de búsqueda. De este modo, puede devolver resultados de búsqueda en una gran variedad de tipos de soluciones personalizadas.
  
    
    
Además del modelo de objetos de servidor que había en versiones anteriores de SharePoint, Buscar en SharePoint 2013 también ofrece lo siguiente:
  
    
    

- Modelo de objetos de cliente (CSOM)
    
  
- Modelo de objetos de JavaScript (JSOM)
    
  
- Servicio Transferencia de estado representacional (REST)
    
  
En la tabla 1 se recogen las API que puede usar para programar consultas de búsqueda y la ruta de acceso al archivo de código fuente en el servidor.
  
    
    

**Tabla 1. Las API de búsqueda**


|**Nombre de la API**|**Biblioteca de clases o esquema y ruta de acceso**|
|:-----|:-----|
|.NET CSOM  <br/> |Microsoft.SharePoint.Client.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|Silverlight CSOM  <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|JavaScript CSOM  <br/> |SP.search.js          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|Extremos del servicio REST  <br/> |http://server/_api/search/query          http://server/_api/search/suggest  <br/> |
|Modelo de objetos de servidor  <br/> |Microsoft.Office.Server.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   
Como práctica recomendada para el desarrollo de SharePoint 2013, use API de cliente siempre que pueda. Las API de cliente incluyen los modelos de objetos de cliente .NET, Silverlight, Phone y JavaScript, y el servicio REST. Para más información sobre las API de SharePoint 2013 y cuándo usarlas, vea  [Elegir el conjunto de API correcto en SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

### Consultar usando el modelo de objetos de cliente .NET
<a name="bk_QueryNETcsom"> </a>

Buscar en SharePoint 2013 incluye un modelo de objetos de cliente que permite el acceso a los resultados de búsqueda para el desarrollo en línea, local y móvil. El CSOM de Buscar en SharePoint 2013 está integrado en el CSOM de SharePoint 2013. Por lo tanto, el código de cliente tiene que obtener acceso primero al CSOM de SharePoint 2013 y luego al CSOM de Buscar en SharePoint 2013. Para más información sobre el CSOM de SharePoint, vea  [Modelo de objetos cliente administrado](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Para más información sobre la clase  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) , que es el punto de entrada al CSOM, vea [Contexto de cliente como objeto central](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx).
  
    
    
Para el CSOM administrado de .NET, obtenga una instancia de **ClientContext** (que se encuentra en el espacio de nombres [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) en el archivo Microsoft.SharePoint.Client.dll). Luego use el modelo de objetos del espacio de nombres [Microsoft.SharePoint.Search.Client.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Search.Client.Query.aspx) que hay en Microsoft.SharePoint.Search.Client.dll.
  
    
    
Este es un ejemplo básico.
  
    
    



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

Para bajarse un ejemplo, vea el siguiente ejemplo de código que ha publicado el MVP de SharePoint  [Corey Roth](http://mvp.microsoft.com/es-es/mvp/Corey%20Roth-4029260):  [SharePoint 2013: Búsqueda de consultas con el modelo de objetos de cliente administrado](http://code.msdn.microsoft.com/Query-Search-with-the-649f1bc1).
  
    
    

### Consultar usando el modelo de objetos de cliente JavaScript
<a name="bk_QueryJSOM"> </a>

Para el CSOM de JavaScript CSOM, obtenga una instancia de  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) y luego use el modelo de objetos del archivo SP.Search.js.
  
    
    
Este es un ejemplo básico.
  
    
    



```

var clientContext = new SP.ClientContext("<serverRelativeUrl>");
var contextSite = clientContext.get_site();
var keywordQuery = new Microsoft.SharePoint.Client.Search.Query.KeywordQuery(clientContext); 
keywordQuery.set_queryText("SharePoint"); 
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(clientContext);  
var results = searchExecutor.executeQuery(keywordQuery); 
context.executeQueryAsync(onQuerySuccess, onQueryError);
```

Para bajarse un ejemplo, vea el siguiente ejemplo de código que ha publicado el MVP de SharePoint  [Corey Roth](http://mvp.microsoft.com/es-es/mvp/Corey%20Roth-4029260):  [SharePoint 2013: Búsqueda de consultas con el modelo de objetos de cliente JavaScript](http://code.msdn.microsoft.com/SharePoint-2013-Querying-a629b53b).
  
    
    

### Consultar usando el servicio REST
<a name="bk_QueryREST"> </a>

SharePoint 2013 incluye un servicio REST que le permite ejecutar consultas de forma remota en el servicio de búsqueda de SharePoint 2013 desde aplicaciones de cliente usando una tecnología que admite las solicitudes web de REST. El servicio de búsqueda REST expone dos extremos, **query** y **suggest**, y admite las operaciones **GET** y **POST**. Los resultados se devuelven en formato XML o Notación de objetos de JavaScript (JSON).
  
    
    
Este es el punto de acceso del servicio:  `http://server/_api/search/`. También puede especificar el sitio en la dirección URL de esta forma:  `http://server/site/_api/search/`. El servicio de búsqueda devuelve resultados de toda la colección de sitios, de modo que los mismos resultados se devuelven para que se pueda obtener acceso al servicio por ambos lados.
  
    
    
Vea  [Información general de la API de REST de SharePoint Search](sharepoint-search-rest-api-overview.md) y [Recuperación de sugerencias de consulta con el servicio REST de búsqueda](retrieving-query-suggestions-using-the-search-rest-service.md) para más información.
  
    
    

### Consultar usando el modelo de objetos de servidor .NET
<a name="bk_QuerySOM"> </a>

Las aplicaciones que usan el modelo de objetos de servidor se deben ejecutar directamente en un servidor que esté ejecutando SharePoint 2013. El modelo de objetos de servidor de consulta reside en el espacio de nombres  [Microsoft.Office.Server.Search.Query](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.aspx) , que se encuentra en Microsoft.Office.Server.Search.dll.
  
    
    
Como en SharePoint Server 2010, se usa la clase  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.KeywordQuery.aspx) para definir la consulta y luego se llama al método [Execute()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.Execute.aspx) para enviar la consulta. En SharePoint 2013, el método **Execute** está obsoleto y, aunque aún funcione, hay que usar la clase [SearchExecutor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.aspx) . Para enviar la consulta, llame al método [ExecuteQuery()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.ExecuteQuery.aspx) y pase la instancia de la clase **KeywordQuery** en la llamada.
  
    
    
Este es un ejemplo básico.
  
    
    



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

Para bajarse un ejemplo, vea el siguiente ejemplo de código que ha publicado el MVP de SharePoint  [Corey Roth](http://mvp.microsoft.com/es-es/mvp/Corey%20Roth-4029260):  [SharePoint 2013: Búsqueda de consultas con la clase KeywordQuery](http://code.msdn.microsoft.com/Query-Search-with-the-372139b5).
  
    
    

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Generar consultas de búsqueda en SharePoint 2013](building-search-queries-in-sharepoint-2013.md)
    
  
-  [Información general de la API de REST de SharePoint Search](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013: usar el servicio REST de búsqueda desde una aplicación para SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  

  
    
    
