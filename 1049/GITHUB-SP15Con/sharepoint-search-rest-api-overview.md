---
title: Общие сведения об API службы поиска REST для SharePoint
ms.prod: SHAREPOINT
ms.assetid: 8a4f7863-e4c1-4099-9189-a1894db36930
---


# Общие сведения об API службы поиска REST для SharePoint
Добавление функции поиска в клиентские и мобильные приложения с помощью службы поиска REST в SharePoint Server 2013 и в любой технологии, поддерживающей веб-запросы REST.
## Выполнение запросов с помощью службы поиска REST
<a name="bk_queryrest"> </a>

Поиск в SharePoint 2013 включает службу поиска REST, которую вы можете использовать для добавления функции поиска в свои клиентские или мобильные приложения с помощью любой технологии, поддерживающей веб-запросы REST. Вы можете использовать службу поиска REST для отправки запросов на языке запросов по ключевым словам (KQL) или на языке FAST-запросов (FQL) в своих Надстройки SharePoint, удаленных клиентских приложениях, мобильных и других приложениях.
  
    
    
Служба поиска REST поддерживает HTTP-запросы **POST** и **GET**.
  
    
    

### Запросы GET

Создайте URI, чтобы отправлять службе поиска REST запросы **GET**:
  
    
    
 `/_api/search/query`
  
    
    
Укажите параметры запроса для запросов **GET** в URL-адресе. Вы можете создать URL-адрес запроса **GET** двумя способами:
  
    
    


  
    
    
>  `http://server/_api/search/query?query_parameter=value&amp;query_parameter=value`
    
  

  
    
    
>  `http://server/_api/search/query(query_parameter=value&amp;query_parameter=<value>)`
    
  

### Запросы POST

Создайте URI, чтобы отправлять службе поиска REST запросы **POST**:
  
    
    
 `/_api/search/postquery`
  
    
    
Для запросов **POST** передайте параметры запроса в запросе в формате Нотация объектов JavaScript (JSON).
  
    
    
HTTP-версия **POST** службы поиска REST поддерживает все параметры, поддерживаемые версией **GET**. Однако некоторые параметры имеют различные типы данных, как это описано в таблице 1.
  
    
    

**Таблица 1. Параметры запроса с различными типами данных для запросов POST**


