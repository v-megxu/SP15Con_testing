---
title: Développement de flux de travail dans SharePoint Designer et Visio
ms.prod: SHAREPOINT
ms.assetid: 496780d5-47d6-4a43-bf14-70aefb8d820c
---


# Développement de flux de travail dans SharePoint Designer et Visio
Découvrez comment utiliser Visio 2013 et SharePoint Designer 2013 pour créer et publier des flux de travail sur un site SharePoint 2013 sans recourir à du code.
## Introduction
<a name="VSSPD_Intro"> </a>

Visio 2013 et SharePoint Designer 2013 facilitent la collaboration et la création de flux de travail aux analystes d'entreprise, consultants de processus et professionnels de l'informatique. Visio Professionnel 2013 et le concepteur visuel dans SharePoint Designer 2013 offrent une représentation riche des flux de travail dans un format compréhensible pour les programmeurs et les non-programmeurs.
  
    
    

> **REMARQUE**
> Pour obtenir des instructions sur le paramétrage et la configuration de SharePoint Server 2013 et du serveur Workflow Manager, voir  [Configurer le flux de travail dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj658586.aspx). 
  
    
    

Visio 2013 permet de créer visuellement un flux de travail SharePoint, de l'exporter vers SharePoint Designer 2013, puis de le publier sur un site SharePoint. Une fois le flux de travail créé dans Visio 2013, il doit être exporté vers SharePoint Designer 2013. Un propriétaire de site SharePoint ou un professionnel de l'informatique ajoute ensuite des paramètres au flux de travail à l'aide de l'éditeur de texte ou du nouveau concepteur visuel du flux de travail, lequel constitue un contrôle ActiveX Visio 2013 hébergé dans SharePoint Designer 2013. Une fois le flux de travail terminé, il peut être publié sur le site SharePoint.
  
    
    
Cette fonction est idéale pour les analystes d'entreprise et les consultants de processus déjà familiarisés avec les diagrammes de flux dans Visio, car elle leur permet de concevoir un flux de travail que représente la logique métier. La personne qui conçoit le flux de travail peut se concentrer uniquement sur les besoins en aide à la décision (BI) du flux de travail sans être experte en flux de travail déclaratifs.
  
    
    

## À propos de la création de flux de travail SharePoint dans Visio 2013 et SharePoint Designer 2013
<a name="VSSPD_About"> </a>

Visio 2013 inclut un modèle de flux de travail SharePoint 2013 pouvant être utilisé pour créer des flux de travail SharePoint 2013. Le modèle de flux de travail SharePoint 2013 est associé à trois gabarits : les actions de flux de travail SharePoint 2013, les conditions de flux de travail SharePoint 2013 et les terminateurs de flux de travail SharePoint 2013. Les formes de ces gabarits correspondent à des actions et des conditions spécifiques pouvant être utilisées dans un flux de travail SharePoint 2013. Pour créer un flux de travail, il vous suffit de déposer les formes sur la zone de dessin Visio 2013 pour modéliser la logique métier derrière le flux de travail.
  
    
    

### Phases, boucles et étapes

Les flux de travail dans SharePoint Designer 2013 incluent maintenant les notions de phases, de boucles et d'étapes. Les auteurs de flux de travail peuvent regrouper un certain nombre d'actions et de conditions individuelles dans une seule unité afin de définir plus clairement le processus. Par exemple, ils peuvent introduire une phase ou une étape d'approbation ou d'obtention de commentaires. Cette phase ou étape contiendrait toutes les actions nécessaires à ce processus. La phase ou l'étape elle-même pourrait être le nœud d'un flux de travail plus long, permettant à un observateur de connaître l'état de cette phase dans son ensemble, plutôt qu'un ensemble d'actions individuelles.
  
    
    
Le modèle de flux de travail SharePoint 2013 inclus dans Visio 2013 utilise également des phases, boucles et étapes, telles que des blocs de construction logiques pour la création de flux de travail. 
  
    
    

> **IMPORTANTE**
> En raison des différences sous-jacentes entre les modèles de flux de travail Microsoft SharePoint 2010 et SharePoint 2013, vous ne pouvez pas utiliser les formes d'un modèle dans un diagramme créé par un autre modèle. Seules les formes des gabarits Actions de flux de travail SharePoint 2013, Conditions de flux de travail SharePoint 2013 et Terminateurs de flux de travail SharePoint 2013 peuvent être utilisés pour créer un flux de travail SharePoint 2013 workflow. 
  
    
    


### Formes de phase

