---
title: SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス
ms.prod: SHAREPOINT
ms.assetid: c05755df-846d-4a39-941d-950d066cc6d4
---



# SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス
 **SocialRestFollowingManager** リソースと **PeopleManager** リソースを使用して、ユーザーやコンテンツのフォローの SharePoint REST エンドポイントを特定します。
SharePoint 2013 の Representational State Transfer (REST) サービスを使用すると, .NET クライアント オブジェクト モデルや JavaScript オブジェクト モデルを使用したときに実行できるタスクと同様のタスクを実行できます。REST サービスを使用するには、実行するタスクを表すリソース エンドポイントに対して HTTP の **GET** 要求と **POST** 要求を作成して送信します。これらのリソース エンドポイントは、SharePoint オブジェクト、プロパティ、およびメソッドに対応しています。
  
    
    

ほとんどのフォロー タスクのエンドポイント URI は、 **SocialRestFollowingManager** リソース ( `social.following`) で始まり、特定のタスクを実行するリソースで終わります。たとえば、現在のユーザーでユーザーやコンテンツのフォローを開始する場合は URI  `http://www.contoso.com/_api/social.following/follow` を使用し、現在のユーザーがフォローしているユーザーやコンテンツを取得する場合は URI `https://www.contoso.com/sites/devSite/_api/social.following/followed` を使用します。
> **メモ**
> この記事では、HTTP 要求のエンドポイント URI とパラメーター コンポーネントについて説明します。完全な要求の例については、 [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)を参照してください。 
  
    
    

ユーザーのフォローおよびコンテンツのフォローに関するタスクでは、 **SocialRestFollowingManager** API を使用することをお勧めしますが、 **SocialRestFollowingManager** でサポートされない一部のユーザーのフォロー タスクでは、 **PeopleManager** リソースを使用することができます。たとえば、誰かが現在のユーザーをフォローしているかどうかを確認したり、別のユーザーのフォロワーを取得したりすることができます。これらのタスクでは、HTTP の **GET** 要求を **PeopleManager** リソース ( `sp.userprofiles.peoplemanager`) で始まり、特定のタスクを実行するリソースで終わるエンドポイント URI に対して送信します。エンドポイントがパラメーターを取る場合、パラメーターのメタデータが URI、あるいは XML または JavaScript Object Notation (JSON) 形式の要求本文で送信されます。HTTP 要求は、JavaScript や C# をなどの任意の言語で実行できます。既定では、REST サービスは Atom プロトコルを使用して書式設定された応答を返しますが、HTTP **Accept** ヘッダーを使用して JSON 形式を要求することができます。「 [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)」を参照してください。
## ユーザーのフォローおよびコンテンツのフォロー タスクのリソース エンドポイント
<a name="bk_Overview"> </a>


||
|:-----|
| [Follow](#bk_Follow)           [StopFollowing](#bk_StopFollowing)           [IsFollowed](#bk_IsFollowed)           [My](#bk_My)           [My/FollowedDocumentsUri](#bk_MyFollowedDocumentsUri)           [My/FollowedSitesUri](#bk_MyFollowedSitesUri)           [My/Followed](#bk_Followed)           [My/FollowedCount](#bk_FollowedCount)           [My/Followers](#bk_Followers)           [My/Suggestions](#bk_Suggestions)           [GetMySuggestions](#bk_GetMySuggestions)           [IsMyPeopleListPublic](#bk_IsMyPeopleListPublic)           [AmIFollowedBy](#bk_AmIFollowedBy)           [GetPeopleFollowedBy](#bk_GetPeopleFollowedBy)           [GetFollowersFor](#bk_GetFollowersFor)|
   

## Follow
<a name="bk_Follow"> </a>

現在のユーザーにユーザー、ドキュメント、サイト、またはタグをフォローさせます。
  
    
    

### エンドポイント URI 構造

 **POST** `http://<siteCollection>/<site>/_api/social.following/follow`
  
    
    

### 要求パラメーター

 _actor_
  
    
    
型: **SP.Social.SocialActorInfo**
  
    
    
フォローを始めるアクター。
  
    
    
 **URI のユーザー  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=0,AccountName=@v,Id=null)?@v='domain\\user'
