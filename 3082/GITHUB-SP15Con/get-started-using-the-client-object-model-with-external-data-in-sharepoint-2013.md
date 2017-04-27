---
title: Introducción al uso del modelo de objetos de cliente con datos externos en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8ed91929-fdb6-4fde-ba2a-7942870575f3
---



# Introducción al uso del modelo de objetos de cliente con datos externos en SharePoint 2013
Aprenda a usar el modelo de objetos de cliente de SharePoint 2013 para trabajar con Servicios de conectividad empresarial (BCS) en SharePoint 2013.
## ¿Qué es el modelo de objetos de cliente de SharePoint 2013?


|||
|:-----|:-----|
|El modelo de objetos de cliente de SharePoint 2013 es un conjunto de bibliotecas basadas en clientes que representa el modelo de objetos de servidor. Se empaquetan en tres archivos DLL diferentes para adaptarse a una serie de tipos de desarrollo. El modelo de objetos de cliente incluye la mayor parte de las funciones principales de la API del servidor. Esto permite el acceso a los mismos tipos de funcionalidad desde scripts del explorador, además de aplicaciones web. NET y aplicaciones de Silverlight.  <br/> Para mejorar y ampliar las funciones para trabajar con datos externos, Servicios de conectividad empresarial (BCS) ha ampliado el modelo de objetos de cliente para incluir funcionalidad adicional.  <br/>  [![Para empezar](images/mod_icon_getstartbox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_getstarted) [![Ponerse manos a la obra](images/mod_icon_dobox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_Tasks) [![Obtener más información](images/mod_icon_startbox.gif)          ](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md#BCScsom_Learnmore) <br/> ||
   

## Introducción al uso del modelo de objetos de cliente de SharePoint 2013 con datos externos
<a name="BCScsom_getstarted"> </a>

Para desarrollar soluciones mediante el modelo de objetos de cliente de SharePoint (CSOM), necesita lo siguiente:
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools para Visual Studio 2012
    
  
Para obtener información sobre cómo configurar el entorno de desarrollo, consulte  [Cómo configurar un entorno de desarrollo para BCS en SharePoint 2013](setting-up-a-development-environment-for-bcs-in-sharepoint-2013.md).
  
    
    
Para acceder a las funciones proporcionadas por el modelo de objetos de cliente, solo debe agregar referencias a los archivos **Microsoft.SharePoint.Client.Runtime.dll** y **Microsoft.SharePoint.Client.dll** en sus proyectos. También puede usar el modelo de objetos de cliente si hace referencia a los siguientes archivos DLL en la caché global de ensamblados:
  
    
    

-  `\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\isapi\\Microsoft.SharePoint.Client.Runtime.dll`
    
  
-  `\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\isapi\\Microsoft.SharePoint.Client.dll`
    
  

### Conceptos básicos del modelo de objetos de cliente de SharePoint 2013

Los siguientes artículos le ayudarán a comprender mejor el modelo de objetos de cliente de SharePoint 2013.
  
    
    

**Tabla 1. Conceptos principales para entender el modelo de objetos de cliente**


|**Artículo**|**Descripción**|
|:-----|:-----|
| [Tipos de contenido externo en SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |Aprenda lo que puede hacer con tipos de contenido externo y lo que necesita para comenzar a crearlos en SharePoint 2013.  <br/> |
| [Uso de orígenes OData con Servicios de conectividad empresarial en SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |Proporciona información para ayudar a comenzar a crear tipos de contenido externo basados en orígenes OData y a usar esos datos en componentes de SharePoint 2013 o Office 2013.  <br/> |
| [Elegir el conjunto de API correcto en SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md) <br/> |Obtenga información sobre los distintos conjuntos de API proporcionados en SharePoint 2013, lo que incluye el modelo de objetos de servidor, los distintos modelos de objetos de cliente y el servicio web REST/OData.  <br/> |
| [Referencia a API de cliente .NET para SharePoint 2013](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx) <br/> |Busque información sobre las bibliotecas de clases de clientes de .NET en SharePoint 2013.  <br/> |
| [Referencia a API de JavaScript para SharePoint 2013](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx) <br/> |Busque información sobre las bibliotecas de objetos de JavaScript en SharePoint 2013.  <br/> |
   

## ¿Qué se puede hacer con el modelo de objetos de cliente?
<a name="BCScsom_Tasks"> </a>

Puede usar el modelo de objetos de cliente de SharePoint para recuperar, actualizar y administrar los datos incluidos en SharePoint 2013. SharePoint ofrece bibliotecas de cliente en diferentes formatos para adaptarse a la mayoría de los desarrolladores. En el caso de los desarrolladores web que usan lenguajes de scripting, la biblioteca de cliente se ofrece en JavaScript. En el caso de los desarrolladores .NET, se ofrece como un archivo DLL administrado de cliente de .NET. En el caso de los desarrolladores de aplicaciones de Silverlight, la biblioteca de cliente es proporcionada por un archivo DLL de Silverlight.
  
    
    
Consulte los artículos de la tabla 2 para obtener más información sobre lo que se puede hacer con el modelo de objetos de cliente de SharePoint 2013.
  
    
    

**Tabla 2. Tareas básicas para usar el modelo de objetos de cliente con datos externos**


|**Tarea**|**Descripción**|
|:-----|:-----|
| [Realizar operaciones básicas con código de biblioteca de cliente de SharePoint 2013](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx) <br/> |Aprenda a escribir código para ejecutar operaciones básicas con el modelo de objetos de cliente de SharePoint 2013.  <br/> |
| [Cómo usar la biblioteca de códigos de cliente para obtener acceso a datos externos en SharePoint 2013](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |Aprenda a usar el modelo de objetos de cliente de SharePoint 2013 para que funcione con objetos de BCS de SharePoint mediante scripts basados en el explorador.  <br/> |
   
A continuación se ofrecen algunos ejemplos básicos de tareas que se pueden realizar con CSOM.
  
    
    

### Obtener una entidad específica

En este ejemplo se muestra cómo obtener contexto de SharePoint y luego recuperar una entidad de origen de datos dada.
  
    
    

```cs

ClientContext ctx = new ClientContext("http://sharepointservername"); 
Web web = ctx.Web; 
ctx.Load(web); 
Entity entity = ctx.Web.GetEntity("http://sharepointservername", "EntityName"); 
ctx.Load(entity); 
ctx.ExecuteQuery(); 

```


### Crear un invocador genérico

En este ejemplo se muestra cómo escribir un invocador genérico para poder crear un objeto de entidad para trabajar en el código.
  
    
    

```cs

ObjectCollection myObj; 
entity.Execute("MethodInstanceName", lsi, myObj); 
ctx.Load(myObj); 
ctx.ExecuteQuery(); 

```


### Recuperar conjuntos de resultados paginados

En el siguiente ejemplo se muestra cómo recuperar un conjunto de datos filtrado paginado. En este caso, el valor de página es 50.
  
    
    

```cs

// Find filters for given Method Name. 
FilterCollection fCollection = entity.GetFilters("methodName"); 
ctx.Load(fCollection); 
ctx.ExecuteQuery(); 
FilterCollection modifiedFCollection = new FilterCollection(); 
foreach( Filter filter in fCollection) 
{ 
    if( filter.FilterField.equals("X.Y.Z.Country")) 
    { 
        filter.FilterValue = "India"; 
        modifiedFCollection.Add(Filter); 
    } 
    if(filter.FilterType == FilterType.Limit) 
    { 
        filter.FilterValue = 50; 
        modifiedFCollection.Add(Filter); 
    } 
} 
EntityInstanceCollection eCollection = entity.FindFiltered(modifiedFCollection, 
"nameOfFinder", lsi); 
ctx.ExecuteQuery(); 

```


### Consultar información filtrada

En el ejemplo siguiente se muestra cómo devolver un conjunto de resultados filtrados. En este caso, la columna de datos filtrada es el campo **X.Y.Z.Country**. El código busca algo con el valor "India" y luego lo coloca en una colección.
  
    
    

```cs

// Find filters for given Method Name. 
FilterCollection fCollection = entity.GetFilters("methodName"); 
ctx.Load(fCollection); 
ctx.ExecuteQuery(); 
FilterCollection modifiedFCollection = new FilterCollection(); 
foreach( Filter filter in fCollection) 
{ 
    if( filter.FilterField.equals("X.Y.Z.Country")) 
    { 
        filter.FilterValue = "India"; 
        modifiedFCollection.Add(Filter); 
    } 
} 
EntityInstanceCollection eCollection = entity.FindFiltered(modifiedFCollection, 
"nameOfFinder", lsi); 
ctx.ExecuteQuery(); 

```


## Más allá de los aspectos básicos: Obtenga más información sobre el modelo de objetos de cliente
<a name="BCScsom_Learnmore"> </a>

Para obtener más información sobre el uso del modelo de objetos de cliente de SharePoint 2013, consulte la información de la tabla 3.
  
    
    

**Tabla 3. Conceptos avanzados del modelo de objetos de cliente**


|**Artículo**|**Descripción**|
|:-----|:-----|
| [Referencia al modelo de objetos del cliente BCS para SharePoint 2013](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |Resume los objetos disponibles para crear scripts de cliente con el modelo de objetos de cliente de SharePoint 2013 para acceder a los datos externos expuestos por BCS.  <br/> |
   

## Recursos adicionales
<a name="BCScsom_Learnmore"> </a>


-  [Servicios de conectividad empresarial de SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Complementos de SharePoint](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [Cómo usar la biblioteca de códigos de cliente para obtener acceso a datos externos en SharePoint 2013](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md)
    
  
-  [Realizar operaciones básicas con código de biblioteca de cliente de SharePoint 2013](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [SharePoint 2013: Access complex external content types with CSOM (SharePoint 2013: acceder a tipos de contenido externo complejos con CSOM)](http://code.msdn.microsoft.com/SharePoint-2013-Accessing-ccbc24cf)
    
  
