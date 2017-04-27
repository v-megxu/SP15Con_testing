---
title: Información general sobre el Administrador de diseño de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 29834b3f-3815-4347-91d3-296387663114
---


# Información general sobre el Administrador de diseño de SharePoint 2013
Obtenga información general sobre cómo usar el Administrador de diseño para personalizar la marca de su sitio de SharePoint 2013. El Administrador de diseño es una característica de publicación que está disponible en sitios de publicación tanto en SharePoint Server 2013 como en Office 365. También puede usar el Administrador de diseño para personalizar la marca del sitio de acceso público en Office 365.
## Introducción al Administrador de diseño
<a name="Introduction"> </a>

Si quiere que su sitio de SharePoint 2013 represente la marca de su organización y no "se parezca a SharePoint", puede crear un diseño personalizado y usar el Administrador de diseño. El Administrador de diseño es una característica de SharePoint 2013 que permite crear fácilmente un diseño totalmente personalizado y perfecto hasta el último detalle usando las herramientas de diseño web con las que está familiarizado. El Administrador de diseño es una característica de publicación que está disponible en sitios de publicación tanto en SharePoint Server 2013 como en Office 365. También puede usar el Administrador de diseño para personalizar la marca del sitio de acceso público en Office 365.
  
    
    
Con el Administrador de diseño, puede crear un diseño visual para su sitio web con la herramienta de diseño web o el editor HMTL que prefiera, usando solo HTML y CSS, y después cargar el diseño en SharePoint. El Administrador de diseño es la interfaz y el concentrador centralizado desde donde se administran todos los aspectos de un diseño personalizado.
  
    
    
