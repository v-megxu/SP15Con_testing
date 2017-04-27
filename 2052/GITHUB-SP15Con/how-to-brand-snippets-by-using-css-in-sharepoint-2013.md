---
title: 如何：在 SharePoint 2013 中使用 CSS 标记代码段
ms.prod: SHAREPOINT
ms.assetid: d18d07b6-1a6b-4589-a65c-932b67cef595
---


# 如何：在 SharePoint 2013 中使用 CSS 标记代码段
要设置代码段的样式，您可以用自定义 CSS 覆盖默认样式。您可以用 CSS ID 和元素选择器覆盖应用于元素上的所有默认样式，或者您也可以使用 HTML 编辑器或 Internet Explorer 中类似于 F12 开发工具的工具来识别并覆盖特定的默认样式。
## 使用 CSS 设置代码段样式简介
<a name="Introduction"> </a>

转换一个 HTML 母版页或创建一个 HTML 页面布局之后，您可以预览位于设计管理器服务器端预览中的页面。您可以从预览页面导航至代码段库，然后复制代码段至您的 HTML 文件。代码段是 SharePoint 控件的 HTML 表示形式，例如顶端导航控件或搜索框。
  
    
    
在将代码段复制至您映射驱动器中的 HTML 文件并保存更改后，可以刷新 HTML 文件的服务器端预览，以查看控件的呈现方式。代码段包含提供您所选择的 HTML 编辑器中设计时预览的标记，但您不能编辑这一标记，因为它是只读属性并且不影响控件在服务器上显示的方式。相反，服务器端预览可使用实时数据显示高保真预览（如适用），例如，导航控件将使用数据源中的实时数据显示网站的当前导航架构（例如 SharePoint 针对托管导航的术语存储）。
  
    
    

> **注释**
> 有关映射网络驱动器的详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。 
  
    
    

默认情况下，代码段从 SharePoint 2013 样式表继承它们的样式，例如 corev15.css.。要设置代码段的样式，您需要使用自定义 CSS 覆盖这些默认样式。为此，您可以：
  
    
    

- 使用 CSS ID 和元素选择器完全覆盖应用于选定元素上的默认样式。
    
  
- 使用 Internet Explorer 中基于浏览器的工具（例如 F12 开发工具）检查设计管理器服务器端预览中的默认样式，然后确定要覆盖的特定样式。
    
  
- 利用 HTML 编辑器的功能检查代码段只读属性预览中的默认样式，然后确定要覆盖的特定样式。 
    
  
若要使用 Internet Explorer 中的开发工具确定默认样式，您应该使用设计管理器中的服务器端预览功能，查看您的 HTML 母版页或页面布局，按"F12"启动开发人员工具栏，选择"查找"菜单，然后选择"单击选择元素"。这些步骤让您可以在单击页面上的元素后，准确观察通过添加 CSS 至自定义样式表（与您的 HTML 母版页或页面布局相关联）可以覆盖的样式。
  
    
    
默认的 SharePoint 2013 样式表中包含很多样式，很难从中确定特定样式。作为基于浏览器工具的替代方法，您可以根据自己的 HTML 编辑器，找到更简单的方法来将代码段库中代码段复制到您 HTML 文件中。在代码段库中，当您选择"更新"，然后选择"制到剪贴板"，该代码段就会包含那个代码段的 HTML 预览。将这一代码段复制到您的 HTML 文件后，您可以查看代码段中用于只读预览的样式。按照这种方式，您可以解析较小的默认样式子集。
  
    
    
根据代码段和自定义的范围，您可能想要使用 CSS ID 和元素选择器覆盖所有的默认样式，而不是选择特定的默认样式进行覆盖。以下示例将为您演示如何使用此方法将自定义样式应用到顶部导航代码段中。
  
    
    

## 示例： 设置顶部导航代码段的样式
<a name="Example"> </a>

顶部导航代码段是广为使用的代码段之一，所以它也是最常被标记的代码段之一。在 SharePoint 2013 网站，您可以选择一个选项使用托管导航，这样术语储存就会变成顶部导航代码段的数据源。按照这种方式，您可以使用"网站设置" 中的术语储存管理工具，添加或删除导航术语，管理顶部导航代码段显示的导航分类。 
  
    
    
在这个示例中，网站使用了托管导航，这样顶部导航控件就可以从一个术语储存中提取条目。当您将鼠标悬停在一个高级导航术语处时，会出现一个浮出控件。比如"计算机"。这一部分展示自定义样式如何覆盖默认的 SharePoint 样式。
  
    
    

### 示例 1： HTML 模型文件中的导航

使用设计管理器前，当您为母版页设计 HTML 模型时，您很有可能会使用 HTML 和 CSS 来设计一个功能性的顶部导航元素。此 HTML 样本为顶部导航使用了一个基础结构： 带有一个 ID 和类别名称的 **<div>** 元素，顶级导航条目列表，以及针对每个浮出控件子菜单的嵌套列表。
  
    
    

