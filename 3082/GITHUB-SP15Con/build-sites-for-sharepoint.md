---
title: Crear sitios para SharePoint
ms.prod: SHAREPOINT
ms.assetid: 3b372a63-7cdf-462a-abb4-750e611e967d
---


# Crear sitios para SharePoint
Conozca el nuevo modelo de creación y publicación de sitios para sitios web en SharePoint 2013.
## Introducción a la publicación de sitios para diseñadores y desarrolladores en SharePoint
<a name="SP15_BuildSitesForSP2013_IntroToSitePublishing"> </a>

SharePoint 2013 presenta un modelo de creación y publicación de sitios para crear sitios de publicación. Puede usar sitios de publicación para publicar contenido en sitios de Internet o intranet. Los sitios de publicación se diferencian de otros tipos de sitios de SharePoint, como los sitios de equipos, principalmente en su propósito; muchos usuarios leen contenido del sitio de publicación, pero solo unos pocos contribuyen agregando, actualizando y eliminando contenido de una o varias colecciones de sitios. Estos sitios contrastan con los de equipos, donde muchos usuarios pueden colaborar y contribuir al contenido.
  
    
    
Puede usar las funciones de publicación de sitios de SharePoint 2013 para crear, personalizar y mantener sitios de publicación que cubran las necesidades específicas de la empresa. Si es un diseñador profesional con HTML, CSS y conoce JavaScript o es un desarrollador que escribe aplicaciones de SharePoint y usa código .NET personalizado para crear sitios y soluciones de granja, puede utilizar las características de sitios en SharePoint 2013 para administrar todas las fases del ciclo de vida del contenido, lo que incluye:
  
    
    

- **Authoring** y la reutilización de contenido del sitio.
    
  
- **Branding** y el diseño de la apariencia y el comportamiento de su sitio.
    
  
- **Managing metadata**: puede construir un sistema de navegación del sitio orientado a la taxonomía.
    
  
- **Publishing** fácil de contenidos en la colección de sitios actual o publicación de contenidos a través de colecciones de sitios, abarcando incluso la intranet y el límite del sitio de Internet.
    
  
- **Accessibility**: puede usarlo para mejorar la accesibilidad de los sitios publicados.
    
  
Si quiere ver un resumen de las novedades de la publicación de sitios web en SharePoint 2013 para diseñadores y desarrolladores, consulte  [Novedades sobre el desarrollo de sitios de SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md).
  
    
    

## Creación, diseño y personalización de marca en SharePoint
<a name="SP15_BuildSitesForSP2013_AuthoringDesignBranding"> </a>

SharePoint 2013 ofrece un nuevo enfoque para el diseño de sitios web. Se ha revisado el flujo de trabajo de creación de contenido para que pueda crear contenido excepcional con cualquier herramienta de creación y personalización de marca. Para personalizar la marca de su sitio sin necesidad de escribir código .NET personalizado, use el  [Administrador de diseño](overview-of-design-manager-in-sharepoint-2013.md) para importar los elementos de diseño. Con el Administrador de diseño, también puede crear una página maestra basada en HTML para definir el cromo que comparten todas las páginas de su sitio y crear diseños de página para diseñar plantillas para las páginas. Si decide escribir código personalizado, puede usar las bibliotecas de servidor .NET, cliente .NET (CSOM), Silverlight y JavaScript.
  
    
    
SharePoint 2013 también ofrece un nuevo enfoque para el contenido y para la creación del mismo. Se ha revisado el flujo de trabajo de creación de contenido para que pueda crear contenido excepcional con cualquier herramienta de creación y personalización de marca. Para personalizar la marca de su sitio sin necesidad de escribir código .NET personalizado, use el Administrador de diseño. Puede importar elementos de diseño y crear una página maestra basada en HTML para definir los elementos de enmarcado (el cromo) que comparten todas las páginas y diseños de página de su sitio. Si decide escribir código personalizado para personalizar la marca de su sitio, puede usar las bibliotecas de publicación y taxonomía.
  
    
    

