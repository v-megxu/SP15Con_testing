---
title: 如何：在 SharePoint 2013 中将样式应用到页面字段
ms.prod: SHAREPOINT
ms.assetid: e227613d-0e4d-4312-924d-bb55e1fe4293
---


# 如何：在 SharePoint 2013 中将样式应用到页面字段
在页面布局中，您可以将样式应用到一个页字段，当内容作者从该页面布局中创建一个页面时，这些样式会应用于内容作者添加的所有内容中。另外，您还有更多选项来控制设置 RichHtmlField 页字段内容样式的方式。
## 将样式应用于页字段的简介
<a name="Introduction"> </a>

作为设计者，您对页面布局上页字段和从该页面布局创建的所有页面的定位和样式设置拥有最终控制权。内容作者通过浏览器创建页面时，他们不能移动页面上的页字段，或者覆盖您设定的样式。这可帮助您的品牌在站内所有页面保持一致。
  
    
    
当您将样式应用于页字段时，需要考虑两类基础字段类型：
  
    
    

- **非 RichHtmlField 的字段类型** 组成页面布局的页字段符合该页面布局的内容类型。页字段可以是多种类型，比如单行文本 (TextField) 或多行文本 (NoteField)。作为设计者，您可以在页面布局中直接将样式应用于页字段，并以相同方式将样式应用于所有页字段。
    
  
- **RichHtmlField** rich HTML 字段控件（也称为发布 HTML字段）是页面布局中最强大且最常使用的控件。默认情况下，在 rich HTML 字段中，内容作者使用功能区来设计样式，并将样式应用于内容，以插入表格、图像和音频等多媒体，以及 Web 部件。当您想授权内容作者在您控制的参数内自由添加和设置内容样式时，该字段类型是有用的。您可以通过两种方式控制 RichHtmlField：
    
  - **创建自定义样式表** 默认情况下，RichHtmlField 功能区上可用的样式来自名为 HtmlEditorStyles.css 的样式表。您可以为这个代码段配置 **PrefixStyleSheet** 属性，这样您的自定义样式将会出现在供内容作者使用的功能区上。
    
  
  - **配置 Allow 属性** RichHtmlField 的一个代码段拥有 28 个以 **Allow** 开头的可用属性，您可以使用这些属性使内容作者不可以使用功能区上特定的命令或命令群。例如，如果您将 **AllowFontsMenu** 属性设置为 **False**，作者就不能使用功能区的字体菜单来更改应用于文本的字体；他们只能使用您规定的 CSS 样式。
    
  
对包括 RichHtmlField 在内的所有页字段类型而言，设计者决定设置内容样式的方式。您可以使用 RichHtmlField 授权内容作者自由插入多种格式的内容和应用样式，但是您仍拥有可添加内容和可应用样式的最终控制权。
  
    
    

## 将样式应用于非 RichHtmlField 的页字段
<a name="Applying"> </a>

使用页字段控件，您可定义内容使用的样式。 作者可添加内容至页面，但是设计者控制如何通过应用于这些控件的 CSS 呈现内容。
  
    
    
HTML 页面布局中，每个页面字段都封装在一个 **<div>** 标记中。要将样式应用于一个页字段，您可以直接将一个样式添加至 **<div>**，例如  `<div style="font-weight:bold"`。但是更为常见和有效的情形是，您为页面布局中每个页面字段的 **<div>** 添加一个 **id** 属性，然后使用此 **id** 作为驻留在外部样式表中的样式选择器。这样的话，如果您拥有多种设备渠道，并且每个渠道拥有自己的样式表，您就可以为每个渠道的每个页字段应用不同的样式。例如，下列 TextField（也称为多行文本）类型的页字段在 **<div>** 标记上可能只有一个 **id** 属性。
  
    
    



```HTML

<div id="ShortSummaryPageField">
<!--CS: Start Page Field: ShortSummary Snippet-->
<!--SPM:<%@Register Tagprefix="PageFieldNoteField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<PageFieldNoteField:NoteField FieldName="a5249942-2dc5-4917-85e2-661d019ad548" runat="server">-->
<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">ShortSummary</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field">ShortSummary field value.</div></div></div><!--PE: End of READ-ONLY PREVIEW-->
<!--ME:</PageFieldNoteField:NoteField>-->
<!--CE: End Page Field: ShortSummary Snippet-->
</div>
```

