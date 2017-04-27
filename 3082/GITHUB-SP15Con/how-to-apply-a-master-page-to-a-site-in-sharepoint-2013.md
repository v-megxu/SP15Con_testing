---
title: Aplicar una página maestra a un sitio de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 04861390-84d5-40ea-b0db-6c0748eff196
---


# Aplicar una página maestra a un sitio de SharePoint 2013
Aprenda a asignar una página maestra a un sitio de SharePoint 2013.
## Asignar una página maestra a un sitio

En SharePoint 2013, una página maestra define los elementos compartidos de tramas, como el contenedor visual de todas las páginas de un sitio. Después de crear una página maestra, se puede asignar a un sitio. Se puede hacer con todas las páginas de publicación designadas a todos los usuarios o con las páginas administrativas que se usan para el mantenimiento del sitio. Otra opción es, al configurar un sitio secundario de un sitio primario, heredar la página maestra de la principal. Este artículo recoge los pasos para asignar a un sitio una página maestra creada, heredar la página maestra del sitio principal o asignar una página maestra al canal de un dispositivo determinado.
  
    
    

> **NOTA**
> Para obtener más información sobre el Administrador de diseño y las páginas maestras, consulte  [Información general sobre el Administrador de diseño de SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md). Para obtener más información sobre cómo crear canales de dispositivo, consulte  [Canales de dispositivos del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-device-channels.md). 
  
    
    


### Para asignar una página maestra a un sitio de SharePoint


1.  En la **Configuración del sitio** del sitio designado, en la sección **Apariencia**, elija **Página maestra**.
    
    > **NOTA**
      > Si el vínculo **Página maestra** no está, tiene que habilitar la característica de publicación siguiendo estos pasos. Vaya a **Configuración del sitio | Administración de la colección de sitios | Características de la colección de sitios**. Desplácese hasta la característica **Infraestructura de publicación de SharePoint Server** y pulse **Activar**. 
2. En **Configuración de la página maestra del sitio**, seleccione una de las dos opciones para las secciones **Página maestra del sitio** o **Página maestra del sistema**:
    
  - **Heredar del sitio principal la página maestra del sitio**: elija esta opción si va a configurar un sitio secundario de SharePoint y quiere usar la página maestra principal. 
    
    > **NOTA**
      > Cuando se trabaja con el sitio principal de primer nivel, esta opción no está disponible. 
  - **Especificar una página maestra para este sitio y todos los sitios que hereden de éste su configuración de página**: elija esta opción si quiere asignar una página maestra concreta al sitio o para páginas administrativas. Verá un cuadro desplegable denominado **Predetermiando** o **Todos los canales**, según la configuración del sitio o el sistema, en el que podrá seleccionar un página maestra determinada almacenada en la galería de páginas maestras. Seleccione la página que quiera en este cuadro desplegable.
    
    > **NOTA**
      > Si tiene configurado algún canal de dispositivo, verá otros cuadros desplegables con opciones adicionales para la asignación de páginas maestras. 
3. Elija **Aceptar**.
    
  

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Desarrollar el diseño del sitio en SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Información general sobre el Administrador de diseño de SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Novedades sobre el desarrollo de sitios de SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md)
    
  

