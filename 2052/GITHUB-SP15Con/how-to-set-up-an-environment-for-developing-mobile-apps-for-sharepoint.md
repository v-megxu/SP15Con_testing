---
title: 如何：设置用于为 SharePoint 开发移动应用程序的环境
ms.prod: SHAREPOINT
ms.assetid: acaf556d-e20d-478d-8c59-2efd8efb9dcb
---


# 如何：设置用于为 SharePoint 开发移动应用程序的环境
了解系统要求和配置 SharePoint 移动项目的开发环境。
使用 SharePoint 移动项目的最小配置要求运行 SharePoint 2013 的服务器（或一个 SharePoint Online 帐户），以及一个单独客户端操作系统上的开发环境。不支持在客户端操作系统（如 Windows 7）上安装 SharePoint 2013，且不支持在服务器操作系统（如 Windows Server 2008）上安装 Windows Phone 开发所需的工具。
  
    
    


## Windows Phone 开发项目和 SharePoint Server
<a name="SP15Setupmobile_winphone"> </a>

要创建并测试与 SharePoint 交互的 Windows Phone 应用程序，您需要访问运行 SharePoint 2013 的服务器或 SharePoint Online 帐户，同时还需要网站上的足够权限以及您打算在解决方案中使用的列表。我们建议您在开发项目时将专用于测试和开发的 SharePoint Server 安装用作目标服务器。仅在开发方案经过充分测试后，才在生产环境中使用 SharePoint Server 作为目标服务器。
  
    
    
