---
title: 工作流启动和配置属性
ms.prod: SHAREPOINT
ms.assetid: 7386bbf9-3ed6-4732-bcdb-b27baed7397e
---


# 工作流启动和配置属性
请参阅 SharePoint 在工作流上设置的启动和关联属性的概述。
## 

当您启动工作流时，SharePoint 会自动设置一些支持工作流的关联和启动属性。如下表所列。属性集的设置会有所不同，这取决于是 **网站** 工作流还是 **列表** 工作流。这些差异会在列表中标识出来。
  
    
    
使用工作流对象模型关联和启动工作流，请遵循以下准则：
  
    
    

- 若要对 **列表** 工作流创建关联，请使用 [PublishSubscriptionForList](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscriptionForList.aspx) 方法。
    
  
- 若要对 **网站** 工作流创建关联，请使用 [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) 方法。
    
  
- 若要启动 **列表** 工作流，请使用 [StartWorkflowOnListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflowOnListItem.aspx) 方法。
    
  
- 若要启动 **网站** 工作流，请使用 [StartWorkflow](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflow.aspx) 方法。
    
  

> **注释**
> 两种 **关联** 工作流的方法都建立在 [WorkflowSubscriptionService](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.aspx) 类的基础上，而两种 **启动** 工作流的方法都建立在 [WorkflowInstanceService](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.aspx) 类的基础上。
  
    
    


## 关联属性

调用  [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) 时设置关联属性值。关联属性值是关联级属性，这意味着给定关联的所有工作流实例具有相同的属性值。您可以使用 **GetConfigurationValue** 活动检索工作流本身的关联属性值。
  
    
    
以下是在调用  [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) 时，默认情况下对 **列表** 和 **网站** 工作流设置的关联属性列表。
  
    
    

-  [AssociationTitle](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.AssociationTitle.aspx)
    
  
-  [AssociatorUserId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.AssociatorUserId.aspx)
    
  
-  [LayoutsFolder](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.LayoutsFolder.aspx)
    
  
-  [ParentContentTypeId()](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ParentContentTypeId.aspx)
    
  
- **HistoryListId***
    
  
- **TaskListId***
    
  
- **FormData***
    
  
- **SharePointWorkflowContext.Subscription.EventSourceId***
    
  
- **SharePointWorkflowContext.Subscription.EventType***
    
  
- **SharePointWorkflowContext.Subscription.DisplayName***
    
  
- **SharePointWorkflowContext.Subscription.Id***
    
  
- **SharePointWorkflowContext.Subscription.Name***
    
  
- **SharePointWorkflowContext.Subscription.CreatedDate***
    
  

> **重要信息**
> 标有星号 (*) 的属性不在工作流 API 中进行定义，因此访问它们只需使用它们的字符串值。 
  
    
    

对于 **列表** 工作流的情况，当调用 [PublishSubscriptionForList(WorkflowSubscription, Guid)](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscriptionForList.aspx) 时，默认情况下会设置四个其他关联属性。
  
    
    

-  [ListId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ListId.aspx)
    
  
-  [ListName](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ListName.aspx)
    
  
- **StatusColumnCreated***
    
  
- **StatusFieldName***
    
  

> **重要信息**
> 标有星号 (*) 的属性不在工作流 API 中进行定义，因此访问它们只需使用它们的字符串值。 
  
    
    


> **注释**
> 可以通过使用关联窗体添加自定义的关联属性。 
  
    
    


## 启动属性

启动属性是外部变量，这些变量的值是在启动工作流时设置的，即调用 **StartWorkflow** 时。但要注意，使用 **ExternalVariableValue** 活动在工作流实例中运行时可更新这些属性值。通过使用 [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstance.Properties.aspx) 可以从 *外部*  工作流检索外部变量的值。
  
    
    
外部变量的值特定于每个工作流实例（与所有工作流实例共享相同属性值的关联属性不同）。 
  
    
    
所有工作流实例（列表和网站）都有一些外部变量，默认情况下，这些变量在调用 **StartWorkflow** 时设置：
  
    
    

-  [InitiatorUserId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.InitiatorUserId.aspx)
    
  
-  [RetryCode](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.RetryCode.aspx)
    
  
-  [RelatedItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.RelatedItems.aspx)
    
  
列表工作流实例有一些其他外部变量，默认情况下，这些变量在调用  [StartWorkflowOnListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflowOnListItem.aspx) 时设置：
  
    
    

-  [CurrentItemUrl](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.CurrentItemUrl.aspx)
    
  
-  [ItemId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ItemId.aspx)
    
  
-  [ItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ItemGuid.aspx)
    
  
-  [ContextListId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ContextListId.aspx)
    
  
-  [UniqueId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.UniqueId.aspx)
    
  

> **注释**
> 可以通过使用启动窗体添加自定义的启动属性。 
  
    
    


## 其他资源
<a name="bk_addresources"> </a>


-  [使用 Visual Studio 开发 SharePoint 2013 工作流](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [如何：使用 Visual Studio 创建 SharePoint 2013 工作流](how-to-create-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

