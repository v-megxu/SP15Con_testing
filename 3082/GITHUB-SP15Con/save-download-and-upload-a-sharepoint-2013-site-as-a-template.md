---
title: Guardar, descargar y cargar un sitio de SharePoint 2013 como una plantilla
ms.prod: SHAREPOINT
ms.assetid: 2e637172-ddac-4a70-bd77-55a1645a3db1
---


# Guardar, descargar y cargar un sitio de SharePoint 2013 como una plantilla
Obtenga información sobre el diseño y la creación de aplicaciones robustas mediante las plantillas de sitio de SharePoint.
Es posible diseñar y crear aplicaciones robustas de SharePoint 2013 que incluyan un rico conjunto de orígenes de datos, vistas y formularios utilizados por el cliente, flujos de trabajo altamente personalizados, etc. Una vez creado el sitio de la solución empresarial, se puede comenzar a usar de inmediato en el entorno de SharePoint. O bien, se puede convertir la solución en una plantilla e implementarla en otro entorno, ponerla a disposición de los usuarios para que puedan crear nuevos sitios a partir de ella o entregarla para desarrollo adicional en Visual Studio.
  
    
    


## Qué es una plantilla de sitio de SharePoint
<a name="bkmk_WhatIsTemplate"> </a>

Las plantillas de sitio de SharePoint son definiciones preintegradas diseñadas en torno a una necesidad empresarial concreta. Se pueden usar tal cual para crear un sitio propio de SharePoint y luego personalizarlo tanto como se desee. Es probable que ya esté familiarizado con las plantillas de sitio predeterminadas, como Sitio de grupo, Sitio de proyecto y Sitio de la comunidad.
  
    
    
Además de las plantillas predeterminadas, puede crear su propia plantilla de sitio basada en un sitio que haya creado y personalizado. Se trata de una eficaz característica que permite crear una solución personalizada y luego compartirla con colegas, toda la organización u organizaciones externas. También se puede empaquetar el sitio y abrirlo en otro entorno o aplicación como Visual Studio y además personalizarlo allí.
  
    
    
La conversión del sitio personalizado o la solución empresarial en una plantilla es una posibilidad extremadamente útil y muy eficaz. Una vez que se comienza a empaquetar la solución como una plantilla, se empieza a observar el potencial de SharePoint como plataforma de aplicaciones empresariales. La opción de plantilla de sitio hace posible todo esto.
  
    
    
Al guardar el sitio como una plantilla, se crea un paquete de soluciones web, o WSP. Un WSP es un archivo CAB que usa el manifiesto de la solución. La solución que se crea se almacena en la galería de soluciones de la colección de sitios de SharePoint. Una vez guardada la plantilla, se crea un archivo de solución (.wsp) y se almacena en la galería de soluciones, en donde se puede descargar o activar la solución.
  
    
    

> **NOTA**
> El WSP que se crea es una solución de usuario de confianza parcial con el mismo formato declarativo que una solución de plena confianza de SharePoint. Sin embargo, no admite toda la gama de tipos de elementos de características admitidos por las soluciones de plena confianza. 
  
    
    


### Qué se guarda en una plantilla

Al guardar un sitio de SharePoint como una plantilla, se está guardando el marco general del sitio: sus listas y bibliotecas, vistas y formularios y flujos de trabajo. Además de estos componentes, es posible incluir el contenido del sitio en la plantilla, por ejemplo, los documentos almacenados en las bibliotecas de documentos. Eso podría resultar útil para ofrecer contenido de ejemplo con el que los usuarios puedan comenzar a trabajar. Tenga en cuenta que eso además podría aumentar el tamaño de la plantilla más allá del límite predeterminado de 50 MB de las plantillas de sitio.
  
    
    
La plantilla incluye y admite la mayoría de los objetos de un sitio. Sin embargo, hay varios objetos y características que no se admiten. 
  
    
    

