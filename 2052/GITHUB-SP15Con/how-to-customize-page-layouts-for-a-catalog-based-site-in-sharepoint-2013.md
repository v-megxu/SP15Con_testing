---
title: 如何：在 SharePoint 2013 中为基于目录的网站定制页面布局
ms.prod: SHAREPOINT
ms.assetid: 21d8db99-73b3-4429-b6cb-04e375af9f55
---


# 如何：在 SharePoint 2013 中为基于目录的网站定制页面布局
了解如何创建和自定义 SharePoint Server 2013 跨网站发布站点的类别页面和目录项页面布局。
## 为基于目录的网站创建和自定义页面布局的必备组件
<a name="bk_prereqs"> </a>

若要遵循此示例中的这些步骤，您必须具备以下组件：
  
    
    

- 一个 HTML 编辑器
    
  
- 一个 SharePoint Server 2013 跨网站发布环境
    
  
有关如何建立 SharePoint 跨网站发布环境的信息，请参阅 [在 SharePoint Server 2013 中配置跨网站发布](http://technet.microsoft.com/zh-cn/library/jj656774.aspx)。
  
    
    

### 为基于目录的网站创建和自定义页面布局需要了解的核心概念

表 1 列出了可以帮助您了解与为基于目录的网站创建和自定义页面布局相关的概念和步骤。
  
    
    

**表 1. 为基于目录的网站创建和自定义页面布局的核心概念**


|**文章标题**|**说明**|
|:-----|:-----|
| [SharePoint Server 2013 中的跨网站发布概述](http://technet.microsoft.com/zh-cn/library/jj635883.aspx) <br/> |了解如何使用跨网站发布和搜索 Web 部件来创建自适应 SharePoint Internet、Intranet 和 Extranet 网站。  <br/> |
| [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md) <br/> |了解如何在 SharePoint Server 2013 中创建页面布局。  <br/> |
| [如何：在 SharePoint 2013 中预览页面时解决错误和警告](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md) <br/> |了解如何解决有关防止服务器端预览呈现您的页面的问题。  <br/> |
| [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md) <br/> |了解如何使用代码段将 SharePoint 功能添加到您的 HTML 母版页或页面布局中。  <br/> |
   

## 类别页面布局和目录项页面布局简介
<a name="bk_introduction"> </a>

类别页面和目录项页面是可用于跨网站一致地显示结构化目录内容的页面布局。默认情况下，SharePoint Server 2013 可以对每个目录连接自动创建一个类别页面布局和一个目录项页面布局。当您将网站连接到目录时，基于这些布局的页面将被创建在发布网站的页面库中。有关页面布局的详细信息，请参阅 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)。有关特定于类别页面布局和目录项页面布局的功能的详细信息，请参阅  [SharePoint Server 2013 中的跨网站发布概述](http://technet.microsoft.com/zh-cn/library/jj635883.aspx)。
  
    
    
默认情况下，当您将发布网站连接到目录时，会自动创建类别页面布局和目录项页面布局。当您将发布网站连接到目录或当您在发布网站上配置导航术语集时，您还可以使用设计管理器选择创建类别页面布局和目录项页面布局。
  
    
    

## 创建一个类别页面布局
<a name="bk_createCategoryPage"> </a>

在您创建或自定义一个类别页面布局之前，我们建议您创建一个指向 **母版页样式库**的映射网络驱动器。有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
  
    
    
创建类别页面布局的最简单方法是让 SharePoint 在您将发布网站连接到目录时自动创建页面布局，然后再自定义现有的类别页面布局，以根据页面设计按照需要来更改标记。或者，您可以使用设计管理器从头开始创建一个新的类别页面布局。
  
    
    

### 自定义由 SharePoint 自动创建的现有类别页面布局


1. 使用 Windows 资源管理器，打开映射到母版页样式库的网络驱动器。
    
  
2. 若要自定义一个类别页面布局，请编辑直接位于服务器上的 HTML 文件，方法是使用 HTML 编辑器打开和编辑映射驱动器中的 HTML 文件。每次保存 HTML 文件时，所做更改都会同步到关联的 .aspx 文件。
    
  
3. 使用要在页面布局中使用的标记来替换 **id="PlaceHolderMain"** 的内容占位符内的标记。
    
    > **重要信息**
      > 您必须保留内容搜索代码段标记，以便类别页面显示搜索结果。 
4. 若要配置并复制要添加到页面的代码段 HTML，请按照  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)中"从代码段库插入代码段"部分的步骤 1 至步骤 11 进行操作。
    
  
5. 对标记进行其他所有必需的更改，然后保存文件。
    
  
6. 按照 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)中"创建页面布局"部分的步骤 9 至步骤 11 检查文件的状态、预览页面布局并修复所有错误。
    
  

