---
title: Authentification, autorisation et sécurité dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8734790c-eb75-4d78-9604-7cc23b33b693
---


# Authentification, autorisation et sécurité dans SharePoint 2013

## Nouveautés concernant l'authentification, l'autorisation et la sécurité dans SharePoint 2013
<a name="SP15_AuthenticationAuthorizationSecurity_WhatsNew"> </a>

Voici quelques-unes des améliorations ajoutées à SharePoint 2013 : 
  
    
    

- Connexion de l'utilisateur
    
  - SharePoint 2013 prend encore en charge les modes d'authentification classique et par revendications. L'authentification par revendications est l'option d'authentification par défaut dans SharePoint 2013. L'authentification en mode classique est obsolète et ne peut être gérée qu'à l'aide de Windows PowerShell. De nombreuses fonctionnalités dans SharePoint 2013 requièrent le mode de revendications. 
    
  
  - La méthode **MigrateUsers** dans SharePoint 2010 est maintenant obsolète et n'est plus recommandée pour effectuer une migration des comptes. Utilisez la nouvelle cmdlet Windows PowerShell appelée `Convert-SPWebApplication`. Pour plus d'informations, voir  [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013](http://technet.microsoft.com/fr-fr/library/gg251985.aspx).
    
  
  - L'enregistrement requis des fournisseurs de revendications a été supprimé. Cependant, vous devez préconfigurer le type de revendications. Vous pouvez choisir les caractères du type de revendications. En outre, l'ordre des types de revendications n'est pas appliqué.
    
  
  - SharePoint 2013 effectue le suivi des cookies **FedAuth** dans le nouveau service distribué de mise en cache de Windows Server AppFabric.
    
  
  - Une journalisation considérable est fournie dans le but de résoudre les problèmes d'authentification. 
    
  
- Authentification des applications et services
    
  - Dans SharePoint 2013, vous avez maintenant la possibilité de créer des applications pour SharePoint. Une Complément SharePoint possède une identité qui lui est propre et est associée à un principal de sécurité, appelé principal d'application. Comme les utilisateurs et les groupes, un principal d'application dispose de certains droits et autorisations. 
    
  
  - Dans SharePoint 2013, le service d'émission de jeton de sécurité (STS) de serveur à serveur fournit des jetons d'accès pour l'authentification de serveur à serveur. Le STS de serveur à serveur permet à des jetons d'accès temporaires d'accéder à d'autres services d'application, tels que Exchange Server 2013, Microsoft Lync 2013 et les applications pour SharePoint 2013.
    
  

## Authentification et autorisation
<a name="SP15_AuthenticationAuthorizationSecurity_AuthenticationAndAuthorization"> </a>

SharePoint 2013 prend en charge la sécurité de l'accès utilisateur aux niveaux du site web, des listes, des dossiers de listes ou bibliothèques et des éléments. La gestion de la sécurité est basée sur les rôles à tous les niveaux, fournissant une gestion de la sécurité cohérente sur la plateforme SharePoint 2013 avec une interface utilisateur cohérente reposant sur des rôles et un modèle objet pour l'affectation d'autorisations sur les objets. En conséquence, la sécurité au niveau des listes, des dossiers ou des éléments implémente le même modèle utilisateur que la sécurité au niveau du site web, ce qui facilite la gestion des droits d'utilisateurs et des droits de groupes dans un site web. SharePoint 2013 prend également en charge des autorisations uniques sur les dossiers et les éléments contenus dans les listes et les bibliothèques de documents.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur le processus d'autorisation pour les Compléments SharePoint, voir  [Autorisation et authentification des compléments dans SharePoint](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx). 
  
    
    

L'autorisation fait référence au processus par lequel SharePoint 2013 assure la sécurité des sites web, des listes, des dossiers ou des éléments en déterminant quels utilisateurs peuvent effectuer des actions spécifiques sur un objet donné. Le processus d'autorisation suppose que l'utilisateur a déjà été authentifié, ce qui fait référence au processus par lequel SharePoint 2013 identifie l'utilisateur actuel. SharePoint 2013 n'implémente pas son propre système d'authentification ou de gestion des identités, mais repose sur des systèmes externes, quel que soit le type d'authentification (Windows ou autre).
  
    
    
SharePoint 2013 prend en charge les types d'authentification suivants :
  
    
    

- **Windows :** toutes les options d'intégration de l'authentification Internet Information Services (IIS) et Windows, notamment Basic, Digest, Certificates, Windows NT LAN Manager (NTLM) et Kerberos sont prises en charge. L'authentification Windows permet à IIS d'effectuer l'authentification pour SharePoint 2013.
    
    Pour plus d'informations sur la connexion à SharePoint à l'aide du mode Revendications de Windows, voir  [Revendications entrantes : la connexion SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md).
    
    > **IMPORTANTE**
    >  Pour plus d'informations sur la suspension de l'emprunt d'identité, voir [Éviter de suspendre l'emprunt d'identité de l'utilisateur appelant](http://msdn.microsoft.com/fr-fr/library/ff407852.aspx). 
- **Formulaires ASP.NET :** un système de gestion des identités autre que Windows qui utilise le système d'authentification enfichable basé sur des formulaires ASP.NET est pris en charge. Ce mode permet à SharePoint 2013 d'utiliser un large éventail de systèmes de gestion des identités, y compris les groupes ou rôles définis en externe, tels que les systèmes de gestion des identités de base de données légers Lightweight Directory Access Protocol (LDAP). L'authentification des formulaires permet à ASP.NET d'effectuer l'authentification pour SharePoint 2013, ce qui implique souvent une redirection vers une page d'ouverture de session. Dans SharePoint 2013, les formulaires ASP.NET ne sont pris en charge que sous l'authentification par revendications. Un fournisseur de formulaires doit être inscrit dans une application web configurée pour les revendications.
    
    Pour plus d'informations sur la connexion à SharePoint avec l'appartenance ASP.NET et la connexion de rôle passive, voir  [Revendications entrantes : la connexion SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md).
    
  

> **REMARQUE**
> SharePoint 2013 ne prend pas en charge l'utilisation d'un fournisseur d'appartenances qui respecte la casse. Il utilise le stockage SQL ne respectant pas la casse pour tous les utilisateurs de la base de données, indépendamment du fournisseur d'appartenances. 
  
    
    


## Authentification et identité basée sur les revendications
<a name="SP15_AuthenticationAuthorizationSecurity_ClaimsBasedIdentity"> </a>

L'identité basée sur des revendications est un modèle d'identité de SharePoint 2013 qui comprend des fonctionnalités telles que l'authentification des utilisateurs sur des systèmes Windows et non-Windows, les types d'authentification multiples, l'authentification en temps réel renforcée, un jeu plus large de types principaux et la délégation de l'identité des utilisateurs entre les applications.
  
    
    
Lorsqu'un utilisateur se connecte à SharePoint 2013, son jeton est validé, puis utilisé pour la connexion à SharePoint. Le jeton de l'utilisateur est un jeton de sécurité émis par un fournisseur de revendications. Les modes d'accès ou de connexion pris en charge sont les suivants :
  
    
    

- Connexion en mode de revendications Windows (par défaut)
    
  
- Mode de connexion passive SAML
    
  
- Appartenance ASP.NET et connexion de rôle passive
    
  
- Connexion en mode classique Windows (déconseillé dans cette version)
    
  

> **REMARQUE**
> Pour plus d'informations sur la connexion à SharePoint et sur les différents modes de connexion, voir  [Revendications entrantes : la connexion SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md). 
  
    
    

Lorsque vous créez des applications prenant en charge les revendications, l'utilisateur présente une identité à votre application sous la forme d'un jeu de revendications. Une revendication peut être le nom d'utilisateur, une autre une adresse de messagerie. En l'occurrence, l'idée est qu'un système d'identité externe est configuré pour donner à votre application toutes les informations dont elle a besoin sur l'utilisateur avec chaque demande, ainsi qu'une assurance cryptographique que les données d'identité reçues par votre application proviennent d'une source approuvée.
  
    
    
Sous ce modèle, l'authentification unique est beaucoup plus facile à obtenir et votre application n'est plus responsable des aspects suivants :
  
    
    

- authentification des utilisateurs ;
    
  
- stockage des comptes et mots de passe utilisateur ;
    
  
- appel des annuaires d'entreprise pour rechercher les détails de l'identité de l'utilisateur ;
    
  
- intégration aux systèmes d'identité à partir d'autres plateformes ou entreprises.
    
  
Sous ce modèle, votre application prend des décisions au sujet de l'identité en fonction des revendications fournies par l'utilisateur. Cela peut aller d'une simple personnalisation d'application avec le prénom de l'utilisateur à l'octroi à l'utilisateur de l'autorisation d'accéder à des fonctionnalités et à des ressources de plus grande valeur dans votre application.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur l'identité basée sur des revendications et sur les fournisseurs de revendications, voir  [Identité basée sur les revendications et des concepts en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md) et [Fournisseur de revendications dans SharePoint 2013](claims-provider-in-sharepoint-2013.md). 
  
    
    


## Authentification basée sur les formulaires
<a name="SP15_AuthenticationAuthorizationSecurity_FormsBasedAuthentication"> </a>

L'authentification à base de formulaires fournit la gestion des identités personnalisées dans SharePoint 2013 en implémentant un fournisseur d'appartenances, ce qui définit les interfaces permettant d'identifier et d'authentifier les utilisateurs individuels, et un gestionnaire de rôles, qui définit les interfaces pour le regroupement des utilisateurs individuels en groupes logiques ou rôles. Dans SharePoint 2013, un fournisseur d'appartenances doit implémenter la méthode  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) requise. En fonction d'un nom d'utilisateur, le système de fournisseur de rôles retourne une liste de rôles à laquelle l'utilisateur appartient.
  
    
    
Le fournisseur d'appartenances est responsable de la validation des informations d'identification à l'aide de la méthode  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) (désormais requise dans SharePoint 2013). Toutefois, le jeton utilisateur proprement dit est créé par le service d'émission de jeton de sécurité (STS, Security Token Service). Le service STS crée le jeton utilisateur à partir du nom d'utilisateur validé par le fournisseur d'appartenances et de l'ensemble des appartenances au groupe associées au nom d'utilisateur et fournies par le fournisseur d'appartenances.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur STS, voir  [Identité basée sur les revendications et des concepts en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md). 
  
    
    

Le gestionnaire de rôles est facultatif. Si un système d'authentification personnalisé ne prend pas en charge les groupes, un gestionnaire de rôles n'est pas nécessaire. SharePoint 2013 prend en charge un fournisseur d'appartenances et un gestionnaire de rôles par zone d'URL ( [SPUrlZone](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPUrlZone.aspx) ). Les rôles des formulaires ASP.NET ne possèdent aucun droit inhérent qui leur soit associé. À la place, SharePoint 2013 assigne des droits aux rôles de formulaires via ses stratégies et autorisations. Dans SharePoint 2013, l'authentification par formulaire est intégrée au modèle d'identité basée sur des revendications. Si vous avez besoin d'une augmentation supplémentaire pour contourner la limite d'un fournisseur par zone URL, vous pouvez vous en remettre à des fournisseurs de revendications.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur l'identité basée sur des revendications et sur les fournisseurs de revendications, voir  [Identité basée sur les revendications et des concepts en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md) et [Fournisseur de revendications dans SharePoint 2013](claims-provider-in-sharepoint-2013.md). 
  
    
    

Dans la connexion passive avec rôle et appartenance ASP.NET, le client est redirigé vers une page web qui héberge les contrôles de connexion ASP.NET. Une fois que l'objet d'identité représentant une identité utilisateur est créé, SharePoint 2013 le convertit en un objet  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) (qui représente un utilisateur sur la base de revendications).
  
    
    

