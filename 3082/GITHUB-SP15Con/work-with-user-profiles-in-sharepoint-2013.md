---
title: Trabajar con perfiles de usuario en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7437a7a8-85cb-4233-84af-1eec30dd54b2
---



# Trabajar con perfiles de usuario en SharePoint 2013
Obtenga información sobre tareas de programación comunes para trabajar con perfiles de usuario en SharePoint Server 2013.
## API para trabajar con perfiles de usuario en SharePoint 2013
<a name="bkmk_APIversions"> </a>

Los perfiles de usuario y las propiedades de perfil de usuario ofrecen información sobre los usuarios de SharePoint. SharePoint Server 2013 proporciona las siguientes API que se pueden usar para trabajar con perfiles de usuario mediante programación:
  
    
    

- Modelos de objetos de cliente para código administrado
    
  - Modelo de objetos de cliente de .NET
    
  
  - Modelo de objetos de cliente de Silverlight
    
  
  - Modelo de objetos de cliente móvil
    
  
- Modelo de objetos de JavaScript
    
  
- Servicio Transferencia de estado representacional (REST)
    
  
- Modelo de objetos de servidor
    
  
Como práctica recomendada para el desarrollo de SharePoint 2013, use API de cliente siempre que pueda. Las API de cliente incluyen el modelo de objetos de cliente de .NET, el modelo de objetos de JavaScript y el servicio REST. Para obtener más información sobre las API de SharePoint 2013 y cuándo usarlas, consulte  [Elegir el conjunto de API correcto en SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

> **NOTA**
> No toda la funcionalidad que se encuentra en el ensamblado **Microsoft.Office.Server.UserProfiles** está disponible en las API de cliente. Por ejemplo, hay que usar el modelo de objetos de servidor para crear o cambiar perfiles de usuario, ya que son de solo lectura en las API de cliente (excepto la imagen del perfil de usuario). Además, no hay acceso de cliente a algunos espacios de nombre, como [Microsoft.Office.Server.Audience](https://msdn.microsoft.com/library/Microsoft.Office.Server.Audience.aspx) , [Microsoft.Office.Server.ReputationModel](https://msdn.microsoft.com/library/Microsoft.Office.Server.ReputationModel.aspx) o [Microsoft.Office.Server.SocialData](https://msdn.microsoft.com/library/Microsoft.Office.Server.SocialData.aspx) . Para ver la funcionalidad compatible con las API de cliente, consulte [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) y [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) .
  
    
    

Cada API incluye un objeto de administrador que se usa para realizar tareas principales relacionadas con el perfil. En la tabla 1 se muestra el administrador y otros objetos fundamentales (o recursos REST) en las API y la biblioteca de clases (o punto de acceso) en las que se pueden encontrar.
  
    
    

> **NOTA**
> Los modelos de objetos de cliente de Silverlight y de cliente móvil no están incluidos en la tabla 1 ni la 2 porque ofrecen la misma funcionalidad principal que el modelo de objetos de cliente de .NET y usan las mismas firmas. El modelo de objetos de cliente de Silverlight se define en Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll y el modelo de objetos de cliente móvil en Microsoft.SharePoint.Client.UserProfiles.Phone.dll. 
  
    
    


**Tabla 1. SharePoint 2013 API usadas para trabajar con perfiles de usuario mediante programación**

|||
|:-----|:-----|
|Modelo de objetos de cliente de .NET  <br/> Consulte  [Recuperar propiedades de perfil de usuario usando el modelo de objetos de cliente .NET en SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |Objeto de administrador:            [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.aspx) <br/> Espacio de nombres principal:            [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) <br/> Otros objetos fundamentales:            [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) , [ProfileLoader](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.aspx) , [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) <br/> Biblioteca de clases:           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|Modelo de objetos de JavaScript  <br/> Consulte:  [Procedimiento para recuperar propiedades de perfil de usuario mediante el modelo de objetos de JavaScript en SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |Objeto de administrador:            [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> Espacio de nombres principal:            [SP.UserProfiles](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx) <br/> Otros objetos fundamentales:            [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx),  [ProfileLoader](http://msdn.microsoft.com/library/c8dd9919-66a9-fffc-1100-14472d2ec2cb%28Office.15%29.aspx),  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) <br/> Biblioteca de clases:           SP.UserProfiles.js  <br/> |
|Servicio REST  <br/> Consulte:  [Referencia sobre la API de REST de perfiles de usuario](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx) <br/> |Recursos de administrador:            [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> URI del extremo:            `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> Espacio de nombres principal:           **SP.UserProfiles** <br/> Otros recursos fundamentales:            [PersonProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PersonProperties),  [ProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoader),  [UserProfile](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfile) <br/> |
|Modelo de objetos de servidor  <br/> Consulte:  [Cómo trabajar con perfiles de usuario y perfiles de organización con el modelo de objetos del servidor en SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |Objetos de administrador:            [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.aspx) , [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) <br/> Espacio de nombres principal:            [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx) <br/> Otros objetos fundamentales:            [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) , [CorePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CorePropertyManager.aspx) , [ProfilePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfilePropertyManager.aspx) , [ProfileSubtypeManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeManager.aspx) , [ProfileSubtypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypePropertyManager.aspx) , [ProfileTypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypePropertyManager.aspx) <br/> Biblioteca de clases:           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## Tareas de programación comunes para trabajar con perfiles de usuario en SharePoint 2013
<a name="bkmk_CommonTasks"> </a>

En la tabla 2 se muestran las tareas de programación comunes para trabajar con perfiles de usuario y los miembros que se usan para realizarlas. Los miembros pertenecen al modelo de objetos de cliente de .NET (CSOM), el modelo de objetos de JavaScript (JSOM), el servicio REST y el modelo de objetos de servidor (SSOM).
  
    
    

**Tabla 2. API de tareas de programación comunes para trabajar con perfiles de usuario**


|**Tarea**|**Miembros**|
|:-----|:-----|
|Crear una instancia de un objeto de administrador en el contexto del usuario actual  <br/> |CSOM:  [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.#ctor.aspx) <br/> JSOM:  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> REST:  [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> SSOM:  [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.#ctor.aspx) (sobrecargado) o [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.#ctor.aspx) <br/> |
|Cambiar la imagen del perfil del usuario actual  <br/> |CSOM:  [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> JSOM:  [setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) <br/> REST:  [SetMyProfilePicture](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerSetMyProfilePicture)          **POST** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/SetMyProfilePicture` y pasar el parámetro _picture_ en el cuerpo de la solicitud <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) [PropertyConstants.PictureUrl].Value o [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> |
|Obtener las propiedades del usuario actual  <br/> |CSOM:  [GetMyProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMyProperties.aspx) <br/> JSOM:  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) <br/> REST:  [GetMyProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetMyProperties)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetMyProperties`          (u obtener algunas propiedades de usuario básicas de  `/_api/social.feed/my` o `/_api/social.following/my`)  <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) <br/> |
|Obtener las propiedades de un usuario concreto  <br/> |CSOM:  [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> JSOM:  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) <br/> REST:  [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPropertiesFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (sobrecargado) o [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> |
|Obtener las propiedades de perfil de usuario de un usuario concreto  <br/> |CSOM:  [GetUserProfilePropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertiesFor.aspx) <br/> JSOM:  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) <br/> REST: no implementado           Llamar a [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor) y luego obtener las propiedades de perfil de usuario de la propiedad **UserProfileProperties** del objeto **PersonProperties** devuelto. <br/> SSOM:  [GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.GetEnumerator.aspx) <br/> |
|Obtener una propiedad de perfil de usuario concreta de un usuario  <br/> |CSOM:  [GetUserProfilePropertyFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertyFor.aspx) <br/> JSOM:  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) <br/> REST:  [GetUserProfilePropertyFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetUserProfilePropertyFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetUserProfilePropertyFor(accountName=@v,propertyName='PreferredName')?@v='domain\\\\user'` <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) (sobrecargado) y especificar el nombre de la propiedad en el indexador <br/> |
|Obtener un perfil de usuario  <br/> |CSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.GetUserProfile.aspx) (devuelve el [perfil de usuario de cliente](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) del usuario actual únicamente) <br/> JSOM:  [getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) (devuelve el [perfil de usuario de cliente](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) del usuario actual únicamente) <br/> REST:  [GetProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderGetProfileLoader)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile` (devuelve el [perfil de usuario del lado cliente](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) del usuario actual únicamente) <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (sobrecargado) <br/> |
|Descubrir si una cuenta de usuario existe  <br/> |CSOM: no implementado  <br/> JSOM: no implementado  <br/> REST: no implementado  <br/> SSOM:  [UserExists](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.UserExists.aspx) <br/> |
|Crear o cambiar perfiles de usuario y propiedades y atributos de perfil de usuario  <br/> (Las API de cliente pueden cambiar la imagen del perfil. Consulte la tarea "Cambiar la imagen del perfil del usuario" en esta tabla.)  <br/> |CSOM: no implementado  <br/> JSOM: no implementado  <br/> REST: no implementado  <br/> SSOM: varios; consulte  [Cómo trabajar con perfiles de usuario y perfiles de organización con el modelo de objetos del servidor en SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |
|Eliminar un perfil de usuario  <br/> |CSOM: no implementado  <br/> JSOM: no implementado  <br/> REST: no implementado  <br/> SSOM:  [RemoveProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveProfile.aspx) o [RemoveUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveUserProfile.aspx) (sobrecargado) <br/> |
|Aprovisionar un sitio personal de un usuario  <br/> |CSOM:  [CreatePersonalSiteEnque](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.CreatePersonalSiteEnque.aspx) (sobrecargado) <br/> JSOM:  [createPersonalSiteEnque](http://msdn.microsoft.com/library/f4bcb82d-4048-0b29-9bc6-ce70ead49988%28Office.15%29.aspx) (sobrecargado) <br/> REST:  [CreatePersonalSiteEnque](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfileCreatePersonalSiteEnque)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile/CreatePersonalSiteEnqueue` <br/> SSOM:  [CreatePersonalSite()](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.CreatePersonalSite.aspx) (sobrecargado) <br/> |
|Aprovisionar sitios personales de uno o varios usuarios  <br/> Disponible para administradores de host de Mi sitio en SharePoint Online únicamente  <br/> |CSOM:  [CreatePersonalSiteEnqueueBulk](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bk_CreatePersonalSiteEnqueueBulk) <br/> JSOM: **createPersonalSiteEnqueueBulk** <br/> REST:  [CreatePersonalSiteEnqueueBulk](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderCreatePersonalSiteEnqueueBulk)          **POST** `https://<domain>-admin.sharepoint.com/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/CreatePersonalSiteEnqueueBulk` y pasar una matriz de cadena de direcciones de correo electrónico para el parámetro _emailIDs_ (200 caracteres máximo) en el cuerpo de la solicitud (ejemplo: `{'emailIDs':['usera@contoso.onmicrosoft.com','userb@contoso.onmicrosoft.com']}`).  <br/> SSOM: **CreatePersonalSiteEnqueueBulk** <br/> |
   

## Nuevos objetos para usuarios y propiedades de usuario en SharePoint 2013
<a name="bkmk_NewUserObjects"> </a>

SharePoint Server 2013 incluye los siguientes objetos nuevos que representan usuarios y propiedades de usuario:
  
    
    

- El objeto  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) y el objeto [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) representan usuarios (y documentos, sitios y tareas) para actividades de suministro y seguimiento.
    
  
- Un nuevo objeto de cliente  [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) que proporciona métodos que se pueden usar para crear un sitio personal para el usuario actual. No obstante, no contiene todas las propiedades de usuario que contiene el objeto de servidor [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) .
    
  
- El objeto  [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) contiene propiedades de usuario generales y su propiedad [UserProfileProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.UserProfileProperties.aspx) contiene propiedades de perfil de usuario. [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) es la API principal para obtener acceso a propiedades de usuario del código de cliente.
    
  

> **NOTA**
> Versiones del modelo de objetos de servidor son el objeto  [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) y el objeto [PersonProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PersonProperties.aspx) .
  
    
    


## Recursos adicionales
<a name="bkmk_AdditionalResources"> </a>


-  [Características sociales y de colaboración en SharePoint 2013](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [Comience a desarrollar con características sociales en SharePoint 2013](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [Recuperar propiedades de perfil de usuario usando el modelo de objetos de cliente .NET en SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Procedimiento para recuperar propiedades de perfil de usuario mediante el modelo de objetos de JavaScript en SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Referencia sobre la API de REST de perfiles de usuario](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [Cómo trabajar con perfiles de usuario y perfiles de organización con el modelo de objetos del servidor en SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [Seguir personas en SharePoint 2013](follow-people-in-sharepoint-2013.md)
    
  