### 使用设计管理器创建一个类别页面布局


1. 按照 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)中"创建页面布局"部分的步骤 1 至步骤 6 执行操作。
    
  
2. 在步骤 7中，选择"文章页面"内容类型。
    
  
3. 选择"确定"。
    
    此时，SharePoint 会创建一个 HTML 文件和一个同名的 .aspx 文件。
    
    在设计管理器中，现在将显示带有"状态"列的 HTML 文件，该列显示两个状态之一：
    
  - 错误
    
  
  - **转换成功**
    
  
4. 使用 Windows 资源管理器，打开映射到母版页样式库的网络驱动器。
    
  
5. 若要自定义一个类别页面布局，请编辑直接位于服务器上的 HTML 文件，方法是使用 HTML 编辑器打开和编辑映射驱动器中的 HTML 文件。每次保存 HTML 文件时，所做更改都会同步到关联的 .aspx 文件。
    
  
6. 在 **<head>** 标记中，使用以下内容来替换 **id="PlaceHolderPageTitle"** 的内容占位符：
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

7. 查找到 **id="PlaceHolderPageTitleInTitleArea"** 的内容占位符，并将其替换为以下内容：
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitleInTitleArea" runat="server">-->
<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

8. 使用要在页面布局中使用的标记来替换 **id="PlaceHolderMain"** 的内容占位符内的标记。
    
  
9. 若要配置并复制要添加到页面的内容搜索代码段和任何其他代码段的 HTML，请按照  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)中"从代码段库插入代码段"部分的步骤 1 至步骤 11 进行操作。
    
    > **注释**
      > 当您将内容搜索代码段添加到页面布局中时，请确保更改查询以使用将发布网站连接到目录时创建的结果源。有关详细信息，请参阅 [在 SharePoint Server 2013 中配置 Web 内容管理的结果源](http://technet.microsoft.com/zh-cn/library/jj715262.aspx)。 
10. 对标记进行其他所有必需的更改，然后保存文件。
    
  
11. 按照 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)中"创建页面布局"部分的步骤 9 至步骤 11 检查文件的状态、预览页面布局并修复所有错误。
    
  

## 了解 HTML 类别页面布局中的标记
<a name="bk_CategoryPageMarkup"> </a>

创建页面布局时，会创建一个 SharePoint 使用的 .aspx 文件，并且会向该页面布局的 HTML 版本添加一些 HTML 标记。类别页面布局有一些标记组件，这些组件将根据跨网站集发布功能添加到页面布局中，并且它们对于类别页面布局而言是唯一的。在 HTML 编辑器中编辑 HTML 类别页面布局时，了解此标记的某些方面可能很有用。
  
    
    

### 浏览窗口页面标题

 **id="PlaceHolderPageTitle"** 的内容占位符内出现的组件中包含可让 SharePoint 使用术语属性作为浏览器窗口页面标题的标记，而不是使用标准页字段值。以下代码显示用于浏览器窗口页面标题的标记。
  
    
    

```HTML

<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
```


### 页面标题

 **id="PlaceHolderPageTitleInTitleArea"** 的内容占位符内出现的组件中包含可让 SharePoint 使用术语属性作为页面上页面标题的标记，而不是使用"SPTitleBreadcrumb"代码段和标准页标题字段值。以下代码显示用于页面标题的标记。
  
    
    

