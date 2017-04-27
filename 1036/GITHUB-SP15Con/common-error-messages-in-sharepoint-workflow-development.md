---
title: Messages d'erreur courants dans le développement de flux de travail SharePoint
ms.prod: SHAREPOINT
ms.assetid: e9bf6878-c722-4b1f-b5b5-b302ae0ea4da
---


# Messages d'erreur courants dans le développement de flux de travail SharePoint
Liste des messages d'erreur courants que vous pouvez rencontrer lors du développement de flux de travail SharePoint et conseils pour résoudre le problème sous-jacent.
## Erreurs courantes de flux de travail SharePoint

Bien que cette liste ne regroupe pas toutes les erreurs possibles que vous pouvez rencontrer lors du développement de flux de travail SharePoint, elle répertorie ceux que vous êtes le plus susceptible de rencontrer.
  
    
    

-  [Expiration du délai d'attente de la demande d'exécution du code en mode bac à sable dans le processus de travail](#bkmk_error01)
    
  
-  [Délai expiré en attendant que la demande se termine dans l'appdomain en mode bac à sable](#bkmk_error02)
    
  
-  [Le processus de travail gérant cette demande a été arrêté, car il dépassait la contrainte de ressource {0}](#bkmk_error03)
    
  
-  [Ce flux de travail n'a pas pu être exécuté car une solution en mode bac à sable a rencontré une erreur](#bkmk_error04)
    
  
-  [Ce flux de travail n'a pas pu être exécuté car le mode bac à sable a échoué : Impossible d'obtenir un processus du pool de processus](#bkmk_error05)
    
  
-  [Ce flux de travail n'a pas pu être exécuté car le mode bac à sable a échoué : Le processus de travail du code en mode bac à sable a été interrompu inopinément](#bkmk_error06)
    
  
-  [Le message électronique n'a pas pu être envoyé. Assurez-vous que les paramètres de courrier électronique sortant pour le serveur sont correctement configurés](#bkmk_error07)
    
  
-  [Le flux de travail n'a pas pu mettre à jour l'élément, car il est possible que des colonnes pour cet élément nécessitent un autre type d'informations.](#bkmk_error08)
    
  
-  [Échec de l'opération de flux de travail, car la recherche du flux de travail n'a trouvé aucun élément correspondant](#bkmk_error09)
    
  
-  [Le flux de travail n'a pas pu créer l'élément de liste, car le nom du fichier manque ou n'est pas valide](#bkmk_error10)
    
  
-  [Échec du forçage de type : Impossible de transformer les données de recherche d'entrée en type demandé](#bkmk_error11)
    
  
-  [Échec de l'opération de flux de travail, car l'action nécessite que le document soit extrait](#bkmk_error12)
    
  
-  [Erreurs lors de la compilation du flux de travail. Les fichiers de flux de travail ont été enregistrés mais ne peuvent pas être exécutés. Erreur inattendue sur le serveur associant le flux de travail](#bkmk_error13)
    
  

### Expiration du délai d'attente de la demande d'exécution du code en mode bac à sable dans le processus de travail
<a name="bkmk_error01"> </a>

Même problème et la même solution que pour l'élément ci-dessous, « Délai expiré en attendant que la demande se termine dans l'appdomain en mode bac à sable »
  
    
    

### Délai expiré en attendant que la demande se termine dans l'appdomain en mode bac à sable
<a name="bkmk_error02"> </a>

Ces deux erreurs résultent du même problème : le dépassement du délai d'expiration par défaut pour l'action de flux de travail à exécuter. Le délai d'expiration par défaut est de 30 secondes.
  
    
    
Vous pouvez modifier la valeur du délai d'expiration dans les installations sur site, mais vous ne pouvez pas la modifier dans les installations SharePoint Online. Pour éviter cette erreur dans les installations SharePoint Online, vous devez modifier votre code pour limiter les actions dans le processus de travail ou appdomain à moins de 30 secondes.
  
    
    
Pour modifier le délai d'expiration dans votre installation sur site, exécutez la commande Windows PowerShell suivante. L'exemple de code redéfinit le délai d'expiration sur 60 secondes, mais vous pouvez utiliser une autre valeur.
  
    
    



```

Add-pssnapin microsoft.sharepoint.powershell
   $userCodeSvc = [Microsoft.SharePoint.Administration.SPUserCodeService]::Local
   #change to 60 second timeout
   $userCodeSvc.WorkerProcessExecutionTimeout = 60 
   $userCodeSvc.Update()
```


### Le processus de travail gérant cette demande a été arrêté, car il dépassait la contrainte de ressource {0}
<a name="bkmk_error03"> </a>

Dans la chaîne d'erreur, la valeur de  `{0}` est un espace réservé pour la ressource spécifique dont le seuil a été dépassé. Pour résoudre ce problème, vous devez modifier votre code afin que le seuil de la ressource ne soit pas dépassé. Les valeurs de ces ressources sont répertoriées dans [Limites de l'utilisation des ressources sur les solutions en bac à sable (sandbox) dans SharePoint 2010](http://msdn.microsoft.com/fr-fr/library/gg615462%28v=office.14%29.aspx).
  
    
    

### Ce flux de travail n'a pas pu être exécuté car une solution en mode bac à sable a rencontré une erreur
<a name="bkmk_error04"> </a>

Le code de flux de travail a généré une exception non gérée. La résolution de cette erreur nécessite le débogage et la révision de votre code en mode bac à sable.
  
    
    

### Ce flux de travail n'a pas pu être exécuté car le mode bac à sable a échoué : Impossible d'obtenir un processus du pool de processus
<a name="bkmk_error05"> </a>

Votre configuration en mode bac à sable présente une erreur. Pour plus d'informations sur la configuration d'une solution en mode bac à sable, voir  [Solutions en mode bac à sable dans SharePoint](http://msdn.microsoft.com/fr-fr/library/ee536577%28v=office.14%29.aspx).
  
    
    

### Ce flux de travail n'a pas pu être exécuté car le mode bac à sable a échoué : Le processus de travail du code en mode bac à sable a été interrompu inopinément
<a name="bkmk_error06"> </a>

Votre configuration en mode bac à sable présente une erreur. Pour plus d'informations sur la configuration d'une solution en mode bac à sable, voir  [Solutions en mode bac à sable dans SharePoint](http://msdn.microsoft.com/fr-fr/library/ee536577%28v=office.14%29.aspx).
  
    
    

### Le message électronique n'a pas pu être envoyé. Assurez-vous que les paramètres de courrier électronique sortant pour le serveur sont correctement configurés
<a name="bkmk_error07"> </a>

Deux problèmes sont à prendre en compte lors de la résolution des problèmes de messagerie électronique. Dans les installations SharePoint Online et sur site, assurez-vous que toutes les adresses figurant sur les lignes **À :** et **Cc :** sont des adresses de messagerie valides. Dans les installations sur site, assurez-vous que les paramètres de messagerie sur le serveur sont correctement configurés.
  
    
    
Passez en revue les éléments suivants pour vous assurer que vous avez correctement configuré les messages électroniques entrants et sortants.
  
    
    

-  [Guide de déploiement de Microsoft SharePoint 2013](http://download.microsoft.com/download/1/F/6/1F6D3BE4-1174-4320-A1D1-C0E2681CCCF3/Deployment-guide-for-SharePoint-2013.pdf)
    
  
-  [Comment configurer les messages électroniques entrants et sortants dans SharePoint Server](http://blogs.msdn.com/b/pareshg/archive/2010/04/23/how-to-configure-incoming-and-outgoing-emails-in-sharepoint-server-2010.aspx)
    
  

### Le flux de travail n'a pas pu mettre à jour l'élément, car il est possible que des colonnes pour cet élément nécessitent un autre type d'informations.
<a name="bkmk_error08"> </a>

Cette erreur résulte généralement de l'une des deux situations suivantes :
  
    
    

- Un des champs de la liste a été supprimé ou modifié, mais le flux de travail n'a pas été mis à jour pour tenir compte de la modification, donc il essaie de définir une valeur pour l'ancien champ. Vous devez vérifier toutes les actions **Mettre à jour les éléments de liste** dans votre flux de travail et assurez-vous qu'elles définissent les valeurs appropriées pour les champs et que ces champs existent dans la liste.
    
  
- Il existe une erreur de type de données ; le flux de travail essaie de définir une valeur dans un champ dans l'élément de liste à l'aide d'un type de données incorrect. Vous devez vérifier que le type de données de l'opération **Retourner le champ en tant que** dans sa recherche est correct.
    
  

### Échec de l'opération de flux de travail, car la recherche du flux de travail n'a trouvé aucun élément correspondant
<a name="bkmk_error09"> </a>

Ceci indique une erreur dans la logique de flux de travail. Vérifiez que vous sélectionnez la liste et le champ appropriés dans votre recherche.
  
    
    

### Le flux de travail n'a pas pu créer l'élément de liste, car le nom du fichier manque ou n'est pas valide
<a name="bkmk_error10"> </a>

Ceci indique une erreur dans la logique de flux de travail. Vérifiez que le nom de fichier saisi dans le champ **Chemin d'accès et nom** est valide. La plupart du temps, les noms de fichier ne sont pas valides car l'extension du fichier n'existe pas ou est incorrecte ou car une chaîne de chemin d'accès/fichier est trop longue et dépasse le nombre maximal de caractères autorisé.
  
    
    

### Échec du forçage de type : Impossible de transformer les données de recherche d'entrée en type demandé
<a name="bkmk_error11"> </a>

L'opération n'a pas pu forcer le type des valeurs en raison d'une incompatibilité de type de données (par exemple, conversion d'une chaîne aléatoire en une valeur date/heure). Vous devez vérifier les paramètres **Renvoyer le champ en tant que** dans votre recherche pour vous assurer qu'il s'agit d'un type de données valide pour les données attendues.
  
    
    

### Échec de l'opération de flux de travail, car l'action nécessite que le document soit extrait
<a name="bkmk_error12"> </a>

Vous devez extraire l'élément à l'aide de l'action **Extraire l'élément** à l'aide de l'action **Mettre à jour l'élément**.
  
    
    

### Erreurs lors de la compilation du flux de travail. Les fichiers de flux de travail ont été enregistrés mais ne peuvent pas être exécutés. Erreur inattendue sur le serveur associant le flux de travail
<a name="bkmk_error13"> </a>

Voir l' [article 2557533 de la base de connaissances du support Microsoft](http://support.microsoft.com/kb/2557533) ( `http://support.microsoft.com/kb/2557533`) pour plus d'informations.
  
    
    

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [SharePoint flux de travail meilleures pratiques de développement](sharepoint-workflow-development-best-practices.md)
    
  
-  [Développer des flux de travail SharePoint 2013 à l'aide de Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

