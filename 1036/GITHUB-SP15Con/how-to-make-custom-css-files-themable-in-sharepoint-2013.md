---
title: Comment transformer des fichiers CSS personnalisés en fichiers à thèmes dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: b8c82c77-c836-47f9-a11e-6c9c656d436b
---


# Comment transformer des fichiers CSS personnalisés en fichiers à thèmes dans SharePoint 2013
Découvrez comment ajouter des balises de style commentaire dans un fichier CSS afin qu'il puisse être utilisé dans le moteur de thèmes SharePoint 2013.
## Présentation des annotations
<a name="Intro"> </a>

Les annotations sont des balises de style commentaire spéciales qui indiquent au moteur de thèmes SharePoint la manière d'appliquer les thèmes aux propriétés dans un fichier CSS. Lorsqu'un thème est appliqué à un site, le moteur de thèmes remplace les valeurs des propriétés CSS par les valeurs de thèmes appropriées. Dans SharePoint 2013, vous pouvez utiliser des annotations pour modifier la couleur, la police ou l'image d'arrière-plan. Vous pouvez également recolorer une image. Si vous utilisez des fichiers CSS personnalisés, vous devez ajouter ces annotations dans les fichiers CSS si vous souhaitez les utiliser avec le moteur de thèmes SharePoint. Si vous appliquez un thème à un site qui utilise des fichiers CSS personnalisés et que vous n'avez pas ajouté d'annotations, les propriétés CSS restent inchangées. Dans ce cas, le site peut présenter une conception qui ne correspond pas.
  
    
    
Cet article décrit les annotations disponibles et la manière d'enregistrer des fichiers CSS.
  
    
    
Pour plus d'informations sur les thèmes personnalisés, voir  [Procédure : Déployer un thème personnalisé dans SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md) et [Comment créer un fichier d'aperçu de page maître dans SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md).
  
    
    

## Ajout d'annotations à des fichiers CSS personnalisés
<a name="annotations"> </a>

Les annotations indiquent au moteur de thèmes SharePoint la manière d'appliquer les thèmes aux propriétés dans un fichier CSS. Cette section décrit les annotations disponibles et la manière de les utiliser.
  
    
    

### Annotation ReplaceColor
<a name="replaceColor"> </a>

L'annotation **ReplaceColor** remplace la valeur de couleur par la couleur de thème spécifiée. Elle peut être utilisée avec des propriétés CSS qui définissent une valeur de couleur, comme **color**, **background-color**, **border** etc.
  
    
    
L'exemple suivant montre le format de l'annotation **ReplaceColor**.
  
    
    



```

/* [ReplaceColor(themeColor:"ColorSlot"[, themeShade:"ShadeValue"][, themeTint:"TintValue"][, opacity:"OpacityValue"])] */

```

Remplacez  _ColorSlot_ par le nom d'annotation de l'emplacement de couleur à utiliser. Pour consulter une liste des emplacements de couleur disponibles, voir la section [Mappage des emplacements de couleur](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots) dans [Palettes de couleurs et polices dans SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md).
  
    
    
Utilisez le paramètre facultatif **themeShade** si vous voulez assombrir la couleur de thème. Remplacez _ShadeValue_ par une valeur numérique comprise entre 0.0 (aucune modification) et 1.0 (couleur la plus sombre).
  
    
    
Utilisez le paramètre facultatif **themeTint** si vous voulez éclaircir la couleur de thème. Remplacez _TintValue_ par une valeur numérique comprise entre 0.0 (aucune modification) et 1.0 (couleur la plus claire).
  
    
    
Utilisez le paramètre **opacity** si vous voulez spécifier l'opacité de la couleur de thème. Remplacez _OpacityValue_ par une valeur numérique qui spécifie le paramètre d'opacité. Le paramètre opacity est compris entre 0.0 (transparence totale) et 1.0 (opacité totale).
  
    
    
Voici des exemples de l'annotation **ReplaceColor** utilisée dans un fichier CSS.
  
    
    

-  `/* [ReplaceColor(themeColor:"BodyText")] */ color:#444;`
    
  
-  `/* [ReplaceColor(themeColor:"BackgroundOverlay",opacity:"0.5")] */ background-color:#fff;`
    
  
-  `/* [ReplaceColor(themeColor:"EmphasisBackground",themeTint:"0.05")] */ background-color:#f2faff;`
    
  

### Annotation ReplaceFont
<a name="replaceFont"> </a>

L'annotation **ReplaceFont** ajoute la police de thème spécifiée à la liste des polices disponibles. Elle peut être utilisée avec les propriétés CSS **font** et **font-family**.
  
    
    
L'exemple suivant montre le format pour l'annotation **ReplaceFont**.
  
    
    



```

/* [ReplaceFont(themeFont:"FontSlot")] */
```

Remplacez  _FontSlot_ par le nom de l'emplacement de police à utiliser. Pour voir la liste des emplacements de police disponibles, voir la section [Emplacements de police](color-palettes-and-fonts-in-sharepoint-2013.md#fontSlot) dans [Palettes de couleurs et polices dans SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md).
  
    
    
Voici un exemple de l'annotation **ReplaceFont**. Dans cet exemple, si l'emplacement de police **body** est défini sur Courier dans le thème, Courier sera ajouté en tant que premier élément dans la liste des polices disponibles dans l'Assistant **Choose the Look**.
  
    
    

-  `/* [ReplaceFont(themeFont:"body")] */ font-family:"Segoe UI","Segoe",Tahoma,Helvetica,Arial,sans-serif;`
    
  