```HTML

<div id="navigation" class="msax-Navigation">
   <ul>
      <li><a href="#">Cameras</a>
         <ul>
            <li><a href="#">Camcorders</a></li>
            <li><a href="#">Digital cameras</a></li>
            <li><a href="#">Disposable cameras</a></li>
            <li><a href="#">Film cameras</a></li>
         </ul>
      </li>
      <li><a href="#">Computers</a>
         <ul>
            <li><a href="#">Desktops</a></li>
            <li><a href="#">Laptops</a></li>
            <li><a href="#">Netbooks</a></li>
            <li><a href="#">Tablets</a></li>
         </ul>
      </li>
      <li><a href="#">Media</a>
         <ul>
            <li><a href="#">Movies</a></li>
            <li><a href="#">Music</a></li>
            <li><a href="#">TV shows </a></li>
            <li><a href="#">Video games </a></li>
         </ul>
      </li>
      <li></li>
   </ul>
</div>

```


### 示例 2： 使用自定义 CSS 设置样式的导航 <div>

要在模型 HTML 文件中覆盖默认 SharePoint 样式，应在结尾 **</head>** 标记正前方包括连接至您 CSS 文件的链接 `(<link rel="stylesheet" type="text/css" href="URLtoYourCustomCSSFile"/>`)。
  
    
    
在这些 HTML 和 XSS 示例中，请注意下列事项：
  
    
    

- 导航条目的样式是使用  `.msax-Navigation ul li` 格式设置的，而不是直接将类应用到 **<ul>** 或 **<li>** 标记中。
    
  
- 样式使用  `.msax-Navigation ul li` 句法，而不是 `.msax-Navigation ul>li`，这是因为代码段标记在选定的元素间可能包含干预 **<div>** 标记。
    
  
- HTML 模型包含一个空的 **<li></li>** 元素，作为高级 **<ul>**的最后一个条目。这是因为，在开启托管导航的情况下， SharePoint 添加了一个 **Edit Links** 命令作为高级导航的最终条目，但是最后一个网站显然不需要显示这一选项。CSS 样例使用 `.msax-Navigation ul li:last-child` 选择这一条目，并把这一显示值设置为 `none`。HTML 文件中的空 **<li></li>** 元素是默认 **Edit Links** 条目的临时替代项。如果您的网站使用托管导航，而且您的 CSS 使用了任意 `li:last-child` 选择器，请注意此最终 **<li>** 元素。
    
  



```HTML

.msax-Navigation {
margin: 10px 0px; top: 0px; position: relative;
z-index:200;
}
.msax-Navigation a {
margin: 0px; padding: 0px; border: 0px currentColor;
}
.msax-Navigation ul {
list-style: none; margin: 0px; padding: 0px; font-size: 16px; z-index:200;
}
.msax-Navigation ul li {
padding: 10px; display: inline-block; position: relative; z-index:200;
}
.msax-Navigation ul li:first-child {
margin: 0px;
}
.msax-Navigation ul li:last-child {
margin: 0px; padding: 0px; display: none;
}
.msax-Navigation ul li a.selected, .msax-Navigation ul li.selected {
background-color: rgb(58,60,62) !important;
color:rgb(255,255,255) !important;
}
.msax-Navigation ul li a {
width: 100%; color: rgb(58,60,62); font-size: 16px;
}
.msax-Navigation ul li:hover {
background-color: rgb(58,60,62);
color:rgb(255,255,255) !important;
}
.msax-Navigation ul li a:hover {
text-decoration: none;
color:rgb(255,255,255) !important;
}
.msax-Navigation li ul {
left: 0px; top: 35px; display: none; position: absolute; min-width: 100px; box-shadow: 5px 5px 10px 0px rgb(0,0,0); background-color: rgb(58,60,62);
}
.msax-Navigation li:hover ul {
display: block; z-index: 150;
}
.msax-Navigation li li {
margin: 0px; padding: 5px 10px 5px 0px; border-top-width: 0px; display: block; min-width: 100px;
}
.msax-Navigation li li:last-child {
margin: 0px; padding: 5px 10px 5px 0px; border-top-width: 0px; display: block; min-width: 100px;
}
.msax-Navigation li li a {
width: 100%; padding-left: 10px; display: block; color:rgb(255,255,255) !important;
}
.msax-Navigation li li:hover {
background-color: rgb(120, 120, 120);
}

```


### 示例 3：顶部导航代码段的只读预览

在您的 HTML 模型应用了自定义样式后，您便拥有一个功能性顶部导航元素，请执行下列步骤：
  
    
    

1. 映射一个网络驱动器。
    
  
2. 上载您的设计文件。
    
  
3. 将 HTML 文件转换为母版页。
    
  
4. 预览并修正问题。
    
  
5. 使用代码段库，将顶部导航代码段添加到 HTML 母版页。
    
  
在代码段库中，当您配置顶部导航代码段的属性时，请注意以下事项：
  
    
    

