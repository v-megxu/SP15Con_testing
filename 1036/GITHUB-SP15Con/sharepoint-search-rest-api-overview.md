---
title: Vue d'ensemble de l'API REST de recherche SharePoint
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# Vue d'ensemble de l'API REST de recherche SharePoint
Ajoutez une fonctionnalité de recherche aux applications clientes et mobiles à l'aide du service REST de recherche dans SharePoint Server 2013 et toute technologie prenant en charge les requêtes web REST.
## Interrogation à l'aide du service REST de recherche
<a name="bk_queryrest"> </a>

Recherche dans SharePoint 2013 comprend un service REST de recherche que vous pouvez utiliser pour ajouter des fonctionnalités de recherche à vos applications mobiles et client en utilisant une technologie prenant en charge les requêtes web REST. Vous pouvez utiliser le service REST de recherche pour soumettre des requêtes KQL ou FQL dans vos Compléments SharePoint, applications client distantes, applications mobiles et autres applications.
  
    
    
Le service REST de recherche prend en charge les requêtes HTTP **POST** et HTTP **GET**.
  
    
    

### Requêtes GET

Créez l'URI pour formuler des requêtes **GET** auprès du service REST de recherche en procédant comme suit :
  
    
    
 `/_api/search/query`
  
    
    
Pour les requêtes **GET**, vous indiquez les paramètres de requête dans l'URL. Vous pouvez créer l'URL de requête **GET** de deux manières :
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### Requêtes POST

Créez l'URI pour formuler des requêtes **POST** auprès du service REST de recherche en procédant comme suit :
  
    
    
 `/_api/search/postquery`
  
    
    
Pour les requêtes **POST**, vous transmettez les paramètres de requête de la demande au format JavaScript Object Notation (JSON).
  
    
    
La version **POST** HTTP du service REST de recherche prend en charge tous les paramètres pris en charge par la version **GET** HTTP. Toutefois, certains paramètres possèdent différents types de données, comme indiqué dans le tableau 1.
  
    
    

**Tableau 1. Paramètres de requête avec différents types de données pour les requêtes POST**


