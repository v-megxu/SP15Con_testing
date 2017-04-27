---
title: Utilisation des API de requête de recherche SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ae9d73ed-1140-430b-9287-01dbbe8ae7d1
---



# Utilisation des API de requête de recherche SharePoint 2013
Découvrez les API de requête disponibles dans SharePoint 2013 qui vous permettent d'ajouter une fonctionnalité de recherche aux solutions et applications personnalisées. 
## API de requête SharePoint 2013
<a name="bk_QueryAPIs"> </a>

Recherche dans SharePoint 2013 fournit plusieurs API de requête, vous offrant ainsi de nombreux moyens d'accéder aux résultats de recherche, afin que vous puissiez renvoyer les résultats de recherche dans une variété de types de solutions personnalisées.
  
    
    
Outre le modèle objet serveur qui était disponible dans les versions précédentes de SharePoint, Recherche dans SharePoint 2013 fournit également les éléments suivants :
  
    
    

- Modèle objet client (CSOM)
    
  
- Modèle objet JavaScript (JSOM)
    
  
- Service REST (Representational State Transfer)
    
  
Le tableau 1 présente les API que vous pouvez utiliser pour programmer des requêtes de recherche et le chemin d'accès au fichier source sur le serveur.
  
    
    

**Tableau 1. API de recherche**


|**Nom de l'API**|**Bibliothèque de classes ou schéma et chemin d'accès**|
|:-----|:-----|
|CSOM .NET  <br/> |Microsoft.SharePoint.Client.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|CSOM Silverlight  <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|CSOM JavaScript  <br/> |SP.search.js          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|Points de terminaison de service REST  <br/> |http://server/_api/search/query          http://server/_api/search/suggest  <br/> |
|Modèle objet serveur  <br/> |Microsoft.Office.Server.Search.dll          %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   
Il est vivement recommandé d'utiliser des API client lorsque vous le pouvez pour le développement SharePoint 2013. Les API client comprennent les modèles objets clients .NET, Silverlight, Phone et JavaScript, ainsi que le service REST. Pour plus d'informations sur les API proposées dans SharePoint 2013 et pour savoir quand les utiliser, voir  [Choisir l'ensemble d'API approprié dans SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

### Requête à l'aide du modèle objet client .NET
<a name="bk_QueryNETcsom"> </a>

Recherche dans SharePoint 2013 inclut un modèle objet client qui permet d'accéder aux résultats de recherche pour un développement en ligne, local et mobile. Le modèle CSOM Recherche dans SharePoint 2013 est construit sur le modèle CSOM SharePoint 2013. Par conséquent, votre code client doit d'abord accéder au modèle CSOM SharePoint 2013, puis au modèle CSOM Recherche dans SharePoint 2013. Pour plus d'informations sur le modèle CSOM SharePoint, voir  [Modèle objet client managé](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Pour plus d'informations sur la classe  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) , qui est le point d'entrée du modèle CSOM, voir [Contexte de client en tant qu'objet central](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx).
  
    
    
Pour le modèle CSOM .NET géré, obtenez une instance **ClientContext** (située dans l'espace de noms [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) dans le fichier Microsoft.SharePoint.Client.dll). Ensuite, utilisez le modèle objet dans l'espace de noms [Microsoft.SharePoint.Search.Client.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Search.Client.Query.aspx) dans le fichier Microsoft.SharePoint.Search.Client.dll.
  
    
    
Voici un exemple de base.
  
    
    



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

Pour télécharger un exemple, consultez l'exemple de code suivant publié par le MVP SharePoint  [Corey Roth](http://mvp.microsoft.com/fr-fr/mvp/Corey%20Roth-4029260) : [SharePoint 2013 : requête de recherche avec le modèle objet client géré](http://code.msdn.microsoft.com/Query-Search-with-the-649f1bc1).
  
    
    

### Requête à l'aide du modèle objet client JavaScript
<a name="bk_QueryJSOM"> </a>

Pour le modèle CSOM JavaScript, obtenez une instance  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) , puis utilisez le modèle objet dans le fichier SP.Search.js.
  
    
    
