---
title: Extraits de code du Gestionnaire de conception SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 68caef4c-5941-4a88-b34b-f88122801cef
---


# Extraits de code du Gestionnaire de conception SharePoint 2013
Un extrait de code est une représentation HTML d'un composant SharePoint ou d'un contrôle, par exemple une barre de navigation ou un composant WebPart. À l'aide de la galerie d'extraits de code dans le Gestionnaire de conception, vous pouvez rapidement ajouter des fonctionnalités SharePoint à votre page maître HTML ou à la mise en page.
## Présentation des extraits de code et de la galerie d'extraits de code
<a name="Introduction"> </a>

Une fois que vous avez converti une page maître ou créé une mise en page, vous disposez d'une version HTML de la page. Avec la galerie d'extraits de code, vous pouvez rapidement ajouter des fonctionnalités SharePoint spécifiques, par exemple la recherche ou la navigation ou bien les panneaux de canaux d'appareil, le fichier HTML associé à votre page maître ou à votre mise en page. La galerie d'extraits de code est une page dans le Gestionnaire de conception dans laquelle vous pouvez :
  
    
    

- Choisir un composant SharePoint dans ceux disponibles dans le ruban.
    
  
- Configurer les propriétés de ce composant.
    
  
- Afficher un aperçu de son apparence dans le navigateur.
    
  
- Copier l'extrait de code HTML dans le Presse-papiers afin de pouvoir le coller à l'emplacement souhaité dans le fichier HTML.
    
  
La galerie d'extraits de code affiche différentes options dans le ruban, selon que vous modifiez une page maître ou une mise en page. Par exemple, les contrôles de navigation sont affichés uniquement pour les pages maîtres et les zones de composant WebPart et les contrôles de champs de page sont affichés uniquement pour les mises en page. En outre, lorsque vous modifiez une mise en page, les champs de page disponibles dépendent du type de contenu de la mise en page que vous êtes en train de modifier.
  
    
    
Après avoir collé un extrait de code dans votre fichier HTML, vous obtenez un aperçu du code HTML fourni par l'extrait de code. Vous pouvez également utiliser l'aperçu côté serveur dans le Gestionnaire de conception pour voir comment le contrôle s'affiche sur le site en ligne. L'aperçu au moment de la conception peut inclure des exemples de données statiques, mais l'aperçu côté serveur utilise des données actives, le cas échéant. Par exemple, un contrôle de navigation qui extrait les liens de navigation d'un jeu de termes affiche ces termes de façon dynamique dans l'aperçu côté serveur, mais l'aperçu au moment de la conception présente un instantané statique des termes au moment où vous avez créé l'extrait de code. Les données en temps réel ne sont toutefois pas disponibles dans l'aperçu côté serveur pour certains extraits de code, par exemple pour les composants WebPart. Dans ce cas, l'aperçu côté serveur peut indiquer **Aperçu non disponible**.
  
    
    

> **REMARQUE**
> Un extrait de code contient des balises HTML qui vous offrent un aperçu de la conception dans votre éditeur HTML, mais les balises HTML dans les commentaires « début de l'aperçu » et « fin de l'aperçu » ne doivent pas être modifiées, car elles affectent uniquement l'aperçu au moment de la conception, et non la manière dont SharePoint assurera le rendu final de l'extrait de code. En revanche, pour appliquer un style à votre extrait de code, vous devez généralement identifier et remplacer les styles SharePoint par défaut qui sont appliqués à l'extrait de code. 
  
    
    


  
    
    

## Insertion d'un extrait de la galerie d'extraits de code
<a name="InsertSnippet"> </a>

La galerie d'extraits de code présente des options différentes en fonction du fichier que vous êtes en train de modifier. Par exemple, différentes mises en page disposent de différents jeux de champs de page. Pour cette raison, pour accéder à la galerie d'extraits de code, vous devez d'abord sélectionner une page maître ou une mise en page à modifier.
  
    
    

### Pour insérer un extrait de code


1. Accédez à votre site de publication.
    
  
2. Dans le coin supérieur droit de la page, sélectionnez l'icône d'engrenage de paramètres, puis choisissez **Gestionnaire de conception**.
    
  
3. Dans le Gestionnaire de conception, dans le volet de navigation de gauche, choisissez **Modifier les pages maîtres** ou **Modifier des mises en page**, en fonction du type de fichier que vous modifiez.
    
  
4. Sélectionnez le nom de la page maître ou de la mise en page à laquelle vous souhaitez ajouter l'extrait de code.
    
  
5. Pour ouvrir la galerie d'extraits de code, choisissez **Extraits de code** dans le coin supérieur droit de l'aperçu côté serveur.
    
  
6. Dans le ruban, dans l'onglet **Création**, cliquez sur l'extrait de code que vous souhaitez ajouter à votre page.
    
    Lorsque vous sélectionnez un extrait de code, la galerie d'extraits de code s'actualise afin que la page affiche un aperçu de cet extrait de code, les propriétés disponibles pour cet extrait de code, ainsi que l'extrait de code HTML que vous pouvez copier dans votre page maître HTML ou dans votre mise en page.
    
  
