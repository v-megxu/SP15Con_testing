---
title: SharePoint 2013 のワークフロー アクティビティ クラス
ms.prod: SHAREPOINT
ms.assetid: 70d5ca8d-520d-40a9-b24e-52bb31bd6c22
---


# SharePoint 2013 のワークフロー アクティビティ クラス
SharePoint 2013で使用できる SharePoint ワークフロー アクティビティ クラスの概要を示します。
SharePoint 2013ではアクティビティ クラスのパレットが更新されました。表 1 に現在のカタログを示します。49 個のアクティビティが対応するアクティビティ カテゴリにグループ化されています。
  
    
    


> **メモ**
> 今後のリリースでは、この表に示されたアクティビティに、対応するマネージ クラスに応じた API 参照ドキュメントへのリンクが提供される予定です。 
  
    
    


## SharePoint 2013で使用できるワークフロー アクティビティ クラス
<a name="bk_wfactivityclasses"> </a>


**表 1: ワークフロー アクティビティ クラス**

||||
|:-----|:-----|:-----|
|**アクティビティ** <br/> |**カテゴリ** <br/> |**説明** <br/> |
|CreatedBy  <br/> |条件  <br/> |現在のアイテムが、指定されたユーザーによって作成されたかどうかを返します。  <br/> |
|CreatedInRange  <br/> |条件  <br/> |現在のアイテムが、指定された期間に作成されたかどうかを返します。  <br/> |
|ModifiedBy  <br/> |条件  <br/> |現在のアイテムが、指定されたユーザーによって変更されたかどうかを返します。  <br/> |
|ModifiedInRange  <br/> |条件  <br/> |現在のアイテムが、指定された期間に変更されたかどうかを返します。  <br/> |
|WordsInTitle  <br/> |条件  <br/> |指定されたキーワードが、現在のアイテムのタイトルに含まれるかどうかを返します。  <br/> |
|WorkflowInterop  <br/> |調整  <br/> |SharePoint 2010 ワークフロー (Windows Workflow Foundation 3.5) を開始します。  <br/> |
|WaitForCustomEvent  <br/> |イベント  <br/> |カスタム イベントがワークフローに送信されるのを待機します。  <br/> |
|WaitForFieldChange  <br/> |イベント  <br/> |指定されたフィールドが、指定されたリスト アイテムの指定された値に変わるのを待機します。  <br/> |
|WaitForItemEvent  <br/> |イベント  <br/> |指定されたイベントが、指定されたリスト アイテムで発生するのを待機します。  <br/> |
|CheckInItem  <br/> |リスト  <br/> |指定されたリスト アイテムをチェックインします。  <br/> |
|CheckOutItem  <br/> |リスト  <br/> |指定されたリスト アイテムをチェックアウトします。  <br/> |
|CopyItem  <br/> |リスト  <br/> |指定されたファイル アイテムを、指定されたドキュメント ライブラリにコピーします。ファイル以外のリスト アイテムには適用されません。  <br/> |
|CreateListItem  <br/> |リスト  <br/> |リスト アイテムを作成します。  <br/> |
|DeleteListItem  <br/> |リスト  <br/> |リスト アイテムを削除します。  <br/> |
|LookupSPList  <br/> |リスト  <br/> |指定されたリスト ID に一致するリストの情報を返します。  <br/> |
|LookupSPListItem  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティを返します。  <br/> |
|LookupSPListItemBooleanProperty  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **Boolean** として返します。 <br/> |
|LookupSPListItemDateTimeProperty  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **DateTime** として返します。 <br/> |
|LookupSPListItemDoubleProperty  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **Double** として返します。 <br/> |
|LookupSPListItemDynamicValueProperty  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **DynamicValue** として返します。 <br/> |
|LookupSPListItemGuid  <br/> |リスト  <br/> |プロパティ名およびプロパティ値に関して指定されたフィルター条件に一致する最初のリスト アイテムの GUID プロパティを返します。  <br/> |
|LookupSPListItemInt32Property  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **Int32** として返します。 <br/> |
|LookupSPListItemProperty  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **Object** として返します。 <br/> |
|LookupSPListItemStringProperty  <br/> |リスト  <br/> |指定されたリスト アイテムのプロパティの値を **String** として返します。 <br/> |
|LookupSPListProperty  <br/> |リスト  <br/> |リストのプロパティを **DynamicValue** として返します。 <br/> |
|UndoCheckOutItem  <br/> |リスト  <br/> |指定されたリスト アイテムのチェックアウトを元に戻します。  <br/> |
|UpdateListItem  <br/> |リスト  <br/> |リスト アイテムを更新します。  <br/> |
|CompositeTask  <br/> |タスク  <br/> |タスク プロセスを実行します。複数のタスクを複数のユーザーに連続または並行して割り当て、タスクの完了を待機し、集計結果を求めます。  <br/> |
|SingleTask  <br/> |タスク  <br/> |単一のタスク プロセスを実行します。単一のタスクを単一のユーザーまたはグループに割り当て、タスクの完了を待機します。  <br/> |
|ExpandGroupToUsers  <br/> |ユーザー  <br/> |指定された SharePoint グループ プリンシパルのメンバーであるユーザーの LoginNames のコレクションを返します。  <br/> |
|IsValidUser  <br/> |ユーザー  <br/> |指定されたユーザー プリンシパル ID が有効な SharePoint ユーザーであるかどうかを返します。  <br/> |
|LookupSPGroup  <br/> |ユーザー  <br/> |指定されたプリンシパル ID に一致する SP グループの情報を返します。  <br/> |
|LookupSPGroupMembers  <br/> |ユーザー  <br/> |グループの各メンバーに関する情報のコレクションを返します。  <br/> |
|LookupSPPrincipal  <br/> |ユーザー  <br/> |SP プリンシパル (プリンシパルとはアクセス許可を割り当てられる SharePoint のユーザーまたはグループです) に関する情報を返します。  <br/> |
|LookupSPPrincipalId  <br/> |ユーザー  <br/> |指定されたユーザー名に一致するプリンシパル ID を返します。  <br/> |
|LookupSPPrincipalProperty  <br/> |ユーザー  <br/> |指定された SP プリンシパルの指定されたプロパティの値を返します。  <br/> |
|LookupSPUser  <br/> |ユーザー  <br/> |指定されたプリンシパル ID に一致するユーザーの情報を返します。  <br/> |
|LookupSPUserProperty  <br/> |ユーザー  <br/> |指定された SP プリンシパルに一致するユーザーの、指定されたプロパティの値を返します。  <br/> |
|Email  <br/> |ユーティリティ  <br/> |電子メール メッセージを SharePoint サイトのユーザーに送信します。  <br/> |
|GetCurrentItemGuid  <br/> |ユーティリティ  <br/> |ワークフロー インスタンスが実行されている SharePoint リスト アイテムの GUID プロパティを返します。  <br/> |
|GetCurrentListId  <br/> |ユーティリティ  <br/> |ワークフロー インスタンスが実行されている SharePoint リストの ID プロパティを返します。  <br/> |
|GetHistoryListId  <br/> |ユーティリティ  <br/> |履歴リストがワークフロー関連付けに対して指定されている場合、ワークフロー インスタンスの履歴リストの ID を返します。  <br/> |
|GetTaskListId  <br/> |ユーティリティ  <br/> |履歴リストがワークフロー関連付けに対して指定されている場合、ワークフロー インスタンスのタスク リストの ID を返します。  <br/> |
|LookupWorkflowContextProperty  <br/> |ユーティリティ  <br/> |指定されたワークフロー コンテキスト プロパティの値を返します。  <br/> |
|SetField  <br/> |ユーティリティ  <br/> |現在のアイテムにフィールドを設定します。  <br/> |
|SetWorkflowStatus  <br/> |ユーティリティ  <br/> |現在のリスト アイテムの指定されたフィールドに、指定されたテキストを状態として設定します。ワークフローで、リスト アイテムの任意の文字列フィールドの値を「ワークフローの状態」として設定できます。  <br/> |
|TranslateDocument  <br/> |ユーティリティ  <br/> |SharePoint Translation Services を使用して、指定されたドキュメント ライブラリの指定されたドキュメントの変換済みコピーを作成します。  <br/> |
|WebUri  <br/> |ユーティリティ  <br/> |ワークフローが含まれる SP Web の絶対 URI を返します。  <br/> |
|WriteToHistory  <br/> |ユーティリティ  <br/> |指定されたコメントを履歴リストに書き込みます。  <br/> |
   

## その他の技術情報
<a name="bkm_addlresource"> </a>


-  [SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [SharePoint 2013 ワークフロー マネージャーをセットアップおよび構成する](set-up-and-configure-sharepoint-2013-workflow-manager.md)
    
  

