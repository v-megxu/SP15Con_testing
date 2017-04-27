---
title: Uso de orígenes OData con Servicios de conectividad empresarial en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7a87e5bf-4428-4055-b113-7665a93e7326
---


# Uso de orígenes OData con Servicios de conectividad empresarial en SharePoint 2013
Obtenga información sobre cómo crear tipos de contenido externo basados en orígenes OData y usar esos datos en componentes de SharePoint 2013 o Office 2013.
## OData y el conector OData
<a name="SP15getstartedOdata_whatisodata"> </a>

El protocolo Open Data (OData) le permite tener acceso a un origen de datos, como una base de datos a través de una dirección URL construida especialmente. Esto permite un enfoque simplificado para conectarse y trabajar con orígenes de datos hospedados en una organización. 
  
    
    
OData es un protocolo que usa HTTP, Atom y Notación de objetos de JavaScript (JSON) que permiten a los desarrolladores escribir aplicaciones que se comunican con un número creciente de orígenes de datos. Microsoft admite la creación de este estándar como una forma de habilitar el intercambio de datos entre las aplicaciones y los almacenes de datos accesibles desde la web.
  
    
    
El nuevo conector OData permite a SharePoint comunicarse con los proveedores de OData.
  
    
    
En SharePoint 2013, Servicios de conectividad empresarial (BCS) puede comunicarse con productores u orígenes OData, sin tener que codificar directamente al origen OData. Los productores exponen los datos de una forma estructurada a través de un servicio web. Algunos productores pueden permitir la actualización de datos subyacentes y otros pueden permitir acceso de solo lectura. Para publicar las operaciones que están disponibles, el productor tiene un documento de servicio que se encuentra en un extremo de la dirección URL especificada. SharePoint ya está un productor de OData. Los datos de la lista de SharePoint se exponen como un origen de OData para cualquier usuario que tenga derechos adecuados.
  
    
    

### Ejemplos de productores de OData
<a name="ExamplesOfODataProducers"> </a>

Los siguientes son algunos ejemplos de implementaciones de OData. Estas aplicaciones y servicios exponen sus datos mediante el protocolo OData.
  
    
    

- SharePoint Foundation 2010
    
  
- SharePoint Server 2010
    
  
- SQL Azure
    
  
- Microsoft AzureAlmacenamiento de tablas
    
  
- Microsoft AzureCatálogo de soluciones
    
  
-  SQL Server Reporting Services
    
  
- Microsoft Dynamics CRM 2011
    
  
- Windows Live
    
  
Para obtener una lista de los productores de servicios OData, consulte el  [sitio web de Open Data Protocol](http://www.odata.org/ecosystem).
  
    
    

## Requisitos previos para trabajar con el conector OData de BCS
<a name="SP15GetstartedOdata_prereq"> </a>

Para desarrollar tipos de contenido externo basado en OData, necesitará lo siguiente:
  
    
    

- Visual Studio 2012
    
  
- SharePoint 2013
    
  
- Office Developer Tools para Visual Studio 2012
    
  
Para obtener información sobre cómo configurar el entorno de desarrollo, consulte  [Configurar un entorno de desarrollo general para SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

## Creación de tipos de contenido externo para orígenes de datos OData
<a name="SP15GetstartedOdata_creatingECT"> </a>

Para que SharePoint use los datos expuestos por un productor de OData específico, debe crearse un tipo de contenido externo dentro de SharePoint. Como con todos tipos de contenido externo de SharePoint, contiene toda la información de conexión necesaria para conectarse y comunicarse con el sistema externo.
  
    
    
Crear un tipo de contenido externo que utiliza un origen de datos OData es similar a crear cualquier tipo de contenido externo. Puede usar Visual Studio 2012 para generar automáticamente los tipos de contenido externo de OData. Simplemente, proporcione el extremo de Representational State Transfer (REST) de la fuente OData al crear el tipo de contenido externo. Para obtener más información, consulte  [Cómo crear un tipo de contenido externo desde un origen de OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md).
  
    
    

## En esta sección
<a name="SP15GetstartedOdata_inthissect"> </a>


-  [Cómo crear un tipo de contenido externo desde un origen de OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Procedimientos: Crear un servicio de datos OData para su uso como un sistema externo de BCS](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md)
    
  
-  [Cómo: Crear una lista externa con un origen de datos de OData en SharePoint 2013](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md)
    
  

## Recursos adicionales
<a name="SP15GetstartedOdata_addres"> </a>


-  [Servicios de conectividad empresarial de SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Tipos de contenido externo en SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [Novedades en Servicios de conectividad empresarial en SharePoint 2013](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Referencia a los programadores de Servicios de conectividad empresarial para SharePoint 2013](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  

