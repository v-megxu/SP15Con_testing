---
title: Información general de la API de REST de SharePoint Search
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# Información general de la API de REST de SharePoint Search
Agregue la función de búsqueda a las aplicaciones de cliente y móviles mediante el servicio REST de búsqueda en SharePoint Server 2013 y en cualquier tecnología que sea compatible con las solicitudes web REST.
## Realizar consultas con el servicio REST de búsqueda
<a name="bk_queryrest"> </a>

Buscar en SharePoint 2013 incluye un servicio REST de búsqueda que se puede usar para agregar funcionalidad de búsqueda a las aplicaciones de cliente y móviles mediante cualquier tecnología compatible con las consultas web REST. Puede usar el servicio REST de búsqueda para enviar consultas de lenguaje de consulta de palabras clave (KQL) o lenguaje de consulta FAST (FQL) en sus Complementos de SharePoint, aplicaciones de cliente remoto, aplicaciones móviles y otras aplicaciones.
  
    
    
El servicio REST de búsqueda admite tanto solicitudes **POST** HTTP como **GET** HTTP.
  
    
    

### Solicitudes GET

Construya el URI de la solicitud **GET** de la consulta en el servicio REST de búsqueda de la siguiente manera:
  
    
    
 `/_api/search/query`
  
    
    
Para las solicitudes **GET**, especifique los parámetros de consulta en la dirección URL. Puede construir la dirección URL de la solicitud **GET** de dos maneras:
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### Solicitudes POST

Construya el URI de la solicitud **POST** de la consulta en el servicio REST de búsqueda de la siguiente manera:
  
    
    
 `/_api/search/postquery`
  
    
    
Para las solicitudes **POST**, pase los parámetros de consulta en la solicitud en el formato Notación de objetos de JavaScript (JSON).
  
    
    
La versión **POST** HTTP del servicio REST de búsqueda admite todos los parámetros que admitía la versión **GET** HTTP. Sin embargo, algunos de los parámetros tienen diferentes tipos de datos, como se describe en la tabla 1.
  
    
    

**Tabla 1. Parámetros de consulta con diferentes tipos de datos para las solicitudes POST**


