---
title: Rendus d'image du Gestionnaire de conception SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: d08a74c0-5674-4f26-8646-11ea1f081c85
---


# Rendus d'image du Gestionnaire de conception SharePoint 2013
Découvrez comment créer un rendu d'image, comment l'ajouter à une page et comment le détourer. Un rendu d'image définit les dimensions utilisées pour afficher des images dans les sites de publication SharePoint.
Les rendus d'image vous permettent d'afficher des versions de différentes tailles d'une image sur différentes pages dans un site de publication, à partir de la même image source. Lorsque vous créez un rendu d'image, vous spécifiez la largeur et/ou la hauteur de toutes les images qui utilisent ce rendu d'image. Les rendus d'image sont disponibles pour chaque image téléchargée dans une bibliothèque dans cette collection de sites. Par exemple, les concepteurs peuvent créer un rendu d'image pour afficher des images miniatures et un autre rendu d'image pour afficher les images de la bannière. Lorsqu'une image est ajoutée à une page, l'auteur peut spécifier le rendu d'image à appliquer à cette image. Les auteurs peuvent également détourer le rendu d'image pour spécifier la partie de l'image à utiliser dans le rendu d'image. La taille correcte de l'image s'affiche lorsque la page est affichée.
  
    
    

Les rendus d'image vous permettent d'afficher une même image de plusieurs manières. Une image peut être affichée dans différentes tailles ou avec un détourage différent. La première fois qu'une image est demandée, SharePoint Server utilise le rendu d'image spécifié pour générer l'image. Lorsqu'un utilisateur consulte un site SharePoint, la version de l'image dimensionnée correctement est téléchargée sur l'ordinateur du client. Ceci réduit la taille du fichier téléchargé chez le client, ce qui améliore les performances du site.
## Conditions préalables pour la gestion des rendus d'image
<a name="Prerequisites"> </a>

Étant donné que les rendus d'image dépendent d'autres fonctionnalités dans SharePoint Server 2013, veillez à respecter les conditions préalables décrites dans cette section avant d'exécuter les procédures énoncées dans cette rubrique. Les conditions préalables sont les suivantes :
  
    
    

