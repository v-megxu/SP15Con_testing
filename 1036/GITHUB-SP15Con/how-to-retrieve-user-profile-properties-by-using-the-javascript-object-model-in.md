---
title: Procédure  Récupérer les propriétés de profil utilisateur à l'aide du modèle objet JavaScript dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c6e1ca38-134f-428a-8d21-b8b2615b161b
---


# Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet JavaScript dans SharePoint 2013
Apprenez à récupérer les propriétés utilisateur et les propriétés de profil utilisateur par programmation à l'aide du modèle objet JavaScriptSharePoint 2013.
## Que sont les propriétés utilisateur et les propriétés de profil utilisateur dans SharePoint 2013 ?
<a name="bkmk_WhatIs"> </a>

Les propriétés utilisateur et les propriétés de profil utilisateur fournissent des informations sur les utilisateurs de SharePoint, tels que le nom d'affichage, l'adresse électronique, le titre et d'autres informations personnelles et professionnelles. Dans les API côté client, vous pouvez accéder à ces propriétés à partir de l'objet  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) et de la propriété [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx). La propriété  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) contient toutes les propriétés de profil utilisateur, tandis que l'objet [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) contient les propriétés couramment utilisées (telles que [accountName](http://msdn.microsoft.com/library/ad1551bf-dad8-d54e-880a-8a4388fad44e%28Office.15%29.aspx),  [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx) et [email](http://msdn.microsoft.com/library/74302f73-aaf6-920b-0605-812b0dbf4568%28Office.15%29.aspx)) qui sont plus faciles d'accès.
  
    
    
L'objet  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) comprend les méthodes suivantes que vous pouvez utiliser pour récupérer les propriétés utilisateur et les propriétés de profil utilisateur à l'aide du modèle objet JavaScript :
  
    
    

- Les méthodes  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) et [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) renvoient un objet [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx).
    
  
- Les méthodes  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) et [getUserProfilePropertyFor ](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) renvoient les valeurs des propriétés de profil utilisateur que vous spécifiez.
    
  
Les propriétés de profil utilisateur des API client sont en lecture seule (sauf l'image de profil, que vous pouvez modifier à l'aide de la méthode  [PeopleManager.setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx)). Pour modifier d'autres propriétés de profil utilisateur, vous devez utiliser le modèle objet serveur. Pour plus d'informations sur l'utilisation de profils utilisateur, voir  [Utiliser des profils utilisateur dans SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md).
  
    
    

> **REMARQUE**
> L'objet  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) côté client ne contient pas toutes les propriétés utilisateur de la version côté serveur. Cependant, la version côté client fournit les méthodes permettant de créer un site personnel pour l'utilisateur actuel. Pour le récupérer, utilisez la méthode [ProfileLoader.getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx). 
  
    
    


## Conditions préalables à la configuration de votre environnement de développement pour récupérer les propriétés utilisateur à l'aide du modèle objet JavaScriptSharePoint 2013
<a name="bk_Prereqs"> </a>

Pour créer une page d'application qui utilise le modèle objet JavaScript afin de récupérer les propriétés utilisateur, vous devez disposer des éléments suivants :
  
    
    

- SharePoint Server 2013 avec des profils créés pour l'utilisateur actuel et un utilisateur cible
    
  
- Visual Studio 2012
    
  
- Outils de développement Office pour Visual Studio 2013
    
  
- Autorisations de connexion en mode **Contrôle total** pour accéder à l'application de service de profil utilisateur pour l'utilisateur actuel
    
  

## Créer la page d'application dans Visual Studio 2012
<a name="bk_CreateAppPage"> </a>