有关页面布局样式和样式引用的位置的详细信息，请参阅 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)。
  
    
    

## 禁用 RichHtmlField 功能区上的选项
<a name="Disabling"> </a>

当内容作者创建或编辑一个页面，然后使用浏览器将内容添加到 RichHtmlField，他们可以使用该字段功能区上的命令来设置格式、样式，或插入多种格式的内容和媒体。 
  
    
    
在代码段库，您可以配置 RichHtmlField 类型的页字段属性，以使作者无法使用功能区上的特定命令或命令群。例如，将 **AllowFontSizesMenu** 属性设置为 **False**，这样您就可以禁用功能区上的 **Font Size** 菜单。将 **AllowFonts** 属性设置为 **False**，您可以禁用功能区上的整个"字体"群。
  
    
    
配置代码段库的这些属性之后，这些属性将出现在  `<!--MS:>` 评论的代码段标记中。
  
    
    



```HTML

<div data-name="Page Field: ArticleBody">
<!--CS: Start Page Field: ArticleBody Snippet-->
<!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<PageFieldRichHtmlField:RichHtmlField runat="server" AllowFonts="False" FieldName="db3168db-8778-4fb6-a48f-57f598497388">-->
<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div id="ctl02_label" style="display:none">ArticleBody</div><div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label"><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">ArticleBody</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field">ArticleBody field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div></div></div></div>
<!--PE: End of READ-ONLY PREVIEW-->
<!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
<!--CE: End Page Field: ArticleBody Snippet-->
</div>
```


> **注释**
> 如果您将 **AllowFonts** 设置为 **False**，内容作者仍可以使用键盘快捷键，例如使用 CTRL+B（粗体）格式化文体。为避免作者为文本添加任意样式，您可以将 **AllowTextMarkup** 设置为 **False**。这样设置以后，当内容作者试图保存包含应用于文体的样式的内容时，浏览器中的 HTML 编辑器会返回一个错误，并提示作者移除无效标记。 
  
    
    

RichHtmlField 页字段包含 28 个不同的 **Allow** 属性。有关特定属性控制内容的详细信息，请参阅 [RichHtmlField 属性](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.publishing.webcontrols.richhtmlfield_properties)。有关添加和配置代码段的详细信息，请参阅  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)。
  
    
    

## 控制 RichHtmlField 中可用的样式
<a name="Controlling"> </a>

在 RichHtmlField 中，内容作者可以使用功能区上的选项格式化内容。使用 CSS 来实施这些格式选项，这些样式在名为 HtmlEditorStyles.css 的 SharePoint 样式表中定义，此表驻留在以下地址其中之一的服务器上：
  
    
    

- C:\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\STYLES 
    
  
- C:\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\FEATURES\\PublishingLayouts\\en-us
    
  
因为浏览器上的 RichHtmlField 使用 CSS 实施其样式，您也可以创建与您网站品牌相一致的样式，然后确保这些样式置于功能区，可为内容作者使用。为了对默认样式做最少的改变，您可以从 HtmlEditorStyles.css 复制一份现有的样式至您的样式表（由页面布局引用），然后通过改变 CSS 属性和值（不是选择器）来修改样式。您也可以将其复制到您的样式表，然后设置  `display:none`，从而从功能区将默认样式隐藏。
  
    
    
要实施自定义样式，您也可以通过改变 RichHtmlField 代码段的 **PrefixStyleSheet** 属性，重新创建一个样式表。默认情况下，这一属性设置为 **ms-rte**，然后在默认样式表 HtmlEditorStyles.css 中的每个样式都将以此前缀开头，例如：
  
    
    



```HTML

H1. ms-rteElement-H1
{
-ms-name:"Heading 1";
-ms-element:"true";
}
```

当您改变 **PrefixStyleSheet** 属性的值，现有 **ms-rte** 样式在 rich HTML 编辑器中都不可用，只有您创建的并使用了新前缀的样式可供内容作者使用。这意味着，如果您想要使用默认样式，您必须将它们复制到您的样式表并进行修改，以使它们使用新的前缀。
  
    
    

