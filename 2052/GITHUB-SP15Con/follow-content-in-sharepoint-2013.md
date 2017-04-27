---
title: 通过 SharePoint 2013 跟踪内容
ms.prod: SHAREPOINT
ms.assetid: 30e68cd6-6e55-4cf9-afd6-7139b0a97288
---



# 通过 SharePoint 2013 跟踪内容
获悉常见编程任务以跟进 SharePoint Server 2013 中的内容（文档、站点和标记）。
## 用于跟进 SharePoint Server 2013 中的内容的 API
<a name="bkmk_APIversions"> </a>

当用户跟进文档、站点或标记时，文档中的状态更新、站点上的会话和标记使用的通知将显示在其新闻源中。用户可以在"新闻源"和"跟进"内容页上查阅与以下内容相关的功能。
  
    
    
SharePoint Server 2013 提供了以下可用于以编程方式跟进内容的 API：
  
    
    

- 托管代码的客户端对象模型
    
  - .NET 客户端对象模型
    
  
  - Silverlight 客户端对象模型
    
  
  - 移动设备客户端对象模型
    
  
- JavaScript 对象模型
    
  
- 代表性状态传输 (REST) 服务
    
  
- 服务器对象模型
    
  
作为 SharePoint 2013 开发中的最佳实践，如果可以，请使用客户端 API。客户端 API 包括客户端对象模型，JavaScript 对象模型和 REST 服务。有关 SharePoint 2013 中的 API 以及何时使用它们的详细信息，请参阅 [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    
每个 API 都包括您用于执行核心任务以关注内容的管理器对象。
  
    
    

> **注释**
> 将使用相同的 API 来关注人员。请参阅 [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)以获得"关注人员"任务的概述。 
  
    
    

表 1 显示了每个 API 中的管理器和其他关键对象（或 REST 资源）以及可在其中找到 API 的类库（或访问点）。
  
    
    

> **注释**
> Silverlight 和移动客户端对象模型未包含在表 1 或表 2 中，因为它们提供了与 .NET 客户端对象模型相同的核心功能，并使用相同的签名。Silverlight 客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll 中进行定义，而移动客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Phone.dll 中进行定义。 
  
    
    


**表 1.用于以编程方式跟进内容的 SharePoint 2013 API**

|||
|:-----|:-----|
|.NET 客户端对象模型  <br/> 请参阅 [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md) <br/> |管理器对象：           [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) <br/> 主命名空间：           [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> 其他关键对象：           [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 、 [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) 、 [SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) 、 [SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) <br/> 类库：          Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript 对象模型  <br/> |管理器对象：           [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> 主命名空间：           [SP.Social](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) <br/> 其他关键对象：           [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx)、 [SocialActorInfo](http://msdn.microsoft.com/library/d940db32-1561-c868-bb66-0612e2031f17%28Office.15%29.aspx)、 [SocialActorType](http://msdn.microsoft.com/library/fbde74da-f292-dc87-0b7e-81bc5b7a880c%28Office.15%29.aspx)、 [SocialActorTypes](http://msdn.microsoft.com/library/a460c3e6-ed88-117d-6755-4c5803a154a0%28Office.15%29.aspx) <br/> 类库：          SP.UserProfiles.js  <br/> |
|REST 服务  <br/> 请参阅 [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md) <br/> |管理器资源：           [social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> 主命名空间 (OData) ：          **sp.social.SocialRestFollowingManager** <br/> 其他关键资源：          **SocialActor**、 **SocialActorInfo**、 **SocialActorType**、 **SocialActorTypes** <br/> 访问点：           `<siteUri>/_api/social.following` <br/> |
|服务器对象模型  <br/> |管理器对象：           [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.aspx) <br/> 主命名空间：           [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> 其他关键对象：           [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) 、 [SPSocialActorInfo](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorInfo.aspx) 、 [SPSocialActorType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorType.aspx) 、 [SPSocialActorTypes](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorTypes.aspx) <br/> 类库：          Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## 用于跟进 SharePoint Server 2013 中的内容的常见编程任务
<a name="bkmk_CommonTasks"> </a>

表 2 显示了用于跟进内容的常见编程任务以及您用于执行它们的成员。这些成员来自于 .NET 客户端对象模型 (CSOM)、JavaScript 对象模型 (JSOM)、REST 服务和服务器对象模型 (SSOM)。
  
    
    

> **注释**
> 将使用相同的 API 来关注人员。请参阅 [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)以获得"关注人员"任务的概述。 
  
    
    


**表 2. 用于跟进 SharePoint Server 2013 中的内容的常见任务的 API**


|**任务**|**成员**|
|:-----|:-----|
|在当前用户的上下文中创建管理器对象的实例  <br/> |CSOM： [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.#ctor.aspx) <br/> JSOM： [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> REST： `<siteUri>/_api/social.following` <br/> SSOM： [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) <br/> |
|创建指定用户的上下文中的管理器对象的实例  <br/> |CSOM：未实现  <br/> JSOM：未实现  <br/> REST：未实现  <br/> SSOM： [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) （重载） <br/> |
|使得当前用户开始或停止跟进项  <br/> |CSOM： [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) ) <br/> JSOM： [follow](http://msdn.microsoft.com/library/40d14320-27ba-2941-b0e2-be3b5a407c89%28Office.15%29.aspx) ( [stopFollowing](http://msdn.microsoft.com/library/65b0e9be-dc5e-09fb-c57f-7a933de09a4c%28Office.15%29.aspx))  <br/> REST： **POST** [<siteUri>/_api/social.following/Follow](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Follow) ( [<siteUri>/_api/social.following/StopFollowing](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_StopFollowing))          并在请求正文中传递  _actor_ 参数 <br/> SSOM： [Follow](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.StopFollowing.aspx) ) <br/> |
|查明当前用户是否正在跟进某特定项  <br/> |CSOM： [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) <br/> JSOM： [isFollowed](http://msdn.microsoft.com/library/2c1f62e6-fb75-ad4d-c081-36408b418c21%28Office.15%29.aspx) <br/> REST： **POST** [<siteUri>/_api/social.following/IsFollowed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_IsFollowed) 并在请求正文中传递 _actor_ 参数 <br/> SSOM： [IsFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.IsFollowed.aspx) <br/> |
|获取当前用户正在跟进的文档、站点和/或标记  <br/> |CSOM： [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) <br/> JSOM： [getFollowed](http://msdn.microsoft.com/library/432a7cec-6add-fdb1-a79f-a93414ee8cd3%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.following/my/Followed(types=2)](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followed)（文档 = **2**，网站 = **4**，标签 = **8**）  <br/> SSOM： [GetFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowed.aspx) <br/> |
|获取用户正在跟进的文档、站点和/或标记的计数  <br/> |CSOM： [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) <br/> JSOM： [getFollowedCount](http://msdn.microsoft.com/library/97b53b4f-481a-cf41-1854-8f3ff860b2bb%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.following/my/FollowedCount(types=2)](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_FollowedCount)（文档 = **2**，网站 = **4**，标签 = **8**）  <br/> SSOM： [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowedCount.aspx) <br/> |
|获取列出当前用户所跟进的文档的站点的 URI  <br/> |CSOM： [FollowedDocumentsUri](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.FollowedDocumentsUri.aspx) <br/> JSOM： [followedDocumentsUri](http://msdn.microsoft.com/library/3a70b9c7-abd7-94ff-d730-70298673d6ec%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.following/my/FollowedDocumentsUri](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_MyFollowedDocumentsUri) <br/> SSOM： [FollowedDocumentsUri](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.FollowedDocumentsUri.aspx) <br/> |
|获取列出当前用户所跟进的站点的站点 URI  <br/> |CSOM： [FollowedSitesUri](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.FollowedSitesUri.aspx) <br/> JSOM： [followedSitesUri](http://msdn.microsoft.com/library/829404bc-1b3a-7545-5e95-0922df330084%28Office.15%29.aspx) <br/> REST： **GET** [<siteUri>/_api/social.following/my/FollowedSitesUri](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_MyFollowedSitesUri) <br/> SSOM： [FollowedSitesUri](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.FollowedSitesUri.aspx) <br/> |
   

> **注释**
> 有关显示了如何使用 REST 服务关注内容的示例，请参阅 [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)。 
  
    
    


## 如何使用 JavaScript 对象模型基于标签名称获取标签 GUID
<a name="bk_getTagGuid"> </a>

若要开始和停止关注标签或者了解当前用户是否关注该标签，您需要使用标签 GUID。下列代码显示了如何基于标签名称获取 GUID。
  
    
    
在运行代码前，您需要向 **sp.taxonomy.js** 添加一个引用，并使用现有标签的名称更改占位符标签名称。
  
    
    



```

function getTagGuid() {
    var tagName = '#tally';
    var clientContext = new SP.ClientContext.get_current();
    var label = SP.Taxonomy.LabelMatchInformation.newObject(clientContext);
    label.set_termLabel(tagName);
    label.set_trimUnavailable(false);
    var taxSession = SP.Taxonomy.TaxonomySession.getTaxonomySession(clientContext);
    var termStore = taxSession.getDefaultKeywordsTermStore();
    var termSet = termStore.get_hashTagsTermSet();
    terms = termSet.getTerms(label);
    clientContext.load(terms);
    clientContext.executeQueryAsync(
        function () {
            var tag = terms.get_item(0);
            if (tag !== null) {
                var tagGuid = tag.get_id().toString();
                if (!SP.ScriptUtility.isNullOrEmptyString(tagGuid)) {
                    alert(tagGuid);
                }
            }
        },
        function (sender, args) {
            alert(args.get_message());
        }
    );
}

```


## 其他资源
<a name="bk_addResources"> </a>


-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  
-  [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)
    
  
-  [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的社交和协作功能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)
    
  