- **Une collection de sites de publication**: la collection de sites où vous ajoutez les rendus d'image doit avoir été créée à l'aide du portail de publication ou du modèle de collection de sites de catalogue de produits. Sinon, les fonctionnalités de publication doivent être activées sur la collection de sites où vous souhaitez utiliser les rendus d'image. Pour plus d'informations, voir [Vue d'ensemble de la publication sur les sites Internet, intranet et extranet](http://technet.microsoft.com/fr-fr/library/jj635881%28office.15%29.aspx) dans la bibliothèque TechNet.
    
  
- **Un cache BLOB configuré**: le cache BLOB sur disque contrôle la mise en cache des objets BLOB, comme les fichiers image, audio et vidéo fréquemment utilisés et d'autres fichiers utilisés pour afficher des pages web, tels que les fichiers .css et .js. Le cache BLOB doit être activé sur chaque serveur web frontal où vous souhaitez utiliser les rendus d'image. Si le cache BLOB n'est pas activé, l'image d'origine est toujours utilisée. Pour plus d'informations, voir [Configurer les paramètres de cache pour une application web](http://technet.microsoft.com/fr-fr/library/cc770229.aspx) dans la bibliothèque TechNet.
    
  
- **Une bibliothèque de biens (recommandé)**: vous pouvez utiliser le modèle Bibliothèque de biens (ou Bibliothèque de composants) pour configurer une bibliothèque qui permet de stocker, d'organiser et de rechercher des biens multimédias enrichis, tels que des fichiers image, audio ou vidéo. Pour plus d'informations, voir [Configurer une bibliothèque de biens pour stocker des fichiers image, audio ou vidéo](http://office.microsoft.com/fr-fr/sharepoint-server-help/set-up-an-asset-library-to-store-image-audio-or-video-files-HA102785730.aspx) sur Office.com.
    
  

## Création d'un rendu d'image
<a name="Create"> </a>

Lors de la création d'un rendu d'image, SharePoint Server 2013 crée un identifiant unique qui identifie ce rendu d'image. Une image est générée lorsque SharePoint Server reçoit une demande de rendu d'image pour la première fois.
  
    
    

### Pour créer un rendu d'image


1. Vérifiez que le compte d'utilisateur qui exécute cette procédure dispose, au minimum, des autorisations de création pour le site de niveau supérieur de la collection de sites.
    
  
2. Dans un navigateur, accédez au site de niveau supérieur de la collection de sites de publication.
    
  
3. Choisissez l'icône **Paramètres**. Sur la page **Paramètres du site**, dans la section **Aspect**, choisissez **Rendus d'image**.
    
    > **REMARQUE**
      > La page Rendus d'image peut également être ouverte à partir de la page d'accueil par défaut du site de publication. Dans la section **Je suis le concepteur visuel**, choisissez **Configurer les rendus d'image**. 
4. Sur la page **Rendus d'image**, sélectionnez **Ajouter un nouvel élément**.
    
  
5. Sur la page **Nouveau rendu d'Image**, dans la zone **Nom**, saisissez un nom pour le rendu. Par exemple, saisissez Miniature_petite.
    
  
6. Dans les zones de texte **Largeur** et **Hauteur**, saisissez la largeur et la hauteur, en pixels, du rendu voulu, puis choisissez **Enregistrer**.
    
  

## Modification d'un rendu d'image
<a name="Edit"> </a>

Lorsqu'un rendu d'image est modifié, les nouvelles dimensions sont appliquées dès que l'image est demandée à nouveau. Si une image a été générée précédemment depuis le rendu d'image, l'image est à nouveau générée avec les nouvelles dimensions lorsqu'elle est demandée à nouveau.
  
    
    

### Pour modifier un rendu d'image


1. Vérifiez que le compte d'utilisateur qui exécute cette procédure dispose, au minimum, des autorisations de création pour le site de niveau supérieur de la collection de sites.
    
  
2. Dans un navigateur, accédez au site de niveau supérieur de la collection de sites de publication.
    
  
3. Choisissez l'icône **Paramètres**. Sur la page **Paramètres du site**, dans la section **Aspect**, choisissez **Rendus d'image**.
    
    > **REMARQUE**
      > La page **Rendus d'image** peut également être ouverte à partir de la page d'accueil par défaut du site de publication. Dans la section **Je suis le concepteur visuel**, choisissez **Configurer les rendus d'image**. 
4. Sur la page **Rendus d'image**, sélectionnez le rendu d'image que vous souhaitez modifier.
    
  
5. Sur la page **Modifier le rendu d'image**, modifiez le nom, la largeur ou la hauteur du rendu d'image.
    
  

## Ajout d'un rendu d'image
<a name="Add"> </a>

Lorsque vous ajoutez une image à une page dans un site de publication SharePoint, vous pouvez spécifier le rendu d'image à utiliser pour cette image. Lorsque la page est affichée dans un navigateur, la taille appropriée de l'image s'affiche. Vous pouvez spécifier le rendu d'image dans l'éditeur de texte enrichi, dans un contrôle de champ d'image ou dans l'URL de l'image.
  
    
    

### Spécifier le rendu d'image à l'aide de l'éditeur de texte enrichi

Lorsqu'une image est insérée dans une page, vous pouvez spécifier le rendu d'image à utiliser pour que la taille appropriée de l'image s'affiche lorsque la page est affichée. Vous pouvez spécifier le rendu d'image dans l'éditeur de texte enrichi uniquement pour les images qui sont stockées dans la même collection de sites que la page en cours de modification.
  
    
    

### Pour spécifier un rendu d'image à l'aide de l'éditeur de texte enrichi


1. Sur l'onglet **Page**, cliquez sur **Modifier**.
    
  
2. Choisissez l'icône **Paramètres**, puis choisissez **Ajouter une page**.
    
  
3. Dans la fenêtre **Ajouter une page**, saisissez le nom de la page, puis choisissez **Créer**.
    
  
4. Placez le pointeur dans le champ **Contenu de la page**.
    
  
5. Sur l'onglet **Insertion**, choisissez **Image**, puis **À partir de SharePoint**.
    
  
6. Recherchez l'image que vous souhaitez ajouter à la page, sélectionnez-la, puis choisissez **Insérer**. L'image sera affichée en taille réelle.
    
  
7. Sur l'onglet **Conception**, dans le groupe **Sélectionner**, choisissez **Choisir un rendu**, puis sélectionnez un rendu d'image. L'image s'affiche en fonction de la taille spécifiée pour le rendu d'image.
    
    > **REMARQUE**
      > La commande **Choisir un rendu** est disponible uniquement pour les images qui sont stockées dans la même collection de sites que la page en cours de modification.
8. Si vous voulez détourer le rendu d'image, choisissez **Choisir un rendu**, puis **Modifier les rendus**.
    
    Pour plus d'informations sur le détourage des rendus d'image, voir la section  [Détourage d'un rendu d'image](#Crop) de cet article.
    
  

### Spécifier le rendu d'image dans l'URL de l'image

Vous pouvez spécifier le rendu d'image en ajoutant les paramètres RenditionID, Width et Height à l'URL de l'image.
  
    
    
 **RenditionID**: le paramètre RenditionID permet de spécifier l'identifiant du rendu d'image à utiliser.
  
    
    
 **Width**: le paramètre Width permet de spécifier la largeur, en pixels, du rendu d'image. SharePoint Server tente de trouver un rendu d'image ayant la largeur spécifiée. Ensuite, SharePoint Server tente de trouver un rendu d'image d'une largeur supérieure à la largeur spécifiée. Si plusieurs rendus d'image remplissent ce critère, SharePoint Server utilise le rendu d'image ayant la largeur la plus proche de celle spécifiée. S'il n'existe aucun rendu d'image ayant une largeur égale ou supérieure à celle spécifiée, l'image d'origine est utilisée.
  
    
    
 **Height**: le paramètre Height permet de spécifier la hauteur, en pixels, du rendu d'image. SharePoint Server tente de trouver un rendu d'image ayant la hauteur spécifiée. Ensuite, SharePoint Server tente de trouver un rendu d'image d'une hauteur supérieure à la hauteur spécifiée. Si plusieurs rendus d'image remplissent ce critère, SharePoint Server utilise le rendu d'image ayant la hauteur la plus proche de celle spécifiée. S'il n'existe aucun rendu d'image ayant une hauteur égale ou supérieure à celle spécifiée, l'image d'origine est utilisée.
  
    
    
 **Width et Height**: si les paramètres Width et Height sont spécifiés, SharePoint Server tente de trouver un rendu d'image ayant la largeur et la hauteur spécifiées. Ensuite, SharePoint Server tente de trouver un rendu dont le rapport largeur/hauteur est le plus proche de celui spécifié. Si plusieurs correspondances sont trouvées, le rendu d'image sur lequel le rapport largeur/hauteur supérieur est le plus proche de la taille requise est choisi.
  
    
    

> **REMARQUE**
> Si l'URL d'image inclut le paramètre RenditionID, ainsi que les paramètres Width et Height, les paramètres Width et Height sont ignorés. 
  
    
    

L'exemple suivant montre comment utiliser le paramètre RenditionID :
  
    
    



```HTML

<img src="/sites/pub/Assets/Lighthouse.jpg?RenditionID=2" />
```

L'exemple suivant montre comment utiliser les paramètres Width et Height :
  
    
    



```HTML
<img src="/sites/pub/Assets/Lighthouse.jpg?Width=400&amp;Height=200" />
```


### Spécifier le rendu d'image dans le contrôle de champ image

Un développeur peut spécifier le rendu d'image à utiliser dans le contrôle de champ d'image. Utilisez la propriété **RenditionId** pour définir l'ID du rendu d'image. Pour plus d'informations, voir **RenditionId**.
  
    
    

## Détourage d'un rendu d'image
<a name="Crop"> </a>

Par défaut, un rendu d'image est généré à partir du centre de l'image. Vous pouvez régler le rendu d'image de chaque image en détourant la partie de l'image que vous souhaitez utiliser. Par exemple, si une photo illustre un paysage avec un phare mais que le rendu d'image n'affiche pas le phare en entier (voir Figure 1), vous pouvez modifier la zone d'image sélectionnée afin que le phare soit visible en entier (voir Figure 2). 
  
    
    

**Figure 1. Rendu d'image d'origine**

  
    
    

  
    
    
![Rendu d'image d'origine](images/ImgRendition_orig.PNG)
  
    
    

**Figure 2. Rendu d'image détouré**

  
    
    

  
    
    
![Rendu d'image rogné](images/ImgRendition_crop.PNG)
  
    
    
Pour détourer un rendu d'image, accédez à la bibliothèque de biens ou à une page, sans modifier l'image d'origine. 
  
    
    
Voici plusieurs manières de détourer les rendus d'image :
  
    
    

- Les concepteurs peuvent détourer un rendu d'image dans la bibliothèque de biens. Par exemple, un concepteur voudra peut-être spécifier la manière dont une image s'affichera dans le rendu d'image miniature.
    
  
- Les auteurs peuvent détourer un rendu d'image lorsqu'ils insèrent une image dans une page. Ainsi, ils peuvent personnaliser l'apparence de leur page. Lorsqu'un auteur détoure un rendu d'image, cela modifie également le rendu d'image de cette image. Toute personne utilisant le rendu d'image voit l'image détourée.
    
    > **REMARQUE**
      > Un auteur peut détourer un rendu d'image uniquement lorsque l'image d'origine est stockée dans une bibliothèque qui se trouve dans la même collection de sites que la page en cours de modification. Par exemple, dans les scénarios de publication intersites, un auteur peut détourer le rendu d'image uniquement si l'image est stockée dans la même collection de sites que le contenu du catalogue. Si ce n'est pas le cas, le rendu d'image doit être détouré dans la bibliothèque de biens. 

### Détourer un rendu d'image dans la bibliothèque de biens

Les concepteurs peuvent détourer un rendu d'image dans la bibliothèque de biens.
  
    
    

### Pour détourer un rendu d'image dans la bibliothèque de biens


1. Vérifiez que le compte d'utilisateur qui exécute cette procédure dispose des autorisations d'accès en écriture à la bibliothèque de biens où se trouve l'image.
    
  
2. Dans un navigateur, accédez à la bibliothèque de biens.
    
  
3. Placez le pointeur dans le coin inférieur droit de l'image dont vous souhaitez modifier le rendu, sélectionnez les points de suspension ( **...**) qui s'affichent, puis **MODIFIER LES RENDUS**.
    
    > **REMARQUE**
      > Vous pouvez également ouvrir la page **Modifier les rendus** en plaçant le pointeur sur l'aperçu de l'image dans la bibliothèque de biens, puis en cochant la case qui apparaît en bas de l'aperçu de l'image. Ensuite, dans l'onglet **Conception**, choisissez **Modifier les rendus**. 

    La page Modifier les rendus affiche l'aperçu d'une image pour chaque rendu d'image défini dans la collection de sites.
    
  
4. Identifiez le rendu d'image que vous souhaitez modifier, puis choisissez **Modifier**.
    
  
5. Dans la fenêtre **rogner le rendu**, utilisez l'outil d'image pour sélectionner la partie de l'image que vous souhaitez utiliser dans le rendu d'image.
    
  
6. Sélectionnez **Enregistrer**.
    
  
Si l'image et la page en cours de modification se trouvent dans la même collection de sites, vous pouvez également détourer un rendu d'image à l'aide de l'éditeur de texte enrichi.
  
    
    

### Détourer un rendu d'image sur une page

Les auteurs peuvent détourer un rendu d'image lorsqu'ils insèrent une image dans une page. Ainsi, ils peuvent personnaliser l'apparence de leur page. Lorsqu'un auteur détoure un rendu d'image, cela modifie également le rendu d'image de cette image. Toute personne utilisant le rendu d'image voit l'image détourée.
  
    
    

### Pour détourer un rendu d'image sur une page


1. Vérifiez que le compte d'utilisateur qui exécute cette procédure dispose des autorisations d'accès en écriture à la bibliothèque de biens où se trouve l'image.
    
  
2. Dans un navigateur, accédez au site SharePoint qui contient l'image.
    
  
3. Sur l'onglet **Page**, cliquez sur **Modifier**.
    
  
4. Sélectionnez l'image que vous souhaitez détourer.
    
  
5. Sur l'onglet **Image** du ruban, dans le groupe **Sélectionner**, choisissez **Choisir un rendu**, puis choisissez **Modifier les rendus**.
    
    La page **Modifier les rendus** affiche l'aperçu d'une image pour chaque rendu d'image défini dans la collection de sites.
    
    > **REMARQUE**
      > La commande **Choisir un rendu** est disponible uniquement pour les images qui sont stockées dans la même collection de sites que la page en cours de modification.
6. Identifiez le rendu d'image que vous souhaitez modifier, puis choisissez **Modifier**.
    
  
7. Dans la fenêtre **rogner le rendu**, utilisez l'outil d'image pour sélectionner la partie de l'image à utiliser dans le rendu d'image.
    
  
8. Sélectionnez **Enregistrer**.
    
  

## Suppression d'un rendu d'image
<a name="Delete"> </a>

Quand un rendu d'image est supprimé, ce rendu d'image n'est plus généré pour les images. Si un site demande le rendu d'image supprimé, l'image d'origine est renvoyée.
  
    
    

### Pour supprimer un rendu d'image


1. Vérifiez que le compte d'utilisateur qui exécute cette procédure dispose, au minimum, des autorisations de création pour le site de niveau supérieur de la collection de sites.
    
  
2. Dans un navigateur, accédez au site de niveau supérieur de la collection de sites de publication.
    
  
3. Choisissez l'icône **Paramètres**. Sur la page **Paramètres du site**, dans la section **Aspect**, choisissez **Rendus d'image**.
    
    > **REMARQUE**
      > La page **Rendus d'image** peut également être ouverte à partir de la page d'accueil par défaut du site de publication. Dans la section **Je suis le concepteur visuel**, choisissez **Configurer les rendus d'image**. 
4. Sur la page **Rendus d'image**, identifiez le rendu d'image que vous voulez supprimer, puis choisissez **Supprimer**.
    
  

## Ressources supplémentaires
<a name="Additional"> </a>


-  [Développer la conception de site dans SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Fonctionnalités de personnalisation et la conception de 2013 le gestionnaire de conception SharePoint](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  
-  [Créer des sites pour SharePoint](build-sites-for-sharepoint.md)
    
  

