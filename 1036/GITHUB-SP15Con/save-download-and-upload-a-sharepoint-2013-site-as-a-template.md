---
title: Enregistrer, télécharger et charger un site SharePoint 2013 comme modèle
ms.prod: SHAREPOINT
ms.assetid: 2e637172-ddac-4a70-bd77-55a1645a3db1
---


# Enregistrer, télécharger et charger un site SharePoint 2013 comme modèle
Apprenez à concevoir et à créer des applications robustes à l'aide de modèles de site SharePoint.
Vous pouvez concevoir et créer des applications SharePoint 2013 robustes qui comprennent un riche ensemble de sources de données, de vues et de formulaires destinés aux clients, de flux de travail hautement personnalisés, et bien plus. Une fois que vous avez créé votre site de solutions d'entreprise, vous pouvez commencer à l'utiliser immédiatement dans votre environnement SharePoint. Vous pouvez également transformer votre solution en modèle et le déployer dans un autre environnement, le mettre à la disposition des utilisateurs afin qu'ils puissent créer d'autres sites en se basant dessus ou encore le transférer pour un développement supplémentaire dans Visual Studio.
  
    
    


## Qu'est-ce qu'un modèle de site SharePoint ?
<a name="bkmk_WhatIsTemplate"> </a>

Les modèles de site SharePoint sont des définitions prédéfinies conçues autour d'un besoin d'entreprise particulier. Vous pouvez utiliser ces modèles tels quels pour créer votre propre site SharePoint, puis personnaliser le site autant que vous le souhaitez. Vous connaissez sans doute les modèles de site par défaut, tels que Site d'équipe, Site de projets et Site de communautés.
  
    
    
En plus des modèles par défaut, vous pouvez créer votre propre modèle de site en fonction d'un site que vous avez créé et personnalisé. Il s'agit d'une fonctionnalité puissante qui vous permet de créer une solution personnalisée et de partager cette solution avec vos pairs, l'organisation dans son intégralité ou des organisations extérieures. Vous pouvez également packager le site et l'ouvrir dans un autre environnement ou dans une autre application, comme Visual Studio, et le personnaliser aussi à cet endroit.
  
    
    
Convertir votre site personnalisé ou votre solution d'entreprise en modèle est une fonctionnalité extrêmement utile et très puissante. Tout le potentiel de SharePoint, conçu comme une plateforme pour les applications d'entreprise, se révèle une fois que vous commencez à packager votre solution comme modèle. L'option de modèle de site rend cela possible.
  
    
    
Lorsque vous enregistrez votre site en tant que modèle, vous créez un package de solution web (ou fichier WSP). Un fichier WSP est un fichier CAB qui utilise le manifeste de la solution. La solution que vous créez est stockée dans la galerie de solutions de la collection de sites SharePoint. Lorsque vous enregistrez le modèle, un fichier de solution (.wsp) est créé, puis stocké dans la galerie de solutions à partir de laquelle vous pouvez télécharger ou activer la solution.
  
    
    

> **REMARQUE**
> Le fichier WSP que vous créez est une solution utilisateur de confiance partielle qui possède le même format déclaratif qu'une solution SharePoint de confiance totale. Cependant, il ne prend pas en charge l'ensemble des types d'éléments de fonctionnalité qui sont pris en charge par des solutions de confiance totale. 
  
    
    


### Qu'est-ce qui est enregistré dans un modèle ?

Lorsque vous enregistrez un site SharePoint en tant que modèle, vous enregistrez l'infrastructure globale du site : ses listes et bibliothèques, ses vues et formulaires, ainsi que ses flux de travail. En plus de ces composants, vous pouvez inclure le contenu du site dans le modèle ; par exemple, les documents stockés dans les bibliothèques de documents. Pour commencer, il peut être utile de fournir des exemples de contenu pour les utilisateurs. Ayez à l'esprit que cela peut également augmenter la taille de votre modèle au-delà de la limite de modèle de site par défaut qui est de 50 Mo.
  
    
    
La plupart des objets d'un site sont inclus et pris en charge par le modèle. Toutefois, plusieurs objets et fonctionnalités ne sont pas pris en charge. 
  
    
    

