---
title: Tipos de contenido externo en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 11d7adb5-5388-4517-ae03-beb7be1c6981
---


# Tipos de contenido externo en SharePoint 2013
Aprenda lo que puede hacer con tipos de contenido externo y lo que necesita para comenzar a crearlos en SharePoint 2013.
## ¿Qué es un tipo de contenido externo?
<a name="SP15ectoverview_what"> </a>

El tipo de contenido externo es un concepto básico de Servicios de conectividad empresarial (BCS). Usados en la funcionalidad y los servicios que ofrece BCS, los tipos de contenido externo son descripciones de metadatos reutilizables de información de conectividad y definiciones de datos además de los comportamientos que se desea aplicar a cierta categoría de datos externos.
  
    
    
Los tipos de contenido externo permiten administrar y volver a usar los metadatos y comportamientos de una entidad de negocio como cliente o pedido desde un punto central, y permiten que los usuarios interactúen con esos datos externos y procesos de forma más significativa.
  
    
    
Las siguientes son algunas ventajas de usar tipos de contenido externo:
  
    
    

- **Proporciona reutilización:** un tipo de contenido externo es una definición de datos reutilizables de una entidad empresarial. Una vez creado el tipo de contenido, puede usarlo con cualquiera de las características de presentación de BCS con el fin de proporcionar una experiencia de usuario enriquecida para interactuar con datos externos.
    
  
- **Inclusión de elementos complejos de los sistemas externos:** los tipos de contenido externo permiten a los trabajadores de información ensamblar soluciones empresariales sin tener que controlar la complejidad de los sistemas externos como la información sobre conectividad y las interfaces de programación. Después de que alguien crea un tipo de contenido externo, este queda a disposición de todos los usuarios para que lo usen de la forma que necesiten (siempre y cuando tengan los permisos para realizar dicha operación y obtener acceso a los datos externos). Sin embargo, el usuario no necesita saber nada acerca de la ubicación de los datos externos o la forma de conectarse a ellos.
    
  
- **Comportamiento integrado de Office y SharePoint:** los tipos de contenido externo proporcionan a los servicios y los datos externos comportamientos de tipo de elemento de Office (por ejemplo, contactos, tareas y calendarios en Outlook, documentos en Word y listas en SharePoint Workspace); comportamientos de SharePoint (como listas, elementos web y páginas de perfil) y las capacidades (como la capacidad de buscar o trabajar sin conexión) a los datos y los servicios externos, de modo que los usuarios pueden trabajar en los entornos de trabajo habituales sin tener que buscar arduamente los datos o tener que aprender a utilizar distintas interfaces de usuario (y de propietario) e interactuar con las mismas.
    
  
- **Ayuda para proporcionar acceso más seguro:** los tipos de contenido externo cumplen con la seguridad que imponen tanto el sistema externo y SharePoint. Al configurar la seguridad en SharePoint, tendrá control absoluto sobre los usuarios que obtienen acceso a los datos.
    
  
- **Mantenimiento simplificado:** como los tipos de contenido externo se pueden crear una vez y usar con varias soluciones en diversos escenarios, se pueden administrar fácilmente. Por ejemplo, puede administrar los permisos de acceso, así como la conexión y las definiciones de datos, en una ubicación central.
    
  
- **Posibilidad de búsqueda de datos externos:** puede usar la Búsqueda en SharePoint Server desde un portal de intranet para buscar información acerca de un tipo de contenido externo específico, como Cliente. La Búsqueda en SharePoint Server obtiene los datos directamente desde el sistema externo. Por lo tanto, los usuarios pueden obtener la información que necesitan sin la necesidad de contar con una aprobación o instalar una aplicación aparte.
    
  
- **Posibilidad de trabajar sin conexión:** es posible poner tipos de contenido externo sin conexión en Outlook 2013. Servicios de conectividad empresarial (BCS) proporciona características de trabajo sin conexión y memoria caché enriquecidas, y es compatible con operaciones basadas en caché. Los usuarios pueden manipular los datos externos de forma eficaz y sin problemas, incluso cuando trabajan sin conexión o cuando la conectividad con el servidor es lenta, intermitente o no está disponible. Las operaciones de lectura y escritura realizadas en las entidades empresariales en caché se sincronizan cuando se restablecerá la conexión con el servidor.
    
  

## Requisitos previos para trabajar con tipos de contenido externo de BCS
<a name="SP15ectoverview_prereq"> </a>

Para empezar a crear tipos de contenido externo, necesitará lo siguiente:
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools para Visual Studio 2012
    
    o
    
  