Crear el diseño visual de un sitio suele ser un proceso de mayor envergadura que involucra a diversas personas u organizaciones. Para ver una guía básica de las tareas desde una perspectiva mayor, consulte  [Diseño y personalización de marca en SharePoint 2013](http://go.microsoft.com/fwlink/?LinkId=262838)
  
    
    
De forma general, el diseñador realizará las siguientes tareas:
  
    
    

- Comprender los conceptos básicos del diseño de SharePoint. Para obtener más información, consulte  [Información general sobre el modelo de páginas de SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
    
  
- Crear un boceto del diseño en HTML y CSS. Crear el diseño es una de las habilidades fundamentales de un diseñador web, y no se trata en este artículo.
    
  
- Implementar el diseño mediante el Administrador de diseño. Las secciones de este artículo proporcionan una introducción al Administrador de diseño y el proceso para usar el Administrador de diseño para implementar un diseño visual.
    
  

> **NOTA**
> Los elementos de diseño que puede crear para un sitio web de acceso público en SharePoint Online son diferentes de los elementos de diseño de otros sitios de publicación. Además, no puede crear paquetes de diseño en la versión del Administrador de diseño que está disponible en el sitio web de acceso público en SharePoint Online. 
  
    
    


## Usar el Administrador de diseño para implementar un diseño
<a name="Use"> </a>

Al mirar el Administrador de diseño, vemos una serie de vínculos en el lado izquierdo que representan las tareas generales que tiene que realizar. En función de su diseño y de los requisitos de su sitio, quizás no tenga que realizar todas estas tareas y no tiene que realizarlas necesariamente en este orden. No obstante, esta secuencia es un punto de partida útil.
  
    
    

### Antes de empezar

Antes de poder usar el Administrador de diseño, necesita un diseño. Puede crear el suyo propio o usar una plantilla de sitio web lista para usar. Un "diseño" es simplemente un grupo de archivos que implementan el diseño visual del sitio, normalmente:
  
    
    

- Al menos un archivo HTML que se convertirá en una página maestra de SharePoint
    
  
- Uno o varios archivos CSS
    
  
- Archivos JavaScript
    
  
- Imágenes
    
  
- Otros archivos complementarios
    
  
A la hora de crear el boceto del sitio en HTML y CSS, probablemente tendrá varios archivos HTML que implementan los diseños con los que quiere que aparezcan las diferentes páginas o tipos de páginas. Recuerde que solo uno de estos archivos HTML se convertirán en la página maestra, a menos que tenga varios canales de dispositivo, en los que cada canal tiene su propia página maestra; consulte la sección siguiente. Después de usar el Administrador de diseño para crear otros elementos de sitio, como diseños de página o plantillas de visualización, puede transferir el marcado de sus bocetos de HTML a los archivos HTML y CSS asociados al diseño de página o plantilla de visualización.
  
    
    
Antes de comenzar, necesitará también los permisos de SharePoint requeridos. Para usar el Administrador de diseño, debe tener al menos el nivel de permisos Diseñador.
  
    
    

### Administrar canales de dispositivo

Antes incluso de diseñar un sitio, querrá considerar a qué dispositivos estará dirigido el sitio y cuál será la experiencia del usuario en cada dispositivo. Por ejemplo, quizás quiera optimizar el diseño de su sitio para una determinada clase de smartphones o tabletas.
  
    
    
Según qué canales defina, puede querer varios diseños y, por lo tanto, varios archivos HTML, convirtiéndose cada archivo en una página maestra diferente. Además, cada archivo HTML (y por lo tanto, cada página maestra) puede hacer referencia a su propio archivo CSS. Antes de diseñar su sitio, una de las primeras cosas a tener en cuenta son los canales de dispositivo.
  
    
    
Con los canales de dispositivo, puede representar un único sitio de publicación de diferentes maneras asignando diferentes diseños a los distintos dispositivos. Cada canal tiene su propia página maestra que vincula a una hoja de estilos optimizada para un dispositivo determinado. Cada canal especifica las subcadenas del agente de usuario para uno o varios dispositivos, como "Windows Phone OS". Estas son reglas que determinan qué dispositivos se incluyen en cada canal. Después, cuando los visitantes examinan su sitio, cada canal captura el tráfico para su dispositivo o clase de dispositivos específicos, como teléfonos de Windows Phone, y los visitantes verán su sitio con un diseño optimizado para su dispositivo.
  
    
    
Los canales de dispositivo se crean y almacenan en una lista de SharePoint en la que el orden es importante, porque los canales de dispositivo también tienen clasificaciones. Los canales de dispositivo de la lista se ordenan de arriba hacia abajo, y las reglas de inclusión se procesan en ese orden. Eso significa que querrá los canales de dispositivo con las reglas más específicas en la parte superior. Por ejemplo, un canal dirigido a "Windows Phone OS 7.0" debe preceder a un canal dirigido a "Windows Phone OS".
  
    
    

### Cargar archivos de diseño

Para crear un diseño puede usar el editor de HTML que prefiera y trabajar con los archivos localmente en su equipo. Sin embargo, en algún momento tendrá que cargar esos archivos en la Galería de páginas maestras de su sitio de SharePoint para poder usar el Administrador de diseño para convertir, mostrar una vista previa y refinar el diseño.
  
    
    
La manera más fácil de cargar los archivos de diseño y continuar trabajando con ellos es asignar en su equipo una unidad a la Galería de páginas maestras de su sitio de SharePoint. De esta manera se conecta una carpeta de su equipo a la Galería de páginas maestras para que pueda trabajar en los archivos ubicados en el servidor en SharePoint 2013 como si fueran archivos locales.
  
    
    
Después de asignar una unidad de red, puede cargar su diseño a SharePoint simplemente copiando los archivos de diseño a una carpeta en la unidad asignada de su equipo que está conectada a SharePoint. Después de convertir el archivo HTML en una página maestra de SharePoint, y después de crear los diseños de página y las plantillas de visualización, cada una con su propio archivo HTML asociado, puede continuar editando esos archivos HTML asociados en el editor de HTML de su equipo. Cada vez que guarde un archivo en la unidad asignada, SharePoint sincronizará automáticamente los archivos de su equipo con la Galería de páginas maestras. Puede crear su propia estructura de carpetas en la unidad asignada y SharePoint mantendrá esa estructura, que aparece en la Galería de páginas maestras. Debe guardar todos los archivos relativos a un diseño en una sola carpeta y después, copiar esa carpeta a la unidad asignada cuando esté listo para cargar su diseño.
  
    
    
Para obtener más información, consulte  [Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

### Editar páginas maestras

La creación de una página maestra con una marca totalmente personalizada, que contenga toda la funcionalidad de SharePoint que quiere, como la navegación y la búsqueda, es un proceso que consta básicamente de tres pasos:
  
    
    

1. Convertir un archivo HTML en una página maestra de SharePoint.
    
  
2. Mostrar una vista previa de la página maestra y corregir los errores.
    
  
3. Agregar fragmentos de código de SharePoint a la página maestra.
    
  
Cada uno de estos tres pasos se realiza en una página diferente del Administrador de diseño.
  
    
    

#### Convertir un archivo HTML

La principal característica del Administrador de diseño es que convierte el diseño HTML en una página maestra de SharePoint. Para que se represente correctamente, una página maestra de SharePoint debe contener numerosos elementos de ASP.NET y elementos que son específicos de SharePoint. Cuando convierte un archivo HTML en una página maestra, el Administrador de diseño crea un archivo .master que contiene todos estos elementos necesarios, por lo que no tiene que saber nada acerca de ellos. Durante la conversión, también se agrega parte del marcado HTML (como los comentarios) al archivo HTML original.
  
    
    
Después de la conversión, el archivo HTML y la página maestra de SharePoint se asocian para que cuando edite y guarde el archivo HTML en la unidad asignada, la página maestra se actualice automáticamente. En el Administrador de diseño, la página maestra HTML tiene una propiedad llamada **Archivo asociado** que determina si los cambios que se realicen en el archivo HTML se sincronizarán con el archivo .master.
  
    
    

> **NOTA**
> El Administrador de diseño también ofrece la opción de comenzar a diseñar usando una página maestra mínima. En este caso, no tiene que comenzar con un diseño HTML; en su lugar, puede crear una página maestra HTML que contenga el número mínimo de elementos de página necesario para representar la página maestra correctamente en SharePoint y, después, crear el diseño editando la página maestra HTML. 
  
    
    


#### Mostrar una vista previa de la página maestra

Además de convertir su página maestra, el Administrador de diseño proporciona una vista previa del lado del servidor (frente a la vista previa en tiempo de diseño del editor HTML), para que pueda tener una vista previa activa de su página maestra y corregir los problemas que podrían impedir que la página se represente. Por ejemplo, su archivo HTML debe ser compatible con XML, por lo que quizás tenga que corregir problemas de marcado menores, tales como proporcionar las etiquetas de cierre para todos los elementos. Para corregir los posibles problemas, debe editar el archivo HTML, guardarlo y después, actualizar la vista previa del lado del servidor.
  
    
    
Cuando esté viendo una vista previa de una página maestra, puede usar la opción **Cambiar la página de vista previa** en la esquina superior izquierda para ver una vista previa de la página maestra junto con las páginas existentes, o crear una nueva página para la que mostrar una vista previa. A diferencia de la vista previa en tiempo de diseño de la página maestra HTML en un editor HTML, esta vista previa del lado del servidor es completamente funcional, por lo que quizás prefiera editar el archivo HTML, guardarlo para que los últimos cambios se sincronicen con el archivo .master asociado, y actualizar la vista previa activa para ver los últimos cambios de diseño en el explorador.
  
    
    

#### Agregar fragmentos de código

Después de convertir la página maestra y mostrar correctamente una vista previa de la misma, está listo para agregar fragmentos de código a la página maestra. Un fragmento de código es una representación HTML de un componente de SharePoint, como un control de navegación, un cuadro de búsqueda o un elemento web, que puede agregar a la página maestra. Agregar fragmentos de código a la página maestra es la manera rápida de incorporar toda la funcionalidad de SharePoint en su página maestra. Agregar fragmentos de código es un proceso que consta básicamente de tres pasos:
  
    
    

1. Buscar y configurar fragmentos de código en la Galería de fragmentos de códigos.
    
  
2. Copiar los fragmentos de código en su página maestra HTML.
    
  
3. Mostrar una vista previa y aplicar estilos a los fragmentos de código mediante CSS.
    
    Para obtener más información, consulte  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  

#### Buscar y configurar fragmentos de código en la Galería de fragmentos de códigos

La Galería de fragmentos de código es el lugar donde puede ver rápidamente qué componentes hay disponibles para el tipo de archivo que está editando, ya sea la página maestra o el diseño de página. En la cinta, seleccione un fragmento de código. En la cuadrícula de propiedades de la derecha, puede configurar las propiedades de esta instancia de un fragmento de código y, en la izquierda, seleccione **Actualizar** para actualizar el fragmento de código HTML.
  
    
    

#### Copiar los fragmentos de código en su página maestra HTML

Después de configurar un fragmento de código, puede copiarlo al Portapapeles y pegarlo en el lugar adecuado del archivo HTML. Su diseño HTML quizás ya contenga bocetos de controles o controles estáticos, en cuyo caso querrá eliminarlos o designarlos como comentarios cuando los reemplace por fragmentos de código dinámicos de la Galería de fragmentos de código.
  
    
    

#### Mostrar una vista previa y aplicar estilos a los fragmentos de código mediante CSS

Después de copiar los fragmentos de código en su archivo HTML y guardar los cambios, puede actualizar la vista previa del lado del servidor de la página maestra para ver cómo se representan los controles. Los fragmentos de código contienen marcado que proporciona una vista previa en tiempo de diseño en un editor HTML, pero la vista previa del lado del servidor muestra una vista previa totalmente fiel, con datos activos; por ejemplo, un control de navegación mostrará la estructura de navegación actual del sitio con datos activos del origen de datos.
  
    
    
De forma predeterminada, la mayoría de los fragmentos de código heredan los estilos de la hoja de estilos principal de SharePoint 2013, corev15.css. Para aplicar estilos a un fragmento de código, tiene que identificar qué estilos se aplican al fragmento de código y después, invalidarlos con CSS personalizadas. Para identificar estos estilos predeterminados, puede usar una herramienta de explorador como las herramientas de desarrollador de Internet Explorer. Cuando esté viendo su página maestra en la vista previa del lado del servidor en Internet Explorer, presione **F12**, elija **Buscar** y después, elija **Seleccionar elemento con un clic**. Esto permite hacer clic en el fragmento de código y ver exactamente qué estilos se anularán al agregar CSS a la página de estilos personalizada con la que esté vinculada su página maestra.
  
    
    

### Editar plantillas de visualización

Si está usando una instalación local de SharePoint Server, puede usar el elemento web Búsqueda de contenido y otros elementos web controlados por búsqueda para mostrar los resultados de las consultas de búsqueda como contenido en sus páginas. Los elementos web controlados por búsqueda usan plantillas de visualización con dos fines principales:
  
    
    

- Para asignar las propiedades administradas que se devuelven en elementos de resultados de búsqueda a las propiedades que estarán disponibles para JavaScript, incluido el código JavaScript personalizado que elija implementar.
    
  
- Para usar HTML y CSS para presentar esas propiedades y aplicarles el estilo con el que se mostrarán.
    
  
Con las páginas maestras y los diseños de página, edita un archivo HTML asociado pero no el archivo .master ni el archivo .aspx. De forma similar, las plantillas de visualización están formadas por un archivo HTML y un archivo .js asociado, y solo se edita el archivo HTML. Cada vez que guarda ese archivo HTML, SharePoint actualiza automáticamente el archivo .js asociado.
  
    
    
Para crear una plantilla de visualización personalizada, debe comenzar por copiar una de las plantillas de visualización existentes y después, personalizarla. Esto resulta útil porque las plantillas de visualización personalizadas contienen información en los comentarios de los archivos HTML, y tendrá la estructura de páginas básica apropiada y un marco para las tareas básicas, como la asignación de campos de entrada.
  
    
    

### Editar diseños de página

El proceso para crear un diseño de página es algo diferente de la creación de una página maestra. En una página maestra, comienza con un diseño HTML, lo convierte en una página maestra de SharePoint y después, continúa editando el archivo HTML asociado. Pero para un diseño de página, primero crea el diseño de página en el Administrador de diseño, que crea un archivo .aspx y un archivo HTML y después, se edita el archivo HTML asociado en la unidad asignada, en el editor HTML. El motivo para usar el Administrador de diseño para crear un diseño de página es poder agregar el conjunto correcto de campos de página al diseño de página.
  
    
    
Al crear un diseño de página, selecciona una página maestra con la que mostrar una vista previa del diseño de página, y selecciona un tipo de contenido de diseño de página. Un tipo de contenido es un esquema de campos y tipos de datos, y los campos disponibles en el tipo de contenido de diseño de página determinan qué controles de campo de página están disponibles en su diseño de página. El diseño de página se crea primero en el explorador para poder agregar los campos de página.
  
    
    
Después de crear un diseño de página con su archivo HTML asociado, los pasos siguientes son los mismos que para una página maestra:
  
    
    

- Mostrar una vista previa del diseño de página y editar y guardar la versión HTML para corregir los problemas.
    
  
- Agregar fragmentos de código al diseño de página (configurar, copiar, mostrar una vista previa y aplicar estilos).
    
  
En la Galería de fragmentos de código hay disponibles diversos fragmentos de código para diseños de página y páginas maestras, y la cinta muestra solo los fragmentos de código relevantes para ese tipo de archivo. Por ejemplo, hay disponibles fragmentos de código de navegación y búsqueda solo para una página maestra, mientras que los campos de página están disponibles solo en un diseño de página.
  
    
    
A la hora de crear un diseño de página, la tarea básica es colocar los controles de campo de página y aplicarles el estilo con el que se mostrará el contenido creado por los autores de contenido. Los estilos de un diseño de página pueden residir en cualquier hoja de estilos con la que esté vinculada la página maestra, o bien cada diseño de página puede vincularse a su propia hoja de estilos específica. Si su diseño HTML incluye contenido más apropiado para un diseño de página que para una página maestra, querrá transferir el contenido fuera de su página maestra HTML y después, aplicar esos estilos a los controles y elementos correctos del diseño de página relevante.
  
    
    
Para obtener más información, consulte  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
  
    
    

### Crear temas y aspectos compuestos

En el sitio web de acceso público de Office 365, pero no en las instalaciones locales de SharePoint Server 2013, el Administrador de diseño tiene la opción de crear temas y aspectos compuestos. Un tema es un conjunto de fuentes y colores que se pueden aplicar a un diseño personalizado (es decir, una página maestra). Los temas se definen en archivos .xml que carga en la galería de Temas. Si quiere poder aplicar un tema a una página maestra, debe agregar un marcado especial a la página maestra que SharePoint reconozca y use para insertar elementos de tema, como fuentes y colores.
  
    
    
Un aspecto compuesto no es más que una asociación entre una imagen de fondo, un tema (fuentes y colores) y un diseño (una página maestra). Un aspecto compuesto toma los elementos de diseño predefinidos (temas, imágenes de fondo y páginas maestras) y las habilita para que se puedan usar en muchas combinaciones diferentes, para que el sitio web de acceso público tenga muchas más opciones de personalización.
  
    
    

### Publicar y aplicar diseño

La mayoría de los activos que usa su diseño, como imágenes, HTML, CSS y archivos JavaScript, residirán en la Galería de páginas maestras. Esta galería es una biblioteca de documentos de SharePoint que tiene activado el control de versiones de forma predeterminada, lo que crea versiones principales y secundarias (borradores) cada vez que edita un archivo.
  
    
    
Antes de poder aplicar su diseño a un sitio, debe publicar una versión principal de cada archivo o activo que use su diseño. Si está diseñando su sitio en un entorno de pruebas, debe desactivar el control de versiones para la Galería de páginas maestras para no tener que acordarse de publicar cada archivo antes de mostrar una vista previa del sitio. Si está diseñando en un sitio activo, este no es un procedimiento recomendado.
  
    
    
Después de publicar todos los archivos de diseño, está listo para aplicar el diseño asignando las páginas maestras terminadas al sitio. Cada sitio puede tener asignada una página maestra diferente a cada canal de dispositivo, y es en esta página del Administrador de diseño donde se aplica una página maestra a un canal.
  
    
    

### Crear un paquete de diseño

Un paquete de diseño es una manera fácil de recopilar todos los archivos y activos que usa su diseño, exportarlos desde un sitio e importarlos a otro, y aplicar el diseño al nuevo sitio. Si implementa y refina su diseño en una colección de sitios de prueba y quiere implementarlo en una colección de sitios activa, puede usar un paquete de diseño para transferir el diseño.
  
    
    
Un paquete de diseño es un archivo .wsp, un archivo de solución de SharePoint, que no es más que un tipo especial de archivo .cab. Cuando crea o importa un paquete de diseño, el archivo .wsp se almacena en la galería Soluciones. Después de importar un paquete de diseño, este se activa automáticamente. Si las páginas maestras y los diseños de página se publicaron antes de empaquetarse, y si las páginas maestras se asignaron a canales de dispositivo antes de empaquetarse, el diseño se aplicará automáticamente al sitio al implementar el paquete de diseño. Si no es así, para aplicar el diseño al nuevo sitio, solo tiene que publicar los archivos de diseño y aplicar la páginas maestras a cada canal de dispositivo.
  
    
    

> **NOTA**
> Los paquetes de diseño no están disponibles en el sitio web de acceso público de Office 365. Para implementar un diseño totalmente personalizado con el Administrador de diseño, puede invitar a un diseñador a su sitio concediéndole temporalmente el nivel de permiso Diseñador. 
  
    
    


## Recursos adicionales
<a name="Additional"> </a>


-  [Información general sobre el modelo de páginas de SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [Cómo convertir un archivo HTML en una página maestra en SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  

