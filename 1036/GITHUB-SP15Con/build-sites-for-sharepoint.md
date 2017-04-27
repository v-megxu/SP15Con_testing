---
title: Créer des sites pour SharePoint
ms.prod: SHAREPOINT
ms.assetid: 3b372a63-7cdf-462a-abb4-750e611e967d
---


# Créer des sites pour SharePoint
Découvrez le nouveau modèle de création et de publication de sites Web dans SharePoint 2013.
## Introduction à la publication de site pour les concepteurs et les développeurs dans SharePoint
<a name="SP15_BuildSitesForSP2013_IntroToSitePublishing"> </a>

SharePoint 2013 présente un modèle de création et de publication de site pour la création de sites de publication. Vous pouvez utiliser les sites de publication pour publier du contenu sur des sites intranet ou Internet. Les sites de publication diffèrent des autres types de sites SharePoint, tels que les sites d'équipe, principalement en raison de leur objectif : de nombreux utilisateurs lisent du contenu de site de publication, mais seulement une partie d'entre eux contribuent au contenu par l'ajout, la mise à jour et la suppression de contenu dans les collections de sites. Ces sites diffèrent des sites d'équipe, dans lesquels plusieurs personnes peuvent collaborer et contribuer au contenu.
  
    
    
Vous pouvez utiliser les fonctionnalités de publication de site SharePoint 2013 pour créer, personnaliser et mettre à jour les sites de publication qui répondent aux besoins spécifiques de l'entreprise. Les concepteurs professionnels qui possèdent des compétences HTML, CSS et JavaScript, de même que les développeurs qui écrivent des applications SharePoint et utilisent un code .NET personnalisé pour créer des sites et des solutions de batterie de serveurs, peuvent utiliser les fonctionnalités de site dans SharePoint 2013 pour gérer toutes les phases du cycle de vie du contenu, y compris les suivantes :
  
    
    

