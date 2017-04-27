---
title: Vue d'ensemble du gestionnaire de conception dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 29834b3f-3815-4347-91d3-296387663114
---


# Vue d'ensemble du gestionnaire de conception dans SharePoint 2013
Découvrez comment utiliser le gestionnaire de conception pour personnaliser votre site SharePoint 2013. Le gestionnaire de conception est une fonctionnalité de publication disponible dans les sites de publication SharePoint Server 2013 et Office 365. Vous pouvez également utiliser le gestionnaire de conception pour personnaliser votre site web public dans Office 365.
## Introduction au gestionnaire de conception
<a name="Introduction"> </a>

Si vous souhaitez que votre site SharePoint 2013 porte les couleurs de votre organisation et n'ait pas simplement l'air d'un site SharePoint, vous pouvez créer une conception personnalisée à l'aide du gestionnaire de conception. Il s'agit d'une fonctionnalité de SharePoint 2013 qui vous permet de créer facilement une conception personnalisée au rendu parfait, à l'aide des outils de conception web que vous avez l'habitude d'utiliser. Le gestionnaire de conception est une fonctionnalité de publication disponible pour les sites de publication SharePoint Server 2013 et Office 365. Vous pouvez également utiliser le gestionnaire de conception pour personnaliser votre site web public dans Office 365.
  
    
    
Le gestionnaire de conception vous permet de créer une conception visuelle pour votre site web à l'aide de l'outil de conception web ou de l'éditeur HTML de votre choix, en utilisant uniquement les langages HTML et CSS, puis de télécharger cette conception dans SharePoint. Le gestionnaire de conception fait office d'interface et de hub central, à partir duquel vous pouvez gérer tous les aspects d'une conception personnalisée.
  
    
    
La conception de l'aspect visuel d'un site s'inscrit souvent dans un processus plus large, dans lequel plusieurs personnes ou organisations sont impliquées. Pour obtenir une feuille de route des tâches dans le cadre d'une perspective plus large, voir le  [document relatif à la conception et à la personnalisation dans SharePoint 2013 ](http://go.microsoft.com/fwlink/?LinkId=262838)
  
    
    
À un niveau global, le concepteur doit effectuer les tâches suivantes :
  
    
    

- Maîtriser les concepts essentiels de conception dans SharePoint. Pour plus d'informations, voir  [Vue d'ensemble du modèle de page SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
    
  
- Créer une maquette de la conception aux formats HTML et CSS. La création de conceptions étant une compétence de base des concepteurs web, elle n'est pas abordée dans cet article.
    
  
- Implémenter la conception à l'aide du gestionnaire de conception. Les sections de cet article fournissent une présentation du gestionnaire de conception et expliquent comment l'utiliser pour mettre en œuvre une conception visuelle.
    
  

> **REMARQUE**
> Les éléments de conception que vous pouvez créer pour un site web public dans SharePoint Online sont différents de ceux des autres sites de publication. En outre, vous ne pouvez pas créer de packages de conception dans la version du gestionnaire de conception disponible dans le site web public de SharePoint Online. 
  
    
    


## Utilisation du gestionnaire de conception pour implémenter une conception
<a name="Use"> </a>

Lorsque vous vous trouvez dans le gestionnaire de conception, une série de liens apparaissent sur le côté gauche. Ils représentent les tâches de haut niveau que vous aurez à accomplir. Selon votre conception et les besoins de votre site, il se peut que vous n'ayez pas à effectuer toutes ces tâches ou que vous ne deviez pas nécessairement les effectuer dans cet ordre. Ceci dit, cette liste est un point de départ utile.
  
    
    

### Avant de commencer

Avant de pouvoir utiliser le gestionnaire de conception, vous devez disposer d'une conception. Vous pouvez en créer une ou utiliser un modèle de site web prêt à l'emploi. Une « conception » est, tout simplement, un groupe de fichiers qui définissent l'aspect visuel de votre site, généralement :
  
    
    

- Au moins un fichier HTML qui sera converti en page maître SharePoint
    
  
- Un ou plusieurs fichiers CSS
    
  
- Des fichiers JavaScript
    
  
- Des images
    
  
- D'autres fichiers de prise en charge
    
  
Lorsque vous créez une maquette de votre site aux formats HTML et CSS, vous devez généralement utiliser plusieurs fichiers HTML pour implémenter les conceptions qui déterminent la façon dont les pages ou types de page doivent apparaître. Rappelez-vous que seul l'un de ces fichiers HTML sera converti en page maître (sauf si vous disposez de plusieurs canaux d'appareils et que chaque canal possède sa propre page maître ; voir la section suivante). Après avoir créé d'autres éléments de site (comme des mises en page ou des modèles d'affichage) à l'aide du gestionnaire de conception, vous pouvez transférer le balisage de vos maquettes HTML vers les fichiers HTML et CSS associés à la mise en page ou au modèle d'affichage.
  
    
    
