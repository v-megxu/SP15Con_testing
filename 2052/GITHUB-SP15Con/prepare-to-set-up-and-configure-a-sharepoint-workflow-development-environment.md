---
title: 准备设置和配置 SharePoint 工作流开发环境
ms.prod: SHAREPOINT
ms.assetid: b6a3321f-4131-4a8e-9cb7-7a1b4ab9e26b
---


# 准备设置和配置 SharePoint 工作流开发环境
了解如何设置工作流开发环境，以通过使用 Visual Studio 2008 开发 SharePoint 2013 工作流作为独立的  [SharePoint 相关应用程序](http://msdn.microsoft.com/library/fp179930.aspx)。
## SharePoint 2013 中的工作流开发概述

尽管从早期的版本开始，工作流就已成为 SharePoint 的一部分，但 SharePoint 2013 工作流是经过显著增强和改进的平台。 
  
    
    

- 首先，SharePoint 工作流现在建立在  [Windows Workflow Foundation 4.5](http://msdn.microsoft.com/library/dd489441%28v=vs.110%29) 的基础上，这是 .NET Framework 4.5 的一部分。
    
  
- 其次，工作流执行引擎 [工作流管理器](http://msdn.microsoft.com/library/windowsazure/jj193528%28v=azure.10%29.aspx)已从 SharePoint 脱离，并独立运行。这同时提供了灵活性和可扩展性。（请注意，对于向后兼容，旧的 2010 工作流引擎仍然是 SharePoint 2013 的一部分。）
    
  
- 现在，您不是通过编写 C# 代码开发工作流，而是通过使用声明性表达式的工作流设计器在 Visual Studio 中构建工作流。
    
  
- SharePoint 2013 工作流与新的应用程序模型集成，这意味着您现在可以在 SharePoint 外接程序中实施工作流。
    
  
- 您还可以使用 SharePoint Designer 2013 开发 SharePoint 2013 工作流。有关详细信息，请参阅  [SharePoint Designer 和 Visio 中的工作流开发](workflow-development-in-sharepoint-designer-and-visio.md)。
    
  

### 入门

首先，查看以下内容，以熟悉 SharePoint 外接程序中新的应用程序模型及概念： 
  
    
    

|||
|:-----|:-----|
| [面向开发人员的 SharePoint](http://msdn.microsoft.com/zh-cn/sharepoint) <br/> |SharePoint 开发人员门户网站，侧重于 SharePoint 相关应用程序。  <br/> |
| [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |了解什么是 SharePoint 相关应用程序、为何应构建该应用程序，以及在 SharePoint 2013 中构建这些应用程序的基础概念。  <br/> |
| [SharePoint 相关应用的新名称](http://msdn.microsoft.com/library/05b07b04-6c8b-4b7e-bd86-e32c589dfead%28Office.15%29.aspx) <br/> |专用于构建 Office 相关应用程序和 SharePoint 相关应用程序的开发人员门户网站。  <br/> |
| [SharePoint 2013 开发概述](sharepoint-2013-development-overview.md) <br/> |SharePoint 2013 是开发 SharePoint 相关应用程序和场解决方案的平台。着手开发之前，请熟悉 SharePoint 2013 的功能和特征。  <br/> |
| [SharePoint 2013 工作流基础](sharepoint-2013-workflow-fundamentals.md) <br/> |提供了 SharePoint 2013 中工作流基础结构的高级概述，包括平台体系结构和工作流互操作性桥梁的视图。  <br/> |
   
下一步是确保安装了最新的工作流开发环境。您不需要在 SharePoint 服务器引擎中进行开发，但是，您肯定也需要安装 SharePoint Server 以针对其进行开发。
  
    
    
以下是您所需的组件。请务必按以下显示的顺序安装这些项：
  
    
    

1. **安装 SharePoint 环境**
    
  -  [SharePoint Server 2013 更新 (KB2767999)](http://support.microsoft.com/kb/2767999)
    
  
  - 或者，您可以订阅  [Office 365 开发环境](http://msdn.microsoft.com/library/office/apps/fp179924%28v=office.15%29)
    
  
2. **安装工作流管理器环境**
    
  -  [工作流程管理器 1.0 累积更新 (KB2799754)](http://support.microsoft.com/kb/2799754/zh-cn)
    
  
3. **安装 Visual Studio 2008 开发环境**
    
  -  [Visual Studio 2012](http://www.microsoft.com/visualstudio/chs/downloads)
    
  
  -  [Visual Studio 2012 更新 2 (KB2797912)](http://support.microsoft.com/kb/2797912/zh-cn)
    
  
  -  [.NET Framework 4.5 更新 (KB2750149)](http://support.microsoft.com/kb/2750149/zh-cn)
    
  
  -  [Visual Studio 2012 Office 开发人员工具](http://aka.ms/OfficeDevToolsForVS2012)
    
  

### 如果您拥有"预览"版本

如果您拥有 SharePoint Server、工作流管理器 1.0 或 Visual Studio 2013 Office 开发人员工具 的预发行（即"预览"）版本（2013 年 3 月之前的版本），则必须更新您的安装。以下是相应更新的列表：
  
    
    

-  [SharePoint Server 2013 更新 (KB2767999)](http://support.microsoft.com/kb/2767999)
    
  
-  [Microsoft Azure Service Bus 1.0 累积更新 (KB2799752)](http://support.microsoft.com/kb/2799752/zh-cn)
    
  
-  [工作流管理器 1.0 累积更新 (KB2799754)](http://support.microsoft.com/kb/2799754/zh-cn)
    
  

### 您还必须更新通过"预览"版本创建的工作流项目

Visual Studio 工作流组件的发行版及其相关更新引入了重要更改，以增强性能、可扩展性和可靠性。遗憾的是，这些升级要求您更新使用"预览"工具创建的工作流项目。
  
    
    
为了使该过程更简便，我们提供了可以通过 CodePlex 获取的转换工具。该工具称为 [适用于 Visual Studio 2012 的 SharePoint 2013 工作流转换器](http://wfconverter.codeplex.com/)。
  
    
    
以下是更新工作流项目需要的更改的总结：
  
    
    

- 对 **Item Guid** 的活动引用替换为 **Item Id**。这一更改会产生重要影响：
    
  -  [LookupSPListItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.Activities.LookupSPListItemGuid.aspx) 和 [GetCurrentItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.Activities.GetCurrentItemGuid.aspx) 活动从工具中删除；替代的活动为 **LookupSPListItemId** 和 **GetCurrentItemId**。
    
  
  - 对于其他使用 **Item Guid** 的活动，您会发现添加了 **Item Id**，并隐藏了 **Item Guid**。使用 **Item Guid** 的现有项目会继续运行（除了条目超过 5000 项的超大列表，这是进行更改的原因之一）。
    
  
- 应用程序中有一种新的工作流打包格式。
    
  
- XAML 中的工作流活动程序集引用已更改为指向一种新的设计时代理程序集，而不是实际 SP 活动程序集。
    
  

## 其他资源
<a name="bk_addresources"> </a>


-  [设置 SharePoint 加载项的本地开发环境](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 工作流的新增功能](what-s-new-in-workflows-for-sharepoint-2013.md)
    
  
-  [SharePoint Designer 和 Visio 中的工作流开发](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [SharePoint 2013 中的工作流](workflows-in-sharepoint-2013.md)
    
  

