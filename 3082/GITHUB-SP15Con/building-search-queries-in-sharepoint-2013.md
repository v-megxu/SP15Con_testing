---
title: Generar consultas de búsqueda en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c4372fcc-4574-4c81-a345-a1bb282ca8f7
---


# Generar consultas de búsqueda en SharePoint 2013
Obtenga información sobre la sintaxis de búsqueda compatible con SharePoint Server 2013 para crear reglas de consulta y consultas de búsqueda.
## Sintaxis de búsqueda compatible en SharePoint Server 2013 para crear consultas de búsqueda
<a name="SP15Buildquery_support"> </a>

La búsqueda de SharePoint Server 2013 admite sintaxis de búsqueda de lenguaje de consulta de palabras clave (KQL) y lenguaje de consulta FAST (FQL) para crear consultas de búsqueda.
  
    
    
 **Lenguaje de consulta de palabras clave (KQL)**
  
    
    
KQL es el lenguaje de consulta de forma predeterminado para crear consultas de búsqueda. Al usar KQL se especifican los términos de búsqueda o restricciones de propiedad que se pasan al servicio de búsqueda de SharePoint.
  
    
    
 **Lenguaje de consulta FAST (FQL)**
  
    
    
FQL es un lenguaje de consulta estructurado que admite operadores de consulta avanzada. Puede usar FQL cuando desee crear consultas complejas que quiera pasar mediante programación al servicio de búsqueda de SharePoint. FQL no está diseñado para exponer a los usuarios finales y está deshabilitado de forma predeterminada. 
  
    
    
Para habilitar FQL, use la propiedad **EnableFQL**. A continuación, copie el origen de resultados predeterminado y modifique la cadena de transformación de consulta  `{?{searchTerms} -ContentClass=urn:content-class:SPSPeople}`, en uno de estos niveles: aplicación de servicio de búsqueda (SSA), colección de sitios o sitio, y en una de las siguientes maneras:
  
    
    

- Quite el filtro KQL,  `-ContentClass:urn:content-class:SPSPeople`, desde la transformación de consulta. La cadena de transformación de consulta resultante será:  `{?{searchTerms}}`
    
  
- Reemplace la cadena de transformación de consulta con el equivalente de FQL como  `{?andnot({searchTerms},filter(contentclass:"urn:content-class:SPSPeople*"))}`.
    
  
Para obtener más información sobre los orígenes de resultados y cómo funcionan, vea:  [Descripción de los orígenes de resultados](http://office.microsoft.com/es-es/support/sharepoint/sharepointsearch/understanding-result-sources-HA102848849.aspx) y [Configuración de orígenes de resultados para búsqueda en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj683115%28v=office.15%29.aspx).
  
    
    

## En esta sección
<a name="SP15Buildquery_support"> </a>


-  [Referencia de sintaxis del lenguaje de consulta de palabra clave (KQL)](keyword-query-language-kql-syntax-reference.md)
    
  
-  [Referencia de sintaxis sobre el lenguaje de consulta FAST (FQL)](fast-query-language-fql-syntax-reference.md)
    
  
-  [Usar las API de consulta de búsqueda en SharePoint 2013](using-the-sharepoint-2013-search-query-apis.md)
    
  

## Recursos adicionales
<a name="SP15Buildquery_addlresources"> </a>


-  [Buscar en SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [Introducción al procesamiento de consultas en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj219620%28v=office.15%29.aspx)
    
  
-  [Variables de consultas en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj683123.aspx)
    
  

