---
title: SharePoint 2013 でのソーシャル フィードの操作
ms.prod: SHAREPOINT
ms.assetid: 39f2163e-15cc-43bc-b131-041d5afdcd90
---



# SharePoint 2013 でのソーシャル フィードの操作
SharePoint Server 2013 のソーシャル フィードとマイクロブログの投稿を操作する一般的なプログラミング作業について説明します。
## SharePoint Server 2013 のソーシャル フィード操作用の API
<a name="bkmk_APIversions"> </a>

SharePoint Server 2013 オンプレミス ファームでは、情報の共有や、ユーザーおよびコンテンツとの常時接続が簡単にできるように対話型ソーシャル フィードが設計されています。フィード機能の多くは、ユーザーの個人サイトの [ **ニュースフィード**] ページに表示されます。フィードには、ミニブログの投稿、会話、ステータス更新情報、およびその他の通知を表すスレッドのコレクションが含まれています。
  
    
    
SharePoint Server 2013 は次のような API を提供し、ソーシャル フィードを操作するプログラミングに使用することができます。
  
    
    

- マネージ コード用のクライアント オブジェクト モデル
    
  - .NET クライアント オブジェクト モデル
    
  
  - Silverlight クライアント オブジェクト モデル
    
  
  - モバイル クライアント オブジェクト モデル
    
  
- JavaScript オブジェクト モデル
    
  
- REST (Representational State Transfer) サービス
    
  
- サーバー オブジェクト モデル
    
  
SharePoint 2013 開発のベスト プラクティスとして、できるだけクライアント API を使用してください。クライアント API にはクライアント オブジェクト モデル、JavaScript オブジェクト モデル、REST サービスが含まれます。SharePoint 2013 の API の詳細と使用するタイミングについては、「 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md) 」を参照してください。
  
    
    
各 API にはマネージャー オブジェクトが含まれ、コアのフィード関連作業の実施に使用します。表 1 は、API のマネージャー オブジェクトとその他の主要なオブジェクト (または REST リソース) および API があるクラス ライブラリ (またはエンドポイント URI) を示します。
  
    
    

> **メモ**
> Silverlight およびモバイル クライアント オブジェクト モデルは, .NET クライアント オブジェクト モデルと中核的な機能が同じであり、同じ署名を使用するので、テーブル 1 やテーブル 2 には明示されていません。Silverlight クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll で定義され、モバイル クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Phone.dll で定義されています。 
  
    
    


**表 1. SharePoint 2013 ソーシャル フィードのプログラミングに使用する API**