> **注释**
> **PrefixStyleSheet** 属性是按照每个 RichHtmlField 页字段定义的，但是多个页字段可以使用此属性的同一值。所以，如果多个页面布局引用同一个样式表，很有可能位于这些页面布局上的多个 RichHtmlFields 包含相同的样式前缀并引用同样的样式。
  
    
    


### 为 RichHtmlField 定义一个新的样式表


1. 浏览您的发布网站。
    
  
2. 在页面右上角，选择"设置"，然后选择"设计管理器"。
    
  
3. 在设计管理器的左导航窗格中，选择"编辑页面布局"。
    
  
4. 选择 RichHtmlField 页字段将驻留的页面布局。
    
  
5. 在服务器端预览的右上角中，选择"代码段库"。
    
  
6. 在功能区上，选择"页字段" ，然后选择"RichHtmlField"样式的一个页字段。
    
  
7. 在属性网格，展开"杂项"部分，然后将 **PrefixStyleSheet** 属性更改为 **ms-rte** 之外的一个值，例如，将值更改为 **customstyle**。
    
    > **重要信息**
      > 该属性值必须是小写字母。 
8. 选择"更新"。
    
  
9. 在代码段库的左侧，选择"复制到剪贴板"。
    
  
10. 在您电脑上映射网络驱动器中，打开您 HTML 编辑器中的 HTML 页面布局。
    
    > **注释**
      > 有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。 
11. 在 HTML 页面布局中，在 **PlaceHolderMain** 中粘贴 HTML 代码段。
    
  
12. 保存 HTML 页面布局。HTML 文件的更改与相关 .aspx 页面布局同步。
    
    关于这一点，如果内容作者基于这个页面布局创建或编辑一个页面，HTML 编辑器功能区上的样式均不可用，因为这个特定的页字段只使用以新前缀 **customstyle** 开头的样式，而这些样式还未被重新定义。
    
  
13. 在服务器上，浏览至以下位置，并打开 HtmlEditorStyles.css：
    
    C:\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\STYLES
    
    查看默认样式，了解它们以何种方式编写，并可能通过将这些样式复制到您的样式表然后进行修改来重新使用其中的一些样式，这些操作是很有用的。如果您执行这些操作，请用您自己的前缀替换默认的 **ms-rte** 前缀。
    
    > **重要信息**
      > 请勿修改默认的样式表 HtmlEditorStyles.css。这个样式表为场中每一个 RichHtmlField 提供样式。另外，服务更新或升级都可能会覆盖这个文件，导致您失去所有更改。 
14. 在您的样式表中，创建一个以新前缀开头的新样式表。
    
    例如，如果 **customstyle** 是新前缀，您的样式表可能会包含以下样式。
    


  ```HTML
  
H2.customstyleElement-H2
{
-ms-name:"Heading 2";
-ms-element:"true";
}
customstyleElement-H2
{
font-weight: bold;
font-family: Cambria;
font-size: 16pt;
} 

  ```


    为清楚起见，类名和出现在功能区的样式名与样式属性分开定义。在此示例中， **H2** 是样式的元素选择器， **customstyleElement-H2** 是样式的类名。类名包含两个部分： **customstyle** 是您为页字段规定的前缀， **Element** 规定该样式将出现在 HTML 编辑器功能区上"样式"库的"页面元素"部分 。 **-ms-name** 属性设置样式库中向内容作者显示的显示名称。
    
    通过解析紧接前缀之后的类名和寻找以下字符串之一，SharePoint 映射一个样式至功能区上的一个菜单或命令：
    
  - **Element**：样式库的"页面元素"部分
    
  
  - **Style**：样式库的"文本样式"部分
    
  
  - **FontSize**："字号"菜单
    
  
  - **ThemeFontFace**："字体"菜单
    
  
  - **ForeColor**： "字体颜色"菜单
    
  
  - **BackColor**："突出显示颜色"菜单
    
  
  - **Image**："图像"菜单
    
  
  - **Table**："表格"菜单
    
  
  - **Position**：段落组的"对齐"按钮
    
  

    有关页面布局样式应驻留位置的详细信息，请参阅 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)。
    
  

## 其他资源
<a name="Additional"> </a>


-  [SharePoint 2013 中的设计管理器概述](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)
    
  

