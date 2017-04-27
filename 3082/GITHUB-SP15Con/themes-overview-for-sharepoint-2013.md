---
title: Introducción a los temas para SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: ae585dd3-82fe-46bb-ac93-065edc0a16f4
---


# Introducción a los temas para SharePoint 2013
Conozca la experiencia de creación de temas en SharePoint 2013 y cómo se pueden usar para personalizar la apariencia de los sitios.
## Introducción a los temas
<a name="section1"> </a>

Los temas ofrecen una forma rápida y fácil de aplicar una personalización de marca ligera a un sitio de SharePoint 2013. Un tema permite al propietario del sitio o a los usuarios que tengan derechos de diseñador personalizar un sitio cambiando su diseño, la paleta de colores, la combinación de fuentes y la imagen de fondo.
  
    
    
La experiencia de creación de temas en SharePoint 2013 se ha rediseñado para simplificar el proceso de personalización de sitios. La interfaz de usuario de temas se ha renovado y ahora hay un conjunto de formatos de archivo nuevos relacionados con los temas. El asistente **Cambiar la apariencia** es el punto de partida de la experiencia de creación de temas, donde puede cambiar la apariencia de los sitios. Puede seleccionar un diseño para el sitio y luego personalizarlo cambiando la disposición del sitio, el fondo, la paleta de colores o la combinación de fuentes. Puede obtener una vista previa del sitio antes de aplicar el diseño. Para más información, vea [Elegir un tema para el sitio de su publicación](http://office.microsoft.com/es-es/office365-sharepoint-online-enterprise-help/choose-a-theme-for-your-publishing-site-HA102891580.aspx) en Office.com.
  
    
    

> **NOTA**
> Los temas creados en SharePoint 2010 no se pueden usar en los sitios de SharePoint 2013, pero los temas creados en SharePoint 2010 sí se pueden usar en las colecciones de sitios que no se han actualizado o en las colecciones de sitios que usan la versión de la experiencia de 2010. 
  
    
    


## Componentes de la experiencia de creación de temas
<a name="section2"> </a>

La experiencia de creación de temas incluye lo siguiente:
  
    
    
 **Paleta de colores**: una paleta de colores o combinación de colores define la combinación de colores que se usan en un sitio. Con SharePoint 2013 vienen instaladas 32 paletas de colores. Los usuarios las pueden usar cuando eligen modificar un diseño en la galería de diseños.
  
    
    
Las paletas de colores son archivos XML (archivos .spcolor). Están almacenados en la Galería de temas del sitio raíz de la colección de sitios en la carpeta **15** (http:// _NombreDeColecciónDeSitios_/_catalogs/theme/15/).
  
    
    
 **Combinación de fuentes**: una combinación de fuentes define las fuentes que se usan en un sitio. Con SharePoint 2013 se incluyen siete combinaciones de fuentes. Los usuarios las pueden usar cuando eligen modificar un diseño en la galería de diseños.
  
    
    
Las combinaciones de fuentes son archivos XML (archivos .spfont). Están almacenados en la Galería de temas del sitio raíz de la colección de sitios en la carpeta **15** (http:// _NombreDeColecciónDeSitios_/_catalogs/theme/15/).
  
    
    
 **Imagen de fondo**: es la imagen de fondo que se usa en el sitio.
  
    
    
 **Página maestra**: una página maestra define el cromo (los elementos de marco compartidos) de un sitio. La experiencia de creación de temas permite a los usuarios seleccionar la página maestra que quieren aplicar a un sitio.
  
    
    
 **Vista previa de página maestra**: la vista previa de página maestra se usa para representar la imagen preliminar de los componentes de tema seleccionados. Todas las páginas maestras deben tener un archivo correspondiente de vista previa de página maestra para que la página maestra esté disponible en la experiencia de creación de temas.
  
    
    
Los archivos de vista previa de página maestra (archivos .preview) se almacenan en la Galería de páginas maestras del sitio (http://  _NombreDelSitio_/_catalogs/masterpage/).
  
    
    
 **Apariencia compuesta**: una apariencia compuesta o diseño consta de la paleta de colores, la combinación de fuentes, la imagen de fondo y la página maestra que determinan la apariencia de un sitio. El diseño y el tema se pueden usar indistintamente para describir la apariencia global de un sitio.
  
    
    
La experiencia de creación de temas usa la lista Apariencias compuestas para ver cuáles son los diseños disponibles. Puede elaborar diseños adicionales creando elementos de lista en la lista Apariencias compuestas. Para obtener acceso a la lista de apariencias compuestas, en la página **Configuración del sitio**, en **Galerías del diseñador web**, elija **Apariencias compuestas**.
  
    
    
 **Cambiar la apariencia**: el asistente **Cambiar la apariencia** es el punto de partida de la experiencia de creación de temas, donde los usuarios pueden cambiar la apariencia de los sitios. Para obtener acceso al asistente **Cambiar la apariencia**, elija el icono **Configuración** y luego elija **Cambiar la apariencia**.
  
    
    
 **Galería de diseños**: la galería de diseños es la primera página del asistente **Cambiar la apariencia**. Esta galería muestra una vista en miniatura de los diseños disponibles.
  
    
    

## Usar los temas
<a name="section3"> </a>

SharePoint 2013 incluye temas preinstalados (también denominados diseños o apariencias compuestas). Puede usar temas preinstalados o crear temas personalizados.
  
    
    

### Temas preinstalados

La experiencia de creación de temas permite a los usuarios personalizar los temas preinstalados cambiando los colores, las fuentes, el diseño o la imagen de fondo. No es necesario crear temas personalizados a menos que quiera combinaciones de fuentes o paletas de colores adicionales.
  
    
    
Cuando se modifica un tema preinstalado, automáticamente se crea un tema nuevo llamado Actual después de aplicarse los cambios al tema. Solo puede haber un tema Actual por cada sitio. SharePoint 2013 no permite al usuario guardar temas desde la interfaz de usuario. Si modifica un tema preinstalado, aplique los cambios (creando un tema nuevo llamado Actual) y luego modifique un segundo tema preinstalado; el segundo tema preinstalado se convierte en el tema Actual cuando se aplica la configuración. Para guardar un tema modificado, puede crear un elemento de lista en la lista Apariencias compuestas que contenga las mismas direcciones URL de página maestra, paleta de colores, combinación de fuentes e imagen de fondo que el tema modificado (el tema modificado aparece como el actual en la lista Apariencias compuestas).
  
    
    

### Temas personalizados

Puede elaborar temas personalizados creando paletas de colores y combinaciones de fuentes adicionales y subiéndolas a la Galerías de temas. Hecho esto, las paletas de colores y las combinaciones de fuentes nuevas estarán disponibles en la experiencia de creación de temas o cuando quiera aplicar un tema mediante programación. De igual modo, si quiere poder elegir entre más diseños de sitio, puede subir páginas maestras adicionales, con sus archivos de vista previa correspondientes, a la Galería de páginas maestras.
  
    
    
Puede elaborar diseños nuevos creando elementos de lista nuevos en la lista Apariencias compuestas. Cree un elemento de lista y especifique la página maestra, la paleta de colores, la combinación de fuentes y la imagen de fondo del nuevo diseño.
  
    
    

## Recursos adicionales
<a name="section4"> </a>


-  [Capacidades de personalización de marca y diseño de SharePoint 2013 Design Manager](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  
-  [Cómo: crear un archivo de vista previa de página maestra en SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [Procedimiento para implementar un tema personalizado en SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [Paletas de colores y fuentes de SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [Blog del equipo de SharePoint: presuma de estilo con los temas de SharePoint](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  