- **Pris en charge** Listes, bibliothèques, listes externes, connexions de sources de données, vues de liste et vues de données, formulaires personnalisés, flux de travail, types de contenu, actions personnalisées, navigation, pages du site, pages maîtres, modules et modèles web.
    
  
- **Non pris en charge** Autorisations personnalisées, instances de flux de travail en cours d'exécution, historique des versions d'élément de liste, tâches de flux de travail associées à des flux de travail en cours d'exécution, valeurs des champs de groupes ou de personnes, valeurs des champs de taxonomie, pages de publication et sites de publication, Mes Sites et fonctionnalités d'agrafage, Compléments SharePoint et récepteurs d'événements distants.
    
    > **REMARQUE**
      > Pour les sites de publication, vous pouvez utiliser des modèles de définition de site. Pour plus d'informations, voir  [Ressources supplémentaires](save-download-and-upload-a-sharepoint-2013-site-as-a-template.md#bkmk_additionalresources) à la fin de cette rubrique.

### Qu'est-il possible de faire avec des modèles SharePoint ?

Enregistrer un site en tant que modèle est une fonctionnalité puissante, car elle permet de nombreuses utilisations des sites personnalisés. Voici les avantages immédiats que vous obtenez en enregistrant un site en tant que modèle :
  
    
    

- **Déployer des solutions immédiatement** Enregistrez et activez le modèle dans la galerie de solutions afin de permettre aux autres employés de créer d'autres sites à partir de ce modèle. Vous pouvez le sélectionner, puis créer un site à partir de ce modèle, qui héritera des composants du site, de sa structure, de ses flux de travail, etc. Vous n'avez pas besoin de Visual Studio pour créer votre solution. Vous devez accéder au serveur directement et exécuter les commandes administrateur. Enregistrez simplement le site en tant que modèle, puis activez-le et c'est parti !
    
  
- **Portabilité** Outre le déploiement d'une solution personnalisée dans votre environnement, vous pouvez télécharger le fichier .wsp et le déployer dans un autre environnement SharePoint. Toute la personnalisation de votre site est stockée dans un seul fichier pour plus de facilité.
    
  
- **Extensibilité** Comme il s'agit d'un package de solution web, vous pouvez ouvrir votre site personnalisé dans Visual Studio, personnaliser davantage le modèle, puis le déployer vers SharePoint. Le développement d'un site SharePoint peut par conséquent passer par un cycle de vie de solution (développement, préparation et mise en production) qui comprend SharePoint Designer 2013, Visual Studio et le navigateur.
    
  
Au fur et à mesure que vous créerez des sites personnalisés dans SharePoint, vous découvrirez encore plus d'avantages résultant de la conversion de votre site en une solution portable dans l'ensemble de l'organisation. Les étapes de base pour utiliser des modèles de site sont les suivantes :
  
    
    

- Enregistrer un site comme modèle dans la galerie de solutions.
    
  
- Télécharger le modèle de site à partir de la galerie de solutions dans un fichier .wsp.
    
  
- Charger le fichier .wsp dans la galerie de solutions.
    
  
Une fois que vous aurez ajouté un modèle de site à la galerie de solutions et que le modèle sera activé, la prochaine fois que vous créerez un site ou un sous-site, le modèle pourra être sélectionné dans l'onglet **Personnalisé** de la section **Sélection du modèle** sur la page **Nouveau site SharePoint**.
  
    
    

## Enregistrer un site en tant que modèle dans la galerie de solutions
<a name="bkmk_SaveTemplate"> </a>


