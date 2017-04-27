---
title: SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法
ms.prod: SHAREPOINT
ms.assetid: 989a5873-49f9-49e4-8d0f-439dde891cc2
---


# SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法
REST サービスを使用して、コンテンツ (ドキュメント、サイト、タグ) をフォローし、フォローされているコンテンツを取得する、SharePoint でホストされるアプリを作成します。
## SharePoint Server 2013 REST サービスを使用してコンテンツをフォローする方法
<a name="bk_intro"> </a>

SharePoint Server 2013 ユーザーはドキュメント、サイト、タグをフォローして、ニュースフィードのアイテムに関する更新を取得し、フォローされているドキュメントやサイトをすばやく開くことができます。アプリまたはソリューションで SharePoint Server 2013 REST API を使用して、現在のユーザーの代わりに、コンテンツのフォローを開始したり、コンテンツのフォローを停止したり、フォローされているコンテンツを取得したりすることができます。
  
    
    
次の REST リソースはコンテンツのフォロー タスク用の主要な API です。
  
    
    

- **SocialRestFollowingManager** は、フォローされているアクターのユーザーのリストを管理するためのメソッドを提供します。
    
  
- **SocialActor** は、サーバーがクライアント側要求への応答で返すドキュメント、サイト、またはタグを表します。
    
  
- **SocialActorInfo** は、サーバーへのクライアント側要求にドキュメント、サイト、またはタグを指定します。
    
  
- **SocialActorType** と **SocialActorTypes** はサーバーへのクライアント側要求内にコンテンツ タイプを指定します。
    
  
REST API を使用して、コンテンツのフォロー タスクを実行するには、HTTP **GET** 要求と HTTP **POST** 要求を REST サービスに送信します。コンテンツのフォロー タスクの REST エンドポイント URI は、 **SocialRestFollowingManager** リソース ( `<siteUri>/_api/social.following`) で始まり、次のいずれかのリソースで終わります。
  
    
    

- **follow** はドキュメント、サイト、またはタグのフォローを開始します
    
  
- **stopfollowing** はドキュメント、サイト、またはタグのフォローを停止します
    
  
- **isfollowed** は、ユーザーが特定のドキュメント、サイト、またはタグをフォローしているかどうかを調べます
    
  
- **my/followed** はドキュメント、サイト、タグをフォローさせます
    
  
- **my/followedcount** はフォローされているドキュメント、サイト、タグのカウントを取得します
    
  

> **メモ**
> さらに、ユーザー フォロー タスクにもこれらのエンドポイントを使用しますが、 **SocialRestFollowingManager** から使用可能な **followers** リソースと **suggestions** リソースは、ユーザーのフォローのみをサポートし、コンテンツのフォローはサポートしません。 **SocialRestFollowingManager** の使用方法の詳細については、「 [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)」および「 [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)」を参照してください。 
  
    
    


## SharePoint 2013 REST サービスを使用して、フォローされているコンテンツを管理する、SharePoint でホストされるアプリケーションを作成するための前提条件
<a name="bkmk_Prereqs"> </a>

この記事では、Office 365 開発者向けサイトで Napaを使用して SharePoint アドインを作成するものとしています。この開発環境を使用している場合は、すでに前提条件を満たしています。
  
    
    

> **メモ**
> 「 [Office 365 開発者向けサイトにサインアップする](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx)」に移動して、開発者向けサイトにサインアップし、Napaの使用を開始します。 
  
    
    

Office 365 開発者向けサイトで Napaを使用していない場合は、SharePoint アドインを展開する前に、次の前提条件を満たす必要があります。
  
    
    

