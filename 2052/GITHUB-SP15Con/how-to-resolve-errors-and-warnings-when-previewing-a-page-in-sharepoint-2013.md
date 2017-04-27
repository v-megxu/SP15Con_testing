---
title: 如何：在 SharePoint 2013 中预览页面时解决错误和警告
ms.prod: SHAREPOINT
ms.assetid: 03f72f65-b22b-4304-be92-f44ce0619372
---


# 如何：在 SharePoint 2013 中预览页面时解决错误和警告
在将 HTML 文件转换为 SharePoint 2013 母版页后，或在创建页面布局后，您可以在浏览器中预览该页面。但在可以预览母版页或页面布局之前，您可能必须解决阻止服务器端预览呈现页面的所有问题。
## 处理预览错误的说明
<a name="Introduction"> </a>

在将 HTML 文件转换为 SharePoint 2013 母版页后，或在创建页面布局后，您可以在浏览器中预览该页面。在编辑和保存 HTML 母版页或页面布局时，您可以刷新预览以充分了解 SharePoint 2013 如何呈现您的页面。
  
    
    
设计管理器中的预览是服务器端实时预览，因此，您的页面中的任何代码段或控件（例如导航控件或搜索驱动的 Web 部件）均使用实时数据。此外，在您预览母版页或页面布局时，可以仅针对该文件选择常规预览，也可以选择预览如何使用该母版页或页面布局呈现您网站中的特定页面。服务器端预览是一个非常有用的工具，它对 HTML 编辑器中的设计时预览进行了补充。有关详细信息，请参阅 [如何：在 SharePoint 2013 设计管理器中更改预览页面](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)。
  
    
    
但在您可以预览母版页或页面布局之前，您可能必须解决阻止服务器端预览呈现页面的所有问题。如果服务器端预览未运行，那么在将母版页或页面布局应用于您的网站之后，它们也不会运行。在设计管理器中，在您转换母版页或创建页面布局后，可单击文件名或转换状态来预览该文件。在预览页面中，页面顶部的通知区域将显示相关错误或警告。
  
    
    
此处是您可能遇到的预览错误和警告，以及如何处理这些错误和警告的相关帮助。
  
    
    

## HTML 文件不能包含 <form> 标记
<a name="FormTags"> </a>


### 消息

 **母版页包含一个或多个 HTML <FORM> 标记。要使母版页工作，请删除标记(但是您可以保留标记内容)。**
  
    
    

### 解决方法

SharePoint 2013 页面已封装在 **<form>** 标记内，以便 ASP.NET 可以进行回发（特别是在 SharePoint 2013 母版页包含 **<SharePoint:SharePointForm>** 标记时，该标记会在呈现关联的内容页时创建一个实际的 **<form>** 标记）。因此，在母版页或页面布局中包含 **<form>** 标记意味着最终呈现的页面中将有嵌入的 **<form>** 标记，这在 HTML 中是无效的。在您的 HTML 编辑器中，删除所有 **<form>** 标记，保存页面，然后刷新预览。
  
    
    
如果您希望在页面布局中使用 HTML **<form>** 标记，则应通过在您的 HTML 页面布局中添加以下代码，将 Form 标记置于 ID 为 **PlaceHolderUtilityContent** 的内容占位符中：
  
    
    



```HTML

<!--CS: Start Create Snippets From Custom ASP.NET Markup Snippet-->
<!--SPM:<SharePoint:AjaxDelta id="DeltaPlaceHolderUtilityContent" runat="server">-->
<!--SPM:<asp:ContentPlaceHolder id="PlaceHolderUtilityContent" runat="server" />-->
<!--SPM:</SharePoint:AjaxDelta>-->
<!--CE: End Create Snippets From Custom ASP.NET Markup Snippet-->
```

您还可以从代码段库向您的页面中添加 HTML 表单 Web 部件或 InfoPath 表单 Web 部件。有关详细信息，请参阅 [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)。
  
    
    

## HTML 文件必须与 XML 兼容
<a name="XMLCompliant"> </a>


### 消息

 **SharePoint 要求 HTML 文件与 XML 兼容。您的文件与 XML 不兼容，可能的原因有: 标记属性缺少引用、缺少结束标记或标记属性无效。{错误类型，错误位置}。发生时间: {时间}。**
  
    
    

### 解决方法

要转换为相应 ASP.NET 文件的 HTML 文件必须与 XML 兼容。该错误确定您的 HTML 文件中与 XML 不兼容的特定标记。通过 XML 验证程序运行 HTML 文件，使用 HTML 编辑器修复任何问题，保存文件并刷新此预览。
  
    
    

> **注释**
> 该要求会覆盖某些 HTML 5 标准。例如，在 HTML 5 中，您可以将文档类型指定为小写，但在 XML 中，文档类型必须为大写。 
  
    
    


  
    
    

## HTML 文件包含有问题的标记
<a name="ProblematicMarkup"> </a>


### 消息

 **SharePoint 无法分析该文件，这很可能是因为错误设置了 SharePoint 代码段的格式。以下位置中的标记导致出现问题。手动编辑该标记以修复它，或者将其替换为代码段库中的新代码段。{错误类型，错误位置}。发生时间: {时间}。**
  
    
    

### 解决方法

如果您的 HTML 文件中的 SharePoint 代码段存在问题，则会显示该错误。若要修复该错误，请撤消导致该错误的任何更改，或者从代码段库或者包含有效代码段版本的其他母版页或页面布局文件，将有问题的代码段替换为新代码段。在您的 HTML 编辑器中，在修复或替换代码段后，保存页面，然后刷新预览。
  
    
    

## 页面布局的母版页已更改
<a name="PageLayoutChanged"> </a>


### 消息

 **此页面布局的母版页已更改，将跨您的网站带来不一致性。单击此处更新页面布局中代表母版页区域的部分。**
  
    
    

### 解决方法

若要将页面布局与给定母版页结合使用，这两者必须具有同一组内容占位符。如果您根据特殊母版页创建页面布局，然后编辑该 HTML 母版页，则会显示该消息。即使您知道更改母版页不会添加或删除内容占位符，您也应该始终更新页面布局的内容区域，以便可以预览母版页中可能影响页面布局的任何更改。
  
    
    

## 重置预览
<a name="ResetPreview"> </a>


### 消息

 **您的母版页(页面布局)没有任何警告或错误。将预览重置为其原始状态。**
  
    
    

### 说明

该消息仅确认已完成转换过程，并且没有产生任何错误或问题。但是，当您预览页面时，您可能通过导航离开该特定页面或者以其他某种方式更改预览。如果出现这种情况，您可以随时选择消息区域中的"重置预览"。这样做将刷新预览，使其可以使用您正在使用的特定母版页或页面布局，以及您在左上角的"更改预览页面"选项中选择的任何页面。
  
    
    

## 更改预览页面
<a name="ChangePreviewPage"> </a>


### 消息

 **您当前正预览的母版页(页面布局)不包含任何内容。您可以通过上面的菜单更改预览页面。**
  
    
    

### 说明

如果您不使用实时 SharePoint 2013 页面预览母版页或页面布局，则会显示该消息。例如，如果要预览某页面布局，您可以选择左上角的"更改预览页面"，然后选择要使用您的页面布局预览的特定内容页。通过这种方式，您可以预览包含页字段中的实际页面内容的页面布局。如果希望预览只显示 **ContentPlaceHolderMain** 或页字段的位置，可以随时使用"更改预览页面"切换回常规预览。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 设计管理器中更改预览页面](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)
    
  

