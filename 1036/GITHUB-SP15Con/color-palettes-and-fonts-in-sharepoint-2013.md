---
title: Palettes de couleurs et polices dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c17d375b-151f-48ae-ac32-f2ce9e68d63f
---


# Palettes de couleurs et polices dans SharePoint 2013
Utilisez cette référence pour définir la palette de couleurs et le jeu de polices utilisés dans un site SharePoint 2013.
## Palettes de couleurs
<a name="color"> </a>

Une palette de couleurs représente la combinaison de couleurs qui sont utilisées dans un site SharePoint. La palette de couleurs pour un site SharePoint est définie dans un fichier de palette de couleurs. Les emplacements de couleurs sont également utilisés par le fichier d'aperçu de la page maître afin de générer la miniature et de prévisualiser les images d'un site. Cette rubrique décrit la structure du fichier de palette de couleurs et du fichier d'aperçu de la page maître :
  
    
    

- **Fichier de palette de couleurs (.spcolor)**
    
Les fichiers de palette de couleurs sont utilisés dans l'Assistant **Modifier l'apparence**. Ce dernier permet aux utilisateurs de changer l'apparence de leur site à l'aide de l'interface utilisateur des thèmes SharePoint. Par défaut, 32 fichiers de palette de couleurs sont installés avec SharePoint 2013. Vous pouvez également créer des fichiers de palette de couleurs supplémentaires. L'exemple suivant illustre le format d'un fichier de palette de couleurs.
    


    ```XML
  
    <s:colorPalette isInverted="InvertedSetting" previewSlot1="Slot1" previewSlot2="Slot2" previewSlot3="Slot3" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:color name="ColorSlot" value="Color" />
    <!--additional color slots-->
    </s:colorPalette>
    ```


Dans un fichier de palette de couleurs, les espaces réservés suivants sont remplacés :
    
-  _InvertedSetting_ est une valeur booléenne. Elle indique **true** si la palette de couleurs définit un texte plutôt clair sur un arrière-plan sombre, **false** si la palette de couleurs définit un texte plutôt foncé sur un fond clair.
    
  
-  _Slot1_ est le nom de l'annotation de l'emplacement de couleur à utiliser comme premier bloc de l'icône de palette dans le sélecteur de couleurs de la palette lors de la création d'un thème.
    
  
-  _Slot2_ est le nom de l'annotation de l'emplacement de couleur à utiliser comme deuxième bloc de l'icône de palette dans le sélecteur de couleurs de la palette lors de la création d'un thème.
    
  
-  _Slot3_ est le nom de l'annotation de l'emplacement de couleur à utiliser comme troisième bloc de l'icône de palette dans le sélecteur de couleurs de la palette lors de la création d'un thème.
    
  
-  _ColorSlot_ est le nom de l'annotation de l'emplacement de couleur que vous définissez (par exemple, SiteTitle).
    
  
-  _Color_ est la valeur hexadécimale de la couleur à utiliser pour l'emplacement de couleur spécifié. Celle-ci peut être composée de 6 chiffres (RRVVBB) ou de 8 chiffres (AARRVVBB). Si la valeur hexadécimale est composée de 8 chiffres, les deux premiers représentent le niveau d'opacité (00-FF correspond à 0-255). Si la valeur hexadécimale est composée de 6 chiffres, l'opacité par défaut est de 100 % ou FF.
    
  

Les fichiers de palette de couleurs sont situés dans la galerie de thèmes du site racine, dans le dossier **15** de la collection de sites (http:// _ SiteCollectionName_ /_catalogs/theme/15 /). Pour accéder à la galerie de thèmes à partir de l'interface utilisateur de SharePoint, ouvrez la page **Paramètres du site**, puis, sous **Galeries du concepteur web**, sélectionnez **Thèmes**, puis **15**.
    
  
- **Fichier d'aperçu de la page maître (.preview)**
    
Les fichiers d'aperçu de la page maître permettent de générer des images miniatures et de prévisualiser les images lorsque vous utilisez l'Assistant **Modifier l'apparence**. Pour pouvoir être utilisée dans l'Assistant **Modifier l'apparence**, une page maître doit être associée à un fichier d'aperçu. Un fichier d'aperçu est un fichier au format spécial qui présente des sections définissant la palette de couleurs par défaut, le jeu de polices par défaut, les fichiers CSS tokenisés et les fichiers HTML tokenisés. Il utilise les jetons de chaîne pour obtenir la valeur des emplacements de couleur, des noms de police et des chaînes d'interface utilisateur localisées. L'exemple suivant présente les emplacements de couleur utilisés dans le fichier d'aperçu de la page maître.
    


    ```HTML
  
[ID] #dgp-pageContainer
{
    background-color: [T_THEME_COLOR_PAGEBACKGROUND];
    color: [T_THEME_COLOR_BODYTEXT];
    width: 100%;
    height:100%;     
    background-image: url('[T_IMAGE]');       
    background-size: cover;
    font-family: [T_BODY_FONT];   
}
    ```


Pour plus d'informations, voir  [Comment créer un fichier d'aperçu de page maître dans SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md).
    
  

