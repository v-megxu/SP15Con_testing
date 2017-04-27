---
title: SharePoint 工作流开发最佳实践
ms.prod: SHAREPOINT
ms.assetid: 63d9c867-0c5e-4f89-bc61-eeefb0320844
---


# SharePoint 工作流开发最佳实践
为使用 Visual Studio 在 SharePoint 2013 中创建工作流的开发人员提供最佳实践集合。
## 工作流开发最佳实践

若要开发无差错的 SharePoint 工作流，最好遵循一些通用准则，或"最佳实践"。无论使用 SharePoint Designer 2013 还是 Visual Studio 2008 开发工作流，这一点都毋庸置疑。
  
    
    

-  [包含集成工作流的 SharePoint 相关应用程序必须编辑 workflowmanifest.xml 文件中的标记](sharepoint-workflow-development-best-practices.md#bkm_00)
    
  
-  [当您使用记录到历史记录列表操作时，信息越多越好](sharepoint-workflow-development-best-practices.md#bkm_01)
    
  
-  [将您构建的每个字符串和变量的值都写入到历史记录列表中](sharepoint-workflow-development-best-practices.md#bkm_02)
    
  
-  [在工作流中的每个工作步骤或重要单元执行前后，都输出跟踪日志](sharepoint-workflow-development-best-practices.md#bkm_03)
    
  
-  [验证变量均为非空且包含预期值](sharepoint-workflow-development-best-practices.md#bkm_04)
    
  
-  [确保工作流文本字段中的字符串不超过 255 个字符](sharepoint-workflow-development-best-practices.md#bkm_05)
    
  
-  [使用模拟时，在中立帐户上使用提升的权限](sharepoint-workflow-development-best-practices.md#bkm_06)
    
  
-  [在可重用工作流中，使用关联栏以确保列表字段无差错](sharepoint-workflow-development-best-practices.md#bkm_07)
    
  
-  [工作流设计：在单一的工作流中模拟一个业务流程](sharepoint-workflow-development-best-practices.md#bkm_08)
    
  
-  [工作流设计：有效地使用审批操作](sharepoint-workflow-development-best-practices.md#bkm_09)
    
  

### 包含集成工作流的 SharePoint 相关应用程序必须编辑 workflowmanifest.xml 文件中的标记
<a name="bkm_00"> </a>

可通过将应用程序包的  `workflowmanifest.xml` 文件中的以下标记更改为 **true**，来区分包含集成工作流（可与父 Web 上的列表相关联）的 SharePoint 外接程序与普通工作流应用程序：
  
    
    

```XML

<SPIntegratedWorkflow xmlns="http://schemas.microsoft.com/sharepoint/2014/app/integratedworkflow">
    <IntegratedApp>true</IntegratedApp>
</SPIntegratedWorkflow>

```


### 当您使用记录到历史记录列表操作时，信息越多越好
<a name="bkm_01"> </a>

通过"记录到历史记录列表"操作（或者， 如果您在使用 Visual Studio，则为  [LogToHistoryListActivity](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.LogToHistoryListActivity.aspx) 类），您可以记录有关工作流在工作流生命周期给定时点的操作的信息。这个功能使它成为了最重要的故障排除工具之一。您在工作流中重要时点提供的信息越多，就越容易解决突发事件。
  
    
    
有关详细信息，请参阅以下资源： 
  
    
    

-  [SharePoint Designer 2010 中的工作流操作：快速参考指南](http://office.microsoft.com/zh-cn/sharepoint-designer-help/workflow-actions-in-sharepoint-designer-2010-a-quick-reference-guide-HA010376961.aspx#_Toc260924447)
    
  
-  [LogToHistoryListActivity](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.LogToHistoryListActivity.aspx) 类
    
  
-  [如何：从工作流活动记录到历史记录列表](http://msdn.microsoft.com/zh-cn/library/ff798337.aspx)
    
  
-  [使用记录到历史记录列表 SharePoint 工作流操作进行调试](http://www.documentmanagementworkflowinfo.com/sample-sharepoint-workflows/use-log-to-history-list-sharepoint-designer-workflow-action-debug.md)
    
  

### 将您构建的每个字符串和变量的值都写入到历史记录列表中
<a name="bkm_02"> </a>

如果您使用 **Log to History List** 操作将字符串和变量写入到历史记录列表中，则对使用 SharePoint 设计器创建的工作流进行调试将变得更加容易。
  
    
    
有关详细信息，请参阅以下资源： 
  
    
    

-  [SharePoint Designer 2010 中的工作流操作：快速参考指南](http://office.microsoft.com/zh-cn/sharepoint-designer-help/workflow-actions-in-sharepoint-designer-2010-a-quick-reference-guide-HA010376961.aspx#_Toc260924447)
    
  
-  [LogToHistoryListActivity](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.LogToHistoryListActivity.aspx) 类
    
  
-  [如何：从工作流活动记录到历史记录列表](http://msdn.microsoft.com/zh-cn/library/ff798337.aspx)
    
  
-  [使用记录到历史记录列表 SharePoint 工作流操作进行调试](http://www.documentmanagementworkflowinfo.com/sample-sharepoint-workflows/use-log-to-history-list-sharepoint-designer-workflow-action-debug.md)
    
  

### 在工作流中的每个工作步骤或重要单元执行前后，都输出跟踪日志
<a name="bkm_03"> </a>

为了帮助调试工作流，在每个工作的重要单元执行前后捕获有意义的信息非常重要；应该将这些重要信息提交到跟踪日志中。有关详细信息，请参阅以下资源：
  
    
    

-  [写入到跟踪日志](http://msdn.microsoft.com/zh-cn/library/aa979595.aspx)
    
  
-  [在 SharePoint 中使用事件和跟踪日志](http://msdn.microsoft.com/zh-cn/library/ff647362.aspx)
    
  

### 验证变量均为非空且包含预期值
<a name="bkm_04"> </a>

在工作流中使用变量之前，请确保没有空变量。此外，也要确保变量包含预期值，并且具有正确的数据类型。有关详细信息，请参阅 [变量和参数](http://msdn.microsoft.com/zh-cn/library/dd489456.aspx)。
  
    
    

### 确保工作流文本字段中的字符串不超过 255 个字符
<a name="bkm_05"> </a>

工作流文本字段中字符串的最大允许长度是 255 个字符。如果您将文本字段设置为超出此限制，则其超出 255 个字符的内容将被截掉。
  
    
    

### 使用模拟时，在中立帐户上使用提升的权限
<a name="bkm_06"> </a>

当在工作流中使用模拟步骤时，您应该使用中立帐户（即不与特定用户绑定的帐户）来编写工作流。这样可以防止您的工作流在作者帐户因故废弃时发生中断。
  
    
    
有关详细信息，请参阅 [使用 SharePoint 2013 工作流平台通过提升的权限创建工作流](create-a-workflow-with-elevated-permissions-by-using-the-sharepoint-2013-workflo.md)。
  
    
    

### 在可重用工作流中，使用关联栏以确保列表字段无差错
<a name="bkm_07"> </a>

如果您创建的可重用工作流依赖于具有特定字段的列表，您可以 (1) 将工作流限制为含有指定字段的内容类型，或者 (2) 使字段成为关联栏。建议使用选项 2，这是因为内容类型有可能会有变化并导致工作流发生中断。
  
    
    

### 工作流设计：在单一的工作流中模拟一个业务流程
<a name="bkm_08"> </a>

在可能的情况下，比起将工作流逻辑分解成几个小的工作流，在单一工作流中模拟业务流程的做法更好。
  
    
    

### 工作流设计：有效地使用审批操作
<a name="bkm_09"> </a>

在可能的情况下，比起创建多个 **Approval** 操作，更有效的做法是在 **Approval** 操作中使用 **Stages** 功能。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的工作流](workflows-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 工作流基础](sharepoint-2013-workflow-fundamentals.md)
    
  
-  [使用 Visual Studio 开发 SharePoint 2013 工作流](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

