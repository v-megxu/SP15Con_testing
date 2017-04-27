---
title: Utiliser des flux sociaux dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 39f2163e-15cc-43bc-b131-041d5afdcd90
---



# Utiliser des flux sociaux dans SharePoint 2013
En savoir plus sur les tâches de programmation courantes pour utiliser des flux sociaux et des billets de microblog dans SharePoint Server 2013.
## API pour utiliser des flux sociaux dans SharePoint Server 2013
<a name="bkmk_APIversions"> </a>

Dans les batteries de serveurs SharePoint Server 2013 en local, les flux sociaux interactifs sont conçus pour encourager les utilisateurs à partager des informations et rester connectés à d'autres personnes et à du contenu. Vous pouvez consulter de nombreuses fonctionnalités de flux sur la page **Échange de News** du site personnel d'un utilisateur. Les flux contiennent des collections de fils de discussion qui représentent des billets de microblog, des conversations, des mises à jour de statut et d'autres notifications.
  
    
    
SharePoint Server 2013 fournit les API suivantes, que vous pouvez utiliser pour manipuler les flux sociaux par programme :
  
    
    

- Modèles objet client pour le code managé
    
  - Modèle objet client .NET
    
  
  - Modèle objet client Silverlight
    
  
  - Modèle objet client mobile
    
  
