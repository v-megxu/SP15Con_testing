---
title: 如何：在 SharePoint 2013 中添加 Web 部件区域代码段
ms.prod: SHAREPOINT
ms.assetid: 7583b217-200c-4569-8f88-fe975c8ebd72
---


# 如何：在 SharePoint 2013 中添加 Web 部件区域代码段
Web 部件区域是一个代码段，您可将其添加到页面布局中以便内容作者可以添加、编辑或删除该区域中的 Web 部件。
## Web 部件区域代码段简介
<a name="Introduction"> </a>

Web 部件是一个服务器控件，它提供特定的 SharePoint 功能；而 Web 部件区域是一个容器，它确定包含在该区域中的 Web 部件的布局、行为和其他属性。例如，Web 部件区域可指定该区域中的 Web 部件：
  
    
    

- 是按水平布局还是垂直布局排列。 
    
  
- 是否显示常见用户界面 (UI) 元素，例如标题栏或边框。
    
  
- 是否可由内容作者在浏览器中编辑页面时进行自定义。
    
  
- 是否可由创建 Web 部件个人视图的网站访问者在浏览器中查看页面时进行个性化设置。
    
  
在发布网站中，具有必要权限的内容作者可以创建或编辑位于页面库中的页面。作为设计人员，您可以向页面布局中添加 Web 部件区域。当内容作者基于该页面布局创建或编辑页面时，该作者可以添加、编辑或删除该区域中的 Web 部件。例如，您可能需要向页面布局中添加 Web 部件区域，以便内容作者可以：
  
    
    

- 使用内容搜索 Web 部件显示搜索查询的结果。作者可以在搜索驱动的 Web 部件位于 Web 部件区域内时更新或修改搜索查询。
    
  
- 使用媒体 Web 部件在网页中嵌入视频或音频剪辑。
    
  
- 使用摘要链接 Web 部件创建易于编辑、分组或重新排序的超链接列表。
    
  
- 使用目录 Web 部件创建列出网站中的所有页面并在添加、删除、重命名或移动页面时自动进行更新的站点地图。
    
  

### 何时使用 Web 部件区域

当页面布局包括一个或多个 Web 部件区域时，这些 Web 部件区域可供使用该布局的所有页面使用，从而使作者能够在这些页面上插入 Web 部件。如果您允许作者在页面上插入 Web 部件，那么您对用户的网站体验的控制将会降低。例如，作者可以在页面上插入目录 Web 部件，这样会公开您不希望访问者从当前页面导航到的网站部分。
  
    
    
如果您希望完全控制 Web 部件在网站上的显示方式，并且希望该 Web 部件显示在某特定类型的所有页面上，请将该 Web 部件直接添加到页面布局中。如果您希望某个 Web 部件显示在网站中的所有页面上，还可以将 Web 部件直接添加到母版页中。
  
    
    

> **注释**
> Web 部件区域可用于页面布局但不适用于母版页  Web 部件区域的用途是允许作者修改 Web 部件，而作者通常不编辑母版页。 
  
    
    

您还可以将 Web 部件区域添加到页面布局但限制其用法。例如，您可以将 Web 部件添加到某个区域中，然后设置该区域的属性以便内容作者可以编辑现有 Web 部件的属性，但不能在该区域中添加或删除 Web 部件。Web 部件区域有一组属性用于双重目的。您可以将一部分属性用于组织 Web 部件在页面上的布局和格式，将另一部分属性用于提供更高级别的保护，以防止修改（或"锁定"）该区域中的 Web 部件。
  
    
    
要对 Web 部件在您网站上的呈现方式进行不同级别的控制，您可以：
  
    
    

- 将 Web 部件直接添加到母版页或页面布局中。这意味着内容作者无法修改 Web 部件。
    
  
- 将 Web 部件添加到页面布局上的区域，但限制只有您添加的默认 Web 部件才能显示在这些区域中。
    
  
- 将 Web 部件区域添加到页面布局中，并使内容作者能够完全控制哪些 Web 部件显示在这些区域中以及这些 Web 部件的配置方式。
    
  
Web 部件区域的属性可以指定是否允许内容作者：
  
    
    

