---
title: 在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门
ms.prod: SHAREPOINT
ms.assetid: 8ed91929-fdb6-4fde-ba2a-7942870575f3
---



# 在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门
了解如何使用 SharePoint 2013 客户端对象模型来处理 SharePoint 2013 中的 Business Connectivity Services (BCS)。
## 什么是 SharePoint 2013 客户端对象模型？


|||
|:-----|:-----|
|SharePoint 2013 客户端对象模型是表示服务器对象模型的一套基于客户端的库。它们打包在三个不同的 DLL 中，可以适应不同的开发类型。客户端对象模型包括服务器 API 的大部分主要函数。这允许从浏览器脚本, .NET Web 应用程序和 Silverlight 应用程序访问相同类型的功能。  <br/> 为了改进和扩展处理外部数据的功能，Business Connectivity Services (BCS) 扩展了客户端对象模型，使其包括其他功能。  <br/>  [![开始设置](images/mod_icon_getstartbox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_getstarted) [![开始工作](images/mod_icon_dobox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_Tasks) [![了解详细信息](images/mod_icon_startbox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_Learnmore) <br/> ||
   

## 使用具有外部数据的 SharePoint 2013 客户端对象模型入门
<a name="BCScsom_getstarted"> </a>

若要使用 SharePoint 客户端对象模型 (CSOM) 开发解决方案，您将需要以下内容：
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
有关如何设置开发环境的信息，请参阅 [为 SharePoint 2013 中的 BCS 设置开发环境](setting-up-a-development-environment-for-bcs-in-sharepoint-2013.md)。
  
    
    
若要访问客户端对象模型提供的功能，您仅需要添加对其项目中的 **Microsoft.SharePoint.Client.Runtime.dll** 和 **Microsoft.SharePoint.Client.dll** 文件的引用。您也可以通过引用全局程序集缓存中的以下 DLL 来使用客户端对象模型：
  
    
    

-  `\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\isapi\\Microsoft.SharePoint.Client.Runtime.dll`
    
  
-  `\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\isapi\\Microsoft.SharePoint.Client.dll`
    
  

### SharePoint 2013 客户端对象模型要素

以下文章将帮助您更好地了解 SharePoint 2013 中的客户端对象模型。
  
    
    

**表 1. 了解客户端对象模型的核心概念**


|**文章**|**说明**|
|:-----|:-----|
| [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md) <br/> |了解您可以使用外部内容类型做什么，以及开始在 SharePoint 2013 中创建它们需要什么。  <br/> |
| [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |提供信息以帮助开始根据 OData 源创建外部内容类型并在 SharePoint 2013 或 Office 2013 组件中使用该数据。  <br/> |
| [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md) <br/> |了解 SharePoint 2013 提供的几组 API，包括服务器对象模型、各种客户端对象模型和 REST/OData Web 服务。  <br/> |
| [SharePoint 2013 的 .NET 客户端 API 引用](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx) <br/> |查找有关 SharePoint 2013 中的 .NET 客户端类库的信息。  <br/> |
| [SharePoint 2013 的 JavaScript API 引用](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx) <br/> |查找有关 SharePoint 2013 中的 JavaScript 对象库的信息。  <br/> |
   

## 您可以使用客户端对象模型进行哪些操作？
<a name="BCScsom_Tasks"> </a>

您可以使用 SharePoint 客户端对象模型检索、更新和管理包含在 SharePoint 2013 中的数据。SharePoint 以不同的格式提供客户端库以适应大部分开发人员。对于使用脚本语言的 Web 开发人员，在 JavaScript 中提供客户端库。对于 .NET 开发人员，客户端库作为 .NET 客户端托管 DLL 提供。对于 Silverlight 应用程序开发人员，由 Silverlight DLL 提供客户端库。
  
    
    
有关您可以使用 SharePoint 2013 中的客户端对象模型执行的操作，请参阅表 2 中的文章。
  
    
    

**表 2. 使用具有外部数据的客户端对象模型的基本任务**


|**任务**|**说明**|
|:-----|:-----|
| [使用 SharePoint 2013 客户端库代码完成基本操作](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx) <br/> |了解如何编写代码以使用 SharePoint 2013 客户端对象模型执行基本操作。  <br/> |
| [如何：使用客户端代码库访问 SharePoint 2013 中的外部数据](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |了解如何借助 SharePoint 2013 客户端对象模型来使用采用基于浏览器的脚本的 SharePoint BCS 对象。  <br/> |
   
以下是您可以使用 CSOM 完成的基本任务示例。
  
    
    

### 获取特定实体

该例展示如何从 SharePoint 获取上下文，然后检索指定的数据源实体。
  
    
    

```cs

ClientContext ctx = new ClientContext("http://sharepointservername"); 
Web web = ctx.Web; 
ctx.Load(web); 
Entity entity = ctx.Web.GetEntity("http://sharepointservername", "EntityName"); 
ctx.Load(entity); 
ctx.ExecuteQuery(); 

```


### 创建通用调用程序

该例展示如何编写通用调用程序，使您可以创建在您的代码中使用的实体对象。
  
    
    

```cs

ObjectCollection myObj; 
entity.Execute("MethodInstanceName", lsi, myObj); 
ctx.Load(myObj); 
ctx.ExecuteQuery(); 

```


### 检索分页结果集

下面的示例展示如何检索经过筛选的分页数据集。在该情况下，页面值是 50。
  
    
    

```cs

// Find filters for given Method Name. 
FilterCollection fCollection = entity.GetFilters("methodName"); 
ctx.Load(fCollection); 
ctx.ExecuteQuery(); 
FilterCollection modifiedFCollection = new FilterCollection(); 
foreach( Filter filter in fCollection) 
{ 
    if( filter.FilterField.equals("X.Y.Z.Country")) 
    { 
        filter.FilterValue = "India"; 
        modifiedFCollection.Add(Filter); 
    } 
    if(filter.FilterType == FilterType.Limit) 
    { 
        filter.FilterValue = 50; 
        modifiedFCollection.Add(Filter); 
    } 
} 
EntityInstanceCollection eCollection = entity.FindFiltered(modifiedFCollection, 
"nameOfFinder", lsi); 
ctx.ExecuteQuery(); 

```


### 查询已筛选的信息

下面的示例展示如何返回已筛选的结果集。在该情况下，已筛选的数据列是 **X.Y.Z.Country** 域。代码查询任何含有"印度"值的内容，然后将结果放入集中。
  
    
    

```cs

// Find filters for given Method Name. 
FilterCollection fCollection = entity.GetFilters("methodName"); 
ctx.Load(fCollection); 
ctx.ExecuteQuery(); 
FilterCollection modifiedFCollection = new FilterCollection(); 
foreach( Filter filter in fCollection) 
{ 
    if( filter.FilterField.equals("X.Y.Z.Country")) 
    { 
        filter.FilterValue = "India"; 
        modifiedFCollection.Add(Filter); 
    } 
} 
EntityInstanceCollection eCollection = entity.FindFiltered(modifiedFCollection, 
"nameOfFinder", lsi); 
ctx.ExecuteQuery(); 

```


## 基本知识之外的内容：了解关于客户端对象模型的详细信息
<a name="BCScsom_Learnmore"> </a>

有关使用 SharePoint 2013 中的客户端对象模型的详细信息，请参阅表 3 中的信息。
  
    
    

**表 3. 客户端对象模型高级概念**


|**文章**|**说明**|
|:-----|:-----|
| [SharePoint 2013 的 BCS 客户端对象模型引用](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |总结可用于使用 SharePoint 2013 客户端对象模型创建客户端脚本以访问 BCS 揭示的外部数据的对象。  <br/> |
   

## 其他资源
<a name="BCScsom_Learnmore"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [如何：使用客户端代码库访问 SharePoint 2013 中的外部数据](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 客户端库代码完成基本操作](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [SharePoint 2013：使用 CSOM 访问复杂外部内容类型](http://code.msdn.microsoft.com/office/SharePoint-2013-Accessing-ccbc24cf)
    
  
