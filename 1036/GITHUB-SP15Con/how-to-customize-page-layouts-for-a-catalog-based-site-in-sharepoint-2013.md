---
title: Comment personnaliser des mises en page pour un site de catalogue dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 21d8db99-73b3-4429-b6cb-04e375af9f55
---


# Comment personnaliser des mises en page pour un site de catalogue dans SharePoint 2013
Découvrez comment créer et personnaliser des mises en page de catégorie et d'élément de catalogue pour un site SharePoint Server 2013 de publication intersites.
## Conditions préalables à la création et la personnalisation de mises en page pour un site de catalogue
<a name="bk_prereqs"> </a>

Pour suivre les étapes décrites dans cet exemple, vous devez disposer des éléments suivants :
  
    
    

- un éditeur HTML ;
    
  
- un environnement de publication intersites SharePoint Server 2013.
    
  
Pour plus d'informations sur la façon de configurer un environnement de publication intersites SharePoint, voir  [Configuration de la publication intersites dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj656774.aspx).
  
    
    

### Concepts fondamentaux pour la création et la personnalisation de mises en page pour un site de catalogue

Le tableau 1 répertorie des articles utiles qui peuvent vous aider à comprendre les concepts et les étapes nécessaires à la création et la personnalisation de mises en page pour un site de catalogue.
  
    
    

**Tableau 1. Concepts fondamentaux pour la création et la personnalisation de mises en page pour un site de catalogue**


|**Titre de l'article**|**Description**|
|:-----|:-----|
| [Vue d'ensemble de la publication intersites dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj635883.aspx) <br/> |Découvrez comment utiliser la publication intersites et les composants WebPart de recherche pour créer des sites Internet, intranet et extranet SharePoint.  <br/> |
| [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) <br/> |Découvrez comment créer des mises en page dans SharePoint Server 2013.  <br/> |
| [Procédure : résoudre les erreurs et avertissements lors de l'aperçu d'une page en SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md) <br/> |Découvrez comment résoudre les problèmes qui empêchent l'aperçu côté serveur de rendre votre page.  <br/> |
| [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md) <br/> |Découvrez comment utiliser des extraits de code pour ajouter des fonctionnalités SharePoint à votre page maître HTML ou mise en page.  <br/> |
   

## Introduction aux mises en page de catégorie et d'élément de catalogue
<a name="bk_introduction"> </a>

Les pages de catégorie et les pages d'élément de catalogue sont des mises en page que vous pouvez utiliser pour afficher du contenu de catalogue structuré de manière cohérente sur un site. Par défaut, SharePoint Server 2013 peut créer automatiquement une mise en page de catégorie et une mise en page d'élément de catalogue par connexion de catalogue. Les pages basées sur ces mises en page sont créées dans la bibliothèque de pages d'un site de publication lorsque vous connectez le site à un catalogue. Pour plus d'informations sur les mises en page, voir  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md). Pour plus d'informations sur les fonctionnalités propres aux mises en page de catégorie et d'élément de catalogue, voir  [Vue d'ensemble de la publication intersites dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj635883.aspx).
  
    
    
Par défaut, les mises en page de catégorie et d'élément de catalogue sont créées automatiquement lorsque vous connectez un site de publication à un catalogue. Vous pouvez également utiliser le gestionnaire de conception pour créer des mises en page de catégorie et d'élément de catalogue que vous pouvez sélectionner lorsque vous connectez un site de publication à un catalogue, ou lorsque vous configurez le terme de navigation défini sur un site de publication.
  
    
    

## Création d'une mise en page de catégorie
<a name="bk_createCategoryPage"> </a>

Avant de créer ou personnaliser une mise en page de catégorie, nous vous recommandons de créer un lecteur réseau mappé qui pointe vers la **galerie de pages maîtres**. Pour plus d'informations, voir  [Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    
Le moyen le plus simple pour créer une mise en page de catégorie consiste à laisser SharePoint créer la mise en page automatiquement lorsque vous connectez le site de publication à un catalogue, pour ensuite personnaliser la mise en page de catégorie existante afin de modifier le balisage comme indiqué dans la conception de page. Vous pouvez également créer une mise en page de catégorie en partant de zéro à l'aide du gestionnaire de conception.
  
    
    

### Personnalisation d'une mise en page de catégorie existante qui a été créée automatiquement par SharePoint


1. À l'aide de l'Explorateur Windows, ouvrez le lecteur réseau mappé à la galerie de pages maîtres.
    
  
2. Pour personnaliser une mise en page de catégorie, modifiez le fichier HTML qui réside directement sur le serveur à l'aide d'un éditeur HTML afin d'ouvrir et de modifier le fichier HTML dans le lecteur mappé. Chaque fois que vous enregistrez le fichier HTML, toutes les modifications sont synchronisées sur le fichier .aspx associé.
    
  
3. Remplacez le balisage à l'intérieur de l'espace réservé de contenu comportant l'élément **id="PlaceHolderMain"** par le balisage que vous souhaitez utiliser dans la mise en page.
    
    > **IMPORTANTE**
      > Vous devez conserver le balisage de l'extrait de code de recherche de contenu afin que la page de catégorie puisse afficher les résultats de la recherche. 
4. Afin de configurer et copier le code HTML pour les extraits de code que vous souhaitez ajouter à la page, suivez les étapes 1 à 11 de la section « Création d'une mise en page » de l'article  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
5. Apportez toute autre modification requise au balisage, puis enregistrez le fichier.
    
  
6. Suivez les étapes 9 à 11 de la section « Création d'une mise en page » de l'article  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) pour vérifier le statut du fichier, afficher un aperçu de la mise en page et corriger les erreurs.
    
  

