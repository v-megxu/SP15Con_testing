---
title: VSS 请求程序和 SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 0b2e5a4e-40f0-4ccf-a21a-7274921f2169
---


# VSS 请求程序和 SharePoint 2013
 **摘要：** 了解卷影复制服务 (VSS) 系统的请求程序系统如何使用 Microsoft SharePoint 2013。
Windows Server 中的 VSS 可用于创建可备份和还原 Microsoft SharePoint Foundation 的应用程序。VSS 提供了一个基础结构，使第三方存储管理程序、业务程序，以及硬件提供程序进行合作，以创建和管理卷影副本。基于此基础结构的解决方案可以使用卷影副本（或镜像副本）来备份和还原一个或多个 SharePoint Foundation 数据库。
  
    
    


## VSS 请求程序系统

VSS 在请求程序（备份应用程序）、编写器（如 SharePoint Foundation 和 Microsoft SQL Server 之类的 Windows 应用程序）以及提供程序（系统、软件或用于创建卷影副本的硬件组件）之间进行协调。若要使用 VSS 功能来备份 SharePoint Foundation，备份程序必须包括了解 SharePoint Foundation 的 VSS 请求程序。由于 Windows Server 提供的备份程序不具备这些请求程序，组织必须使用第三方备份应用程序。
  
    
    
为了符合 SharePoint Foundation 的要求，基于 VSS 的备份应用程序必须遵循两个基本要求，以确保卷影副本备份的完整性和可恢复性。客户应与其备份供应商一同验证备份应用程序是否满足本主题中列出的 SharePoint Foundation 的合规性要求。
  
    
    
以下是卷影副本备份应用程序必须遵循的 SharePoint Foundation 要求，以确保 SharePoint Foundation 数据库的完整性和可恢复性。 
  
    
    

- SharePoint Foundation 数据库和搜索索引文件必须专门通过 SPF-VSS 编写器进行备份。
    
  
- 备份应用程序必须验证卷影副本备份集的完整性。还原到原始位置的操作必须专门由 SPF-VSS 编写器执行。
    
  

## 还原

在执行还原操作之前，必须满足以下条件：
  
    
    

- 以下服务必须 *启动*  ：
    
  - SharePoint VSS 编写器
    
  
  - 卷影副本
    
  
  - SharePoint 跟踪
    
  
- 以下服务必须 *停止*  ：
    
  - SharePoint 管理
    
  
  - SharePoint 搜索
    
  
  - SharePoint 计时器
    
  
  - SharePoint Server 搜索（如果已安装 SharePoint Server。）
    
  
- 如果还原的是整个服务器场，则 SharePoint Foundation *和 Internet 信息服务器 (IIS)*  必须关闭。
    
  
- 如果仅还原选定 Web 应用程序或其他组件，则 Web 应用程序必须关闭，并且在还原过程中不能使用这些组件。
    
  

## 后续步骤
<a name="Next"> </a>

了解如何创建并使用适用于 SharePoint 2013 的 VSS 请求程序：
  
    
    

-  [如何：创建用于 SharePoint 2013 的 VSS 请求程序](how-to-create-a-vss-requestor-for-use-with-sharepoint-2013.md)
    
  
-  [如何：使用 VSS 请求程序备份和还原 SharePoint 2013](how-to-back-up-and-restore-sharepoint-2013-using-a-vss-requestor.md)
    
  
-  [如何：在 SharePoint 2013 中使用 VSS 备份和还原搜索服务应用程序](how-to-back-up-and-restore-a-search-service-application-in-sharepoint-2013-using.md)
    
  

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 和卷影复制服务概述](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  
-  [如何：创建用于 SharePoint 2013 的 VSS 请求程序](how-to-create-a-vss-requestor-for-use-with-sharepoint-2013.md)
    
  
-  [如何：使用 VSS 请求程序备份和还原 SharePoint 2013](how-to-back-up-and-restore-sharepoint-2013-using-a-vss-requestor.md)
    
  
-  [如何：在 SharePoint 2013 中使用 VSS 备份和还原搜索服务应用程序](how-to-back-up-and-restore-a-search-service-application-in-sharepoint-2013-using.md)
    
  