|**Paramètre**|**Type de données**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HithighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Properties](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
Utilisez des requêtes **POST** dans les scénarios suivants :
  
    
    

- Lorsque vous dépassez la restriction de longueur d'URL avec une requête **GET**.
    
  
- Lorsque vous ne pouvez pas indiquer les paramètres de requête dans une URL simple. Par exemple, si vous devez transmettre des valeurs de paramètre contenant un tableau de type complexe ou des chaînes séparées par une virgule, vous avez plus de flexibilité lors de l'élaboration de la requête **POST**.
    
  
- Lorsque vous utilisez le paramètre  [ReorderingRules](#bk_ReorderingRules), qui est pris en charge uniquement avec les requêtes **POST**.
    
  

## Utilisation des paramètres de requête avec le service REST de recherche
<a name="bk_UsingQueryParams"> </a>

Lorsque vous appelez le service REST de recherche, vous indiquez les paramètres de la requête avec la requête. Recherche dans SharePoint 2013 utilise ces paramètres de requête pour créer la requête de recherche. Avec une requête **GET**, vous indiquez les paramètres de requête dans l'URL. Pour les requêtes **POST**, vous transmettez les paramètres de requête au corps au format JavaScript Object Notation (JSON).
  
    
    
Les sections suivantes décrivent les paramètres de requête que vous pouvez utiliser pour soumettre des requêtes de recherche avec le service REST de recherche.
  
    
    

### Paramètre QueryText

Chaîne contenant le texte pour la requête de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

Chaîne contenant le texte qui remplace le texte de requête, dans le cadre d'une transformation de requête.
  
    
    
 **Exemple de requête GET**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:johndoe'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

Valeur booléenne indiquant si les tables de résultats retournées pour le bloc de résultats sont mélangées avec les tables de résultats renvoyées par la requête d'origine.
  
    
    
Valeur **true** pour mélanger les tables de résultats, **false** dans le cas contraire. La valeur par défaut est **true**.
  
    
    
Modifiez cette valeur uniquement si vous souhaitez fournir votre propre implémentation d'entrelacement.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

ID d'origine des résultats à utiliser pour l'exécution de la requête de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

ID du modèle de classement à utiliser pour la requête.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

Première ligne incluse dans les résultats de la recherche renvoyés. Vous utilisez ce paramètre lorsque vous souhaitez implémenter la pagination des résultats de la recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

Nombre maximal global de lignes renvoyées dans les résultats de la recherche. Par rapport à  _RowsPerPage_,  _RowLimit_ est le nombre maximal global de lignes renvoyées.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

Nombre maximal de lignes à renvoyer par page. Par rapport à  _RowLimit_,  _RowsPerPage_ fait référence au nombre maximal de lignes à renvoyer par page, et est utilisé principalement lorsque vous souhaitez implémenter la pagination des résultats de la recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

Propriétés gérées à renvoyer dans les résultats de la recherche. Pour renvoyer une propriété gérée, définissez l'indicateur affichable dans les résultats de la recherche de la propriété sur **true** dans le schéma de recherche.
  
    
    
Pour les requêtes **GET**, vous indiquez le paramètre  _SelectProperties_ dans une chaîne contenant une liste de propriétés séparées par une virgule. Pour les requêtes **POST**, vous indiquez le paramètre  _SelectProperties_ en tant que tableau de chaînes.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SelectProperties' : {
    'results' : [
          'Title,
          Author'
          ]
}
}
```


### Culture
<a name="bk_Culture"> </a>

ID de paramètres régionaux de la requête (voir  [ID de paramètres régionaux assignés par Microsoft](http://msdn.microsoft.com/fr-fr/goglobal/bb964664.aspx)).
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

Ensemble de filtres de perfectionnement utilisés lors de l'émission d'une requête de perfectionnement. Pour les requêtes **GET**, le paramètre  _RefinementFilters_ est indiqué comme un filtre FQL. Pour les requêtes **POST**, le paramètre  _RefinementFilters_ est indiqué comme un tableau de filtres FQL.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RefinementFilters' : {
'results' : ['fileExtension:equals("docx")']
}
}
```


### Refiners
<a name="bk_Refiners"> </a>

Ensemble des affinements à renvoyer dans un résultat de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Refiners': {
'results' : ['author,size']
}
}
```


### HiddenConstraints
<a name="bk_HiddenConstraints"> </a>

Termes de requête supplémentaires à ajouter à la requête.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

Liste des propriétés selon lesquelles les résultats de la recherche sont triés.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SortList' : 
{
    'results' : [
        {
                'Property':'Created',
                'Direction': '0'
        },
        {
                'Property':'FileExtension',
                'Direction': '1'
        }
    ]
}
}
```


### EnableStemming
<a name="bk_EnableStemming"> </a>

Valeur booléenne indiquant si la recherche de radical est activée.
  
    
    
Valeur **true** si la recherche de radical est activée, **false** dans le cas contraire. La valeur par défaut est **true**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

Valeur booléenne indiquant si les éléments en double sont supprimés des résultats.
  
    
    
Valeur **true** pour supprimer les éléments en double, **false** dans le cas contraire. La valeur par défaut est **true**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

Temps en millisecondes avant l'expiration de la requête. La valeur par défaut est 30 000.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

Valeur booléenne indiquant si les termes exacts dans la requête de recherche sont utilisés pour rechercher des correspondances, ou si les surnoms sont également utilisés.
  
    
    
Valeur **true** si des surnoms sont utilisés, **false** dans le cas contraire. La valeur par défaut est **false**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

Valeur booléenne indiquant si les formes phonétiques des termes de requête sont utilisées pour rechercher des correspondances.
  
    
    
Valeur **true** si les formes phonétiques sont utilisées, **false** dans le cas contraire. La valeur par défaut est **false**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

Valeur booléenne indiquant si la requête utilise le langage de requête FAST (FQL).
  
    
    
