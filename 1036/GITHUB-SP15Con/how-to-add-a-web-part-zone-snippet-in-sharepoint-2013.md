---
title: Procédure  Ajouter un extrait de code de zone de composants WebPart dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7583b217-200c-4569-8f88-fe975c8ebd72
---


# Procédure : Ajouter un extrait de code de zone de composants WebPart dans SharePoint 2013
Une zone de composants WebPart est un extrait de code que vous pouvez ajouter à une mise en page pour permettre aux auteurs de contenu d'ajouter, de modifier ou de supprimer des composants WebPart dans cette zone.
## Introduction à l'extrait de code de zone de composants WebPart
<a name="Introduction"> </a>

Un composant WebPart est un contrôle serveur qui fournit un composant spécifique de la fonctionnalité SharePoint. Une zone de composants WebPart constitue un conteneur qui détermine la mise en page, le comportement et d'autres propriétés des composants WebPart contenus dans cette zone. Par exemple, une zone de composants WebPart peut spécifier si les composants WebPart :
  
    
    

- Sont organisés selon une disposition horizontale ou verticale. 
    
  
- Affichent les éléments de l'interface utilisateur courants tels qu'une barre de titre ou une bordure.
    
  
- Peuvent être personnalisés par les auteurs de contenu lorsqu'ils modifient une page dans le navigateur.
    
  
- Peuvent être personnalisés par les visiteurs du site qui créent un affichage personnel d'un composant WebPart lorsqu'ils consultent une page dans le navigateur.
    
  
Dans un site de publication, les auteurs de contenu disposant des autorisations requises peuvent créer ou modifier des pages situées dans la bibliothèque de pages. En tant que concepteur, vous pouvez ajouter une zone de composants WebPart dans une mise en page. Lorsqu'un auteur de contenu crée ou modifie une page en fonction de cette mise en page, l'auteur peut ajouter, modifier ou supprimer des composants WebPart dans cette zone. Par exemple, vous pouvez ajouter une zone de composants WebPart dans une mise en page afin que les auteurs de contenu puissent :
  
    
    

- Afficher les résultats d'une requête de recherche à l'aide d'un composant WebPart de recherche de contenu. Les auteurs peuvent mettre à jour ou modifier la requête de recherche lorsqu'un composant WebPart de recherche réside à l'intérieur d'une zone de composants WebPart.
    
  
- Incorporer des clips audio ou vidéo dans une page web à l'aide d'un composant WebPart multimédia.
    
  
- Créer des listes de liens hypertextes facilement modifiables, regroupables ou réorganisables à l'aide d'un composant WebPart de lien de synthèse.
    
  
- Créer un plan de site qui en répertorie toutes les pages, mis à jour chaque fois qu'une page est ajoutée, supprimée, renommée ou déplacée à l'aide d'un composant WebPart de sommaire.
    
  

### Quand utiliser des zones de composants WebPart

Lorsqu'une mise en page comprend une ou plusieurs zones de composants WebPart, celles-ci sont disponibles sur toutes les pages utilisant cette mise en page, ce qui permet aux auteurs d'insérer des composants WebPart sur ces pages. Si vous permettez aux auteurs d'insérer des composants WebPart sur les pages, vous réduisez votre contrôle sur l'expérience des utilisateurs sur le site. Par exemple, un auteur peut insérer un composant WebPart de sommaire sur une page exposant des parties de votre site que vous ne souhaitez pas rendre accessibles aux visiteurs à partir de la page en cours.
  
    
    
Si vous souhaitez exercer un contrôle complet sur l'affichage d'un composant WebPart sur votre site, et si vous souhaitez que le composant WebPart apparaisse sur toutes les pages d'un certain type, ajoutez-le directement dans une mise en page. Si vous souhaitez qu'un composant WebPart apparaisse sur toutes les pages d'un site, vous pouvez également ajouter un composant WebPart directement dans une page maître.
  
    
    

> **REMARQUE**
> Les zones de composants WebPart sont disponibles sur les mises en page, mais pas sur les pages maîtres. Le but des zones est de permettre aux auteurs de modifier les composants WebPart ; or, les auteurs ne modifient généralement pas les pages maîtres. 
  
    
    

