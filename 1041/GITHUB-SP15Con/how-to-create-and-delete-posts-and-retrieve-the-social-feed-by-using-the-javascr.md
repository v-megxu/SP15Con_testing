---
title: [方法] SharePoint 2013 で JavaScript オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う
ms.prod: SHAREPOINT
ms.assetid: e8c21960-6ea0-43c0-821e-2db2a0ecec90
---


# [方法] SharePoint 2013 で JavaScript オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う
SharePoint 2013 JavaScript オブジェクト モデルを使用したマイクロブログの投稿の作成と削除およびソーシャル フィードの取得の方法について説明します。
## SharePoint Server 2013のソーシャル フィードとは
<a name="bk_intro"> </a>

SharePoint Server 2013 では、ソーシャル フィードは、会話、マイクロブログの個々の投稿、または通知を表すスレッドのコレクションです。スレッドには、ルートの投稿と返信の投稿コレクションが含まれます。JavaScript オブジェクト モデルでは、フィードは  [SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx) オブジェクトで表し、スレッドは [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx) オブジェクトで表し、投稿と返信は [SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx) オブジェクトで表します。フィード関連の主要なタスクは、 [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) オブジェクトを使用して行います。この記事では、JavaScript オブジェクト モデルを使用してソーシャル フィードを操作するアプリケーション ページを作成する方法について解説します。
  
    
    
 [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) の操作や、他の API を使用したソーシャル フィードの操作の詳細については、「 [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)」を参照してください。
  
    
    

## SharePoint 2013 JavaScript オブジェクト モデルでソーシャル フィードを操作する開発環境をセットアップするための前提条件
<a name="bkmk_SetUpDevEnv"> </a>

JavaScript オブジェクト モデルを使用してソーシャル フィードをやり取りするアプリケーション ページを作成するには、次のことが必要になります。
  
    
    

- SharePoint Server 2013で 個人用サイト を公開するように設定し、現在のユーザーおよびターゲット ユーザー用に個人用のサイトを作成し、ターゲット ユーザーが書いたいくつかの投稿を用意する
    
  
- Office Developer Tools for Visual Studio 2013 を持つ Visual Studio 2012 または Visual Studio 2013
    
  
- ログオン ユーザーに対する User Profile Service アプリケーションへの **フル コントロール**のアクセス許可とファーム ソリューションを展開するためのアクセス許可
    
  
- 個人用サイト Web アプリケーションのコンテンツ データベースにアクセスするためのアプリケーション プール アカウントに対する十分な権限
    
  

## SharePoint 2013 JavaScript オブジェクト モデルを使用した、ソーシャル フィードを操作するアプリケーション ページの作成
<a name="bk_CreateApp"> </a>


