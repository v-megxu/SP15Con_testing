---
title: SharePoint 2013 でのコンテンツのフォロー
ms.prod: SHAREPOINT
ms.assetid: 30e68cd6-6e55-4cf9-afd6-7139b0a97288
---



# SharePoint 2013 でのコンテンツのフォロー
SharePoint Server 2013 のコンテンツ (ドキュメント、サイト、タグ) をフォローするための一般的なプログラミング作業について説明します。
## SharePoint Server 2013 でのコンテンツ フォローの API
<a name="bkmk_APIversions"> </a>

ユーザーがドキュメント、サイト、またはタグをフォローすると、ドキュメントからの状態の更新、サイト上の会話、およびタグ使用の通知がニュースフィードに表示されます。コンテンツのフォローに関連する機能は、[ **ニュースフィード**] および [ **フォロー中**] コンテンツ ページに表示されます。
  
    
    
SharePoint Server 2013 では、プログラムによってコンテンツをフォローするのに使用できる、以下の API が提供されています。
  
    
    

- マネージ コード用のクライアント オブジェクト モデル
    
  - .NET クライアント オブジェクト モデル
    
  
  - Silverlight クライアント オブジェクト モデル
    
  
  - モバイル クライアント オブジェクト モデル
    
  
- JavaScript オブジェクト モデル
    
  
- REST (Representational State Transfer) サービス
    
  
- サーバー オブジェクト モデル
    
  
SharePoint 2013 開発のベスト プラクティスとして、できるかぎりクライアント API を使用してください。クライアント API には、クライアント オブジェクト モデル、JavaScript オブジェクトモデル、および REST サービスが含まれます。SharePoint 2013 の API の詳細と使用するタイミングについては、「 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)」を参照してください。
  
    
    
各 API には、コンテンツをフォローするためのコア タスク実行に使用するマネージャー オブジェクトが含まれています。
  
    
    

> **メモ**
> ユーザーのフォローにも同じ API を使用します。ユーザー フォロー タスクの概要については、「 [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)」を参照してください。 
  
    
    

表 1 に、各 API に含まれているマネージャー オブジェクトおよびその他の主要オブジェクト (または REST リソース) と API のクラス ライブラリ (またはアクセス ポイント) を示します。
  
    
    

> **メモ**
> Silverlight およびモバイル クライアント オブジェクト モデルは, .NET クライアント オブジェクト モデルと中核的な機能が同じであり、同じ署名を使用するので、表 1 や表 2 には示されていません。Silverlight クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll で定義され、モバイル クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Phone.dll で定義されています。 
  
    
    


**表 1. SharePoint 2013 コンテンツ フォローのプログラミングに使用する API**

