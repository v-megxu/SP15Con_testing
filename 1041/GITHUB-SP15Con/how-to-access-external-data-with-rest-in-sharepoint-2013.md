---
title: 方法 SharePoint 2013 で REST を使用して外部データにアクセスする
ms.prod: SHAREPOINT
ms.assetid: 0663cc8c-a736-434d-9858-6ce12ce7f748
---


# 方法: SharePoint 2013 で REST を使用して外部データにアクセスする
Business Connectivity Services (BCS) の Representational State Transfer (REST) URL を使用して、SharePoint 2013から外部データにアクセスする方法を説明します。
この記事では、Open Data Protocol (OData) ソースからデータを取得する外部リストを設定する方法を示します。
  
    
    


## REST を使用して外部データにアクセスするための前提条件
<a name="bkmk_Prerequisites"> </a>

REST を使用して SharePoint 2013から外部データにアクセスするには、次のものが必要です。
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2012
    
  
- 機能する SharePoint アドイン開発環境。「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」の手順に従ってください。
    
  
- パブリック OData.org Producer へのアクセス
    
  

### REST を使用した外部データへのアクセスに関する基本概念

SharePoint 2013の REST サービスは、特別に作成された URL を使用して外部データにアクセスする手段を提供します。REST サービスのしくみと使い方については、以下の記事を参照してください。
  
    
    

**表 1. SharePoint 2013の REST の基本概念**


|**記事のタイトル**|**説明**|
|:-----|:-----|
| [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md) <br/> |SharePoint 2013 REST サービスの使用方法を説明します。REST サービスは、既存のクライアント オブジェクト モデルに匹敵する REST プログラミング インターフェイスを提供します。  <br/> |
| [SharePoint 2013 REST サービスの概要](get-to-know-the-sharepoint-2013-rest-service.md) <br/> |SharePoint 2013 REST サービスで、REST および OData Web プロトコル標準を使用して SharePoint データにアクセスし、データを更新するための基本概念を説明します。  <br/> |
| [SharePoint 2013 REST サービスを使用する](e1ff2979-1c16-4cb0-a57e-9168dfe20a7c.md) <br/> |REST サービスで表される SharePoint 2013のデータ構造内を移動し、REST サービス経由で SharePoint アイテムに対する一般的な CRUD (作成、読み取り、更新、削除) 操作を実行し、アプリケーション間で SharePoint アイテムを同期し、アイテムを同時に制御する方法を説明します。  <br/> |
   

## REST を使用して外部データにアクセスする SharePoint アドインの作成
<a name="bkmk_CreateApp"> </a>

ここでは、REST の機能を使用して外部データ ソースからデータを取得する要求を行うために、SharePoint アドインを設定して Web ページを構成する手順を示します。
  
    
    

### SharePoint アドインを作成するには


1. Visual Studio 2012 を開きます。
    
  
2. **SharePoint 2013 用アプリ** プロジェクトを作成します。
    
  
3. アプリ名、アプリのデバッグ用のサイト URL、アプリをホストする方法 (自動ホスト、プロバイダー ホスト、SharePoint ホスト) など、アプリの設定を指定します。ホスティング オプションの詳細については、「 [SharePoint アドインを開発およびホスティングするためのパターンを選択する](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)」を参照してください。
    
  
4. [ **完了**] を選択してアプリを作成します。
    
  

### 外部コンテンツ タイプを生成するには


1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、[ **追加**]、[ **外部データ ソースのコンテンツ タイプ**] の順に選択します。
    
  
2. [ **OData ソースの指定**] ページで、接続先の OData サービスの URL を入力します。ここでは、 [http://www.odata.org/ecosystem](http://www.odata.org/ecosystem) で公開されている Northwind OData ソースを使用します。OData サービスの URL を `http://services.odata.org/Northwind/Northwind.svc/` に設定し、データ ソースの名前を入力します。
    
    [ **次へ**] を選択します。
    
  
3. OData サービスによって公開されているデータ エンティティのリストが表示されます。[ **Customers**] エンティティを選択します。[ **選択されたデータ エンティティのリスト インスタンスを作成します。**] チェック ボックスがオンになっていることを確認します。
    
  
4. [ **完了**] を選択します。
    
  

## コード例: Home.aspx ページにスクリプトと HTML を追加する
<a name="bkmk_AddUIelements"> </a>

ここまでの手順で、Netflix OData ソースからのデータを表示する外部コンテンツ タイプと外部リストが作成されました。 
  
    
    
次は、アプリの作成時に作成された default.aspx ページを変更します。ページの読み込みとともに実行されるクエリの結果を格納するコンテナーを追加します。ページ読み込みイベントに対してスクリプトを実行することで、ページが閲覧されるたびにスクリプトが実行されるようになり、それによって Northwind OData ソースへの REST 呼び出しが行われてページにレコードが追加されます。
  
    
    

### Default.aspx ページにコンテナーを追加するには


1. **ソリューション エクスプローラー**で、[ **Pages**] モジュールにある Default.aspx ページを開きます。
    
  
2. 次の **div** 要素をページに追加します。
    
  ```HTML
  
<div id="displayDiv"></div>
  ```

3. ページを保存します。
    
  
最後に、ページの読み込み時に実行される App.js ファイルにコードを追加します。
  
    
    

### REST 呼び出しを行うように App.js ファイルを変更するには


1. SharePoint プロジェクトの [Scripts] モジュールにある App.js ファイルを開きます。
    
  
2. ファイルの末尾に次のコードを貼り付けます。
    
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

F5 キーを押してアプリを SharePoint に展開します。アプリで Default.aspx ページを参照すると、顧客のリストがページに表示されます。
  
    
    

## その他のリソース
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 REST サービスの概要](get-to-know-the-sharepoint-2013-rest-service.md)
    
  
-  [SharePoint 2013 REST サービスを使用する](e1ff2979-1c16-4cb0-a57e-9168dfe20a7c.md)
    
  
-  [アドイン スコープの外部コンテンツ タイプ (SharePoint 2013)](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  

