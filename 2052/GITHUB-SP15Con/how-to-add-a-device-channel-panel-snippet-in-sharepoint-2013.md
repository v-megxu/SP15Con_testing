---
title: 如何：在 SharePoint 2013 中添加设备通道面板代码段
ms.prod: SHAREPOINT
ms.assetid: 612780a8-6267-49f6-a32d-33600bb5f6b4
---


# 如何：在 SharePoint 2013 中添加设备通道面板代码段
设备通道面板是可添加到母版页或页面布局中以控制您创建的每个通道所呈现内容的代码段。设备通道面板的主要目的是在不同的通道上有选择地显示单个页面布局中的不同页字段。
## 设备通道面板代码段简介
<a name="Introduction"> </a>

设备通道面板是可添加到母版页或页面布局中以控制您创建的每个通道所呈现内容的控件。设备通道面板是指定一个或多个通道的容器；如果呈现页面时，一个或多个这些通道处于活动状态，则还将呈现该设备通道面板的所有内容。设备通道面板可包括任何类型的内容（包括到 CSS 文件或 .js 文件的链接）。它是一种包括特定通道的特定内容的简单方法。
  
    
    
使用设备通道面板最常用的方案也许是有选择地包括特定通道的一部分页面布局。例如，您可使页面布局包含用于长问候语和短问候语的单独的文本字段。通过将页字段置于设备通道面板内，可仅对电话显示短问候语和仅对桌面显示长问候语。设备通道面板的内容不会显示在已排除的通道中，事实上，根本不会呈现该内容，这样避免了内容通过网络传送。因此，与使用带有  `Display:None` 的 CSS 类相比，使用设备通道面板是一种显示特定通道内容的更好办法，因为设备通道面板可帮助降低特定通道的页面权重。
  
    
    
还可在母版页上使用设备通道面板。例如，如果具有可容纳两种不同设备（或两个不同的浏览器） 而几乎不需要进行更改的母版页，则可使用设备通道面板保留特定于其中任一设备的母版页上的内容。
  
    
    
使用设备通道面板有以下两个限制：
  
    
    

- **显示模板** 由于显示模板呈现在客户端，而设备通道面板在服务器端运行，因此您无法在显示模板内使用设备通道面板。相反，您应当在您页面布局上的设备通道面板内使用两个不同的内容搜索 Web 部件，或者使用 JavaScript 变量在显示模板本身内触发所需的行为。
    
  
- **Web 部件区域** 您不能在设备通道面板内插入 Web 部件区域。如果您希望允许作者向某页面添加 Web 部件，并且您不担心移动设备的页面权重，则您可以向设备通道面板添加一个 RTF 编辑器页字段，然后指示作者在那里添加 Web 部件。您可以直接向设备通道面板添加 Web 部件（而无需 Web 部件区域）。
    
  

## 插入设备通道面板代码段
<a name="InsertSnippet"> </a>

像所有代码段一样，您可以从代码段库中添加设备通道面板代码段。若要导航到代码段库，必须首先选择一个要编辑的母版页或页面布局。
  
    
    

### 插入设备通道面板代码段


1. 浏览到您的发布网站。
    
  
2. 在该页面的右上角，选择"设置"齿轮，然后选择"设计管理器"。
    
  
3. 在设计管理器的左侧导航窗格中，选择"编辑母版页"或"编辑页面布局"，具体取决于您所编辑文件的类型。
    
  
4. 选择您要向其中添加代码段的母版页或页面布局的名称。
    
  
5. 若要打开代码段库，请选择服务器端预览右上角中的"代码段"。
    
  
6. 在功能区的"设计"选项卡上，选择"设备通道面板"。
    
  
7. 在代码段库右侧的"关于此组件"下面，单击或选择节标题以展开或折叠属性组，然后配置所需的任何自定义设置。
    
    名为"重要信息"的一节包含决定此特定代码段如何工作的属性。对于设备通道面板，"IncludedChannels"属性是最重要的。对于此属性，输入您要显示此设备通道面板所包含的内容的每个设备通道的别名。如果您输入多个别名，请用逗号将每个别名隔开。
    
    > **注释**
      > 如果您编辑设备通道列表中的通道别名，则必须手动查找并更新在您设计文件中出现的该别名，包括更新使用该别名的每个设备通道面板的"IncludedChannels"属性 
8. 在您配置好任何其他属性后，选择"更新"。这将更新页面左侧的 HTML 代码段，以便该标记反映出您的自定义设置。您始终都可以选择"重置"以将所有属性恢复为其默认设置。
    
  
9. 在代码段库左侧的"HTML 代码段"下面，选择"复制到剪贴板"。
    
  
10. 在您的 HTML 编辑器中，打开计算机上的映射网络驱动器，然后打开您要向其中添加代码段的母版页或页面布局的 HTML 文件。
    
    有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
    
  
11. 在 HTML 文件中，将代码段粘贴到您希望标记显示的位置。
    
    如果您将代码段添加到页面布局，请确保将代码段粘贴到 **PlaceHolderMain** 内部。
    
  
12. 将  `class="DefaultContentBlock"` 的 **<div>** 替换为您自己的特定内容。
    
    通常，如果您要向页面布局添加设备通道面板，则您可以通过在面板内复制页字段来替换 **<div>**。
    
  
13. 保存该页面，然后刷新设计管理器中的服务器端预览，以确保设备通道面板按预期方式显示。
    
    若要在不同通道上预览面板，您可以向 URL 添加查询字符串参数。例如，您可以将查询字符串变量  `"DeviceChannel=YourChannelAlias"` 追加到服务器端预览中任何页面的 URL 后面。
    
  

## 了解代码段标记
<a name="UnderstandMarkup"> </a>

设备通道面板代码段的两个最重要的部分是 **IncludedChannels** 属性和 `class="DefaultContentBlock"` 的 **<div>**。默认情况下， **IncludedChannels** 属性为空。在属性网格的"重要信息"部分中，您应当输入要在此面板显示内容的设备通道的别名（用逗号分隔）。
  
    
    

> **注释**
> 如果您更改设备通道列表中的别名，则还必须更改在您标记中出现的该别名，包括使用该别名的每个设备通道面板的 **IncludedChannels** 属性。
  
    
    

 `class="DefaultContentBlock"` 的 **<div>** 应当替换为您要为包括的通道显示的任意特定内容。设备通道面板可包括几乎任何类型的内容，包括到 CSS 文件或 .js 文件的链接。使用设备通道面板最常用的方案是包括特定通道的页面布局中的特定页字段。在这种情况下，您复制页字段标记，其中 **<div>** 位于设备通道面板内部。
  
    
    



```HTML

<div data-name="DeviceChannelPanel">
    <!--CS: Start Device Channel Panel Snippet-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:DeviceChannelPanel runat="server" IncludedChannels="MyPhoneChannel, MyTabletChannel">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
       <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Device Channel Panel Properties.    
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</Publishing:DeviceChannelPanel>-->
    <!--CE: End Device Channel Panel Snippet-->
</div>

```


## 其他资源
<a name="AdditionalResources"> </a>


-  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)
    
  
-  [SharePoint 2013 设计管理器设备通道](sharepoint-2013-design-manager-device-channels.md)
    
  
-  [为 SharePoint 构建网站](build-sites-for-sharepoint.md)
    
  
-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  