- 通过添加、删除、移动 Web 部件或调整其大小来更改 Web 部件的布局。
    
  
- 更改所有用户的 Web 部件设置（Web 部件的共享视图）。
    
  
- 更改其个人 Web 部件设置（Web 部件的个人视图）。
    
  
表 1 显示了在要限制 Web 部件区域时应考虑的重要属性。
  
    
    

**表 1. 用于限制内容作者的 Web 部件区域属性**


|**属性名称**|**说明**|
|:-----|:-----|
|**AllowLayoutChange** <br/> |指定是否可关闭、最小化、删除或还原 Web 部件区域中的 Web 部件。  <br/> 如果设置为 **False**，则用户无法关闭、最小化、删除或还原 Web 部件区域中的 Web 部件，也无法将 Web 部件拖动到其他区域或者重新排列或移动 Web 部件区域中的 Web 部件。用户也无法添加 Web 部件目录中的 Web 部件，且影响 Web 部件区域中的 Web 部件的 UI 的若干属性将被禁用。此属性不会影响以编程方式更改布局的能力。  <br/> 如果设置为 **True**，则具有适当权限的用户可以执行这些操作。  <br/> |
|**LockLayout** <br/> |指定是否可添加、删除、移动 Web 部件区域中的 Web 部件或调整其大小。无论 Web 部件页是在个人视图中还是共享视图中，此属性的工作方式都相同。  <br/> 如果设置为 **True**，则 Web 部件区域中每个 Web 部件受影响的特定 Web 部件属性为："区域(ZoneID)"、"部件顺序(PartOrder)"、"在页面上可见(IsVisible)"、"高度(Height)"、"宽度(Width)"、"允许关闭(AllowRemove)"和"IsIncluded"（"Web 部件"菜单上的"关闭"命令）。其他 Web 部件属性不受影响。  <br/> 如果设置为 **False**，则 Web 部件属性决定是否可进行修改（须具有适当的网站权限）。  <br/> |
|**AllowCustomization** <br/> |指定是否可修改 Web 部件区域中的 Web 部件的共享属性值。  <br/> 如果设置为 **True**，则具有适当权限的用户可以为所有用户更改 Web 部件区域中的 Web 部件。  <br/> 如果设置为 **False**，则用户无法在共享视图的 UI 中更改 Web 部件区域中的 Web 部件。不过，仍可以编程方式以及通过使用 Web 部件维护页进行更改。  <br/> |
|**AllowPersonalization** <br/> |指定是否可修改 Web 部件区域中的 Web 部件的个人属性值。  <br/> 如果设置为 **True**，则具有适当权限的用户可以对 Web 部件区域中的 Web 部件进行更改。  <br/> 如果设置为 **False**，则用户无法通过 UI 更改 Web 部件，除非 Web 部件是私人 Web 部件且他们具有相应的权限。  <br/> |
   

> **注释**
> 您无法在设备通道面板中插入 Web 部件区域。如果要允许作者向页面中添加 Web 部件，并且您不关心移动设备的页面权重，则可以将富文本编辑器页字段添加到设备通道面板，然后指示作者在那里添加 Web 部件。您可将 Web 部件直接添加到设备通道面板（不使用 Web 部件区域）。有关详细信息，请参阅 [如何：在 SharePoint 2013 中添加设备通道面板代码段](how-to-add-a-device-channel-panel-snippet-in-sharepoint-2013.md)。 
  
    
    


## 插入 Web 部件区域代码段
<a name="InsertSnippet"> </a>

和所有代码段一样，您从代码段库添加此代码段。要导航到代码段库，您必须先选择要编辑的页面布局。Web 部件区域可添加到页面布局中，但无法添加到母版页中。
  
    
    

### 插入 Web 部件区域代码段


