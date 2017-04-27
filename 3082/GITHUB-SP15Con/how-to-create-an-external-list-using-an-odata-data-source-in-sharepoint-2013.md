---
title: Cómo Crear una lista externa con un origen de datos de OData en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 601fbfce-a0c6-43dd-8398-540d094c083c
---


# Cómo: Crear una lista externa con un origen de datos de OData en SharePoint 2013
Obtenga información sobre cómo crear una lista externa mediante programación y enlazar a un tipo contenido externo basado en OData en SharePoint 2013.
Aunque un usuario avanzado o un administrador de SharePoint probablemente creará una lista externa con SharePoint Designer 2013, un desarrollador estará interesado en la capacidad de crear listas externas con las herramientas de su profesión, Visual Studio 2012 y Office Developer Tools para Visual Studio 2012. Esto les ofrece más flexibilidad para agregar funcionalidad y empaquetar una solución que incluya las características Servicios de conectividad empresarial (BCS) para una implementación posterior en uno o varios entornos de host.
  
    
    


## Requisitos previos para crear una lista externa
<a name="bkmk_Prereqs"> </a>

Para crear una lista externa desde un origen de OData se necesitan los siguientes componentes:
  
    
    

- Visual Studio 2012
    
  
- SharePoint 2013
    
  
- Office Developer Tools para Visual Studio 2012
    
  
- Un tipo de contenido externo publicado basado en un origen de OData: para obtener instrucciones, consulte  [Cómo crear un tipo de contenido externo desde un origen de OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md).
    
  
Para obtener información sobre cómo configurar un entorno de desarrollo de SharePoint, consulte  [Configurar un entorno de desarrollo general para SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

### Conceptos básicos para crear listas externas

En los siguientes artículos se proporciona información sobre Complementos de SharePoint y otra información detallada para crear listas externas.
  
    
    

**Tabla 1. Conceptos básicos para listas externas**


|**Título del artículo**|**Descripción**|
|:-----|:-----|
| [Introducción a los Servicios de conectividad empresarial en SharePoint 2013](get-started-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |Obtener información sobre servicios de conectividad empresarial y cómo exponer datos externos en SharePoint 2013.  <br/> |
| [Complementos de SharePoint](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |Obtener información sobre el nuevo modelo de aplicaciones de SharePoint 2013 que permite crear aplicaciones que son soluciones pequeñas y fáciles de usar para usuarios finales.  <br/> |
| [Elegir patrones para desarrollar y hospedar un complemento para SharePoint](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx) <br/> |Información sobre las diferentes maneras en las que puede hospedar Complementos de SharePoint.  <br/> |
   

## Crear una nueva lista externa
<a name="bkmk_CreateNewVList"> </a>

Los procedimientos siguientes mostrarán cómo crear una nueva lista externa, enlazarla a un tipo de contenido externo basado en OData y publicarla en SharePoint 2013 con Visual Studio 2012.
  
    
    

> **NOTA**
> En el primer paso se supone que ha creado correctamente un tipo de contenido externo, como se describe en  [Cómo crear un tipo de contenido externo desde un origen de OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md). 
  
    
    


### Para agregar automáticamente una lista externa


1. Si desea agregar una lista simple a un proyecto que refleje lo que está en el tipo de contenido externo, puede usar las herramientas de generación automática de Visual Studio 2012. La lista se crea cuando al crear el tipo de contenido externo. Cuando se activa la casilla instancias **Cree instancias de lista para las entidades de datos seleccionadas (excepto Operaciones de servicio)** que se encuentra en el segundo paso del proceso de generación automática (paso Seleccionar las entidades de datos), el asistente creará las declaraciones XML y agregará nuevos tipos de contenido externos para cada entidad seleccionada.
    
  
2. Presione F5 para implementar el proyecto y la nueva lista también se habrá implementado.
    
  
Para realizar pruebas, es posible que quiera modificar el archivo AppManifest.xml para que la página de inicio de la aplicación sea la lista que acaba de crear. 
  
    
    

### Para modificar el archivo AppManifest.xml


1. Abra el archivo AppManifest.xml con un editor XML.
    
  
2. Busque la etiqueta <StartPage>.
    
  
3. Cambie el valor a  `~appWebUrl/Lists/Employees`.
    
  
4. Guarde los cambios.
    
  

### Para publicar el proyecto


- Presione F5 para implementar el proyecto y la lista externa. 
    
    Abra un explorador web y vaya a la nueva lista que ha creado.
    
  

## Recursos adicionales
<a name="bkmk_AdditionalResources"> </a>


-  [Servicios de conectividad empresarial de SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Uso de orígenes OData con Servicios de conectividad empresarial en SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Cómo crear un tipo de contenido externo desde un origen de OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Procedimiento para crear una aplicación básica autohospedada en SharePoint](http://msdn.microsoft.com/library/0572894d-c437-4b7d-8ac6-8405496e2145%28Office.15%29.aspx)
    
  
-  [Uso de orígenes OData con Servicios de conectividad empresarial en SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