> **CONSEIL**
> Vous pouvez utiliser la palette de couleurs SharePoint pour vous aider à créer des conceptions SharePoint. Vous pouvez  [télécharger la palette de couleurs SharePoint](http://www.microsoft.com/en-us/download/details.aspx?id=38182) dans le Centre de téléchargement Microsoft.
  
    
    


### Mappage des emplacements de couleur
<a name="colorSlots"> </a>

Le tableau 1 décrit les emplacements de couleur disponibles et les endroits où ils sont utilisés dans un site SharePoint.
  
    
    

> **REMARQUE**
>  Lorsque nous parlons des éléments de navigation,Pressed (appuyé) signifie qu'un utilisateur clique sur un élément ou le touche.Selected (sélectionné) signifie qu'un utilisateur accède à la page.>  Ce qui suit résume une suite d'actions logiques et l'emplacement de couleur qui s'applique au lien de l'élément de navigation à chaque étape :>  Texte de base d'un lien de l'élément de navigation : HeaderNavigationText>  L'utilisateur passe le curseur sur le lien de l'élément de navigation : HeaderNavigationHoverText>  L'utilisateur clique sur le lien de l'élément de navigation, le touche ou le choisit : HeaderNavigationPressedText>  L'utilisateur accède à la page choisie. Emplacement de couleur qui s'applique à l'élément de navigation pour la page sur laquelle se trouve l'utilisateur : HeaderNavigationSelectedText
  
    
    


**Tableau 1. Emplacements de couleur**


|**Nom de l'annotation**|**Emplacement où la couleur est utilisée dans l'interface utilisateur**|**Nom du jeton**|
|:-----|:-----|:-----|
|BodyText  <br/> |Corps de texte normal.  <br/> |[T_THEME_COLOR_BODYTEXT]  <br/> |
|SubtleBodyText  <br/> |Corps de texte qui doit être plus clair que la normale (texte des métadonnées, par exemple).  <br/> |[T_THEME_COLOR_SUBTLEBODYTEXT]  <br/> |
|StrongBodyText  <br/> |Couleur du corps de texte pour du contenu qui doit se détacher du corps de texte normal.  <br/> |[T_THEME_COLOR_STRONGBODYTEXT]  <br/> |
|DisabledText  <br/> |Texte désactivé (éléments non disponibles dans un menu, par exemple).  <br/> |[T_THEME_COLOR_DISABLEDTEXT]  <br/> |
|SiteTitle  <br/> |Couleur du texte du titre de la page.  <br/> |[T_THEME_COLOR_SITETITLE]  <br/> |
|WebPartHeading  <br/> |Couleur du texte des titres des composants WebPart.  <br/> |[T_THEME_COLOR_WEBPARTHEADING]  <br/> |
|ErrorText  <br/> |Couleur principale utilisée pour du texte, des bordures et des arrière-plans se rapportant à des erreurs, le cas échéant.  <br/> |[T_THEME_COLOR_ERRORTEXT]  <br/> |
|AccentText  <br/> |Couleur du corps de texte accentué.  <br/> |[T_THEME_COLOR_ACCENTTEXT]  <br/> |
|SearchURL  <br/> |Couleur du texte des URL dans les résultats de recherche. Permet également de mettre en évidence de nouveaux éléments ou des notifications d'état réussies.  <br/> |[T_THEME_COLOR_SEARCHURL]  <br/> |
|Hyperlink  <br/> |Couleur du texte des liens hypertexte.  <br/> |[T_THEME_COLOR_HYPERLINK]  <br/> |
|HyperlinkFollowed  <br/> |Couleur du texte des liens hypertexte suivis.  <br/> |[T_THEME_COLOR_HYPERLINKFOLLOWED]  <br/> |
|HyperlinkActive  <br/> |Couleur d'un lien hypertexte lorsqu'un utilisateur appuie dessus.  <br/> |[T_THEME_COLOR_HYPERLINKACTIVE]  <br/> |
|CommandLinks  <br/> |Liens de commande longs qui doivent être légèrement plus clairs que le corps du texte en raison de leur taille.  <br/> |[T_THEME_COLOR_COMMANDLINKS]  <br/> |
|CommandLinksSecondary  <br/> |Couleur des liens de commande plus petits qui nécessitent une couleur plus foncée pour être plus facilement distingués.  <br/> |[T_THEME_COLOR_COMMANDLINKSSECONDARY]  <br/> |
|CommandLinksHover  <br/> |Couleur d'un lien de commande lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_COMMANDLINKSHOVER]  <br/> |
|CommandLinksPressed  <br/> |Couleur d'un lien de commande lorsqu'un utilisateur appuie dessus.  <br/> |[T_THEME_COLOR_COMMANDLINKSPRESSED]  <br/> |
|CommandLinksDisabled  <br/> |Couleur d'un lien de commande désactivé.  <br/> |[T_THEME_COLOR_COMMANDLINKSDISABLED]  <br/> |
|BackgroundOverlay  <br/> |Couleur d'arrière-plan principale, visible entre l'image d'arrière-plan facultative et le contenu de la page.  <br/> |[T_THEME_COLOR_BACKGROUNDOVERLAY]  <br/> |
|DisabledBackground  <br/> |Arrière-plan des éléments désactivés tels que les contrôles de navigateur, par exemple, la zone d'entrée ou la zone de sélection (sauf les boutons).  <br/> |[T_THEME_COLOR_DISABLEDBACKGROUND]  <br/> |
|PageBackground  <br/> |Couleur d'arrière-plan de la page. Apparaît derrière l'image d'arrière-plan facultative.  <br/> |[T_THEME_COLOR_PAGEBACKGROUND]  <br/> |
|HeaderBackground  <br/> |Couleur d'arrière-plan de la zone d'en-tête de la page.  <br/> |[T_THEME_COLOR_HEADERBACKGROUND]  <br/> |
|FooterBackground  <br/> |Couleur d'arrière-plan de la zone de pied de page.  <br/> |[T_THEME_COLOR_FOOTERBACKGROUND]  <br/> |
|SelectionBackground  <br/> |Couleur d'arrière-plan des éléments de liste sélectionnés et des éléments de menu déroulant.  <br/> |[T_THEME_COLOR_SELECTIONBACKGROUND]  <br/> |
|HoverBackground  <br/> |Couleur d'arrière-plan des éléments de liste et des éléments de menu déroulant lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_HOVERBACKGROUND]  <br/> |
|RowAccent  <br/> |Bordure gauche accentuée pour les éléments de liste sélectionnés.  <br/> |[T_THEME_COLOR_ROWACCENT]  <br/> |
|StrongLines  <br/> |Bordures des contrôles de navigateur lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_STRONGLINES]  <br/> |
|Lines  <br/> |Bordures des contrôles de navigateur.  <br/> |[T_THEME_COLOR_LINES]  <br/> |
|SubtleLines  <br/> |Couleur de bordure discrète (quadrillage pour la modification intraligne, par exemple).  <br/> |[T_THEME_COLOR_SUBTLELINES]  <br/> |
|DisabledLines  <br/> |Couleur de bordure des contrôles de navigateur désactivés tels que les zones d'entrée et les zones de sélection.  <br/> |[T_THEME_COLOR_DISABLEDLINES]  <br/> |
|AccentLines  <br/> |Couleur de bordure active des contrôles de navigateur sélectionnés.  <br/> |[T_THEME_COLOR_ACCENTLINES]  <br/> |
|DialogBorder  <br/> |Couleur de bordure des boîtes de dialogue.  <br/> |[T_THEME_COLOR_DIALOGBORDER]  <br/> |
|Navigation  <br/> |Couleur du texte des éléments de navigation verticale et horizontale.  <br/> |[T_THEME_COLOR_NAVIGATION]  <br/> |
|NavigationAccent  <br/> |Couleur du texte d'un élément de navigation horizontale sélectionné.  <br/> |[T_THEME_COLOR_NAVIGATIONACCENT]  <br/> |
|NavigationHover  <br/> |Couleur du texte de navigation lorsqu'un utilisateur passe le curseur dessus. S'applique à la navigation supérieure et au menu de lancement rapide en mode horizontal.  <br/> |[T_THEME_COLOR_NAVIGATIONHOVER]  <br/> |
|NavigationPressed  <br/> |Couleur du texte de l'élément de navigation lorsqu'un utilisateur appuie dessus. S'applique à la navigation supérieure et au menu de lancement rapide en mode horizontal.  <br/> |[T_THEME_COLOR_NAVIGATIONPRESSED]  <br/> |
|NavigationHoverBackground  <br/> |Couleur d'arrière-plan des éléments du menu de lancement rapide en mode vertical lorsqu'un utilisateur passe le curseur sur l'élément de navigation.  <br/> |[T_THEME_COLOR_NAVIGATIONHOVERBACKGROUND]  <br/> |
|NavigationSelectedBackground  <br/> |Couleur d'arrière-plan des éléments du menu de lancement rapide en mode vertical après qu'un utilisateur a sélectionné l'élément de navigation.  <br/> |[T_THEME_COLOR_NAVIGATIONSELECTEDBACKGROUND]  <br/> |
|EmphasisText  <br/> |Couleur du texte affiché par-dessus l'arrière-plan d'accentuation.  <br/> |[T_THEME_COLOR_EMPHASISTEXT]  <br/> |
|EmphasisBackground  <br/> |Couleur de l'arrière-plan accentué qui apparaît directement derrière le texte d'accentuation.  <br/> |[T_THEME_COLOR_EMPHASISBACKGROUND]  <br/> |
|EmphasisHoverBackground  <br/> |Couleur de l'arrière-plan lorsqu'un utilisateur passe le curseur dessus, pour les éléments qui utilisent un arrière-plan d'accentuation.  <br/> |[T_THEME_COLOR_EMPHASISHOVERBACKGROUND]  <br/> |
|EmphasisBorder  <br/> |Couleur de bordure des éléments qui utilisent un arrière-plan d'accentuation.  <br/> |[T_THEME_COLOR_EMPHASISBORDER]  <br/> |
|EmphasisHoverBorder  <br/> |Couleur de bordure des éléments qui utilisent un arrière-plan d'accentuation lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_EMPHASISHOVERBORDER]  <br/> |
|SubtleEmphasisText  <br/> |Texte qui apparaît par-dessus un arrière-plan d'accentuation discret.  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISTEXT]  <br/> |
|SubtleEmphasisCommandLinks  <br/> |Couleur des liens de commande qui apparaissent par-dessus un arrière-plan d'accentuation discret.  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISCOMMANDLINKS]  <br/> |
|SubtleEmphasisBackground  <br/> |Arrière-plan qui apparaît directement derrière le texte d'accentuation discret.  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISBACKGROUND]  <br/> |
|TopBarText  <br/> |Couleur du texte et du glyphe du menu d'accueil, des icônes de la barre d'outils d'accès rapide et des onglets de ruban fermés.  <br/> |[T_THEME_COLOR_TOPBARTEXT]  <br/> |
|TopBarBackground  <br/> |Couleur d'arrière-plan de la barre supérieure, située au-dessous à droite de la navigation de suite.  <br/> |[T_THEME_COLOR_TOPBARBACKGROUND]  <br/> |
|TopBarHoverText  <br/> |Couleur du texte et du glyphe du menu d'accueil, des icônes de la barre d'outils d'accès rapide et des onglets de ruban fermés lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_TOPBARHOVERTEXT]  <br/> |
|TopBarPressedText  <br/> |Couleur du texte et du glyphe du menu d'accueil, des icônes de la barre d'outils d'accès rapide et des onglets de ruban fermés lorsqu'un utilisateur appuie dessus.  <br/> |[T_THEME_COLOR_TOPBARPRESSEDTEXT]  <br/> |
|HeaderText  <br/> |Couleur de texte de base de tous les éléments de la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERTEXT]  <br/> |
|HeaderSubtleText  <br/> |Texte d'aide associé à la zone de recherche dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERSUBTLETEXT]  <br/> |
|HeaderDisableText  <br/> |Texte de la zone de recherche, si cette dernière est désactivée dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERDISABLETEXT]  <br/> |
|HeaderNavigationText  <br/> |Couleur de texte de base des liens de navigation dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONTEXT]  <br/> |
|HeaderNavigationHoverText  <br/> |Couleur du texte des liens de navigation dans la zone d'en-tête lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONHOVERTEXT]  <br/> |
|HeaderNavigationPressedText  <br/> |Couleur du texte des liens de navigation dans la zone d'en-tête lorsqu'un utilisateur appuie dessus.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONPRESSEDTEXT]  <br/> |
|HeaderNavigationSelectedText  <br/> |Couleur du texte des liens de navigation dans la zone d'en-tête après qu'un utilisateur a sélectionné un lien.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONSELECTEDTEXT]  <br/> |
|HeaderLines  <br/> |Lignes de la zone de recherche lorsque cette dernière est dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERLINES]  <br/> |
|HeaderStrongLines  <br/> |Lignes de la zone de recherche lorsque cette dernière est dans la zone d'en-tête et qu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_HEADERSTRONGLINES]  <br/> |
|HeaderAccentLines  <br/> |Lignes de la zone de recherche activées lorsque cette dernière est dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERACCENTLINES]  <br/> |
|HeaderSublteLines  <br/> |Lignes discrètes situées dans la zone d'en-tête. Non utilisé dans le fichier CSS par défaut.  <br/> |[T_THEME_COLOR_HEADERSUBTLELINES]  <br/> |
|HeaderDisabledLines  <br/> |Lignes de la zone de recherche lorsque cette dernière est désactivée et qu'elle est dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERDISABLEDLINES]  <br/> |
|HeaderDisabledBackground  <br/> |Arrière-plan de la zone de recherche lorsque cette dernière est désactivée et qu'elle est dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERDISABLEDBACKGROUND]  <br/> |
|HeaderFlyoutBorder  <br/> |Bordure des menus déroulants situés dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERFLYOUTBORDER]  <br/> |
|HeaderSiteTitle  <br/> |Couleur de texte du titre du site dans la zone d'en-tête.  <br/> |[T_THEME_COLOR_HEADERSITETITLE]  <br/> |
|SuiteBarBackground  <br/> |Couleur d'arrière-plan pour la navigation de suite.  <br/> |[T_THEME_COLOR_SUITEBARBACKGROUND]  <br/> |
|SuiteBarHoverBackground  <br/> |Couleur d'arrière-plan pour la navigation de suite lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_SUITEBARHOVERBACKGROUND]  <br/> |
|SuiteBarText  <br/> |Couleur du texte et du glyphe des éléments de la navigation de suite.  <br/> |[T_THEME_COLOR_SUITEBARTEXT]  <br/> |
|SuiteBarDisabledText  <br/> |Couleur du texte et du glyphe des éléments de la navigation de suite désactivés. Non utilisé dans le fichier CSS par défaut.  <br/> |[T_THEME_COLOR_SUITEBARDISABLEDTEXT]  <br/> |
|ButtonText  <br/> |Couleur du texte des boutons.  <br/> |[T_THEME_COLOR_BUTTONTEXT]  <br/> |
|ButtonDisabledText  <br/> |Couleur du texte des boutons désactivés.  <br/> |[T_THEME_COLOR_BUTTONDISABLEDTEXT]  <br/> |
|ButtonBackground  <br/> |Couleur d'arrière-plan des boutons.  <br/> |[T_THEME_COLOR_BUTTONBACKGROUND]  <br/> |
|ButtonHoverBackground  <br/> |Couleur d'arrière-plan des boutons lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_BUTTONHOVERBACKGROUND]  <br/> |
|ButtonPressedBackground  <br/> |Couleur d'arrière-plan des boutons lorsqu'un utilisateur appuie dessus.  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBACKGROUND]  <br/> |
|ButtonDisabledBackground  <br/> |Couleur d'arrière-plan des boutons désactivés.  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBACKGROUND]  <br/> |
|ButtonBorder  <br/> |Couleur de bordure des boutons.  <br/> |[T_THEME_COLOR_BUTTONBORDER]  <br/> |
|ButtonHoverBorder  <br/> |Couleur de bordure des boutons lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_BUTTONHOVERBORDER]  <br/> |
|ButtonPressedBorder  <br/> |Couleur de bordure des boutons lorsqu'un utilisateur appuie dessus.  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBORDER]  <br/> |
|ButtonDisabledBorder  <br/> |Couleur de bordure des boutons désactivés.  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBORDER]  <br/> |
|ButtonGlyph  <br/> |Couleur des glyphes qui apparaissent sur un bouton.  <br/> |[T_THEME_COLOR_BUTTONGLYPH]  <br/> |
|ButtonGlyphActive  <br/> |Couleur des glyphes qui apparaissent sur un bouton lorsqu'un utilisateur passe le curseur dessus.  <br/> |[T_THEME_COLOR_BUTTONGLYPHACTIVE]  <br/> |
|ButtonGlyphDisabled  <br/> |Couleur des glyphes d'un bouton désactivé.  <br/> |[T_THEME_COLOR_BUTTONGLYPHDISABLED]  <br/> |
|TileText  <br/> |Texte qui apparaît par-dessus l'arrière-plan de recouvrement en mosaïque.  <br/> |[T_THEME_COLOR_TILETEXT]  <br/> |
|TileBackgroundOverlay  <br/> |Couleur de l'arrière-plan de recouvrement pour les mosaïques.  <br/> |[T_THEME_COLOR_TILEBACKGROUNDOVERLAY]  <br/> |
|ContentAccent1  <br/> |Première couleur de thème que l'utilisateur peut choisir dans le sélecteur de couleurs de l'Éditeur de texte enrichi.  <br/> |[T_THEME_COLOR_CONTENTACCENT1]  <br/> |
|ContentAccent2  <br/> |Deuxième couleur de thème que l'utilisateur peut choisir dans le sélecteur de couleurs de l'Éditeur de texte enrichi.  <br/> |[T_THEME_COLOR_CONTENTACCENT2]  <br/> |
|ContentAccent3  <br/> |Troisième couleur de thème que l'utilisateur peut choisir dans le sélecteur de couleurs de l'Éditeur de texte enrichi.  <br/> |[T_THEME_COLOR_CONTENTACCENT3]  <br/> |
|ContentAccent4  <br/> |Quatrième couleur de thème que l'utilisateur peut choisir dans le sélecteur de couleurs de l'Éditeur de texte enrichi.  <br/> |[T_THEME_COLOR_CONTENTACCENT4]  <br/> |
|ContentAccent5  <br/> |Cinquième couleur de thème que l'utilisateur peut choisir dans le sélecteur de couleurs de l'Éditeur de texte enrichi.  <br/> |[T_THEME_COLOR_CONTENTACCENT5]  <br/> |
|ContentAccent6  <br/> |Sixième couleur de thème que l'utilisateur peut choisir dans le sélecteur de couleurs de l'Éditeur de texte enrichi.  <br/> |[T_THEME_COLOR_CONTENTACCENT6]  <br/> |
   

