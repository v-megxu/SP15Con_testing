---
title: SharePoint 2013 的好友动态订阅源 REST API 引用
ms.prod: SHAREPOINT
ms.assetid: f1cb914f-1e91-4e23-bf53-d2ab323eac13
---



# SharePoint 2013 的好友动态订阅源 REST API 引用
查找 SharePoint REST 端点，以使用 **SocialRestFeedManager** 资源读取和写入到好友动态订阅源。
您可以使用 SharePoint 2013 代表性状态传输 (REST) 服务来执行与 .NET 客户端对象模型和 JavaScript 对象模型相同的操作。REST 服务会公开 SharePoint 对象、属性和方法对应的资源。要使用 REST 服务，需构建 HTTP **GET** 和 **POST** 请求，并将其发送至表示您想要执行的任务的资源终结点。
  
    
    

大部分订阅源任务的终结点 URI 以 **SocialRestFeedManager** 资源 ( `social.feed`) 开头，后跟  `my` 资源或 `post` 资源：
-  `my` 资源代表当前用户。在终结点 URI 中内嵌使用时，它会将请求的上下文设置为当前用户。例如， `http://contoso.com/_api/social.feed/my/news` 将获取当前用户的新闻源。
    
  
-  `post` 资源代表特定的主题或文章。在终结点 URI 中内嵌使用时，它会将请求的上下文设置为指定主题或文章。例如， `http://contoso.com/_api/social.feed/post/lock` 会锁定指定主题。
    
  
如果资源终结点接受某个参数，参数元数据将在 URI 或请求正文中指定。默认情况下，REST 服务将返回 Atom 协议格式的响应，但您可以使用 HTTP **Accept** 标头请求 JSON 格式。请参阅 [订阅源任务的示例 REST 请求](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_exampleRequests)查看完整请求的示例。
## 订阅源任务的资源终结点
<a name="bk_Overview"> </a>


|||
|:-----|:-----|
| [My](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_my) <br/> |获取有关当前用户的信息。  <br/> |
| [My/Feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeedPost) <br/> |在当前用户的订阅源中创建根文章。  <br/> |
| [My/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeed) <br/> |获取当前用户的活动订阅源。  <br/> |
| [My/News](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myNews) <br/> |获取当前用户和好友的活动订阅源及用户关注的内容  <br/> |
| [My/TimelineFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myTimelineFeed) <br/> |获取当前用户和好友的活动订阅源及用户关注的内容，按创建日期排序。  <br/> |
| [My/Likes](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myLikes) <br/> |获取当前用户喜欢的文章的订阅源。  <br/> |
| [My/MentionFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myMentionFeed) <br/> |获取当前用户提及的文章的订阅源。  <br/> |
| [My/MentionFeed/ClearUnreadMentionCount](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myMentionFeedClearUnreadMentionCount) <br/> |获取当前用户提到的文章的订阅源并清除未读的提及订阅源数量。  <br/> |
| [My/UnreadMentionCount](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myUnreadMentionCount) <br/> |获取当前用户提及的未读订阅源数量。  <br/> |
| [Actor](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actor) <br/> |获取有关指定用户和当前用户的信息。  <br/> |
| [Actor/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> |获取指定用户的活动订阅源。  <br/> |
| [Actor/Feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeedPost) <br/> |在指定网站源中创建根文章。  <br/> |
| [文章](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_post) <br/> |获取包含指定文章的完整主题。  <br/> |
| [Post/Reply](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postReply) <br/> |发布对指定文章的回复。  <br/> |
| [Post/Delete](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postDelete) <br/> |删除指定文章。  <br/> |
| [Post/Like](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLike) <br/> |使当前用户成为指定文章的关注者。  <br/> |
| [Post/Unlike](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlike) <br/> |将当前用户从指定文章的关注者列表中移除。  <br/> |
| [Post/Likers](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLikers) <br/> |获取喜欢指定文章的用户。  <br/> |
| [Post/Lock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLock) <br/> |锁定指定主题。  <br/> |
| [Post/Unlock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlock) <br/> |解锁指定主题。  <br/> |
   

> **注释**
>  以下主题相关的 REST 资源使用与其他 SharePoint REST API 相同的模式来构建终结点 URI。>  对于 **CreateImageAttachment**，向  `http://<siteCollection>/<site>/_api/SP.Social.SocialFeedManager/CreateImageAttachment` 发送一个 **POST** 请求>  对于 **GetPreview**，向  `http://<siteCollection>/<site>/_api/SP.Social.SocialFeedManager/GetPreview` 发送一个 **POST** 请求>  对于 **SuppressThreadNotifications**，向  `http://<siteCollection>/<site>/_api/SP.Social.SocialFeedManager/SuppressThreadNotifications` 发送一个 **POST** 请求
  
    
    


## My
<a name="bk_my"> </a>

获取有关当前用户的信息。
  
    
    
 **my** 终结点将当前用户设置为 URI 中任何后续资源的上下文。例如， `http://contoso.com/_api/social.feed/my/news` 可获取当前用户的新闻源。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my`
  
    
    

### 请求参数

无。
  
    
    

### 响应

类型： [SP.Social.SocialRestActor](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestActor)
  
    
    
关于当前用户的信息。
  
    
    
您可以在 URI 中分别别调用 **SocialRestActor** 属性，例如， `http://<siteCollection>/<site>/_api/social.feed/my/me` 仅获取 **Me** 属性。
  
    
    
以下响应示例表示关于当前用户的信息。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my",
    "uri":"http://serverName/sites/dev/_api/social.feed/my",
    "type":"SP.Social.SocialRestActor"
   },
  "FollowableItem":"domain\\\\username1",
  "FollowableItemActor":null,
  "Me":{
    "__metadata":{"type":"SP.Social.SocialActor"},
    "AccountName":"domain\\\\username1",
    "ActorType":0,
    "CanFollow":false,
    "ContentUri":null,
    "EmailAddress":null,
    "FollowedContentUri":null,
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
    "ImageUri":null,
    "IsFollowed":false,
    "LibraryUri":null,
    "Name":"User1 Name",
    "PersonalSiteUri":"http://serverName/my/personal/username1/",
    "Status":0,
    "StatusText":"This is post 2",
    "TagGuid":"00000000-0000-0000-0000-000000000000",
    "Title":null,
    "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
  }
}}
```


## My/Feed/Post
<a name="bk_myFeedPost"> </a>

在当前用户的订阅源中创建根文章。
  
    
    
您只能在当前用户的上下文中发布内容。您无法在不同用户的订阅源中创建根文章，但您可以回复其他用户的文章。请参阅  [Post/Reply](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postReply)。
  
    
    

> **注释**
> 请勿将此  `Post` 资源与表示指定主题或文章的 `Post` 资源相混淆。
  
    
    


### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/my/feed/post`
  
    
    

### 请求参数

 _restCreationData_
  
    
    
类型： [SP.Social.SocialRestPostCreationData](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestPostCreationData)
  
    
    
新文章的一个 **null** ID 和属性，如下例所示。
  
    
    

```

"restCreationData":{
  "__metadata":{
    "type":"SP.Social.SocialRestPostCreationData"
  },
  "ID":null,
  "creationData":{
    "__metadata":{
      "type":"SP.Social.SocialPostCreationData"
    },
    "ContentText":"This post was published using REST.", 
    "UpdateStatusText":false
  }
}
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
包含新的根文章的主题。
  
    
    
以下响应示例展示了包含新的根文章的主题。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username1",
        "ActorType":0, 
        "CanFollow":false, 
        "ContentUri":null, 
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":false, 
        "LibraryUri":null, 
        "Name":"User1 Name",
        "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
        "Status":0, 
        "StatusText":"",
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
      }]
    },
    "Attributes":6,
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "OwnerIndex":0,
    "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "PostReference":null, 
    "Replies":{"results":[]},
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:31:57.204511Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-17T19:31:57.204511Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0,
    "ThreadType":0,
    "TotalReplyCount":0
  }
}}
```


## My/Feed
<a name="bk_myFeed"> </a>

获取当前用户的活动订阅源（ **Personal** 源类型）。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/feed`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/feed(MaxThreadCount=10,SortOrder=1,NewerThan=@v)?@v=datetime'2013-01-01T08:00'`
  
    
    

### 请求参数

 _feedOptions_（可选）
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
主题的最大数量、日期-时间范围和排序顺序。您可以选择性地指定这些属性的任意组合，例如，您可以仅指定 **MaxThreadCount** 属性。
  
    
    
您可以使用一个 **@** 别名传递特殊字符。例如， `<siteUri>/_api/social.feed/my/feed(OlderThan=@v)?@v=datetime'2013-01-01T08:00'` 使用 **@v** 别名发送一个 **:** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
当前用户的个人订阅源。
  
    
    