### Création d'une mise en page de catégorie à l'aide du gestionnaire de conception


1. Suivez les étapes 1 à 6 de la section « Création d'une mise en page » de l'article  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  
2. À l'étape 7, choisissez le type de contenu **Page d'article**.
    
  
3. Sélectionnez **OK**.
    
    À ce stade, SharePoint crée un fichier HTML et un fichier .aspx portant le même nom.
    
    Dans le gestionnaire de conception, votre fichier HTML apparaît désormais avec une colonne **Statut** indiquant l'un des deux statuts possibles :
    
  - Erreurs
    
  
  - **La conversion a réussi**
    
  
4. À l'aide de l'Explorateur Windows, ouvrez le lecteur réseau mappé à la galerie de pages maîtres.
    
  
5. Pour personnaliser la mise en page de catégorie, modifiez le fichier HTML qui réside directement sur le serveur à l'aide d'un éditeur HTML afin d'ouvrir et de modifier le fichier HTML dans le lecteur mappé. Chaque fois que vous enregistrez le fichier HTML, toutes les modifications sont synchronisées sur le fichier .aspx associé.
    
  
6. Dans le balisage **<head>**, remplacez l'espace réservé de contenu comportant l'élément **id="PlaceHolderPageTitle"** par :
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

7. Recherchez l'espace réservé de contenu comportant l'élément **id="PlaceHolderPageTitleInTitleArea"** et remplacez-le par :
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitleInTitleArea" runat="server">-->
<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

8. Remplacez le balisage à l'intérieur de l'espace réservé de contenu comportant l'élément **id="PlaceHolderMain"** par le balisage que vous souhaitez utiliser dans la mise en page.
    
  
9. Afin de configurer et copier le code HTML pour l'extrait de code de recherche de contenu et tout autre extrait de code que vous souhaitez ajouter à la page, suivez les étapes 1 à 11 de la section « Création d'une mise en page » de l'article  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
    > **REMARQUE**
      > Lorsque vous ajoutez l'extrait de code de recherche de contenu à la mise en page, veillez à modifier la requête afin d'utiliser la source de résultat qui a été créée lorsque vous avez connecté le site de publication à un catalogue. Pour plus d'informations, voir  [Configurer les origines des résultats pour la gestion du contenu web dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj715262.aspx). 
10. Apportez toute autre modification requise au balisage, puis enregistrez le fichier.
    
  
11. Suivez les étapes 9 à 11 de la section « Création d'une mise en page » de l'article  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) pour vérifier le statut du fichier, afficher un aperçu de la mise en page et corriger les erreurs.
    
  

## Présentation du balisage dans la mise en page de catégorie HTML
<a name="bk_CategoryPageMarkup"> </a>

