---
title: SharePoint 2013 で他のユーザーをフォローする
ms.prod: SHAREPOINT
ms.assetid: 0fa2e235-63d0-41b1-9eed-4aeb2f59a14d
---



# SharePoint 2013 で他のユーザーをフォローする
SharePoint Server 2013 で人々をフォローするための一般的なプログラミング タスクについて説明します。
## SharePoint Server 2013 で人々をフォローするための API
<a name="bkmk_APIversions"> </a>

SharePoint Server 2013 でユーザーをフォローすると、ユーザーが発行したマイクロブログの投稿、およびアクティビティについての通知がニュースフィードに表示されます。ユーザーのフォローに関連する機能は、[ **ニュースフィード**] および [ **フォロー相手**] のページに表示されます。
  
    
    
SharePoint Server 2013 では、プログラムによって人々をフォローするのに使用できる、以下の API が提供されています。
  
    
    

- マネージ コード用のクライアント オブジェクト モデル
    
  - クライアント オブジェクト モデル
    
  
  - Silverlight クライアント オブジェクト モデル
    
  
  - モバイル クライアント オブジェクト モデル
    
  
- JavaScript オブジェクト モデル
    
  
- REST (Representational State Transfer) サービス
    
  
- サーバー オブジェクト モデル
    
  
SharePoint 2013 開発のベスト プラクティスとして、可能な場合はクライアント API を使用します。クライアント API には、クライアント オブジェクト モデル、JavaScript オブジェクト モデル、および REST サービスが含まれます。SharePoint 2013 の API の詳細と使用するタイミングについては、「 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)」を参照してください。
  
    
    
各 API には、ユーザーをフォローするコア タスクを実行する際に使用するマネージャー オブジェクトが含まれています。
  
    
    

> **メモ**
> 同じ API を使用してコンテンツをフォローします。コンテンツのフォロー タスクの概要については、「 [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)」をご覧ください。 
  
    
    

表 1 に、API のマネージャー オブジェクトとその他のキー オブジェクト (または REST リソース)、および、それらがあるクラス ライブラリ (またはアクセス ポイント) を示します。
  
    
    

> **メモ**
> Silverlight およびモバイル クライアント オブジェクト モデルは, .NET クライアント オブジェクト モデルと中核的な機能が同じであり、同じ署名を使用するので、表 1 や表 2 には明示されていません。Silverlight クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll で定義され、モバイル クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Phone.dll で定義されています。 
  
    
    


**表 1. 人々をプログラムによってフォローするために使用するSharePoint 2013 API**