Une phase peut contenir n'importe quel nombre de formes et inclure un branchement. Toutefois, il ne peut y avoir qu'un chemin vers une phase (et une étape) et qu'un chemin hors de celle-ci. Toutes les actions dans le flux de travail doivent être contenues par une phase. Les formes de phase sont affichées à l'aide des formes de conteneur. La forme d'une phase requiert l'ajout de formes d'entrée et de sortie aux bords du conteneur pour définir les chemins vers et hors de la phase. Visio 2013 et le concepteur visuel dans SharePoint Designer 2013 ajoutent les formes d'entrée et de sortie pour vous lorsque vous déposez le conteneur pour la première fois.
  
    
    
Les phases respectent également les règles suivantes :
  
    
    

- Tous les diagrammes doivent posséder au moins une phase. Une phase, ainsi que ses formes d'entrée, de sortie et de début, font partie du modèle de flux de travail SharePoint 2013 par défaut.
    
  
- Lorsque vous ajoutez une nouvelle phase à la zone de dessin, Visio 2013 ajoute les connecteurs de début et de fin lorsque la phase est déposée.
    
  
- Les phases ne peuvent pas avoir de connecteurs d'entrée et de sortie autrement que via les formes d'entrée et de sortie.
    
  
- Les conteneurs de phase ne peuvent pas être imbriqués. Si vous souhaitez imbriquer un autre sous-processus dans une phase, utilisez une étape.
    
  
- Les formes de flux de travail d'arrêt peuvent exister dans une phase.
    
  
- Une forme de début explicite est requise hors de la phase pour l'ensemble du diagramme. Une forme de terminaison explicite hors de la phase n'est pas requise.
    
  
- Au niveau supérieur, le flux de travail ne peut contenir que des phases, des formes conditionnelles et des terminateurs de début et de terminaison. Toutes les autres formes doivent être contenues dans une phase.
    
  

### Formes de boucle

Les boucles sont une série de formes connectées qui s'exécutent en boucle, repassant de la dernière forme de la série à la première, jusqu'à ce qu'une condition soit satisfaite. 
  
    
    
Comme les phases, les boucles sont représentées par une forme de conteneur incluant une forme d'entrée et une forme de sortie (ajoutées lorsque la forme est déposée sur la zone de dessin). Une forme de boucle requiert également l'ajout d'une forme d'entrée et de sortie aux bords du conteneur pour définir les chemins vers et hors de la boucle.
  
    
    
Visio 2013 et SharePoint Designer 2013 prennent en charge deux types de boucles : la boucle  *n*  fois et la boucle jusqu'à ce que *value1*  soit égale à *value2*  .
  
    
    
Les boucles doivent également respecter les règles suivantes :
  
    
    

- Les boucles doivent être situées dans une phase, et les phases ne peuvent pas être situées dans une boucle.
    
  
- Les étapes peuvent être situées dans une boucle.
    
  
- Les boucles ne peuvent avoir qu'un seul point d'entrée et de sortie.
    
  

### Formes d'étape

Les étapes représentent une série groupée d'actions séquentielles. Elles doivent être contenues par une phase. Une forme d'étape doit également posséder une forme d'entrée et de sortie pour définir les chemins vers et hors de la forme. Les deux formes sont ajoutées par défaut lorsque la forme est déposée sur la zone de dessin.
  
    
    

## Création d'un flux de travail dans Visio 2013
<a name="VSSPD_Creating"> </a>

Toutes les formes de base des gabarits de flux de travail SharePoint 2013 correspondent à des actions, des conditions et autres constructions logiques d'un flux de travail SharePoint 2013. Pour créer un flux de travail, vous pouvez déposer des formes sur la zone de dessin, comme n'importe quel autre diagramme de flux dans Visio. Une fois le flux de travail créé dans Visio 2013, enregistrez-le pour que SharePoint Designer 2013 puisse l'ouvrir.
  
    
    
Pour ouvrir le modèle de flux de travail SharePoint 2013 dans Visio 2013, procédez comme suit :
  
    
    

### Pour ouvrir le modèle de flux de travail SharePoint 2013 dans Visio 2013 :


1. Ouvrez Visio 2013.
    
  
2. Sélectionnez **Nouveau**.
    
  
3. Sous **Catégories de modèles**, sélectionnez **Diagramme de flux**.
    
  
4. Sous **Choisissez un modèle**, sélectionnez **Flux de travail SharePoint 2013**, puis **Créer**.
    
    Le modèle s'ouvre et la zone de dessin est préremplie avec les formes de début et de phase. La forme de phase contient une forme d'entrée et de sortie, reliées par un connecteur unique.
    
  
