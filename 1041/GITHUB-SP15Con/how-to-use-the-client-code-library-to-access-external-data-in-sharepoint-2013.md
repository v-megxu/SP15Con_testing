---
title: [方法] SharePoint 2013 のクライアント コード ライブラリを使用して外部データにアクセスする
ms.prod: SHAREPOINT
ms.assetid: c280ae92-c52b-4658-b0f3-805fb215ef8e
---


# [方法] SharePoint 2013 のクライアント コード ライブラリを使用して外部データにアクセスする
ブラウザーベースのスクリプトを使用する SharePoint 2013で SharePoint 2013 クライアント オブジェクト モデルを使用して Business Connectivity Services (BCS) オブジェクトを処理する方法について学習します。
この記事は、SharePoint 2013でクライアント オブジェクト モデルを使用して OData (Open Data プロトコル) ソースからデータを取得する外部リストをセットアップする方法を示します。
  
    
    


## SharePoint 2013 クライアント オブジェクト モデルを使用して外部データにアクセスするための前提条件
<a name="bkmk_Prerequisites"> </a>

以下は、SharePoint クライアント オブジェクト モデルを使用してアプリを開発するための要件です。
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2012
    
  
- 機能している SharePoint アドイン 開発環境: 「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」の指示に従ってください。
    
  
- パブリック OData.org プロデューサーへのアクセス
    
  

### SharePoint 2013 クライアント オブジェクト モデルで外部データにアクセスする際に知っておく必要がある主な概念

SharePoint 2013 クライアント オブジェクト モデルは、サーバー側の API を模倣するクライアント側の呼び出しを使用して外部データにアクセスする手段を提供します。仕組みと使用方法については、表 1 で示されている記事を参照してください。
  
    
    

**表 1. クライアント オブジェクト モデルを使用するための主な概念**


|**記事**|**説明**|
|:-----|:-----|
| [SharePoint 2013 のクライアント ライブラリ コードを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx) <br/> |SharePoint 2013 .NET Framework クライアント オブジェクト モデル (CSOM) で基本操作を実行するコードを作成する方法を学習します。  <br/> |
   

## クライアント オブジェクト モデルを使用して外部データにアクセスする SharePoint アドインの作成
<a name="bkmk_CreateApp"> </a>

以下の手順は、クライアント オブジェクト モデルのメソッドとオブジェクトを使用して外部データ ソースからデータを取得する要求を作成するために SharePoint アドインをセットアップして Web ページを構成する方法を示しています。
  
    
    

### SharePoint アドインの作成


1. Visual Studio 2012 を開きます。
    
  
2. [ **App for SharePoint 2013 (SharePoint 2013 用アプリ)**] プロジェクトを作成します。
    
  
3. アプリ名、アプリをデバッグするためのサイト URL、アプリのホスト方法 (自動ホスト、プロバイダーホスト、SharePoint ホスト) を含むアプリ設定を指定します。ホスティング オプションの詳細については、「 [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)」を参照してください。
    
  
4. [ **完了**] をクリックしてアプリを作成します。
    
  

### 外部コンテンツ タイプを生成するには


1. **ソリューション エクスプローラー**でプロジェクトのショートカット メニューを開き、[ **追加**]、[ **Content types for External Data source (外部データ ソース用のコンテンツ タイプ)**] の順に選択します。
    
  
2. [ **Specify OData Source (OData ソースの指定)**] ウィザードで、接続先の OData サービスの URL を入力します。この例では、 [http://www.odata.org/ecosystem](http://www.odata.org/ecosystem) で公開されている Northwind OData ソースを使用します。OData サービスの URL を `http://services.odata.org/Northwind/Northwind.svc/` に設定してください。
    
    データ ソースの名前を指定し、[ **次へ**] をクリックします。
    
  
3. OData サービスによって露出されるエンティティのリストが表示されます。[ **Customers (顧客)**] エンティティーを選択してください。[ **Create list instances for the selected data entities (except Service Operations) (選択したデータ エンティティのリスト インスタンスの作成 (サービス操作を除く))**] チェックボックスがオンになっていることを確認してください。
    
  
4. [ **完了**] を選択します。
    
  

## コードの例: Default.aspx ページにスクリプトと HTML を追加する
<a name="bkmk_AddUIelements"> </a>

この時点で、Netflix OData ソースからのデータを表示する外部コンテンツ タイプと外部リストが存在するようになりました。 
  
    
    
次の目標は、アプリの作成時に作成した Default.aspx ページの変更です。ページのロード時に実行されるクエリの結果を保持するコンテナーを追加します。ページ ロード イベントでスクリプトを実行することにより、ページが参照されるたびにスクリプトが実行されることを保証します。結果のクライアント オブジェクト モデル呼び出しは Netflix OData ソースに対して出され、レコードをページに追加します。 
  
    
    

### コンテナーを Default.aspx ページに追加するには


1. **ソリューション エクスプローラー**で、[ **Pages (ページ)**] モジュールにある Default.aspx ページを開きます。
    
  
2. 次の **div** 要素をページに追加します。
    
  ```HTML
  
<div id="displayDiv"></div>
  ```

3. ページを保存します。
    
  
最後に、ページのロード時に実行される App.js ファイルにコードを追加します。
  
    
    

### クライアント オブジェクト モデル呼び出しを行うように App.js ファイルを変更するには


1. SharePoint プロジェクトの [Scripts (スクリプト)] モジュールで App.js ファイルを開きます。
    
  
2. 次のコードをファイルの終わりに貼り付けます。
    
  ```
  $(document).ready(function () {

    // Namespace
    window.AppLevelECT = window.AppLevelECT || {};

    // Constructor
    AppLevelECT.Grid = function (hostElement, surlWeb) {
        this.hostElement = hostElement;
        if (surlWeb.length > 0 &amp;&amp; surlWeb.substring(surlWeb.length - 1, surlWeb.length) != "/")
            surlWeb += "/";
        this.surlWeb = surlWeb;
    }

    // Prototype
    AppLevelECT.Grid.prototype = {

        init: function () {

            $.ajax({
                url: this.surlWeb + "_api/lists/getbytitle('Customer')/items?$select=BdcIdentity,CustomerID,ContactName",
                headers: {
                    "accept": "application/json",
                    "X-RequestDigest": $("#__REQUESTDIGEST").val()
                },
                success: this.showItems
            });
        },

        showItems: function (data) {
            var items = [];

            items.push("<table>");
            items.push('<tr><td>Customer ID</td><td>Customer Name</td></tr>');

            $.each(data.d.results, function (key, val) {
                items.push('<tr id="' + val.BdcIdentity + '"><td>' +
                    val.CustomerID + '</td><td>' +
                    val.ContactName + '</td></tr>');
            });

            items.push("</table>");

            $("#displayDiv").html(items.join(''));
        }
    }

    ExecuteOrDelayUntilScriptLoaded(getCustomers, "sp.js");
});

function getCustomers() {
    var grid = new AppLevelECT.Grid($("#displayDiv"), _spPageContextInfo.webServerRelativeUrl);
    grid.init();
}
  ```

F5 キーを押して、アプリを SharePoint に展開します。Default.aspx ページをアプリで参照すると、顧客リストがページに表示されます。
  
    
    

## その他の技術情報
<a name="bkmk_Addresources"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 BCS クライアント オブジェクト モデル リファレンス](bcs-client-object-model-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクライアント ライブラリ コードを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  