- SharePoint Designer 2013
    
  
Para configurar un entorno de desarrollo para crear tipos de contenido externo, consulte  [Configurar un entorno de desarrollo general para SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

## ¿Qué puede hacer con tipos de contenido externo?
<a name="SP15ectoverview_whattodo"> </a>

Cuando SharePoint está configurado para comunicarse con el sistema externo, puede usar los tipos de contenido externo para crear los siguientes objetos con el fin de presentar los datos subyacentes:
  
    
    

- **Listas externas**
    
    Una lista externa permite el acceso a los datos desde sistemas externos de la misma forma en que se obtiene acceso a los datos de la lista de SharePoint. Las listas externas usan tipos de contenido externo como orígenes de datos. Las listas externas permiten usar los metadatos que ya están definidos acerca de un tipo de contenido externo a fin de crear una lista de SharePoint con datos externos que tengan el mismo aspecto y rendimiento que cualquier otra lista de SharePoint.
    
    También puede usar listas externas sin conexión en Outlook 2013. Esto permite trabajar con datos externos, al igual que los tipos de elementos nativos de Outlook, como contactos, tareas y elementos para exponer, y usar los datos externos en aplicaciones cliente de Office.
    
    Las listas externas habilitan la reescritura en el sistema externo si este lo permite y si está modelado según corresponde mediante el tipo de contenido externo. Esto implica que los usuarios pueden modificar datos externos directamente desde dentro. Todos los cambios realizados en los elementos de la lista se sincronizan automáticamente con el sistema externo. Además, al usar el botón **Actualizar datos** de la lista, se pueden sincronizar y obtener datos actualizados del sistema externo de forma automática.
    
  
- **Columnas de datos externos**
    
    La columna de datos externos permite a los usuarios agregar datos de tipos de contenido externo a las listas de SharePoint estándar. Al igual que una lista externa, la columna de datos externos puede mostrar datos de cualquier tipo de contenido externo que se haya modelado en Servicios de conectividad empresarial (BCS).
    
  
- **Elementos web de datos empresariales**
    
    SharePoint 2013 proporciona cinco elementos web diferentes para trabajar con datos externos: lista de datos empresariales, elemento de datos empresariales, generador de elementos de datos empresariales, lista relacionada con datos empresariales y acciones de datos empresariales.
    
  
- **Selector de tipo de contenido externo**
    
    Un selector de tipo de contenido externo reporta al usuario funciones de selección y resolución. Este selector se puede insertar en un formulario o página en escenarios donde un usuario debe poder elegir un tipo de contenido externo de la lista de tipos de contenido externo disponibles. 
    
  
- **Selector de elementos externos**
    
    Un selector de elementos externos proporciona funciones de selección y resolución para los elementos externos en el servidor y en aplicaciones de Office de cliente enriquecido. Este selector se puede insertar en un formulario o página en escenarios donde un usuario debe poder elegir un elemento externo, como un cliente de una lista de clientes. 
    
  
- **Páginas de perfil**
    
    Las páginas de perfil son páginas de SharePoint disponibles en SharePoint 2013 que muestran los detalles acerca de un elemento externo. Al igual que cualquier otra página de Página de elementos web de SharePoint, puede personalizarla para mostrar los detalles de un elemento externo.
    
  
- **Aplicaciones y páginas personalizadas**
    
    Puede usar las opciones de programación de SharePoint 2013, como el modelo de objetos de SharePoint, el modelo de objetos de cliente y las direcciones URL de transferencia de estado representacional (REST).
    
  
La tabla 1 contiene ejemplos de tareas que ilustran el trabajo con tipos de contenido externo.
  
    
    

**Tabla 1. Tareas básicas para trabajar con tipos de contenido externo**


|**Tarea**|**Descripción**|
|:-----|:-----|
| [Cómo crear un tipo de contenido externo desde un origen de OData en SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |Aprenda a usar Visual Studio 2012 para descubrir un origen OData publicado y crear un tipo de contenido externo reutilizable para usarlo en SharePoint 2013 Servicios de conectividad empresarial (BCS).  <br/> |
| [Cómo: Crear tipos de contenido externo para SQL Server en SharePoint 2013](how-to-create-external-content-types-for-sql-server-in-sharepoint-2013.md) <br/> |Obtenga información sobre cómo crear un tipo de contenido externo basado en una base de datos de SQL Server.  <br/> |
   

## Recursos adicionales
<a name="SP15ectoverview_addres"> </a>


-  [Servicios de conectividad empresarial de SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Cómo: crear un tipo de contenido externo agregar en el ámbito en SharePoint 2013](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [Cómo: Crear tipos de contenido externo para SQL Server en SharePoint 2013](how-to-create-external-content-types-for-sql-server-in-sharepoint-2013.md)
    
  
-  [Introducción a los Servicios de conectividad empresarial en SharePoint 2013](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Novedades en Servicios de conectividad empresarial en SharePoint 2013](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  