以下响应示例表示当前用户的个人订阅源。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my/feed",
    "uri":"http://serverName/sites/dev/_api/social.feed/my/feed",
    "type":"SP.Social.SocialRestFeed"
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"},
    "Attributes":1, 
    "NewestProcessed":"2013-04-15T06:10:11Z",
    "OldestProcessed":"2013-04-15T05:33:12Z",
    "Threads":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":null, 
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          },{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
            "IsFollowed":true, 
            "LibraryUri":null, 
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName/my/personal/username2",
            "Status":6, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
          }]
        },
        "Attributes":6, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "PostReference":null, 
        "Replies":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialPost"},
            "Attachment":null, 
            "Attributes":23, 
            "AuthorIndex":1, 
            "CreatedTime":"2013-04-15T06:10:11.3480926Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.59c0273c6c7b41e784b496c9aaa909a8.17.24.S-1-5-21-2127521184-1604012920-1887927527-66602",
            "LikerInfo":{
              "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
              "IncludesCurrentUser":false,
              "Indexes":{"results":[]},
              "TotalCount":0
            },
            "ModifiedTime":"2013-04-15T06:10:11.3480926Z",
            "Overlays":{"results":[]},
            "PostType":1, 
            "PreferredImageUri":null, 
            "Source":{
              "__metadata":{"type":"SP.Social.SocialLink"},
              "Text":null, 
              "Uri":null
            },
            "Text":"This is a reply to post 1."
          }]
        },
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null,
          "Attributes":23, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-15T05:58:24Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false,
            "Indexes":{"results":[]},
            "TotalCount":0
          },
          "ModifiedTime":"2013-04-15T06:10:11Z",
          "Overlays":{"results":[]},
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"This is post 1." 
        },
        "Status":0, 
        "ThreadType":0, 
        "TotalReplyCount":1
      },{
      "__metadata":{"type":"SP.Social.SocialThread"},
      "Actors":{
        "results":[{
          "__metadata":{"type":"SP.Social.SocialActor"},
          "AccountName":"domain\\\\username1",
          "ActorType":0, 
          "CanFollow":false, 
          "ContentUri":null, 
          "EmailAddress":null, 
          "FollowedContentUri":null, 
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
          "ImageUri":null, 
          "IsFollowed":false, 
          "LibraryUri":null, 
          "Name":"User1 Name",
          "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
          "Status":0, 
          "StatusText":"",
          "TagGuid":"00000000-0000-0000-0000-000000000000",
          "Title":null, 
          "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
        }]
      },
      "Attributes":6, 
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "OwnerIndex":0, 
      "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "PostReference":null, 
      "Replies":{"results":[]},
      "RootPost":{
        "__metadata":{"type":"SP.Social.SocialPost"},
        "Attachment":null, 
        "Attributes":23, 
        "AuthorIndex":0, 
        "CreatedTime":"2013-04-15T06:07:05Z",
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "LikerInfo":{
          "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
          "IncludesCurrentUser":false, 
          "Indexes":{"results":[]},
          "TotalCount":0},
          "ModifiedTime":"2013-04-15T06:07:05Z",
          "Overlays":{"results":[]},
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null,"Uri":null},
            "Text":"This is post 2." 
          }, 
          "Status":0, 
          "ThreadType":0, 
          "TotalReplyCount":0
        },{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":null, 
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          },{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
            "IsFollowed":true, 
            "LibraryUri":null, 
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName/my/personal/username2",
            "Status":6, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
          }]
      },
      "Attributes":0, 
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.cecc0de3d7d04520bb87a181b24c105a.16.16.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "OwnerIndex":0, 
      "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
      "PostReference":{
        "__metadata":{"type":"SP.Social.SocialPostReference"},
        "Digest":null, 
        "Post":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":1, 
          "CreatedTime":"2013-04-15T05:05:13Z",
          "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":true, 
            "Indexes":{"results":[]},
            "TotalCount":1
          },
          "ModifiedTime":"2013-04-15T05:05:13Z",
          "Overlays":{
            "results":[{
              "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[0]}, 
              "Index":1, 
              "Length":18, 
              "LinkUri":null, 
              "OverlayType":1
            }]
          },
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"@User1 Name presented at the conference."}, 
          "ThreadId":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
          "ThreadOwnerIndex":1
        },
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":14, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-15T05:33:12Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.cecc0de3d7d04520bb87a181b24c105a.16.16.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":null, 
          "ModifiedTime":"2013-04-15T05:33:12Z",
          "Overlays":{
            "results":[{
              "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[0]}, 
              "Index":0, 
              "Length":18, 
              "LinkUri":null, 
              "OverlayType":1
            },{
            "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[1]}, 
              "Index":35, 
              "Length":10, 
              "LinkUri":null, 
              "OverlayType":1
            }]
          },
          "PostType":0, 
          "PreferredImageUri":"http://serverName:80/_layouts/15/Images/Like.11x11x32.png",
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null,"Uri":null
          },
          "Text":"User1 Name liked a post by User2 Name."
        }, 
        "Status":0, 
        "ThreadType":1, 
        "TotalReplyCount":0
      }]
    },
    "UnreadMentionCount":1
  }
}}
```


## My/News
<a name="bk_myNews"> </a>

获取当前用户和好友的活动订阅源及用户关注的内容，按最后修改日期排序（ **News** 订阅源类型）。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/news`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/news(MaxThreadCount=10,NewerThan=@v)?@v=datetime'2013-01-01T08:00'`
  
    
    

### 请求参数

 _feedOptions_（可选）
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
主题的最大数量、日期-时间范围和排序顺序。您可以选择性地指定这些属性的任意组合，例如，您可以仅指定 **MaxThreadCount** 属性。
  
    
    
您可以使用一个 **@** 别名传递特殊字符。例如， `<siteUri>/_api/social.feed/my/News(OlderThan=@v)?@v=datetime'2013-01-01T08:00'` 使用 **@v** 别名发送一个 **:** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
当前用户的新闻源。
  
    
    
以下响应示例表示当前用户的新闻源。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my/news",
    "uri":"http://serverName/sites/dev/_api/social.feed/my/news",
    "type":"SP.Social.SocialRestFeed"
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"},
    "Attributes":1, 
    "NewestProcessed":"2013-04-15T06:10:11.4730902Z",
    "OldestProcessed":"2013-04-12T20:51:51Z",
    "Threads":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":"http://serverName:80/my/_layouts/15/MySite.aspx?MySiteRedirect=FollowedDocuments",
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          },{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
            "IsFollowed":true, 
            "LibraryUri":null, 
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName/my/personal/username2",
            "Status":0, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
          }]
        },
        "Attributes":6, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "PostReference":null, 
        "Replies":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialPost"},
            "Attachment":null, 
            "Attributes":23, 
            "AuthorIndex":1, 
            "CreatedTime":"2013-04-15T06:10:11.3480926Z",
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.59c0273c6c7b41e784b496c9aaa909a8.17.24.S-1-5-21-2127521184-1604012920-1887927527-66602",
            "LikerInfo":{
              "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
              "IncludesCurrentUser":false, 
              "Indexes":{"results":[]},
              "TotalCount":0
            },
            "ModifiedTime":"2013-04-15T06:10:11.3480926Z",
            "Overlays":{"results":[]},
            "PostType":1, 
            "PreferredImageUri":null, 
            "Source":{
              "__metadata":{"type":"SP.Social.SocialLink"},
              "Text":null, 
              "Uri":null
            },
            "Text":"This is a reply to post 1." 
          }]
        },
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-15T05:58:24Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false, 
            "Indexes":{"results":[]},
            "TotalCount":0},
            "ModifiedTime":"2013-04-15T06:10:11.4730902Z",
            "Overlays":{"results":[]},
            "PostType":0, 
            "PreferredImageUri":null, 
            "Source":{
              "__metadata":{"type":"SP.Social.SocialLink"},
              "Text":null, 
              "Uri":null
            },
            "Text":"This is post 1." 
          },
          "Status":0, 
          "ThreadType":0, 
          "TotalReplyCount":1
        },{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":"http://serverName:80/my/_layouts/15/MySite.aspx?MySiteRedirect=FollowedDocuments",
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          }]
        },
        "Attributes":6, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "PostReference":null, 
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-15T06:07:05.4804434Z","Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false, 
            "Indexes":{"results":[]},
            "TotalCount":0
          },
          "ModifiedTime":"2013-04-15T06:07:05.4804434Z",
          "Overlays":{"results":[]},
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"This is post 2." 
        },
        "Status":0, 
        "ThreadType":0, 
        "TotalReplyCount":0
      }]
    },
    "UnreadMentionCount":1
  }
}}
```


## My/TimelineFeed
<a name="bk_myTimelineFeed"> </a>

获取当前用户和好友的活动订阅源及用户关注的内容，按创建日期排序（ **Timeline** 订阅源类型）。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/timelinefeed`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/timelinefeed(MaxThreadCount=10,NewerThan=@v)?@v=datetime'2013-01-01T08:00'`
  
    
    

### 请求参数

 _feedOptions_（可选）
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
主题的最大数量、日期-时间范围和排序顺序。您可以选择性地指定这些属性的任意组合，例如，您可以仅指定 **MaxThreadCount** 属性。
  
    
    
您可以使用一个 **@** 别名传递特殊字符。例如， `<siteUri>/_api/social.feed/my/timelinefeed(OlderThan=@v)?@v=datetime'2013-01-01T08:00'` 使用 **@v** 别名发送一个 **:** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
当前用户的时间线订阅源。
  
    
    
