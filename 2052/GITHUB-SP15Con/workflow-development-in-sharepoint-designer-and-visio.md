---
title: SharePoint Designer 和 Visio 中的工作流开发
ms.prod: SHAREPOINT
ms.assetid: 496780d5-47d6-4a43-bf14-70aefb8d820c
---


# SharePoint Designer 和 Visio 中的工作流开发
了解如何使用 Visio 2013 和 SharePoint Designer 2013 来创建工作流并将其发布到 SharePoint 2013 网站而无需任何代码。
## 简介
<a name="VSSPD_Intro"> </a>

使用 Visio 2013 和 SharePoint Designer 2013，业务分析师、流程顾问和 IT 专业人员可以轻松开展协作和构建 工作流。Visio Professional 2013 和 SharePoint Designer 2013 中的可视化设计器都以编程人员和非编程人员都容易理解的形式提供了工作流的丰富展现形式。
  
    
    

> **注释**
> 有关设置与配置 SharePoint Server 2013 和 工作流管理器 服务器的指南，请参阅 [在 SharePoint Server 2013 中配置工作流](http://technet.microsoft.com/zh-cn/library/jj658586.aspx)。 
  
    
    

使用 Visio 2013，您可以直观地创建 SharePoint 工作流，将工作流导出到 SharePoint Designer 2013，然后将该工作流发布到 SharePoint 网站。在 Visio 2013 中创建工作流后，必须将其导出到 SharePoint Designer 2013。然后，SharePoint 网站所有者或 IT 专业人员使用工作流文本编辑器或新的 Visual Workflow Designer（在 SharePoint Designer 2013 中承载的一个 Visio 2013 ActiveX 控件）将参数添加到工作流。完成工作流后，可以将其发布到 SharePoint 网站。
  
    
    
这非常适合已熟悉 Visio 中流程图的业务分析师和流程顾问用来设计表示业务逻辑的工作流。工作流设计者可以只专注于业务智能 (BI) 工作流需求，而无需是声明性工作流方面的专家。
  
    
    

## 关于在 Visio 2013 和 SharePoint Designer 2013 中创建 SharePoint 工作流
<a name="VSSPD_About"> </a>

Visio 2013 包括一个可用于生成 SharePoint 2013 工作流的 SharePoint 2013 工作流模板。SharePoint 2013 工作流模板与三个模具相关联：SharePoint 2013 工作流操作、SharePoint 2013 工作流条件及 SharePoint 2013 工作流终止符。这些模具中的形状对应于可在 SharePoint 2013 工作流中使用的特定操作和条件。若要生成一个工作流，只需将形状拖到 Visio 2013 中的绘图画布中以对工作流背后的业务逻辑建模。
  
    
    

### 阶段、循环和步骤

SharePoint Designer 2013 中的工作流现在包括阶段、循环及步骤三个概念。工作流作者可以将若干操作和条件组合成一个单元来更明确地定义过程。例如，可能有"批准"或"请求反馈"阶段或步骤。在某个阶段或步骤中，可能包含该流程所必需的所有操作。阶段或步骤本身可能是较长工作流的一个节点，并允许查看者将此阶段视为一个整体（而不是一组操作）来查看其状态。
  
    
    
Visio 2013 中包含的 SharePoint 2013 工作流模板还将阶段、循环和步骤用作创建工作流的逻辑构造基块。 
  
    
    

> **重要信息**
> 由于 Microsoft SharePoint 2010 工作流模板和 SharePoint 2013 工作流模板之间存在基本差别，您不能在由一个模板创建的图表中使用另一个模板中的形状。只有来自 SharePoint 2013 工作流操作、SharePoint 2013 工作流条件和 SharePoint 2013 工作流终止符模具的形状可用于构建 SharePoint 2013 工作流。 
  
    
    


### 阶段形状

一个阶段可以包含任意数目的形状，并可能包含分支。但是，一个阶段（和步骤）只能有一条进入路径和一条外出路径。工作流中的所有操作都必须包含在一个阶段中。阶段形状是通过使用容器形状实现可视化的。阶段形状要求在容器的边缘添加进入和退出形状来定义阶段的进入和退出路径。当您第一次放置容器时，Visio 2013 与 SharePoint Designer 2013 中的可视化设计器会为您添加进入和退出形状。
  
    
    
阶段还具有下列规则：
  
    
    

- 所有图表必须至少有一个阶段。一个阶段，连同进入、退出和开始形状一起，呈现为默认 SharePoint 2013 工作流模板的一部分。
    
  
- 当您向绘图画布添加一个新阶段时，Visio 2013 会在放置阶段时添加开始和结束连接线。
    
  
- 除了进入和退出形状外，阶段不能有其他任何进入和外出连接线。
    
  
- 阶段容器不能嵌套。如果要在一个阶段内嵌套另一个子流程，请使用一个步骤。
    
  
- 在阶段内可能存在停止工作流形状。
    
  
- 在整个图表的阶段之外需要一个明确的开始形状。阶段之外不需要明确的终止形状。
    
  
- 在顶层，工作流只能包含阶段、条件形状以及开始和终止终止符。所有其他形状必须包含在一个阶段内。
    
  

### 循环形状

循环是将作为一个循环执行的连接在一起的一系列形状，在该系列中的最后一个形状返回第一个形状，直到满足一个条件为止。 
  
    
    
像阶段一样，循环呈现为一个容器形状，其中包括一个进入和退出形状（当在画布上放置形状时添加）。循环形状还要求将一个进入和退出形状添加到容器边缘来定义进入和退出循环的路径。
  
    
    
Visio 2013 和 SharePoint Designer 2013 支持两种类型的循环：循环  *n*  次和循环到 *value1*  等于 *value2*  。
  
    
    
循环还必须符合以下规则：
  
    
    

- 循环必须在一个阶段内，并且阶段不能在一个循环内。
    
  
- 步骤可以在一个循环内。
    
  
- 循环只能有一个进入点和一个退出点。
    
  

### 步骤形状

步骤代表组合在一起的一系列连续动作。步骤必须包含于一个阶段中。一个步骤形状还必须包含一个进入和退出形状来定义形状的进入和退出路径。默认情况下，将形状放置到画布上时，会添加两个形状。
  
    
    

## 在 Visio 2013 中创建工作流
<a name="VSSPD_Creating"> </a>

SharePoint 2013 工作流模具中的所有主控形状对应 SharePoint 2013 工作流中的操作、条件和其他逻辑结构。若要生成一个工作流，可以将形状拖到绘图画布上，就像对 Visio 中的任何其他流程图一样。在 Visio 2013 中完成工作流的构建后，必须保存工作流才能在 SharePoint Designer 2013 中将其打开。
  
    
    
若要在 Visio 2013 中打开 SharePoint 2013 工作流模板，请执行以下操作：
  
    
    

### 在 Visio 2013 中打开 SharePoint 2013 工作流模板


1. 打开 Visio 2013。
    
  
2. 选择"新建"。
    
  
3. 在"模板类别"下，选择"流程图"。
    
  
4. 在"选择模板"下，选择"SharePoint 2013 工作流"，然后选择"创建"。
    
    模板将打开，并使用开始和阶段形状预填充绘图画布。阶段形状包含一个进入和一个退出形状，由单一连接线相连。
    
  
当 SharePoint 2013 工作流模板打开后，将操作、条件和其他形状拖到绘图画布以设计工作流。有关各个形状及其含义的详细信息，请参阅文章  [Visio 中的 SharePoint Server 工作流模板中的形状](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)。
  
    
    

> **提示**
>  在设计工作流时，请牢记以下其他注意事项：>  若要快速生成一个工作流，请将操作和条件形状放置到新的阶段形状包含的内部连接线上。Visio 2013 自动将该连接线拆分成多个连接线，使得工作流从进入形状到退出形状连接在一起。>  除了 SharePoint 2013 工作流操作、SharePoint 2013 工作流条件及 SharePoint 2013 工作流终止符模具以外，不要使用来自其他模具的任何形状。只使用 SharePoint 2013 工作流模板提供的连接线工具来添加形状之间的连接。在 SharePoint 2013 工作流中，所有其他连接线形状都无效。>  操作形状、步骤和循环必须始终包含在一个阶段形状内。一些条件形状可以在阶段之外。>  一个阶段形状必须恰好只有一个进入形状和一个退出形状。阶段中包含的工作流子流程必须以进入形状开始，以退出形状结束。>  条件形状必须具有两个离开该形状的连接线，一个标记为"是"，另一个标记为"否"。您可以右键单击连接线来选择"是"或"否"。>  工作流必须只有一个开始形状。开始形状必须在阶段之外。>  您可以将文本添加到工作流中的形状，但形状文本不影响该工作流。
  
    
    


  
    
    
在 Visio 2013 中验证工作流就像验证任何其他连接的图表一样：Visio 根据一组规则检查图表并返回在图表中发现的错误列表。若要了解如何解决验证问题，请参阅文章  [对 Visio 中的 SharePoint Server 工作流验证进行故障排除](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)。
  
    
    

### 在 Visio 2013 中验证 SharePoint 2013 工作流


1. 在"流程"选项卡中，在"图表验证"组中，选择"检查图表"。
    
  
2. 如果在工作流中发现了任何错误，"问题"窗格在图表下打开。选定列表中的每个项来选择图表中引起错误的形状。
    
  
3. 解决在"问题"列表中列出的每个验证错误。处理所有错误后，再次选择"检查图表"。有关如何解决 Visio 2013 中的验证问题的详细信息，请参阅文章  [对 Visio 中的 SharePoint Server 工作流验证进行故障排除](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)。
    
  
4. 如果在工作流中没有发现任何错误，Visio 将显示一条消息，说明图表验证完成且未发现任何问题。
    
  
在 Visio 2013 中成功验证工作流后，您可以保存该文件并将其导入 SharePoint Designer 2013。与 Microsoft SharePoint 2010 工作流模板不同，您可以将 SharePoint 2013 工作流图表的副本另存为默认 Visio 2013 文件格式 (.vsdx)，SharePoint Designer 2013 可以打开该文件。 
  
    
    
使用以下过程将 Visio 2013 中的 SharePoint Designer 2013 工作流另存为可以在 SharePoint 2013 中打开的 Visio 2013 .vsdx 文件：
  
    
    

### 在 Visio 2013 中保存工作流


1. 选择"文件"，然后选择"另存为"。
    
  
2. 在"另存为"下，选择"保存"，然后选择"浏览"。
    
  
3. 在"另存为"对话框中，选择文件的保存位置，并为该文件键入一个名称（"我的 SP 工作流"）。
    
  
4. 选择"保存"。
    
  

## 在 SharePoint Designer 2013 中自定义和发布工作流
<a name="VSSPD_Customizing"> </a>

在您为 Visio 2013 中的 SharePoint 2013 工作流创建基本业务逻辑并保存图表后，即可在 SharePoint Designer 2013 中打开 Visio .vsdx 文件并开始根据您的 SharePoint 2013 网站修改工作流。.vsdx 文件包包含 XML 文档，SharePoint Designer 2013 可以将这些文档转换为工作流。
  
    
    
使用以下过程在 SharePoint Designer 2013 中打开 SharePoint 2013 网站：
  
    
    

### 在 SharePoint Designer 2013 中打开 SharePoint 2013 网站


1. 打开 SharePoint Designer 2013。
    
  
2. 在"打开 SharePoint 网站"下，选择"打开网站"。
    
  
3. 在"打开网站"对话框中，选择您要打开的网站。
    
  
4. 选择"打开"。
    
  
在 SharePoint 2013 网站打开后，您就可以在 SharePoint Designer 2013 内打开 Visio 2013 .vsdx 图表。
  
    
    

### 在 SharePoint Designer 2013 中打开 Visio Professional 2013 工作流


1. 选择"文件"，然后选择"添加项"。
    
  
2. 若要创建列表工作流，请执行下列操作：
    
1. 在"工作流"下，选择"列表工作流"。
    
  
2. 在左窗格中的"列表工作流"下，为您的工作流键入一个名称（My First SP2013 Workflow），然后在您要在其上发布工作流的网站上选择列表。
    
  
3. 在"选择新工作流的工作流平台"列表中，选择"SharePoint 2013 工作流"。
    
  
4. 选择"创建"。
    
  
3. 若要创建一个网站工作流，请执行以下操作：
    
1. 在"工作流"下，选择"网站工作流"。
    
  
2. 在左窗格中的"网站工作流"下，为您的工作流键入一个名称（My First SP2013 Workflow）。
    
  
3. 在"选择新工作流的工作流平台"列表中，选择"SharePoint 2013 工作流"。
    
  
4. 选择"创建"。
    
  
4. 在"工作流"选项卡的"管理"组中，选择"工作流设置"。
    
  
5. 在"工作流设置"选项卡的"管理"组中，选择"从 Visio 导入"。
    
  
6. 在"从 Visio 绘图导入工作流"对话框中，浏览到 .vsdx 文件所在的位置。
    
  
7. 选择您要打开的文件（我的 SP 工作流），然后选择"打开"。
    
  
当您在 SharePoint Designer 2013 中打开一个 .vsdx 文件时，该文件将显示在可视化设计器（即在 SharePoint Designer 中承载的一个 Visio ActiveX 控件）中。Visio 2013 图表保留在 Visio 中创建的所有形状和形状文本。 
  
    
    

> **注释**
> 若要在可视化设计器和 SharePoint Designer 2013 中的 Declarative Designer 之间进行切换，请在"工作流"选项卡的"管理"组中，选择"视图"。此过程可能需要几分钟，因为 SharePoint Designer 2013 要验证工作流，然后将工作流信息从一种格式转换为另一种格式。在此过程中，会进行另一个形状级别的验证。如果检测到图表有错误，这些错误将显示在画布底部的错误窗格中（就像在 Visio 中一样）。 
  
    
    

在可视化设计器中显示的形状还有操作标记（由位于形状左下角的工作流设置类型图标显示）。当您选择一个操作标记时，下拉菜单将显示工作流中该操作或条件的属性 (Attribute) 和"属性"属性 (Property)。这些属性将定义用于该操作的参数值：从哪个列表拉出项，使用什么计算运算符，或者向哪个电子邮件地址发送邮件。当您选择在列表中显示的一个属性时，会出现一个对话框，您可以在其中自定义该属性的设置。 
  
    
    
例如，"发送电子邮件"形状有两个与之相关联的属性："创建电子邮件"和"属性"。当您选择"创建电子邮件"时，"定义电子邮件"对话框将显示，您可以在其中创建要由操作发送的邮件。如果您选择"属性"，"发送电子邮件属性"对话框将显示，它显示该操作的所有参数。
  
    
    

> **注释**
> 有关各个操作、形状及其属性的详细信息，请参阅文章  [Visio 中的 SharePoint Server 工作流模板中的形状](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)和  [工作流操作快速参考（SharePoint 2013 工作流平台）](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)。 
  
    
    

在您设置了工作流中的属性并准备发布时，您必须首先在 SharePoint Designer 2013 中检查工作流是否有错误。当您在功能区上的"可视化设计器"选项卡中选择"发布"时，SharePoint Designer 2013 会自动检查工作流的错误。如果需要，您还可以手动启动错误检查。
  
    
    
使用以下过程在 SharePoint Designer 2013 中检查 SharePoint 2013 工作流：
  
    
    

### 在 SharePoint Designer 2013 中手动检查工作流错误


1. 在"可视化设计器"选项卡上的"保存"组中，选择"检查错误"。
    
  
2. 如果在工作流中发现了任何错误，可视化设计器画布下会打开"问题"窗格。在列表中选择每个项目来选择工作流中引起错误的操作、条件、连接线、终止符或容器。
    
  
3. 解决"问题"列表中列出的每个验证错误。解决所有错误后，请再次选择"检查错误"。 
    
  
4. 如果在工作流中没有发现任何错误，SharePoint Designer 将显示一条消息，说明工作流中没有发现任何问题。
    
  
在完成检查工作流且没有发现任何问题后，您可以将工作流发布到 SharePoint 列表。若要从 SharePoint Designer 2013 发布工作流，请在"可视化设计器"选项卡的"保存"组中，选择"发布"。如果在发布过程中出现任何错误，SharePoint Designer 2013 将返回可视化设计器，并在"问题"窗格中显示错误。
  
    
    

## 其他资源
<a name="VSSPD_Additional"> </a>

有关详细信息，请参阅以下资源：
  
    
    

-  [工作流操作快速参考（SharePoint 2013 工作流平台）](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Visio 中的 SharePoint Server 工作流模板中的形状](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)
    
  
-  [对 Visio 中的 SharePoint Server 工作流验证进行故障排除](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)
    
  
-  [在 Visio 2010 中创建、导入和导出 SharePoint 工作流](http://office.microsoft.com/zh-cn/HA101888007.aspx)
    
  
-  [SharePoint 开发中心](http://msdn.microsoft.com/zh-cn/sharepoint/default.aspx)
    
  
-  [Visio 开发中心](http://msdn.microsoft.com/zh-cn/office/aa905478)
    
  

