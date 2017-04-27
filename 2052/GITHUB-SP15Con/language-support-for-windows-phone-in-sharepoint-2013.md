---
title: SharePoint 2013 中对 Windows Phone 的语言支持
ms.prod: SHAREPOINT
ms.assetid: 2c396a91-0fc1-4e25-942b-fffad49bd2c6
---


# SharePoint 2013 中对 Windows Phone 的语言支持
了解对 Visual Studio 模板的语言支持，这些模板由用于移动应用程序开发的 SharePoint 软件开发工具包 (SDK) 针对 Windows Phone 安装。
要开发多种语言版本的移动应用程序，您需要全球化和本地化您的应用程序。您需要实现的大部分全球化和本地化功能已内置在 .NET Framework 中。使用该功能，您可与许多其他国家和地区的客户保持联系。
  
    
    

Windows Phone SDK 包括 Visual Studio 2010 Express 针对 Windows Phone、Windows Phone 仿真程序、XNA Game Studio 以及 Expression Blend。若要开始使用该工具包，请安装用于 Windows Phone 开发的  [Windows Phone SDK 7.1](http://www.microsoft.com/zh-cn/download/details.aspx?id=27570)。然后安装  [Microsoft SharePoint SDK 针对 Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476)，以便安装适用于 Windows Phone 的 SharePoint 模板。
在设置开发环境和安装 SharePoint SDK 针对 Windows Phone 后，请参阅 [如何：设置用于为 SharePoint 开发移动应用程序的环境](how-to-set-up-an-environment-for-developing-mobile-apps-for-sharepoint.md)。
  
    
    

有关适用于 Windows Phone 的 SharePoint 模板的详细信息，请参阅  [Visual Studio 中的 Windows Phone SharePoint 2013 应用程序模板概述](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)。
## 由 SharePoint SDK 针对 Windows Phone 安装的模板和库
<a name="LanguageSupportForWindowsPhoneForSharePoint2013_TemplatesInstalledBySharePointSDKForWindowsPhone"> </a>

SharePoint SDK 针对 Windows Phone 7.1 可安装适用于 Windows Phone 的客户端对象模型 (CSOM) 库、适用于 Windows Phone 的 SharePoint 身份验证库，以及可用于针对 SharePoint 2013 或 SharePoint 2010 构建 Windows Phone 7.1 应用程序的 Windows Phone 项目模板。
  
    
    
在安装 SharePoint SDK 针对 Windows Phone 时，还为项目提供其他两个 Silverlight 针对 Windows Phone 模板：
  
    
    

- Windows Phone Empty SharePoint 应用程序
    
  
- Windows Phone SharePoint 列表应用程序
    
  

## SharePoint SDK 针对 Windows Phone 的本地化版本
<a name="LanguageSupportForWindowsPhoneForSharePoint2013_LocalizedVersionsOfSharePointSDKForWindowsPhone"> </a>

SharePoint SDK 针对 Windows Phone Developer Toolkit 7.1 支持 9 种语言。创建应用程序的大多数工作已在设计阶段完成，包括创建项目、设计表单、开发控件和添加代码。您可以使用下面任一本地化版本的 SharePoint SDK 针对 Windows Phone 编写 Windows Phone 应用程序：
  
    
    

- 英语 (en-US)
    
  
- 法语 (fr-FR)
    
  
- 德语 (de-DE)
    
  
- 意大利语 (it-IT)
    
  
- 日语 (ja-JP)
    
  
- 朝鲜语 (Ko-KR)
    
  
- 俄语 (ru-RU)
    
  
- 西班牙语 (es-ES)
    
  
- 繁体中文 (zh-TW)
    
  

## SharePoint Windows Phone 应用程序支持的本地化语言
<a name="bk_supplocallangs"> </a>

当应用程序获得控制权后，您可以通过用户所采用的方式与该应用程序进行交互。您可以查看代码、运行和调试应用程序，但您无法更改代码。
  
    
    
尽管您可以编程方式访问 9 种语言，但您仍可以采用表 1 中所示的 20 种语言运行 SharePoint 移动应用程序。
  
    
    

**表 1. SharePoint SDK 针对 Windows Phone 中支持的显示/运行时语言**


|**区域性名称**|**区域性代码**|
|:-----|:-----|
|简体中文（中国）  <br/> |zh-CN  <br/> |
|繁体中文（台湾）  <br/> |zh-TW  <br/> |
|捷克语（捷克共和国）  <br/> |cs  <br/> |
|丹麦语（丹麦）  <br/> |da  <br/> |
|荷兰语（荷兰）  <br/> |nl  <br/> |
|芬兰语（芬兰）  <br/> |fi  <br/> |
|法语（法国）  <br/> |fr  <br/> |
|德语（德国）  <br/> |de  <br/> |
|希腊语（希腊）  <br/> |el  <br/> |
|匈牙利语（匈牙利）  <br/> |hu  <br/> |
|意大利语（意大利）  <br/> |it  <br/> |
|日语（日本）  <br/> |ja  <br/> |
|朝鲜语（韩国）  <br/> |ko  <br/> |
|挪威语（挪威）  <br/> |nb  <br/> |
|波兰语（波兰）  <br/> |pl  <br/> |
|葡萄牙语（巴西）  <br/> |pt-BR  <br/> |
|葡萄牙语（葡萄牙）  <br/> |pt-PT  <br/> |
|俄语（俄罗斯）  <br/> |ru  <br/> |
|西班牙语（西班牙）  <br/> |es  <br/> |
|瑞典语（瑞典）  <br/> |sv  <br/> |
   

## 其他资源
<a name="bk_addresources"> </a>


-  [Visual Studio 中的 Windows Phone SharePoint 2013 应用程序模板概述](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)
    
  
-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/zh-cn/download/details.aspx?id=35471)
    
  
-  [适用于 Windows Phone 8 的 Microsoft SharePoint SDK](http://www.microsoft.com/zh-cn/download/details.aspx?id=36818)
    
  

  
    
    

