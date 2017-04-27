---
title: ワークフローの相互運用ブリッジで使用可能なワークフロー アクション
ms.prod: SHAREPOINT
ms.assetid: a8903440-ff8f-41a4-8c2a-5dbe12c07cfb
---


# ワークフローの相互運用ブリッジで使用可能なワークフロー アクション
ワークフロー相互運用ブリッジを使って SharePoint 2013 ワークフローで利用可能な SharePoint 2010 のワークフロー アクションを簡潔に一覧にまとめています。
## 相互運用ブリッジのワークフロー アクション
<a name="bkm_wfactions"> </a>

SharePoint 2013のワークフロー インフラストラクチャは Windows Workflow Foundation (WF) 4 を基に構築されているため、Microsoft Azure でワークフローが実行されます。このような理由から、 [SharePoint ワークフロー相互運用機能 ](sharepoint-2013-workflow-fundamentals.md#bkm_InteropBridge) を使用する場合に限り、SharePoint 2010 ワークフロー内の一部のアクションを SharePoint 2013で実行できます。
  
    
    
ワークフロー相互運用ブリッジを使用する場合のみ、次のアクションが可能となります。
  
    
    

- リスト アイテムの権限を追加する
    
  
- フォームをグループに割り当てる
    
  
- タスク アイテムを割り当てる
    
  
- ドキュメント セットのバージョンを取得する
    
  
- データをユーザーから収集する
    
  
- リスト アイテムをコピーする
    
  
- レコードを宣言する
    
  
- リスト アイテムの権限を継承する
    
  
- ユーザーのマネージャーを参照する
    
  
- リスト アイテムの権限を削除する
    
  
- リスト アイテムの権限を置換する
    
  
- ドキュメント セットをリポジトリに送信する
    
  
- コンテンツの承認の状態を設定する
    
  
- ドキュメント セットにコンテンツの承認の状態を設定する
    
  
- ワークフローの状態を設定する
    
  
- 承認プロセスを開始する
    
  
- カスタム タスク プロセスを開始する
    
  
- ドキュメント セットの承認プロセスを開始する
    
  
- フィードバック プロセスを開始する
    
  
- レコードの宣言を解除する
    
  

## 条件とブロック
<a name="bkm_wfconditions"> </a>

 **条件**
  
    
    

- 現在のアイテム フィールドが値に等しい場合
    
  
- リスト アイテムの権限レベルのチェック
    
  
- リスト アイテムの権限のチェック
    
  
 **ブロック**
  
    
    

- 偽装のブロック
    
  

## その他の技術情報
<a name="bkm_addlresources"> </a>


-  [ワークフロー アクション クイック リファレンス (SharePoint 2013 ワークフロー プラットフォーム)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [SharePoint ワークフロー相互運用機能 ](sharepoint-2013-workflow-fundamentals.md#bkm_InteropBridge)
    
  
-  [SharePoint Designer および Visio でのワークフロー開発](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [SharePoint 2013 ワークフロー マネージャーをセットアップおよび構成する](set-up-and-configure-sharepoint-2013-workflow-manager.md)
    
  

