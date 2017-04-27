---
title: SharePoint 2013 中的设计管理器概述
ms.prod: SHAREPOINT
ms.assetid: 29834b3f-3815-4347-91d3-296387663114
---


# SharePoint 2013 中的设计管理器概述
了解如何使用设计管理器品牌化 SharePoint 2013 网站。设计管理器是可用于 SharePoint Server 2013 和 Office 365 中发布网站的发布功能。您还可以使用设计管理器品牌化 Office 365 中面向公众的网站。
## 设计管理器简介
<a name="Introduction"> </a>

如果希望 SharePoint 2013 网站代表您所在组织的品牌而不"像 SharePoint 品牌"，则可以创建自定义设计，并使用设计管理器实现此目的。设计管理器是 SharePoint 2013 中的一种功能，在使用您已经熟悉的 Web 设计工具时，利用它可以更轻松地创建完全自定义的完美像素设计。设计管理器是可用于 SharePoint Server 2013 和 Office 365 中发布网站的发布功能。您还可以使用设计管理器品牌化 Office 365 中面向公众的网站。
  
    
    
借助设计管理器，您可以通过您喜欢的任何 Web 设计工具或 HTML 编辑器，仅使用 HTML 和 CSS 为您的网站创建可视化设计，然后将该设计上载到 SharePoint 中。设计管理器是管理自定义设计各个方面的中心枢纽和界面。
  
    
    
