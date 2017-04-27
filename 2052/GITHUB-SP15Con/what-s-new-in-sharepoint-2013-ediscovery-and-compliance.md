---
title: SharePoint 2013 eDiscovery 和合规中的新增内容
ms.prod: SHAREPOINT
ms.assetid: 39a1cc3f-c78d-478f-8c15-928b96386a52
---


# SharePoint 2013 eDiscovery 和合规中的新增内容
了解 SharePoint 2013 在电子数据展示和合规性方面的新功能。使用这些功能来管理和恢复民事诉讼中的证据。
## SharePoint 2013 在电子数据展示和合规性方面的新功能

在 SharePoint 2013 中，您可以使用电子数据展示和合规性功能来管理在民事诉讼中使用的证据，以及管理企业的记录。SharePoint 2013 还提供对 Content Management Interoperability Services (CMIS) 互操作性标准的内在支持。若要了解有关 CMIS 的更多信息，请参阅  [OASIS 网站](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=cmis)（https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=cmis）上的标准规范。
  
    
    

### SharePoint 2013 中的电子数据展示

"展示"是用于在民事诉讼中恢复证据的法律过程。SharePoint Server 2010 提供了电子数据展示 (eDiscovery) 功能和 API 作为其记录管理功能集的一部分。SharePoint 2013 提供了经过大幅扩展和修订的电子数据展示功能。电子数据展示的关键功能和 API 包括：
  
    
    

- **案例管理器** ，它使记录管理者可以创建和管理企业范围的展示项目，保留潜在的大量和多种类型的内容，并保留一个内容快照。
    
  
- **企业范围的访问** ，它能够保留内容，并从一个中心位置搜索内容。它还能够开展搜索、访问 SharePoint 内容，以及在配置的任何 SharePoint 位置保留内容。
    
  
- **就地保留** ，它使律师可以保留内容快照，同时确保用户可以继续进行更改而不影响内容快照的状态。
    
  
- **分析** ，它使律师、管理员和记录管理者能够收集和分析有关电子数据展示活动的数据。
    
  

### 记录管理可编程性有哪些新增内容？

.NET 服务器编程模型在 SharePoint 2013 中经过更新，具备了管理项目细节和获得项目元数据的新功能。具备新功能的类包括：
  
    
    

-  [ProjectPolicy](https://msdn.microsoft.com/library/Microsoft.Office.RecordsManagement.InformationPolicy.ProjectPolicy.aspx) 类。您可以使用此类来自定义项目策略的细节。
    
  
- 所有的  [Microsoft.Office.RecordsManagement.Preservation](https://msdn.microsoft.com/library/Microsoft.Office.RecordsManagement.Preservation.aspx) 类。这些类使您能够自定义如何保留信息和管理状态信息。
    
  
-  [Microsoft.Office.RecordsManagement.SearchAndProcess](https://msdn.microsoft.com/library/Microsoft.Office.RecordsManagement.SearchAndProcess.aspx) 类。使用这些类可以创建和管理搜索参数。
    
  

### 内容管理互操作性服务 (CMIS) 创建器

在 SharePoint Server 2010 发布数月后，CMIS 创建器作为 SharePoint 管理员工具包的一部分被引入。它在 SharePoint 2013 中经过彻底重新设计。当您要迁移数据、为产品创建存储库图形用户界面以及将数据从创作应用程序保存到内容管理系统时，CMIS 创建器特别有用。CMIS 创建器支持基本文件管理操作，例如创建、更新、删除、签入签出以及管理不同版本的文档和文档元数据。
  
    
    
CMIS 标准是 OASIS 标准，各内容管理系统可用它来实现互操作。
  
    
    
SharePoint 2013 中 CMIS 连接器的增强功能包括：
  
    
    

- 支持 CMIS 1.0。
    
  
- 能够在运行 SharePoint 列表网络服务的大多数创作环境中使用。
    
  
- 支持声明环境中的互操作。
    
  
- 支持与他创作协议的互操作，这些协议包括基本身份验证、NTLM 身份验证、摘要式身份验证、Kerberos 协议转换/约束委派、Windows 声明身份验证、声明多重身份验证和混合身份验证。
    
  
CMIS 客户 Web 部件已从 SharePoint 2013 中删除。
  
    
    

### 项目合规性

网站以及其他大型对象有时要求用户遵守特定使用策略。为了支持这些方案，SharePoint 2013 中的企业内容管理可以将策略应用于 SharePoint 网站、SharePoint 网站内容和相关联的邮箱，以及将策略流应用于相关联的邮箱。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的 eDiscovery](ediscovery-in-sharepoint-2013.md)
    
  

