---
title: 基于 SharePoint 模板为 Windows Phone 生成本地化应用程序
ms.prod: SHAREPOINT
ms.assetid: c12d7fd4-8c6b-446b-970b-1eb0e5d0a9b2
---


# 基于 SharePoint 模板为 Windows Phone 生成本地化应用程序
了解使用新的 SharePoint 模板构建可本地化的 Windows Phone 应用程序与使用其他 Windows Phone 模板构建可本地化的 Windows Phone 应用程序有何不同。
SharePoint SDK for Windows Phone 7.1 可安装 Windows Phone 项目模板，后者可用于对 SharePoint 2013 或 SharePoint 2010 构建 Windows Phone 7.1 应用程序。有关详细信息，请参阅  [Visual Studio 中的 Windows Phone SharePoint 2013 应用程序模板概述](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)。 
  
    
    

Visual Studio 使用特定语言的资源文件创建程序集，以使您的移动应用程序支持多种语言。有关此过程的详细信息，请参阅 [在桌面应用程序中打包和部署资源](http://msdn.microsoft.com/library/b224d7c0-35f8-4e82-a705-dd76795e8d16%28Office.15%29.aspx)。
> **重要信息**
> 如果打算本地化中文应用程序，请务必阅读  [Windows Phone 字体支持](http://msdn.microsoft.com/library/b0d855ad-3fd2-4872-9a88-7f5d0a270ff9%28Office.15%29.aspx)的"字体和应用程序"一节 
  
    
    


## 使用 SharePoint 模板构建 Windows Phone 本地化应用程序的区别

使用新的 SharePoint 模板构建可本地化的 Windows Phone 应用程序与使用其他 Windows Phone 模板构建此应用程序略有不同。在使用 SharePoint 模板时， **SupportedCultures** 元素需要略有不同的格式。例如，在使用英语（美国）作为其默认区域性语言，还支持德语（德国）和西班牙语（西班牙）的标准 Windows Phone 应用程序中， **SupportedCultures** 元素显示如下：
  
    
    
 `<SupportedCultures>de-DE;es-ES;</SupportedCultures>`
  
    
    
在构建基于 SharePoint 模板的本地化 Windows Phone 应用程序时，此格式无效。您需要在 .csproj 文件中查找 **SupportedCultures** 元素，并添加应用程序需要支持的各个区域性（语言）的名称（除默认区域性语言以外）。可使用分号分隔这些名称。项目中的每个 .resx 文件都应该有一个条目。
  
    
    
对于上面的示例， **SupportedCultures** 元素显示如下：
  
    
    
 `<SupportedCultures>de;es;</SupportedCultures>`
  
    
    
若要查看如何构建 Windows Phone 的本地化应用程序的分步过程，请参阅 [如何：构建 Windows Phone 的本地化应用程序](http://msdn.microsoft.com/library/9306a6ed-6efb-4f32-b850-d2e508431eeb%28Office.15%29.aspx)。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [如何：构建 Windows Phone 的本地化应用程序](http://msdn.microsoft.com/library/9306a6ed-6efb-4f32-b850-d2e508431eeb%28Office.15%29.aspx)。
    
  
-  [Windows Phone 的全球化和本地化](http://msdn.microsoft.com/library/e82118a4-6247-4d75-a16f-749677349be4%28Office.15%29.aspx)
    
  

  
    
    

