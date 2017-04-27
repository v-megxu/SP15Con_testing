---
title: Rôle, héritage, élévation de privilèges et modifications de mot de passe dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: a72c6cad-9e3d-4d57-bf26-24cd1ad7f020
---


# Rôle, héritage, élévation de privilèges et modifications de mot de passe dans SharePoint 2013

## Rôles, définitions de rôles et attributions de rôles
<a name="SP15_RoleInheritance_Role"> </a>

Un rôle se compose de deux parties : une définition de rôle et une affectation de rôle. 
  
    
    
La définition de rôle, ou niveau d'autorisation, est la liste des droits associés au rôle. Un droit est une action contrôlable de manière unique au sein d'un site web SharePoint. Par exemple, un utilisateur doté du rôle **Read** peut parcourir les pages du site web et afficher les éléments des listes. Les autorisations des utilisateurs ne sont jamais gérées directement à l'aide des droits. Toutes les autorisations d'utilisateurs et de groupes sont gérées par le biais des rôles. Une définition de rôle est une collection de droits liés à un objet spécifique. La portée des définitions de rôles (par exemple, **Full Control**, **Read**, **Contribute**, **Design** ou **Limited Access**) s'étend au site web et leur signification reste la même partout sur le site web (cette dernière peut toutefois être différente dans différents sites de la même collection). Par ailleurs, les définitions de rôles peuvent être héritées du site web parent, à l'instar des autorisations. 
  
    
    
