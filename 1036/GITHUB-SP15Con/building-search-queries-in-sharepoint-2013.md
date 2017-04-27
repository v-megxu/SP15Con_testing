---
title: Création de requêtes de recherche dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c4372fcc-4574-4c81-a345-a1bb282ca8f7
---


# Création de requêtes de recherche dans SharePoint 2013
Découvrez la syntaxe de recherche prise en charge dans SharePoint Server 2013 pour la création de règles de requête et de requêtes de recherche.
## Syntaxe de recherche prise en charge dans SharePoint Server 2013 pour créer des requêtes de recherche
<a name="SP15Buildquery_support"> </a>

La recherche SharePoint Server 2013 prend en charge la syntaxe de recherche KQL (Keyword Query Language) et FQL (FAST Query Language) pour créer des requêtes de recherche.
  
    
    
 **KQL (Keyword Query Language)**
  
    
    
KQL est le langage de requête par défaut pour la création de requêtes de recherche. À l'aide de KQL, spécifiez les termes de recherche ou les restrictions de propriété qui sont transmis au service de recherche SharePoint.
  
    
    
 **FQL (FAST Query Language)**
  
    
    
FQL est un langage de requête structuré qui prend en charge les opérateurs de requête avancée. Vous pouvez utiliser FQL lorsque vous souhaitez créer des requêtes complexes que vous souhaitez transmettre par programmation au service de recherche SharePoint. FQL n'est pas destiné à être exposé aux utilisateurs finals et il est désactivé par défaut. 
  
    
    
Pour activer FQL, utilisez la propriété **EnableFQL**. Ensuite, copiez la source de résultats par défaut et modifiez la chaîne de transformation de requête  `{?{searchTerms} -ContentClass=urn:content-class:SPSPeople}`, à l'un de ces niveaux (application de service de recherche (SSA), collection de sites ou site) et de l'une des manières suivantes :
  
    
    

- Supprimez le filtre KQL,  `-ContentClass:urn:content-class:SPSPeople`, de la transformation de requête. La chaîne de transformation de requête qui en résulte sera :  `{?{searchTerms}}`
    
  
- Remplacez la chaîne de transformation de requête par un équivalent FQL, comme  `{?andnot({searchTerms},filter(contentclass:"urn:content-class:SPSPeople*"))}`.
    
  
Pour plus d'informations sur les origines de résultats et leur fonctionnement, consultez les rubriques  [Présentation des origines des résultats](http://office.microsoft.com/fr-fr/support/sharepoint/sharepointsearch/understanding-result-sources-HA102848849.aspx) et [Configurer des origines de résultats pour la recherche dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj683115%28v=office.15%29.aspx).
  
    
    

## Dans cette section
<a name="SP15Buildquery_support"> </a>


-  [Référence de syntaxe de langage de requête de mot clé (KQL)](keyword-query-language-kql-syntax-reference.md)
    
  
-  [Référence de la syntaxe du langage de requête FQL (FAST Query Language)](fast-query-language-fql-syntax-reference.md)
    
  
-  [Utilisation des API de requête de recherche SharePoint 2013](using-the-sharepoint-2013-search-query-apis.md)
    
  

## Ressources supplémentaires
<a name="SP15Buildquery_addlresources"> </a>


-  [Recherche dans SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [Planifier la transformation de requêtes et le tri des résultats dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj219620%28v=office.15%29.aspx)
    
  
-  [Variables de requête dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj683123.aspx)
    
  