以下响应示例表示当前用户的时间线订阅源，按创建日期排序。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my/timelinefeed",
    "uri":"http://serverName/sites/dev/_api/social.feed/my/timelinefeed",
    "type":"SP.Social.SocialRestFeed"
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"},
    "Attributes":1, 
    "NewestProcessed":"2013-04-15T06:07:05.4804434Z",
    "OldestProcessed":"2013-04-12T20:51:51Z",
    "Threads":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":"http://serverName:80/my/_layouts/15/MySite.aspx?MySiteRedirect=FollowedDocuments",
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"This is post 2.", 
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          }]
        },
        "Attributes":6, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "PostReference":null, 
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-15T06:07:05.4804434Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.82e71ca2381b4657935546e57f1992d5.23.23.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false, 
            "Indexes":{"results":[]},
            "TotalCount":0
          },
          "ModifiedTime":"2013-04-15T06:07:05.4804434Z",
          "Overlays":{"results":[]},
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"This is post 2." 
        },
        "Status":0, 
        "ThreadType":0, 
        "TotalReplyCount":0
      },{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":"http://serverName:80/my/_layouts/15/MySite.aspx?MySiteRedirect=FollowedDocuments",
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"This is post 2.", 
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          }]
        },
        "Attributes":6, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "PostReference":null, 
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-15T05:58:24Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false, 
            "Indexes":{"results":[]},
            "TotalCount":0
          },
          "ModifiedTime":"2013-04-15T06:04:49Z",
          "Overlays":{"results":[]},
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"This is post 1." 
        },
        "Status":0, 
        "ThreadType":0, 
        "TotalReplyCount":0
      }]
    },
    "UnreadMentionCount":1
  }
}}
```


## My/Likes
<a name="bk_myLikes"> </a>

获取当前用户喜欢的微博文章的订阅源，按 **LikeReference** 主题类型呈现。请参阅 [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/likes`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/likes(MaxThreadCount=10,SortOrder=1,NewerThan=@v)?@v=datetime'2013-01-01T08:00'`
  
    
    

### 请求参数

 _feedOptions_（可选）
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
主题的最大数量、日期-时间范围和排序顺序。您可以选择性地指定这些属性的任意组合，例如，您可以仅指定 **MaxThreadCount** 属性。
  
    
    
您可以选择在查询字符串中指定检索选项。您可以使用 **@** 别名传递特殊字符。例如， `<siteUri>/_api/social.feed/my/likes(OlderThan=@v)?@v=datetime'2013-01-01T08:00'` 使用 **@v** 别名发送 **:** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
包含当前用户喜欢的文章的订阅源。
  
    
    
以下响应示例表示对当前用户喜欢的文章的引用。主题为 **LikeReference** 主题类型（值 = **1**），其 **PostReference** 属性会引用实际文章。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my/likes",
    "uri":"http://serverName/sites/dev/_api/social.feed/my/likes",
    "type":"SP.Social.SocialRestFeed"
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"}.
    "Attributes":1,
    "NewestProcessed":"2013-04-15T05:33:12Z",
    "OldestProcessed":"2013-04-15T05:33:12Z",
    "Threads":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0,
            "CanFollow":false,
            "ContentUri":null,
            "EmailAddress":null,
            "FollowedContentUri":null,
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"This is post 2",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null,
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          },{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
            "IsFollowed":true, 
            "LibraryUri":null, 
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName/my/personal/username2",
            "Status":6, 
            "StatusText":"@User1 Name presented at the conference.",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"}]
          },
          "Attributes":0, 
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.cecc0de3d7d04520bb87a181b24c105a.16.16.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "OwnerIndex":0, 
          "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
          "PostReference":{
            "__metadata":{"type":"SP.Social.SocialPostReference"},
            "Digest":null, 
            "Post":{
              "__metadata":{"type":"SP.Social.SocialPost"},
              "Attachment":null, 
              "Attributes":23, 
              "AuthorIndex":1, 
              "CreatedTime":"2013-04-15T05:05:13Z",
              "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
              "LikerInfo":{
                "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
                "IncludesCurrentUser":true, 
                "Indexes":{"results":[]},
                "TotalCount":1
              },
              "ModifiedTime":"2013-04-15T05:05:13Z",
              "Overlays":{
                "results":[{
                  "__metadata":{"type":"SP.Social.SocialDataOverlay"},
                  "ActorIndexes":{"results":[0]}, 
                  "Index":1, 
                  "Length":18, 
                  "LinkUri":null, 
                  "OverlayType":1
                }]
              },
              "PostType":0, 
              "PreferredImageUri":null, 
              "Source":{
                "__metadata":{"type":"SP.Social.SocialLink"},
                "Text":null, 
                "Uri":null
              },
              "Text":"@User1 Name presented at the conference." 
            },
            "ThreadId":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
            "ThreadOwnerIndex":1
          },
          "Replies":{"results":[]},
          "RootPost":{
            "__metadata":{"type":"SP.Social.SocialPost"},
            "Attachment":null, 
            "Attributes":14, 
            "AuthorIndex":0, 
            "CreatedTime":"2013-04-15T05:33:12Z",
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.cecc0de3d7d04520bb87a181b24c105a.16.16.S-1-5-21-2127521184-1604012920-1887927527-66602",
            "LikerInfo":null, 
            "ModifiedTime":"2013-04-15T05:33:12Z",
            "Overlays":{
              "results":[{
                "__metadata":{"type":"SP.Social.SocialDataOverlay"},
                "ActorIndexes":{"results":[0]}, 
                "Index":0, 
                "Length":18, 
                "LinkUri":null, 
                "OverlayType":1
              },{
                "__metadata":{"type":"SP.Social.SocialDataOverlay"},
                "ActorIndexes":{"results":[1]}, 
                "Index":35, 
                "Length":10, 
                "LinkUri":null, 
                "OverlayType":1
              }]
            },
            "PostType":0, 
            "PreferredImageUri":"http://serverName:80/_layouts/15/Images/Like.11x11x32.png",
            "Source":{
              "__metadata":{"type":"SP.Social.SocialLink"},
              "Text":null, 
              "Uri":null
            },
            "Text":"User1 Name liked a post by User2 Name." 
          },
          "Status":0, 
          "ThreadType":1, 
          "TotalReplyCount":0
        }]
      },
    "UnreadMentionCount":1
  }
}}
```


## My/MentionFeed
<a name="bk_myMentionFeed"> </a>

获取提及当前用户的微博文章的订阅源，按 **MentionReference** 主题类型呈现。请参阅 [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/mentionfeed`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/mentionfeed(MaxThreadCount=10,SortOrder=1,NewerThan=@v)?@v=datetime'2013-01-01T08:00'`
  
    
    

### 请求参数

 _feedOptions_（可选）
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
主题的最大数量、日期-时间范围和排序顺序。您可以选择性地指定这些属性的任意组合，例如，您可以仅指定 **MaxThreadCount** 属性。
  
    
    
您可以使用一个 **@** 别名传递特殊字符。例如， `<siteUri>/_api/social.feed/my/likes(OlderThan=@v)?@v=datetime'2013-01-01T08:00'` 使用 **@v** 别名发送一个 **:** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
包含提及当前用户的文章的订阅源。
  
    
    
以下响应示例表示提及当前用户的主题。主题为 **MentionReference** 主题类型（值 = **3**），其 **PostReference** 属性会引用实际文章。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my/mentionfeed",
    "uri":"http://serverName/sites/dev/_api/social.feed/my/mentionfeed",
    "type":"SP.Social.SocialRestFeed"
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"},
    "Attributes":1,
    "NewestProcessed":"2013-04-15T05:05:19Z",
    "OldestProcessed":"2013-04-15T05:05:19Z",
    "Threads":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":null, 
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
            "Status":0, 
            "StatusText":"This is post 2",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          },{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
            "IsFollowed":true, 
            "LibraryUri":null, 
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName/my/personal/username2",
            "Status":6, 
            "StatusText":"@User1 Name presented at the conference.", 
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
          }]
        },
        "Attributes":0, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ec5198399300401fb44f0f5c9d8dea80.15.15.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
        "PostReference":{
          "__metadata":{"type":"SP.Social.SocialPostReference"},
          "Digest":null,
          "Post":{
            "__metadata":{"type":"SP.Social.SocialPost"},
            "Attachment":null,
            "Attributes":23,
            "AuthorIndex":1,
            "CreatedTime":"2013-04-15T05:05:12.0102795Z",
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
            "LikerInfo":{
              "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
              "IncludesCurrentUser":false,
              "Indexes":{"results":[]},
              "TotalCount":0
            },
            "ModifiedTime":"2013-04-15T05:05:12.0102795Z",
            "Overlays":{
              "results":[{
                "__metadata":{"type":"SP.Social.SocialDataOverlay"},
                "ActorIndexes":{"results":[0]},
                "Index":1,
                "Length":18,
                "LinkUri":null,
                "OverlayType":1
              }]
            },
            "PostType":0,
            "PreferredImageUri":null,
            "Source":{
              "__metadata":{"type":"SP.Social.SocialLink"},
              "Text":null,
              "Uri":null
            },
            "Text":"@User1 Name presented at the conference."
          },
          "ThreadId":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
          "ThreadOwnerIndex":1
        },
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null,
          "Attributes":14, 
          "AuthorIndex":1, 
          "CreatedTime":"2013-04-15T05:05:19Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ec5198399300401fb44f0f5c9d8dea80.15.15.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":null, 
          "ModifiedTime":"2013-04-15T05:05:19Z",
          "Overlays":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialDataOverlay"},
            "ActorIndexes":{"results":[1]}, 
            "Index":13, 
            "Length":10, 
            "LinkUri":null, 
            "OverlayType":1
          }]
        },
        "PostType":0, 
        "PreferredImageUri":"http://serverName:80/_layouts/15/Images/mention.11x11x32.png",
        "Source":{
          "__metadata":{"type":"SP.Social.SocialLink"},
          "Text":null,
          "Uri":null
        },
        "Text":"Mentioned by User2 Name."},
        "Status":0,
        "ThreadType":3,
        "TotalReplyCount":0
      }]
    },
    "UnreadMentionCount":1
  }
}}
```


## My/MentionFeed/ClearUnreadMentionCount
<a name="bk_myMentionFeedClearUnreadMentionCount"> </a>

获取提及当前用户的微博文章，按 **MentionReference** 主题类型呈现，并将用户未读的提及订阅源数量设置为 0。请参阅 [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/my/mentionfeed/clearunreadmentioncount`
  
    
    

