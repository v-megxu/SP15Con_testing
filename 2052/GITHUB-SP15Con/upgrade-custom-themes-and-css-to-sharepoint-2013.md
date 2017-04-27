---
title: 将自定义主题和 CSS 升级到 SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8d1a4e3a-ae6f-41a5-bd80-3398ba541207
---


# 将自定义主题和 CSS 升级到 SharePoint 2013
了解主题自定义（如自定义 CSS 和自定义母版页）的升级问题，以及如何更新自定义，以便其在 SharePoint 2013 中使用。
## 主题自定义和升级 SharePoint 2013 网站简介
<a name="Intro"> </a>

我们通过更改网站布局、调色板、字体方案和背景图像，对 SharePoint 2013 中的主题设置体验进行了重新设计，以简化自定义网站的过程。用户界面的主题经过了重新设计，有了一组与主题相关的新文件格式。在 SharePoint 2010 中创建的自定义主题无法在 SharePoint 2013 网站上使用，您必须重新创建它们。自定义 CSS 文件可能无法在 SharePoint 2013 网站上正常工作，除非它们已更新为可与新母版页、颜色插槽和其他主题设置更改共同使用。
  
    
    
本文介绍了当您尝试在自定义 SharePoint 2010 主题、SharePoint 2010 CSS 和自定义 CSS 中使用新主题设置体验时可能遇到的问题。本文还介绍了要在 SharePoint 2013 网站上使用自定义 SharePoint 2010 主题、SharePoint 2010 CSS 和自定义 CSS 时，您必须对它们做出的更改。
  
    
    

