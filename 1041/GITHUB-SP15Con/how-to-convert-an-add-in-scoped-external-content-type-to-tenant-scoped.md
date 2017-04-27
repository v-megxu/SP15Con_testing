---
title: 方法 アドイン スコープの外部コンテンツ タイプをテナント スコープに変換する
ms.prod: SHAREPOINT
ms.assetid: 35c5d670-e402-4641-b3c5-6f61ae1ec69b
---


# 方法: アドイン スコープの外部コンテンツ タイプをテナント スコープに変換する
Visual Studio 2012 自動生成ツールを使用して OData ベースの外部コンテンツ タイプを作成し、それをテナント ワークスペース全体で使用できるように Business Connectivity Services (BCS) メタデータ ストアにインポートする方法について説明します。
BDC モデルは、外部データ ソースの複雑な XML 定義です。BDC モデルは、BCS 用に外部コンテンツ タイプを定義するときに使用されます。BDC モデルは手動で作成するのが非常に難しいため、Visual Studio 2012 および Office Developer Tools for Visual Studio 2012 を使用してファイルを自動的に生成するツールが組み込まれています。このようなツールを使用すれば、Visual Studio の発行機能を使用して .app パッケージを作成し、そのパッケージを開いてモデル ファイルを抜き出すことができます。
  
    
    


## Visual Studio アドイン パッケージから BDC モデル ファイルを抜き出す

以下の手順では、OData ベースの外部コンテンツ タイプを作成し、それをテナント ワークスペース全体で使用できるように BCS メタデータ ストアにインポートする方法について説明します。
  
    
    

### OData ソースから BDC モデル ファイルを作成するには


1. Visual Studio 2012 で、 **SharePoint 2013 用アドイン**プロジェクトを作成します。
    
  
2. アドイン名、アドインをデバッグするサイトの URL、アドインをホストする方法 ( **自動的にホストする**、 **プロバイダーでホストする**、または **SharePoint でホストする**) など、アドインの設定を指定します。詳細については、「 [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)」を参照してください。
    
  
3. [ **完了**] を選択すると、アプリが作成されます。
    
  
4. [ **ソリューション エクスプローラー**] で、プロジェクトのショートカット メニューを開き、[ **追加**]、[ **外部データ ソースのコンテンツ タイプ**] の順に選択します。
    
    この操作により、選択したデータ ソースの検索と BDC モデルの作成を支援するウィザードが起動します。
    
  
5. [ **OData ソースの指定**] ページで、接続先の OData サービスの URL を入力します。この URL は  `http://services.odata.org/Northwind/Northwind.svc/` のような形式になります。
    
    OData ソースの名前を指定します。
    
    > **メモ**
      > この例では、 [Open Data Protocol の Web サイト](http://www.odata.org//)にあるプロデューサーの一覧から利用できる Northwind サービスを使用します。 
6. この OData サービスによって公開されているデータ エンティティを示す一覧が表示されます。1 つ以上のエンティティを選択し、[ **完了**] を選択します。
    
  

### アドインを対象範囲とする外部コンテンツ タイプをアドイン パッケージとして展開するには


1. Visual Studio の [ **ビルド**] メニューで、[ **発行**] を選択します。
    
  
2. パッケージに名前を付け、ローカル ハード ドライブの保存場所を指定し、[ **完了**] を選択します。
    
  

### .app パッケージからモデル ファイルを取り出すには


1. .app パッケージが作成されているフォルダーを開きます。
    
  
2.  ファイル名の拡張子を.app から.zip に変更します。
    
  
3. ZIP パッケージをローカル フォルダーに展開します。
    
  
4. 展開されたフォルダーを開き、WSP ファイルを探します。
    
  
5. WSP ファイルを別の場所に移動します。
    
  
6. このファイルの .wsp ファイル名拡張子を .cab に変更します。
    
  
7. .cab ファイルを開き、Bdcmodel.bdcm ファイルを探します。
    
  
8. Bdcmodel.bdcm ファイルを別の場所に保存します。
    
  

### SharePoint 全体管理ページを使用してモデル ファイルをインポートするには


1. SharePoint Online または SharePoint 2013 社内全体管理ページを開きます。
    
  
2. [ **サーバー アプリケーションの管理**] を選択します。
    
  
3. [ **Business Data Connectivity Service**] を選択します。
    
  
4. サーバーのリボンにある [ **インポート**] リンクを選択します。
    
  
5. [ **参照**] ボタンを選択して, .bdcm ファイルを展開した場所を指定します。
    
  
6. 既定の設定をそのまま使用し、[ **インポート**] を選択します。
    
  

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [方法: アドイン スコープの外部コンテンツ タイプを作成する (SharePoint 2013 )](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Open Data Protocol](http://www.odata.org)
    
  

  
    
    