### 请求参数

 _feedOptions_
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
此参数必须作为请求正文的 **data** 属性中的空字符串发送，如以下示例中所示。
  
    
    

```

'feedOptions': {
  '__metadata': {
    'type': 'SP.Social.SocialFeedOptions'
  }, 
}
```


### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
当前用户提及的订阅源。
  
    
    
以下响应示例表示当前用户提及的订阅源。主题为 **MentionReference** 主题类型（值 = **3**），其 **PostReference** 属性会引用实际文章。检索订阅源之后，未读的提及订阅源数量将清除。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/my/mentionfeed",
    "uri":"http://serverName/sites/dev/_api/social.feed/my/mentionfeed",
    "type":"SP.Social.SocialRestFeed" 
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"},
    "Attributes":1,
    "NewestProcessed":"2013-04-15T05:05:19Z",
    "OldestProcessed":"2013-04-15T05:05:19Z",
    "Threads":{
      "results":[{
      "__metadata":{"type":"SP.Social.SocialThread"},
      "Actors":{
        "results":[{
          "__metadata":{"type":"SP.Social.SocialActor"},
          "AccountName":"domain\\\\username1",
          "ActorType":0, 
          "CanFollow":false, 
          "ContentUri":null, 
          "EmailAddress":null, 
          "FollowedContentUri":null, 
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
          "ImageUri":null, 
          "IsFollowed":false, 
          "LibraryUri":null, 
          "Name":"User1 Name",
          "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
          "Status":0, 
          "StatusText":"Posted with REST.", 
          "TagGuid":"00000000-0000-0000-0000-000000000000",
          "Title":null, 
          "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
        },{
          "__metadata":{"type":"SP.Social.SocialActor"},
          "AccountName":"domain\\\\username2",
          "ActorType":0, 
          "CanFollow":true, 
          "ContentUri":null, 
          "EmailAddress":"username2@somecompany.com",
          "FollowedContentUri":null, 
          "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
          "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
          "IsFollowed":true, 
          "LibraryUri":null, 
          "Name":"User2 Name",
          "PersonalSiteUri":"http://serverName/my/personal/username2",
          "Status":6, 
          "StatusText":"This is post 1 from the specified user.", 
          "TagGuid":"00000000-0000-0000-0000-000000000000",
          "Title":"SOME TITLE",
          "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
        }]
      },
      "Attributes":0, 
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ec5198399300401fb44f0f5c9d8dea80.15.15.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "OwnerIndex":0, 
      "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
      "PostReference":{
        "__metadata":{"type":"SP.Social.SocialPostReference"},
        "Digest":null, 
        "Post":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":1, 
          "CreatedTime":"2013-04-15T05:05:12.0102795Z",
          "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false, 
            "Indexes":{"results":[]},
            "TotalCount":0
          },
          "ModifiedTime":"2013-04-15T05:05:12.0102795Z",
          "Overlays":{
            "results":[{
              "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[0]}, 
              "Index":1, 
              "Length":18, 
              "LinkUri":null, 
              "OverlayType":1
            }]
          },
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"@User1 Name presented at the conference."}, 
          "ThreadId":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.ca83f758aab04065bc303398f2701eb9.10.10.S-1-5-21-124525095-708259637-1543119021-628175",
          "ThreadOwnerIndex":1
        },
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":14, 
          "AuthorIndex":1, 
          "CreatedTime":"2013-04-15T05:05:19Z",
          "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ec5198399300401fb44f0f5c9d8dea80.15.15.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "LikerInfo":null, 
          "ModifiedTime":"2013-04-15T05:05:19Z",
          "Overlays":{
            "results":[{
              "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[1]}, 
              "Index":13, 
              "Length":10, 
              "LinkUri":null, 
              "OverlayType":1
            }]
          },
          "PostType":0, 
          "PreferredImageUri":"http://serverName:80/_layouts/15/Images/mention.11x11x32.png",
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"Mentioned by User2 Name."
        }, 
        "Status":0, 
        "ThreadType":3, 
        "TotalReplyCount":0
      }]
    },
    "UnreadMentionCount":1
  }
}}
```


## My/UnreadMentionCount
<a name="bk_myUnreadMentionCount"> </a>

获取当前用户未读的提及订阅源数量。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/my/unreadmentioncount`
  
    
    

### 请求参数

无。
  
    
    

### 响应

类型： **Int32**
  
    
    
当前用户提及的未读订阅源数量。
  
    
    
以下响应示例表示未读的提及订阅源数量为 1。
  
    
    



```

{"d":{"UnreadMentionCount":1}}
```


## Actor
<a name="bk_actor"> </a>

获取有关指定用户和当前用户的信息。
  
    
    

> **注释**
>  `actor` 终结点将指定用户或网站源设置为 URI 中任何后续资源的上下文。例如， `http://contoso.com/_api/social.feed/actor(item='domain\\\\user')/feed` 可获取指定用户的个人订阅源， `http://contoso.com/_api/social.feed/actor(item=@v)/feed?@v='http://<server>/<teamSite>/newsfeed.aspx'` 可获取指定团队网站的网站源。
  
    
    


### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/actor(item='domain\\\\user')`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/actor(item=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 请求参数

 _item_
  
    
    
类型： **String**
  
    
    
指定用户的帐户名称。
  
    
    
您可在查询字符串中发送  _item_ 参数。您可以使用 **@** 别名传递特殊字符，例如 `<siteUri>/_api/social.feed/actor(item=@v)?@v='i:0"%23".f|membership|user@domain.com'` 使用 **@v** 别名和 **"%23"** 编码发送 **#** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestActor](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestActor)
  
    
    
关于指定用户和当前用户的信息。
  
    
    
您可以在 URI 中分别调用 **SocialRestActor** 属性，例如， `http://<siteCollection>/<site>/_api/social.feed/actor(item='domain\\\\user')/followableitem` 仅获取指定用户的 **FollowableItem** 属性。
  
    
    
