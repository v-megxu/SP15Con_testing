---
title: 在 SharePoint 2013 中生成搜索查询
ms.prod: SHAREPOINT
ms.assetid: c4372fcc-4574-4c81-a345-a1bb282ca8f7
---


# 在 SharePoint 2013 中生成搜索查询
了解 SharePoint Server 2013 支持用于构建查询规则和搜索查询的搜索语法。
## SharePoint Server 2013 支持用于构建搜索查询的搜索语法
<a name="SP15Buildquery_support"> </a>

SharePoint Server 2013 搜索支持使用关键字查询语言 (KQL) 和 FAST 查询语言 (FQL) 搜索语法来构建搜索查询。
  
    
    
 **关键字查询语言 (KQL)**
  
    
    
KQL 是构建搜索查询的默认查询语言。使用 KQL，您可以指定传递给 SharePoint 搜索服务的搜索字词或属性限制。
  
    
    
 **FAST 查询语言 (FQL)**
  
    
    
FQL 是结构化查询语言，支持高级查询运算符。在需要创建希望以编程方式传递给 SharePoint 搜索服务的复杂查询时，可以使用 FQL。FQL 不适合对最终用户公开，默认情况下，FQL 已禁用。 
  
    
    
若要启用 FQL，请使用 **EnableFQL** 属性。然后复制默认结果源，并通过以下方式之一修改查询转换字符串 `{?{searchTerms} -ContentClass=urn:content-class:SPSPeople}`，应至少在以下一个级别执行此操作 -- Search Service Application (SSA)、网站集或网站。
  
    
    

- 从查询转换中删除 KQL 筛选器  `-ContentClass:urn:content-class:SPSPeople`。生成的查询转换字符串为： `{?{searchTerms}}`
    
  
- 将此查询转换字符串替换为 FQL 等效项，例如  `{?andnot({searchTerms},filter(contentclass:"urn:content-class:SPSPeople*"))}`。
    
  
有关结果源和工作原理的详细信息，请参阅： [了解结果源](http://office.microsoft.com/zh-cn/support/sharepoint/sharepointsearch/understanding-result-sources-HA102848849.aspx)和 [在 SharePoint Server 2013 中配置搜索的结果源](http://technet.microsoft.com/zh-cn/library/jj683115%28v=office.15%29.aspx)。
  
    
    

## 本节内容
<a name="SP15Buildquery_support"> </a>


-  [关键字查询语言 (KQL) 语法参考](keyword-query-language-kql-syntax-reference.md)
    
  
-  [FAST 查询语言 (FQL) 语法参考](fast-query-language-fql-syntax-reference.md)
    
  
-  [使用 SharePoint 2013 搜索查询 API](using-the-sharepoint-2013-search-query-apis.md)
    
  

## 其他资源
<a name="SP15Buildquery_addlresources"> </a>


-  [SharePoint 2013 中的搜索](search-in-sharepoint-2013.md)
    
  
-  [SharePoint Server 2013 中的查询处理概述](http://technet.microsoft.com/zh-cn/library/jj219620%28v=office.15%29.aspx)
    
  
-  [SharePoint Server 2013 中的查询变量](http://technet.microsoft.com/zh-cn/library/jj683123.aspx)
    
  

