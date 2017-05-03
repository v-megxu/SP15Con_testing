

# SharePoint 用のワークフロー駆動型アプリの作成

  
    
    
![概要情報トピック](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013のワークフローの仕組みを取り込んだ SharePoint アドインの作成方法を簡単に紹介します。
 * **適用対象:**
  
    
    


|||
|:-----|:-----|
|**この記事の内容**   |   [コード例: ワークフロー駆動型 SharePoint アドイン](#WFappbk_sample)   <br/>   [その他の技術情報](#WFappbk_addres) <br/> |   ![関連するコード スニペットおよびサンプル アプリ](images/mod_icon_links_samples.png) <br/>  [SharePoint 2013 workflow: Build a workflow-powered app for SharePoint (英語)](http://code.msdn.microsoft.com/SharePoint-2013-workflow-580034f9) <br/> |
   

## コード例: ワークフロー駆動型 SharePoint アドイン
<a name="WFappbk_sample"> </a>


> **メモ**
> これは、現在のドキュメント リリースのために提供された暫定的な内容です。今後、情報の追加とサンプル コードの拡張で内容を充実させる予定です。 
  
    
    

このコード例では、SharePoint アドインと新しい SharePoint アドイン用のモデルに、SharePoint 2013のワークフローのための新しいフレームワークがどのように活用されているかを示しています。
  
    
    
ワークフローは、長期に使用されるビジネス ロジックの中間層として、あらゆるタイプの SharePoint アプリに使用できます。コード例には、Web にマーケティング情報を定期的に公開するためのドキュメント承認システムおよびワークフロー ロジックが含まれています。
  
    
    
この例は、SharePoint 2013 ワークフローを使用して、SharePoint がホストするシンプルなアプリを示しています。サンプルのアプリでは、以下のことを実演します。
  
    
    

- リスト アイテムが作成されると自動的にワークフローを開始する。
    
  
- リスト アイテムのイベントを待機し、リスンするワークフロー。
    
  
- リスト アイテムを作成するワークフロー。
    
  
-  _List Id_ トークンを使用して、ワークフローのポータブル化を図る。
    
  
このサンプル コードはこのサイトで入手できます。 [SharePoint 2013 workflow: Workflow-powered app for SharePoint (英語)](http://code.msdn.microsoft.com/SharePoint-2013-workflow-580034f9) (http://code.msdn.microsoft.com/SharePoint-2013-workflow-580034f9) (英語)
  
    
    

## その他の技術情報
<a name="WFappbk_addres"> </a>


-  [SharePoint 2013 ワークフロー サンプル](sharepoint-2013-workflow-samples.md)
    
  
-  [SharePoint 2013 ワークフローのアクションとアクティビティのリファレンス](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    