7. Sur le côté droit de la galerie d'extraits de code, sous **À propos de ce composant**, sélectionnez ou cliquez sur les en-têtes de section pour développer ou réduire les groupes de propriétés, puis configurez les paramètres personnalisés souhaités.
    
    Les propriétés les plus importantes pour l'objectif principal de l'extrait de code apparaissent dans la partie supérieure Important. Voici les principales propriétés que vous devez comprendre lorsque vous utilisez un extrait de code.
    
    
    
    > **REMARQUE**
      > Si la grille de propriétés possède un en-tête qui se termine par AjaxDelta, ignorez ces propriétés, car elles s'appliquent aux contrôles liés à la stratégie de téléchargement minimale, qui est désactivée pour les pages maîtres et les mises en page créées par le biais du Gestionnaire de conception. 
8. Après avoir configuré toutes les propriétés, choisissez **Mettre à jour**. Cela met à jour l'aperçu et l'extrait de code HTML sur le côté gauche de la page, de sorte que le balisage reflète vos paramètres personnalisés. Vous pouvez toujours choisir **Réinitialiser** pour restaurer toutes les propriétés sur leurs paramètres par défaut.
    
  
9. Sur le côté gauche de la galerie d'extraits de code, sous **Extrait de code HTML**, choisissez **Copier dans le Presse-papiers**.
    
  
10. Dans votre éditeur HTML, ouvrez le lecteur réseau mappé sur votre ordinateur, puis le fichier HTML de la page maître ou la mise en page à laquelle vous ajoutez l'extrait de code.
    
  
11. Dans le fichier HTML, collez l'extrait de code à l'endroit où vous souhaitez que le balisage s'affiche.
    
    Chaque extrait contient du code HTML qui fournit un aperçu visuel du composant, ainsi que des exemples de données. Vous ne devez pas modifier ce code HTML pour l'aperçu en lecture seule à l'intérieur des balises **<!--PS>** et **<!--PE>**, car ce balisage affecte uniquement l'aperçu au moment de la conception de l'extrait de code, et non la manière dont l'extrait de code s'affiche sur le site en ligne.
    
  
12. Pour afficher l'aperçu côté serveur de l'extrait de code, enregistrez le fichier HTML pour synchroniser les modifications apportées au fichier ASP.NET associé et actualisez l'aperçu côté serveur dans le Gestionnaire de conception.
    
    Contrairement à l'aperçu au moment de la création, l'aperçu côté serveur affiche le contrôle tel qu'affiché par SharePoint.
    
  

## Comprendre le balisage dans un extrait de code HTML
<a name="UnderstandMarkup"> </a>

Chaque extrait de code contient quatre sections de base :
  
    
    