Avec le modèle de flux de travail SharePoint 2013 ouvert, déposez les actions, conditions et autres formes sur la zone de dessin pour concevoir un flux de travail. Pour plus d'informations sur les formes individuelles et leur signification, consultez l'article  [Formes dans le modèle de flux de travail SharePoint Server dans Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md).
  
    
    

> **CONSEIL**
>  Lorsque vous concevez un flux de travail, gardez à l'esprit les notions supplémentaires suivantes :>  Pour créer rapidement un flux de travail, déposez les formes d'action et de condition sur le connecteur interne contenu par les nouvelles formes de phase. Visio 2013 divise automatiquement le connecteur en connecteurs supplémentaires, en maintenant le flux de travail connecté entre la forme d'entrée et celle de sortie.>  N'utilisez pas les formes d'un gabarit autre que les actions de flux de travail SharePoint 2013, les conditions de flux de travail SharePoint 2013 et les terminateurs de flux de travail SharePoint 2013. Utilisez uniquement l'outil Connecteur fourni par le modèle de flux de travail SharePoint 2013 pour ajouter des connexions entre les formes. Toutes les autres formes de connecteur ne sont pas valides dans un flux de travail SharePoint 2013.>  Les formes d'action, les étapes et les boucles doivent toujours être contenues dans une forme de phase. Il est possible de trouver certaines formes conditionnelles hors d'une phase.>  Une forme de phase doit contenir précisément une forme d'entrée et une forme de sortie. Le sous-processus de flux de travail contenu dans la phase doit commencer par la forme d'entrée et finir par celle de sortie.>  Une forme de condition doit posséder deux connecteurs quittant la forme, l'un étiqueté « Oui », l'autre étiqueté « Non ». Vous pouvez cliquer avec le bouton droit sur un connecteur pour choisir **Oui** ou **Non**. >  Un flux de travail ne doit contenir qu'une seule forme de début. La forme de début doit être située hors d'une phase.>  Vous pouvez ajouter du texte aux formes dans le flux de travail, mais le texte de la forme n'affectera pas le flux de travail.
  
    
    


  
    
    
La validation du flux de travail dans Visio 2013 est identique à celle de tout autre diagramme connecté : Visio vérifie le diagramme en fonction d'un ensemble de règles et renvoie la liste des erreurs trouvées dans le diagramme. Pour découvrir comment résoudre les problèmes de validation, consultez l'article  [Dépannage des erreurs de validation des flux de travail SharePoint Server 2013 dans Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md).
  
    
    

### Pour valider un flux de travail SharePoint 2013 dans Visio 2013 :


1. Dans l'onglet **Processus**, dans le groupe **Validation de diagramme**, sélectionnez **Vérifier le diagramme**.
    
  
2. Si des erreurs sont détectées dans le flux de travail, le volet **Problèmes** s'ouvre sous le diagramme. Choisissez chaque élément de la liste pour sélectionner la forme du diagramme qui constitue la cause de l'erreur.
    
  
3. Corrigez chaque erreur de validation répertoriée dans la liste **Problèmes**. Après avoir corrigé toutes les erreurs, sélectionnez **Vérifier le diagramme** à nouveau. Pour plus d'informations sur la résolution des problèmes de validation dans Visio 2013, consultez l'article [Dépannage des erreurs de validation des flux de travail SharePoint Server 2013 dans Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md).
    
  
4. Si aucune erreur n'est détectée dans le flux de travail, Visio affiche un message indiquant que la validation de diagramme est terminée et qu'aucun problème n'a été trouvé.
    
  
Une fois le flux de travail validé dans Visio 2013, vous pouvez enregistrer le fichier et l'importer dans SharePoint Designer 2013. Contrairement au modèle de flux de travail Microsoft SharePoint 2010, vous pouvez enregistrer une copie du diagramme de flux de travail SharePoint 2013 par défaut au format de fichier Visio 2013 (.vsdx). De cette façon, SharePoint Designer 2013 peut ouvrir le fichier. 
  
    
    
Utilisez la procédure suivante pour enregistrer un flux de travail SharePoint 2013 dans Visio 2013 en tant que fichier .vsdx Visio 2013 pouvant être ouvert dans SharePoint Designer 2013 :
  
    
    

### Pour enregistrer un flux de travail dans Visio 2013 :


