---
title: Cómo crear una página maestra minimalista en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 634aa471-07e1-41d6-aa80-27f7ef7e9dc8
---


# Cómo: crear una página maestra minimalista en SharePoint 2013
Una página maestra mínima contiene solo aquellos elementos que son requeridos por la página SharePoint 2013 para representar la página correctamente en el explorador. Con el Administrador de diseño, puede crear rápidamente una página maestra mínima sin tener primero que diseñar y convertir un archivo HTML.
## Introducción a la página maestra mínima
<a name="Introduction"> </a>

Con el Administrador de diseño, puede convertir un archivo HTML normal en una página principal SharePoint 2013. Sin embargo, si no tiene una maqueta preconstruida, puede empezar rápidamente desde el principio mediante la creación de una página maestra mínima. La página maestra mínima contiene solo los elementos de página requeridos por SharePoint para procesar la página en el explorador.
  
    
    
Al crear una página maestra mínima, le Administrador de diseño crea el archivo .master y un archivo HTML asociado, por lo que puede seguir trabajando con solo el archivo HTML si lo prefiere. Trabajar con una página maestra mínima es exactamente lo misma que trabajar con una página maestra que se convierte desde un archivo HTML. El archivo HTML y la página principal están asociados, por lo que siempre que edite y guarde el archivo HTML, esos cambios se sincronizan con la página maestra asociada. Y el archivo HTML contiene tipos especiales de marcado que posibilitan la sincronización con el archivo .master. Para obtener más información sobre esta asociación y estos tipos de marcado, consulte  [Cómo convertir un archivo HTML en una página maestra en SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md).
  
    
    
Partir de una página maestra mínima es útil cuando:
  
    
    

- Desea empezar rápidamente desde el principio y, a continuación, crear el diseño en el archivo HTML que está asociado con la página maestra mínima, en lugar de a partir de un archivo HTML de maqueta.
    
  
- Desea probar rápidamente o crear el prototipo de un elemento de diseño que requiere una página maestra funcional de SharePoint. Por ejemplo, crear una página maestra mínima no requiere preparar un archivo HTML para la conversión o resolver cualquier error de vista previa que resulten del marcado que no es válido en el archivo HTML. Esto significa que puede trabajar inmediatamente con la vista previa del lado del servidor o la Galería de fragmentos.
    
  
- Desea trabajar directamente con el archivo .master. Si es un desarrollador de ASP.NET o de SharePoint, puede crear una página maestra mínima, quitar la asociación entre el archivo HTML y el archivo .master desactivando la casilla **Archivo asociado** en las propiedades del archivo HTML y, a continuación, trabajando directamente con el archivo .master.
    
  

## Crear una página maestra mínima
<a name="CreateMinimalMaster"> </a>


  
    
    

### Para crear una página maestra mínima


1. Vaya a su sitio de publicación.
    
  
2. En la esquina superior derecha de la página, elija **Configuración** y luego **Administrador de diseño**.
    
  
3. En el Administrador de diseño, en el panel de navegación izquierdo, elija **Editar páginas maestras**.
    
  
4. Elija **Crear una página maestra mínima**.
    
  
5. En el cuadro de diálogo **Crear una página maestra**, escriba un nombre para la página maestra y, a continuación, elija **Aceptar**.
    
    En este momento, SharePoint crea un archivo .master y un archivo HTML asociado con el mismo nombre en la Galería de páginas maestras.
    
    En el Administrador de diseño, el archivo HTML ahora aparece con **Se realizó la conversión** mostrado en la columna Estado.
    
  
6. Siga el vínculo de la columna Estado para obtener una vista previa del archivo.
    
    La página de vista previa es una previsualización dinámica del servidor de la página maestra.
    
    Para obtener más información sobre cómo mostrar una vista previa de la página maestra con diferentes páginas, vea  [Cómo: cambiar la página de vista previa en el Administrador de diseño de SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md).
    
    La página de vista previa también contiene un vínculo **Fragmentos** en la esquina superior derecha. Este vínculo abre la Galería de fragmentos, donde puede comenzar a reemplazar los bocetos de controles o los controles estáticos de su diseño por los controles dinámicos de SharePoint. Para obtener más información, consulte [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
    Después de mostrar la vista previa de su página maestra correctamente, verá que se agrega una etiqueta **<div>** al archivo HTML. Puede que tenga que desplazarse al final de la página para ver la etiqueta **<div>**.
    
    Esta etiqueta **<div>** es el bloque de contenido principal. Reside dentro de un marcador de posición de contenido llamado **ContentPlaceHolderMain**. En tiempo de ejecución, cuando un visitante explora el sitio y solicita una página, este marcador de posición se llena con contenido procedente de un diseño de página que incluye contenido en una región de contenido coincidente. Debe colocar esta etiqueta **<div>** en el lugar donde quiera que aparezcan los diseños de página en la página maestra.
    
  
7. Puede editar el archivo HTML que se encuentra directamente en el servidor usando un editor de HTML para abrir y editar el archivo HTML en una unidad asignada. Cada vez que guarde el archivo HTML, los cambios se sincronizan con el archivo .master asociado. Para obtener más información, vea  [Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
    
  
8. Para trabajar solo con el archivo .master y no con el archivo HTML, deberá romper la asociación entre los dos archivos. En el Administrador de diseño, en la página de Editar páginas maestras, seleccione el código HTML del archivo, abra el menú **Propiedades** y elija **Editar propiedades**. En la ficha **Edición**, desmarque la casilla **Archivo asociado** y, a continuación, elija **Guardar**.
    
    Romper la asociación permite trabajar directamente con el archivo .master y guardar los cambios sin necesidad de que se sobrescriban con los cambios realizados en el archivo HTML. Puede restaurar esta asociación en cualquier momento. Si restaura la asociación, el archivo HTML asociado se sincroniza con el archivo .master y lo sobrescribirá.
    
  

## Comprender el archivo HTML asociado
<a name="UnderstandHTML"> </a>

Cuando se crea una página maestra mínima, se crea un archivo HTML que está asociado con el archivo .master y este archivo HTML contiene muchas líneas de marcado específicas de cómo SharePoint 2013 funciona. Puede pasar por alto la mayor parte de este marcado, y gran parte de él no aparece en el marcado final del sitio al ver el código fuente en el explorador, pero este marcado es fundamental para cambios de sincronización desde el archivo HTML en el archivo .master que SharePoint 2013 usa realmente. Cada vez que guarde un cambio en el archivo HTML, este marcado de SharePoint hace posible para ese mismo cambio que pueda introducirse en el archivo .master asociado en segundo plano. Para más información, vea el ejemplos de marcado en  [Cómo convertir un archivo HTML en una página maestra en SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md).
  
    
    

## Recursos adicionales
<a name="Additional"> </a>


-  [Información general sobre el Administrador de diseño de SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Cómo convertir un archivo HTML en una página maestra en SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md)
    
  