以下响应示例表示关于指定用户和当前用户的信息。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/actor(Item=@ai)/?@ai='domain\\\\username2'",
    "uri":"http://serverName/sites/dev/_api/social.feed/actor(Item=@ai)/?@ai='domain%5cusername2'",
    "type":"SP.Social.SocialRestActor"
  },
  "FollowableItem":"domain\\\\username2",
  "FollowableItemActor":{
    "__metadata":{"type":"SP.Social.SocialActor"},
    "AccountName":"domain\\\\username2",
    "ActorType":0,
    "CanFollow":true,
    "ContentUri":null,
    "EmailAddress":"username2@somecompany.com",
    "FollowedContentUri":null,
    "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
    "ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
    "IsFollowed":true,
    "LibraryUri":null,
    "Name":"User2 Name",
    "PersonalSiteUri":"http://serverName/my/personal/username2",
    "Status":0,
    "StatusText":"",
    "TagGuid":"00000000-0000-0000-0000-000000000000",
    "Title":"SOME TITLE",
    "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
  },
  "Me":{
    "__metadata":{"type":"SP.Social.SocialActor"},
    "AccountName":"domain\\\\username1",
    "ActorType":0,
    "CanFollow":false,
    "ContentUri":null,
    "EmailAddress":null,
    "FollowedContentUri":null,
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
    "ImageUri":null,
    "IsFollowed":false,
    "LibraryUri":null,
    "Name":"User1 Name",
    "PersonalSiteUri":"http://serverName/my/personal/username1/",
    "Status":0,
    "StatusText":"This is post 2",
    "TagGuid":"00000000-0000-0000-0000-000000000000",
    "Title":null,
    "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
  }
}}
```


## Actor/Feed
<a name="bk_actorFeed"> </a>

获取指定用户的活动订阅源（ **Personal** 订阅源类型）或者获取指定网站源。
  
    
    

### 终结点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.feed/actor(item='domain\\\\user')/feed`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/actor(item=@v)/feed?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/actor(item='domain\\\\user')/feed(MaxThreadCount=10,SortOrder=1,NewerThan=@v)?@v=datetime'2013-01-01T08:00'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/social.feed/actor(item=@v)/feed?@v='http://<teamSiteUri>/newsfeed.aspx'`
  
    
    

### 请求参数

 _feedOptions_（可选）
  
    
    
类型： [SP.Social.SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)
  
    
    
主题的最大数量、日期-时间范围和排序顺序。您可以选择性地指定这些属性的任意组合，例如，您可以仅指定 **MaxThreadCount** 属性。
  
    
    
您可以使用 **@** 别名传递特殊字符。例如， `<siteUri>/_api/social.feed/actor(item=@v)/feed(NewerThan=@x)?@v='i:0"%23".f|membership|user@domain.com'&amp;@x=datetime'2013-01-01T08:00'` 使用 **@v** 别名和 **"%23"** 编码发送 **#** 字符，使用 **@x** 别名发送 **:** 字符。
  
    
    

### 响应

类型： [SP.Social.SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)
  
    
    
指定用户的个人订阅源或指定 URI 的网站源。
  
    
    
以下响应示例表示指定用户的个人订阅源。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/actor(Item=@ai)/feed/?@ai='domain\\\\username2'",
    "uri":"http://serverName/sites/dev/_api/social.feed/actor(Item=@ai)/feed/?@ai='domain%5cusername2'",
    "type":"SP.Social.SocialRestFeed"
  },
  "SocialFeed":{
    "__metadata":{"type":"SP.Social.SocialFeed"},
    "Attributes":1, 
    "NewestProcessed":"2013-04-16T22:40:55Z",
    "OldestProcessed":"2013-04-16T22:40:07Z",
    "Threads":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User%20Photos/Profile%20Pictures/username2_MThumb.jpg",
            "IsFollowed":true, 
            "LibraryUri":null, 
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username2",
            "Status":0, 
            "StatusText":"This is post 1 from the specified user.", 
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
          },{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username1",
            "ActorType":0, 
            "CanFollow":false, 
            "ContentUri":null, 
            "EmailAddress":null, 
            "FollowedContentUri":null, 
            "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":null, 
            "IsFollowed":false, 
            "LibraryUri":null, 
            "Name":"User1 Name",
            "PersonalSiteUri":"http://serverName/my/personal/username1/",
            "Status":0, 
            "StatusText":"",
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":null, 
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
          }]
        },
        "Attributes":0, 
        "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.4cb7a5d36cb14d62b0fb68ef98f9765e.15.15.S-1-5-21-124525095-708259637-1543119021-628175",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "PostReference":{
          "__metadata":{"type":"SP.Social.SocialPostReference"},
          "Digest":null, 
          "Post":null, 
          "ThreadId":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.c554cbf1934b4c82bb1d43ebf961de92.17.17.S-1-5-21-2127521184-1604012920-1887927527-66602",
          "ThreadOwnerIndex":1
        },
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":14, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-16T22:40:55Z",
          "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.4cb7a5d36cb14d62b0fb68ef98f9765e.15.15.S-1-5-21-124525095-708259637-1543119021-628175",
          "LikerInfo":null, 
          "ModifiedTime":"2013-04-16T22:40:55Z",
          "Overlays":{
            "results":[{
              "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[0]}, 
              "Index":0, 
              "Length":10, 
              "LinkUri":null, 
              "OverlayType":1
            },{
              "__metadata":{"type":"SP.Social.SocialDataOverlay"},
              "ActorIndexes":{"results":[1]}, 
              "Index":32, 
              "Length":18, 
              "LinkUri":null, 
              "OverlayType":1
            }]
          },
          "PostType":0, 
          "PreferredImageUri":"http://serverName:80/_layouts/15/Images/RepliedTo.11x11x32.png",
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"User2 Name replied to a post by User1 Name." 
        },
        "Status":0, 
        "ThreadType":2, 
        "TotalReplyCount":0
      },{
        "__metadata":{"type":"SP.Social.SocialThread"},
        "Actors":{
          "results":[{
            "__metadata":{"type":"SP.Social.SocialActor"},
            "AccountName":"domain\\\\username2",
            "ActorType":0, 
            "CanFollow":true, 
            "ContentUri":null, 
            "EmailAddress":"username2@somecompany.com",
            "FollowedContentUri":null, 
            "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b",
            "ImageUri":"http://serverName:80/my/User%20Photos/Profile%20Pictures/username2_MThumb.jpg",
            "IsFollowed":true,
            "LibraryUri":null,
            "Name":"User2 Name",
            "PersonalSiteUri":"http://serverName:80/my/personal/username2",
            "Status":0, 
            "StatusText":"This is post 1 from the specified user.", 
            "TagGuid":"00000000-0000-0000-0000-000000000000",
            "Title":"SOME TITLE",
            "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
          }]
        },
        "Attributes":6, 
        "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.b83675d28e264e69823205ad4e76df9f.14.14.S-1-5-21-124525095-708259637-1543119021-628175",
        "OwnerIndex":0, 
        "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.b83675d28e264e69823205ad4e76df9f.14.14.S-1-5-21-124525095-708259637-1543119021-628175",
        "PostReference":null, 
        "Replies":{"results":[]},
        "RootPost":{
          "__metadata":{"type":"SP.Social.SocialPost"},
          "Attachment":null, 
          "Attributes":23, 
          "AuthorIndex":0, 
          "CreatedTime":"2013-04-16T22:40:07Z",
          "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b.b83675d28e264e69823205ad4e76df9f.14.14.S-1-5-21-124525095-708259637-1543119021-628175",
          "LikerInfo":{
            "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
            "IncludesCurrentUser":false, 
            "Indexes":{"results":[]},
            "TotalCount":0
          },
          "ModifiedTime":"2013-04-16T22:40:07Z",
          "Overlays":{"results":[]},
          "PostType":0, 
          "PreferredImageUri":null, 
          "Source":{
            "__metadata":{"type":"SP.Social.SocialLink"},
            "Text":null, 
            "Uri":null
          },
          "Text":"This is post 1 from the specified user."
        }, 
        "Status":0, 
        "ThreadType":0, 
        "TotalReplyCount":0
      }]
    },
    "UnreadMentionCount":0
  }
}}
```


## Actor/Feed/Post
<a name="bk_actorFeedPost"> </a>

在指定网站源中创建根文章。
  
    
    
您只能在当前用户的上下文中发布内容。您无法在不同用户的订阅源中创建根文章，但您可以回复其他用户的文章。请参阅  [Post/Reply](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postReply)。
  
    
    

> **注释**
> 请勿将此  `Post` 资源与表示指定主题或文章的 `Post` 资源相混淆。
  
    
    


### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/actor(item=@v)/feed/post?@v='http://<siteCollection>/<teamSite>/newsfeed.aspx'`
  
    
    

### 请求参数

 _restCreationData_
  
    
    
类型： [SP.Social.SocialRestPostCreationData](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestPostCreationData)
  
    
    
新文章的一个 **null** ID 和属性，如下例所示。
  
    
    

```

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
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
包含新的根文章的主题。
  
    
    
以下响应示例展示了包含新的根文章的主题。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b.866d920d78d949a394f26073b767cb19.3.3.1'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b.866d920d78d949a394f26073b767cb19.3.3.1'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b.866d920d78d949a394f26073b767cb19.3.3.1",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":null, 
        "ActorType":2, 
        "CanFollow":true, 
        "ContentUri":"http://serverName:80/sites/teamSite",
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":true, 
        "LibraryUri":null, 
        "Name":"Team Site",
        "PersonalSiteUri":null, 
        "Status":0, 
        "StatusText":null, 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/sites/teamSite"
      },{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username1",
        "ActorType":0, 
        "CanFollow":false, 
        "ContentUri":null, 
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":false, 
        "LibraryUri":null, 
        "Name":"User1 Name",
        "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
        "Status":0, 
        "StatusText":"Posted with REST.", 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
      }]
    },
    "Attributes":6,
    "Id":"8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b.866d920d78d949a394f26073b767cb19.3.3.1",
    "OwnerIndex":0,
    "Permalink":"http://serverName/sites/teamSite/newsfeed.aspx?ThreadID=8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b.866d920d78d949a394f26073b767cb19.3.3.1",
    "PostReference":null,
    "Replies":{"results":[]},
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":1, 
      "CreatedTime":"2013-04-18T22:44:11.8485085Z",
      "Id":"8.c4bb19b167a448a3be9b597522152420.c305b669c2b649e9b820e7feabe3c095.c4bb19b167a448a3be9b597522152420.0c37852b34d0418e91c62ac25af4be5b.866d920d78d949a394f26073b767cb19.3.3.1",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-18T22:44:11.8485085Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0, 
    "ThreadType":0, 
    "TotalReplyCount":0
  }
}}
```


## 文章
<a name="bk_post"> </a>

获取包含指定微博文章的完整主题。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
文章的唯一标识符，如下例中所示。
  
    
    

```

'ID':'1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.644240140e0b43379883ebcb859deaab.27.32.S-1-5-21-2127521184-1604012920-1887927527-66602'
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
包含指定文章的完整主题。
  
    
    
以下响应示例表示包含指定文章的完整主题。与仅包含两个最近的回复的摘要主题不同，完整主题包含所有回复。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.62bff48184bd433b8f7b04f6ea76268b.27.27.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.62bff48184bd433b8f7b04f6ea76268b.27.27.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.62bff48184bd433b8f7b04f6ea76268b.27.27.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username1",
        "ActorType":0, 
        "CanFollow":false, 
        "ContentUri":null, 
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":false, 
        "LibraryUri":null, 
        "Name":"User1 Name",
        "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
        "Status":0, 
        "StatusText":"Posted with REST.", 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
      },{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username2",
        "ActorType":0, 
        "CanFollow":true, 
        "ContentUri":null, 
        "EmailAddress":"username2@somecompany.com",
        "FollowedContentUri":null, 
        "Id":"1.ed418efb7f984ee49ce276c9c5441938.de1675d4929d431894c18908ac53516a.65da910de21f4e40abb318ba33520931.0c37852b34d0418e91c62ac25af4be5b","ImageUri":"http://serverName:80/my/User Photos/Profile Pictures/username2_MThumb.jpg",
        "IsFollowed":true, 
        "LibraryUri":null,"Name":"User2 Name","PersonalSiteUri":"http://serverName/my/personal/username2","Status":6,"StatusText":"This is post 1 from the specified user.", 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":"SOME TITLE",
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername2"
      }]
    },
    "Attributes":6, 
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.62bff48184bd433b8f7b04f6ea76268b.27.27.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "OwnerIndex":0, 
    "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.62bff48184bd433b8f7b04f6ea76268b.27.27.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "PostReference":null, 
    "Replies":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialPost"},
        "Attachment":null, 
        "Attributes":23, 
        "AuthorIndex":1, 
        "CreatedTime":"2013-04-23T23:02:40Z",
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.644240140e0b43379883ebcb859deaab.27.32.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "LikerInfo":{
          "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
          "IncludesCurrentUser":false, 
          "Indexes":{"results":[]},
          "TotalCount":0
        },
        "ModifiedTime":"2013-04-23T23:02:40Z",
        "Overlays":{"results":[]},
        "PostType":1, 
        "PreferredImageUri":null, 
        "Source":{
          "__metadata":{"type":"SP.Social.SocialLink"},
          "Text":null, 
          "Uri":null
        },
        "Text":"This is a reply." 
      }]
    },
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:45:45Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.62bff48184bd433b8f7b04f6ea76268b.27.27.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[1]}, 
        "TotalCount":1
      },
      "ModifiedTime":"2013-04-23T23:02:41Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0, 
    "ThreadType":0, 
    "TotalReplyCount":1
  }
}}
```