> **REMARQUE**
> Pour plus d'informations sur la connexion à SharePoint, voir  [Revendications entrantes : la connexion SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md). 
  
    
    

SharePoint 2013 utilise l'interface du fournisseur de rôles ASP.NET standard pour collecter des informations de groupe sur l'utilisateur actuel. Pour l'authentification, les rôles et les groupes représentent la même chose : un moyen de regrouper les utilisateurs dans des jeux logiques pour l'autorisation. Chaque rôle ASP.NET est traité comme un groupe de domaines par SharePoint 2013. 
  
    
    
Pour plus d'informations sur l'infrastructure d'authentification enfichable fournie par ASP.NET, reportez-vous à la documentation dédiée aux développeurs ASP.NET.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur l'authentification basée sur les formulaires, voir  [Authentification par formulaires dans les produits et technologies SharePoint (partie 1) : Introduction](http://msdn.microsoft.com/library/e5efd4d7-b369-49f0-a6f7-431d21daff20%28Office.15%29.aspx). 
  
    
    


## Ressources supplémentaires
<a name="SP15_AuthenticationAuthorizationSecurity_AdditionalResources"> </a>


-  [Autorisation, utilisateurs, groupes et modèle objet dans SharePoint 2013](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [Rôle, héritage, élévation de privilèges et modifications de mot de passe dans SharePoint 2013](role-inheritance-elevation-of-privilege-and-password-changes-in-sharepoint-2013.md)
    
  
-  [Identité basée sur les revendications dans SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Identité basée sur les revendications et des concepts en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [Configuration, administration et ressources en SharePoint 2013](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

