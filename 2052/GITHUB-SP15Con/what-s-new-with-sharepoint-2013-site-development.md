---
title: SharePoint 2013 网站开发的新增内容
ms.prod: SHAREPOINT
ms.assetid: ac1e9891-5ce9-4707-84e5-6e2fc02fda6b
---


# SharePoint 2013 网站开发的新增内容
了解 SharePoint 2013 中的可让您创建发布网站的新网站创作和发布模型。
## SharePoint 2013 中的网站发布简介（针对设计人员和开发人员）
<a name="SP15_WhatsNewSiteDevelopment_IntroductionToSitePublishing"> </a>

以下功能为 SharePoint 2013 中的新增功能，并支持针对发布网站的企业内容管理 (ECM) 网站创建工作流。
  
    
    

### 针对发布网站开发的客户端编程模型

在 SharePoint 2013 中，您可以使用 .NET 客户端对象模型 (CSOM)、Silverlight 和 JavaScript 编程模型开发自定义网站、网站组件、品牌元素和行为。相应 .NET 客户端 (CSOM)、Silverlight 和 JavaScript 程序集提供用于 .NET 服务器编程的大多数 API。某些情况下，Windows Phone 库中还提供相应 API。
  
    
    
若要了解详细信息，请参阅网站的参考主页和  [.NET server](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)、 [.NET client](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx) 和 [JavaScript](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx) 的内容。或者如果您想要在顶部启动，然后浏览每个编程模型的内容，请从 [参考主页](http://msdn.microsoft.com/library/7940ba4e-f6f0-4bc0-b995-ceb2d358ca0d%28Office.15%29.aspx)开始。
  
    
    

### 使用新的 SharePoint 应用程序模型的发布和分类 API

您可以在 SharePoint 外接程序中编写自定义客户端和服务器代码，以便通过用户界面 (UI) 扩展可供用户使用的 SharePoint 发布和分类功能。 
  
    
    
开发将增强网站发布的应用程序的一些理念包括调查、帐户管理应用程序、电子商务支持、将社交功能和外部数据集成到发布网站的应用程序、将外包内容添加到您的网站的应用程序以及移动伴侣应用程序。
  
    
    

## 创作、设计和品牌功能
<a name="SP15_WhatsNewSiteDevelopment_AuthoringAndBranding"> </a>

SharePoint 2013 包括您可用于创作、设计、品牌化和扩展您的网站、网站设计和品牌元素及行为的功能和 API。 
  
    
    

### 设计管理器

在以前的 SharePoint 版本中，品牌化网站需要关于母版页中需要什么内容占位符或母版页如何实现某类样式方面的具体技术知识。SharePoint 2013 引入了 [设计管理器](overview-of-design-manager-in-sharepoint-2013.md)，它是管理品牌化您的 SharePoint 网站各个方面的一个全新界面和中心枢纽。您可以在您的网站集的顶级网站中找到设计管理器。它是 SharePoint 2013 中发布门户网站集模板的一部分。
  
    
    
设计管理器可让您以分步方式创建您可用于品牌化网站的设计资产。上载设计资产（图像、HTML、CSS 等等），然后创建母版页和页布局。设计时，您可以在客户端侧代码编辑器中或服务器上预览您设计的外观。您可以通过使用设计管理器 UI 添加自定义 SharePoint 组件和带状元素。设计管理器生成任何 Web 设计工具都可使用的 HTML  [代码段](sharepoint-2013-design-manager-snippets.md)，它呈现 HTML 并忽略 ASP.NET 和 SharePoint 标记，而 SharePoint 仅呈现 ASP.NET 和 SharePoint 标记，忽略 HTML。
  
    
    
您可以使用您在 HTML、CSS 和 JavaScript 方面的知识设计 HTML 格式的母版页，并在您选择的 HTML 编辑器中设计 HTML 页面布局。若要将您最喜爱的创作和设计工具添加到 SharePoint 网站， [映射一个网络驱动器](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)，然后像编辑本地文件一样编辑 SharePoint file 文件。准备好网站设计后，上载 HTML 和支持文件，然后使用设计管理器 [将 HTML 文件转换成 ASP.NET 母版页 (.master) 文件](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)。现在， [将母版页应用](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)到 SharePoint 网站。使用设计管理器  [创建新的页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)，其 HTML 版本将自动与 SharePoint 解读的相应 ASP.NET 页（aspx 文件）关联。 
  
    
    
转换 HTML 文件后，您可以使用 HTML 编辑器继续改善您的设计，预览文件并保存。每次您保存 HTML 版本的母版页或页面布局文件，SharePoint 2013 都会自动更新相关 SharePoint 母版页和页面布局以反映您的更改。 
  
    
    
有了设计管理器，您只需要编辑 HTML 文件 - 您可以使用 ASP.NET 和 SharePoint 开发技能继续编写自定义母版页和页面布局时，设计管理器可让您在不具备 SharePoint 开发人员专业知识的情况下设计出很棒的网站。
  
    
    
如果您愿意，SharePoint 2013 还包括 HTML 版本的几种母版页和您可用作起始模板的页面布局。如果您想要从这些文件开始，请创建 HTML 文件（将为您看管关联的 ASP.NET 文件）的副本，然后像往常一样编辑 HTML 文件。您还可以通过使用"来自迷你模板的母版页"选项（该选项将自动创建关联 .master 文件）从基本模板开始。
  
    
    

### 代码段库

SharePoint 2013 包含许多您可以添加到您的网页的即用型组件，如 Web 部件和控件。例如，通过将 SharePoint 组件（如搜索框或导航控件）插入您的 HTML 母版页，您可以快速且轻松地将许多功能置入网页中。
  
    
    
在功能区的"代码段库"组中，您可以选择一个组件，配置其属性和更新该代码段，复制生成的 HTML 代码段并将 HTML 代码段粘贴到 HTML 文件中。HTML 代码段在服务器端预览中和您选择的 HTML 编辑器中向您呈现该组件的高保真预览。将 SharePoint 组件添加到 HTML 文件后，您可以使用 CSS 对这些文件进行完全品牌化。就像对 HTML 文件的任何更新一样，添加 SharePoint 组件并对其进行品牌化后，将自动同步对关联母版页或页面布局的更改。HTML 代码段将自动转换成 SharePoint 组件。
  
    
    
 无论您的 HTML 文件是母版页还是页面布局，代码段库都会向您显示您所需的组件。如果您没有看到您想要的代码段，您可以创建具有 ASP.NET 标记的 HTML 代码段，并将其添加到 HTML 母版页或页面布局中。
  
    
    
设计管理器生成任何 Web 设计工具可使用的 HTML 代码段 - 它只呈现 HTML 并忽略 ASP.NET 和 SharePoint 标记，而 SharePoint 只呈现 ASP.NET 和 SharePoint 标记，忽略 HTML。
  
    
    

### 设备频道

在"设计管理器"中，创建 [设备通道](sharepoint-2013-design-manager-device-channels.md)，然后通过使用每个传入设备的用户代理字符串将通道映射到移动设备或浏览器。一个设备可以属于多个通道，所以可以对通道分级。例如，如果您为"智能电话"和"Windows Phone 8"创建设备通道，您可以对通道进行分级，以便运行 Windows Phone 8 的设备获取专门分配的通道，而其他所有智能电话获得与"智能电话"通道关联的内容。
  
    
    
定义通道后，将母版页映射到每个通道。此母版页可引用不同于默认通道母版页的 CSS 文件。您创建的所有页面布局都将与您创建的所有通道一起工作；若要区分通道之间的页面布局设计，请使用"设备通道面板"控件。
  
    
    
已优化在 SharePoint 2013 中发布网站，以便进行移动开发。您可以使用设备通道功能为一个或多个设备定义通道 - 使您能够精密控制移动用户在您的网站上的体验。您可以将备用母版页分配给每个通道，给予其唯一的版式。您可以选择包括还是排除通道中的任何页面布局部分，预览开发时移动通道设计的进度。设计设备通道时考虑到了搜索引擎优化 (SEO)。您可以使用设备通道转换现有页面的感观以支持移动方案。
  
    
    
您可以使用通道强迫特定呈现出现在特定设备上，此称强迫通道。这在移动方案中极为有用，因为您定义了最适合特定移动设备的呈现。 
  
    
    

### 设备频道面板控件

设备频道面板是一种新型控件，您可以将其包括在页面布局中以控制在哪个频道呈现何种内容。设备频道面板是映射到一个或多个频道的容器：如果呈现页面时其中一个或多个频道处于活动状态，则将呈现设备频道面板的所有内容。设备频道面板帮助您确定何时包括特定频道的特定内容。
  
    
    

### 显示模板
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

您可能想要控制您网站上搜索结果的格式和呈现方式。您可以使用显示模板来实现这一点，显示模板通过用户界面将可用于自定义搜索结果的选项扩展到映射您想要显示的预定义字段。
  
    
    
您想要对搜索结果使用显示模板时 - 您想要映射搜索结果的整体结构的呈现方式时，您想要显示结果组时，以及您想要显示结果集中每个结果或项的呈现方式时，存在三种上下文。它们分别称为控件、组和项模板。
  
    
    
若要了解有关显示模板的详细信息，请参阅  [SharePoint 2013 Design Manager 显示模板](sharepoint-2013-design-manager-display-templates.md)。
  
    
    

### 图像呈现
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

您可以使用 [图像呈现](sharepoint-2013-design-manager-image-renditions.md)来以预定义大小、宽度和裁剪显示已上载的图像。您可以创建源图像文件的多个呈现，也就是说您可以一次性设置显示特性，然后将其应用到若干图像。例如，名为 **Article_image** 的呈现将在文章中显示全尺寸的图像，而名为 **Thumbnail_small** 的呈现将在您定义的上下文中显示较小版本的图像。
  
    
    
可以使用图像呈现之前，请确保在服务器上已启用 BLOB 缓存（您可以在 Internet 信息服务 (IIS) 中的管理工具中执行该操作）。找到您的 **web.config** 文件并启用 BLOB 缓存。刷新网页后，图像呈现将可用。
  
    
    

## SharePoint 2013 中的管理元数据和导航
<a name="SP15_WhatsNewSiteDevelopment_MetadataAndNavigation"> </a>

 中引入的企业管理元数据 (EMM) 功能已在 SharePoint 2013 中得到了改善和扩展，以便获得性能更佳、更容易通过 UI 进行访问和分类驱动的导航（称管理导航）。
  
    
    

### 管理导航

管理导航是传统 SharePoint 导航功能（基于 SharePoint 的结构，称结构导航）的基于分类的备选。 [管理导航](managed-navigation-in-sharepoint-2013.md)功能可让您设计由管理元数据驱动的网站导航。管理导航将创建派生自管理导航结构的 SEO 友好型 URL。因为管理导航由分类驱动，所以您可以用它来设计围绕重要业务理念的网站导航，而无需更改网站或网站组件的结构。
  
    
    

### 内容搜索 Web 部件
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

您可以使用 [内容搜索 Web 部件 (CSWP)](content-search-web-part-in-sharepoint-2013.md) 来显示网页上的搜索数据。它的功能类似于内容查询 Web 部件，但是它服务于不同的网站设计目标。与内容查询 Web 部件样式相比，CSWP 样式更易于自定义。CSWP 以 JSON 格式返回客户端结果。在服务器上，您可以使用显示模板自定义结果。
  
    
    

### 针对网站的其他管理元数据改善
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

SharePoint 2013 为管理元数据 UI 和功能引入了几项改善。若要了解详细信息，请参阅  [SharePoint 2013 中的托管元数据和导航](managed-metadata-and-navigation-in-sharepoint-2013.md)。
  
    
    

## SharePoint 2013 中发布内容
<a name="SP15_WhatsNewSiteDevelopment_Publishing"> </a>

SharePoint 2013 提供新的内容发布功能，利用这些功能，您可以开发支持新的、更灵活且更复杂的拓扑和方案的发布网站。 
  
    
    

### 设计包

如果您是专业的 Web 设计人员，您可能想要在您自己的环境或网站集中创建和测试某项设计，然后提交以安装在其他网站集中。如果您使用的是跨网站发布以在网站集之间共享内容，您可能想要在每个网站打包并安装相同的设计。
  
    
    
在以前的 SharePoint 版本中，如果您想要再使用某项设计，您必须使用 Visual Studio 创建一个 SharePoint 解决方案包（.wsp 文件）。然后在目标网站中，将该包上载到解决方案库中并执行该包。现在，在 SharePoint 2013 中，完成网站设计后，您可以选择在设计管理器中"导出包" 以便导出一个名为 [设计包](sharepoint-2013-design-manager-design-packages.md)的 .wsp 文件。导出设计包时，SharePoint 2013 会自动将您在母版页库、样式库、主题库、设备通道列表和网页内容类型中添加或更改的所有内容打包到一个设计包中。 
  
    
    

> **注释**
> 设计包不包括网页、导航设置或术语库。 
  
    
    

对于 Office 365 公共网站，设计包不会重写现有文件。安装设计包会在隔离设计资产所在的母版库、样式库和主题库中创建一个新文件夹。 
  
    
    
导入设计包时，包中的设计资产会重写任何现有文件，并且作为网站的现有设计应用。网站的默认和系统母版页、主题和备选 CSS 都是从该设计包的文件设置的。有了设计包，置入某个环境的设计可以轻松应用到其他单独的环境。
  
    
    

### 目录

SharePoint 2013 网站发布引入了目录，通过目录您可以将列表并入到发布网站中。利用目录，可以在网站集中发布（跨网站发布功能有赖于目录）内容。使用目录，您可以在 Intranet 网站、Internet 网站和 Extranet 网站之间跨网站和边界真正地再使用内容。对于预定义的搜索查询，目录被标记在搜索中。您可以通过使用 [内容搜索 Web 部件 (CSWP)](content-search-web-part-in-sharepoint-2013.md) 将存储在网站集的目录中的内容置于表面。您可以编写自定义代码来将目录填充到网站中，将产品目录连接到网站以及用自定义页面布局、Web 部件和仅在已定义的上下文中显示的 HTML 内容装饰各个网页。
  
    
    

### 客户端侧呈现控件

SharePoint 2013 中的所有新控件都在客户端呈现。作为设计人员或开发人员，您拥有对内容如何在网页上呈现的控制，并且您可以使用多种设计技术通过内容搜索 Web 部件和显示模板等功能在已发布网页上获取您想要的外观和行为。数据被写入客户端 JSON 数组中的控件，并且您可以使用 JavaScript、CSS 和模板显示内容。 
  
    
    

### 跨网站发布

Microsoft SharePoint 2013 引入了跨网站发布功能，利用此功能，您可以跨多个网站集再使用内容。它使用内置的搜索功能启用发布方案和架构。首先，您可设计跨 SharePoint 场的网站，以使您的网站在 Intranet 和 Internet之间的边界进行扩展。 
  
    
    
使用主题页功能为跨网站发布的内容自定义登录页体验。使用 SEO 友好型 URL 管理以及更轻松地跨越各种方案（包括复杂的多语种网站拓扑）维持和维护网站结构。
  
    
    
若要了解有关跨网站发布的详细信息，请参阅 [方案：使用 SharePoint Server 2013 中的跨网站发布创建 SharePoint 网站](http://technet.microsoft.com/zh-cn/sharepoint/jj872721)。若要了解有关跨网站发布的开发选项的详细信息，请参阅  [SharePoint 2013 中的跨站点发布](cross-site-publishing-in-sharepoint-2013.md)。
  
    
    

### SEO 增强

Bing 及其全球竞争者这样的大型搜索引擎的许多业务网站用户会涉足 Internet 业务网站。SharePoint 2013 包括友好型 URL、主页重定向、XML 站点地图、可让您灵活定义浏览器标题的 SEO 属性和 **<Meta>**标记描述和关键字以及针对多语种网站变体易于理解的 URL 等功能。
  
    
    
在 Office 365 中，网站基础架构在网站变更 24 小时内为您生成已更新的 XML 站点地图。内部安装后，您可以调整站点地图的新鲜度，并指定更新站点地图时您想要 Microsoft ping 哪些搜索引擎。
  
    
    
您 Facebook 上的好友喜欢的内容将影响您在搜索结果中看到的由 Bing 和其他大型搜索引擎返回的内容。您可以使用 SharePoint 2013 编程模型中的 API 自定义如何为您的网站优化搜索。
  
    
    

### 分析和推荐

您可以使用与搜索引擎紧密集成的 SharePoint 2013 分析功能跟踪人们使用发布网站及其组件的方式。分析会驱动内容上的推荐功能，并将计算作为管理属性注入搜索索引。搜索分析提供的推荐（包括网页视图和每天的唯一项）可以影响搜索结果的相关性。
  
    
    
分析将使数据处于匿名状态，并每隔 15 天汇总一次数据，每隔 15 天清除一次事件，然后 3 年后每月清除一次。将一直保留生命周期视图。访问不频繁的内容将被修剪，之后分析会将汇总数据推入报告数据库。您可以使用自定义代码以便从报告数据库将数据导出到 Excel，自定义 **View** 事件的权重以及创建自定义事件（包括 JavaScript 提交的事件）。
  
    
    

### 变体和多语种网站

您可以使用 SharePoint 2013 中的变体功能来创建您在其中希望变化内容呈现方式的多语种网站或其他网站。变体功能仅限于一个网站集。也就是，您可以将源语/区域设置的目标语/区域设置"变体"作为同一 SharePoint 网站集内的当前网站创建。变体支持友好型 URL 和以  [XLIFF 文件格式](the-xliff-interchange-file-format-in-sharepoint-2013.md)导出或导入第三方翻译内容。您可以包括标签、翻译和副本页、各种列表项（如文档库）和导出包中的导航。 
  
    
    

## 其他资源
<a name="SP15_WhatsNewSiteDevelopment_AdditionalResources"> </a>


-  [使用 SharePoint 2013 客户端库代码完成基本操作](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [使用 SharePoint 2013 中的 JavaScript 库代码完成基本操作](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
-  [如何：在 SharePoint 2013 中为基于目录的网站定制页面布局](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 设计管理器中更改预览页面](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [如何：在 SharePoint 2013 中预览页面时解决错误和警告](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 主题概述](themes-overview-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的托管元数据和导航](managed-metadata-and-navigation-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 搜索功能中面向开发人员的新增内容](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

