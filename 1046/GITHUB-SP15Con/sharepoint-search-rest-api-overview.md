---
title: Visão geral da API REST da Pesquisa do SharePoint
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# Visão geral da API REST da Pesquisa do SharePoint
Adicione a funcionalidade de pesquisa e aplicativos móveis para os clientes usando o serviço de Pesquisa REST no SharePoint Server 2013 e em qualquer tecnologia compatível com os requisitos da Web para REST.
## Como consultar com o serviço de Pesquisa REST
<a name="bk_queryrest"> </a>

O Pesquisa no SharePoint 2013 inclui um serviço de Pesquisa REST que você pode usar para adicionar funcionalidade de pesquisa a aplicativos de cliente e móveis usando qualquer tecnologia que dê suporte a solicitações da Web REST. Você pode usar o serviço de Pesquisa REST para enviar consultas KQL (Linguagem de Consulta de Palavra-chave) ou FQL (Linguagem de Consulta FAST) em Suplementos do SharePoint, aplicativos cliente remotos, aplicativos móveis e outros aplicativos.
  
    
    
O serviço de Pesquisa REST dá suporte a solicitações HTTP **POST** e HTTP **GET**.
  
    
    

### Solicitações GET

Crie o URI para solicitações **GET** de consulta para o serviço de Pesquisa REST da seguinte maneira:
  
    
    
 `/_api/search/query`
  
    
    
Para solicitações **GET**, especifique os parâmetros de consulta na URL. Você pode criar a URL da solicitação **GET** de duas maneiras:
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### Solicitações POST

Crie o URI para solicitações **POST** de consulta para o serviço de Pesquisa REST da seguinte maneira:
  
    
    
 `/_api/search/postquery`
  
    
    
Para solicitações **POST**, passe os parâmetros de consulta na solicitação no formato JavaScript Object Notation (JSON).
  
    
    
A versão HTTP **POST** do serviço de Pesquisa REST dá suporte a todos os parâmetros com suporte na versão HTTP **GET**. No entanto, alguns dos parâmetros têm tipos de dados diferentes, conforme descrito na Tabela 1.
  
    
    

**Tabela 1. Parâmetros de consulta com tipos de dados diferentes para solicitações POST**