L'affectation de rôle est la relation entre la définition de rôle, les utilisateurs et les groupes, et l'étendue (par exemple, un utilisateur peut être lecteur sur la liste 1 tandis qu'un autre est lecteur sur la liste 2). La relation exprimée par le biais de l'affectation de rôle est la clé de voûte du système de gestion de la sécurité SharePoint 2013 par les rôles. Toutes les autorisations sont gérées via les rôles ; vous n'affectez jamais des droits directement à un utilisateur. Vous affectez seulement des collections de droits explicites (définitions de rôles) à la fois bien définies et cohérentes. Vous gérez les autorisations uniques en ajoutant ou supprimant des utilisateurs et des groupes des définitions de rôles à travers les affectations de rôles.
  
    
    
L'administrateur du site web peut personnaliser les définitions de rôles par défaut et créer des rôles personnalisés supplémentaires à l'aide de la page Gérer les rôles, qui répertorie les définitions de rôles disponibles dans le site.
  
    
    

## Héritage des définitions de rôles
<a name="SP15_RoleInheritance_RoleDefInheritance"> </a>

SharePoint 2013 prend en charge l'héritage des définitions de rôles de la même manière qu'il prend en charge l'héritage des autorisations. Ainsi, l'interruption d'un héritage de définition de rôle requiert celle de l'héritage des autorisations.
  
    
    
Chaque objet SharePoint peut avoir son propre jeu d'autorisations ou hériter ses autorisations de son conteneur parent. SharePoint 2013 ne prend pas en charge l'héritage partiel, selon lequel un objet hérite de toutes les autorisations de son parent tout en possédant lui-même quelques autorisations qui lui sont propres. Les autorisations sont soit uniques, soit héritées. SharePoint 2013 ne prend pas en charge l'héritage dirigé. Par exemple, un objet peut hériter uniquement de son conteneur parent, et non d'un quelconque autre objet ou conteneur.
  
    
    
Lorsqu'un site web hérite de définitions de rôles, les rôles sont en lecture seule, à l'instar des autorisations en lecture seule d'un site web hérité. L'utilisateur peut, par le biais d'un lien, accéder au site parent qui détient les définitions de rôles uniques. Le paramètre par défaut pour tous les nouveaux sites web, même les sites avec des autorisations uniques, définit l'héritage des définitions de rôles depuis le site web parent. Lorsque les autorisations sont uniques, les définitions de rôles peuvent être rétablies en définitions de rôles héritées ou modifiées comme des définitions de rôles locales.
  
    
    
L'héritage des définitions de rôles dans un site web a un impact sur l'héritage des autorisations, conformément aux règles suivantes :
  
    
    

- Impossible d'hériter d'autorisations à moins d'hériter aussi de définitions de rôles.
    
  
- Impossible de créer des définitions de rôles uniques à moins de créer aussi des autorisations uniques.
    
  
- Impossible de rétablir les définitions de rôles héritées à moins de rétablir toutes les autorisations uniques du site web. Les autorisations existantes dépendent des définitions de rôles.
    
  
- Impossible de rétablir les autorisations héritées à moins de rétablir aussi les définitions de rôles héritées. Les autorisations d'un site web sont toujours liées aux définitions de rôles du site web en question.
    
  

## Gestion des jetons utilisateur
<a name="SP15_RoleInheritance_ManagingUserTokens"> </a>

SharePoint extrait les informations de jeton utilisateur de la base de données SharePoint. Si l'utilisateur n'a jamais consulté le site ou si le jeton de l'utilisateur a été généré plus de 24 heures auparavant, SharePoint génère un nouveau jeton utilisateur en essayant d'actualiser la liste des groupes auxquels appartient l'utilisateur. 
  
    
    
Si le compte d'utilisateur est un compte Windows NT, SharePoint utilise l'interface **AuthZ** pour demander la propriété **TokenGroups** au service d'annuaire Active Directory. Cette opération peut échouer si SharePoint est exécuté en mode extranet et qu'il n'est pas autorisé à demander cette propriété à Active Directory.
  
    
    
Si le compte d'utilisateur est un utilisateur d'appartenance (membership), SharePoint demande tous les rôles auxquels appartient l'utilisateur à **RoleManager** dans ASP.NET. Cette opération peut échouer s'il n'existe pas de fichier .config approprié pour le fichier exécutable en cours.
  
    
    
Si SharePoint ne peut pas obtenir les appartenances de groupe de l'utilisateur auprès d'Active Directory ou avec **<roleManager>**, le jeton nouvellement généré contient uniquement l'identificateur de sécurité unique de l'utilisateur (SID). Aucune exception n'est générée, mais une entrée est écrite dans le journal de serveur ULS. Le nouveau jeton est également écrit dans la base de données SharePoint afin qu'il ne soit pas regénéré dans les 24 heures.
  
    
    
Une fois que SharePoint a obtenu un jeton à jour, auprès de la base de données SharePoint ou en en générant un nouveau, SharePoint définit l'horodatage sur l'heure actuelle, puis le renvoie à l'appelant. Cela garantit que le jeton est à jour pendant 24 heures.
  
    
    
Une fois l'objet  [SPUserToken](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserToken.aspx) renvoyé à l'appelant, il est de la responsabilité de l'appelant de ne pas utiliser le jeton après qu'il a expiré. Vous pouvez écrire un utilitaire d'aide pour savoir quand le jeton expirera en enregistrant l'heure à laquelle vous obtenez le jeton et comparer la différence entre l'heure actuelle et [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) .
  
    
    
Si un jeton ayant expiré est utilisé pour créer un site web SharePoint, une exception est générée. La valeur d'expiration par défaut des jetons est de 24 heures. Cette valeur est accessible via  [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) .
  
    
    

## Élévation de privilèges
<a name="SP15_RoleInheritance_ElevationOfPrivilege"> </a>

L'élévation de privilèges, fonctionnalité ajoutée dans Windows SharePoint Services 3.0, vous permet d'exécuter par programme des actions dans le code à l'aide d'un niveau de privilèges supérieur. La méthode  [SPSecurity.RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) vous permet d'indiquer un délégué qui exécute un sous-ensemble de code dans le contexte d'un compte disposant de privilèges supérieurs à ceux de l'utilisateur actuel.
  
    
    
Voici un exemple d'utilisation standard de **RunWithElevatedPrivileges**.
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    // Do things by assuming the permission of the "system account".
});
```

Souvent, pour exécuter des actions dans SharePoint, vous devez obtenir un nouvel objet  [SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.aspx) afin d'appliquer les modifications. Par exemple :
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    using (SPSite site = new SPSite(web.Site.ID))
    {
       // Do things by assuming the permission of the "system account".
    }
});
```

