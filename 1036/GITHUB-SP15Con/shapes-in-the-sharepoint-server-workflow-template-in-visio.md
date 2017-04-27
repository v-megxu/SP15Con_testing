---
title: Formes dans le modèle de flux de travail SharePoint Server dans Visio
ms.prod: SHAREPOINT
ms.assetid: f35bdf5d-c102-4e2d-8a23-1d2df17155b9
---



# Formes dans le modèle de flux de travail SharePoint Server dans Visio
Découvrez les formes dans le modèle de flux de travail SharePoint 2013 dans Visio 2013.
## Introduction
<a name="VSSPD_Shapes_Intro"> </a>

Cet article répertorie les formes contenues dans le modèle de flux de travail SharePoint 2013 dans Visio 2013 et dans le concepteur visuel dans SharePoint Designer 2013. Lors de l'ouverture du modèle, ouvre également les actions de flux de travail SharePoint 2013, les conditions de flux de travail SharePoint 2013 et les gabarits de terminateurs de flux de travail SharePoint 2013. De nombreuses formes répertoriées dans les gabarits correspondent à des actions spécifiques, des conditions ou autres constructions logiques dans le concepteur déclaratif pour la création de flux de travail dans SharePoint Designer 2013.
  
    
    

> **IMPORTANTE**
> Ce qui suit est une référence pour les actions de flux de travail prises en charge dans SharePoint Designer 2013. La plupart de ces actions sont disponibles dans SharePoint Designer 2010, bien que l'une d'entre elles (Attendre un événement dans un élément de liste) ait été révisée et améliorée dans la version actuelle. Douze nouvelles actions ont été introduites dans la version actuelle et 25 actions ont été supprimées. (Pour consulter la liste des actions, des conditions et des blocs supprimés, voir  [Actions de flux de travail disponibles via la passerelle interopérabilité de base de flux de travail](workflow-actions-available-using-the-workflow-interop-bridge.md).) 
  
    
    


## Formes Action
<a name="VSSDP_Actions"> </a>

Le tableau suivant présente une liste de toutes les formes contenues dans le gabarit Actions SharePoint 2013 du modèle de flux de travail SharePoint 2013 dans Visio 2013.
  
    
    

> **REMARQUE**
> Chaque forme répertoriée dans le tableau suivant aura une propriété **Propriétés** et ses propriétés seront répertoriées.
  
    
    



