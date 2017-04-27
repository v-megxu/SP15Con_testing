---
title: Prise en main de Business Connectivity Services dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c6bf3db0-db79-4b13-9834-891d24b2c9e5
---



# Prise en main de Business Connectivity Services dans SharePoint 2013
Découvrez les principes de base des éléments fournis par Business Connectivity Services (BCS) aux développeurs de solutions SharePoint 2013, et la façon de commencer à utiliser BCS dans différents types de solutions.
## Qu'est-ce que Business Connectivity Services ?


|||
|:-----|:-----|
|Business Connectivity Services (BCS) a été introduit dans SharePoint Server 2010 en tant qu'évolution du catalogue de données métiers publié dans Office SharePoint Server 2007. BCS permet à SharePoint 2013 d'utiliser les données hébergées en externe. Les sources possibles peuvent inclure des bases de données, des services web, des services Windows Communication Foundation (WCF), des sources Open Data Protocol (OData) et d'autres données propriétaires accessibles à l'aide d'assemblys .NET personnalisés. [![Configurer](images/mod_icon_getstartbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatDoYouNeed) [![Se mettre au travail](images/mod_icon_dobox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatCanYouDo) [![En savoir plus](images/mod_icon_startbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_LearnMore)|
**Regardez la vidéo : Vue d'ensemble des services OData et Business Connectivity SharePoint 2013**

  
    
    

  
    
    
![Vidéos](images/mod_icon_video.png)
  
    
    

  
    
    

  
    
    
|
   
Dans un espace de travail dynamique, les travailleurs de l'information doivent accéder aux données qui se trouvent dans des logiciels distincts, par exemple :
  
    
    

