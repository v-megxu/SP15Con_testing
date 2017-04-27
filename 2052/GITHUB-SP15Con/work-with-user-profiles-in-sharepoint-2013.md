---
title: 在 SharePoint 2013 中使用用户配置文件
ms.prod: SHAREPOINT
ms.assetid: 7437a7a8-85cb-4233-84af-1eec30dd54b2
---



# 在 SharePoint 2013 中使用用户配置文件
了解用于使用 SharePoint Server 2013 中的用户配置文件的常见编程任务。
## 用于使用 SharePoint 2013 中的用户配置文件的 API
<a name="bkmk_APIversions"> </a>

用户配置文件和用户配置文件属性提供有关 SharePoint 用户的信息。SharePoint Server 2013 提供以下可用于以编程方式使用用户配置文件的 API：
  
    
    

- 托管代码的客户端对象模型
    
  - .NET 客户端对象模型
    
  
  - Silverlight 客户端对象模型
    
  
  - 移动设备客户端对象模型
    
  
- JavaScript 对象模型
    
  
- 代表性状态传输 (REST) 服务
    
  
- 服务器对象模型
    
  
如果可以，最好在 SharePoint 2013 开发中使用客户端 API。客户端 API 包括 .NET 客户端对象模型、JavaScript 对象模型和 REST 服务。有关 SharePoint 2013 中的 API 以及何时使用它们的详细信息，请参阅 [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    

> **注释**
> 在 **Microsoft.Office.Server.UserProfiles** 程序集中找到的所有功能并非都能供客户端 API 使用。例如，您必须使用服务器对象模型创建或更改用户配置文件，因为从客户端 API 看来，它们为只读文件（用户配置文件图片除外）。此外，客户端无法访问某些命名空间，例如 [Microsoft.Office.Server.Audience](https://msdn.microsoft.com/library/Microsoft.Office.Server.Audience.aspx) 、 [Microsoft.Office.Server.ReputationModel](https://msdn.microsoft.com/library/Microsoft.Office.Server.ReputationModel.aspx) 或 [Microsoft.Office.Server.SocialData](https://msdn.microsoft.com/library/Microsoft.Office.Server.SocialData.aspx) 。若要查看客户端 API 支持的功能，请参阅 [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) 和 [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) 。
  
    
    

每个 API 都包括一个用于执行配置文件相关的核心任务的管理器对象。表 1 显示了每个 API 中的管理器和其他关键对象（或 REST 资源）以及可在其中找到 API 的类库（或访问点）。
  
    
    

> **注释**
> Silverlight 和移动客户端对象模型未包括在表 1 或表 2 中，因为它们提供与 .NET 客户端对象模型相同的核心功能并且使用相同的签名。Silverlight 客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll 中定义，移动客户端对象模型在 Microsoft.SharePoint.Client.UserProfiles.Phone.dll 中定义。 
  
    
    


**表 1. 用于以编程方式使用用户配置文件的 SharePoint 2013 API**

|||
|:-----|:-----|
|.NET 客户端对象模型  <br/> 请参阅： [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |管理器对象：           [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.aspx) <br/> 主命名空间：           [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) <br/> 其他关键对象：           [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) 、 [ProfileLoader](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.aspx) 、 [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) <br/> 类库：          Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript 对象模型  <br/> 请参阅： [如何：在 SharePoint 2013 中使用 JavaScript 对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |管理器对象：           [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> 主命名空间：           [SP.UserProfiles](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx) <br/> 其他关键对象：           [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx)、 [ProfileLoader](http://msdn.microsoft.com/library/c8dd9919-66a9-fffc-1100-14472d2ec2cb%28Office.15%29.aspx)、 [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) <br/> 类库：          SP.UserProfiles.js  <br/> |
|REST 服务  <br/> 请参阅： [用户配置文件 REST API 引用](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx) <br/> |管理器资源：           [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> 终结点 URI：           `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> 主命名空间：          **SP.UserProfiles** <br/> 其他关键资源：           [PersonProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PersonProperties)、 [ProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoader)、 [UserProfile](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfile) <br/> |
|服务器对象模型  <br/> 请参阅： [如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |管理器对象：           [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.aspx) 、 [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) <br/> 主命名空间：           [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx) <br/> 其他关键对象：           [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) 、 [CorePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CorePropertyManager.aspx) 、 [ProfilePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfilePropertyManager.aspx) 、 [ProfileSubtypeManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeManager.aspx) 、 [ProfileSubtypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypePropertyManager.aspx) 、 [ProfileTypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypePropertyManager.aspx) <br/> 类库：          Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## 用于使用 SharePoint 2013 中的用户配置文件
<a name="bkmk_CommonTasks"> </a>

表 2 显示用于使用用户配置文件的常见编程任务和用于执行这些任务的成员。这些成员来自 .NET 客户端对象模型 (CSOM)、JavaScript 对象模型 (JSOM)、REST 服务和服务器对象模型 (SSOM)。
  
    
    

**表 2. 用于使用用户配置文件的常见编程任务的 API**


|**任务**|**成员**|
|:-----|:-----|
|在当前用户的上下文中创建管理器对象实例  <br/> |CSOM： [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.#ctor.aspx) <br/> JSOM： [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> REST： [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> SSOM： [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.#ctor.aspx) （重载）或 [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.#ctor.aspx) <br/> |
|更改当前用户的配置文件图片。  <br/> |CSOM： [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> JSOM： [setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) <br/> REST： [SetMyProfilePicture](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerSetMyProfilePicture)          **POST** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/SetMyProfilePicture`并在请求正文中传递  _picture_ 参数 <br/> SSOM： [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) [PropertyConstants.PictureUrl].Value 或 [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> |
|获取当前用户的属性  <br/> |CSOM： [GetMyProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMyProperties.aspx) <br/> JSOM： [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) <br/> REST： [GetMyProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetMyProperties)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetMyProperties`          （或从  `/_api/social.feed/my` 或 `/_api/social.following/my` 获取一些基本用户属性） <br/> SSOM： [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) <br/> |
|获取特定用户的属性  <br/> |CSOM： [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> JSOM： [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) <br/> REST： [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPropertiesFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM： [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) （重载）或 [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> |
|获取特定用户的用户配置文件属性  <br/> |CSOM： [GetUserProfilePropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertiesFor.aspx) <br/> JSOM： [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) <br/> REST：未实现          调用  [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)，然后从返回的 **PersonProperties** 对象的 **UserProfileProperties** 属性获取用户配置文件属性。 <br/> SSOM： [GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.GetEnumerator.aspx) <br/> |
|获取用户的特定用户配置文件属性  <br/> |CSOM： [GetUserProfilePropertyFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertyFor.aspx) <br/> JSOM： [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) <br/> REST： [GetUserProfilePropertyFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetUserProfilePropertyFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetUserProfilePropertyFor(accountName=@v,propertyName='PreferredName')?@v='domain\\\\user'` <br/> SSOM： [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) （重载）并在索引器中指定属性名称 <br/> |
|获取用户配置文件  <br/> |CSOM： [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.GetUserProfile.aspx) （仅为当前用户返回 [客户端用户配置文件](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)）  <br/> JSOM： [getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx)（仅为当前用户返回 [客户端用户配置文件](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)）  <br/> REST： [GetProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderGetProfileLoader)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile`（仅为当前用户返回 [客户端用户配置文件](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)）  <br/> SSOM： [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) （重载） <br/> |
|了解用户帐户是否存在  <br/> |CSOM：未实现  <br/> JSOM：未实现  <br/> REST：未实现  <br/> SSOM： [UserExists](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.UserExists.aspx) <br/> |
|创建或更改用户配置文件以及用户配置文件属性 (Property) 和属性 (Attribute)  <br/> （客户端 API 可更改配置文件图片。请参阅此表中的"更改用户的配置文件图片"任务）。  <br/> |CSOM：未实现  <br/> JSOM：未实现  <br/> REST：未实现  <br/> SSOM：多重 - 请参阅 [如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |
|删除用户配置文件  <br/> |CSOM：未实现  <br/> JSOM：未实现  <br/> REST：未实现  <br/> SSOM： [RemoveProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveProfile.aspx) 或 [RemoveUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveUserProfile.aspx) （重载） <br/> |
|配置用户的个人网站  <br/> |CSOM： [CreatePersonalSiteEnque](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.CreatePersonalSiteEnque.aspx) （重载） <br/> JSOM： [createPersonalSiteEnque](http://msdn.microsoft.com/library/f4bcb82d-4048-0b29-9bc6-ce70ead49988%28Office.15%29.aspx)（重载）  <br/> REST： [CreatePersonalSiteEnque](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfileCreatePersonalSiteEnque)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile/CreatePersonalSiteEnqueue` <br/> SSOM： [CreatePersonalSite()](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.CreatePersonalSite.aspx) （重载） <br/> |
|配置一个或多个用户的个人网站  <br/> 仅在 SharePoint Online 上可用于 我的网站 主机管理员  <br/> |CSOM： [CreatePersonalSiteEnqueueBulk](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bk_CreatePersonalSiteEnqueueBulk) <br/> JSOM： **createPersonalSiteEnqueueBulk** <br/> REST： [CreatePersonalSiteEnqueueBulk](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderCreatePersonalSiteEnqueueBulk)          **POST** `https://<domain>-admin.sharepoint.com/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/CreatePersonalSiteEnqueueBulk`，在请求正文中传递  _emailIDs_ 参数的电子邮件地址的字符串数组（最多 200 个字符），例如 `{'emailIDs':['usera@contoso.onmicrosoft.com','userb@contoso.onmicrosoft.com']}`。  <br/> SSOM： **CreatePersonalSiteEnqueueBulk** <br/> |
   

## 针对 SharePoint 2013 中的用户和用户属性的新对象
<a name="bkmk_NewUserObjects"> </a>

SharePoint Server 2013 包括表示用户和用户属性的以下新对象：
  
    
    

-  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 对象和 [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) 对象表示源和以下活动的用户（以及文档、网站和任务）。
    
  
- 新客户端  [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) 对象，提供您可用于为当前用户创建个人网站的方法。但是，它不包含服务器端 [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) 对象所包含的所有用户属性。
    
  
-  [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) 对象包含一般用户属性，其 [UserProfileProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.UserProfileProperties.aspx) 属性包含用户配置文件属性。 [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) 是用于从客户端代码访问用户属性的主 API。
    
  

> **注释**
> 服务器对象模型版本是  [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) 对象和 [PersonProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PersonProperties.aspx) 对象。
  
    
    


## 其他资源
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 中的社交和协作功能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [如何：在 SharePoint 2013 中使用 JavaScript 对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [用户配置文件 REST API 引用](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)
    
  
