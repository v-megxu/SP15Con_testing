---
title: Novedades sobre el desarrollo de sitios de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ac1e9891-5ce9-4707-84e5-6e2fc02fda6b
---


# Novedades sobre el desarrollo de sitios de SharePoint 2013
Conozca el nuevo modelo de creación y publicación de sitios de SharePoint 2013 que permite crear sitios de publicación.
## Introducción a la publicación de sitios para diseñadores y desarrolladores en SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_IntroductionToSitePublishing"> </a>

Las siguientes características son nuevas en SharePoint 2013 y admiten el flujo de trabajo de creación de sitios de administración de contenido empresarial (ECM) para los sitios de publicación.
  
    
    

### Modelos de programación de clientes para el desarrollo de sitios de publicación

En SharePoint 2013, puede usar el modelo de objetos de cliente (CSOM) .NET, Silverlight y los modelos de programación de JavaScript para desarrollar sitios, componentes de sitios, elementos de personalización de marca, y comportamientos personalizados. La mayoría de las API disponibles para la programación de servidores .NET se encuentran disponibles en el cliente (CSOM) .NET correspondiente, Silverlight y ensamblados de JavaScript. En algunos casos, las API correspondientes también se encuentran disponibles en bibliotecas de Windows Phone.
  
    
    
Para más información, vea las páginas de inicio de referencia sobre sitios y contenido para  [el servidor .NET](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx),  [el cliente .NET](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx) y [JavaScript](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx). También puede empezar con la  [página de inicio de referencia](http://msdn.microsoft.com/library/7940ba4e-f6f0-4bc0-b995-ceb2d358ca0d%28Office.15%29.aspx) si quiere empezar en la parte superior y después explorar el contenido de cada modelo de programación.
  
    
    

### Usar las API de publicación y taxonomía con el nuevo modelo de aplicación de SharePoint

Puede escribir código personalizado de cliente y servidor en Complementos de SharePoint para ampliar las funciones de publicación y taxonomía de SharePoint que están disponibles para usuarios en la interfaz de usuario (UI). 
  
    
    
Estas son algunas ideas para desarrollar aplicaciones que mejoran la publicación de sitios: encuestas, aplicaciones de gestión de cuentas, compatibilidad con comercio electrónico, aplicaciones que integran características sociales y datos externos en sitios de publicación, adiciones de contenido subcontratado a sus sitios y aplicaciones móviles complementarias.
  
    
    

## Características de creación, diseño y personalización de marca
<a name="SP15_WhatsNewSiteDevelopment_AuthoringAndBranding"> </a>

SharePoint 2013 incluye características y API que sirven para crear, diseñar y personalizar la marca, así como para ampliar el sitio, su diseño, los comportamientos y los elementos de personalización. 
  
    
    

### Administrador de diseño

En versiones anteriores de SharePoint, la personalización de marca de un sitio requería ciertos conocimientos técnicos sobre cuestiones como qué marcadores de posición de contenido se necesitan en una página maestra o cómo una página maestra implementa ciertas clases de estilos. SharePoint 2013 introduce el  [Administrador de diseño](overview-of-design-manager-in-sharepoint-2013.md), una nueva interfaz y concentrador central para administrar todos los aspectos de personalización de marca de su sitio de SharePoint. Puede encontrar el Administrador de diseño en el sitio de nivel superior de su colección de sitios. Forma parte de la plantilla de colección de sitios del Portal de publicación de SharePoint 2013.
  
    
    
El Administrador de diseño permite un enfoque paso a paso para crear activos de diseño que puede usar para personalizar la marca de los sitios. Suba activos de diseño (imágenes, HTML, CSS, etc.) y después cree las páginas maestras y los diseños de páginas. Puede obtener una vista previa de cómo aparece su diseño en un editor de código del lado cliente o en el servidor cuando lo está diseñando. Puede agregar componentes personalizados de SharePoint y elementos de cinta con la interfaz de usuario del Administrador de diseño. El Administrador de diseño genera  [fragmentos de código](sharepoint-2013-design-manager-snippets.md) HTML que cualquier herramienta de diseño web puede usar (representa HTML e ignora el marcado de SharePoint y ASP.NET, mientras que SharePoint representa solamente el marcado de SharePoint y ASP.NET e ignora HTML).
  
    
    
Puede usar su experiencia en HTML, CSS y JavaScript para diseñar páginas maestras en HTML y crear diseños de páginas HTML en el editor HTML que quiera. Para conectar su herramienta favorita de creación y diseño a su sitio de SharePoint,  [asigne una unidad de red](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md) y después edite el archivo de SharePoint como si fuera un archivo local. Cuando esté listo el diseño del sitio, suba los archivos auxiliares y HTML, y use el Administrador de diseño para [convertir el archivo HTML en un archivo de página maestra (.master) ASP.NET](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md). Ahora  [aplique la página .master](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md) a su sitio de SharePoint. Use el Administrador de diseño para [crear un nuevo diseño de página](how-to-create-a-page-layout-in-sharepoint-2013.md): la versión HTML del archivo se asociará automáticamente con la página ASP.NET (archivo .aspx) correspondiente que SharePoint interpreta. 
  
    
    
Después de convertir los archivos HTML, puede usar el editor HTML para seguir perfeccionado el diseño, obtener una vista previa de los archivos y guardarlos. Cada vez que guarda las versiones HTML de los archivos de página maestra o de diseño de página, SharePoint 2013 actualiza automáticamente la página maestra y los diseños de página asociados de SharePoint para reflejar los cambios. 
  
    
    
Con el Administrador de diseño, solo tiene que editar los archivos HTML. Aunque puede seguir escribiendo páginas maestras y diseños de páginas personalizados con sus habilidades de desarrollo de SharePoint y ASP.NET, el Administrador de diseño le permite diseñar excelentes sitios sin tener experiencia de desarrollo en SharePoint.
  
    
    
Si lo prefiere, SharePoint 2013 también incluye versiones HTML de varias páginas maestras y diseños de páginas que puede usar como plantillas para empezar. Si quiere empezar a partir de estos archivos, cree una copia del archivo HTML (no tiene que preocuparse por el archivo ASP.NET asociado) y después edite el archivo HTML como siempre. También puede empezar usando una plantilla básica con la opción **página maestra a partir de plantilla mínima**, que crea automáticamente el archivo .master asociado.
  
    
    

### Galería de fragmentos

SharePoint 2013 contiene muchos componentes listos para usar, como elementos web y controles, que puede agregar a las páginas de su sitio. Por ejemplo, con la inserción de un componente de SharePoint como un cuadro de búsqueda o un control de navegación en su página maestra HTML, puede compilar rápida y fácilmente muchas funciones en sus páginas.
  
    
    
En el grupo **Galería de fragmentos** de la cinta, puede seleccionar un componente, configurar sus propiedades y actualizar el fragmento de código, copiar el fragmento HTML generado y pegarlo en su archivo HTML. El fragmento HTML le ofrece una vista previa de alta fidelidad de dicho componente, tanto en la vista previa del lado servidor como en el editor HTML que elija. Después de agregar componentes de SharePoint a sus archivos HTML, puede usar CSS para personalizar completamente su marca. También, al igual que cualquier actualización en el archivo HTML, después de agregar componentes de SharePoint y personalizar la marca allí, los cambios se sincronizan automáticamente con la página maestra o el diseño de página asociados. Los fragmentos HTML se convierten automáticamente en componentes de SharePoint.
  
    
    
 Ya sea su archivo HTML una página maestra o un diseño de página, la Galería de fragmentos le muestra los componentes que necesita. Si no ve el fragmento que quiere, puede crear un fragmento HTML de marcado ASP.NET y agregarlo a su página maestra o diseño de página HTML.
  
    
    
El Administrador de diseño genera fragmentos HTML que cualquier herramienta de diseño web puede usar: solo representa HTML e ignora el marcado de SharePoint y ASP.NET. (SharePoint representa solamente el marcado de SharePoint y ASP.NET e ignora HTML).
  
    
    

### Canales de dispositivos

En el Administrador de diseño, se crean  [canales de dispositivos](sharepoint-2013-design-manager-device-channels.md) y después se asignan a dispositivos móviles o exploradores usando subcadenas de la cadena de agente del usuario de cada dispositivo de entrada. Un dispositivo puede pertenecer a varios canales, de modo que los canales se pueden clasificar. Por ejemplo, si crea canales de dispositivo para "teléfonos inteligentes" y "Windows Phone 8", puede clasificar los canales de modo que los dispositivos que usen Windows Phone 8 obtengan el canal específicamente asignado a ellos y que todos los demás teléfonos inteligentes obtengan contenido asociado con el canal de "teléfonos inteligentes".
  
    
    
Después de definir canales, asigne una página maestra a cada uno. Esta página maestra puede hacer referencia a un archivo CSS que no sea la página maestra para el canal predeterminado. Todos los diseños de página que cree funcionarán con todos los canales que cree; para diferenciar diseños de página entre canales, use el control **Panel de canales de dispositivos**.
  
    
    
Los sitios de publicación de SharePoint 2013 están optimizados para el desarrollo móvil. Puede usar la característica de canales de dispositivos para definir canales para un dispositivo o varios (esto le permite tener un control preciso sobre la manera en que los usuarios móviles experimentan el sitio). Puede asignar una página maestra alternativa a cada canal, lo que le da un cromo único. Puede elegir incluir o excluir porciones de cualquier diseño de página en un canal y obtener una vista previa de la manera en que progresa el diseño de canal móvil mientras se desarrolla. Los canales de dispositivos se diseñan pensando en la optimización de motor de búsqueda (SEO). Puede usarlos para transformar el aspecto de las páginas existentes y admitir escenarios móviles.
  
    
    
Puede usar canales para forzar que ciertas representaciones aparezcan en dispositivos concretos (esto se conoce como forzar canales). Resulta útil en escenarios móviles donde ha definido una representación que es óptima para un dispositivo móvil específico.
  
    
    

### Control Panel de canales de dispositivos

El Panel de canales de dispositivos es un nuevo control que se puede incluir en un diseño de página para controlar qué contenido se representa en qué canal. El Panel de canales de dispositivos es un contenedor que se asigna a uno o varios canales: si uno o varios de estos canales están activos cuando se representa la página, también se representa todo el contenido del Panel de canales de dispositivos. El Panel de canales de dispositivos hace que sea más fácil determinar cuándo incluir contenido específico para determinados canales.
  
    
    

### Plantillas de visualización
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

Puede que quiera controlar el formato y la presentación de los resultados de búsqueda en su sitio web. Puede hacerlo usando plantillas de visualización, que amplían las opciones disponibles para personalizar los resultados de búsqueda con la interfaz del usuario más allá de asignar los campos predefinidos que quiere que se vean.
  
    
    
Existen tres contextos en los que podría necesitar usar plantillas de visualización con resultados de búsqueda: cuando quiera asignar cómo se presenta la estructura general de los resultados de búsqueda, cuando quiera mostrar grupos de resultados y cuando quiera mostrar cómo se visualizará cada resultado o elemento en el conjunto de resultados. Se denominan, respectivamente, plantillas de control, de grupo y de elemento.
  
    
    
Para más información sobre las plantillas de visualización, vea  [Plantillas para mostrar del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-display-templates.md).
  
    
    

### Representaciones de imágenes
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

Puede usar  [representaciones de imágenes](sharepoint-2013-design-manager-image-renditions.md) para mostrar imágenes subidas en tamaños, anchos y recortes predefinidos. Puede crear más de una representación de un archivo de imagen de origen, lo que significa que puede establecer las características de visualización una vez y aplicarlas a todas las imágenes que quiera. Por ejemplo, una representación llamada **Article_image** muestra una imagen a tamaño completo en un artículo, mientras que la representación llamada **Thumbnail_small** muestra una versión más pequeña de la imagen en un contexto definido por usted.
  
    
    
Para poder usar representaciones de imágenes, asegúrese de que la memoria caché BLOB esté habilitada en el servidor (puede hacerlo en las herramientas de administración en Internet Information Services (IIS)). Busque su archivo **web.config** allí y habilite la memoria caché BLOB. Actualice la página y verá que las representaciones de imágenes estarán disponibles.
  
    
    

## Metadatos y navegación administrados en SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_MetadataAndNavigation"> </a>

Las capacidades de metadatos administrados empresariales (EMM) introducidas en se han mejorado y ampliado en SharePoint 2013 para un mejor rendimiento, acceso más fácil a través de la interfaz de usuario y navegación controlada por taxonomía, llamada navegación administrada.
  
    
    

### Navegación administrada

La navegación administrada es la alternativa basada en taxonomía a la característica de navegación de SharePoint tradicional (llamada navegación estructurada), que se basa en la estructura de SharePoint. La característica de  [navegación administrada](managed-navigation-in-sharepoint-2013.md) le permite diseñar una navegación de sitios controlada por metadatos administrados y crea direcciones URL apropiadas para SEO que derivan de la estructura de navegación administrada. Como la navegación administrada está controlada por taxonomía, puede usarla para diseñar la navegación de sitios en torno a conceptos de negocios importantes sin cambiar la estructura de sus sitios ni de los componentes de sitios.
  
    
    

### Elemento web Búsqueda de contenido
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

Puede usar el  [Elemento web Búsqueda de contenido (CSWP)](content-search-web-part-in-sharepoint-2013.md) para mostrar datos de búsqueda en sus páginas. Cumple una función parecida a la del Elemento Web Consulta de contenido, pero cumple objetivos de diseño de sitios diferentes. Los estilos del CSWP son más fáciles de personalizar que los estilos del Elemento Web Consulta de contenido. CSWP devuelve resultados de cliente en formato JSON. En el servidor, puede personalizar los resultados con plantillas de visualización.
  
    
    

### Otras mejoras de metadatos administrados para sitios
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

SharePoint 2013 introduce varias mejoras en las funciones y la interfaz de usuario de metadatos administrados. Para más información, vea  [Navegación y metadatos administrados en SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md).
  
    
    

## Publicar contenido en SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_Publishing"> </a>

SharePoint 2013 ofrece nuevas características de publicación de contenido que le permiten desarrollar sitios de publicación que admiten escenarios y topologías nuevas, más flexibles y más complejas. 
  
    
    

### Paquetes de diseño

Si es diseñador web profesional, es posible que quiera crear y probar un diseño en su propio entorno o en su propia colección de sitios antes de entregarlo para instalarlo en otras colecciones de sitios. Si está usando la publicación entre sitios para compartir contenido entre colecciones de sitios, posiblemente quiera empaquetar e instalar el mismo diseño en todos los sitios.
  
    
    
En versiones anteriores de SharePoint, si quería volver a usar un diseño, había que usar Visual Studio para crear un paquete de solución de SharePoint (archivo .wsp). Después, en el sitio de destino, se subía el paquete a la Galería de soluciones y se ejecutaba. Ahora, en SharePoint 2013, al terminar de diseñar su sitio, puede elegir **Exportar paquete** en el Administrador de diseño para exportar un solo archivo .wsp, llamado [paquete de diseño](sharepoint-2013-design-manager-design-packages.md). Cuando exporta un paquete de diseño, SharePoint 2013 empaqueta en un paquete de diseño automáticamente todo el contenido que haya agregado o cambiado en la Galería de páginas maestras, la Biblioteca de estilos, la Galería de temas, la lista Canales de dispositivos y los tipos de contenido de página. 
  
    
    

> **NOTA**
> Un paquete de diseño no incluye páginas, configuración de navegación ni el almacén de términos. 
  
    
    

Para sitios web públicos de Office 365, los paquetes de diseño no sobrescriben los archivos existentes. La instalación de un paquete de diseño crea una nueva carpeta en la Galería de páginas maestras, la Galería de estilos y la Galería de temas donde están aislados los activos de diseño. 
  
    
    
Cuando importa un paquete de diseño, los activos de diseño del paquete sobrescriben los archivos que haya y se aplican al diseño actual del sitio. La CSS alternativa, el tema y la página maestra del sistema y predeterminados del sitio se establecen a partir de los archivos que hay en el paquete de diseño. Con los paquetes de diseño, un diseño creado en un entorno puede aplicarse fácilmente a otro entorno independiente.
  
    
    

### Catálogos

La publicación de sitios de SharePoint 2013 introduce los catálogos, que permiten incorporar listas en los sitios de publicación. Los catálogos permiten la publicación de contenido en colecciones de sitios (las características de publicación entre sitios depende de catálogos). Puede usar catálogos para reutilizar realmente el contenido entre sus sitios y entre el límite de sus sitios de intranet, de Internet y de extranet. Para consultas de búsquedas predefinidas, los catálogos se marcan en la búsqueda. Puede mostrar el contenido almacenado en catálogos entre colecciones de sitios con el  [Elemento web Búsqueda de contenido (CSWP)](content-search-web-part-in-sharepoint-2013.md). Puede escribir código personalizado para rellenar catálogos, conectar un catálogo de productos a un sitio y ajustar páginas individuales con elementos web, contenido HTML y diseños de páginas personalizados que aparecen únicamente en el contexto definido.
  
    
    

### Controles de representación del lado cliente

Todos los controles nuevos en SharePoint 2013 se representan en el cliente. Como diseñador o desarrollador, tiene control sobre la manera de representar el contenido en la página, y puede usar diversas técnicas de diseño para obtener el aspecto y los comportamientos que desea en sus páginas publicadas con características como el elemento web de búsqueda de contenido y las plantillas de visualización. Los datos se escriben en los controles en una matriz JSON del lado cliente y puede mostrar contenido usando JavaScript, CSS y plantillas. 
  
    
    

### Publicación entre sitios

Microsoft SharePoint 2013 presenta una característica de publicación entre sitios que le permite reutilizar contenido en varias colecciones de sitios. Usa capacidades de búsqueda integradas para permitir las arquitecturas y los escenarios de publicación. Por primera vez, se puede diseñar sitios que abarcan granjas de servidores de SharePoint; esto permite que los sitios amplíen el límite entre intranets e Internet. 
  
    
    
Use la característica de páginas de tema para personalizar la experiencia de página de aterrizaje para el contenido publicado entre sitios. Use direcciones URL adecuadas para SEO con el fin de administrar y hacer persistir y mantener con más facilidad la estructura de sitio en una amplia variedad de escenarios, incluidas las complejas topologías de sitios en varios idiomas.
  
    
    
Para más información sobre la publicación entre sitios, vea  [Escenario: Crear sitios de SharePoint con la publicación entre sitios en SharePoint Server 2013](http://technet.microsoft.com/es-es/sharepoint/jj872721). Si quiere más información sobre las opciones de desarrollo para la publicación entre sitios, vea  [Publicación cruzada en SharePoint 2013](cross-site-publishing-in-sharepoint-2013.md).
  
    
    

### Mejoras de SEO

Muchos usuarios de sitios comerciales son remitidos a sitios comerciales de Internet desde grandes motores de búsqueda, como Bing y sus competidores globales. SharePoint 2013 incluye características como direcciones URL descriptivas, redireccionamientos de página de inicio, mapas de sitio XML, propiedades de SEO personalizadas que le permiten definir de manera flexible el título del explorador, palabras clave y descripciones de etiquetas de **<Meta>**, y direcciones URL fáciles de entender para variaciones de sitios en varios idiomas.
  
    
    
En Office 365, la infraestructura del sitio genera un mapa de sitio XML actualizado en las 24 horas posteriores al cambio en el sitio. Con una instalación local, puede ajustar la actualización de sus mapas de sitio y especificar a qué motores de búsqueda quiere que Microsoft haga ping cuando actualicemos el mapa de sitio.
  
    
    
El contenido que gusta a sus amigos en Facebook afecta a lo que ve en los resultados de búsqueda devueltos por Bing y otros grandes motores de búsqueda. Puede usar API en modelos de programación de SharePoint 2013 para personalizar la optimización de la búsqueda para su sitio.
  
    
    

### Análisis y recomendaciones

Puede hacer un seguimiento de cómo las personas usan los sitios de publicación y sus componentes usando la característica de análisis de SharePoint 2013, que está muy integrada con el motor de búsqueda. El análisis genera capacidades de recomendaciones sobre el contenido e introduce cálculos en el índice de búsqueda como propiedades administradas. Las recomendaciones proporcionadas por el análisis de búsqueda, que incluyen vistas de página y elementos únicos por día, pueden influir en la relevancia de los resultados de búsqueda.
  
    
    
El análisis hace que los datos sean anónimos y los resume cada 15 días; también depura los eventos cada 15 días y luego todos los meses pasados 3 años. Las vistas del ciclo de vida siempre se retienen. El contenido menos visitado se recorta antes de que el análisis agregue datos a una base de datos de informes. Puede usar código personalizado para exportar datos a Excel desde la base de datos de informes, personalizar el peso del evento **View** y crear eventos personalizados (incluidos los eventos que JavaScript envió.
  
    
    

### Variaciones y sitios en varios idiomas

Puede usar la característica de variaciones que hay en SharePoint 2013 para crear sitios en varios idiomas u otros sitios donde quiera modificar la presentación del contenido. La característica de variaciones está limitada a una colección de sitios. O sea, puede crear "variantes" de idioma o configuración regional de destino de un idioma o una configuración regional de origen como sitios web actuales dentro de la misma colección de sitios de SharePoint. Las variaciones admiten direcciones URL descriptivas y la capacidad de exportar o importar contenido para la traducción por parte de terceros en  [formato de archivo XLIFF](the-xliff-interchange-file-format-in-sharepoint-2013.md). Puede incluir etiquetas, una página para traducción y replicación, una variedad de elementos de lista (por ejemplo, bibliotecas de documentos) y navegación en sus paquetes de exportación. 
  
    
    

## Recursos adicionales
<a name="SP15_WhatsNewSiteDevelopment_AdditionalResources"> </a>


-  [Realizar operaciones básicas con código de biblioteca de cliente de SharePoint 2013](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [Completar operaciones básicas con código de biblioteca de JavaScript en SharePoint 2013](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
-  [Procedimientos: Personalizar diseños de página para un sitio basado en catálogos en SharePoint 2013](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md)
    
  
-  [Cómo: cambiar la página de vista previa en el Administrador de diseño de SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [Cómo: resolver errores y advertencias durante la vista previa de una página en SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)
    
  
-  [Introducción a los temas para SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Navegación y metadatos administrados en SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md)
    
  
-  [Novedades en la búsqueda para desarrolladores en SharePoint 2013](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