- アプリの分離用に構成された SharePoint 2013 開発環境。リモートで開発している場合は、サーバーでアプリのサイドローディングをサポートしているか、開発者向けサイトにアプリをインストールする必要があります。
    
  
- 個人用サイト ホストが構成されており、現在のユーザーの個人用サイトが作成されている。
    
  
- Office Developer Tools for Visual Studio 2013 を含む Visual Studio 2012 または Visual Studio 2013。
    
  
- ログオン ユーザーの次の十分なアクセス許可。
    
  - 開発用コンピュータのローカル管理者権限。
    
  
  - アプリをインストールする SharePoint サイトへの Web サイトの管理およびサブサイトの作成ユーザー権限。既定でこれらの権限は、フル コントロール権限レベルを持つか、サイト所有者グループに属するユーザーにのみ使用できます。
    
  
  - システム アカウント以外の誰かとしてログオンする必要があります。システム アカウントにはアプリをインストールする権限がありません。
    
  

> **メモ**
> オンプレミスの設定 (必要に応じてループバック チェックを無効にする方法を含む) に関するガイダンスについては、「 [SharePoint アドインのオンプレミスの開発環境をセットアップする](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)」を参照してください。 
  
    
    


  
    
    

## SharePoint アドイン プロジェクトを作成する
<a name="bkmk_CreateApp"> </a>


1. 開発者向けサイトで、Napaを開き、[ **新しいプロジェクトの追加**] を選択します。
    
  
2. [ **SharePoint 用アプリ**] テンプレートを選択し、プロジェクトに名前を付けて、[ **作成**] ボタンを選択します。
    
  
3. アプリの権限を設定します。
    
1. ページの下部の [ **プロパティ**] ボタンを選択します。
    
  
2. [ **プロパティ**] ウィンドウで、[ **アクセス許可**] を選択します。
    
  
3. [ **コンテンツ**] カテゴリで、[ **テナント**] スコープに **Write** 権限を設定します。
    
  
4. [ **ソーシャル**] カテゴリで、[ **ユーザー プロファイル**] スコープに **Read** 権限を設定します。
    
  
5. [ **プロパティ**] ウィンドウを閉じます。
    
  
4. [ **スクリプト**] ノードを展開し、App.js ファイルを選択して、その内容を次のいずれかのシナリオのコードで置き換えます。
    
  -  [ドキュメントのフォローを開始し、フォローを停止する](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowDocs)
    
  
  -  [サイトのフォローを開始し、フォローを停止する](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowSites)
    
  
  -  [タグのフォローを開始し、フォローを停止する](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowTags)
    
  
  -  [フォローされているコンテンツを取得する](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_GetFollowed)
    
  
5. アプリを実行するには、ページの下部で [ **プロジェクトの実行**] ボタンをクリックします。
    
  
6. 開いた [ **信頼しますか**] ページで、[ **信頼する**] ボタンを選択します。 アプリ ページが開き、コードが実行されます。ページをデバッグするには、 **F12** キーを選択し、[ **スクリプト**] タブの App.js を選択します。
    
  

## コード例: SharePoint 2013 REST サービスを使用して、ドキュメントのフォローを開始し、フォローを停止する
<a name="bkmk_FollowDocs"> </a>

次のコード例に、App.js ファイルの内容と次の操作方法を示します。
  
    
    

- クエリ文字列からアプリの Web URI を取得し、 `<siteUri>/_api/social.following` エンドポイント URI を作成します。
    
  
- **POST** 要求を作成し、 `isfollowed` エンドポイントに送信して、現在のユーザーが指定したドキュメントを既にフォローしているかどうかを調べます。
    
  
- **POST** 要求を作成し、 `follow` エンドポイントに送信して、ドキュメントのフォローを開始します。
    
  
- **POST** 要求を作成し、 `stopfollowing` エンドポイントに送信して、ドキュメントのフォローを停止します。
    
  
-  `isfollowed` 要求と `follow` 要求によって返された JSON 応答を読み取ります ( `stopfollowing` 要求は応答で何も返しません)。 [JSON 応答の例](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)を参照してください。
    
  
コードを実行する前に、ドキュメントをアップロードし、 **documentUrl** 変数のプレースホルダー値をドキュメントの URL に変更する必要があります。
  
    
    



