---
title: Notions de base sur les flux de travail SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 1e622296-f78b-4e3a-a1e7-8effa24111a8
---


# Notions de base sur les flux de travail SharePoint 2013
Offre une vue d'ensemble de l'infrastructure de flux de travail dans SharePoint 2013, notamment une présentation de l'architecture de la plateforme et du pont d'interopérabilité de flux de travail.
## Vue d'ensemble des flux de travail dans SharePoint 2013
<a name="bkm_overview"> </a>

Les flux de travail SharePoint 2013 sont alimentés par Windows Workflow Foundation 4, considérablement remodelé par rapport aux versions antérieures. Par ailleurs, Windows Workflow Foundation (WF) est basé sur la fonctionnalité de messagerie fournie par  [Windows Communication Foundation (WCF)](http://msdn.microsoft.com/fr-fr/library/vstudio/ms735119%28v=vs.90%29.aspx).
  
    
    
Au niveau conceptuel, les flux de travail modélisent des processus d'entreprise structurés. Par conséquent, les flux de travail Windows Workflow Foundation 4 constituent un ensemble structuré d'activités de flux de travail et chacune d'elles représente un composant fonctionnel d'un processus d'entreprise.
  
    
    
La plateforme de flux de travail dans SharePoint 2013 utilise le modèle d'activité Windows Workflow Foundation 4 pour représenter un processus d'entreprise basé sur SharePoint. En outre, SharePoint 2013 introduit un modèle par étape de niveau supérieur sur lequel créer des flux de travail.
  
    
    
Il convient de signaler la relation entre les activités de flux de travail et lesactions SharePoint. Les activités de flux de travail représentent les objets gérés sous-jacents dont les méthodes induisent le comportement de flux de travail. En revanche, les actions de flux de travail sont des wrappers qui encapsulent les activités sous-jacentes et les présentent dans un formulaire convivial dans SharePoint Designer. Les auteurs de flux de travail interagissent avec les actions de flux de travail, tandis que le moteur d'exécution de flux de travail agit sur les activités correspondantes.
  
    
    
Les activités, qui sont des implémentations de classes d'activités, sont mises en oeuvre de façon déclarative à l'aide de XAML.
  
    
    
Les activités de flux de travail sont appelées à l'aide de services web faiblement couplés qui utilisent des API de messagerie pour communiquer avec SharePoint. Ces API sont basées sur la fonctionnalité de messagerie fournie par  [Windows Communication Foundation (WCF)](http://msdn.microsoft.com/fr-fr/library/vstudio/ms735119%28v=vs.90%29.aspx).
  
    
    
L'infrastructure de messagerie est très souple et prend en charge quasiment tous les modèles de messagerie nécessaires. Notez que sur une batterie de serveurs SharePoint 2013, Windows Workflow Foundation et WCF sont hébergés dans Workflow Manager Client 1.0.
  
    
    
Workflow Manager Client 1.0, SharePoint 2013 et SharePoint Designer 2013 fournissent chacun des parties significatives de la nouvelle infrastructure :
  
    
    

- **Workflow Manager Client 1.0** fournit la gestion des définitions de flux de travail et héberge les processus d'exécution pour les instances de flux de travail.
    
  
- **SharePoint 2013** fournit l'infrastructure des flux de travail SharePoint, qui modélisent les processus d'entreprise basés sur SharePoint impliquant des tâches, des listes, des utilisateurs et des documents SharePoint. En outre, les flux de travail SharePoint, les associations, les activités et autres métadonnées de flux de travail sont stockées et gérées dans SharePoint 2013.
    
  
- **SharePoint Designer 2013** constitue le principal outil utilisateur d'entreprise pour la création et la publication de définitions de flux de travail, comme dans les versions précédentes. Il peut également être utilisé pour mettre en package une définition de flux de travail avec ou sans composants SharePoint associés.
    
  

## Architecture de la plateforme
<a name="bkm_Architecture"> </a>

La figure 1 présente une vue d'ensemble de l'infrastructure de flux de travail SharePoint 2013. Notez, tout d'abord, que la nouvelle infrastructure de flux de travail présente Workflow Manager Client 1.0 comme le nouvel hôte d'exécution de flux de travail. Contrairement aux versions précédentes, dans SharePoint 2013, l'exécution de flux de travail n'est plus hébergée dans SharePoint. Workflow Manager Client 1.0 est externe à SharePoint et communique à l'aide de protocoles communs sur le bus des services Microsoft Azure, via OAuth. Par ailleurs, SharePoint comprend les fonctionnalités prévues : éléments de contenu, événements, applications, etc. Il existe également une implémentation de l'hôte de flux de travail SharePoint 2010 (en d'autres termes, le moteur Windows Workflow Foundation 3) pour la compatibilité descendante. Pour plus d'informations, voir  [Utilisez interopérabilité des flux de travail pour SharePoint 2013](use-workflow-interop-for-sharepoint-2013.md).
  
    
    

**Figure 1. Architecture de niveau supérieur de l'infrastructure de flux de travail**

  
    
    

  
    
    
![Architecture de flux de travail de niveau supérieur](images/wfArchitecture1.png)
  
    
    
Workflow Manager Client 1.0 est représenté dans SharePoint 2013 sous forme de proxy d'application de service Workflow Manager Client 1.0. Ce composant permet à SharePoint de communiquer et d'interagir avec le serveur Workflow Manager Client 1.0. L'authentification de serveur à serveur est fournie par OAuth.
  
    
    
Les événements SharePoint pour lesquels un flux de travail est à l'écoute, comme **itemCreated**, **itemUpdated**, etc., sont routés vers Workflow Manager Client 1.0 à l'aide du bus des services Microsoft Azure. Pour le retour, la plateforme utilise l'API REST SharePoint pour effectuer un appel dans SharePoint.
  
    
    
Le modèle objet de flux de travail SharePoint a subi des ajouts, rassemblés dans le gestionnaire des services de flux de travail, qui vous permettent de gérer et de contrôler vos flux de travail et leur exécution. Les zones principales d'interaction du gestionnaire de services sont le déploiement, la messagerie, le contrôle d'instance et (pour la compatibilité descendante) l'interopérabilité avec les flux de travail SharePoint 2010.
  
    
    
Enfin, il existe le composant de création de flux de travail. SharePoint Designer peut désormais créer et déployer les flux de travail de SharePoint 2010 et SharePoint 2013. Visual Studio 2012 ne fournit pas seulement un espace de conception pour la création de flux de travail déclaratifs, mais peut aussi créer des Compléments SharePoint et des solutions qui intègrent pleinement la fonctionnalité Workflow Manager Client 1.0.
  
    
    

## Abonnements et associations de flux de travail
<a name="bkm_Subscriptions"> </a>

La modification la plus importante apportée aux flux de travail SharePoint 2013 étant le déplacement du traitement sur les hôtes de flux de travail externes tels que Microsoft Azure, une connexion à l'infrastructure de flux de travail dans Microsoft Azure s'est avérée essentielle pour les messages et les événements Sharepoint, ainsi qu'une connexion entre l'infrastructure et les données des clients pour Microsoft Azure . Les associations de flux de travail (basées sur le concept d'abonnements WF) sont les éléments d'infrastructure SharePoint qui prennent en charge ces exigences.
  
    
    

### Service de publication/d'abonnement Microsoft Azure

Pour pouvoir aborder les abonnements et les associations de flux de travail, vous devez consulter le service de publication/d'abonnementMicrosoft Azure, connu sous le nom de pub/sub ou simplementPubSub. PubSub est une infrastructure de messagerie asynchrone. Les expéditeurs de messages (éditeurs) n'envoient pas de messages directement aux récepteurs (abonnés). Au lieu de cela, les messages sont affichés en tant que classes par les éditeurs sans connaissance des abonnés. Les abonnés utilisent ensuite les messages publiés en identifiant les messages d'intérêt, quel que soit l'éditeur, en fonction des abonnements qu'ils ont créés.
  
    
    
Cette séparation entre création de message et consommation de message permet l'évolutivité et la flexibilité, ainsi que la messagerie multidiffusion côté éditeur et la libre consommation de message côté abonné.
  
    
    

> **REMARQUE**
> La fonctionnalité PubSub fait partie de Microsoft Azure Service Bus, qui offre des options de connectivité pour WCF et d'autres points de terminaison de service, notamment les points de terminaison REST, lesquels peuvent être situés derrière les limites de traduction d'adresses réseau (NAT) ou liés à des adresses IP affectées dynamiquement et modifiées fréquemment, ou les deux. Pour plus d'informations sur Azure Service Bus, voir  [Service Bus](http://msdn.microsoft.com/fr-fr/library/ee732537.aspx). 
  
    
    


### Associations de flux de travail et étendue d'association

Les associations de flux de travail lient les définitions de flux de travail à une étendue SharePoint spécifique, avec des valeurs par défaut données. Les associations elles-mêmes représentent un ensemble de règles d'abonnement stockées dans le service de publication/d'abonnement Azure qui traite les messages entrants afin de s'assurer qu'ils sont consommés par des instances de flux de travail appropriées (c'est-à-dire, abonnées).
  
    
    
Par défaut, l'infrastructure de messagerie prend en charge les flux de travail dans les étendues suivantes :
  
    
    

-  [SPList](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPList.aspx) (pour les flux de travail de liste)
    
  
-  [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) (pour les flux de travail de site)
    
  
Contrairement aux versions précédentes, SharePoint 2013 ne prend pas en charge les flux de travail dont l'étendue s'applique à un type de contenu ( [SPContentType](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPContentType.aspx) ). Toutefois, l'infrastructure de messagerie étant extensible, elle peut prendre en charge n'importe quelle étendue arbitraire. En tant que développeur, vous pouvez définir la propriété [EventSourceId](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscription.EventSourceId.aspx) sur une instance [WorkflowSubscription](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.WorkflowSubscription.aspx) donnée sur n'importe quel **guid**. Vous pouvez utiliser la valeur **EventSourceId** pour appeler **PublishEvent(Guid, String, IDictionary<String, Object>)**, qui déclenche une nouvelle instance de flux de travail de la propriété **WorkflowSubscription** spécifiée.
  
    
    

### Service de flux de travail dans Microsoft Azure

Les associations des flux de travail SharePoint sont représentées par leur service de flux de travail dans Microsoft Azure. Lorsqu'une application doit acquérir une association de flux de travail et ses données, elle doit d'abord soumettre une requête à tous les services de flux de travail disponibles sur une étendue donnée.
  
    
    
De même, les instances de flux de travail rapportent un pointeur à leurs services de flux de travail respectifs. C'est de cette façon que leur association appropriée est déterminée.
  
    
    

### Démarrage des flux de travail

Les flux de travail peuvent être démarrés manuellement ou automatiquement.
  
    
    
 **Flux de travail manuels**
  
    
    
Les flux de travail manuels démarrent lorsque le service PubSub reçoit un message **StartWorkflow**. Le message contient les informations descriptives suivantes :
  
    
    

- L'identificateur d'association (en d'autres termes, l'instance **WorkflowSubscription**)
    
  
- L'ID du contexte d'élément d'origine. Il est transmis avec le paramètre  _ItemId_ et la propriété **EventSource** sur l'appel de méthode **PublishEvent**.
    
  
- Le type d'événement pour un démarrage manuel ( **WorkflowStart**).
    
  
- Les paramètres d'initiation de flux de travail supplémentaires, à partir de l'abonnement ou du formulaire **Init**, selon le cas ( **CorrelationId** pour l'abonnement et **WFInstanceId** pour le formulaire **Init**).
    
  
 **Flux de travail à démarrage automatique**
  
    
    
Les flux de travail à démarrage automatique sont lancés à l'aide d'un message **Add** envoyé au service PubSub. Le message contient les informations descriptives suivantes :
  
    
    

- L'ID du contexte d'élément d'origine
    
  
- L'événement lui-même en tant qu'événement **Add** SharePoint normal
    
  
- Les paramètres de lancement du flux de travail
    
  

> **REMARQUE**
> Lorsqu'un flux de travail démarre automatiquement sur un événement renouvelable (par exemple, sur l'événement **OnItemChanged**), il ne peut pas démarrer un autre flux de travail d'une association donnée jusqu'à ce que l'exécution de l'instance existante de flux de travail de l'association soit terminée. 
  
    
    


### Abonnements de flux de travail

Le complément naturel des associations est les abonnements : ils permettent au flux de travail d'interagir avec celles-ci. Le flux de travail doit créer des abonnements sur Azure Service Bus à l'aide des méthodes **create** et **delete**.
  
    
    
Les signatures des méthodes qui créent l'abonnement et instancient le flux de travail spécifient les paramètres facultatifs et obligatoires. La liste des paramètres est déterminée par le créateur du flux de travail ; ils peuvent donc varier d'une définition de flux de travail à une autre. La liste des paramètres d'abonnement est spécifiée en tant que métadonnées des définitions de flux de travail. Les paramètres d'abonnement sont fournis lorsque celui-ci est créé. La liste des paramètres d'initialisation est spécifiée dans XAML et fait partie de la définition de flux de travail. Les paramètres d'initialisation sont fournis lorsque le flux de travail est instancié.
  
    
    
Les abonnements sont liés à un objet SharePoint spécifique : une instance **SPList** ou **SPWeb**. Le type d'objet d'abonnement est transmis en tant que valeur d'un paramètre obligatoire lorsque l'abonnement est créé. Le type d'objet définit l'étendue de l'abonnement, de sorte que l'abonnement ne peut répondre qu'à des événements qui se produisent sur l'objet auquel ils sont abonnés.
  
    
    

## Interopérabilité de flux de travail SharePoint
<a name="bkm_InteropBridge"> </a>

L'interopérabilité de flux de travail SharePoint permet aux flux de travail SharePoint 2010 (créés sur Windows Workflow Foundation 3) d'être appelés à partir de flux de travail SharePoint 2013, basés sur Windows Workflow Foundation 4. Cela vous permet d'exécuter des flux de travail 2010 dans des flux de travail 2013.
  
    
    
Ceci est important car vous disposez peut-être de SharePoint 2010, que vous pouvez réutiliser conjointement avec vos flux de travail SharePoint 2013. En outre, vous pouvez utiliser des activités ou fonctionnalités à partir de SharePoint 2010 qui ne sont pas encore implémentées dans SharePoint 2013.
  
    
    
Pour obtenir une description complète de l'interopérabilité de flux de travail SharePoint, voir  [Utilisez interopérabilité des flux de travail pour SharePoint 2013](use-workflow-interop-for-sharepoint-2013.md).
  
    
    

## Ressources supplémentaires
<a name="bk_additional"> </a>


-  [Mise en route avec les flux de travail dans SharePoint 2013](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [Référence d'actions et les activités de flux de travail pour SharePoint 2013](workflow-actions-and-activities-reference-for-sharepoint-2013.md)
    
  
-  [Développer des flux de travail SharePoint 2013 à l'aide de Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  
-  [Développement de flux de travail dans SharePoint Designer et Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [Flux de travail dans SharePoint 2013](workflows-in-sharepoint-2013.md)
    
  
-  [Utilisez interopérabilité des flux de travail pour SharePoint 2013](use-workflow-interop-for-sharepoint-2013.md)
    
  