1. 浏览到发布网站。
    
  
2. 在页面右上角，选择"设置"齿轮，然后选择"设计管理器"。
    
  
3. 在设计管理器的左导航窗格中，选择"编辑页面布局"。
    
  
4. 选择要向其添加代码段的页面布局的名称。
    
  
5. 若要打开代码段库，请选择服务器端预览右上角的"代码段"。
    
  
6. 在功能区的"设计"选项卡上，选择"Web 部件区域"。
    
  
7. 在代码段库右侧的"关于此组件"下，单击或选择节标题以展开或折叠属性组，然后配置所需的任何自定义设置。
    
    名为"重要"的节包含对此特定代码段的工作方式至关重要的属性。对于 Web 部件区域，此代码段具有一个唯一 ID。在将此代码段复制到您的页面布局后，您不应重用此 ID。如果您要添加另一个 Web 部件区域代码段，请选择"刷新"以便为下一代码段生成一个新 ID。
    
    有关限制 Web 部件区域所需属性（ **LockLayout**、 **AllowCustomization** 和 **AllowPersonalization**）的说明，请参见表 1。
    
    > **注释**
      > 您可能注意到某些属性名称在代码段库的属性网格中是粗体。这些属性的值已从此组件的默认设置更改为其他设置，但这些属性不一定与设计人员方案相关。换言之，虽然某个属性可能为粗体，但它未必对您的方案很重要。 
8. 配置任何属性后，选择"更新"。这将更新页面左侧的 HTML 代码段，以使标记反映出您的自定义设置。您可以随时选择"重置"将所有属性恢复为其默认设置。
    
  
9. 在代码段库左侧的"HTML 代码段"下，选择"复制到剪贴板"。
    
  
10. 在 HTML 编辑器中，打开您计算机上的映射网络驱动器，然后打开您要向其添加代码段的母版页或页面布局对应的 HTML 文件。
    
    有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
    
  
11. 在 HTML 文件中，将代码段粘贴到希望显示标记的位置。
    
    在将代码段添加到页面布局时，务必将代码段粘贴到 **PlaceHolderMain** 内。
    
  
12. 将  `class="DefaultContentBlock"` 的 **<div>** 替换为您自己的特定内容。
    
  
13. 如果您要用 Web 部件预填充此区域  例如，如果此区域将限制内容作者只能修改现有 Web 部件而不能添加新 Web 部件  请在 **<!--DC … -->** 标记出现的位置插入 Web 部件代码段。
    
  
14. 保存页面，然后刷新设计管理器中的服务器端预览以确保页面按预期显示。
    
  

## 理解代码段标记
<a name="UnderstandMarkup"> </a>

Web 部件区域代码段的两个最重要部分是"ID"属性和 **<!--DC … -->** 注释。每个区域都应具有一个唯一 ID。如果您要将多个 Web 部件区域添加到您的页面布局，请确保在代码段库中选择"刷新"，然后再复制每个代码段，以便生成新 ID。 **<!--DC … -->** 注释应替换为您希望默认显示在此区域中的任何 Web 部件。
  
    
    
下面的代码中显示了可用于限制内容作者使用区域的方式的其他属性（ **AllowCustomization**、 **AllowPersonalization** 和 **LockLayout**）。
  
    
    

> **注释**
> 仅当您在属性网格中更改 **AllowCustomization**、 **AllowPersonalization** 和 **LockLayout** 属性的默认值时，这些属性才显示在标记中。
  
    
    




```HTML

<div data-name="WebPartZone">
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <div xmlns:ie="ie">
        <!--MS:<WebPartPages:WebPartZone runat="server" ID="x0e5f5212505f48a9aac43df13eeae4f9" AllowCustomization="True" AllowPersonalization="False" FrameType="TitleBarOnly" LockLayout="True" Orientation="Vertical">-->
            <!--MS:<ZoneTemplate>-->
               <!--DC: Replace this comment with default web parts for new pages. -->
            <!--ME:</ZoneTemplate>-->
        <!--ME:</WebPartPages:WebPartZone>-->
    </div>
    <!--CE: End Web Part Zone Snippet-->
</div>

```


## 其他资源
<a name="AdditionalResources"> </a>


-  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)
    
  
-  [WebPartZone 类](http://msdn.microsoft.com/zh-cn/library/system.web.ui.webcontrols.webparts.webpartzone.aspx)
    
  
-  [WebPartZoneBase 属性](http://msdn.microsoft.com/zh-cn/library/335sw9k3.aspx)
    
  
-  [为 SharePoint 构建网站](build-sites-for-sharepoint.md)
    
  
-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  