```

 **要求本文のユーザー  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":0,
  "AccountName":"domain\\\\user",
  "Id":null
}
```

クレームベースの ID モデルを使用している場合は、クエリ文字列で形式  `@v='i:0"%23".f|membership|user@domain.com'` を使用するか、要求本文で `"i:0#.f|membership|user@domain.com"` を使用して、アカウント名を渡すことができます。
  
    
    
 **URI のドキュメント  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=1,ContentUri=@v,Id=null)?@v='http://server/Shared%20Documents/fileName.docx'
```

 **要求本文のドキュメント  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":1,
  "ContentUri":"http://server/Shared%20Documents/fileName.docx",
  "Id":null
}
```

 **URI のサイト  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=2,ContentUri=@v,Id=null)?@v='http://server/site'
```

 **要求本文のサイト  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":2,
  "ContentUri":"http://siteCollection/site",
  "Id":null
}
```

 **URI のタグ  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/follow(ActorType=3,TagGuid='19a4a484-c1dc-4bc5-8c93-bb96245ce928',Id=null)
```

 **要求本文のタグ  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":3,
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928",
  "Id":null
}
```

タグをフォローするには、タグの GUID が必要です。REST サービスを使用して GUID を取得することはできませんが, .NET クライアント オブジェクト モデルや JavaScript オブジェクト モデルを使用することはできます。「 [JavaScript オブジェクト モデルを使用してタグの名前に基づいてタグの GUID を取得する方法](follow-content-in-sharepoint-2013.md#bk_getTagGuid)」を参照してください。
  
    
    

### 応答

 **Follow**
  
    
    
Type: **SP.Social.SocialFollowResult**
  
    
    
要求のステータス: 0 = OK、1 = AlreadyFollowing、2 = LimitReached、3 = InternalError
  
    
    
次の応答は、要求が成功したことを示します。
  
    
    



```

{"d":{"Follow":0}}
```


## StopFollowing
<a name="bk_StopFollowing"> </a>

現在のユーザーにユーザー、ドキュメント、サイト、またはタグのフォローをやめさせます。
  
    
    

### エンドポイント URI 構造

 **POST** `http://<siteCollection>/<site>/_api/social.following/stopfollowing`
  
    
    

### 要求パラメーター

 _actor_
  
    
    
型: **SP.Social.SocialActorInfo**
  
    
    
フォローをやめるアクター。
  
    
    
 **URI のユーザー  _actor_**
  
    
    



```
http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=0,AccountName=@v,Id=null)?@v='domain\\user'
```

 **要求本文のユーザー  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":0,
  "AccountName":"domain\\\\user",
  "Id":null
}
```

クレームベースの ID モデルを使用している場合は、クエリ文字列で形式  `@v='i:0"%23".f|membership|user@domain.com'` を使用するか、要求本文で `"i:0#.f|membership|user@domain.com"` を使用して、アカウント名を渡すことができます。
  
    
    
 **URI のドキュメント  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=1,ContentUri=@v,Id=null)?@v='http://server/Shared%20Documents/fileName.docx'
```

 **要求本文のドキュメント  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":1,
  "ContentUri":"http://server/Shared%20Documents/fileName.docx",
  "Id":null
}
```

 **URI のサイト  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=2,ContentUri=@v,Id=null)?@v='http://server/site'
```

 **要求本文のサイト  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":2,
  "ContentUri":"http://siteCollection/site",
  "Id":null
}
```

 **URI のタグ  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/stopfollowing(ActorType=3,TagGuid='19a4a484-c1dc-4bc5-8c93-bb96245ce928',Id=null)
```

 **要求本文のタグ  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":3,
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928",
  "Id":null
}
```

タグのフォローを開始するには、タグの GUID が必要です。REST サービスを使用して GUID を取得することはできませんが, .NET クライアント オブジェクト モデルや JavaScript オブジェクト モデルを使用することはできます。「 [JavaScript オブジェクト モデルを使用してタグの名前に基づいてタグの GUID を取得する方法](follow-content-in-sharepoint-2013.md#bk_getTagGuid)」を参照してください。
  
    
    

### 応答

なし。
  
    
    

```

