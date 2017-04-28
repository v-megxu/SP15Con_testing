---
title: SharePoint 2013 的 BCS REST API 引用
ms.prod: SHAREPOINT
ms.assetid: 364fb8d7-87d9-4be7-affd-90caba3cd0c0
---



# SharePoint 2013 的 BCS REST API 引用

  
    
    
![类库和引用](images/mod_icon_badge_reference.png)
  
    
    

  
    
    

  
    
    
包含用于构建代表性状态传输 (REST) URL 的参考信息，以使用 SharePoint 2013 中的 Business Connectivity Services (BCS) 访问和操作外部数据源。
## 在 SharePoint 2013 中使用 RESTful API 访问外部数据
<a name="bkmk_Overview"> </a>

SharePoint 2013 提供的 REST 界面使您可以通过特殊构建的 URL 访问大部分 SharePoint 2013 资源。Business Connectivity Services (BCS) 使用此架构提供对外部数据的访问权限。
  
    
    
您可以通过构造 URL 来访问外部数据，就像访问标准列表项一样。
  
    
    

> **注释**
> 不提供通过 BDC 直接访问实体的权限。若要使用外部数据，您必须创建一个外部列表，并使用 REST URL 来访问外部列表中的列表项。 
  
    
    

用于外部列表的受支持 HTTP 动词为 **GET**、 **PUT**、 **POST** 和 **DELETE**。
  
    
    
不同于正常列表，您不能使用 REST 创建外部列表。您必须通过使用 Visual Studio 2008 创建一个 BDC 模型和一个外部列表来做到这一点。
  
    
    
表 1 中的信息显示了如何构建 RESTful URL 和相应的客户端对象模型调用来访问和操作外部数据源中的数据。
  
    
    

**表1. 用于访问外部数据的 RESTful URL 格式**


|**URL**|**说明**|**HTTP 方法**|
|:-----|:-----|:-----|
| `http://[sharepointsite]/_api` <br/> |任何 REST 请求的基础。_api 虚拟目录映射到 client.svc 中的调用，其中可以使用客户端对象模型。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/web/title` <br/> |检索当前网页的标题。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists` <br/> |检索一个网站上的所有列表。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')` <br/> |检索指定列表上的元数据。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')/items` <br/> |检索一个指定列表中的列表项。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')?select=Title` <br/> |检索一个特定列表的标题。  <br/> |GET  <br/> |
   

## 构造筛选数据的查询字符串
<a name="bkmk_constructquery"> </a>

为了限制返回的数据数量，或者使其与用户更加相关，您可以使用表 2 中的筛选操作。
  
    
    

**表 2. 筛选数据的运算符**


|**运算符**||
|:-----|:-----|
|EQ  <br/> |等于  <br/> *注释* <br/> 当您使用 **EQ** 进行筛选时，筛选器条件就会传递到服务器上发生筛选的外部系统上。          |
|GT  <br/> |大于  <br/> *注释* <br/> 当您使用 **GT** 运算符时，仅执行客户端筛选。 <br/> 例如： `web/lists/getByTitle('ListName')/Items?$select=Title&amp;$filter=AverageRating gt 3` 返回所有平均得分超过 3 的标题。          |
   

> **注释**
> 若要检索关联部分的列，您必须在查询字符串中使用 **$select**，将该列显式包含在 URL 中。 
  
    
    


## 其他资源
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 REST 终结点完成基本操作](http://msdn.microsoft.com/library/e3000415-50a0-426e-b304-b7de18f2f7d9%28Office.15%29.aspx)
    
  
-  [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  
-  [SharePoint 2013：在应用程序中使用 REST 执行基本的数据访问操作](http://code.msdn.microsoft.com/SharePoint-2013-Perform-335d925b)
    
  
-  [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的 JavaScript 库代码完成基本操作](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
