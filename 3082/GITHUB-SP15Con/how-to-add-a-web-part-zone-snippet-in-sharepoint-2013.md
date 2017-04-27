---
title: Cómo agregar un fragmento de código de zona de elementos web en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7583b217-200c-4569-8f88-fe975c8ebd72
---


# Cómo agregar un fragmento de código de zona de elementos web en SharePoint 2013
Una zona de elementos web es un fragmento de código que puede agregar a un diseño de página para que los autores de contenido puedan agregar, editar o eliminar elementos web de esa zona.
## Introducción al fragmento de código de zona de elementos web
<a name="Introduction"> </a>

Un elemento web es un control de servidor que proporciona una funcionalidad de SharePoint específica, y una zona de elementos web es un contenedor que determina el diseño, el comportamiento y otras propiedades de los elementos web contenidos en esa zona. Por ejemplo, una zona de elementos web puede especificar si los elementos web de la zona:
  
    
    

- Está dispuestos en un diseño horizontal o vertical. 
    
  
- Muestran elementos de interfaz de usuario comunes, como una barra de título o un borde.
    
  
- Pueden personalizarlos los autores de contenido cuando editan una página en el explorador.
    
  
- Pueden personalizarlos los visitantes del sitio que crean una vista personal de un elemento web cuando ven una página en el explorador.
    
  
En un sitio de publicación, los autores de contenido con los permisos necesarios pueden crear o editar páginas que residen en la biblioteca Páginas. Como diseñador, puede agregar una zona de elementos web a un diseño de página. Cuando un autor de contenido crea o edita una página basada en ese diseño de página, el autor puede agregar, editar o eliminar los elementos web de esa zona. Por ejemplo, quizás quiera agregar una zona de elementos web a un diseño de página para que los autores de contenido puedan:
  
    
    

- Mostrar los resultados de una consulta de búsqueda usando un elemento web Búsqueda de contenido. Los autores pueden actualizar o modificar la consulta de búsqueda cuando un elemento web controlado por búsquedas reside dentro de una zona de elementos web.
    
  
- Insertar clips de vídeo o audio en una página web mediante un elemento web Multimedia.
    
  
- Crear listas de hipervínculos que se puedan editar, agrupar o reordenar fácilmente usando un elemento web Vínculo de resumen.
    
  
- Crear un mapa del sitio que enumere todas las páginas de un sitio y que se actualice automáticamente siempre que se agregue, elimine, cambie de nombre o mueva una página usando un elemento web Tabla de contenido.
    
  

### Cuándo usar zonas de elementos web

Cuando un diseño de página incluye una o varias zonas de elementos web, estas están disponibles en todas las páginas que usan ese diseño, lo que permite a los autores insertar elementos web en esas páginas. Permitir a los autores insertar elementos web en las páginas reduce su control sobre la experiencia de los usuarios en el sitio. Por ejemplo, un autor podría insertar en una página un elemento web Tabla de contenido que expone partes del sitio a las que no desea que el visitante navegue desde la página actual.
  
    
    
Si quiere controlar completamente cómo aparece un elemento web en el sitio, y si quiere que el elemento web aparezca en todas las páginas de un tipo de determinado, agréguelo directamente a un diseño de página. Si quiere que un elemento web aparezca en todas las páginas de un sitio, también puede agregarlo a una página maestra.
  
    
    

> **NOTA**
> Las zonas de elementos web están disponibles en los diseños de página pero no en las páginas maestras. El propósito de las zonas es permitir a los autores modificar los elementos web, y los autores normalmente no editan una página maestra. 
  
    
    

También puede agregar zonas de elementos web a un diseño de página y restringir su uso. Por ejemplo, puede agregar elementos web a una zona y después, establecer una propiedad de esa zona para que los autores de contenido puedan editar las propiedades de los elementos web existentes, pero no agregar ni quitar elementos web de la zona. Las zonas de elementos web tienen un conjunto de propiedades con una doble finalidad. Puede usar un subconjunto de propiedades para organizar el diseño y el formato de los elementos web de la página. Puede usar otro subconjunto de propiedades para proporcionar un nivel adicional de protección contra modificaciones (o "bloqueo") de los elementos web dentro de la zona.
  
    
    
Para los distintos niveles de control sobre cómo se presentan los elementos web en el sitio, puede:
  
    
    

- Agregar elementos web directamente a una página maestra o diseño de página. Esto significa que los autores de contenido no pueden modificar los elementos web.
    
  
- Agregar elementos web a zonas en diseños de página, restringiendo esas zonas solo a los elementos web predeterminados que agregue.
    
  
- Agregar zonas de elementos web a diseños de página y dar a los autores de contenido un control completo sobre qué elementos web aparecen en esas zonas y cómo se configuran.
    
  
Las propiedades de una zona de elementos web pueden especificar si los autores de contenido están autorizados a cambiar:
  
    
    