{"d":{"StopFollowing":null}}
```


## IsFollowed
<a name="bk_IsFollowed"> </a>

現在のユーザーが指定したユーザー、ドキュメント、サイト、またはタグをフォローしているかどうかを示します。
  
    
    

### エンドポイント URI 構造

 **POST** `http://<siteCollection>/<site>/_api/social.following/isfollowed`
  
    
    

### 要求パラメーター

 _actor_
  
    
    
型: **SP.Social.SocialActorInfo**
  
    
    
フォロー状態を検出するアクター。
  
    
    
 **URI のユーザー  _actor_**
  
    
    



```
http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=0,AccountName=@v,Id=null)?@v='domain\\user'
```

 **要求本文のユーザー  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":0,
  "AccountName":"domain\\\\user",
  "Id":null
}
```

クレームベースの ID モデルを使用している場合は、クエリ文字列で形式  `@v='i:0"%23".f|membership|user@domain.com'` を使用するか、要求本文で `"i:0#.f|membership|user@domain.com"` を使用して、アカウント名を渡すことができます。
  
    
    
 **URI のドキュメント  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=1,ContentUri=@v,Id=null)?@v='https://domain.sharepoint.com/Shared%20Documents/fileName.docx'
```

 **要求本文のドキュメント  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":1,
  "ContentUri":"http://server/Shared%20Documents/fileName.docx",
  "Id":null
}
```

 **URI のサイト  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=2,ContentUri=@v,Id=null)?@v='http://domain.sharepoint.com'
```

 **要求本文のサイト  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":2,
  "ContentUri":"http://siteCollection/site",
  "Id":null
}
```

 **URI のタグ  _actor_**
  
    
    



```

http://<siteCollection>/<site>/_api/social.following/isfollowed(ActorType=3,TagGuid='19a4a484-c1dc-4bc5-8c93-bb96245ce928',Id=null)
```

 **要求本文のタグ  _actor_**
  
    
    



```
"actor":{
  "__metadata":{"type":"SP.Social.SocialActorInfo"},
  "ActorType":3,
  "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928",
  "Id":null
}
```

タグのフォローを開始するには、タグの GUID が必要です。REST サービスを使用して GUID を取得することはできませんが, .NET クライアント オブジェクト モデルや JavaScript オブジェクト モデルを使用することはできます。「 [JavaScript オブジェクト モデルを使用してタグの名前に基づいてタグの GUID を取得する方法](follow-content-in-sharepoint-2013.md#bk_getTagGuid)」を参照してください。
  
    
    

### 応答

 **IsFollowed**
  
    
    
型: **bool**
  
    
    
現在のユーザーがアクターをフォローしている場合は **true**、そうでない場合は **false**。
  
    
    
次の応答は、ユーザーが指定されたアクターをフォローしていないことを示します。
  
    
    



```

{"d":{"IsFollowed":false}}
```


## My
<a name="bk_My"> </a>

 **SocialRestFollowingManager** インスタンスに関する情報および現在のユーザーに関する情報を取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

型: **SP.Social.SocialRestFollowingManager**
  
    
    
 **SocialRestFollowingManager** インスタンスに関する情報、および現在のユーザーの **MyFollowedDocumentsUri**、 **MyFollowedSitesUri**、 **SocialActor** プロパティ。
  
    
    
次の応答は、現在のユーザーの **SocialRestFollowingManager** インスタンスを表します。
  
    
    



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

現在のユーザーの [ **フォロー中のドキュメント**] ページに対する URI を取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followeddocumentsuri`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

 **FollowedDocumentsUri**
  
    
    