Valeur **true** si la requête est une requête FQL, **false** dans le cas contraire. La valeur par défaut est **false**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HithighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

Propriétés à mettre en surbrillance dans le résumé des résultats de la recherche lorsque la valeur de propriété correspond aux termes de recherche saisis par l'utilisateur. Pour les requêtes **GET**, indiquez-les dans une chaîne contenant une liste de propriétés séparées par une virgule. Pour les requêtes **POST**, indiquez-les comme un tableau de chaînes.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlightedProperties' :  {
    'results' : [
         'Title'   
    ]
}
}
```


### BypassResultTypes
<a name="bk_BypassResultTypes"> </a>

Valeur booléenne indiquant s'il faut effectuer un traitement du type de résultat pour la requête.
  
    
    
Valeur **true** pour effectuer le traitement du type de résultat, **false** dans le cas contraire. La valeur par défaut est **false**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

Valeur booléenne indiquant s'il faut renvoyer de meilleurs résultats pour la requête.
  
    
    
Valeur **true** pour renvoyer les meilleurs résultats, **false** dans le cas contraire. Ce paramètre est utilisé uniquement lorsque la propriété **EnableQueryRules** est définie sur **true**, sinon il est ignoré. La valeur par défaut est **false**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessBestBets' : 'true',
'EnableQueryRules' : 'true'
}
```


### ClientType
<a name="bk_ClientType"> </a>

Type du client ayant émis la requête.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

GUID de l'utilisateur ayant envoyé la requête de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

URL de la page des résultats de la recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

Indicateurs personnalisées identifiant la requête. Vous pouvez indiquer plusieurs indicateurs de requête, séparés par un point-virgule.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Properties
<a name="bk_Properties"> </a>

Propriétés supplémentaires pour la requête. Les requêtes **GET** prennent en charge uniquement les valeurs de chaîne. Les requêtes **POST** prennent en charge les valeurs de tout type.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Properties' : {
     'results' : [
          {
               'Name' : 'sampleBooleanProperty',
               'Value' :
               {
                    'BoolVal' : 'True',
                    'QueryPropertyValueTypeIndex' : 3
               }
          },
          {
               'Name' : 'sampleIntProperty',
               'Value' : 
               {
                    'IntVal' : '1234',
                    'QueryPropertyValueTypeIndex' : 2
               }
          }
     ]
}
}
```


> **REMARQUE**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) indique le type de la propriété. Chaque type a une valeur d'index spécifique.
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

Valeur booléenne indiquant s'il faut activer les règles de requête pour la requête.
  
    
    
Valeur **true** pour activer les règles de requête, **false** dans le cas contraire. La valeur par défaut est **true**.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

Règles spéciales pour réorganiser les résultats de la recherche. Ces règles peuvent indiquer que les documents correspondant à certaines conditions sont classés plus haut ou plus bas dans les résultats. Cette propriété s'applique uniquement lorsque les résultats sont triés en fonction d'un classement. Vous devez utiliser une requête **POST** pour cette propriété, car elle ne fonctionne pas dans les requêtes **GET**.
  
    
    
Dans l'exemple suivant,  _MatchType_ fait référence à [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) . Dans l'exemple suivant, `'MatchType' : '0'` indique [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) .
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ReorderingRules' :  {
    'results' : [
         {
             'MatchValue' : '<someValue>',
             'Boost' : '10',
             'MatchType' : '0'
         }
    ]
}
}
```


### ProcessPersonalFavorites
<a name="bk_ProcessPersonalFavorites"> </a>

Valeur booléenne indiquant s'il faut renvoyer les favoris personnels avec les résultats de la recherche.
  
    
    
Valeur **true** pour renvoyer les favoris personnels, **false** dans le cas contraire.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

Emplacement du fichier queryparametertemplate.xml. Ce fichier est utilisé pour permettre aux utilisateurs anonymes d'effectuer des requêtes REST de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

Nombre de propriétés pour afficher la mise en surbrillance pour les résultats de la recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