```HTML

<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->"
```


### 内容搜索代码段

出现在页面内容代码段之后、 **id="PlaceHolderMain"** 的内容占位符内的组件中包含用于 Web 部件区域代码段（包含四个 Web 部件区域）的标记。第一个 Web 部件区域包含一个内容搜索代码段，它在页面上显示内容搜索 Web 部件。这个代码段还包含帮助内容搜索 Web 部件查询结果源并在页面上显示结果的信息。后三个 Web 部件区域为空。如果您选择创建自己的类别页面布局，就必须将内容搜索代码段的标记包括在用于页面布局的 HTML 文件中。以下代码显示用于内容搜索代码段的标记。请使用结果源的 GUID 替换 _ResultSourceID_，并使用目录的 URL 替换  _CatalogURL_。
  
    
    

> **注释**
> 代码段添加到页面布局时， **ID** 和 **__WebPartId** 的 GUID 将由 SharePoint 随机生成。
  
    
    


```HTML
<!--
CS: Start Content Search Snippet-->
<!--SPM:<%@Register Tagprefix="a781102493" Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<a781102493:ContentBySearchWebPart runat="server" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;&amp;#34;,&amp;#34;SourceID&amp;#34;
:&amp;#34;ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;
{'Tag':'{Term.IDWithChildren}','Scope':'CatalogURL'}&amp;#34;}" ResultsPerPage="3" RenderTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Control_ListWithPaging.js" 
ItemTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Item_PictureOnTop.js" SelectedPropertiesJson="[&amp;#34;WorkId&amp;#34;,&amp;#34;Rank&amp;#34;,&amp;#34;Title&amp;#34;,&amp;#34;Author&amp;#34;,&amp;#34;
Size&amp;#34;,&amp;#34;Path&amp;#34;,&amp;#34;Description&amp;#34;,&amp;#34;Write&amp;#34;,&amp;#34;CollapsingStatus&amp;#34;,&amp;#34;
HitHighlightedSummary&amp;#34;,&amp;#34;HitHighlightedProperties&amp;#34;,&amp;#34;ContentClass&amp;#34;,&amp;#34;
PictureThumbnailURL&amp;#34;,&amp;#34;ServerRedirectedURL&amp;#34;,&amp;#34;ServerRedirectedEmbedURL&amp;#34;,&amp;#34;
ServerRedirectedPreviewURL&amp;#34;,&amp;#34;FileExtension&amp;#34;,&amp;#34;ContentTypeId&amp;#34;,&amp;#34;ParentLink&amp;#34;,&amp;#34;
ViewsLifeTime&amp;#34;,&amp;#34;ViewsRecent&amp;#34;,&amp;#34;SectionNames&amp;#34;,&amp;#34;SectionIndexes&amp;#34;,&amp;#34;
SiteLogo&amp;#34;,&amp;#34;SiteDescription&amp;#34;,&amp;#34;deeplinks&amp;#34;,&amp;#34;importance&amp;#34;]" ShouldHideControlWhenEmpty="True" FrameType="None" SuppressWebPartChrome="False" Description="$Resources:Microsoft.Office.Server.Search,CBS_Description;" IsIncluded="True" 
ZoneID="" PartOrder="0" FrameState="Normal" AllowRemove="True" AllowZoneChange="True" 
AllowMinimize="True" AllowConnect="True" AllowEdit="True" AllowHide="True" IsVisible="True" 
DetailLink="" HelpLink="" HelpMode="Modeless" Dir="Default" PartImageSmall="" IsIncludedFilter="" ExportControlledProperties="True" ConnectionID="00000000-0000-0000-0000-000000000000" ID="g_54e35103_6f29_4dd9_b93b_8d4c863834af" ChromeType="None" ExportMode="All" __MarkupType="vsattributemarkup" __WebPartId="54e35103-6f29-4dd9-b93b-8d4c863834af" 
WebPart="true" Height="" Width="" Title="$Resources:cms,WebPartZoneTitle_Dynamic;">-->
<!--ME:</a781102493:ContentBySearchWebPart>-->
<!--CE: End Content Search Snippet-->

```