有关安装和配置 SharePoint 2013 的信息，请参阅 Microsoft TechNet 库的  [SharePoint 产品](http://technet.microsoft.com/zh-cn/library/ee428287.aspx)部分的文档。有关在您的开发解决方案中使用 SharePoint Online 的信息，请访问  [SharePoint Online 开发人员资源中心](http://msdn.microsoft.com/zh-cn/sharepoint/gg153540.aspx)。
  
    
    
本文档中的代码示例假定使用样本的开发人员拥有或可以获得足够的 SharePoint 网站权限，以及可以添加、编辑和删除数据的列表。
  
    
    

## 为 SharePoint 移动项目配置客户端开发环境
<a name="SP15Setupmobile_configure"> </a>

若要开发用于 Windows Phone 设备的 SharePoint 外接程序，您需要在运行客户端操作系统（而不是服务器操作系统）的计算机上设置开发工具。
  
    
    

### 配置 Windows Phone SDK 8.0

要开发用于 Windows Phone 8 的 SharePoint 外接程序，您需要在运行 Windows 8 64 位 (x64) 客户端版本或 Windows 8 专业版 的计算机上设置开发工具。Windows Phone 8 仿真程序需要 Windows 8 专业版，以及支持二级地址转换 (SLAT) 的处理器。
  
    
    

1. 在安装了受支持的客户端操作系统的计算机上，安装  [Windows Phone SDK 8.0](http://www.microsoft.com/zh-cn/download/details.aspx?id=35471)。Windows Phone 软件开发工具包 (SDK) 8.0 向您提供为 Windows Phone 8 和 Windows Phone 7.5 开发应用程序和游戏所需的工具。
    
    Windows Phone SDK 8.0 是功能全面的开发环境，用于为 Windows Phone 8.0 和 Windows Phone 7.5 开发应用程序和游戏。Windows Phone SDK 可以为 Windows Phone 提供一个单独的 Visual Studio Express 2012 版本，或者作为 Visual Studio 2012 Professional、Premium 或 Ultimate 版的一个插件。使用 SDK，您可以利用现有编程技巧和代码来构建托管代码或本机代码应用程序。此外，SDK 包括多个仿真程序和其他工具，可以让您在真实条件下分析和测试您的 Windows Phone 应用应用程序。
    
    > **注释**
      > 如果您的计算机满足硬件和操作系统要求，但不满足 Windows Phone 8 仿真程序要求，那么您仍然可以安装和运行 Windows Phone SDK 8.0。 不过，Windows Phone 8 仿真程序将无法工作，您也无法在 Windows Phone 8 仿真程序上部署或测试应用。有关运行 Windows Phone 仿真程序的系统要求的信息，请参阅  [Windows Phone 模拟器的系统要求](http://msdn.microsoft.com/zh-cn/library/ff626524)。 
2. 安装  [Microsoft SharePoint SDK for Windows Phone 8](http://www.microsoft.com/zh-cn/download/details.aspx?id=36818)。
    
    适用于 Windows Phone 的 SharePoint SDK 安装了两个 Silverlight for Windows Phone 模板（除由 Windows Phone SDK 安装的模板之外）：Windows Phone 空的 SharePoint 应用程序模板和 Windows Phone SharePoint 列表应用程序模板。SDK 还安装了 SharePoint CSOM 库、身份验证库和 Windows Phone 项目模板，并且现在支持 NTLM 身份验证。您可以使用捆绑的 API 和模板，针对 SharePoint 2013 构建 Windows Phone 8 应用程序。
    
    此外，用于 Windows Phone 的 SharePoint SDK 安装了数个支持性运行时程序集（对于标准安装，位于  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v8.0\\Libraries` 中）。
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **注释**
      > 适用于 Windows Phone 的 SharePoint SDK 中的模板目前仅适用于 C# 项目。 
有关用于 Windows Phone 的 SharePoint SDK 中模板的详细信息，请参阅  [Visual Studio 中的 Windows Phone SharePoint 2013 应用程序模板概述](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)。
  
    
    

### 配置 Windows Phone SDK 7.1

若要开发在 Windows Phone 7 上使用的 SharePoint 外接程序，您需要在运行 Windows 7（32 位或 64 位）或 Windows Vista Service Pack 2（32 位或 64 位）的计算机上设置开发工具。Windows Server 2008 或 Windows XP 不支持 Windows Phone 软件开发工具包 (SDK) 7.1。
  
    
    

1. 在安装了受支持的客户端操作系统的计算机上，安装  [Windows Phone SDK 7.1](http://www.microsoft.com/zh-cn/download/details.aspx?id=27570)。
    
    > **注释**
      > Windows Phone SDK 的一个早期版本名为 Windows Phone Developer Tools。 

    Windows Phone SDK 安装 Microsoft Visual Studio 2010 Express for Windows Phone、Windows Phone Emulator、XNA Game Studio 和 Microsoft Expression Blend for Windows Phone。Visual Studio 2010 Express for Windows Phone 是一个适合大多数 Windows Phone 解决方案的开发环境。您还可以使用 Visual Studio 2010 Professional 作为首选开发环境，但您仍然需要安装 Windows Phone SDK，它会将所需的加载项安装到 Visual Studio。（Windows Phone SDK 当前不支持与 Visual Studio 2008 配合使用。）
    
    有关安装 Windows Phone SDK 的其他系统要求和说明，请参阅 [安装 Windows Phone SDK](http://msdn.microsoft.com/zh-cn/library/ff402530%28VS.92%29.aspx)。有关运行 Windows Phone Emulator 的系统要求信息，请参阅  [Windows Phone Emulator 的设置和系统要求](http://msdn.microsoft.com/zh-cn/library/ff626524%28VS.92%29.aspx)。
    
  
2. 安装  [Microsoft SharePoint SDK for Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476)。
    
    适用于 Windows Phone 的 SharePoint SDK 安装了两个 Silverlight for Windows Phone 模板（除由 Windows Phone SDK 安装的模板之外）：Windows Phone 空的 SharePoint 应用程序模板和 Windows Phone SharePoint 列表应用程序模板。
    
    此外，适用于 Windows Phone 的 SharePoint SDK 安装了数个支持性运行时程序集（对于标准安装，位于  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v7.1\\Libraries` 中）。
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **注释**
      > 适用于 Windows Phone 的 SharePoint SDK 中的模板目前仅适用于 C# 项目。 
有关适用于 Windows Phone 的 SharePoint SDK 中模板的详细信息，请参阅  [Visual Studio 中的 Windows Phone SharePoint 2013 应用程序模板概述](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)。
  
    
    

## 其他资源
<a name="SP15Setupmobile_addlresources"> </a>


-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/zh-cn/download/details.aspx?id=35471)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 8](http://www.microsoft.com/zh-cn/download/details.aspx?id=36818)
    
  
-  [Windows Phone 软件开发工具包 (SDK) 7.1](http://www.microsoft.com/zh-cn/download/details.aspx?id=27570)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476)
    
  

