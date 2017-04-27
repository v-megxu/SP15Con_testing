---
title: SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要
ms.prod: SHAREPOINT
ms.assetid: 8ed91929-fdb6-4fde-ba2a-7942870575f3
---



# SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要
SharePoint 2013 クライアント オブジェクト モデルを使用して SharePoint 2013 で Business Connectivity Services (BCS) を操作する方法を説明します。
## SharePoint 2013 クライアント オブジェクト モデルとは


|||
|:-----|:-----|
|SharePoint 2013 のクライアント オブジェクト モデルは、サーバー オブジェクト モデルを表すクライアントベース ライブラリ セットです。多様な開発のタイプに合わせて、3 種類の DLL にパッケージ化されています。クライアント オブジェクト モデルには、サーバー API の主要な機能のほとんどが含まれています。そのため、ブラウザー スクリプト, .NET Web アプリケーション、および Silverlight アプリケーションからも同じ種類の機能にアクセスできます。  <br/> 外部データを操作する機能を強化および拡張するために、Business Connectivity Services (BCS) ではクライアント オブジェクト モデルが拡張され、機能が追加されました。  <br/>  [![設定開始](images/mod_icon_getstartbox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_getstarted) [![開始](images/mod_icon_dobox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_Tasks) [![詳細を見る](images/mod_icon_startbox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_Learnmore) <br/> ||
   

## SharePoint 2013 クライアント オブジェクト モデルと外部データの使用方法の概要
<a name="BCScsom_getstarted"> </a>

SharePoint クライアント オブジェクト モデル (CSOM) を使用してソリューションを開発するには、以下が必要です。
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2012
    
  
開発環境をセットアップする方法については、「 [SharePoint 2013 の BCS 開発環境のセットアップ](setting-up-a-development-environment-for-bcs-in-sharepoint-2013.md)」を参照してください。
  
    
    
クライアント オブジェクト モデルが提供する機能にアクセスするために必要なことは、プロジェクトで **Microsoft.SharePoint.Client.Runtime.dll** ファイルと **Microsoft.SharePoint.Client.dll** ファイルへの参照を追加することだけです。また、グローバル アセンブリ キャッシュの次のような DLL を参照して、クライアント オブジェクト モデルを使用することもできます。
  
    
    

-  `\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\isapi\\Microsoft.SharePoint.Client.Runtime.dll`
    
  
-  `\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\isapi\\Microsoft.SharePoint.Client.dll`
    
  

### SharePoint 2013 クライアント オブジェクト モデルの要点

SharePoint 2013 のクライアント オブジェクト モデルの詳細については、次の記事を参照してください。
  
    
    

**表 1. クライアント オブジェクト モデルを理解するための中心的な概念**


|**記事**|**説明**|
|:-----|:-----|
| [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md) <br/> |外部コンテンツ タイプによって実現できる処理、および SharePoint 2013 で外部コンテンツ タイプの作成を始めるための必要事項を説明します。  <br/> |
| [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |OData ソースに基づいて外部コンテンツ タイプを作成し、そのデータを SharePoint 2013 コンポーネントまたは Office 2013 コンポーネントで使用する方法の概要を説明します。  <br/> |
| [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md) <br/> |サーバー オブジェクト モデル、多様なクライアント オブジェクト モデル、REST/OData web サービスなど、SharePoint 2013 で提供されている API の一部について説明します。  <br/> |
| [SharePoint 2013 .NET クライアント API リファレンス](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx) <br/> |ここでは、SharePoint 2013の .NET クライアント クラス ライブラリに関する情報を入手できます。  <br/> |
| [SharePoint 2013 JavaScript API リファレンス](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx) <br/> |ここでは、SharePoint 2013における JavaScript オブジェクト ライブラリに関する情報を入手できます。  <br/> |
   

## クライアント オブジェクト モデルによって実現できる処理
<a name="BCScsom_Tasks"> </a>

SharePoint クライアント オブジェクト モデルを使用すると、SharePoint 2013 に含まれるデータを取得、更新、および管理できます。SharePoint は、さまざまな形式でクライアント ライブラリを提供しているため、ほとんどの開発者にご利用いただけます。スクリプト言語を使用している Web 開発者の場合、JavaScript でクライアント ライブラリが提供されています。.NET 開発者の場合, .NET クライアント管理 DLL として提供されています。Silverlight アプリケーションの開発者の場合、クライアント ライブラリは Silverlight DLL で提供されています。
  
    
    
SharePoint 2013 のクライアント オブジェクト モデルを使用して実現できる処理の詳細については、表 2 の記事を参照してください。
  
    
    

**表 2. クライアント オブジェクト モデルと外部データを使用するための基本的なタスク**


|**タスク**|**説明**|
|:-----|:-----|
| [SharePoint 2013 のクライアント ライブラリ コードを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx) <br/> |SharePoint 2013 クライアント オブジェクト モデルを使用して基本的な操作を実行するコードを記述する方法を説明します。  <br/> |
| [[方法] SharePoint 2013 のクライアント コード ライブラリを使用して外部データにアクセスする](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |SharePoint 2013 クライアント オブジェクト モデルを使用して、ブラウザーベースのスクリプトを使用して BCS を操作する方法を説明します。  <br/> |
   
次に、CSOM を使用して実現できるタスクの基本的な例をいくつか示します。
  
    
    

### 特定のエンティティを取得する

この例は、SharePoint からコンテキストを取得し、指定したデータ ソース エンティティを取得する方法を示しています。
  
    
    

```cs

ClientContext ctx = new ClientContext("http://sharepointservername"); 
Web web = ctx.Web; 
ctx.Load(web); 
Entity entity = ctx.Web.GetEntity("http://sharepointservername", "EntityName"); 
ctx.Load(entity); 
ctx.ExecuteQuery(); 

```


### 汎用的な呼び出し元を作成する

この例は、コード内で動作するエンティティ オブジェクトを作成できるように汎用的な呼び出し元を作成する方法を示しています。
  
    
    

```cs

ObjectCollection myObj; 
entity.Execute("MethodInstanceName", lsi, myObj); 
ctx.Load(myObj); 
ctx.ExecuteQuery(); 

```


### ページ化された結果セットを取得する

次の例は、フィルターされ、ページ化されたデータセットを取得する方法を示しています。この場合、ページ値は 50 です。
  
    
    

```cs

// Find filters for given Method Name. 
FilterCollection fCollection = entity.GetFilters("methodName"); 
ctx.Load(fCollection); 
ctx.ExecuteQuery(); 
FilterCollection modifiedFCollection = new FilterCollection(); 
foreach( Filter filter in fCollection) 
{ 
    if( filter.FilterField.equals("X.Y.Z.Country")) 
    { 
        filter.FilterValue = "India"; 
        modifiedFCollection.Add(Filter); 
    } 
    if(filter.FilterType == FilterType.Limit) 
    { 
        filter.FilterValue = 50; 
        modifiedFCollection.Add(Filter); 
    } 
} 
EntityInstanceCollection eCollection = entity.FindFiltered(modifiedFCollection, 
"nameOfFinder", lsi); 
ctx.ExecuteQuery(); 

```


### フィルターされた情報のクエリ

次の例は、フィルターされた結果セットを返す方法を示しています。この場合、フィルターされるデータ列は **X.Y.Z.Country** フィードです。"India" という値が含まれるデータが検索され、コレクションに格納されます。
  
    
    

```cs

// Find filters for given Method Name. 
FilterCollection fCollection = entity.GetFilters("methodName"); 
ctx.Load(fCollection); 
ctx.ExecuteQuery(); 
FilterCollection modifiedFCollection = new FilterCollection(); 
foreach( Filter filter in fCollection) 
{ 
    if( filter.FilterField.equals("X.Y.Z.Country")) 
    { 
        filter.FilterValue = "India"; 
        modifiedFCollection.Add(Filter); 
    } 
} 
EntityInstanceCollection eCollection = entity.FindFiltered(modifiedFCollection, 
"nameOfFinder", lsi); 
ctx.ExecuteQuery(); 

```


## 次の手順: クライアント オブジェクト モデルについての理解を深める
<a name="BCScsom_Learnmore"> </a>

SharePoint 2013 でクライアント オブジェクト モデルを使用する方法の詳細については、表 3 を参照してください。
  
    
    

**表 3. クライアント オブジェクト モデルの高度な概念**


|**記事**|**説明**|
|:-----|:-----|
| [SharePoint 2013 BCS クライアント オブジェクト モデル リファレンス](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |SharePoint 2013 クライアント オブジェクト モデルを使用してクライアント側スクリプトを作成し、BCS で公開されている外部データにアクセスするために使用できるオブジェクトについてまとめています。  <br/> |
   

## その他の技術情報
<a name="BCScsom_Learnmore"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [[方法] SharePoint 2013 のクライアント コード ライブラリを使用して外部データにアクセスする](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクライアント ライブラリ コードを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [SharePoint 2013: CSOM を使用した複雑な外部コンテンツ タイプへのアクセス](http://code.msdn.microsoft.com/office/SharePoint-2013-Accessing-ccbc24cf)
    
  