## Post/Reply
<a name="bk_postReply"> </a>

发布对指定文章的回复。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/reply`
  
    
    

### 请求参数

 _restCreationData_
  
    
    
类型： [SP.Social.SocialRestPostCreationData](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestPostCreationData)
  
    
    
要回复的文章的 ID 以及回复的属性，如下例中所示。
  
    
    

```

'restCreationData':{
  '__metadata':{
    'type': 'SP.Social.SocialRestPostCreationData'
  },
  'ID':'1.4975bef1e1bc42608c1dfae9f320c751.35c9fd7b79904800aaa5f74684bf0f75.623664921f034e8d814c000267d3e5e4.0c37852b34d0418e91c62ac25af4be5b.230d3c5272fc499f88ac0b74b2f4512f.119.119.S-1-5-21-124525095-708259637-1543119021-565461',
  'creationData':{
    '__metadata':{
      'type':'SP.Social.SocialPostCreationData'
    },
    'ContentText':'Posted with REST.', 
    'UpdateStatusText':false
  }
}
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
包含指定文章的已修改主题的一个摘要。
  
    
    
以下响应示例表示包含指定文章和回复的主题。
  
    
    



```

{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
      "__metadata":{
        "type":"SP.Social.SocialActor"
      },
      "AccountName":"domain\\\\username1",
      "ActorType":0, 
      "CanFollow":false, 
      "ContentUri":null, 
      "EmailAddress":null, 
      "FollowedContentUri":null, 
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
      "ImageUri":null, 
      "IsFollowed":false, 
      "LibraryUri":null, 
      "Name":"User1 Name",
      "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
      "Status":0, 
      "StatusText":"Posted with REST.", 
      "TagGuid":"00000000-0000-0000-0000-000000000000",
      "Title":null,"Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"}
    ]}, 
    "Attributes":6, 
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "OwnerIndex":0, 
    "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "PostReference":null, 
    "Replies":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialPost"},
        "Attachment":null, 
        "Attributes":23, 
        "AuthorIndex":0, 
        "CreatedTime":"2013-04-17T20:52:51.0650454Z",
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ce3ac812293c4903b5c406efe01b9432.26.29.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "LikerInfo":{
          "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
          "IncludesCurrentUser":false, 
          "Indexes":{"results":[]},
          "TotalCount":0
        },
        "ModifiedTime":"2013-04-17T20:52:51.0650454Z",
        "Overlays":{"results":[]},
        "PostType":1, 
        "PreferredImageUri":null, 
        "Source":{
          "__metadata":{"type":"SP.Social.SocialLink"},
          "Text":null, 
          "Uri":null
        },
        "Text":"Replied with REST." 
      }]
    },
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:33:17Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-17T20:52:51.6900774Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0, 
    "ThreadType":0, 
    "TotalReplyCount":1
  }
}}
```


## Post/Delete
<a name="bk_postDelete"> </a>

删除指定的微博文章。如果文章是根文章，将删除整个主题。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/delete`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
要删除的文章的 ID，如下例中所示。
  
    
    

```

'ID':'1.94fdcc5fc39b4a2c99ae4570caf02321.d0a03fb1761a404a9a8e7f9f5ec58e17.5a1067e8af65410b9e2ba6a74a4b718a.0c37852b34d0418e91c62ac25af4be5b.9dbfb5598e2248d7b57eee57abf2e7c1.31.31.S-1-5-21-124525095-708259637-1543119021-565461'
```


### 响应

无。
  
    
    

```
{"d":{"Delete":null}}
```


## Post/Like
<a name="bk_postLike"> </a>

使当前用户成为指定微博文章的关注者。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/like`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
要喜欢的文章的 ID，如下例中所示。
  
    
    

```
'ID':'1.94fdcc5fc39b4a2c99ae4570caf02321.d0a03fb1761a404a9a8e7f9f5ec58e17.5a1067e8af65410b9e2ba6a74a4b718a.0c37852b34d0418e91c62ac25af4be5b.9dbfb5598e2248d7b57eee57abf2e7c1.31.31.S-1-5-21-124525095-708259637-1543119021-565461'
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
包含指定文章的摘要主题。
  
    
    
以下响应示例表示包含喜欢的文章的主题。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username1",
        "ActorType":0, 
        "CanFollow":false, 
        "ContentUri":null, 
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":false, 
        "LibraryUri":null, 
        "Name":"User1 Name",
        "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
        "Status":0, 
        "StatusText":"Posted with REST.", 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
      }]
    },
    "Attributes":6, 
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "OwnerIndex":0, 
    "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "PostReference":null, 
    "Replies":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialPost"},
        "Attachment":null, 
        "Attributes":23, 
        "AuthorIndex":0, 
        "CreatedTime":"2013-04-17T20:52:51.0650454Z",
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ce3ac812293c4903b5c406efe01b9432.26.29.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "LikerInfo":{
          "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
          "IncludesCurrentUser":false, 
          "Indexes":{"results":[]},
          "TotalCount":0
        },
        "ModifiedTime":"2013-04-17T20:52:51.0650454Z",
        "Overlays":{"results":[]},
        "PostType":1, 
        "PreferredImageUri":null, 
        "Source":{
          "__metadata":{"type":"SP.Social.SocialLink"},
          "Text":null, 
          "Uri":null
        },
        "Text":"Replied with REST." 
      }]
    },
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:33:17Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":true, 
        "Indexes":{"results":[]},
        "TotalCount":1
      },
      "ModifiedTime":"2013-04-17T20:52:51Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0, 
    "ThreadType":0, 
    "TotalReplyCount":1
  }
}}
```


## Post/Unlike
<a name="bk_postUnlike"> </a>

将当前用户从指定微博文章的关注者列表中移除。如果当前用户不是文章的关注者，该请求将忽略。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/unlike`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
要喜欢的文章的 ID，如下例中所示。
  
    
    

```

'ID':'1.94fdcc5fc39b4a2c99ae4570caf02321.d0a03fb1761a404a9a8e7f9f5ec58e17.5a1067e8af65410b9e2ba6a74a4b718a.0c37852b34d0418e91c62ac25af4be5b.9dbfb5598e2248d7b57eee57abf2e7c1.31.31.S-1-5-21-124525095-708259637-1543119021-565461'
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
包含指定文章的已修改主题的一个摘要。
  
    
    
以下响应示例表示包含用户不再喜欢的文章的主题。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username1",
        "ActorType":0, 
        "CanFollow":false, 
        "ContentUri":null, 
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":false, 
        "LibraryUri":null, 
        "Name":"User1 Name",
        "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
        "Status":0, 
        "StatusText":"Posted with REST.", 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
      }]
    },
    "Attributes":6, 
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "OwnerIndex":0, 
    "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "PostReference":null, 
    "Replies":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialPost"},
        "Attachment":null, 
        "Attributes":23, 
        "AuthorIndex":0, 
        "CreatedTime":"2013-04-17T20:52:51.0650454Z",
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ce3ac812293c4903b5c406efe01b9432.26.29.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "LikerInfo":{
          "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
          "IncludesCurrentUser":false, 
          "Indexes":{"results":[]},
          "TotalCount":0
        },
        "ModifiedTime":"2013-04-17T20:52:51.0650454Z",
        "Overlays":{"results":[]},
        "PostType":1, 
        "PreferredImageUri":null, 
        "Source":{
          "__metadata":{"type":"SP.Social.SocialLink"},
          "Text":null, 
          "Uri":null
        },
        "Text":"Replied with REST." 
      }]
    },
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:33:17Z","Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-17T20:52:51Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0,
    "ThreadType":0,
    "TotalReplyCount":1
  }
}}
```


## Post/Likers
<a name="bk_postLikers"> </a>

获取喜欢指定微博文章的用户。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/likers`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
要获取其关注者的文章的 ID，如下例中所示。
  
    
    

```

'ID':'1.94fdcc5fc39b4a2c99ae4570caf02321.d0a03fb1761a404a9a8e7f9f5ec58e17.5a1067e8af65410b9e2ba6a74a4b718a.0c37852b34d0418e91c62ac25af4be5b.9dbfb5598e2248d7b57eee57abf2e7c1.31.31.S-1-5-21-124525095-708259637-1543119021-565461'
```


### 响应

 **Likers**
  
    
    
类型： [SP.Social.SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx)[]
  
    
    
喜欢指定文章的用户。
  
    
    
以下响应示例表示喜欢指定文章的用户。
  
    
    



```
{"d":{
  "Likers":{
    "results":[{
      "__metadata":{"type":"SP.Social.SocialActor"},
      "AccountName":"domain\\\\username1",
      "ActorType":0, 
      "CanFollow":false, 
      "ContentUri":null, 
      "EmailAddress":null, 
      "FollowedContentUri":null, 
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
      "ImageUri":null, 
      "IsFollowed":false, 
      "LibraryUri":null, 
      "Name":"User1 Name",
      "PersonalSiteUri":"http://serverName/my/personal/username1/",
      "Status":0, 
      "StatusText":"Posted with REST.", 
      "TagGuid":"00000000-0000-0000-0000-000000000000",
      "Title":null, 
      "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
    }]
  }
}}
```


