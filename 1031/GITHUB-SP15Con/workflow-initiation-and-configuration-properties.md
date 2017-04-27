---
title: Workflow initiation and configuration properties
ms.prod: SHAREPOINT
ms.assetid: 7386bbf9-3ed6-4732-bcdb-b27baed7397e
---


# Workflow initiation and configuration properties
Finden Sie unter Übersicht über die Initiierung und Zuordnung Eigenschaften, die für Workflows SharePoint festlegt.
## 

Wenn Sie einen Workflow starten, stellt SharePoint automatisch eine Reihe von Zuordnungs- und Initiierungsformularen Eigenschaften, die den Workflow zu unterstützen. Diese sind unten aufgeführt. Die Gruppe von Eigenschaften, die festgelegt werden hingegen etwas je nach, ob es sich um eine **Website** -Workflows oder **einen Listenworkflow** handelt. Diese Unterschiede werden in den Listen identifiziert.
  
    
    
Verwenden Sie die folgenden Richtlinien, um zuzuordnen und Ihre Workflows mithilfe des Workflow-Objektmodells (Initialisieren) zu starten:
  
    
    

- Verwenden Sie die  [PublishSubscriptionForList](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscriptionForList.aspx) -Methode, um eine Zuordnung für **einen Listenworkflow** zu erstellen.
    
  
- Verwenden Sie die  [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) -Methode, um eine Zuordnung für **einen Websiteworkflow** zu erstellen.
    
  
- Verwenden Sie die  [StartWorkflowOnListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflowOnListItem.aspx) -Methode, um **einen Listenworkflow** zu initiieren.
    
  
- Verwenden Sie die  [StartWorkflow](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflow.aspx) -Methode, um einen **Website** -Workflow zu initiieren.
    
  

> **HINWEIS**
> Die beiden Methoden zum **Zuordnen von** Workflows befinden sich auf die [WorkflowSubscriptionService](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.aspx) -Klasse, solange die beiden Methoden zum **Starten von** Workflows für die Klasse [WorkflowInstanceService](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.aspx) gefunden werden.
  
    
    


## Zuordnungseigenschaften

Die Werte der Zuordnungseigenschaften werden festgelegt, wenn Sie  [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) aufrufen. Werte der Zuordnung sind Association-Level-Eigenschaften, was bedeutet, dass alle Workflowinstanzen mit einer bestimmten Zuordnung den gleichen Eigenschaftswert freigeben. Sie können einen Zuordnung Eigenschaftswert innerhalb des Workflows selbst abrufen, mithilfe der **GetConfigurationValue** -Aktivitätsfeeds ab.
  
    
    
Es folgt eine Liste der Zuordnungseigenschaften, die standardmäßig für **Listen** und **Website** -Workflows festgelegt sind, wenn Sie [PublishSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscription.aspx) aufrufen.
  
    
    

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
    
  

> **WICHTIG**
> Eigenschaften, die mit einem Sternchen (*) markiert sind nicht in den Workflow-APIs definiert, damit Zugriff auf sie einfach ihre Zeichenfolgenwerte verwenden.
  
    
    

Im Fall von **Listenworkflows** gibt es vier zusätzliche Zuordnungseigenschaften standardmäßig aktiviert sind, wenn Sie [PublishSubscriptionForList(WorkflowSubscription, Guid)](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscriptionService.PublishSubscriptionForList.aspx) aufrufen.
  
    
    

-  [ListId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ListId.aspx)
    
  
-  [ListName](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowConfigurationPropertyName.ListName.aspx)
    
  
- **StatusColumnCreated***
    
  
- **StatusFieldName***
    
  

> **WICHTIG**
> Eigenschaften, die mit einem Sternchen (*) markiert sind nicht in den Workflow-APIs definiert, damit Zugriff auf sie einfach ihre Zeichenfolgenwerte verwenden.
  
    
    


> **HINWEIS**
> Sie können benutzerdefinierte Zuordnungseigenschaften mithilfe eines Zuordnungsformulars hinzufügen.
  
    
    


## Initiation-Eigenschaften

Initiation Eigenschaften sind externe Variablen, deren Werte festgelegt werden, wenn der Workflow - d. h., initiiert wird Wenn Sie **StartWorkflow**aufrufen. Beachten Sie jedoch, dass der Eigenschaftswerte zur Laufzeit über innerhalb der Workflow-Instanz mithilfe der **ExternalVariableValue** Aktivitätsfeeds aktualisiert werden können. Sie können die Werte von externen Variablen von *außerhalb*  des Workflows mithilfe von [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstance.Properties.aspx) abrufen.
  
    
    
Externe Variablenwerte sind für jede Workflowinstanz (im Gegensatz zur Zuordnungseigenschaften, in dem alle Workflowinstanzen die gleichen Eigenschaftswerte gemeinsam) spezifisch.
  
    
    
Alle Workflowinstanzen (Liste und Site) verfügen einige externen Variablen, die standardmäßig beim Aufruf von **StartWorkflow**festgelegt werden:
  
    
    

-  [InitiatorUserId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.InitiatorUserId.aspx)
    
  
-  [RetryCode](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.RetryCode.aspx)
    
  
-  [RelatedItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.RelatedItems.aspx)
    
  
Listeninstanzen Workflows verfügen einige zusätzlichen externen Variablen, die standardmäßig beim Aufruf von  [StartWorkflowOnListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowInstanceService.StartWorkflowOnListItem.aspx) festgelegt werden:
  
    
    

-  [CurrentItemUrl](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.CurrentItemUrl.aspx)
    
  
-  [ItemId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ItemId.aspx)
    
  
-  [ItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ItemGuid.aspx)
    
  
-  [ContextListId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.ContextListId.aspx)
    
  
-  [UniqueId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.ExternalVariableName.UniqueId.aspx)
    
  

> **HINWEIS**
> Sie können benutzerdefinierte Initiation Eigenschaften mit einem Initiierungsformular hinzufügen.
  
    
    


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Entwickeln von SharePoint 2013-Workflows mit Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [Gewusst wie: Erstellen von SharePoint 2013-Workflows mit Visual Studio](how-to-create-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