## 创建一个目录项页面布局
<a name="bk_createCatItemPage"> </a>

在您创建或自定义一个目录项页面布局之前，我们建议您创建一个指向母版页样式库的映射网络驱动器。有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
  
    
    
与类别页面布局相同，创建目录项页面布局的最简单方法是让 SharePoint 在您将发布网站连接到目录时自动创建页面布局，然后再自定义现有的目录项页面布局，以根据页面设计按照需要添加其他标记。或者，您可以使用设计管理器从头开始创建一个目录项页面布局。
  
    
    

### 自定义由 SharePoint 自动创建的现有目录项页面布局


1. 使用 Windows 资源管理器，打开映射到母版页样式库的网络驱动器。
    
  
2. 若要自定义一个目录项页面布局，请编辑直接位于服务器上的 HTML 文件，方法是使用 HTML 编辑器打开和编辑映射驱动器中的 HTML 文件。每次保存 HTML 文件时，所做更改都会同步到关联的 .aspx 文件。
    
  
3. 在 **id="PlaceHolderMain"** 的内容占位符内，添加要在页面布局中使用的标记。
    
  
4. 删除所有不希望在页面布局中使用的代码段，并将剩余的代码段移动到希望属性值在标记中出现的位置。
    
    > **警告**
      > 默认情况下，包含目录项重复使用代码段的 Web 部件区域代码段将添加到页面布局中。此代码段包含用于返回页面上其他所有代码段使用的查询结果的数据提供程序。我们建议您将目录项重复使用代码段保留在此默认 Web 部件区域代码段中。（您可以将目录项重复使用代码段移到 Web 部件区域之外，还可以更改其显示的属性。但是，您必须将目录项重复使用代码段保留在页面布局中。）有关详细信息，请参阅本文后面的 [页面字段](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields)。 
5. 要配置并复制要在页面中使用的任意代码段的 HTML 代码段，请按照 [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)中"从代码段库插入代码段"的步骤 1 至步骤 11 执行操作。
    
  
6. 对标记进行其他所有必需的更改，然后保存文件。
    
  
7. 按照 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)中"创建页面布局"部分的步骤 9 至步骤 11 检查文件的状态、预览页面布局并修复所有错误。
    
  

### 使用设计管理器创建一个目录项页面布局


1. 按照 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)中"创建页面布局"部分的步骤 1 至步骤 6 执行操作。
    
  
2. 在步骤 7 中，选择"远程目录"，然后选择包含要出现在页面上的数据的目录。
    
  
3. 选择"确定"。
    
    此时，SharePoint 会创建一个 HTML 文件和一个同名的 .aspx 文件。
    
    在设计管理器中，现在将显示带有"状态"列的 HTML 文件，该列显示两个状态之一：
    
  - 错误
    
  
  - **转换成功**
    
  
4. 使用 Windows 资源管理器，打开映射到母版页样式库的网络驱动器。
    
  
5. 若要自定义一个目录项页面布局，请编辑直接位于服务器上的 HTML 文件，方法是使用 HTML 编辑器打开和编辑映射驱动器中的 HTML 文件。每次保存 HTML 文件时，所做更改都会同步到关联的 .aspx 文件。
    
  
6. 在 **id="PlaceHolderMain"** 的内容占位符内，添加要在页面布局中使用的标记。
    
  
7. 删除所有不希望在页面布局中使用的代码段，并将剩余的代码段移动到希望属性值在标记中出现的位置。
    
    > **警告**
      > 默认情况下，包含目录项重复使用代码段的 Web 部件区域代码段将添加到页面布局中。此代码段包含用于返回页面上其他所有代码段使用的查询结果的数据提供程序。我们建议您将目录项重复使用代码段保留在此默认 Web 部件区域代码段中。（您可以将目录项重复使用代码段移到 Web 部件区域之外，还可以更改其显示的属性。但是，您必须将目录项重复使用代码段保留在页面布局中。）有关详细信息，请参阅本文后面的 [页面字段](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields)。 