|**Параметр**|**Тип данных**|
|:-----|:-----|
| [SelectProperties](#bk_SelectProperties) <br/> |string[]  <br/> |
| [RefinementFilters](#bk_RefinementFilters) <br/> |string[]  <br/> |
| [SortList](#bk_SortList) <br/> | [Sort](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.Sort.aspx) <br/> |
| [HithighlightedProperties](#bk_HithighlightedProperties) <br/> |​string[]  <br/> |
| [Properties](#bk_Properties) <br/> | [Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.KeywordQueryProperties.aspx) <br/> |
   
Используйте запросы **POST** в следующих случаях:
  
    
    

- Если вы превысите ограничение длины URL-адреса с помощью запроса **GET**.
    
  
- Если вы не можете указать параметры запроса в простом URL-адресе. Например, если вам нужно передать значения параметров, которые содержат массив сложных типов или строки с разделителем-запятой, запрос **POST** предоставит вам более широкие возможности.
    
  
- Если вы используете параметр  [ReorderingRules](#bk_ReorderingRules), так как он поддерживается только с помощью запросов **POST**.
    
  

## Использование параметров запроса с помощью службы поиска REST
<a name="bk_UsingQueryParams"> </a>

При вызове службы поиска REST вы указываете параметры запроса вместе с самим запросом. Поиск в SharePoint 2013 использует эти параметры для создания запроса поиска. Для запроса **GET** укажите параметры запроса в URL-адресе, для запросов **POST** передайте их в теле в формате Нотация объектов JavaScript (JSON).
  
    
    
В следующих разделах описаны параметры запроса, которые можно использовать для отправки запросов поиска с помощью службы поиска REST.
  
    
    

### Параметр QueryText

Строка, содержащая текст для запроса поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
}
```


### QueryTemplate
<a name="bk_QueryTemplate"> </a>

Строка, содержащая текст, который замещает текст запроса в ходе преобразования запроса.
  
    
    
 **Пример запроса GET**
  
    
    
http://server/_api/search/query?querytext='sharepoint'&amp;querytemplate='{searchterms} author:johndoe'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Querytemplate' : '{searchterms} Author:johndoe'
}
```


### EnableInterleaving
<a name="bk_EnableInterleaving"> </a>

Логическое значение, которое указывает смешаны ли таблицы результатов, возвращенных для блока результатов, с таблицами результатов, возвращенных для исходного запроса.
  
    
    
Значение **true**, чтобы связать ResultTables; иначе  **false**. Значение по умолчанию  **true**.
  
    
    
Изменяйте это значение только в том случае, если вы хотите предоставить собственное чередующееся выполнение.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableinterleaving=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'​EnableInterleaving' : 'True'
}
```


### SourceId
<a name="bk_SourceId"> </a>

Идентификатор источника результатов, использующийся для выполнения запроса поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sourceid='8413cd39-2156-4e00-b54d-11efd9abdb89'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'SourceId' : '8413cd39-2156-4e00-b54d-11efd9abdb89'
}
```


### RankingModelId
<a name="bk_RankingModelId"> </a>

Идентификатор модели ранжирования для запроса.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rankingmodelid​= _CustomRankingModelID_
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RankingModelId' : 'CustomRankingModelID '
}
```


### StartRow
<a name="bk_StartRow"> </a>

Первая строка, включаемая в возвращаемые результаты поиска. Используйте этот параметр, чтобы разбить результаты поиска по страницам.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;startrow=10
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'StartRow' : '10'
}
```


### RowLimit
<a name="bk_RowLimit"> </a>

Общее максимальное количество строк, которые возвращаются в результатах поиска. По сравнению с  _RowsPerPage_,  _RowLimit_  это максимальное количество возвращаемых строк в целом.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowlimit=30
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowLimit' : '30'
}
```


### RowsPerPage
<a name="bk_RowsPerPage"> </a>

Максимальное количество строк, возвращаемых на каждую страницу. По сравнению с  _RowLimit_,  _RowsPerPage_ ссылается на максимальное количество строк, возвращаемых на страницу, и обычно используется в случаях, когда необходимо разбить результаты поиска по страницам.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;rowsperpage=10
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'RowsPerPage' : '10'
}
```


### SelectProperties
<a name="bk_SelectProperties"> </a>

Управляемые свойства, возвращаемые в результатах поиска. Чтобы вернуть управляемое свойство, установите флаг извлечения свойства в схеме поиска в значение **true**.
  
    
    
Для запросов **GET** укажите в строке, содержащей список свойств, разделенных запятыми, параметр _SelectProperties_. Для запросов **POST** укажите параметр _SelectProperties_ в виде массива строк.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;selectproperties='Title,Author'
  
    
    
 **Пример запроса POST**
  
    
    



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

Код языка (LCID) для запроса (см. статью  [Коды языков, присвоенные Майкрософт](http://msdn.microsoft.com/ru-ru/goglobal/bb964664.aspx)).
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;culture=1044
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Culture' : '1044'
}
```


### RefinementFilters
<a name="bk_RefinementFilters"> </a>

Набор фильтров уточнения, используемых при получении запроса уточнения. Для запросов **GET** параметр _RefinementFilters_ указывается в виде FQL-фильтра. Для запросов **POST** параметр _RefinementFilters_ указывается в виде массива FQL-фильтров.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refinementfilters='fileExtension:equals("docx")'
  
    
    
 **Пример запроса POST**
  
    
    



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

Набор уточнений, возвращаемых в результатах поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;refiners='author,size'
  
    
    
 **Пример запроса POST**
  
    
    



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

Дополнительные термины, присоединяемые к запросу.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hiddenconstraints='developer'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'HiddenConstraints'='developer'
}
```


### SortList
<a name="bk_SortList"> </a>

Список свойств, по которым упорядочиваются результаты поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;sortlist='rank:descending,modifiedby:ascending'
  
    
    
 **Пример запроса POST**
  
    
    



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

Логическое значение, указывающее, включено ли выделение корней.
  
    
    
Значение **true**, если выделение корней включено, иначе  **false**. Значение по умолчанию  **true**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablestemming=false
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableStemming : 'False'
}
```


### TrimDuplicates
<a name="bk_TrimDuplicates"> </a>

Логическое значение, указывающее, удалены ли из результатов повторяющиеся элементы.
  
    
    
Значение **true**, чтобы удалить повторяющиеся элементы, иначе  **false**. Значение по умолчанию  **true**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;trimduplicates=false
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'TrimDuplicates'='False'
}
```


### Timeout
<a name="bk_Timeout"> </a>

Время до истечения времени запроса в миллисекундах. Значение по умолчанию: 30 000.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;timeout=60000
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'Timeout'='60000'
}
```


### EnableNicknames
<a name="bk_EnableNicknames"> </a>

Логическое значение, указывающее, используются для поиска совпадений только точные термины или еще и псевдонимы.
  
    
    
Значение **true**, если используются псевдонимы; иначе  **false**. Значение по умолчанию  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablenicknames=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableNicknames'='True'
}
```


### EnablePhonetic
<a name="bk_EnablePhonetic"> </a>

Логическое значение, которое указывает, используется ли для поиска соответствий фонетические формы терминов запроса.
  
    
    
Значение **true**, если используются фонетические формы, иначе  **false**. Значение по умолчанию  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablephonetic=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnablePhonetic'='True'
}
```


### EnableFql
<a name="bk_EnableFql"> </a>

Логическое значение, указывающее, использует ли запрос язык FAST-запросов (FQL).
  
    
    
Значение **true**, если запрос является FQL-запросом, иначе  **false**. Значение по умолчанию  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablefql=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'EnableFQL':'True'
}
```


