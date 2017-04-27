---
title: Types de contenus externes dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 11d7adb5-5388-4517-ae03-beb7be1c6981
---


# Types de contenus externes dans SharePoint 2013
Découvrez les fonctions des types de contenu externe et les éléments nécessaires à leur création dans SharePoint 2013.
## Qu'est-ce qu'un type de contenu externe ?
<a name="SP15ectoverview_what"> </a>

Le type de contenu externe est l'un des principaux concepts de Business Connectivity Services (BCS). Utilisés dans tous les services et fonctionnalités proposés par BCS, les types de contenu externe sont des descriptions de métadonnées réutilisables des informations de connectivité et des définitions de données, ainsi que les comportements que vous souhaitez appliquer à une catégorie spécifique de données externes.
  
    
    
Les types de contenu externe vous permettent de gérer et réutiliser les métadonnées et les comportements d'une entité métier, comme un client ou une commande effectuée à partir d'un emplacement central, et permet aux utilisateurs d'interagir efficacement avec les données externes et les processus.
  
    
    
Voici quelques-uns des avantages de l'utilisation de types de contenu externe :
  
    
    

- **Possibilité de réutilisation :** un type de contenu externe est une définition de données réutilisable d'une entité métier. Une fois que vous l'avez créé, vous pouvez l'utiliser avec toutes les fonctionnalités de présentation dans BCS pour fournir une expérience utilisateur enrichie lors des interactions avec les données externes.
    
  
- **Encapsulation des complexités des systèmes externes :** les types de contenu externe permettent aux travailleurs de l'information d'assembler des solutions métiers sans avoir à gérer la complexité des systèmes externes, telles que les informations de connectivité et les interfaces de code. Lorsqu'une personne crée un type de contenu externe, celui-ci est disponible pour tout usage souhaité par les utilisateurs (à condition qu'ils disposent des autorisations pour effectuer ces opérations et accéder aux données externes). En revanche, il n'est pas nécessaire que l'utilisateur connaisse l'emplacement des données externes ou sache comment s'y connecter.
    
  
- **Comportements Office et SharePoint intégrés :** les types de contenu externe fournissent aux services et aux données externes des comportements de type élément Office (tels que des contacts, des tâches, des calendriers dans Outlook, des documents dans Word et des listes dans SharePoint Workspace), des comportements SharePoint (tels que des listes, des composants WebPart et des pages de profil) et des fonctionnalités (telles que la possibilité de rechercher ou de travailler hors connexion). De cette façon, les utilisateurs peuvent travailler dans des environnements familiers sans avoir à rechercher des données ou apprendre à interagir avec des interfaces utilisateur différentes (et propriétaires).
    
  
- **Accès plus sécurisé :** les types de contenu externe sont conformes à la sécurité instaurée par le système externe et SharePoint. Vous pouvez bénéficier d'un contrôle absolu sur les personnes qui accèdent aux différentes données, en configurant la sécurité dans SharePoint.
    
  
- **Maintenance simplifiée :** étant donné que les types de contenu externe peuvent être créés une fois, mais utilisés par de multiples solutions dans différents scénarios, vous pouvez les gérer facilement. Par exemple, vous pouvez gérer leurs autorisations d'accès, la connexion et les définitions de données dans un emplacement central.
    
  
- **Possibilité de recherche de données externes :** vous pouvez utiliser SharePoint Server Search à partir d'un portail intranet pour rechercher des informations sur un type de contenu externe spécifique, comme un client. SharePoint Server Search récupère les données directement à partir du système externe. Par conséquent, les utilisateurs peuvent obtenir des informations nécessaires sans avoir à obtenir d'approbation ni à installer une application distincte.
    
  
- **Possibilité de travail hors connexion :** vous pouvez utiliser les types de contenu externe en mode hors connexion dans Outlook 2013. Business Connectivity Services (BCS) offre des fonctionnalités de travail hors connexion et de cache riche, et prend en charge des opérations basées sur le cache. Les utilisateurs peuvent manipuler des données externes en toute transparence et plus efficacement, même s'ils sont hors connexion ou si la connectivité au serveur est lente, interrompue ou indisponible. Lorsqu'une connexion au serveur est disponible, les opérations de lecture/écriture effectuées sur des entités métiers mises en cache sont synchronisées.
    
  

## Conditions préalables pour l'utilisation de types de contenu externe BCS
<a name="SP15ectoverview_prereq"> </a>

Pour commencer la création de types de contenu externe, vous avec besoin des éléments suivants :
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Outils de développement Office pour Visual Studio 2012
    
    ou
    
  