|**Parámetro**|**Tipo de datos**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HithighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Properties](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
Use las solicitudes **POST** en las siguientes situaciones:
  
    
    

- Cuando va a superar la restricción de longitud de la dirección URL con una solicitud **GET**.
    
  
- Cuando no puede especificar los parámetros de consulta en una dirección URL simple. Por ejemplo, si tiene que pasar valores de parámetro que contienen una matriz de tipo complejo, o cadenas de valores separados por comas, tendrá más flexibilidad si construye la solicitud **POST**.
    
  
- Cuando usa el parámetro  [ReorderingRules](#bk_ReorderingRules), porque solo es compatible con las solicitudes **POST**.
    
  

## Uso de parámetros de consulta con el servicio REST de búsqueda
<a name="bk_UsingQueryParams"> </a>

Cuando realiza una llamada al servicio REST de búsqueda, debe especificar parámetros de consulta con la solicitud. Buscar en SharePoint 2013 usa esos parámetros de consulta para construir la consulta de búsqueda. Con una solicitud **GET**, se especifican los parámetros de consulta en la dirección URL. Para las solicitudes **POST**, se pasan los parámetros de consulta en el cuerpo del formato Notación de objetos de JavaScript (JSON).
  
    
    
Las siguientes secciones describen los parámetros de consulta que puede usar para enviar consultas de búsqueda con el servicio REST de búsqueda.
  
    
    

### Parámetro QueryText

Una cadena que contiene el texto de la consulta de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

Una cadena que contiene el texto que reemplaza al texto de la consulta, como parte de una transformación de consulta.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:johndoe'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

Un valor booleano que especifica si las tablas de resultados que se devuelven para el bloque de resultados están combinadas con las tablas de resultados que se devuelven para la consulta original.
  
    
    
 **true** para combinar las tablas de resultados; en caso contrario, **false**. El valor predeterminado es **true**.
  
    
    
Cambie este valor solo si desea proporcionar su propia implementación intercalada.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

El identificador de origen de resultados que se va a usar para ejecutar la consulta de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

El identificador del modelo de clasificación que se va a usar para la consulta.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

La primera fila que se incluye en los resultados de búsqueda que se devuelven. Utilice este parámetro cuando desee implementar la paginación en los resultados de la búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

El número máximo de filas generales que se devuelven en los resultados de búsqueda. En comparación con  _RowsPerPage_,  _RowLimit_ es el número máximo de filas devuelto en general.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

El número máximo de filas que devolver por página. En comparación con  _RowLimit_,  _RowsPerPage_ hace referencia al número máximo de filas que devolver por página y se utiliza principalmente cuando se desea implementar la paginación en los resultados de la búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

Las propiedades administradas que se devolverán en los resultados de búsqueda. Para devolver una propiedad administrada, establezca el indicador recuperable de la propiedad en **true** en el esquema de búsqueda.
  
    
    
Para la solicitud **GET**, especifique el parámetro  _SelectProperties_ en una cadena que contiene una lista separada por comas de propiedades. Para la solicitud **POST**, especifique el parámetro  _SelectProperties_ como una matriz de cadenas.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

El identificador de configuración regional (LCID) para la consulta (vea  [ID de configuración regional asignados por Microsoft](http://msdn.microsoft.com/es-es/goglobal/bb964664.aspx)).
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

El conjunto de filtros de refinamiento que se utiliza cuando se emite una consulta de refinamiento. Para las solicitudes **GET**, se especifica el parámetro  _RefinementFilters_ como un filtro FQL. Para las solicitudes **POST**, se especifica el parámetro  _RefinementFilters_ como una matriz de filtros FQL.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

El conjunto de refinadores que devolver en un resultado de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

Los términos de consulta adicionales para anexar a la consulta.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

La lista de propiedades por las que se ordenan los resultados de la búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

Un valor booleano que especifica si la lematización está habilitada.
  
    
    
 **true** si está habilitada la lematización; de lo contrario, **false**. El valor predeterminado es **true**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

Un valor booleano que especifica si se han quitado los elementos duplicados de los resultados.
  
    
    
 **true** para quitar los elementos duplicados; de lo contrario, **false**. El valor predeterminado es **true**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

La cantidad de tiempo en milisegundos antes de que la solicitud de consulta agote el tiempo de espera. El valor predeterminado es 30000.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

Un valor booleano que especifica si se usan los términos exactos de la consulta de búsqueda para buscar coincidencias o si también se utilizan los sobrenombres.
  
    
    
 **true** si se utilizan sobrenombres; de lo contrario, **false**. El valor predeterminado es **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

Un valor booleano que especifica si se utilizan las formas fonéticas de los términos de la consulta para buscar coincidencias.
  
    
    
 **true** si se utilizan las formas fonéticas; de lo contrario, **false**. El valor predeterminado es **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

Un valor booleano que especifica si la consulta usa el lenguaje de consulta FAST (FQL).
  
    
    
 **true** si la consulta es una consulta FQL; de lo contrario, **false**. El valor predeterminado es **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HithighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

Las propiedades que se desean resaltar en el resumen de resultados de la búsqueda cuando el valor de la propiedad coincida con los términos de búsqueda especificados por el usuario. Para las solicitudes **GET**, los términos se especifican en una cadena que contiene una lista separada por comas de las propiedades. Para las solicitudes **POST**, se especifican como una matriz de cadenas.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

Un valor booleano que especifica si se debe realizar un procesamiento de tipo de resultado de la consulta.
  
    
    
 **true** para realizar el procesamiento de tipo de resultado; de lo contrario, **false**. El valor predeterminado es **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

Un valor booleano que especifica si se devuelven los resultados más probables de la consulta.
  
    
    
 **true** para devolver los resultados más probables; de lo contrario, **false**. Este parámetro se usa únicamente cuando **EnableQueryRules** está establecido en **true**, de lo contrario se omite. El valor predeterminado es **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

El tipo de cliente que emitió la consulta.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

El GUID para el usuario que envió la consulta de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

La dirección URL de la página de resultados de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

Etiquetas personalizadas que identifican la consulta. Puede especificar varias etiquetas de consulta, separadas por punto y coma.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Properties
<a name="bk_Properties"> </a>

Propiedades adicionales para la consulta. Las solicitudes **GET** solo admiten valores de cadena. Las solicitudes **POST** admiten valores de cualquier tipo.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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


> **NOTA**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) especifica el tipo de la propiedad; cada tipo tiene un valor de índice específico.
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

Un valor booleano que especifica si se habilitan las reglas de consulta para la consulta.
  
    
    
 **true** para habilitar las reglas de consulta; de lo contrario, **false**. El valor predeterminado es **true**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

Reglas especiales para reordenar los resultados de la búsqueda. Estas reglas pueden especificar que los documentos que cumplan ciertas condiciones se clasifiquen más arriba o más abajo en los resultados. Esta propiedad solo se aplica cuando los resultados de la búsqueda se ordenan en función de la clasificación. Debe usar una solicitud **POST** para esta propiedad; no funciona en una solicitud **GET**.
  
    
    
En el ejemplo siguiente,  _MatchType_ hace referencia a [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) . En el ejemplo siguiente, `'MatchType' : '0'` especifica [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) .
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



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

Un valor booleano que especifica si se devuelven favoritos personales con los resultados de búsqueda.
  
    
    
 **true** para devolver favoritos personales; de lo contrario, **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

La ubicación del archivo queryparametertemplate.xml. Este archivo se utiliza para permitir que los usuarios anónimos realicen consultas REST de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

El número de propiedades para mostrar el resaltado de referencias en los resultados de la búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

Un valor booleano que especifica si se pueden ordenar las propiedades destacadas de los resultados.
  
    
    
 **true** para habilitar reglas de ordenación; de lo contrario, **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

Las propiedades administradas que se utilizan para determinar cómo contraer los resultados de búsqueda individuales. Los resultados se contraen en uno o en un número especificado de resultados si coinciden con cualquiera de las especificaciones de contracción individuales. Dentro de una única especificación de contracción, los resultados se contraen si sus propiedades coinciden con todas las propiedades individuales de la especificación de contracción.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

Un valor booleano que especifica si se van a ordenar los resultados de búsqueda.
  
    
    
 **true** para ordenar los resultados de búsqueda mediante _SortList_, o por clasificación si el parámetro  _SortList_ está vacío. **false** para dejar los resultados sin ordenar.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

Un valor booleano que especifica si se debe devolver la información de registro de la clasificación por bloques en la propiedad **BlockRankLog** de la tabla de resultados intercalados. Un registro de clasificación por bloques contiene la información textual de la puntuación de los bloques y los documentos que se desduplicaron.
  
    
    
 **true** para devolver la información de registro de la clasificación por bloques; de lo contrario, **false**.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

El identificador de configuración regional (LCID) de la interfaz de usuario (consulte  [ID de configuración regional asignados por Microsoft ](http://msdn.microsoft.com/es-es/goglobal/bb964664)).
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

El número preferido de caracteres que se mostrarán en el resumen de resaltado de referencias generado para un resultado de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

El número máximo de caracteres que se mostrarán en el resumen de resaltado de referencias generado para un resultado de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

El número de caracteres que se mostrarán en el resumen de resultados para un resultado de búsqueda.
  
    
    
 **Ejemplo de solicitud GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **Ejemplo de solicitud POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## Habilitar las consultas REST de búsqueda anónimas
<a name="bk_AnonymousREST"> </a>

Puede configurar la búsqueda para admitir consultas REST de búsqueda de usuarios anónimos. Los administradores de sitio pueden decidir qué parámetros de consulta exponer a los usuarios anónimos mediante el uso del archivo queryparametertemplate.xml. En esta sección se describe cómo configurar su sitio para habilitar el acceso anónimo y crear el archivo queryparametertemplate.xml.
  
    
    

### Para habilitar las consultas REST de búsqueda anónimas


1. Habilite el acceso anónimo en la aplicación web y el sitio de publicación. Para obtener más información acerca de cómo hacerlo, consulte  [Administración de directivas de permisos para una aplicación web en SharePoint 2013](http://technet.microsoft.com/es-es/library/ff608071.aspx) y [Planear los métodos de autenticación de usuario en SharePoint 2013](http://technet.microsoft.com/es-es/library/cc262350.aspx) en [TechNet](http://technet.microsoft.com/es-es/).
    
  
2. Agregue una nueva biblioteca de documentos denominada QueryPropertiesTemplate al sitio de publicación.
    
  
3. Cree un archivo XML llamado queryparametertemplate.xml y copie el siguiente código XML en el archivo.
    
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

4. Actualice los elementos  _SiteId_,  _FarmId_ y _WebId_ con los valores de la granja, el sitio web y la colección de sitios de publicación.
    
  
5. Guarde queryparametertemplate.xml en la biblioteca de documentos QueryPropertiesTemplate.
    
  
6. Agregue el parámetro  _QueryTemplatePropertiesUrl_ a la llamada de REST de búsqueda y, como valor, especifiquespfile://webroot/queryparametertemplate.xml.
    
  

### Archivo queryparametertemplate.xml

Los elementos principales del archivo queryparametertemplate.xml son:
  
    
    

- Elemento **QueryProperties**
  
    
    
Contiene un objeto  [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) serializado.
    
  
- Elemento **WhiteList**
  
    
    
Contiene la lista de propiedades de consulta que puede establecer el usuario anónimo.
    
  
Cuando se envía una consulta REST de búsqueda anónima, el objeto de consulta se construye con lo especificado en el elemento **QueryProperties**. A continuación, todas las propiedades que aparecen en la lista blanca se copian de la consulta entrante en el objeto de consulta recién construido.
  
    
    

## En esta sección
<a name="bk_AnonymousREST"> </a>


-  [Recuperación de sugerencias de consulta con el servicio REST de búsqueda](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Buscar en SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013: usar el servicio REST de búsqueda desde una aplicación para SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [Novedades en la búsqueda para desarrolladores en SharePoint 2013](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [Cómo programar con el servicio REST de SharePoint 2013](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

