---
title: Nouveautés du développement de sites SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ac1e9891-5ce9-4707-84e5-6e2fc02fda6b
---


# Nouveautés du développement de sites SharePoint 2013
Découvrez le nouveau modèle de création et de publication de sites dans SharePoint 2013 qui vous permet de créer des sites de publication.
## Introduction à la publication de sites pour les concepteurs et les développeurs dans SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_IntroductionToSitePublishing"> </a>

Voici les nouvelles fonctionnalités dans SharePoint 2013 qui prennent en charge le flux de travail de création de sites de gestion de contenu d'entreprise (ECM) pour les sites de publication.
  
    
    

### Modèles de programmation clients pour le développement de sites de publication

Dans SharePoint 2013, vous pouvez utiliser le modèle objet client .NET (CSOM), Silverlight et les modèles de programmation JavaScript pour développer des sites, composants de site, éléments de personnalisation et comportements personnalisés. La plupart des API disponibles pour la programmation de serveur .NET sont disponibles dans les assemblys clients .NET (CSOM), Silverlight, et JavaScript correspondants. Dans certains cas, les API correspondantes sont également disponibles dans les bibliothèques Windows Phone.
  
    
    
Pour en savoir plus, consultez les pages d'accueil de référence afin d'obtenir des sites et du contenu concernant le  [serveur .NET](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx), le  [client .NET](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx) et [JavaScript](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx). Sinon, commencez par la  [page d'accueil de référence](http://msdn.microsoft.com/library/7940ba4e-f6f0-4bc0-b995-ceb2d358ca0d%28Office.15%29.aspx) si vous souhaitez commencer par le haut puis explorer le contenu de chaque modèle de programmation.
  
    
    

### Utilisation des API de publication et de taxonomie avec le nouveau modèle d'application SharePoint

Vous pouvez écrire du code client et du code serveur personnalisé dans les Compléments SharePoint qui étendent la fonctionnalité de publication et de taxonomie SharePoint disponible pour les utilisateurs par le biais de l'interface utilisateur (UI). 
  
    
    
Voici quelques idées pour le développement d'applications qui permettent d'améliorer la publication de sites : les enquêtes, les applications de gestion de compte, la prise en charge du commerce électronique, les applications qui intègrent des fonctionnalités sociales et des données externes dans les sites de publication, les ajouts de contenu externalisé sur vos sites et les applications compléments mobiles.
  
    
    

## Fonctionnalités de création, de conception et de personnalisation
<a name="SP15_WhatsNewSiteDevelopment_AuthoringAndBranding"> </a>

SharePoint 2013 inclut des fonctionnalités et des API que vous pouvez utiliser pour créer, concevoir, personnaliser et étendre votre site, la conception de votre site et vos éléments de personnalisation, ainsi que leurs comportements. 
  
    
    

### Gestionnaire de conception

Dans les versions précédentes de SharePoint, la personnalisation d'un site exigeait une connaissance technique spécifique de certains aspects, comme les espaces réservés de contenu nécessaires sur une page maître ou la façon dont une page maître implémente certaines catégories de styles. SharePoint 2013 introduit le  [Gestionnaire de conception](overview-of-design-manager-in-sharepoint-2013.md) ; il s'agit d'une nouvelle interface qui agit comme un concentrateur central de gestion de tous les aspects de la personnalisation de votre site SharePoint. Vous pouvez trouver le Gestionnaire de conception dans le site de niveau supérieur pour votre collection de sites. Il fait partie du modèle de collection de sites Portail de publication dans SharePoint 2013.
  
    
    
Le Gestionnaire de conception permet une approche étape par étape pour la création d'éléments de conception que vous pouvez utiliser pour personnaliser des sites. Téléchargez des éléments de conception (des images, du code HTML, du code CSS, etc.), puis créez vos pages maîtres et vos mises en page. Vous pouvez obtenir un aperçu de ce à quoi ressemble votre conception soit sur l'éditeur de code côté client, soit sur le serveur pendant la conception. Vous pouvez ajouter des composants SharePoint personnalisés et des éléments du ruban à l'aide de l'interface utilisateur du Gestionnaire de conception. Le Gestionnaire de conception génère des  [extraits](sharepoint-2013-design-manager-snippets.md) de code HTML qui peuvent être utilisés par n'importe quel outil de conception web ; il affiche le code HTML et ignore les balises ASP.NET et SharePoint (tandis que SharePoint affiche uniquement les balises ASP.NET et SharePoint et ignore le code HTML).
  
    
    
Vous pouvez utiliser vos connaissances en HTML, CSS et JavaScript pour concevoir des pages maîtres en HTML et des mises en page HTML dans l'éditeur HTML de votre choix. Pour connecter votre outil de création et de conception préféré à votre site SharePoint,  [mappez un lecteur réseau](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md) puis modifiez le fichier SharePoint comme s'il s'agissait d'un fichier local. Lorsque la conception de votre site est prête, téléchargez le code HTML et les fichiers de prise en charge, puis utilisez le Gestionnaire de conception pour [convertir le fichier HTML en fichier de page maître (.master) ASP.NET](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md). Maintenant,  [appliquez la page maître](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md) à votre site SharePoint. Utilisez le Gestionnaire de conception pour [créer une nouvelle mise en page](how-to-create-a-page-layout-in-sharepoint-2013.md) et la version HTML est automatiquement associée à la page ASP.NET correspondante (fichier .aspx) que SharePoint interprète.
  
    
    
Après avoir converti vos fichiers HTML, vous pouvez utiliser votre éditeur HTML pour continuer à affiner votre conception, prévisualiser vos fichiers et les enregistrer. Chaque fois que vous enregistrez les versions HTML de la page maître ou des fichiers de mise en page, SharePoint 2013 met automatiquement à jour la page maître et les mises en page SharePoint associées pour prendre en compte vos modifications. 
  
    
    
Avec le Gestionnaire de conception, il suffit de modifier les fichiers HTML ; pendant que vous continuez à rédiger des pages maîtres et des mises en page personnalisées en utilisant vos compétences en développement ASP.NET et SharePoint, le Gestionnaire de conception vous permet de concevoir de grands sites sans que vous ayez besoin des connaissances de développeur SharePoint.
  
    
    
Si vous préférez, SharePoint 2013 inclut également des versions HTML de plusieurs pages maîtres et mises en page, que vous pouvez utiliser comme modèles de démarrage. Si vous souhaitez commencer à partir de ces fichiers, créez une copie du fichier HTML (le fichier ASP.NET associé sera pris en charge pour vous), puis modifiez le fichier HTML comme vous le feriez normalement. Vous pouvez également commencer à partir d'un simple modèle de base en utilisant l'option **page maître du modèle minimal**, qui crée automatiquement le fichier .master associé.
  
    
    

### Galerie d'extraits de code

SharePoint 2013 contient de nombreux composants prêts à l'emploi, comme les composants WebPart et les contrôles, que vous pouvez ajouter aux pages de votre site. Par exemple, en insérant un composant SharePoint tel qu'une zone de recherche ou un contrôle de navigation dans votre page maître HTML, vous pouvez créer rapidement et facilement un grand nombre de fonctionnalités dans vos pages.
  
    
    
Sur le ruban, dans le groupe **Galerie d'extraits de code**, vous pouvez sélectionner un composant, configurer ses propriétés et mettre à jour l'extrait, copier l'extrait de code HTML qui est généré et coller cet extrait de code HTML dans votre fichier HTML. L'extrait de code HTML vous donne un aperçu très fidèle de ce composant, à la fois dans l'aperçu côté serveur et dans l'éditeur HTML de votre choix. Après avoir ajouté des composants SharePoint à vos fichiers HTML, vous pouvez utiliser du code CSS pour les personnaliser entièrement. En outre, comme pour toute mise à jour du fichier HTML, après avoir ajouté des composants SharePoint et les avoir personnalisés, les modifications sont automatiquement synchronisées avec la page maître ou la mise en page associée. Les extraits de code HTML sont automatiquement convertis en composants SharePoint.
  
    
    
 Que votre fichier HTML soit une page maître ou une mise en page, la galerie d'extraits de code vous montre les composants dont vous avez besoin. Si vous ne voyez pas l'extrait que vous voulez, vous pouvez créer un extrait de code HTML avec des balises ASP.NET et l'ajouter à votre page maître HTML ou mise en page HTML.
  
    
    
Le Gestionnaire de conception génère des extraits de code HTML qui peuvent être utilisés par n'importe quel outil de conception web : il affiche uniquement le code HTML et ignore les balises ASP.NET et SharePoint. SharePoint affiche uniquement les balises ASP.NET et SharePoint et ignore le code HTML.
  
    
    

### Canaux d'appareils

Dans le Gestionnaire de conception, vous créez des  [canaux des appareils](sharepoint-2013-design-manager-device-channels.md), puis les mappez à des appareils mobiles ou à des navigateurs en utilisant les sous-chaînes de chaque chaîne d'agent utilisateur de l'appareil entrant. Un appareil peut appartenir à plusieurs canaux, de sorte que les canaux peuvent être classés. Par exemple, si vous créez des canaux des appareils pour les « smartphones » et « Windows Phone 8 », vous pouvez classer les canaux afin que les appareils exécutant Windows Phone 8 obtiennent le canal qui leur est spécialement attribué, tandis que tous les autres smartphones obtiennent du contenu en étant associés au canal « smartphones ».
  
    
    
Après avoir défini les canaux, mappez une page maître à chacun d'entre eux. Cette page maître peut faire référence à un fichier CSS autre que la page maître pour le canal par défaut. Toutes les mises en page que vous créez vont fonctionner avec tous les canaux que vous créez ; pour différencier les conceptions de mises en page entre les canaux, utilisez le contrôle **Volet Canaux des appareils**.
  
    
    
Les sites de publication de SharePoint 2013 sont optimisés pour le développement mobile. Vous pouvez utiliser la fonctionnalité de canaux des appareils pour définir des canaux pour un ou plusieurs appareils, ce qui vous permet de maîtriser de façon précise l'expérience des utilisateurs mobile sur votre site. Vous pouvez attribuer une page maître de remplacement à chaque canal en lui donnant un chrome unique. Vous pouvez choisir d'inclure ou d'exclure des parties d'une mise en page dans un canal et d'obtenir un aperçu de la progression de la conception de canal mobile pendant son développement. Les canaux des appareils ont été conçus en gardant à l'esprit le concept d'optimisation du référencement d'un site auprès d'un moteur de recherche (SEO). Vous pouvez les utiliser pour transformer l'apparence des pages existantes afin qu'elles prennent en charge les scénarios mobiles.
  
    
    
Vous pouvez utiliser les canaux pour forcer des rendus spécifiques à apparaître sur des appareils spécifiques ; cela s'appelle le forçage de canaux. Cette méthode est utile pour les scénarios mobiles dans lesquels vous avez défini un rendu optimal pour un appareil mobile spécifique.
  
    
    

### Contrôle du volet Canaux des appareils

Le volet Canaux des appareils est un nouveau contrôle que vous pouvez inclure dans une mise en page pour contrôler le contenu qui est affiché dans tel canal. Le contrôle du volet Canaux des appareils est un conteneur mappé à un ou plusieurs canaux : si un ou plusieurs de ces canaux sont actifs lorsque la page est affichée, la totalité du contenu du volet Canaux des appareils est affichée. Le volet Canaux des appareils vous aide à déterminer quand inclure du contenu spécifique pour des canaux spécifiques.
  
    
    

### Modèles d'affichage
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

Il se peut que vous souhaitiez contrôler le format et la présentation des résultats de la recherche sur votre site web. Vous pouvez le faire en utilisant des modèles d'affichage, qui étendent les options disponibles de personnalisation des résultats de la recherche grâce à l'interface utilisateur, au-delà du mappage des champs prédéfinis que vous souhaitez afficher.
  
    
    
Il se peut que vous souhaitiez utiliser les modèles d'affichage avec les résultats de la recherche dans trois contextes : lorsque vous souhaitez mapper la présentation de la structure globale des résultats de la recherche, lorsque vous voulez afficher des groupes de résultats et lorsque vous voulez montrer l'affichage de chaque résultat, ou élément, dans le jeu de résultats. Il s'agit des modèles de contrôle, de groupe et d'élément, respectivement.
  
    
    
Pour en savoir plus sur les modèles d'affichage, voir  [Modèles d'affichage du gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-display-templates.md).
  
    
    