1. Accédez au site de niveau supérieur de votre collection de sites.
    
  
2. Cliquez sur **Paramètres**, puis sur **Paramètres du site**.
    
  
3. Dans la section **Actions du site**, cliquez sur **Enregistrer le site en tant que modèle**.
    
  
4. Indiquez le nom à utiliser pour le fichier de modèle dans la case **Nom de fichier**.
    
  
5. Entrez le nom et la description du modèle dans les cases **Nom du modèle** et **Description du modèle**.
    
  
6. Pour inclure le contenu du site dans le modèle de site, cochez la case **Inclure le contenu**.
    
    > **REMARQUE**
      > Inclure le contenu du site peut augmenter la taille du modèle de façon significative. La limite de taille par défaut d'un modèle de site est de 50 Mo, mais elle peut être inférieure dans votre organisation. Vous pouvez toujours exclure le contenu, puis copier ce dont vous avez besoin plus tard dans le nouveau site. Vous pouvez aussi augmenter la limite de taille. Par exemple, pour augmenter la limite jusqu'au maximum autorisé, vous devez utiliser la syntaxe de commande Stsadm suivante. >  `stsadm -o setproperty -pn max-template-document-size -pv 524288000`
7. Cliquez sur **OK** pour enregistrer le modèle.
    
    Si tous les composants sur le site sont valides, le modèle est créé et un message indiquant « Opération terminée » apparaît.
    
  
8. Effectuez l'une des opérations suivantes :
    
  - Pour revenir à votre site, cliquez sur **OK**.
    
  
  - Pour accéder directement au modèle de site, cliquez sur la **galerie de solutions**.
    
  

## Télécharger le modèle de site de la galerie de solutions vers un fichier
<a name="bkmk_DownloadTemplate"> </a>


1. Accédez au site de niveau supérieur de votre collection de sites.
    
  
2. Cliquez sur **Paramètres**, puis sur **Paramètres du site**.
    
  
3. Dans la section **Galeries du concepteur web**, cliquez sur **Solutions**.
    
  
4. S'il est nécessaire d'activer la solution, sélectionnez-la, puis, dans le groupe **Commandes**, cliquez sur **Activer**. Ensuite, sur l'écran de **confirmation Activer la solution**, dans le groupe **Commandes**, cliquez sur **Activer**.
    
  
5. Pour télécharger la solution, cliquez sur son nom dans la galerie de solutions, puis cliquez sur **Enregistrer**. Ensuite, dans la boîte de dialogue **Enregistrer sous**, sélectionnez l'emplacement dans lequel enregistrer la solution, puis cliquez sur **Enregistrer** et sur **Fermer**.
    
  

## Charger le fichier de modèle de site vers une galerie de solutions
<a name="bkmk_UploadTemplate"> </a>


1. Accédez au site de niveau supérieur de votre collection de sites.
    
  
2. Cliquez sur **Paramètres**, puis sur **Paramètres du site**.
    
  
3. Dans la section **Galeries du concepteur web**, cliquez sur **Solutions**.
    
  
4. Pour charger la solution, dans le groupe **Commandes**, cliquez sur **Télécharger**, puis, dans la boîte de dialogue **Ajouter un document**, cliquez sur **Parcourir**. Ensuite, dans la boîte de dialogue **Choisir un fichier à télécharger**, localisez le fichier et sélectionnez-le, puis cliquez sur **Ouvrir** et sur **OK**.
    
  
5. Pour activer la solution, cliquez sur **Activer** dans le groupe **Commandes** sur l'écran de confirmation de l'activation de la solution.
    
  

## Ressources supplémentaires
<a name="bkmk_additionalresources"> </a>


-  [Types de site : modèles web et définitions de site](http://msdn.microsoft.com/fr-fr/library/ms434313.aspx)
    
  
-  [Comprendre comment empaqueter et déployer des flux de travail dans SharePoint 2013](http://msdn.microsoft.com/fr-fr/library/jj819316%28v=office.15%29.aspx)
    
  
-  [Créer des solutions de batterie dans SharePoint 2013](http://msdn.microsoft.com/fr-fr/library/jj163902%28v=office.15%29.aspx)
    
  
-  [Copier ou déplacer une liste à l'aide d'un modèle de liste](http://office.com/redir/HA101782479.aspx)
    
  
-  [Copier ou déplacer une bibliothèque à l'aide d'un modèle de bibliothèque](http://office.com/en-us/redir/HA101814157.aspx)
    
  
-  [Copier ou déplacer des fichiers de bibliothèque à l'aide de la commande Ouvrir avec l'Explorateur](http://office.com/redir/HA101811182.aspx)
    
  

