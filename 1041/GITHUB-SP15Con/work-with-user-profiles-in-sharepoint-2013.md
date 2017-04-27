---
title: SharePoint 2013 のユーザー プロファイルの操作
ms.prod: SHAREPOINT
ms.assetid: 7437a7a8-85cb-4233-84af-1eec30dd54b2
---



# SharePoint 2013 のユーザー プロファイルの操作
SharePoint Server 2013のユーザー プロファイルを操作するための一般的なプログラミング タスクについて説明します。
## SharePoint 2013のユーザー プロファイルを操作するための API
<a name="bkmk_APIversions"> </a>

ユーザー プロファイルおよびユーザー プロファイルのプロパティは、SharePoint ユーザーに関する情報を提供します。SharePoint Server 2013 には、ユーザー プロファイルをプログラムによって操作するための次のような API が用意されています。
  
    
    

- マネージ コード用のクライアント オブジェクト モデル
    
  - .NET クライアント オブジェクト モデル
    
  
  - Silverlight クライアント オブジェクト モデル
    
  
  - モバイル クライアント オブジェクト モデル
    
  
- JavaScript オブジェクト モデル
    
  
- REST (Representational State Transfer) サービス
    
  
- サーバー オブジェクト モデル
    
  
SharePoint 2013開発のベスト プラクティスとして、可能な限りクライアント API を使用してください。クライアント API には .NET クライアント オブジェクト モデル、JavaScript オブジェクト モデル、REST サービスが含まれています。SharePoint 2013の API およびその使用に関する詳細については、「 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)」を参照してください。
  
    
    

