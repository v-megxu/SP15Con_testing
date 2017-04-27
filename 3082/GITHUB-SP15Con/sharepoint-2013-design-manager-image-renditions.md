---
title: Representaciones de imágenes del Administrador de diseño de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: d08a74c0-5674-4f26-8646-11ea1f081c85
---


# Representaciones de imágenes del Administrador de diseño de SharePoint 2013
Descubra cómo crear una representación de imágenes, cómo agregarla a una página y recortarla. Una representación de imágenes define las dimensiones que se usan para mostrar imágenes en los sitios de publicación de SharePoint.
Las representaciones de imágenes permiten mostrar versiones de diferentes tamaños de una imagen en distintas páginas de un sitio de publicación, en función de la misma imagen de origen. Al crear una representación de imágenes, especifique el ancho o el alto de todas las imágenes que usan esa representación de imágenes. Las representaciones de imágenes están disponibles para todas las imágenes que se cargan en una biblioteca de esa colección de sitios. Por ejemplo, los diseñadores pueden crear una representación de imágenes para mostrar imágenes en miniatura y otra representación de imágenes para mostrar imágenes de pancarta. Cuando se agrega una imagen a una página, el autor puede especificar la representación de imágenes para usar en dicha imagen. Los autores también pueden recortar la representación de imágenes para especificar la parte de la imagen que desean usar en la representación de imágenes. Cuando se representa la página, se muestra el tamaño correcto de la imagen.
  
    
    

Las representaciones de imágenes permiten representar una sola imagen de varias maneras. Se puede mostrar una imagen en varios tamaños o con recortes diferentes. La primera vez que se solicita una imagen, SharePoint Server usa la representación de la imagen especificada para generar la imagen. Cuando un usuario ve un sitio de SharePoint, el tamaño correcto de versión de la imagen se descarga en el equipo cliente. Esto reduce el tamaño del archivo que se descarga en el cliente, lo que mejora el rendimiento del sitio.
## Requisitos previos para la administración de representaciones de imágenes
<a name="Prerequisites"> </a>

Dado que las representaciones de imágenes tienen dependencias en otras características de SharePoint Server 2013, asegúrese de que cumple los requisitos previos de esta sección antes de realizar los procedimientos descritos en este tema. Entre los requisitos previos se incluyen:
  
    
    