|||
|:-----|:-----|
|.NET クライアント オブジェクト モデル  <br/> 「 [方法: SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)」を参照  <br/> |マネージャー オブジェクト:            [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) プライマリ名前空間: <br/> プライマリ名前空間::            [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> その他の主要なオブジェクト:            [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 、 [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) 、 [SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) 、 [SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) <br/> クラス ライブラリ:           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript オブジェクト モデル  <br/> 以下をご覧ください:  [SharePoint 2013 で JavaScript オブジェクト モデルを使用してユーザーをフォローする方法](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md) <br/> |マネージャー オブジェクト:            [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> プライマリ名前空間:           **SP.Social** <br/> その他の主要なオブジェクト:            [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx)、 [SocialActorInfo](http://msdn.microsoft.com/library/d940db32-1561-c868-bb66-0612e2031f17%28Office.15%29.aspx)、 [SocialActorType](http://msdn.microsoft.com/library/fbde74da-f292-dc87-0b7e-81bc5b7a880c%28Office.15%29.aspx)、 [SocialActorTypes](http://msdn.microsoft.com/library/a460c3e6-ed88-117d-6755-4c5803a154a0%28Office.15%29.aspx) <br/> クラス ライブラリ:           SP.UserProfiles.js  <br/> |
|REST サービス  <br/> 参照:  [SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> |マネージャー リソース:            [social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> エンドポイント URI:            `<siteUri>/_api/social.following` <br/> プライマリ名前空間 (OData):           **sp.social.SocialRestFollowingManager** <br/> その他の主要なリソース:           **SocialActor**、 **SocialActorInfo**、 **SocialActorType**、 **SocialActorTypes** <br/> |
|サーバー オブジェクト モデル  <br/> |マネージャー オブジェクト:            [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.aspx) <br/> プライマリ名前空間:            [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> その他の主要なオブジェクト:            [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) 、 [SPSocialActorInfo](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorInfo.aspx) 、 [SPSocialActorType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorType.aspx) 、 [SPSocialActorTypes](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorTypes.aspx) <br/> クラス ライブラリ:           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## SharePoint Server 2013 で人々をフォローするための一般的なプログラミング タスク
<a name="bkmk_CommonTasks"> </a>

表 2 は、人々をフォローするための一般的なプログラミング タスクとそれらを実行するのに使用するメンバーを示します。メンバーは .NET クライアント オブジェクト モデル (CSOM)、JavaScript オブジェクト モデル (JSOM)、REST サービス、サーバー オブジェクト モデル (SSOM) です。
  
    
    

> **メモ**
> 同じ API を使用してコンテンツをフォローします。コンテンツのフォロー タスクの概要については、「 [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)」をご覧ください。 
  
    
    

The **SocialFollowingManager** オブジェクトは、現在のユーザー向けに人々のフォローおよびコンテンツのフォローのコア機能を統合します。ただし、 **PeopleManager** オブジェクト (表 3 を参照) は、 **SocialFollowingManager** が提供しないいくつかの機能を提供します。この機能には、他のユーザーによる人々のフォローのステータスを取得する方法が含まれます。
  
    
    

**表 2. SocialFollowingManager オブジェクトを使用して人々をフォローするための一般的なタスクの API**


|**タスク**|**メンバー**|
|:-----|:-----|
|現在のユーザーのコンテキストでマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM:  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.#ctor.aspx) <br/> JSOM: **SocialFollowingManager** <br/> REST:  `<siteUri>/_api/social.following` <br/> SSOM:  [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) <br/> |
|特定のユーザーのコンテキストでマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM: 実装されていません  <br/> JSOM: 実装されていません  <br/> REST: 実装されていません  <br/> SSOM:  [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) (オーバーロードされている) <br/> |
|現在のユーザーが誰かのフォローを開始 (停止) するようにする  <br/> |CSOM:  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) ) <br/> JSOM:  [フォロー](http://msdn.microsoft.com/library/40d14320-27ba-2941-b0e2-be3b5a407c89%28Office.15%29.aspx) ( [stopFollowing](http://msdn.microsoft.com/library/65b0e9be-dc5e-09fb-c57f-7a933de09a4c%28Office.15%29.aspx))  <br/> REST:  [Follow](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Follow) ( [StopFollowing](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_StopFollowing))          **POST** `<siteUri>/_api/social.following/Follow` ( `<siteUri>/_api/social.following/StopFollowing`)、および要求本文に入れて  _actor_ パラメーターを引き渡す <br/> SSOM:  [Follow](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.StopFollowing.aspx) ) <br/> |
|現在のユーザーが特定のユーザーをフォローしているかどうかを特定する  <br/> |CSOM:  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) <br/> JSOM:  [isFollowed](http://msdn.microsoft.com/library/2c1f62e6-fb75-ad4d-c081-36408b418c21%28Office.15%29.aspx) <br/> REST:  [IsFollowed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_IsFollowed)          **POST** `<siteUri>/_api/social.following/my/IsFollowed`、および要求本文に入れて  _actor_ パラメーターを引き渡す <br/> SSOM:  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.IsFollowed.aspx) <br/> |
|現在のユーザーをフォローしている人々を取得する  <br/> |CSOM:  [GetFollowers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowers.aspx) <br/> JSOM:  [getFollowers](http://msdn.microsoft.com/library/ae4a944b-c043-05fb-c74b-101d2ce4a813%28Office.15%29.aspx) <br/> REST:  [Followers](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followers)          **GET** `<siteUri>/_api/social.following/my/Followers` <br/> SSOM:  [GetFollowers](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowers.aspx) <br/> |
|現在のユーザーがフォローしている人々を取得する  <br/> |CSOM:  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) <br/> JSOM:  [getFollowed](http://msdn.microsoft.com/library/432a7cec-6add-fdb1-a79f-a93414ee8cd3%28Office.15%29.aspx) <br/> REST:  [Followed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followed)          **GET** `<siteUri>/_api/social.following/my/Followed(types=1)` <br/> SSOM:  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowed.aspx) <br/> |
|現在のユーザーがフォローしている人々の数を取得する  <br/> |CSOM:  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) <br/> JSOM:  [getFollowedCount](http://msdn.microsoft.com/library/97b53b4f-481a-cf41-1854-8f3ff860b2bb%28Office.15%29.aspx) <br/> REST:  [FollowedCount](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_FollowedCount)          **GET** `<siteUri>/_api/social.following/my/FollowedCount(types=1)` <br/> SSOM:  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowedCount.aspx) <br/> |
|現在のユーザーがフォローする可能性のある人々を取得する  <br/> |CSOM:  [GetSuggestions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetSuggestions.aspx) <br/> JSOM:  [getSuggestions](http://msdn.microsoft.com/library/95fd9c48-6974-ec08-d3e9-00c2c76f4f79%28Office.15%29.aspx) <br/> REST:  [Suggestions](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Suggestions)          **GET** `<siteUri>/_api/social.following/my/Suggestions` <br/> SSOM:  [GetSuggestions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetSuggestions.aspx) <br/> |
   
表 3 は、ユーザーをフォローするために使用できる **PeopleManager** メンバーの機能を示します。
  
    
    

**PeopleManager オブジェクトを使用して人々をフォローするための一般的なタスクの API**


|**Task**|**Members**|
|:-----|:-----|
|**フォローしている人々**のリストが公開されているかどうかを確認する  <br/> |CSOM:  [IsMyPeopleListPublic](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.IsMyPeopleListPublic.aspx) <br/> JSOM:  [isMyPeopleListPublic](http://msdn.microsoft.com/library/2ffc73a5-24ce-1ed4-d850-a6fea4c773bb%28Office.15%29.aspx) <br/> REST:  [IsMyPeopleListPublic](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerProperties)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/IsMyPeopleListPublic` <br/> SSOM:  [IsMyPeopleListPublic](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.IsMyPeopleListPublic.aspx) <br/> |
|誰かが現在のユーザーをフォローしているかどうかを確認する  <br/> |CSOM:  [AmIFollowedBy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.AmIFollowedBy.aspx) <br/> JSOM:  [amIFollowedBy](http://msdn.microsoft.com/library/3641c469-0063-054d-355d-e56697cb08ae%28Office.15%29.aspx) <br/> REST:  [AmIFollowedBy](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerAmIFollowedBy)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/AmIFollowedBy(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [AmIFollowedBy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.AmIFollowedBy.aspx) <br/> |
|特定のユーザーがフォローしている人々を取得する  <br/> |CSOM:  [GetPeopleFollowedBy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPeopleFollowedBy.aspx) <br/> JSOM:  [getPeopleFollowedBy](http://msdn.microsoft.com/library/e781c0fa-b14a-40ef-976b-b1c6c82beb89%28Office.15%29.aspx) <br/> REST:  [GetPeopleFollowedBy](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPeopleFollowedBy)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPeopleFollowedBy(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetPeopleFollowedBy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPeopleFollowedBy.aspx) <br/> |
|特定のユーザーをフォローしている人々を取得する  <br/> |CSOM:  [GetFollowersFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetFollowersFor.aspx) <br/> JSOM:  [getFollowersFor](http://msdn.microsoft.com/library/51ef3b75-42b2-4efb-4441-e088dc7d168e%28Office.15%29.aspx) <br/> REST:  [GetFollowersFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetFollowersFor)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/GetFollowersFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetFollowersFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetFollowersFor.aspx) <br/> |
|特定のユーザーが別のユーザーをフォローしているかどうかを確認する  <br/> |CSOM:  [IsFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.IsFollowing.aspx) <br/> JSOM:  [isFollowing](http://msdn.microsoft.com/library/6a5ce6cb-c710-9e19-0cb9-7fae9e013ec8%28Office.15%29.aspx) <br/> REST:  [IsFollowing](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerIsFollowing) (静的)          **GET** `<siteUri>/_api/SP_UserProfiles_PeopleManager_IsFollowing(possibleFollowerAccountName=@v,possibleFolloweeAccountName=@y)?@v='domain\\\\user'&amp;@y='domain\\\\user'` <br/> SSOM:  [IsFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.IsFollowing.aspx) <br/> |
   

## SharePoint Online での、おすすめのユーザー機能の仕組み
<a name="bk_PeopleSuggestions"> </a>

おすすめのユーザー機能の結果は、確立されたユーザー フォローのアクティビティに基づいています。ユーザーがまだフォローしていないユーザーと相互にフォローしている別のユーザーをフォローする場合に提案されます。
  
    
    
検索クロールの間、フォローに関連する情報にインデックスが設定されます。クロールの終了後、検索分析によりクロールされたフォロー情報を分析し、ユーザーへの提案を出力する必要があります。既定により、検索分析は 1 日に 1 回実行されます。
  
    
    
ユーザーが [ **フォロー相手**] ページを開くと、 [PeopleManager.GetMySuggestions()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMySuggestions.aspx) メソッドが呼び出されます。 [GetMySuggestions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMySuggestions.aspx) 現在のユーザーに対する新しい提案を検索し、データベース中でユーザーの提案を更新し、ページに提案を表示します。
  
    
    

## その他の技術情報
<a name="bk_addResources"> </a>


-  [SharePoint 2013 のソーシャルおよびコラボレーション機能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)
    
  
-  [ユーザー プロファイル REST API リファレンス](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [方法: SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 で JavaScript オブジェクト モデルを使用してユーザーをフォローする方法](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