型: **String**
  
    
    
現在のユーザーの [ **フォロー中のドキュメント**] ページに対する URI。
  
    
    
次の応答は、現在のユーザーの **FollowedDocumentsUri** を表します。
  
    
    



```

{"d":{"FollowedDocumentsUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/Social/FollowedContent.aspx"}}
```


## My/FollowedSitesUri
<a name="bk_MyFollowedSitesUri"> </a>

現在のユーザーの [ **フォロー中のサイト**] ページに対する URI を取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followedsitesuri`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

 **FollowedSitesUri**
  
    
    
型: **String**
  
    
    
現在のユーザーの [ **フォロー中のサイト**] ページに対する URI。
  
    
    
次の応答は、現在のユーザーの **FollowedSitesUri** を表します。
  
    
    



```
{"d":{"FollowedSitesUri":"https://somecompany-my.sharepoint.com/personal/someone_somecompany_onmicrosoft_com/Social/Sites.aspx"}}
```


## My/Followed
<a name="bk_Followed"> </a>

現在のユーザーがフォローしているユーザー、ドキュメント、サイト、およびタグを取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followed(types=15)`
  
    
    

### 要求パラメーター

 _types_
  
    
    
型: **Int32**
  
    
    
含めるアクターのタイプ。ユーザー = 1、ドキュメント = 2、サイト = 4、タグ = 8。ビット単位の組み合わせが可能。
  
    
    

### 応答

 **Followed**
  
    
    
型: **SP.Social.SocialActor** の配列
  
    
    
現在のユーザーがフォローしているユーザー、ドキュメント、サイト、およびタグ。
  
    
    
次の応答は、ドキュメント、サイト、およびタグを表します。要求内の  _types_ パラメーターでは、含めるアクターのタイプを指定します。
  
    
    



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

現在のユーザーがフォローしているユーザー、ドキュメント、サイト、およびタグの数を取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followedcount(types=15)`
  
    
    

### 要求パラメーター

 _types_
  
    
    
型: **Int32**
  
    
    
含めるアクターのタイプ。ユーザー = 1、ドキュメント = 2、サイト = 4、タグ = 8。ビット単位の組み合わせが可能。
  
    
    

### 応答

 **FollowedCount**
  
    
    
型: **Int32**
  
    
    
現在のユーザーがフォローしているユーザー、ドキュメント、サイト、およびタグの数。
  
    
    
次の応答は、現在のユーザーが指定されたタイプの 3 つのアクターをフォローしていることを示します。要求内の  _types_ パラメーターでは、含めるアクターのタイプを指定します。
  
    
    



```

{"d":{"FollowedCount":3}}
```


## My/Followers
<a name="bk_Followers"> </a>

現在のユーザーをフォローしているユーザーを取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/followers`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

 **Followers**
  
    
    
型: **SP.Social.SocialActor** の配列
  
    
    

  
    
    
次の応答は、現在のユーザーをフォローしている 1 人のユーザーを表します。
  
    
    



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

現在のユーザーがフォローする可能性のあるユーザーを取得します。
  
    
    