1. Sur le serveur exécutant SharePoint Server 2013, ouvrez Visual Studio et sélectionnez **Fichier**, **Nouveau**, puis **Projet**.
    
  
2. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **.NET Framework 4.5** dans la liste déroulante située en haut de la boîte de dialogue.
    
  
3. Dans la liste **Modèles**, développez **Office/SharePoint**, sélectionnez la catégorie **Solutions SharePoint**, puis le modèle **Projet SharePoint 2013**.
    
  
4. Nommez le projet UserProfilesJSOM, puis cliquez sur le bouton **OK**.
    
  
5. Dans la boîte de dialogue **Assistant Personnalisation de SharePoint**, entrez l'URL de votre site SharePoint cible, sélectionnez **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Terminer**.
    
  
6. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet UserProfilesJSOM, puis ajoutez un dossier mappé « Dispositions » SharePoint.
    
  
7. Dans le dossier **Dispositions**, ouvrez le menu contextuel du dossier UserProfilesJSOM, puis ajoutez une nouvelle page d'application SharePoint nommée UserProfiles.aspx.
    
    > **REMARQUE**
      > Les exemples de code figurant dans cet article définissent le code personnalisé dans le balisage de la page, mais n'utilisez pas le fichier de classe code-behind que Visual Studio crée pour la page. 
8. Ouvrez le menu contextuel de la page UserProfiles.aspx, puis sélectionnez **Définir comme élément de démarrage**.
    
  
9. Dans le balisage de la page UserProfiles.aspx, collez le code suivant dans les balises **asp:Content** « Main ». Ce code ajoute un contrôle **span** qui affiche les résultats de la requête, les contrôles **SharePoint:ScriptLink** qui référencent les fichiers de bibliothèque de classe JavaScript SharePoint et les balises **script** qui doivent contenir votre logique personnalisée.
    
  ```HTML
  
<span id="results"></span><br />
<SharePoint:ScriptLink ID="ScriptLink1" name="SP.js" runat="server"
    ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:ScriptLink ID="ScriptLink2" name="SP.UserProfiles.js" runat="server"
    ondemand="false" localizable="false" loadafterui="true" />
<script type="text/javascript">

    // Replace this comment with the code for your scenario.

</script>

  ```

10. Pour ajouter une logique permettant de récupérer les propriétés de profil utilisateur, remplacez le commentaire entre les balises **script** par l'exemple de code que vous trouverez dans l'un des scénarios suivants :
    
  -  [Récupérer les propriétés de profil utilisateur à partir de l'objet PersonProperties et de la propriété userProfileProperties](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_examplePersonPropsObj)
    
  
  -  [Récupérer un jeu de propriétés de profil utilisateur à l'aide de la méthode getUserProfilePropertiesFor](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_exampleGetUPMethod)
    
  
11. Pour tester la page d'application, dans la barre de menus, sélectionnez **Déboguer**, puis **Démarrer le débogage**. Si vous êtes invité à modifier le fichier web.config, cliquez sur le bouton **OK**.
    
  

## Exemple de code : récupérer les propriétés de profil utilisateur à partir de l'objet PersonProperties et de la propriété userProfileProperties dans le modèle objet JavaScriptSharePoint 2013
<a name="bk_examplePersonPropsObj"> </a>

L'exemple de code suivant montre comment obtenir les propriétés de profil utilisateur pour un utilisateur cible en interrogeant l'objet  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) et la propriété [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx). Il montre comment :
  
    
    

- Obtenir l'objet  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx), qui représente l'utilisateur cible, à l'aide la méthode  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx). (Pour obtenir l'objet  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) pour l'utilisateur actuel, utilisez la méthode [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx).)
    
  
- Obtenir une propriété directement à partir de l'objet  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx). Cet exemple permet d'obtenir la propriété  [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx).
    
  
- Obtenir une propriété à partir de la propriété  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) de l'objet [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx). Cet exemple permet d'obtenir la propriété **Department**.
    
  

> **REMARQUE**
> Collez le code suivant entre les balises **script** que vous avez ajoutées au fichier UserProfiles.aspx dans la procédure [Créer la page d'application](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage). Remplacez la valeur d'espace réservé  `domainName\\\\userName` avant d'exécuter le code. (Cet exemple de code n'utilise pas le fichier de classe code-behind.)
  
    
    