- 在顶部 **重要**区域，请勿对 **CssClass** 属性做出任何改变。
    
  
- 请勿对 **AjaxDelta** 标题下的属性做出任何改变，因为这些属性与 SharePoint 用来将 HTML 代码段转换为相应 ASP.NET 代码段的 MDS 属性相关联。这一点适用于所有代码段，并不仅仅是针对顶部导航代码段。
    
  
- 如果您打算覆盖默认的 SharePoint 样式，在代码段库中，在 **AspMenu** 下的 **Behavior** 部分中（如果代码段包含多个控件(如委托控件)，可能有多个 **Behavior** 部分），将 **ClientIDMode** 设置为 **Static**。如果您保留 **ClientIDMode** 设置为默认设置 **Inherit**，则应用了 CSS 类的代码段将根据该页面上代码段的排序而变化。有关 **ClientIDMode** 的详细信息，请参阅 [Control.ClientIDMode 属性](http://msdn.microsoft.com/zh-cn/library/system.web.ui.control.clientidmode.aspx)。
    
    例如，默认情况下，顶部导航控件使用默认 SharePoint ID 属性，例如 **zz5_TopNavigationMenu** 和 **zz6_RootAspMenu**。通过将 **ClientIDMode** 更改为 **Static**，您可以使用这些默认 ID 作为您自己 CSS 的选择器，然后覆盖默认 SharePoint 样式。
    
  
- 已配置一些属性，从而通过消除默认动态 CSS 和 JavaScript 行为来使标识顶部导航代码段更为简便，例如，默认情况下， **UseSimpleRendering** 设为 **True**，而 **MaximumDynamicDisplayLevels** 设为 **0**。有关顶部导航代码段特殊属性的详细信息，请参阅  [AspMenu 属性](http://msdn.microsoft.com/zh-cn/library/ms412476.aspx) 和 [Menu 属性](http://msdn.microsoft.com/zh-cn/library/282668a1.aspx)。
    
  
在代码段库中配置好顶部导航代码段之后，选择"更新"，然后再选择"复制到剪贴板"。在 HTML 母版页中，删除导航  `<div id="navigation" class="msax-Navigation">` 的内容，这些内容包括您的模型控件（只删除 **<div>** 标记的内容，而不是删除 **<div>** 标记本身），然后复制代码段至导航 **<div>**。如有需要，复位导航 **<div>**，通常在启用  `<div id="s4-bodyContainer">` 标记之后，但在 **<div>** 包含 `PlaceHolderMain` 之前。
  
    
    
为了便于与上述导航 **<div>** 的 HTML 进行比较，以下示例包含顶部导航代码段的导航 **<div>** 部分。请注意，这并不是整个代码段。
  
    
    



```HTML

<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
     <ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
          <li class="static">
          <a accesskey="1" class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Cameras</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/camcorders" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Camcorders</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/digital-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Digital cameras</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/disposable-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Disposable cameras</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/film-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Film cameras</span></span></a></li>
          </ul>
          </li>
          <li class="static">
          <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Computers</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/desktops" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Desktops</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/laptops" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Laptops</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/netbooks" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Netbooks</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/tablets" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Tablets</span></span></a></li>
          </ul>
          </li>
          <li class="static">
          <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Media</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/movies" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Movies</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/music" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Music</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/tv-shows" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">TV shows</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/video-games" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Video games</span></span></a></li>
          </ul>
          </li>
          <li class="static ms-verticalAlignTop ms-listMenu-editLink ms-navedit-editArea">
          <span id="zz7_TopNavigationMenu_NavMenu_Edit" class="ms-navedit-editSpan">
          <a id="zz7_TopNavigationMenu_NavMenu_EditLinks" class="ms-navedit-editLinksText" href="#" onclick="g_QuickLaunchMenu = null; EnsureScriptParams('quicklaunch.js', 'QuickLaunchInitEditMode', 'zz7_TopNavigationMenu', 2, 0, 0, ''); cancelDefault(event); return false;">
          <span class="ms-displayInlineBlock">
          <span class="ms-navedit-editLinksIconWrapper ms-verticalAlignMiddle">
          <img class="ms-navedit-editLinksIcon" src="/_layouts/15/images/spcommon.png?rev=23" /></span><span class="ms-metadata ms-verticalAlignMiddle">Edit Links</span></span></a><span id="zz7_TopNavigationMenu_NavMenu_Loading" class="ms-navedit-menuLoading ms-hide"><a id="zz7_TopNavigationMenu_NavMenu_GearsLink" href="#" onclick="HideGears(); return false;" title="This animation indicates the operation is in progress. Click to remove this animated image."><img id="zz7_TopNavigationMenu_NavMenu_GearsImage" src="/_layouts/15/images/loadingcirclests16.gif?rev=23" /></a></span><div id="zz7_TopNavigationMenu_NavMenu_ErrorMsg" class="ms-navedit-errorMsg">
          </div>
          </span></li>
     </ul>
</div>

```

可能有一种情况下，您不是使用纯自定义样式，而是想要覆盖一个特定的样式。例如，隐藏"Edit Links" 节点，这样您可以创建一个使用默认 id **zz7_TopNavigationMenu_NavMenu_Edit** 的自定义样式，来将显示设置设为 `none`。
  
    
    

## 其他资源
<a name="Additional"> </a>


-  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)
    
  
-  [SharePoint 2013 中的设计管理器概述](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中将 HTML 文件转换为母版页](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  