|**Forme dans Visio 2013 et dans le concepteur visuel SharePoint Designer 2013**|**Action dans le concepteur déclaratif SharePoint Designer 2013**|**Propriétés dans le concepteur visuel SharePoint Designer 2013**|**Description**|
|:-----|:-----|:-----|:-----|
|Ajouter un commentaire  <br/> |**Ajouter un commentaire** <br/> |**Commentaire** <br/> |Permet de laisser des commentaires dans le concepteur de flux de travail à des fins de référence. Ceci est particulièrement utile quand plusieurs utilisateurs collaborent sur le flux de travail.  <br/> |
|Ajouter l'heure à la date  <br/> |**Ajouter l'heure à la date** <br/> |**Mois** <br/> **Jours** <br/> **Heures** <br/> **Minutes** <br/> **Date** <br/> **Résultat** <br/> |Ajoute une heure spécifique en minutes, heures, jours ou mois à une date et stocke la valeur de sortie dans une variable. La valeur de date peut être la date du jour, une date spécifique ou le résultat d'une recherche. La valeur « Date en cours » renvoie à minuit UTC.  <br/> |
|Affecter une tâche  <br/> |**Affecter une tâche** <br/> |**Paramètres de la tâche** <br/> **Résultat de la tâche** <br/> **ID de l'élément de tâche** <br/> |Affecte une tâche de flux de travail à un utilisateur et définit une échéance pour la fin de cette tâche.  <br/> |
|Appeler le service web HTTP  <br/> |**Appeler le service web HTTP** <br/> |**Requête HTTP** <br/> **Paramètres** <br/> **Variable de contenu de réponse** <br/> **Variable d'en-tête de réponse** <br/> **Variable de code de réponse** <br/> |Fonctionne en tant qu'appel de méthode à un service web HTTP.  <br/> > **REMARQUE**> La version actuelle prend en charge les appels SharePoint uniquement aux services HTTP **anonymes** et uniquement à l'aide des paramètres et types de retour **string**. Les éléments XML composites ne sont pas pris en charge. Seuls les éléments ASMX classiques sont pris en charge, le service WCG ne l'est pas.           |
|Archiver l'élément  <br/> |**Archiver l'élément** <br/> |**Élément** <br/> **Commentaire** <br/> |Archive un élément qui est extrait. Vous pouvez archiver des éléments uniquement à partir d'une bibliothèque de documents.  <br/> > **ATTENTION**> Le flux de travail se bloque si vous essayez d'archiver un élément qui n'est pas extrait.           |
|Extraire l'élément  <br/> |**Extraire l'élément** <br/> |**Élément** <br/> |Extrait un élément. Le flux de travail vérifie si l'élément est archivé avant d'extraire un document. Vous pouvez extraire des éléments uniquement à partir d'une bibliothèque de votre site.  <br/> > **ATTENTION**> Le flux de travail se bloque si vous essayez d'extraire un élément qui n'est pas archivé.           |
|Copier le document  <br/> |**Copier le document** <br/> |**Document** <br/> **Bibliothèque** <br/> |Copie un document à partir de la liste actuelle vers une autre liste de la bibliothèque de documents.  <br/> |
|Compter les éléments du dictionnaire  <br/> |**Nombre d'éléments dans un dictionnaire** <br/> |**Dictionnaire** <br/> **Variable de sortie** <br/> |Compte le nombre d'éléments dans une variable de dictionnaire.  <br/> |
|Créer un projet à partir de l'élément actif  <br/> |**Créer un projet à partir de l'élément actuel** <br/> |**Type de projet d'entreprise** <br/> |Prend l'élément actuel et crée un projet dans le site PWA de batterie de serveurs SharePoint.  <br/> |
|Créer un élément dans la liste  <br/> |**Créer un élément dans la liste** <br/> |**Élément** <br/> **Variable de sortie** <br/> |Crée un élément de liste dans la liste que vous spécifiez. Vous pouvez fournir les champs et les valeurs dans le nouvel élément. Vous pouvez utiliser cette action pour créer un élément avec des informations spécifiques.  <br/> |
|Supprimer l'élément  <br/> |**Supprimer l'élément** <br/> |**Élément** <br/> |Supprime un élément.  <br/> > **REMARQUE**> Cette action est effectuée sur l'ordinateur qui exécute le moteur de flux de travail du Gestionnaire de workflow et génère une exception **System.InvalidOperationException**. Il n'existe aucune solution de contournement.           |
|Ignorer l'extraction  <br/> |**Annuler l'extraction de l'élément** <br/> |**Élément** <br/> |Annule les modifications et archive à nouveau l'élément si celui-ci a été extrait et que des modifications y ont été apportées.  <br/> > **ATTENTION**> Le flux de travail se bloque si vous essayez d'archiver un élément qui n'est pas extrait.           |
|Effectuer un calcul  <br/> |**Effectuer un calcul** <br/> |**Opérande gauche** <br/> **Opérateur** <br/> **Opérande droite** <br/> **Pour** <br/> |Effectue un calcul arithmétique et stocke la valeur de sortie dans une variable.  <br/> > **REMARQUE**> Dans SharePoint 2013, cette action ne prend en charge que le type numérique **Double**. Les entiers ne sont pas pris en charge. L'utilisation de l'opérateur « + » (concaténation) pour les chaînes n'est pas pris en charge.           |
|Extraire la sous-chaîne de la fin de la chaîne  <br/> |**Extraire la sous-chaîne de la fin de la chaîne** <br/> |**Nombre de caractères** <br/> **Chaîne** <br/> **Résultat** <br/> |Copie un nombre spécifié de caractères à partir de la fin d'une chaîne et stocke la sortie dans une variable.  <br/> |
|Extraire la sous-chaîne de l'index de la chaîne  <br/> |**Extraire la sous-chaîne de l'index de la chaîne** <br/> |**Chaîne** <br/> **Index** <br/> **Résultat** <br/> |Copie une sous-chaîne à partir d'un index spécifié dans la chaîne et place la valeur dans une variable.  <br/> > **REMARQUE**> Notez que SharePoint Designer utilise un index de base zéro dans la présente version d'évaluation technique, tandis que les valeurs de SharePoint Designer 2010 sont indexées à partir de 1.           |
|Extraire la sous-chaîne depuis le début de la chaîne  <br/> |**Extraire la sous-chaîne depuis le début de la chaîne** <br/> |**Nombre de caractères** <br/> **Chaîne** <br/> **Résultat** <br/> |Copie un nombre spécifié de caractères à partir du début d'une chaîne et stocke la sortie dans une variable.  <br/> |
|Extraire la sous-chaîne de la chaîne à partir de l'index avec la longueur  <br/> |**Extraire la sous-chaîne de la chaîne à partir de l'index avec la longueur** <br/> |**Chaîne** <br/> **Index** <br/> **Nombre de caractères** <br/> **Résultat** <br/> |Copie une sous-chaîne comprenant un nombre spécifié de caractères, à partir d'un index spécifié dans la chaîne, et place la valeur dans une variable.  <br/> > **REMARQUE**> Notez que SharePoint Designer utilise un index de base zéro dans la présente version d'évaluation technique, tandis que les valeurs de SharePoint Designer 2010 sont indexées à partir de 1.           |
|Rechercher l'intervalle entre les dates  <br/> |**Rechercher l'intervalle entre les dates** <br/> |**Unités** <br/> **Date de début** <br/> **Date de fin** <br/> **Résultat** <br/> |Calcule l'intervalle en minutes, heures ou jours entre deux dates et stocke la sortie dans une variable.  <br/> |
|Rechercher la sous-chaîne dans la chaîne  <br/> |**Rechercher la sous-chaîne dans la chaîne** <br/> |**Sous-chaîne** <br/> **Chaîne** <br/> **Résultat** <br/> |Recherche une sous-chaîne spécifique dans une chaîne et renvoie l'index de la position de départ de la sous-chaîne.  <br/> |
|Obtenir l'élément du dictionnaire  <br/> |**Obtenir l'élément du dictionnaire** <br/> |**Nom ou chemin d'accès de l'élément** <br/> **Dictionnaire** <br/> **Variable de sortie** <br/> |Renvoie un élément spécifique à partir d'une variable de dictionnaire.  <br/> |
|Consigner dans l'historique  <br/> |**Consigner dans l'historique** <br/> |**Message** <br/> |Écrit un message dans la liste d'historique des flux de travail à partir d'une liste d'éléments de messages prédéfinis.  <br/> |
|Mettre en pause pour une certaine durée  <br/> |**Mettre en pause pour une certaine durée** <br/> |**Jours** <br/> **Heures** <br/> **Minutes** <br/> |Suspend le flux de travail pour un intervalle spécifié en jours, heures et minutes.  <br/> |
|Mettre en pause jusqu'à une date donnée  <br/> |**Mettre en pause jusqu'à une date donnée** <br/> |**Date** <br/> |Suspend le flux de travail jusqu'à une date et une heure spécifiées.  <br/> |
|Remplacer la sous-chaîne dans la chaîne  <br/> |**Remplacer la sous-chaîne dans la chaîne** <br/> |**Chaîne de recherche** <br/> **Chaîne de remplacement** <br/> **Chaîne** <br/> **Résultat** <br/> |Remplace une sous-chaîne spécifique par une autre sous-chaîne.  <br/> |
|Envoyer un courrier électronique  <br/> |**Envoyer un courrier électronique** <br/> |**Courrier électronique** <br/> |Envoie automatiquement un message électronique qui contient un message prédéterminé à un utilisateur ou un groupe lorsqu'un événement de flux de travail spécifié se produit.  <br/> > **IMPORTANTE**> Si le site n'est pas ajouté à la liste des sites de confiance, les messages électroniques sont routés vers le dossier de courrier indésirable d'Outlook.           |
|Définir le champ dans l'élément actif  <br/> |**Définir le champ dans l'élément actif** <br/> |**Champ** <br/> **Valeur** <br/> |Affecte une valeur à un champ dans l'élément actuel.  <br/> |
|Définir la partie heure du champ Date/Heure  <br/> |**Définir la partie heure du champ Date/Heure** <br/> |**Heures** <br/> **Minutes** <br/> **Date** <br/> **Résultat** <br/> |Crée un horodatage et stocke la valeur de sortie dans une variable. Vous pouvez définir l'heure en heures et en minutes, ainsi qu'ajouter la date du jour, une date spécifique ou le résultat d'une recherche.  <br/> |
|Définir l'état du flux de travail  <br/> |**Définir l'état du flux de travail** <br/> |**État** <br/> |Définit l'état du flux de travail.  <br/> |
|Définir la variable de flux de travail  <br/> |**Définir la variable de flux de travail** <br/> |**Variable** <br/> **Valeur** <br/> |Affecte une valeur à une variable de flux de travail. Vous pouvez également utiliser cette action pour que le flux de travail affecte des données à une variable.  <br/> |
|Démarrer un flux de travail de liste  <br/> |**Démarrer un flux de travail de liste** <br/> |**Nom de l'association** <br/> **Entrées** <br/> **Élément** <br/> |Démarre un flux de travail de liste SharePoint 2010.  <br/> > **REMARQUE**>  Le démarrage d'un flux de travail de liste présente les problèmes suivants :>  Le champ de type « Affectations » ne peut pas être utilisé comme un paramètre lorsque le flux de travail 2010 renferme une action TaskProcess.>  Lorsque plusieurs appels sont effectués sur le même flux de travail 2010, des sources de données multiples sont générées dans la fonctionnalité de recherche de flux de travail 2013. Ces sources de données sont toutes identiques.>  Les noms des variables dans la version 2013 ne peuvent pas contenir de caractères spéciaux tels que « ? » et « # ». Si un flux de travail 2010 contient des caractères spéciaux, il est converti en code hexadécimal dans le flux de travail 2013.          |
|Démarrer un flux de travail de site  <br/> |**Démarrer un flux de travail de site** <br/> |**Nom de l'association** <br/> **Paramètres** <br/> |Démarre un flux de travail de site SharePoint 2010.  <br/> > **REMARQUE**>  Le démarrage d'un flux de travail de site présente les problèmes suivants :>  Le champ de type « Affectations » ne peut pas être utilisé comme un paramètre lorsque le flux de travail 2010 renferme une action TaskProcess.>  Lorsque plusieurs appels sont effectués sur le même flux de travail 2010, des sources de données multiples sont générées dans la fonctionnalité de recherche de flux de travail 2013. Ces sources de données sont toutes identiques.>  Les noms des variables dans la version 2013 ne peuvent pas contenir de caractères spéciaux tels que « ? » et « # ». Si un flux de travail 2010 contient des caractères spéciaux, il est converti en code hexadécimal dans le flux de travail 2013.          |
|Démarrer un processus de tâche  <br/> |**Démarrer un processus de tâche** <br/> |**Paramètres du processus** <br/>  Résultat du processus <br/> |Crée des tâches pour plusieurs utilisateurs et permet de les prendre par le biais d'un processus personnalisé.  <br/> |
|Traduire le document  <br/> |**Traduire le document** <br/> |**Document** <br/> **Langue** <br/> **Bibliothèque de documents** <br/> |Traduit un document dans une langue spécifique.  <br/> > **REMARQUE**> Nécessite une application de service de traduction automatique préconfigurée.           |
|Découper la chaîne  <br/> |**Découper la chaîne** <br/> |**Chaîne** <br/> **Résultat** <br/> |Supprime les espaces en début et en fin de chaîne.  <br/> |
|Mettre à jour l'élément de la liste  <br/> |**Mettre à jour l'élément de la liste** <br/> |**Élément** <br/> |Met à jour un élément de liste. Vous pouvez spécifier les champs et les nouvelles valeurs que vous souhaitez leur attribuer.  <br/> |
|Attendre un événement dans un élément de liste  <br/> |**Attendre un événement dans un élément de liste** <br/> |**Événement** <br/> **Élément connexe** <br/> |[Version améliorée de l'action Office 2010.] Suspend l'instance de flux de travail en cours pour attendre l'événement d'élément de liste spécifié. Cette action fonctionne pour deux types d'événement : **ItemUpdated** et **ItemAdded**.  <br/> |
|Attendre la modification du champ  <br/> |**Attendre la modification du champ** <br/> |**Champ** <br/> **Valeur** <br/> |Attend qu'un champ de l'élément actuel soit égal à une valeur spécifique.  <br/> |
|Définir le champ de projet  <br/> |**Définir le champ de projet** <br/> |**Champ** <br/> **Valeur** <br/> |Définit une valeur pour un champ spécifique dans Project Server.  <br/> > **REMARQUE**> Cette action nécessite d'archiver d'abord le projet. Si le projet n'est pas archivé, le flux de travail est arrêté et les utilisateurs ne peuvent pas ouvrir ce projet dans Project Web App.           |
|Définir l'état de l'étape du projet  <br/> |**Définir l'état de l'étape du projet** <br/> |**État de l'étape** <br/> **Informations de l'étape** <br/> |Définit l'état de l'étape du projet.  <br/> > **REMARQUE**> Une exception se produit lorsqu'un projet en cours est extrait.           |
|Définir le champ d'état dans la liste d'idées  <br/> |**Définir le champ d'état dans la liste d'idées** <br/> |**État** <br/> |Met à jour l'état de l'élément de liste d'origine qui est associé au projet actuel.  <br/> |
|Attendre un événement de projet  <br/> |**Attendre un événement de projet** <br/> |**Nom de l'événement** <br/> |Attend un événement de projet spécifique.  <br/> |
   

## Formes Condition
<a name="VSSPD_Conditions"> </a>

Le tableau suivant présente la liste de toutes les formes contenues dans le gabarit Conditions SharePoint 2013 du modèle de flux de travail SharePoint 2013.
  
    
    


|**Forme dans Visio 2013 et dans le concepteur visuel SharePoint Designer 2013**|**Action dans le concepteur déclaratif SharePoint Designer 2013**|**Propriétés dans le concepteur visuel SharePoint Designer 2013**|**Description**|
|:-----|:-----|:-----|:-----|
|Si une valeur est égale à la valeur  <br/> |**Si une valeur est égale à la valeur** <br/> |**Valeur** <br/> **Opérande** <br/> **Valeur** <br/> |Compare deux valeurs. Vous pouvez indiquer si les valeurs doivent être égales ou non.  <br/> |
|La personne est un utilisateur SharePoint valide  <br/> |**La personne est un utilisateur SharePoint valide** <br/> |**Utilisateur** <br/> |Vérifie si un utilisateur spécifique est un utilisateur inscrit ou un membre d'un groupe sur le site SharePoint.  <br/> |
|Ignorer le stade de projet  <br/> |**Ignorer le stade de projet** <br/> |N/A  <br/> |Cette condition vérifie si la fonctionnalité Ignorer le stade a été activée sur le serveur pour l'instance de flux de travail actuelle.  <br/> |
   

## Formes Terminateur
<a name="VSSPD_Terminators"> </a>

Le tableau suivant présente une liste de toutes les formes contenues dans le gabarit Terminateurs SharePoint 2013 du modèle de flux de travail SharePoint 2013.
  
    
    


|**Forme dans Visio 2013 et dans le concepteur visuel SharePoint Designer 2013**|**Action dans le concepteur déclaratif SharePoint Designer 2013**|**Propriétés dans le concepteur visuel SharePoint Designer 2013**|**Description**|
|:-----|:-----|:-----|:-----|
|Début  <br/> |N/A  <br/> |N/A  <br/> |Démarre le flux de travail. Chaque diagramme de flux de travail SharePoint 2013 doit comporter une seule forme de début.  <br/> |
|Stade  <br/> |**Stade** <br/> |N/A  <br/> |Contient un certain nombre de formes et peut inclure un branchement. Toutes les actions du flux de travail doivent figurer dans un stade. Vous pouvez visualiser les formes de stade à l'aide de formes de conteneur. Une forme de stade exige l'ajout d'une forme d'entrée et de sortie aux bords du conteneur de manière à définir les chemins permettant d'entrer et de sortir de l'étape.  <br/> Pour plus d'informations, consultez la section relative aux stades, boucles et étapes dans l'article  [Développement de flux de travail dans SharePoint Designer et Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Étape  <br/> |**Étape** <br/> |N/A  <br/> |Représente une série groupée d'actions séquentielles. Les étapes doivent être contenues dans un stade. Une forme d'étape doit également comporter une forme d'entrée et de sortie, qui sont ajoutées lorsque la forme est déposée sur le canevas.  <br/> Pour plus d'informations, consultez la section relative aux stades, boucles et étapes dans l'article  [Développement de flux de travail dans SharePoint Designer et Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Étape unique  <br/> |**Stade** <br/> |N/A  <br/> |Ajoute de nouveaux stades au niveau supérieur du flux de travail lorsque vous êtes dans la vue des stades dans Visio 2013.  <br/> |
|Boucle n fois  <br/> |**Boucle n fois** <br/> |**Nombre de boucles** <br/> |Définit une série de formes connectées qui seront exécutées en boucle, repartant de la dernière forme de la série à la première jusqu'à ce que la boucle ait été exécutée le nombre de fois spécifié. Comme les stades, les boucles sont représentées par une forme de conteneur comportant une forme d'entrée et de sortie.  <br/> Pour plus d'informations, consultez la section relative aux stades, boucles et étapes dans l'article  [Développement de flux de travail dans SharePoint Designer et Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Boucle avec condition  <br/> |**Boucle avec condition** <br/> |**Nombre de boucles** <br/> |Effectue une boucle jusqu'à ce qu'une condition spécifique soit remplie.  <br/> |
|Démarrer une action parallèle  <br/> |**Bloc parallèle** <br/> |N/A  <br/> ||
|Terminer une action parallèle  <br/> |**Bloc parallèle** <br/> |N/A  <br/> ||
   

## Ressources supplémentaires
<a name="VSSPD_Additional"> </a>


-  [Développement de flux de travail dans SharePoint Designer et Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [Référence rapide relative aux actions de flux de travail (plateforme de flux de travail SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Guide des formes de modèles de flux de travail SharePoint](http://office.microsoft.com/fr-fr/visio-help/sharepoint-workflow-template-shapes-guide-HA101903894.aspx)
    
  
-  [Centre de développement SharePoint](http://msdn.microsoft.com/fr-fr/sharepoint/default.aspx)
    
  
-  [Centre de développement Visio](http://msdn.microsoft.com/fr-fr/office/aa905478)
    
  