Lorsque vous créez une mise en page, un fichier .aspx que SharePoint utilise est créé, et un balisage HTML est ajouté à la version HTML de la mise en page. Les mises en page de catégorie disposent de composants de balisage qui sont ajoutés à la mise en page selon la fonctionnalité de publication de collections intersites, et qui sont propres aux mises en page de catégorie. Lorsque vous modifiez la mise en page de catégorie HTML dans votre éditeur HTML, il peut être utile de comprendre une partie de ce balisage.
  
    
    

### Titre de la page de la fenêtre du navigateur

Le composant qui apparaît à l'intérieur de l'espace réservé de contenu avec l'élément **id="PlaceHolderPageTitle"** comporte un balisage qui indique à SharePoint d'utiliser une propriété de terme comme titre de page dans la fenêtre du navigateur, plutôt que la valeur du champ de page standard. Le code suivant affiche le balisage pour le titre de la page de la fenêtre du navigateur.
  
    
    

```HTML

<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
```


### Titre de la page

Le composant qui apparaît à l'intérieur de l'espace réservé de contenu avec l'élément **id="PlaceHolderPageTitleInTitleArea"** comporte un balisage qui indique à SharePoint d'utiliser une propriété de terme comme titre de page sur la page, plutôt que l'extrait de code **SPTitleBreadcrumb** et la valeur de champ de titre de page standard. Le code suivant affiche le balisage du titre de la page.
  
    
    

```HTML

<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->"
```


### Extrait de code de recherche de contenu

Les composants qui s'affichent après l'extrait de code de contenu de page, à l'intérieur de l'espace réservé de contenu avec l'élément **id="PlaceHolderMain"**, comportent un balisage pour un extrait de code de zone de composants WebPart qui contient les quatre zones de composants WebPart. La première zone contient un extrait de code de recherche de contenu qui affiche un composant WebPart de recherche de contenu sur la page. Cet extrait contient également des informations qui aident la requête du composant WebPart de recherche de contenu à demander une source de résultat et à afficher les résultats sur la page. Les trois dernières zones de composants WebPart sont vides. Si vous choisissez de créer votre propre mise en page de catégorie, vous devez inclure le balisage de l'extrait de code de recherche de contenu dans le fichier HTML correspondant à votre mise en page. Le code suivant affiche le balisage de l'extrait de code de recherche de contenu. Remplacez  _ResultSourceID_ par le GUID de la source de résultat, et remplacez l'élément _CatalogURL_par l'URL du catalogue.
  
    
    

> **REMARQUE**
> Les GUID pour **ID** et **__WebPartId** sont générés de façon aléatoire par SharePoint lorsque les extraits de code sont ajoutés à la mise en page.
  
    
    


```HTML
<!--
CS: Start Content Search Snippet-->
<!--SPM:<%@Register Tagprefix="a781102493" Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<a781102493:ContentBySearchWebPart runat="server" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;&amp;#34;,&amp;#34;SourceID&amp;#34;
:&amp;#34;ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;
{'Tag':'{Term.IDWithChildren}','Scope':'CatalogURL'}&amp;#34;}" ResultsPerPage="3" RenderTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Control_ListWithPaging.js" 
ItemTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Item_PictureOnTop.js" SelectedPropertiesJson="[&amp;#34;WorkId&amp;#34;,&amp;#34;Rank&amp;#34;,&amp;#34;Title&amp;#34;,&amp;#34;Author&amp;#34;,&amp;#34;
Size&amp;#34;,&amp;#34;Path&amp;#34;,&amp;#34;Description&amp;#34;,&amp;#34;Write&amp;#34;,&amp;#34;CollapsingStatus&amp;#34;,&amp;#34;
HitHighlightedSummary&amp;#34;,&amp;#34;HitHighlightedProperties&amp;#34;,&amp;#34;ContentClass&amp;#34;,&amp;#34;
PictureThumbnailURL&amp;#34;,&amp;#34;ServerRedirectedURL&amp;#34;,&amp;#34;ServerRedirectedEmbedURL&amp;#34;,&amp;#34;
ServerRedirectedPreviewURL&amp;#34;,&amp;#34;FileExtension&amp;#34;,&amp;#34;ContentTypeId&amp;#34;,&amp;#34;ParentLink&amp;#34;,&amp;#34;
ViewsLifeTime&amp;#34;,&amp;#34;ViewsRecent&amp;#34;,&amp;#34;SectionNames&amp;#34;,&amp;#34;SectionIndexes&amp;#34;,&amp;#34;
SiteLogo&amp;#34;,&amp;#34;SiteDescription&amp;#34;,&amp;#34;deeplinks&amp;#34;,&amp;#34;importance&amp;#34;]" ShouldHideControlWhenEmpty="True" FrameType="None" SuppressWebPartChrome="False" Description="$Resources:Microsoft.Office.Server.Search,CBS_Description;" IsIncluded="True" 
ZoneID="" PartOrder="0" FrameState="Normal" AllowRemove="True" AllowZoneChange="True" 
AllowMinimize="True" AllowConnect="True" AllowEdit="True" AllowHide="True" IsVisible="True" 
DetailLink="" HelpLink="" HelpMode="Modeless" Dir="Default" PartImageSmall="" IsIncludedFilter="" ExportControlledProperties="True" ConnectionID="00000000-0000-0000-0000-000000000000" ID="g_54e35103_6f29_4dd9_b93b_8d4c863834af" ChromeType="None" ExportMode="All" __MarkupType="vsattributemarkup" __WebPartId="54e35103-6f29-4dd9-b93b-8d4c863834af" 
WebPart="true" Height="" Width="" Title="$Resources:cms,WebPartZoneTitle_Dynamic;">-->
<!--ME:</a781102493:ContentBySearchWebPart>-->
<!--CE: End Content Search Snippet-->

```


