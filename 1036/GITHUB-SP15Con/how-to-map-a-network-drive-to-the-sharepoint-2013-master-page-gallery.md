---
title: Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7d416f6e-2471-4d03-97ae-4e8d907784c6
---


# Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013
Découvrez comment mapper un lecteur réseau sur la galerie Pages maîtres afin de pouvoir utiliser le Gestionnaire de conception pour télécharger des fichiers de conception dans SharePoint Server 2013.
Vous pouvez créer une conception visuelle pour votre site web à l'aide d'un outil de conception web ou d'un éditeur HTML, puis utiliser le Gestionnaire de conception pour importer la conception dans SharePoint. Pour ce faire, vous devez vous assurer que l'outil de conception stocke ses fichiers dans la galerie Pages maîtres de votre site, soit l'emplacement où SharePoint recherche les fichiers. Il est recommandé de mapper un lecteur réseau sur la galerie Pages maîtres pour faciliter l'enregistrement des fichiers au bon endroit.
  
    
    

Tout d'abord, recherchez l'emplacement de la galerie Pages maîtres.
### Pour trouver l'emplacement de la galerie Pages maîtres


1. Sur le site pour lequel vous créez une conception, démarrez le Gestionnaire de conception (par exemple, dans le menu **Paramètres**, choisissez **Gestionnaire de conception**).
    
    > **IMPORTANTE**
      > Si votre site est hébergé dans SharePoint Online, lorsque vous vous connectez au site à l'aide de vos informations d'identification Office 365, veillez à cocher la case **Maintenir la connexion**. Pour plus d'informations, consultez la rubrique  [Comment faire pour configurer et dépanner les lecteurs réseau mappés qui se connectent à des sites SharePoint Online dans Office 365](https://support.microsoft.com/fr-fr/kb/2616712). 
2. Dans la liste numérotée, sélectionnez **Charger les fichiers de conception sur le réseau**.
    
  
3. La page Gestionnaire de conception : Charger les fichiers de conception sur le réseau contient l'emplacement de la galerie Pages maîtres. L'emplacement se termine probablement par  `/_catalogs/masterpage/`. Il s'agit de l'emplacement sur lequel mapper un lecteur réseau.
    
  
4. Prenez note de l'emplacement de la galerie Pages maîtres ou copiez-le dans le Presse-papiers.
    
  
Sur l'ordinateur qui exécute l'outil de conception ou l'éditeur HTML, mappez un lecteur réseau sur l'emplacement que vous venez de copier. La procédure permettant de mapper un lecteur réseau diffère selon le système d'exploitation de l'ordinateur :
- Si l'ordinateur fonctionne sous Windows 8, suivez les étapes décrites dans la version Windows 8 de l'article  [Créer un raccourci pour (mapper) un lecteur réseau](http://windows.microsoft.com/fr-fr/windows-8/create-shortcut-to-map-network-drive).
    
  
- Si l'ordinateur fonctionne sous Windows 7, suivez les étapes décrites dans la version Windows 7 de l'article  [Créer un raccourci pour (mapper) un lecteur réseau](http://windows.microsoft.com/fr-fr/windows/create-shortcut-map-network-drive#1TC=windows-7).
    
  
- Si l'ordinateur fonctionne sous Windows Vista, suivez les étapes décrites dans la version de l'article  [Créer un raccourci pour (mapper) un lecteur réseau](http://windows.microsoft.com/fr-fr/windows/create-shortcut-map-network-drive#1TC=windows-vista).
    
  
- Si l'ordinateur fonctionne sous Windows XP, suivez les étapes décrites dans l'article  [Procédure de connexion et de déconnexion d'un lecteur réseau dans Windows XP](https://support.microsoft.com/fr-fr/kb/308582).
    
  
- ** *Si l'ordinateur fonctionne sous un autre système d'exploitation, suivez les instructions pour la création d'un raccourci vers un nouvel emplacement pour ce système d'exploitation.* ** Vous devrez peut-être fournir différentes informations d'identification pour vous connecter au site SharePoint et vous devrez peut-être préciser que la connexion doit être rétablie à chaque fois que vous ouvrez une session sur l'ordinateur.
    
  

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Comment appliquer une page maître à un site dans SharePoint 2013](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)
    
  
-  [Développer la conception de site dans SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Canaux d'appareils du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-device-channels.md)
    
  
-  [Comment modifier la page d'aperçu dans le Gestionnaire de conception SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [Rendus d'image du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-image-renditions.md)
    
  

