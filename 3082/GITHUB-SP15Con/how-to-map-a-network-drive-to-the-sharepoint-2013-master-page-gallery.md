---
title: Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 7d416f6e-2471-4d03-97ae-4e8d907784c6
---


# Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013
Descubra cómo asignar una unidad de red a la Galería de páginas maestras para que pueda usar el Administrador de diseño para cargar archivos de diseño en SharePoint Server 2013.
Puede crear un diseño visual para su sitio web con cualquier herramienta de diseño web o editor HTML y después usar el Administrador de diseño para importar el diseño en SharePoint. Para ello, debe asegurarse de que la herramienta de diseño almacene sus archivos en la Galería de páginas maestras del sitio, que es donde SharePoint espera encontrar los archivos. Se recomienda asignar una unidad de red a la Galería de páginas maestras facilitar el guardado de archivos en la ubicación correcta.
  
    
    

En primer lugar, busque la ubicación de la Galería de páginas maestras.
### Para buscar la ubicación de la Galería de páginas maestras


1. En el sitio para el que va a crear un diseño, inicie el Administrador de diseño. (Por ejemplo, en el menú **Configuración**, elija **Administrador de diseño**).
    
    > **IMPORTANTE**
      > Si su sitio está hospedado en SharePoint Online, al iniciar sesión en el sitio mediante las credenciales de Office 365, asegúrese de que activa la casilla **Mantener la sesión iniciada**. Para obtener más información, vea  [Cómo configurar y solucionar problemas en las unidades de red que se conectan a los sitios de SharePoint Online en Office 365 para empresas](http://support.microsoft.com/kb/2616712). 
2. En la lista numerada, seleccione **Cargar archivos de diseño**.
    
  
3. La página Administrador de diseño: cargar archivos de diseño contiene la ubicación de la Galería de páginas maestras. La ubicación probablemente termina en  `/_catalogs/masterpage/`. Esta es la ubicación en la que se asignará una unidad de red.
    
  
4. Tome nota de la ubicación de la Galería de páginas maestras o cópiela al Portapapeles.
    
  
En el equipo que ejecuta la herramienta de diseño o editor HTML, asigne una unidad de red a la ubicación que acaba de copiar. El procedimiento para asignar una unidad de red varía según el sistema operativo del equipo:
- Si el equipo ejecuta Windows 8, siga los pasos que se describen en la versión Windows 8 del artículo  [Crear un acceso directo para asignar una unidad de red](http://windows.microsoft.com/es-es/windows-8/create-shortcut-to-map-network-drive).
    
  
- Si el equipo ejecuta Windows 7, siga los pasos que se describen en la versión Windows 7 del artículo  [Crear un acceso directo para asignar una unidad de red](http://windows.microsoft.com/es-es/windows7/Create-a-shortcut-to-map-a-network-drive).
    
  
- Si el equipo ejecuta Windows Vista, siga los pasos que se describen en la versión del artículo  [Crear un acceso directo para asignar una unidad de red](http://windows.microsoft.com/es-es/windows-vista/Create-a-shortcut-to-map-a-network-drive).
    
  
- Si el equipo ejecuta Windows XP, siga los pasos que se describen en el artículo  [Cómo conectar y desconectar una unidad de red en Windows XP](http://support.microsoft.com/kb/308582).
    
  
- ** *Si el equipo ejecuta otro sistema operativo, siga las instrucciones para crear un acceso directo a una nueva ubicación para ese sistema operativo.* ** Tal vez tenga que proporcionar diferentes credenciales para conectarse al sitio de SharePoint y tenga que especificar que la conexión se restablezca cada vez que inicie sesión en el equipo.
    
  

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Aplicar una página maestra a un sitio de SharePoint 2013](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)
    
  
-  [Desarrollar el diseño del sitio en SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Canales de dispositivos del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-device-channels.md)
    
  
-  [Cómo: cambiar la página de vista previa en el Administrador de diseño de SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [Representaciones de imágenes del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-image-renditions.md)
    
  