## Jeux de polices
<a name="font"> </a>

Les polices sont définies dans le jeu de polices (fichier .spfont) et l'aperçu de la page maître (fichier .preview) pour un site SharePoint donné. Le jeu de polices définit les polices utilisées dans quatre zones : titre, navigation, en-tête et corps. Sept jeux de polices sont inclus dans SharePoint 2013. Vous pouvez créer des jeux de polices supplémentaires. Les fichiers de jeu de polices sont situés dans le sous-dossier **15** de la galerie de thèmes du site racine de la collection de sites (http:// _SiteCollectionName_/_catalogs/theme/15/). Pour accéder à la galerie de thèmes à partir de l'interface utilisateur de SharePoint, ouvrez la page **Paramètres du site**, puis, sous **Galeries du concepteur web**, sélectionnez **Thèmes**, puis **15**.
  
    
    
L'exemple suivant décrit le format d'un fichier .spfont.
  
    
    



```XML

<?xml version="1.0" encoding="utf-8"?>
<s:fontScheme name="FontSchemeName" previewSlot1="Slot1" previewSlot2="Slot2" xmlns:s="http://schemas.microsoft.com/sharepoint/">
  <s:fontSlots>
    <s:fontSlot name="FontSlotName">
      <s:latin typeface="LatinScriptFont" />
      <s:ea typeface="EAScriptFont"/>
      <s:cs typeface="CSFont" />
      <s:font script="Language" typeface="ScriptFont" />
      <!--Additional fonts-->
  </s:fontSlots>
  <!--Additional font slots-->
</s:fontScheme>
```