- Modèle objet JavaScript
    
  
- Service REST (Representational State Transfer)
    
  
- Modèle objet serveur
    
  
Il est vivement recommandé d'utiliser des API clientes quand vous le pouvez pour le développement SharePoint 2013. Les API clientes comprennent les modèles objet client, le modèle objet JavaScript et le service REST. Pour plus d'informations sur les API proposées dans SharePoint 2013 et pour savoir quand les utiliser, voir  [Choisir l'ensemble d'API approprié dans SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    
Chaque API inclut un objet gestionnaire que vous utilisez pour effectuer les tâches principales liées au flux. Le tableau 1 répertorie les objets gestionnaire et autres objets clés (ou ressources REST) inclus dans les API, ainsi que la bibliothèque de classes (ou URI de point de terminaison) où vous pouvez les trouver.
  
    
    

> **REMARQUE**
> Les modèles objet client Silverlight et mobile ne sont pas mentionnés de manière explicite dans les tableaux 1 et 2, car ils fournissent les mêmes fonctionnalités de base que le modèle objet client .NET et utilisent les mêmes signatures. Le modèle objet client Silverlight est défini dans Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll et le modèle objet client mobile est défini dans Microsoft.SharePoint.Client.UserProfiles.Phone.dll. 
  
    
    


**Tableau 1. API SharePoint 2013 permettant d'utiliser les profils utilisateur par programmation**

|||
|:-----|:-----|
|Modèle objet client .NET  <br/> Voir :  [Comment : créer et supprimer des messages et de récupérer le flux de mise en réseau à l'aide du modèle objet de client .NET en SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md) <br/> |Objet Gestionnaire :            [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) <br/> Espace de noms principal :            [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) <br/> Autres objets clés :            [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) , [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) , [SocialPost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPost.aspx) , [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) , [SocialFeedOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedOptions.aspx) , [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) <br/> Bibliothèque de classes :           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|Modèle objet JavaScript  <br/> Voir  [Comment : créer et supprimer des publications et récupérer le flux social en utilisant le modèle d'objet JavaScript dans SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md) <br/> |Objet Gestionnaire :            [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) <br/> Espace de noms principal :            [SP.Social](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) <br/> Autres objets clés :            [SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx),  [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx),  [SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx),  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx),  [SocialFeedOptions](http://msdn.microsoft.com/library/65caf283-6e7a-50dc-ef8e-a4e12bd237ac%28Office.15%29.aspx),  [SocialActor](http://msdn.microsoft.com/library/4e369fd5-b9b0-9804-957e-b3e39c559cd4%28Office.15%29.aspx) <br/> Bibliothèque de classes :           SP.UserProfiles.js  <br/> |
|Service REST  <br/> Voir  [Comment : en savoir plus lire et écrire dans le flux social en utilisant le service reste dans SharePoint 2013](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md) <br/> |Ressource Gestionnaire :            [social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md) (SocialRestFeedManager) <br/> Espace de noms principal (OData) :           **SP.Social** <br/> Autres ressources clés :           SocialFeed,  [SocialRestFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestFeed), SocialThread,  [SocialRestThread](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestThread), SocialPost, SocialPostCreationData,  [SocialRestPostCreationData](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestPostCreationData),  [SocialFeedOptions](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialFeedOptions), SocialActor,  [SociaRestActor](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_SocialRestActor) <br/> Point d'accès :            `<siteUri>/_api/social.feed` <br/> |
|Modèle objet serveur  <br/> > **REMARQUE**> Le code utilisant le modèle objet Serveur pour accéder aux flux de données et s'exécuter à distance doit utiliser un objet  [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) .          
|Objet Gestionnaire :            [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.aspx) <br/> Espace de noms principal :            [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) <br/> Autres objets clés :            [SPSocialFeed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeed.aspx) , [SPSocialThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialThread.aspx) , [SPSocialPost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPost.aspx) , [SPSocialFeedOptions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedOptions.aspx) , [SPSocialActor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialActor.aspx) <br/> Bibliothèque de classes :           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   
Si vous utilisez le modèle objet Serveur pour accéder au contenu du flux et que votre code n'est pas en cours d'exécution dans une instance de SharePoint (autrement dit, si votre extension n'est pas installée dans le dossier de mises en page du serveur d'applications), utilisez un objet  [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) dans votre code. L'exemple suivant illustre une des méthodes d'incorporation de l'objet [SPServiceContextScope](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPServiceContextScope.aspx) dans votre code.
  
    
    



```cs

using (SPSite site = new SPSite(<siteURL>))
{
    using (new Microsoft.SharePoint.SPServiceContextScope(SPServiceContext.GetContext(site)))
    {
        // code
    }
}

```


## Tâches de programmation courantes pour l'utilisation des flux sociaux dans SharePoint Server 2013
<a name="bkmk_CommonTasks"> </a>

Le tableau 2 répertorie les tâches de programmation courantes pour l'utilisation des flux sociaux, ainsi que les membres que vous utilisez pour cela. Les membres proviennent du modèle objet client .NET (CSOM), du modèle objet JavaScript (JSOM), du service REST et du modèle objet serveur (SSOM).
  
    
    

**Tableau 2. API pour les tâches de programmation courantes pour l'utilisation des flux sociaux dans SharePoint Server 2013**


|**Tâche**|**Membres**|
|:-----|:-----|
|Créer une instance de l'objet Gestionnaire dans le contexte de l'utilisateur actuel  <br/> |CSOM :  [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.#ctor.aspx) <br/> JSOM :  [SocialFeedManager](http://msdn.microsoft.com/library/f7cf172f-970b-6b71-9eb4-b9a8bb7a0001%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md) <br/> SSOM :  [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.#ctor.aspx) <br/> |
|Créer une instance d'objet Gestionnaire dans le contexte d'un utilisateur particulier  <br/> |CSOM : non implémenté  <br/> JSOM : non implémenté  <br/> REST : non implémenté  <br/> SSOM :  [SPSocialFeedManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.#ctor.aspx) <br/> |
|Obtenir l'utilisateur pour le contexte actuel  <br/> |CSOM :  [Owner](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.Owner.aspx) <br/> JSOM :  [owner](http://msdn.microsoft.com/library/0307264e-d733-77f0-edae-f5468e58d0b7%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed/my](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_my) <br/> SSOM :  [Owner](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.Owner.aspx) <br/> |
|Obtenir le flux de l'utilisateur actuel  <br/> (spécifier le type de flux)  <br/> |CSOM :  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) <br/> JSOM :  [getFeed](http://msdn.microsoft.com/library/cddaccd8-28da-6798-d8cb-4e9351efddf3%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed/my/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeed) (flux personnel), [<Uri_du_site>/_api/social.feed/my/News](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myNews),  [<Uri_du_site>/_api/social.feed/my/TimelineFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myTimelineFeed) ou [<Uri_du_site>/_api/social.feed/my/Likes](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myLikes) <br/> SSOM :  [GetFeed](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeed.aspx) <br/> |
|Obtenir le flux personnel d'un utilisateur particulier  <br/> |CSOM :  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) <br/> JSOM :  [getFeedFor](http://msdn.microsoft.com/library/074ed255-9393-448d-1f7e-720fdeb05f48%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed/actor(item='domain\\\\user')/Feed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> SSOM :  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeedFor.aspx) <br/> |
|Accéder au flux de site d'un site d'équipe  <br/> (spécifiez l'URL du site de flux en tant qu'acteur (par exemple : http://<Collection_de_sites>/<Site_d_équipe>/newsfeed.aspx))  <br/> |CSOM :  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) <br/> JSOM :  [getFeedFor](http://msdn.microsoft.com/library/074ed255-9393-448d-1f7e-720fdeb05f48%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed/actor(item=@v)/Feed?@v='http://<Collection_de_sites>/<Site_d_équipe>/newsfeed.aspx'](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeed) <br/> SSOM :  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFeedFor.aspx) <br/> |
|Publier un billet racine pour le flux de l'utilisateur actuel  <br/> (spécifier **null** pour la cible) <br/> |CSOM :  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM :  [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/my/Feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myFeedPost) puis transmettez le paramètre _restCreationData_ dans le corps de la requête <br/> SSOM :  [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|Publier un billet vers un flux de site  <br/> (spécifiez l'URL du site de flux en tant que cible (par exemple : http://<Collection_de_sites>/Site_d_équipe>/Échange_de_News.aspx))  <br/> |CSOM :  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM :  [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/actor(item=@av)/feed/post/?@av='<Uri_du_site_d_équipe>/newsfeed.aspx'](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_actorFeedPost) puis transmettez le paramètre _restCreationData_ dans le corps de la requête (spécifiez **null** pour le paramètre _ID_)  <br/> SSOM :  [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|Publier une réponse à un billet  <br/> (spécifier l'ID du fil de discussion cible)  <br/> |CSOM :  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) <br/> JSOM :  [createPost](http://msdn.microsoft.com/library/e9ad06a1-831d-8ed0-c76e-8b049f14216f%28Office.15%29.aspx) <br/> RES : **POST** [<Uri_du_site>/_api/social.feed/Post/Reply](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postReply) puis transmettez le paramètre _restCreationData_ dans le corps de la requête <br/> SSOM :  [CreatePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.CreatePost.aspx) <br/> |
|Supprimer un billet, une réponse ou un fil de discussion du flux de l'utilisateur actuel (supprimer un billet racine supprime l'intégralité du discussion)  <br/> |CSOM :  [DeletePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.DeletePost.aspx) <br/> JSOM :  [deletePost](http://msdn.microsoft.com/library/06e03f87-c97d-8634-a02b-f7812eb7beeb%28Office.15%29.aspx) <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/Post/Delete](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postDelete) puis transmettez le paramètre _ID_ dans le corps de la requête <br/> SSOM :  [DeletePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.DeletePost.aspx) <br/> |
|Obtenir un fil de discussion (un billet racine et toutes ses réponses) à partir du flux d'un utilisateur  <br/> |CSOM :  [GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) <br/> JSOM :  [getFullThread](http://msdn.microsoft.com/library/6bb384f3-9474-581f-e18d-e8c4f44c3cdf%28Office.15%29.aspx) <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/Post](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_post), puis transmettez le paramètre  _ID_ dans le corps de la requête <br/> SSOM :  [GetFullThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetFullThread.aspx) <br/> |
|Faire en sorte qu'un utilisateur « aime » (ou « n'aime plus ») un billet ou une réponse  <br/> |CSOM :  [LikePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.LikePost.aspx) ( [UnlikePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.UnlikePost.aspx) ) <br/> JSOM :  [likePost](http://msdn.microsoft.com/library/f401a584-1712-50af-ee08-2999a16388d6%28Office.15%29.aspx) ( [unlikePost](http://msdn.microsoft.com/library/c778bd7d-91e5-15dc-eeb8-b571957e8338%28Office.15%29.aspx))  <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/Post/Like](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLike) ( [<Uri_du_site>/_api/social.feed/Post/Unlike](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlike)), puis transmettez le paramètre  _ID_ dans le corps de la requête <br/> SSOM :  [LikePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.LikePost.aspx) ( [UnlikePost](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.UnlikePost.aspx) ) <br/> |
|Récupérer toutes les personnes ayant « aimé » un billet  <br/> |CSOM :  [GetAllLikers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetAllLikers.aspx) <br/> JSOM :  [getAllLikers](http://msdn.microsoft.com/library/76286fdc-002f-2b13-dc26-53097eb2e3a2%28Office.15%29.aspx) <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/Post/Likers](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLikers), puis transmettez le paramètre  _ID_ dans le corps de la requête <br/> SSOM :  [GetAllLikers](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetAllLikers.aspx) <br/> |
|Obtenir les billets faisant référence à un utilisateur  <br/> |CSOM :  [GetMentions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetMentions.aspx) <br/> JSOM :  [getMentions](http://msdn.microsoft.com/library/78f064c3-5b96-373e-e7f0-8603aedc5ded%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed/my/MentionFeed](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myMentionFeed) <br/> SSOM :  [GetMentions](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetMentions.aspx) <br/> |
|Obtenir le nombre de mentions Non lu de l'utilisateur actuel  <br/> |CSOM :  [GetUnreadMentionCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetUnreadMentionCount.aspx) <br/> JSOM :  [getUnreadMentionCount](http://msdn.microsoft.com/library/18dde16a-f78f-f65e-0644-4eb737b1ae00%28Office.15%29.aspx) <br/> REST : **GET** [<Uri_du_site>/_api/social.feed/my/UnreadMentionCount](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_myUnreadMentionCount) <br/> SSOM :  [GetUnreadMentionCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.GetUnreadMentionCount.aspx) <br/> |
|Verrouiller (ou déverrouiller) un fil de discussion dans le flux de l'utilisateur actuel  <br/> |CSOM :  [LockThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.LockThread.aspx) ( [UnlockThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.UnlockThread.aspx) ) <br/> JSOM :  [lockThread](http://msdn.microsoft.com/library/cc696bb7-e7fd-7a57-5db5-736c3733589e%28Office.15%29.aspx) ( [unlockThread](http://msdn.microsoft.com/library/ee9288d6-ace0-1ec2-ea7c-0ee300b6e1ea%28Office.15%29.aspx))  <br/> REST : **POST** [<Uri_du_site>/_api/social.feed/Post/Lock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postLock) ( [<Uri_du_site>/_api/social.feed/Post/Unlock](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_postUnlock)), puis transmettez le paramètre  _ID_ dans le corps de la requête <br/> SSOM :  [LockThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.LockThread.aspx) ( [UnlockThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialFeedManager.UnlockThread.aspx) ) <br/> |
   

> **REMARQUE**
> La valeur de l'espace réservé  _domain\\\\user_ dans l'exemple REST doit être remplacée par le nom du compte d'un utilisateur réel. Pour savoir comment transmettre un paramètre REST dans le corps d'une requête, voir les [exemples](social-feed-rest-api-reference-for-sharepoint-2013.md#bk_exampleRequests) dans la référence Flux social de l'API REST.
  
    
    

SharePoint Server 2013 ne fournit pas d'API pour personnaliser directement la disposition ou le rendu des billets de microblog. SharePoint Server 2013 fournit uniquement les données et permet aux applications clientes inter-périphériques et multiplateformes de définir des dispositions qui conviennent à leurs facteurs de forme et à leurs besoins. Dans le développement SharePoint 2013, vous pouvez utiliser les remplacements JavaScript dans le rendu côté client, comme décrit dans  [Personnaliser le mode Liste dans les compléments pour SharePoint à l'aide du rendu côté client](http://msdn.microsoft.com/library/8d5cabb2-70d0-46a0-bfe0-9e21f8d67d86%28Office.15%29.aspx).
  
    
    

## Présentation des types de flux dans l'API Mon site social
<a name="bkmk_FeedTypes"> </a>

Les types de flux représentent des coupes de données de flux. Lorsque vous récupérez un flux de l'utilisateur actuel, vous pouvez spécifier un des types de flux suivants :
  
    
    

- **Personal** contient les mises à jour et les billets générés par un utilisateur. Sur Site Mon site, ce flux est visible sur la page **À propos de moi** d'un utilisateur.
    
  
- **News** contient les mises à jour et les billets générés par l'utilisateur actuel, ainsi que par les personnes et le contenu qu'il suit. Lorsque vous récupérez le type de flux **News**, utilisez l'option de tri **ByModifiedTime** pour obtenir les activités les plus récentes (mises en cache) des personnes suivies par l'utilisateur. Sur Site Mon site, ce flux est visible sur la page **Échange de News** d'un utilisateur.
    
  
- **Timeline** contient les mises à jour et les billets générés par l'utilisateur actuel, ainsi que par les personnes et le contenu qu'il suit. **Timeline** est particulièrement utile lorsque vous souhaitez obtenir le flux de données d'un intervalle de temps spécifique ou effectuer un tri avec l'option **ByCreatedTime** (qui inclut le plus grand échantillon de personnes).
    
  
- **Likes** contient des fils de discussion de référence avec une propriété **PostReference** qui représente un billet de l'utilisateur actuel a marqué avec l'attribut **J'aime**.
    
  
- **Everyone** contient les fils de discussion provenant de l'ensemble de l'organisation de l'utilisateur actuel.
    
  
Les modèles objet Serveur, Client et JavaScript fournissent la méthode **GetFeed** que vous pouvez utiliser pour récupérer chaque type de flux de l'utilisateur actuel et la méthode **GetFeedFor** que vous pouvez utiliser pour extraire le type de flux **Personal** (uniquement) d'un utilisateur spécifié. Les deux méthodes utilisent un objet **SocialFeedOptions** en tant que paramètre, qui vous permet de spécifier l'ordre du tri en fonction du temps, de la plage de dates et du nombre maximal de fils de discussion à renvoyer.
  
    
    

> **REMARQUE**
> Le service REST offre des ressources distinctes pour récupérer chaque type de flux, comme illustré dans le tableau 2. 
  
    
    

Si un fil de discussion contient plus de deux réponses, le serveur renvoie un résumé du fil de discussion qui contient uniquement les deux réponses les plus récentes. L'attribut de fil de discussion **IsDigest** est appliqué à ces résumés de fil de discussion. Si vous souhaitez obtenir toutes les réponses d'un fil de discussion, appelez la méthode **GetFullThread** à partir de l'objet Gestionnaire du flux, puis transmettez l'identificateur du fil de discussion.
  
    
    

## Ressources supplémentaires
<a name="bkmk_AdditionalResources"> </a>


- **Articles conceptuels et pratiques**
    
  
-  [Fonctions sociales et de collaboration dans SharePoint 2013](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [Mise en route du développement avec les fonctions sociales dans SharePoint 2013](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [Comment : créer et supprimer des messages et de récupérer le flux de mise en réseau à l'aide du modèle objet de client .NET en SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)
    
  
-  [Comment : créer et supprimer des publications et récupérer le flux social en utilisant le modèle d'objet JavaScript dans SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)
    
  
-  [Comment : en savoir plus lire et écrire dans le flux social en utilisant le service reste dans SharePoint 2013](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [Comment : inclure mentionne, les balises et des liens vers des sites et des documents dans des publications dans SharePoint Server 2013](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
    
  
-  [Comment : incorporer des images, des vidéos et des documents dans les publications de SharePoint Server 2013](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md)
    
  
-  [Threads de référence et les threads de digest dans les flux de mise en réseau SharePoint Server 2013](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  
- **Documentation de référence de l'API**
    
  
-  [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) (modèle objet client)
    
  
-  [Espace de noms SP.Social](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx) (modèle objet JavaScript)
    
  
-  [Référence de l'API REST des flux sociaux pour SharePoint 2013](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [Microsoft.Office.Server.Social](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.aspx) (modèle objet Serveur)
    
  