8. 要配置并复制要在页面中使用的任意代码段的 HTML 代码段，请按照 [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)中"从代码段库插入代码段"的步骤 1 至步骤 11 执行操作。
    
  
9. 对标记进行其他所有必需的更改，然后保存文件。
    
  
10. 按照 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)中"创建页面布局"部分的步骤 9 至步骤 11 检查文件的状态、预览页面布局并修复所有错误。
    
  

## 了解 HTML 目录项页面布局中的标记
<a name="bk_CatItemMarkup"> </a>

创建页面布局时，会创建一个 SharePoint 使用的 .aspx 文件，并且会向该页面布局的 HTML 版本添加一些 HTML 标记。目录项页面布局有一些标记组件，这些组件将根据跨网站集发布功能添加到页面布局中，并且它们对于目录项页面布局而言是唯一的。在 HTML 编辑器中编辑 HTML 目录项页面布局时，了解此标记的某些方面可能很有用。
  
    
    

### 浏览窗口页面标题

 **id="PlaceHolderPageTitle"** 的内容占位符内出现的组件包含一个目录项重用代码段，可让 SharePoint 使用目录项名称作为浏览器窗口的页面标题，而不是使用标准页标题字段值。以下代码显示用于浏览器窗口页面标题的标记。
  
    
    

> **注释**
> 代码段添加到页面布局时， **ID** 和 **__WebPartId** 的 GUID 将由 SharePoint 随机生成。
  
    
    


```HTML

<!--CS: [Title] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_863912c1_c849_46dc_8781_2920ee2bc83f" __WebPartId="{863912c1-c849-46dc-8781-2920ee2bc83f}">-->
<!--SPM:<RenderFormat>-->
<!--DC:Renders value from search without any additional formatting.-->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->

```


### 页面字段
<a name="bk_pagefields"> </a>

 **id="PlaceHolderMain"** 的内容占位符内出现的组件包含用于 **Title**、 **Page Content** 和 **Catalog-Item URL** 字段的代码段。您可以将任意代码段从页面布局中删除。以下代码显示用于这些页面字段的标记。
  
    
    

```HTML

<div>
    <!--CS: Start Page Field: Title Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldTextField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
        <!--MS:<PageFieldTextField:TextField FieldName="fa564e0f-0c70-4ab9-b863-0177e6ddd247" 
runat="server">-->
        <!--ME:</PageFieldTextField:TextField>-->
    <!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Page Field: Title Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Page Content Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldRichHtmlField:RichHtmlField FieldName="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" runat="server">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
            <div id="ctl02_label" style="display:none">Page Content</div>
            <div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label">
                <div align="left" class="ms-formfieldcontainer">
                    <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                        <span class="ms-formfieldlabel" nowrap="nowrap">Page Content</span>
                    </div>
                    <div class="ms-formfieldvaluecontainer">
                        <div class="ms-rtestate-field">Page Content field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
                    </div>
                </div>
            </div>
        <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
    <!--CE: End Page Field: Page Content Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Catalog-Item URL Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldCatalogSourceFieldControl" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl FieldName="75772bbf-0c25-4710-b52c-7b78344ad136" runat="server">-->
    <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
        <div align="left" class="ms-formfieldcontainer">
            <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                <span class="ms-formfieldlabel" nowrap="nowrap">Catalog-Item URL</span>
            </div>
            <div class="ms-formfieldvaluecontainer">
                <a href="http://www.example.com">Link to sample web site.</a>
            </div>
        </div>
    <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl>-->
    <!--CE: End Page Field: Catalog-Item URL Snippet-->
</div>

```

如果目录项页面布局在将发布网站连接到目录时自动创建，或是在页面布局创建期间通过选择远程目录创建，该页面布局也会包含一个 Web 部件区域代码段，其中含有注册了页面数据提供程序的目录项重用代码段。目录项重用代码段包含一个设置为 **False** 的 **UseSharedDataProvider** 属性。Web 部件区域代码段可从页面布局中删除。但是，必须将目录项重用代码段保存在页面布局标记中，以便页面显示目录项。创建使用此页面布局的页面后，就可以配置 Web 部件，以便用户查看页面时隐藏该 Web 部件。
  
    
    