Valeur booléenne indiquant si les propriétés mises en surbrillance peuvent être classées.
  
    
    
Valeur **true** pour activer les règles de classement, **false** dans le cas contraire.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

Propriétés gérées utilisées pour déterminer la façon de réduire les résultats de recherche individuels. Ils sont réduits en un seul résultat ou en un nombre spécifié de résultats s'ils correspondent aux spécifications de réduction individuelles. Dans une seule spécification de réduction, les résultats sont réduits si leurs propriétés correspondent à toutes les propriétés individuelles dans la spécification de réduction.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

Valeur booléenne indiquant s'il faut trier les résultats de la recherche.
  
    
    
Valeur **true** pour trier les résultats de la recherche à l'aide de _SortList_, ou par classement si  _SortList_ est vide. Valeur **false** pour ne pas trier les résultats.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

Valeur booléenne indiquant s'il faut renvoyer les informations de journal de classement de bloc dans la propriété **BlockRankLog** de la table de résultats entrelacés. Un journal de classement de bloc contient des informations textuelles sur le score de bloc et les documents qui ont été dédupliqués.
  
    
    
Valeur **true** pour renvoyer des informations de journal de classement de bloc, **false** dans le cas contraire.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

Identificateur de paramètres régionaux (LCID) de l'interface utilisateur (voir  [ID de paramètres régionaux assignés par Microsoft](http://msdn.microsoft.com/fr-fr/goglobal/bb964664)).
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

Nombre de caractères préféré à afficher dans le résumé mis en surbrillance généré pour un résultat de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

Nombre maximal de caractères à afficher dans le résumé mis en surbrillance généré pour un résultat de recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

Nombre de caractères à afficher dans le résumé des résultats d'une recherche.
  
    
    
 **Exemple de requête GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **Exemple de requête POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## Activation des requêtes REST de recherche anonymes
<a name="bk_AnonymousREST"> </a>

Vous pouvez configurer la recherche pour prendre en charge les requêtes REST de recherche provenant d'utilisateurs anonymes. Les administrateurs de site peuvent déterminer les paramètres de requête à exposer aux utilisateurs anonymes à l'aide du fichier queryparametertemplate.xml. Cette section décrit la façon de configurer votre site afin d'autoriser l'accès anonyme et de créer le fichier queryparametertemplate.xml.
  
    
    

### Procédure pour activer les requêtes REST de recherche anonymes


