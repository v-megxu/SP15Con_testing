---
title: SharePoint 2013 设计管理器代码段
ms.prod: SHAREPOINT
ms.assetid: 68caef4c-5941-4a88-b34b-f88122801cef
---


# SharePoint 2013 设计管理器代码段
代码段是 SharePoint 组件或控件（如导航栏或 Web 部件）的 HTML 表示形式。通过使用设计管理器中的代码段库，您可以将 SharePoint 功能快速添加到您的 HTML 母版页或页面布局中。
## 代码段和代码段库简介
<a name="Introduction"> </a>

在转换母版页或创建页面布局后，您即拥有了该页面的 HTML 版本。使用代码段库，您可以将特定 SharePoint 功能（例如搜索或导航或设备通道面板）快速添加到与您的母版页或页面布局关联的 HTML 文件。代码段库是设计管理器中的一个页面，您可以在其中执行以下功能：
  
    
    

- 从功能区上可用的 SharePoint 组件中选择一个。
    
  
- 配置该组件的属性。
    
  
- 在浏览器中预览其外观。
    
  
- 将 HTML 代码段复制到剪贴板，以便可以将该代码段粘贴到 HTML 文件中所需的位置。
    
  
代码段库在功能区上显示不同的选项，具体取决于您是要编辑母版页还是页面布局  例如，只有母版页会显示导航控件，页面布局仅显示 Web 部件区域和页字段控件。另外，当您编辑页面布局时，可用的页字段取决于您所编辑的页面布局的内容类型。
  
    
    
将代码段粘贴到 HTML 文件中后，您即获得代码段中提供的 HTML 的设计时预览。还可以使用设计管理器中的服务器端预览查看控件在活动网站上的外观。设计时预览可能包括静态示例数据，但服务器端预览使用活动数据（如果可用）。例如，从术语集提取导航链接的导航控件将在服务器端预览中动态显示这些术语，但设计时预览将显示这些术语在您创建代码段时的静态快照。但是，活动数据在某些代码段的服务器端预览中不可用，包括许多 Web 部件。在此情况下，服务器端预览可能提示"无法预览"。
  
    
    

> **注释**
> 代码段包含的 HTML 标记可在您的 HTML 编辑器中为您呈现设计时预览，但包含在"开始预览"和"结束预览"注释中的 HTML 标记不应进行编辑，因为它仅影响设计时预览，而不影响 SharePoint 最终呈现该代码段的方式。要设置代码段的样式，您通常必须标识和覆盖应用于该代码段的默认 SharePoint 样式。 
  
    
    


  
    
    

## 从代码段库插入代码段
<a name="InsertSnippet"> </a>

代码段库会根据您所编辑的文件显示不同选项。例如，不同的页面布局具有可用的不同页字段集。出于此原因，要导航到代码段库，您必须先选择要编辑的母版页或页面布局。
  
    
    

### 插入代码段


1. 浏览到发布网站。
    
  
2. 在页面右上角，选择"设置"齿轮，然后选择"设计管理器"。
    
  
3. 在设计管理器的左导航窗格中，选择"编辑母版页"或"编辑页面布局"，具体取决于您所编辑的文件类型。
    
  
4. 选择要向其添加代码段的母版页或页面布局的名称。
    
  
5. 若要打开代码段库，请选择服务器端预览右上角的"代码段"。
    
  
6. 在功能区的"设计"选项卡上，选择要添加到页面中的代码段。
    
    选择代码段时，代码段库会刷新，以使页面向您显示该代码段的预览、该代码段的可用属性以及您可复制到您的 HTML 母版页或页面布局的 HTML 代码段。
    
  
7. 在代码段库右侧的"关于此组件"下，单击或选择节标题以展开或折叠属性组，然后配置所需的任何自定义设置。
    
    对代码段核心用途最重要的属性显示在最上面名为"重要"的节中。这些是您在使用代码段时必须了解的关键属性。
    
    
    
    > **注释**
      > 如果属性网格的标题以 AjaxDelta 结尾，您应忽略这些属性，因为它们适用于与"最少下载策略"相关的控件，通过设计管理器创建的母版页和页面布局已禁用此策略。 
8. 配置任何属性后，选择"更新"。这将同时更新预览和页面左侧的 HTML 代码段，以使标记反映出您的自定义设置。您可以随时选择"重置"将所有属性恢复为其默认设置。
    
  
9. 在代码段库左侧的"HTML 代码段"下，选择"复制到剪贴板"。
    
  
10. 在您的 HTML 编辑器中，打开您计算机上的映射网络驱动器，然后打开您要向其添加代码段的母版页或页面布局对应的 HTML 文件。
    
  
11. 在 HTML 文件中，将代码段粘贴到希望显示标记的位置。
    
    每个代码段包含的 HTML 提供了组件和示例数据的直观预览。您不应修改此 HTML 中 **<!--PS>** 和 **<!--PE>** 标记内的只读预览，因为此标记只影响代码段的设计时预览，而不影响代码段在活动网站上的外观。
    
  
12. 若要查看代码段的服务器端预览，请保存 HTML 文件以将更改同步到关联的 ASP.NET 文件，然后刷新设计管理器中的服务器端预览。
    
    与设计时预览不同，服务器端预览显示 SharePoint 呈现的控件。
    
  

## 了解 HTML 代码段中的标记
<a name="UnderstandMarkup"> </a>

代码段包含四个基本部分：
  
    
    