Dans un fichier .spfont, les espaces réservés suivants sont remplacés :
  
    
    

-  _FontSchemeName_ est le nom du jeu de polices.
    
  
-  _Slot1_ est le nom de l'emplacement de police que vous souhaitez utiliser comme premier bloc de l'icône de police dans le sélecteur de jeux de polices de l'Assistant **Modifier l'apparence**.
    
  
-  _Slot2_ est le nom de l'emplacement de police que vous souhaitez utiliser comme deuxième bloc de l'icône de police dans le sélecteur de jeux de polices de l'Assistant **Modifier l'apparence**.
    
  
-  _ FontSlotName_ est le nom de l'emplacement de police que vous définissez (par exemple, le titre).
    
  
-  _LatinScriptFont_ est la police à utiliser pour les scripts latins. Il s'agit également de la police de secours, c'est-à-dire qu'elle est utilisée pour les langues pour lesquelles aucun script n'est explicitement défini dans le jeu de polices.
    
    > **REMARQUE**
      > Vous devez fournir des informations supplémentaires pour utiliser les polices web dans votre jeu de polices. Pour plus d'informations, reportez-vous à la section  [Polices web](#webFont) de cet article.
-  _EAScriptFont_ est la police à utiliser pour les scripts employant des langues d'Asie de l'Est. L'élément **<s:ea>** n'est actuellement pas utilisé par SharePoint, mais l'élément **<s:ea>** est toujours requis dans le jeu de polices.
    
  
-  _CSFont_ est la police à utiliser pour les scripts complexes. L'élément **<s:cs>** n'est actuellement pas utilisé par SharePoint, mais l'élément **<s:cs>** est toujours requis dans le jeu de polices.
    
  
-  _Language_ est le script de langue.
    
  
-  _ScriptFont_ est la police à utiliser pour le script de langue spécifié.
    
  
L'exemple suivant présente une partie d'un fichier .spfont.
  
    
    