- El diseño de los elementos web de la zona (agregar, eliminar, cambiar el tamaño o mover los elementos web).
    
  
- La configuración de los elementos web para todos los usuarios (la vista compartida de un elemento web).
    
  
- Su configuración personal del elemento web (la vista personal de un elemento web).
    
  
La tabla 1 muestra las propiedades importantes que hay que tener en cuenta cuando se quiere restringir una zona de elementos web.
  
    
    

**Tabla 1. Propiedades de la zona de elementos web que se usan para restringir a los autores de contenido**


|**Nombre de propiedad**|**Descripción**|
|:-----|:-----|
|**AllowLayoutChange** <br/> |Especifica si los elementos web dentro de la zona se pueden cerrar, minimizar, eliminar o restaurar.  <br/> Si se establece en **False**, los usuarios no pueden cerrar, minimizar, eliminar ni restaurar elementos web en la zona, arrastrar elementos web a una zona diferente ni reorganizar o mover elementos web dentro de la zona. Los usuarios tampoco pueden agregar elementos web del catálogo de elementos web, y varias propiedades que afectan a la interfaz de usuario de elementos web en la zona están deshabilitadas. Esta propiedad no afecta a la capacidad para cambiar el diseño mediante programación.  <br/> Si se establece en **True**, los usuarios con los permisos apropiados pueden realizar estas acciones.  <br/> |
|**LockLayout** <br/> |Especifica si los elementos web dentro de la zona se pueden agregar, eliminar, cambiar de tamaño o mover. Esta propiedad funciona igual tanto si el elemento web está en la vista personal o en la vista compartida.  <br/> Si se establece en **True**, las propiedades específicas de cada elemento web de la zona que resultan afectadas son: **Zona (ZoneID)**, **Orden de elemento (PartOrder)**, **Visible en la página (IsVisible)**, **Alto (Height)**, **Ancho (Width)**, **Permitir cerrar (AllowRemove)** e **IsIncluded** (el comando **Cerrar** del menú **Elemento web**). Otras propiedades de elemento web no resultan afectadas.  <br/> Si se establece en **False**, las propiedades del elemento web determinan si se pueden hacer modificaciones (además de los permisos de sitio apropiados).  <br/> |
|**AllowCustomization** <br/> |Especifica si los valores de la propiedad compartida de los elementos web de la zona se pueden modificar.  <br/> Si se establece en **True**, los usuarios con los permisos apropiados pueden realizar cambios en los elementos web de la zona para todos los usuarios.  <br/> Si se establece en **False**, los usuarios no pueden realizar cambios en los elementos web de la zona en la interfaz de usuario de la vista compartida. Sin embargo, se pueden realizar cambios mediante programación y usando la página de mantenimiento de elementos web.  <br/> |
|**AllowPersonalization** <br/> |Especifica si los valores de la propiedad personal de los elementos web de la zona se pueden modificar.  <br/> Si se establece en **True**, los usuarios con los permisos apropiados pueden realizar cambios personales en los elementos web de la zona.  <br/> Si se establece en **False**, los usuarios no pueden realizar cambios personales en los elementos web mediante la interfaz de usuario, a menos que el elemento web sea privado y tengan los permisos apropiados.  <br/> |
   

> **NOTA**
> No puede insertar una zona de elementos web dentro de un panel de canales de dispositivo. Si quiere permitir que los autores agreguen elementos web a una página, y no le preocupa el tamaño de la página para los dispositivos móviles, puede agregar un campo de página Editor de texto enriquecido a un panel de canales de dispositivo y después, indicar a los autores que agreguen elementos web al mismo. Puede agregar elementos web directamente a un panel de canales de dispositivo (sin una zona de elementos web). Para obtener más información, consulte  [Cómo: agregar un fragmento de código de Panel de canal de dispositivo en SharePoint 2013](how-to-add-a-device-channel-panel-snippet-in-sharepoint-2013.md). 
  
    
    


## Insertar un fragmento de código de zona de elementos web
<a name="InsertSnippet"> </a>

Igual que todos los fragmentos de código, este se agrega desde la Galería de fragmentos de código. Para navegar hasta la Galería de fragmentos de código, primero debe seleccionar un diseño de página para editar. Las zonas de elementos web se pueden agregar a los diseños de página pero no a las páginas maestras.
  
    
    

### Para insertar un fragmento de código de zona de elementos web


