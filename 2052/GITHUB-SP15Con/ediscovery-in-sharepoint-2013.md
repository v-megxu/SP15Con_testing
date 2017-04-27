---
title: SharePoint 2013 中的 eDiscovery
ms.prod: SHAREPOINT
ms.assetid: 45cb324a-75f5-444d-a0fa-5c223df19016
---


# SharePoint 2013 中的 eDiscovery
在 SharePoint 2013 中了解电子数据展示功能。您可以使用电子数据展示以便向诉讼人提供搜索该功能电子格式的内容的功能。
## SharePoint 2013 中的电子数据展示的简介
<a name="SP15_eDiscoveryInSP_IntroductionToeDiscovery"> </a>

电子数据展示是指记录管理者和诉讼人如何搜索电子格式的内容。通常，电子数据展示需要搜索在便携式计算机上分布的文档、网站和电子邮件、电子邮件服务器、文件服务器和其他来源，并在满足法律案件的条件的内容上进行收集和使用。
  
    
    
在 SharePoint Server 2010 中，Microsoft 添加了保留和电子数据展示功能，该功能尽可能保留 SharePoint 中的任何网站。记录管理者可能保留文档、页面和列表项，这将阻止用户删除会编辑它们。Exchange 2010 介绍了某种方式来保留邮箱，执行跨多个邮箱搜索并使用 Windows PowerShell cmdlet 来导出邮箱。
  
    
    
SharePoint 2013 和 中的电子数据展示包括新方式来减少搜索的成本和复杂性。这些包括：
  
    
    

- **电子数据展示中心**，用于管理 Exchange 和 SharePoint（跨 SharePoint 场和 Exchange 服务器） 中存储的内容的演示文稿、搜索和导出的中央 SharePoint 网站。
    
  
- **SharePoint In-Place Hold**，保留整个 SharePoint 网站。就地保留保护该网站内的所有温度、页面和列表项，但允许用户继续编辑和删除保留的内容。 
    
  
- **Exchange In-Place Hold**，保留 Exchange 邮箱。In-Place Hold 通过相同 UI 和 API（用于保留 SharePoint 网站）保护所有邮箱内容。
    
  
- **基于查询的演示文稿** 可让用户将查询筛选器应用到一个或多个 Exchange 邮箱和 SharePoint 网站，并限制保留的内容。
    
  

## 电子数据展示在 SharePoint 2013 中工作方式
<a name="SP15_eDiscoveryInSP_HoweDiscoveryWorks"> </a>

电子数据展示将搜索服务应用程序 (SSA) 用于对 SharePoint 场进行爬网。您可以以多种方式来配置 SSA，但最常用方式是使用中央搜索服务场对多个 SharePoint 场进行爬网。您可以使用这个搜索服务对所有 SharePoint 内容进行爬网，或可以将其用于对特定区域（例如，位于欧洲的所有 SharePoint 内容）进行爬网。
  
    
    
若要对 SharePoint 场进行爬网，搜索首先使用要与其连接的服务应用程序代理。电子数据展示中心使用代理连接以便向在其他 SharePoint 场中的 SharePoint 网站发送演示文档。
  
    
    

## 先决条件
<a name="SP15_eDiscoveryInSP_Prerequisites"> </a>

在部署 SharePoint Server 电子数据展示功能之前，您应该计划贵公司的搜索服务应用程序基础架构。例如，如果您具有对特定几组 SharePoint 网站爬网的两个独立的 SSA，则您将需要针对各 SSA 的一个电子数据展示中心。
  
    
    

## 网站保留
<a name="SP15_eDiscoveryInSP_SiteHolds"> </a>

SharePoint 保留网站级别上的内容。在您保留网站时，保留其列表、库和子网站。如果您保留根网站集，则保留该网站集中所有文档、页面和子网站。
  
    
    
若要保留某网站，在电子数据展示中心中创建 Discovery Case。 某案例是与特定诉讼关联的所有查询、内容和演示文档的容器。在您创建该案例之后，创建 Discovery Set 来指定该网站。若要验证该网站，只需访问其 URL 地址。
  
    
    
In-Place Hold 通过保留其实时的内容（在同一时间完成发现搜索）工作。在编辑或删除内容项时，电子数据展示在修改内容的 SharePoint 网站（称为 Preservation Hold Library）上复制特定文档库中的项。只有搜索索引器以及具有网站及管理员权限或 Web 应用程序权限的用户可以访问 Preservation Hold Library。不具有这些权限的大多数用户未看到该库，并且不知道它是否存在或是否对其内容进行复制。
  
    
    