1. Visual Studio を開いて、[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。
    
  
2. [ **新しいプロジェクト**] ダイアログ ボックスの上部にあるドロップダウン リストから [ **.NET Framework 4.5**] を選択します。
    
  
3. [ **テンプレート**] リストの [ **Office SharePoint**] を展開し、[ **SharePoint ソリューション**] カテゴリを選択して、[ **SharePoint 2013 Project**] テンプレートを選択します。
    
  
4. プロジェクト名に 「SocialFeedJSOM」という名前を付け、[ **OK**] をクリックします。
    
  
5. [ **SharePoint カスタマイズ ウィザード**] ダイアログ ボックスで、[ **ファーム ソリューションとして配置する**] を選択して、[ **完了**] をクリックします。
    
  
6. **Solution Explorer** で、SocialFeedJSOM プロジェクトのショートカット メニューを開き、SharePoint のマップされた "Layouts" フォルダーを追加します。
    
  
7. [ **Layouts**] フォルダーで、[SocialFeedJSOM] フォルダーのショートカット メニューを開き、「SocialFeed.aspx」という名前の新しい SharePoint アプリケーション ページを作成します。
    
    > **メモ**
      > この記事のコード例では、ページ マークアップにカスタム コードを定義していますが、Visual Studio によって作成されるページの分離コードは使用しません。 
8. SocialFeed.aspx ページのショートカット メニューを開き、[ **スタートアップ アイテムとして設定**] を選択します。
    
  
9. SocialFeed.aspx ページのマークアップで、次のコードに示すように、"Main" **asp:Content** タグ内のコントロールを定義します。
    
  ```HTML
  
<table width="100%" id="tblPosts"></table><br/>
<button id="btnDelete" type="button"></button><br />
<span id="spanMessage" style="color: #FF0000;"></span>
  ```


    > **メモ**
      > これらのコントロールは、すべてのシナリオで使用する必要はありません。たとえば、"投稿と返信の公開" シナリオでは、 **span** コントロールのみを使用します。
10. 次のコードに示されているように、 **span** の終了タグの後に **SharePoint:ScriptLink** コントロール、 **SharePoint:FormDigest** コントロール、および **script** タグを追加します。 **SharePoint:ScriptLink** タグは、JavaScript オブジェクト モデルを定義するクラスを参照します。このモデルは 個人用サイト ソーシャル 開発に使用できます。 **SharePoint:FormDigest** タグは、サーバーのコンテンツを更新する操作によってセキュリティの検証が必要とされたときに、メッセージ ダイジェストを生成します。
    
  ```HTML
  
<SharePoint:ScriptLink ID="ScriptLink1" name="SP.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:ScriptLink ID="ScriptLink2" name="SP.UserProfiles.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:FormDigest id="FormDigest" runat="server"/>
<script type="text/javascript">

    // Replace this comment with the code for your scenario.

</script>

  ```

11. フィードとやり取りするロジックを追加するには、 **script** タグで囲まれたコメントの内容を、次のいずれかのシナリオのコード例で置き換えます。
    
  -  [ソーシャル フィードへの投稿と返信の公開](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_PubPosts)
    
  
  -  [ソーシャル フィードの取得](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_GetFeeds)
    
  
  -  [ソーシャル フィードからの投稿と返信の削除](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_DeletePosts)
    
  
12. アプリケーション ページをテストするには、[ **デバッグ**] メニューの [ **デバッグ開始**] をクリックします。web.config ファイルの変更を確認するメッセージが表示されたら、[ **OK**] をクリックします。
    
    応答が失敗のコールバック メソッドを呼び出す場合、メソッドにブレークポイントを設定し、 **args** オブジェクトにウォッチを追加するか、詳細について ULS ログおよびイベント ビューアーを確認します。
    
  

## コード例: SharePoint 2013 JavaScript オブジェクト モデルを使用した、ソーシャル フィードへの投稿と返信の公開
<a name="bkmk_PubPosts"> </a>

次のコードは、投稿と返信を公開する例です。以下の操作方法が記述されています。
  
    
    

- 投稿内容を定義する。この例では、投稿にリンクが含まれています。
    
  
- **createPost** メソッドを使用し、 **null** を _targetId_ パラメーターとして渡すことで、現在のユーザーのフィードに投稿を公開する。
    
  
- **createPost** メソッドを使用し、スレッド識別子を _targetId_ パラメーターとして渡すことで、投稿に返信する。
    
  

> **メモ**
> 「 [アプリケーション ページの作成](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)」の手順で追加した **script** タグの間に次のコードを貼り付けます。
  
    
    


```

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(PublishPost, 'SP.UserProfiles.js');

// Declare global variables.
var clientContext;
var feedManager;
var resultThread;

function PublishPost() {

    // Initialize the current client context and the SocialFeedManager instance.
    clientContext = SP.ClientContext.get_current();
    feedManager = new SP.Social.SocialFeedManager(clientContext);

    // Create a link to include in the post.
    var linkDataItem = new SP.Social.SocialDataItem();
    linkDataItem.set_itemType(SP.Social.SocialDataItemType.link);
    linkDataItem.set_text('link');
    linkDataItem.set_uri('http://bing.com');
    var socialDataItems = [ linkDataItem ];

    // Create the post content.
    var postCreationData = new SP.Social.SocialPostCreationData();
    postCreationData.set_contentText('The text for the post, which contains a {0}.');
    postCreationData.set_contentItems(socialDataItems);

    // Publish the post. Pass null for the "targetId" parameter because this is a root post.
    resultThread = feedManager.createPost(null, postCreationData);
    clientContext.executeQueryAsync(PublishReply, PostFailed);
    }
function PublishReply(sender, args) {

    // Create the reply content.
    var postCreationData = new SP.Social.SocialPostCreationData();
    postCreationData.set_contentText('The text for the reply.');

    // Publish the reply.
    resultThread = feedManager.createPost(resultThread.get_id(), postCreationData);
    clientContext.executeQueryAsync(PostSucceeded, PostFailed);
}
function PostSucceeded(sender, args) {
    $get("spanMessage").innerText = 'The post and reply were published.';
}
function PostFailed(sender, args) {
    $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
}

```


## コード例: SharePoint 2013 JavaScript オブジェクト モデルを使用した、ソーシャル フィードの取得
<a name="bkmk_GetFeeds"> </a>

次のコード例では、現在のユーザーとターゲット ユーザーのフィードを取得します。以下の操作方法が記述されています。
  
    
    

- **getFeed** メソッドを使用して、現在のユーザーの **Personal**、 **News**、および **Timeline** のフィード タイプを取得する。
    
  
- **getFeedFor** メソッドを使用して、ターゲット ユーザーの **Personal** フィード タイプを取得する。
    
  
- フィードを反復処理して非参照スレッドをすべて検出し、それらのスレッドと投稿に関する情報を取得する。参照スレッドは、別のスレッドに関する情報を含む通知を表します。たとえば、誰かに関するユーザーのメンションが投稿内にあると、元の投稿へのリンクと投稿についての他のメタデータを含む **MentionReference** 型のスレッドがサーバーによって生成されます。
    
  
フィード タイプの詳細については、「 [個人用サイト ソーシャル API のフィード タイプの概要](work-with-social-feeds-in-sharepoint-2013.md#bkmk_FeedTypes)」を参照してください。参照スレッドの詳細については、「 [SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)」を参照してください。
  
    
    

> **メモ**
> 「 [アプリケーション ページの作成](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)」の手順で追加した **script** タグの間に次のコードを貼り付け、コードを実行する前に **targetUser** 変数のプレースホルダーの値を変更します。
  
    
    




```cs

// Replace the placeholder value with the account name of the target user.
var targetUser = 'domainName\\\\userName';

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(GetFeeds, 'SP.UserProfiles.js');

// Declare global variables.
var clientContext;
var feedManager;
var personalFeed;
var newsFeed;
var timelineFeed;
var targetUserFeed;

function GetFeeds() {

    // Initialize the current client context and the SocialFeedManager instance.
    clientContext = SP.ClientContext.get_current();
    feedManager = new SP.Social.SocialFeedManager(clientContext);

    // Set parameters for the feed content that you want to retrieve.
    var feedOptions = new SP.Social.SocialFeedOptions();
    feedOptions.set_maxThreadCount(10); // default is 20

    // Get all feed types for current user and get the Personal feed
    // for the target user.
    personalFeed = feedManager.getFeed(SP.Social.SocialFeedType.personal, feedOptions);
    newsFeed = feedManager.getFeed(SP.Social.SocialFeedType.news, feedOptions);
    targetUserFeed = feedManager.getFeedFor(targetUser, feedOptions);

    // Change the sort order to optimize the Timeline feed results.
    feedOptions.set_sortOrder(SP.Social.SocialFeedSortOrder.byCreatedTime); 
    timelineFeed = feedManager.getFeed(SP.Social.SocialFeedType.timeline, feedOptions);

    clientContext.load(feedManager);
    clientContext.executeQueryAsync(CallIterateFunctionForFeeds, RequestFailed);
}
function CallIterateFunctionForFeeds() {
    IterateThroughFeed(personalFeed, "Personal", true);
    IterateThroughFeed(newsFeed, "News", true);
    IterateThroughFeed(timelineFeed, "Timeline", true); 
    IterateThroughFeed(targetUserFeed, "Personal", false);
}
function IterateThroughFeed(feed, feedType, isCurrentUser) {
    tblPosts.insertRow().insertCell();
    var feedHeaderRow = tblPosts.insertRow();
    var feedOwner = feedManager.get_owner().get_name();

    // Iterate through the array of threads in the feed.
    var threads = feed.get_threads();
    for (var i = 0; i < threads.length ; i++) {
        var thread = threads[i];
        var actors = thread.get_actors();

        if (i == 0) {

            // Get the name of the target user for the feed header row. Users are 
            // owners of all threads in their Personal feed.
            if (!isCurrentUser) {
                feedOwner = actors[thread.get_ownerIndex()].get_name();
            }
            feedHeaderRow.insertCell().innerText = feedType.toUpperCase() + ' FEED FOR '
                + feedOwner.toUpperCase();
        }

        // Use only Normal-type threads and ignore reference-type threads. (SocialThreadType.Normal = 0)
        if (thread.get_threadType() == 0) {

            // Get the root post's author, content, and number of replies.
            var post = thread.get_rootPost();
            var authorName = actors[post.get_authorIndex()].get_name();
            var postContent = post.get_text();
            var totalReplies = thread.get_totalReplyCount();

            var postRow = tblPosts.insertRow();
            postRow.insertCell().innerText = authorName + ' posted \\"' + postContent
                + '\\" (' + totalReplies + ' replies)';

            // If there are any replies, iterate through the array and
            // get the author and content. 
            // If a thread contains more than two replies, the server
            // returns a thread digest that contains only the two most
            // recent replies. To get all replies, call the 
            // SocialFeedManager.getFullThread method.
            if (totalReplies > 0) {
                var replies = thread.get_replies();

                for (var j = 0; j < replies.length; j++) {
                    var replyRow = tblPosts.insertRow();

                    var reply = replies[j];
                    replyRow.insertCell().innerText = '  - ' + actors[reply.get_authorIndex()].get_name()
                        + ' replied \\"' + reply.get_text() + '\\"';
                }
            }
        }
    }
}
function RequestFailed(sender, args) {
    $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
}
```


## コード例: SharePoint 2013 JavaScript オブジェクト モデルを使用した、ソーシャル フィードからの投稿と返信の削除
<a name="bkmk_DeletePosts"> </a>

次のコード例では、投稿または返信を削除します。以下の操作方法が記述されています。
  
    
    

- **getFeed** メソッドを使用して、現在のユーザーの **News** フィード タイプを取得する。
    
  
- フィード内で投稿と返信を繰り返し処理して、投稿または返信を削除するために使用する **id** プロパティを取得する。
    
  
- **deletePost** メソッドを使用して、大元の投稿または返信を削除する (大元の投稿を削除するとスレッド全体が削除される)。
    
  

> **メモ**
> 「 [アプリケーション ページの作成](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)」の手順で追加した **script** タグの間に次のコードを貼り付けます。この例では、現在のユーザーのニュースフィードに少なくとも 1 つの投稿があることを前提としています。
  
    
    


```cs

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(GetFeeds, 'SP.UserProfiles.js');

// Declare global variables.
var clientContext;
var feedManager;
var feed;
var postOrReplyToDelete;

function GetFeeds() {

    // Initialize the current client context and the SocialFeedManager instance.
    clientContext = SP.ClientContext.get_current();
    feedManager = new SP.Social.SocialFeedManager(clientContext);

    // Set parameters for the feed content that you want to retrieve.
    var feedOptions = new SP.Social.SocialFeedOptions();
    feedOptions.set_maxThreadCount(10); // default is 20

    // Get all the News feed type for current user.
    feed = feedManager.getFeed(SP.Social.SocialFeedType.news, feedOptions);
    clientContext.executeQueryAsync(IterateThroughFeed, RequestFailed);
}
function IterateThroughFeed() {

    // Iterate through the array of threads in the feed.
    var threads = feed.get_threads();
    for (var i = 0; i < threads.length ; i++) {
        var thread = threads[i];
        var actors = thread.get_actors();

        // Get the root post's author, content, and number of replies.
        var post = thread.get_rootPost();

        var authorName = actors[post.get_authorIndex()].get_name();
        var postContent = post.get_text();
        var totalReplies = thread.get_totalReplyCount();

        var postRow = tblPosts.insertRow();
        postRow.insertCell().innerText = authorName + ' posted \\"' + postContent
            + '\\" (' + totalReplies + ' replies)';
        postOrReplyToDelete = post.get_id();

        // If there are any replies, iterate through the array and
        // get the author and content.
            // If a thread contains more than two replies, the server
            // returns a thread digest that contains only the two most
            // recent replies. To get all replies, call the 
            // SocialFeedManager.getFullThread method.
        if (totalReplies > 0) {
            var replies = thread.get_replies();
            for (var j = 0; j < replies.length; j++) {
                var replyRow = tblPosts.insertRow();

                var reply = replies[j];
                replyRow.insertCell().innerText = '  - ' + actors[reply.get_authorIndex()].get_name()
                    + ' replied \\"' + reply.get_text() + '\\"';
                postOrReplyToDelete = reply.get_id();
            }
        }

        // Initialize button properties.
        $get("btnDelete").onclick = function () { DeletePostOrReply(); };
        $get("btnDelete").innerText = 'Click to delete the last post or reply';
    }
}

// Delete the last post or reply listed on the page.
function DeletePostOrReply() {
    feedManager.deletePost(postOrReplyToDelete);
    clientContext.executeQueryAsync(DeleteSucceeded, RequestFailed);
}
function DeleteSucceeded(sender, args) {
    $get("spanMessage").innerText = 'The post or reply was deleted. Refresh the page to see your changes.';
}
function RequestFailed(sender, args) {
    $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
}
```


## その他の技術情報
<a name="bk_addResources"> </a>


-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [SP へソーシャル名前空間 (sp.userprofiles)](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx)
    
  
-  [[方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)
    
  
-  [[方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  