- SharePoint Designer 2013
    
  
Pour configurer un environnement de développement pour la création de types de contenu externe, voir  [Configurer un environnement de développement général pour SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

## Fonctions des types de contenu externes
<a name="SP15ectoverview_whattodo"> </a>

Lorsque SharePoint est configuré pour communiquer avec le système externe, vous pouvez utiliser les types de contenu externe pour créer les objets suivants et présenter les données sous-jacentes :
  
    
    

- **Listes externes**
    
    Une liste externe permet d'accéder à des données provenant de systèmes externes de la même façon qu'à des données de liste SharePoint. Les listes externes utilisent des types de contenu externe en tant que sources de données. Elles vous permettent d'utiliser les métadonnées déjà définies sur un type de contenu externe pour créer une liste SharePoint contenant des données externes qui s'exécutent comme n'importe quelle liste SharePoint.
    
    En outre, vous pouvez utiliser des listes externes hors connexion dans Outlook 2013. Cela vous permet d'utiliser les données externes comme les types d'élément natif Outlook, tels que les contacts, les tâches et les publications, et d'utiliser les données externes dans les applications clientes Office.
    
    Les listes externes activent la réécriture dans le système externe si celui-ci le permet, et s'il est modélisé en conséquence par le type de contenu externe. Cela implique que les utilisateurs peuvent modifier les données externes directement à partir du système. Toutes les modifications qui ont été apportées aux éléments de la liste sont automatiquement synchronisées avec le système externe. En outre, vous pouvez synchroniser et obtenir les données mises à jour du système externe automatiquement en appuyant sur le bouton **Actualiser les données** dans la liste.
    
  
- **Colonnes de données externes**
    
    La colonne de données externes permet aux utilisateurs d'ajouter des données de types de contenu externe à des listes SharePoint standard. Comme pour une liste externe, les colonnes de données externes peuvent afficher des données à partir de n'importe quel type de contenu externe modélisé dans Business Connectivity Services (BCS).
    
  
- **Composants WebPart de données métiers**
    
    SharePoint 2013 fournit cinq composants WebPart différents pour l'utilisation de données externes : liste de données métiers, élément de données métiers, générateur d'éléments de données métiers, liste liée aux données métiers et actions de données métiers.
    
  
- **Sélecteur de types de contenu externe**
    
    Le sélecteur de types de contenu externe fournit des fonctionnalités de récupération et de résolution à l'utilisateur. Vous pouvez incorporer un sélecteur dans un formulaire ou une page pour les scénarios où un utilisateur doit être en mesure de choisir un type de contenu externe dans la liste des types de contenu externe disponibles. 
    
  
- **Sélecteur d'éléments externes**
    
    Le sélecteur d'éléments externes fournit des fonctionnalités de récupération et de résolution pour les éléments externes sur le serveur et dans les applications Office clientes riches. Vous pouvez incorporer un sélecteur dans un formulaire ou une page pour les scénarios où un utilisateur doit être en mesure de choisir un élément externe, comme un client dans une liste de clients. 
    
  
- **Pages de profil**
    
    Les pages de profil sont des pages SharePoint dans SharePoint 2013 qui affichent les détails d'un élément externe. Comme pour toute autre page de Page de composants WebPart SharePoint, vous pouvez personnaliser cette page pour afficher les détails d'un élément externe.
    
  
- **Applications et pages personnalisées**
    
    Vous pouvez utiliser les options de programmabilité SharePoint 2013, telles que le modèle objet SharePoint, le modèle objet client et les URL REST.
    
  
Le tableau 1 contient des exemples de tâches qui illustrent l'utilisation des types de contenu externe.
  
    
    

**Tableau 1. Tâches de base pour l'utilisation des types de contenu externe**


|**Tâche**|**Description**|
|:-----|:-----|
| [Comment : créer un type de contenu externe d'une source OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |Apprenez à utiliser Visual Studio 2012 pour découvrir une source OData publiée et créer un type de contenu externe réutilisable pour utilisation dans SharePoint 2013Business Connectivity Services (BCS).  <br/> |
| [Comment créer des types de contenu externe pour SQL Server dans SharePoint 2013](how-to-create-external-content-types-for-sql-server-in-sharepoint-2013.md) <br/> |Apprenez à créer un type de contenu externe basé sur une base de données SQL Server.  <br/> |
   

## Ressources supplémentaires
<a name="SP15ectoverview_addres"> </a>


-  [Business Connectivity Services dans SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Comment : créer un type de contenu externe add-de-étendus dans SharePoint 2013](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [Comment créer des types de contenu externe pour SQL Server dans SharePoint 2013](how-to-create-external-content-types-for-sql-server-in-sharepoint-2013.md)
    
  
-  [Prise en main de Business Connectivity Services dans SharePoint 2013](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Nouveautés dans Business Connectivity Services dans SharePoint 2013](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  

