

# SharePoint アプリに SharePoint 2013 オブジェクト モデルを使用する

  
    
    
![概要情報トピック](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013のオブジェクト モデルを使用して高度なワークフロー開発シナリオをサポートする方法の概要を示します。
 * **適用対象:*** 
  
    
    


|||
|:-----|:-----|
|**この記事の内容**          [ワークフロー オブジェクト モデルの使用](#bk_usewfom)           [SharePoint 2013 ワークフロー: SharePoint アプリのワークフロー OM](#bk_codesample)           [その他の技術情報](#bk_addresources) <br/> |
  
    
    
![関連するコード スニペットおよびサンプル アプリ](images/mod_icon_links_samples.png)
  
    
    

  
    
    
 <br/>  [SharePoint 2013 workflow: Using the workflow object model in an app for SharePoint (英語)](http://code.msdn.microsoft.com/SharePoint-2013-workflow-050f5211) <br/> |
   

## ワークフロー オブジェクト モデルの使用
<a name="bk_usewfom"> </a>

SharePoint 2013の新しいワークフロー オブジェクト モデルは、新しい SharePoint ワークフロー プラットフォームの能力を活用するための高度なシナリオをサポートしています。このオブジェクト モデルを使用すると、ワークフローを展開してワークフロー インスタンスを管理できます。ワークフロー インスタンスへのメッセージングもサポートされます。
  
    
    
SharePoint 2013のワークフロー オブジェクト モデルはさまざまな形式で使用できます。管理 API である SharePoint Server オブジェクト モデル、クライアント オブジェクト モデル (または CSOM)、JavaScript オブジェクト モデル (JSOM) および SharePoint REST (Representational State Transfer) API があります。 
  
    
    
 SharePoint でホストされるアプリは、SharePoint JSOM および SharePoint REST API を使用してワークフロー オブジェクト モデルにアクセスできます。プロバイダーでホストされるアプリと自動的にホストされるアプリは、SharePoint JSOM および SharePoint REST API に加えて SharePoint CSOM を使用してワークフロー オブジェクト モデルにアクセスできます。これらのホスティング オプションの詳細については、「 [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)」を参照してください。
  
    
    
プログラミング タスクに最適な API を選択する方法の詳細については、「 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)」を参照してください。
  
    
    

## SharePoint 2013 ワークフロー: SharePoint アプリのワークフロー OM
<a name="bk_codesample"> </a>

コード サンプル「 **SharePoint 2013 ワークフロー: SharePoint アプリのワークフロー OM** 」は、SharePoint でホストされる対話式アプリの例です。これは、SharePoint ワークフロー JSOM を使用して、ワークフロー定義をアプリ Web と "親 Web" (つまり、アプリをホストしている SharePoint Web) に展開します。
  
    
    
このサンプル コードは、「 [SharePoint 2013 workflow: Workflow OM in a SharePoint app (英語)](http://code.msdn.microsoft.com/SharePoint-2013-workflow-050f5211)」にあります。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 ワークフローの概要](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 ワークフロー サンプル](sharepoint-2013-workflow-samples.md)
    
  
-  [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [Visual Studio を使用した SharePoint 2013 ワークフローの開発](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  