- **Authoring** et réutilisation de contenu de site
    
  
- **Branding** et conception de l'apparence et du comportement de votre site
    
  
- **Managing metadata** et création d'un système de navigation de site basé sur la taxonomie.
    
  
- **Publishing** de contenu en toute simplicité dans la collection de sites actuelle ou publication de contenu sur les collections de sites (s'étendant même au-delà des limites du site Internet et intranet).
    
  
- **Accessibility** permet d'améliorer l'accessibilité de vos sites publiés.
    
  
Si vous souhaitez afficher un résumé des nouveautés pour les concepteurs et les développeurs de publication de sites web dans SharePoint 2013, voir  [Nouveautés du développement de sites SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md).
  
    
    

## Création, conception et personnalisation dans SharePoint
<a name="SP15_BuildSitesForSP2013_AuthoringDesignBranding"> </a>

SharePoint 2013 offre une nouvelle approche de conception de sites web. Le flux de travail de création de contenu est révisé de sorte que vous pouvez créer du contenu intéressant à l'aide de n'importe quel outil de création et de personnalisation. Pour personnaliser votre site sans avoir à écrire du code .NET personnalisé, utilisez le  [gestionnaire de conception](overview-of-design-manager-in-sharepoint-2013.md) pour importer des éléments de conception. Avec le gestionnaire de conception, vous pouvez également créer une page maître basée sur HTML pour définir le chrome partagé par toutes les pages de votre site et créer des mises en page pour concevoir des modèles de pages. Si vous choisissez d'écrire du code personnalisé, vous pouvez utiliser un serveur .NET, un client .NET (OMCS), Silverlight et les bibliothèques JavaScript.
  
    
    
SharePoint 2013 offre également une nouvelle approche de contenu et de création. Le flux de travail de création de contenu est révisé de sorte que vous pouvez créer du contenu intéressant à l'aide de n'importe quel outil de création et de personnalisation. Pour personnaliser votre site sans avoir à écrire du code ASP.NET personnalisé, utilisez le gestionnaire de conception. Vous pouvez importer des éléments de conception et créer une page maître basée sur HTML pour définir les éléments de tramage partagés (chrome) par toutes les pages et mises en page de votre site. Si vous choisissez d'écrire du code personnalisé lors de la personnalisation de votre site, vous pouvez utiliser les bibliothèques de publication et de taxonomie.
  
    
    

## Sites de publication, programmation du modèle objet client et nouveau modèle d'application SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingSites"> </a>

Vous pouvez utiliser le nouveau modèle objet client .NET (CSOM) pour développer des applications SharePoint avec le modèle de complément SharePoint. Vous pouvez utiliser la plupart des API également disponibles pour la programmation de serveur .NET dans les modèles objets clients .NET, qui prennent en charge le client .NET, Silverlight, JavaScript et, dans certains cas, le développement Windows Phone. Voici quelques idées pour le développement des applications pour des sites web qui comprennent des enquêtes, des applications de gestion des comptes, la prise en charge du commerce électronique, l'intégration de fonctionnalités sociales et les données externes dans les sites web de publication, les ajouts de contenu externe et les applications complément mobile.
  
    
    

## Modèle de page pour la publication de sites web
<a name="SP15_BuildSitesForSP2013_PageModel"> </a>

SharePoint 2013 inclut un modèle de page pour les sites web de publication. Le modèle de page comprend des pages maîtres, des mises en page et d'autres composants pour l'affichage de la structure, du contenu, de l'apparence et du comportement de votre site. Pour plus d'informations, voir  [Vue d'ensemble du modèle de page SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Pages maîtres et mises en page
<a name="SP15_BuildSitesForSP2013_MasterAndLayout"> </a>

Une page maître constitue le modèle principal qui définit les éléments structurels partagés de votre site (chrome). Toutes les pages du site partagent ces éléments, lesquels définissent les zones de la page affichant le contenu de mise en page.
  
    
    
Seules les pages individuelles d'un certain type utilisent des mises en page. Elles sont remplies avec des dispositions de champs de page. Ces pages définissent les éléments individuels de la page. Les pages individuelles sont basées sur les mises en page et créées dans votre navigateur web de deux façons : avec du code personnalisé ou par les utilisateurs du site, qui remplissent les champs de la page. Pour en savoir plus sur le modèle de page dans SharePoint 2013, voir  [Vue d'ensemble du modèle de page SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Contrôles d'affichage côté client
<a name="SP15_BuildSitesForSP2013_ClientSideRendering"> </a>

Tous les nouveaux contrôles dans SharePoint 2013 sont affichés. Les données sont écrites sur les contrôles dans un tableau JSON côté client, et vous pouvez afficher le contenu en utilisant JavaScript, CSS et des modèles. En tant que concepteur ou développeur, vous pouvez contrôler la façon dont le contenu est restitué sur la page et utiliser différentes techniques de conception pour obtenir l'apparence et le comportement souhaités sur vos pages publiées à l'aide de fonctionnalités telles que le  [Composant WebPart de recherche de contenu dans SharePoint 2013](content-search-web-part-in-sharepoint-2013.md) et les modèles d'affichage.
  
    
    

## Sites et appareils mobiles
<a name="SP15_BuildSitesForSP2013_SitesAndMobile"> </a>

Les sites web de publication dans SharePoint 2013 sont optimisés pour le développement mobile. Vous pouvez définir des canaux pour différents appareils (canaux d'appareils) et attribuer une page maître alternative pour chaque canal en leur octroyant des éléments structurels uniques, ou chrome. Vous pouvez choisir d'inclure ou d'exclure les parties de n'importe quelle mise en page dans un canal, et prévisualiser la façon dont la conception de canal mobile progresse durant son développement.
  
    
    

## Métadonnées et navigation dans SharePoint
<a name="SP15_BuildSitesForSP2013_MetadataNav"> </a>

Les fonctionnalités de métadonnées gérées introduites dans SharePoint 2013 sont améliorées et étendues dans Microsoft SharePoint Server 2010. Elles contribuent à de meilleures performances, un accès facilité par le biais de l'interface utilisateur et une navigation basée sur la taxonomie, appelée navigation gérée. Vous pouvez utiliser la navigation gérée ou la navigation basée sur la structure du site web SharePoint, appelée navigation de structure, pour créer votre navigation de site. Pour plus d'informations sur la navigation gérée, voir  [Métadonnées et navigation gérées dans SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md) et [Navigation gérée dans SharePoint 2013](managed-navigation-in-sharepoint-2013.md).
  
    
    

## Publication de contenu dans SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingContent"> </a>

SharePoint 2013 offre les nouvelles fonctionnalités de publication de contenu suivantes, qui vous permettent de développer des sites de publication prenant en charge des topologies et scénarios plus flexibles, plus accessibles et plus complexes. 
  
    
    

### Catalogues

SharePoint 2013 introduit des catalogues, que vous pouvez utiliser pour publier du contenu dans des collections de sites. Les fonctionnalités de publication intersite dépendent des catalogues. Vous pouvez les utiliser pour réutiliser le contenu dans vos sites et dans la limite de vos sites intranet et Internet. Pour les requêtes de recherche prédéfinies, les catalogues sont marqués lors de la recherche. Vous pouvez attacher du contenu stocké dans les catalogues à travers les collections de sites en utilisant le  [Composant WebPart de recherche de contenu dans SharePoint 2013](content-search-web-part-in-sharepoint-2013.md).
  
    
    

### Publication intersite

SharePoint 2013 introduit une fonctionnalité de publication intersite pour réutiliser le contenu dans plusieurs collections de sites. Elle emploie des fonctionnalités de recherche intégrées pour permettre la publication de scénarios et d'architectures. Pour la première fois, vous pouvez concevoir des sites traversant les batteries de serveurs SharePoint, leur permettant ainsi d'ignorer la limite entre Internet et intranet. Vous pouvez utiliser CSWP pour afficher les données de recherche publiées sur les sites et collections de sites.
  
    
    

### Variantes et sites multilingues

Vous pouvez utiliser la fonctionnalité de variantes dans SharePoint 2013 pour créer des sites multilingues ou d'autres sites où vous souhaitez modifier la présentation de votre contenu. La fonctionnalité de variantes est limitée à une collection de sites. En d'autres termes, vous pouvez créer des « variantes » pour une langue/un paramètre régional cible d'un site rédigé dans une langue/un paramètre régional source en tant que sites web actuels au sein de la même collection de sites SharePoint. Les variantes prennent en charge les URL conviviales et la possibilité d'exporter ou d'importer du contenu pour sa traduction par un tiers au  [format de fichier XLIFF](the-xliff-interchange-file-format-in-sharepoint-2013.md). Vous pouvez inclure des étiquettes, une page de traduction et de réplication, un ensemble d'éléments de liste (par exemple, les bibliothèques de documents) et la navigation dans vos packages d'exportation.
  
    
    

### Sites accessibles

Vous pouvez utiliser la fonctionnalité de variantes dans SharePoint 2013 pour créer des sites accessibles ou d'autres sites sur lesquels vous souhaitez adapter la présentation de votre contenu pour les utilisateurs présentant de nombreux besoins en matière d'accessibilité. SharePoint 2013 fournit un « mode plus accessible » qui peut être activé en ouvrant une page web SharePoint, puis en appuyant sur la touche TAB jusqu'à ce que vous trouviez le lien « Activer le mode plus accessible ». Cette fonctionnalité recrée la page web en code HTML standard, ce qui peut la rendre plus conviviale pour les lecteurs d'écran. En vous assurant que les utilisateurs peuvent appuyer sur la touche TAB pour accéder à ce lien, vous pouvez créer une version plus accessible de votre page web SharePoint. Cela inclut des menus déroulants JavaScript convertis en listes sous forme de liens hypertextes, ainsi que des objets convertis dans un format HTML simplifié pour permettre aux lecteurs d'écran de comprendre le contenu. 
  
    
    

## Ressources supplémentaires
<a name="SP15_BuildSitesForSP2013_AdditionalResources"> </a>


-  [Optimiser l'accessibilité de site SharePoint](optimize-sharepoint-site-accessibility.md)
    
  
-  [Configurer un environnement de développement général pour SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md)
    
  
-  [Nouveautés du développement de sites SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [Vue d'ensemble de stratégie de télécharger minimal](minimal-download-strategy-overview.md)
    
  
-  [Modifier des composants de SharePoint pour MDS](modify-sharepoint-components-for-mds.md)
    
  
-  [Bibliothèque de classes de serveur Sites et Contenu SharePoint 2013](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)
    
  
-  [Bibliothèque de classes de client Sites et contenu](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx)
    
  