## Post/Lock
<a name="bk_postLock"> </a>

锁定指定主题。如果主题已锁定，则不会将回复文章添加到主题中，直至其解锁。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/lock`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
要锁定的主题的 ID，如下例中所示。
  
    
    

```

'ID':'1.94fdcc5fc39b4a2c99ae4570caf02321.d0a03fb1761a404a9a8e7f9f5ec58e17.5a1067e8af65410b9e2ba6a74a4b718a.0c37852b34d0418e91c62ac25af4be5b.9dbfb5598e2248d7b57eee57abf2e7c1.31.31.S-1-5-21-124525095-708259637-1543119021-565461'
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
已锁定主题的摘要。
  
    
    
以下响应示例表示锁定主题。主题的 **Attributes** 属性包含 [SP.Social.SocialThreadAttributes](http://msdn.microsoft.com/library/21ff9f92-3223-bcc7-ceec-7b899ee29b6e%28Office.15%29.aspx) 枚举的按位值，该值将指示主题是否已锁定。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'
    uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
  "__metadata":{"type":"SP.Social.SocialThread"},
  "Actors":{
    "results":[{
      "__metadata":{"type":"SP.Social.SocialActor"},
      "AccountName":"domain\\\\username1",
      "ActorType":0, 
      "CanFollow":false, 
      "ContentUri":null, 
      EmailAddress":null, 
      "FollowedContentUri":null, 
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
      "ImageUri":null, 
      "IsFollowed":false, 
      "LibraryUri":null, 
      "Name":"User1 Name",
      "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
      "Status":0, 
      "StatusText":"Posted with REST.", 
      "TagGuid":"00000000-0000-0000-0000-000000000000",
      "Title":null, 
      "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
    }]
  },
  "Attributes":12,
  "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "OwnerIndex":0,
  "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "PostReference":null,
  "Replies":{
    "results":[{
      "__metadata":{"type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":22, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T20:52:51.0650454Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ce3ac812293c4903b5c406efe01b9432.26.29.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-17T20:52:51.0650454Z",
      "Overlays":{"results":[]},
      "PostType":1, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Replied with REST." 
    }]
  },
  "RootPost":{
    "__metadata":{
      "type":"SP.Social.SocialPost"},
      "Attachment":null, 
      "Attributes":22, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:33:17Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-17T20:52:51Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":0,
    "ThreadType":0,
    "TotalReplyCount":1
  }
}}
```


## Post/Unlock
<a name="bk_postUnlock"> </a>

解锁指定主题。
  
    
    

### 终结点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.feed/post/unlock`
  
    
    

### 请求参数

 **ID**
  
    
    
类型： **String**
  
    
    
要解锁的主题的 ID，如下例中所示。
  
    
    

```

'ID':'1.94fdcc5fc39b4a2c99ae4570caf02321.d0a03fb1761a404a9a8e7f9f5ec58e17.5a1067e8af65410b9e2ba6a74a4b718a.0c37852b34d0418e91c62ac25af4be5b.9dbfb5598e2248d7b57eee57abf2e7c1.31.31.S-1-5-21-124525095-708259637-1543119021-565461'
```


### 响应

类型： [SP.Social.SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)
  
    
    
已解锁主题的摘要。
  
    
    
以下响应示例表示解锁主题。主题的 **Attributes** 属性包含 [SP.Social.SocialThreadAttributes](http://msdn.microsoft.com/library/21ff9f92-3223-bcc7-ceec-7b899ee29b6e%28Office.15%29.aspx) 枚举的按位值，该值将指示主题是否已锁定。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "uri":"http://serverName/sites/dev/_api/social.feed/post(ID=@ai)/?@ai='1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602'",
    "type":"SP.Social.SocialRestThread"
  },
  "ID":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
  "SocialThread":{
    "__metadata":{"type":"SP.Social.SocialThread"},
    "Actors":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialActor"},
        "AccountName":"domain\\\\username1",
        "ActorType":0, 
        "CanFollow":false, 
        "ContentUri":null, 
        "EmailAddress":null, 
        "FollowedContentUri":null, 
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b",
        "ImageUri":null, 
        "IsFollowed":false, 
        "LibraryUri":null, 
        "Name":"User1 Name",
        "PersonalSiteUri":"http://serverName:80/my/personal/username1/",
        "Status":0, 
        "StatusText":"Posted with REST.", 
        "TagGuid":"00000000-0000-0000-0000-000000000000",
        "Title":null, 
        "Uri":"http://serverName:80/my/Person.aspx?accountname=domain%5Cusername1"
      }
    ]}, 
    "Attributes":6, 
    "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "OwnerIndex":0, 
    "Permalink":"http://serverName:80/my/ThreadView.aspx?ThreadID=1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
    "PostReference":null, 
    "Replies":{
      "results":[{
        "__metadata":{"type":"SP.Social.SocialPost"},
        "Attachment":null, 
        "Attributes":23, 
        "AuthorIndex":0, 
        "CreatedTime":"2013-04-17T20:52:51.0650454Z",
        "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.ce3ac812293c4903b5c406efe01b9432.26.29.S-1-5-21-2127521184-1604012920-1887927527-66602",
        "LikerInfo":{
          "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
          "IncludesCurrentUser":false, 
          "Indexes":{"results":[]},
          "TotalCount":0
        },
        "ModifiedTime":"2013-04-17T20:52:51.0650454Z",
        "Overlays":{"results":[]},
        "PostType":1, 
        "PreferredImageUri":null, 
        "Source":{
          "__metadata":{"type":"SP.Social.SocialLink"},
          "Text":null, 
          "Uri":null
        },
        "Text":"Replied with REST." 
      }]
    },
    "RootPost":{
      "__metadata":{"type":"SP.Social.SocialPost"},
      
      "Attachment":null, 
      "Attributes":23, 
      "AuthorIndex":0, 
      "CreatedTime":"2013-04-17T19:33:17Z",
      "Id":"1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602",
      "LikerInfo":{
        "__metadata":{"type":"SP.Social.SocialPostActorInfo"},
        "IncludesCurrentUser":false, 
        "Indexes":{"results":[]},
        "TotalCount":0
      },
      "ModifiedTime":"2013-04-17T20:52:51Z",
      "Overlays":{"results":[]},
      "PostType":0, 
      "PreferredImageUri":null, 
      "Source":{
        "__metadata":{"type":"SP.Social.SocialLink"},
        "Text":null, 
        "Uri":null
      },
      "Text":"Posted with REST." 
    },
    "Status":5,
    "ThreadType":0,
    "TotalReplyCount":1
  }
}}
```


## 订阅源任务的示例 REST 请求
<a name="bk_exampleRequests"> </a>

 **GET** 订阅源任务请求指定 URI 中的参数或请求的 **url** 属性中的参数。 **POST** 请求指定请求正文中的 **data** 属性的参数，格式为 XML 或 JavaScript 对象表示法 (JSON)。您可以提出任何语言的 HTTP 请求，包括 JavaScript 和 C#。下列示例请求显示如何使用 JavaScript 提出请求，如何传递 JSON 格式的实体信息。
  
    
    
 **示例：**如何指定请求正文中的  _ID_ 参数（在 **data** 属性中）。
  
    
    

> **注释**
> 主题和文章 **Id** 属性的值太长，无法在 URL 中发送，因此您要在请求正文中发送它们。结果，即使在逻辑上为 **GET** 请求的只读操作也必须作为 **POST** 请求发送。例如，若要获取某个主题，您必须发送 **POST** 请求并将主题 **Id** 作为一个实体在请求正文中传递。
  
    
    




```

var endpoint = siteUrl + '/_api/social.feed/post';
var postId = '1.655c70c348374d48839daabc24a360f0.82baa3bdfa2f481a8185802eb9c6c6cd.5d227a6fa3894f0c9dde26876b71d619.0c37852b34d0418e91c62ac25af4be5b.4316bdaa94bf4984be5dfea1ba96954e.26.26.S-1-5-21-2127521184-1604012920-1887927527-66602';

$.ajax({
    url: endpoint,
    type: 'POST',
    data: JSON.stringify({
        'ID': postId
    }),
    headers: {
        "accept": "application/json;odata=verbose",
        "content-type": "application/json;odata=verbose",
        "X-RequestDigest": $("#__REQUESTDIGEST").val()
    },
    success: function(data) { 
        var stringData = JSON.stringify(data);
        alert(stringData);

        // Converts the response data into an object that you can work with.
        var jsonObject = JSON.parse(stringData);
    },
    error: function(xhr, ajaxOptions, thrownError) {
        alert("Error: " + xhr.status + " " + thrownError + "\\nResponseText: " + xhr.responseText);
    }
});
```

 **示例：**如何发布根文章并指定 **data** 属性中的 _restCreationData_ 参数。
  
    
    



```

var endpoint = <site url> + '/_api/social.feed/my/feed/post';
var postContent = 'Posted with REST.';

$.ajax({
    url: endpoint,
    type: 'POST',
    data: JSON.stringify({
        'restCreationData': {
            '__metadata': {
                'type': 'SP.Social.SocialRestPostCreationData'
            },
            'ID': null,
            'creationData': {
                '__metadata': {
                    'type': 'SP.Social.SocialPostCreationData'
                },
                'ContentText': postContent
            }
        }
    }),
    headers: {
        "accept": "application/json;odata=verbose",
        "content-type": "application/json;odata=verbose",
        "X-RequestDigest": $("#__REQUESTDIGEST").val()
    },
    success: function(data) { 
        var stringData = JSON.stringify(data);
        alert(stringData);

        // Converts the response data into an object that you can work with.
        var jsonObject = JSON.parse(stringData);
    },
    error: function(xhr, ajaxOptions, thrownError) {
        alert("Error: " + xhr.status + " " + thrownError + "\\nResponseText: " + xhr.responseText);
    }
});
```

要发布对指定主题的回复，请将 **POST** 请求发送至 **Reply** 资源 ( `<site url>/_api/social.feed/Post/Reply`) 并传递包含目标文章 ID 的 **restCreationData** 信息。
  
    
    



```

