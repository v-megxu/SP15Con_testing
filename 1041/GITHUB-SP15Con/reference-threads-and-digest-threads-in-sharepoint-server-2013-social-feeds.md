---
title: SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド
ms.prod: SHAREPOINT
ms.assetid: 58e68fb2-ba40-4861-912f-355e119a1c41
---


# SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド
参照スレッドおよびダイジェスト スレッドについて説明します。これらは、SharePoint Server 2013 でソーシャル フィードを構成するスレッドのコレクションに含めることができるスレッドの種類です。
ソーシャル フィードを取得すると、SharePoint Server 2013 からは、フィードを構成する  [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) オブジェクトのコレクションを含む [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) オブジェクトが返されます。スレッドは、会話、1 つのミニブログ投稿、および通知を表す場合があり、イベントや参照スレッドが含まれます。会話を表すスレッドは、サーバーからダイジェスト スレッドとして返される場合があります。
  
    
    


> **メモ**
> この記事で参照されている API は, .NET クライアント オブジェクト モデルのものです。ただし、他の API の対応するオブジェクトは異なる場合があります。他の関連 API へのリンクについては、「 [その他の技術情報](#bk_addresources)」を参照してください。 
  
    
    


## SharePoint Server 2013 ソーシャル フィードでの参照スレッドの概要
<a name="bk_whatAreRefThreads"> </a>

ユーザーが投稿をお気に入りにしたとき、投稿で他のユーザーに言及したとき、投稿に返信したとき、または投稿にタグを含めたときは、SharePoint Server 2013 によって参照スレッドが生成されます。参照されているスレッドまたは投稿に関する情報を取得するには、参照スレッドに含まれる 2 つのプロパティ  [ThreadType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.ThreadType.aspx) および [PostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.PostReference.aspx) を使用します。
  
    
    
参照スレッドを識別するには  [ThreadType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.ThreadType.aspx) プロパティを使用します。このプロパティで返される値を表 1 に示します。
  
    
    

**表 1. 参照スレッドの種類**


|**参照の種類**|**説明**|
|:-----|:-----|
| [LikeReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.LikeReference.aspx) **** <br/> |ユーザーがお気に入りの投稿に対する参照。  <br/> |
| [MentionReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.MentionReference.aspx) <br/> |ユーザーに言及している投稿に対する参照。  <br/> |
| [ReplyReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.ReplyReference.aspx) <br/> |返信への参照。  <br/> |
| [TagReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.TagReference.aspx) <br/> |タグを含む投稿への参照。  <br/> |
| [Normal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.Normal.aspx) <br/> |参照スレッドではありません。  <br/> |
   
 [PostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.PostReference.aspx) プロパティは、イベントをトリガーしたスレッドに関する情報を含む [SocialPostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostReference.aspx) オブジェクトを返します。このオブジェクトには少なくともソース スレッドの ID が含まれ、スレッドがまだ存在する場合は、この ID を [SocialFeedManager.GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) メソッドで使用してスレッドを取得できます。
  
    
    
 [SocialPostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostReference.aspx) には、ソース投稿またはソース スレッドのコピーも含まれる場合があります。これらが含まれるかどうかは、フィードの種類、スレッドの種類、およびセキュリティ トリミングによって決まります。参照に投稿またはスレッドが含まれる場合、これらのオブジェクトはイベントが発生した時点での投稿またはスレッドのスナップショットを表します。
  
    
    
フィード関連のアクティビティの中には、参照スレッドとしてフィードに投稿されないものもあります。たとえば、フォロー通知 (他のユーザーがサイトのフォローを開始したときなど) は、参照スレッドではありません。
  
    
    

> **メモ**
> SharePoint Server 2013 は、自動生成された投稿の内容およびサイト フィード宛のすべての投稿におけるサイト アクセスに対して、自動的にセキュリティ トリミングを行います。ただし、 **SecurityUris** 属性を使用すると、URL を指定することにより任意の投稿に対してセキュリティ トリミングを行うことができます。URL へのアクセス権を持たないユーザーは、投稿を受け取りません。
  
    
    

返信、お気に入り、および言及の参照は、ユーザーの個人フィードに無期限に格納されます。タグ参照は分散キャッシュに格納されるので、保存は一時的です。キャッシュの詳細については、「 [SharePoint Server 2013 のミニブログ機能、フィード、分散キャッシュ サービスの概要](http://technet.microsoft.com/ja-jp/library/jj219700%28v=office.15%29.aspx#cache)」を参照してください。
  
    
    

## SharePoint Server 2013 ソーシャル フィードでのダイジェスト スレッドの概要
<a name="bk_whatAreDigests"> </a>

ダイジェスト スレッドはスレッドの簡易版を表し、スレッドのルート投稿と最新の 2 つの返信を含みます。ダイジェスト スレッドは、スレッドの  [Attributes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.Attributes.aspx) プロパティで [IsDigest](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadAttributes.IsDigest.aspx) 属性が適用されているかどうかを調べることによって識別できます。スレッドに 3 つ以上の返信が含まれるかどうかを知るには、 [TotalReplyCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.TotalReplyCount.aspx) プロパティを調べます。
  
    
    
パフォーマンスを最適化するため、スレッドに 3 つ以上の返信が含まれるときは、サーバーはダイジェスト スレッドを返します。スレッドのすべての返信を取得する場合は、 [SocialFeedManager.GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) メソッドを呼び出してスレッド ID を渡します。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  
- .NET クライアント オブジェクト モデルの  [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx)
    
  
- JavaScript オブジェクト モデルの  [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx)
    
  
- サーバー オブジェクト モデルの  [SPSocialThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialThread.aspx)
    
  

