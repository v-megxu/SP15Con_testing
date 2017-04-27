---
title: SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス
ms.prod: SHAREPOINT
ms.assetid: 88e09f75-480f-4a68-87a6-b496350345cc
---


# SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス
SharePoint Designer 2013でのワークフロー作成に使用できるワークフロー アクションと、Visual Studio 2012 を使用するワークフロー開発者が使用できるワークフロー アクティビティ クラスについて確認します。
## ワークフロー アクティビティおよびアクション
<a name="bkm_Activities"> </a>

ワークフロー "アクティビティ" はコードレベルのオブジェクトを表し、ワークフローの動作を実行する各種の API に対するメソッド呼び出しを処理します。ワークフロー アクティビティをコードで操作するには、 またはその他の開発環境を使用します。
  
    
    
使用可能なアクティビティの一覧については、「 [SharePoint 2013 のワークフロー アクティビティ クラス](workflow-activity-classes-in-sharepoint-2013.md)」を参照してください。
  
    
    
一方、ワークフロー "アクション" は、これらの基になっているアクティビティをカプセル化して SharePoint Designer でユーザーにわかりやすい形式にするラッパー オブジェクトです。ワークフロー アクションの操作には SharePoint Designer を使用します。
  
    
    
使用可能なワークフロー アクションの一覧については、「 [ワークフロー アクション クイック リファレンス (SharePoint 2013 ワークフロー プラットフォーム)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)」および「 [ワークフローの相互運用ブリッジで使用可能なワークフロー アクション](workflow-actions-available-using-the-workflow-interop-bridge.md)」を参照してください。
  
    
    

## Windows Workflow Foundation 4.0 のアクティビティ
<a name="bkm_WF4"> </a>

SharePoint プラットフォームおよびインフラストラクチャは、ユーザー設定の SharePoint ワークフローを作成するために特別に作成されたアクティビティ クラスを提供しますが、Windows Workflow Foundation (WF) 4.0 によって提供されるアクティビティのいずれかを使用することもできます。これらの WF 4.0 アクティビティ クラスは、「 [System.Activities.Statements 名前空間](http://msdn.microsoft.com/ja-jp/library/system.activities.statements.aspx)」の Microsoft .NET Framework 4 で提供されています。
  
    
    
WF 4.0 アクティビティ クラスは、SharePoint アクティビティ クラス ライブラリには含まれない可能性のある有効な機能をいくつか提供します。たとえば、WF 4.0 には **If** クラスが含まれていて、これを使用すると条件付きアクティビティを作成できます。さらに、「 [Send クラス](http://msdn.microsoft.com/ja-jp/library/system.servicemodel.activities.send.aspx)」アクティビティを使用して Web サービスに接続することもできます。
  
    
    

## このセクションの内容
<a name="bkm_inthissection"> </a>


-  [SharePoint 2013 のワークフロー アクティビティ クラス](workflow-activity-classes-in-sharepoint-2013.md)
    
  
-  [ワークフロー アクション クイック リファレンス (SharePoint 2013 ワークフロー プラットフォーム)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [ワークフローの相互運用ブリッジで使用可能なワークフロー アクション](workflow-actions-available-using-the-workflow-interop-bridge.md)
    
  

## その他の技術情報
<a name="bkm_addlres"> </a>


-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [SharePoint 2013 ワークフローの基盤](sharepoint-2013-workflow-fundamentals.md)
    
  
-  [SharePoint 2013 のワークフロー](workflows-in-sharepoint-2013.md)
    
  