若要以某种方式（最大程度地减少存储控件和最大程度地提高效率）保存内容，电子数据展示使用写入时复制来管理同一信息的相同副本。由于将不会对保留的大多数内容进行修改，因此没有理由通过复制来占据空间。反之，就地演示文档仅在删除各项时或在首次更改各项（启动演示文档后）之后对其进行复制。如果再次更改某文档，则电子数据展示仅保存当前签入或删除版本，并且该版本是在初始保留文档时创建的。
  
    
    
如果在某网站上进行多次保留，则再次复制下一个编辑的文档I，尽管可能在首次保存时已对其进行复制。
  
    
    

## 电子数据展示编程模型
<a name="SP15_eDiscoveryInSP_eDiscoveryProgrammingModel"> </a>

SharePoint 2013 提供可用于生成自定义解决方案以及包括电子数据展示功能的应用的 Microsoft .NET 服务器编程模型。表 1 列出了 **Microsoft.Office.Server.Discovery** 命名空间中的类型。
  
    
    

**表 1. 电子数据展示类型**


|**类型**|**说明**|
|:-----|:-----|
| [Case](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Case.aspx) <br/> |表示电子数据展示案例。案例与指定的  [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) 对象关联，它可以在指定日期关闭或作为特定操作关闭。案例可以包含来源组、位置、邮箱、保管人、保存的搜索、导出、指定 ID 的导出配置、查询以及此 **Case** 对象中所有来源组、保管人和位置的列表。 <br/> |
| [Custodian](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Custodian.aspx) <br/> |表示负责保留电子数据展示案例记录的人员。  <br/> |
| [CustodianCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.CustodianCollection.aspx) <br/> |表示 **Custodian** 对象的集合。 <br/> |
| [DiscoveryDuplicateSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.DiscoveryDuplicateSourceCollection.aspx) <br/> |在 **Source** 对象的值不唯一时将引发异常。 <br/> |
| [DiscoveryException](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.DiscoveryException.aspx) <br/> |特定于电子数据展示 API 的异常，它携带一条消息并且还可能携带内部异常。  <br/> |
| [Export](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Export.aspx) <br/> |表示与特定 **Case** 对象关联的导出。 **Export** 对象可以从 **T:Microsoft.SharePoint.SPListItem** 对象进行构造。您可以将 **SavedSearch** 对象添加到 **Export** 对象，并且可以选择权限管理并下载 **Export** 对象。 <br/> |
| [ExportCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.ExportCollection.aspx) <br/> |表示 **Export** 对象的集合。 <br/> |
| [ExportStatus](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.ExportStatus.aspx) <br/> |表示导出的状态，它可以指示导出是否已开始、未开始、已完成或已完成但失败。  <br/> |
| [SavedSearch](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SavedSearch.aspx) <br/> |表示一个保存的电子数据展示搜索。 **SavedSearch** 对象可以复制、删除或更新。与保存的搜索关联的统计信息可以进行更新。搜索优化条件、Exchange 2013 优化条件、来源 ID、来源组 ID、查询和筛选器可以与 **SavedSearch** 对象关联。 <br/> |
| [SavedSearchCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SavedSearchCollection.aspx) <br/> |表示 **SavedSearch** 对象的集合。 <br/> |
| [Source](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Source.aspx) <br/> |表示电子数据展示操作中使用的数据源类型。 **Source** 对象携带特定的 **Case** 对象、一类数据源和一个筛选器（即识别来源的容器的部分或完整规范）作为参数。可以返回关于来源的信息，例如其保存状态、SharePoint 创建索引时来源的位置以及来源是否为邮箱。 <br/> |
| [SourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceCollection.aspx) <br/> |表示 **Source** 对象的集合。 <br/> |
| [SourceGroup](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceGroup.aspx) <br/> |表示一组 **Source** 对象。 <br/> |
| [SourceGroupCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceGroupCollection.aspx) <br/> |表示 **SourceGroup** 对象的集合。 <br/> |
| [SourceManagementType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceManagementType.aspx) <br/> |表示管理的来源范围。选项包括来源、来源组和所有内容。  <br/> |
| [SourceType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceType.aspx) <br/> |表示来源类型。来源类型包括 Exchange 2013、SharePoint Server 的当前及更早版本以及文件共享。  <br/> |
| [SourceValidation](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceValidation.aspx) <br/> |指示来源是否有效。  <br/> |
   

## 其他资源
<a name="SP15_eDiscoveryInSP_AdditionalResources"> </a>


-  [SharePoint 2013 eDiscovery 和合规中的新增内容](what-s-new-in-sharepoint-2013-ediscovery-and-compliance.md)
    
  
-  [使用 SharePoint 2013 客户端库代码完成基本操作](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  

