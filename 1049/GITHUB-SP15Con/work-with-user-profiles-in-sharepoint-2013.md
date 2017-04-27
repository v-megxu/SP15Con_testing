---
title: Работа с профилями пользователей в SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7437a7a8-85cb-4233-84af-1eec30dd54b2
---



# Работа с профилями пользователей в SharePoint 2013
Узнайте о распространенных задачах программирования для работы с профилями пользователей в SharePoint Server 2013.
## Интерфейсы API для работы с профилями пользователей в SharePoint 2013
<a name="bkmk_APIversions"> </a>

Профили пользователей и свойства этих профилей предоставляют информацию о пользователях SharePoint. SharePoint Server 2013 предусматривает следующие интерфейсы API, которые можно использовать для программной работы с данными профилями:
  
    
    

- Клиентские объектные модели для управляемого кода:
    
  - клиентская объектная модель .NET;
    
  
  - клиентская объектная модель Silverlight;
    
  
  - мобильная клиентская объектная модель.
    
  
- Объектная модель JavaScript.
    
  
- Служба передачи репрезентативного состояния (REST).
    
  
- Серверная объектная модель
    
  
Согласно передовой практике в разработке SharePoint 2013, используйте клиентские интерфейсы API, когда это возможно. Клиентские интерфейсы API включают клиентскую объектную модель .NET, объектную модель JavaScript и службу REST. Более подробную информацию об интерфейсах API в SharePoint 2013 и их использовании можно узнать в статье  [Выбор правильного набора API в SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

> **Примечание**
> В клиентских интерфейсах API доступен не весь функционал, представленный в сборке **Microsoft.Office.Server.UserProfiles**. Например, вы хотите использовать серверную объектную модель, чтобы создать или изменить профили пользователей, так как из клиентских API они доступны только для чтения (кроме изображения профиля пользователя). Кроме того, к некоторым пространствам имен, например  [Microsoft.Office.Server.Audience](https://msdn.microsoft.com/library/Microsoft.Office.Server.Audience.aspx) , [Microsoft.Office.Server.ReputationModel](https://msdn.microsoft.com/library/Microsoft.Office.Server.ReputationModel.aspx) или [Microsoft.Office.Server.SocialData](https://msdn.microsoft.com/library/Microsoft.Office.Server.SocialData.aspx) , отсутствует доступ со стороны клиента. Чтобы узнать, какой функционал поддерживается для клиентских интерфейсов API, ознакомьтесь со статьями [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) и [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) .
  
    
    

Каждый интерфейс API включает диспетчер объектов, который можно использовать для выполнения основных задач, связанных с профилем. В таблице 1 приведен диспетчер и другие ключевые объекты (или источники REST) в интерфейсах API, а также библиотека классов (или точка доступа), где их можно найти.
  
    
    

> **Примечание**
> Модель Silverlight и мобильная клиентская объектная модель не включены в таблицу 1 или таблицу 2, так как они предоставляют такой же основной функционал, как и клиентская объектная модель .NET, и одинаковые подписи. Клиентская объектная модель Silverlight определена в Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll, а мобильная клиентская объектная модель  в Microsoft.SharePoint.Client.UserProfiles.Phone.dll. 
  
    
    


**Таблица 1. SharePoint 2013 Интерфейсы API, используемые для программной работы с профилями пользователей**

|||
|:-----|:-----|
|Клиентская объектная модель .NET  <br/> См. статью  [Как: получение свойств профиля пользователя с помощью клиентской объектной модели .NET в SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |Диспетчер объектов:            [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.aspx) <br/> Основное пространство имен:            [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) <br/> Другие ключевые объекты:            [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) , [ProfileLoader](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.aspx) , [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) <br/> Библиотека классов:           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|Объектная модель JavaScript  <br/> См. статью  [Инструкции. Получение свойств профиля пользователя с помощью объектной модели JavaScript в SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |Диспетчер объектов:            [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> Основное пространство имен:            [SP.UserProfiles](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx) <br/> Другие ключевые объекты:            [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx),  [ProfileLoader](http://msdn.microsoft.com/library/c8dd9919-66a9-fffc-1100-14472d2ec2cb%28Office.15%29.aspx),  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) <br/> Библиотека классов:           SP.UserProfiles.js  <br/> |
|Служба REST  <br/> См. статью  [Справочник по API REST для профилей пользователей](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx) <br/> |Диспетчер объектов:            [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> URI конечной точки:            `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> Основное пространство имен:           **SP.UserProfiles** <br/> Другие ключевые ресурсы:            [PersonProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PersonProperties),  [ProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoader),  [UserProfile](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfile) <br/> |
|Серверная объектная модель  <br/> См. статью  [Инструкции. Работа с профилями пользователей и организации с использованием объектной модели сервера в SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |Диспетчер объектов:            [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.aspx) , [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) <br/> Основное пространство имен:            [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx) <br/> Другие ключевые объекты:            [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) , [CorePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CorePropertyManager.aspx) , [ProfilePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfilePropertyManager.aspx) , [ProfileSubtypeManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeManager.aspx) , [ProfileSubtypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypePropertyManager.aspx) , [ProfileTypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypePropertyManager.aspx) <br/> Библиотека классов:           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## Общие задачи программирования для работы с профилями пользователей в SharePoint 2013
<a name="bkmk_CommonTasks"> </a>

В таблице 2 приведены распространенные задачи программирования для работы с профилями пользователей и участники, используемые для их выполнения. Участники находятся в клиентской объектной модели .NET (CSOM), объектной модели JavaScript (JSOM), службе REST и серверной объектной модели (SSOM).
  
    
    

**Таблица 2. Интерфейс API для общих задач программирования для работы с профилями пользователей**


|**Задача**|**Участники**|
|:-----|:-----|
|Создание экземпляра объекта диспетчера в контексте текущего пользователя  <br/> |CSOM:  [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.#ctor.aspx) <br/> JSOM:  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> REST:  [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> SSOM:  [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.#ctor.aspx) (перегруженный) или [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.#ctor.aspx) <br/> |
|Изменение изображения в профиле текущего пользователя  <br/> |CSOM:  [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> JSOM:  [setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) <br/> REST:  [SetMyProfilePicture](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerSetMyProfilePicture)          **POST** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/SetMyProfilePicture` и передайте в тексте запроса параметр _picture_ <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) [PropertyConstants.PictureUrl].Value или [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> |
|Получение свойств текущего пользователя  <br/> |CSOM:  [GetMyProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMyProperties.aspx) <br/> JSOM:  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) <br/> REST:  [GetMyProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetMyProperties)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetMyProperties`          (либо получите некоторые основные свойства пользователя из  `/_api/social.feed/my` или `/_api/social.following/my`)  <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) <br/> |
|Получение свойств конкретного пользователя  <br/> |CSOM:  [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> JSOM:  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) <br/> REST:  [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPropertiesFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (перегруженный) или [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> |
|Получение свойств профиля пользователя для конкретного пользователя  <br/> |CSOM:  [GetUserProfilePropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertiesFor.aspx) <br/> JSOM:  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) <br/> REST: не реализовано.           Вызовите [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor), а затем получите свойства профиля пользователя из свойства **UserProfileProperties**, принадлежащего возвращенному объекту **PersonProperties**.  <br/> SSOM:  [GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.GetEnumerator.aspx) <br/> |
|Получение конкретного свойства профиля пользователя для пользователя  <br/> |CSOM:  [GetUserProfilePropertyFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertyFor.aspx) <br/> JSOM:  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) <br/> REST:  [GetUserProfilePropertyFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetUserProfilePropertyFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetUserProfilePropertyFor(accountName=@v,propertyName='PreferredName')?@v='domain\\\\user'` <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) (перегружен) и укажите имя свойства в индексаторе <br/> |
|Получение профиля пользователя  <br/> |CSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.GetUserProfile.aspx) (возвращает [клиентский профиль пользователя](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) только для текущего пользователя) <br/> JSOM:  [getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) (возвращает [клиентский профиль пользователя](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) только для текущего пользователя) <br/> REST:  [GetProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderGetProfileLoader)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile` (возвращает [клиентский профиль пользователя](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) только для текущего пользователя) <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (перегружен) <br/> |
|Узнать, существует ли учетная запись пользователя  <br/> |CSOM: не реализовано  <br/> JSOM: не реализовано  <br/> REST: не реализовано  <br/> SSOM:  [UserExists](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.UserExists.aspx) <br/> |
|Создание или изменение профилей пользователей, а также свойств и атрибутов профиля пользователя  <br/> (Клиентские интерфейсы API могут изменять изображение профиля. См. задачу "Изменение изображения в профиле пользователя" в этой таблице.)  <br/> |CSOM: не реализовано  <br/> JSOM: не реализовано  <br/> REST: не реализовано  <br/> SSOM: несколько вариантов, ознакомьтесь со статьей  [Инструкции. Работа с профилями пользователей и организации с использованием объектной модели сервера в SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |
|Удаление профиля пользователя  <br/> |CSOM: не реализовано  <br/> JSOM: не реализовано  <br/> REST: не реализовано  <br/> SSOM:  [RemoveProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveProfile.aspx) или [RemoveUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveUserProfile.aspx) (перегружен) <br/> |
|Подготовка личного сайта пользователя  <br/> |CSOM:  [CreatePersonalSiteEnque](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.CreatePersonalSiteEnque.aspx) (перегружен) <br/> JSOM:  [createPersonalSiteEnque](http://msdn.microsoft.com/library/f4bcb82d-4048-0b29-9bc6-ce70ead49988%28Office.15%29.aspx) (перегружен) <br/> REST:  [CreatePersonalSiteEnque](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfileCreatePersonalSiteEnque)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile/CreatePersonalSiteEnqueue` <br/> SSOM:  [CreatePersonalSite()](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.CreatePersonalSite.aspx) (перегружен) <br/> |
|Подготовка одного или нескольких личных сайтов пользователей  <br/> Доступно только для администраторов узлов Личный сайт на SharePoint Online  <br/> |CSOM:  [CreatePersonalSiteEnqueueBulk](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bk_CreatePersonalSiteEnqueueBulk) <br/> JSOM: **createPersonalSiteEnqueueBulk** <br/> REST:  [CreatePersonalSiteEnqueueBulk](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderCreatePersonalSiteEnqueueBulk)          **POST** `https://<domain>-admin.sharepoint.com/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/CreatePersonalSiteEnqueueBulk` и передайте в тексте запроса массив строк электронных адресов для параметра _emailIDs_ (не более 200 символов). Пример: `{'emailIDs':['usera@contoso.onmicrosoft.com','userb@contoso.onmicrosoft.com']}`.  <br/> SSOM: **CreatePersonalSiteEnqueueBulk** <br/> |
   

## Новые объекты для пользователей и свойства пользователей в SharePoint 2013
<a name="bkmk_NewUserObjects"> </a>

SharePoint Server 2013 содержит следующие новые объекты, которые представляют пользователей и их свойства:
  
    
    

- Объекты  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) и [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) , представляющие пользователей (а также документы, веб-сайты и задачи) для веб-каналов и подписки.
    
  
- Новый клиентский объект  [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) , предоставляющий методы для создания личных веб-сайтов для текущего пользователя. Однако данный объект содержит не все свойства, имеющиеся в объекте [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) .
    
  
- Объект  [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) содержит общие свойства пользователей, и его свойство [UserProfileProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.UserProfileProperties.aspx) содержит свойства профилей пользователей. [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) является основным интерфейсом API, предназначенным для доступа к свойствам пользователя из кода на стороне клиента.
    
  

> **Примечание**
> Версии серверной объектной модели являются объектами  [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) и [PersonProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PersonProperties.aspx) .
  
    
    


## Дополнительные ресурсы
<a name="bkmk_AdditionalResources"> </a>


-  [Социальные функции и функции совместной работы в SharePoint 2013](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [Начало разработки с использованием социальных функций в SharePoint 2013](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [Как: получение свойств профиля пользователя с помощью клиентской объектной модели .NET в SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Инструкции. Получение свойств профиля пользователя с помощью объектной модели JavaScript в SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Справочник по API REST для профилей пользователей](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [Инструкции. Работа с профилями пользователей и организации с использованием объектной модели сервера в SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [Подписка на людей в SharePoint 2013](follow-people-in-sharepoint-2013.md)
    
  
