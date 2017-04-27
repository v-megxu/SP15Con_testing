---
title: SharePoint 2013 搜索功能中面向开发人员的新增内容
ms.prod: SHAREPOINT
ms.assetid: b8d69685-3612-421e-b011-50b4d580d461
---


# SharePoint 2013 搜索功能中面向开发人员的新增内容
了解 SharePoint 2013 Search 中开发人员可用的新功能。
## 适用于访问可实现在线、本地和移动开发的 Query 对象模型功能的 Search 客户端对象模型
<a name="SPSearchnew_clientOM"> </a>

SharePoint 2013 Search 包括可访问大多数实现在线、本地和移动开发的客户端对象模型 (CSOM)。您可以使用 Search CSOM 来创建在未安装有 SharePoint 2013 来返回 SharePoint 2013 搜索结果的计算机上运行的客户端应用程序。
  
    
    
Search CSOM 包括 Microsoft .NET Framework 托管客户端对象模型和 JavaScript 对象模型，并且其内置于 SharePoint 2013。首先，客户端代码访问 SharePoint CSOM。然后，再访问 Search CSOM。 
  
    
    
要使用 Search .NET Framework 托管 CSOM，您必须获得  [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) 实例（位于 Microsoft.SharePoint.Client.dll 的 [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) 命名空间中）。然后，再使用位于 Microsoft.Office.Server.Search.Client.dll 的 [Microsoft.SharePoint.Client.Search.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.aspx) 命名空间中的对象模型。有关 SharePoint CSOM 的详细信息，请参阅 [托管客户端对象模型](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)。有关 **ClientContext** 对象（CSOM 的入口点）的详细信息，请参阅 [作为中心对象的客户端上下文](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)。
  
    
    
Search CSOM 以 JavaScript 对象表示法 (JSON) 形式从服务器返回搜索结果。搜索结果数据的 JSON 包含  [ResultTableCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.ResultTableCollection.aspx) 集合，该集合由代表不同结果集的 [ResultTable](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.ResultTable.aspx) 对象组成。
  
    
    

## SQL Syntax Support 已删除
<a name="SP15Searchnew_support"> </a>

