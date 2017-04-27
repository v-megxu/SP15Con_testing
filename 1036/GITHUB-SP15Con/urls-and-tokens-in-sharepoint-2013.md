---
title: URL et jetons dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 161418d7-8123-4c4e-91a1-97e43c17f0e6
---



# URL et jetons dans SharePoint 2013
Découvrez comment formuler des URL et utiliser des jetons d'URL dans SharePoint 2013.
|||
|:-----|:-----|
|**Dans cet article**          [Types d'URL dans SharePoint 2013](#TypesOfURLs)           [Bonnes pratiques pour les URL d'image](#GoodPracticeImageURL)           [Jetons d'URL dans SharePoint 2013](#URLtokens)           [Ressources supplémentaires](#SP15URLS_addlresources)||
   

## Types d'URL dans SharePoint 2013
<a name="TypesOfURLs"> </a>

SharePoint 2013 analyse les chaînes d'URL afin de déterminer la forme de l'URL d'après un protocole spécifié (par exemple, **http:**) ou d'après l'insertion d'une barre oblique (/) dans la chaîne. Selon le membre particulier, vous pouvez utiliser les formes d'URL suivantes :
  
    
    

- Une **URL absolue** spécifie un chemin d'accès complet et commence par un protocole. Par exemple, `http://` _Domaine_ou_Serveur_/[ `sites/`] _Site_Web_/ `Lists`/ _Titre_Liste_/ `AllItems.aspx`.
    
  
- Une **URL relative de serveur** repose sur l'adresse du domaine (qui peut être le nom d'un serveur) et commence toujours par une barre oblique. Elle spécifie un chemin d'accès complet depuis le site web de niveau supérieur jusqu'au nom du fichier. Par exemple, /[ `sites/`] _Site_Web_/ `Lists`/ _Titre_Liste_/ `AllItems.aspx`. 
    
  
- Une **URL relative de site web** repose sur l'adresse d'un objet de site web ( [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) ). Elle _ne commence pas_ par une barre oblique et spécifie un chemin d'accès complet depuis l'adresse du site web jusqu'au nom du fichier. Par exemple, `Lists/` _Titre_Liste_/ `AllItems.aspx`.
    
  
- Une **URL relative à un fichier ou à un dossier** repose sur le dossier contenant le fichier. Elle ne contient _aucune_ barre oblique et spécifie simplement le nom du fichier. Par exemple, `AllItems.aspx`.
    
  

> **REMARQUE**
> Il n'existe pas de concept « d'URL relative à une collection de sites » ; par conséquent, l'envoi d'une telle URL peut entraîner l'échec du code. 
  
    
    


## Bonnes pratiques pour les URL d'image
<a name="GoodPracticeImageURL"> </a>

Lorsque vous créez une URL vers un fichier image situé dans le répertoire %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\IMAGES, spécifiez un chemin d'accès qui utilise le site web racine de la collection de sites, mais n'incluez pas de sous-site dans le chemin d'accès. Par exemple, utilisez /_layouts/images/MyImage.gif pour un fichier image, mais pas /MySubsite/_layouts/images/MyImage.gif. En effet, les URL de sous-site sont résolues de façons différentes selon leur utilisation. Pour contourner ces variations, vous devez donc toujours utiliser l'URL relative au site web racine.
  
    
    

## Jetons d'URL dans SharePoint 2013
<a name="URLtokens"> </a>

SharePoint 2013 prend en charge les jetons figurant dans les tableaux suivants pour une utilisation dans des Compléments SharePoint ou des solutions de batterie de serveurs. En outre, certains jetons sont utilisables uniquement dans les applications. Pour plus d'informations à ce sujet, consultez la rubrique  [Chaînes URL et jetons dans les compléments pour SharePoint](http://msdn.microsoft.com/library/800ec8cd-a448-46bc-b41e-d4030eeb4048%28Office.15%29.aspx).
  
    
    
Les jetons figurant dans les tableaux de cette section peuvent être utilisés dans les URL pour de nombreuses situations lors du développement SharePoint, comme dans des actions personnalisées et dans des liens sur des pages personnalisées. Parfois, certains jetons ne peuvent pas être utilisés. Les trois emplacements principaux pour lesquels seule une liste limitée de jetons peut être utilisée sont la page de démarrage d'une application, une action personnalisée sur le site web hôte et la propriété  [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) d'un composant d'application. Ces emplacements sont présentés dans des colonnes séparées, mais ils ne constituent pas une liste exhaustive des emplacements où les jetons peuvent être utilisés.
  
    
    
