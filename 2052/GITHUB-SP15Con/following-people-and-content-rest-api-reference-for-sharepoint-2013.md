---
title: 关注好友及 SharePoint 2013 的内容 REST API 引用
ms.prod: SHAREPOINT
ms.assetid: c05755df-846d-4a39-941d-950d066cc6d4
---



# 关注好友及 SharePoint 2013 的内容 REST API 引用
使用 **SocialRestFollowingManager** 资源和 **PeopleManager** 资源找到关注好友和内容的 SharePoint REST 端点。
您可以使用 SharePoint 2013 代表性状态传输 (REST) 服务执行与使用 .NET 客户端对象模型和 JavaScript 对象模型时相同的任务。若要使用 REST 服务，您需要构建 HTTP **GET** 和 **POST** 请求并将其发送至表示您想要完成的任务的资源端点。这些端点与 SharePoint 对象、属性和方法相对应。
  
    
    

大多数关注任务的端点 URI 开始于 **SocialRestFollowingManager** 资源 ( `social.following`) 并且结束于执行这一特定任务的资源。例如，您使用 URI  `http://www.contoso.com/_api/social.following/follow` 让当前用户开始关注好友或内容，并使用 URI `https://www.contoso.com/sites/devSite/_api/social.following/followed` 获取当前用户关注的好友或内容。
> **注释**
> 本文介绍 HTTP 请求的端点 URI 和参数组件。有关完整请求的示例，请参阅 [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)。 
  
    
    

针对关注好友和关注内容任务，我们建议您使用 **SocialRestFollowingManager** API，但您也可以使用 **PeopleManager** 资源来处理 **SocialRestFollowingManager** 不支持的一些关注好友任务。例如，您可以找出某人是否在关注当前用户或获取另一个用户的粉丝。针对这些任务，您可以将 HTTP **GET** 请求发送至以 **PeopleManager** 资源 ( `sp.userprofiles.peoplemanager`) 打头且以执行特定任务的资源结尾的端点 URI。如果端点使用一个参数，那么参数元数据将以 XML 中 URI 或请求主体或是 JavaScript 对象表示法 (JSON) 格式发送。您可以使用任意语言创建 HTTP请求，包括 JavaScript 和 C#。默认情况下，REST 服务会返回使用 Atom 协议格式化的响应，但您也可以使用 HTTP **Accept** 头请求 JSON 格式。请参阅 [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)。
## 用于关注好友和关注内容任务的资源端点
<a name="bk_Overview"> </a>


||
|:-----|
| [Follow](#bk_Follow)           [StopFollowing](#bk_StopFollowing)           [IsFollowed](#bk_IsFollowed)           [My](#bk_My)           [My/FollowedDocumentsUri](#bk_MyFollowedDocumentsUri)           [My/FollowedSitesUri](#bk_MyFollowedSitesUri)           [My/Followed](#bk_Followed)           [My/FollowedCount](#bk_FollowedCount)           [My/Followers](#bk_Followers)           [My/Suggestions](#bk_Suggestions)           [GetMySuggestions](#bk_GetMySuggestions)           [IsMyPeopleListPublic](#bk_IsMyPeopleListPublic)           [AmIFollowedBy](#bk_AmIFollowedBy)           [GetPeopleFollowedBy](#bk_GetPeopleFollowedBy)           [GetFollowersFor](#bk_GetFollowersFor)|
   

## Follow
<a name="bk_Follow"> </a>

使当前用户开始关注某用户、文档、站点或标签。
  
    
    

### 端点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.following/follow`
  
    
    

### 请求参数

 _actor_
  
    
    
类型： **SP.Social.SocialActorInfo**
  
    
    
开始关注的角色。
  
    
    
 **URI 中的用户  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=0,AccountName=@v,Id=null)?@v='domain\\user'
```

 **请求正文中的用户  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":0,
  "AccountName":"domain\\\\user",
  "Id":null
}
```

如果您正在使用基于声明的标识模型，则可以使用查询字符串中的格式  `@v='i:0"%23".f|membership|user@domain.com'` 或请求正文中的 `"i:0#.f|membership|user@domain.com"` 传递帐户名称。
  
    
    
 **URI 中的文档  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=1,ContentUri=@v,Id=null)?@v='http://server/Shared%20Documents/fileName.docx'