创建网站的可视化设计通常适合涉及多个人员或组织的较大流程。有关这些任务的较大流程路线图，请参阅  [SharePoint 2013 中的设计与品牌](http://go.microsoft.com/fwlink/?LinkId=262838)
  
    
    
从较高层次上来说，设计人员将执行以下任务：
  
    
    

- 了解 SharePoint 核心设计概念。有关详细信息，请参阅  [SharePoint 2013 页面模型概述](overview-of-the-sharepoint-2013-page-model.md)。
    
  
- 使用 HTML 和 CSS 创建设计模型。创建设计是 Web 设计人员的核心技术，本文暂不介绍。
    
  
- 使用设计管理器执行设计。本文的某些部分将提供设计管理器简介，以及使用设计管理器执行可视化设计的流程。
    
  

> **注释**
> 可为 SharePoint Online 中面向公众的网站创建的设计元素与其他发布网站的设计元素不同。此外，还不能在此版本的设计管理器中创建可用于 SharePoint Online 中面向公众的网站的设计包。 
  
    
    


## 使用设计管理器执行设计
<a name="Use"> </a>

在查看设计管理器时，您会在左侧看到一系列表示必须执行的高级别任务的链接。根据您的设计和网站要求，您可能不必执行其中所有任务，并且没有必要按此顺序执行这些任务。尽管如此，此序列还是一个很有用的出发点。
  
    
    

### 开始之前

在使用设计管理器之前，需要一个设计。您可以创建自己的设计，也可以使用现成的网站模板。"设计"只是一组最常用于执行网站的可视化设计的文件：
  
    
    

- 至少一个要转换为 SharePoint 母版页的 HTML 文件
    
  
- 一个或多个 CSS 文件
    
  
- JavaScript 文件
    
  
- 图像
    
  
- 其他支持文件
    
  
在使用 HTML 和 CSS 模拟网站时，您可能有几个 HTML 文件，用于执行希望如何显示不同页面或页面类型的设计。请记住，其中只有一个 HTML 文件将转换为母版页（除非您有多个设备通道，其中每个通道都具有自己的母版页，请参阅下一节）。在使用设计管理器创建其他网站元素（例如页面布局或显示模板）后，可以将标记从 HTML 模型传输到与页面布局或显示模板关联的 HTML 和 CSS 文件。
  
    
    
开始之前，您还需要拥有必需的 SharePoint 权限。若要使用设计管理器，您至少必须拥有设计者权限级别。
  
    
    

### 管理设备通道

在设计网站之前，需要考虑您的网站应针对哪些设备，以及各个设备的用户体验。例如，您可能需要为某些种类的智能电话或平板电脑优化网站设计。
  
    
    
根据定义的通道，您可能需要几种设计，因此需要几个 HTML 文件，其中每个文件都会转换为单独的母版页。此外，每个 HTML 文件（和每个母版页）均可引用其自己的 CSS 文件。在设计网站前，设备通道是要考虑的首要问题之一。
  
    
    
借助设备通道，您可通过将不同设计映射到不同设备，以多种方式呈现单个发布网站。每个通道都有其自己的母版页，可链接到为特定设备优化的样式表。每个通道均为一个或多个设备指定用户代理子字符串，例如"Windows Phone OS"。有相关规则确定每个通道包括哪些设备。然后，在访问者浏览您的网站时，每个通道均可捕获其指定设备或设备类（例如 Windows Phone）的流量，并且访问者可使用为特定设备优化的设计查看您的网站。
  
    
    
设备通过创建和存储于顺序很重要的 SharePoint 列表中，这是因为设备通道也具有分级。此列表中的设备通道由上至下进行排序，包含规则也按此顺序进行处理。这表示您希望规则最详细精确的设备通道位于最上面。例如，针对"Windows Phone OS 7.0"的通道应在针对"Windows Phone OS"的通道之前。
  
    
    

### 上载设计文件

在创建设计时，您可以使用您喜欢的任何 HTML 编辑器并在您的本地计算机上处理文件。但最终您必须将这些文件上载到 SharePoint 网站的母版页样式库，以便您可以使用设计管理器转换、预览和完善设计。
  
    
    
上载并继续处理设计文件的最简单方式是将您计算机上的驱动器映射到 SharePoint 网站的母版页样式库。这样可将您计算机上的文件夹连接到母版页样式库，以使您可以像处理本地文件一样处理驻留在 SharePoint 2013 的服务器上的文件。
  
    
    
在映射网络驱动器后，只需将设计文件复制到您的计算机中与 SharePoint 连接的映射驱动器上的文件夹中，即可将设计上载到 SharePoint。在将 HTML 文件转换为 SharePoint 母版页后，以及在创建页面布局和显示各自有其自己的相关 HTML 文件的模板后，您可以继续在您计算机上的 HTML 编辑器中编辑这些相关 HTML 文件。每次在映射驱动器中保存文件后，SharePoint 都会自动将您计算机上的文件与母版页样式库同步。您可以在映射驱动器上创建自己的文件夹结构，该结构由 SharePoint 维护，并会显示在母版页样式库中。您应将与一个设计相关的所有文件保存在单个文件夹下，然后在准备好上载设计时，将该文件夹复制到映射驱动器中。
  
    
    
有关详细信息，请参阅 [如何：将网络驱动器映射到 SharePoint 2013 母版页样式库](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
  
    
    

### 编辑母版页

创建包含所有所需 SharePoint 功能（例如导航和搜索）的完全品牌化的母版页，基本上是一个包含三个步骤的过程：
  
    
    

1. 将 HTML 文件转换为 SharePoint 母版页。
    
  
2. 预览母版页，修复所有问题。
    
  
3. 在母版页中添加 SharePoint 代码段。
    
  
这三个步骤各自在设计管理器的不同页面上执行。
  
    
    

#### 转换 HTML 文件

设计管理器的核心功能是将 HTML 设计转换为 SharePoint 母版页。若要成功呈现，SharePoint 母版页必须包含多个 ASP.NET 元素和特定于 SharePoint 的元素。在将 HTML 文件转换为母版页时，设计管理器会创建一个包含以上所有必需元素的 .master 文件，因此您不必知道这些元素。在转换过程中，还会在原始 HTML 文件中添加某些 HTML 标记（例如注释）。
  
    
    
在转换后，HTML 文件和 SharePoint 母版页相关联，因此在映射驱动器中编辑并保存 HTML 文件后，母版页会自动更新。在设计管理器中，HTML 母版页有一个名为 **Associated File** 的属性，它可确定是否将 HTML 文件的更改内容同步到 .master 文件中。
  
    
    

> **注释**
> 设计管理器还提供了使用最简单的母版页开始设计的选项。在此方案中，您不必从 HTML 设计着手；您可以创建特定 HTML 母版页，其中包含使母版页正确呈现在 SharePoint 中所需的最少页面元素，然后通过编辑 HTML 母版页扩建设计。 
  
    
    


#### 预览母版页

除了转换母版页外，设计管理器还提供服务器端预览（与 HTML 编辑器中的设计时预览对比）功能，因此您可以实时预览母版页，并修复可能阻止页面呈现的所有问题。例如，HTML 文件必须与 XML 兼容，因此您可能必须修复较小的标记问题，例如为所有元素提供结束标记。若要修复任何问题，请编辑 HTML 文件，保存该文件，然后刷新服务器端预览。
  
    
    
在预览母版页时，可以使用左上角的 **更改预览页面** 选项预览母版页和任何现有页面，或创建要预览的新页面。与 HTML 编辑器中的 HTML 母版页设计时预览不同，此服务器端预览是功能完整的实时预览，因此您可能更希望编辑 HTML 文件，保存该文件以使最新更改同步到关联的 .master 文件中，然后刷新实时预览并在浏览器中查看最新设计更改。
  
    
    

#### 添加代码段

在转换母版页并成功预览它后，即可在母版页中添加代码段。代码段是 SharePoint 组件（例如导航控件、搜索框或 Web 部件）的 HTML 表示形式，您可以将其添加到母版页中。通过在母版页中添加代码段，可将各种 SharePoint 功能快速内置到母版页中。添加代码段基本上是一个包含三个步骤的过程：
  
    
    

1. 在代码段库中查找和配置代码段。
    
  
2. 将代码段复制到 HTML 母版页中。
    
  
3. 使用 CSS 预览代码段，并设计代码段的样式。
    
    有关详细信息，请参阅  [SharePoint 2013 设计管理器代码段](sharepoint-2013-design-manager-snippets.md)。
    
  

#### 在代码段库中查找和配置代码段

代码段库是可以快速查看哪些组件可用于您所编辑的文件类型（母版页或页面布局）的位置。在功能区上，可选择代码段。在右侧的属性网格中，可以配置此代码段实例的属性，然后选择 **更新** 以刷新左侧的 HTML 代码段。
  
    
    

#### 将代码段复制到 HTML 母版页中

在配置代码段后，可以将其复制到剪贴板，然后将其粘贴到 HTML 文件中的适当位置。您的 HTML 设计可能已包含模型或静态控件，在此情况下，如果要将它们替换为代码段库中的动态代码段，则需要删除或注释掉它们。
  
    
    

#### 使用 CSS 预览代码段，并设计代码段的样式

在将代码段复制到 HTML 文件并保存更改后，可以刷新母版页的服务器端预览，以查看控件的呈现方式。代码段包含提供 HTML 编辑器中设计时预览的标记，但服务器端预览可使用实时数据显示高保真预览，例如，导航控件将使用数据源中的实时数据显示网站的当前导航结构。
  
    
    
默认情况下，大多数代码段都会继承主 SharePoint 2013 样式表 corev15.css 中的样式。若要设计代码段的样式，必须确定对此代码段应用哪些样式，然后使用自定义 CSS 覆盖它们。若要确定这些默认样式，可以使用浏览器工具（例如 Internet Explorer 中的开发人员工具）。在使用 Internet Explorer 的服务器端预览查看母版页时，可以按 **F12**，选择 **查找**，然后选择 **通过单击选择元素 **。这样可以单击代码段并查看要覆盖的确切样式，具体方法是将 CSS 添加到母版页链接到的自定义样式表中。****
  
    
    

### 编辑显示模板

如果是使用本地安装的 SharePoint Server，则可使用内容搜索 Web 部件和其他搜索驱动 Web 部件将搜索查询结果显示为页面内容。搜索驱动 Web 部件可将显示模板用于两个主要用途：
  
    
    

- 将搜索结果项中返回的托管属性映射到可供 JavaScript（包括您选择实现的所有自定义 JavaScript）使用的属性。
    
  
- 使用 HTML 和 CSS 呈现如何显示这些属性，并对其设计样式。
    
  
借助母版页和页面布局，可编辑关联的 HTML 文件，但不能编辑 .master 文件或 .aspx 文件。同样，显示模板由一个 HTML 文件和一个关联的 .js 文件组成，在其中只能编辑 HTML 文件。每次保存该 HTML 文件后，SharePoint 都会自动更新关联的 .js 文件。
  
    
    
在希望创建自定义显示模板时，应先复制现有显示模板之一，然后再修改它。此做法很有益，因为默认显示模板包含 HTML 文件中注释的信息，并且您将具有用于执行映射输入字段等基本任务的正确基本页面结构和框架。
  
    
    

### 编辑页面布局

创建页面布局的过程与创建母版页的过程略有不同。对于母版页，需要先从 HTML 设计着手，将其转换为 SharePoint 母版页，然后继续编辑关联的 HTML 文件。但对于页面布局，需要先在设计管理器中创建页面布局，这样会创建 .aspx 文件和 HTML 文件，然后在 HTML 编辑器中编辑映射驱动器中的关联 HTML 文件。必须使用设计管理器创建页面布局的原因是，使正确的页字段集能够添加到页面布局中。
  
    
    
在创建页面布局时，可以选择预览页面布局时使用的母版页，并可选择页面布局内容类型。内容类型是字段和数据类型的架构，页面布局内容类型中的可用字段可确定所设计的页面布局提供的页字段控件。您可以先在浏览器中创建页面布局，以便添加页字段。
  
    
    
在创建具有关联的 HTML 文件的页面布局后，其他步骤与母版页的相关步骤相同：
  
    
    

- 预览页面布局，通过编辑并保存 HTML 版本修复所有问题。
    
  
- 在页面布局中添加代码段（配置、复制、预览、设计样式）。
    
  
在代码段库中，有不同代码段可用于页面布局和母版页，功能区仅显示与该文件类型相关的代码段。例如，导航和搜索框代码段仅适用于母版页，而页字段仅适用于页面布局。
  
    
    
在设计页面布局时，基本任务是放置将显示内容作者创建的内容的页字段控件并设计其样式。页面布局的样式可以驻留在母版页链接到的任何样式表中，每个页面布局也可链接到其自己的特定样式表。如果 HTML 设计包括与母版页相比更适合页面布局的内容，则需要从 HTML 母版页中转移出该内容，然后将这些样式应用到相关页面布局的适当控件和元素。
  
    
    
有关详细信息，请参阅 [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)。
  
    
    

### 创建主题和组合外观

在 Office 365 中（而非本地 SharePoint Server 2013 安装中）面向公众的网站中，设计管理器具有创建主题和组合外观的选项。主题是一组可应用于自定义设计（即母版页）的字体和颜色。主题在上载到主题库的 .xml 文件中进行定义。如果希望自定义母版页成为可设置主题的母版页，则需要在 SharePoint 可识别和使用的母版页中添加特殊标记，以插入主题元素（例如字体和颜色）。
  
    
    
组合外观只是背景图像、主题（即字体和颜色）和设计（即母版页）之间的关联内容。组合外观采用预定义设计元素（主题、背景图像和母版页），使其用于许多不同组合，以使面向公众的网站具有更多自定义选项。
  
    
    

### 发布和应用设计

设计使用的大多数资产（例如图像、HTML、CSS 和 JavaScript 文件）将驻留在母版页样式库中。母版页样式库是一种 SharePoint 文档库，默认情况下，已开启版本控制，每次您编辑文件后，它都会创建主要版本和次要（草稿）版本。
  
    
    
在将设计应用到网站之前，首先必须发布设计使用的各个文件或资产的主要版本。如果是在测试环境下设计网站，则应关闭母版页样式库的版本控制，以使您不必在预览网站之前记住发布每个文件。但是，如果是在活动网站上设计，此做法并非最佳实践。
  
    
    
在发布所有设计文件后，即可通过向网站分配创建完的母版页来应用设计。各个网站均可具有分配给各个设备通道的不同母版页，此设计管理器页面是对通道应用母版页的位置。
  
    
    

### 创建设计包

设计包是一种收集设计使用的所有文件和资产，将它们从一个网站导出，将它们导入另一个网站并将此设计应用到新网站的简单方式。如果在测试网站集中实现和完善设计，并希望在活动网站集中部署此设计，则可使用设计包传输您的设计。
  
    
    
设计包是一个 .wsp 文件（SharePoint 解决方案文件），它基本上是一种特殊类型的 .cab 文件。在创建或导入设计包时，.wsp 文件将存储在解决方案库中。在导入设计包后，设计包会自动激活。如果母版页和页面布局在打包之前已发布，并且母版页在打包之前已分配给设备通道，则在部署此设计包时此设计会自动应用到网站。另外，若要将此设计应用到新网站，则只需发布这些设计文件，并按设备通道应用母版页。
  
    
    

> **注释**
> 设计包不可用于 Office 365 中面向公众的网站。若要使用设计管理器实现完全自定义设计，可通过向设计者暂时授予设计者权限级别来将该人邀请到您的网站中。 
  
    
    


## 其他资源
<a name="Additional"> </a>


-  [SharePoint 2013 页面模型概述](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [如何：在 SharePoint 2013 中将 HTML 文件转换为母版页](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建页面布局](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
