---
title: 为 SharePoint 2013 中的 BCS 设置开发环境
ms.prod: SHAREPOINT
ms.assetid: d83c8a43-49dd-47eb-94d4-23aa2cf71a9a
---


# 为 SharePoint 2013 中的 BCS 设置开发环境
了解如何为使用 Business Connectivity Services (BCS) 开发 SharePoint 2013 解决方案和 SharePoint 外接程序设置开发环境。
您可以根据自己正在构建的解决方案类型，在客户端计算机或服务器计算机上使用 BCS 创建 SharePoint 2013 解决方案和 SharePoint 外接程序。
  
    
    


## 构建基于服务器的解决方案和 SharePoint 外接程序
<a name="SP15SettingupdevenvBCS_server"> </a>

通常情况下，多数 BCS 解决方案和应用程序将在服务器环境中驻留。这些服务器解决方案和应用程序具备最高的灵活性，拥有 SharePoint 2013 中所有 BCS 功能。
  
    
    
对于基于服务器的解决方案，最好在安装 SharePoint 2013 的本地计算机中开发，然后，当创建并测试解决方案后，将其部署到生产服务器。您可以在主机工作站或者运行 Windows Server 2008 Service Pack 2 的一台或多台虚拟计算机上安装开发环境。
  
    
    

### 设置构建 SharePoint 外接程序所需的环境

您用于使用 BCS 开发应用程序的环境与开发任何 SharePoint 外接程序所使用的环境相同。 
  
    
    
若要了解如何安装这些开发环境组件，包括操作系统、SharePoint 2013、Visual Studio 2008 以及 Visual Studio 2012 Office 开发人员工具，请按照 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)中的说明进行操作。
  
    
    

## 构建基于客户端的解决方案
<a name="SP15SettingupdevenvBCS_client"> </a>

基于客户端的解决方案使 Office 2013 客户端应用程序可以访问 SharePoint 2013 解决方案或 SharePoint 外接程序可以访问的外部数据。您可以通过使用 BCS 客户端缓存执行代码来实现此目的。客户端组件通过客户端代码和客户端缓存与 BCS 进行通信。这为 Office 客户端应用程序提供了丰富的数据，SharePoint 可以通过外部内容类型使用这些数据。
  
    
    
因为这些解决方案不需要代码，您可以使用 SharePoint Designer 2013 和 Office 2013。
  
    
    

## 其他资源
<a name="SP15SettingupdevenvBCS_addresources"> </a>


-  [设置 SharePoint 加载项的本地开发环境](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 开发概述](sharepoint-2013-development-overview.md)
    
  

