---
title: Fonctionnalités prises en charge et non prises en charge
ms.prod: OFFICE365
ms.assetid: 6e4acad6-7665-493c-94cc-d38684b2842f
---


# Fonctionnalités prises en charge et non prises en charge


  
    
    

Microsoft Excel est riche en fonctionnalités. À chaque nouvelle version, l'écart en matière de fonctionnalités entre Excel et Excel Services est réduit, tout comme le nombre de fonctionnalités non prises en charge. Toutefois, il est impossible de prendre en charge toutes les fonctionnalités Excel dans la deuxième version d'Excel Services, dans Microsoft SharePoint Server 2010. 
Lors du choix des fonctionnalités à prendre en charge, la priorité est donnée à celles requises dans les scénarios Excel Services clés, et consiste à s'assurer qu'Excel Services est un service de niveau serveur qui répond aux attentes des clients en matière de fiabilité, d'évolutivité et de sécurité.
  
    
    


> **REMARQUE**
> Cette rubrique suppose que vous êtes familiarisé avec les fonctionnalités prises en charge et non prises en charge dans Microsoft Office SharePoint Server 2007. Vous trouverez plus d'informations sur les fonctionnalités non prises en charge dans Office SharePoint Server 2007 dans la rubrique  [Fonctionnalités non prises en charge dans Excel Services](http://msdn.microsoft.com/fr-fr/library/ms496823.aspx). 
  
    
    


## Prise en charge de nouvelles fonctionnalités Excel

La plupart des nouvelles fonctionnalités dans Microsoft Excel 2010 fonctionnent dans Excel Services. Certaines fonctionnalités se présentent de la même façon que dans Excel. D'autres peuvent être affichées et sont également interactives.
  
    
    
 **Voici quelques nouvelles fonctionnalités qui peuvent apparaître :**
  
    
    

