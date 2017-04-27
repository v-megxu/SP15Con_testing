---
title: SharePoint 2013 中的调色板和字体
ms.prod: SHAREPOINT
ms.assetid: c17d375b-151f-48ae-ac32-f2ce9e68d63f
---


# SharePoint 2013 中的调色板和字体
使用此引用定义 SharePoint 2013 网站中使用的调色板或字体方案。
## 调色板
<a name="color"> </a>

调色板是在 SharePoint 网站中使用的多种颜色的集合。SharePoint 网站的调色板在调色板文件中定义。颜色插槽也用于母版页预览文件，以生成网站的缩略图和预览图像。下面介绍了调色板文件和母版页预览文件的结构：
  
    
    

- **调色板文件 (.spcolor)**
    
    调色板文件用于"更改外观"向导，可让用户通过使用 SharePoint 主题用户界面更改其网站的外观。默认情况下，SharePoint 2013 安装了 32 个调色板文件。您还可以创建其他调色板文件。以下示例介绍了调色板文件的格式。
    


  ```XML
  
<s:colorPalette isInverted="InvertedSetting" previewSlot1="Slot1" previewSlot2="Slot2" previewSlot3="Slot3" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:color name="ColorSlot" value="Color" />
    <!--additional color slots-->
</s:colorPalette>
  ```


    在调色板文件中，以下占位符会被替换：
    
  -  _InvertedSetting_ 是一个布尔值。如果调色板是在深色背景上采用普遍浅色文本，则为 **true**。如果调色板是在浅色背景上采用普遍深色文本，则为 **false**。
    
  
  -  _Slot1_ 是将用作调色板图标中第一个颜色块的颜色插槽的批注名称，该图标位于主题设置体验的调色板选取器中。
    
  
  -  _Slot2_ 是将用作调色板图标中第二个颜色块的颜色插槽的批注名称，该图标位于主题设置体验的调色板选取器中。
    
  
  -  _Slot3_ 是将用作调色板图标中第三个颜色块的颜色插槽的批注名称，该图标位于主题设置体验的调色板选取器中。
    
  
  -  _ColorSlot_ 是您所定义的颜色插槽的批注名称（例如，SiteTitle）。
    
  
  -  _Color_ 是将用于指定颜色插槽的颜色的十六进制值。该值可能为 6 位 (RRGGBB) 或 8 位 (AARRGGBB)。如果十六进制值为 8 位，则前两位代表不透明度（00-FF，映射到 0-255）。如果十六进制值为 6 位，则默认不透明度为 100% 或 FF。
    
  

    调色板文件位于根网站的主题库中，根网站位于"15"文件夹 (http:// _SiteCollectionName_/_catalogs/theme/15/) 的网站集中。若要从 SharePoint 用户界面访问主题库，在"网站设置"页面的"Web 设计器库"下选择"主题"，然后选择"15"。
    
  
- **母版页预览文件 (.preview)**
    
    母版页预览文件用于在您使用"更改外观"向导时生成缩略图图像和预览图像。母版页必须具有用于"更改外观"向导的相应预览文件。预览文件是经过特殊格式化的文件，具有针对默认调色板、默认字体方案、已标记化的 CSS 和已标记化的 HTML 的部分。它使用字符串标记来获取颜色插槽、字体名称和本地化 UI 字符串的值。以下示例显示了母版页预览文件中使用的颜色插槽。
    


  ```HTML
  
[ID] #dgp-pageContainer
{
    background-color: [T_THEME_COLOR_PAGEBACKGROUND];
    color: [T_THEME_COLOR_BODYTEXT];
    width: 100%;
    height:100%;     
    background-image: url('[T_IMAGE]');       
    background-size: cover;
    font-family: [T_BODY_FONT];   
}
  ```


    有关详细信息，请参阅 [如何：在 SharePoint 2013 中创建母版页预览文件](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  

> **提示**
> 您可以使用 SharePoint 调色板工具来帮助创建 SharePoint 设计。您可以从 Microsoft 下载中心 [下载 SharePoint 调色板工具](http://www.microsoft.com/en-us/download/details.aspx?id=38182)。 
  
    
    


### 颜色插槽映射
<a name="colorSlots"> </a>

表 1 介绍了可用的颜色插槽及其在 SharePoint 网站中的使用位置。
  
    
    

> **注释**
>  论及导航项，已按下适用于用户单击或触摸导航项的情况。已选定适用于用户导航到页面的情况。 >  下面总结了常规操作流程，以及每一步中适用于导航项链接的颜色插槽：>  导航项链接的基准文字：HeaderNavigationText>  用户将光标悬停在导航项链接上：HeaderNavigationHoverText>  用户单击、触摸或选择导航项链接：HeaderNavigationPressedText>  用户导航到所选择的页面。适用于用户当前所在页面的导航项的颜色插槽：HeaderNavigationSelectedText
  
    
    


**表 1. 颜色插槽**


|**批注名称**|**颜色在 UI 中的使用位置**|**标记名称**|
|:-----|:-----|:-----|
|BodyText  <br/> |正常正文文本。  <br/> |[T_THEME_COLOR_BODYTEXT]  <br/> |
|SubtleBodyText  <br/> |必须比正常文本更浅的正文文本。元数据文本就是一个示例。  <br/> |[T_THEME_COLOR_SUBTLEBODYTEXT]  <br/> |
|StrongBodyText  <br/> |必须从正常正文文本中突出显示的文本的正文文本颜色。  <br/> |[T_THEME_COLOR_STRONGBODYTEXT]  <br/> |
|DisabledText  <br/> |禁用的文本。例如，菜单中不可用的项。  <br/> |[T_THEME_COLOR_DISABLEDTEXT]  <br/> |
|SiteTitle  <br/> |页面标题的文本颜色。  <br/> |[T_THEME_COLOR_SITETITLE]  <br/> |
|WebPartHeading  <br/> |Web 部件标题的文本颜色。  <br/> |[T_THEME_COLOR_WEBPARTHEADING]  <br/> |
|ErrorText  <br/> |根据需要用于错误文本、边框和背景的主要错误颜色。  <br/> |[T_THEME_COLOR_ERRORTEXT]  <br/> |
|AccentText  <br/> |强调正文文本的文本颜色。  <br/> |[T_THEME_COLOR_ACCENTTEXT]  <br/> |
|SearchURL  <br/> |搜索结果中找到的 URL 的文本颜色。也用于突出显示新项或成功状态通知。  <br/> |[T_THEME_COLOR_SEARCHURL]  <br/> |
|Hyperlink  <br/> |超链接的文本颜色。  <br/> |[T_THEME_COLOR_HYPERLINK]  <br/> |
|HyperlinkFollowed  <br/> |已访问过的超链接的文本颜色。  <br/> |[T_THEME_COLOR_HYPERLINKFOLLOWED]  <br/> |
|HyperlinkActive  <br/> |按下时的超链接颜色。  <br/> |[T_THEME_COLOR_HYPERLINKACTIVE]  <br/> |
|CommandLinks  <br/> |必须比正文文本更浅（由于尺寸问题）的大型命令链接。  <br/> |[T_THEME_COLOR_COMMANDLINKS]  <br/> |
|CommandLinksSecondary  <br/> |命令链接颜色，适用于链接较短且因此需要较深颜色来突出显示的情况。  <br/> |[T_THEME_COLOR_COMMANDLINKSSECONDARY]  <br/> |
|CommandLinksHover  <br/> |鼠标悬停时的命令链接颜色。  <br/> |[T_THEME_COLOR_COMMANDLINKSHOVER]  <br/> |
|CommandLinksPressed  <br/> |按下时的命令链接颜色。  <br/> |[T_THEME_COLOR_COMMANDLINKSPRESSED]  <br/> |
|CommandLinksDisabled  <br/> |命令链接被禁用时的命令链接颜色。  <br/> |[T_THEME_COLOR_COMMANDLINKSDISABLED]  <br/> |
|BackgroundOverlay  <br/> |可选背景图像和页面内容之间可见的主要背景颜色。  <br/> |[T_THEME_COLOR_BACKGROUNDOVERLAY]  <br/> |
|DisabledBackground  <br/> |被禁用元素的背景，如输入框或选择框（按钮除外）等的浏览器控件。  <br/> |[T_THEME_COLOR_DISABLEDBACKGROUND]  <br/> |
|PageBackground  <br/> |页面背景颜色。显示在可选背景图像后面。  <br/> |[T_THEME_COLOR_PAGEBACKGROUND]  <br/> |
|HeaderBackground  <br/> |页面页眉区域的背景颜色。  <br/> |[T_THEME_COLOR_HEADERBACKGROUND]  <br/> |
|FooterBackground  <br/> |页面页脚区域的背景颜色。  <br/> |[T_THEME_COLOR_FOOTERBACKGROUND]  <br/> |
|SelectionBackground  <br/> |选定列表项和下拉菜单项的背景颜色。  <br/> |[T_THEME_COLOR_SELECTIONBACKGROUND]  <br/> |
|HoverBackground  <br/> |鼠标悬停时列表项和下拉菜单项的背景颜色。  <br/> |[T_THEME_COLOR_HOVERBACKGROUND]  <br/> |
|RowAccent  <br/> |选定列表项上的强调左边框。  <br/> |[T_THEME_COLOR_ROWACCENT]  <br/> |
|StrongLines  <br/> |鼠标悬停时浏览器控件的边框。  <br/> |[T_THEME_COLOR_STRONGLINES]  <br/> |
|Lines  <br/> |浏览器控件的边框。  <br/> |[T_THEME_COLOR_LINES]  <br/> |
|SubtleLines  <br/> |细边框颜色。例如内联编辑的网格线。  <br/> |[T_THEME_COLOR_SUBTLELINES]  <br/> |
|DisabledLines  <br/> |被禁用浏览器控件（例如输入框和选择框）的边框颜色。  <br/> |[T_THEME_COLOR_DISABLEDLINES]  <br/> |
|AccentLines  <br/> |选定浏览器控件的聚焦边框颜色。  <br/> |[T_THEME_COLOR_ACCENTLINES]  <br/> |
|DialogBorder  <br/> |对话框边框颜色。  <br/> |[T_THEME_COLOR_DIALOGBORDER]  <br/> |
|Navigation  <br/> |水平导航项和垂直导航项的文本颜色。  <br/> |[T_THEME_COLOR_NAVIGATION]  <br/> |
|NavigationAccent  <br/> |选定水平导航项的文本颜色。  <br/> |[T_THEME_COLOR_NAVIGATIONACCENT]  <br/> |
|NavigationHover  <br/> |鼠标悬停时的导航文本颜色。适用于顶部导航和水平模式中的"快速启动"。  <br/> |[T_THEME_COLOR_NAVIGATIONHOVER]  <br/> |
|NavigationPressed  <br/> |按下时的导航项文本颜色。适用于顶部导航和水平模式中的"快速启动"。  <br/> |[T_THEME_COLOR_NAVIGATIONPRESSED]  <br/> |
|NavigationHoverBackground  <br/> |鼠标悬停在导航项上时，垂直模式中"快速启动"项的背景颜色。  <br/> |[T_THEME_COLOR_NAVIGATIONHOVERBACKGROUND]  <br/> |
|NavigationSelectedBackground  <br/> |选择导航项后，垂直模式中"快速启动"项的背景颜色。  <br/> |[T_THEME_COLOR_NAVIGATIONSELECTEDBACKGROUND]  <br/> |
|EmphasisText  <br/> |显示在强调背景顶层的文本颜色。  <br/> |[T_THEME_COLOR_EMPHASISTEXT]  <br/> |
|EmphasisBackground  <br/> |直接显示在强调文本后的强调背景颜色。  <br/> |[T_THEME_COLOR_EMPHASISBACKGROUND]  <br/> |
|EmphasisHoverBackground  <br/> |鼠标悬停时的背景颜色，适用于使用强调背景的元素。  <br/> |[T_THEME_COLOR_EMPHASISHOVERBACKGROUND]  <br/> |
|EmphasisBorder  <br/> |使用强调背景的元素的边框颜色。  <br/> |[T_THEME_COLOR_EMPHASISBORDER]  <br/> |
|EmphasisHoverBorder  <br/> |鼠标悬停时使用强调背景的元素的边框颜色。  <br/> |[T_THEME_COLOR_EMPHASISHOVERBORDER]  <br/> |
|SubtleEmphasisText  <br/> |显示在轻微强调背景顶层的文本。  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISTEXT]  <br/> |
|SubtleEmphasisCommandLinks  <br/> |显示在轻微强调背景顶层的链接的命令链接颜色。  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISCOMMANDLINKS]  <br/> |
|SubtleEmphasisBackground  <br/> |直接显示在轻微强调文本后的背景。  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISBACKGROUND]  <br/> |
|TopBarText  <br/> |欢迎菜单、快速访问工具栏图标和关闭的功能区选项卡的文本和字形颜色。  <br/> |[T_THEME_COLOR_TOPBARTEXT]  <br/> |
|TopBarBackground  <br/> |显示在套件导航下方和右侧的上栏的背景颜色。  <br/> |[T_THEME_COLOR_TOPBARBACKGROUND]  <br/> |
|TopBarHoverText  <br/> |鼠标悬停时欢迎菜单、快速访问工具栏图标和关闭的功能区选项卡的文本和字形颜色。  <br/> |[T_THEME_COLOR_TOPBARHOVERTEXT]  <br/> |
|TopBarPressedText  <br/> |按下时欢迎菜单、快速访问工具栏图标和关闭的功能区选项卡的文本和字形颜色。  <br/> |[T_THEME_COLOR_TOPBARPRESSEDTEXT]  <br/> |
|HeaderText  <br/> |页眉区域中任何内容的基准文字颜色。  <br/> |[T_THEME_COLOR_HEADERTEXT]  <br/> |
|HeaderSubtleText  <br/> |页眉区域中搜索框的帮助器文本。  <br/> |[T_THEME_COLOR_HEADERSUBTLETEXT]  <br/> |
|HeaderDisableText  <br/> |搜索框的文本（如果搜索框位于页眉区域时被禁用）。  <br/> |[T_THEME_COLOR_HEADERDISABLETEXT]  <br/> |
|HeaderNavigationText  <br/> |页眉区域导航链接的基准文字颜色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONTEXT]  <br/> |
|HeaderNavigationHoverText  <br/> |将鼠标悬停在页眉区域导航链接上时的链接文本颜色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONHOVERTEXT]  <br/> |
|HeaderNavigationPressedText  <br/> |按下页眉区域导航链接时的链接文本颜色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONPRESSEDTEXT]  <br/> |
|HeaderNavigationSelectedText  <br/> |选择页眉区域导航链接时的链接文本颜色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONSELECTEDTEXT]  <br/> |
|HeaderLines  <br/> |当搜索框位于页眉区域时的搜索框线条。  <br/> |[T_THEME_COLOR_HEADERLINES]  <br/> |
|HeaderStrongLines  <br/> |将鼠标悬停在页眉区域的搜索框时的搜索框线条。  <br/> |[T_THEME_COLOR_HEADERSTRONGLINES]  <br/> |
|HeaderAccentLines  <br/> |聚焦页眉区域的搜索框时的搜索框线条。  <br/> |[T_THEME_COLOR_HEADERACCENTLINES]  <br/> |
|HeaderSublteLines  <br/> |页眉区域内看到的细线。不用于默认 CSS。  <br/> |[T_THEME_COLOR_HEADERSUBTLELINES]  <br/> |
|HeaderDisabledLines  <br/> |当搜索框位于页眉区域且被禁用时的搜索框线条。  <br/> |[T_THEME_COLOR_HEADERDISABLEDLINES]  <br/> |
|HeaderDisabledBackground  <br/> |当搜索框位于页眉区域且被禁用时的搜索框背景。  <br/> |[T_THEME_COLOR_HEADERDISABLEDBACKGROUND]  <br/> |
|HeaderFlyoutBorder  <br/> |源自页眉区域的下拉菜单的边框。  <br/> |[T_THEME_COLOR_HEADERFLYOUTBORDER]  <br/> |
|HeaderSiteTitle  <br/> |网站标题位于页眉区域时的文本颜色。  <br/> |[T_THEME_COLOR_HEADERSITETITLE]  <br/> |
|SuiteBarBackground  <br/> |套件导航的背景颜色。  <br/> |[T_THEME_COLOR_SUITEBARBACKGROUND]  <br/> |
|SuiteBarHoverBackground  <br/> |鼠标悬停时套件导航的背景颜色。  <br/> |[T_THEME_COLOR_SUITEBARHOVERBACKGROUND]  <br/> |
|SuiteBarText  <br/> |套件导航项的文本和字形颜色。  <br/> |[T_THEME_COLOR_SUITEBARTEXT]  <br/> |
|SuiteBarDisabledText  <br/> |已禁用套件项的文本和字形颜色。不用于默认 CSS。  <br/> |[T_THEME_COLOR_SUITEBARDISABLEDTEXT]  <br/> |
|ButtonText  <br/> |按钮的文本颜色。  <br/> |[T_THEME_COLOR_BUTTONTEXT]  <br/> |
|ButtonDisabledText  <br/> |已禁用按钮的颜色。  <br/> |[T_THEME_COLOR_BUTTONDISABLEDTEXT]  <br/> |
|ButtonBackground  <br/> |按钮的背景颜色。  <br/> |[T_THEME_COLOR_BUTTONBACKGROUND]  <br/> |
|ButtonHoverBackground  <br/> |鼠标悬停时按钮的背景颜色。  <br/> |[T_THEME_COLOR_BUTTONHOVERBACKGROUND]  <br/> |
|ButtonPressedBackground  <br/> |按下时按钮的背景颜色。  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBACKGROUND]  <br/> |
|ButtonDisabledBackground  <br/> |已禁用按钮的背景颜色。  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBACKGROUND]  <br/> |
|ButtonBorder  <br/> |按钮的边框颜色。  <br/> |[T_THEME_COLOR_BUTTONBORDER]  <br/> |
|ButtonHoverBorder  <br/> |鼠标悬停时按钮的边框颜色。  <br/> |[T_THEME_COLOR_BUTTONHOVERBORDER]  <br/> |
|ButtonPressedBorder  <br/> |按下时按钮的边框颜色。  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBORDER]  <br/> |
|ButtonDisabledBorder  <br/> |已禁用按钮的边框颜色。  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBORDER]  <br/> |
|ButtonGlyph  <br/> |按钮中显示的字形的字形颜色。  <br/> |[T_THEME_COLOR_BUTTONGLYPH]  <br/> |
|ButtonGlyphActive  <br/> |鼠标悬停时按钮中显示的字形的字形颜色。  <br/> |[T_THEME_COLOR_BUTTONGLYPHACTIVE]  <br/> |
|ButtonGlyphDisabled  <br/> |已禁用按钮的字形颜色。  <br/> |[T_THEME_COLOR_BUTTONGLYPHDISABLED]  <br/> |
|TileText  <br/> |显示在图块背景叠加顶层的文本。  <br/> |[T_THEME_COLOR_TILETEXT]  <br/> |
|TileBackgroundOverlay  <br/> |图块背景叠加的颜色。  <br/> |[T_THEME_COLOR_TILEBACKGROUNDOVERLAY]  <br/> |
|ContentAccent1  <br/> |用户可以从 RTF 编辑器颜色选取器中选择的第一个强调文字颜色。  <br/> |[T_THEME_COLOR_CONTENTACCENT1]  <br/> |
|ContentAccent2  <br/> |用户可以从 RTF 编辑器颜色选取器中选择的第二个强调文字颜色。  <br/> |[T_THEME_COLOR_CONTENTACCENT2]  <br/> |
|ContentAccent3  <br/> |用户可以从 RTF 编辑器颜色选取器中选择的第三个强调文字颜色。  <br/> |[T_THEME_COLOR_CONTENTACCENT3]  <br/> |
|ContentAccent4  <br/> |用户可以从 RTF 编辑器颜色选取器中选择的第四个强调文字颜色。  <br/> |[T_THEME_COLOR_CONTENTACCENT4]  <br/> |
|ContentAccent5  <br/> |用户可以从 RTF 编辑器颜色选取器中选择的第五个强调文字颜色。  <br/> |[T_THEME_COLOR_CONTENTACCENT5]  <br/> |
|ContentAccent6  <br/> |用户可以从 RTF 编辑器颜色选取器中选择的第六个强调文字颜色。  <br/> |[T_THEME_COLOR_CONTENTACCENT6]  <br/> |
   

