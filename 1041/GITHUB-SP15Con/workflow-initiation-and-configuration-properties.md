---
title: ワークフローの開始と構成のプロパティ
ms.prod: SHAREPOINT
ms.assetid: 7386bbf9-3ed6-4732-bcdb-b27baed7397e
---


# ワークフローの開始と構成のプロパティ
SharePoint がワークフローに設定する開始プロパティと関連付けプロパティの概要を参照してください。
## 

ワークフローを起動すると、SharePoint は、ワークフローをサポートするいくつかの関連付けプロパティと開始プロパティを自動的に設定します。それらを以下にリストします。設定されるプロパティの組み合わせは、それが **サイト** ワークフローであるか **リスト** ワークフローであるかによって多少異なります。それらの違いは、リストに示されています。
  
    
    
以下のガイドラインを使用することにより、ワークフロー オブジェクト モデルを使用してワークフローを関連付け、起動 (開始) します。
  
    
    

- **リスト** ワークフローの関連付けを作成するには、 [PublishSubscriptionForList](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscriptionForList.aspx) メソッドを使用します。
    
  
- **サイト** ワークフローの関連付けを作成するには、 [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) メソッドを使用します。
    
  
- **リスト** ワークフローを開始するには、 [StartWorkflowOnListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflowOnListItem.aspx) メソッドを使用します。
    
  
- **サイト** ワークフローを開始するには、 [StartWorkflow](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflow.aspx) メソッドを使用します。
    
  

> **メモ**
> ワークフローを **関連付ける** ための 2 つのメソッドは [WorkflowSubscriptionService](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.aspx) クラスにあり、ワークフローを **起動する** ための 2 つのメソッドは [WorkflowInstanceService](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.aspx) クラスにあります。
  
    
    


## 関連付けプロパティ

関連付けプロパティの値は、 [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) を呼び出すと設定されます。関連付けプロパティの値は、関連付けレベルのプロパティです。つまり、指定の関連付けを持つすべてのワークフロー インスタンスが同じプロパティ値を共有します。関連付けプロパティの値は、 **GetConfigurationValue** アクティビティを使用して、ワークフロー自体の中から取り出すことができます。
  
    
    
 [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) を呼び出すとき、 **リスト** ワークフローと **サイト** ワークフローの両方に対して既定で設定される、関連付けプロパティのリストを以下に示します。
  
    
    

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
    
  

> **重要**
> アスタリスク (*) のマークが付いたプロパティは、ワークフロー API に定義されていないため、それらにアクセスするには単に文字列値を使用します。 
  
    
    

 **リスト** ワークフローの場合、 [PublishSubscriptionForList(WorkflowSubscription, Guid)](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscriptionForList.aspx) を呼び出すと既定で設定される、4 つの追加の関連付けプロパティがあります。
  
    
    

-  [ListId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ListId.aspx)
    
  
-  [ListName](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ListName.aspx)
    
  
- **StatusColumnCreated***
    
  
- **StatusFieldName***
    
  

> **重要**
> アスタリスク (*) のマークが付いたプロパティは、ワークフロー API に定義されていないので、それらにアクセスするには単に文字列値を使用します。 
  
    
    


> **メモ**
> 関連付けフォームを使用して、カスタムの関連付けプロパティを追加できます。 
  
    
    


## 開始プロパティ

開始プロパティは、ワークフローが開始されるとき (つまり **StartWorkflow** を呼び出したとき) に値が設定される外部変数です。ただし、このプロパティ値は、 **ExternalVariableValue** アクティビティを使用して実行時にワークフロー インスタンス内から更新できることに注意してください。外部変数の値をワークフローの *外部*  から取得するには、 [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstance.Properties.aspx) を使用します。
  
    
    
外部変数の値は、各ワークフロー インスタンスに固有のものです (それに対して関連付けプロパティでは、すべてのワークフロー インスタンスが同じプロパティ値を共有します)。 
  
    
    
すべての (リストとサイトの両方の) ワークフロー インスタンスには、 **StartWorkflow** を呼び出すと既定で設定される、いくつかの外部変数があります。
  
    
    

-  [InitiatorUserId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.InitiatorUserId.aspx)
    
  
-  [RetryCode](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.RetryCode.aspx)
    
  
-  [RelatedItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.RelatedItems.aspx)
    
  
リストのワークフロー インスタンスには、 [StartWorkflowOnListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflowOnListItem.aspx) を呼び出すと既定で設定される、いくつかの追加の外部変数があります。
  
    
    

-  [CurrentItemUrl](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.CurrentItemUrl.aspx)
    
  
-  [ItemId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ItemId.aspx)
    
  
-  [ItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ItemGuid.aspx)
    
  
-  [ContextListId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ContextListId.aspx)
    
  
-  [UniqueId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.UniqueId.aspx)
    
  

> **メモ**
> 開始フォームを使用してカスタムの開始プロパティを追加できます。 
  
    
    


## その他の技術情報
<a name="bk_addresources"> </a>


-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [方法: Visual Studio を使用した SharePoint 2013 ワークフローの作成](how-to-create-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