1. Vaya a su sitio de publicación.
    
  
2. En la esquina superior derecha de la página, elija el icono de Configuración y, después, elija **Administrador de diseño**.
    
  
3. En el Administrador de diseño, en el panel de navegación izquierdo, elija **Editar diseños de página**.
    
  
4. Seleccione el nombre del diseño de página al que quiere agregar el fragmento de código.
    
  
5. Para abrir la Galería de fragmentos de código, elija **Fragmentos de código** en la esquina superior derecha de la vista previa del lado del servidor.
    
  
6. En la cinta, en la pestaña **Diseño**, elija **Zona de elementos web**.
    
  
7. En el lado derecho de la Galería de fragmentos de código, en **Acerca de este componente**, haga clic o seleccione los encabezados de sección para expandir o contraer los grupos de propiedades y después, configure las opciones personalizadas que quiera.
    
    La sección **Importante** contiene las propiedades que son fundamentales para el funcionamiento de este fragmento de código determinado. El fragmento de código tiene un identificador único para una zona de elementos web. Después de copiar el fragmento de código en su diseño de página, no debe reutilizar este identificador. Si quiere agregar otro fragmento de código de zona de elementos web, elija **Actualizar** para generar un identificador nuevo para el siguiente fragmento de código.
    
    Para ver las descripciones de las propiedades que son necesarias para restringir una zona de elementos web ( **LockLayout**, **AllowCustomization** y **AllowPersonalization**), consulte la tabla 1.
    
    > **NOTA**
      > Quizás note que algunos nombres de propiedad están en negrita en la cuadrícula de propiedades de la Galería de fragmentos de código. Estas propiedades tienen valores que han cambiado respecto al valor predeterminado para este componente, pero no son necesariamente relevantes en un escenario de desarrollador. En otras palabras, una propiedad puede estar en negrita pero no ser necesariamente importante para su escenario. 
8. Después de configurar las propiedades, elija **Actualizar**. Así se actualiza el fragmento de código HTML en el lado izquierdo de la página, para que el marcado refleje los cambios. Siempre puede elegir **Restablecer** para devolver todas las propiedades a sus configuraciones predeterminadas.
    
  
9. En el lado izquierdo de la Galería de fragmentos de código, en **Fragmento de código HTML**, elija **Copiar al Portapapeles**.
    
  
10. En su editor HTML, abra la unidad de red asignada en su equipo y después, abra el archivo HTML de la página maestra o diseño de página a la que quiere agregar el fragmento de código.
    
    Para obtener más información, consulte  [Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
    
  
11. En el archivo HTML, pegue el fragmento de código en el lugar donde quiere que aparezca el marcado.
    
    Cuando agregue el fragmento de código a un diseño de página, asegúrese de pegar el fragmento de código dentro de **PlaceHolderMain**.
    
  
12. Reemplace la etiqueta **<div>** donde `class="DefaultContentBlock"` por su propio contenido específico.
    
  
13. Si quiere volver a rellenar la zona con elementos web (por ejemplo, si la zona restringirá a los autores de contenido para que solo modifiquen los elementos web existentes y no puedan agregar nuevos), inserte fragmentos de código de elementos web donde aparezca la etiqueta **<!--DC … -->**.
    
  
14. Guarde la página y actualice la vista previa del lado del servidor en el Administrador de diseño para asegurarse de que la página se muestra tal y como se espera.
    
  

## Descripción del marcado del fragmento de código
<a name="UnderstandMarkup"> </a>

Las dos partes más importantes de un fragmento de código de zona de elementos web son la propiedad **ID** y el comentario **<!--DC … -->**. Cada zona debe tener un identificador único. Si quiere agregar más de una zona de elementos web a su diseño de página, asegúrese de elegir **Actualizar** en la Galería de fragmentos de código antes de copiar cada fragmento de código para que se genere un nuevo identificador. El comentario **<!--DC … -->** debe reemplazarse con los elementos web que quiera que aparezcan en la zona de forma predeterminada.
  
    
    
En el siguiente código se muestran otras propiedades que se pueden usar para restringir la manera en que los autores de contenido pueden usar las zonas **AllowCustomization**, **AllowPersonalization** y **LockLayout**.
  
    
    

> **NOTA**
> Las propiedades **AllowCustomization**, **AllowPersonalization** y **LockLayout** aparecen en el marcado solo si cambia sus valores predeterminados en la cuadrícula de propiedades.
  
    
    




```HTML

<div data-name="WebPartZone">
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <div xmlns:ie="ie">
        <!--MS:<WebPartPages:WebPartZone runat="server" ID="x0e5f5212505f48a9aac43df13eeae4f9" AllowCustomization="True" AllowPersonalization="False" FrameType="TitleBarOnly" LockLayout="True" Orientation="Vertical">-->
            <!--MS:<ZoneTemplate>-->
               <!--DC: Replace this comment with default web parts for new pages. -->
            <!--ME:</ZoneTemplate>-->
        <!--ME:</WebPartPages:WebPartZone>-->
    </div>
    <!--CE: End Web Part Zone Snippet-->
</div>

```


## Recursos adicionales
<a name="AdditionalResources"> </a>


-  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md)
    
  
-  [Clase WebPartZone](http://msdn.microsoft.com/es-es/library/system.web.ui.webcontrols.webparts.webpartzone.aspx)
    
  
-  [Propiedades de WebPartZoneBase](http://msdn.microsoft.com/es-es/library/335sw9k3.aspx)
    
  
-  [Crear sitios para SharePoint](build-sites-for-sharepoint.md)
    
  
-  [Desarrollar el diseño del sitio en SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  