Vous pouvez également ajouter des zones de composants WebPart à une mise en page, mais limiter leur utilisation. Par exemple, vous pouvez ajouter des composants WebPart à une zone, puis définir une propriété de cette zone afin que les auteurs de contenu puissent modifier les propriétés des composants WebPart existants, mais pas ajouter ou supprimer des composants WebPart dans la zone. Les zones de composants WebPart possèdent un ensemble de propriétés dont l'objectif est double. Vous pouvez utiliser un sous-ensemble de propriétés afin d'organiser la mise en page et le format des composants WebPart sur la page, et un autre pour fournir un niveau de protection supplémentaire contre la modification (ou « verrouillage ») des composants WebPart dans la zone.
  
    
    
Pour obtenir différents niveaux de contrôle sur la façon dont les composants WebPart sont présentés sur votre site, vous pouvez :
  
    
    

- Ajouter des composants WebPart directement à une page maître ou une mise en page. De cette façon, les auteurs de contenu ne peuvent pas modifier les composants WebPart.
    
  
- Ajouter des composants WebPart à des zones sur les mises en page, mais limiter ces zones uniquement aux composants WebPart par défaut ajoutés.
    
  
- Ajouter des zones de composants WebPart aux mises en page et octroyer aux auteurs de contenu le contrôle complet sur les composants WebPart apparaissant dans ces zones, ainsi que sur leur configuration.
    
  
Les propriétés d'une zone de composants WebPart peuvent spécifier si les auteurs de contenu sont autorisés à modifier les éléments suivants :
  
    
    