```

// Replace the documentUrl placeholder value before you run the code.
var documentUrl = "https://domain.sharepoint.com/Shared%20Documents/fileName.docx";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the document.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the document.');
                stopFollowDocument();
            }
            else {
                alert('The user is currently NOT following the document.');
                followDocument();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a document.
// The request body includes a SocialActorInfo object that represents
// the document to follow.
// The success function reads the response from the REST service.
function followDocument() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the document. ',
                1 : 'The user is already following the document. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a document.
// The request body includes a SocialActorInfo object that represents
// the document to stop following.
function stopFollowDocument() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the document.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## コード例: SharePoint 2013 REST サービスを使用して、サイトのフォローを開始し、フォローを停止する
<a name="bkmk_FollowSites"> </a>

次のコード例に、App.js ファイルの内容と次の操作方法を示します。
  
    
    

- クエリ文字列からアプリの Web URI を取得し、 `<siteUri>/_api/social.following` エンドポイント URI を作成します。
    
  
- **POST** 要求を作成し、 `isfollowed` エンドポイントに送信して、現在のユーザーが指定したサイトを既にフォローしているかどうかを調べます。
    
  
- **POST** 要求を作成し、 `follow` エンドポイントに送信して、サイトのフォローを開始します。
    
  
- **POST** 要求を作成し、 `stopfollowing` エンドポイントに送信して、サイトのフォローを停止します。
    
  
-  `isfollowed` 要求と `follow` 要求によって返された JSON 応答を読み取ります ( `stopfollowing` 要求は応答で何も返しません)。 [JSON 応答の例](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)を参照してください。
    
  
コードを実行する前に、 **siteUrl** 変数のプレースホルダー値をフォローするサイトに一致するように変更します。サイト コレクションのサイトには **http://server/siteCollection/site** の形式を使用します。そのサイトの任意のページまたはライブラリからサイトをフォローできます。サイトでフォローをサポートしないテンプレート (個人用サイトなど) を使用すると、 **UnsupportedSite** エラー (エラー コード 10) を受け取ります。
  
    
    



```