```XML

<s:fontScheme name="Georgia" previewSlot1="title" previewSlot2="body" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:fontSlots>
        <s:fontSlot name="title">
            <s:latin typeface="Georgia"/>
            <s:ea typeface=""/>
            <s:cs typeface="Segoe UI Light" />
            <s:font script="Arab" typeface="Tahoma" />
            <s:font script="Deva" typeface="Mangal" />
            <s:font script="Grek" typeface="Segoe UI Light" />
            <s:font script="Hang" typeface="Malgun Gothic" />
            <s:font script="Hans" typeface="Microsoft YaHei" />
            <s:font script="Hant" typeface="Microsoft JhengHei" />
            <s:font script="Hebr" typeface="Tahoma" />
            <s:font script="Hira" typeface="Meiryo" />
            <s:font script="Thai" typeface="Tahoma" />
            <s:font script="Armn" typeface="Tahoma" />
            <s:font script="Beng" typeface="Vrinda" />
            <s:font script="Cher" typeface="Plantagenet Cherokee" />
            <s:font script="Ethi" typeface="Nyala" />
            <s:font script="Geor" typeface="Sylfaen" />
            <s:font script="Gujr" typeface="Shruti" />
            <s:font script="Guru" typeface="Raavi" />
            <s:font script="Knda" typeface="Tunga" />
            <s:font script="Khmr" typeface="DaunPenh" />
            <s:font script="Laoo" typeface="DokChampa" />
            <s:font script="Mlym" typeface="Kartika" />
            <s:font script="Mymr" typeface="Myanmar Text" />
            <s:font script="Orya" typeface="Kalinga" />
            <s:font script="Sinh" typeface="Iskoola Pota" />
            <s:font script="Syrc" typeface="Estrangelo Edessa" />
            <s:font script="Taml" typeface="Latha" />
            <s:font script="Telu" typeface="Gautami" />
            <s:font script="Thaa" typeface="MV Boli" />
            <s:font script="Tibt" typeface="Cordia New" />
            <s:font script="Yiii" typeface="Microsoft Yi Baiti" />
        </s:fontSlot>
…
```