> **メモ**
> **Microsoft.Office.Server.UserProfiles** アセンブリで見つかった機能のすべてを、クライアント API から使用できるわけではありません。たとえば、(ユーザー プロファイル画像を除く) ユーザー プロファイルはクライアント API からは読み取り専用なので、ユーザー プロファイルを作成または変更するには、サーバー オブジェクト モデルを使用する必要があります。また、 [Microsoft.Office.Server.Audience](https://msdn.microsoft.com/library/Microsoft.Office.Server.Audience.aspx) 、 [Microsoft.Office.Server.ReputationModel](https://msdn.microsoft.com/library/Microsoft.Office.Server.ReputationModel.aspx) 、または [Microsoft.Office.Server.SocialData](https://msdn.microsoft.com/library/Microsoft.Office.Server.SocialData.aspx) など、一部の名前空間には、クライアント側からアクセスできません。クライアント API でサポートされている機能の詳細については、 [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) と [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) を参照してください。
  
    
    

API には基幹となるプロファイル関連タスクの実行に使用するマネージャー オブジェクトが含まれます。表 1 に、各 API に含まれているマネージャー オブジェクトおよびその他の主要オブジェクト (または REST リソース) と API のクラス ライブラリ (またはアクセス ポイント) を示します。
  
    
    

> **メモ**
> Silverlight およびモバイル クライアント オブジェクト モデルは, .NET クライアント オブジェクト モデルと中核的な機能が同じであり、同じ署名を使用するので、表 1 や表 2 には含まれていません。Silverlight クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll で定義され、モバイル クライアント オブジェクト モデルは、Microsoft.SharePoint.Client.UserProfiles.Phone.dll で定義されています。 
  
    
    


**表 1: ユーザー プロファイルをプログラムによって操作するための SharePoint 2013の API**

|||
|:-----|:-----|
|.NET クライアント オブジェクト モデル  <br/> 参照:  [[方法] SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |マネージャー オブジェクト:            [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.aspx) <br/> プライマリ名前空間:            [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) <br/> その他の主要なオブジェクト:            [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) 、 [ProfileLoader](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.aspx) 、 [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) <br/> クラス ライブラリ:           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript オブジェクト モデル  <br/> 参照先:  [SharePoint 2013 で JavaScript オブジェクトモデルを使用して、ユーザー プロファイル プロパティを取得する方法](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |マネージャー オブジェクト:            [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> プライマリ名前空間:            [SP.UserProfiles](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx) <br/> その他の主要なオブジェクト:            [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx)、 [ProfileLoader](http://msdn.microsoft.com/library/c8dd9919-66a9-fffc-1100-14472d2ec2cb%28Office.15%29.aspx)、 [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) <br/> クラス ライブラリ:           SP.UserProfiles.js  <br/> |
|REST サービス  <br/> 参照:  [ユーザー プロファイル REST API リファレンス](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx) <br/> |マネージャー リソース:            [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> エンドポイント URI:            `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> プライマリ名前空間:           **SP.UserProfiles** <br/> その他の主要なリソース:            [PersonProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PersonProperties)、 [ProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoader)、 [UserProfile](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfile) <br/> |
|サーバー オブジェクト モデル  <br/> 参照:  [[方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |マネージャー オブジェクト:            [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.aspx) 、 [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) <br/> プライマリ名前空間:            [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx) <br/> その他の主要なオブジェクト:            [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) 、 [CorePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CorePropertyManager.aspx) 、 [ProfilePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfilePropertyManager.aspx) 、 [ProfileSubtypeManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeManager.aspx) 、 [ProfileSubtypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypePropertyManager.aspx) 、 [ProfileTypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypePropertyManager.aspx) <br/> クラス ライブラリ:           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## SharePoint 2013のユーザー プロファイルを操作するための一般的なプログラミング タスク
<a name="bkmk_CommonTasks"> </a>

表 2 に、ユーザー プロファイルを操作するための一般的なプログラミング タスクとそのタスクの実行に使用するメンバーを示します。メンバーは, .NET クライアント オブジェクト モデル (CSOM)、JavaScript オブジェクト モデル (JSOM)、REST サービス、およびサーバー オブジェクト モデル (SSOM) に由来します。
  
    
    

**表 2: ユーザー プロファイルを操作するための一般的なプログラミング タスク用 API**


|**タスク**|**メンバー**|
|:-----|:-----|
|現在のユーザーのコンテキストでマネージャー オブジェクトのインスタンスを作成する  <br/> |CSOM:  [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.#ctor.aspx) <br/> JSOM:  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> REST:  [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> SSOM:  [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.#ctor.aspx) (オーバーロード) または [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.#ctor.aspx) <br/> |
|現在のユーザーのプロファイル画像を変更する  <br/> |CSOM:  [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> JSOM:  [setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) <br/> REST:  [SetMyProfilePicture](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerSetMyProfilePicture)          **POST** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/SetMyProfilePicture` そして要求本文の _picture_ パラメータを渡します <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) [PropertyConstants.PictureUrl].Value or [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> |
|現在のユーザーのプロパティを取得する  <br/> |CSOM:  [GetMyProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMyProperties.aspx) <br/> JSOM:  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) <br/> REST:  [GetMyProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetMyProperties)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetMyProperties`          (または、 `/_api/social.feed/my` または `/_api/social.following/my` からいくつかの基本的なユーザー プロパティを取得する) <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) <br/> |
|特定のユーザーのプロパティを取得する  <br/> |CSOM:  [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> JSOM:  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) <br/> REST:  [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPropertiesFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (オーバーロード) または [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> |
|特定ユーザーのユーザー プロファイル プロパティを取得する  <br/> |CSOM:  [GetUserProfilePropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertiesFor.aspx) <br/> JSOM:  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) <br/> REST: 実装されていません           [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor) を呼び出し、返された **PersonProperties** オブジェクトの **UserProfileProperties** プロパティからユーザー プロファイルのプロパティを取得します。 <br/> SSOM:  [GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.GetEnumerator.aspx) <br/> |
|ユーザーの特定のユーザー プロファイル プロパティを取得する  <br/> |CSOM:  [GetUserProfilePropertyFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertyFor.aspx) <br/> JSOM:  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) <br/> REST:  [GetUserProfilePropertyFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetUserProfilePropertyFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetUserProfilePropertyFor(accountName=@v,propertyName='PreferredName')?@v='domain\\\\user'` <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) (オーバーロード)、およびインデクサーでプロパティ名を指定する <br/> |
|ユーザー プロファイルを取得する  <br/> |CSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.GetUserProfile.aspx) (現在のユーザーのみの [クライアント側のユーザー プロファイル](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)を返します)  <br/> JSOM:  [getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) (現在のユーザーのみの [クライアント側のユーザー プロファイル](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)を返します)  <br/> REST:  [GetProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderGetProfileLoader)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile` (現在のユーザーのみの [クライアント側のユーザー プロファイル](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)を返します)  <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (オーバーロード) <br/> |
|ユーザー アカウントが存在するかどうかを確認する  <br/> |CSOM: 実装されていません  <br/> JSOM: 実装されていません  <br/> REST: 実装されていません  <br/> SSOM:  [UserExists](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.UserExists.aspx) <br/> |
|ユーザー プロファイルおよびユーザー プロファイルのプロパティと属性を作成または変更する  <br/> (クライアント API によりプロファイル画像を変更可能。この表の「現在のユーザーのプロファイル画像を変更する」タスクを参照)  <br/> |CSOM: 実装されていません  <br/> JSOM: 実装されていません  <br/> REST: 実装されていません  <br/> SSOM: 複数。「 [[方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)」を参照してください。  <br/> |
|ユーザー プロファイルを削除する  <br/> |CSOM: 実装されていません  <br/> JSOM: 実装されていません  <br/> REST: 実装されていません  <br/> SSOM:  [RemoveProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveProfile.aspx) または [RemoveUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveUserProfile.aspx) (オーバーロード) <br/> |
|ユーザーの個人サイトをプロビジョニングする  <br/> |CSOM:  [CreatePersonalSiteEnque](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.CreatePersonalSiteEnque.aspx) (オーバーロード) <br/> JSOM:  [createPersonalSiteEnque](http://msdn.microsoft.com/library/f4bcb82d-4048-0b29-9bc6-ce70ead49988%28Office.15%29.aspx) (オーバーロード) <br/> REST:  [CreatePersonalSiteEnque](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfileCreatePersonalSiteEnque)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile/CreatePersonalSiteEnqueue` <br/> SSOM:  [CreatePersonalSite()](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.CreatePersonalSite.aspx) (オーバーロード) <br/> |
|1 人以上のユーザーの個人サイトをプロビジョニングする  <br/> SharePoint Online の 個人用サイト ホスト管理者のみ利用可能  <br/> |CSOM:  [CreatePersonalSiteEnqueueBulk](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bk_CreatePersonalSiteEnqueueBulk) <br/> JSOM: **createPersonalSiteEnqueueBulk** <br/> REST:  [CreatePersonalSiteEnqueueBulk](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderCreatePersonalSiteEnqueueBulk)          **POST** `https://<domain>-admin.sharepoint.com/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/CreatePersonalSiteEnqueueBulk` および _emailIDs_ パラメーターのメールアドレスの文字列配列 (最大 200 文字) を要求の本文で渡します (例: `{'emailIDs':['usera@contoso.onmicrosoft.com','userb@contoso.onmicrosoft.com']}`)。  <br/> SSOM: **CreatePersonalSiteEnqueueBulk** <br/> |
   

## SharePoint 2013のユーザーおよびユーザー プロパティ向けの新しいオブジェクト
<a name="bkmk_NewUserObjects"> </a>

SharePoint Server 2013には、ユーザーおよびユーザー プロパティを表す次の新しいオブジェクトが含まれています。
  
    
    

-  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) オブジェクトと [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) オブジェクトは、フィードおよびフォロー アクティビティのユーザー (およびドキュメント、サイト、タスク) を表します。
    
  
- 新しいクライアント側の  [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) オブジェクト。このオブジェクトは、現在のユーザーの個人サイトを作成するために使用することができるメソッドを提供します。しかし、サーバー側の [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) オブジェクトに含まれるすべてのユーザー プロパティはこのオブジェクトに含まれません。
    
  
-  [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) オブジェクトには一般的なユーザー プロパティが含まれ、その [UserProfileProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.UserProfileProperties.aspx) プロパティにはユーザー プロファイル プロパティが含まれます。 [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) はクライアント側コードからユーザー プロパティにアクセスするためのプライマリ API です。
    
  

> **メモ**
> サーバー オブジェクト モデル バージョンは  [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) オブジェクトおよび [PersonProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PersonProperties.aspx) オブジェクトです。
  
    
    


## その他の技術情報
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 のソーシャルおよびコラボレーション機能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのソーシャル機能の開発の概要](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [SharePoint 2013 で JavaScript オブジェクトモデルを使用して、ユーザー プロファイル プロパティを取得する方法](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [ユーザー プロファイル REST API リファレンス](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [[方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)
    
  