// Replace the siteUrl placeholder value before you run the code.
var siteUrl = "https://domain.sharepoint.com";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the site.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the site.');
                stopFollowSite();
            }
            else {
                alert('The user is currently NOT following the site.');
                followSite();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a site.
// The request body includes a SocialActorInfo object that represents
// the site to follow.
// The success function reads the response from the REST service.
function followSite() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the site. ',
                1 : 'The user is already following the site. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a site.
// The request body includes a SocialActorInfo object that represents
// the site to stop following.
function stopFollowSite() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the site.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## コード例: SharePoint 2013 REST サービスを使用して、タグのフォローを開始し、フォローを停止する
<a name="bkmk_FollowTags"> </a>

次のコード例に、App.js ファイルの内容と次の操作方法を示します。
  
    
    

- クエリ文字列からアプリの Web URI を取得し、 `<siteUri>/_api/social.following` エンドポイント URI を作成します。
    
  
- **POST** 要求を作成し、 `isfollowed` エンドポイントに送信して、現在のユーザーが指定したタグを既にフォローしているかどうかを調べます。
    
  
- **POST** 要求を作成し、 `follow` エンドポイントに送信して、タグのフォローを開始します。
    
  
- **POST** 要求を作成し、 `stopfollowing` エンドポイントに送信して、タグのフォローを停止します。
    
  
-  `isfollowed` 要求と `follow` 要求によって返された JSON 応答を読み取ります ( `stopfollowing` 要求は応答で何も返しません)。 詳細は [JSON 応答の例](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)を参照してください。
    
  
コードを実行する前に、 **tagGuid** 変数のプレースホルダー値を既存のタグの GUID に変更します。 **HashTagsTermSet** からタグを取得するために使用するタクソノミー API には REST インターフェイスがないため, .NET クライアント オブジェクト モデルまたは JavaScript オブジェクト モデルを使用する必要があります。例については、「 [JavaScript オブジェクト モデルを使用して、タグの名前に基づいてタグの GUID を取得する方法](follow-content-in-sharepoint-2013.md#bk_getTagGuid)」を参照してください。
  
    
    



```

// Replace the tagGuid placeholder value before you run the code.
var tagGuid = "19a4a484-c1dc-4bc5-8c93-bb96245ce928";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the tag.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the tag.');
                stopFollowTag();
            }
            else {
                alert('The user is currently NOT following the tag.');
                followTag();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a tag.
// The request body includes a SocialActorInfo object that represents
// the tag to follow.
// The success function reads the response from the REST service.
function followTag() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the tag. ',
                1 : 'The user is already following the tag. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a tag.
// The request body includes a SocialActorInfo object that represents
// the tag to stop following.
function stopFollowTag() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the tag.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## コード例: SharePoint 2013 REST サービスを使用して、フォローされているコンテンツを取得する
<a name="bkmk_GetFollowed"> </a>

次のコード例に、App.js ファイルの内容と次の操作方法を示します。
  
    
    

- クエリ文字列からアプリの Web URI を取得し、 `<siteUri>/_api/social.following` エンドポイント URI を作成します。
    
  
- **GET** 要求を作成し、 `my/followedcount` エンドポイントに送信して、現在のユーザーがフォローしているコンテンツのカウントを取得します。
    
  
- **GET** 要求を作成し、 `my/followed` エンドポイントに送信して、現在のユーザーがフォローしているコンテンツを取得します。
    
  
- 要求によって返された JSON 応答を読み取ります。 [JSON 応答の例](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)を参照してください。
    
  

```

var followingManagerEndpoint;
var followedCount;

// Get the SPAppWebUrl parameter from the query string and build
// the following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl)+ "/_api/social.following";
    getMyFollowedCount();
} );

// Get the count of content that the current user is following.
// The "types=14" parameter specifies all content types
// (documents = 2 + sites = 4 + tags = 8).
function getMyFollowedCount() {
    $.ajax( {
        url: followingManagerEndpoint + "/my/followedcount(types=14)",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: function (data) { 
            followedCount = data.d.FollowedCount;
            getMyFollowedContent();
        },
        error: requestFailed
    } );
}

// Get the content that the current user is following.
// The "types=14" parameter specifies all content types
// (documents = 2 + sites = 4 + tags = 8).
function getMyFollowedContent() {
    $.ajax( {
        url: followingManagerEndpoint + "/my/followed(types=14)",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: followedContentRetrieved,
        error: requestFailed
    });
}

// Parse the JSON data and iterate through the collection.
function followedContentRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
    var types = {
        1: "document",
        2: "site",
        3: "tag" 
    };
 
    var followedActors = jsonObject.d.Followed.results; 
    var followedList = "You're following " + followedCount + " items:";
    for (var i = 0; i < followedActors.length; i++) {
        var actor = followedActors[i];
        followedList += "<p>The " + types[actor.ActorType] + ": \\"" +
        actor.Name + "\\"</p>";
    } 
    $("#message").html(followedList); 
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## コンテンツのフォロー要求に対する JSON 応答の例
<a name="bk_exampleResponses"> </a>

既定で、REST サービスは、Atom プロトコルで書式設定された応答を返しますが、HTTP **Accept** ヘッダーを使用して、JSON 形式を要求することができます (例: `"accept":"application/json;odata=verbose"`)。応答データは文字列として返されるので、前のコード例に示すように、 **JSON.stringify** 関数および **JSON.parse** 関数を使用して、文字列をオブジェクトに変換できます。
  
    
    