## Création d'une mise en page d'élément de catalogue
<a name="bk_createCatItemPage"> </a>

Avant de créer ou personnaliser une mise en page d'élément de catalogue, nous vous recommandons de créer un lecteur réseau mappé qui pointe vers la galerie de pages maîtres. Pour plus d'informations, voir  [Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    
De la même manière qu'avec la mise en page de catégorie, le moyen le plus simple de créer une mise en page d'élément de catalogue consiste à laisser SharePoint créer la mise en page automatiquement lorsque vous connectez le site de publication à un catalogue, pour ensuite personnaliser la mise en page d'élément de catalogue existante afin d'ajouter tout balisage supplémentaire requis par la conception de page. Vous pouvez également créer une mise en page d'élément de catalogue en partant de zéro à l'aide du gestionnaire de conception.
  
    
    

### Personnalisation d'une mise en page d'élément de catalogue existante qui a été créée automatiquement par SharePoint


1. À l'aide de l'Explorateur Windows, ouvrez le lecteur réseau mappé à la galerie de pages maîtres.
    
  
2. Pour personnaliser une mise en page d'élément de catalogue, modifiez le fichier HTML qui réside directement sur le serveur à l'aide d'un éditeur HTML afin d'ouvrir et de modifier le fichier HTML dans le lecteur mappé. Chaque fois que vous enregistrez le fichier HTML, toutes les modifications sont synchronisées sur le fichier .aspx associé.
    
  
3. À l'intérieur de l'espace réservé de contenu comportant l'élément **id="PlaceHolderMain"**, ajoutez le balisage que vous souhaitez utiliser dans la mise en page.
    
  
4. Supprimez les extraits de code que vous ne souhaitez pas utiliser dans la mise en page et déplacez les extraits de code restants vers des emplacements au sein du balisage où vous souhaitez que les valeurs de propriété apparaissent.
    
    > **ATTENTION**
      > Par défaut, un extrait de code de zone de composants WebPart comportant un extrait de code de réutilisation de l'élément de catalogue est ajouté à la mise en page. Cet extrait de code contient le fournisseur de données qui renvoie les résultats de la requête qui sont utilisés par tous les autres extraits de code sur la page. Nous vous recommandons de conserver l'extrait de code de réutilisation de l'élément de catalogue dans cet extrait de code de zone de composants WebPart par défaut. (Vous pouvez déplacer l'extrait de code de réutilisation de l'élément de catalogue en dehors de la zone de composants WebPart, et vous pouvez modifier la propriété qui s'affiche. Toutefois, vous devez conserver l'extrait de code de réutilisation de l'élément de catalogue dans la mise en page.) Pour plus d'informations, voir  [Champs de page](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields), plus loin dans cet article. 