SharePoint 2013 prend en charge les polices web. Vous devez fournir des informations supplémentaires pour utiliser les polices web dans votre jeu de polices. Pour plus d'informations, reportez-vous à la section  [Polices web](#webFont) de cet article.
  
    
    

### Polices adaptées au web
<a name="websafeFont"> </a>

Les polices adaptées au web sont un jeu de polices largement utilisées et disponibles par défaut sur la plupart des périphériques. Pour spécifier une police adaptée au web dans le jeu de polices, ajoutez le nom de la police dans l'attribut **typeface** de l'emplacement de police. L'exemple suivant présente une police adaptée au web utilisée dans un jeu de polices.
  
    
    

```XML

<s:fontSlot name="title">
  <s:latin typeface="Georgia"/>
…
</s:fontSlot>
```


### Polices web
<a name="webFont"> </a>

Les polices web sont des polices disponibles sur Internet. Lorsqu'un utilisateur se rend sur un site qui utilise une police web, le navigateur web télécharge les fichiers de police nécessaires en même temps que le reste de la page. Pour spécifier une police web, vous devez fournir l'URL de vos fichiers de police web dans quatre formats de police (pour une prise en charge par tous les navigateurs), ainsi qu'une petite et une grande image miniature à utiliser pour afficher les noms de police dans le sélecteur de jeux de polices.
  
    
    