Avant de commencer, vous devez également disposer des autorisations SharePoint nécessaires. Pour utiliser le gestionnaire de conception, vous devez au moins disposer du niveau d'autorisation Concepteur.
  
    
    

### Gestion des canaux d'appareils

Avant même de concevoir votre site, vous devez déterminer les appareils qu'il doit cibler et l'expérience utilisateur que vous souhaitez offrir pour chaque appareil. Par exemple, vous pouvez optimiser la conception du site pour une certaine catégorie de smartphones ou de tablettes.
  
    
    
Selon les canaux que vous définissez, vous aurez peut-être besoin de plusieurs conceptions, et donc de plusieurs fichiers HTML, qui seront chacun convertis en une page maître distincte. En outre, chaque fichier HTML (et par conséquent, chaque page maître) peut référencer son propre fichier CSS. Avant de concevoir votre site, pensez en priorité à la configuration des canaux d'appareils.
  
    
    
Les canaux d'appareils permettent de générer des affichages différents pour un même site de publication, en mappant des conceptions distinctes à divers appareils. Chaque canal peut ainsi avoir sa propre page maître, liée à une feuille de style optimisée pour un appareil spécifique. Chaque canal spécifie des sous-chaînes d'agent utilisateur correspondant à un ou plusieurs appareils, comme « Windows Phone OS ». Il s'agit de règles qui déterminent les appareils inclus dans chaque canal. Lorsque les visiteurs consultent votre site, chaque canal détecte le trafic correspondant à son appareil ou sa catégorie d'appareils (les Windows Phones, par exemple) et le site s'affiche selon une conception spécifiquement optimisée pour l'appareil des utilisateurs.
  
    
    
Les canaux d'appareils sont créés et stockés dans une liste SharePoint dans un ordre spécifique, car les canaux des appareils sont, eux aussi, hiérarchisés. Ils sont classés de haut en bas et les règles d'inclusion sont appliquées dans cet ordre. Cela signifie que les canaux disposant des règles les plus spécifiques doivent être placés en haut de la liste. Par exemple, un canal ciblant « Windows Phone OS 7.0 » doit être placé avant un canal ciblant « Windows Phone OS ».
  
    
    

### Téléchargement des fichiers de conception

Pour créer une conception, vous pouvez utiliser l'éditeur HTML de votre choix et travailler sur les fichiers sur votre ordinateur. Cependant, vous devrez ensuite télécharger ces fichiers dans la galerie de pages maîtres de votre site SharePoint, afin de pouvoir utiliser le gestionnaire de conception pour convertir, prévisualiser et parfaire votre conception.
  
    
    
Le moyen le plus simple de télécharger les fichiers de conception et de continuer à travailler dessus est de mapper un lecteur de votre ordinateur à la galerie de pages maîtres de votre site SharePoint. Cette opération connecte un dossier de votre ordinateur à la galerie de pages maîtres, ce qui vous permet de travailler sur des fichiers qui se trouvent sur le serveur SharePoint 2013 comme s'il s'agissait de fichiers locaux.
  
    
    
