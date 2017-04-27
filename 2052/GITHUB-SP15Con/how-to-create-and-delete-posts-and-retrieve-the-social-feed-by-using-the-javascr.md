---
title: 如何：使用 SharePoint 2013 中的 JavaScript 对象模型创建和删除帖子以及检索好友动态订阅源
ms.prod: SHAREPOINT
ms.assetid: e8c21960-6ea0-43c0-821e-2db2a0ecec90
---


# 如何：使用 SharePoint 2013 中的 JavaScript 对象模型创建和删除帖子以及检索好友动态订阅源
学习如何使用 SharePoint 2013 JavaScript 对象模型来创建和删除微博文章以及检索好友动态订阅源。
## 在 SharePoint Server 2013 中，什么是好友动态订阅源？
<a name="bk_intro"> </a>

在 SharePoint Server 2013 中，好友动态订阅源是表示对话、单个微博或通知的线索的集合。线索包含了根帖子以及回复的集合。在 JavaScript 对象模型中， [SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx) 对象表示订阅源， [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx) 对象表示线索， [SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx) 对象表示帖子和回复。若要执行与订阅源相关的核心任务，您可以使用 [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) 对象。本文将演示如何创建使用JavaScript 对象模型应用程序页以使用好友动态订阅源。
  
    
    
有关使用  [社交源管理器](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) 的详细信息，或有关使用其他 API 以使用社交源的信息，请参阅 [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)。
  
    
    

## 为了使用 SharePoint 2013JavaScript 对象模型中的好友动态订阅源而设置开发坏境的先决条件
<a name="bkmk_SetUpDevEnv"> </a>

若要创建使用 JavaScript 对象模型以使用好友动态订阅源的应用程序页，您将需要：
  
    
    

- SharePoint Server 2013、公开配置的 我的网站 、为当前用户和目标用户创建的个人网站、当前用户和目标用户，以及目标用户写的一些文章。
    
  
- Visual Studio 2008 或带 Visual Studio 2013 Office 开发人员工具 的 Visual Studio 2013
    
  
- "完全控制"针对 User Profile Service 应用程序的访问权限和为已登录用户部署场解决方案的权限
    
  
- 应用程序池帐户用于访问"我的网站"网络应用程序内容数据库的充足访问权限
    
  

## 通过使用 SharePoint 2013 JavaScript 对象模型创建使用好友动态订阅源的应用程序页
<a name="bk_CreateApp"> </a>


1. 打开 Visual Studio，然后选择"文件"、"新建" 和"项目"。
    
  
2. 在"新建项目" 对话框中，对话框中，从对话框的顶部下拉列表中选择".NET Framework 4.5"。
    
  
3. 在"模版"列表中，展开"Office SharePoint"，选择"SharePoint 解决方案"类别，然后选择"SharePoint 2013 项目"模板。
    
  
4. 将项目命名为 SocialFeedJSOM，然后选择"确定"按钮。
    
  
5. 在"SharePoint 自定义向导"对话框中，选择"部署场解决方案"，然后选择"完成"按钮。
    
  
6. 在"解决方案资源管理器"中，打开 SocialFeedJSOM 项目的快捷菜单，然后添加 SharePoint"布局"映射文件夹。
    
  
7. 在"布局"文件夹中，打开 SocialFeedJSOM 文件夹的快捷菜单，然后添加一个新的名为SocialFeed.aspx 的 SharePoint 应用程序页。
    
    > **注释**
      > 本文的代码示例定义了页面标记中的自定义代码，但是没有使用 Visual Studio 为该页面创建的代码隐藏类。 
8. 打开 SocialFeed.aspx 页的快捷菜单，然后选择"设置启动项"。
    
  
9. 在 SocialFeed.aspx 页的标记中，定义"主要" **asp:Content** 标记内的控件（如以下代码所示）。
    
  ```HTML
  
<table width="100%" id="tblPosts"></table><br/>
<button id="btnDelete" type="button"></button><br />
<span id="spanMessage" style="color: #FF0000;"></span>
  ```


    > **注释**
      > 这些控件可能不会用于每个应用场景。例如，"发布帖子和回复"应用场景只使用 **span** 控件。