### Annotation ReplaceBGImage
<a name="replaceBGimage"> </a>

L'annotation **ReplaceBGImage** remplace l'image d'arrière-plan dans le fichier CSS par l'image d'arrière-plan du thème. Elle peut être utilisée avec les propriétés CSS **background** et **background-image**.
  
    
    
L'exemple suivant montre le format de l'annotation **ReplaceBGImage**. L'annotation **ReplaceBGImage** peut également être utilisée avec le filtre **AlphaImageLoader** pour prendre en charge les versions antérieures d'Internet Explorer.
  
    
    



```
/* [ReplaceBGImage] */
```


### Annotation RecolorImage
<a name="replaceBGimage"> </a>

L'annotation **RecolorImage** recolore l'image spécifiée.
  
    
    
Les éléments suivants décrivent le format de l'annotation **RecolorImage**.
  
    
    



```
/* [RecolorImage(themeColor:"ColorSlot"[, method:["Tinting"|"Blending"|"Filling"]][, includeRectangle: {x:x-Setting,y:y-Setting,width:RegionWidth,height:RegionHeight})] */

```

Remplacez  _ColorSlot_ par le nom de l'annotation de l'emplacement de couleur. Pour consulter la liste des emplacements de couleur disponibles, voir la section [Mappage des emplacements de couleur](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots) dans [Palettes de couleurs et polices dans SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md).
  
    
    
Utilisez le paramètre facultatif **method** si vous souhaitez spécifier la méthode de recolorisation.
  
    
    
Utilisez le paramètre facultatif **includeRectangle** si vous voulez recolorer uniquement une zone spécifique d'une image. Remplacez _x-Setting_,  _y-Setting_,  _RegionWidth_ et _RegionHeight_ par les coordonnées de l'axe des abscisses (X), les coordonnées de l'axe des ordonnées (Y), la largeur et la hauteur de la zone que vous voulez recolorer.
  
    
    
Voici des exemples de l'utilisation de l'annotation **RecolorImage** dans un fichier CSS.
  
    
    

-  `/* [RecolorImage(themeColor:"SubtleBodyText",method:"Tinting")] */ background-image:url("/_layouts/15/images/tabtitlerowbottombg.png?rev=23");`
    
  
-  `/* [RecolorImage(themeColor:"BodyText",method:"Filling",includeRectangle:{x:161,y:178,width:16;height:16})] */ background:url("/_layouts/15/images/spcommon.png?rev=23") no-repeat -161px -178px;`
    
  

## Téléchargement du fichier CSS dans le dossier Themable dans la bibliothèque de styles
<a name="uploadCSS"> </a>

Placez les fichiers CSS personnalisés dans le dossier Themable de la bibliothèque de styles (pas le dossier Themable de la galerie de pages maîtres). Seuls les fichiers CSS stockés dans le dossier Themable de la bibliothèque de styles sont reconnus par le moteur de thèmes. Le dossier Themable est créé automatiquement pour les sites de publication. Sinon, vous pouvez créer le dossier Themable à l'emplacement correct (http:// _SiteCollectionName_/Style Library/ _langue_/Themable/).
  
    
    

> **REMARQUE**
> Le nom du dossier  _langue_ doit être dans un format à 4 chiffres _ll-cc_ pour identifier la langue et la culture, respectivement. Par exemple, en-us ou ar-sa. Pour plus d'informations, consultez la rubrique [Identificateurs de langue et valeurs d'ID de l'élément OptionState dans Office 2013](http://technet.microsoft.com/fr-fr/library/cc179219.aspx). 
  
    
    

Les fichiers CSS doivent être enregistrés et publiés. Si les fichiers CSS sont modifiés, vous devez appliquer à nouveau le thème pour que les modifications soient reconnues.
  
    
    

## Enregistrer le fichier CSS
<a name="registerCSS"> </a>

Vous devez enregistrer le fichier CSS auprès d'une page maître pour que le fichier CSS puisse être utilisé par le moteur de thèmes. Cela permet d'indiquer à la page maître où se trouve le fichier CSS lorsque vous appliquez un thème à un site. Pour enregistrer un fichier CSS, ajoutez un élément **<SharePoint:CssRegistration>** à l'élément **<head>** de la page maître. L'exemple suivant montre le format de l'élément **<SharePoint:CssRegistration>**.
  
    
    

```HTML

<SharePoint:CssRegistration Name="CSSFileLocation" runat="server" />
```

Remplacez  _CSSFileLocation_ par l'emplacement du fichier CSS.
  
    
    
Voici un exemple d'un élément **<SharePoint:CssRegistration>**.
  
    
    



```HTML
<head>
…
<SharePoint:CssRegistration Name="<%$SPUrl:~SiteCollection/Style Library/~language/Themable/MyCustomFile.css%>" runat="server" />
</head>
```


> **REMARQUE**
> Le jeton **%$SPUrl** ne peut pas être utilisé sur SharePoint Foundation 2013. Vous devez utiliser une URL pour spécifier l'emplacement du fichier CSS.
  
    
    


## Ressources supplémentaires
<a name="addresources"> </a>


-  [Vue d'ensemble des thèmes pour SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Procédure : Déployer un thème personnalisé dans SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [Mettre à niveau les thèmes personnalisés et CSS pour SharePoint 2013](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [Comment créer un fichier d'aperçu de page maître dans SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [Palettes de couleurs et polices dans SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [Blog de l'équipe SharePoint : Affichez votre style avec les thèmes SharePoint](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [Fonctionnalités de personnalisation et la conception de 2013 le gestionnaire de conception SharePoint](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