1. Sélectionnez **Fichier**, puis **Enregistrer sous**.
    
  
2. Sous **Enregistrer sous**, sélectionnez **Enregistrer**, puis **Parcourir**.
    
  
3. Dans la boîte de dialogue **Enregistrer sous**, sélectionnez un emplacement pour enregistrer le fichier et tapez le nom du fichier (« Mon flux de travail SP »).
    
  
4. Sélectionnez **Enregistrer**.
    
  

## Personnalisation et publication d'un flux de travail dans SharePoint Designer 2013
<a name="VSSPD_Customizing"> </a>

Une fois que vous avez créé la logique métier sous-jacente du flux de travail SharePoint 2013 dans Visio 2013 et enregistré le diagramme, vous pouvez ouvrir le fichier .vsdx Visio dans SharePoint Designer 2013 et commencer à personnaliser le flux de travail pour votre site SharePoint 2013. Le package du fichier .vsdx contient des documents XML que SharePoint Designer 2013 peut traduire par des flux de travail.
  
    
    
Utilisez la procédure suivante pour ouvrir un site SharePoint 2013 dans SharePoint Designer 2013 :
  
    
    

### Pour ouvrir un site SharePoint 2013 dans SharePoint Designer 2013 :


1. Ouvrez SharePoint Designer 2013.
    
  
2. Sous **Ouvrir le site SharePoint**, sélectionnez **Ouvrir le site**.
    
  
3. Dans la boîte de dialogue **Ouvrir le site**, sélectionnez le site que vous souhaitez ouvrir.
    
  
4. Sélectionnez **Ouvrir**.
    
  
Après avoir ouvert le site SharePoint 2013, vous pouvez ouvrir le diagramme .vsdx Visio 2013 dans SharePoint Designer 2013.
  
    
    

### Pour ouvrir un flux de travail Visio Professionnel 2013 dans SharePoint Designer 2013 :


1. Sélectionnez **Fichier**, puis **Ajouter un élément**.
    
  
2. Pour créer un flux de travail de liste, procédez comme suit :
    
1. Sous **Flux de travail**, sélectionnez **Flux de travail de liste**.
    
  
2. Dans le volet gauche sous **Flux de travail de liste**, tapez un nom pour votre flux de travail (Mon premier flux de travail SP2013) et sélectionnez la liste sur le site sur lequel vous souhaitez publier le flux de travail.
    
  
3. Dans la liste **Choisir la plateforme pour le nouveau flux de travail**, sélectionnez **Flux de travail SharePoint 2013**.
    
  
4. Choisissez **Créer**.
    
  
3. Pour créer un flux de travail de site, procédez comme suit :
    
1. Sous **Flux de travail**, sélectionnez **Flux de travail de site**.
    
  
2. Dans le volet gauche sous **Flux de travail de site**, tapez un nom pour votre flux de travail (Mon premier flux de travail SP2013).
    
  
3. Dans la liste **Choisir la plateforme pour le nouveau flux de travail**, sélectionnez **Flux de travail SharePoint 2013**.
    
  
4. Choisissez **Créer**.
    
  
4. Dans l'onglet **Flux de travail**, dans le groupe **Gérer**, sélectionnez **Paramètres du flux de travail**.
    
  
5. Dans l'onglet **Paramètres du flux de travail**, dans le groupe **Gérer**, sélectionnez **Importer à partir de Visio**.
    
  
6. Dans la boîte de dialogue **Importer un flux de travail d'un dessin Visio**, accédez à l'emplacement où se trouve le fichier .vsdx.
    
  
7. Sélectionnez le fichier que vous souhaitez ouvrir (Mon flux de travail SP), puis sélectionnez **Ouvrir**.
    
  
Lorsque vous ouvrez un fichier .vsdx dans SharePoint Designer 2013, celui-ci est affiché dans le concepteur visuel, un contrôle ActiveX Visio hébergé dans SharePoint Designer. Le diagramme Visio 2013 conserve toutes les formes et le texte de forme qui a été créé dans Visio. 
  
    
    

> **REMARQUE**
> Pour basculer entre les concepteurs visuel et déclaratif dans SharePoint Designer 2013, dans l'onglet **Flux de travail**, dans le groupe **Gérer**, choisissez **Vues**. Ce processus peut prendre quelques instants, étant donné que SharePoint Designer 2013 valide le flux de travail, puis convertit les informations de flux de travail d'un format à un autre. Au cours de ce processus, une autre validation au niveau des formes est effectuée. Si des erreurs sont détectées sur le diagramme, elles sont affichées dans un volet d'erreur au bas de la zone de dessin (comme dans Visio). 
  
    
    

