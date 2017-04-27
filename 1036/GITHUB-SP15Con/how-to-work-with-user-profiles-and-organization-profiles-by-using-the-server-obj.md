---
title: Comment travailler avec les profils utilisateur et les profils d'organisation en utilisant le modèle objet serveur dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 13f16dc3-f652-4fb3-996b-5f2166236d2b
---


# Comment travailler avec les profils utilisateur et les profils d'organisation en utilisant le modèle objet serveur dans SharePoint 2013
Découvrez comment créer, récupérer et modifier des profils utilisateur et des propriétés de profil utilisateur SharePoint 2013 par programmation à l'aide du modèle objet serveur SharePoint 2013.
## Que sont les profils utilisateur dans SharePoint 2013 ?

Dans SharePoint 2013, les profils utilisateur représentent les utilisateurs SharePoint. Les propriétés de profil utilisateur représentent des informations sur les utilisateurs et également sur les propriétés elles-mêmes. Par exemple, les propriétés incluent l'adresse de messagerie ou le nom de compte d'un utilisateur et le type de données d'une propriété. Vous pouvez utiliser le modèle objet serveur pour créer, récupérer et modifier les profils utilisateur, les sous-types de profil et les propriétés de profil par programmation.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur les tâches de programmation courantes permettant de gérer les profils utilisateur et l'API que vous utilisez pour effectuer les tâches, consultez la rubrique  [Utiliser des profils utilisateur dans SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md). 
  
    
    


## Conditions préalables pour configurer votre environnement de développement afin qu'il gère les profils utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_Prereqs"> </a>

Pour créer une application console qui se sert du modèle objet serveur pour gérer les profils utilisateur et les propriétés de profil utilisateur, vous avez besoin des éléments suivants :
  
    
    