- Graphiques sparkline
    
  
-  [Jeu d'icônes](http://blogs.msdn.com/excel/archive/2009/08/05/icon-set-improvements-in-excel-2010.aspx) et [améliorations apportées à la barre de données](http://blogs.msdn.com/excel/archive/2009/08/07/data-bar-improvements-in-excel-2010.aspx)
    
  
-  [Jeux nommés de tableaux croisés dynamiques](http://blogs.msdn.com/excel/archive/2009/10/05/pivottable-named-sets-in-excel-2010.aspx)
    
  
-  [Améliorations apportées aux tableaux croisés dynamiques](http://blogs.msdn.com/excel/archive/2009/10/15/a-few-more-pivottable-improvements-in-excel-2010.aspx)
    
  
 **Voici quelques nouvelles fonctionnalités qui peuvent apparaître et avec lesquelles vous pouvez interagir :**
  
    
    

- Slicers
    
  
- Fichiers PowerPivot
    
  
Les nouvelles fonctions dans Excel sont également prises en charge. Les images incorporées, une fonctionnalité présente dans Excel depuis longtemps, sont désormais prises en charge et peuvent être affichées dans Excel Services. 
  
    
    

## Fonctionnalités ayant précédemment empêché le chargement de fichiers Excel

Dans Office SharePoint Server 2007, les classeurs Excel qui contiennent des fonctionnalités non prises en charge, comme des macros VBA, des contrôles de formulaire, etc., ne sont pas chargés dans Excel Services.
  
    
    
Dans SharePoint Server 2010, pour aider les utilisateurs à travailler avec cette limitation, Excel Services ignore certaines fonctionnalités non prises en charge. Autrement dit, au lieu de bloquer l'intégralité du chargement de fichier, Excel Services charge le fichier, mais vous ne voyez pas les fonctionnalités non prises en charge par Excel Services.
  
    
    
Voici quelques fonctionnalités qui n'empêchent pas Excel Services de charger un fichier :
  
    
    

- Commentaires de cellule
    
  
- Références de formule provenant de livres externes
    
  
- Tables de requêtes (également appelées plages de données externes)
    
  
- Microsoft Visual Basic pour Applications (VBA)
    
  
- N'importe quelle technologie OfficeArt Par exemple, les formes, WordArt, SmartArt, les organigrammes hiérarchiques, les diagrammes, les lignes de signature, les annotations manuscrites, etc.
    
  
Ces fonctionnalités ne sont toujours pas prises en charge. Cela signifie qu'elles ne s'affichent pas, ne s'exécutent pas ou ne fonctionnent pas comme sur le client. La plupart des fonctionnalités de la liste ne s'affichent pas dans Excel Services. Par exemple, s'il existe une forme près de la cellule A1 lorsqu'elle est affichée sur le client, vous ne voyez aucune forme lorsqu'elle est affichée sur le serveur. D'autres fonctionnalités, telles que les références de formule et les tables de requêtes, affichent les dernières valeurs actualisées sur le client. Autrement dit, les valeurs des cellules sont toujours là, mais vous ne pouvez pas les mettre à jour. 
  
    
    
Enfin, le code VBA ne s'exécute pas sur le serveur. Dans Office SharePoint Server 2007, Excel Services ne prenait pas en charge le chargement de fichiers *.xlsm. Dans SharePoint Server 2010, Excel Services ignore les macros VBA. Par conséquent, les fichiers *.xlsm peuvent maintenant être chargés dans Excel Services.
  
    
    

## Affichage d'un fichier avec des fonctionnalités ignorées

Si Excel Services peut charger des fichiers mais ne peut pas afficher certaines fonctionnalités non prises en charge, comment pouvez-vous savoir que certaines fonctionnalités ne figurent pas dans le fichier visualisé ? Vous savez que vous visualisez un fichier dans lequel certaines fonctionnalités sont manquantes, car Excel Services affiche une notification au-dessus de la feuille de calcul pour vous en avertir. La capture d'écran suivante présente la notification.
  
    
    

**Notification relative aux fonctionnalités non prises en charge en haut du classeur**

  
    
    
Cette notification est le premier signe indiquant que le fichier est affiché différemment que dans le client Excel.
  
    
    
Dans la figure suivante, si vous cliquez sur **En savoir plus sur les fonctionnalités non prises en charge**, vous obtenez des informations sur les fonctionnalités non prises en charge dans le fichier.
  
    
    

**Message d'erreur de fonctionnalité non prise en charge pour VBA**

  
    
    

  
    
    
![Message d'erreur de fonctionnalité non prise en charge pour VBA](images/aebc97ae-c886-4d50-94ff-238049a259c7.gif)
  
    
    
Les images rognées ne sont pas affichées (fonctionnalités manquantes). 
  
    
    

    
> **REMARQUE**
> Pour les classeurs qui contiennent des fonctionnalités non prises en charge ignorées ou manquantes, et qui sont chargés en mode d'affichage avec une barre de notifications, le fait d'essayer d'enregistrer une copie du classeur implique la suppression des fonctionnalités non prises en charge. Une boîte de dialogue avertit l'utilisateur de ce phénomène. 
  
    
    


## Autres fonctionnalités non prises en charge

Toutes les autres fonctionnalités non prises en charge continuent à se comporter de la même façon que dans Office SharePoint Server 2007 pour Excel Services. Autrement dit, Excel Services bloque le chargement d'un fichier s'il détecte l'existence d'au moins une de ces fonctionnalités non prises en charge. Les utilisateurs sont informés que le fichier ne peut pas être chargé, comme indiqué dans la capture d'écran suivante. 
  
    
    

> **REMARQUE**
> La rubrique  [Fonctionnalités non prises en charge dans Excel Services](http://msdn.microsoft.com/fr-fr/library/ms496823.aspx) contient plus d'informations sur ces fonctionnalités non prises en charge.
  
    
    


> **ATTENTION**
> La barre d'informations avec la liste des fonctionnalités non prises en charge ne s'affiche pas si le fichier est chargé à partir d'un composant WebPart. 
  
    
    


**Message d'erreur de fonctionnalité non prise en charge pour les mappages XML**

  
    
    

  
    
    
![Message d'erreur de fonctionnalité non prise en charge pour les mappages XML](images/7745688c-c612-4a38-b8aa-b5fdb5e4eeb8.gif)
  
    
    
Contrairement aux classeurs contenant des liens externes, le chargement des graphiques avec des liens externes est bloqué. 
  
    
    

## Voir aussi


#### Concepts


  
    
    
 [Vue d'ensemble d'Excel Services](excel-services-overview.md)
  
    
    
 [Architecture d'Excel Services](excel-services-architecture.md)
  
    
    
 [Blogs sur Excel Services](excel-services-blogs-forums-and-resources.md)
#### Autres ressources


  
    
    
 [Procédure pas à pas : développement d'une application personnalisée à l'aide des services Web Excel](walkthrough-developing-a-custom-application-using-excel-web-services.md)