- Un **En-tête** avec des balises de début **<div>** et de fin **<!--CS>** (à l'exception des extraits de code ASP.NET personnalisés, qui ne sont pas encapsulés dans une balise **<div>**)
    
  
- Le **balisage SharePoint**, dans lequel les extraits sont entourés de balises de début **<!--MS>** et de fin **<!--ME>**
    
  
- **Aperçu HTML** entre les balises de début **<!--PS>** et de fin **<!--PE>**
    
  
- **Pied de page** avec balises de fermeture **<!--CE>** et **</div>**
    
  
Toutes les sections de l'extrait de code, à l'exception de l'aperçu HTML, sont entourées de commentaires HTML pour éviter toute interaction avec le modèle DOM (Document Object Model) et les styles existants. L'extrait de code commence par le nom du composant, puis inclut sa balise ASP.NET réelle, un aperçu HTML pour le rendu au moment de la conception, puis les balises de fin. Le balisage ASP.NET est commenté, mais SharePoint supprime les balises de commentaire et utilise ce balisage lorsque le fichier HTML est synchronisé avec le fichier .master ou .aspx. Si vous connaissez ASP.NET, vous pouvez personnaliser ce balisage dans l'extrait de code.
  
    
    
Par exemple, voici le balisage par défaut Modifier le panneau des modes, qui est simplement un conteneur qui affiche en fonction des conditions un autre contenu et d'autres contrôles.
  
    
    

### En-tête


```HTML

<div data-name="EditModePanelShowInEdit">
    <!--CS: Start Edit Mode Panel Snippet-->
```


### Balisage SharePoint


```HTML

<!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### Aperçu du code HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
        <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Edit Mode Panel Properties.
    
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
```


### Pied de page


```HTML

<!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Edit Mode Panel Snippet-->
</div>
```

Voici le balisage par défaut pour un extrait de code de la navigation supérieure, qui est plus complexe, car cet extrait de code contient plusieurs contrôles différents, certains imbriqués les uns dans les autres, avec une source de données pour les termes de navigation, un contrôle délégué et un espace réservé au contenu.
  
    
    

> **REMARQUE**
> Certains contrôles, comme l'espace réservé au contenu, contiennent des balises vides pour un aperçu HTML, étant donné que cet élément ne requiert aucune représentation visuelle sur la page. 
  
    
    


### En-tête


```HTML

<div data-name="TopNavigationNoFlyoutWithStartNode">
<!--CS: Start Top Navigation Snippet-->    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### Balisage SharePoint


```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<SharePoint:AjaxDelta ID="DeltaTopNavigation" BlockElement="true" CssClass="ms-displayInline ms-core-navigation ms-dialogHidden" runat="server">-->
```


### Aperçu du code HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### Balisage SharePoint


```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
```


### Aperçu du code HTML


```HTML
<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<span style="display:none">
<table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow">
<tr><td nowrap="nowrap">
<span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span>
<!--PE: End of READ-ONLY PREVIEW-->
```


### Balisage SharePoint


```HTML

<!--MS:<Template_Controls>-->
<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
```


### Balisage SharePoint


```HTML

<!--ME:</asp:SiteMapDataSource>-->
<!--ME:</Template_Controls>-->
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>
```


### Balisage SharePoint


```HTML

<!--MS:<asp:ContentPlaceHolder ID="PlaceHolderTopNavBar" runat="server">-->
<!--MS:<SharePoint:AspMenu ID="TopNavigationMenu" runat="server" EnableViewState="false" DataSourceID="topSiteMap" AccessKey="&amp;#60;%$Resources:wss,navigation_accesskey%&amp;#62;" UseSimpleRendering="true" UseSeparateCss="false" Orientation="Horizontal" StaticDisplayLevels="2" AdjustForShowStartingNode="false" MaximumDynamicDisplayLevels="0" SkipLinkText="">-->
```


### Aperçu du code HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" />
<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
<ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
<li class="static">
<a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1">
<span class="additional-background ms-navedit-flyoutArrow">
<span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div>
<!--PE: End of READ-ONLY PREVIEW-->
```


### Balisage SharePoint


```HTML

<!--ME:</SharePoint:AspMenu>-->
<!--ME:</asp:ContentPlaceHolder>-->
```


### Aperçu du code HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### Balisage SharePoint


```HTML

<!--ME:</SharePoint:AjaxDelta>-->
```


### Pied de page


```HTML
<!--CE: End Top Navigation Snippet-->
</div>
```


### Types de balisage

Voici le détail des types de balises qui sont inclus dans les extraits de code.
  
    
    
 **Enregistrement d'espace de noms SharePoint :** la balise SPM (« balisage SharePoint ») indique une ligne pour l'enregistrement d'un espace de noms SharePoint.
  
    
    



```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
```

 **Commentaires :** les balises CS et CE (« début du commentaire » et « fin du commentaire ») vous aident à analyser les lignes de balisage.
  
    
    



```HTML
<!--CS: Start Top Navigation Snippet-->
…
<!--CE: End Top Navigation Snippet-->

```

 **Extraits de code :** les balises MS et ME (« début du balisage » et « fin du balisage ») indiquent le début et la fin du contrôle SharePoint ou de l'extrait de code. Certains extraits de code, comme le ruban ou le contrôle de navigation supérieure ci-dessus, contiennent plusieurs contrôles imbriqués dans un seul extrait de code.
  
    
    



```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
…
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>

<!--MS:<Template_Controls>-->
…
<!--ME:</Template_Controls>-->

<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
…
<!--ME:</asp:SiteMapDataSource>-->

```

 **Blocs d'aperçu :** les balises PS et PE (« début d'aperçu » et « fin d'aperçu ») entourent une section de code HTML à ne pas modifier. Ces sections d'aperçu sont une capture instantanée dans le temps du contrôle SharePoint inséré par cet extrait de code. L'aperçu vous permet d'utiliser de façon plus significative le fichier HTML dans un éditeur HTML côté client. Toutefois, la modification du contenu ou du style au sein de cet aperçu n'a pas d'effet durable sur le fichier .master, ce que SharePoint utilise, en fin de compte. Pour définir le style d'un extrait de code, vous devez identifier et remplacer les styles SharePoint avec vos propres feuilles CSS personnalisées.
  
    
    



```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><span style="display:none"><table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow"><tr><td nowrap="nowrap"><span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span><!--PE: End of READ-ONLY PREVIEW-->

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" /><div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox"><ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static"><li class="static"><a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1"><span class="additional-background ms-navedit-flyoutArrow"><span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div><!--PE: End of READ-ONLY PREVIEW-->
```


## Ressources supplémentaires
<a name="Resources"> </a>


-  [Procédure : Convertir un fichier HTML en page maître dans SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Comment : ajouter un extrait du panneau de configuration en Mode modifier dans SharePoint 2013](how-to-add-an-edit-mode-panel-snippet-in-sharepoint-2013.md)
    
  
-  [Comment : ajouter un fragment Trim de sécurité dans SharePoint 2013](how-to-add-a-security-trim-snippet-in-sharepoint-2013.md)
    
  