### HithighlightedProperties
<a name="bk_HithighlightedProperties"> </a>

Свойства, которые выделяются в сводке результатов поиска, если значение свойства соответствует терминам поиска, которые указал пользователь. Для запросов **GET** укажите в виде строки, содержащую список свойств, разделенных запятыми; для запросов **POST**  в виде массива строк.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedproperties='Title'
  
    
    
 **Пример запроса POST**
  
    
    



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

Логическое значение, указывающее, следует ли выполнять обработку типа результата для запроса.
  
    
    
Значение **true**, чтобы выполнить обработку типа результата, иначе  **false**. Значение по умолчанию  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;bypassresulttypes=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'BypassResultTypes' : 'true'
}
```


### ProcessBestBets
<a name="bk_ProcessBestBets"> </a>

Логическое значение, указывающее, следует ли возвращать наиболее подходящие элементы результатов для запроса.
  
    
    
Значение **true**, чтобы вернуть наиболее подходящие элементы, иначе  **false**. Этот параметр используется только когда **EnableQueryRules** установлен в значение **true**, в противном случае он игнорируется. Значение по умолчанию  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processbestbets=true&amp;enablequeryrules=true
  
    
    
 **Пример запроса POST**
  
    
    



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

Тип клиента, выдавшего запрос.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;clienttype='custom'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint',
'ClientType':'custom'
}
```


### PersonalizationData
<a name="bk_PersonalizationData"> </a>

GUID пользователя, отправившего запрос поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _<server>_/_api/search/query?querytext='sharepoint'&amp;personalizationdata=' _<GUID>_'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'PersonalizationData' : ' <GUID> '
}
```


### ResultsURL
<a name="bk_ResultsURL"> </a>

URL-адрес для страницы результатов поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;resultsurl='http://server/site/resultspage.aspx'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint'
'ResultURL' : 'http://server/site/resultspage.aspx'
}
```


### QueryTag
<a name="bk_QueryTag"> </a>

Пользовательские теги, идентифицирующие запрос. Вы можете указать несколько тегов запроса, разделенных точкой с запятой.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext':'sharepoint'
}
```


### Properties
<a name="bk_Properties"> </a>

Дополнительные свойства для запроса. Запросы **GET** поддерживают только строковое значение. Запросы **POST** поддерживают значения любого типа.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;properties='termid:guid'
  
    
    
 **Пример запроса POST**
  
    
    



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


> **Примечание**
>  [QueryPropertyValueType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryPropertyValueType.aspx) указывает тип свойства; каждый тип имеет определенное значение индекса.
  
    
    


### EnableQueryRules
<a name="bk_EnableQueryRules"> </a>

Логическое значение, указывающее, включены ли правила запросов для запроса.
  
    
    
Значение **true**, чтобы включить правила запросов, иначе  **false**. Значение по умолчанию  **true**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablequeryrules=false
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableQueryRules' : 'false' 
}
```


