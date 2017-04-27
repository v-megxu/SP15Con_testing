---
title: SharePoint ワークフロー開発のベスト プラクティス
ms.prod: SHAREPOINT
ms.assetid: 63d9c867-0c5e-4f89-bc61-eeefb0320844
---


# SharePoint ワークフロー開発のベスト プラクティス
Visual Studio を使用して SharePoint 2013 でワークフローを作成する開発者に対して、ベスト プラクティスのコレクションを提供します。
## ワークフロー開発のベスト プラクティス

SharePoint 用にエラーのないワークフローを開発するには、一般的なガイドラインか、「ベスト プラクティス」に従うことをお勧めします。このことは、ワークフローの開発に SharePoint Designer 2013 または Visual Studio 2012 のどちらを使用しても該当します。
  
    
    

-  [統合されたワークフローを含む SharePoint 用アプリでは、workflowmanifest.xml ファイルでタグを編集する必要がある](sharepoint-workflow-development-best-practices.md#bkm_00)
    
  
-  [[履歴リストに記録する] を使用する場合は詳細な情報が好ましい](sharepoint-workflow-development-best-practices.md#bkm_01)
    
  
-  [作成するすべての文字列および変数の値を履歴リストに書き込む](sharepoint-workflow-development-best-practices.md#bkm_02)
    
  
-  [ワークフローの各ステップまたは重要な作業単位の前後でトレース ログを出力する](sharepoint-workflow-development-best-practices.md#bkm_03)
    
  
-  [変数が Null でなく、変数には期待値が含まれていることを確認する](sharepoint-workflow-development-best-practices.md#bkm_04)
    
  
-  [ワークフロー テキスト フィールド内の文字列の長さが必ず 255 文字以内になるようにする](sharepoint-workflow-development-best-practices.md#bkm_05)
    
  
-  [偽装を使用する場合はニュートラル アカウントでアクセス許可を使用する](sharepoint-workflow-development-best-practices.md#bkm_06)
    
  
-  [再利用可能なワークフローでは、関連付け列を使用してエラーのないリスト フィールドを実現する](sharepoint-workflow-development-best-practices.md#bkm_07)
    
  
-  [ワークフロー設計: 単一のワークフローでビジネス プロセスをモデル化する](sharepoint-workflow-development-best-practices.md#bkm_08)
    
  
-  [ワークフロー設計: 承認アクションの効果的な使用](sharepoint-workflow-development-best-practices.md#bkm_09)
    
  

### 統合されたワークフローを含む SharePoint 用アプリでは、workflowmanifest.xml ファイルでタグを編集する必要がある
<a name="bkm_00"> </a>

統合されたワークフローを含む SharePoint アドイン (親 Web のリストと関連付けられる) は、アプリのパッケージにある  `workflowmanifest.xml` ファイルで次のタグを **true** に変更することで、通常のワークフローと区別されます。
  
    
    

```XML

<SPIntegratedWorkflow xmlns="http://schemas.microsoft.com/sharepoint/2014/app/integratedworkflow">
    <IntegratedApp>true</IntegratedApp>
</SPIntegratedWorkflow>

```


### [履歴リストに記録する] を使用する場合は詳細な情報が好ましい
<a name="bkm_01"> </a>

[ **履歴リストに記録する**] アクション (または、Visual Studio を使用している場合は  [LogToHistoryListActivity](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.LogToHistoryListActivity.aspx) クラス) により、ワークフローのライフサイクルの指定のポイントでワークフローが実行した内容に関する情報を記録できます。つまり、これは使用できる最も重要なトラブルシューティング ツールの 1 つです。重要なポイントで提供する情報が詳細であればあるほど、予期しないイベントをより簡単にトラブルシューティングすることができます。
  
    
    
詳細については、以下を参照してください。 
  
    
    

-  [SharePoint Designer 2010 のワークフロー アクション: クイック リファレンス ガイド](http://office.microsoft.com/ja-jp/sharepoint-designer-help/workflow-actions-in-sharepoint-designer-2010-a-quick-reference-guide-HA010376961.aspx#_Toc260924447)
    
  
-  [LogToHistoryListActivity](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.LogToHistoryListActivity.aspx) クラス
    
  
-  [ワークフロー アクティビティから履歴リストに記録する方法](http://msdn.microsoft.com/ja-jp/library/ff798337.aspx)
    
  
-  [デバッグには [履歴リストに記録する] SharePoint ワークフロー アクションを使用する](http://www.documentmanagementworkflowinfo.com/sample-sharepoint-workflows/use-log-to-history-list-sharepoint-designer-workflow-action-debug.md)
    
  

### 作成するすべての文字列および変数の値を履歴リストに書き込む
<a name="bkm_02"> </a>

 **Log to History List** アクションを使用して履歴リストに文字列および変数を書き込めば、SharePoint デザイナーを使用して作成されたワークフローのデバッグが簡単になります。
  
    
    
詳細については、以下を参照してください。 
  
    
    

-  [SharePoint Designer 2010 のワークフロー アクション: クイック リファレンス ガイド](http://office.microsoft.com/ja-jp/sharepoint-designer-help/workflow-actions-in-sharepoint-designer-2010-a-quick-reference-guide-HA010376961.aspx#_Toc260924447)
    
  
-  [LogToHistoryListActivity](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowActions.LogToHistoryListActivity.aspx) クラス
    
  
-  [ワークフロー アクティビティから履歴リストに記録する方法](http://msdn.microsoft.com/ja-jp/library/ff798337.aspx)
    
  
-  [デバッグには [履歴リストに記録する] SharePoint ワークフロー アクションを使用する](http://www.documentmanagementworkflowinfo.com/sample-sharepoint-workflows/use-log-to-history-list-sharepoint-designer-workflow-action-debug.md)
    
  

### ワークフローの各ステップまたは重要な作業単位の前後でトレース ログを出力する
<a name="bkm_03"> </a>

ワークフローのデバッグをサポートするために、それぞれの重要な作業単位の前後で意味のある情報を収集することが重要です。この情報はトレース ログに書き込まれます。詳細については、以下を参照してください。
  
    
    

-  [トレース ログに書き込む](http://msdn.microsoft.com/ja-jp/library/aa979595.aspx)
    
  
-  [SharePoint のイベント ログおよびトレース ログを使用する](http://msdn.microsoft.com/ja-jp/library/ff647362.aspx)
    
  

### 変数が Null でなく、変数には期待値が含まれていることを確認する
<a name="bkm_04"> </a>

ワークフローで変数を使用する前に、存在する変数が Null でないことを確認します。さらに、変数に期待値が含まれ、データ型が正しいことを確認します。詳細については、「 [変数と引数](http://msdn.microsoft.com/ja-jp/library/dd489456.aspx)」を参照してください。
  
    
    

### ワークフロー テキスト フィールド内の文字列の長さが必ず 255 文字以内になるようにする
<a name="bkm_05"> </a>

ワークフロー テキスト フィールドでの文字列の最大許容長は 255 文字です。テキスト フィールドを、これを超える文字列長に設定しても、テキスト フィールドのコンテンツは切り捨てられて 255 文字になります。
  
    
    

### 偽装を使用する場合はニュートラル アカウントでアクセス許可を使用する
<a name="bkm_06"> </a>

ワークフローで偽装ステップを使用する場合、ニュートラル アカウント (すなわち、特定のユーザーに関連付けられていないアカウント) を使用してワークフローを作成します。これにより、作成者のアカウントが何らかの理由で廃止になってもワークフローが壊れるのを防ぐことができます。
  
    
    
詳細については、「 [SharePoint 2013 ワークフロー プラットフォームを使用した引き上げられた権限でのワークフローの作成](create-a-workflow-with-elevated-permissions-by-using-the-sharepoint-2013-workflo.md)」を参照してください。
  
    
    

### 再利用可能なワークフローでは、関連付け列を使用してエラーのないリスト フィールドを実現する
<a name="bkm_07"> </a>

特定のフィールドが存在するリストに依存する、再利用可能なワークフローを作成する場合は、(1) ワークフローを、特定のフィールドを持つコンテンツ タイプに限定することも、(2) フィールドを関連付け列とすることもできます。コンテンツ タイプは変化し、ワークフローが壊れる原因となる可能性があるので、オプション (2) をお勧めします。
  
    
    

### ワークフロー設計: 単一のワークフローでビジネス プロセスをモデル化する
<a name="bkm_08"> </a>

可能な限り、ワークフロー ロジックをいくつかの小さなワークフローに分割するよりも、単一のワークフローでビジネス プロセスのモデル化を行うことをお勧めします。
  
    
    

### ワークフロー設計: 承認アクションの効果的な使用
<a name="bkm_09"> </a>

可能な限り、複数の **Approval** アクションを作成するのでなく、 **Approval** アクション内の **Stages** 機能を使用するほうが効果的です。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 のワークフロー](workflows-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 ワークフローの基盤](sharepoint-2013-workflow-fundamentals.md)
    
  
-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

