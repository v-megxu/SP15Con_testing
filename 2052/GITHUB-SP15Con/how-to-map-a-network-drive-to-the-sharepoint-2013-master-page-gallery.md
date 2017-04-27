---
title: 如何：将网络驱动器映射到 SharePoint 2013 母版页样式库
ms.prod: SHAREPOINT
ms.assetid: 7d416f6e-2471-4d03-97ae-4e8d907784c6
---


# 如何：将网络驱动器映射到 SharePoint 2013 母版页样式库
了解如何将网络驱动器映射到母版页样式库，以便您可以使用设计管理器将设计文件上载到 SharePoint Server 2013 中。
您可以通过使用任何 Web 设计工具或 HTML 编辑器为您的网站创建可视化设计，然后使用设计管理器将该设计导入到 SharePoint 中。为此，您必须确保设计工具将其文件存储在您的网站的母版页样式库中，SharePoint 预期在其中查找文件。建议您将网络驱动器映射到母版页样式库以便可以更轻松地将文件保存在正确位置。
  
    
    

首先，查找母版页样式库的位置。
### 查找母版页样式库的位置


1. 在要为其创建设计的网站上，启动设计管理器。（例如，在"设置"菜单上，选择"设计管理器"。）
    
    > **重要信息**
      > 如果您的网站位于 SharePoint Online 中，则当您通过使用 Office 365 凭据登录到网站时，确保选中了"保持登录"复选框。有关详细信息，请参阅 [如何配置连接到 Office 365 企业版中的 SharePoint Online 网站的映射网络驱动器并进行故障排除](http://support.microsoft.com/kb/2616712/zh-cn)。 
2. 在编号列表中，选择"上载设计文件"。
    
  
3. 设计管理器："上载设计文件"页包含母版页样式库的位置。位置可能以  `/_catalogs/masterpage/` 结尾。这是您将把网络驱动器映射到的位置。
    
  
4. 记下母版页样式库的位置，或将它复制到剪贴板。
    
  
在运行您的设计工具或 HTML 编辑器的计算机上，将网络驱动器映射到您刚才复制的位置。映射网络驱动器的过程将因计算机的操作系统而异：
- 如果计算机运行的是 Windows 8，请按照 [创建网络驱动器的快捷方式（映射）](http://windows.microsoft.com/zh-CN/windows-8/create-shortcut-to-map-network-drive)一文的 Windows 8 版中描述的步骤操作。
    
  
- 如果计算机运行的是 Windows 7，请按照 [创建网络驱动器的快捷方式（映射）](http://windows.microsoft.com/zh-cn/windows7/create-a-shortcut-to-map-a-network-drive)一文的 Windows 7 版本中介绍的步骤操作。
    
  
- 如果计算机运行的是 Windows Vista，请按照 [创建网络驱动器的快捷方式（映射）](http://windows.microsoft.com/zh-cn/windows-vista/create-a-shortcut-to-map-a-network-drive)一文的 版本中介绍的步骤操作。
    
  
- 如果计算机运行的是 Windows XP，请按照 [如何在 Windows XP 中连接和断开网络驱动器](http://support.microsoft.com/kb/308582/zh-cn)一文中介绍的步骤操作。
    
  
- ** *如果计算机运行的是其他操作系统，请按照为该操作系统创建新位置的快捷方式的说明操作。* ** 您可能必须提供不同凭据来连接到 SharePoint 网站，并且您可能必须指定每次登录到计算机时都重新建立的连接。
    
  

## 其他资源
<a name="bk_addresources"> </a>


-  [如何：向 SharePoint 2013 中的网站应用母版页](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 设计管理器设备通道](sharepoint-2013-design-manager-device-channels.md)
    
  
-  [如何：在 SharePoint 2013 设计管理器中更改预览页面](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [SharePoint 2013 设计管理器图像呈现形式](sharepoint-2013-design-manager-image-renditions.md)
    
  