Les formes affichées dans le concepteur visuel possèdent également des balises d'action (indiquées par une icône de type paramètres de flux de travail sur le côté gauche en bas de la forme). Lorsque vous choisissez une balise d'action, un menu déroulant affiche les attributs pour cette action ou cette condition dans le flux de travail et la propriété **Propriétés**. Ces propriétés définissent les valeurs des paramètres à utiliser pour cette action : les listes desquelles seront extraits les éléments, l'opérateur de calcul à utiliser, l'adresse de courrier électronique à laquelle envoyer un message. Lorsque vous choisissez une propriété affichée dans la liste, une boîte de dialogue apparaît, dans laquelle vous pouvez personnaliser les paramètres de cette propriété. 
  
    
    
Par exemple, la forme **Envoyer un courrier électronique** possède deux propriétés qui lui sont associées : **Créer un courrier électronique** et **Propriétés**. Lorsque vous choisissez **Créer un courrier électronique**, la boîte de dialogue **Définir un message électronique** apparaît, dans laquelle vous pouvez créer le message à envoyer par l'action. Si vous choisissez **Propriétés**, la boîte de dialogue **Propriétés d'envoi de courrier électronique** apparaît ; elle affiche tous les paramètres de l'action.
  
    
    

> **REMARQUE**
> Pour plus d'informations sur les actions individuelles, les formes et leurs propriétés, consultez les articles  [Formes dans le modèle de flux de travail SharePoint Server dans Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md) et [Référence rapide relative aux actions de flux de travail (plateforme de flux de travail SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md). 
  
    
    

Une fois que vous avez défini les propriétés dans le flux de travail et que celles-ci sont prêtes à être publiées, vous devez d'abord vérifier le flux de travail à la recherche d'erreurs dans SharePoint Designer 2013. Lorsque vous choisissez **Publier** dans l'onglet **Concepteur visuel** dans le ruban, SharePoint Designer 2013 vérifie automatiquement les erreurs du flux de travail. Si vous le souhaitez, vous pouvez également lancer manuellement la vérification des erreurs.
  
    
    
Utilisez la procédure suivante pour vérifier le flux de travail SharePoint 2013 dans SharePoint Designer 2013 :
  
    
    

### Pour vérifier manuellement les erreurs d'un flux de travail dans SharePoint Designer 2013 :


1. Dans l'onglet **Concepteur visuel**, dans le groupe **Enregistrer**, choisissez **Rechercher les erreurs**.
    
  
2. Si des erreurs sont détectées dans le flux de travail, le volet **Problèmes** s'ouvre sous la zone de dessin du concepteur visuel. Choisissez chaque élément de la liste pour sélectionner l'action, la condition, le connecteur, le terminateur ou le conteneur du flux de travail à l'origine de l'erreur.
    
  
3.  Corrigez chaque erreur de validation répertoriée dans la liste **Problèmes**. Après avoir corrigé toutes les erreurs, sélectionnez **Rechercher les erreurs** à nouveau.
    
  
4. Si aucune erreur n'est détectée dans le flux de travail, SharePoint Designer affiche un message indiquant qu'aucun problème n'a été détecté dans le flux de travail.
    
  
Une fois que le flux de travail a été vérifié et qu'aucune erreur n'a été détectée, vous pouvez le publier dans la liste SharePoint. Pour publier le flux de travail à partir de SharePoint Designer 2013, dans l'onglet **Concepteur visuel**, dans le groupe **Enregistrer**, choisissez **Publier**. Si des erreurs se produisent lors du processus de publication, SharePoint Designer 2013 revient dans le concepteur visuel et affiche les erreurs dans le volet **Problèmes**.
  
    
    

## Ressources supplémentaires
<a name="VSSPD_Additional"> </a>

Pour plus d'informations, voir les ressources suivantes :
  
    
    

-  [Référence rapide relative aux actions de flux de travail (plateforme de flux de travail SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Formes dans le modèle de flux de travail SharePoint Server dans Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)
    
  
-  [Dépannage des erreurs de validation des flux de travail SharePoint Server 2013 dans Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)
    
  
-  [Créer, importer et exporter des flux de travail SharePoint dans Visio](http://office.microsoft.com/fr-fr/visio-help/create-import-and-export-sharepoint-workflows-in-visio-HA101888007.aspx)
    
  
-  [Centre de développement SharePoint](http://msdn.microsoft.com/fr-fr/sharepoint/default.aspx)
    
  
-  [Centre de développement Visio](http://msdn.microsoft.com/fr-fr/office/aa905478)
    
  

