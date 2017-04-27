---
title: SharePoint 2013 的工作流操作和活动引用
ms.prod: SHAREPOINT
ms.assetid: 88e09f75-480f-4a68-87a6-b496350345cc
---


# SharePoint 2013 的工作流操作和活动引用
了解在 SharePoint Designer 2013 中创建的工作流可用的工作流操作，以及使用 Visual Studio 2008 的工作流开发人员可用的工作流活动类。
## 工作流活动和操作
<a name="bkm_Activities"> </a>

工作流活动表示代码级的对象，这些对象处理对驱动工作流行为的多个 API 的方法调用。您使用 或其他开发环境与代码中的工作流交互。
  
    
    
有关可用活动的列表，请参阅 [SharePoint 2013 中的工作流活动类](workflow-activity-classes-in-sharepoint-2013.md)。
  
    
    
另一方面，工作流操作是封装这些基础活动并将其以用户友好的方式呈现在 SharePoint Designer 中的包装对象。您在 SharePoint Designer 中与工作流操作交互。
  
    
    
有关可用工作流操作的列表，请参阅  [工作流操作快速参考（SharePoint 2013 工作流平台）](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md) 和 [可使用工作流互操作性桥执行的工作流操作](workflow-actions-available-using-the-workflow-interop-bridge.md)。
  
    
    

## Windows Workflow Foundation 4.0 活动
<a name="bkm_WF4"> </a>

尽管 SharePoint 平台和基础架构为您提供了特别构造的活动类，以便创建自定义 SharePoint 工作流，但是您还可以使用 Windows Workflow Foundation (WF) 4.0 提供的任一活动。 [System.Activities.Statements](http://msdn.microsoft.com/zh-cn/library/system.activities.statements.aspx) 命名空间中的 Microsoft .NET Framework 4 中提供了这些 WF 4.0 活动类。
  
    
    
WF 4.0 活动类提供一些您在 SharePoint 活动类库中可能找不到的有用功能。例如，WF 4.0 包括 **If** 类，该类可让您创建条件活动。此外，您还可以使用 [System.ServiceModel.Activities.Send](http://msdn.microsoft.com/zh-cn/library/system.servicemodel.activities.send.aspx) 活动连接到 Web 服务。
  
    
    

## 本节中
<a name="bkm_inthissection"> </a>


-  [SharePoint 2013 中的工作流活动类](workflow-activity-classes-in-sharepoint-2013.md)
    
  
-  [工作流操作快速参考（SharePoint 2013 工作流平台）](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [可使用工作流互操作性桥执行的工作流操作](workflow-actions-available-using-the-workflow-interop-bridge.md)
    
  

## 其他资源
<a name="bkm_addlres"> </a>


-  [使用 Visual Studio 开发 SharePoint 2013 工作流](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [SharePoint 2013 工作流基础](sharepoint-2013-workflow-fundamentals.md)
    
  
-  [SharePoint 2013 中的工作流](workflows-in-sharepoint-2013.md)
    
  