```

 **请求正文中的文档  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":1,
  "ContentUri":"http://server/Shared%20Documents/fileName.docx",
  "Id":null
}
```

 **URI 中的网站  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=2,ContentUri=@v,Id=null)?@v='http://server/site'
```

 **请求正文中的网站  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":2,
  "ContentUri":"http://siteCollection/site",
  "Id":null
}
```

 **URI 中的标记  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=3,TagGuid='19a4a484-c1dc-4bc5-8c93-bb96245ce928',Id=null)
```

 **请求正文中的标记  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":3,
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928",
  "Id":null
}
```

您需要标记 GUID 才能开始关注一个标记。您无法使用 REST 服务获取 GUID，但您可以使用 .NET 客户端对象模型或 JavaScript 对象模型。请参阅 [如何使用 JavaScript 对象模型根据标记的名称获取标记的 GUID](follow-content-in-sharepoint-2013.md#bk_getTagGuid)。
  
    
    

### 响应

 **Follow**
  
    
    
类型： **SP.Social.SocialFollowResult**
  
    
    
请求的状态：0 = OK；1 = AlreadyFollowing；2 = LimitReached；或 3 = InternalError。
  
    
    
以下响应表示请求已成功。
  
    
    



```

{"d":{"Follow":0}}
```


## StopFollowing
<a name="bk_StopFollowing"> </a>

使当前用户停止关注用户、文档、站点或标签。
  
    
    

### 端点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.following/stopfollowing`
  
    
    

### 请求参数

 _actor_
  
    
    
类型： **SP.Social.SocialActorInfo**
  
    
    
停止关注的角色。
  
    
    
 **URI 中的用户  _actor_**
  
    
    



```
http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=0,AccountName=@v,Id=null)?@v='domain\\user'
```

 **请求正文中的用户  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":0,
  "AccountName":"domain\\\\user",
  "Id":null
}
```

如果您正在使用基于声明的标识模型，则可以使用查询字符串中的格式  `@v='i:0"%23".f|membership|user@domain.com'` 或请求正文中的 `"i:0#.f|membership|user@domain.com"` 传递帐户名称。
  
    
    
 **URI 中的文档  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=1,ContentUri=@v,Id=null)?@v='http://server/Shared%20Documents/fileName.docx'
```

 **请求正文中的文档  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":1,
  "ContentUri":"http://server/Shared%20Documents/fileName.docx",
  "Id":null
}
```

 **URI 中的网站  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=2,ContentUri=@v,Id=null)?@v='http://server/site'
```

 **请求正文中的网站  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":2,
  "ContentUri":"http://siteCollection/site",
  "Id":null
}
```

 **URI 中的标记  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=3,TagGuid='19a4a484-c1dc-4bc5-8c93-bb96245ce928',Id=null)
```

 **请求正文中的标记  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":3,
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928",
  "Id":null
}
```

您需要标记 GUID 才能开始关注一个标记。您无法使用 REST 服务获取 GUID，但您可以使用 .NET 客户端对象模型或 JavaScript 对象模型。请参阅 [如何使用 JavaScript 对象模型根据标记的名称获取标记的 GUID](follow-content-in-sharepoint-2013.md#bk_getTagGuid)。
  
    
    

### 响应

无。
  
    
    

```

{"d":{"StopFollowing":null}}
```


## IsFollowed
<a name="bk_IsFollowed"> </a>

显示当前用户是否关注某特定用户、文档、站点或标签。
  
    
    

### 端点 URI 结构

 **POST** `http://<siteCollection>/<site>/_api/social.following/isfollowed`
  
    
    

### 请求参数

 _actor_
  
    
    
类型： **SP.Social.SocialActorInfo**
  
    
    
要找到其关注状态的角色。
  
    
    
 **URI 中的用户  _actor_**
  
    
    