5. Afin de configurer et copier l'extrait de code HTML pour les extraits de code que vous souhaitez utiliser dans la page, suivez les étapes 1 à 11 de la section « Création d'une mise en page » de l'article  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
6. Apportez toute autre modification requise au balisage, puis enregistrez le fichier.
    
  
7. Suivez les étapes 9 à 11 de la section « Création d'une mise en page » de l'article  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) pour vérifier le statut du fichier, afficher un aperçu de la mise en page et corriger les erreurs.
    
  

### Création d'une mise en page d'élément de catalogue à l'aide du gestionnaire de conception


1. Suivez les étapes 1 à 6 de la section « Création d'une mise en page » de l'article  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  
2. À l'étape 7, choisissez **Catalogue distant**, puis sélectionnez le catalogue qui contient les données supposées s'afficher sur la page.
    
  
3. Sélectionnez **OK**.
    
    À ce stade, SharePoint crée un fichier HTML et un fichier .aspx portant le même nom.
    
    Dans le gestionnaire de conception, votre fichier HTML apparaît désormais avec une colonne **Statut** indiquant l'un des deux statuts possibles :
    
  - Erreurs
    
  
  - **La conversion a réussi**
    
  
4. À l'aide de l'Explorateur Windows, ouvrez le lecteur réseau mappé à la galerie de pages maîtres.
    
  
5. Pour personnaliser la mise en page d'élément de catalogue, modifiez le fichier HTML qui réside directement sur le serveur à l'aide d'un éditeur HTML afin d'ouvrir et de modifier le fichier HTML dans le lecteur mappé. Chaque fois que vous enregistrez le fichier HTML, toutes les modifications sont synchronisées sur le fichier .aspx associé.
    
  
6. À l'intérieur de l'espace réservé de contenu comportant l'élément **id="PlaceHolderMain"**, ajoutez le balisage que vous souhaitez utiliser dans la mise en page.
    
  
7. Supprimez les extraits de code que vous ne souhaitez pas utiliser dans la mise en page et déplacez les extraits de code restants vers des emplacements au sein du balisage où vous souhaitez que les valeurs de propriété apparaissent.
    
    > **ATTENTION**
      > Par défaut, un extrait de code de zone de composants WebPart comportant un extrait de code de réutilisation de l'élément de catalogue est ajouté à la mise en page. Cet extrait de code contient le fournisseur de données qui renvoie les résultats de la requête qui sont utilisés par tous les autres extraits de code sur la page. Nous vous recommandons de conserver l'extrait de code de réutilisation de l'élément de catalogue dans cet extrait de code de zone de composants WebPart par défaut. (Vous pouvez déplacer l'extrait de code de réutilisation de l'élément de catalogue en dehors de la zone de composants WebPart, et vous pouvez modifier la propriété qui s'affiche. Toutefois, vous devez conserver l'extrait de code de réutilisation de l'élément de catalogue dans la mise en page.) Pour plus d'informations, voir  [Champs de page](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields), plus loin dans cet article. 
8. Afin de configurer et copier l'extrait de code HTML pour les extraits de code que vous souhaitez utiliser dans la page, suivez les étapes 1 à 11 de la section « Création d'une mise en page » de l'article  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
9. Apportez toute autre modification requise au balisage, puis enregistrez le fichier.
    
  
10. Suivez les étapes 9 à 11 de la section « Création d'une mise en page » de l'article  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) pour vérifier le statut du fichier, afficher un aperçu de la mise en page et corriger les erreurs.
    
  

## Présentation du balisage dans la mise en page d'élément de catalogue HTML
<a name="bk_CatItemMarkup"> </a>

Lorsque vous créez une mise en page, un fichier .aspx que SharePoint utilise est créé, et un balisage HTML est ajouté à la version HTML de la mise en page. Les mises en page d'élément de catalogue disposent de composants de balisage qui sont ajoutés à la mise en page selon la fonctionnalité de publication de collections intersites, et qui sont propres aux mises en page d'élément de catalogue. Lorsque vous modifiez la mise en page d'élément de catalogue HTML dans votre éditeur HTML, il peut être utile de comprendre une partie de ce balisage.
  
    
    

### Titre de la page de la fenêtre du navigateur

Le composant qui apparaît à l'intérieur de l'espace réservé de contenu avec l'élément **id="PlaceHolderPageTitle"** comporte un extrait de code de réutilisation de l'élément de catalogue qui indique à SharePoint d'utiliser le nom de l'élément de catalogue comme titre de page dans la fenêtre du navigateur, plutôt que la valeur du champ de page standard. Le code suivant affiche le balisage pour le titre de la page de la fenêtre du navigateur.
  
    
    

