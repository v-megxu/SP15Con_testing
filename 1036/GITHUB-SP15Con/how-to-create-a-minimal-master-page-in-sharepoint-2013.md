---
title: Procédure  Créer une page maître minimale dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 634aa471-07e1-41d6-aa80-27f7ef7e9dc8
---


# Procédure : Créer une page maître minimale dans SharePoint 2013
Une page maître minimale ne contient que les éléments de la page requis par SharePoint 2013 pour afficher la page correctement dans le navigateur. Le gestionnaire de conception vous permet de créer rapidement une page maître minimale sans avoir à concevoir et à convertir un fichier HTML.
## Introduction à la page maître minimale
<a name="Introduction"> </a>

Avec le gestionnaire de conception, vous pouvez convertir un fichier HTML normal en une page maître SharePoint 2013. Toutefois, si vous ne disposez pas d'une maquette prédéfinie, vous pouvez quand même rapidement tout reprendre à zéro en créant une page maître minimale. La page maître minimale ne contient que les éléments de la page requis par SharePoint pour afficher la page correctement dans le navigateur.
  
    
    
Lorsque vous créez une page maître minimale, le gestionnaire de conception crée le fichier .master et un fichier HTML associé, de sorte que vous pouvez continuer à utiliser uniquement le fichier HTML si vous préférez. L'utilisation d'une page maître minimale est exactement identique à l'utilisation d'une page maître que vous convertissez à partir d'un fichier HTML. La page maître et le fichier HTML sont associés, de sorte que chaque fois que vous modifiez et enregistrez le fichier HTML, ces modifications sont synchronisées avec la page maître associée. En outre, le fichier HTML contient des types spéciaux de balisage qui rendent la synchronisation avec le fichier .master possible. Pour plus d'informations sur cette association et ces types de balisage, voir  [Procédure : Convertir un fichier HTML en page maître dans SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md).
  
    
    
Commencer à partir d'une page maître minimale est utile lorsque :
  
    
    

- Vous souhaitez commencer rapidement à partir de zéro, pour ensuite créer votre conception dans le fichier HTML qui est associé à la page maître minimale, plutôt que de commencer avec un fichier HTML maquette.
    
  
- Vous souhaitez réaliser un prototype d'un élément de conception ou le tester rapidement et que cette action nécessite une page maître SharePoint de travail. Par exemple, la création d'une page maître minimale ne nécessite pas la préparation d'un fichier HTML pour la conversion ou la résolution des erreurs de prévision qui résultent de balisage non valide dans le fichier HTML. Cela signifie que vous pouvez immédiatement travailler avec l'aperçu côté serveur ou la galerie d'extraits de code.
    
  
- Vous souhaitez travailler directement avec le fichier .master. Si vous êtes un développeur ASP.NET ou un développeur SharePoint, vous pouvez créer une page maître minimale, supprimer l'association entre le fichier HTML et le fichier .master en désactivant la case **Fichier associé** dans les propriétés du fichier HTML, et ensuite travailler directement avec le fichier .master.
    
  

## Création d'une page maître minimale
<a name="CreateMinimalMaster"> </a>


  
    
    

### Pour créer une page maître minimale, procédez comme suit :


1. Accédez à votre site de publication.
    
  
2. Dans le coin supérieur droit de la page, sélectionnez **Paramètres**, puis **Gestionnaire de conception**.
    
  
3. Dans le gestionnaire de conception, dans le volet de navigation de gauche, sélectionnez **Modifier les pages maîtres**.
    
  
4. Choisissez **Créer une page maître minimale**.
    
  
5. Dans la boîte de dialogue **Créer une page maître minimale**, saisissez le nom de la page maître, puis choisissez **OK**.
    
    À ce stade, SharePoint crée un fichier .master et un fichier HTML associé portant le même nom dans la galerie de pages maîtres.
    
    Dans le gestionnaire de conception, votre fichier HTML apparaît maintenant avec l'état **Conversion réussie** dans la colonne d'état.
    
  
6. Cliquez sur le lien dans la colonne d'état pour prévisualiser le fichier.
    
    La page de prévisualisation est un aperçu côté serveur en temps réel de votre page maître.
    
    Pour plus d'informations sur l'aperçu de la page maître avec différentes pages, voir  [Comment modifier la page d'aperçu dans le Gestionnaire de conception SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md).
    
    L'aperçu de la page contient également un lien **Extraits de code** dans le coin supérieur droit. Ce lien ouvre la galerie d'extraits de code, où vous pouvez initier le remplacement de contrôles de maquette ou statiques dans votre conception par des contrôles dynamiques SharePoint. Pour plus d'informations, voir [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
    Une fois l'aperçu de votre page maître affiché, une balise **<div>** s'ajoute à votre fichier HTML. Vous devrez peut-être faire défiler la page vers le bas pour voir la balise **<div>**.
    
    Cette balise **<div>** constitue le bloc de contenu principal. Elle se trouve à l'intérieur d'un espace réservé de contenu appelé **ContentPlaceHolderMain**. En exécution, lorsqu'un visiteur parcourt votre site et demande une page, cet espace réservé de contenu se remplit avec le contenu d'une mise en page dans une zone de contenu correspondante. Positionnez la balise **<div>** là où vous souhaitez que vos mises en page apparaissent sur la page maître.
    
  
7. Vous pouvez modifier le fichier HTML qui réside directement sur le serveur en utilisant un éditeur HTML pour ouvrir et modifier le fichier HTML dans un lecteur mappé. Chaque fois que vous enregistrez le fichier HTML, toutes les modifications sont synchronisées avec le fichier .master associé. Pour plus d'informations, voir  [Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
    
  
8. Pour travailler uniquement avec le fichier .master et non avec le fichier HTML, vous devez rompre le lien entre les deux fichiers. Dans le gestionnaire de conceptions, sur la page Modifier les pages maîtres, sélectionnez le fichier HTML, ouvrez le menu **Propriétés**, puis choisissez **Modifier les propriétés**. Dans l'onglet **Modifier**, désactivez la case **Fichier associé**, puis cliquez sur **Enregistrer**.
    
    La rupture de l'association vous permet de travailler directement avec le fichier .master et d'enregistrer les modifications sans qu'elles soient remplacées par les modifications apportées au fichier HTML. Vous pouvez restaurer cette association à tout moment. Si vous restaurez l'association, le fichier HTML associé se synchronise avec le fichier .master et l'écrase.
    
  

## Comprendre le fichier HTML associé
<a name="UnderstandHTML"> </a>

Lorsque vous créez une page maître minimale, un fichier HTML est créé, qui est associé au fichier .master, et ce fichier HTML contient de nombreuses lignes de balisage qui sont propres à la façon dont SharePoint 2013 fonctionne. Vous pouvez ignorer la plupart de ce balisage, car une grande partie n'apparaît pas dans le balisage final de votre site lorsque vous affichez la source dans le navigateur. Toutefois, ce balisage est essentiel pour la synchronisation des modifications entre le fichier HTML et le fichier .master que SharePoint 2013 utilise réellement. Chaque fois que vous enregistrez une modification dans votre fichier HTML, ce balisage SharePoint permet à cette même modification d'être apportée au fichier .master associé en arrière-plan. Pour plus d'informations, voir les exemples de balisage dans  [Procédure : Convertir un fichier HTML en page maître dans SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md).
  
    
    

## Ressources supplémentaires
<a name="Additional"> </a>


-  [Vue d'ensemble du gestionnaire de conception dans SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Procédure : Convertir un fichier HTML en page maître dans SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md)
    
  

