---
title: 方法 アドイン スコープの外部コンテンツ タイプを作成する (SharePoint 2013 )
ms.prod: SHAREPOINT
ms.assetid: de4b50a3-84da-48ce-9ba0-fe06571e52a8
---


# 方法: アドイン スコープの外部コンテンツ タイプを作成する (SharePoint 2013 )
SharePoint アドインでのインストール、セキュリティ保護、および使用が可能な外部コンテンツ タイプの作成方法について説明します。
## アドインを対象範囲とする外部コンテンツ タイプを開発するための前提条件
<a name="bkmk_Prerequisites"> </a>

アドインを対象範囲とする外部コンテンツ タイプの開発を開始するには、以下が必要です。
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2012
    
  
- インターネットで使用可能な公開された OData サービス
    
  
SharePoint 展開環境のセットアップの詳細については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」を参照してください。
  
    
    

## アドインを対象範囲とする外部コンテンツ タイプを作成する
<a name="bkmk_CreateECT"> </a>

以下の手順は、Open Data Protocol (OData) ソースに基づいて外部コンテンツ タイプを作成する方法、またスコープが SharePoint アドインに設定されるように外部コンテンツ タイプを変更する方法を示しています。
  
    
    

### 新しい SharePoint アドインを作成するには


1. Visual Studio 2012 を開きます。
    
  
2. [ **Add-in for SharePoint 2013**] プロジェクトを作成します。
    
  
3. アドイン名、アドインをデバッグするためのサイト URL、アドインの任意のホスト方法 (自動ホスト、プロバイダーによるホスト、または SharePoint によるホスト) など、アドインの設定を指定します。詳細については、「 [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)」を参照してください。
    
  
4. [ **完了**] を選択すると、アプリが作成されます。
    
  
SharePoint アドインを作成するためのすべての手順については、次のトピックを参照してください。
  
    
    

-  [プロバイダー ホスト型 SharePoint アドインの作成を始める](http://msdn.microsoft.com/library/3038dd73-41ee-436f-8c78-ef8e6869bf7b%28Office.15%29.aspx)
    
  
-  [[方法]: 基本的な自動ホスト型 SharePoint 用アプリを作成する](http://msdn.microsoft.com/library/0572894d-c437-4b7d-8ac6-8405496e2145%28Office.15%29.aspx)
    
  
-  [SharePoint ホスト型の SharePoint アドインの作成を始める](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx)
    
  

### 外部コンテンツ タイプを生成するには


1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、[ **追加**]、[ **外部データ ソースのコンテンツ タイプ**] の順に選択します。
    
    この操作により、選択したデータ ソースの検索と BDC モデルの作成を支援するウィザードが起動します。
    
  
2. [ **OData ソースの指定**] ページで、接続先の OData サービスの URL を入力します。この URL は  `http://services.odata.org/Northwind/Northwind.svc/` のような形式になります。
    
    OData ソースの名前を指定します。
    
    > **メモ**
      > この例では、 [Open Data Protocol の Web サイト](http://www.odata.org//)にあるプロデューサーの一覧から利用できる Northwind サービスを使用します。 
3. この OData サービスによって公開されているデータ エンティティを示す一覧が表示されます。1 つ以上のエンティティを選択し、[ **完了**] を選択します。
    
  

### アドインを対象範囲とする外部コンテンツ タイプを展開するには


- F5 キーを押すと、プロジェクトがコンパイルされ、プロジェクト ファイルが SharePoint にアップロードされます。
    
  

## その他の技術情報
<a name="bk_addresources"> </a>


-  [アドイン スコープの外部コンテンツ タイプ (SharePoint 2013)](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
    
  
-  [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  