Après avoir mappé un lecteur réseau, vous pouvez télécharger votre conception sur SharePoint, en copiant simplement les fichiers de conception dans un dossier du lecteur mappé de votre ordinateur qui est connecté à SharePoint. Après avoir converti votre fichier HTML en page maître SharePoint et créé des mises en page et des modèles d'affichage dotés chacun de leur propre fichier HTML associé, vous pouvez continuer à modifier ces fichiers HTML dans l'éditeur HTML de votre ordinateur. Chaque fois que vous enregistrez un fichier sur le lecteur mappé, SharePoint synchronise automatiquement les fichiers de votre ordinateur avec la galerie de pages maîtres. Vous pouvez créer votre propre structure de dossiers sur le lecteur mappé ; cette structure sera conservée par SharePoint et apparaîtra dans la galerie de pages maîtres. Placez tous les fichiers associés à une conception dans un même dossier, puis copiez ce dossier sur le lecteur mappé lorsque vous êtes prêt à télécharger votre conception.
  
    
    
Pour plus d'informations, voir  [Comment mapper un lecteur réseau sur la galerie Pages maîtres SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

### Modification des pages maîtres

La création d'une page maître entièrement personnalisée contenant toutes les fonctionnalités SharePoint que vous souhaitez, comme la navigation et la recherche, se divise en trois grandes étapes :
  
    
    

1. Convertir un fichier HTML en page maître SharePoint
    
  
2. Afficher un aperçu de la page maître et résoudre tous les problèmes
    
  
3. Ajouter des extraits de code SharePoint à la page maître
    
  
Chacune de ces trois étapes est effectuée sur une page différente du gestionnaire de conception.
  
    
    

#### Conversion d'un fichier HTML

La fonctionnalité principale du gestionnaire de conception est de convertir votre conception HTML en page maître SharePoint. Pour un affichage correct, une page maître SharePoint doit contenir de nombreux éléments ASP.NET, ainsi que des éléments propres à SharePoint. Lorsque vous convertissez un fichier HTML en page maître, le gestionnaire de conception crée un fichier .master qui contient tous ces éléments, vous n'avez ainsi pas besoin de connaissances particulières à leur sujet. Lors de la conversion, certaines balises HTML (comme des commentaires) sont également ajoutées à votre fichier HTML d'origine.
  
    
    
Après la conversion, le fichier HTML et la page maître SharePoint sont associés, de sorte que lorsque vous modifiez et enregistrez le fichier HTML sur votre lecteur mappé, la page maître est mise à jour automatiquement. Dans le gestionnaire de conception, la page maître HTML possède une propriété nommée **Fichier associé**, qui détermine si les modifications apportées au fichier HTML sont synchronisées sur le fichier .master.
  
    
    

> **REMARQUE**
> Le gestionnaire de conception fournit également une option permettant de commencer la conception en utilisant une page maître minimale. Dans ce cas, vous n'avez pas besoin de partir d'une conception HTML : vous pouvez créer une page maître HTML qui ne contient que les éléments de page strictement nécessaires pour afficher la page maître correctement dans SharePoint, puis construire votre conception en modifiant cette page maître HTML. 
  
    
    


#### Affichage d'un aperçu de la page maître

En plus de la conversion de votre page maître, le gestionnaire de conception permet d'en générer un aperçu côté serveur (différent de l'aperçu dans votre éditeur HTML lors de la conception), ce qui vous permet d'obtenir un aperçu instantané de votre page maître et de résoudre tous les problèmes qui pourraient empêcher son affichage. Par exemple, votre fichier HTML doit être compatible XML, ce qui implique que vous pouvez avoir à corriger des problèmes de balisage mineurs, comme l'ajout de balises de fermeture pour tous les éléments. Pour résoudre tous les problèmes, vous devez modifier le fichier HTML, l'enregistrer, puis actualiser l'aperçu côté serveur.
  
    
    