{ 'restCreationData': {
    '__metadata': { 'type': 'SP.Social.SocialRestPostCreationData' },
    'ID':'1.4975bef1e1bc42608c1dfae9f320c751.35c9fd7b79904800aaa5f74684bf0f75.623664921f034e8d814c000267d3e5e4.0c37852b34d0418e91c62ac25af4be5b.230d3c5272fc499f88ac0b74b2f4512f.119.119.S-1-5-21-124525095-708259637-1543119021-565461',
    'creationData':{
        '__metadata':{ 'type':'SP.Social.SocialPostCreationData' },
        'ContentText':'This is a reply to the specified post.',
        'UpdateStatusText':false
    }
} }
```


## 用于订阅源相关 REST 请求和响应的资源
<a name="bk_FeedRelatedRestResources"> </a>

下列 REST 资源用作客户端请求中的参数，或在服务器响应中返回。
  
    
    

### SP.Social.SocialFeedOptions
<a name="bk_SocialFeedOptions"> </a>

表示检索订阅源时可以指定的选项。
  
    
    
客户端 **GET** 订阅源请求可以将 **SocialFeedOptions** 属性指定为参数。这些属性在查询字符串中指定。
  
    
    

||||
|:-----|:-----|:-----|
|MaxThreadCount  <br/> |**Int32** <br/> |要检索的最大主题数。默认数量为 20。  <br/> |
|NewerThan  <br/> |**String** <br/> |要检索的时间跨度的"newer than"边界，作为 **DateTime** 对象的字符串表示形式。默认情况下未指定边界。 <br/> |
|OlderThan  <br/> |**String** <br/> |要检索的时间跨度的"older than"边界，作为 **DateTime** 对象的字符串表示形式。默认情况下未指定边界。 <br/> |
|SortOrder  <br/> |**Int32** <br/> |订阅源中主题的排序顺序。默认排序顺序为按修改日期，只有时间线订阅源按创建日期排序。          **0** 根据文章的最新修改时间，将主题按修改时间排序。          **1** 根据根文章的创建时间，将主题按创建时间排序。 <br/> |
   

  
    
    

  
    
    

### SP.Social.SocialRestActor
<a name="bk_SocialRestActor"> </a>

表示用户、文档、站点或标签。
  
    
    
服务器在响应中返回 **SocialRestActor** 资源，以响应客户端对主角信息的请求。
  
    
    
 **SocialRestActor** 具有以下属性。
  
    
    

||||
|:-----|:-----|:-----|
|FollowableItem  <br/> |**String** <br/> |指定主角的唯一标识符。返回用户的帐户名称或文档、站点或标签的 URI。  <br/> |
|FollowableItemActor  <br/> | [SP.Social.SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx) <br/> |指定的用户。如果用户是当前用户，或者资源不是用户类型的主角，返回 **null**。  <br/> |
|Me  <br/> | [SP.Social.SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx) <br/> |当前用户。  <br/> |
   

  
    
    

  
    
    

### SP.Social.SocialRestFeed
<a name="bk_SocialRestFeed"> </a>

表示好友动态订阅源。
  
    
    
服务器在响应中返回 **SocialRestFeed** 资源，以响应客户端对订阅源内容的请求。
  
    
    
 **SocialRestFeed** 包含包装的 [SP.Social.SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx) 对象，该对象具有以下属性。
  
    
    

||||
|:-----|:-----|:-----|
|属性  <br/> | [SP.Social.SocialFeedAttributes](http://msdn.microsoft.com/library/9ea7d3c5-7f96-88a6-5bdf-d7749b044ad3%28Office.15%29.aspx) <br/> |适用于订阅源的按位属性集。  <br/> |
|NewestProcessed  <br/> |**DateTime** <br/> |检索的最新文章的日期和时间。  <br/> |
|OldestProcessed  <br/> |**DateTime** <br/> |检索的最旧文章的日期和时间。  <br/> |
|主题  <br/> | [SP.Social.SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx)[]  <br/> |组成订阅源的主题。  <br/> |
|UnreadMentionCount  <br/> |**Int32** <br/> |当前用户提及的未读订阅源数量。  <br/> |
   

  
    
    

  
    
    

### SP.Social.SocialRestPostCreationData
<a name="bk_SocialRestPostCreationData"> </a>

表示新文章的内容及相关信息。
  
    
    
客户端将 **SocialRestPostCreationData** 属性指定为请求中用于发布根文章或回复的参数。这些属性在请求正文的 **data** 属性中指定。
  
    
    
 **SocialRestPostCreationData** 包含 **ID** 属性和包装的 [SP.Social.SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) 对象。 **ID** 为必需， **SocialPostCreationData** 属性为可选。
  
    
    

||||
|:-----|:-----|:-----|
|ID（必需）  <br/> |**null** 或 **String** <br/> |文章的目标目的地。其值可为下列任一项：          **null**，以将根文章发布到当前用户的订阅源           要回复的文章的 ID           要发布到的网站源的 URL（例如： `http://<teamSiteURL>/newsfeed.aspx`）  <br/> |
   
以下属性属于 **SocialPostCreationData** 对象。
  
    
    

||||
|:-----|:-----|:-----|
|附件  <br/> | [SP.Social.SocialAttachment](http://msdn.microsoft.com/library/dfdee790-a1b0-19c8-0e92-5a6e058ba4db%28Office.15%29.aspx) <br/> |文章的图像、视频或文档附件。  <br/> |
|ContentItems  <br/> | [SP.Social.SocialDataItem](http://msdn.microsoft.com/library/757e7b62-66a6-b03f-0ff0-769a42eb2b4a%28Office.15%29.aspx)[]  <br/> |用于替换文章内容文本中的相应令牌的项目  <br/> |
|ContentText  <br/> |**String** <br/> |文章的纯文本，可能包含位置插入令牌（例如，"今天是 {0} 的生日！"）。  <br/> |
|SecurityUris  <br/> |**String[]** <br/> |用于定义文章访问权限的 SharePoint 对象的 URI 字符串表示形式。  <br/> |
|源  <br/> | [SP.Social.SocialLink](http://msdn.microsoft.com/library/c71efc66-c9ca-ea35-b1c0-cb9ec3bbfcd3%28Office.15%29.aspx) <br/> |文章来源。  <br/> |
|UpdateStatusText  <br/> |**Boolean** <br/> |控制文章的纯文本内容是否应该替换当前用户的状态文本的值。  <br/> |
   

  
    
    

  
    
    

### SP.Social.SocialRestThread
<a name="bk_SocialRestThread"> </a>

表示包含根文章和回复集的主题。
  
    
    
服务器在响应中返回 **SocialRestThread** 资源，以响应创建文章或获取完整主题的客户端请求。
  
    
    
 **SocialRestThread** 包含 **ID** 属性和包装的 [SP.Social.SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx) 对象。
  
    
    

||||
|:-----|:-----|:-----|
|ID  <br/> |**String** <br/> |主题的唯一标识符。  <br/> |
   
以下属性属于 **SocialThread** 对象。
  
    
    

||||
|:-----|:-----|:-----|
|主角  <br/> | [SP.Social.SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx)[]  <br/> |合并的参与主角阵列。  <br/> |
|属性  <br/> |**Int32** <br/> |表示主题属性集的按位值。请参阅  [SP.Social.SocialThreadAttributes](http://msdn.microsoft.com/library/21ff9f92-3223-bcc7-ceec-7b899ee29b6e%28Office.15%29.aspx)。  <br/> |
|Id  <br/> |**String** <br/> |主题的唯一标识符。  <br/> |
|OwnerIndex  <br/> |**Int32** <br/> |主题的主角中主题所有者的索引。  <br/> |
|Permalink  <br/> |**String** <br/> |直接浏览到主题的稳定 URI（如果可用）的字符串表示形式。  <br/> |
|PostReference  <br/> | [SP.Social.SocialPostReference](http://msdn.microsoft.com/library/529e1db7-2e9a-5141-6b1e-94a5c63e7c16%28Office.15%29.aspx) <br/> |引用的文章。  <br/> |
|回复  <br/> | [SP.Social.SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx)[]  <br/> |对主题的回复。  <br/> |
|RootPost  <br/> | [SP.Social.SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx) <br/> |主题的根文章。  <br/> |
|状态  <br/> |**Int32** <br/> |用于识别在主题检索过程中发生的可恢复错误的代码。请参阅  [SP.Social.SocialStatusCode](http://msdn.microsoft.com/library/79292329-19de-43e1-5928-60b0edc36c94%28Office.15%29.aspx)。  <br/> |
|ThreadType  <br/> | [SP.Social.SocialThreadType](http://msdn.microsoft.com/library/7444217e-ddda-d3a0-b19f-146cf8c6fcaa%28Office.15%29.aspx) <br/> |主题类型。  <br/> |
|TotalReplyCount  <br/> |**Int32** <br/> |主题回复总数。  <br/> |
   

## 其他资源
<a name="bk_addresources"> </a>


-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
- 要查看 SharePoint 2013 REST 服务使用的 **SP.Social** OData 架构中的成员，请浏览到 `http://<siteUri>/_api/$metadata`。
    
  