- Les données structurées qui existent dans les applications d'entreprise de l'organisation, telles que les applications de gestion des ressources client (CRM) et de planification des ressources d'entreprise (ERP).
    
  
- Les données non structurées dans les applications de productivité d'entreprise, telles que celles dans Microsoft Office, dans les applications d'équipe et de collaboration telles que SharePoint, et dans les services Web 2.0 telles que les applications Internet, les wikis, les blogs et les sites de réseaux sociaux.
    
  
Bien que la plupart des employés passent la majeure partie de leur temps de travail dans les applications de productivité (par exemple, l'environnement Microsoft Office), ils ont également besoin d'une façon d'intégrer cet environnement dans les applications d'entreprise et les logiciels et services de collaboration qu'ils utilisent. BCS fournit cette fonctionnalité dans SharePoint 2013.
  
    
    

## Prise en main de Business Connectivity Services
<a name="SP15GettingStartedBCS_WhatDoYouNeed"> </a>

Pour commencer à développer avec BCS, vous avez besoin des éléments suivants :
  
    
    

- SharePoint 2013
    
  
- Visual Studio
    
  
- Outils de développement Office pour Visual Studio 2012
    
    ou
    
  
- SharePoint Designer
    
  
Pour plus d'informations sur la façon de configurer votre environnement de développement, consultez  [Configurer un environnement de développement général pour SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

### Principes de base de Business Connectivity Services

Le tableau suivant met en évidence les concepts fondamentaux que vous avez besoin de connaître pour commencer à développer des solutions BCS.
  
    
    

**Tableau 1. Concepts de base pour comprendre BCS**


|**Article**|**Description**|
|:-----|:-----|
| [Concepts clés du modèle de données d'entité](http://msdn.microsoft.com/fr-fr/library/ee382840.aspx) <br/> |Le modèle de données d'entité (EDM) utilise trois concepts clés pour décrire la structure des données : le type d'entité, le type d'association et la propriété. Il s'agit des concepts les plus importants pour décrire la structure des données dans n'importe quelle implémentation du modèle EDM.  <br/> |
| [Pratiques de sécurité de base pour les applications web](http://msdn.microsoft.com/fr-fr/library/zdh19h94.aspx) <br/> |Le sujet de la création d'une application web sécurisée est vaste. Des recherches sont requises pour comprendre les problèmes de sécurité. Vous devez également vous familiariser avec les fonctionnalités de sécurité du système d'exploitation Windows, .NET Framework et ASP.NET. Enfin, il est essentiel de comprendre la façon d'utiliser ces fonctionnalités de sécurité pour faire face aux menaces.  <br/> |
| [Services de données WCF](http://msdn.microsoft.com/en-us/data/odata.aspx) <br/> |Les services de données WCF, anciennement ADO.NET Data Services, permettent de créer et d'utiliser des services OData pour le web.  <br/> |
| [Open Data Protocol (OData)](http://www.odata.org) <br/> |OData est un protocole standard permettant d'accéder aux données par le biais d'URL. Essentiellement, il repose sur le protocole HTTP pour fournir des fonctions de lecture-écriture à l'aide de verbes HTTP existants.  <br/> |
| [Internet Information Services](http://www.iis.net/) <br/> |Internet Information Services (IIS) est la plateforme sur laquelle SharePoint s'exécute. Vous devez comprendre la façon de créer des sites web, des répertoires virtuels, des services web, des URL, une sécurité web et d'autres technologies associées à IIS.  <br/> |
| [Types de contenus externes dans SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |Les types de contenus externes sont des descriptions des systèmes externes qu'ils représentent. Ils sont réutilisables lorsqu'ils sont importés dans SharePoint et peuvent être utilisés pour créer des solutions complexes sans code à l'aide de SharePoint Designer 2013, Outlook 2013, de composants WebPart, de listes externes et d'applications clientes personnalisées.  <br/> |
| [Commencer à utiliser le modèle objet client avec des données externes dans SharePoint 2013](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md) <br/> |SharePoint 2013 offre la possibilité d'accéder à tous les objets au moyen d'une URL conçue avec soin. BCS a été étendu pour fournir ces mêmes fonctionnalités.  <br/> |
   

## Que pouvez-vous faire avec Business Connectivity Services ?
<a name="SP15GettingStartedBCS_WhatCanYouDo"> </a>

Avec BCS, vous pouvez transférer des informations dans SharePoint à partir de nombreuses sources différentes. Par exemple, vous pouvez transférer des données à partir d'une base de données SQL Server externe, d'un service web traditionnel, d'un service WCF, de systèmes propriétaires et de services OData.
  
    
    

**Tableau 2. Tâches de base pour l'utilisation de Business Connectivity Services**


|**Tâche**|**Description**|
|:-----|:-----|
| [Types de contenus externes dans SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |En savoir plus sur la création de Business Connectivity Services (BCS) types de contenus externes.  <br/> |
| [Comment : créer un type de contenu externe d'une source OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |Accédez aux informations nécessaires pour commencer à créer des types de contenus externes basés sur des sources OData et à utiliser ces données dans SharePoint ou des composants Office.  <br/> |
| [Comment : créer des récepteurs d'événements externe](how-to-create-external-event-receivers.md) <br/> |Découvrez les concepts inhérents à la création de récepteurs d'événements pouvant être attachés à des listes externes et exécutés lorsque les données externes que la liste représente sont mises à jour.  <br/> |
| [Comment : créer un type de contenu externe add-de-étendus dans SharePoint 2013](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md) <br/> |Découvrez comment créer des types de contenus externes qui sont installés ou étendus au niveau de l'application, permettant ainsi aux développeurs de créer des applications riches en données à l'aide de sources de données externes.  <br/> |
| [Comment : utiliser la bibliothèque de code client pour accéder aux données externes dans SharePoint 2013](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |Découvrez comment utiliser le modèle objet client SharePoint 2013 pour utiliser BCS dans SharePoint 2013.  <br/> |
   

## Pour aller plus loin que les principes de base : En savoir plus sur Business Connectivity Services
<a name="SP15GettingStartedBCS_LearnMore"> </a>

Lorsque vous maîtrisez les concepts de base de BCS, vous pouvez utiliser les fonctionnalités plus avancées permettant de créer de nombreux types de solutions puissantes.
  
    
    

**Tableau 3. Concepts avancés dans BCS**


|**Rubrique**|**Description**|
|:-----|:-----|
| [Comment : créer un service de données OData pour une utilisation comme un système externe BCS](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md) <br/> |Découvrez comment créer un service Internet dédié WCF qui utilise OData pour envoyer des notifications à SharePoint 2013 lorsque les données sous-jacentes changent. Ces notifications sont utilisées pour déclencher des événements qui sont attachés à des listes externes.  <br/> |
| [Référence de schéma de modèle BDC pour SharePoint 2013](bdc-model-schema-reference-for-sharepoint-2013.md) <br/> |Trouvez la documentation de référence pour le schéma du modèle BDC.  <br/> |
| [Référence du modèle BCS client objet SharePoint 2013](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |Obtenez un résumé des objets qui sont disponibles pour la création de scripts côté client à l'aide du modèle objet client SharePoint 2013 afin d'accéder aux données externes exposées par Business Connectivity Services (BCS).  <br/> |
| [Référence de l'API REST BCS pour SharePoint 2013](bcs-rest-api-reference-for-sharepoint-2013.md) <br/> |Trouvez des informations de référence pour la construction d'URI REST (Representational State Transfer) permettant d'accéder aux sources OData et de les manipuler.  <br/> |
   

## Ressources supplémentaires
<a name="SP15GettingStartedBCS_LearnMore"> </a>


-  [Business Connectivity Services dans SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Site web Open Data Protocol](http://www.odata.org/)
    
  
-  [Types de contenus externes dans SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [À l'aide de sources d'OData avec les Services Business Connectivity dans SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Des événements externes et les alertes dans SharePoint 2013](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [Ajoutez dans-étendue de types de contenu externe dans SharePoint 2013](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [Commencer à utiliser le modèle objet client avec des données externes dans SharePoint 2013](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