> **REMARQUE**
> Les GUID pour **ID** et **__WebPartId** sont générés de façon aléatoire par SharePoint lorsque les extraits de code sont ajoutés à la mise en page.
  
    
    


```HTML

<!--CS: [Title] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_863912c1_c849_46dc_8781_2920ee2bc83f" __WebPartId="{863912c1-c849-46dc-8781-2920ee2bc83f}">-->
<!--SPM:<RenderFormat>-->
<!--DC:Renders value from search without any additional formatting.-->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->

```


### Champs de page
<a name="bk_pagefields"> </a>

Les composants qui s'affichent à l'intérieur de l'espace réservé de contenu avec l'élément **id="PlaceHolderMain"** contiennent des extraits de code pour les champs **Title**, **Page Content** et **Catalog-Item URL**. Vous pouvez supprimer l'un de ces extraits de code de la mise en page. Le code suivant illustre le balisage de ces champs de page.
  
    
    

```HTML

<div>
    <!--CS: Start Page Field: Title Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldTextField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
        <!--MS:<PageFieldTextField:TextField FieldName="fa564e0f-0c70-4ab9-b863-0177e6ddd247" 
runat="server">-->
        <!--ME:</PageFieldTextField:TextField>-->
    <!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Page Field: Title Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Page Content Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldRichHtmlField:RichHtmlField FieldName="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" runat="server">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
            <div id="ctl02_label" style="display:none">Page Content</div>
            <div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label">
                <div align="left" class="ms-formfieldcontainer">
                    <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                        <span class="ms-formfieldlabel" nowrap="nowrap">Page Content</span>
                    </div>
                    <div class="ms-formfieldvaluecontainer">
                        <div class="ms-rtestate-field">Page Content field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
                    </div>
                </div>
            </div>
        <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
    <!--CE: End Page Field: Page Content Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Catalog-Item URL Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldCatalogSourceFieldControl" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl FieldName="75772bbf-0c25-4710-b52c-7b78344ad136" runat="server">-->
    <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
        <div align="left" class="ms-formfieldcontainer">
            <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                <span class="ms-formfieldlabel" nowrap="nowrap">Catalog-Item URL</span>
            </div>
            <div class="ms-formfieldvaluecontainer">
                <a href="http://www.example.com">Link to sample web site.</a>
            </div>
        </div>
    <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl>-->
    <!--CE: End Page Field: Catalog-Item URL Snippet-->
</div>

```

Si la page d'élément de catalogue a été créée automatiquement lorsque le site de publication a été connecté à un catalogue, ou lorsqu'il a été créé en sélectionnant un catalogue distant lors de la création de la mise en page, la mise en page contient également un extrait de code de zone de composants WebPart qui contient un extrait de code de réutilisation de l'élément de catalogue qui enregistre un fournisseur de données pour la page. L'extrait de code de réutilisation de l'élément de catalogue contient une propriété **UseSharedDataProvider** qui est définie sur **False**. L'extrait de code de zone de composants WebPart peut être supprimé de la mise en page. Toutefois, l'extrait de code de réutilisation de l'élément de catalogue doit être conservé dans le balisage de la mise en page pour que la page puisse afficher les éléments de catalogue. Lorsque vous créez une page qui utilise cette mise en page, vous pouvez configurer le composant WebPart afin qu'il soit masqué lorsqu'un utilisateur consulte la page.
  
    
    

> **IMPORTANTE**
> Si vous créez une mise en page d'élément de catalogue et que vous choisissez un type de contenu au lieu d'un catalogue distant, vous devez inclure un extrait de code de réutilisation de l'élément de catalogue dans la mise en page. Le code suivant présente le balisage pour l'extrait de code de réutilisation de l'élément de catalogue tel qu'il apparaît dans l'extrait de code de zone de composants WebPart. Remplacez  _ManagedPropertyName_ par le nom de la propriété gérée à afficher, remplacez _ResultSourceID_ par le GUID de la source des résultats, et remplacez _CatalogURL_ par l'URL du catalogue.
  
    
    




