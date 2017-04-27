---
title: SharePoint 2013 中的内容搜索 Web 部件
ms.prod: SHAREPOINT
ms.assetid: 6fb4bf41-0846-4dca-ad9e-906afdfd3d2b
---


# SharePoint 2013 中的内容搜索 Web 部件

  
    
    
![概念概述主题](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
了解 SharePoint 2013 中的内容搜索 Web 部件 (CSWP)。
## 内容搜索 Web 部件 (CSWP) 简介
<a name="SP15_CSWP_IntroducingCSWP"> </a>

内容搜索 Web 部件 (CSWP) 是 SharePoint 2013 中引入的一个 Web 部件，使用多个样式选项在 SharePoint 页面上显示动态内容。
  
    
    

## 内容搜索 Web 部件的工作方式
<a name="SP15_CSWP_HowCSWPWorks"> </a>

内容搜索 Web 部件以可轻松设置格式的方式显示搜索结果。每个内容搜索 Web 部件都与搜索查询关联，并显示搜索查询的结果。
  
    
    
可使用显示模板更改搜索结果在页面上的显示方式。显示模板时呈现 SharePoint 返回的信息的 HTML 和 JavaScript 的代码段。要显示的信息插入到 JSON 格式的页面中。 
  
    
    

## 何时使用内容搜索 Web 部件 (CSWP) 或内容查询 Web 部件 (CQWP)
<a name="SP15_CSWP_WhenToUseCSWPorCQWP"> </a>

CSWP 可从搜索索引返回任何内容。在连接到搜索服务，并希望在您的页面上显示已编制索引的搜索结果时，在您的 SharePoint 2013 网站上使用。 
  
    
    
CSWP 返回的内容的新旧程度取决于对您的内容的最新爬网，因此，如果您经常爬网，则CSWP 返回的内容比很少爬网返回的内容更新。如果您需要显示即时内容或已刷新的版本的内容，则改为使用内容查询 Web 部件 (CQWP)。
  
    
    
搜索仅对主要版本的内容进行爬网，而从不对次要版本进行爬网。如果您希望显示次要版本的内容，则使用 CQWP 进行此操作。
  
    
    
一些网站集管理员将网站标记为未编制索引。按此方式标记的内容在 CSWP 中不可用。如果您想要从标记为未编制索引的网站返回结果，则改为使用 CQWP。
  
    
    

## 其他资源
<a name="SP15_CSWP_AdditionalResources"> </a>


-  [SharePoint 2013 中的托管导航](managed-navigation-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 搜索功能中面向开发人员的新增内容](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