1. Activez l'accès anonyme sur l'application web et le site de publication. Pour plus d'informations sur la façon de procéder, voir  [Gérer des stratégies d'autorisation pour une application web dans SharePoint 2013](http://technet.microsoft.com/fr-fr/library/ff608071.aspx) et [Planifier les méthodes d'authentification des utilisateurs dans SharePoint 2013](http://technet.microsoft.com/fr-fr/library/cc262350.aspx) sur [TechNet](http://technet.microsoft.com/fr-fr/).
    
  
2. Ajoutez une bibliothèque de documents appelée QueryPropertiesTemplate au site de publication.
    
  
3. Créez un fichier XML portant le nom queryparametertemplate.xml, puis copiez le code XML suivant dans celui-ci.
    
  ```XML
  
<QueryPropertiesTemplate xmlns="http://www.microsoft.com/sharepoint/search/KnownTypes/2008/08" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <QueryProperties i:type="KeywordQueryProperties">
        <EnableStemming>true</EnableStemming>
        <FarmId>FarmID</FarmId>
        <IgnoreAllNoiseQuery>true</IgnoreAllNoiseQuery>
        <KeywordInclusion>AllKeywords</KeywordInclusion>
        <SiteId>SiteID</SiteId>
        <SummaryLength>180</SummaryLength>
        <TrimDuplicates>true</TrimDuplicates>
        <WcfTimeout>120000</WcfTimeout>
        <WebId>WebID</WebId>
        <Properties xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a:KeyValueOfstringanyType>
                <a:Key>_IsEntSearchLicensed</a:Key>
                <a:Value i:type="b:boolean" xmlns:b="http://www.w3.org/2001/XMLSchema">true</a:Value>
            </a:KeyValueOfstringanyType>
            <a:KeyValueOfstringanyType>
                <a:Key>EnableSorting</a:Key>
                <a:Value i:type="b:boolean" xmlns:b="http://www.w3.org/2001/XMLSchema">true</a:Value>
            </a:KeyValueOfstringanyType>
            <a:KeyValueOfstringanyType>
                <a:Key>MaxKeywordQueryTextLength</a:Key>
                <a:Value i:type="b:int" xmlns:b="http://www.w3.org/2001/XMLSchema">4096</a:Value>
            </a:KeyValueOfstringanyType>
            <a:KeyValueOfstringanyType>
                <a:Key>TryCache</a:Key>
                <a:Value i:type="b:boolean" xmlns:b="http://www.w3.org/2001/XMLSchema">true</a:Value>
            </a:KeyValueOfstringanyType>
        </Properties>
        <PropertiesContractVersion>15.0.0.0</PropertiesContractVersion>
        <EnableFQL>false</EnableFQL>
        <EnableSpellcheck>Suggest</EnableSpellcheck>
        <EnableUrlSmashing>true</EnableUrlSmashing>
        <IsCachable>false</IsCachable>
        <MaxShallowRefinementHits>100</MaxShallowRefinementHits>
        <MaxSummaryLength>185</MaxSummaryLength>
        <MaxUrlLength>2048</MaxUrlLength>
        <SimilarType>None</SimilarType>
        <SortSimilar>true</SortSimilar>
        <TrimDuplicatesIncludeId>0</TrimDuplicatesIncludeId>
        <TrimDuplicatesKeepCount>1</TrimDuplicatesKeepCount>
    </QueryProperties>
    <WhiteList xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a:string>RowLimit</a:string>
        <a:string>SortList</a:string>
        <a:string>StartRow</a:string>
        <a:string>RefinementFilters</a:string>
        <a:string>Culture</a:string>
        <a:string>RankingModelId</a:string>
        <a:string>TrimDuplicatesIncludeId</a:string>
        <a:string>ReorderingRules</a:string>
        <a:string>EnableQueryRules</a:string>
        <a:string>HiddenConstraints</a:string>
        <a:string>QueryText</a:string>
        <a:string>QueryTemplate</a:string>
    </WhiteList>
</QueryPropertiesTemplate>
  ```

4. Mettez à jours les éléments  _SiteId_,  _FarmId_ et _WebId_ avec les valeurs de votre batterie de serveurs, site web et collection de sites de publication.
    
  
5. Enregistrez le fichier queryparametertemplate.xml dans la bibliothèque de documents QueryPropertiesTemplate.
    
  
6. Ajoutez le paramètre  _QueryTemplatePropertiesUrl_ à votre appel REST de recherche, en indiquantspfile://webroot/queryparametertemplate.xml comme valeur.
    
  

### Fichier queryparametertemplate.xml

Principaux éléments du fichier queryparametertemplate.xml
  
    
    

- Élément **QueryProperties**
  
    
    
 : contient un objet [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) sérialisé.
    
  
- Élément **WhiteList**
  
    
    
 : contient la liste des propriétés de requête que l'utilisateur anonyme est autorisé à définir.
    
  
Lorsqu'une requête REST de recherche anonyme est envoyée, l'objet de requête est créé à l'aide de ce qui est indiqué dans l'élément **QueryProperties**. Ensuite, toutes les propriétés répertoriées dans la liste verte sont copiées à partir de la requête entrante vers l'objet de requête récemment créé.
  
    
    

## Dans cette section
<a name="bk_AnonymousREST"> </a>


-  [Lors de la récupération des suggestions de requête à l'aide du service de recherche reste](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Recherche dans SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 : utilisation du service REST de recherche à partir d'une application pour SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [Nouveautés en recherche de SharePoint 2013 pour les développeurs](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [Programmation à l'aide du service SharePoint 2013 REST](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