SharePoint Server 2013 中的自定义搜索解决方案不支持  [SQL 语法](http://msdn.microsoft.com/zh-cn/library/ee558869.aspx)。SharePoint 2013 中的搜索功能 的自定义搜索解决方案支持 FQL 语法和 KQL 语法。您不能在使用任何技术的自定义搜索解决方案中使用 SQL 语法，其中包括 Query 服务器对象模型、客户端对象模型以及 Search REST 服务。将以早期版本的 SharePoint Server 创建的 Query 服务器对象模型和 Query Web 服务升级到 SharePoint Server 2013 后，结合这二者使用 SQL 语法的自定义搜索解决方案将不在有用。通过这些应用程序提交的查询将返回错误。有关使用 FQL 语法和 KQL 语法的详细信息，请参阅  [关键字查询语言 (KQL) 语法参考](keyword-query-language-kql-syntax-reference.md)和  [FAST 查询语言 (FQL) 语法参考](fast-query-language-fql-syntax-reference.md)。
  
    
    

## 适用于从客户端应用程序远程执行查询的 Search REST 服务
<a name="SP15Searchnew_support"> </a>

SharePoint Server 2013 包括 Representational State Transfer (REST) 服务，使用该服务，您能够通过任何支持 REST 网络请求的技术从客户端应用程序对 SharePoint 2013 Search 服务执行查询。Search REST 服务暴露两个端点： **query** 和 **suggest**，并将支持 **GET** 和 **POST** 操作。相关结果以 XML 或 JSON 格式返回。
  
    
    
以下是服务的访问点： `http://server/_api/search/`。您还可以以 URL 格式指定网站，格式如下： `http://server/site/_api/search/`。搜索服务从整个网站集返回结果，因此，通过这两种方法访问服务都将返回相同的结果。
  
    
    
您还可以使用引用 client.svc 的 URL 来访问服务，格式如下： `http://server/_vti_bin/client.svc/search/`。但是，使用  `_api` 是首选惯例。
  
    
    
通过以下访问点访问服务元数据： 
  
    
    
 `http://server/_api/$metadata`
  
    
    
有关 SharePoint 2013 中 REST 服务的一般信息，请参阅 [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)。
  
    
    

## SharePoint Search Query Web 服务已被弃用
<a name="SP15Searchnew_support"> </a>

SharePoint 2013 中的 Query Web 服务（位于路径  `http://server/site/_vti_bin/search.asmx` 下）已被弃用。编写新应用程序时，请避免使用此弃用功能，改为使用新的 Query CSOM 或 Query REST 服务。修改现有应用程序时，强烈建议您删除此功能的所有依赖项。
  
    
    

## SharePoint Search Query 对象模型增强
<a name="SP15Searchnew_support"> </a>

Query 属性提供有关搜索查询的信息。在 SharePoint 2013 Search 中，属性包已被添加到查询和结果类中，以支持用户定义的查询属性。您可以通过其中一个查询类的属性访问现有查询属性，方法如下： 
  
    
    
 `KeywordQuery.EnableStemming`
  
    
    
或者，您可以使用属性包，如下所示： 
  
    
    
 `KeywordQuery.Properties["EnableStemming"]`
  
    
    
您只能通过使用属性包访问用户定义的属性，如下所示： 
  
    
    
 `KeywordQuery.Properties["UserDefinedProperty"]`
  
    
    
SharePoint 2013 Search 的属性包中包含查询属性，其中包括新的查询属性，如：
  
    
    

- **BypassResultTypes** 指定是否返回查询结果的搜索结果项类型。如不返回结果类型，则指定 **true**；否则，指定 **false**。
    
  
- **EnableInterleaving** 指定由执行查询规则操作以添加结果块生成的结果集是否混合原始查询的结果集。如要使生成的结果集混合原始结果集，则指定 **true**；否则，指定 **false**。
    
  
- **EnableQueryRules** 指定是否对此查询启用查询规则。如要对查询启用查询规则，则指定 **true**；否则，指定 **false**。
    
  
您可以在属性包中指定任何属性，其中包括用户定义的属性，如查询规则条件。您可以使用查询规则来自定义某些对用户至关重要的查询的搜索条件。如果查询满足查询规则中指定的条件，则规则指定用以提高关联搜索结果相关性的操作。 
  
    
    

## Keyword 查询语言增强
<a name="SP15Searchnew_support"> </a>

SharePoint 2013 包括 Keyword 查询语言的增强，相关增强将在本节中说明。 
  
    
    

### 改进的 NEAR 运算符

在 SharePoint Server 2010 中， **NEAR** 运算符隐含最大标记距离 **8** 并保留了输入标记的排序。在 SharePoint 2013 中， **NEAR** 运算符不再保留标记的排序。此外， **NEAR** 运算符现在接收了一个指示最大标记距离的可选参数。但是，默认值仍为 **8** 。如果您必须使用以前的行为，则改为使用 **ONEAR**。
  
    
    
 **NEAR** 运算符可在属性限制表达式中使用，如下面的示例所示：
  
    
    
 `"acquisition" NEAR "debt"`
  
    
    
此查询与同一文档中出现"acquisition"和"debt"标记的项匹配，最大标记距离为 **8** （如果未提供值，则其为 _n_ 的默认值）。标记的顺序对该匹配不重要。
  
    
    
如果你需要更小的标记距离，则可以按如下所示指定：
  
    
    
 `"acquisition" NEAR(n=3) "debt"`
  
    
    
此查询与同一文档中出现"acquisition"和"debt"两个标记的项匹配，最大标记距离为 **3** 。标记的顺序对该匹配不重要。
  
    
    

### 新的 ONEAR 运算符

 **ONEAR** 运算符提供有序接近功能。它接收一个指示最大标记距离的可选参数；默认值为 **8** 。
  
    
    
 **ONEAR** 运算符保留输入表达式的顺序。对于无序接近，请使用 **NEAR**。
  
    
    
您可以在属性显示表达式中使用 **ONEAR** 运算符，如下面的示例所示：
  
    
    
 `"acquisition" ONEAR "debt"`
  
    
    
此查询与同一文档中出现"acquisition"和"debt"两个标记的项匹配，最大标记距离为 **8** （如果未提供值，则其为 _n_ 的默认值）。标记的顺序必须与要返回的项的顺序匹配。
  
    
    
如果您需要更小的标记距离，则可以按如下所示指定：
  
    
    
 `"acquisition" ONEAR(n=3) "debt"`
  
    
    
此查询与同一文档中出现"acquisition"和"debt"两个标记的项匹配，最大标记距离为 **3** 。标记的顺序必须与要返回的项的顺序匹配。
  
    
    

### 新的 XRANK 运算符

在 SharePoint Server 2010 中， **XRANK** 运算符仅适用于 FAST Query Language (FQL)。 SharePoint 2013 引入了功能强大的新 **XRANK** 运算符。
  
    
    
 **XRANK** 运算符可对排序进行动态控制。此运算符基于某些条款的发生增强项的动态排序，且不更改与查询匹配的项。
  
    
    

## 适用于定制搜索结果 UI 的丰富结果框架
<a name="SP15Searchnew_support"> </a>

SharePoint 2013 Search 包括新的结果框架，可以更轻松地定制搜索结果用户界面 (UI) 的外观（外观和感受）。现在，改为写入自定义 XSLT 即可更改搜索结果的显示方式，您可以通过使用显示模板和结果类型来定制重要结果类型的外观。
  
    
    

### 显示模板

显示模板通过使用 HTML、CSS 和 JavaScript 来定义结果类型的可视化布局和行为。您可以通过使用 HTML 编辑器来定制现有显示模板或创建显示模板，并将其上载到显示模板库。
  
    
    

### 结果类型

结果类型定义如何基于以下内容的集显示一组搜索结果：
  
    
    

- **Rules** 确定应用结果类型的时间（基于指定条件）。规则条件可与等号、比较和逻辑运算符结合使用。
    
  
- **Properties** 确定结果的托管属性列表。您必须先将托管属性添加到列表然后才能将托管属性映射到显示模板。
    
  
- **Display templates** 定义结果类型的可视化布局。
    
  
管理员可以在网站或服务应用程序级别创建和管理结果类型；而不需要自定义代码。
  
    
    

## 连接器框架增强
<a name="SP15Searchnew_support"> </a>

使用 SharePoint 2013 Search，您可以检索可通过使用连接器框架对其进行爬网的自定义外部数据源中存储的内容的声明信息。
  
    
    
连接器框架还提供改进的异常捕获和日志记录功能，以帮助您解决使用内置于连接器框架顶部的自定义连接器对内容源进行爬网时遇到的错误。有关连接器框架的信息，请参阅  [SharePoint 2013 中的搜索连接器框架](search-connector-framework-in-sharepoint-2013.md)。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [使用 SharePoint Search 搜索新内容](searching-new-content-with-sharepoint-search.md)
    
  
-  [配置 SharePoint 2013 中的搜索功能](configure-search-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中生成搜索查询](building-search-queries-in-sharepoint-2013.md)
    
  
-  [如何：对 SharePoint Server 搜索结果使用自定义安全修整程序](how-to-use-a-custom-security-trimmer-for-sharepoint-server-search-results.md)
    
  

