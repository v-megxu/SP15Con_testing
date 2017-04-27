---
title: 如何：在 SharePoint 2013 中将自定义 CSS 文件设置为可主题化
ms.prod: SHAREPOINT
ms.assetid: b8c82c77-c836-47f9-a11e-6c9c656d436b
---


# 如何：在 SharePoint 2013 中将自定义 CSS 文件设置为可主题化
了解如何向 CSS 文件添加注释样式标记，以便将其用于 SharePoint 2013 主题设置引擎。
## 批注简介
<a name="Intro"> </a>

批注是特殊的注释样式标记，告知 SharePoint 主题设置引擎如何设置 CSS 文件中的主题属性。将主题应用于网站时，主题设置引擎会将 CSS 属性值替换为适当的主题值。在 SharePoint 2013 中，您可以使用批注来更改颜色、字体或背景图像。您还可以为图像重新着色。如果您使用的是自定义 CSS 文件，并且希望将其用于 SharePoint 主题设置引擎，则必须将这些批注添加到 CSS 文件。如果您将主题应用到使用自定义 CSS 文件的网站，但没有添加批注，那么 CSS 属性会保持不变。这会导致网站设计不匹配。
  
    
    
本文介绍了可用批注和如何注册 CSS 文件。
  
    
    
有关自定义主题的详细信息，请参阅 [如何：在 SharePoint 2013 中部署自定义主题](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)和 [如何：在 SharePoint 2013 中创建母版页预览文件](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)。
  
    
    

## 向自定义 CSS 文件添加批注
<a name="annotations"> </a>

批注会告知 SharePoint 主题设置引擎如何在 CSS 文件中设置主题属性。本节介绍了可用批注和使用方法。
  
    
    

### ReplaceColor 批注
<a name="replaceColor"> </a>

 **ReplaceColor** 批注将颜色值替换为指定的主题颜色。该批注可与定义颜色值的 CSS 属性一起使用，例如 **color** 、 **background-color** 、 **border** 等。
  
    
    
下面介绍了 **ReplaceColor** 批注的格式。
  
    
    



```

/* [ReplaceColor(themeColor:"ColorSlot"[, themeShade:"ShadeValue"][, themeTint:"TintValue"][, opacity:"OpacityValue"])] */

```

将  _ColorSlot_ 替换为要使用的颜色插槽批注名称。若要查看可用颜色插槽的列表，请参阅 [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)中的 [颜色插槽映射](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots)一节。
  
    
    
如果您想将主题颜色变暗，请使用可选的 **themeShade** 参数。将 _ShadeValue_ 替换为从 0.0 （没有变化）到 1.0（最暗）的数值。
  
    
    
如果您想将主题颜色变亮，请使用可选的 **themeTint** 参数。将 _TintValue_ 替换为从 0.0 （没有变化）到 1.0 （最亮）的数值。
  
    
    
如果您想指定主题颜色的不透明度，请使用可选的 **opacity** 参数。将 _OpacityValue_ 替换为指定不透明度设置的数值。不透明度设置范围为从 0.0（完全透明）到 1.0（完全不透明）。
  
    
    
下面显示了 CSS 文件中使用的 **ReplaceColor** 批注示例。
  
    
    

-  `/* [ReplaceColor(themeColor:"BodyText")] */ color:#444;`
    
  
-  `/* [ReplaceColor(themeColor:"BackgroundOverlay",opacity:"0.5")] */ background-color:#fff;`
    
  
-  `/* [ReplaceColor(themeColor:"EmphasisBackground",themeTint:"0.05")] */ background-color:#f2faff;`
    
  

### ReplaceFont 批注
<a name="replaceFont"> </a>

 **ReplaceFont** 批注向可用字体的列表添加指定主题字体。该批注可与 **font** 和 **font-family** CSS 属性一起使用。
  
    
    
下面介绍了 **ReplaceFont** 批注的格式。
  
    
    



```

/* [ReplaceFont(themeFont:"FontSlot")] */
```

