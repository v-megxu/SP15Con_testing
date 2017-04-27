---
title: 使用搜索 REST 服务检索查询建议
ms.prod: SHAREPOINT
ms.assetid: a64c5bec-64a8-4752-9c72-433d1c864aed
---


# 使用搜索 REST 服务检索查询建议
了解如何从客户端和移动应用程序使用搜索 REST 服务，以从 SharePoint 2013 中的搜索功能 检索查询建议。
查询建议（也称为搜索建议）是用户已搜索的短语，在用户键入查询时向其显示或"建议"。您可以使用 SharePoint 2013 中的搜索功能 打开查询前和查询后建议。这些建议会在用户键入查询时显示在搜索框下面的列表中。有关查询建议和如何启用的详细信息，请参阅 [在 SharePoint Server 2013 中管理查询建议](http://technet.microsoft.com/zh-cn/library/jj721441.aspx)。
  
    
    


## 搜索 REST 服务中的建议端点
<a name="bk_SuggestEndpoint"> </a>

搜索 REST 服务包括可用于任何技术的 **Suggest** 端点，只要该技术支持从客户端或移动应用程序使用 REST Web 请求以检索搜索系统针对查询生成的查询建议。
  
    
    
针对搜索 REST 服务 **Suggest** 端点的 **GET** 请求的 URI 为：
  
    
    
 `/_api/search/suggest`
  
    
    
查询建议参数在 URL 中指定。您可以通过两种方式构建请求 URL：
  
    
    


  
    
    
>  `http://server/_api/search/suggest?parameter=value&amp;parameter=value`
    
  

  
    
    
>  `http://server/_api/search/suggest(parameter=value&amp;parameter=value)`
    
  

> **注释**
> 搜索 REST 服务不支持针对 **Suggest** 端点的匿名请求。
  
    
    


## 查询建议参数
<a name="bk_SuggestParameters"> </a>

以下几节介绍了可用于 **Suggest** 端点的参数。
  
    
    

### Querytext

一个包含搜索查询文本的字符串。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'
  
    
    

### iNumberOfQuerySuggestions

要检索的查询建议数量。必须大于零 (0)。默认值为 5。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;inumberofquerysuggestions=3
  
    
    

### iNumberOfResultSuggestions

要检索的个人搜索结果数量。必须大于零 (0)。默认值为 5。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;inumberofresultsuggestions=4
  
    
    

### fPreQuerySuggestions

一个指定是否检索查询前或查询后建议的布尔值。若要返回查询前建议，则选择 **true**；否则，选择 **false**。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fprequerysuggestions=true
  
    
    

### fHitHighlighting

一个指定是否突出显示或加粗显示查询建议的布尔值。若要加粗显示返回的查询建议中与指定查询中的字词匹配的字词，则选择 **true**；否则，选择 **false**。默认值为 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fhithighlighting=false
  
    
    

### fCapitalizeFirstLetters

一个指定是否将返回的查询建议中每个字词的首字母大写的布尔值。若要将每个字词的首字母大写，则选择 **true**；否则，选择 **false**。默认值为 **false**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fcapitalizefirstletters=false
  
    
    

### 区域性

查询的区域设置 ID (LCID)（请参阅  [Microsoft 分配的区域设置 ID](http://msdn.microsoft.com/zh-cn/goglobal/bb964664.aspx)）。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;culture=1044
  
    
    

### EnableStemming

一个指定是否启用词干分解的布尔值。若要启用词干分解，则选择 **true**；否则，选择 **false**。默认值为 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;enablestemming=false
  
    
    

### ShowPeopleNameSuggestions

一个指定是否在返回的查询建议中包含人员姓名的布尔值。若要在返回的查询建议中包含人员姓名，则选择 **true**；否则，选择 **false**。默认值为 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;showpeoplenamesuggestions=false
  
    
    

### EnableQueryRules

一个指定是否对此查询启用查询规则的布尔值。若要启用查询规则，则选择 **true**；否则，选择 **false**。默认值为 **true**。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    

### fPrefixMatchAllTerms

一个指定是否针对前缀匹配返回查询建议的布尔值。若要根据前缀匹配返回查询建议，则选择 **true**；否则，选择 **false**（查询建议应与网站查询字词匹配）。
  
    
    
 **示例 GET 请求**
  
    
    
http:// _server_/_api/search/suggest?querytext='sharepoint'&amp;fprefixmatchallterms=false
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint Search REST API 概述](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint 2013 中的搜索](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013：从 SharePoint 相关应用程序使用搜索 REST 服务](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [SharePoint 2013 搜索功能中面向开发人员的新增内容](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