|||
|:-----|:-----|
|.NET クライアント オブジェクト モデル  <br/> 「 [[方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)」を参照してください。  <br/> |マネージャー オブジェクト:           [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) <br/> プライマリ名前空間:           [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> その他の主要なオブジェクト:            [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) 、 [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) 、 [SocialPost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPost.aspx) 、 [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 、 [SocialFeedOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedOptions.aspx) 、 [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) <br/> クラス ライブラリ:          Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript オブジェクト モデル  <br/> 「 [[方法] SharePoint 2013 で JavaScript オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)」を参照してください。  <br/> |マネージャー オブジェクト:            [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) <br/> プライマリ名前空間:            [SP.Social](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) <br/> その他の主要なオブジェクト:            [SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx)、 [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx)、 [SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx)、 [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx)、 [SocialFeedOptions](http://msdn.microsoft.com/library/65caf283-6e7a-50dc-ef8e-a4e12bd237ac%28Office.15%29.aspx)、 [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx) <br/> クラスライブラリ          SP.UserProfiles.js  <br/> |
|REST サービス  <br/> 「 [[方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)」を参照  <br/> |マネージャー リソース:            [social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md) (SocialRestFeedManager) <br/> プライマリ名前空間 (OData):           **SP.Social** <br/> その他の主要なリソース:           SocialFeed、 [SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed)、SocialThread、 [SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread)、SocialPost、SocialPostCreationData、 [SocialRestPostCreationData](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestPostCreationData)、 [SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions)、SocialActor、 [SociaRestActor](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestActor) <br/> アクセス ポイント:            `<siteUri>/_api/social.feed` <br/> |
|サーバー オブジェクト モデル  <br/> > **メモ**> サーバー オブジェクト モデルを使用してフィード データにアクセスし、リモートで実行するコードは  [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) オブジェクトを使用する必要があります。          
|マネージャー オブジェクト           [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.aspx) <br/> プライマリ名前空間           [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> その他の主要なオブジェクト:            [SPSocialFeed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeed.aspx) 、 [SPSocialThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialThread.aspx) 、 [SPSocialPost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPost.aspx) 、 [SPSocialFeedOptions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedOptions.aspx) 、 [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) <br/> クラス ライブラリ          Microsoft.Office.Server.UserProfiles.dll  <br/> |
   
サーバー オブジェクト モデルを使用してフィード コンテンツにアクセスしていて、コードが Share Point インスタンスで実行されていない場合 (つまり、拡張機能がアプリケーション サーバーの [LAYOUTS] フォルダーにインストールされていない場合 )、 [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) オブジェクトをコードで使用します。以下のコード例は [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) オブジェクトをコードに組み込む 1 つの例を示します。
  
    
    



```cs

using (SPSite site = new SPSite(<siteURL>))
{
    using (new Microsoft.SharePoint.SPServiceContextScope(SPServiceContext.GetContext(site)))
    {
        // code
    }
}

```


## SharePoint Server 2013 のソーシャル フィードを操作する一般的なプログラミング作業
<a name="bkmk_CommonTasks"> </a>

表 2 はソーシャル フィードとそれを実行するメンバーを操作する一般的なプログラミング作業を示します。メンバーは .NET クライアント オブジェクト モデル (CSOM)、JavaScript オブジェクト モデル (JSOM)、REST サービス、サーバー オブジェクト モデル (SSOM) です。
  
    
    

**表 2. SharePoint Server 2013 のソーシャル フィードを操作する一般的なプログラミング作業の API**


|**作業**|**メンバー**|
|:-----|:-----|
|現在のユーザーのコンテキスト内にマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM:  [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.#ctor.aspx) <br/> JSOM:  [SocialFeedManager](http://msdn.microsoft.com/library/f7cf172f-970b-6b71-9eb4-b9a8bb7a0001%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md) <br/> SSOM:  [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.#ctor.aspx) <br/> |
|特定のユーザーのコンテキスト内にマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM: 実装されていません  <br/> JSOM: 実装されていません  <br/> REST: 実装されていません  <br/> SSOM:  [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.#ctor.aspx) <br/> |
|現在のコンテキストのユーザーを取得する  <br/> |CSOM:  [Owner](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.Owner.aspx) <br/> JSOM:  [owner](http://msdn.microsoft.com/library/0307264e-d733-77f0-edae-f5468e58d0b7%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed/my](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_my) <br/> SSOM:  [Owner](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.Owner.aspx) <br/> |
|現在のユーザーのフィードを取得する  <br/> (フィードの種類を指定します)  <br/> |CSOM:  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) <br/> JSOM:  [getFeed](http://msdn.microsoft.com/library/cddaccd8-28da-6798-d8cb-4e9351efddf3%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed/my/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeed) (personal feed)、 [<siteUri>/_api/social.feed/my/News](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myNews),  [<siteUri>/_api/social.feed/my/TimelineFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myTimelineFeed)、または  [<siteUri>/_api/social.feed/my/Likes](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myLikes) <br/> SSOM:  [GetFeed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeed.aspx) <br/> |
|特定のユーザーの個人用フィードを取得する  <br/> |CSOM:  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) <br/> JSOM:  [getFeedFor](http://msdn.microsoft.com/library/074ed255-9393-448d-1f7e-720fdeb05f48%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed/actor(item='domain\\\\user')/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> SSOM:  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeedFor.aspx) <br/> |
|チーム サイトのサイト フィードを取得する  <br/> (サイト フィードの URL をアクターとして指定します (例: http://<siteCollection>/<teamSite>/newsfeed.aspx))  <br/> |CSOM:  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) <br/> JSOM:  [getFeedFor](http://msdn.microsoft.com/library/074ed255-9393-448d-1f7e-720fdeb05f48%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed/actor(item=@v)/Feed?@v='http://<siteCollection>/<teamSite>/newsfeed.aspx'](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> SSOM:  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeedFor.aspx) <br/> |
|ルートの投稿を現在のユーザーのフィードに公開する  <br/> (ターゲットに **null** を指定します) <br/> |CSOM:  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM:  [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.feed/my/Feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeedPost) および要求本文で _restCreationData_ パラメーターを渡す <br/> SSOM:  [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|投稿をサイト フィードに公開する  <br/> (サイト フィードの URL をターゲットとして指定します (例: http://<siteCollection>/teamSite>/newsfeed.aspx))  <br/> |CSOM:  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM:  [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.feed/actor(item=@av)/feed/post/?@av='<teamSiteUri>/newsfeed.aspx'](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeedPost) および要求本文の _restCreationData_ パラメーターを渡す ( _ID_ パラメーターに **null** を指定します) <br/> SSOM:  [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|投稿への返信を公開する  <br/> (対象スレッドの ID を指定)  <br/> |CSOM:  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM:  [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.feed/Post/Reply](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postReply) および要求本文で _restCreationData_ パラメーターを渡す <br/> SSOM:  [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|現在のユーザーのフィード内の投稿、返信、スレッドを削除する (ルートの投稿を削除すると、すべてのスレッドが削除されます)  <br/> |CSOM:  [DeletePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.DeletePost.aspx) <br/> JSOM:  [deletePost](http://msdn.microsoft.com/library/06e03f87-c97d-8634-a02b-f7812eb7beeb%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.feed/Post/Delete](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postDelete) および要求本文で _ID_ パラメーターを渡す <br/> SSOM:  [DeletePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.DeletePost.aspx) <br/> |
|ユーザーのフィードからスレッド (ルートの投稿とそれに対するすべての返信) を取得する  <br/> |CSOM:  [GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) <br/> JSOM:  [getFullThread](http://msdn.microsoft.com/library/6bb384f3-9474-581f-e18d-e8c4f44c3cdf%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_post) および要求本文で _ID_ パラメーターを渡す <br/> SSOM:  [GetFullThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFullThread.aspx) <br/> |
|ユーザーに投稿や返信を like (unlike) してもらう  <br/> |CSOM:  [LikePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.LikePost.aspx) ( [UnlikePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.UnlikePost.aspx) ) <br/> JSOM:  [likePost](http://msdn.microsoft.com/library/f401a584-1712-50af-ee08-2999a16388d6%28Office.15%29.aspx) ( [unlikePost](http://msdn.microsoft.com/library/c778bd7d-91e5-15dc-eeb8-b571957e8338%28Office.15%29.aspx))  <br/> REST: **POST** [<siteUri>/_api/social.feed/Post/Like](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLike) ( [<siteUri>/_api/social.feed/Post/Unlike](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlike)) および要求本文で  _ID_ パラメーターを渡す <br/> SSOM:  [LikePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.LikePost.aspx) ( [UnlikePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.UnlikePost.aspx) ) <br/> |
|投稿の liker をすべて取得する  <br/> |CSOM:  [GetAllLikers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetAllLikers.aspx) <br/> JSOM:  [getAllLikers](http://msdn.microsoft.com/library/76286fdc-002f-2b13-dc26-53097eb2e3a2%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.feed/Post/Likers](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLikers) および要求本文で _ID_ パラメーターを渡す <br/> SSOM:  [GetAllLikers](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetAllLikers.aspx) <br/> |
|注意しているユーザーの投稿を取得する  <br/> |CSOM:  [GetMentions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetMentions.aspx) <br/> JSOM:  [getMentions](http://msdn.microsoft.com/library/78f064c3-5b96-373e-e7f0-8603aedc5ded%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed/my/MentionFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myMentionFeed) <br/> SSOM:  [GetMentions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetMentions.aspx) <br/> |
|現在のユーザーの未読注意数を取得する  <br/> |CSOM:  [GetUnreadMentionCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetUnreadMentionCount.aspx) <br/> JSOM:  [getUnreadMentionCount](http://msdn.microsoft.com/library/18dde16a-f78f-f65e-0644-4eb737b1ae00%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.feed/my/UnreadMentionCount](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myUnreadMentionCount) <br/> SSOM:  [GetUnreadMentionCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetUnreadMentionCount.aspx) <br/> |
|現在のユーザーのフィード内スレッドをロック (ロック解除) する  <br/> |CSOM:  [LockThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.LockThread.aspx) ( [UnlockThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.UnlockThread.aspx) ) <br/> JSOM:  [lockThread](http://msdn.microsoft.com/library/cc696bb7-e7fd-7a57-5db5-736c3733589e%28Office.15%29.aspx) ( [unlockThread](http://msdn.microsoft.com/library/ee9288d6-ace0-1ec2-ea7c-0ee300b6e1ea%28Office.15%29.aspx))  <br/> REST: **POST** [<siteUri>/_api/social.feed/Post/Lock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLock) ( [<siteUri>/_api/social.feed/Post/Unlock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlock)) および要求本文で  _ID_ パラメーターを渡す <br/> SSOM:  [LockThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.LockThread.aspx) ( [UnlockThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.UnlockThread.aspx) ) <br/> |
   

> **メモ**
> REST 例の  _domain\\\\user_ プレースホルダーの値は、実際のユーザーのアカウント名で置き換えてください。要求本文で REST パラメーターを渡す方法については、ソーシャル フィード REST API リファレンスの「 [例](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_exampleRequests)」を参照してください。 
  
    
    

SharePoint Server 2013 には、ミニブログの投稿のレイアウトまたはレンダリングを直接カスタマイズするための API はありません。SharePoint Server 2013 では、データだけが提供され、クロス プラットフォームおよびクロス デバイスのクライアント アプリケーションはフォーム ファクターおよびニーズに適したレイアウトを定義できます。SharePoint 2013 の開発では、「 [クライアント側レンダリングを使用して SharePoint アドインのリスト ビューをカスタマイズする](http://msdn.microsoft.com/library/8d5cabb2-70d0-46a0-bfe0-9e21f8d67d86%28Office.15%29.aspx)」で説明されているように、クライアント側レンダリングで JavaScript のオーバーライドを使用できます。
  
    
    

## 個人用サイト ソーシャル API のフィード タイプの概要
<a name="bkmk_FeedTypes"> </a>

フィード タイプはフィード データのスライスを表します。現在のユーザーのフィードを取得するとき、次のフィード タイプの 1 つを指定できます。
  
    
    

- **Personal**: ユーザーが作成した投稿や更新が格納されます。個人用サイトでは、このフィードがユーザーの [ **自己紹介**] ページに表示されます。
    
  
- **News**: 現在のユーザーや他のユーザーによって生成された投稿や更新情報、ユーザーがフォローしているコンテンツが格納されます。 **News** フィード タイプを取得する際には、 **ByModifiedTime** の並べ替え順序オプションを使用して、ユーザーがフォローしている他のユーザーの最新の (キャッシュされた) アクティビティを取得します。個人用サイトでは、このフィードがユーザーの [ **ニュースフィード**] ページに表示されます。
    
  
- **Timeline**: 現在のユーザーや人々によって作成された投稿や更新、またユーザーがフォローしているコンテンツが格納されます。 **Timeline** は特定の期間のフィードデータを取得したり、 **ByCreatedTime** オプション (人々の最大サンプリングを含む) で並べ替えるときに特に有用です。
    
  
- **Likes** には、現在のユーザーが [ **Like**] 属性のフラグを付けた投稿を表す **PostReference** プロパティのある参照スレッドが含まれます。
    
  
- **Everyone**: 現在のユーザーの組織全体から取得したスレッドを格納します。
    
  
サーバー オブジェクト モデル、クライアント オブジェクト モデル、JavaScript オブジェクト モデルは **GetFeed** メソッドを提供し、このメソッドを使用して現在のユーザーのフィード タイプを取得します。また **GetFeedFor** メソッドで指定したユーザー (だけ) の **Personal** フィード タイプを取得できます。両メソッドとも **SocialFeedOptions** オブジェクトをパラメーターにとり、時間に基づく並べ替え順序、期間、返却するスレッドの最大数を特定できます。
  
    
    

> **メモ**
> REST サービスは、表 2 で示されているような各フィード タイプを取得するための別のリソースを提供します。 
  
    
    

スレッドに 2 つ以上の返信がある場合、サーバーは最新の 2 つの返信だけが含まれたスレッドの要約を返します。(スレッドの要約には **IsDigest** スレッド属性が適用されています) スレッド内のすべての返信を取得する場合は、フィード マネージャー オブジェクトの **GetFullThread** メソッドを呼び出し、スレッド識別子を渡します。
  
    
    

## その他の技術情報
<a name="bkmk_AdditionalResources"> </a>


- **概念と方法に関する記事**
    
  
-  [SharePoint 2013 のソーシャルおよびコラボレーション機能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)
    
  
-  [[方法] SharePoint 2013 で JavaScript オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)
    
  
-  [[方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [[方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
    
  
-  [SharePoint Server 2013 で投稿にイメージ、ビデオ、ドキュメントを埋め込む方法](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md)
    
  
-  [SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  
- **API リファレンス文書**
    
  
-  [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) (クライアント オブジェクト モデル)
    
  
-  [SP.Social namespace](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) (JavaScript オブジェクト モデル)
    
  
-  [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) (サーバー オブジェクト モデル)
    
  