将  _FontSlot_ 替换为要使用的字体插槽的名称。若要查看可用字体插槽的列表，请参阅 [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)中的 [字体插槽](color-palettes-and-fonts-in-sharepoint-2013.md#fontSlot)一节。
  
    
    
下面介绍了 **ReplaceFont** 批注的示例。在该示例中，如果主题中 **body** 字体插槽定义为 Courier，则在 **Choose the Look**向导中，Courier 将作为第一项添加到可用字体列表中。
  
    
    

-  `/* [ReplaceFont(themeFont:"body")] */ font-family:"Segoe UI","Segoe",Tahoma,Helvetica,Arial,sans-serif;`
    
  

### ReplaceBGImage 批注
<a name="replaceBGimage"> </a>

 **ReplaceBGImage** 批注将 CSS 文件中的背景图像替换为主题背景图像。该批注可与 **background** 和 **background-image** CSS 属性一起使用。
  
    
    
下面介绍了 **ReplaceBGImage** 批注的格式。 **ReplaceBGImage** 批注还可以与 **AlphaImageLoader** 过滤器一起使用，以支持 Internet Explorer 的早期版本。
  
    
    



```
/* [ReplaceBGImage] */
```


### RecolorImage 批注
<a name="replaceBGimage"> </a>

 **RecolorImage** 批注为指定图像重新着色。
  
    
    
下面介绍了 **RecolorImage** 注释的格式。
  
    
    



```
/* [RecolorImage(themeColor:"ColorSlot"[, method:["Tinting"|"Blending"|"Filling"]][, includeRectangle: {x:x-Setting,y:y-Setting,width:RegionWidth,height:RegionHeight})] */

```

将  _ColorSlot_ 替换为颜色插槽的批注名称。若要查看可用颜色插槽的列表，请参阅 [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)中的 [颜色插槽映射](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots)一节。
  
    
    
如果您想要指定重新着色方法，请使用可选的 **method** 参数。
  
    
    
如果您只想针对图像的特定区域重新着色，请使用可选的 **includeRectangle** 参数。将 _x-Setting_、 _y-Setting_、 _RegionWidth_ 和 _RegionHeight_ 替换为您想重新着色的区域的 x 坐标、y 坐标、宽度和高度。
  
    
    
下面显示了 CSS 文件中使用的 **RecolorImage** 批注的示例。
  
    
    

-  `/* [RecolorImage(themeColor:"SubtleBodyText",method:"Tinting")] */ background-image:url("/_layouts/15/images/tabtitlerowbottombg.png?rev=23");`
    
  
-  `/* [RecolorImage(themeColor:"BodyText",method:"Filling",includeRectangle:{x:161,y:178,width:16;height:16})] */ background:url("/_layouts/15/images/spcommon.png?rev=23") no-repeat -161px -178px;`
    
  

## 将 CSS 文件上载到样式库中的主题文件夹
<a name="uploadCSS"> </a>

将自定义 CSS 文件置于样式库中的主题文件夹中（不是母版页样式库中的主题文件夹）。只有存储在样式库主题文件夹中的 CSS 文件才能被主题设置引擎识别。主题文件夹针对发布网站自动创建。或者，您也可以在正确位置 (http://  _SiteCollectionName_/Style Library/ _language_/Themable/) 创建主题文件夹。
  
    
    

> **注释**
>  _语言_文件夹的名称必须采用 4 位格式  _ll-cc_ 来分别标识语言和区域。例如，en-us 或 ar-sa。有关详细信息，请参阅 [Office 2013 中的语言标识符和 OptionState Id 值](http://technet.microsoft.com/zh-cn/library/cc179219.aspx)。 
  
    
    

您必须签入并发布 CSS 文件。如果 CSS 文件发生更改，您必须重新应用主题，以让系统识别更改。
  
    
    

## 注册 CSS 文件
<a name="registerCSS"> </a>

您必须为 CSS 文件注册一个母版页，然后才能将其用于主题设置引擎。这样，当您向网站应用主题时，会指引母版页访问 CSS 文件。若要注册 CSS 文件，您可以将 **<SharePoint:CssRegistration>** 元素添加到母版页的 **<head>** 元素中。下面介绍了 **<SharePoint:CssRegistration>** 元素的格式。
  
    
    

```HTML

<SharePoint:CssRegistration Name="CSSFileLocation" runat="server" />
```

将  _CSSFileLocation_ 替换为 CSS 文件的位置。
  
    
    
以下是 **<SharePoint:CssRegistration>** 元素的示例。
  
    
    



```HTML
<head>
…
<SharePoint:CssRegistration Name="<%$SPUrl:~SiteCollection/Style Library/~language/Themable/MyCustomFile.css%>" runat="server" />
</head>
```


> **注释**
> **%$SPUrl** 令牌无法用于 SharePoint Foundation 2013。您必须使用 URL 指定 CSS 文件的位置。
  
    
    


## 其他资源
<a name="addresources"> </a>


-  [SharePoint 2013 主题概述](themes-overview-for-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中部署自定义主题](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [将自定义主题和 CSS 升级到 SharePoint 2013](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建母版页预览文件](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的调色板和字体](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [SharePoint 团队博客：通过 SharePoint 主题设置秀出自己的风格](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 Design Manager 品牌和设计功能](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

