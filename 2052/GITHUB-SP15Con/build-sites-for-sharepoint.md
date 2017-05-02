---
title: 为 SharePoint 构建网站
ms.prod: SHAREPOINT
ms.assetid: 3b372a63-7cdf-462a-abb4-750e611e967d
---


# 为 SharePoint 构建网站
了解 SharePoint 2013 中网站的新网站创作和发布模型。
## SharePoint 中的网站发布简介（针对设计人员和开发人员）
<a name="SP15_BuildSitesForSP2013_IntroToSitePublishing"> </a>

SharePoint 2013 介绍网站创作和发布模型来创建发布网站。可以使用发布内容在 Intranet 或 Internet 网站中发布内容。发布网站与其他类型的 SharePoint 网站（例如工作组网站）不同，主要是因为其用途 - 许多用户读取发布网站内容，但仅有少数用户通过从一个或多个网站集中添加、更新和删除内容来参与网站内容。将这些网站与工作组网站进行比较，在工作组网站中许多人员可协作和参与内容。
  
    
    
可以使用 SharePoint 2013 网站发布功能来生成、自定义和维护满足特定业务需要的发布网站。您是具有 HTML、 CSS 和 JavaScript 技能的专业设计者还是编写 SharePoint 应用和使用自定义 .NET 代码来生成网站和场解决方案的开发人员，您可以使用 SharePoint 2013 中的网站功能来管理内容生命周期的所有阶段，包括：
  
    
    

- **Authoring** 和重用网站内容。
    
  
- **Branding** 和设计您的网站外观和行为。
    
  
- **Managing metadata** - 您可以生成分类法驱动的网站导航系统。
    
  
- **Publishing** 顺利满足当前网站集或跨网站集发布内容 - 甚至跨 Intranet 和 Internet 网站界限。
    
  
- **Accessibility** - 您可以用于提高已发布网站的可访问性。
    
  
如果您想查看 SharePoint 2013 中发布网站的最新功能（针对设计人员和开发人员）摘要，请参阅  [SharePoint 2013 网站开发的新增内容](what-s-new-with-sharepoint-2013-site-development.md)。
  
    
    

## SharePoint 中的创作、设计和品牌
<a name="SP15_BuildSitesForSP2013_AuthoringDesignBranding"> </a>

SharePoint 2013 提供一种新方法来设计网站。内容创建工作流已经过修改，以便您可以使用任何工具创建内容和创作重要内容。若要在您的网站上加商标而无需编写自定义 .NET 代码，请使用 [设计管理器](overview-of-design-manager-in-sharepoint-2013.md)来导入设计元素。有设计管理器，您还可以创建基于 HTML 的母版页来定义您的所有网站的网页共享的部件版式，并且创建页面布局来设计页面模版。如果您选择创建自定义代码，则您可以使用 .NET 服务器、 .NET 客户端 (CSOM)、Silverlight 和 JavaScript 库。
  
    
    
SharePoint 2013 还提供一种用于内容和创作的新方法。内容创建工作流已经过修改，以便您可以使用任何创作和品牌工具创建内容和创作重要内容。若要在您的网站上加商标而无需编写自定义 ASP.NET 代码，请使用设计管理器。您可以导入设计元素并创建基于 HTML 的母版页，以便确定您的所有网站的网页以及网页布局共享的框架元素，即版式。如果在您的网站上加上商标时选择编写自定义代码，则可以使用发布和分类法库。
  
    
    

## 发布网站、客户端模型编程以及新 SharePoint 应用模型。
<a name="SP15_BuildSitesForSP2013_PublishingSites"> </a>

您可以使用新 .NET 客户端对象模型 (CSOM) 来开发带 SharePoint 外接程序的模型 的 SharePoint 应用。 您可以使用许多 API，它们还可以提供支持 .NET 客户端、Silverlight、JavaScript 开发（某些情况下支持 Windows Phone 开发）的 .NET 客户端模型中 .NET 服务器编程使用。用于开发网站应用的某些构想包括调查、帐户管理应用、集成社交功能以及发布网站中的外部数据、外包内容附件以及移动伴侣应用。
  
    
    

## 发布网页的页面模型
<a name="SP15_BuildSitesForSP2013_PageModel"> </a>

SharePoint 2013 包括发布网页的页面模型。该页面包括主页、页面布局以及呈现您的网页结构、内容、外观和行为的其他组件。有关详细信息，请参阅  [SharePoint 2013 页面模型概述](overview-of-the-sharepoint-2013-page-model.md)。
  
    
    

## 主页和页面布局
<a name="SP15_BuildSitesForSP2013_MasterAndLayout"> </a>

主页是指定义您的网页的共享结构元素的主模板 - 版式。该网页上的所有页面共享定义显示网页布局内容的网页区域的这些元素。
  
    
    
网页布局供某种类型的个别网页使用。在整理页面字段的同时对其进行填充。这些页面定义该页面上的个别元素。个别网页基于网页布局，并且这些网页可通过自定义代码或通过网页的使用者填充网页的字段的方式在您的 Web 浏览器中进行创建。若要更多了解 SharePoint 2013 中的页面模型，请参阅  [SharePoint 2013 页面模型概述](overview-of-the-sharepoint-2013-page-model.md)。
  
    
    