|||
|:-----|:-----|
|.NET クライアント オブジェクト モデル  <br/> 「 [方法: SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)」を参照してください。  <br/> |マネージャー オブジェクト:           [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) <br/> プライマリ名前空間:            [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> その他の主要なオブジェクト:            [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 、 [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) 、 [SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) 、 [SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) <br/> クラス ライブラリ:          Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript オブジェクト モデル  <br/> |マネージャー オブジェクト:            [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> プライマリ名前空間:            [SP.Social](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) <br/> その他の主要なオブジェクト:            [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx)、 [SocialActorInfo](http://msdn.microsoft.com/library/d940db32-1561-c868-bb66-0612e2031f17%28Office.15%29.aspx)、 [SocialActorType](http://msdn.microsoft.com/library/fbde74da-f292-dc87-0b7e-81bc5b7a880c%28Office.15%29.aspx)、 [SocialActorTypes](http://msdn.microsoft.com/library/a460c3e6-ed88-117d-6755-4c5803a154a0%28Office.15%29.aspx) <br/> クラス ライブラリ:          SP.UserProfiles.js  <br/> |
|REST サービス  <br/> 「 [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)」を参照  <br/> |マネージャー リソース:            [social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> プライマリ名前空間 (OData):          **sp.social.SocialRestFollowingManager** <br/> その他の主要なリソース:           **SocialActor**、 **SocialActorInfo**、 **SocialActorType**、 **SocialActorTypes** <br/> アクセス ポイント:            `<siteUri>/_api/social.following` <br/> |
|サーバー オブジェクト モデル  <br/> |マネージャー オブジェクト:           [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.aspx) <br/> プライマリ名前空間:           [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> その他の主要なオブジェクト:            [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) 、 [SPSocialActorInfo](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorInfo.aspx) 、 [SPSocialActorType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorType.aspx) 、 [SPSocialActorTypes](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorTypes.aspx) <br/> クラス ライブラリ:          Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## SharePoint Server 2013でのコンテンツ フォローの一般的なプログラミング作業
<a name="bkmk_CommonTasks"> </a>

表 2 はコンテンツ フォローの一般的なプログラミング作業とそれらを実行するのに使用するメンバーを示します。メンバーは .NET クライアント オブジェクト モデル (CSOM)、JavaScript オブジェクト モデル (JSOM)、REST サービス、サーバー オブジェクト モデル (SSOM) です。
  
    
    

> **メモ**
> ユーザーのフォローにも同じ API を使用します。ユーザー フォロー タスクの概要については、「 [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)」を参照してください。 
  
    
    


**表 2. SharePoint Server 2013 のコンテンツ フォローの一般的なタスク用の API**


|**タスク**|**メンバー**|
|:-----|:-----|
|現在のユーザーのコンテキストでマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM:  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.#ctor.aspx) <br/> JSOM:  [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> REST:  `<siteUri>/_api/social.following` <br/> SSOM:  [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) <br/> |
|指定したユーザーのコンテキストでマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM: 実装されていません  <br/> JSOM: 実装されていません  <br/> REST: 実装されていません  <br/> SSOM:  [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) (オーバーロード) <br/> |
|現在のユーザーのアイテムのフォローを開始 (停止) する  <br/> |CSOM:  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) ) <br/> JSOM:  [follow](http://msdn.microsoft.com/library/40d14320-27ba-2941-b0e2-be3b5a407c89%28Office.15%29.aspx) ( [stopFollowing](http://msdn.microsoft.com/library/65b0e9be-dc5e-09fb-c57f-7a933de09a4c%28Office.15%29.aspx))  <br/> REST: **POST** [<siteUri>/_api/social.following/Follow](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Follow) ( [<siteUri>/_api/social.following/StopFollowing](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_StopFollowing))、          および要求本文で  _actor_ パラメーターを渡す <br/> SSOM:  [Follow](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.StopFollowing.aspx) ) <br/> |
|現在のユーザーが特定の項目をフォローしているかどうかを特定する  <br/> |CSOM:  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) <br/> JSOM:  [isFollowed](http://msdn.microsoft.com/library/2c1f62e6-fb75-ad4d-c081-36408b418c21%28Office.15%29.aspx) <br/> REST: **POST** [<siteUri>/_api/social.following/IsFollowed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_IsFollowed)、および要求本文で  _actor_ パラメーターを渡す <br/> SSOM:  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.IsFollowed.aspx) <br/> |
|現在のユーザーがフォローしているドキュメント、サイト、タグを取得する  <br/> |CSOM:  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) <br/> JSOM:  [getFollowed](http://msdn.microsoft.com/library/432a7cec-6add-fdb1-a79f-a93414ee8cd3%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.following/my/Followed(types=2)](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followed) (documents = **2**, sites = **4**, tags = **8**)  <br/> SSOM:  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowed.aspx) <br/> |
|ユーザーがフォローしているドキュメント、サイト、タグの数を取得する  <br/> |CSOM:  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) <br/> JSOM:  [getFollowedCount](http://msdn.microsoft.com/library/97b53b4f-481a-cf41-1854-8f3ff860b2bb%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.following/my/FollowedCount(types=2)](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_FollowedCount) (documents = **2**, sites = **4**, tags = **8**)  <br/> SSOM:  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowedCount.aspx) <br/> |
|現在のユーザーのフォロー ドキュメントを表示するサイトの URI を取得する  <br/> |CSOM:  [FollowedDocumentsUri](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.FollowedDocumentsUri.aspx) <br/> JSOM:  [followedDocumentsUri](http://msdn.microsoft.com/library/3a70b9c7-abd7-94ff-d730-70298673d6ec%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.following/my/FollowedDocumentsUri](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_MyFollowedDocumentsUri) <br/> SSOM:  [FollowedDocumentsUri](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.FollowedDocumentsUri.aspx) <br/> |
|現在のユーザーのフォロー サイトを表示する URI を取得する  <br/> |CSOM:  [FollowedSitesUri](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.FollowedSitesUri.aspx) <br/> JSOM:  [followedSitesUri](http://msdn.microsoft.com/library/829404bc-1b3a-7545-5e95-0922df330084%28Office.15%29.aspx) <br/> REST: **GET** [<siteUri>/_api/social.following/my/FollowedSitesUri](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_MyFollowedSitesUri) <br/> SSOM:  [FollowedSitesUri](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.FollowedSitesUri.aspx) <br/> |
   

> **メモ**
> REST サービスを使用したコンテンツ フォローの方法を示す例については、「 [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)」を参照してください。 
  
    
    


## JavaScript オブジェクト モデルを使用して、タグの名前に基づいてタグの GUID を取得する方法
<a name="bk_getTagGuid"> </a>

タグのフォローを開始または停止する、あるいは現在のユーザーがそのタグをフォローしているかどうかを確認するには、タグの GUID を使用する必要があります。次のコードに、タグ名に基づいて GUID を取得する方法を示します。
  
    
    
コードを実行する前に、 **sp.taxonomy.js** への参照を追加し、プレースホルダー タグの名前を既存のタグの名前に変更する必要があります。
  
    
    



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


## その他の技術情報
<a name="bk_addResources"> </a>


-  [方法: SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  
-  [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)
    
  
-  [SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のソーシャルおよびコラボレーション機能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)
    
  
