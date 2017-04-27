---
title: Arbeiten mit Benutzerprofilen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7437a7a8-85cb-4233-84af-1eec30dd54b2
---



# Arbeiten mit Benutzerprofilen in SharePoint 2013
Informationen zu allgemeinen Programmierungsaufgaben für das Arbeiten mit Benutzerprofilen in SharePoint Server 2013.
## APIs für das Arbeiten mit Benutzerprofilen in SharePoint 2013
<a name="bkmk_APIversions"> </a>

Benutzerprofile und Benutzerprofileigenschaften liefern Informationen zu SharePoint-Benutzern. SharePoint Server 2013 stellt die folgenden APIs für eine programmtechnisch Verwendung von Benutzerprofilen bereit:
  
    
    

- Clientobjektmodelle für verwalteten Code
    
  - .NET-Clientobjektmodell
    
  
  - Silverlight-Clientobjektmodell
    
  
  - Mobiles Clientobjektmodell
    
  
- JavaScript-Objektmodell
    
  
- REST-Dienst (Representational State Transfer)
    
  
- Serverobjektmodell
    
  
Verwenden Sie als bewährtes Verfahren bei der SharePoint 2013-Entwicklung, wenn immer möglich, Client-APIs. Client-APIs enthalten das .NET-Clientmodell, das JavaScript-Objektmodell und den REST-Dienst. Weitere Informationen zu APIs finden Sie unter SharePoint 2013. Informationen zur Verwendungsweise finden Sie unter  [Auswählen des richtigen API-Satzes in SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    

> **HINWEIS**
> Nicht alle Funktionalitäten in der **Microsoft.Office.Server.UserProfiles**-Assembly ist durch Client-APIs verfügbar. Beispiel: Sie benötigen das Serverobjektmodell, um Benutzerprofile zu erstellen oder zu ändern, da sie in der Client-API schreibgeschützt sind (mit Ausnahme des Benutzerprofilbilds). Auch auf gewisse Namespaces, wie  [Microsoft.Office.Server.Audience](https://msdn.microsoft.com/library/Microsoft.Office.Server.Audience.aspx) , [Microsoft.Office.Server.ReputationModel](https://msdn.microsoft.com/library/Microsoft.Office.Server.ReputationModel.aspx) oder [Microsoft.Office.Server.SocialData](https://msdn.microsoft.com/library/Microsoft.Office.Server.SocialData.aspx) gibt es keinen clientseitigen Zugriff. Informationen dazu, welche Funktionalitäten für Client-APIs unterstützt werden, finden Sie unter [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) und [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) .
  
    
    

Jede API schließt ein verwaltetes Objekt mit ein, das Sie zum Ausführen von wichtigen profilbezogenen Aufgaben verwenden.
  
    
    

> **HINWEIS**
> Die Silverlight- und mobilen Clientobjektmodelle sind in Tabelle 1 oder Tabelle 2 nicht enthalten, da sie dieselben Kernfunktionen wie das .NET-Clientobjektmodell bereitstellen und dieselben Signaturen verwenden. Das Silverlight-Clientobjektmodell ist in Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll definiert und das mobile Clientobjektmodell in Microsoft.SharePoint.Client.UserProfiles.Phone.dll. 
  
    
    


**Tabelle 1. SharePoint 2013 APIs für das programmtechnische Arbeiten mit Benutzerprofilen**

|||
|:-----|:-----|
|.NET-Clientobjektmodell  <br/> Weitere Informationen:  [Vorgehensweise: Abrufen von Benutzerprofileigenschaften mithilfe des .NET-Clientobjektmodells in SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |Manager-Objekt:            [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.aspx) <br/> Primärer Namespace:            [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) <br/> Sonstige Schlüsselobjekte:            [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) , [ProfileLoader](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.aspx) , [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) <br/> Klassenbibliothek:           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|JavaScript-Objektmodell  <br/> Weitere Informationen:  [Vorgehensweise: Abrufen von Benutzerprofileigenschaften mithilfe des JavaScript-Objektmodells in SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |Manager-Objekt:            [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> Primärer Namespace:            [SP.UserProfiles](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx) <br/> Sonstige Schlüsselobjekte:            [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx),  [ProfileLoader](http://msdn.microsoft.com/library/c8dd9919-66a9-fffc-1100-14472d2ec2cb%28Office.15%29.aspx),  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) <br/> Klassenbibliothek:           SP.UserProfiles.js  <br/> |
|REST-Dienst  <br/> Siehe:  [Benutzerprofile - REST-API-Referenz](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx) <br/> |Manager-Ressource:            [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> Endpunkt-URI:            `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> Primärer Namespace:           **SP.UserProfiles** <br/> Sonstige Schlüsselobjekte:            [PersonProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PersonProperties),  [ProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoader),  [UserProfile](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfile) <br/> |
|Serverobjektmodell  <br/> Weitere Informationen:  [Vorgehensweise: Arbeiten mit Benutzerprofilen und Organisationsprofilen mithilfe des Serverobjektmodells in SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |Manager-Objekte:            [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.aspx) , [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) <br/> Primärer Namespace:            [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx) <br/> Sonstige Schlüsselobjekte:            [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) , [CorePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CorePropertyManager.aspx) , [ProfilePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfilePropertyManager.aspx) , [ProfileSubtypeManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeManager.aspx) , [ProfileSubtypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypePropertyManager.aspx) , [ProfileTypePropertyManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypePropertyManager.aspx) <br/> Klassenbibliothek:           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

## Allgemeine Programmierungsaufgaben für das Arbeiten mit Benutzerprofilen in SharePoint 2013
<a name="bkmk_CommonTasks"> </a>

Tabelle 2 zeigt allgemeine Programmierungsaufgaben für das Arbeiten mit Benutzerprofilen sowie die Elemente, die Sie zur Ausführung verwenden. Die Elemente stammen aus dem .NET-Clientobjektmodell (CSOM), dem JavaScript-Objektmodell (JSOM), dem REST-Dienst und dem Serverobjektmodell (SSOM).
  
    
    

**Tabelle 2. API für allgemeine Programmierungsaufgaben für das Arbeiten mit Benutzerprofilen**


|**Aufgabe**|**Elemente**|
|:-----|:-----|
|Erstellen einer Instanz eines Manager-Objekts im Kontext des aktuellen Benutzers  <br/> |CSOM:  [PeopleManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.#ctor.aspx) <br/> JSOM:  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) <br/> REST:  [PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager` <br/> SSOM:  [UserProfileManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.#ctor.aspx) (überladen) oder [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.#ctor.aspx) <br/> |
|Ändern des aktuellen Benutzerprofilbilds  <br/> |CSOM:  [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> JSOM:  [setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) <br/> REST:  [SetMyProfilePicture](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerSetMyProfilePicture)          **POST** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/SetMyProfilePicture` und den _picture_-Parameter im Anforderungstext weitergeben  <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) [PropertyConstants.PictureUrl].Value oder [SetMyProfilePicture](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.SetMyProfilePicture.aspx) <br/> |
|Abrufen der aktuellen Benutzereigenschaften  <br/> |CSOM:  [GetMyProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMyProperties.aspx) <br/> JSOM:  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) <br/> REST:  [GetMyProperties](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetMyProperties)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetMyProperties`          (oder einige grundlegende Benutzereigenschaften aus  `/_api/social.feed/my` oder `/_api/social.following/my` abrufen) <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) <br/> |
|Abrufen bestimmter Benutzereigenschaften  <br/> |CSOM:  [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> JSOM:  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) <br/> REST:  [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPropertiesFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (überladen) oder [GetPropertiesFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPropertiesFor.aspx) <br/> |
|Abrufen der Benutzerprofileigenschaften eines bestimmten Benutzers  <br/> |CSOM:  [GetUserProfilePropertiesFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertiesFor.aspx) <br/> JSOM:  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) <br/> REST: nicht implementiert           Aufrufen [GetPropertiesFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPropertiesFor) und dann die Benutzerprofileigenschaften aus der **UserProfileProperties**-Eigenschaft des zurückgegebenen **PersonProperties**-Objekts abrufen.  <br/> SSOM:  [GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.GetEnumerator.aspx) <br/> |
|Abrufen einer bestimmten Benutzerprofileigenschaft eines Benutzers  <br/> |CSOM:  [GetUserProfilePropertyFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetUserProfilePropertyFor.aspx) <br/> JSOM:  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) <br/> REST:  [GetUserProfilePropertyFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetUserProfilePropertyFor)          **GET** `http://<siteUri>/_api/SP.UserProfiles.PeopleManager/GetUserProfilePropertyFor(accountName=@v,propertyName='PreferredName')?@v='domain\\\\user'` <br/> SSOM:  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) (überladen) und den Eigenschaftennamen im Indexer angeben <br/> |
|Abrufen eines Benutzerprofils  <br/> |CSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.ProfileLoader.GetUserProfile.aspx) (gibt nur das [clientseitige Benutzerprofil](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects)für den aktuellen Benutzer zurück)  <br/> JSOM:  [getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) (gibt nur das [clientseitige Benutzerprofil](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) für den aktuellen Benutzer zurück) <br/> REST:  [GetProfileLoader](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderGetProfileLoader)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile` ((gibt nur das [clientseitige Benutzerprofil](work-with-user-profiles-in-sharepoint-2013.md#bkmk_NewUserObjects) für den aktuellen Benutzer zurück) <br/> SSOM:  [GetUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.GetUserProfile.aspx) (überladen) <br/> |
|Ermitteln, ob ein Benutzerkonto vorhanden ist  <br/> |CSOM: nicht implementiert  <br/> JSOM: nicht implementiert  <br/> REST: nicht implementiert  <br/> SSOM:  [UserExists](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.UserExists.aspx) <br/> |
|Erstellen oder Ändern von Benutzerprofilen und Benutzerprofileigenschaften und -attributen  <br/> (Client-APIs können das Profilbild ändern. Siehe auch die Aufgabe "Ändern des Benutzerprofilbilds" in dieser Tabelle.)  <br/> |CSOM: nicht implementiert  <br/> JSOM: nicht implementiert  <br/> REST: nicht implementiert  <br/> SSOM: mehrere - finden Sie unter  [Vorgehensweise: Arbeiten mit Benutzerprofilen und Organisationsprofilen mithilfe des Serverobjektmodells in SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |
|Löschen eines Benutzerprofils  <br/> |CSOM: nicht implementiert  <br/> JSOM: nicht implementiert  <br/> REST: nicht implementiert  <br/> SSOM:  [RemoveProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveProfile.aspx) oder [RemoveUserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfileManager.RemoveUserProfile.aspx) (überladen) <br/> |
|Bereitstellen einer persönlichen Benutzerwebsite  <br/> |CSOM:  [CreatePersonalSiteEnque](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.CreatePersonalSiteEnque.aspx) (überladen) <br/> JSOM:  [createPersonalSiteEnque](http://msdn.microsoft.com/library/f4bcb82d-4048-0b29-9bc6-ce70ead49988%28Office.15%29.aspx) (überladen) <br/> REST:  [CreatePersonalSiteEnque](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_UserProfileCreatePersonalSiteEnque)          **POST** `http://<siteUri>/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/GetUserProfile/CreatePersonalSiteEnqueue` <br/> SSOM:  [CreatePersonalSite()](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.CreatePersonalSite.aspx) (überladen) <br/> |
|Bereitstellen von mindestens einer persönlichen Benutzerwebsite  <br/> Nur verfügbar für Meine Website Hostadministratoren in SharePoint Online  <br/> |CSOM:  [CreatePersonalSiteEnqueueBulk](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bk_CreatePersonalSiteEnqueueBulk) <br/> JSOM: **createPersonalSiteEnqueueBulk** <br/> REST:  [CreatePersonalSiteEnqueueBulk](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_ProfileLoaderCreatePersonalSiteEnqueueBulk)          **POST** `https://<domain>-admin.sharepoint.com/_api/SP.UserProfiles.ProfileLoader.GetProfileLoader/CreatePersonalSiteEnqueueBulk` und Zeichenfolgenarray der E-Mail-Adressen für den _emailIDs_-Parameter (max. 200 Zeichen) im Anforderungstext (Beispiel:  `{'emailIDs':['usera@contoso.onmicrosoft.com','userb@contoso.onmicrosoft.com']}`).  <br/> SSOM: **CreatePersonalSiteEnqueueBulk** <br/> |
   

## Neue Objekte für Benutzer und Benutzereigenschaften in SharePoint 2013
<a name="bkmk_NewUserObjects"> </a>

SharePoint Server 2013 umfasst die folgenden neuen Objekte, die für Benutzer und Benutzereigenschaften stehen:
  
    
    

- Das  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) -Objekt und das [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) -Objekt stehen für Benutzer (und Dokumente, Websites und Aufgaben) für einen Feed und die folgenden Aktivitäten.
    
  
- Ein neues clientseitiges  [UserProfile](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.UserProfile.aspx) -Objekt stellt Methoden bereit, mit denen Sie eine persönliche Website für den aktuellen Benutzer erstellen können. Es enthält aber nicht alle Benutzereigenschaften, die das serverseitige [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) -Objekt enthält.
    
  
- Das  [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) -Objekt enthält allgemeine Benutzereigenschaften und die [UserProfileProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.UserProfileProperties.aspx) -Eigenschaft enthält Benutzerprofileigenschaften. [PersonProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PersonProperties.aspx) ist die primäre API für den Zugriff auf Benutzereigenschaften aus dem clientseitigen Code.
    
  

> **HINWEIS**
> Versionen des Serverobjektmodells sind das  [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) -Objekt und das [PersonProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PersonProperties.aspx) -Objekt.
  
    
    


## Zusätzliche Ressourcen
<a name="bkmk_AdditionalResources"> </a>


-  [Soziale Funktionen und Zusammenarbeit in SharePoint 2013](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [Erste Schritte bei der Entwicklung mit thematischen Features in SharePoint 2013](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Abrufen von Benutzerprofileigenschaften mithilfe des .NET-Clientobjektmodells in SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Vorgehensweise: Abrufen von Benutzerprofileigenschaften mithilfe des JavaScript-Objektmodells in SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Benutzerprofile - REST-API-Referenz](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [Vorgehensweise: Arbeiten mit Benutzerprofilen und Organisationsprofilen mithilfe des Serverobjektmodells in SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [Folgen von Personen in SharePoint 2013](follow-people-in-sharepoint-2013.md)
    
  