- **Admitidos** Listas, bibliotecas, listas externas, conexiones de orígenes de datos, vistas de lista y de datos, formularios personalizados, flujos de trabajo, tipos de contenido, acciones personalizadas, navegación, páginas de sitio, páginas maestras, módulos y plantillas web.
    
  
- **No admitidos** Permisos personalizados, instancias de flujo de trabajo en ejecución, historial de versiones de elementos de lista, tareas de flujo de trabajo asociadas a flujos de trabajo en ejecución, valores de campo de persona o grupo, valores de campo de taxonomía, páginas y sitios de publicación, Mis sitios, características con grapas, Complementos de SharePoint y receptores de eventos remotos.
    
    > **NOTA**
      > En los sitios de publicación se pueden usar plantillas de definición de sitio. Para obtener más información, consulte  [Recursos adicionales](save-download-and-upload-a-sharepoint-2013-site-as-a-template.md#bkmk_additionalresources) al final de este tema.

### Qué se puede hacer con las plantillas de SharePoint

La opción de guardar un sitio como una plantilla es una eficaz característica, ya que ofrece muchos usos distintos de los sitios personalizados. Estos son los beneficios inmediatos que se obtienen al guardar un sitio como una plantilla:
  
    
    

- **Implementación inmediata de soluciones** Guarde y active la plantilla en la galería de soluciones y deje que otros empleados creen sitios nuevos a partir de ella. Puede seleccionarla y luego crear un sitio nuevo a partir de ella, con lo que heredaría los componentes del sitio, su estructura, flujos de trabajo, etc. No necesita Visual Studio para crear la solución y tiene que obtener acceso al servidor directamente y ejecutar comandos del administrador del servidor. Simplemente guarde el sitio como una plantilla, actívela y comience a trabajar.
    
  
- **Portabilidad** Además de implementar una solución personalizada en el entorno, puede descargar el archivo .wsp, llevarlo consigo e implementarlo en otro entorno de SharePoint. Toda la personalización del sitio se almacena cómodamente en un archivo.
    
  
- **Extensibilidad** Como paquete de soluciones web, puede abrir el sitio personalizado en Visual Studio, realizar personalizaciones de desarrollo adicionales de la plantilla y luego implementarla en SharePoint. Como resultado, el desarrollo de soluciones de SharePoint puede pasar por un ciclo de vida de solución (desarrollo, copia intermedia y paso a producción) que incluye SharePoint Designer 2013, Visual Studio y el explorador.
    
  
A medida que empiece a crear sitios personalizados en SharePoint, descubrirá aún más beneficios de la conversión del sitio en una solución que se puede compartir en la organización. Los pasos básicos para trabajar con plantillas de sitio son los siguientes:
  
    
    

- Guarde un sitio como plantilla en la galería de soluciones.
    
  
- Descargue la plantilla de sitio de la galería de soluciones en un archivo .wsp.
    
  
- Cargue el archivo .wsp en la galería de soluciones.
    
  
Después de agregar una plantilla de sitio a la galería de soluciones y de activar la plantilla, la siguiente vez que cree un sitio o subsitio, la plantilla estará disponible para seleccionar en la pestaña **Personalizado** de la sección **Selección de plantilla** de la página **Nuevo sitio de SharePoint**.
  
    
    

## Guardar un sitio como una plantilla en la galería de soluciones
<a name="bkmk_SaveTemplate"> </a>


1. Vaya al sitio de nivel superior de la colección de sitios.
    
  
2. Haga clic en **Configuración** y luego en **Configuración del sitio**.
    
  
3. En la sección **Acciones del sitio**, haga clic en **Guardar sitio como plantilla**.
    
  
4. Especifique un nombre para el archivo de la plantilla en el cuadro **Nombre de archivo**.
    
  
5. Especifique un nombre y una descripción para la plantilla en los cuadros **Nombre de plantilla** y **Descripción de plantilla**.
    
  
6. Para incluir el contenido del sitio en la plantilla de sitio, active la casilla **Incluir contenido**.
    
    > **NOTA**
      > La inclusión del contenido del sitio puede aumentar considerablemente el tamaño de la plantilla. El límite de tamaño predeterminado de una plantilla de sitio es de 50 MB, pero podría ser inferior en su organización. Siempre puede excluir el contenido y luego copiar lo que necesite posteriormente en el nuevo sitio. También puede aumentar el límite de tamaño. Por ejemplo, para aumentar el límite al máximo permitido, use la siguiente sintaxis del comando Stsadm. >  `stsadm -o setproperty -pn max-template-document-size -pv 524288000`
7. Haga clic en **Aceptar** para guardar la plantilla.
    
    Si todos los componentes del sitio son válidos, se crea la plantilla y aparece un mensaje que indica "La operación se realizó correctamente".
    
  
8. Tiene las siguientes opciones:
    
  - Para volver al sitio, haga clic en **Aceptar**.
    
  
  - Para ir directamente a la plantilla de sitio, haga clic en **Galería de soluciones**.
    
  

## Descargar la plantilla de sitio de la galería de soluciones en un archivo
<a name="bkmk_DownloadTemplate"> </a>


1. Vaya al sitio de nivel superior de la colección de sitios.
    
  
2. Haga clic en **Configuración** y luego en **Configuración del sitio**.
    
  
3. En la sección **Galerías del diseñador web**, haga clic en **Soluciones**.
    
  
4. Si es necesario activar la solución, selecciónela y, en el grupo **Comandos**, haga clic en **Activar**. A continuación, en la pantalla **Confirmación de activación de solución**, en el grupo **Comandos**, haga clic en **Activar**.
    
  
5. Para descargar la solución, haga clic en su nombre en la galería de soluciones y en **Guardar**. A continuación, en el cuadro de diálogo **Guardar como**, vaya a la ubicación en la que desea guardar la solución, haga clic en **Guardar** y luego en **Cerrar**.
    
  

## Cargar el archivo de la plantilla de sitio en una galería de soluciones
<a name="bkmk_UploadTemplate"> </a>


1. Vaya al sitio de nivel superior de la colección de sitios.
    
  
2. Haga clic en **Configuración** y luego en **Configuración del sitio**.
    
  
3. En la sección **Galerías del diseñador web**, haga clic en **Soluciones**.
    
  
4. Para cargar la solución, en el grupo **Comandos**, haga clic en **Cargar** y luego, en el cuadro de diálogo **Agregar un documento**, haga clic en **Examinar**. A continuación, en el cuadro de diálogo **Elegir archivos para cargar**, busque el archivo, selecciónelo, haga clic en **Abrir** y luego en **Aceptar**.
    
  
5. Para activar la solución, en la pantalla de confirmación de activación de la solución, en el grupo **Comandos**, haga clic en **Activar**.
    
  

## Recursos adicionales
<a name="bkmk_additionalresources"> </a>


-  [Tipos de sitio: WebTemplates y definiciones de sitio](http://msdn.microsoft.com/es-es/library/ms434313.aspx)
    
  
-  [Descripción de cómo empaquetar e implementar el flujo de trabajo en SharePoint 2013](http://msdn.microsoft.com/es-es/library/jj819316%28v=office.15%29.aspx)
    
  
-  [Crear soluciones de granjas de servidores en SharePoint 2013](http://msdn.microsoft.com/es-es/library/jj163902%28v=office.15%29.aspx)
    
  
-  [Copiar o mover una lista con una plantilla de lista](http://office.com/redir/HA101782479.aspx)
    
  
-  [Copiar o mover una biblioteca mediante una plantilla de biblioteca](http://office.com/en-us/redir/HA101814157.aspx)
    
  
-  [Copiar o mover archivos de bibliotecas mediante Abrir con el Explorador](http://office.com/redir/HA101811182.aspx)
    
  