Voici un exemple de base.
  
    
    



```

var clientContext = new SP.ClientContext("<serverRelativeUrl>");
var contextSite = clientContext.get_site();
var keywordQuery = new Microsoft.SharePoint.Client.Search.Query.KeywordQuery(clientContext); 
keywordQuery.set_queryText("SharePoint"); 
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(clientContext);  
var results = searchExecutor.executeQuery(keywordQuery); 
context.executeQueryAsync(onQuerySuccess, onQueryError);
```

Pour télécharger un exemple, consultez l'exemple de code suivant publié par le MVP SharePoint  [Corey Roth](http://mvp.microsoft.com/fr-fr/mvp/Corey%20Roth-4029260) : [SharePoint 2013 : requête de recherche avec le modèle objet client JavaScript](http://code.msdn.microsoft.com/SharePoint-2013-Querying-a629b53b).
  
    
    

### Requête à l'aide du service REST
<a name="bk_QueryREST"> </a>

SharePoint 2013 inclut un service REST qui vous permet d'exécuter des requêtes à distance sur le service de recherche SharePoint 2013 à partir d'applications clientes à l'aide d'une technologie prenant en charge les requêtes web REST. Le service REST de recherche expose deux points de terminaison, **query** et **suggest**, et prend en charge les opérations **GET** et **POST**. Les résultats sont renvoyés au format XML ou JavaScript Object Notation (JSON).
  
    
    
Le point d'accès du service est le suivant :  `http://server/_api/search/`. Vous pouvez également spécifier le site dans l'URL, comme suit :  `http://server/site/_api/search/`. Le service de recherche renvoie les résultats de l'intégralité de la collection de sites, les mêmes résultats sont donc renvoyés pour les deux méthodes d'accès au service.
  
    
    
Pour plus d'informations, voir  [Vue d'ensemble de l'API REST de recherche SharePoint](sharepoint-search-rest-api-overview.md) et [Lors de la récupération des suggestions de requête à l'aide du service de recherche reste](retrieving-query-suggestions-using-the-search-rest-service.md).
  
    
    

### Requête à l'aide du modèle objet serveur .NET
<a name="bk_QuerySOM"> </a>

Les applications qui utilisent le modèle objet serveur doivent être exécutées directement sur un serveur qui exécute SharePoint 2013. Le modèle objet serveur de requête de recherche réside dans l'espace de noms  [Microsoft.Office.Server.Search.Query](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.aspx) situé dans le fichier Microsoft.Office.Server.Search.dll.
  
    
    
Comme dans SharePoint Server 2010, vous utilisez la classe  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.KeywordQuery.aspx) pour définir la requête, puis appelez la méthode [Execute()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.Execute.aspx) pour la soumettre. Dans SharePoint 2013, la méthode **Execute** est obsolète, et même si elle fonctionne toujours, nous vous recommandons d'utiliser la classe [SearchExecutor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.aspx) à la place. Pour soumettre la requête, appelez la méthode [ExecuteQuery()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SearchExecutor.ExecuteQuery.aspx) , en transmettant l'instance de la classe **KeywordQuery** dans l'appel.
  
    
    
Voici un exemple de base.
  
    
    



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

Pour télécharger un exemple, consultez l'exemple de code suivant publié par le MVP SharePoint  [Corey Roth](http://mvp.microsoft.com/fr-fr/mvp/Corey%20Roth-4029260) : [SharePoint 2013 : requête de recherche avec la classe KeywordQuery](http://code.msdn.microsoft.com/Query-Search-with-the-372139b5).
  
    
    

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Création de requêtes de recherche dans SharePoint 2013](building-search-queries-in-sharepoint-2013.md)
    
  
-  [Vue d'ensemble de l'API REST de recherche SharePoint](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013 : utilisation du service REST de recherche à partir d'une application pour SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  

  
    
    
