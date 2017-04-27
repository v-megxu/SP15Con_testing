---
title: SharePoint 2013 中的 URL 和标记
ms.prod: SHAREPOINT
ms.assetid: 161418d7-8123-4c4e-91a1-97e43c17f0e6
---



# SharePoint 2013 中的 URL 和标记
了解如何表述 URL 以及如何在 SharePoint 2013 中使用 URL 标记。
|||
|:-----|:-----|
|**本文内容**          [SharePoint 2013 中的 URL 的类型](#TypesOfURLs)           [图像 URL 的最佳实践](#GoodPracticeImageURL)           [SharePoint 2013 中的 URL 标记](#URLtokens)           [其他资源](#SP15URLS_addlresources)||
   

## SharePoint 2013 中的 URL 的类型
<a name="TypesOfURLs"> </a>

SharePoint 2013 可根据指定协议（如 **http:**）或字符串中左斜线 (/) 的位置来分析 URL 字符串以确定 URL 的格式。您可以根据具体的成员使用以下 URL 格式：
  
    
    

- **绝对 URL** 指定完整路径并以协议开头。例如， `http://` _domain_or_server_/[ `sites/`] _Web_Site_/ `Lists`/ _List_Title_/ `AllItems.aspx`。
    
  
- **相对于域的 URL** 基于域（可能为服务器的名称）地址并始终以正斜杠开头。它指定从首要网站到文件名的完整路径。例如，/[ `sites/`] _Web_Site_/ `Lists`/ _List_Title_/ `AllItems.aspx`。 
    
  
- **相对于网站的 URL** 基于网站对象的地址 ( [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) )。它 _不_ 以正斜杠开头，并指定从网站地址到文件名的完整路径。例如， `Lists/` _List_Title_/ `AllItems.aspx`。
    
  
- **相对于文件或文件夹的 URL** 基于包含文件的文件夹。它不包含 _任何_左斜杠，而仅指定文件的名称。例如， `AllItems.aspx`。
    
  

> **注释**
> 不存在"相对于网站集的 URL"这一概念；传递此类 URL 可能会导致代码失败。 
  
    
    


## 图像 URL 的最佳实践
<a name="GoodPracticeImageURL"> </a>

在创建指向位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\IMAGES 目录中的图像文件的 URL 时，指定一个使用网站集的根网站的路径，但该路径不包含子网站。例如，对图像文件使用 /_layouts/images/MyImage.gif 而不是 /MySubsite/_layouts/images/MyImage.gif。这是因为，将通过不同的方式解析子网站 URL，具体取决于在何处使用它们。如果您始终使用相对于根网站的 URL，则可以忽略这些变化。
  
    
    

## SharePoint 2013 中的 URL 标记
<a name="URLtokens"> </a>

SharePoint 2013 允许在 SharePoint 外接程序或场解决方案中使用在以下各表中列出的标记。有关详细信息，请参阅  [SharePoint 外接程序中的 URL 字符串和标记](http://msdn.microsoft.com/library/800ec8cd-a448-46bc-b41e-d4030eeb4048%28Office.15%29.aspx)。
  
    
    
在 SharePoint 开发的各种不同情景下，可在 URL 中使用本节表格中的标记，这些情景包括自定义操作和自定义页面上的链接。在某些上下文中，其中一些标记不可使用。只可使用有限标记的三个最重要位置是应用程序的起始页、主机 Web 的自定义操作和应用程序部件的  [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) 属性。这三个位置在单独的列中标注，但这三者不构成可以使用标记的位置的详尽列表。
  
    
    
 **StartPage** 列将指定是否可以在应用程序清单的 **StartPage** 元素中使用令牌。 **自定义操作** 列将指定是否可以在托管 Web 的自定义操作的 URL 中使用令牌。 **应用程序部件** 列将指定是否可以在应用程序部件的 [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) 属性中使用令牌。
  
    
    

**可在 URL 的开头使用的标记**


|**标记**|**解析为**|**StartPage**|**自定义操作**|**应用程序部件**|**备注**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|~controlTemplates  <br/> |当前网站的 ControlTemplates 虚拟文件夹的 URL。  <br/> |否  <br/> |否  <br/> |否  <br/> ||
|~layouts  <br/> |当前网站的 Layouts 虚拟文件夹的 URL。  <br/> |否  <br/> |否  <br/> |否  <br/> ||
|~site  <br/> |当前网站的 URL。  <br/> |否  <br/> |否  <br/> |是  <br/> ||
|~sitecollection  <br/> |当前网站的父网站集的 URL。  <br/> |否  <br/> |否  <br/> |是  <br/> ||
   
除非另有规定，否则下个表格中的任何标记都不可在应用程序部件的  [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) 属性值的 *路径*  部分使用。 **应用程序部件** 列是指这些标记在值的 *查询字符串*  部分的使用。
  
    
    

**可在 URL 内使用的标记**


|**标记**|**解析为**|**StartPage**|**自定义操作**|**应用程序部件**|**备注**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|{ControlTemplates}  <br/> |当前网站的 ControlTemplates 虚拟文件夹的 URL。  <br/> |否  <br/> |否  <br/> |否  <br/> ||
|{ItemId}  <br/> |列表或库中的项目的 ID（整数）。  <br/> |否  <br/> |是  <br/> |否  <br/> ||
|{ItemUrl}  <br/> |正在处理的项的 URL。  <br/> |否  <br/> |是  <br/> |否  <br/> ||
|{Layouts}  <br/> |当前网站的 Layouts 虚拟文件夹的 URL。  <br/> |否  <br/> |否  <br/> |否  <br/> ||
|{ListId}  <br/> |当前列表的 ID（一个 GUID）。  <br/> |否  <br/> |是  <br/> |否  <br/> ||
|{RecurrenceId}  <br/> |定期事件的定期索引。  <br/> |否  <br/> |是  <br/> |否  <br/> |不支持将该标记用于列表项的上下文菜单中。  <br/> |
|{Site}  <br/> |当前网站的 URL。  <br/> |否  <br/> |是  <br/> |是  <br/> ||
|{SiteCollection}  <br/> |当前网站的父网站的 URL。  <br/> |否  <br/> |是  <br/> |是  <br/> ||
|{SiteUrl}  <br/> |当前网站的 URL。  <br/> |否  <br/> |是  <br/> |否  <br/> ||
|{Source}  <br/> |HTTP 请求 URL。  <br/> |否  <br/> |是  <br/> |否  <br/> ||
   

## 其他资源
<a name="SP15URLS_addlresources"> </a>


-  [在 SharePoint 2013 中生成场解决方案](build-farm-solutions-in-sharepoint-2013.md)
    
  
-  [高级 Extranet 支持](http://msdn.microsoft.com/library/21d67796-23c5-4339-8f0e-124208d21ab2%28Office.15%29.aspx)
    
  
-  [获取对网站、Web 应用程序和其他关键对象的引用](http://msdn.microsoft.com/library/8623ef1d-e3cc-426c-84a3-6379e0ae284f%28Office.15%29.aspx)
    
  
-  [使用列表对象和集合](http://msdn.microsoft.com/library/d4167b10-6f1e-49f1-8b22-16ce20012a27%28Office.15%29.aspx)
    
  
-  [示例对象模型任务](http://msdn.microsoft.com/library/94d6898d-6a0f-43a7-ad06-1b27ec6916ea%28Office.15%29.aspx)
    
  