REST サービスによって返されたエラーをトラブルシューティングするには、デバッグ モードで、前の例の **requestFailed** コールバック関数に示すように、 **responseText** プロパティを調べます。Fiddler などのネットワーク スニファーまたは HTTP デバッガから ULS サーバー ログの関連付け ID を取得することもできます。関連付け ID は HTTP 応答の要求 ID と同じです。
  
    
    

### Follow エンドポイントへの応答の例

 `follow` エンドポイントへのクライアント側要求の応答で、REST サービスは **Follow** 要求が成功したかどうかを表す **SocialFollowResult** 値を返します。
  
    
    
次の応答は、 **AlreadyFollowing** のステータスを表します。
  
    
    



```

{"d":{"Follow":1}}
```

表 1 に **SocialFollowResult** のステータス コードとそれらの値を示します。
  
    
    

**表 1. SocialFollowResult のコードと値**

|||
|:-----|:-----|
|0  <br/> |**OK**。現在のユーザーはアクターをフォローしています。  <br/> |
|1  <br/> |**AlreadyFollowing**。現在のユーザーは既にアクターをフォローしています。  <br/> |
|2  <br/> |**LimitReached**。内部制限に達したため、要求が失敗しました。  <br/> |
|3  <br/> |**InternalError**。内部エラーのため、要求が失敗しました。  <br/> |
   

> **メモ**
> REST サービスは、 **StopFollowing** 要求に応答を返しません。 `{"d":{"StopFollowing":null}}` を返します。
  
    
    


### IsFollowed エンドポイントへの応答の例

 `isfollowed` エンドポイントへのクライアント側要求の応答で、REST サービスは現在のユーザーが指定したアクターをフォローしているかどうかを表す **bool** 値を返します。
  
    
    
次の応答は、現在のユーザーが指定したドキュメント、サイト、またはタグをフォローしていないことを示しています。
  
    
    



```
{"d":{"IsFollowed":false}}
```


### My/Followed エンドポイントへの応答の例

 `my/followed` エンドポイントへのクライアント側要求の応答で、REST サービスは、現在のユーザーがフォローしているドキュメント、サイト、およびタグを表す **SP.Social.SocialActor** オブジェクトの配列を返します。
  
    
    
次の応答は、フォローされているドキュメント、サイト、およびタグを表します。要求には含めるコンテンツの種類を指定します。
  
    
    



```
{"d":{"Followed":{"results":[
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":1
    "CanFollow":true
    "ContentUri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"2.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.
      51bbb5d8e214457ba794669345d23040.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"snippets.txt"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"00000000-0000-0000-0000-000000000000"
    "Title":null
    "Uri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
  }
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":2
    "CanFollow":true
    "ContentUri":"https://domain.sharepoint.com:443/"
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"8.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.
      089f4944a6374a64b52b7af5ba140392.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"Developer Site"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"00000000-0000-0000-0000-000000000000"
    "Title":null
    "Uri":"https://domain.sharepoint.com:443/"
  }
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":3
    "CanFollow":true
    "ContentUri":null
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"16.00000000000000000000000000000000.00000000000000000000000000000000.
      19a4a484c1dc4bc58c93bb96245ce928.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"#someTag"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928"
    "Title":null
    "Uri":"https://domain-my.sharepoint.com:443/_layouts/15/HashTagProfile.aspx?
      TermID=19a4a484-c1dc-4bc5-8c93-bb96245ce928"
  }
]}}}
```


### My/FollowedCount エンドポイントへの応答の例

 `my/followedcount` エンドポイントへのクライアント側要求の応答で、REST サービスは現在のユーザーがフォローしている指定したアクターの種類の合計カウントを表す **Int32** 値を返します。
  
    
    
次の応答は、3 つのフォローされているドキュメント、サイト、またはタグのカウントを表します。要求には含めるコンテンツの種類を指定します。
  
    
    



```

{"d":{"FollowedCount":3}}
```


## その他の技術情報
<a name="bkmk_AddtionalResources"> </a>


-  [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [方法: SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  