### Rendus d'image
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

Vous pouvez utiliser les  [rendus d'image](sharepoint-2013-design-manager-image-renditions.md) pour afficher les images téléchargées avec des tailles, largeurs et formats prédéfinis. Vous pouvez créer plusieurs rendus d'un fichier image source, ce qui signifie que vous pouvez définir les caractéristiques d'affichage une fois et les appliquer à n'importe quel nombre d'images. Par exemple, un rendu nommé **Article_image** affiche une image en taille réelle dans un article, alors que le rendu nommé **Thumbnail_small** affiche une version miniature de l'image dans un contexte que vous définissez.
  
    
    
Avant de pouvoir utiliser les rendus d'image, assurez-vous que le cache BLOB est activé sur le serveur. Pour ce faire, vous pouvez accéder aux outils d'administration des services IIS (Internet Information Services). Trouvez-y votre fichier **web.config** et activez le cache BLOB. Actualisez la page et les rendus d'image seront disponibles.
  
    
    

## Métadonnées et navigation gérées dans SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_MetadataAndNavigation"> </a>

Les fonctionnalités de métadonnées gérées d'entreprise (EMM) introduites dans ont été améliorées et étendues à SharePoint 2013 pour de meilleures performances, un accès facilité grâce à l'interface utilisateur et une navigation axée sur la taxonomie appelée navigation gérée.
  
    
    

### Navigation gérée

La navigation gérée est l'alternative taxonomique à la fonctionnalité de navigation SharePoint traditionnelle, appelée navigation structurée, qui est basée sur la structure de SharePoint. La fonctionnalité de  [navigation gérée](managed-navigation-in-sharepoint-2013.md) vous permet de concevoir une navigation de site pilotée par les métadonnées gérées. La navigation gérée crée des URL compatibles SEO dérivées de la structure de navigation gérée. Puisque la navigation gérée est pilotée par la taxonomie, vous pouvez l'utiliser pour concevoir une navigation de site autour de concepts commerciaux importants sans modifier la structure de vos sites ou composants de site.
  
    
    

### Composant WebPart de recherche de contenu
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

Vous pouvez utiliser le  [composant WebPart de recherche de contenu](content-search-web-part-in-sharepoint-2013.md) pour afficher les données de recherche sur vos pages. Il a une fonction semblable à celle du composant WebPart de requête de contenu, mais a des objectifs de conception de sites différents. Les styles du composant WebPart de recherche de contenu sont plus faciles à personnaliser que les styles du composant WebPart de requête de contenu. Le composant WebPart de recherche de contenu renvoie les résultats côté client au format JSON. Sur le serveur, vous pouvez personnaliser les résultats à l'aide des modèles d'affichage.
  
    
    

### Autres améliorations des métadonnées gérées pour les sites
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

SharePoint 2013 présente plusieurs améliorations de l'interface utilisateur et de la fonctionnalité de métadonnées gérées. Pour en savoir plus, consultez  [Métadonnées et navigation gérées dans SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md).
  
    
    

## Contenu de publication dans SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_Publishing"> </a>

SharePoint 2013 offre de nouvelles fonctionnalités de publication de contenu qui vous permettent de développer des sites de publication qui prennent en charge de nouvelles topologies et de nouveaux scénarios, plus souples et plus complexes. 
  
    
    

### Packages de conception

Si vous êtes concepteur de sites web professionnel, vous pouvez créer et tester une conception dans votre propre environnement ou collection de sites avant de tout installer dans d'autres collections de sites. Si vous utilisez la publication intersites pour partager du contenu sur toutes les collections de sites, vous voudrez peut-être créer un package et installer la même conception sur chaque site.
  
    
    
Dans les versions précédentes de SharePoint, si vous vouliez réutiliser une conception, vous deviez utiliser Visual Studio pour créer un package de solution SharePoint (fichier .wsp). Puis, dans le site de destination, vous téléchargiez le package dans la galerie de solutions et vous l'exécutiez. Désormais, dans SharePoint 2013, après avoir terminé la conception de votre site, vous pouvez sélectionner **Exporter un package** dans le Gestionnaire de conception pour exporter un seul fichier .wsp appelé [package de conception](sharepoint-2013-design-manager-design-packages.md). Lorsque vous exportez un package de conception, SharePoint 2013 crée automatiquement un package avec tout le contenu que vous avez ajouté ou modifié dans la Galerie de pages maîtres, la bibliothèque de styles, la galerie Thèmes, la liste de canaux des appareils et les types de contenu Page dans le package de conception. 
  
    
    

> **REMARQUE**
> Un package de conception ne contient pas de pages, de paramètres de navigation ni de magasin de termes. 
  
    
    

Pour les sites web publics Office 365, les packages de conception ne remplacent pas les fichiers existants. L'installation d'un package de conception crée un nouveau dossier dans la galerie de pages maîtres, la galerie Styles et la galerie Thèmes, où les éléments de conception sont isolés. 
  
    
    
Lorsque vous importez un package de conception, les éléments de conception du package remplacent les fichiers existants et sont appliqués en tant que modèle de conception actuel du site. La page maître du système et par défaut, le thème et le code CSS de remplacement du site sont tous définis à partir des fichiers du package de conception. Avec les packages de conception, une conception intégrée dans un environnement peut facilement être appliquée à un autre environnement, distinct.
  
    
    

### Catalogues

La publication de sites SharePoint 2013 présente des catalogues qui vous permettent d'intégrer des listes dans vos sites de publication. Les catalogues permettent au contenu d'être publié dans toutes les collections de sites, les fonctionnalités de publication intersites dépendant des catalogues. Vous pouvez utiliser des catalogues pour réutiliser véritablement le contenu dans tous vos sites et indépendamment de la frontière entre vos sites intranet, vos sites Internet et vos sites extranet. Pour les requêtes de recherche prédéfinies, les catalogues sont signalés dans la recherche. Vous pouvez faire apparaître le contenu stocké dans les catalogues dans toutes les collections de sites en utilisant le [composant WebPart de recherche de contenu](content-search-web-part-in-sharepoint-2013.md). Vous pouvez créer du code personnalisé pour renseigner les catalogues, connecter un catalogue de produits à un site et traiter des pages individuelles avec des mises en page, des composants WebPart et du contenu HTML personnalisés, qui apparaît uniquement dans le contexte défini.
  
    
    

### Contrôles d'affichage côté client

L'ensemble des nouveaux contrôles de SharePoint 2013 sont affichés côté client. En tant que concepteur ou développeur, vous contrôlez la façon dont le contenu s'affiche sur la page et vous pouvez utiliser diverses techniques de conception pour obtenir l'apparence et les comportements que vous souhaitez sur vos pages publiées, à l'aide de fonctionnalités dont le composant WebPart de recherche de contenu et les modèles d'affichage. Les données sont rédigées dans les contrôles, dans un tableau JSON côté client et vous pouvez afficher le contenu à l'aide de JavaScript, de code CSS et de modèles. 
  
    
    

### Publication intersite

Microsoft SharePoint 2013 présente une fonctionnalité de publication intersite qui vous permet de réutiliser le contenu dans de nombreuses collections de sites. Il utilise des fonctionnalités de recherche intégrées pour activer des architectures et des scénarios de publication. La première fois, vous pouvez concevoir des sites qui croisent les batteries de serveurs SharePoint, permettant ainsi à vos sites de « traverser » la frontière entre les espaces intranets et Internet. 
  
    
    
Utilisez la fonctionnalité Pages de rubrique pour personnaliser le contenu de la page de destination qui est publié entre les sites. Utilisez des URL compatibles SEO pour gérer et conserver et maintenir plus facilement la structure du site sur un grand nombre de scénarios, y compris les topologies de sites multilingues complexes.
  
    
    
Pour en savoir plus sur la publication intersites, voir  [Scénario : création de sites SharePoint à l'aide de la publication intersites dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/sharepoint/jj872721). Pour en savoir plus sur les options de développement pour la publication intersites, voir  [Publication dans SharePoint 2013 intersites](cross-site-publishing-in-sharepoint-2013.md).
  
    
    

### Améliorations de l'optimisation du référencement d'un site auprès d'un moteur de recherche

De nombreux utilisateurs de sites commerciaux sont renvoyés vers des sites Internet commerciaux à partir de grands moteurs de recherche comme Bing et ses concurrents mondiaux. SharePoint 2013 inclut des fonctionnalités telles que les URL conviviales, les redirections vers la page d'accueil, les plans de site XML et les propriétés SEO personnalisées qui vous permettent de définir le titre dans le navigateur de manière flexible, ainsi que les mots-clés et les descriptions de balises **<Meta>**, les URL plus faciles à comprendre pour les variantes de sites multilingues.
  
    
    
Dans Office 365, l'infrastructure du site génère un plan de site XML mis à jour pour vous dans les 24 heures après une modification de site. Avec une installation sur site, vous pouvez régler les paramètres d'actualisation de vos plans de site et préciser sur quels moteurs de recherche vous souhaitez que Microsoft effectue un test Ping lorsque nous mettons à jour le plan de site.
  
    
    
Ce que vos amis aiment sur Facebook influence ce que vous voyez dans les résultats de la recherche renvoyés par Bing et d'autres grands moteurs de recherche. Vous pouvez utiliser des API dans les modèles de programmation SharePoint 2013 pour personnaliser la façon dont la recherche est optimisée pour votre site.
  
    
    

### Analyses et recommandations

Vous pouvez suivre l'utilisation des sites de publication et leurs composants en utilisant la fonctionnalité d'analyse SharePoint 2013, qui est entièrement intégrée au moteur de recherche. L'analyse oriente les fonctionnalités de recommandations sur le contenu et injecte des calculs dans l'indice de recherche en tant que propriétés gérées. Les recommandations fournies par l'analyse de la recherche, qui comprennent les pages consultées et les éléments uniques par jour, peuvent influencer la pertinence des résultats de recherche.
  
    
    
L'analyse anonymise les données et les regroupe tous les 15 jours. L'analyse supprime définitivement les événements tous les 15 jours, puis tous les mois après 3 ans. Les listes des affichages sont toujours conservées. Le contenu le moins consulté est effacé avant que l'analyse envoie les données agrégées vers une base de données de création de rapports. Vous pouvez utiliser du code personnalisé pour exporter des données vers Excel à partir de la base de données de création de rapports, personnaliser le poids de l'événement **View** et créer des événements personnalisés, y compris ceux envoyés par JavaScript.
  
    
    

### Variantes et sites multilingues

Vous pouvez utiliser la fonctionnalité de variantes dans SharePoint 2013 pour créer des sites multilingues ou d'autres sites où vous souhaitez modifier la présentation de votre contenu. La fonctionnalité de variantes est limitée à une collection de sites. En d'autres termes, vous pouvez créer des « variantes » pour une langue/un paramètre régional cible d'un site rédigé dans une langue/un paramètre régional source en tant que sites web actuels au sein de la même collection de sites SharePoint. Les variantes prennent en charge les URL conviviales et la possibilité d'exporter ou d'importer du contenu pour sa traduction par un tiers au  [format de fichier XLIFF](the-xliff-interchange-file-format-in-sharepoint-2013.md). Vous pouvez inclure des étiquettes, une page de traduction et de réplication, un ensemble d'éléments de liste (par exemple, les bibliothèques de documents) et la navigation dans vos packages d'exportation. 
  
    
    

## Ressources supplémentaires
<a name="SP15_WhatsNewSiteDevelopment_AdditionalResources"> </a>


-  [Effectuer des opérations de base avec du code de bibliothèque client SharePoint 2013](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [Procédure : effectuer des opérations de base avec du code de bibliothèque JavaScript dans SharePoint 2013](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
-  [Comment personnaliser des mises en page pour un site de catalogue dans SharePoint 2013](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md)
    
  
-  [Comment modifier la page d'aperçu dans le Gestionnaire de conception SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [Procédure : résoudre les erreurs et avertissements lors de l'aperçu d'une page en SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)
    
  
-  [Vue d'ensemble des thèmes pour SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Métadonnées et navigation gérées dans SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md)
    
  
-  [Nouveautés en recherche de SharePoint 2013 pour les développeurs](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