- La mise en page des composants WebPart dans la zone par l'ajout, la suppression, le redimensionnement ou le déplacement des composants WebPart.
    
  
- Les paramètres de composant WebPart pour tous les utilisateurs (affichage partagé d'un composant WebPart).
    
  
- Leurs paramètres personnels de composant WebPart (affichage personnel d'un composant WebPart).
    
  
Le tableau 1 indique les propriétés importantes à prendre en compte lorsque vous souhaitez limiter une zone de composants WebPart.
  
    
    

**Tableau 1. Propriétés de la zone des composants WebPart utilisées pour limiter les auteurs de contenu**


|**Nom de la propriété**|**Description**|
|:-----|:-----|
|**AllowLayoutChange** <br/> |Indique si les composants WebPart dans la zone peuvent être fermés, réduits, supprimés ou restaurés.  <br/> Si la valeur est définie sur **False**, les utilisateurs ne peuvent pas fermer, réduire, supprimer, restaurer, réorganiser ou déplacer des composants WebPart dans la zone, ni les déposer dans une zone différente. De même, ils ne peuvent pas ajouter de composants WebPart à partir du catalogue. En outre, plusieurs propriétés ayant une incidence sur l'interface utilisateur des composants WebPart dans la zone sont désactivées. Cette propriété n'a pas d'incidence sur la possibilité de changer la mise en page par programmation.  <br/> Si la valeur est définie sur **True**, les utilisateurs disposant des autorisations appropriées peuvent effectuer ces actions.  <br/> |
|**LockLayout** <br/> |Indique si les composants WebPart dans la zone peuvent être ajoutés, supprimés, redimensionnés ou déplacés. Cette propriété fonctionne de la même façon que l'affichage de la page de composants WebPart soit personnel ou partagé.  <br/> Si la valeur est définie sur **True**, les propriétés spécifiques de chaque composant WebPart de la zone affectées sont les suivantes : **Zone (ZoneID)**, **Ordre du composant (PartOrder)**, **Visible sur la page (IsVisible)**, **Hauteur (Height)**, **Largeur (Width)**, **Autoriser la fermeture (AllowRemove)** et **IsIncluded** (commande **Fermer** dans le menu **Composant WebPart**). Les autres propriétés de composant WebPart ne sont pas affectées.  <br/> Si la valeur est définie sur **False**, les propriétés de composant WebPart déterminent si des modifications peuvent être effectuées (avec les autorisations de site appropriées).  <br/> |
|**AllowCustomization** <br/> |Indique si les valeurs de propriété partagées des composants WebPart au sein de la zone peuvent être modifiées.  <br/> Si la valeur est définie sur **True**, les utilisateurs disposant des autorisations appropriées peuvent apporter des modifications aux composants WebPart dans la zone pour tous les utilisateurs.  <br/> Si la valeur est définie sur **False**, les utilisateurs ne peuvent pas modifier les composants WebPart de la zone dans l'interface utilisateur en affichage partagé. Toutefois, des modifications peuvent être apportées par programme et à l'aide de la page de maintenance des composants WebPart.  <br/> |
|**AllowPersonalization** <br/> |Indique si les valeurs de propriété personnelles des composants WebPart au sein de la zone peuvent être modifiées.  <br/> Si la valeur est définie sur **True**, les utilisateurs disposant des autorisations appropriées peuvent apporter des modifications personnelles aux composants WebPart dans la zone.  <br/> Si la valeur est définie sur **False**, les utilisateurs ne peuvent pas apporter de modifications personnelles aux composants WebPart via l'interface utilisateur, excepté s'il s'agit d'un composant WebPart privé et qu'ils disposent des autorisations appropriées.  <br/> |
   

> **REMARQUE**
> Vous ne pouvez pas insérer une zone de composants WebPart dans un volet Canaux des appareils. Si vous souhaitez permettre aux auteurs d'ajouter des composants WebPart à une page, et si vous n'attachez pas d'importance au poids de la page pour les appareils mobiles, vous pouvez ajouter un champ de page d'éditeur de texte enrichi au volet Canaux des appareils, puis inviter les auteurs à y ajouter des composants WebPart. Vous pouvez ajouter des composants WebPart directement dans le volet Canaux des appareils (sans zone de composants WebPart). Pour plus d'informations, voir  [Comment : ajouter un fragment de panneau de configuration de canal périphérique en SharePoint 2013](how-to-add-a-device-channel-panel-snippet-in-sharepoint-2013.md). 
  
    
    


## Insertion d'un extrait de code de zone de composants WebPart
<a name="InsertSnippet"> </a>

Comme tous les extraits de code, celui-ci s'ajoute à partir de la galerie d'extraits de code. Pour y accéder, vous devez d'abord sélectionner une mise en page à modifier. Les zones de composants WebPart peuvent être ajoutées aux mises en page, mais pas aux pages maîtres.
  
    
    

### Pour insérer un extrait de code de zone de composants WebPart


1. Accédez à votre site de publication.
    
  
2. Dans le coin supérieur droit de la page, sélectionnez l'icône d'engrenage de paramètres, puis choisissez **Gestionnaire de conception**.
    
  
3. Dans le gestionnaire de conception, dans le volet de navigation de gauche, sélectionnez **Modifier les mises en page**.
    
  
4. Sélectionnez le nom de la mise en page à laquelle vous souhaitez ajouter l'extrait de code.
    
  
5. Pour ouvrir la galerie d'extraits de code, choisissez **Extraits de code** dans le coin supérieur droit de l'aperçu côté serveur.
    
  
6. Sur le ruban, dans l'onglet **Conception**, sélectionnez **Zone de composants WebPart**.
    
  
7. Sur le côté droit de la galerie d'extraits de code, sous **À propos de ce composant**, sélectionnez ou cliquez sur les en-têtes de section pour développer ou réduire les groupes de propriétés, puis configurez les paramètres personnalisés souhaités.
    
    La section intitulée **Important** contient les propriétés essentielles au fonctionnement de cet extrait de code. L'extrait de code possède un identifiant unique pour une zone de composants WebPart. Une fois l'extrait de code copié dans votre mise en page, vous ne devez pas réutiliser cet ID. Si vous souhaitez ajouter un autre extrait de code de zone de composants WebPart, choisissez **Actualiser** pour générer un autre ID pour l'extrait de code suivant.
    
    Pour obtenir une description des propriétés nécessaires à la limitation d'une zone de composants WebPart ( **LockLayout**, **AllowCustomization** et **AllowPersonalization**), voir le tableau 1.
    
    > **REMARQUE**
      > Vous pouvez constater que certains noms de propriété apparaissent en gras dans la grille des propriétés de la galerie d'extraits de code. Ces propriétés possèdent des valeurs qui ont été modifiées par rapport à la configuration par défaut de ce composant, mais elles ne sont pas nécessairement pertinentes pour un scénario de concepteur. En d'autres termes, une propriété peut être affichée en gras sans être obligatoirement importante pour votre scénario. 
8. Après avoir configuré toutes les propriétés, choisissez **Mettre à jour**. Cela met à jour l'extrait de code HTML sur le côté gauche de la page, de sorte que le balisage reflète vos paramètres personnalisés. Vous pouvez toujours choisir **Réinitialiser** pour restaurer toutes les propriétés sur leurs paramètres par défaut.
    
  
9. Sur le côté gauche de la galerie d'extraits de code, sous **Extrait de code HTML**, choisissez **Copier dans le Presse-papiers**.
    
  
10. Dans votre éditeur HTML, ouvrez le lecteur réseau mappé sur votre ordinateur, puis le fichier HTML de la page maître ou la mise en page à laquelle vous ajoutez l'extrait de code.
    
    Pour plus d'informations, voir  [Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
    
  
11. Dans le fichier HTML, collez l'extrait de code à l'endroit où vous souhaitez que le balisage s'affiche.
    
    Lorsque vous ajoutez l'extrait de code à une mise en page, veillez à le coller dans **PlaceHolderMain**.
    
  
12. Remplacez la balise **<div>** avec `class="DefaultContentBlock"` par votre propre contenu spécifique.
    
  
13. Si vous souhaitez préremplir la zone avec des composants WebPart (par exemple, si la zone limite les auteurs de contenu à la modification des composants WebPart existants uniquement et les empêche d'en ajouter de nouveaux), insérez des extraits de code de composant WebPart à l'endroit où la balise **<!--DC … -->** apparaît.
    
  
14. Enregistrez la page, puis actualisez l'aperçu côté serveur dans le gestionnaire de conception pour vous assurer que la page s'affiche comme prévu.
    
  

## Présentation du balisage d'extrait de code
<a name="UnderstandMarkup"> </a>

Les deux principaux éléments d'un extrait de code de zone de composants WepPart sont la propriété **ID** et le commentaire **<!--DC … -->**. Chaque zone doit posséder un ID unique. Si vous souhaitez ajouter plus d'une zone de composants WebPart à votre mise en page, choisissez **Actualiser** dans la galerie d'extraits de code avant de copier chaque extrait de code afin de générer un nouvel ID. Le commentaire **<!--DC … -->** doit être remplacé par les composants WebPart que vous souhaitez voir apparaître dans la zone par défaut.
  
    
    
Les propriétés supplémentaires pouvant être utilisées pour limiter l'utilisation des zones par les auteurs de contenu ( **AllowCustomization**, **AllowPersonalization** et **LockLayout**) sont présentées dans le code suivant.
  
    
    

> **REMARQUE**
> Les propriétés **AllowCustomization**, **AllowPersonalization** et **LockLayout** n'apparaissent dans le balisage que si vous modifiez leurs valeurs par défaut dans la grille des propriétés.
  
    
    




```HTML

<div data-name="WebPartZone">
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <div xmlns:ie="ie">
        <!--MS:<WebPartPages:WebPartZone runat="server" ID="x0e5f5212505f48a9aac43df13eeae4f9" AllowCustomization="True" AllowPersonalization="False" FrameType="TitleBarOnly" LockLayout="True" Orientation="Vertical">-->
            <!--MS:<ZoneTemplate>-->
               <!--DC: Replace this comment with default web parts for new pages. -->
            <!--ME:</ZoneTemplate>-->
        <!--ME:</WebPartPages:WebPartZone>-->
    </div>
    <!--CE: End Web Part Zone Snippet-->
</div>

```


## Ressources supplémentaires
<a name="AdditionalResources"> </a>


-  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md)
    
  
-  [Classe WebPartZone](http://msdn.microsoft.com/fr-fr/library/system.web.ui.webcontrols.webparts.webpartzone.aspx)
    
  
-  [Propriétés WebPartZoneBase](http://msdn.microsoft.com/fr-fr/library/335sw9k3.aspx)
    
  
-  [Créer des sites pour SharePoint](build-sites-for-sharepoint.md)
    
  
-  [Développer la conception de site dans SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  

