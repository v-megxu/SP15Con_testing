---
title: SharePoint 2013 解决方案中的虚拟目录
ms.prod: SHAREPOINT
ms.assetid: c26c4160-31be-4358-89cf-082b8a1e6a6c
---


# SharePoint 2013 解决方案中的虚拟目录
了解虚拟目录系统中的变化如何影响在 SharePoint 2013 中创建 服务器场解决方案的方法。
## 使您的解决方案与新的 UI 模式系统兼容

如果您使用的是 Microsoft SharePoint 2010 软件开发工具包 (SDK)，但要针对 SharePoint 2013 进行开发，则需要在工作时考虑虚拟目录系统中的一项变化。该变化是新 SharePoint 2013 功能的不利影响，该功能允许网站集以 SharePoint 2010 模式或 SharePoint 2013 模式运行。这些模式有时称为兼容级别或 UI 版本。对于虚拟文件夹  `_layouts` 或 `_controltemplates` 中的文件，SharePoint 需要使用 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\（有时称为15 hive）或相应 14 hive 中的文件版本，具体取决于网站集的模式。一旦虚拟目录名称表明应使用 SharePoint 2013 文件，SharePoint 即会将"/15"添加到虚拟目录路径。如果没有该额外字符串，则表示不应使用 SharePoint 2010 文件。
  
    
    
这一新系统对您开发 SharePoint 2013 解决方案和应用程序有一定影响，特别是使用 SharePoint 2010 SDK 的情况下。在任何 SharePoint 外接程序（仅以 SharePoint 2013 模式运行）和任何 SharePoint 解决方案（您已知将仅用于以 SharePoint 2013 模式运行的网站集）中，您需要自行将"/15" 添加到您在解决方案/应用程序中创建的  `_layouts` 和 `_controltemplates` 虚拟路径中。（除非路径指向 *.aspx 文件），即使该字符串未显示在您在 SharePoint 2010 SDK 中阅读的任何说明中，也应该这样做。例如，如果 SharePoint 2010 SDK 指示您使用 `~/_layouts/images/myimage.png`，那么您应在针对 SharePoint 2013 开发时使用  `~/_layouts/15/images/myimage.png`。
  
    
    
如果您需要让解决方案与任一模式的网站集兼容，则需要分支逻辑来确定当前网站集的模式，并构建相应虚拟路径。 [CompatibilityLevel](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.CompatibilityLevel.aspx) 属性是可供代码检查模式的一个位置，也适用于所有 SharePoint 客户端对象模型和 REST 界面。 [SPUtility](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.aspx) 类还具有几个新属性，可帮助管理解决方案中的兼容级别。这些属性不适用于客户端对象模型。最后，SharePoint 中有几个控件会揭示 **UIVersion** 属性，您的代码也可以使用该属性查找当前兼容级别。
  
    
    

> **注释**
> 如果虚拟路径中的文件为 *.aspx，SharePoint 会自动检测当前网站集的模式，并从相应配置单元返回文件。因此，您不必将"/15"插入虚拟路径。 
  
    
    


## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中生成场解决方案](build-farm-solutions-in-sharepoint-2013.md)
    
  
-  [针对 SharePoint 2013 规划场解决方案部署](http://blogs.technet.com/b/mspfe/archive/2013/02/04/planning-deployment-of-farm-solutions-for-sharepoint-2013.aspx)
    
  
-  [SPUtility properties](http://msdn.microsoft.com/library/Properties.T:Microsoft.SharePoint.Utilities.SPUtility.aspx)
    
  

