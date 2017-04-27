---
title: 使用 SharePoint 2013 中的社交源
ms.prod: SHAREPOINT
ms.assetid: 39f2163e-15cc-43bc-b131-041d5afdcd90
---



# 使用 SharePoint 2013 中的社交源
了解处理 SharePoint Server 2013 中的好友动态订阅源和微博文章的一般编程任务
## 处理 SharePoint Server 2013 中的好友动态订阅源的 API
<a name="bkmk_APIversions"> </a>

在本地 SharePoint Server 2013 场中，互动好友动态订阅源旨在鼓励好友共享信息，以及与好友和内容保持联系。您可以在用户个人网站上的"新闻源"页上看到很多订阅源功能。订阅源包含表示微博帖子、会话、状态更新和其他通知的线索集合。
  
    
    
SharePoint Server 2013 提供了以下可用于以编程方式处理好友动态订阅源的 API：
  
    
    

- 托管代码的客户端对象模型
    
  - .NET 客户端对象模型
    
  
  - Silverlight 客户端对象模型
    
  
  - 移动设备客户端对象模型
    
  
- JavaScript 对象模型
    
  
- 代表性状态传输 (REST) 服务
    
  
- 服务器对象模型
    
  
作为 SharePoint 2013 开发中的最佳实践，在可能的时候使用客户端 API。客户端 API 包括客户端对象模型、JavaScript 对象模型和 REST 服务。有关 SharePoint 2013 中的 API 以及何时使用这些 API 的详细信息，请参阅  [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    
每个 API 都包括您用于执行与订阅源相关的核心任务的管理器对象。表 1 显示了这些 API 中的管理器和其他关键对象（或 REST 资源）以及可在其中找到 API 的类库（或终结点 URI）。
  
    
    

> **注释**
> Silverlight 和移动客户端对象模型未明确记载在表 1 或表 2 中，因为它们提供了与 .NET 客户端对象模型相同的核心功能，并使用相同的签名。Silverlight 客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll 中进行定义，而移动客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Phone.dll 中进行定义。 
  
    
    


**表 1. SharePoint 2013 用于以编程方式处理好友动态订阅源的 API**

|||
|:-----|:-----|
|.NET 客户端对象模型  <br/> 请参阅： [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md) <br/> |管理器对象：           [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) <br/> 主命名空间：           [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> 其他关键对象：           [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) 、 [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) 、 [SocialPost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPost.aspx) 、 [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 、 [SocialFeedOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedOptions.aspx) 、 [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) <br/> 类库：          Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript 对象模型  <br/> 请参阅  [如何：使用 SharePoint 2013 中的 JavaScript 对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md) <br/> |管理器对象：           [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) <br/> 主命名空间：           [SP.Social](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) <br/> 其他关键对象：           [SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx)、 [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx)、 [SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx)、 [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx)、 [SocialFeedOptions](http://msdn.microsoft.com/library/65caf283-6e7a-50dc-ef8e-a4e12bd237ac%28Office.15%29.aspx)、 [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx) <br/> 类库：          SP.UserProfiles.js  <br/> |
|REST 服务  <br/> 请参阅 [如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md) <br/> |管理器资源：           [social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md) (SocialRestFeedManager) <br/> 主命名空间 (OData)：          **SP.Social** <br/> 其他关键资源：          SocialFeed、 [SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)、SocialThread、 [SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)、SocialPost、SocialPostCreationData、 [SocialRestPostCreationData](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestPostCreationData)、 [SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)、SocialActor、 [SociaRestActor](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestActor) <br/> 访问点：           `<siteUri>/_api/social.feed` <br/> |
|服务器对象模型  <br/> > **注释**> 使用服务器对象模型以访问订阅源数据并在远程运行的代码必须使用 [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) 对象。          
|管理器对象：           [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.aspx) <br/> 主命名空间：           [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> 其他关键对象：           [SPSocialFeed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeed.aspx) 、 [SPSocialThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialThread.aspx) 、 [SPSocialPost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPost.aspx) 、 [SPSocialFeedOptions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedOptions.aspx) 、 [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) <br/> 类库：          Microsoft.Office.Server.UserProfiles.dll  <br/> |
   
如果您使用的是服务器对象模型来访问订阅源内容，并且代码未在 SharePoint 实例上运行（也就是说，如果您的扩展名未安装在应用程序服务器上的 LAYOUTS 文件夹中），请使用代码中的  [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) 对象。以下代码示例显示了一种将 [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) 对象合并到代码中的方法。
  
    
    



```cs

using (SPSite site = new SPSite(<siteURL>))
{
    using (new Microsoft.SharePoint.SPServiceContextScope(SPServiceContext.GetContext(site)))
    {
        // code
    }
}

```


## 处理 SharePoint Server 2013 中的好友动态订阅源的一般编程任务
<a name="bkmk_CommonTasks"> </a>

表 2 显示了处理好友动态订阅源的一般编程任务及您用于执行这些任务的成员。这些成员来自 .NET 客户端对象模型 (CSOM)、JavaScript 对象模型 (JSOM)、REST 服务和服务器对象模型 (SSOM)。
  
    
    

**表 2. 处理 SharePoint Server 2013 中的好友动态订阅源的一般编程任务的 API**


|**任务**|**成员**|
|:-----|:-----|
|在当前用户上下文中创建管理器对象的实例  <br/> |CSOM： [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.#ctor.aspx) <br/> JSOM： [SocialFeedManager](http://msdn.microsoft.com/library/f7cf172f-970b-6b71-9eb4-b9a8bb7a0001%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md) <br/> SSOM： [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.#ctor.aspx) <br/> |
|在特定用户的上下文中创建管理器对象的实例  <br/> |CSOM：未实现  <br/> JSOM：未实现  <br/> REST：未实现  <br/> SSOM： [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.#ctor.aspx) <br/> |
|获取当前上下文的用户  <br/> |CSOM： [Owner](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.Owner.aspx) <br/> JSOM： [owner](http://msdn.microsoft.com/library/0307264e-d733-77f0-edae-f5468e58d0b7%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed/my](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_my) <br/> SSOM： [Owner](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.Owner.aspx) <br/> |
|获取当前用户的订阅源  <br/> （指定订阅源类型）  <br/> |CSOM： [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) <br/> JSOM： [getFeed](http://msdn.microsoft.com/library/cddaccd8-28da-6798-d8cb-4e9351efddf3%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed/my/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeed)（个人订阅源）、 [<siteUri>/_api/social.feed/my/News](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myNews)、 [<siteUri>/_api/social.feed/my/TimelineFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myTimelineFeed) 或 [<siteUri>/_api/social.feed/my/Likes](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myLikes) <br/> SSOM： [GetFeed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeed.aspx) <br/> |
|获取特定用户的个人订阅源  <br/> |CSOM： [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) <br/> JSOM： [getFeedFor](http://msdn.microsoft.com/library/074ed255-9393-448d-1f7e-720fdeb05f48%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed/actor(item='domain\\\\user')/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> SSOM： [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeedFor.aspx) <br/> |
|获取工作组网站的网站源  <br/> （指定网站源的 URL 作为主角（示例：http://<siteCollection>/<teamSite>/newsfeed.aspx））  <br/> |CSOM： [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) <br/> JSOM： [getFeedFor](http://msdn.microsoft.com/library/074ed255-9393-448d-1f7e-720fdeb05f48%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed/actor(item=@v)/Feed?@v='http://<siteCollection>/<teamSite>/newsfeed.aspx'](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> SSOM： [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeedFor.aspx) <br/> |
|将根帖子发布到当前用户的订阅源  <br/> （将 **null** 指定给目标） <br/> |CSOM： [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM： [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.feed/my/Feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeedPost) 并在请求正文中传递 _restCreationData_ 参数 <br/> SSOM： [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|将文章发布到网站源  <br/> （指定网站源的 URL 作为目标（示例：http://<siteCollection>/teamSite>/newsfeed.aspx））  <br/> |CSOM： [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM： [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.feed/actor(item=@av)/feed/post/?@av='<teamSiteUri>/newsfeed.aspx'](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeedPost) 并在请求正文中传递 _restCreationData_ 参数（将 **null** 指定给 _ID_ 参数） <br/> SSOM： [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|发布对文章的回复  <br/> （指定目标线索的 ID）  <br/> |CSOM： [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM： [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.feed/Post/Reply](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postReply) 并在请求正文中传递 _restCreationData_ 参数 <br/> SSOM： [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|删除当前用户的订阅源中的帖子、回复或线索（删除根帖子会删除整个线索）  <br/> |CSOM： [DeletePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.DeletePost.aspx) <br/> JSOM： [deletePost](http://msdn.microsoft.com/library/06e03f87-c97d-8634-a02b-f7812eb7beeb%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.feed/Post/Delete](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postDelete) 并在请求正文中传递 _ID_ 参数 <br/> SSOM： [DeletePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.DeletePost.aspx) <br/> |
|从用户的订阅源获取线索（根帖子及其所有回复）  <br/> |CSOM： [GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) <br/> JSOM： [getFullThread](http://msdn.microsoft.com/library/6bb384f3-9474-581f-e18d-e8c4f44c3cdf%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_post) 并在请求正文中传递 _ID_ 参数 <br/> SSOM： [GetFullThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFullThread.aspx) <br/> |
|让用户喜欢（不喜欢）一篇文章或一则回复  <br/> |CSOM： [LikePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.LikePost.aspx) ( [UnlikePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.UnlikePost.aspx) ) <br/> JSOM： [likePost](http://msdn.microsoft.com/library/f401a584-1712-50af-ee08-2999a16388d6%28Office.15%29.aspx) ( [unlikePost](http://msdn.microsoft.com/library/c778bd7d-91e5-15dc-eeb8-b571957e8338%28Office.15%29.aspx))  <br/> REST： **POST** [<siteUri>/_api/social.feed/Post/Like](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLike) ( [<siteUri>/_api/social.feed/Post/Unlike](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlike)) 并在请求正文中传递  _ID_ 参数 <br/> SSOM： [LikePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.LikePost.aspx) ( [UnlikePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.UnlikePost.aspx) ) <br/> |
|获取文章的所有爱好者  <br/> |CSOM： [GetAllLikers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetAllLikers.aspx) <br/> JSOM： [getAllLikers](http://msdn.microsoft.com/library/76286fdc-002f-2b13-dc26-53097eb2e3a2%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.feed/Post/Likers](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLikers) 并在请求正文中传递 _ID_ 参数 <br/> SSOM： [GetAllLikers](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetAllLikers.aspx) <br/> |
|获取提及某个用户的文章  <br/> |CSOM： [GetMentions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetMentions.aspx) <br/> JSOM： [getMentions](http://msdn.microsoft.com/library/78f064c3-5b96-373e-e7f0-8603aedc5ded%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed/my/MentionFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myMentionFeed) <br/> SSOM： [GetMentions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetMentions.aspx) <br/> |
|获取未读取的提及当前用户的数量  <br/> |CSOM： [GetUnreadMentionCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetUnreadMentionCount.aspx) <br/> JSOM： [getUnreadMentionCount](http://msdn.microsoft.com/library/18dde16a-f78f-f65e-0644-4eb737b1ae00%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.feed/my/UnreadMentionCount](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myUnreadMentionCount) <br/> SSOM： [GetUnreadMentionCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetUnreadMentionCount.aspx) <br/> |
|锁定（解锁）当前用户的订阅源中的线索  <br/> |CSOM： [LockThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.LockThread.aspx) ( [UnlockThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.UnlockThread.aspx) ) <br/> JSOM： [lockThread](http://msdn.microsoft.com/library/cc696bb7-e7fd-7a57-5db5-736c3733589e%28Office.15%29.aspx) ( [unlockThread](http://msdn.microsoft.com/library/ee9288d6-ace0-1ec2-ea7c-0ee300b6e1ea%28Office.15%29.aspx))  <br/> REST： **POST** [<siteUri>/_api/social.feed/Post/Lock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLock) ( [<siteUri>/_api/social.feed/Post/Unlock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlock)) 并在请求正文中传递  _ID_ 参数 <br/> SSOM： [LockThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.LockThread.aspx) ( [UnlockThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.UnlockThread.aspx) ) <br/> |
   

> **注释**
> REST 示例中的  _domain\\\\user_ 占位符值应替换为实际用户的帐户名。如要查看如何在请求正文中传递 REST 参数，请参阅好友动态订阅源 REST API 参考中的 [示例](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_exampleRequests)。 
  
    
    

SharePoint Server 2013 不提供 API 直接自定义微博文章的布局或呈现。SharePoint Server 2013 仅提供数据，使跨平台和跨设备客户端应用程序可以定义适合其外形结构和需要的布局。在 SharePoint 2013 开发中，可以在客户端呈现中使用 JavaScript 覆盖，如 [使用客户端呈现在 SharePoint 外接程序中自定义列表视图](http://msdn.microsoft.com/library/8d5cabb2-70d0-46a0-bfe0-9e21f8d67d86%28Office.15%29.aspx)中所述。
  
    
    

## 我的网站社交 API 中的订阅源类型概览
<a name="bkmk_FeedTypes"> </a>

订阅源类型表示订阅源数据的类型。检索当前用户的订阅源时，您可以指定以下订阅源类型：
  
    
    

- **Personal** 包含用户生成的帖子和更新。在"我的网站"上，此订阅源显示在用户的"关于我"页上。
    
  
- **News** 包含当前用户以及该用户关注的好友和内容所生成的帖子和更新。检索 **News** 订阅源类型时，请使用 **ByModifiedTime** 分类顺序选项从该用户关注的好友那里获取最近（缓存）的活动。在"我的网站"上，此订阅源显示在用户的"新闻源"页上。
    
  
- **Timeline** 包含当前用户以及该用户关注的好友和内容所生成的文章和更新。当您想要从特定时间范围馈入数据时或您想要使用 **ByCreatedTime** 选项（该选项包括好友的最大抽样）进行分类时， **Timeline** 特别有用。
    
  
- **Likes** 包含具有 **PostReference** 属性的引用线索，该属性表示当前用户标记为"喜欢" 属性的文章。
    
  
- **Everyone** 包含来自当前用户的整个组织的线索。
    
  
服务器、客户端和 JavaScript 对象模型提供您可用于检索当前用户的任何订阅源类型的 **GetFeed** 方法和您可用于检索特定用户的 **Personal** 订阅源类型（仅）的 **GetFeedFor** 方法。两种方法都将 **SocialFeedOptions** 对象视作参数，您可用其指定基于时间的分类顺序、日期范围和要返回的最大线索数量。
  
    
    

> **注释**
> REST 服务提供单独的资源以检索每个订阅源类型，如表 2 所示。 
  
    
    

如果线索包含两个以上的回复，则服务器返回仅包含最近的两则回复的线索摘要。（线索摘要应用了 **IsDigest** 线索属性。）如果您想要获取线索中的所有回复，请从订阅源管理器对象调用 **GetFullThread** 方法，并传递线索标识符。
  
    
    

## 其他资源
<a name="bkmk_AdditionalResources"> </a>


- **概念性和帮助文章**
    
  
-  [SharePoint 2013 中的社交和协作功能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)
    
  
-  [如何：使用 SharePoint 2013 中的 JavaScript 对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)
    
  
-  [如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
    
  
-  [如何：在 SharePoint Server 2013 中的文章中嵌入图像、视频和文档](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md)
    
  
-  [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  
- **API 参考文档**
    
  
-  [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) （客户端对象模型）
    
  
-  [SP.Social 命名空间](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx)（JavaScript 对象模型）
    
  
-  [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) （服务器对象模型）
    
  