Lorsque vous prévisualisez une page maître, vous pouvez utiliser l'option **Modifier la page d'aperçu** dans le coin supérieur gauche pour afficher un aperçu de la page maître avec une page existante, ou créer une page sur laquelle générer l'aperçu. Contrairement à l'aperçu de l'éditeur HTML, lors de la conception, l'aperçu instantané côté serveur est entièrement fonctionnel ; mieux vaut donc modifier le fichier HTML, l'enregistrer pour synchroniser les dernières modifications sur le fichier .master associé, puis actualiser l'aperçu instantané pour consulter vos dernières modifications de conception dans le navigateur.
  
    
    

#### Ajout d'extraits de code

Après avoir converti votre page maître et généré un aperçu satisfaisant, vous êtes prêt à ajouter des extraits de code à la page maître. Un extrait de code est une représentation HTML d'un composant SharePoint (comme un contrôle de navigation, une zone de recherche ou un composant WebPart) que vous pouvez ajouter à votre page maître. L'ajout d'extraits de code à votre page maître permet de créer rapidement la gamme complète des fonctionnalités SharePoint sur votre page maître. L'ajout d'extraits de code s'effectue essentiellement en trois étapes :
  
    
    

1. Rechercher et configurer des extraits de code dans la galerie d'extraits de code
    
  
2. Copier des extraits de code dans votre page maître HTML
    
  
3. Générer des aperçus et appliquer des styles aux extraits de code à l'aide de CSS
    
    Pour plus d'informations, voir  [Extraits de code du Gestionnaire de conception SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  

#### Recherche et configuration des extraits de code dans la galerie d'extraits de code

La galerie d'extraits de code permet de consulter rapidement les composants disponibles pour le type de fichier que vous modifiez (page maître ou mise en page). Vous devez commencer par sélectionner un extrait de code sur le ruban. La grille de propriétés située à droite vous permet de configurer les propriétés de cette instance d'extrait de code. Cliquez ensuite sur **Mettre à jour** pour actualiser l'extrait de code HTML à gauche.
  
    
    

#### Copie d'extraits de code dans votre page maître HTML

Après avoir configuré un extrait de code, copiez-le dans le Presse-papiers, puis collez-le à l'emplacement approprié de votre fichier HTML. Votre conception HTML peut déjà contenir des contrôles de maquette ou des contrôles statiques, auquel cas, vous devez les supprimer ou les commenter en les remplaçant par des extraits de code dynamiques de la galerie d'extraits de code.
  
    
    

#### Génération d'aperçus et application de styles aux extraits de code à l'aide de CSS

Après avoir copié des extraits de code dans votre fichier HTML, puis enregistré les modifications, vous pouvez actualiser l'aperçu côté serveur de la page maître pour vérifier l'affichage du contrôle. Les extraits de code contiennent des balises permettant de générer un aperçu au moment de la conception dans un éditeur HTML, mais vous pouvez aussi générer un aperçu côté serveur, qui est entièrement fidèle et affiche des données actives : par exemple, un contrôle de navigation affiche la structure de navigation actuelle du site et les données actives issues de votre source de données.
  
    
    
Par défaut, la plupart des extraits de code héritent des styles de la feuille de style SharePoint 2013 principale, corev15.css. Pour appliquer des styles à un extrait de code, vous devez identifier les styles appliqués à l'extrait de code, puis les remplacer par ceux de votre feuille de style CSS personnalisée. Pour identifier ces styles par défaut, vous pouvez utiliser un outil de navigateur, tel que les outils de développement d'Internet Explorer. Lorsque vous générez un aperçu de l'affichage de votre page maître côté serveur dans Internet Explorer, appuyez sur **F12**, choisissez **Rechercher**, puis **Sélectionner l'élément par clic**. Cela vous permet de cliquer sur l'extrait de code et de voir exactement les styles à remplacer, en ajoutant des styles CSS à toute feuille de style personnalisée à laquelle votre page maître est associée.
  
    
    

### Modification des modèles d'affichage

