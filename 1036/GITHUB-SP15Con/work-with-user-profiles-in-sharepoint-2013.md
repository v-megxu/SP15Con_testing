---
title: Utiliser des profils utilisateur dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7437a7a8-85cb-4233-84af-1eec30dd54b2
---



# Utiliser des profils utilisateur dans SharePoint 2013
Découvrez les tâches de programmation courantes pour l'utilisation de profils utilisateur dans SharePoint Server 2013.
## API pour l'utilisation de profils dans SharePoint 2013
<a name="bkmk_APIversions"> </a>

Les profils utilisateur et les propriétés des profils utilisateur fournissent des informations sur les utilisateurs SharePoint. SharePoint Server 2013 propose les API suivantes qui permettent d'utiliser les profils utilisateur par programmation :
  
    
    

- Modèles objet client pour le code managé
    
  - Modèle objet client .NET
    
  
  - Modèle objet client Silverlight
    
  
  - Modèle objet client mobile
    
  
- Modèle objet JavaScript
    
  
- Service REST (Representational State Transfer)
    
  
- Modèle objet serveur
    
  
Il est vivement recommandé d'utiliser des API client quand vous le pouvez pour le développement SharePoint 2013. Les API client comprennent le modèle objet client .NET, le modèle objet JavaScript et le service REST. Pour plus d'informations sur les API proposées dans SharePoint 2013 et pour savoir quand les utiliser, voir  [Choisir l'ensemble d'API approprié dans SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

> **REMARQUE**
> Les fonctionnalités que vous trouvez dans l'assembly **Microsoft.Office.Server.UserProfiles** ne sont pas toutes disponibles dans les API client. Par exemple, vous devez utiliser le modèle objet serveur pour créer ou modifier les profils utilisateur, car ils sont en lecture seule dans l'API client (sauf l'image du profil utilisateur). Il n'existe pas non plus d'accès côté client à certains espaces de noms, tels que [Microsoft.Office.Server.Audience](https://msdn.microsoft.com/library/Microsoft.Office.Server.Audience.aspx) , [Microsoft.Office.Server.ReputationModel](https://msdn.microsoft.com/library/Microsoft.Office.Server.ReputationModel.aspx) ou [Microsoft.Office.Server.SocialData](https://msdn.microsoft.com/library/Microsoft.Office.Server.SocialData.aspx) . Pour connaître les fonctionnalités prises en charge dans les API client, voir [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) et [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) .
  
    
    

Chaque API inclut un objet gestionnaire que vous utilisez pour effectuer les tâches principales liées au profil. Le tableau 1 répertorie les objets gestionnaire et autres objets clés (ou ressources REST) inclus dans les API, ainsi que la bibliothèque de classes (ou point d'accès) où vous pouvez les trouver.
  
    
    

> **REMARQUE**
> Les modèles objet client Silverlight et mobile ne sont pas inclus dans les tableaux 1 et 2, car ils fournissent les mêmes fonctionnalités de base que le modèle objet client .NET et utilisent les mêmes signatures. Le modèle objet client Silverlight est défini dans Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll et le modèle objet client mobile est défini dans Microsoft.SharePoint.Client.UserProfiles.Phone.dll. 
  
    
    


**Tableau 1. API SharePoint 2013 permettant d'utiliser les profils utilisateur par programmation**

|||
|:-----|:-----|
|Modèle objet client .NET  <br/> Voir :  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet client .NET dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |Objet gestionnaire :            [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.aspx) <br/> Espace de noms principal :            [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) <br/> Autres objets clés :            [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) , [ProfileLoader](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.aspx) , [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) <br/> Bibliothèque de classes :           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|Modèle objet JavaScript  <br/> Voir :  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet JavaScript dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |Objet gestionnaire :            [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> Espace de noms principal :            [SP.UserProfiles](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx) <br/> Autres objets clés :            [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx),  [ProfileLoader](http://msdn.microsoft.com/library/c8dd9919-66a9-fffc-1100-14472d2ec2cb%28Office.15%29.aspx),  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) <br/> Bibliothèque de classes :           SP.UserProfiles.js  <br/> |
|Service REST  <br/> Voir :  [Référence de l'API REST des profils utilisateur](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx) <br/> |Ressource de gestionnaire :            [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> URI du point de terminaison :            `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> Espace de noms principal :           **SP.UserProfiles** <br/> Autres ressources clés :            [PersonProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PersonProperties),  [ProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoader),  [UserProfile](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfile) <br/> |
|Modèle objet serveur  <br/> Voir :  [Comment travailler avec les profils utilisateur et les profils d'organisation en utilisant le modèle objet serveur dans SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |Objets gestionnaire :            [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.aspx) , [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) <br/> Espace de noms principal :            [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx) <br/> Autres objets clés :            [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) , [CorePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CorePropertyManager.aspx) , [ProfilePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfilePropertyManager.aspx) , [ProfileSubtypeManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeManager.aspx) , [ProfileSubtypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypePropertyManager.aspx) , [ProfileTypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypePropertyManager.aspx) <br/> Bibliothèque de classes :           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## Tâches de programmation courantes pour l'utilisation de profils utilisateur dans SharePoint 2013
<a name="bkmk_CommonTasks"> </a>

Le tableau 2 répertorie les tâches de programmation courantes pour l'utilisation de profils utilisateur et les membres que vous utilisez pour les effectuer. Les membres proviennent du modèle objet client .NET (CSOM), du modèle objet JavaScript (JSOM), du service REST et du modèle objet serveur (SSOM).
  
    
    

**Tableau 2. API pour les tâches de programmation courantes pour l'utilisation de profils utilisateur**


|**Tâche**|**Membres**|
|:-----|:-----|
|Créer une instance d'un objet gestionnaire dans le contexte de l'utilisateur actuel  <br/> |CSOM :  [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.#ctor.aspx) <br/> JSOM :  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> REST :  [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> SSOM :  [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.#ctor.aspx) (surchargé) ou [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.#ctor.aspx) <br/> |
|Modifier l'image de profil de l'utilisateur actuel  <br/> |CSOM :  [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> JSOM :  [setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) <br/> REST :  [SetMyProfilePicture](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerSetMyProfilePicture)          **POST** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/SetMyProfilePicture` et passer le paramètre _picture_ dans le corps de la demande <br/> SSOM :  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) [PropertyConstants.PictureUrl].Value ou [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> |
|Obtenir les propriétés de l'utilisateur actuel  <br/> |CSOM :  [GetMyProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMyProperties.aspx) <br/> JSOM :  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) <br/> REST :  [GetMyProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetMyProperties)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetMyProperties`          (ou obtenir des propriétés utilisateur de base à partir de  `/_api/social.feed/my` ou `/_api/social.following/my`)  <br/> SSOM :  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) <br/> |
|Obtenir les propriétés d'un utilisateur spécifique  <br/> |CSOM :  [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> JSOM :  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) <br/> REST :  [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPropertiesFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM :  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (surchargé) ou [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> |
|Obtenir les propriétés de profil d'un utilisateur spécifique  <br/> |CSOM :  [GetUserProfilePropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertiesFor.aspx) <br/> JSOM :  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) <br/> REST : non implémenté           Appeler [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor), puis obtenir les propriétés du profil utilisateur à partir de la propriété **UserProfileProperties** de l'objet **PersonProperties** renvoyé. <br/> SSOM :  [GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.GetEnumerator.aspx) <br/> |
|Obtenir une propriété de profil utilisateur spécifique pour un utilisateur  <br/> |CSOM :  [GetUserProfilePropertyFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertyFor.aspx) <br/> JSOM :  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) <br/> REST :  [GetUserProfilePropertyFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetUserProfilePropertyFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetUserProfilePropertyFor(accountName=@v,propertyName='PreferredName')?@v='domain\\\\user'` <br/> SSOM :  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) (surchargé) et spécifier le nom de propriété dans l'indexeur <br/> |
|Obtenir un profil utilisateur  <br/> |CSOM :  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.GetUserProfile.aspx) (renvoie le [profil utilisateur côté client](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) de l'utilisateur actuel uniquement) <br/> JSOM :  [getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) (renvoie le [profil utilisateur côté client](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) de l'utilisateur actuel uniquement) <br/> REST :  [GetProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderGetProfileLoader)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile` (renvoie le [profil utilisateur côté client](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) de l'utilisateur actuel uniquement) <br/> SSOM :  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (surchargé) <br/> |
|Déterminer l'existence d'un compte d'utilisateur  <br/> |CSOM : non implémenté  <br/> JSOM : non implémenté  <br/> REST : non implémenté  <br/> SSOM :  [UserExists](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.UserExists.aspx) <br/> |
|Créer ou modifier les profils utilisateur ainsi que les attributs et les propriétés des profils utilisateur  <br/> (Les API client peuvent modifier l'image de profil. Voir la tâche « Modifier l'image de profil de l'utilisateur actuel » dans ce tableau.)  <br/> |CSOM : non implémenté  <br/> JSOM : non implémenté  <br/> REST : non implémenté  <br/> SSOM : multiples. Voir  [Comment travailler avec les profils utilisateur et les profils d'organisation en utilisant le modèle objet serveur dans SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |
|Supprimer un profil utilisateur  <br/> |CSOM : non implémenté  <br/> JSOM : non implémenté  <br/> REST : non implémenté  <br/> SSOM :  [RemoveProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveProfile.aspx) ou [RemoveUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveUserProfile.aspx) (surchargé) <br/> |
|Configurer le site personnel d'un utilisateur  <br/> |CSOM :  [CreatePersonalSiteEnque](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.CreatePersonalSiteEnque.aspx) (surchargé) <br/> JSOM :  [createPersonalSiteEnque](http://msdn.microsoft.com/library/f4bcb82d-4048-0b29-9bc6-ce70ead49988%28Office.15%29.aspx) (surchargé) <br/> REST :  [CreatePersonalSiteEnque](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfileCreatePersonalSiteEnque)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile/CreatePersonalSiteEnqueue` <br/> SSOM :  [CreatePersonalSite()](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.CreatePersonalSite.aspx) (surchargé) <br/> |
|Configurer les sites personnels d'un ou de plusieurs utilisateurs  <br/> Disponible pour les administrateurs de l'hôte Site Mon site sur SharePoint Online uniquement  <br/> |CSOM :  [CreatePersonalSiteEnqueueBulk](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bk_CreatePersonalSiteEnqueueBulk) <br/> JSOM : **createPersonalSiteEnqueueBulk** <br/> REST :  [CreatePersonalSiteEnqueueBulk](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderCreatePersonalSiteEnqueueBulk)          **POST** `https://<domain>-admin.sharepoint.com/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/CreatePersonalSiteEnqueueBulk` et transmettre un tableau de chaînes d'adresses de messagerie pour le paramètre _emailIDs_ (200 caractères maximum) dans le corps de la demande (exemple : `{'emailIDs':['usera@contoso.onmicrosoft.com','userb@contoso.onmicrosoft.com']}`).  <br/> SSOM : **CreatePersonalSiteEnqueueBulk** <br/> |
   

## Nouveaux objets pour les utilisateurs et les propriétés utilisateur dans SharePoint 2013
<a name="bkmk_NewUserObjects"> </a>

SharePoint Server 2013 inclut les nouveaux objets suivants, qui représentent des utilisateurs et des propriétés utilisateur :
  
    
    

- L'objet  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) et l'objet [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) représentent les utilisateurs (ainsi que les documents, les sites et les tâches) pour le flux et les activités suivantes.
    
  
- L'objet  [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) côté client fournit des méthodes que vous pouvez utiliser en vue de créer un site personnel pour l'utilisateur actuel. Cependant, il ne contient pas toutes les propriétés utilisateur que contient l'objet [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) côté serveur.
    
  
- L'objet  [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) contient des propriétés utilisateur générales et sa propriété [UserProfileProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.UserProfileProperties.aspx) contient des propriétés de profil utilisateur. [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) est l'API principale permettant d'accéder aux propriétés utilisateur à partir du code côté client.
    
  

> **REMARQUE**
> Les versions de modèle objet serveur sont l'objet  [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) et l'objet [PersonProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PersonProperties.aspx) .
  
    
    


## Ressources supplémentaires
<a name="bkmk_AdditionalResources"> </a>


-  [Fonctions sociales et de collaboration dans SharePoint 2013](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [Mise en route du développement avec les fonctions sociales dans SharePoint 2013](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet client .NET dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet JavaScript dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Référence de l'API REST des profils utilisateur](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [Comment travailler avec les profils utilisateur et les profils d'organisation en utilisant le modèle objet serveur dans SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [Suivre les personnes dans SharePoint 2013](follow-people-in-sharepoint-2013.md)
    
  