> **注释**
> SharePoint 2010 主题可以用在运行 2010 模式的网站集上。有关网站集模式的详细信息，请参阅 [在 SharePoint 2013 中规划网站集升级](http://technet.microsoft.com/zh-cn/library/ff191199.aspx)或 [规划升级到 SharePoint 2013](https://technet.microsoft.com/zh-cn/library/cc303429.aspx)。 
  
    
    

有关主题的详细信息，请参阅  [SharePoint 2013 主题概述](themes-overview-for-sharepoint-2013.md)。
  
    
    

## SharePoint 2013 中的自定义 SharePoint 2010 主题
<a name="themes"> </a>

在 SharePoint 2010 中，主题存储在 THMX 文件中。在 SharePoint 2013 中，有一组与主题相关的新文件格式。调色板和字体方案存储在单独的 XML 文件中（分别是 .spcolor 和 .spfont 文件）。
  
    
    
您不能将 THMX 文件从 SharePoint 2010 升级到 SharePoint 2013。如果您在 SharePoint 2010 网站上应用了自定义主题，当您升级到 SharePoint 2013，主题文件仍保留在原位，但是该主题将不再应用到此网站，网站将恢复到默认主题。如果您想在 SharePoint 2013 网站上使用 SharePoint 2010 主题自定义,您就必须使用 SharePoint 2013 主题设置向导重新创建它们。
  
    
    
有关创建主题自定义的详细信息，请参阅 [如何：在 SharePoint 2013 中部署自定义主题](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)和  [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)。您还可以使用 SharePoint 调色板工具帮助您创建 SharePoint 设计。您可以从 Microsoft 下载中心 [下载 SharePoint 调色板工具](http://www.microsoft.com/en-us/download/details.aspx?id=38182)。
  
    
    

> **提示**
> 您可以在 PowerPoint 中打开一个 THMX 文件，查看如何在自定义主题中定义颜色，然后使用调色板工具重新将颜色创建为调色板文件（.spcolor 文件）。调色板是在 SharePoint 网站中使用的多种颜色的集合。 
  
    
    

您还可以决定使用一个预安装的 SharePoint 2013 主题。有关详细信息，请参阅 Office.com 上的 [为发布网站选择主题](http://office.microsoft.com/zh-cn/office365-sharepoint-online-enterprise-help/choose-a-theme-for-your-publishing-site-HA102891580.aspx?CTT=1)。
  
    
    

## 升级自定义母版页
<a name="MasterPages"> </a>

当您将 SharePoint 2010 网站升级到 SharePoint 2013，网站就会被配置为使用 SharePoint 2013 的默认母版页。如果您的 SharePoint 2010 网站已经有自定义母版页，则该母版页仍存在于网站上，并且您可以将它应用于 SharePoint 2013 网站。您可以使用 SharePoint 用户界面或 **SPWeb** 类将自定义母版页应用于升级的网站。有关如何更改母版页的详细信息，请参阅 [如何：向 SharePoint 2013 中的网站应用母版页](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)。
  
    
    
在您决定是否将 SharePoint 2010 自定义母版页应用到升级的 SharePoint 2013 网站前，请考虑以下各项：
  
    
    

- **如果自定义母版页取决于自定义 CSS 文件：**将自定义母版页应用于升级网站应该会将网站恢复为它初始的 2010 体验。但是，您无法将 SharePoint 2013 主题应用到该网站。
    
    如果您想同时使用自定义母版页、自定义 CSS 文件和 SharePoint 2013 主题设置体验，您就必须将 CSS 文件更新为使用新的 SharePoint 2013 颜色插槽。如果您想从主题用户界面访问自定义母版页，您还必须创建一个母版页预览文件。有关详细信息，请参阅 [如何：在 SharePoint 2013 中创建母版页预览文件](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)。
    
  
- **如果自定义母版页取决于 SharePoint 2010 CSS 文件：**从 SharePoint 2010 到 SharePoint 2013，CSS 文件已经发生了显著改变。在许多情况下，您必须重新加工母版页，以便它可以与新类一起使用，然后才可以将它成功应用到升级网站上。有关 CSS 类的详细信息，请参阅  [SharePoint 外接程序 UX 设计准则](http://msdn.microsoft.com/library/a4a8f53c-27d7-43dc-b6db-aa7b1f1c7d45%28Office.15%29.aspx)中的 **在 SharePoint 相关应用程序中使用主机 Web CSS** 部分。
    
  

## SharePoint 2010 CSS 和自定义 CSS 文件
<a name="CSS"> </a>

未修改的 SharePoint 2010 CSS 文件和自定义 CSS 文件不能用在 SharePoint 2013 网站上。下文介绍适用于 SharePoint 2010 CSS 和自定义 CSS 文件的 SharePoint 2013 变化：
  
    
    

- **颜色插槽**。SharePoint 2013 中可用颜色插槽的数量已显著增多。您必须更新 SharePoint 2010 CSS 文件中的颜色插槽，然后才能将它们用在新的主题设置体验中。有关详细信息，请参阅 [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)中的 [颜色插槽映射](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots)部分。
    
  
- **字体插槽**。您应该检查可用字体插槽列表，并验证您要在 SharePoint 2013 中使用的 CSS 文件是否使用了正确的字体插槽。有关详细信息，请参阅 [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)中的 [字体插槽](color-palettes-and-fonts-in-sharepoint-2013.md#fontSlot)部分。
    
  
- **新的注释**。SharePoint 2013 有一个新的注释功能，允许您替换背景图像。有关详细信息，请参阅 [如何：在 SharePoint 2013 中将自定义 CSS 文件设置为可主题化](how-to-make-custom-css-files-themable-in-sharepoint-2013.md)。
    
  
- **新的类**。您可能需要更新 CSS 文件以与 SharePoint 2013 中的新类共同使用。有关 CSS 类（也称为 CSS 样式）的详细信息，请参阅  [SharePoint 外接程序 UX 设计准则](http://msdn.microsoft.com/library/a4a8f53c-27d7-43dc-b6db-aa7b1f1c7d45%28Office.15%29.aspx)中的 **在 SharePoint 相关应用程序中使用主机 Web CSS** 部分。
    
  

## 其他资源
<a name="addresources"> </a>


-  [SharePoint 2013 主题概述](themes-overview-for-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建母版页预览文件](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中部署自定义主题](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [SharePoint 团队博客：通过 SharePoint 主题设置秀出自己的风格](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 Design Manager 品牌和设计功能](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