```
http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=0,AccountName=@v,Id=null)?@v='domain\\user'
```

 **请求正文中的用户  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":0,
  "AccountName":"domain\\\\user",
  "Id":null
}
```

如果您正在使用基于声明的标识模型，则可以使用查询字符串中的格式  `@v='i:0"%23".f|membership|user@domain.com'` 或请求正文中的 `"i:0#.f|membership|user@domain.com"` 传递帐户名称。
  
    
    
 **URI 中的文档  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=1,ContentUri=@v,Id=null)?@v='https://domain.sharepoint.com/Shared%20Documents/fileName.docx'
```

 **请求正文中的文档  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":1,
  "ContentUri":"http://server/Shared%20Documents/fileName.docx",
  "Id":null
}
```

 **URI 中的网站  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=2,ContentUri=@v,Id=null)?@v='http://domain.sharepoint.com'
```

 **请求正文中的网站  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":2,
  "ContentUri":"http://siteCollection/site",
  "Id":null
}
```

 **URI 中的标记  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=3,TagGuid='19a4a484-c1dc-4bc5-8c93-bb96245ce928',Id=null)
```

 **请求正文中的标记  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":3,
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928",
  "Id":null
}
```

您需要标记 GUID 才能开始关注一个标记。您无法使用 REST 服务获取 GUID，但您可以使用 .NET 客户端对象模型或 JavaScript 对象模型。请参阅 [如何使用 JavaScript 对象模型根据标记的名称获取标记的 GUID](follow-content-in-sharepoint-2013.md#bk_getTagGuid)。
  
    
    

### 响应

 **IsFollowed**
  
    
    
类型： **bool**
  
    
    
 **true** 表示当前用户已关注该角色；否则，为 **false**。
  
    
    
以下响应表示用户没有关注指定角色。
  
    
    



```

{"d":{"IsFollowed":false}}
```


## My
<a name="bk_My"> </a>

获取有关 **SocialRestFollowingManager** 实例和当前用户的信息。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my`
  
    
    

### 请求参数

无。
  
    
    

### 响应

类型： **SP.Social.SocialRestFollowingManager**
  
    
    
有关 **SocialRestFollowingManager** 实例的信息，以及当前用户的 **MyFollowedDocumentsUri**、 **MyFollowedSitesUri** 和 **SocialActor** 属性。
  
    
    
以下响应表示当前用户的 **SocialRestFollowingManager** 实例。
  
    
    



```
{"d":{
  "__metadata":{
    "id":"https://somecompany-a2ef5dfc05b1da.sharepoint.com/appInstance/_api/social.following/my/following",
    "uri":"https://somecompany-a2ef5dfc05b1da.sharepoint.com/appInstance/_api/social.following/my/following",
    "type":"SP.Social.SocialRestFollowingManager"
  },
  "MyFollowedDocumentsUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/Social/FollowedContent.aspx",
  "MyFollowedSitesUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/Social/Sites.aspx",
  "SocialActor":
    {"__metadata":{"type":"SP.Social.SocialActor"},
    "AccountName":"i:0#.f|membership|someone@somecompany.onmicrosoft.com",
    "ActorType":0,
    "CanFollow":false,
    "ContentUri":null,
    "EmailAddress":"someone@somecompany.onmicrosoft.com",
    "FollowedContentUri":null,
    "Id":"1.0f435d74164149cfa76e19ad21dc7c2e.8a7874906a9348189f2fb83295b598d5.06ff4087162c48dcb43828e4ddf82c38.98b9fc73d5224265b039586688b15b98",
    "ImageUri":"https://somecompany-my.sharepoint.com/User%20Photos/Profile%20Pictures/someone_somecompany_onmicrosoft_com_MThumb.jpg",
    "IsFollowed":false,
    "LibraryUri":null,
    "Name":"User Name",
    "PersonalSiteUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/",
    "Status":0,
    "StatusText":"I like rabbits.",
    "TagGuid":"00000000-0000-0000-0000-000000000000",
    "Title":null,
    "Uri":"https://somecompany-my.sharepoint.com:443/Person.aspx?accountname=i%3A0%23%2Ef%7Cmembership%7Csomeone%40somecompany%2Eonmicrosoft%2Ecom"
  }
}}
```


## My/FollowedDocumentsUri
<a name="bk_MyFollowedDocumentsUri"> </a>