> **メモ**
> おすすめのユーザー機能は、ユーザーのフォロー状況、検索クロール、検索分析に依存します。 [SharePoint Online での、おすすめのユーザー機能の仕組み](follow-people-in-sharepoint-2013.md#bk_PeopleSuggestions)を参照してください。 
  
    
    


### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/social.following/my/suggestions`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

 **Suggestions**
  
    
    
型: **SP.Social.SocialActor** の配列
  
    
    
現在のユーザーがフォローする可能性のあるユーザー。
  
    
    

## GetMySuggestions
<a name="bk_GetMySuggestions"> </a>

現在のユーザーがフォローする可能性のあるユーザーを取得します。
  
    
    

> **メモ**
> おすすめのユーザー機能は、ユーザーのフォロー状況、検索クロール、検索分析に依存します。 [SharePoint Online での、おすすめのユーザー機能の仕組み](follow-people-in-sharepoint-2013.md#bk_PeopleSuggestions)を参照してください。 
  
    
    


### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getmysuggestions`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

 **Suggestions**
  
    
    
型: **SP.UserProfiles.PersonProperties** のリスト
  
    
    
現在のユーザーがフォローする可能性のあるユーザー。
  
    
    

## IsMyPeopleListPublic
<a name="bk_IsMyPeopleListPublic"> </a>

現在のユーザーの [ **フォローしている人々**] のリストが公開されているかどうかを確認します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/ismypeoplelistpublic`
  
    
    

### 要求パラメーター

なし。
  
    
    

### 応答

 **IsMyPeopleListPublic**
  
    
    
型: **bool**
  
    
    
現在のユーザーのフォローしている人々のリストが公開されている場合は **true**、それ以外の場合は **false**。
  
    
    
次の応答は、現在のユーザーのフォローしている人々のリスト公開されていることを示します。
  
    
    



```

{"d":{"IsMyPeopleListPublic":true}}
```


## AmIFollowedBy
<a name="bk_AmIFollowedBy"> </a>

指定したユーザーが現在のユーザーをフォローしているかどうかを確認します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/amifollowedby(accountName=@v)?@v='domain\\user'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/amifollowedby(accountName=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 要求パラメーター

 _accountName_
  
    
    
型: **String**
  
    
    
対象ユーザーのアカウント名。
  
    
    

### 応答

 **AmIFollowedBy**
  
    
    
型: **bool**
  
    
    
指定されたユーザーが現在のユーザーをフォローしている場合は **true**、そうでない場合は **false**。
  
    
    
次の応答は、指定されたユーザーが現在のユーザーをフォローしていないことを示します。
  
    
    



```
{"d":{"AmIFollowedBy":false}}
```


## GetPeopleFollowedBy
<a name="bk_GetPeopleFollowedBy"> </a>

指定したユーザーがフォローしているユーザーを取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getpeoplefollowedby(accountName=@v)?@v='domain\\user'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getpeoplefollowedby(accountName=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 要求パラメーター

 _accountName_
  
    
    
型: **String**
  
    
    
対象ユーザーのアカウント名。
  
    
    

### 応答

 **GetPeopleFollowedBy**
  
    
    
型: **SP.UserProfiles.PersonProperties** のリスト
  
    
    
指定したユーザーがフォローしているユーザー。
  
    
    
次の応答は、指定したユーザーがフォローしている 2 人のユーザーを表します。
  
    
    



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

指定したユーザーをフォローしているユーザーを取得します。
  
    
    

### エンドポイント URI 構造

 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getfollowersfor(accountName=@v)?@v='domain\\user'`
  
    
    
 **GET** `http://<siteCollection>/<site>/_api/sp.userprofiles.peoplemanager/getfollowersfor(accountName=@v)?@v='i:0"%23".f|membership|user@domain.com'`
  
    
    

### 要求パラメーター

 _accountName_
  
    
    
型: **String**
  
    
    
対象ユーザーのアカウント名。
  
    
    

### 応答

 **GetFollowersFor**
  
    
    
型: **SP.UserProfiles.PersonProperties** のリスト
  
    
    
指定したユーザーをフォローしているユーザー。
  
    
    
次の応答は、指定したユーザーをフォローしている 1 人のユーザーを表します。
  
    
    



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


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)
    
  
-  [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint ユーザー プロファイルの JavaScript 参照 (sp.userprofiles.js)](http://msdn.microsoft.com/library/80cf5436-6aa2-6f11-a782-66a04f6e2fb0%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