> **重要信息**
> 如果您创建了一个新的目录项页面布局，并选择内容类型，而不是远程目录，就必须在页面布局中包含目录项重用代码段。同显示在 Web 部件区域代码段中一样，以下代码显示用于目录项重用代码段的标记。使用要显示的托管属性名称替换  _ManagedPropertyName_，使用结果源的 GUID 替换  _ResultSourceID_，使用目录的 URL 替换  _CatalogURL_。 
  
    
    




```HTML

<div>
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="cc1"  Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
    <!--MS:<WebPartPages:WebPartZone runat="server" Title="&amp;#60;%$Resources:cms,WebPartZoneTitle_Body%&amp;#62;" AllowPersonalization="False" FrameType="TitleBarOnly" ID="Body" Orientation="Vertical">-->
        <!--MS:<ZoneTemplate>-->
            <!--CS: [ManagedPropertyName] Start Catalog-Item Reuse Snippet-->
            <!--DC:To render the search property using a rendering template, change the "UseServerSideRenderFormat" property to "False".-->
            <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" AddSEOPropertiesFromSearch="True" LogAnalyticsViewEvent="True" UseSharedDataProvider="False" OverwriteResultPath="False" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;ListItemID:{URLTOKEN.1}&amp;#34;,&amp;#34;SourceID&amp;#34;:&amp;#34; ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;{&amp;#39;Scope&amp;#39;:&amp;#39;  CatalogURL&amp;#39;,&amp;#39;Tag&amp;#39;:&amp;#39;{Term}&amp;#39;}&amp;#34;}" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;ManagedPropertyName&amp;#34;]" Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" MissingAssembly="Cannot import this Web Part." ID="g_d63eebe7_207f_4e8c_9566_7381acc80cc7" __WebPartId="{d63eebe7-207f-4e8c-9566-7381acc80cc7}">-->
            <!--SPM:<RenderFormat>-->
            <!--DC:Renders value from search without any additional formatting.-->
            <!--SPM:</RenderFormat>-->
            <!--SPM:</cc1:CatalogItemReuseWebPart>-->
        <!--ME:</ZoneTemplate>-->
    <!--ME:</WebPartPages:WebPartZone>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

如果目录项页面布局在将发布网站连接到目录时创建，或者在页面布局创建期间通过选择远程目录创建，该页面的其余部分会包含目录项重用代码段，此代码段对应于创作网站上目录中的托管属性。这些托管属性显示通过使用目录项页面布局所显示的特定目录项的详细信息。这些目录项重用代码段显示在 Web 部件区域以外，并且将在类型页面上选定项目时直接呈现。表 2 列出了自动包含在目录项页面布局中的托管属性。
  
    
    

> **注释**
> 有些托管属性仅当目录为页面库时才包含在内。表 2 中的 **使用方**列表示哪些属性可被页面库和列表使用，以及哪些属性只能被页面库使用。 
  
    
    


**表 2. 默认的托管属性目录项重用代码段**


|**托管属性**|**说明**|**使用方**|
|:-----|:-----|:-----|
|**AuthorOWSUSER** <br/> |创建了页面的用户的用户名。  <br/> |仅页面库  <br/> |
|**CreatedOWSDATE** <br/> |创建页面或列表项的日期。  <br/> |页面库和列表  <br/> |
|**EditorOWSUSER** <br/> |最后更改页面或列表项的用户的用户名。  <br/> |页面库和列表  <br/> |
|**ListItemID** <br/> |页面或列表项的 ID。  <br/> |页面库和列表  <br/> |
|**ModifiedOWSDATE** <br/> |最后更改页面或列表项的日期。  <br/> |页面库和列表  <br/> |
|**PublishingContactOWSUSER** <br/> |联系人是由发布功能创建的一个网站栏。它在页面内容类型中用作该页面联系人的个人或团体。  <br/> |仅页面库  <br/> |
|**PublishingIsFurlPageOWSBOOL** <br/> |一个布尔值，它表示页面是否与一个友好的 URL 相关联。  <br/> |仅页面库  <br/> |
|**PublishingPageContentOWSHTML** <br/> |该页面的 HTML 内容。  <br/> |仅页面库  <br/> |
|**PublishingPageLayoutOWSURLH** <br/> |到用来创建页面的页面布局的 URL。  <br/> |仅页面库  <br/> |
|**Title** <br/> |页面或列表项的标题。  <br/> |页面库和列表  <br/> |
   
您添加到页面库或列表的自定义列的托管属性也包含在目录项重用代码段中。托管属性名称会各有不同，取决于您创建网站栏时使用的网站栏类型。有关详细信息，请参阅  [SharePoint Server 2013 中自动创建的托管属性](http://technet.microsoft.com/zh-cn/library/jj613136.aspx) 和 [SharePoint Server 2013 中的搜索架构概述](http://technet.microsoft.com/zh-cn/library/jj219669.aspx)。
  
    
    

> **重要信息**
> 页面库中的 **Page Image** 网站栏会映射到 **PublishingImage** 托管属性。但是， **PublishingImage** 托管属性不会自动包含在目录项页面布局中。若要将图像包含到页面布局中，就必须为 **PublishingImage** 托管属性添加一个目录项重用代码段。使用以下 HTML 添加目录项重用代码段，以在您的页面布局中显示 **PublishingImage** 托管属性的值。使用对每个代码段实例唯一的 GUID 来替换 _UniqueID_。 
  
    
    




```HTML