- SharePoint Server 2013 avec le profil créé pour l'utilisateur actuel ;
    
  
- les Visual Studio 2012 ;
    
  
- les autorisations pour créer, récupérer et modifier des objets de profil utilisateur. (La création et la modification de profils requiert l'autorisation **Modifier les profils utilisateur**.)
    
  

## Création d'une application console qui fonctionne avec les profils utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_CreateConsoleApp"> </a>


1. Ouvrez Visual Studio et choisissez **Fichier**, **Nouveau**, **Projet**.
    
  
2. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **.NET Framework 4.5** dans la liste déroulante située en haut de la boîte de dialogue.
    
  
3. Dans la liste **Modèles**, choisissez **Windows**, puis choisissez **Application console**.
    
  
4. Nommez le projet UserProfilesSSOM, puis cliquez sur le bouton **OK**.
    
    > **REMARQUE**
      > Assurez-vous que le paramètre **Préférer 32 bits** n'est pas sélectionné dans les propriétés **Générer** du projet.
5. Ajoutez des références aux assemblies suivants :
    
  - Microsoft.Office.Server
    
  
  - Microsoft.Office.Server.UserProfiles
    
  
  - Microsoft.SharePoint
    
  
  - System.Web
    
  
6. Remplacez le contenu de la classe **Program** par l'exemple de code de l'un des scénarios suivants :
    
  -  [Créer un profil utilisateur](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_CreateUP)
    
  
  -  [Créer une propriété de profil utilisateur](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_CreateUPProp)
    
  
  -  [Récupérer et modifier des profils utilisateur](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangeUP)
    
  
  -  [Récupérer et modifier les attributs des propriétés de profil utilisateur](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangePropAttributes)
    
  
  -  [Récupérer et modifier les valeurs des propriétés d'utilisateur](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangePropValues)
    
  
7. Pour tester l'application console, dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage**. Vous pouvez vérifier vos modifications sur la page **Gérer le service de profil** pour l'application de service de profil utilisateur dans l'Administration centrale.
    
  

## Exemple de code : créer des profils utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_CreateUP"> </a>

Dans SharePoint 2013, les profils utilisateur représentent les utilisateurs SharePoint. Les types et sous-types de profil permettent de classer les profils dans des groupes, comme les employés ou les clients. Les types et les sous-types de profil sont utilisés pour définir des propriétés et attributs de profil communs au niveau du sous-type. SharePoint Server inclut un sous-type de profil utilisateur par défaut.
  
    
    
L'exemple de code suivant crée un objet  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) associé au sous-type de profil utilisateur par défaut. Certaines propriétés de profil utilisateur sont remplies automatiquement avec les informations importées à partir du répertoire qui contient les comptes d'utilisateur, comme Services de domaine Active Directory. Pour obtenir un exemple de code qui crée un sous-type personnalisé, voir [ProfileSubtype](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtype.aspx) .
  
    
    

> **REMARQUE**
> Modifiez les valeurs d'espace réservé domain\\\\username etservername avant d'exécuter le code.
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "domain\\\\username" and "servername" with actual values.
            string newAccountName = "domain\\\\username";
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {

                    // Create a user profile that uses the default user profile
                    // subtype.
                    UserProfileManager userProfileMgr = new UserProfileManager(serviceContext);
                    UserProfile userProfile = userProfileMgr.CreateUserProfile(newAccountName);

                    Console.WriteLine("A profile was created for " + userProfile.DisplayName);
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## Exemple de code : créer des propriétés de profil utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_CreateUPProp"> </a>

Les propriétés de profil utilisateur comprennent des informations personnelles et relatives à l'organisation sur les utilisateurs. Vous pouvez créer une propriété de profil personnalisée et l'ajouter au jeu de propriétés de profil SharePoint par défaut.
  
    
    
Une propriété de profil et ses attributs sont représentés par un ensemble d'objets liés : un objet  [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) , un objet [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) et un objet [ProfileSubtypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.aspx) .
  
    
    
L'exemple de code suivant crée un objet  [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) ayant un type de données d'URL (ou éventuellement un objet [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) ayant un type de données de chaîne à valeurs multiples). En outre, il crée un objet [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) et un objet [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) qui définissent la disponibilité, la confidentialité et d'autres paramètres pour la propriété. La propriété [ProfileSubtypeProperty.DefaultPrivacy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.DefaultPrivacy.aspx) contrôle la visibilité des propriétés et d'autres contenus de site Mon site. Pour obtenir une liste complète des types de données possibles pour les valeurs de propriété de profil, voir [PropertyDataType](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyDataType.aspx) .
  
    
    

> **REMARQUE**
> Modifiez la valeur d'espace réservé servername avant d'exécuter le code.
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.Administration;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "servername" with an actual value.
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {
                    ProfilePropertyManager profilePropMgr = new UserProfileConfigManager(serviceContext).ProfilePropertyManager;
                    CorePropertyManager corePropMgr = profilePropMgr.GetCoreProperties();

                    // Create a URL property.
                    CoreProperty coreProp = corePropMgr.Create(false);
                    coreProp.Name = "AppsWebsite";
                    coreProp.DisplayName = "Apps site";
                    coreProp.Type = PropertyDataType.URL;
                    coreProp.Length = 100;
                    corePropMgr.Add(coreProp);

                    //// Create a multivalue property.
                    //// To create this property, comment out the previous
                    //// block of code and uncomment this block of code.
                    //CoreProperty coreProp = corePropMgr.Create(false);
                    //coreProp.Name = "PublishedAppsList";
                    //coreProp.DisplayName = "Published apps";
                    //coreProp.Type = PropertyDataType.StringMultiValue;
                    //coreProp.IsMultivalued = true;
                    //coreProp.Length = 100;
                    //corePropMgr.Add(coreProp);

                    // Create a profile type property and make the core property 
                    // visible in the Details section page.
                    ProfileTypePropertyManager typePropMgr = profilePropMgr.GetProfileTypeProperties(ProfileType.User);
                    ProfileTypeProperty typeProp = typePropMgr.Create(coreProp);
                    typeProp.IsVisibleOnViewer = true;
                    typePropMgr.Add(typeProp);

                    // Create a profile subtype property.
                    ProfileSubtypeManager subtypeMgr = ProfileSubtypeManager.Get(serviceContext);
                    ProfileSubtype subtype = subtypeMgr.GetProfileSubtype(ProfileSubtypeManager.GetDefaultProfileName(ProfileType.User));
                    ProfileSubtypePropertyManager subtypePropMgr = profilePropMgr.GetProfileSubtypeProperties(subtype.Name);
                    ProfileSubtypeProperty subtypeProp = subtypePropMgr.Create(typeProp);
                    subtypeProp.IsUserEditable = true;
                    subtypeProp.DefaultPrivacy = Privacy.Public;
                    subtypeProp.UserOverridePrivacy = true;
                    subtypePropMgr.Add(subtypeProp);

                    Console.WriteLine("The properties were created.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## Exemple de code : récupérer et modifier des profils utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_GetChangeUP"> </a>

L'exemple de code suivant récupère tous les profils utilisateur dans le contexte et modifie la valeur de la propriété  [DisplayName](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.DisplayName.aspx) d'un utilisateur. La plupart des propriétés de profil sont accessibles à l'aide de l'accesseur [UserProfile.Item](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.Item.aspx) .
  
    
    

> **REMARQUE**
> Modifiez les valeurs d'espace réservé domain\\\\username etservername avant d'exécuter le code.
  
    
    


```cs

using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "domain\\\\username" and "servername" with actual values.
            string targetAccountName = "domain\\\\username";
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {

                    // Retrieve and iterate through all of the user profiles in this context.
                    Console.WriteLine("Retrieving user profiles:");
                    UserProfileManager userProfileMgr = new UserProfileManager(serviceContext);
                    IEnumerator userProfiles = userProfileMgr.GetEnumerator();
                    while (userProfiles.MoveNext())
                    {
                        UserProfile userProfile = (UserProfile)userProfiles.Current;
                        Console.WriteLine(userProfile.AccountName);
                    }

                    // Retrieve a specific user profile. Change the value of a user profile property
                    // and save (commit) the change on the server.
                    UserProfile user = userProfileMgr.GetUserProfile(targetAccountName);
                    Console.WriteLine("\\nRetrieving user profile for " + user.DisplayName + ".");
                    user.DisplayName = "Pat";
                    user.Commit();
                    Console.WriteLine("\\nThe user\\'s display name has been changed.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## Exemple de code : récupérer et modifier des attributs des propriétés de profil utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_GetChangePropAttributes"> </a>

L'exemple de code suivant récupère le jeu de propriétés qui représentent une propriété d'utilisateur spécifique et ses attributs, puis modifie l'attribut  [CoreProperty.DisplayName](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.DisplayName.aspx) , l'attribut [ProfileTypeProperty.IsVisibleOnViewer](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.IsVisibleOnViewer.aspx) et l'attribut [ProfileSubtypeProperty.PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) . Ces modifications s'appliquent à l'ensemble du jeu de propriétés. L'attribut [ProfileSubtypeProperty.PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) spécifie si les utilisateurs doivent obligatoirement indiquer une valeur pour la propriété. L'attribut [PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) s'applique aux propriétés de profil utilisateur uniquement.
  
    
    

> **REMARQUE**
> Modifiez la valeur d'espace réservé servername avant d'exécuter le code.
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "servername" with an actual value.
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {
                    ProfilePropertyManager profilePropMgr = new UserProfileConfigManager(serviceContext).ProfilePropertyManager;
                    ProfileSubtypePropertyManager subtypePropMgr = profilePropMgr.GetProfileSubtypeProperties("UserProfile");

                    // Retrieve a specific property set (a profile subtype property and
                    // its associated core and profile type properties).
                    // Changing these properties affects all instances of this property set.
                    ProfileSubtypeProperty subtypeProp = subtypePropMgr.GetPropertyByName(PropertyConstants.Title);
                    CoreProperty coreProp = subtypeProp.CoreProperty;
                    ProfileTypeProperty typeProp = subtypeProp.TypeProperty;

                    Console.WriteLine("Property name: " + coreProp.DisplayName);
                    Console.WriteLine("IsVisibleOnViewer = " + typeProp.IsVisibleOnViewer);
                    Console.WriteLine("PrivacyPolicy = " + subtypeProp.PrivacyPolicy);
                    Console.WriteLine("Press Enter to change the values.");
                    Console.Read();

                    // Change attributes on the properties and save (commit) the changes
                    // on the server.
                    coreProp.DisplayName = "Position";
                    coreProp.Commit();
                    typeProp.IsVisibleOnViewer = true;
                    typeProp.Commit();
                    subtypeProp.PrivacyPolicy = PrivacyPolicy.OptOut;
                    subtypeProp.Commit();
                    Console.WriteLine("The property attributes have been changed.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## Exemple de code : récupérer et modifier les valeurs des propriétés d'utilisateur à l'aide du modèle objet serveur SharePoint 2013
<a name="bkmk_GetChangePropValues"> </a>

L'exemple de code suivant récupère toutes les propriétés de type **UserProfile** et récupère les valeurs de propriété pour un utilisateur spécifique. Ensuite, il modifie la propriété [PictureUrl](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.PictureUrl.aspx) à valeur unique et la propriété [PastProjects](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.PastProjects.aspx) à valeurs multiples. Pour obtenir la liste complète des constantes de nom de propriété de profil, voir [PropertyConstants](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.aspx) .
  
    
    

> **REMARQUE**
> Modifiez les valeurs d'espace réservé domain\\\\username, http://servername/docLib/pic.jpg etservername avant d'exécuter le code.
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "domain\\\\username," "http://servername/docLib/pic.jpg," and "servername" with actual values.
            string accountName = "domain\\\\username";
            string newPictureUrl = "http://servername/docLib/pic.jpg";
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);

                try
                {
                    UserProfileManager userProfileMgr = new UserProfileManager(serviceContext);
                    ProfilePropertyManager profilePropMgr = new UserProfileConfigManager(serviceContext).ProfilePropertyManager;
                   
                    // Retrieve all properties for the "UserProfile" profile subtype,
                    // and retrieve the property values for a specific user.
                    ProfileSubtypePropertyManager subtypePropMgr = profilePropMgr.GetProfileSubtypeProperties("UserProfile");
                    UserProfile userProfile = userProfileMgr.GetUserProfile(accountName);
                    IEnumerator<ProfileSubtypeProperty> userProfileSubtypeProperties = subtypePropMgr.GetEnumerator();
                    while (userProfileSubtypeProperties.MoveNext())
                    {
                        string propName = userProfileSubtypeProperties.Current.Name;
                        ProfileValueCollectionBase values = userProfile.GetProfileValueCollection(propName);
                        if (values.Count > 0)
                        {

                            // Handle multivalue properties.
                            foreach (var value in values)
                            {
                                Console.WriteLine(propName + ": " + value.ToString());
                            }
                        }
                        else
                        {
                            Console.WriteLine(propName + ": ");
                        }
                    }
                    Console.WriteLine("Press Enter to change the values.");
                    Console.Read();

                    // Change the value of a single-value user property.
                    userProfile[PropertyConstants.PictureUrl].Value = newPictureUrl;

                    // Add a value to a multivalue user property.
                    userProfile[PropertyConstants.PastProjects].Add((object)"Team Feed App");
                    userProfile[PropertyConstants.PastProjects].Add((object)"Social Ratings View Web Part");

                    // Save the changes to the server.
                    userProfile.Commit();
                    Console.WriteLine("The property values for the user have been changed.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Utiliser des profils utilisateur dans SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet client .NET dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Procédure : Récupérer les propriétés de profil utilisateur à l'aide du modèle objet JavaScript dans SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx)
    
  