- **标头**，具有开始标记 **<div>** 和 **<!--CS>**（自定义 ASP.NET 代码段除外，这些代码段不封装在 **<div>** 标记中）
    
  
- **SharePoint 标记**，其中的代码段包含在 **<!--MS>** 起始标记和 **<!--ME>** 结束标记中
    
  
- **HTML 预览**，包含在 **<!--PS>** 起始标记和 **<!--PE>** 结束标记中
    
  
- **页脚**，具有结束标记 **<!--CE>** 和 **</div>**
    
  
除 HTML 预览外，代码段的所有部分都包含在 HTML 注释中，以避免与文档对象模型 (DOM) 和现有样式发生交互。代码段以组件名称开头，然后是其实际 ASP.NET 标记（设计时呈现的 HTML 预览），最后是结束标记。ASP.NET 标记被注释掉，但 SharePoint 去除了注释标记并在将 HTML 文件同步到 .master 或 .aspx 文件时使用此标记。如果您了解 ASP.NET，则可以在代码段中自定义此标记。
  
    
    
例如，下面是编辑模式面板的默认标记，该面板只是一个根据条件显示其他内容和控件的容器。
  
    
    

### 标头


```HTML

<div data-name="EditModePanelShowInEdit">
    <!--CS: Start Edit Mode Panel Snippet-->
```


### SharePoint 标记


```HTML

<!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### HTML 预览


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
        <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Edit Mode Panel Properties.
    
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
```


### 页脚


```HTML

<!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Edit Mode Panel Snippet-->
</div>
```

下面是顶部导航代码段的默认标记，此代码段更为复杂，因为它包含多个不同控件，其中某些控件彼此嵌套，包括导航术语的数据源、委派控件和内容占位符。
  
    
    

> **注释**
> 其中某些控件（如内容占位符）包含 HTML 预览的空标记，这是因为该元素不需要直观显示在页面上。 
  
    
    


### 标头


```HTML

<div data-name="TopNavigationNoFlyoutWithStartNode">
<!--CS: Start Top Navigation Snippet-->    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### SharePoint 标记


```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<SharePoint:AjaxDelta ID="DeltaTopNavigation" BlockElement="true" CssClass="ms-displayInline ms-core-navigation ms-dialogHidden" runat="server">-->
```


### HTML 预览


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint 标记


```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
```


### HTML 预览


```HTML
<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<span style="display:none">
<table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow">
<tr><td nowrap="nowrap">
<span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span>
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint 标记


```HTML

<!--MS:<Template_Controls>-->
<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
```


### SharePoint 标记


```HTML

<!--ME:</asp:SiteMapDataSource>-->
<!--ME:</Template_Controls>-->
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>
```


### SharePoint 标记


```HTML

<!--MS:<asp:ContentPlaceHolder ID="PlaceHolderTopNavBar" runat="server">-->
<!--MS:<SharePoint:AspMenu ID="TopNavigationMenu" runat="server" EnableViewState="false" DataSourceID="topSiteMap" AccessKey="&amp;#60;%$Resources:wss,navigation_accesskey%&amp;#62;" UseSimpleRendering="true" UseSeparateCss="false" Orientation="Horizontal" StaticDisplayLevels="2" AdjustForShowStartingNode="false" MaximumDynamicDisplayLevels="0" SkipLinkText="">-->
```


### HTML 预览


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" />
<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
<ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
<li class="static">
<a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1">
<span class="additional-background ms-navedit-flyoutArrow">
<span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div>
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint 标记


```HTML

<!--ME:</SharePoint:AspMenu>-->
<!--ME:</asp:ContentPlaceHolder>-->
```


### HTML 预览


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint 标记


```HTML

<!--ME:</SharePoint:AjaxDelta>-->
```


### 页脚


```HTML
<!--CE: End Top Navigation Snippet-->
</div>
```


### 标记类型

以下是包含在代码段中的标记类型的细分。
  
    
    
 **SharePoint 命名空间注册** SPM（"SharePoint 标记"）指示注册 SharePoint 命名空间的一行。
  
    
    



```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
```

 **注释** CS 和 CE（"注释开始"和"注释结束"）可帮助您分析标记行。
  
    
    



```HTML
<!--CS: Start Top Navigation Snippet-->
…
<!--CE: End Top Navigation Snippet-->

```

 **代码段** MS 和 ME（"标记开始"和"标记结束"）表示 SharePoint 控件或代码段的开始和结束。某些代码段（如功能区或上面的顶部导航控件）包含嵌套在单个代码段中的多个控件。
  
    
    



```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
…
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>

<!--MS:<Template_Controls>-->
…
<!--ME:</Template_Controls>-->

<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
…
<!--ME:</asp:SiteMapDataSource>-->

```

 **预览块** PS 和 PE（"预览开始"和"预览结束"）内包括一节不应编辑的 HTML 代码。这些预览节是 SharePoint 控件在插入代码段时的快照。您可以通过预览在客户端 HTML 编辑器中更有目的地处理 HTML 文件。不过，在该预览中更改内容或样式不会对 .master 文件（SharePoint 最终将使用的文件）产生任何持久影响。要设置代码段样式，您必须标识并用您自己的 CSS 覆盖 SharePoint 样式。
  
    
    



```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><span style="display:none"><table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow"><tr><td nowrap="nowrap"><span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span><!--PE: End of READ-ONLY PREVIEW-->

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" /><div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox"><ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static"><li class="static"><a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1"><span class="additional-background ms-navedit-flyoutArrow"><span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div><!--PE: End of READ-ONLY PREVIEW-->
```


## 其他资源
<a name="Resources"> </a>


-  [如何：在 SharePoint 2013 中将 HTML 文件转换为母版页](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中添加编辑模式面板代码段](how-to-add-an-edit-mode-panel-snippet-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中添加安全修整代码段](how-to-add-a-security-trim-snippet-in-sharepoint-2013.md)
    
  

