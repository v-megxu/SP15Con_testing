---
title: Comment appliquer une page maître à un site dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 04861390-84d5-40ea-b0db-6c0748eff196
---


# Comment appliquer une page maître à un site dans SharePoint 2013
Découvrez comment mapper une page maître vers un site SharePoint 2013.
## Mappage d'une page maître vers un site

Dans SharePoint 2013, une page maître définit les éléments de tramage partagés, tels que le chrome, pour toutes les pages de votre site. Après qu'une page maître est créée, elle peut être mappée vers un site. Il peut s'agir de toutes les pages de publication destinées à tous les utilisateurs ou des pages d'administration utilisées pour la maintenance du site. Sinon, si vous configurez un site enfant d'un site parent, vous pouvez hériter de la page maître de la part du parent. Cet article décrit les étapes permettant de mapper une page maître créée vers un site, d'hériter de la page maître depuis un site parent ou de mapper une page maître vers un canal de périphérique spécifique.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur le Gestionnaire de conception et les pages maîtres, consultez la rubrique  [Vue d'ensemble du gestionnaire de conception dans SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md). Pour plus d'informations sur la création de canaux de périphérique, consultez la rubrique  [Canaux d'appareils du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-device-channels.md). 
  
    
    


### Mapper une page maître vers un site SharePoint


1.  Dans **Paramètres du site** pour le site désigné, dans la section **Aspect**, choisissez **Page maître**.
    
    > **REMARQUE**
      > Si le lien **Page maître** n'est pas accessible, vous devez activer la fonctionnalité de publication en procédant comme suit. Accédez à **Paramètres du site | Administration de la collection de sites | Fonctionnalités de la collection de sites**. Faites défiler jusqu'à la fonctionnalité **Infrastructure de publication de SharePoint Server** et appuyez sur **Activer**. 
2. Dans **Paramètres de la page maître du site**, sélectionnez une des deux options pour la section **Page maître de site** ou **Page maître système**:
    
  - **Hériter de la page maître du site parent** Choisissez cette option si vous configurez un site SharePoint enfant et que vous souhaitez utiliser la page maître parente.
    
    > **REMARQUE**
      > Cette option n'est pas disponible si vous travaillez sur le site parent de niveau supérieur. 
  - **Spécifiez une page maître à utiliser par ce site et tous les sites qui en héritent** Choisissez cette option si vous voulez mapper une page maître spécifique vers le site, ou si vous voulez mapper une page maître spécifique vers les pages d'administration. Une zone de liste déroulante appelée **Par défaut** ou **Tous les canaux** est disponible, selon la configuration de votre site ou de votre système, pour que vous puissiez sélectionner une page maître spécifique, enregistrée dans la galerie Pages maîtres. Sélectionnez la page maître souhaitée dans la zone de liste déroulante.
    
    > **REMARQUE**
      > Si vous avez configuré des canaux de périphérique, des zones déroulantes supplémentaires sont disponibles pour les options de mappage de pages maîtres supplémentaires. 
3. Sélectionnez **OK**.
    
  

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Développer la conception de site dans SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Vue d'ensemble du gestionnaire de conception dans SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Nouveautés du développement de sites SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md)
    
  