Si vous utilisez une installation sur site de SharePoint Server, vous pouvez utiliser le composant WebPart Recherche de contenu et d'autres composants WebPart de recherche pour afficher les résultats des requêtes de recherche en tant que contenu sur vos pages. Les composants WebPart de recherche utilisent des modèles d'affichage à deux fins principales :
  
    
    

- Pour mapper les propriétés gérées renvoyées dans les résultats de recherche à des propriétés qui seront disponibles pour JavaScript, y compris tout script JavaScript personnalisé que vous choisissez d'implémenter.
    
  
- Pour utiliser les codes HTML et CSS afin de présenter l'affichage de ces propriétés et de gérer les styles régissant cet affichage.
    
  
Avec les pages maîtres et les mises en page, vous modifiez un fichier HTML associé, mais pas le fichier .master ou .aspx. De même, les modèles d'affichage sont constitués d'un fichier HTML et d'un fichier .js associé, mais seul le fichier HTML est modifié. Chaque fois que vous enregistrez ce fichier HTML, SharePoint met automatiquement à jour le fichier .js associé.
  
    
    
Pour créer un modèle d'affichage personnalisé, vous devez commencer par copier et modifier l'un des modèles d'affichage existants. Cette méthode est pratique car les modèles d'affichage par défaut contiennent des informations sous forme de commentaires dans les fichiers HTML, et vous disposez ainsi d'une infrastructure et de la structure de base correcte de la page pour effectuer des tâches de base, comme le mappage des champs de saisie.
  
    
    

### Modification des mises en page

Le processus de création d'une mise en page est légèrement différent de la création d'une page maître. Pour une page maître, vous commencez avec une conception HTML, la convertissez en page maître SharePoint, puis continuez à modifier le fichier HTML associé. Pour une mise en page, en revanche, vous devez d'abord créer la mise en page dans le gestionnaire de conception, ce qui crée un fichier .aspx et un fichier HTML, puis modifier le fichier HTML associé se trouvant sur le lecteur mappé dans votre éditeur HTML. Vous devez utiliser le gestionnaire de conception ici pour que le bon ensemble de champs de page soit ajouté à la mise en page.
  
    
    
Lorsque vous créez une mise en page, vous devez sélectionner une page maître à partir de laquelle générer un aperçu de votre mise en page, puis sélectionner le type de contenu de mise en page. Un type de contenu est un schéma de champs et de types de données. Les champs disponibles pour le type de contenu de mise en page déterminent les contrôles de champ de page disponibles sur la mise en page que vous concevez. Vous devez d'abord créer une mise en page dans le navigateur pour que les champs de page puissent être ajoutés.
  
    
    
Après avoir créé une mise en page avec son fichier HTML associé, les étapes suivantes sont les mêmes que pour une page maître :
  
    
    

- Afficher un aperçu de la mise en page et résoudre tous les problèmes en modifiant et en enregistrant la version HTML
    
  
- Ajouter des extraits de code à la mise en page (configurer, copier, afficher un aperçu, gérer les styles)
    
  
Dans la galerie d'extraits de code, plusieurs extraits sont disponibles pour les mises en page et les pages maîtres, et le ruban n'affiche que les extraits de code qui sont pertinents pour votre type de fichier. Par exemple, les extraits de code de navigation et de zone de recherche ne sont disponibles que pour les pages maîtres, tandis que les champs de page ne sont disponibles que pour les mises en page.
  
    
    
Lorsque vous concevez une mise en page, votre tâche principale consiste à positionner les contrôles de champ de page qui permettront d'afficher le contenu créé par les auteurs, et à en définir les styles. Les styles d'une mise en page peuvent être issus de n'importe quelle feuille de style à laquelle la page maître est associée. Sinon, chaque mise en page peut être liée à sa propre feuille de style. Si votre conception HTML comprend du contenu qui est plus adapté à une mise en page qu'à une page maître, vous devez transférer ce contenu hors de votre page maître HTML, puis appliquer ces styles aux contrôles et éléments concernés de la mise en page correspondante.
  
    
    
Pour plus d'informations, voir  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
  
    
    

