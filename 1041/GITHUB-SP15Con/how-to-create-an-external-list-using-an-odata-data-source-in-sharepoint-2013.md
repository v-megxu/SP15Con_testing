---
title: [方法] SharePoint 2013 で OData データ ソースを使用して外部リストを作成する
ms.prod: SHAREPOINT
ms.assetid: 601fbfce-a0c6-43dd-8398-540d094c083c
---


# [方法] SharePoint 2013 で OData データ ソースを使用して外部リストを作成する
外部リストをプログラムによって作成し、SharePoint 2013 の OData ベースの外部コンテンツ タイプにバインドする方法を説明します。
パワー ユーザーや SharePoint 管理者は SharePoint Designer 2013 を使用して外部リストを作成する確率が高いですが、開発者は、自分が開発するツール (Visual Studio 2012 および Office Developer Tools for Visual Studio 2012) を使用して外部リストを作成する能力に関心があります。これにより開発者は、より柔軟に機能を追加し、1 つまたは多くのホスト環境へのその後の展開において Business Connectivity Services (BCS) の機能を組み込んだソリューションをパッケージングできます。
  
    
    


## 外部リストを作成する場合の前提条件
<a name="bkmk_Prereqs"> </a>

OData ソースから外部リストを作成するには、次のコンポーネントが必要です。
  
    
    

- Visual Studio 2012
    
  
- SharePoint 2013
    
  
- Office Developer Tools for Visual Studio 2012
    
  
- OData ソースに基づく公開外部コンテンツ タイプ: 指示については、「 [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)」を参照してください。
    
  
SharePoint 開発環境のセットアップの詳細については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」を参照してください。
  
    
    

### 外部リスト作成の中心概念

以降の記事では、SharePoint アドイン に関する情報と外部リストの作成に関する背景情報を提供します。
  
    
    

**表 1. 外部リストの中心概念**


|**記事のタイトル**|**説明**|
|:-----|:-----|
| [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |Business Connectivity Services と SharePoint 2013 での外部データの公開方法について説明します。  <br/> |
| [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |エンド ユーザー向けの小型で使いやすいソリューションであるアプリを作成するために使用できる SharePoint 2013 の新しいアプリ モデルについて説明します。  <br/> |
| [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx) <br/> |SharePoint アドイン のさまざまなホスト方法について説明します。  <br/> |
   

## 新しい外部リストの作成
<a name="bkmk_CreateNewVList"> </a>

次の手順は、新しい外部リストを作成し、そのリストを OData ベースの外部コンテンツ タイプにバインドし、Visual Studio 2012 を使用して SharePoint 2013 に公開する方法を示しています。
  
    
    

> **メモ**
> 最初の手順では、「 [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)」での説明に従って外部コンテンツ タイプが正常に作成されていることを想定しています。 
  
    
    


### 外部リストを自動的に追加するには


1. 外部コンテンツ タイプの内容を反映する簡単なリストをプロジェクトに追加する場合は、Visual Studio 2012 の自動生成ツールを使用できます。リストは、外部コンテンツ タイプの作成時に作成されます。自動生成プロセスの 2 番目のステップ ([データ エンティティの選択] ステップ) にある [ **選択したデータ エンティティのリスト インスタンスを作成する (サービスの操作を除く)**] チェック ボックスをオンにすると、ウィザードによって XML 宣言が作成され、選択したエンティティごとに新しい外部コンテンツ タイプが追加されます。
    
  
2. F5 を押してプロジェクトを展開します。新しいリストも展開されます。
    
  
テスト目的で AppManifest.xml ファイルを変更し、アプリの開始ページが、作成したリストとなるようにすることができます。 
  
    
    

### AppManifest.xml ファイルを変更するには


1. XML エディターを使用して AppManifest.xml ファイルを開きます。
    
  
2. <StartPage> タグを見つけます。
    
  
3. 値を  `~appWebUrl/Lists/Employees` に変更します。
    
  
4. 変更を保存します。
    
  

### プロジェクトを発行するには


- F5 を押してプロジェクトと外部リストを展開します。 
    
    Web ブラウザーを開き、作成した新しいリストに移動します。
    
  

## その他の技術情報
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [[方法]: 基本的な自動ホスト型 SharePoint 用アプリを作成する](http://msdn.microsoft.com/library/0572894d-c437-4b7d-8ac6-8405496e2145%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