```HTML

<div>
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="cc1"  Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
    <!--MS:<WebPartPages:WebPartZone runat="server" Title="&amp;#60;%$Resources:cms,WebPartZoneTitle_Body%&amp;#62;" AllowPersonalization="False" FrameType="TitleBarOnly" ID="Body" Orientation="Vertical">-->
        <!--MS:<ZoneTemplate>-->
            <!--CS: [ManagedPropertyName] Start Catalog-Item Reuse Snippet-->
            <!--DC:To render the search property using a rendering template, change the "UseServerSideRenderFormat" property to "False".-->
            <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" AddSEOPropertiesFromSearch="True" LogAnalyticsViewEvent="True" UseSharedDataProvider="False" OverwriteResultPath="False" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;ListItemID:{URLTOKEN.1}&amp;#34;,&amp;#34;SourceID&amp;#34;:&amp;#34; ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;{&amp;#39;Scope&amp;#39;:&amp;#39;  CatalogURL&amp;#39;,&amp;#39;Tag&amp;#39;:&amp;#39;{Term}&amp;#39;}&amp;#34;}" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;ManagedPropertyName&amp;#34;]" Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" MissingAssembly="Cannot import this Web Part." ID="g_d63eebe7_207f_4e8c_9566_7381acc80cc7" __WebPartId="{d63eebe7-207f-4e8c-9566-7381acc80cc7}">-->
            <!--SPM:<RenderFormat>-->
            <!--DC:Renders value from search without any additional formatting.-->
            <!--SPM:</RenderFormat>-->
            <!--SPM:</cc1:CatalogItemReuseWebPart>-->
        <!--ME:</ZoneTemplate>-->
    <!--ME:</WebPartPages:WebPartZone>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

Si la mise en page d'élément de catalogue a été créée automatiquement lorsque le site de publication a été connecté à un catalogue, ou lorsqu'il a été créé en sélectionnant un catalogue distant lors de la création de la mise en page, le reste de la page contient des extraits de code de réutilisation de l'élément de catalogue qui correspondent aux propriétés gérées provenant du catalogue sur le site de création. Ces propriétés gérées affichent les détails de l'élément de catalogue spécifique qui s'affiche à l'aide de la mise en page d'élément de catalogue. Ces extraits de code de réutilisation de l'élément de catalogue apparaissent en dehors de la zone de composants WebPart et sont rendus directement sur la page lorsque vous sélectionnez un élément sur une page de catégorie. Le tableau 2 répertorie les propriétés gérées qui sont automatiquement incluses dans la mise en page d'élément de catalogue.
  
    
    

> **REMARQUE**
> Certaines propriétés gérées sont incluses uniquement si le catalogue est une bibliothèque de pages. La colonne **Utilisateur** dans le tableau 2 indique les propriétés gérées qui sont utilisées à la fois par une bibliothèque de pages et une liste, et celles qui proviennent d'une bibliothèque de pages uniquement.
  
    
    


**Tableau 2. Extraits de code de réutilisation de l'élément de catalogue de propriétés gérées par défaut**


|**Propriété gérée**|**Description**|**Utilisateur**|
|:-----|:-----|:-----|
|**AuthorOWSUSER** <br/> |Nom de l'utilisateur qui a créé la page.  <br/> |Bibliothèque de pages uniquement  <br/> |
|**CreatedOWSDATE** <br/> |Date de création de l'élément de liste ou de page.  <br/> |Liste et bibliothèque de pages  <br/> |
|**EditorOWSUSER** <br/> |Nom de l'utilisateur qui a modifié l'élément de liste ou de page.  <br/> |Liste et bibliothèque de pages  <br/> |
|**ListItemID** <br/> |ID de l'élément de liste ou de page.  <br/> |Liste et bibliothèque de pages  <br/> |
|**ModifiedOWSDATE** <br/> |Date de la dernière modification de l'élément de liste ou de page.  <br/> |Liste et bibliothèque de pages  <br/> |
|**PublishingContactOWSUSER** <br/> |Contact est une colonne de site créée par la fonctionnalité de publication. Cet élément est utilisé sur le type de contenu de page en tant que la personne ou le groupe qui est le contact pour la page.  <br/> |Bibliothèque de pages uniquement  <br/> |
|**PublishingIsFurlPageOWSBOOL** <br/> |Valeur booléenne qui indique si la page est associée à une URL conviviale.  <br/> |Bibliothèque de pages uniquement  <br/> |
|**PublishingPageContentOWSHTML** <br/> |Contenu HTML de la page.  <br/> |Bibliothèque de pages uniquement  <br/> |
|**PublishingPageLayoutOWSURLH** <br/> |URL vers la mise en page utilisée pour créer la page.  <br/> |Bibliothèque de pages uniquement  <br/> |
|**Title** <br/> |Titre de l'élément de liste ou de la page.  <br/> |Liste et bibliothèque de pages  <br/> |
   
Les propriétés gérées pour les colonnes personnalisées que vous ajoutez à la liste ou la bibliothèque de pages sont également incluses dans les extraits de code de réutilisation de l'élément de catalogue. Le nom de la propriété gérée varie en fonction du type de colonne de site que vous utilisez lorsque vous créez la colonne de site. Pour plus d'informations, voir  [Propriétés gérées créées automatiquement dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj613136.aspx) et [Vue d'ensemble du schéma de recherche dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj219669.aspx).
  
    
    

> **IMPORTANTE**
> La colonne de site **Page Image** dans une bibliothèque de pages est mappée à la propriété gérée **PublishingImage**. Toutefois, la propriété gérée **PublishingImage** n'est pas automatiquement incluse dans la mise en page d'élément de catégorie. Pour inclure l'image dans votre mise en page, vous devez ajouter un extrait de code de réutilisation de l'élément de catalogue pour la propriété gérée **PublishingImage**. Le code HTML suivant permet d'ajouter un extrait de code de réutilisation de l'élément de catalogue pour afficher la valeur de la propriété gérée **PublishingImage** dans votre mise en page. Remplacez _UniqueID_ par un GUID unique à chaque instance de l'extrait de code.
  
    
    




```HTML

