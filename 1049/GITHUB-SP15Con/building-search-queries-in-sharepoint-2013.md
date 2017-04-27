---
title: Построение запросов поиска в SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c4372fcc-4574-4c81-a345-a1bb282ca8f7
---


# Построение запросов поиска в SharePoint 2013
Узнайте о синтаксисе поиска, который поддерживается в SharePoint Server 2013 для создания правил запроса и поисковых запросов.
## Поддерживаемый синтаксис поиска в SharePoint Server 2013 для создания поисковых запросов
<a name="SP15Buildquery_support"> </a>

Поиск в SharePoint Server 2013 поддерживает синтаксис языка запросов по ключевым словам (KQL) и языка запросов FAST (FQL).
  
    
    
 **Язык запросов по ключевым словам (KQL)**
  
    
    
KQL  это язык запросов для создания поисковых запросов, использующийся по умолчанию. С его помощью можно задать условия поиска или ограничения свойств, передающиеся в службу поиска SharePoint.
  
    
    
 **Язык запросов FAST (FQL)**
  
    
    
FQL  это язык SQL, поддерживающий расширенные операторы запросов. Его можно использовать для создания сложных запросов, которые необходимо программно передать в службу запросов SharePoint. FQL не предназначен для пользователей и отключен по умолчанию. 
  
    
    
Чтобы его включить, используйте свойство **EnableFQL**. Затем скопируйте источник результатов по умолчанию и измените строку преобразования запроса  `{?{searchTerms} -ContentClass=urn:content-class:SPSPeople}` на одном из трех уровней (в приложении службы поиска, или SSA, семействе веб-сайтов, а также на сайте), одним из этих способов:
  
    
    

- Удалите фильтр KQL  `-ContentClass:urn:content-class:SPSPeople` в строке преобразования запроса. В результате получится следующая строка: `{?{searchTerms}}`.
    
  
- Замените строку преобразования запроса на аналогичную строку FQL, например  `{?andnot({searchTerms},filter(contentclass:"urn:content-class:SPSPeople*"))}`.
    
  
Дополнительные сведения об источниках результатов и принципах их использования см. в статьях  [Источники результатов](http://office.microsoft.com/ru-ru/support/sharepoint/sharepointsearch/understanding-result-sources-HA102848849.aspx) и [Настройка источников результатов для поиска в SharePoint Server 2013](http://technet.microsoft.com/ru-ru/library/jj683115%28v=office.15%29.aspx).
  
    
    

## В этой статье
<a name="SP15Buildquery_support"> </a>


-  [Справочник по синтаксису языка запросов по ключевым словам (KQL)](keyword-query-language-kql-syntax-reference.md)
    
  
-  [справочник по синтаксису языка запросов FAST (FQL)](fast-query-language-fql-syntax-reference.md)
    
  
-  [Использование API поисковых запросов SharePoint 2013](using-the-sharepoint-2013-search-query-apis.md)
    
  

## Дополнительные ресурсы
<a name="SP15Buildquery_addlresources"> </a>


-  [Поиск в SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [Планирование преобразования запросов и упорядочивания результатов в SharePoint 2013](http://technet.microsoft.com/ru-ru/library/jj219620%28v=office.15%29.aspx)
    
  
-  [Переменные запроса в SharePoint Server 2013](http://technet.microsoft.com/ru-ru/library/jj683123.aspx)
    
  