```

var personProperties;

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(getUserProperties, 'SP.UserProfiles.js');

function getUserProperties() {

    // Replace the placeholder value with the target user's credentials.
    var targetUser = "domainName\\\\userName";

    // Get the current client context and PeopleManager instance.
    var clientContext = new SP.ClientContext.get_current();
    var peopleManager = new SP.UserProfiles.PeopleManager(clientContext);

    // Get user properties for the target user.
    // To get the PersonProperties object for the current user, use the
    // getMyProperties method.
    personProperties = peopleManager.getPropertiesFor(targetUser);

    // Load the PersonProperties object and send the request.
    clientContext.load(personProperties);
    clientContext.executeQueryAsync(onRequestSuccess, onRequestFail);
}

// This function runs if the executeQueryAsync call succeeds.
function onRequestSuccess() {

    // Get a property directly from the PersonProperties object.
    var messageText = " \\"DisplayName\\" property is "
        + personProperties.get_displayName();

    // Get a property from the UserProfileProperties property.
    messageText += "<br />\\"Department\\" property is "
        + personProperties.get_userProfileProperties()['Department'];
    $get("results").innerHTML = messageText;
}

// This function runs if the executeQueryAsync call fails.
function onRequestFail(sender, args) {
    $get("results").innerHTML = "Error: " + args.get_message();
}
```


## Exemple de code : récupérer un jeu de propriétés de profil utilisateur à l'aide de la méthode getUserProfilePropertiesFor dans le modèle objet JavaScriptSharePoint 2013
<a name="bk_exampleGetUPMethod"> </a>

L'exemple de code suivant récupère les valeurs d'un jeu spécifique de propriétés de profil utilisateur pour un utilisateur cible à l'aide de la méthode  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx). Il montre comment :
  
    
    

- Créer un objet  [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx) qui spécifie l'utilisateur cible et les propriétés de profil utilisateur à récupérer. Cet exemple permet d'obtenir les propriétés **PreferredName** et **Department**.
    
  
- Obtenir les valeurs des propriétés spécifiées en utilisant la méthode  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) et en transmettant l'objet [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx). (Pour récupérer la valeur d'une seule propriété de profil utilisateur, utilisez la méthode  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx).)
    
  
- Obtenir les valeurs issues du tableau des valeurs de propriété renvoyé.
    
  

> **REMARQUE**
> Collez le code suivant entre les balises **script** que vous avez ajoutées au fichier UserProfiles.aspx dans la procédure [Créer la page d'application](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage). Remplacez la valeur d'espace réservé  `domainName\\\\userName` avant d'exécuter le code. (Cet exemple de code n'utilise pas le fichier de classe code-behind.)
  
    
    


```

var userProfileProperties;

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(getUserProperties, 'SP.UserProfiles.js');

function getUserProperties() {

    // Replace the placeholder value with the target user's credentials.
    var targetUser = "domainName\\\\userName";

    // Get the current client context and PeopleManager instance.
    var clientContext = new SP.ClientContext.get_current();
    var peopleManager = new SP.UserProfiles.PeopleManager(clientContext);

    // Specify the properties to retrieve and target user for the 
    // UserProfilePropertiesForUser object.
    var profilePropertyNames = ["PreferredName", "Department"];
    var userProfilePropertiesForUser = 
        new SP.UserProfiles.UserProfilePropertiesForUser(
            clientContext,
            targetUser,
            profilePropertyNames);

    // Get user profile properties for the target user.
    // To get the value for only one user profile property, use the
    // getUserProfilePropertyFor method.
    userProfileProperties = peopleManager.getUserProfilePropertiesFor(
        userProfilePropertiesForUser);

    // Load the UserProfilePropertiesForUser object and send the request.
    clientContext.load(userProfilePropertiesForUser);
    clientContext.executeQueryAsync(onRequestSuccess, onRequestFail);
}

// This function runs if the executeQueryAsync call succeeds.
function onRequestSuccess() {
    var messageText = "\\"PreferredName\\" property is " 
        + userProfileProperties[0];
    messageText += "<br />\\"Department\\" property is " 
        + userProfileProperties[1];
    $get("results").innerHTML = messageText;
}

// This function runs if the executeQueryAsync call fails.
function onRequestFail(sender, args) {
    $get("results").innerHTML = "Error: " + args.get_message();
}
```


## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Utiliser des profils utilisateur dans SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet client .NET dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Comment travailler avec les profils utilisateur et les profils d'organisation en utilisant le modèle objet serveur dans SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [SP.UserProfiles Espace de noms (sp.userprofiles)](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx)
    
  