|**Parâmetro**|**Tipo de dados**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Propriedades](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
Use solicitações **POST** nas seguintes situações:
  
    
    

- Quando você vai exceder a restrição de comprimento de URL com uma solicitação **GET**. 
    
  
- Quando você não pode especificar os parâmetros de consulta em uma URL simples. Por exemplo, se tiver que passar valores de parâmetros que contêm uma matriz de tipo complexo ou cadeias de caracteres separados por vírgula, você terá mais flexibilidade ao criar a solicitação **POST**.
    
  
- Quando você usa o parâmetro  [ReorderingRules](#bk_ReorderingRules) porque ele só tem suporte com solicitações **POST**.
    
  

## Como usar parâmetros de consulta com o serviço de Pesquisa REST
<a name="bk_UsingQueryParams"> </a>

Ao fazer uma chamada ao serviço de Pesquisa REST, você especifica parâmetros de consulta com a solicitação. O Pesquisa no SharePoint 2013 usa esses parâmetros de consulta para criar a consulta de pesquisa. Com uma solicitação **GET**, você especifica os parâmetros de consulta na URL. Para solicitações **POST**, você passa os parâmetros de consulta no corpo no formato JavaScript Object Notation (JSON). 
  
    
    
As seções a seguir descrevem os parâmetros de consulta que você pode usar para enviar consultas de pesquisa com o serviço de Pesquisa REST.
  
    
    

### Parâmetro QueryText

Uma cadeia de caracteres que contém o texto da consulta de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

Uma cadeia de caracteres que contém o texto que substitui o texto da consulta, como parte de uma transformação de consulta.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:diogomartins'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

Um valor booliano que especifica se as tabelas de resultados que são retornadas para o bloco de resultados são misturadas às tabelas de resultados que são retornadas para a consulta original. 
  
    
    
 **true** para misturar ResultTables; caso contrário, **false**. O valor padrão é **true**. 
  
    
    
Altere esse valor somente se você quiser fornecer sua própria implementação de intercalação.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

A ID de origem de resultado a ser usada para executar a consulta de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

A ID do modelo de classificação a ser usado para a consulta.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

A primeira linha que é incluída nos resultados de pesquisa que são retornados. Use esse parâmetro quando desejar implementar a paginação nos resultados de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

O número máximo geral de linhas que são retornadas nos resultados de pesquisa. Em comparação com  _RowsPerPage_,  _RowLimit_ é o número máximo geral de linhas retornadas.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

O número máximo de linhas a serem retornadas por página. Em comparação com  _RowLimit_,  _RowsPerPage_ se refere ao número máximo de linhas a serem retornadas por página e é usado principalmente quando você deseja implementar a paginação nos resultados de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

As propriedades gerenciadas a serem retornadas nos resultados de pesquisa. Para retornar uma propriedade gerenciada, defina o sinalizador recuperável da propriedade como **true** no esquema de pesquisa.
  
    
    
Para solicitações **GET**, você especifica o parâmetro  _SelectProperties_ em uma cadeia de caracteres que contém uma lista de propriedades separadas por vírgulas. Para solicitações **POST**, você especifica o parâmetro  _SelectProperties_ como uma matriz de cadeia de caracteres.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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


### Cultura
<a name="bk_Culture"> </a>

A LCID (identificação de localidade) da consulta (confira  [Identificações de localidade atribuídas pela Microsoft](http://msdn.microsoft.com/en-us/goglobal/bb964664.aspx)).
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

O conjunto de filtros de refinamento usados quando você emite uma consulta de refinamento. Para solicitações **GET**, o parâmetro  _RefinementFilters_ é especificado como um filtro FQL. Para solicitações **POST**, o parâmetro  _RefinementFilters_ é especificado como uma matriz de filtros FQL.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RefinementFilters' : {
'results' : ['fileExtension:equals("docx")']
}
}
```


### Refinadores
<a name="bk_Refiners"> </a>

O conjunto de refinadores a serem retornados em um resultado de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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

Os termos de consulta adicionais a serem acrescentados à consulta.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

A lista de propriedades de acordo com as quais os resultados de pesquisa são ordenados.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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

Um valor booliano que especifica se a lematização está habilitada. 
  
    
    
 **true** se a lematização estiver habilitada; caso contrário, **false**. O valor padrão é **true**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

Um valor booliano que especifica se itens duplicados são removidos dos resultados. 
  
    
    
 **true** para remover os itens duplicados; caso contrário, **false**. O valor padrão é **true**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

O tempo em milissegundos antes que a solicitação de consulta atinja o tempo limite. O valor padrão é 30000.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

Um valor booliano que especifica se os termos exatos na consulta de pesquisa são usados para localizar correspondências ou se apelidos também são usados. 
  
    
    
 **true** se forem usados apelidos; caso contrário, **false**. O valor padrão é **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

Um valor booliano que especifica se as formas fonéticas dos termos de consulta são usadas para localizar correspondências. 
  
    
    
 **true** se as formas fonéticas forem usadas; caso contrário, **false**. O valor padrão é **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

Um valor booliano que especifica se a consulta usa a FQL (Linguagem de Consulta FAST). 
  
    
    
 **true** se for uma consulta FQL; caso contrário, **false**. O valor padrão é **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

As propriedades a serem realçadas no resumo dos resultados de pesquisa quando o valor da propriedade corresponde aos termos de pesquisa inseridos pelo usuário. Para solicitações **GET**, especifique uma cadeia de caracteres que contenha uma lista de propriedades separadas por vírgulas. Para solicitações **POST**, especifique esse item como uma matriz de cadeias de caracteres.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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

Um valor booliano que especifica se você deseja realizar o processamento de tipos de resultados para a consulta. 
  
    
    
 **true** para executar o processamento de tipos de resultados; caso contrário, **false**. O valor padrão é **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

Um valor booliano que especifica se devem ser retornados os resultados de melhores opções para a consulta. 
  
    
    
 **true** para retornar as melhores opções; caso contrário, **false**. Esse parâmetro é usado apenas quando **EnableQueryRules** é definido como **true**; caso contrário, é ignorado. O valor padrão é **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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

O tipo de cliente que emitiu a consulta.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

GUID do usuário que enviou a consulta de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

A URL da página de resultados de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

Marcas personalizadas que identificam a consulta. Você pode especificar várias marcas de consulta, separadas por ponto e vírgula.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Propriedades
<a name="bk_Properties"> </a>

Propriedades adicionais para a consulta. Solicitações **GET** dão suporte apenas a valores de cadeia de caracteres. Solicitações **POST** dão suporte a valores de qualquer tipo.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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


> **OBSERVAçãO**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) especifica o tipo de propriedade; cada tipo tem um valor de índice específico.
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

Um valor booliano que especifica se devem ser habilitadas regras de consulta para a consulta. 
  
    
    
 **true** para habilitar regras de consulta; caso contrário, **false**. O valor padrão é **true**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

Regras especiais para reordenar resultados de pesquisa. Essas regras podem especificar que documentos que correspondam a certas condições sejam classificados em posição mais elevada ou mais baixa nos resultados. Essa propriedade é aplicada apenas quando os resultados de pesquisa são classificados com base na classificação. Você deve usar uma solicitação **POST** para essa propriedade; ela não funciona em uma solicitação **GET**.
  
    
    
No exemplo a seguir,  _MatchType_ se refere a [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) . No exemplo a seguir, `'MatchType' : '0'` especifica [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) .
  
    
    
 **Exemplo de solicitação POST**
  
    
    



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

Um valor booliano que especifica se devem ser retornados favoritos pessoais com os resultados de pesquisa. 
  
    
    
 **true** para retornar favoritos pessoais; caso contrário, **false**. 
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

O local do arquivo queryparametertemplate.xml. Esse arquivo é usado para habilitar usuários anônimos a fazer consultas de Pesquisa REST.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

O número de propriedades que devem mostrar realce de ocorrências nos resultados de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

Um valor booliano que especifica se as propriedades com realce de ocorrências podem ser ordenadas. 
  
    
    
 **true** para habilitar a ordenação de regras; caso contrário, **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

As propriedades gerenciadas que são usadas para determinar como recolher resultados de pesquisa individuais. Os resultados serão recolhidos em um resultado ou em um número especificado de resultados se eles corresponderem a qualquer uma das especificações de recolhimento individuais. Em uma única especificação de recolhimento, os resultados serão recolhidos se suas propriedades corresponderem a todas as propriedades individuais na especificação de recolhimento.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

Um valor booliano que especifica se os resultados de pesquisa devem ser classificados. 
  
    
    
 **true** para classificar os resultados de pesquisa usando _SortList_ ou por classificação se _SortList_ estiver vazio. **false** para manter os resultados sem classificação.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

Um valor booliano que especifica se devem ser retornadas informações de log de classificação de bloco na propriedade **BlockRankLog** da tabela de resultados de intercalação. Um log de classificação de bloco contém as informações textuais sobre a pontuação do bloco e os documentos que foram submetidos à eliminação de duplicação.
  
    
    
 **true** para retornar informações de log de classificação de bloco; caso contrário, **false**.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

A LCID (identificação de localidade) da interface do usuário (confira  [Identificações de localidade atribuídas pela Microsoft](http://msdn.microsoft.com/en-us/goglobal/bb964664)).
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

O número preferencial de caracteres a serem exibidos no resumo com realce de ocorrências gerado para um resultado de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

O número máximo de caracteres a serem exibidos no resumo com realce de ocorrências gerado para um resultado de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

O número de caracteres a serem exibidos no resumo de resultados para um resultado de pesquisa.
  
    
    
 **Exemplo de solicitação GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **Exemplo de solicitação POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## Como habilitar consultas de Pesquisa REST anônimas
<a name="bk_AnonymousREST"> </a>

Você pode configurar a pesquisa para dar suporte a consultas de Pesquisa REST de usuários anônimos. Os administradores de sites podem decidir quais parâmetros de consulta expor a usuários anônimos usando o arquivo queryparametertemplate.xml. Esta seção descreve como configurar o site para habilitar o acesso anônimo e criar o arquivo queryparametertemplate.xml.
  
    
    

### Para habilitar consultas de Pesquisa REST anônimas


1. Habilite o acesso anônimo no aplicativo Web e no site de publicação. Para obter mais informações sobre como fazer isso, confira  [Gerenciar políticas de permissão para um aplicativo Web no SharePoint 2013](http://technet.microsoft.com/pt-br/library/ff608071.aspx) e [Planejar métodos de autenticação do usuário no SharePoint 2013](http://technet.microsoft.com/pt-br/library/cc262350.aspx) no [TechNet](http://technet.microsoft.com/en-US/).
    
  
2. Adicione uma nova biblioteca de documentos chamada QueryPropertiesTemplate ao site de publicação.
    
  
3. Crie um arquivo XML chamado queryparametertemplate.xml e copie o XML a seguir para o arquivo.
    
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

4. Atualize os elementos  _SiteId_,  _FarmId_ e _WebId_ com os valores de farm, site e conjunto de sites de publicação.
    
  
5. Salve queryparametertemplate.xml na biblioteca de documentos QueryPropertiesTemplate.
    
  
6. Adicione o parâmetro  _QueryTemplatePropertiesUrl_ à chamada de Pesquisa REST, especificandospfile://webroot/queryparametertemplate.xml como o valor.
    
  

### Arquivo queryparametertemplate.xml

Os principais elementos no arquivo queryparametertemplate.xml são:
  
    
    

- Elemento **QueryProperties**
  
    
    
Contém um objeto  [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) serializado.
    
  
- Elemento **WhiteList**
  
    
    
Contém a lista de propriedades de consulta que o usuário anônimo tem permissão para definir.
    
  
Quando uma consulta de Pesquisa REST anônima é enviada, o objeto consulta é criado usando o que é especificado no elemento **QueryProperties**. Em seguida, todas as propriedades que são listadas na lista branca são copiadas da consulta recebida para o objeto consulta recém-criado.
  
    
    

## Nesta seção
<a name="bk_AnonymousREST"> </a>


-  [Recuperando as sugestões de consulta usando o serviço de pesquisa restante](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## Recursos adicionais
<a name="bk_addresources"> </a>


-  [Pesquisa no SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013: Como usar o serviço de Pesquisa REST de um aplicativo para o SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [O que há de novo no SharePoint 2013 pesquisa para desenvolvedores](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [Programação usando o serviço SharePoint 2013 REST](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