<div>
<!--CS: [PublishingImage] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingImage&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_UniqueID" __WebPartId="{UniqueID}">-->
<!--SPM:<RenderFormat>-->
<!--SPM:<Format Type="HTML"> -->
<!--SPM:<Picture>-->True<!--SPM:</Picture>-->
<!--SPM:</Format> -->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

如果您使用设计管理器创建一个新的目录项页面布局，并选择内容类型，而不是远程目录，您就可以通过使用代码段库将目录项重用代码段添加到页面中。以下代码显示用于 **Title**、 **PublishingPageContentOWSHTML**、 **CreatedOWSDATE** 和 **owstaxIdPageCategory** 托管属性目录项重用代码段的标记。
  
    
    

> **注释**
> 代码段添加到页面布局时， **ID** 和 **__WebPartId** 的 GUID 将由 SharePoint 随机生成。
  
    
    




```HTML

<div>
    <!--CS: [Title] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_0dc23bb8_8d34_4f9f_8085_5a6ac286cb9e" 
__WebPartId="{0dc23bb8-8d34-4f9f-8085-5a6ac286cb9e}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [PublishingPageContentOWSHTML] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingPageContentOWSHTML&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_25253a49_a9a6_4277_bf9d_416961024cee" 
__WebPartId="{25253a49-a9a6-4277-bf9d-416961024cee}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [CreatedOWSDATE] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;CreatedOWSDATE&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." 
ID="g_4e1f180b_12f8_4e50_84d7_c72b0ee3793f" 
__WebPartId="{4e1f180b-12f8-4e50-84d7-c72b0ee3793f}">-->
    <!--SPM:<RenderFormat>-->
    <!--SPM:<Format Type="DateTime"> -->
    <!--DC:To render Date and Time, change this value to False.-->
    <!--SPM:<DateOnly>-->True<!--SPM:</DateOnly>-->
    <!--SPM:</Format> -->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [owstaxIdPageCategory] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;owstaxIdPageCategory&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_22e39e9d_1b25_42c7_bf2a_7ebca37616d4" 
__WebPartId="{22e39e9d-1b25-42c7-bf2a-7ebca37616d4}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```


## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的设计管理器概述](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 页面模型概述](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Design Manager 显示模板](sharepoint-2013-design-manager-display-templates.md)
    
  

