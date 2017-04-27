---
title: Vue d'ensemble des thèmes pour SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ae585dd3-82fe-46bb-ac93-065edc0a16f4
---


# Vue d'ensemble des thèmes pour SharePoint 2013
Découvrez l'utilisation des thèmes dans SharePoint 2013 et la façon dont ils permettent de personnaliser l'apparence des sites.
## Vue d'ensemble des thèmes
<a name="section1"> </a>

Les thèmes offrent un moyen rapide et facile d'appliquer une personnalisation légère à un site SharePoint 2013. Un thème permet au propriétaire d'un site ou à un utilisateur qui dispose de droits de conception de personnaliser un site en modifiant la mise en page, la palette de couleurs, le jeu de polices et l'image d'arrière-plan.
  
    
    
L'utilisation des thèmes dans SharePoint 2013 a été repensée pour simplifier le processus de personnalisation des sites. L'interface utilisateur des thèmes a été reconçue et un ensemble de nouveaux formats de fichier liés aux thèmes a été ajouté. L'Assistant **Modifier l'apparence** représente le point d'entrée de l'expérience des thèmes, qui vous permet de modifier l'apparence de votre site. Vous pouvez sélectionner la présentation du site. Ensuite, vous pouvez la personnaliser en modifiant la mise en page du site, l'arrière-plan, la palette de couleurs ou le jeu de polices. Vous pouvez afficher un aperçu du site avant d'appliquer la présentation. Pour plus d'informations, voir [Choisir un thème pour votre site de publication](http://office.microsoft.com/fr-fr/office365-sharepoint-online-enterprise-help/choose-a-theme-for-your-publishing-site-HA102891580.aspx) sur Office.com.
  
    
    

> **REMARQUE**
> Les thèmes créés dans SharePoint 2010 ne peuvent pas être utilisés sur les sites SharePoint 2013. Cependant, les thèmes créés dans SharePoint 2010 peuvent toujours être utilisés sur les collections de sites qui n'ont pas été mises à niveau ou sur celles qui utilisent la version 2010 de l'expérience. 
  
    
    


## Composants d'utilisation des thèmes
<a name="section2"> </a>

L'expérience d'utilisation des thèmes comprend les éléments suivants :
  
    
    
 **Palette de couleurs** Une palette de couleurs, ou un jeu de couleurs, définit la combinaison des couleurs utilisées dans un site. Trente-deux palettes de couleurs sont installées avec SharePoint 2013. Elles sont disponibles pour les utilisateurs lorsqu'ils choisissent de modifier une présentation dans la bibliothèque de présentations.
  
    
    
Les palettes de couleurs sont des fichiers XML (fichiers .spcolor). Elles sont stockées dans la galerie de thèmes du site racine de la collection de sites, dans le dossier **15** (http:// _SiteCollectionName_/_catalogs/ theme/15/).
  
    
    
 **Jeu de polices** Un jeu de polices définit les polices utilisées dans un site. Sept jeux de polices sont inclus dans SharePoint 2013. Ils sont disponibles pour les utilisateurs lorsqu'ils choisissent de modifier une présentation dans la bibliothèque de présentations.
  
    
    
Les jeux de polices sont des fichiers XML (fichiers .spfont). Ils sont stockés dans la galerie de thèmes du site racine de la collection de sites, dans le dossier **15** (http:// _SiteCollectionName_/_catalogs/theme/15/).
  
    
    
 **Image d'arrière-plan** Image d'arrière-plan utilisée sur le site.
  
    
    
 **Page maître** Une page maître définit le chrome (éléments de structure partagés) d'un site. L'expérience de thème permet aux utilisateurs de sélectionner la page maître à appliquer à un site.
  
    
    
 **Aperçu de page maître** Un aperçu de page maître permet d'afficher une image d'aperçu des composants de thème sélectionnés. Chaque page maître doit avoir un fichier d'aperçu de page maître correspondant afin que cette dernière soit disponible dans l'expérience de thème.
  
    
    
Les fichiers d'aperçu de page maître (fichiers .preview) sont stockés dans la galerie de pages maîtres du site (http:// _SiteName_/_catalogs/masterpage/).
  
    
    
 **Présentation composée** Une présentation, ou apparence, composée correspond à la palette de couleurs, au jeu de polices, à l'image d'arrière-plan et à la page maître qui déterminent l'apparence d'un site. La présentation et le thème peuvent être utilisés alternativement pour décrire l'apparence globale d'un site.
  
    
    
L'expérience de thème utilise la liste Présentations composées pour déterminer les présentations disponibles. Vous pouvez créer des présentations supplémentaires en créant des éléments de liste dans la liste Présentations composées. Pour accéder à cette liste, sur la page **Paramètres du site**, sous **Galeries du concepteur web**, sélectionnez **Présentations composées**.
  
    
    
 **Modifier l'apparence** L'Assistant **Modifier l'apparence** représente le point d'entrée de l'expérience de thème, qui permet aux utilisateurs de modifier l'apparence de leur site. Pour accéder à l'Assistant **Modifier l'apparence**, sélectionnez l'icône **Paramètres**, puis choisissez **Modifier l'apparence**.
  
    
    
 **Bibliothèque de présentations** La bibliothèque de présentations correspond à la première page de l'Assistant **Modifier l'apparence**. Elle présente une vue miniature des présentations disponibles.
  
    
    

## Utilisation des thèmes
<a name="section3"> </a>

SharePoint 2013 inclut des thèmes préinstallés (aussi appelés « présentations » ou « apparences composées »). Vous pouvez utiliser les thèmes préinstallés ou créer des thèmes personnalisés.
  
    
    

### Thèmes préinstallés

L'expérience d'utilisation des thèmes permet aux utilisateurs de personnaliser les thèmes préinstallés en modifiant les couleurs, les polices, la mise en page ou l'image d'arrière-plan. Vous n'avez pas besoin de créer des thèmes personnalisés, à moins que vous vouliez des jeux de polices ou des palettes de couleurs supplémentaires.
  
    
    
Lors de la modification d'un thème préinstallé, un nouveau thème nommé Actuel est créé automatiquement une fois que les modifications du thème sont appliquées. Il n'y a qu'un thème actuel par site. SharePoint 2013 ne permet pas à l'utilisateur d'enregistrer les thèmes à partir de l'interface utilisateur. Si vous modifiez un thème préinstallé, appliquez les modifications (en créant un nouveau thème nommé Actuel), puis modifiez un deuxième thème préinstallé ; le deuxième thème préinstallé devient le thème Actuel lorsque les paramètres sont appliqués. Pour enregistrer un thème modifié, vous pouvez créer un élément de liste dans la liste Présentations composées qui contient les mêmes page maître, palette de couleurs, jeu de polices et URL d'image d'arrière-plan que le thème modifié (le thème modifié est répertorié en tant que thème Actuel dans la liste Présentations composées).
  
    
    

### Thèmes personnalisés

Vous pouvez créer des thèmes personnalisés en créant des palettes de couleurs et des jeux de polices supplémentaires, que vous chargez dans la galerie de thèmes. Les nouveaux jeux de polices et palettes de couleurs sont dès lors disponibles dans l'interface de thèmes ou lorsque vous voulez appliquer un thème par programmation. De la même manière, si vous souhaitez disposer de modèles de mise en page de site supplémentaires, vous pouvez charger des pages maîtres supplémentaires et les fichiers d'aperçu correspondants dans la galerie de pages maîtres.
  
    
    
Vous pouvez créer de nouvelles présentations en créant des éléments dans la liste Présentations composées. Vous pouvez créer un élément de liste et spécifier la page maître, la palette de couleurs, le jeu de polices et l'image d'arrière-plan de la nouvelle présentation.
  
    
    

## Ressources supplémentaires
<a name="section4"> </a>


-  [Fonctionnalités de personnalisation et la conception de 2013 le gestionnaire de conception SharePoint](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  
-  [Comment créer un fichier d'aperçu de page maître dans SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [Procédure : Déployer un thème personnalisé dans SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [Palettes de couleurs et polices dans SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [Blog de l'équipe SharePoint : Affichez votre style avec les thèmes SharePoint](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  