10. 在结束 **span** 标记之后，添加 **SharePoint:ScriptLink** 控件、 **SharePoint:FormDigest** 控件和 **script** 标记（如以下代码所示）。 **SharePoint:ScriptLink** 标记引用了定义您可以用于 我的网站社交 的 JavaScript 对象模型的类库文件当更新服务器内容的操作所需时， **SharePoint:FormDigest** 标记将生成用于安全验证的消息摘要。
    
  ```HTML
  
<SharePoint:ScriptLink ID="ScriptLink1" name="SP.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:ScriptLink ID="ScriptLink2" name="SP.UserProfiles.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:FormDigest id="FormDigest" runat="server"/>
<script type="text/javascript">

    // Replace this comment with the code for your scenario.

</script>

  ```

11. 若要添加逻辑以使用订阅源，请替换 **script** 标记和以下某一应用场景中的代码示例间的注释。
    
  -  [发布帖子和回复好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_PubPosts)
    
  
  -  [检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_GetFeeds)
    
  
  -  [删除好友动态订阅源中的帖子和回复](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_DeletePosts)
    
  
12. 若要测试该应用程序页，请在菜单栏选择"调试"和"开始调式"。如果您试图修改 web.config 文件，请选择"确定"按钮。
    
    如果响应调用失败回调方法，在该方法中设置一个断点，然后添加对 **args** 对象的监视或查阅 ULS 日志和事件查看器，以获取更多信息。
    
  

## 代码示例：通过使用 SharePoint 2013JavaScript 对象模型发布文章和回复到好友动态
<a name="bkmk_PubPosts"> </a>

以下代码示例发布了一篇文章和一条回复。它演示了如何：
  
    
    

- 定义文章内容。此示例包括了该文章中的一个链接。
    
  
- 通过使用 **createPost** 方法并将 **null** 作为 _targetId_ 参数进行传递以发布文章到当前用户的动态。
    
  
- 通过使用 **createPost** 方法，并将线索标识符作为 _targetId_ 参数进行传递，以回复某文章。
    
  

> **注释**
> 粘贴您在 [创建应用程序页](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)过程中添加的 **script** 标记间的以下代码。
  
    
    


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


## 代码示例：使用 SharePoint 2013 JavaScript 对象模型检索好友动态
<a name="bkmk_GetFeeds"> </a>

以下代码示例检索了当前用户和目标用户的动态。它演示了如何：
  
    
    

- 使用 **getFeed** 方法获得当前用户的 **Personal**、 **News** 和 **Timeline** 动态类型。
    
  
- 使用 **getFeedFor** 方法获得目标用户的 **Personal** 动态类型。
    
  
- 循环访问动态以查找所有非引用线索并获取有关线索和文章的信息。引用线索表示包含有关另一个线索的信息的通知。例如，如果用户在帖子中提到某人，则服务器将生成包含指向原帖和帖子其他元数据的链接的 **MentionReference** 类型的线索。
    
  
有关订阅源类型的详细信息，请参阅 [我的网站社交 API 中的订阅源类型概览](work-with-social-feeds-in-sharepoint-2013.md#bkmk_FeedTypes)。有关引用线索的详细信息，请参阅 [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)。
  
    
    

> **注释**
> 粘贴您在 [创建应用程序页](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)过程中添加的 **script** 标记间的以下代码。然后在运行代码之前，请先更改 **targetUser** 变量的占位符值。
  
    
    




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


## 代码示例：使用 SharePoint 2013 JavaScript 对象模型从好友动态中删除文章和回复
<a name="bkmk_DeletePosts"> </a>

以下代码示例将删除文章或回复。它演示了如何：
  
    
    

- 使用 **News** 方法获得当前用户的 **getFeed** 动态类型。
    
  
- 循环访问动态中的文章和回复以获取您用于删除文章或回复的 **id** 属性。
    
  
- 使用 **deletePost** 方法删除根帖子或回复（删除根帖子将删除整个线索）。
    
  

> **注释**
> 粘贴您在 [创建应用程序页](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)过程中添加的 **script** 标记间的以下代码。此示例假设当前用户的新闻源包含了至少一条帖子。
  
    
    


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


## 其他资源
<a name="bk_addResources"> </a>


-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [SP。社会的命名空间 (sp.userprofiles)](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)
    
  
-  [如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  