## 字体方案
<a name="font"> </a>

字体在给定 SharePoint 网站的字体方案（.spfont 文件）和母版页预览（.preview 文件）中定义。字体方案定义四个区域内使用的字体：片头、导航、标题和正文。SharePoint 2013 中包含七种字体方案。您可以创建其他字体方案。字体方案文件位于网站集根网站主题库的 **15** 子文件夹 (http:// _SiteCollectionName_/_catalogs/theme/15/) 中。若要从 SharePoint 用户界面访问主题库，在"网站设置"页面的"Web 设计器库"下选择"主题"，然后选择"15"。
  
    
    
以下示例介绍了 .spfont 文件的格式。
  
    
    



```XML

<?xml version="1.0" encoding="utf-8"?>
<s:fontScheme name="FontSchemeName" previewSlot1="Slot1" previewSlot2="Slot2" xmlns:s="http://schemas.microsoft.com/sharepoint/">
  <s:fontSlots>
    <s:fontSlot name="FontSlotName">
      <s:latin typeface="LatinScriptFont" />
      <s:ea typeface="EAScriptFont"/>
      <s:cs typeface="CSFont" />
      <s:font script="Language" typeface="ScriptFont" />
      <!--Additional fonts-->
  </s:fontSlots>
  <!--Additional font slots-->
</s:fontScheme>
```

在 .spfont 文件中，以下占位符会被替换：
  
    
    

-  _FontSchemeName_ 是字体方案的名称。
    
  
-  _Slot1_ 是您要用作字体图标中第一个字体块的字体插槽名称，该图标位于"更改外观"向导的字体方案选取器中。
    
  
-  _Slot2_ 是您要用作字体图标中第二个字体块的字体插槽名称，该图标位于"更改外观"向导的字体方案选取器中。
    
  
-  _FontSlotName_ 是您所定义的字体插槽的名称（例如，title）。
    
  
-  _LatinScriptFont_ 是用于拉丁语脚本的字体。该字体也是回退字体。也就是说，该字体用于在字体方案中不具有明确设置的脚本的语言。
    
    > **注释**
      > 您必须提供其他信息才能在字体方案中使用 Web 字体。有关详细信息，请参阅本文中的  [Web 字体](#webFont)一节。 
-  _EAScriptFont_ 是用于东亚地区脚本的字体。SharePoint 目前不使用 **<s:ea>** 元素。但是，字体方案中仍然需要 **<s:ea>** 元素。
    
  
-  _CSFont_ 是用于复杂脚本的字体。SharePoint 目前不使用 **<s:cs>** 元素。但是，字体方案中仍然需要 **<s:cs>** 元素。
    
  
-  _Language_ 是语言脚本。
    
  
-  _ScriptFont_ 是用于指定语言脚本的字体。
    
  
以下示例显示了 .spfont 文件的一部分。
  
    
    



```XML

<s:fontScheme name="Georgia" previewSlot1="title" previewSlot2="body" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:fontSlots>
        <s:fontSlot name="title">
            <s:latin typeface="Georgia"/>
            <s:ea typeface=""/>
            <s:cs typeface="Segoe UI Light" />
            <s:font script="Arab" typeface="Tahoma" />
            <s:font script="Deva" typeface="Mangal" />
            <s:font script="Grek" typeface="Segoe UI Light" />
            <s:font script="Hang" typeface="Malgun Gothic" />
            <s:font script="Hans" typeface="Microsoft YaHei" />
            <s:font script="Hant" typeface="Microsoft JhengHei" />
            <s:font script="Hebr" typeface="Tahoma" />
            <s:font script="Hira" typeface="Meiryo" />
            <s:font script="Thai" typeface="Tahoma" />
            <s:font script="Armn" typeface="Tahoma" />
            <s:font script="Beng" typeface="Vrinda" />
            <s:font script="Cher" typeface="Plantagenet Cherokee" />
            <s:font script="Ethi" typeface="Nyala" />
            <s:font script="Geor" typeface="Sylfaen" />
            <s:font script="Gujr" typeface="Shruti" />
            <s:font script="Guru" typeface="Raavi" />
            <s:font script="Knda" typeface="Tunga" />
            <s:font script="Khmr" typeface="DaunPenh" />
            <s:font script="Laoo" typeface="DokChampa" />
            <s:font script="Mlym" typeface="Kartika" />
            <s:font script="Mymr" typeface="Myanmar Text" />
            <s:font script="Orya" typeface="Kalinga" />
            <s:font script="Sinh" typeface="Iskoola Pota" />
            <s:font script="Syrc" typeface="Estrangelo Edessa" />
            <s:font script="Taml" typeface="Latha" />
            <s:font script="Telu" typeface="Gautami" />
            <s:font script="Thaa" typeface="MV Boli" />
            <s:font script="Tibt" typeface="Cordia New" />
            <s:font script="Yiii" typeface="Microsoft Yi Baiti" />
        </s:fontSlot>
…
```

SharePoint 2013 包含对 Web 字体的支持。您必须提供其他信息才能在字体方案中使用 Web 字体。有关详细信息，请参阅本文中的  [Web 字体](#webFont)一节。
  
    
    

### Web-safe 字体
<a name="websafeFont"> </a>

Web-safe 字体是一组广泛使用的字体，大部分设备都默认提供这一组字体。若要在字体方案中指定 web-safe 字体，请在字体插槽的 **typeface** 属性中添加字体名称。以下示例显示了字体方案中使用的 web-safe 字体。
  
    
    

```XML

<s:fontSlot name="title">
  <s:latin typeface="Georgia"/>
…
</s:fontSlot>
```


### Web 字体
<a name="webFont"> </a>

Web 字体是 Internet 中提供的字体。当用户查看使用 Web 字体的网站时，Web 浏览器会下载必需的字体文件以及页面的其余部分。若要指定 Web 字体，您必须以四种格式向 Web 字体文件提供 URL（为了跨浏览器提供支持），并且提供小型和大型缩略图图像，以用于在字体方案选取器中呈现字体名称。
  
    
    
以下示例说明了在 **<s:latin>** 元素中使用 Web 字体所需的信息。
  
    
    



```XML

<s:latin typeface="FontName"
  eotsrc="EotFile"
  woffsrc="WoffFile"
  ttfsrc="TtfFile"
  svgsrc="SvgFile"
  largeimgsrc="LargeImgFile"
  smallimgsrc="SmallImgFile" />

```

在这个使用 Web 字体的示例中，以下占位符会被替换：
  
    
    

-  _FontName_ 是 Web 字体的名称。
    
  
-  _EotFile_ 是"嵌入式开放类型"字体文件的相对 URL。
    
  
-  _WoffFile_ 是"Web 开放字体格式"字体文件的相对 URL。
    
  
-  _TtfFile_ 是 TrueType 字体文件的相对 URL。
    
  
-  _SvgFile_ 是"可缩放的向量图形"字体文件的相对 URL。
    
  
-  _LargeImgFile_ 是您想用于字体方案选取器的大型缩略图图像的相对 URL。
    
  
-  _SmallImgFile_ 是您想用于字体方案选取器的小型缩略图图像的相对 URL。
    
  

### 字体插槽
<a name="fontSlot"> </a>

表 1 介绍了可用的字体插槽，以及它们在页面中的使用位置。
  
    
    

**表 1. 字体插槽**


|**字体插槽名称**|**说明**|
|:-----|:-----|
|title  <br/> |用于页面片头。  <br/> |
|navigation  <br/> |用于页面水平导航元素和垂直导航元素。  <br/> |
|large-heading  <br/> |用于 H1 标题。  <br/> |
|heading  <br/> |用于 H2 和 H3 标题、Web 部件标题、对话框标题和标注标题。  <br/> |
|small-heading  <br/> |用于 H4 标题。  <br/> |
|large-body  <br/> |用于大型正文文本（15 像素和 19 像素）。  <br/> |
|body  <br/> |用于页面上其他任何位置的基字体。  <br/> |
   

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 主题概述](themes-overview-for-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中部署自定义主题](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [将自定义主题和 CSS 升级到 SharePoint 2013](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建母版页预览文件](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [SharePoint 团队博客：通过 SharePoint 主题设置秀出自己的风格](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 Design Manager 品牌和设计功能](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

  
    
    