La colonne **StartPage** indique si le jeton peut être utilisé dans l'élément **StartPage** d'un manifeste d'application. La colonne **Action personnalisée** indique si le jeton peut être utilisé dans l'URL d'une action personnalisée sur un site Web hôte. Enfin, la colonne **Composant d'application** indique si le jeton peut être utilisé dans la propriété [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) du composant d'application.
  
    
    

**Jetons pouvant être utilisés au début d'une URL**


|**Jeton**|**Est résolu en**|**StartPage**|**Action personnalisée**|**Composant d'application**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|~controlTemplates  <br/> |L'URL du dossier virtuel ControlTemplates pour le site web actuel.  <br/> |Non  <br/> |Non  <br/> |Non  <br/> ||
|~layouts  <br/> |L'URL du dossier virtuel Dispositions pour le site web actuel.  <br/> |Non  <br/> |Non  <br/> |Non  <br/> ||
|~site  <br/> |L'URL du site web actuel.  <br/> |Non  <br/> |Non  <br/> |Oui  <br/> ||
|~sitecollection  <br/> |L'URL de la collection de sites parente du site web actuel.  <br/> |Non  <br/> |Non  <br/> |Oui  <br/> ||
   
Sauf mention contraire, aucun des jetons figurant dans le tableau suivant ne peut être utilisé dans la partie  *chemin d'accès*  de la valeur de propriété [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) du composant d'application. La colonne **Composant d'application** fait référence à l'utilisation des jetons dans la partie *chaîne de requête*  de la valeur.
  
    
    

**Jetons pouvant être utilisés dans une URL**


|**Jeton**|**Est résolu en**|**StartPage**|**Action personnalisée**|**Composant d'application**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|{ControlTemplates}  <br/> |L'URL du dossier virtuel ControlTemplates pour le site web actuel.  <br/> |Non  <br/> |Non  <br/> |Non  <br/> ||
|{ItemId}  <br/> |ID d'un élément d'une liste ou d'une bibliothèque (un entier).  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> ||
|{ItemUrl}  <br/> |URL de l'élément faisant l'objet d'une opération.  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> ||
|{Layouts}  <br/> |L'URL du dossier virtuel Dispositions pour le site web actuel.  <br/> |Non  <br/> |Non  <br/> |Non  <br/> ||
|{ListId}  <br/> |L'ID de la liste actuelle (GUID).  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> ||
|{RecurrenceId}  <br/> |L'index de périodicité d'un événement périodique.  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> |Ce jeton n'est pas pris en charge dans les menus contextuels des éléments de liste.  <br/> |
|{Site}  <br/> |L'URL du site web actuel.  <br/> |Non  <br/> |Oui  <br/> |Oui  <br/> ||
|{SiteCollection}  <br/> |L'URL du site parent du site web actuel.  <br/> |Non  <br/> |Oui  <br/> |Oui  <br/> ||
|{SiteUrl}  <br/> |L'URL du site web actuel.  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> ||
|{Source}  <br/> |URL de la requête HTTP.  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> ||
   

## Ressources supplémentaires
<a name="SP15URLS_addlresources"> </a>


-  [Créer des solutions de batterie dans SharePoint 2013](build-farm-solutions-in-sharepoint-2013.md)
    
  
-  [Support extranet avancé](http://msdn.microsoft.com/library/21d67796-23c5-4339-8f0e-124208d21ab2%28Office.15%29.aspx)
    
  
-  [Obtention de références aux sites, applications Web et autres objets clés](http://msdn.microsoft.com/library/8623ef1d-e3cc-426c-84a3-6379e0ae284f%28Office.15%29.aspx)
    
  
-  [Utilisation des objets Liste et des collections](http://msdn.microsoft.com/library/d4167b10-6f1e-49f1-8b22-16ce20012a27%28Office.15%29.aspx)
    
  
-  [Exemples de tâches de modèle objet](http://msdn.microsoft.com/library/94d6898d-6a0f-43a7-ad06-1b27ec6916ea%28Office.15%29.aspx)
    
  
