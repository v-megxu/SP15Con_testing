---
title: Folgen von Personen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 0fa2e235-63d0-41b1-9eed-4aeb2f59a14d
---



# Folgen von Personen in SharePoint 2013
Informationen Sie zu allgemeinen Programmieraufgaben für folgende Personen in SharePoint Server 2013.
## APIs für die folgenden Personen in SharePoint Server 2013
<a name="bkmk_APIversions"> </a>

Wenn ein Benutzer Personen in SharePoint Server 2013 folgt, Blogbeiträge mikroblogs, dass Personen veröffentlichen und Benachrichtigungen über deren Aktivitäten im Newsfeed eines Benutzers angezeigt. Die Features im Zusammenhang mit der folgenden Personen können auf den Seiten der **Newsfeed** und **Personen, die ich Folge** angezeigt werden.
  
    
    
SharePoint Server 2013 bietet die folgenden APIs, die Sie verwenden können, um programmgesteuert Personen folgen:
  
    
    

- Clientobjektmodelle für verwalteten Code
    
  - .NET-Clientobjektmodell
    
  
  - Silverlight-Clientobjektmodell
    
  
  - Mobiles Clientobjektmodell
    
  
- JavaScript-Objektmodell
    
  
- REST (Representational State Transfer)-Dienst
    
  
- Serverobjektmodell
    
  
Als bewährte Methode bei der Entwicklung von SharePoint 2013 wann immer möglich verwenden Sie-Client-APIs. Client-APIs gehören die Clientobjektmodelle, ein JavaScript-Objektmodell und REST-Dienst. Weitere Informationen zu den APIs in SharePoint 2013 und wann sie verwendet werden finden Sie unter  [Auswählen des richtigen API-Satzes in SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    
Jede API enthält ein Managerobjekt, mit denen Sie wichtige Aufgaben für die folgenden Personen.
  
    
    

> **HINWEIS**
> Die gleichen APIs dienen zum Folgen von Inhalten. Finden Sie unter  [Folgen von Inhalten in SharePoint 2013](follow-content-in-sharepoint-2013.md) eine Übersicht über die Aufgaben zum folgenden Inhalt.
  
    
    

Tabelle 1 zeigt den Manager und andere Schlüsselobjekte (oder REST-Ressourcen) in den APIs und die Klassenbibliothek (oder Zugriffspunkt), in dem Sie diese finden können.
  
    
    

> **HINWEIS**
> Die Objektmodelle von mobilen Client und Silverlight sind nicht explizit in Tabelle 1 oder Tabelle 2 enthalten, da sie die gleichen Kernfunktionen als .NET Client-Objektmodell bieten und die gleichen Signaturen verwenden. Das Silverlight-Clientobjektmodell in Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll definiert ist, und mobiles Clientobjektmodell in Microsoft.SharePoint.Client.UserProfiles.Phone.dll definiert ist.
  
    
    


**In Tabelle 1. SharePoint 2013 APIs für die folgenden Personen programmgesteuert verwendet**

|||
|:-----|:-----|
|.NET-Clientobjektmodell <br/> Weitere Informationen:  [Vorgehensweise: führen Sie die Personen mithilfe des clientobjektmodells .NET SharePoint 2013](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md) <br/> |Manager-Objekt:            [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) <br/> Primärer Namespace:            [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> Sonstige Schlüsselobjekte:            [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) , [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) , [SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) , [SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) <br/> Klassenbibliothek:           Microsoft.SharePoint.Client.UserProfiles.dll <br/> |
|JavaScript-Objektmodell <br/> Weitere Informationen:  [Vorgehensweise: folgen Sie Menschen mit der JavaScript-Objektmodell in SharePoint 2013](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md) <br/> |Manager-Objekt:            [SocialFollowingManager](http://msdn.microsoft.com/library/9ee1c0c0-b864-f0c3-f0cb-4dd4f1870dfa%28Office.15%29.aspx) <br/> Primärer Namespace:           SP.Social **SP.Social** <br/> Sonstige Schlüsselobjekte:            [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx),  [SocialActorInfo](http://msdn.microsoft.com/library/d940db32-1561-c868-bb66-0612e2031f17%28Office.15%29.aspx),  [SocialActorType](http://msdn.microsoft.com/library/fbde74da-f292-dc87-0b7e-81bc5b7a880c%28Office.15%29.aspx),  [SocialActorTypes](http://msdn.microsoft.com/library/a460c3e6-ed88-117d-6755-4c5803a154a0%28Office.15%29.aspx) <br/> Klassenbibliothek:           SP.UserProfiles.js <br/> |
|REST-Dienst <br/> Weitere Informationen:  [REST-API-Referenz zum Folgen von Personen und Inhalten für SharePoint 2013](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> |Manager-Ressource:            [social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md) <br/> Endpunkt-URI:            `<siteUri>/_api/social.following` <br/> Primärer Namespace (OData):           **sp.social.SocialRestFollowingManager** <br/> Andere wichtigen Ressourcen:           **SocialActor**, **SocialActorInfo**, **SocialActorType**, **SocialActorTypes** <br/> |
|Serverobjektmodell <br/> |Manager-Objekt:            [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.aspx) <br/> Primärer Namespace:            [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> Sonstige Schlüsselobjekte:            [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) , [SPSocialActorInfo](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorInfo.aspx) , [SPSocialActorType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorType.aspx) , [SPSocialActorTypes](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActorTypes.aspx) <br/> Klassenbibliothek:           Microsoft.Office.Server.UserProfiles.dll <br/> |
   

## Allgemeine Programmieraufgaben für die folgenden Personen in SharePoint Server 2013
<a name="bkmk_CommonTasks"> </a>

In Tabelle 2 sind allgemeine Programmieraufgaben für folgende Personen und die Elemente, mit denen Sie diese ausführen. Elemente werden aus der .NET-Clientobjektmodell (CSOM), JavaScript-Objektmodell (JSOM), REST-Dienst und Serverobjektmodell (SSOM).
  
    
    

> **HINWEIS**
> Die gleichen APIs dienen zum Folgen von Inhalten. Finden Sie unter  [Folgen von Inhalten in SharePoint 2013](follow-content-in-sharepoint-2013.md) eine Übersicht über die Aufgaben zum folgenden Inhalt.
  
    
    

Das Objekt **SocialFollowingManager** konsolidiert die Basisfunktionalität folgende Personen und folgenden Inhalt für den aktuellen Benutzer. Das Objekt **PeopleManager** (siehe Tabelle 3) bietet jedoch einige Funktionen, **SocialFollowingManager** wird nicht bereitgestellt, einschließlich Methoden, um die folgenden Personen Status anderer Benutzer zu erhalten.
  
    
    

**In Tabelle 2. API für allgemeine Aufgaben für die folgenden Personen mithilfe des SocialFollowingManager-Objekts**


|**Aufgabe**|**Elemente**|
|:-----|:-----|
|Erstellen einer Instanz eines Manager-Objekts im Kontext des aktuellen Benutzers <br/> |CSOM:  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.#ctor.aspx) <br/> JSOM: **SocialFollowingManager** <br/> REST:  `<siteUri>/_api/social.following` <br/> SSOM:  [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) <br/> |
|Erstellt eine Instanz eines Manager-Objekts im Kontext eines bestimmten Benutzers <br/> |CSOM: nicht implementiert <br/> JSOM: nicht implementiert <br/> REST: nicht implementiert <br/> SSOM:  [SPSocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.#ctor.aspx) (überladen) <br/> |
|Bitten Sie den aktuellen Benutzer folgende (Stop Folgendes) Starten einer Person <br/> |CSOM:  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) ) <br/> JSOM:  [Führen Sie die](http://msdn.microsoft.com/library/40d14320-27ba-2941-b0e2-be3b5a407c89%28Office.15%29.aspx) ( [StopFollowing](http://msdn.microsoft.com/library/65b0e9be-dc5e-09fb-c57f-7a933de09a4c%28Office.15%29.aspx)) <br/> REST:  [Follow](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Follow) ( [StopFollowing](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_StopFollowing))          **POST** `<siteUri>/_api/social.following/Follow` ( `<siteUri>/_api/social.following/StopFollowing`), und übergeben Sie den Parameter  _actor_ im Textkörper Anforderung <br/> SSOM:  [Follow](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.Follow.aspx) ( [StopFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.StopFollowing.aspx) ) <br/> |
|Hier erfahren Sie, ob der aktuelle Benutzer einen bestimmten Benutzer folgt <br/> |CSOM:  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) <br/> JSOM:  [isFollowed](http://msdn.microsoft.com/library/2c1f62e6-fb75-ad4d-c081-36408b418c21%28Office.15%29.aspx) <br/> REST:  [IsFollowed](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_IsFollowed)          **POST** `<siteUri>/_api/social.following/my/IsFollowed` und übergeben Sie den Parameter _actor_ im Textkörper Anforderung <br/> SSOM:  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.IsFollowed.aspx) <br/> |
|Abrufen Sie die Personen, die den aktuellen Benutzer folgen <br/> |CSOM:  [GetFollowers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowers.aspx) <br/> JSOM:  [getFollowers](http://msdn.microsoft.com/library/ae4a944b-c043-05fb-c74b-101d2ce4a813%28Office.15%29.aspx) <br/> REST:  [nachfolgende Aktivitäten](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followers)          **GET** `<siteUri>/_api/social.following/my/Followers` <br/> SSOM:  [GetFollowers](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowers.aspx) <br/> |
|Abrufen Sie die Personen, die der aktuelle Benutzer folgt <br/> |CSOM:  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) <br/> JSOM:  [getFollowed](http://msdn.microsoft.com/library/432a7cec-6add-fdb1-a79f-a93414ee8cd3%28Office.15%29.aspx) <br/> REST:  [gefolgt](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Followed)          **GET** `<siteUri>/_api/social.following/my/Followed(types=1)` <br/> SSOM:  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowed.aspx) <br/> |
|Rufen Sie die Anzahl der Personen, die der aktuelle Benutzer folgt <br/> |CSOM:  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) <br/> JSOM:  [getFollowedCount](http://msdn.microsoft.com/library/97b53b4f-481a-cf41-1854-8f3ff860b2bb%28Office.15%29.aspx) <br/> REST:  [FollowedCount](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_FollowedCount)          **GET** `<siteUri>/_api/social.following/my/FollowedCount(types=1)` <br/> SSOM:  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetFollowedCount.aspx) <br/> |
|Abrufen der Personen, die der aktuelle Benutzer, denen Sie folgen möchten möglicherweise <br/> |CSOM:  [GetSuggestions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetSuggestions.aspx) <br/> JSOM:  [getSuggestions](http://msdn.microsoft.com/library/95fd9c48-6974-ec08-d3e9-00c2c76f4f79%28Office.15%29.aspx) <br/> REST:  [Vorschläge](following-people-and-content-rest-api-reference-for-sharepoint-2013.md#bk_Suggestions)          **GET** `<siteUri>/_api/social.following/my/Suggestions` <br/> SSOM:  [GetSuggestions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFollowingManager.GetSuggestions.aspx) <br/> |
   
Tabelle 3 werden die **PeopleManager** -Member, um zusätzliche Funktionen zu folgenden Personen verwenden können.
  
    
    

**Tabelle 3. API für allgemeine Aufgaben für die folgenden Personen mithilfe des PeopleManager-Objekts**


|**Aufgabe**|**Elemente**|
|:-----|:-----|
|Hier erfahren Sie, ob die Liste der **Personen, die ich Folge** für den aktuellen Benutzer Öffentliche ist <br/> |CSOM:  [IsMyPeopleListPublic](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.IsMyPeopleListPublic.aspx) <br/> JSOM:  [isMyPeopleListPublic](http://msdn.microsoft.com/library/2ffc73a5-24ce-1ed4-d850-a6fea4c773bb%28Office.15%29.aspx) <br/> REST:  [IsMyPeopleListPublic](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerProperties)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/IsMyPeopleListPublic` <br/> SSOM:  [IsMyPeopleListPublic](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.IsMyPeopleListPublic.aspx) <br/> |
|Hier erfahren Sie, ob eine Person der aktuellen Benutzer folgt <br/> |CSOM:  [AmIFollowedBy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.AmIFollowedBy.aspx) <br/> JSOM:  [amIFollowedBy](http://msdn.microsoft.com/library/3641c469-0063-054d-355d-e56697cb08ae%28Office.15%29.aspx) <br/> REST:  [AmIFollowedBy](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerAmIFollowedBy)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/AmIFollowedBy(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [AmIFollowedBy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.AmIFollowedBy.aspx) <br/> |
|Abrufen Sie die Personen, die ein bestimmter Benutzer folgt <br/> |CSOM:  [GetPeopleFollowedBy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetPeopleFollowedBy.aspx) <br/> JSOM:  [getPeopleFollowedBy](http://msdn.microsoft.com/library/e781c0fa-b14a-40ef-976b-b1c6c82beb89%28Office.15%29.aspx) <br/> REST:  [GetPeopleFollowedBy](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetPeopleFollowedBy)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/GetPeopleFollowedBy(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetPeopleFollowedBy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetPeopleFollowedBy.aspx) <br/> |
|Abrufen Sie die Personen, die einen bestimmten Benutzer folgen <br/> |CSOM:  [GetFollowersFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetFollowersFor.aspx) <br/> JSOM:  [getFollowersFor](http://msdn.microsoft.com/library/51ef3b75-42b2-4efb-4441-e088dc7d168e%28Office.15%29.aspx) <br/> REST:  [GetFollowersFor](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerGetFollowersFor)          **GET** `<siteUri>/_api/SP.UserProfiles.PeopleManager/GetFollowersFor(accountName=@v)?@v='domain\\\\user'` <br/> SSOM:  [GetFollowersFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.GetFollowersFor.aspx) <br/> |
|Hier erfahren Sie, ob ein bestimmter Benutzer einen anderen Benutzer folgt. <br/> |CSOM:  [IsFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.IsFollowing.aspx) <br/> JSOM:  [isFollowing](http://msdn.microsoft.com/library/6a5ce6cb-c710-9e19-0cb9-7fae9e013ec8%28Office.15%29.aspx) <br/> REST:  [IsFollowing](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManagerIsFollowing) (statisch)          **GET** `<siteUri>/_api/SP_UserProfiles_PeopleManager_IsFollowing(possibleFollowerAccountName=@v,possibleFolloweeAccountName=@y)?@v='domain\\\\user'&amp;@y='domain\\\\user'` <br/> SSOM:  [IsFollowing](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.IsFollowing.aspx) <br/> |
   

## Funktionsweise von Personen Vorschläge auf SharePoint Online
<a name="bk_PeopleSuggestions"> </a>

Ergebnisse für Personen Vorschläge basieren auf eingerichteten folgenden Personen Aktivität. Wenn ein Benutzer eine Person folgt, die eine gegenseitige nachfolgende mit einer anderen Person umfasst, die der Benutzer nicht bereits folgt Vorschläge angeboten.
  
    
    
Im folgenden-bezogene Informationen wird während des Such-Crawls indiziert. Nach Abschluss eine Durchforstung müssen suchanalyse folgende Informationen und Ausgabe Benutzer Vorschläge dann die durchforstete analysieren. Suchen Sie in der Standardeinstellung Analytics ausgeführt wird einmal pro Tag.
  
    
    
Wenn ein Benutzer auf die Seite **Personen, die ich Folge** öffnet, wird die [PeopleManager.GetMySuggestions()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMySuggestions.aspx) -Methode aufgerufen. [GetMySuggestions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.GetMySuggestions.aspx) sucht nach neuen Vorschläge für den aktuellen Benutzer, der Benutzer Vorschläge in der Datenbank aktualisiert und zeigt die Vorschläge auf der Seite.
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addResources"> </a>


-  [Soziale Funktionen und Zusammenarbeit in SharePoint 2013](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [Erste Schritte bei der Entwicklung mit thematischen Features in SharePoint 2013](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [Folgen von Inhalten in SharePoint 2013](follow-content-in-sharepoint-2013.md)
    
  
-  [Benutzerprofile - REST-API-Referenz](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [Vorgehensweise: führen Sie die Personen mithilfe des clientobjektmodells .NET SharePoint 2013](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: folgen Sie Menschen mit der JavaScript-Objektmodell in SharePoint 2013](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md)
    
  
-  [REST-API-Referenz zum Folgen von Personen und Inhalten für SharePoint 2013](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
