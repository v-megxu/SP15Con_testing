---
title: Comparaison des compléments pour SharePoint et des solutions SharePoint
ms.prod: SHAREPOINT
ms.assetid: 0e9efadb-aaf2-4c0d-afd5-d6cf25c4e7a8
---


# Comparaison des compléments pour SharePoint et des solutions SharePoint
Découvrez le moment où il est préférable de développer votre extension SharePoint 2013 comme une Complément SharePoint et quand il vaut mieux la développer comme une solution de batterie de serveurs SharePoint ou une solution bac à sable sans code.
 * **S'applique à :*** 
  
    
    

Cet article compare les cas d'utilisation des Compléments SharePoint, solutions de batterie de serveurs et des solutions bac à sable sans code (NCSS).
- Les nouvelles Compléments SharePoint sont des extensions autonomes pouvant inclure des données et une logique informatique, des composants SharePoint et des scripts côté client, mais pas de code géré personnalisé qui fonctionne sur les serveurs SharePoint. Elles sont installées à partir du Office Store ou d'un catalogue de compléments d'organisation et peuvent être installées sur les batteries de serveurs locales ou sur Microsoft SharePoint Online. Pour une vue d'ensemble des Compléments SharePoint, consultez la rubrique  [Compléments](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx).
    
  
- Les SharePointsolutions de batterie de serveurs sont des packages de composants SharePoint téléchargés vers une galerie de l'échelle de la batterie de serveurs à partir de l'emplacement où elles peuvent être installées. Elles ne peuvent pas être distribuées par le biais du Office Store et elles ne peuvent pas être installées sur SharePoint Online. Elles peuvent inclure du code géré personnalisé qui fonctionne sur les serveurs de la batterie SharePoint. Pour plus d'informations sur les principes de base de solutions de batterie de serveurs, consultez les rubriques  [Vue d'ensemble des solutions](http://msdn.microsoft.com/library/1983cab9-4b29-494a-a62a-0f8e83908744%28Office.15%29.aspx) et [Solutions de batterie de serveurs](http://msdn.microsoft.com/library/845f7524-b9ff-412b-aa29-3afacda91100%28Office.15%29.aspx).
    
  
-  Les NCSS sont également des packages de composants SharePoint. Toutefois, elles sont téléchargées vers une galerie de collection de sites à partir de l'emplacement où elles peuvent être installées. Elles peuvent être installées sur des batteries de serveurs locales ou sur SharePoint Online, mais elles ne peuvent pas être distribuées par le biais du Office Store. Elles peuvent inclure quasiment les mêmes types de composants descriptifs que les Compléments SharePoint et, tout comme les compléments, elles peuvent disposer de JavaScript, mais elles ne peuvent pas comporter de contenu géré personnalisé qui fonctionne sur les serveurs SharePoint. Étant donné les différences existantes entre les systèmes de déploiement de compléments et de NCSS, ces dernières représentent une option de développement plus performante pour une courte liste de scénarios. Pour plus d'informations sur solutions bac à sable, consultez la rubrique relative aux [solutions en bac à sable (SharePoint 2010)](https://technet.microsoft.com/fr-fr/library/ee721992%28v=office.14%29.aspx).
    
  

> **IMPORTANTE**
> Lorsque le développement de solutions bac à sable contenant uniquement le balisage déclaratif et JavaScript (également nommées solutions en bac à sable sans code (NCSS)) est toujours viable, nous déconseillons l'utilisation de code géré personnalisé dans le solution bac à sable. Nous avons introduit le nouveau modèle de complément SharePoint pour remplacer les scénarios nécessitant l'utilisation de code géré. Le modèle de complément dissocie le produit principal SharePoint de l'exécution du complément. Cela permet une plus grande flexibilité et vous donne la possibilité d'exécuter le code dans l'environnement de votre choix. Nous sommes conscients que nos clients ont réalisé des investissements en solutions bac à sable codées, c'est pourquoi nous les supprimerons de manière progressive et responsable. Les solutions bac à sable codées existantes continueront à fonctionner dans les batteries de serveurs SharePoint locales dans un avenir prévisible. Étant donné la nature dynamique des services en ligne, nous déterminerons les besoins de prise en charge pour les solutions bac à sable codées dans SharePoint Online en fonction de la demande des clients. Les NCSS sont toujours prises en charge. Tous les investissements futurs rendront le nouveau modèle de complément SharePoint plus riche et plus puissant. En conséquence, nous conseillons que tout nouveau développement utilise le nouveau modèle de complément dès que possible. Pour les scénarios dans lesquels vous devez développer une solution de batterie de serveurs ou une solution bac à sable codée, nous vous recommandons de la concevoir de sorte qu'elle puisse facilement évoluer vers un modèle de développement plus faiblement couplé. 
  
    
    


## Développer un complément dès que possible
<a name="AppWhenYouCan"> </a>

Les conseils les plus importants que nous pouvons vous donner consistent à développer une Complément SharePoint au lieu d'une solution de batterie de serveurs ou NCSS dès que possible. Les Compléments SharePoint présentent les avantages suivants par rapport aux solutions classiques :
  
    
    

- Elles fournissent aux utilisateurs les processus les plus simples en matière de découverte, d'achat et d'installation.
    
  
- Elles offrent aux administrateurs les extensions SharePoint les plus sûres.
    
  
- Elles vous fournissent le système de vente et de marketing le plus simple, basé sur un magasin de compléments en ligne de Microsoft.
    
  
- Elles maximisent votre flexibilité pour le développement de futures mises à niveau.
    
  
- Elles optimisent votre capacité à tirer parti de vos compétences existantes en matière de programmation d'applications autres que SharePoint.
    
  
- Elles intègrent les ressources informatiques de manière plus fluide et plus souple.
    
  
- Elles activent votre extension pour obtenir des autorisations qui sont distinctes des autorisations de l'utilisateur qui exécute le complément.
    
  
- Elles vous permettent d'utiliser des normes interplateformes, notamment HTML, REST, OData, JavaScript et OAuth.
    
  
- Elles vous permettent de tirer parti de la bibliothèque SharePoint inter-domaines JavaScript pour accéder aux données SharePoint. Vous pouvez également utiliser un service de jeton sécurisé fourni par Microsoft compatible avec OAuth ou utiliser des certificats numériques pour obtenir l'autorisation pour les données SharePoint.
    
  

## Concevoir des compléments ou des NCSS pour les utilisateurs finaux et des solutions de batterie de serveurs pour les administrateurs
<a name="SPAppVsClassic_Overview"> </a>

Les Compléments SharePoint et les NCSS utilisent l'un des modèles objet client SharePoint ou l'un des points de terminaison REST pour accéder au contenu et aux composants SharePoint. Ces API clientes activent les extensions SharePoint qui sont conçues pour les utilisateurs finaux. (Les « utilisateurs finaux » dans ce contexte sont les administrateurs de collection de sites, les propriétaires de site web et les membres de site web.) Le modèle objet de serveur a des API supplémentaires qui autorisent des extensions de programmation pour la gestion, la configuration et la sécurité de SharePoint. Cela comprend les extensions de l'Administration centrale, les commandes Windows PowerShell personnalisées, les travaux du minuteur et les sauvegardes personnalisées. Pour plus d'informations sur les types d'extensions d'administration que vous pouvez développer, consultez  [Administration de Windows SharePoint Services](http://msdn.microsoft.com/library/cdcc1b8a-4144-446f-b471-03d4a754a8ab%28Office.15%29.aspx). Ces extensions d'administration sont déployées dans les fonctionnalités SharePoint concernant la batterie de serveurs, l'application web ou la collection de sites. Les solutions de batterie de serveursSharePoint sont également installées par les administrateurs de batterie de serveurs, même si les compléments et les NCSS peuvent être installés par le client et les administrateurs de collections de sites.
  
    
    
Le modèle objet serveur possède également des API pour les opérations de création, lecture, mise à jour et suppression (CRUD) sur les listes, bibliothèques et sites web et pour des opérations sur d'autres composants SharePoint. Cela signifie que le modèle objet serveur peut être utilisé pour les extensions conçues pour les utilisateurs finaux. Toutefois, pour les raisons évoquées dans la section précédente, les solutions de batterie de serveurs ne sont généralement pas la meilleure option pour ces extensions. Par conséquent, il n'est pas surprenant que les solutions de batterie de serveurs ne puissent pas être installées sur Microsoft SharePoint Online. Étant donné que Microsoft prend en charge toute la gestion de SharePoint Online, les extensions d'administration ne sont pas nécessaires. Pour plus d'informations sur les différents ensembles d'API dans SharePoint et sur les endroits où elles se chevauchent, consultez  [Choisir l'ensemble d'API approprié dans SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    
Les modèles objet client et les points de terminaison REST ne dupliquent pas les API orientées administration du modèle objet serveur. En outre, étant donné que ni une Complément SharePoint ni une NCSS ne peuvent contenir du code personnalisé qui fonctionne sur les serveurs SharePoint, elles ne peuvent pas appeler ces API d'administration. De plus, toutes les fonctionnalités des Compléments SharePoint doivent avoir une étendue de site web, et les fonctionnalités des NCSS doivent avoir une étendue de collection de sites ou de site web. Ainsi, une extension SharePoint orientée administration n'est pas vraiment possible avec une Complément SharePoint ou une NCSS. Par conséquent, selon le deuxième principe, qui n'est pas une règle absolue, les compléments et les NCSS sont faits pour les utilisateurs finaux et les solutions de batterie de serveurs sont faites pour les administrateurs.
  
    
    

## Concevoir des NCSS pour des extensions de type modèle et de personnalisation
<a name="SPAppVsClassic_Overview"> </a>

Vous pouvez rencontrer l'un des quelques scénarios de développement SharePoint pour lesquels le modèle de complément n'est pas adapté, mais que vous ne pouvez pas implémenter avec une solution de batterie de serveurs, peut-être parce que la solution doit être installée sur SharePoint Online ou doit être installée par un administrateur de collection de sites. Il existe deux catégories générales, et qui se chevauchent, de tels scénarios.
  
    
    

- **Personnalisation :** les utilisateurs SharePoint veulent souvent donner à leurs sites SharePoint, y compris leurs sites SharePoint Online, une apparence personnalisée, avec leurs propres couleurs, styles, mises en page et logos. Ceci est généralement plus facile avec des NCSS qu'avec des Compléments SharePoint. Une Complément SharePoint dispose d'un contrôle déclaratif sur l'apparence de son propre site web uniquement. Pour le site web hôte, elle peut ajouter de manière déclarative uniquement des boutons de ruban et des éléments de menu (et composants de complément). Toute autre modification apportée à un site web hôte ou à sa collection de sites parent, sa location ou une application web SharePoint locale doit être effectuée avec le code ou le script qui utilise l'un des modèles objet client SharePoint. Par exemple, de nouvelles icônes ou de nouveaux fichiers CSS doivent être déployés par programme. Ce code peut être exécuté à partir du complément après son installation ou il peut être exécuté dans le gestionnaire d'événements d'installation d'un complément. Toutefois, la création de ce code demanderait énormément de travail. En outre, le complément nécessiterait des autorisations étendues aux collections de site pour modifier tous les sites web en dehors de son propre site web de complément et du site web hôte, ainsi que des autorisations étendues à la location pour modifier plus d'éléments que sa seule collection de sites parent. Une personnalisation de NCSS, toutefois, peut être déployée et activée sur toutes les collections de sites et peut être formée de seulement quelques composants purement déclaratifs.
    
    > **REMARQUE**
      > Notez que les SharePointsolutions de batterie de serveurs sont potentiellement plus puissantes que des NCSS ou des Compléments SharePoint pour la personnalisation, mais elles ne constituent pas une option envisageable sur SharePoint Online. 
- **Extensions de type modèle :** supposons que vous devez créer une extension de gestion de crise pour SharePoint, pour une analyse collaborative et une solution de crises d'entreprise. Votre extension comprend plusieurs types de liste personnalisée, des flux de travail sans code et d'autres composants SharePoint, tous combinés en un élément WebTemplate personnalisé. Supposons que vous créez un package et déployez l'extension sous forme de NCSS. Une fois la fonctionnalité de la solution activée, les utilisateurs peuvent créer un sous-site web de gestion de crise de leur site SharePoint à chaque fois qu'une crise se produit. Ils peuvent remplir le site web avec des données propres à la crise. En revanche, vous pouvez implémenter la même extension qu'une Complément SharePoint à l'aide du même ensemble de composants SharePoint. Lorsque le complément est installé sur le site d'équipe, le sous-site web (appelé « site web de complément ») est immédiatement créé. Là encore, les utilisateurs remplissent le site web avec des données pertinentes.
    
    Maintenant, que se passe-t-il en cas de deuxième crise ? Si vous avez implémenté l'extension sous forme de NCSS, vos utilisateurs peuvent simplement créer un autre sous-site web à partir de votre élément WebTemplate personnalisé. Cependant, si vous avez implémenté l'extension sous forme d'Complément SharePoint, un problème se pose pour vos utilisateurs. Ils ne peuvent pas installer une deuxième instance du même complément sur leur site web parent. Une seule instance d'un complément peut être installée sur un site web hôte. Tout ce que vous pouvez faire consiste à créer un sous-site du site web parent pour servir d'emplacement pour une autre instance du complément à installer. Lorsque le complément est installé, un nouveau site web de complément, qui est un sous-site du site web parent, est créé pour les composants de complément. Cette comparaison démontre un principe général, mais pas absolu : les extensions SharePoint qui ont un caractère de type modèle, c'est-à-dire, une collection de composants réutilisable qui doit être configurée pour chaque cas d'utilisation spécifique, mais qui a naturellement plusieurs instances associées au même site web SharePoint, sont plus adaptées au modèle de développement NCSS qu'au modèle de complément. Dans cet exemple, l'élément variable est la crise, mais il est facile d'imaginer des extensions SharePoint de type modèle dans lesquelles les instances varient par région, date ou de nombreuses autres caractéristiques.
    
  
Pour plus d'informations sur l'extension des capacités des Compléments SharePoint, consultez les rubriques  [Utiliser des gestionnaires d'événements de complément de manière conventionnelle](#AppEventHandlers) et [Les compléments qui créent des extensions](#ExtensionFactories).
  
    
    

## Activer des fonctionnalités comme dans un complément
<a name="Questions"> </a>

Comme indiqué précédemment, un code personnalisé qui fonctionne sur les serveurs SharePoint n'est pas autorisé dans les Compléments SharePoint. Il ne s'agit  *pas*  d'une limitation importante. Cela signifie simplement que votre logique métier personnalisée est soit « hors service » sur le périphérique client, soit « en service » dans le cloud. Dans les deux cas, vous pouvez utiliser le [service REST/OData SharePoint](http://msdn.microsoft.com/library/f60ed19e-9840-4f39-911e-4676751a2f6b%28Office.15%29.aspx) pour accéder aux sites, listes et autres données SharePoint. Vous pouvez également accéder à distance aux données SharePoint via les [modèles objet client SharePoint JavaScript, Silverlight ou .NET Framework](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Enfin, sur les Windows Phones, vous pouvez accéder à SharePoint via le modèle objet SharePointWindows Phone. Pour plus d'informations sur les différents ensembles d'API dans SharePoint 2013, consultez la rubrique  [Choisir l'ensemble d'API approprié dans SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    
De même, les fonctionnalités des Compléments SharePoint ne peuvent pas disposer d'une étendue de collection de sites, d'application web ou de batterie de serveurs. Toutefois, il est inutile d'abandonner des fonctionnalités ou des éléments de l'interface utilisateur. Cela signifie que l'implémentation du composant ne s'effectue plus sur SharePoint mais sur une application web cliente ou distante, ou sur une base de données distante.
  
    
    
Le tableau suivant répertorie les composants SharePoint qui ne peuvent pas être déployés dans une Complément SharePoint et décrit comment obtenir ces mêmes fonctionnalités à la manière d'un complément.
  
    
    


|**Pour obtenir la fonctionnalité...**|**... essayez les approches suivantes.**|
|:-----|:-----|
|Composants WebPart personnalisés  <br/> |Une Complément SharePoint peut avoir des pages distantes qui contiennent des composants WebPart personnalisés. Une autre option consiste à exposer une page à partir d'une application web distante dans un composant de complément sur une page de site SharePoint. La page distante peut avoir les mêmes contrôles d'interface utilisateur et la même fonctionnalité qu'un composant WebPart. Pour plus d'informations, consultez  [Créer des composants de complément à installer avec votre complément pour SharePoint](http://msdn.microsoft.com/library/a2664289-6c56-4cb1-987a-22367fad55eb%28Office.15%29.aspx).  <br/> |
|Récepteurs d'événements et récepteurs de fonctionnalités  <br/> |Une Complément SharePoint peut contenir des récepteurs d'événements distants de fonctionnalité équivalente. Pour plus d'informations, consultez  [Gestion des événements dans les compléments pour SharePoint](http://msdn.microsoft.com/library/c050d056-8548-4496-a053-016779d723d9%28Office.15%29.aspx).  <br/> |
|Types de champs personnalisés (colonne)  <br/> |Un complément peut déployer un nouveau champ (colonne) basé sur l'un des  [types de champs existants](http://msdn.microsoft.com/fr-fr/library/microsoft.sharepoint.spfieldtype.aspx%28Office.15%29.aspx). Les types de champs  [Calculé](http://msdn.microsoft.com/library/8703373d-bb55-4132-8c5f-37a41c383f81%28Office.15%29.aspx) et [Calculé](http://msdn.microsoft.com/fr-fr/library/microsoft.sharepoint.spfieldcomputed.aspx%28Office.15%29.aspx) sont particulièrement flexibles. Une autre option consiste à présenter vos données dans une page web distante à l'aide de grilles ou de contrôles personnalisés. <br/> |
|Services web personnalisés créés dans le  [Infrastructure des applications de service](http://msdn.microsoft.com/library/6d0300d2-5b5c-4477-a9e2-17594aea5a7d%28Office.15%29.aspx) SharePoint <br/> |Vous pouvez développer vos services web personnalisés en tant que services distants.  <br/> |
|Pages d'application  <br/> |Une Complément SharePoint peut inclure des pages web distantes qui sont disponibles à partir de chaque site web sur lequel le complément est installé. Un complément peut également utiliser des composants WebPart SharePoint intégrés sur les pages du site.  <br/> |
   
Certains composants SharePoint, répertoriés ci-dessous, sont utilisés dans des scénarios d'utilisateur final, mais n'ont aucune équivalence dans le modèle de complément SharePoint et ne peuvent pas être déployés dans des NCSS. Dans ce cas, vous devez utiliser des solutions de batterie de serveurs.
  
    
    

- **Définitions de site personnalisées** Toutefois, les éléments WebTemplate personnalisés, qui sont fonctionnellement semblables à des définitions de site, sont disponibles à la fois dans les NCSS et les Compléments SharePoint. Pour plus d'informations, consultez [Utilisation des modèles et des définitions](http://msdn.microsoft.com/library/1edf6d4d-eddb-4cb5-9034-ed394e8a3e01%28Office.15%29.aspx).
    
  
- **Contrôles de délégation** Pour plus d'informations, consultez [Contrôle de délégation (modélisation des contrôles)](http://msdn.microsoft.com/library/e979328d-4985-4ed6-9085-7ff32a998dfc%28Office.15%29.aspx).
    
  
- **Thèmes personnalisés**
    
  
- **Groupes d'actions personnalisées et masquage d'actions personnalisées**
    
  
- **Contrôles utilisateur (fichiers .ascx)** Aucun scénario ne requiert réellement ces contrôles.
    
  

### Utiliser des gestionnaires d'événements de complément de manière conventionnelle
<a name="AppEventHandlers"> </a>

Vous pouvez contourner certaines des limitations des Compléments SharePoint en créant des gestionnaires pour les événements d'installation, de mise à jour et de désinstallation du complément. Ces gestionnaires sont des services web hébergés sur des serveurs web en dehors de la batterie de serveurs SharePoint, éventuellement dans le cloud. Ils peuvent utiliser le modèle objet client SharePoint ou les API REST pour effectuer des opérations CRUD sur les composants SharePoint, y compris les composants du site web hôte. En théorie, vous pouvez utiliser ces gestionnaires pour contourner certaines restrictions de déploiement dans les éléments de **personnalisation** et d' **extensions de type modèle** évoqués précédemment. Toutefois, nous vous recommandons d'utiliser ces gestionnaires uniquement en dernier ressort, lorsqu'il est impossible de fournir aux clients la fonctionnalité nécessaire. Lorsque vous décidez de créer un gestionnaire, prenez en compte les informations suivantes :
  
    
    

- Le déploiement de programmation pour le site web hôte exige que le complément demande l'autorisation Contrôle total au site web hôte. Les compléments qui requièrent ce niveau d'autorisation ne peuvent pas être vendus via le Office Store.
    
  
- Le déploiement de composants vers le site web hôte tend à compromettre les avantages de sécurité consistant à placer les composants SharePoint dans un complément web avec son propre domaine.
    
  
- La création et le débogage du code de déploiement complet représentent un travail énorme par rapport au balisage de déploiement descriptif qui peut être utilisé pour les composants web de complément et dans les NCSS.
    
  
- Certaines meilleures pratiques indispensables doivent être suivies pour la création de gestionnaires d'événements de complément. Votre code doit inclure une logique de restauration pour annuler tout ce qu'il a créé en cas d'erreur. Il doit également alerter l'infrastructure SharePoint de l'erreur, afin que l'infrastructure puisse annuler tout ce qui a été effectué.
    
  
- Les gestionnaires d'événements de complément ne peuvent pas exister avec le type d'Complément SharePoint appelé « hébergée sur SharePoint ».
    
  
Pour plus d'informations sur les gestionnaires d'événements de complément, consultez le nœud SDK  [Gestion des événements dans les compléments pour SharePoint](http://msdn.microsoft.com/library/c050d056-8548-4496-a053-016779d723d9%28Office.15%29.aspx). Pour plus d'informations sur la logique de restauration, consultez la section **Ajouter la logique de restauration au gestionnaire** de la rubrique [Créer un gestionnaire pour l'événement de mise à jour dans des compléments pour SharePoint](http://msdn.microsoft.com/library/0fa088c5-54c6-482c-84ed-51c4f77c4127%28Office.15%29.aspx). Cette dernière concerne un événement de mise à jour de complément, mais les principes de base s'appliquent à tous les gestionnaires d'événements de complément.
  
    
    

### Les compléments qui créent des extensions
<a name="ExtensionFactories"> </a>

Une autre façon d'utiliser le modèle objet client SharePoint, ou ses API REST, pour résoudre les problèmes de déploiement des composants avec les Compléments SharePoint, consiste à disposer d'un code CRUD dans le complément lui-même, plutôt que dans un gestionnaire d'événements de complément. Le complément devient alors un type de fabrique pour un type d'extension personnalisée. Par exemple, un complément hébergé par SharePoint peut utiliser le modèle objet JavaScriptSharePoint pour effectuer le déploiement et d'autres opérations CRUD sur le site web hôte ou ailleurs dans la location ou l'application web. Pour obtenir un autre exemple, consultez la rubrique **Brève introduction à la mise en service à distance** de l'article [Techniques de mise en service de site et mise en service à distance dans SharePoint 2013](http://blogs.msdn.com/b/vesku/archive/2013/08/23/site-provisioning-techniques-and-remote-provisioning-in-sharepoint-2013.aspx), qui décrit comment une Complément SharePoint hébergée par un fournisseur est utilisée pour la mise en service d'un sous-site de manière parfaitement identique à la mise en service d'un sous-site web de SharePoint. Il existe, cependant, un grand nombre de méthodes réinventées, et donc la création d'une fabrique d'Complément SharePoint représente un travail énorme. En outre, ce type complément ne peut pas être vendu via le Office Store, car le complément nécessite le contrôle total du site web hôte.
  
    
    

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Modèles de programmation dans SharePoint 2013](programming-models-in-sharepoint-2013.md)
    
  
-  [Utilisation de solutions](http://msdn.microsoft.com/library/0da0518c-24eb-48e0-89bd-21282fdeef94%28Office.15%29.aspx)
    
  