## 客户端侧呈现控件
<a name="SP15_BuildSitesForSP2013_ClientSideRendering"> </a>

在 SharePoint 2013 中呈现所有的新控件。将数据写入客户端 JSON 数组中的这些控件，并且您可以使用 JavaScript、CSS 和模板显示内容。作为设计者或开发人员，您可以控制在页面上呈现内容的方式，并且可以借助各种设计技术通过使用如 [SharePoint 2013 中的内容搜索 Web 部件](content-search-web-part-in-sharepoint-2013.md)和显示模板的功能来了解您已发布网页上的想要的外观和行为。
  
    
    

## 网站和移动设备
<a name="SP15_BuildSitesForSP2013_SitesAndMobile"> </a>

在 SharePoint 2013 中优化移动开发的发布网站。您可以定义一个或多个设备的通道（设备通道），并且将备用母版页分配给各个通道，向其提供结构元素或版式。您可以选择包括或排除通道中的任何页面布局的各部分，并在开发的同时预览如何进行移动通道设计。
  
    
    

## SharePoint 中的元数据和导航
<a name="SP15_BuildSitesForSP2013_MetadataNav"> </a>

改进 Microsoft SharePoint Server 2010 中介绍的管理元数据功能并在 SharePoint 2013 中进行扩展以提高性能，通过用户界面简化访问以及获得分类法驱动的导航（被称为管理导航。您可以使用基于 SharePoint 网站结构（称为结构导航）的管理导航或导航来构建您的网站导航。有关托管导航的详细信息，请参阅 [SharePoint 2013 中的托管元数据和导航](managed-metadata-and-navigation-in-sharepoint-2013.md)和 [SharePoint 2013 中的托管导航](managed-navigation-in-sharepoint-2013.md)。
  
    
    

## SharePoint 中的发布内容
<a name="SP15_BuildSitesForSP2013_PublishingContent"> </a>

SharePoint 2013 提供以下新的内容发布功能，利用这些功能，您可以开发支持更灵活、更容易使用且更复杂的拓扑和方案的发布网站。
  
    
    

### 目录

SharePoint 2013 介绍了目录，该目录可用于跨网站集发布内容。跨网站发布功能取决于目录。您可以使用它们跨网页或跨 Intranet 网站和 Internet 之间的边界重用内容。对于预定义的搜索查询，目录被标记在搜索中。您可以通过使用 [SharePoint 2013 中的内容搜索 Web 部件](content-search-web-part-in-sharepoint-2013.md) 将存储在网站集的目录中的内容置于表面。
  
    
    

### 跨网站发布

SharePoint 2013 介绍了跨网站发布功能以便跨多个网站集重用内容。它使用内置的搜索功能启用发布方案和架构。首先，您可设计跨 SharePoint 场的网站，以使您的网站在 Intranet 和 Internet之间的边界进行扩展。 您可以使用 CSWP 来显示从网站和网站集中发布的搜索数据。
  
    
    

### 变体和多语种网站

您可以使用 SharePoint 2013 中的变体功能来创建您在其中希望变化内容呈现方式的多语种网站或其他网站。变体功能仅限于一个网站集。也就是，您可以将源语/区域设置的目标语/区域设置"变体"作为同一 SharePoint 网站集内的当前网站创建。变体支持友好型 URL 和以  [XLIFF 文件格式](the-xliff-interchange-file-format-in-sharepoint-2013.md)导出或导入第三方翻译内容。您可以包括标签、翻译和副本页、各种列表项（如文档库）和导出包中的导航。
  
    
    

### 可访问的网站

您可以使用 SharePoint 2013 中的变体功能创建易于访问的网站或其他网站（您可在其中为具有多种可访问性需求的用户调整内容演示）。SharePoint 2013 提供"更易于访问的模式"，您可以通过打开 SharePoint 网页，然后按下 TAB 键，直到找到"打开更易于访问的模式"链接来激活。此功能将重新创建标准 HTML 格式的网页，使其对屏幕阅读器而言更友好。通过确保用户可以按下 TAB 键来关注此链接，您可以创建更易于访问的 SharePoint 网页版本。这包括被转换为超链接列表的基于 JavaScript 的下拉菜单和被转换为更简单的 HTML 的对象，使屏幕阅读器可以理解内容。 
  
    
    

## 其他资源
<a name="SP15_BuildSitesForSP2013_AdditionalResources"> </a>


-  [优化 SharePoint 网站辅助功能](optimize-sharepoint-site-accessibility.md)
    
  
-  [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 网站开发的新增内容](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [最少下载策略概述](minimal-download-strategy-overview.md)
    
  
-  [为 MDS 修改 SharePoint 组件](modify-sharepoint-components-for-mds.md)
    
  
-  [SharePoint 2013 网站和内容服务器类库](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)
    
  
-  [网站和内容客户端类库](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx)
    
  

