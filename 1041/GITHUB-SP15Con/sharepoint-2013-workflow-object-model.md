---
title: SharePoint 2013 ワークフロー オブジェクト モデル
ms.prod: SHAREPOINT
ms.assetid: be615a89-3201-4cd8-bbc7-15f3abf9f668
---


# SharePoint 2013 ワークフロー オブジェクト モデル
SharePoint 2013のワークフロー オブジェクト モデルの概要について説明します。
## SharePoint 2013 ワークフロー オブジェクト モデル
<a name="bk_SPwfom"> </a>

SharePoint 2013のオブジェクト モデルは Windows Workflow Foundation 4 用の .NET Framework 4 オブジェクト モデルを基に構築されていますが、SharePoint のワークフロー機能、特に SharePoint アドイン のワークフロー機能を使用できるように技術が革新されています。Windows Workflow Foundation 4 用のネイティブの .NET Framework 4 オブジェクト モデルは, .NET Framework  [System.Workflow namespaces](http://msdn.microsoft.com/ja-jp/library/gg145026.aspx) にあります。
  
    
    
SharePoint ワークフロー オブジェクト モデルは、ワークフロー サービスの 1 つの集合と考えることができます。以下の 4 つのサービスがります。 
  
    
    

- **インスタンス管理サービス:** ワークフロー インスタンスとその実行を管理します。
    
  
- **展開サービス:** ワークフロー定義の展開を管理します。
    
  
- **相互運用機能サービス:** 従来のワークフローをサポートするための相互運用機能ブリッジを管理します。
    
  
- **メッセージング サービス:** メッセージ キューおよび転送を管理します。
    
  

### SharePoint ワークフロー名前空間

一方、SharePoint ワークフロー オブジェクト モデルは、10 個の名前空間に含まれています。5 個は SharePoint の名前空間で、その他の 5 個は Microsoft Office の名前空間です。
  
    
    
 **Microsoft.SharePoint** の名前空間:
  
    
    

-  [Microsoft.SharePoint.Workflow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Workflow.aspx)
    
  
-  [Microsoft.SharePoint.Workflow.Application](https://msdn.microsoft.com/library/Microsoft.SharePoint.Workflow.Application.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowActions](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowActions.WithKey](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.WithKey.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowServices](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.aspx)
    
  
-  [Microsoft.SharePoint.WorkflowServices.Activities](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.Activities.aspx)
    
  
 **Microsoft.Office** の名前空間:
  
    
    

-  [Microsoft.Office.Workflow](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.aspx)
    
  
-  [Microsoft.Office.Workflow.Actions](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Actions.aspx)
    
  
-  [Microsoft.Office.Workflow.Feature](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Feature.aspx)
    
  
-  [Microsoft.Office.Workflow.Routing](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Routing.aspx)
    
  
-  [Microsoft.Office.Workflow.Utility](https://msdn.microsoft.com/library/Microsoft.Office.Workflow.Utility.aspx)
    
  

### SharePoint ワークフロー スキーマ

SharePoint 2013 スキーマの参照コンテンツは [ワークフロー スキーマ](http://msdn.microsoft.com/library/b36ded16-3ffd-4931-811e-c402c1e35b07%28Office.15%29.aspx)という参照ノードに含まれます。以下の内容が含まれます。
  
    
    

-  [WorkflowActions4 スキーマの参照](http://msdn.microsoft.com/library/1c0112de-0139-e64d-d3d6-658541695391%28Office.15%29.aspx)
    
  
-  [WorkflowActions スキーマ要素](http://msdn.microsoft.com/library/7a03ead8-30e0-4601-9c6f-edfb04ce57f9%28Office.15%29.aspx)
    
  
-  [ワークフロー構成スキーマの概要](http://msdn.microsoft.com/library/63824239-6eb2-4cf1-ba84-44eace4d3781%28Office.15%29.aspx)
    
  
-  [WorkflowInfo スキーマ要素](http://msdn.microsoft.com/library/f3bdcc70-15a0-44b2-9b01-330f13430354%28Office.15%29.aspx)
    
  

## その他の技術情報
<a name="bk_additionalresources"> </a>


-  [.NET 4 での Windows Workflow Foundation (WF) の開発者向けの概要](http://msdn.microsoft.com/ja-jp/library/ee342461.aspx)
    
  
-  [Windows Workflow Foundation 4.0: 概要](http://weblogs.asp.net/gunnarpeipman/archive/2009/07/08/windows-workflow-foundation-4-0-hello-workflow.aspx)
    
  
-  [Windows Workflow Foundation (WF) のスクリーンキャスト](http://msdn.microsoft.com/ja-jp/vstudio/aa496123)
    
  
-  [SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