### Création de thèmes et d'apparences composées

Dans le site web public Office 365 (mais pas dans les installations sur site de SharePoint Server 2013), le gestionnaire de conception dispose d'une option permettant de créer des thèmes et des apparences composées. Un thème est un ensemble de polices et de couleurs qui peuvent être appliquées à une conception personnalisée (c'est-à-dire, une page maître). Les thèmes sont définis dans des fichiers .xml que vous téléchargez vers la galerie de thèmes. Pour pouvoir appliquer des thèmes à une page maître personnalisée, vous devez ajouter à la page maître un balisage spécial que SharePoint reconnaît et utilise pour insérer des éléments de thème tels que des polices et des couleurs.
  
    
    
Une apparence composée est simplement l'association d'une image d'arrière-plan, d'un thème (c'est-à-dire, de polices et de couleurs) et d'une conception (c'est-à-dire, d'une page maître). Une apparence composée utilise des éléments de conception prédéfinis (thèmes, images d'arrière-plan et pages maîtres) et permet de les combiner de différentes façons, offrant ainsi bien plus d'options de personnalisation pour le site public.
  
    
    

### Publication et application de la conception

La plupart des éléments utilisés par votre conception, tels que des images, fichiers HTML, CSS et JavaScript, doivent résider dans la galerie de pages maîtres. La galerie de pages maîtres est une bibliothèque de documents SharePoint dans laquelle, par défaut, le contrôle des versions est activé, ce qui crée des versions principale et secondaires (brouillons) chaque fois que vous modifiez un fichier.
  
    
    
Avant de pouvoir appliquer votre conception à un site, vous devez d'abord publier une version principale de chaque fichier ou élément utilisé par votre conception. Si vous concevez votre site dans un environnement de test, vous devez désactiver le contrôle des versions pour la galerie de pages maîtres, pour éviter d'avoir à vous rappeler de publier chaque fichier avant de générer un aperçu du site. En revanche, ce n'est pas une pratique conseillée si vous concevez un site actif.
  
    
    
Après avoir publié tous les fichiers de conception, vous êtes prêt à appliquer la conception en affectant vos pages maîtres finies à votre site. Pour chaque site, vous pouvez affecter une page maître différente à chaque canal d'appareil, et c'est sur cette page du gestionnaire de conception que vous appliquez une page maître à un canal.
  
    
    

### Création d'un package de conception

Un package de conception est un moyen simple de rassembler tous les fichiers et éléments utilisés par votre conception, de les exporter d'un site, de les importer dans un autre site et d'appliquer la conception à ce nouveau site. Si vous implémentez et peaufinez votre conception dans une collection de sites de test et que vous souhaitez la déployer dans une collection de sites actifs, vous pouvez utiliser un package de conception pour la transférer.
  
    
    
Un package de conception est un fichier .wsp, un fichier solution SharePoint, qui est un type particulier de fichier .cab. Lorsque vous créez ou importez un package de conception, le fichier .wsp est stocké dans la galerie de solutions. Après importation, le package de conception est automatiquement activé. Si les pages maîtres et les mises en page ont été publiées avant d'être mises en package, et si les pages maîtres ont été affectées à des canaux d'appareils avant d'être mises en package, la conception sera automatiquement appliquée au site lors du déploiement du package de conception. Sinon, pour appliquer la conception à ce nouveau site, il vous suffit de publier les fichiers de conception et d'appliquer les pages maîtres pour chaque canal d'appareil.
  
    
    

> **REMARQUE**
> Les packages de conception ne sont pas disponibles dans le site web public Office 365. Pour implémenter une conception entièrement personnalisée avec le gestionnaire de conception, vous pouvez inviter un concepteur sur votre site en lui accordant temporairement le niveau d'autorisation Concepteur. 
  
    
    


## Ressources supplémentaires
<a name="Additional"> </a>


-  [Vue d'ensemble du modèle de page SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [Procédure : Convertir un fichier HTML en page maître dans SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Procédure : Créer une mise en page dans SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  

