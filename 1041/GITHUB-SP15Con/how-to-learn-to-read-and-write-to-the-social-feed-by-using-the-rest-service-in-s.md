---
title: [方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う
ms.prod: SHAREPOINT
ms.assetid: 1da8d484-3666-42c3-8a8f-8b3ef93e96e9
---


# [方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う
REST サービスを使用して、現在のユーザーの投稿を公開し、個人フィードを取得する、SharePoint でホストされるアプリを作成します。
## SharePoint 2013 REST サービスを使用して、投稿を公開し、ソーシャル フィードを取得する、SharePoint でホストされる SharePoint アドインを作成する際の前提条件
<a name="bkmk_Prereqs"> </a>

この記事では、Office 365 開発者向けサイトで Napaを使用して SharePoint アドインを作成するものとしています。この開発環境を使用している場合は、すでに前提条件を満たしています。
  
    
    

> **メモ**
> 「 [Office 365 開発者向けサイトにサインアップする](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx)」にアクセスして、開発者向けサイトにサインアップする方法、および Napaの使用を開始する方法を確認します。 
  
    
    

開発者向けサイトの Napaを使用していない場合、次のツールが必要です。
  
    
    

- 個人用サイトを構成済みの SharePoint Server 2013、および現在のユーザー向けに作成した個人用サイト
    
  
- Visual Studio 2012 および Office Developer Tools for Visual Studio 2013
    
  
- ログオン ユーザーに対する、User Profile Service アプリケーションへの **フル コントロール** アクセス許可
    
  

> **メモ**
> ニーズに合った開発環境をセットアップする方法については、「 [Office 用アプリおよび SharePoint 用アプリの作成を開始する](http://msdn.microsoft.com/library/187f8c8c-1b15-471c-80b5-69a40e67deea%28Office.15%29.aspx)」を参照してください。 
  
    
    


## SharePoint 2013 のソーシャル フィードの操作に関する重要な概念
<a name="bkmk_CoreConcepts"> </a>

この記事で作成する、SharePoint でホストされるアプリは、JavaScript を使用して、Representational State Transfer (REST) エンドポイントに HTTP 要求を作成および送信します。この要求によって、現在のユーザーの投稿を公開し、個人フィードを取得します。表 1 は、作業を開始する前に理解しておく必要がある一般的な概念を説明する記事へのリンクをまとめたものです。
  
    
    

**表 1. SharePoint 2013 のソーシャル フィードの操作に関する重要な概念**


|**記事のタイトル**|**説明**|
|:-----|:-----|
| [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |SharePoint アドインおよび、その作成に関する基本的な概念について説明しています。  <br/> |
| [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md) <br/> | のソーシャル フィードとマイクロブログの投稿を使用したプログラミングを開始し、ユーザーやコンテンツ (ドキュメント、サイト、およびタグ) のフォローや、ユーザー プロファイルの操作を行う方法を説明しています。 <br/> |
| [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md) <br/> |ソーシャル フィードを操作するための一般的なプログラミング作業と、そうした作業の実行に使用する API について説明しています。  <br/> |
   

## SharePoint アドイン プロジェクトを作成する
<a name="bkmk_CreateApp"> </a>


1. 開発者向けサイトで、Napaを開き、[ **新しいプロジェクトの追加**] をクリックします。
    
  
2. [ **SharePoint 用アプリ**] テンプレートを選択して、プロジェクトに「SocialFeedREST」という名前を付けてから [ **作成**] をクリックします。
    
  
3. 次のようにして、アプリに必要なアクセス許可を指定します。
    
1. ページの下部にある [ **プロパティ**] をクリックします。 
    
  
2. [ **プロパティ**] ウィンドウで、[ **Permissions**] をクリックします。
    
  
3. [ **コンテンツ**] カテゴリで、[ **テナント**] スコープに **Write** 権限を設定します。
    
  
4. [ **ソーシャル**] カテゴリで、[ **ユーザー プロファイル**] スコープに **Read** 権限を設定します。
    
  
5. [ **プロパティ**] ウィンドウを閉じます。
    
  
4. [ **スクリプト**] ノードを展開して、App.js ファイルを選択し、ファイルの内容を削除します。
    
  

## SharePoint 2013 REST サービスを使用して、ソーシャル フィードに投稿する
<a name="bkmk_PubPost"> </a>


1. App.js ファイルでは、 **SocialFeedManager** エンドポイントの URL 用にグローバル変数を宣言します。
    
  ```
  
var feedManagerEndpoint;
  ```

2. 次のコードを追加します。このコードでは、クエリ文字列から **SPAppWebUrl** パラメーターを取得し、それを使用して **SocialFeedManager** エンドポイントを構築します。
    
  ```
  $(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    feedManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.feed";
    postToMyFeed();
});
  ```

3. 次のコードを追加します。このコードでは、 `/my/Feed/Post` エンドポイントへの HTTP **POST** 要求を構築し、投稿の作成データを定義して、投稿を公開します。
    
    この要求では、要求本文で **SocialRestPostCreationData** リソースを送信します。 **SocialRestPostCreationData** には、投稿の対象 (この場合、現在のユーザーの最初の投稿を指定する `null`) および、投稿のプロパティを定義する **SocialPostCreationData** 複合型が含まれます。
    


  ```
  
function postToMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed/Post",
        type: "POST",
        data: JSON.stringify( { 
            'restCreationData':{
                '__metadata':{ 
                    'type':'SP.Social.SocialRestPostCreationData'
                },
                'ID':null, 
                'creationData':{ 
                    '__metadata':{ 
                        'type':'SP.Social.SocialPostCreationData'
                    },
                'ContentText':'This post was published using REST.',
                'UpdateStatusText':false
                } 
            } 
        }),
        headers: { 
            "accept": "application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest": $("#__REQUESTDIGEST").val()
        },
        success: getMyFeed,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("POST error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });
}

  ```


## SharePoint 2013 REST サービスを使用して、現在のユーザーのソーシャル フィードを取得する
<a name="bkmk_GetFeed"> </a>

次のコードを追加します。このコードでは、 `/my/Feed` エンドポイントを使用して、現在のユーザーの **Personal** フィード タイプを取得します。 **accept** ヘッダーでは、サーバーがフィードの JavaScript Object Notation (JSON) 表現を応答で返すように要求しています。
  
    
    

```

function getMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: feedRetrieved,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("GET error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });    
}

```


## SharePoint 2013 REST サービスを使用して、ソーシャル フィードを反復処理して読み取る
<a name="bkmk_ReadFeed"> </a>

次のコードを追加します。このコードでは、 **JSON.stringify** 関数および **JSON.parse** 関数を使用して、返されたデータを準備してから、フィードを反復処理して、スレッドの所有者および最初の投稿のテキストを取得します。
  
    
    

```

function feedRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
 
    var feed = jsonObject.d.SocialFeed.Threads; 
    var threads = feed.results;
    var feedContent = "";
    for (var i = 0; i < threads.length; i++) {
        var thread = threads[i];
        var participants = thread.Actors;
        var owner = participants.results[thread.OwnerIndex].Name;
        feedContent += '<p>' + owner + 
            ' said "' + thread.RootPost.Text + '"</p>';
    }  
    $("#message").html(feedContent); 
}
```


## 開発者向けサイトで SharePoint 用アプリを実行する
<a name="bkmk_ReadFeed"> </a>


1. アプリを実行するには、ページの下部で [ **Run Project**] をクリックします。 
    
  
2. 開いた [ **Do you trust**] ページで、[ **Trust It**] をクリックします。アプリ ページが開き、所有者の名前が表示され、フィード内にある最初の投稿のそれぞれについてテキストが表示されます。
    
  

  
    
    

## コード例: SharePoint 2013 REST サービスを使用して、現在のユーザーの投稿を公開し、フィードを取得する
<a name="bkmk_PubPosts1"> </a>

以下に、App.js ファイルの完全なコード例を示します。このコード例では、現在のユーザーの投稿を公開し、個人フィードを取得します。個人フィードは JSON オブジェクトとして返されます。その後、フィードを反復処理します。
  
    
    

```

var feedManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the feed manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    feedManagerEndpoint = decodeURIComponent(appweburl)+ "/_api/social.feed";
    postToMyFeed();
});

// Publish a post to the current user's feed by using the 
// "<app web URL>/_api/social.feed/my/Feed/Post" endpoint.
function postToMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed/Post",
        type: "POST",
        data: JSON.stringify( { 
            'restCreationData':{
                '__metadata':{ 
                    'type':'SP.Social.SocialRestPostCreationData'
                },
                'ID':null, 
                'creationData':{ 
                    '__metadata':{ 
                        'type':'SP.Social.SocialPostCreationData'
                    },
                'ContentText':'This post was published using REST.',
                'UpdateStatusText':false
                } 
            } 
        }),
        headers: { 
            "accept": "application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest": $("#__REQUESTDIGEST").val()
        },
        success: getMyFeed,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("POST error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });
}

// Get the current user's feed by using the 
// "<app web URL>/_api/social.feed/my/Feed" endpoint.
function getMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: feedRetrieved,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("GET error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });    
}

// Parse the JSON data and iterate through the feed.
function feedRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
 
    var feed = jsonObject.d.SocialFeed.Threads; 
    var threads = feed.results;
    var feedContent = "";
    for (var i = 0; i < threads.length; i++) {
        var thread = threads[i];
        var participants = thread.Actors;
        var owner = participants.results[thread.OwnerIndex].Name;
        feedContent += '<p>' + owner + 
            ' said "' + thread.RootPost.Text + '"</p>';
    }  
    $("#message").html(feedContent); 
}
```


## 次の手順
<a name="bkmk_PubPosts1"> </a>

ソーシャル機能へのアクセスに使用できるその他の REST エンドポイントについては、「 [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)」および「 [SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)」を参照してください。
  
    
    

## その他の技術情報
<a name="bk_addResources"> </a>


-  [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  

