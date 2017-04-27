---
title: SharePoint 2013 ワークフローの新機能
ms.prod: SHAREPOINT
ms.assetid: 1d51421b-61ac-46b6-a865-52f968ddc5b3
---


# SharePoint 2013 ワークフローの新機能
SharePoint 2013 のワークフローの新しい機能について説明します。
SharePoint 2013 のワークフロー フレームワークは以前のバージョンから大幅に変更されました。以下のシナリオでは、ワークフロー インフラストラクチャの大幅な更新と機能拡張について概要を簡単に説明します。
  
    
    


## 完全に再設計されたワークフロー インフラストラクチャ
<a name="SP15Whatsnewinworflow_infrastructure"> </a>

SharePoint 2013 ワークフローは、以前のバージョンから大幅に再設計された Windows Workflow Foundation 4 (WF) により動作します。Windows Workflow Foundation は、 [Windows Communication Foundation (WCF)](http://msdn.microsoft.com/ja-jp/vstudio/aa496123) により提供されるメッセージング機能上に構築されます。
  
    
    
この新しいワークフロー インフラストラクチャの最も目立った機能は、新しいワークフロー実行ホストとしての Microsoft Azure の導入です。ワークフロー実行エンジンは今は SharePoint の外部の Microsoft Azure にあります。図 1 は新しいワークフロー インフラストラクチャの一般的な概要を示しています。図 1 に示される概念の詳細については、「 [SharePoint 2013 ワークフローの基盤](sharepoint-2013-workflow-fundamentals.md)」を参照してください。
  
    
    

**図 1. ワークフロー インフラストラクチャのアーキテクチャの概要**

  
    
    

  
    
    
![ワークフロー アーキテクチャの概要](images/wfArchitecture1.png)
  
    
    

  
    
    

  
    
    

## 完全な宣言型のコード不要な作成環境
<a name="SP15Whatsnewinworflow_environment"> </a>

もう一方の大きな変更は WF 4 プラットフォーム上のワークフローは完全に宣言型になっていることです。つまり、ワークフローをマネージ センブリにコンパイルしてアセンブリ キャッシュに展開する必要がなくなった代わりに、XAML ファイルでワークフローを定義し、実行を計画します。
  
    
    

## SharePoint Designer 2013 作成サポートの強化
<a name="SP15Whatsnewinworflow_SPDauthoring"> </a>

SharePoint Designer 2013 は、SharePoint ワークフローの作成に選択する作成環境になることを目標に更新されています。SharePoint Designer 2013 は、ワークフロー作成者にデザイナー画面とテキストベースのワークフロー作成環境の両方を提供します。さらに、Visual Studio 2012 でワークフローのカスタム アクションを開発し、それらを SharePoint Designer 2013 にインポートできます。インポートしたカスタム アクションは ワークフロー ​​デザイナー からアクセスできます。
  
    
    
つまり、インフォメーション ワーカー ("パワー ユーザー") と開発者の両者のニーズを SharePoint ワークフローの作成および開発環境で活用できるようになっています。
  
    
    

## Visual Studio 2012 ワークフロー プロジェクト タイプのサポート
<a name="SP15Whatsnewinworflow_VSworkflow"> </a>

インフォメーション ワーカーとソフトウェア開発者との間の共同作業を容易にするために、Visual Studio 2012 には SharePoint ワークフロー プロジェクト タイプとワークフロー カスタム アクション アイテム タイプが用意されています。Visual Studio 2012 を使用したワークフローの開発について、およびワークフロー開発における SharePoint Designer 2013 と Visual Studio 2012 の区別についての詳細は、「 [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)」を参照してください。
  
    
    

## カスタム アクション作成のサポート
<a name="SP15Whatsnewinworflow_customactions"> </a>

今まで SharePoint Designer 2013 および Visual Studio 2012 における、ワークフロー テンプレート、アクション、およびアクティビティの提供でのワークフロー作成者のビジネス要件を予測することに努力を費やしてきましたが、それぞれの人の特定のニーズを予測することはできません。そのため、Visual Studio 2012 では開発者がカスタム アクションを作成する、ワークフロー カスタム アクション アイテム タイプを用意しています。ワークフロー カスタム アクションについての詳細は、「 [[方法] ワークフローのカスタム アクションを作成および展開する](how-to-build-and-deploy-workflow-custom-actions.md)」を参照してください。
  
    
    

## SharePoint ワークフローのツール サポート
<a name="SP15Whatsnewinworflow_Tools"> </a>

Visual Studio 2012 は、SharePoint 2013 ワークフロー フレームワークでワークフローを作成するためのテンプレートおよびサポートを提供します。SharePoint 2013 ワークフローは、WF 4 によって動作し、Microsoft Azure 内で実行すること以外は以前のバージョンのワークフローと同様です。これらは宣言型のみで (XAML)、クラウドと対話し、SharePoint アドイン で動作するように設計されています。主な利点の 1 つは、ワークフローをリモートでホストし、SharePoint Server の外部からワークフローを実行できることです。
  
    
    

## 新しいワークフロー アクション
<a name="SP15Whatsnewinworflow_Newwfactions"> </a>

以下に SharePoint 2013 に用意された新しいワークフロー アクションを示します。新しいアクションおよび非推奨のアクションの詳細については、「 [SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス](workflow-actions-and-activities-reference-for-sharepoint-2013.md)」を参照してください。SharePoint 2013 のワークフローでは、Project 2013 に統合できプロジェクト ベースのワークフローを作成できるワークフロー アクションのセットが新しくなっています。
  
    
    

**表 1. SharePoint 2013 の新しいワークフロー アクション**


|**アクション**|**説明**|
|:-----|:-----|
|タスクの割り当て  <br/> |ユーザーまたはグループに単一のワークフロー タスクを割り当てます。  <br/> |
|タスク処理の開始  <br/> |タスク処理の実行を開始します。  <br/> |
|このステージに移動  <br/> |フロー制御を渡す必要があるワークフロー内の次のステージを指定します。  <br/> |
|HTTP Web サービスの呼び出し  <br/> |REST (Representational State Transfer) エンドポイントへのメソッド呼び出しとして機能します。  <br/> |
|リスト ワークフローの開始  <br/> |リストを範囲とするワークフローを開始します。  <br/> |
|サイト ワークフローの開始  <br/> |サイトを範囲とするワークフローを開始します。  <br/> |
|DynamicValue の構築  <br/> |**DynamicValue** 型の新しい変数を作成します。 <br/> |
|DynamicValue からプロパティを取得  <br/> |**DynamicValue** 型の指定された変数からプロパティ値を取得します。 <br/> |
|DynamicValue 内のアイテムをカウント  <br/> |**DynamicValue** 型の変数内の行数を返します。 <br/> |
|文字列のトリミング  <br/> |現在の文字列の先頭および末尾の空白文字をすべて削除します。  <br/> |
|文字列内のサブ文字列を検索  <br/> |文字列内の最初の 1 文字以上、または最初の文字列の 1 ベースのインデックスを返します。  <br/> |
|文字列内のサブ文字列を置換  <br/> |指定された文字または文字列のすべてを別の指定された文字または文字列に置き換えた新しい文字列を返します。  <br/> |
|ドキュメントの翻訳  <br/> |同期翻訳 API を呼び出す HTTP アクティビティを囲むラッパーとして機能します。ワークフローを実行する SharePoint サイトの Machine Translation Service Application を構成する必要があります。  <br/> |
|ワークフローの状態の設定  <br/> |ワークフローの状態をメッセージ文字列で指定されたように更新します。  <br/> |
|現在のアイテムからプロジェクトを作成 [Microsoft Project]  <br/> |現在のアイテムに基づいて Project Server プロジェクトを作成します。  <br/> |
|現在のプロジェクト ステージの状態をこの値に設定 [Microsoft Project]  <br/> |プロジェクトの現在のステージ内に 2 つの状態フィールドを設定します。  <br/> |
|アイデア リスト アイテムの状態フィールドをこの値に設定 [Microsoft Project]  <br/> |オリジナルの SharePoint リスト アイテムの状態フィールドを更新します。  <br/> |
|プロジェクト イベントを待機 [Microsoft Project]  <br/> |ワークフローの現在のインスタンスを停止し、指定したプロジェクト イベント (チェックインされたプロジェクト、コミットされたプロジェクト、提出されたプロジェクト) を待機します。  <br/> |
|プロジェクトのこのフィールドをこの値に設定 [Microsoft Project]  <br/> |エンタープライズ ユーザー設定フィールドの値を指定したプロジェクトに設定します。  <br/> |
   

## その他の技術情報
<a name="SP15Whatsnewinworflow_Addresources"> </a>


-  [SharePoint 2013 ワークフローの概要](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の開発者のための新機能](what’s-new-for-developers-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [ワークフロー アクション クイック リファレンス (SharePoint 2013 ワークフロー プラットフォーム)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  