- **Una colección de sitios de publicación** La colección de sitios a la que se van a agregar representaciones de imágenes debe haberse creado con la plantilla de colección de sitios de Catálogo de productos o Portal de publicación. O bien, las características de publicación deben estar habilitadas en la colección de sitios donde se van a usar representaciones de imágenes. Para obtener más información, vea [Introducción a la publicación en sitios de Internet, intranet y extranet](http://technet.microsoft.com/es-es/library/jj635881%28office.15%29.aspx) en la Biblioteca de TechNet.
    
  
- **Una memoria caché BLOB configurada** La memoria caché BLOB basada en disco controla el almacenamiento en caché de objetos binarios grandes (BLOB), como archivos frecuentemente utilizados de imágenes, audio y vídeo, y otros archivos que se usan para mostrar páginas web, como archivos .css y archivos .js. La memoria caché BLOB debe estar habilitada en cada servidor front-end web donde desea usar representaciones de imágenes. Si la memoria caché BLOB no está habilitada, se usa siempre la imagen original. Para obtener más información, vea [Configuración de la memoria caché para una aplicación web](http://technet.microsoft.com/es-es/library/cc770229.aspx) en la Biblioteca de TechNet.
    
  
- **Una biblioteca de activos (recomendado)** Puede usar la plantilla de biblioteca de activos para configurar una biblioteca que facilite el almacenamiento, la organización y la búsqueda de activos de medios enriquecidos, como archivos de imagen, audio o vídeo. Para obtener más información, vea [Configurar una biblioteca de activos para almacenar archivos de imagen, audio o vídeo](http://office.microsoft.com/es-es/sharepoint-server-help/set-up-an-asset-library-to-store-image-audio-or-video-files-HA102785730.aspx) en Office.com.
    
  

## Crear una representación de imágenes
<a name="Create"> </a>

Cuando se crea una representación de imágenes, SharePoint Server 2013 crea un identificador único que identifica esta representación de imágenes. Se genera una imagen cuando SharePoint Server recibe una solicitud para la representación de imágenes por primera vez.
  
    
    

### Para crear una representación de imágenes


1. Compruebe que la cuenta de usuario que está realizando este procedimiento tenga, como mínimo, permisos de diseño en el sitio de nivel superior de la colección de sitios.
    
  
2. En un explorador, vaya al sitio de nivel superior de la colección de sitios de publicación.
    
  
3. Elija el icono **Configuración**. En la página **Configuración del sitio**, en la sección **Aspecto**, elija **Representaciones de imágenes**.
    
    > **NOTA**
      > La página Representaciones de imágenes también se puede abrir desde la página principal predeterminada del sitio de publicación. En la sección **Soy el diseñador visual**, elija **Configurar representaciones de imágenes**. 
4. En la página **Representaciones de imágenes**, elija **Agregar nuevo elemento**.
    
  
5. En la página **Nueva representación de imagen**, en el cuadro **Nombre**, escriba un nombre para la representación. Por ejemplo, escriba Miniatura_pequeña.
    
  
6. En los cuadros de texto **Ancho** y **Alto**, escriba el ancho y alto, en píxeles, de la representación y luego elija **Guardar**.
    
  

## Editar una representación de imágenes
<a name="Edit"> </a>

Cuando se edita una representación de imágenes, las nuevas dimensiones surten efecto la próxima vez que se solicita la imagen. Si hay una imagen que se generó anteriormente en la representación de imágenes, la imagen se regenera con las dimensiones nuevas la próxima vez que se solicita la imagen.
  
    
    

### Para editar una representación de imágenes


1. Compruebe que la cuenta de usuario que está realizando este procedimiento tenga, como mínimo, permisos de diseño en el sitio de nivel superior de la colección de sitios.
    
  
2. En un explorador, vaya al sitio de nivel superior de la colección de sitios de publicación.
    
  
3. Elija el icono **Configuración**. En la página **Configuración del sitio**, en la sección **Aspecto**, elija **Representaciones de imágenes**.
    
    > **NOTA**
      > La página **Representaciones de imágenes** también se puede abrir desde la página principal predeterminada del sitio de publicación. En la sección **Soy el diseñador visual**, elija **Configurar representaciones de imágenes**. 
4. En la página **Representaciones de imágenes**, elija la representación de imagen que desea editar.
    
  
5. En la página **Editar representación de imagen**, modifique el nombre, el ancho o el alto de la representación de imagen.
    
  

## Agregar una representación de imágenes
<a name="Add"> </a>

Al agregar una imagen a una página en un sitio de publicación de SharePoint, puede especificar la representación de imagen que se usará para esa imagen. Cuando se represente la página en un explorador, se muestra el tamaño de la imagen correcta. Puede especificar la representación de imagen en el Editor de texto enriquecido, en un control de campo de imagen o en la dirección URL de la imagen.
  
    
    

### Especificar la representación de imagen con el Editor de texto enriquecido

Cuando se inserta una imagen en una página, puede especificar la representación de imágenes que se va a usar para que se muestre el tamaño de la imagen correcta cuando se represente la página. Puede especificar la representación de imagen en el Editor de texto enriquecido solo para las imágenes que se almacenan en la misma colección de sitios como la página que se está editando.
  
    
    

### Para especificar la representación de imagen con el Editor de texto enriquecido


1. En la pestaña **Página**, seleccione **Editar**.
    
  
2. Elija el icono **Configuración** y luego **Agregar una página**.
    
  
3. En la ventana **Agregar una página**, escriba un nombre para la página y luego elija **Crear**.
    
  
4. Coloque el puntero en el campo **Contenido de la página**.
    
  
5. En la pestaña **Insertar**, elija **Imagen** y, después, **De SharePoint**.
    
  
6. Busque la imagen que desea agregar a la página, seleccione la imagen y después elija **Insertar**. La imagen se mostrará en tamaño completo.
    
  
7. En el grupo **Seleccionar** de la pestaña **Diseño**, elija **Seleccionar representación** y después seleccione una representación de imágenes. La imagen se mostrará según el tamaño especificado para la representación de imagen.
    
    > **NOTA**
      > El comando **Seleccionar representación** está disponible solamente para las imágenes que se almacenan en la misma colección de sitios como la página que se está editando.
8. Si desea recortar la representación de imagen, elija **Seleccionar representación** y luego elija **Editar representaciones**.
    
    Para más información sobre cómo recortar representaciones de imágenes, vea la sección  [Recortar una representación de imágenes](#Crop) de este artículo.
    
  

### Especificar la representación de imagen en la dirección URL de la imagen

Para especificar la representación de imagen, puede agregar los parámetros RenditionID, Ancho o Alto a la dirección URL de la imagen.
  
    
    
 **RenditionID** Use el parámetro RenditionID para especificar el identificador de la representación de imagen que se va a usar.
  
    
    
 **Ancho** Use el parámetro Ancho para especificar el ancho, en píxeles, de la representación de imagen. SharePoint Server intenta encontrar una representación de imágenes con el ancho especificado. A continuación, SharePoint Server intenta encontrar una representación de imágenes con un ancho mayor que el ancho especificado. Si hay varias representaciones de imágenes que coinciden con este criterio, SharePoint Server usa la representación de imagen con el ancho más cercano a lo especificado. Si no hay ninguna representación de imagen con un ancho que sea igual o mayor que el ancho especificado, se usa la imagen original.
  
    
    
 **Alto** Use el parámetro Alto para especificar el alto, en píxeles, de la representación de imagen. SharePoint Server intenta encontrar una representación de imágenes con el alto especificado. A continuación, SharePoint Server intenta encontrar una representación de imágenes con un alto mayor que el alto especificado. Si hay varias representaciones de imágenes que coinciden con este criterio, SharePoint Server usa la representación de imagen con el alto más cercano a lo especificado. Si no hay ninguna representación de imagen con un alto que sea igual o mayor que el alto especificado, se usa la imagen original.
  
    
    
 **Ancho y alto** Si se especifican parámetros de ancho y alto, SharePoint Server intenta encontrar una representación de imágenes con el ancho y alto especificados. A continuación, SharePoint Server intenta encontrar una representación más cercana a la proporción de ancho y alto especificada. Si hay varias coincidencias, se elige la representación de imagen con la mayor proporción de ancho y alto más cercana al tamaño solicitado.
  
    
    

> **NOTA**
> Si la dirección URL de la imagen incluye el parámetro RenditionID y los parámetros Ancho y Alto, se omiten los parámetros Ancho y Alto. 
  
    
    

En el ejemplo siguiente se muestra cómo usar el parámetro RenditionID:
  
    
    



```HTML

<img src="/sites/pub/Assets/Lighthouse.jpg?RenditionID=2" />
```

En el ejemplo siguiente se muestra cómo usar los parámetros Ancho y Alto:
  
    
    



```HTML
<img src="/sites/pub/Assets/Lighthouse.jpg?Width=400&amp;Height=200" />
```


### Especificar la representación de imagen en el control de campo de la imagen

Un desarrollador puede especificar la representación de imágenes para usar en el control de campo de la imagen. Use la propiedad **RenditionId** para establecer el identificador de la representación de imagen. Para obtener más información, vea **RenditionId**.
  
    
    

## Recortar una representación de imágenes
<a name="Crop"> </a>

De forma predeterminada, se genera una representación de imágenes desde el centro de la imagen. Puede ajustar la representación de imagen para imágenes individuales al recortar la parte de la imagen que desea usar. Por ejemplo, si una foto muestra una escena de un faro pero la representación de imagen no muestra todo el faro (vea la figura 1), puede cambiar el área de la imagen seleccionada para que se muestre todo el faro (vea la figura 2). 
  
    
    

**Ilustración 1. Representación de imagen original**

  
    
    

  
    
    
![Representación de imagen original](images/ImgRendition_orig.PNG)
  
    
    

**Ilustración 2. Representación de imagen recortada**

  
    
    

  
    
    
![Representación de imagen recortada](images/ImgRendition_crop.PNG)
  
    
    
Una representación de imágenes se puede recortar en la biblioteca de activos o en una página, sin cambiar la imagen original. 
  
    
    
Las representaciones de imágenes se pueden recortar de las siguientes maneras:
  
    
    

- Los diseñadores pueden recortar una representación de imágenes en la biblioteca de activos. Por ejemplo, un diseñador quiere especificar cómo aparece una imagen en la representación de imágenes en miniatura.
    
  
- Los autores pueden recortar una representación de imágenes cuando insertan una imagen en una página. Esto les permite personalizar la apariencia de su página. Cuando un autor recorta una representación de imágenes, también se cambia la representación de dicha imagen. Cualquiera que use esta representación de imágenes verá la imagen recortada.
    
    > **NOTA**
      > Un autor puede recortar una representación de imágenes solo cuando la imagen original se almacena en una biblioteca que está en la misma colección de sitios como la página que se está editando. Por ejemplo, en escenarios de publicación entre sitios, un autor puede recortar la representación de imágenes solo si la imagen se almacena en la misma colección de sitios que el contenido del catálogo. De lo contrario, se debe recortar la representación de imágenes en la biblioteca de activos. 

### Recortar una representación de imágenes en la biblioteca de activos

Los diseñadores pueden recortar una representación de imágenes en la biblioteca de activos.
  
    
    

### Para recortar una representación de imágenes en la biblioteca de activos


1. Compruebe que la cuenta de usuario que está realizando este procedimiento tiene permisos de escritura en la biblioteca de activos donde se encuentra la imagen.
    
  
2. En un explorador, vaya a la biblioteca de activos.
    
  
3. Coloque el puntero en la esquina inferior derecha de la imagen cuya representación desea cambiar, seleccione los puntos suspensivos ( **...**) que aparecen y después elija **EDITAR REPRESENTACIONES**.
    
    > **NOTA**
      > También puede abrir la página **Editar representaciones** si coloca el puntero sobre la imagen de vista previa en la biblioteca de activos y después active la casilla que aparece en la parte inferior de la imagen de vista previa. A continuación, en la pestaña **Diseño**, elija **Editar representaciones**. 

    La página Editar representaciones muestra una imagen de vista previa de cada representación de la imagen que se define en la colección de sitios.
    
  
4. Busque la representación de imagen que desea cambiar y después **Haga clic para cambiar**.
    
  
5. En la ventana **Recortar representación**, use la herramienta de imágenes para seleccionar la parte de la imagen que desea usar en la representación de imagen.
    
  
6. Elija **Guardar**.
    
  
Si la imagen y la página que se está editando se encuentran en la misma colección de sitios, también puede recortar una representación de imágenes con el Editor de texto enriquecido.
  
    
    

### Recortar una representación de imágenes en una página

Los autores pueden recortar una representación de imágenes cuando insertan una imagen en una página. Esto les permite personalizar la apariencia de su página. Cuando un autor recorta una representación de imágenes, también se cambia la representación de dicha imagen. Cualquiera que use esta representación de imágenes verá la imagen recortada.
  
    
    

### Para recortar una representación de imágenes en una página


1. Compruebe que la cuenta de usuario que está realizando este procedimiento tiene permisos de escritura en la biblioteca de activos donde se encuentra la imagen.
    
  
2. En un explorador, vaya al sitio de SharePoint que contiene la imagen.
    
  
3. En la pestaña **Página**, seleccione **Editar**.
    
  
4. Seleccione la imagen que desee recortar.
    
  
5. En la pestaña **Imagen** de la cinta de opciones, en el grupo **Seleccionar**, elija **Seleccionar representación** y luego elija **Editar representaciones**.
    
    La página **Editar representaciones** muestra una imagen de vista previa de cada representación de la imagen que se define en la colección de sitios.
    
    > **NOTA**
      > El comando **Seleccionar representación** está disponible solamente para las imágenes que se almacenan en la misma colección de sitios como la página que se está editando.
6. Busque la representación de imagen que desea cambiar y después **Haga clic para cambiar**.
    
  
7. En la ventana **Recortar representación**, use la herramienta de imágenes para seleccionar la parte de la imagen que va a usar en la representación de imagen.
    
  
8. Elija **Guardar**.
    
  

## Eliminar una representación de imágenes
<a name="Delete"> </a>

Cuando se elimina una representación de imagen, esta representación ya no se genera para las imágenes. Si un sitio solicita la representación de imagen eliminada, se devuelve la imagen original.
  
    
    

### Para eliminar una representación de imágenes


1. Compruebe que la cuenta de usuario que está realizando este procedimiento tenga, como mínimo, permisos de diseño en el sitio de nivel superior de la colección de sitios.
    
  
2. En un explorador, vaya al sitio de nivel superior de la colección de sitios de publicación.
    
  
3. Elija el icono **Configuración**. En la página **Configuración del sitio**, en la sección **Aspecto**, elija **Representaciones de imágenes**.
    
    > **NOTA**
      > La página **Representaciones de imágenes** también se puede abrir desde la página principal predeterminada del sitio de publicación. En la sección **Soy el diseñador visual**, elija **Configurar representaciones de imágenes**. 
4. En la página **Representaciones de imágenes**, busque la representación de imagen que desea eliminar y luego elija **Eliminar**
    
  

## Recursos adicionales
<a name="Additional"> </a>


-  [Desarrollar el diseño del sitio en SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Capacidades de personalización de marca y diseño de SharePoint 2013 Design Manager](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  
-  [Crear sitios para SharePoint](build-sites-for-sharepoint.md)
    
  

