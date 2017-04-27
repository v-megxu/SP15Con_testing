---
title: SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索
ms.prod: SHAREPOINT
ms.assetid: 58e68fb2-ba40-4861-912f-355e119a1c41
---


# SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索
了解引用线索和摘要线索，它们是组成 SharePoint Server 2013 中好友动态订阅源的线索集合中可能包括的线索类型。
当您检索好友动态订阅源时，SharePoint Server 2013 将返回一个  [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) 对象，该对象包含组成该源的 [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) 对象的集合。这些线索可以代表对话、单个微博帖子和通知（其中包括事件和引用线索）。代表对话的线索可能会由服务器作为摘要线索返回。
  
    
    


> **注释**
> 本文中引用的 API 来自 .NET 客户端对象模型。但是，其他 API 中的相应对象可能会有所不同。请参阅 [其他资源](#bk_addresources)获取指向其他相关 API 的链接。 
  
    
    


## SharePoint Server 2013 好友动态订阅源中的引用线索是什么？
<a name="bk_whatAreRefThreads"> </a>

当用户关注某帖子、在帖子中提及某人、回复帖子或者在帖子中包含标签时，SharePoint Server 2013 会生成一个引用线索。引用线索具有两个可用于获取有关所引用对话或帖子的信息的属性： [ThreadType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.ThreadType.aspx) 和 [PostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.PostReference.aspx) 。
  
    
    
您可以通过引用线索的  [ThreadType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.ThreadType.aspx) 属性（可返回表 1 中所示的某个值）来标识该线索。
  
    
    

**表 1. 引用线索类型**


|**引用类型**|**说明**|
|:-----|:-----|
| [LikeReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.LikeReference.aspx) **** <br/> |对用户关注的帖子的引用。  <br/> |
| [MentionReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.MentionReference.aspx) <br/> |对提及某用户的帖子的引用。  <br/> |
| [ReplyReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.ReplyReference.aspx) <br/> |对回复的引用。  <br/> |
| [TagReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.TagReference.aspx) <br/> |对包含标签的帖子的引用。  <br/> |
| [Normal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.Normal.aspx) <br/> |不是引用线索。  <br/> |
   
 [PostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.PostReference.aspx) 属性返回包含有关触发该事件的线索信息的 [SocialPostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostReference.aspx) 对象。它至少包含源线索的 ID，稍后您可将其与 [SocialFeedManager.GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) 方法结合使用以检索该线索（如果仍存在）。
  
    
    
 [SocialPostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostReference.aspx) 还可能包含源帖子或线索的副本。其可用性取决于源类型、线索类型和安全修整。如果该引用确实包含帖子或线索，则这些对象代表事件发生时帖子或线索的快照。
  
    
    
并非所有与源相关的活动都会作为引用线索发布到订阅源。例如，关注通知（例如某人何时开始关注某网站）并不是引用线索。
  
    
    

> **注释**
> SharePoint Server 2013 会对自动生成的帖子中的内容以及定向到网站源的所有帖子中的网站访问自动进行安全修整。但是，您可以使用 **SecurityUris** 属性通过指定 URL 来对所有帖子进行安全修整。没有访问该 URL 的权限的用户不会收到帖子。
  
    
    

回复、关注和提及引用将无限期存储在用户的个人订阅源中。标签引用存储在分布式缓存中，以便暂时存储它们。有关缓存的详细信息，请参阅  [SharePoint Server 2013 中的微博功能、订阅源和分布式缓存服务概述](http://technet.microsoft.com/zh-cn/library/jj219700%28v=office.15%29.aspx#cache)。
  
    
    

## SharePoint Server 2013 好友动态订阅源中的摘要线索是什么？
<a name="bk_whatAreDigests"> </a>

摘要线索代表对话的精简版本它包含线索的根帖子以及两条最新回复。您可以通过检查线索是否在其  [Attributes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.Attributes.aspx) 属性 (property) 中应用了 [IsDigest](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadAttributes.IsDigest.aspx) 属性 (attribute) 来确定摘要线索。若要查看某线索是否包含两条以上回复，请检查 [TotalReplyCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.TotalReplyCount.aspx) 属性 (property)。
  
    
    
为了优化性能，当线索包含两条以上回复时，服务器将返回摘要线索。如果您要获取某个线索的所有回复，请调用  [SocialFeedManager.GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) 方法并传入线索 ID。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  
- .NET 客户端对象模型中的  [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx)
    
  
- JavaScript 对象模型中的  [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx)
    
  
- 服务器对象模型中的  [SPSocialThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialThread.aspx)
    
  