获取当前用户对应的"我正在关注的文档"页面的 URI。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followeddocumentsuri`
  
    
    

### 请求参数

无。
  
    
    

### 响应

 **FollowedDocumentsUri**
  
    
    
类型： **String**
  
    
    
当前用户对应的"我正在关注的文档"页面的 URI。
  
    
    
以下响应表示当前用户的 **FollowedDocumentsUri**。
  
    
    



```

{"d":{"FollowedDocumentsUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/Social/FollowedContent.aspx"}}
```


## My/FollowedSitesUri
<a name="bk_MyFollowedSitesUri"> </a>

获取当前用户对应的"我正在关注的站点"页面的 URI。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followedsitesuri`
  
    
    

### 请求参数

无。
  
    
    

### 响应

 **FollowedSitesUri**
  
    
    
类型： **String**
  
    
    
当前用户对应的"我正在关注的站点"页面的 URI。
  
    
    
以下响应表示当前用户的 **FollowedSitesUri**。
  
    
    



```
{"d":{"FollowedSitesUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/Social/Sites.aspx"}}
```


## My/Followed
<a name="bk_Followed"> </a>

获取当前用户正在关注的用户、文档、站点以及标签。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followed(types=15)`
  
    
    

### 请求参数

 _types_
  
    
    
类型： **Int32**
  
    
    
要包含的角色类型。用户 = 1，文档 = 2，站点 = 4，标签 = 8。允许按位组合。
  
    
    

### 响应

 **Followed**
  
    
    
类型： **SP.Social.SocialActor** 的数组
  
    
    
当前用户正在关注的用户、文档、站点以及标签。
  
    
    
以下响应表示一个文件、一个站点和一个标签。请求中的  _types_ 参数指定了要包含的角色类型。
  
    
    



```
{"d":{"Followed":{"results":[
  {"__metadata":{"type":"SP.Social.SocialActor"}
  "AccountName":null
  "ActorType":1
  "CanFollow":true
  "ContentUri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
  "EmailAddress":null
  "FollowedContentUri":null
  "Id":"2.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.51bbb5d8e214457ba794669345d23040.98b9fc73d5224265b039586688b15b98"
  "ImageUri":null
  "IsFollowed":true
  "LibraryUri":null
  "Name":"snippets.txt"
  "PersonalSiteUri":null
  "Status":0
  "StatusText":null
  "TagGuid":"00000000-0000-0000-0000-000000000000"
  "Title":null
  "Uri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"}
  {"__metadata":{"type":"SP.Social.SocialActor"}
  "AccountName":null
  "ActorType":2
  "CanFollow":true
  "ContentUri":"https://domain.sharepoint.com:443/"
  "EmailAddress":null
  "FollowedContentUri":null
  "Id":"8.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.089f4944a6374a64b52b7af5ba140392.98b9fc73d5224265b039586688b15b98"
  "ImageUri":null
  "IsFollowed":true
  "LibraryUri":null
  "Name":"Developer Site"
  "PersonalSiteUri":null
  "Status":0
  "StatusText":null
  "TagGuid":"00000000-0000-0000-0000-000000000000"
  "Title":null
  "Uri":"https://domain.sharepoint.com:443/"}
  {"__metadata":{"type":"SP.Social.SocialActor"}
  "AccountName":null
  "ActorType":3
  "CanFollow":true
  "ContentUri":null
  "EmailAddress":null
  "FollowedContentUri":null
  "Id":"16.00000000000000000000000000000000.00000000000000000000000000000000.19a4a484c1dc4bc58c93bb96245ce928.98b9fc73d5224265b039586688b15b98"
  "ImageUri":null
  "IsFollowed":true
  "LibraryUri":null
  "Name":"#someTag"
  "PersonalSiteUri":null
  "Status":0
  "StatusText":null
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928"
  "Title":null
  "Uri":"https://somecompany-my.sharepoint.com:443/_layouts/15/HashTagProfile.aspx?
    TermID=19a4a484-c1dc-4bc5-8c93-bb96245ce928"}
]}}}
```


## My/FollowedCount
<a name="bk_FollowedCount"> </a>

获取当前用户正在关注的用户、文档、站点和标签的数目。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followedcount(types=15)`
  
    
    

### 请求参数

 _types_
  
    
    
类型： **Int32**
  
    
    
要包含的主角类型。用户 = 1，文档 = 2，站点 = 4，标签 = 8。允许按位组合。
  
    
    

### 响应

 **FollowedCount**
  
    
    
类型： **Int32**
  
    
    
当前用户正在关注的用户、文档、站点和标签的数目。
  
    
    
以下响应表示当前用户正在关注三个指定类型的角色。请求中的  _types_ 参数指定了要包含的角色类型。
  
    
    



```

{"d":{"FollowedCount":3}}
```


## My/Followers
<a name="bk_Followers"> </a>

获取正在关注当前用户的用户。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followers`
  
    
    

### 请求参数

无。
  
    
    

### 响应

 **Followers**
  
    
    
类型： **SP.Social.SocialActor** 的数组
  
    
    

  
    
    
下列响应表示正在关注当前用户的一个用户。
  
    
    



```
{"d":{"Followers":{"results":[
  {"__metadata":{"type":"SP.Social.SocialActor"},
  "AccountName":"domain\\\\user",
  "ActorType":0, 
  "CanFollow":true, 
  "ContentUri":null, 
  "EmailAddress":"user@domain.com", 
  "FollowedContentUri":null, 
  "Id":"1.60a6bd2d1537446880bb4a5a5b07fd63.3a6c6893e6b549cebffefcfa97412dcf.00093edb336e47ac8791bab0a0b77c5d.0c37852b34d0418e91c62ac25af4be5b",
  "ImageUri":null, 
  "IsFollowed":true, 
  "LibraryUri":null, 
  "Name":"User Name",
  "PersonalSiteUri":"http://server/my/personal/user/",
  "Status":0, 
  "StatusText":"",
  "TagGuid":"00000000-0000-0000-0000-000000000000",
  "Title":"SALES DIRECTOR", 
  "Uri":"http://server:80/my/Person.aspx?accountname=domain%5Cuser"}
]}}}
```


## My/Suggestions
<a name="bk_Suggestions"> </a>

获取当前用户可能需要关注的人员。
  
    
    

> **注释**
> 联系人建议功能取决于用户的关注活动、搜索爬网和搜索分析。请参阅 [SharePoint Online 上的联系人建议的工作原理](follow-people-in-sharepoint-2013.md#bk_PeopleSuggestions)。 
  
    
    


### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/suggestions`
  
    
    

### 请求参数

无。
  
    
    

### 响应

 **Suggestions**
  
    
    
类型： **SP.Social.SocialActor**的数组
  
    
    
当前用户可能需要关注的人员。
  
    
    

## GetMySuggestions
<a name="bk_GetMySuggestions"> </a>

获取当前用户可能需要关注的人员。
  
    
    

> **注释**
> 联系人建议功能取决于用户的关注活动、搜索爬网和搜索分析。请参阅 [SharePoint Online 上的联系人建议的工作原理](follow-people-in-sharepoint-2013.md#bk_PeopleSuggestions)。 
  
    
    


### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getmysuggestions`
  
    
    

### 请求参数

无。
  
    
    

### 响应

 **Suggestions**
  
    
    
类型： **SP.UserProfiles.PersonProperties** 的列表
  
    
    
当前用户可能需要关注的人员。
  
    
    

## IsMyPeopleListPublic
<a name="bk_IsMyPeopleListPublic"> </a>

了解当前用户的"我正在关注的人员"列表是否为公共列表。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/ismypeoplelistpublic`
  
    
    

### 请求参数

无。
  
    
    

### 响应

 **IsMyPeopleListPublic**
  
    
    
类型： **bool**
  
    
    
 **true** 表示当前用户的好友列表为公开列表；否则，为 **false**。
  
    
    
下列响应表示当前用户的好友列表为公开列表。
  
    
    



```

{"d":{"IsMyPeopleListPublic":true}}
```


## AmIFollowedBy
<a name="bk_AmIFollowedBy"> </a>

了解指定人员是否在关注当前用户。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/amifollowedby(accountName=@v)?@v='domain\\user'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/amifollowedby(accountName=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 请求参数

 _accountName_
  
    
    
类型： **String**
  
    
    
目标用户的帐户名称。
  
    
    

### 响应

 **AmIFollowedBy**
  
    
    
类型： **bool**
  
    
    
 **true** 表示指定用户正在关注当前用户；否则，为 **false**。
  
    
    
下列响应表示指定人员没有关注当前用户。
  
    
    



```
{"d":{"AmIFollowedBy":false}}
```


## GetPeopleFollowedBy
<a name="bk_GetPeopleFollowedBy"> </a>

让指定用户关注一些用户。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getpeoplefollowedby(accountName=@v)?@v='domain\\user'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getpeoplefollowedby(accountName=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 请求参数

 _accountName_
  
    
    
类型： **String**
  
    
    
目标用户的帐户名称。
  
    
    

### 响应

 **GetPeopleFollowedBy**
  
    
    
类型： **SP.UserProfiles.PersonProperties** 的列表
  
    
    
被指定用户关注的用户。
  
    
    
下列响应表示指定用户关注的两位用户。
  
    
    



```
{"d":{"results":[
  {"__metadata":{
    "id":"http://server/sites/dev/_api/SP.UserProfiles.PersonPropertiesa776ccd0-5566-47d2-9d59-3422cf1fb362",
    "uri":"http://server/sites/dev/_api/SP.UserProfiles.PersonPropertiesa776ccd0-5566-47d2-9d59-3422cf1fb362",
    "type":"SP.UserProfiles.PersonProperties"
  },
  "AccountName":"domain\\\\user1",
  "DirectReports":{"results":[]},
  "DisplayName":"User Name",
  "Email":"user@domain.com",
  "ExtendedManagers":{"results":[]},
  "ExtendedReports":{"results":["domain\\\\user1"]},
  "IsFollowed":true,
  "LatestPost":null,
  "Peers":{"results":[]},
  "PersonalUrl":"http://server/my/personal/user1/",
  "PictureUrl":null,
  "Title":null,
  "UserProfileProperties":{"results":[
    {"__metadata":{"type":"SP.KeyValue"},"Key":"UserProfile_GUID","Value":"00093edb-336e-47ac-8791-bab0a0b77c5d","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SID","Value":"S-1-5-09-4830882673-197582990-1037597527-29477","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"ADGuid","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"AccountName","Value":"domain\\\\user1","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"FirstName","Value":"User","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticFirstName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"LastName","Value":"Name","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticLastName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PreferredName","Value":"User Name","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticDisplayName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WorkPhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Department","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Title","Value":"SALES DIRECTOR","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-JobTitle","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Department","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Manager","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"AboutMe","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PersonalSpace","Value":"/my/personal/user1/","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PictureURL","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"UserName","Value":"user1","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"QuickLinks","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WebSite","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PublicSiteRedirect","Value":"http://cox64-096/my/personal/user1/","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Dotted-line","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Peers","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Responsibility","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SipAddress","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MySiteUpgrade","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ProxyAddresses","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-HireDate","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DisplayOrder","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimProviderID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimProviderType","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SavedAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SavedSID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ResourceSID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ResourceAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ObjectExists","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MasterAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-UserPrincipalName","Value":"user1@company.com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PersonalSiteCapabilities","Value":"14","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-O15FirstRunExperience","Value":"15","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PersonalSiteInstantiationState","Value":"2","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DistinguishedName","Value":"CN=user1 (User Name),OU=UserAccounts,DC=domain,DC=corp,DC=company,DC=com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SourceObjectDN","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-FeedIdentifier","Value":"http://server/my/personal/user1;1.60a6bd2d1537446880bb4a5a5b07fd63.3a6c6893e6b549cebffefcfa97412dcf.50dcee8186ae4dd6904d1650d3d39e54.0c37852b34d0418e91c62ac25af4be5b","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WorkEmail","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"CellPhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Fax","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"HomePhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Office","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Location","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Assistant","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PastProjects","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Skills","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-School","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Birthday","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-StatusNotes","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Interests","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-HashTags","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-EmailOptin","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PrivacyPeople","Value":"True","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PrivacyActivity","Value":"4095","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-TimeZone","Value":"","ValueType":"Edm.String"}]
  },
  "UserUrl":"http://server:80/my/Person.aspx?accountname=domain%5Cuser1"},
  {"__metadata":{
    "id":"http://server/sites/dev/_api/SP.UserProfiles.PersonPropertiesf0ddf6e4-e69c-453f-9a7f-44e0e47d89d4",
    "uri":"http://server/sites/dev/_api/SP.UserProfiles.PersonPropertiesf0ddf6e4-e69c-453f-9a7f-44e0e47d89d4",
    "type":"SP.UserProfiles.PersonProperties"},
  "AccountName":"domain\\\\user2",
  "DirectReports":{"results":[]},
  "DisplayName":"User Name",
  "Email":"user2@company.com", 
  "ExtendedManagers":{"results":[]},
  "ExtendedReports":{"results":["domain\\\\user2"]},
  "IsFollowed":true,"LatestPost":null, 
  "Peers":{"results":[]},
  "PersonalUrl":"http://server/my/Person.aspx?accountname=domain%5Cuser2",
  "PictureUrl":null, 
  "Title":null, 
  "UserProfileProperties":{"results":[
    {"__metadata":{"type":"SP.KeyValue"},"Key":"UserProfile_GUID","Value":"40deca2e-6231-43f9-9559-9a51b0135067","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SID","Value":" S-1-5-09-4830882673-197582990-1037597527-0688328","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"ADGuid","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"AccountName","Value":"domain\\\\user2","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"FirstName","Value":"User","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticFirstName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"LastName","Value":"Name","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticLastName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PreferredName","Value":"User2","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticDisplayName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WorkPhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Department","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Title","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-JobTitle","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Department","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Manager","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"AboutMe","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PersonalSpace","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PictureURL","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"UserName","Value":"user2","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"QuickLinks","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WebSite","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PublicSiteRedirect","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Dotted-line","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Peers","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Responsibility","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SipAddress","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MySiteUpgrade","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ProxyAddresses","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-HireDate","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DisplayOrder","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimProviderID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimProviderType","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SavedAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SavedSID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ResourceSID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ResourceAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ObjectExists","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MasterAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-UserPrincipalName","Value":"user2@company.com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PersonalSiteCapabilities","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-O15FirstRunExperience","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PersonalSiteInstantiationState","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DistinguishedName","Value":"CN=User2,OU=UserAccounts,DC=domain,DC=corp,DC=company,DC=com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SourceObjectDN","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-FeedIdentifier","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WorkEmail","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"CellPhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Fax","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"HomePhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Office","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Location","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Assistant","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PastProjects","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Skills","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-School","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Birthday","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-StatusNotes","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Interests","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-HashTags","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-EmailOptin","Value":"0","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PrivacyPeople","Value":"True","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PrivacyActivity","Value":"4095","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-TimeZone","Value":"","ValueType":"Edm.String"}]
  },
  "UserUrl":"http://server:80/my/Person.aspx?accountname=domain%5Cuser2"}
]}}
```


## GetFollowersFor
<a name="bk_GetFollowersFor"> </a>

获取正在关注指定用户的用户。
  
    
    

### 端点 URI 结构

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getfollowersfor(accountName=@v)?@v='domain\\user'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getfollowersfor(accountName=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 请求参数

 _accountName_
  
    
    
类型： **String**
  
    
    
目标用户的帐户名称。
  
    
    

### 响应

 **GetFollowersFor**
  
    
    
类型： **SP.UserProfiles.PersonProperties** 的列表
  
    
    
正在关注指定用户的用户。
  
    
    
以下响应表示正在关注指定用户的用户。
  
    
    



```

{"d":{"results":[
  {"__metadata":{
    "id":"http://server/sites/dev/_api/SP.UserProfiles.PersonPropertiesabe0c40e-ce77-4631-9fc9-ec20b859061c",
    "uri":"http://server/sites/dev/_api/SP.UserProfiles.PersonPropertiesabe0c40e-ce77-4631-9fc9-ec20b859061c",
    "type":"SP.UserProfiles.PersonProperties"
  },
  "AccountName":"domain\\\\user",
  "DirectReports":{"results":[]},
  "DisplayName":"User Name",
  "Email":"user@domain.com",
  "ExtendedManagers":{"results":[]},
  "ExtendedReports":{"results":["domain\\\\user"]},
  "IsFollowed":false,
  "LatestPost":"#tally",
  "Peers":{"results":[]},
  "PersonalUrl":"http://server/my/personal/user/",
  "PictureUrl":null,
  "Title":"MARKETING DIRECTOR",
  "UserProfileProperties":{"results":[
    {"__metadata":{"type":"SP.KeyValue"},"Key":"UserProfile_GUID","Value":"fa59ba73-edd4-4dc9-97d1-8ada702aae7f","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SID","Value":" S-1-5-09-4830882673-197582990-1037597527-002428","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"ADGuid","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"AccountName","Value":"domain\\\\user","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"FirstName","Value":"User","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticFirstName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"LastName","Value":"Name","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticLastName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PreferredName","Value":"User Name","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PhoneticDisplayName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WorkPhone","Value":"+1 (208) 3192190 X2190","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Department","Value":"Marketing","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Title","Value":"MARKETING DIRECTOR","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-JobTitle","Value":"MARKETING DIRECTOR","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Department","Value":"Marketing","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Manager","Value":"DOMAIN\\\\randalli","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"AboutMe","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PersonalSpace","Value":"/my/personal/user/","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PictureURL","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"UserName","Value":"user","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"QuickLinks","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WebSite","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"PublicSiteRedirect","Value":"http://my/sites/user/","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DataSource","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MemberOf","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Dotted-line","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Peers","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Responsibility","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SipAddress","Value":"user@domain.com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MySiteUpgrade","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DontSuggestList","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ProxyAddresses","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-HireDate","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DisplayOrder","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimProviderID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ClaimProviderType","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-LastColleagueAdded","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-OWAUrl","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SavedAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SavedSID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ResourceSID","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ResourceAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ObjectExists","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MasterAccountName","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-UserPrincipalName","Value":"user@domain.com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PersonalSiteCapabilities","Value":"14","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-O15FirstRunExperience","Value":"15","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PersonalSiteInstantiationState","Value":"2","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-DistinguishedName","Value":"CN=User Name,OU=UserAccounts,DC=domain,DC=corp,DC=company,DC=com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-SourceObjectDN","Value":"CN=User Name,OU=UserAccounts,DC=domain,DC=corp,DC=company,DC=com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-LastKeywordAdded","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-FeedIdentifier","Value":"http://server/my/personal/user;1.64769ec247734e699a5616f1701f7d94.ab42c829ec534daa99fc5909ef940213.3fb2a502be274948a665fcb5e8b2a58d.0c37852b34d0418e91c62ac25af4be5b","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"WorkEmail","Value":"user@domain.com","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"CellPhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Fax","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"HomePhone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Office","Value":"2253","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Location","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"Assistant","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PastProjects","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Skills","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-School","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Birthday","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-StatusNotes","Value":"#tally","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Interests","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-HashTags","Value":"#tally","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-EmailOptin","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PrivacyPeople","Value":"True","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-PrivacyActivity","Value":"4095","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-MUILanguages","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ContentLanguages","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-TimeZone","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-RegionalSettings-FollowWeb","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Locale","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-CalendarType","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-AltCalendarType","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-AdjustHijriDays","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-ShowWeeks","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-WorkDays","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-WorkDayStartHour","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-WorkDayEndHour","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-Time24","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-FirstDayOfWeek","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-FirstWeekOfYear","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SPS-RegionalSettings-Initialized","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"EduUserRole","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"EduPersonalSiteState","Value":"","ValueType":"Edm.String"}, 
    {"__metadata":{"type":"SP.KeyValue"},"Key":"EduOAuthTokenProviders","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"SISUserId","Value":"","ValueType":"Edm.String"},
    {"__metadata":{"type":"SP.KeyValue"},"Key":"EduExternalSyncState","Value":"","ValueType":"Edm.String"}]
  },
  "UserUrl":"http://server:80/my/Person.aspx?accountname=domain%5Cuser"}
]}}
```


## 其他资源
<a name="bk_addresources"> </a>


-  [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)
    
  
-  [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint User Profiles JavaScript Reference (sp.userprofiles.js)](http://msdn.microsoft.com/library/80cf5436-6aa2-6f11-a782-66a04f6e2fb0%28Office.15%29.aspx)
    
  
-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
