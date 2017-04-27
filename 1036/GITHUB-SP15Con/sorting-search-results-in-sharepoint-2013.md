---
title: Tri des résultats de recherche dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 66af835e-2c8f-405e-8bed-cb1e5436e190
---



# Tri des résultats de recherche dans SharePoint 2013

  
    
    
![Rubrique de présentation conceptuelle](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
Trie les résultats de la recherche par programmation (par pertinence, par valeur de propriété gérée, par expression de formule ou dans un ordre aléatoire) à l'aide du modèle objet de requête dans SharePoint Server 2013. 
Vous pouvez trier les résultats de la recherche pour SharePoint Server 2013 de quatre façons différentes :
  
    
    


-  [Trier les résultats de la recherche par pertinence](#SP15_Sort_search_resuilts_by_rank) : permet de trier les résultats de la recherche par pertinence.
    
  
-  [Trier les résultats de la recherche par valeur de propriété gérée](#SP15_Sort_search_results_by_managed_property_value) : permet de trier les résultats de la recherche en fonction de la valeur d'une ou de plusieurs propriétés gérées.
    
  
-  [Trier les résultats de la recherche en fonction d'une expression de formule](#SP15_Sort_search_results_by_formula) : permet de trier les résultats de la recherche par une formule spécifiée dans la requête.
    
  
-  [Trier les résultats de la recherche dans un ordre aléatoire](#SP15_Sort_search_results_in_random_order) : permet de trier les résultats de la requête dans un ordre aléatoire ou d'ajouter un composant aléatoire à l'ordre de tri.
    
  

Cet article porte sur le tri par programmation des résultats de recherche. Pour découvrir comment trier des résultats de recherche à l'aide de règles de requête SharePoint Server 2013, consultez les articles suivants :
  
    
    


-  [Modifier les résultats de recherche classés dans Gérer les règles de requête ](http://technet.microsoft.com/fr-fr/library/jj871676.aspx#BKMK_ChangeRankedSearchResults)
    
  
-  [Modifier les résultats de recherche classés dans Créer des règles de requête pour la gestion de contenu web](http://technet.microsoft.com/fr-fr/library/jj871014.aspx#BKMK_ChangeRankedSearchResults)
    
  

## Définition du tri dans une requête
<a name="SP15_Specify_sorting_in_query_request"> </a>

Lorsque vous utilisez le modèle objet de requête, vous pouvez choisir le critère de tri en fournissant une spécification de tri via la propriété  [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) de la classe [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) . La propriété [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) est du type [SortCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortCollection.aspx) , ce qui représente une collection d'objets [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) .
  
    
    
Un objet  [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) définit une façon de trier les résultats de recherche. Il se compose d'une valeur en fonction de laquelle vous souhaitez trier les résultats de recherche ( [Property](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Property.aspx) ) et d'un sens dans lequel vous souhaitez trier les résultats ( [Direction](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Direction.aspx) ). Le sens est du type [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) et peut être croissant ou décroissant.
  
    
    
Si vous disposez de plusieurs valeurs dans  [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) , le tri est effectué en fonction de la séquence dans laquelle les valeurs s'affichent. Cela signifie que chaque objet **Sort** représente un niveau d'ordre de tri. Un nouveau niveau ne modifie pas le classement des résultats qui ont été différenciés par les niveaux précédents, mais peut avoir une incidence sur l'ordre interne des résultats qui ont les mêmes valeurs de tri dans les niveaux précédents.
  
    
    
Outre le modèle objet de requête, SharePoint Server 2013 fournit également un service REST de recherche que vous pouvez utiliser pour interroger l'index de recherche avec votre client ou vos applications mobiles. Le service REST de recherche prend en charge les demandes HTTP POST et HTTP GET. Pour plus d'informations sur la construction d'URI pour ces demandes, voir  [Interrogation à l'aide du service REST de recherche](sharepoint-search-rest-api-overview.md#bk_queryrest).
  
    
    

## Trier les résultats de la recherche par pertinence
<a name="SP15_Sort_search_resuilts_by_rank"> </a>

Par défaut, les résultats de la recherche sont triés par pertinence. Cela signifie que SharePoint Server 2013 place les résultats les plus pertinents en première place du jeu de résultats de la recherche. Si vous triez par pertinence, les résultats sont toujours triés par ordre décroissant. Toutefois, vous pouvez modifier l'ordre de tri pour qu'il soit croissant à l'aide de  [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) .
  
    
    
Vous pouvez également influencer le calcul du classement dans la chaîne de requête de deux manières :
  
    
    

- À l'aide de l'opérateur **XRANK** disponible dans [Référence de syntaxe de langage de requête de mot clé (KQL)](keyword-query-language-kql-syntax-reference.md) et [Référence de la syntaxe du langage de requête FQL (FAST Query Language)](fast-query-language-fql-syntax-reference.md). Vous pouvez utiliser **XRANK** pour appliquer une amélioration de classement conditionnel si une condition de requête spécifique est remplie.
    
  
- En choisissant une pondération de pertinence pour le classement dynamique. Lorsque vous utilisez FQL, vous pouvez spécifier une pondération de pertinence individuelle pour chaque opérateur **STRING**.
    
  

## Trier les résultats de la recherche par valeur de propriété gérée
<a name="SP15_Sort_search_results_by_managed_property_value"> </a>

Vous pouvez spécifier un tri des résultats de la recherche en fonction de la valeur d'une ou de plusieurs propriétés gérées. Cela signifie que SharePoint Server 2013 effectue le tri en fonction de tous les résultats qui correspondent à la requête.
  
    
    
Vous pouvez trier en fonction de propriétés de texte et numériques. Pour les propriétés de texte, le tri est basé sur un tri de chaînes de texte standard. En revanche, pour les propriétés numériques (y compris les propriétés gérées de type  [DateTime](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.DateTime.aspx) ), le tri est basé sur une valeur numérique.
  
    
    

### Exemple

L'exemple suivant décrit comment trier les résultats de la recherche à l'aide de la propriété gérée **Size**.
  
    
    

```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("Size", SortDirection.Descending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"] + " Size:" + result["Size"]);
    }
}
```

Sinon, vous pouvez utiliser l'API REST de recherche pour trier les résultats de la recherche à l'aide de la propriété **Size** avec l'appel suivant.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='size:descending'
```


## Trier les résultats de la recherche en fonction d'une expression de formule
<a name="SP15_Sort_search_results_by_formula"> </a>

Vous pouvez indiquer un tri des résultats de la recherche basé sur une spécification de tri qui utilise une formule mathématique afin de créer la valeur de tri.
  
    
    
La fonctionnalité de tri par formule est une extension de la fonctionnalité de tri à niveau unique et à plusieurs niveaux pour les résultats de la recherche. Cette fonctionnalité vous permet de spécifier une formule au lieu d'une propriété gérée en tant que critère de tri. 
  
    
    
À l'aide de la fonctionnalité de tri par formule, vous pouvez appliquer des opérations mathématiques sur la valeur d'une ou de plusieurs propriétés gérées pour chaque élément dans les résultats de la requête.
  
    
    
Voici des exemples qui peuvent être implémentés à l'aide d'une formule pour spécifier un tri des résultats de la recherche :
  
    
    

- Algorithme voisin le plus proche de K pour classer des documents.
    
  
- Distance euclidienne ou distance de Manhattan pour calculer les distances géographiques.
    
  
- Valeur préférée, par exemple, pour trier les documents en fonction de l'écart entre une valeur de propriété gérée donnée et une valeur préférée.
    
  
La fonctionnalité de tri par formule n'inclut pas le contrôle de paramètres de classement dynamique statistique, tels que la fréquence ou la proximité d'un terme.
  
    
    
La formule est évaluée de gauche à droite et utilise la priorité d'opérateur mathématique standard. Autrement dit, les fonctions et les groupes entre parenthèses sont évalués en premier, les opérations de multiplication et de division sont réalisées en deuxième, puis les additions et soustractions sont effectuées en dernier.
  
    
    

> **IMPORTANTE**
> Le résultat final d'une formule doit être compris dans la plage de valeurs d'un entier signé 32 bits. Dans le cas contraire, il est possible que le tri soit incorrect. 
  
    
    


### Spécification de la formule de tri dans une requête

Vous spécifiez une formule de tri au lieu d'une propriété gérée dans la spécification de tri de la requête.
  
    
    
La spécification de tri est au format suivant :  `[formula:<sort-formula>]`
  
    
    
Dans le format,  _<sort-formula>_ est l'expression de formule de tri.
  
    
    

> **REMARQUE**
> Les crochets font partie de la syntaxe de spécification de tri. 
  
    
    

Le sens du tri par défaut est décroissant. Vous pouvez également utiliser une formule qui trie les résultats par ordre croissant, par exemple dans le cas où la formule indique une distance géographique.
  
    
    
L'exemple de code suivant montre comment spécifier un tri en fonction d'une formule par ordre croissant à l'aide du modèle objet de requête.
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(2000-size)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

Sinon, vous pouvez utiliser l'API REST de recherche pour trier les résultats de la recherche à l'aide de la propriété **Size** avec l'appel suivant.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(2000-size)]:ascending'

```


### Utilisation des propriétés gérées dans la formule de tri

Vous pouvez appliquer une formule de tri à la valeur des propriétés gérées de type  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) , [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) et [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) . Vous devez activer le tri de la propriété gérée spécifiée dans le schéma de recherche.
  
    
    
Pour plus de propriétés gérées de type  [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) , la valeur est multipliée par 10^ (décimales) avant d'être utilisée dans l'évaluation de la formule.
  
    
    
Pour les propriétés gérées de type  [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) , la valeur est convertie au nombre de 100 nanosecondes depuis le 1er janvier 29 000 av. J.-C. avant d'être utilisée dans l'évaluation de la formule. Une année comporte 366 jours.
  
    
    

### Expressions de formule de tri

Le tableau 1 répertorie les fonctions que vous pouvez utiliser dans l'expression de la formule de tri. L'expression ne doit pas contenir d'espaces.
  
    
    

**Tableau 1. Fonctions pour les expressions de formule de tri**


|**Fonction**|**Description**|
|:-----|:-----|
|**+** <br/> |Indique l'addition.  <br/> |
|**-** <br/> |Indique la soustraction.  <br/> |
|* <br/> |Indique la multiplication.  <br/> |
|**/** <br/> |Indique la division.  <br/> > **REMARQUE**> Par défaut, une division par zéro entraîne une exception et la requête est renvoyée avec une erreur. À l'aide de l'opérateur **errtolast**, vous pouvez éviter l'erreur de la requête et placer les éléments ayant échoué à la fin du jeu de résultats.           |
|**rank** <br/> |Mot clé spécial qui représente le classement dynamique d'un élément.  <br/> Exemple :  `abs(rank-100)` utilise la distance à partir de la valeur de classement 100 comme critère de tri. <br/> |
|**[0-9.]+** <br/> |Indique que les nombres peuvent être affectés en tant que valeurs entières ou doubles.  <br/> Exemples : 503, 3,14 ou 5,4352262  <br/> |
|**[a-z0-9]+]** <br/> |Indique que n'importe quelle séquence de caractères non reconnue en tant que nom de fonction est considérée comme un nom de propriété gérée. Vous devez activer le tri pour la propriété gérée spécifiée dans le schéma de recherche.  <br/> Exemple : vous pouvez définir une propriété gérée nommée **height** avec le tri activé. Cela vous permet d'utiliser « height » comme une expression dans la formule. Celle-ci utilise la valeur de la propriété gérée **height**.  <br/> |
|**( and )** <br/> |Fonction utilisée pour grouper les calculs afin d'assurer une priorité correcte.  <br/> Exemple : 4*(3+2)  <br/> |
|**sqrt(n)** <br/> |Racine carrée de  _n_.  <br/> |
|**exp(n)** <br/> |Fonction exponentielle équivalent à  *puissance(2,71828182846,n)*  <br/> |
|**log(n)** <br/> |Logarithme népérien de  _n_.  <br/> |
|**abs(n)** <br/> |Valeur absolue de  _n_.  <br/> |
|**ceil(n)** <br/> |Plafond de  _n_. Autrement dit, si  _n_ n'est pas un nombre entier, il est arrondi au nombre entier suivant. Si _n_ est un nombre entier, utilisez _n_.  <br/> |
|**floor(n)** <br/> |Plancher de  _n_. Autrement dit, si  _n_ n'est pas un nombre entier, il est arrondi au nombre entier inférieur. Si _n_ est un nombre entier, utilisez _n_.  <br/> |
|**round(n)** <br/> |Arrondi de  _n_ au nombre entier pair le plus proche. Également appelé « arrondi bancaire » ou « arrondi au chiffre pair ». <br/> |
|**sin(n)** <br/> |Sinus de  _n_ radians. <br/> |
|**cos(n)** <br/> |Cosinus de  _n_ radians. <br/> |
|**tan(n)** <br/> |Tangente de  _n_ radians. <br/> |
|**asin(n)** <br/> |Arc sinus, exprimé en radians, de  _n_.  <br/> |
|**acos(n)** <br/> |Arc cosinus, exprimé en radians, de  _n_.  <br/> |
|**atan(n)** <br/> |Arc tangente, exprimé en radians, de  _n_.  <br/> |
|**pow(x,y)** <br/> |Valeur de  _x_ élevé à la puissance de _y_.  <br/> > **REMARQUE**> La valeur de  _y_ doit être un nombre réel.          |
|**atan2(y,x)** <br/> |Arc tangente à deux arguments de l'angle exprimé en radians, entre l'axe des abscisses positif et l'axe des coordonnées cartésien indiqué (x, y).  <br/> |
|**bucket(b,n1,n2,…)** <br/> |Opérateur pouvant être utilisé pour fournir des valeurs distinctes pour des plages de distribution de valeur données pour une expression.  <br/> L'expression  _b_ peut être une propriété gérée ou toute autre expression de formule. Les arguments _n1, n2, …_ représentent des seuils numériques. Vous pouvez spécifier un nombre arbitraire de seuils de compartiments. <br/> > **REMARQUE**> Vous devez organiser les arguments  _n1, n2, n3, …_ dans l'ordre suivant : `n1 < n2 < n3 < ...` où `n1 >= 0`.           Une valeur donnée pour l'expression d'entrée  _b_ est arrondie au seuil numérique inférieur le plus proche. Si elle est inférieure au seuil le plus bas donné, la valeur sortante est zéro. <br/> |
|**errtolast(x)** <br/> |Un opérateur peut être utilisé pour contrôler la gestion des exceptions de formule.  _x_ peut représenter toute expression de formule. Si le calcul de cette expression formule aboutit à une exception mathématique pour un élément du jeu de résultats, comme une division par zéro, ces éléments s'affichent à la fin de la liste de tri, quel que soit l'ordre de tri spécifié. <br/> |
   

### Caractéristiques de performances pour le tri par formule

L'utilisation d'une formule de tri implique que les calculs de formule soient appliqués à tous les éléments correspondants dans le jeu de résultats. Cela signifie que l'impact des performances de requête dépend du nombre d'éléments qui correspondent à la requête.
  
    
    
Les formules longues comportant de nombreux opérateurs nécessitent plus de temps de traitement que les formules courtes.
  
    
    

### Utilisation du tri par formule pour les distances géographiques

Vous pouvez utiliser le tri par formule pour appliquer un classement en fonction de la distance. Pour ce faire, vous devez inclure des propriétés gérées qui représentent la latitude et la longitude de chaque élément.
  
    
    
Par exemple, vous pouvez utiliser l'une des formules standard suivantes :
  
    
    

- Distance de Manhattan
    
  
- Distance euclidienne (voir exemple 2)
    
  
- Formule de Haversine
    
  

> **IMPORTANTE**
> Utilisez des propriétés gérées de type **Decimal** ou **Float** pour représenter les valeurs de latitude et de longitude.
  
    
    


### Exemples

Les exemples suivants montrent comment spécifier la formule de tri à l'aide du modèle objet de requête.
  
    
    
 **Exemple 1.** Placez les éléments dont la propriété gérée **height** est la plus proche de 20 en haut de la liste des résultats.
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(20-height)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

Vous pouvez aussi utiliser l'API REST de recherche pour placer les éléments dont la propriété gérée **height** est la plus proche de 20 en haut de la liste des résultats, à l'aide de l'appel suivant.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(20-height)]:ascending
```

 **Exemple 2.** Triez par véritable distance euclidienne 3D à partir d'une position donnée (par exemple la position de l'utilisateur) en fonction des informations de position fournies dans les propriétés gérées **latitude**, **longitude** et **height**. La formule suivante indique la distance euclidienne 3D, car la position de base est 50/100/200 (latitude, longitude, altitude).
  
    
    
 `sqrt(pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2))`
  
    
    
Si vous souhaitez appliquer un tri basé sur la distance (sans combiner la distance avec d'autres paramètres dans une formule), vous pouvez supprimer le composant  `sqrt()`. Ce dernier ne modifie pas la séquence de tri, mais il améliore les performances des requêtes.
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

 **Exemple 3.** Arrondissez les valeurs de taille en compartiments, en arrondissant les valeurs à l'une des unités inférieures suivantes : 0, 5, 15, 50, 100. Effectuez le tri avec les valeurs les plus élevées d'abord.
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:bucket(size,5,15,50,100)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## Trier les résultats de la recherche dans un ordre aléatoire
<a name="SP15_Sort_search_results_in_random_order"> </a>

Vous pouvez appliquer un tri aléatoire aux résultats de la requête, ou ajouter un composant aléatoire pour le tri des résultats.
  
    
    
La spécification de tri aléatoire est au format suivant :  `[random:seed=<seed>:hashfield=<managed property>]`
  
    
    

> **REMARQUE**
> Les crochets font partie de la syntaxe de spécification de tri. 
  
    
    

Le tableau 2 décrit les paramètres pour la spécification de tri aléatoire.
  
    
    

**Tableau 2. Paramètres pour la spécification de tri aléatoire**


|**Paramètre**|**Description**|**Obligatoire**|
|:-----|:-----|:-----|
| _Seed_ <br/> |Valeur de départ pour la génération de la valeur aléatoire.  <br/> La valeur de départ est saisie dans une fonction qui génère un nombre aléatoire. Ce numéro aléatoire est utilisé lors du tri final. En utilisant uniquement l'option  _seed_, vous obtiendrez un jeu de résultats de requête trié de manière aléatoire. L'ordre de tri pour la même requête (lorsque vous utilisez la même valeur de départ) est susceptible de changer après une mise à jour de l'index.  <br/> |Oui  <br/> |
| _Hashfield_ <br/> |Propriété gérée qui est utilisée en tant que valeur de hachage pour la génération aléatoire. Vous pouvez utiliser ce paramètre pour vous assurer que l'ordre de tri pour la même requête (lorsque vous utilisez la même valeur de départ) n'est pas modifié après une mise à jour de l'index.  <br/> La propriété gérée doit être de type  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) et doit être [Sortable()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.Sortable.aspx) . Vous pouvez remplir cette propriété gérée avec des valeurs aléatoires ou uniques (par exemple, un numéro de séquence rempli par une étape de traitement d'élément). <br/> |Non  <br/> |
   
En fournissant la même valeur de départ pour des requêtes identiques, les éléments se présentent dans le même ordre. Cela vous permet de conserver le même ordre aléatoire lors de la pagination des résultats de la recherche. Utilisez le paramètre  _hashfield_ si vous souhaitez conserver le même ordre aléatoire lorsqu'une mise à jour de l'index survient accidentellement entre les requêtes.
  
    
    

### Exemples

Les exemples suivants montrent comment spécifier un tri aléatoire à l'aide du modèle objet de requête.
  
    
    
 **Exemple 1.** Triez l'ensemble du jeu de résultats dans un ordre aléatoire.
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=5432]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

Sinon, vous pouvez utiliser l'API REST de recherche pour trier l'ensemble du jeu de résultats dans un ordre aléatoire, à l'aide de l'appel suivant.
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[random:seed=5432]:ascending
```

 **Exemple 2.** Triez l'ensemble du jeu de résultats dans un ordre aléatoire. Conservez la même séquence aléatoire pour la même requête avec la même valeur de départ, même en cas de basculement de l'index. Une propriété gérée personnalisée appelée **hashvalue** doit être disponible dans le schéma de recherche et remplie avec des valeurs numériques aléatoires ou séquentielles pour tous les éléments indexés.
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=6543:hashfield=hashvalue]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## Ressources supplémentaires
<a name="bk_addresources"> </a>


-  [Recherche dans SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [Référence de syntaxe de langage de requête de mot clé (KQL)](keyword-query-language-kql-syntax-reference.md)
    
  
-  [Référence de la syntaxe du langage de requête FQL (FAST Query Language)](fast-query-language-fql-syntax-reference.md)
    
  
-  [Vue d'ensemble de l'API REST de recherche SharePoint](sharepoint-search-rest-api-overview.md)
    
  
-  [Vue d'ensemble des propriétés analysées et gérées dans SharePoint Server 2013](http://technet.microsoft.com/fr-fr/library/jj219630%28office.15%29.aspx)
    
  

  
    
    