Bien que l'élévation de privilèges représente une technique efficace pour gérer la sécurité, elle doit être utilisée avec précaution. Vous ne devez pas mettre entre les mains de personnes disposant de privilèges limités des mécanismes directs et non contrôlés pour contourner les autorisations qui leur sont accordées.
  
    
    

> **IMPORTANTE**
> Si la méthode transmise à  [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) inclut des opérations d'écriture, l'appel à [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) doit être précédé d'un appel à [SPUtility.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.ValidateFormDigest.aspx) ou [SPWeb.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.ValidateFormDigest.aspx) .
  
    
    


## Modifications automatiques de mot de passe
<a name="SP15_RoleInheritance_AutomaticPasswordChange"> </a>

La fonctionnalité de modification automatique de mot de passe vous permet de mettre à jour et de déployer des mots de passe sans avoir à exécuter des tâches de mise à jour manuelle de mot de passe sur plusieurs comptes, services et applications web. Elle facilite la gestion des mots de passe dans SharePoint 2013. Vous pouvez utiliser la fonctionnalité de modification automatique de mot de passe afin de déterminer si un mot de passe arrive à expiration et réinitialiser le mot de passe à l'aide d'une chaîne aléatoire longue et à chiffrement fort.
  
    
    

### Compte géré

Pour implémenter la fonctionnalité de modification automatique de mot de passe, vous devez utiliser les comptes gérés. Les comptes gérés améliorent la sécurité et garantissent l'isolation des applications. Avec les comptes gérés, vous pouvez :
  
    
    

- Configurer la fonctionnalité de modification automatique de mot de passe afin de déployer les mots de passe dans tous les services d'une batterie de serveurs.
    
  
- Configurer les applications et les services web SharePoint qui sont exécutés sur des serveurs d'applications dans une batterie de serveurs SharePoint afin qu'ils utilisent différents comptes de domaine.
    
  
- Mapper des comptes gérés à différents services et applications web dans une batterie de serveurs.
    
  
- Créer plusieurs comptes dans les services de domaine Active Directory (AD DS), puis inscrire chacun de ces comptes dans SharePoint.
    
  
Vous pouvez également inscrire les comptes gérés et activer SharePoint 2013 pour contrôler les mots de passe des comptes. Les utilisateurs devront être informés des changements programmés de mot de passe et des interruptions de service associées, mais les comptes utilisés par une batterie de serveurs SharePoint, les applications web et divers services peuvent être automatiquement réinitialisés et déployés au sein de la batterie de serveurs, si nécessaire, en fonction de calendriers de réinitialisation de mot de passe configurés individuellement.
  
    
    
Voici quelques opérations que vous pouvez exécuter à l'aide de la classe  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx) :
  
    
    

- Modifier le mot de passe
    
  
- Définir un calendrier de modification de mot de passe
    
  
- Propager les modifications de mot de passe
    
  
- Déterminer la date de dernière modification d'un mot de passe
    
  
- Appliquer une longueur minimale pour les mots de passe
    
  
Pour plus d'informations sur l'API de comptes gérés, consultez les liens suivants :
  
    
    

-  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx)
    
  
-  [SPManagedAccount.EventProcessingOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventProcessingOptions.aspx)
    
  
-  [SPManagedAccount.EventType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventType.aspx)
    
  

## Ressources supplémentaires
<a name="SP15_RoleInheritance_AdditionalResources"> </a>


-  [Authentification, autorisation et sécurité dans SharePoint 2013](authentication-authorization-and-security-in-sharepoint-2013.md)
    
  
-  [Autorisation, utilisateurs, groupes et modèle objet dans SharePoint 2013](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [Identité basée sur les revendications dans SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Identité basée sur les revendications et des concepts en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [Configuration, administration et ressources en SharePoint 2013](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