### ReorderingRules
<a name="bk_ReorderingRules"> </a>

Специальные правила для изменения порядка результатов поиска. Эти правила могут указывать, что документы, соответствующие определенным условиям, имеют более высокий или более низкий рейтинг в результатах. Это свойство применяется только тогда, когда результаты поиска отсортированы на основе рейтинга. Используйте для этого свойства запрос **POST**, оно не работает с запросом **GET**.
  
    
    
В следующем примере  _MatchType_ относится к [ReorderingRuleMatchType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.aspx) . В следующем примере `'MatchType' : '0'` определяет [ResultContainsKeyword](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.ReorderingRuleMatchType.ResultContainsKeyword.aspx) .
  
    
    
 **Пример запроса POST**
  
    
    



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

Логическое значение, указывающее, возвращать ли личное избранное с результатами поиска.
  
    
    
Значение **true**, чтобы вернуть личное избранное, иначе  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;processpersonalfavorites=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'ProcessPersonalFavorites' : 'false'
}
```


### QueryTemplatePropertiesUrl
<a name="bk_ProcessPersonalFavorites"> </a>

Расположение файла queryparametertemplate.xml. Этот файл используется для того, чтобы разрешить анонимным пользователям создавать запросы поиска REST.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;querytemplatepropertiesurl='spfile://webroot/queryparametertemplate.xml'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
QueryTemplatePropertiesUrl : 'spfile://webroot/queryparametertemplate.xml'
}
```


### HitHighlightedMultivaluePropertyLimit
<a name="bk_ProcessPersonalFavorites"> </a>

Количество свойств, которые отображаются как подсвеченные совпадения в результатах поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;hithighlightedmultivaluepropertylimit=2
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'HitHighlihtedMultivaluePropertyLimit' : '2'
}
```


### EnableOrderingHitHighlightedProperty
<a name="bk_ProcessPersonalFavorites"> </a>

Логическое значение, указывающее, упорядочивать ли свойства подсвеченных совпадений.
  
    
    
Значение **true**, чтобы включить правила упорядочивания, иначе  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enableorderinghithighlightedproperty=false
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableOrderingHitHighlightedProperty' : 'false'
}
```


### CollapseSpecification
<a name="bk_ProcessPersonalFavorites"> </a>

Управляемые свойства, которые используются для определения способа свертывания отдельных результатов поиска. Результаты сворачиваются в один результат или указанное число результатов, если они соответствуют любым отдельным спецификациям свертывания. В рамках одной спецификации результаты сворачиваются, если их свойства соответствуют всем отдельным свойствам в спецификации.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;collapsespecification='Author:1 ContentType:2'
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'CollapseSpecification' : 'Author:1 ContentType:2'
}
```


### EnableSorting
<a name="bk_ProcessPersonalFavorites"> </a>

Логическое значение, указывающее, требуется ли сортировка результатов поиска.
  
    
    
Значение **true**, чтобы отсортировать результаты поиска с использованием параметра  _SortList_, или по рейтингу, если  _SortList_  пустое. Значение **false**, чтобы оставить результаты неотсортированными.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;enablesorting=false
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'EnableSorting' : 'false'
}
```


### GenerateBlockRankLog
<a name="bk_ProcessPersonalFavorites"> </a>

Логическое значение, указывающее, следует ли возвращать сведения о журнале для рейтинга блоков в свойстве **BlockRankLog** таблицы чередующихся результатов. Журнал рейтинга блоков содержит текстовые сведения по рейтингу блоков и удаленным повторяющимся документам.
  
    
    
Значение **true**, чтобы вернуть сведения о журнале рейтинга блоков, иначе  **false**.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;generateblockranklog=true
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'GenerateBlockRankLog' : 'true'
}
```


### UIlanguage
<a name="bk_ProcessPersonalFavorites"> </a>

Код языка (LCID) интерфейса пользователя (см. статью  [Коды языков, присвоенные Майкрософт](http://msdn.microsoft.com/ru-ru/goglobal/bb964664)).
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;uilanguage=1044
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'UILanguage' : '1044'
}
```


### DesiredSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

Предпочтительное количество символов для отображения в сводке подсвеченных совпадений, которая создана для результатов поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;desiredsnippetlength=80
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'DesiredSnippetLength' : '80'
}
```


### MaxSnippetLength
<a name="bk_ProcessPersonalFavorites"> </a>

Максимальное количество символов, которые отображаются в сводке подсвеченных совпадений, созданной для результатов поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;maxsnippetlength=100
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'MaxSnippetLength' : '100' 
}
```


### SummaryLength
<a name="bk_ProcessPersonalFavorites"> </a>

Количество символов, которые отображаются в сводке результатов для результатов поиска.
  
    
    
 **Пример запроса GET**
  
    
    
http:// _server_/_api/search/query?querytext='sharepoint'&amp;summarylength=150
  
    
    
 **Пример запроса POST**
  
    
    



```

{
'__metadata':{'type':'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'sharepoint',
'Summarylength' : '150'
}
```


## Включение анонимных запросов поиска REST
<a name="bk_AnonymousREST"> </a>

Вы можете настроить поиск, который поддерживает запросы поиска REST от анонимных пользователей. Администраторы сайта могут определить с помощью файла queryparametertemplate.xml, какие параметры запросов предоставить анонимным пользователям. В этом разделе описано, как настроить свой сайт, чтобы включить анонимный доступ, и создать файл queryparametertemplate.xml.
  
    
    

### Чтобы включить анонимные запросы поиска REST:


1. Включите анонимный доступ в веб-приложении и на сайте публикации. Более подробную информацию о том, как это сделать, можно узнать в статьях  [Управление политиками разрешений для веб-приложения в SharePoint 2013](http://technet.microsoft.com/ru-ru/library/ff608071.aspx) и [Планирование методов проверки подлинности пользователя в SharePoint 2013](http://technet.microsoft.com/ru-ru/library/cc262350.aspx) на сайте [TechNet](http://technet.microsoft.com/ru-ru/).
    
  
2. Добавьте на сайт публикации новую библиотеку документов с именем QueryPropertiesTemplate.
    
  
3. Создайте XML-файл с именем queryparametertemplate.xml и скопируйте в него следующий XML-код:
    
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

4. Обновите элементы  _SiteId_,  _FarmId_ и _WebId_ со значениями для вашей фермы, веб-сайта и семейства сайтов публикации.
    
  
5. Сохраните queryparametertemplate.xml в библиотеку документов QueryPropertiesTemplate.
    
  
6. Добавьте параметр  _QueryTemplatePropertiesUrl_ в свой вызов поиска REST, указав в качестве значенияspfile://webroot/queryparametertemplate.xml.
    
  

### queryparametertemplate.xml file

Основными элементами в файле queryparametertemplate.xml являются:
  
    
    

- Элемент **QueryProperties**
  
    
    
Содержит сериализованный объект  [QueryProperties](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.QueryProperties.aspx) .
    
  
- Элемент **WhiteList**
  
    
    
Содержит список свойств запроса, которые разрешено устанавливать анонимным пользователям.
    
  
При отправке анонимного запроса поиска REST создается объект запроса с использованием значения, указанного в элементе **QueryProperties**. Затем все свойства, перечисленные в whitelist, копируются из входящего запроса в только что созданный объект запроса.
  
    
    

## В этом разделе
<a name="bk_AnonymousREST"> </a>


-  [Получение предложений запроса, с помощью службы Search REST](retrieving-query-suggestions-using-the-search-rest-service.md)
    
  

## Дополнительные ресурсы
<a name="bk_addresources"> </a>


-  [Поиск в SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013: использование службы поиска REST в приложении для SharePoint](http://code.msdn.microsoft.com/sharepoint/SharePoint-2013-Perform-a-1bf3e87d)
    
  
-  [Новые возможности поиска в SharePoint для разработчиков (en)](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  
-  [Программирование с использованием службы SharePoint 2013 REST](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  

  
    
    

