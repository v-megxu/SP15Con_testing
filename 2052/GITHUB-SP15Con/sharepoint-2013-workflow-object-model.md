---
title: SharePoint 2013 工作流对象模型
ms.prod: SHAREPOINT
ms.assetid: be615a89-3201-4cd8-bbc7-15f3abf9f668
---


# SharePoint 2013 工作流对象模型
获取对 SharePoint 2013 中工作流对象模型的简要介绍。
## SharePoint 2013 工作流对象模型
<a name="bk_SPwfom"> </a>

SharePoint 2013 对象模型内置于 Windows Workflow Foundation 4 的 .NET Framework 4 对象模型顶部，但具有在 SharePoint（通常）实现工作流功能的创新，特别是在 SharePoint 外接程序 中。Windows Workflow Foundation 4 的本机 .NET Framework 4 对象模型位于 .NET Framework  [System.Workflow 命名空间](http://msdn.microsoft.com/zh-cn/library/gg145026.aspx)中。
  
    
    
其中一种方法是将 SharePoint 工作流对象模型视为一套工作流服务。以下是 4 个服务： 
  
    
    

- **实例管理服务：**管理工作流实例及其执行情况。
    
  
- **开发服务：**管理工作流定义的部署。
    
  
- **互操作服务：**管理支持传统工作流的互操作桥。
    
  
- **消息传递服务**管理消息队列和传输。
    
  

### SharePoint 工作流命名空间

另一方面，SharePoint 工作流对象模型包含在 10 个命名空间中：其中 5 个为 SharePoint 命名空间，另外 5 个为 Microsoft Office 命名空间。
  
    
    
 **Microsoft.SharePoint** 命名空间：
  
    
    

-  [Microsoft.SharePoint.Workflow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Workflow.aspx)
    
  
-  [Microsoft.SharePoint.Workflow.Application](https://msdn.microsoft.com/library/Microsoft.SharePoint.Workflow.Application.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowActions](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowActions.WithKey](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.WithKey.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowServices](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowServices.Activities](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.Activities.aspx)
    
  
 **Microsoft.Office** 命名空间：
  
    
    

-  [Microsoft.Office.Workflow](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.aspx)
    
  
-  [Microsoft.Office.Workflow.Actions](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Actions.aspx)
    
  
-  [Microsoft.Office.Workflow.Feature](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Feature.aspx)
    
  
-  [Microsoft.Office.Workflow.Routing](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Routing.aspx)
    
  
-  [Microsoft.Office.Workflow.Utility](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Utility.aspx)
    
  

### SharePoint 工作流架构

SharePoint 2013 架构的引用内容包含在 [工作流架构](http://msdn.microsoft.com/library/b36ded16-3ffd-4931-811e-c402c1e35b07%28Office.15%29.aspx)引用节点中，并且包含以下内容：
  
    
    

-  [WorkflowActions4 架构参考](http://msdn.microsoft.com/library/1c0112de-0139-e64d-d3d6-658541695391%28Office.15%29.aspx)
    
  
-  [WorkflowActions 架构元素](http://msdn.microsoft.com/library/7a03ead8-30e0-4601-9c6f-edfb04ce57f9%28Office.15%29.aspx)
    
  
-  [工作流配置架构概述](http://msdn.microsoft.com/library/63824239-6eb2-4cf1-ba84-44eace4d3781%28Office.15%29.aspx)
    
  
-  [WorkflowInfo 架构元素](http://msdn.microsoft.com/library/f3bdcc70-15a0-44b2-9b01-330f13430354%28Office.15%29.aspx)
    
  

## 其他资源
<a name="bk_additionalresources"> </a>


-  [开发人员对 .NET 4 中 Windows Workflow Foundation (WF) 的简介](http://msdn.microsoft.com/zh-cn/library/ee342461.aspx)
    
  
-  [Windows 工作流基础 4.0：您好，工作流！](http://weblogs.asp.net/gunnarpeipman/archive/2009/07/08/windows-workflow-foundation-4-0-hello-workflow.aspx)
    
  
-  [Windows 工作流基础 (WF) 视频](http://msdn.microsoft.com/zh-cn/vstudio/aa496123)
    
  
-  [SharePoint 2013 的工作流操作和活动引用](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [使用 Visual Studio 开发 SharePoint 2013 工作流](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

