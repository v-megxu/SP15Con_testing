---
title: 通过 SharePoint 2013 跟踪人员
ms.prod: SHAREPOINT
ms.assetid: 0fa2e235-63d0-41b1-9eed-4aeb2f59a14d
---



# 通过 SharePoint 2013 跟踪人员
了解有关在 SharePoint Server 2013 中关注人员的常见编程任务。
## 用于在 SharePoint Server 2013 中关注人员的 API
<a name="bkmk_APIversions"> </a>

当用户在 SharePoint Server 2013 中关注人员时，人员发布的微博文章以及与其活动相关的通知将显示在用户的新闻源中。与关注人员相关的功能会显示在"新闻源"和"我正在关注的人员" 页上。
  
    
    
SharePoint Server 2013 提供了以下几个可用于以编程方式关注人员的 API：
  
    
    

- 托管代码的客户端对象模型
    
  - .NET 客户端对象模型
    
  
  - Silverlight 客户端对象模型
    
  
  - 移动设备客户端对象模型
    
  
- JavaScript 对象模型
    
  
- 代表性状态传输 (REST) 服务
    
  
- 服务器对象模型
    
  
作为 SharePoint 2013 开发中的最佳实践，只要可能，就是用客户端 API。客户端 API 包括客户端对象模型、JavaScript 对象模型和 REST 服务。有关 SharePoint 2013 中的 API 以及何时使用他们的详细信息，请参阅  [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    
每个 API 均包含一个可用于执行关注人员的核心任务的管理器对象。
  
    
    

> **注释**
> 使用相同的 API 关注内容。请参阅 [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)，获取"关注内容"任务的概述。 
  
    
    

表 1 显示了这些 API 中的管理器和其他关键对象（或 REST 资源），以及可在其中查找 API 的类库（或接入点）。
  
    
    

> **注释**
> 表 1 或表 2 中没有明确包含 Silverlight 和移动客户端对象模型，这是因为它们提供与 .NET 客户端对象模型相同的核心功能并使用相同的签名。Silverlight 客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll 中定义，而移动客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Phone.dll 中定义。 
  
    
    


**表 1. 用于以编程方式关注人员的 SharePoint 2013 API**

|||
|:-----|:-----|
|.NET 客户端对象模型  <br/> 请参阅： [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md) <br/> |管理器对象：           [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) <br/> 主命名空间：           [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> 其他关键对象：           [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 、 [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) 、 [SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) 、 [SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) <br/> 类库：          Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript 对象模型  <br/> 请参阅： [如何：在 SharePoint 2013 中使用 JavaScript 对象模型关注好友](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md) <br/> |管理器对象：           [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> 主命名空间：          **SP.Social** <br/> 其他关键对象：           [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx)、 [SocialActorInfo](http://msdn.microsoft.com/library/d940db32-1561-c868-bb66-0612e2031f17%28Office.15%29.aspx)、 [SocialActorType](http://msdn.microsoft.com/library/fbde74da-f292-dc87-0b7e-81bc5b7a880c%28Office.15%29.aspx)、 [SocialActorTypes](http://msdn.microsoft.com/library/a460c3e6-ed88-117d-6755-4c5803a154a0%28Office.15%29.aspx) <br/> 类库：          SP.UserProfiles.js  <br/> |
|REST 服务  <br/> 请参阅： [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> |管理器资源：           [social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> 终结点 URI：           `<siteUri>/_api/social.following` <br/> 主命名空间 (OData)：          **sp.social.SocialRestFollowingManager** <br/> 其他关键资源：          **SocialActor**、 **SocialActorInfo**、 **SocialActorType**、 **SocialActorTypes** <br/> |
|服务器对象模型  <br/> |管理器对象：           [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.aspx) <br/> 主命名空间：           [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> 其他关键对象：           [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) 、 [SPSocialActorInfo](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorInfo.aspx) 、 [SPSocialActorType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorType.aspx) 、 [SPSocialActorTypes](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorTypes.aspx) <br/> 类库：          Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## 有关在 SharePoint Server 2013 中关注人员的常见编程任务
<a name="bkmk_CommonTasks"> </a>

表 2 显示了用于关注人员的常见编程任务以及可用于执行这些任务的成员。这些成员来自 .NET 客户端对象模型 (CSOM)、JavaScript 对象模型 (JSOM)、REST 服务和服务器对象模型 (SSOM)。
  
    
    

> **注释**
> 使用相同的 API 关注内容。请参阅 [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)，获取"关注内容"任务的概述。 
  
    
    

 **SocialFollowingManager** 对象将当前用户的核心"关注人员"和"关注内容"功能融合在一起。但是， **PeopleManager** 对象（见表 3）提供了 **SocialFollowingManager** 未提供的某些功能，包括用于获取其他用户的关注人员状态的方法。
  
    
    

**表 2. 用于通过使用 SocialFollowingManager 对象关注人员的常见任务的 API**


|**任务**|**成员**|
|:-----|:-----|
|在当前用户的上下文中创建管理器对象实例  <br/> |CSOM： [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.#ctor.aspx) <br/> JSOM： **SocialFollowingManager** <br/> REST： `<siteUri>/_api/social.following` <br/> SSOM： [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) <br/> |
|在特定用户的上下文中创建管理器对象实例  <br/> |CSOM：未实现  <br/> JSOM：未实现  <br/> REST：未实现  <br/> SSOM： [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) （重载） <br/> |
|让当前用户开始关注（停止关注）某个人员  <br/> |CSOM： [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) ) <br/> JSOM： [follow](http://msdn.microsoft.com/library/40d14320-27ba-2941-b0e2-be3b5a407c89%28Office.15%29.aspx) ( [stopFollowing](http://msdn.microsoft.com/library/65b0e9be-dc5e-09fb-c57f-7a933de09a4c%28Office.15%29.aspx))  <br/> REST： [Follow](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Follow) ( [StopFollowing](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_StopFollowing))          **POST** `<siteUri>/_api/social.following/Follow` ( `<siteUri>/_api/social.following/StopFollowing`) 并在请求正文中传递  _actor_ 参数 <br/> SSOM： [Follow](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.StopFollowing.aspx) ) <br/> |
|了解当前用户是否正在关注某个特定用户  <br/> |CSOM： [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) <br/> JSOM： [isFollowed](http://msdn.microsoft.com/library/2c1f62e6-fb75-ad4d-c081-36408b418c21%28Office.15%29.aspx) <br/> REST： [IsFollowed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_IsFollowed)          **POST** `<siteUri>/_api/social.following/my/IsFollowed` 并在请求正文中传递 _actor_ 参数 <br/> SSOM： [IsFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.IsFollowed.aspx) <br/> |
|获取正在关注当前用户的人员  <br/> |CSOM： [GetFollowers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowers.aspx) <br/> JSOM： [getFollowers](http://msdn.microsoft.com/library/ae4a944b-c043-05fb-c74b-101d2ce4a813%28Office.15%29.aspx) <br/> REST： [Followers](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followers)          **GET** `<siteUri>/_api/social.following/my/Followers` <br/> SSOM： [GetFollowers](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowers.aspx) <br/> |
|获取当前用户正在关注的人员  <br/> |CSOM： [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) <br/> JSOM： [getFollowed](http://msdn.microsoft.com/library/432a7cec-6add-fdb1-a79f-a93414ee8cd3%28Office.15%29.aspx) <br/> REST： [Followed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followed)          **GET** `<siteUri>/_api/social.following/my/Followed(types=1)` <br/> SSOM： [GetFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowed.aspx) <br/> |
|获取当前用户正在关注的人员的计数  <br/> |CSOM： [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) <br/> JSOM： [getFollowedCount](http://msdn.microsoft.com/library/97b53b4f-481a-cf41-1854-8f3ff860b2bb%28Office.15%29.aspx) <br/> REST： [FollowedCount](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_FollowedCount)          **GET** `<siteUri>/_api/social.following/my/FollowedCount(types=1)` <br/> SSOM： [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowedCount.aspx) <br/> |
|获取当前用户可能需要关注的人员  <br/> |CSOM： [GetSuggestions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetSuggestions.aspx) <br/> JSOM： [getSuggestions](http://msdn.microsoft.com/library/95fd9c48-6974-ec08-d3e9-00c2c76f4f79%28Office.15%29.aspx) <br/> REST： [Suggestions](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Suggestions)          **GET** `<siteUri>/_api/social.following/my/Suggestions` <br/> SSOM： [GetSuggestions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetSuggestions.aspx) <br/> |
   
表 3 显示了可用于其他关注人员功能的 **PeopleManager** 成员
  
    
    

**表 3. 用于通过使用 PeopleManager 对象关注人员的常见任务的 API**


|**任务**|**成员**|
|:-----|:-----|
|了解当前用户的"我正在关注的人员"列表是否为公共列表  <br/> |CSOM： [IsMyPeopleListPublic](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.IsMyPeopleListPublic.aspx) <br/> JSOM： [isMyPeopleListPublic](http://msdn.microsoft.com/library/2ffc73a5-24ce-1ed4-d850-a6fea4c773bb%28Office.15%29.aspx) <br/> REST： [IsMyPeopleListPublic](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerProperties)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/IsMyPeopleListPublic` <br/> SSOM： [IsMyPeopleListPublic](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.IsMyPeopleListPublic.aspx) <br/> |
|了解某人是否正在关注当前用户  <br/> |CSOM： [AmIFollowedBy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.AmIFollowedBy.aspx) <br/> JSOM： [amIFollowedBy](http://msdn.microsoft.com/library/3641c469-0063-054d-355d-e56697cb08ae%28Office.15%29.aspx) <br/> REST： [AmIFollowedBy](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerAmIFollowedBy)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/AmIFollowedBy(accountName=@v)?@v='domain\\\\user'` <br/> SSOM： [AmIFollowedBy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.AmIFollowedBy.aspx) <br/> |
|获取某个特定用户正在关注的人员  <br/> |CSOM： [GetPeopleFollowedBy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPeopleFollowedBy.aspx) <br/> JSOM： [getPeopleFollowedBy](http://msdn.microsoft.com/library/e781c0fa-b14a-40ef-976b-b1c6c82beb89%28Office.15%29.aspx) <br/> REST： [GetPeopleFollowedBy](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPeopleFollowedBy)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPeopleFollowedBy(accountName=@v)?@v='domain\\\\user'` <br/> SSOM： [GetPeopleFollowedBy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPeopleFollowedBy.aspx) <br/> |
|获取正在关注某个特定用户的人员  <br/> |CSOM： [GetFollowersFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetFollowersFor.aspx) <br/> JSOM： [getFollowersFor](http://msdn.microsoft.com/library/51ef3b75-42b2-4efb-4441-e088dc7d168e%28Office.15%29.aspx) <br/> REST： [GetFollowersFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetFollowersFor)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/GetFollowersFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM： [GetFollowersFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetFollowersFor.aspx) <br/> |
|了解某个特定用户是否正在关注另一个用户  <br/> |CSOM： [IsFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.IsFollowing.aspx) <br/> JSOM： [isFollowing](http://msdn.microsoft.com/library/6a5ce6cb-c710-9e19-0cb9-7fae9e013ec8%28Office.15%29.aspx) <br/> REST： [IsFollowing](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerIsFollowing)（静态）          **GET** `<siteUri>/_api/SP_UserProfiles_PeopleManager_IsFollowing(possibleFollowerAccountName=@v,possibleFolloweeAccountName=@y)?@v='domain\\\\user'&amp;@y='domain\\\\user'` <br/> SSOM： [IsFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.IsFollowing.aspx) <br/> |
   

## SharePoint Online 上的联系人建议的工作原理
<a name="bk_PeopleSuggestions"> </a>

联系人建议的结果基于已建立的关注人员活动。当用户关注某人时，如果该人员与另一个用户尚未关注的人员相互关注，则会提供建议。
  
    
    
与关注相关的内容会在搜索爬网过程中编入索引。完成爬网后，搜索分析必须分析已爬网的关注信息，并输出用户建议。默认情况下，搜索分析每天运行一次。
  
    
    
当用户打开"我正在关注的人员"页时，会调用  [PeopleManager.GetMySuggestions()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMySuggestions.aspx) 方法。 [GetMySuggestions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMySuggestions.aspx) 可为当前用户搜索新的建议、更新数据库中的用户建议并在页面上显示建议。
  
    
    

## 其他资源
<a name="bk_addResources"> </a>


-  [SharePoint 2013 中的社交和协作功能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)
    
  
-  [用户配置文件 REST API 引用](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中使用 JavaScript 对象模型关注好友](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md)
    
  
-  [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