L'exemple suivant décrit les informations nécessaires à l'utilisation d'une police web dans un élément **<s:latin>**.
  
    
    



```XML

<s:latin typeface="FontName"
  eotsrc="EotFile"
  woffsrc="WoffFile"
  ttfsrc="TtfFile"
  svgsrc="SvgFile"
  largeimgsrc="LargeImgFile"
  smallimgsrc="SmallImgFile" />

```

Dans cet exemple d'utilisation d'une police web, les espaces réservés suivants seraient remplacés :
  
    
    

-  _FontName_ est le nom de la police web.
    
  
-  _EotFile_ est l'URL relative du fichier de police Embedded Open Type.
    
  
-  _WoffFile_ est l'URL relative du fichier de police web Open Font Format.
    
  
-  _TtfFile_ est l'URL relative du fichier de police TrueType.
    
  
-  _SvgFile_ est l'URL relative du fichier de police Scalable Vector Graphics.
    
  
-  _LargeImgFile_ est l'URL relative de la grande image miniature que vous souhaitez utiliser dans le sélecteur de jeux de polices.
    
  
-  _SmallImgFile_ est l'URL relative de la petite image miniature que vous souhaitez utiliser dans le sélecteur de jeux de polices.
    
  

### Emplacements de police
<a name="fontSlot"> </a>

