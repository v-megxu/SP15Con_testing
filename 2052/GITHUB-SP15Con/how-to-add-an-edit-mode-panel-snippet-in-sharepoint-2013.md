---
title: 如何：在 SharePoint 2013 中添加编辑模式面板代码段
ms.prod: SHAREPOINT
ms.assetid: 39fa1e32-9129-407d-914f-96f4c6e66dc8
---


# 如何：在 SharePoint 2013 中添加编辑模式面板代码段
编辑模式面板是一个代码段，您可使用它对内容作者显示说明或其他内容，仅当内容作者编辑页面时，才能看到该面板的内容。相反地，还可将此代码段配置为仅在普通（视图）模式而非编辑模式中显示其内容。
## 编辑模式面板简介
<a name="Introduction"> </a>

在发布网站中，拥有必需权限的内容作者可创建或编辑驻留在页面库中的页面。通常，作者会选择创建或编辑页面，然后将内容添加到不同页字段中。
  
    
    
作为设计者，您可以将编辑模式面板添加到母版页或页面布局中，并且仅当内容作者选择编辑基于该页面布局的页面或与该母版页关联的页面时，他们才会看到此代码段的内容。例如，您可以使用编辑模式面板，仅在页面处于编辑模式时才对内容作者显示以下内容：
  
    
    

- 页字段（例如 **Schedule Publishing Date**），该内容对内容作者很重要，但对查看活动网站页面的访问者不重要。
    
  
- 应在页字段中输入哪种类型的内容的描述。
    
  
- 内容作者的注意事项：他们应考虑页面针对不同设备通道显示的外观。
    
  
您还可以在编辑模式面板中放入指向不同样式表的链接，以便您可以为编辑模式和查看模式提供不同样式。
  
    
    
在内容作者的注意事项特定于页面布局基于的内容类型时，应在此页面布局中添加编辑模式面板。在作者的注意事项适用于将与母版页关联的所有页面时（例如，如果此面板包含有关为使用该母版页的特定设备通道提供内容的说明），您还可以在该母版页中添加此代码段。
  
    
    
如果在您的方案中，仅当网站访问者编辑页面时才对他们（但不对内容作者）显示内容很有用或有益，您还可以将编辑模式面板设置为仅在普通模式而非编辑模式中显示其内容。
  
    
    

### 插入编辑模式面板
<a name="InsertSnippet"> </a>

与所有代码段一样，您可以从代码段库添加此代码段。若要导航到代码段库，必须先选择要编辑的母版页或页面布局。
  
    
    

### 插入编辑模式面板


1. 浏览到发布网站。
    
  
2. 在页面右上角中，选择"设置"齿轮，然后选择"设计管理器"。
    
  
3. 在设计管理器的左导航窗格中，选择"编辑母版页"或"编辑页面布局"，具体取决于要编辑的文件的类型。
    
  
4. 选择要在其中添加代码段的母版页或页面布局的名称。
    
  
5. 若要打开代码段库，请选择服务器端预览右上角的"代码段"。
    
  
6. 在功能区的"设计"选项卡上，选择"编辑模式面板"，然后选择希望代码段显示在其中的模式。
    
  
7. 在代码段库右侧的"关于此组件"下，单击或选择节标题可展开或折叠属性组，然后配置需要的所有自定义设置。
    
    名为"重要信息"的一节包含决定此特定代码段的运行方式的属性。对于编辑模式面板， **PageDisplayMode** 属性将设置为 **Edit** 或 **Display**，具体取决于在功能区上选择的模式。
    
  
8. 在配置完所有属性后，选择"更新"。这样会更新页面左侧的 HTML 代码段，以使标记反映您的自定义设置。您随时都可以选择"重置"，以将所有属性恢复为其默认设置。
    
  
9. 在代码段库左侧的"HTML 代码段"下，选择"复制到剪贴板"。
    
  
10. 在 HTML 编辑器中，打开您计算机上的映射网络驱动器，然后打开要在其中添加代码段的母版页或页面布局对应的 HTML 文件。有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
    
  
11. 在 HTML 文件中，将代码段粘贴到您希望此标记显示的位置。
    
    如果是在页面布局中添加编辑模式面板，请确保将此代码段粘贴到 **PlaceHolderMain** 中，以使此面板在编辑模式下对内容作者可见。您可以将此代码段直接粘贴到特定页字段前面，也可以将一个或多个页字段放入编辑模式面板中。
    
  
12. 将 **<div>**（其中  `class="DefaultContentBlock"`）替换为自己的特定内容（例如，内容作者的注意事项或说明），或对作者有用但对网站访问者没有用的特定页字段。
    
  
13. 保存页面，然后刷新设计管理器中的服务器端预览，以确保编辑模式面板按预期显示。
    
  

## 了解代码段标记
<a name="UnderstandMarkup"> </a>

编辑模式面板代码段的两个最重要部分是 **PageDisplayMode** 属性和 **<div>**（其中  `class="DefaultContentBlock"`）。 **PageDisplayMode** 属性用于确定面板内容是仅显示在编辑模式中还是普通/显示模式中（意即在页面不处于编辑模式时）。
  
    
    

> **注释**
> 此属性不会显示在标记中，除非将值更改为 **Display**。当此属性不显示在标记中时，此代码段的默认模式是编辑模式。 
  
    
    

 **<div>**（其中  `class="DefaultContentBlock"`）是使用自己的内容替换的内容，其中可包含其他代码段和控件。
  
    
    



```HTML

<div data-name="EditModePanelShowInEdit">
    <!--CS: Start Edit Mode Panel Snippet-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" PageDisplayMode="Display" CssClass="edit-mode-panel">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
        <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Edit Mode Panel Properties.
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Edit Mode Panel Snippet-->
</div>
```


## 其他资源
<a name="AdditionalResources"> </a>


-  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)
    
  
-  [如何：在 SharePoint 2013 中添加安全修整代码段](how-to-add-a-security-trim-snippet-in-sharepoint-2013.md)
    
  
-  [为 SharePoint 构建网站](build-sites-for-sharepoint.md)
    
  
-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  