<div>
<!--CS: [PublishingImage] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingImage&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_UniqueID" __WebPartId="{UniqueID}">-->
<!--SPM:<RenderFormat>-->
<!--SPM:<Format Type="HTML"> -->
<!--SPM:<Picture>-->True<!--SPM:</Picture>-->
<!--SPM:</Format> -->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

Si vous créez une mise en page d'élément de catalogue à l'aide du gestionnaire de conception et que vous choisissez un type de contenu au lieu d'un catalogue distant, vous pouvez ajouter des extraits de code de réutilisation de l'élément de catalogue à la page à l'aide de la galerie d'extraits de code. Le code suivant illustre le balisage pour les extraits de code de réutilisation de l'élément de catalogue pour les propriétés gérées **Title**, **PublishingPageContentOWSHTML**, **CreatedOWSDATE** et **owstaxIdPageCategory**.
  
    
    

> **REMARQUE**
> Les GUID pour **ID** et **__WebPartId** sont générés de façon aléatoire par SharePoint lorsque les extraits de code sont ajoutés à la mise en page.
  
    
    




```HTML

<div>
    <!--CS: [Title] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_0dc23bb8_8d34_4f9f_8085_5a6ac286cb9e" 
__WebPartId="{0dc23bb8-8d34-4f9f-8085-5a6ac286cb9e}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [PublishingPageContentOWSHTML] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingPageContentOWSHTML&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_25253a49_a9a6_4277_bf9d_416961024cee" 
__WebPartId="{25253a49-a9a6-4277-bf9d-416961024cee}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [CreatedOWSDATE] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;CreatedOWSDATE&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." 
ID="g_4e1f180b_12f8_4e50_84d7_c72b0ee3793f" 
__WebPartId="{4e1f180b-12f8-4e50-84d7-c72b0ee3793f}">-->
    <!--SPM:<RenderFormat>-->
    <!--SPM:<Format Type="DateTime"> -->
    <!--DC:To render Date and Time, change this value to False.-->
    <!--SPM:<DateOnly>-->True<!--SPM:</DateOnly>-->
    <!--SPM:</Format> -->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [owstaxIdPageCategory] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;owstaxIdPageCategory&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_22e39e9d_1b25_42c7_bf2a_7ebca37616d4" 
__WebPartId="{22e39e9d-1b25-42c7-bf2a-7ebca37616d4}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```


## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Développer la conception de site dans SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Vue d'ensemble du gestionnaire de conception dans SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Vue d'ensemble du modèle de page SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Modèles d'affichage du gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-display-templates.md)
    
  