## Publicación de sitios, programación del modelo de objetos de cliente y el nuevo modelo de aplicación de SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingSites"> </a>

Puede usar el nuevo modelo de objetos de cliente .NET (CSOM) para desarrollar aplicaciones SharePoint con modelo para aplicaciones para SharePoint. Puede usar muchas de las API que también están disponibles para la programación de servidor .NET en los modelos de objetos de cliente .NET compatibles con el desarrollo del cliente .NET, Silverlight, JavaScript y, en algunos casos Windows Phone. Algunas ideas para desarrollar aplicaciones para sitios web incluyen encuestas, aplicaciones de administración de cuentas, compatibilidad con comercio electrónico, integración de funciones sociales y datos externos en sitios web de publicación, subcontratación de contenidos adiciones y aplicaciones empresariales móviles.
  
    
    

## Modelo de páginas de sitios web de publicación
<a name="SP15_BuildSitesForSP2013_PageModel"> </a>

SharePoint 2013 incluye un modelo de páginas para sitios web de publicación. El modelo de páginas incluye páginas maestras, diseños de página y otros componentes que representan la estructura del sitio, el contenido, la apariencia y el comportamiento. Para más información, consulte  [Información general sobre el modelo de páginas de SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Páginas maestras y diseños de página
<a name="SP15_BuildSitesForSP2013_MasterAndLayout"> </a>

Una página maestra es la plantilla principal que define los elementos estructurales comunes del sitio: el cromo. Todas las páginas del sitio comparten estos elementos, que definen las regiones de la página que muestran el contenido del diseño de página.
  
    
    
Las páginas individuales de un determinado tipo usan diseños de página. Se rellenan con las disposiciones de los campos de la página. Estas páginas definen elementos individuales de la página. Las páginas individuales se basan en diseños de página y se crean en el explorador web mediante código personalizado o según rellenen los campos de la página los usuarios del sitio. Para más información sobre el modelo de páginas en SharePoint 2013, consulte  [Información general sobre el modelo de páginas de SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Controles de representación de cliente
<a name="SP15_BuildSitesForSP2013_ClientSideRendering"> </a>

Todos los nuevos controles en SharePoint 2013 están representados. Los datos se escriben en los controles en una matriz JSON del lado cliente y pueden mostrar contenido con JavaScript, CSS y plantillas. Como desarrollador o diseñador, tiene control sobre cómo se representa el contenido de la página y puede usar varias técnicas de diseño para conseguir la apariencia y los comportamientos que desea en sus páginas publicadas con características como el  [Elemento web de búsqueda de contenido en SharePoint 2013](content-search-web-part-in-sharepoint-2013.md) y las plantillas de visualización.
  
    
    

## Sitios y dispositivos móviles
<a name="SP15_BuildSitesForSP2013_SitesAndMobile"> </a>

Los sitios web de publicación en SharePoint 2013 están optimizados para desarrollo móvil. Puede definir canales para uno o más dispositivos (canales de dispositivo) y asignar una página maestra alternativa para cada canal, dándole elementos estructurales únicos o cromo. Puede optar por incluir o excluir partes de cualquier diseño de página en un canal y realizar una vista previa de cómo progresa el diseño del canal móvil mientras se está desarrollando.
  
    
    

## Metadatos y navegación en SharePoint
<a name="SP15_BuildSitesForSP2013_MetadataNav"> </a>

Las funciones de metadatos administrados presentadas en Microsoft SharePoint Server 2010 se mejoran y amplían en SharePoint 2013 para conseguir mejor rendimiento, acceso más fácil a través de la interfaz de usuario y navegación basada en la taxonomía, denominada navegación administrada. Puede usar la navegación administrada o la navegación basada en la estructura del sitio web de SharePoint, denominada navegación estructurada, para crear la navegación de su sitio. Para más información, consulte  [Navegación y metadatos administrados en SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md) and [Navegación administrada en SharePoint 2013](managed-navigation-in-sharepoint-2013.md).
  
    
    

## Publicar contenido en SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingContent"> </a>

SharePoint 2013 ofrece las siguientes características de publicación de contenido nuevas que permiten desarrollar sitios de publicación y que admiten escenarios y topologías más flexibles, accesibles y complejas.
  
    
    

### Catálogos

SharePoint 2013 presenta catálogos, que puede usar para publicar contenido a través de colecciones de sitios. Las funciones de publicación entre sitios dependen de los catálogos. Puede usarlos para reutilizar el contenido a través de sus sitios y a través del límite entre sitios de intranet y sitios de Internet. Para consultas de búsquedas predefinidas, los catálogos se marcan en la búsqueda. Puede examinar superficialmente el contenido almacenado en los catálogos a través de colecciones de sitios con  [Elemento web de búsqueda de contenido en SharePoint 2013](content-search-web-part-in-sharepoint-2013.md).
  
    
    

### Publicación entre sitios

SharePoint 2013 incorpora una característica de publicación entre sitios que le permite reutilizar el contenido entre varias colecciones de sitios. Usa funcionalidades de búsqueda integradas para habilitar arquitecturas y escenarios de publicación. Por primera vez, puede diseñar sitios para trabajar con varias granjas de servidores de SharePoint; esto permite que los sitios traspasen el límite entre intranets e Internet. Puede usar CSWP para mostrar los datos de búsqueda publicados en varios sitios y colecciones de sitios.
  
    
    

### Variaciones y sitios en varios idiomas

Puede usar la característica de variaciones que hay en SharePoint 2013 para crear sitios en varios idiomas u otros sitios donde quiera modificar la presentación del contenido. La característica de variaciones está limitada a una colección de sitios. O sea, puede crear "variantes" de idioma o configuración regional de destino de un idioma o una configuración regional de origen como sitios web actuales dentro de la misma colección de sitios de SharePoint. Las variaciones admiten direcciones URL descriptivas y la capacidad de exportar o importar contenido para la traducción por parte de terceros en  [formato de archivo XLIFF](the-xliff-interchange-file-format-in-sharepoint-2013.md). Puede incluir etiquetas, una página para traducción y replicación, una variedad de elementos de lista (por ejemplo, bibliotecas de documentos) y navegación en sus paquetes de exportación.
  
    
    

### Sitios accesibles

Puede usar la característica de variaciones en SharePoint 2013 para crear sitios accesibles u otros sitios cuya presentación del contenido quiera adaptar para los usuarios que tengan ciertas necesidades de accesibilidad. SharePoint 2013 proporciona un "Modo más accesible", que puede activarse abriendo una página web de SharePoint y presionando la tecla TAB hasta que encuentre el vínculo "Activar modo más accesible". Esta característica permite volver a crear la página web en HTML estándar para que sea más descriptiva para los lectores de pantalla. Al asegurarse de que los usuarios puedan presionar la tecla TAB para centrarse en este vínculo, puede crear una versión más accesible de la página web de SharePoint. Esto incluye menús desplegables basados en JavaScript que se convierten en listas de hipervínculos, y los objetos se convierten en HTML más sencillo para permitir que los lectores de pantalla entiendan el contenido. 
  
    
    

## Recursos adicionales
<a name="SP15_BuildSitesForSP2013_AdditionalResources"> </a>


-  [Optimizar la accesibilidad de sitio de SharePoint](optimize-sharepoint-site-accessibility.md)
    
  
-  [Configurar un entorno de desarrollo general para SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md)
    
  
-  [Novedades sobre el desarrollo de sitios de SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [Información general de estrategia de descarga mínima](minimal-download-strategy-overview.md)
    
  
-  [Modificar los componentes de SharePoint para MDS](modify-sharepoint-components-for-mds.md)
    
  
-  [Biblioteca de clases de servidor de sitios y contenido de SharePoint 2013](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)
    
  
-  [Biblioteca de clases de cliente de sitios y contenido](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx)
    
  