Le tableau 1 décrit les emplacements de police disponibles et les endroits où ils sont utilisés dans une page.
  
    
    

**Tableau 1. Emplacements de police**


|**Nom de l'emplacement de police**|**Description**|
|:-----|:-----|
|title  <br/> |Utilisé pour le titre de la page.  <br/> |
|navigation  <br/> |Utilisé pour les éléments de navigation verticale et horizontale sur la page.  <br/> |
|large-heading  <br/> |Utilisé pour les en-têtes H1.  <br/> |
|heading  <br/> |Utilisé pour les titres des composants WebPart, les titres des boîtes de dialogue, les titres des légendes et les en-têtes H2 et H3.  <br/> |
|small-heading  <br/> |Utilisé pour les en-têtes H4.  <br/> |
|large-body  <br/> |Utilisé pour les corps de texte de grande taille (15 pixels et 19 pixels).  <br/> |
|body  <br/> |Police de base utilisée partout ailleurs sur la page.  <br/> |
   

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Vue d'ensemble des thèmes pour SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Procédure : Déployer un thème personnalisé dans SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [Mettre à niveau les thèmes personnalisés et CSS pour SharePoint 2013](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [Comment créer un fichier d'aperçu de page maître dans SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [Blog de l'équipe SharePoint : Affichez votre style avec les thèmes SharePoint](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [Fonctionnalités de personnalisation et la conception de 2013 le gestionnaire de conception SharePoint](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

  
    
    

