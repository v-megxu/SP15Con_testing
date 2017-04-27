---
title: Cómo convertir un archivo HTML en una página maestra en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: a76ab289-3256-45de-ac63-d5112a74e3c7
---


# Cómo convertir un archivo HTML en una página maestra en SharePoint 2013
Con el Administrador de diseño, puede convertir un archivo .html en una página maestra de SharePoint 2013, un archivo .master. Después de la conversión, el archivo HTML y la página maestra se asocian para que siempre que edite y guarde el archivo HTML, los cambios se sincronicen con la página maestra.
## Introducción a la conversión de una página maestra
<a name="Introduction"> </a>

Con el Administrador de diseño, puede convertir un archivo .html en una página maestra de SharePoint 2013, un archivo .master. Después de la conversión, el archivo HTML y la página maestra se asocian para que siempre que edite y guarde el archivo HTML, los cambios se sincronicen con la página maestra.
  
    
    
¿Por qué querría convertir un archivo HTML en lugar de crear un archivo .master de cero? En SharePoint 2013, las páginas maestras funcionan exactamente igual que en ASP.NET, pero SharePoint requiere también que ciertos elementos, como los controles y los marcadores de posición de contenido que son específicos de SharePoint, estén presentes en la página para que SharePoint represente correctamente esa página maestra. Si usa el Administrador de diseño para convertir un archivo HTML en una página maestra de SharePoint completamente funcional, no tendrá que saber nada acerca de ASP.NET ni del marcado específico de SharePoint; en su lugar, podrá centrarse en diseñar su sitio en HTML, CSS y JavaScript.
  
    
    
Al convertir un archivo HTML en una página maestra:
  
    
    

- Se crea un archivo .master con el mismo nombre que su archivo HTML en la Galería de páginas maestras.
    
  
- Todo el marcado que SharePoint 2013 requiere se agrega al archivo .master para que el diseño de página se represente correctamente.
    
  
- Otro marcado, como los comentarios, las etiquetas **<div>**, los fragmentos de código y los marcadores de posición de contenido, se agregan al archivo HTML.
    
  
- El archivo HTML y la página maestra están asociados, por lo que los cambios que se realicen en el archivo HTML se sincronizan con el archivo .master al guardar el archivo HTML.
    
  

> **NOTA**
> La sincronización es unidireccional. Los cambios que se realicen en la página maestra HTML se sincronizan con el archivo .master asociado, pero si elige editar el archivo .master directamente, los cambios no se sincronizarán con el archivo HTML. Todas las páginas maestras HTML (y todos los diseños de página) tienen una propiedad denominada **Archivo asociado**, establecida en **True** de forma predeterminada, que crea la asociación y la sincronización entre los archivos.
  
    
    

Si tiene un par de archivos asociados (HTML y .master) y edita el archivo .master sin romper la asociación, se guardarán los cambios del archivo .master, pero no puede protegerlo ni publicarlo, por lo que los cambios no se guardan de una forma útil. Los cambios que se realicen en el archivo HTML invalidan el archivo .master. Si protege o publica el archivo HTML, los cambios del archivo HTML invalidan los cambios realizados en el archivo .master. Los cambios del archivo .master se pierden.
  
    
    
Si usted es desarrollador y se siente cómodo trabajando con ASP.NET, puede elegir trabajar solo con el archivo .master rompiendo la asociación entre los archivos. Para romper la asociación entre el archivo HTML y el archivo .master, en el Administrador de diseño, elija **Editar propiedades** para el archivo HTML y después, desactive la casilla **Archivo asociado**. Más adelante puede volver a asociar los archivos; para ello, edite las propiedades y seleccione esta casilla. En este caso, el archivo HTML volverá a sobrescribir el archivo .master y los cambios guardados en el archivo .master se perderán.
  
    
    

## Preparar el archivo HTML para la conversión
<a name="Prepare"> </a>

Antes de convertir el archivo HTML, tenga en cuenta estas instrucciones y procedimientos recomendados:
  
    
    

- Tenga en cuenta el modelo de páginas de SharePoint. Para obtener más información, consulte  [Información general sobre el modelo de páginas de SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md). Cuando diseñe los bocetos HTML de su sitio, probablemente tendrá varios archivos HTML para los diferentes tipos de páginas, como una página de artículo o una página de categoría que contiene elementos web que muestran una categoría de elementos de un catálogo. Sin embargo, solo se convertirá un archivo HTML en página maestra. Un archivo HTML se puede convertir en página maestra pero no se puede convertir directamente en un diseño de página porque un diseño de página requiere campos de página.
    
  
- Asegúrese de que su archivo HTML es compatible con XML. Para que la conversión funcione, el archivo HTML debe ser compatible con XML. Lamentablemente, este requisito invalida algunos estándares HTML 5; por ejemplo, en HTML 5 puede especificar **doctype** en minúsculas, pero en XML, **doctype** debe estar en mayúsculas. Además, debe quitar todas las etiquetas **<form>** del archivo HTML. Considere la posibilidad de ejecutar su archivo HTML en un validador XML externo para identificar errores de XML antes de la conversión.
    
  
- Tenga en cuenta estas indicaciones importantes para sus referencias a CSS:
    
  - No ponga bloques **<style>** en la etiqueta **<head>**. Estos estilos se quitan durante la conversión. En su lugar, cree un vínculo desde su archivo HTML a un archivo CSS externo.
    
  
  - Agregue  `ms-design-css-conversion="no"` a la etiqueta **<CSS link>** si está usando una fuente web.
    
  
  - Tenga cuidado al aplicar estilos a las etiquetas HTML generales como **<body>**, **<div>** y **< img>**. En su diseño de SharePoint, todo, incluida la cinta, está dentro de la etiqueta **<body>**. Para los estilos que normalmente aplicaría a la etiqueta **<body>**, considere la posibilidad de aplicarlos en su lugar a **<div id="s4-bodyContainer">**, que es una etiqueta que SharePoint 2013 usa para el cuerpo principal de la página. Además, SharePoint 2013 usa muchas imágenes que se ven afectadas por los estilos que se apliquen a la etiqueta **<img>**.
    
  
  - Muchos diseñadores aplican estilos a la navegación aplicando clases a los elementos **<ul>** y **<li>**. Pero SharePoint 2013 usa un control de navegación dinámica que puede agregar a la página maestra desde la Galería de fragmentos de código. De forma predeterminada, los controles de navegación de SharePoint 2013 tienen aplicados estilos que hay que invalidar.
    
  
- Tenga en cuenta estos posibles problemas con los nombres de los archivos:
    
  - Si tiene Index.html e Index.htm, estos archivos tendrán el mismo archivo .master.
    
  
  - Si tiene Design/Index.html y Design/SubDesign/Index.html, ambos estarán disponibles para conversión en sus propios archivos .master separados, pero ambos se mostrarán como Index.html en la lista de páginas maestras del Administrador de diseño. Para distinguirlos, haga clic o seleccione el botón de puntos suspensivos de cada archivo para ver la ruta de acceso completa.
    
  
- Si va a agregar un widget de JavaScript, asegúrese de que la etiqueta de inicio **<script>** está en su propia línea.
    
  ```
  
<script>
(function( …

  ```


    No las ponga en la misma línea, así.
    


  ```
  
<Script> (function( …
  ```

- Una referencia a la biblioteca JQuery (una referencia externa) debe ir antes de la etiqueta **</head>**.
    
  

## Convertir el archivo HTML en una página maestra
<a name="Convert"> </a>

Antes de convertir un archivo HTML debe cargar todos sus archivos de diseño, incluido su archivo HTML. Para obtener más información, vea  [Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

### Para convertir el archivo HTML en un archivo .master


1. Vaya a su sitio de publicación.
    
  
2. En la esquina superior derecha de la página, elija **Configuración** y, después, elija **Administrador de diseño**.
    
  
3. En el Administrador de diseño, en el panel de navegación izquierdo, elija **Editar páginas maestras**.
    
  
4. Elija **Convertir un archivo HTML a una página maestra de SharePoint**.
    
  
5. En el cuadro de diálogo **Seleccionar un activo**, vaya al archivo HTML que quiere convertir y selecciónelo.
    
    > **NOTA**
      > Al cargar sus archivos de diseño, debe guardar todos los archivos relacionados con un diseño en su propia carpeta en la Galería de páginas maestras. Cuando copie la carpeta del diseño en la unidad de red asignada, la Galería de páginas maestras conserva la estructura de carpetas que haya creado. 
6. Elija **Insertar**.
    
    En este momento, SharePoint 2013 convierte su archivo HTML en un archivo .master con el mismo nombre.
    
    En el Administrador de diseño, el archivo HTML aparece ahora con una columna Estado que muestra uno de dos posibles estados:
    
  - Errores
    
  
  - **Conversión correcta**
    
  
7. Siga el vínculo de la columna Estado para mostrar una vista previa del archivo y para ver los errores o advertencias acerca de la página maestra.
    
    Errores
    
    Para obtener más información sobre como resolver errores y advertencias, consulte  [Cómo: resolver errores y advertencias durante la vista previa de una página en SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md).
    
    Para obtener más información sobre cómo mostrar una vista previa de la página maestra con diferentes páginas, vea  [Cómo: cambiar la página de vista previa en el Administrador de diseño de SharePoint 2013](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md).
    
    La página de vista previa también contiene un vínculo Fragmentos de código en la esquina superior derecha. Este vínculo abre la Galería de fragmentos de código, donde puede comenzar a reemplazar los bocetos de controles o los controles estáticos de su diseño por los controles dinámicos de SharePoint. Para obtener más información, consulte  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
8. Para corregir los errores, edite el archivo HTML que reside directamente en el servidor usando un editor HTML para abrirlo y editarlo en la unidad asignada. Cada vez que guarde el archivo HTML, los cambios realizados se sincronizan con el archivo .master asociado.
    
  
9. Después de mostrar la vista previa de su página maestra correctamente, verá que se agrega una etiqueta **<div>** al archivo HTML. Puede que tenga que desplazarse al final de la página para ver la etiqueta **<div>**.
    
    Esta etiqueta **<div>** es el bloque de contenido principal. Reside dentro de un marcador de posición de contenido llamado **ContentPlaceHolderMain**. En tiempo de ejecución, cuando un visitante explora el sitio y solicita una página, este marcador de posición se llena con contenido procedente de un diseño de página que incluye contenido en una región de contenido coincidente. Debe colocar esta etiqueta **<div>** en el lugar donde quiera que aparezcan los diseños de página en la página maestra.
    
    Si su archivo HTML incluye contenido estático o bocetos de contenido en el cuerpo de la página, ahora comienza el proceso de eliminar ese contenido estático de la página maestra HTML y de aplicar estos estilos a otros elementos del modelo de páginas de SharePoint, como los diseños de página, controles de campo de página, fragmentos de código y plantillas de visualización. Para ver un ejemplo, consulte  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  

## Descripción del archivo HTML después de la conversión
<a name="Understand"> </a>

Cuando se convierte un archivo HTML en una página maestra, se agregan muchas líneas de marcado a su archivo HTML. Puede pasar por alto sin problemas la mayoría de este marcado, y la mayoría de él no aparecerá en el marcado final de su sitio cuando vea el código fuente en el explorador, pero este marcado es vital para convertir el archivo HTML en el archivo .master que SharePoint usa en realidad. Cada vez que guarde un cambio en el archivo HTML, este marcado de SharePoint permite realizar el mismo cambio en el archivo .master asociado, en segundo plano.
  
    
    
El marcado que se agrega incluye etiquetas antes y en la etiqueta **<head>**, los fragmentos de código y los marcadores de posición de contenido. La mayoría del marcado se incluye entre etiquetas de comentario: siempre que guarde un cambio en el archivo HTML, la conversión procesa los comentarios para usar el marcado ASP.NET que contienen.
  
    
    

### Tipos de marcado

A continuación se desglosan los tipos de marcado que se agrega al archivo HTML:
  
    
    

- **Propiedades de documentos** La etiqueta **<mso>** contiene metadatos de SharePoint, incluida información sobre el propio archivo y algunas propiedades necesarias para la correcta conversión al archivo .master.
    
  ```HTML
  
<mso:CustomDocumentProperties>
<mso:HtmlDesignFromMaster msdt:dt="string"></mso:HtmlDesignFromMaster>
<mso:HtmlDesignStatusAndPreview msdt:dt="string">http://[server_name]/sites/PubSite/_catalogs/masterpage/[site_name]/index.html, Conversion successful.</mso:HtmlDesignStatusAndPreview>
<mso:ContentTypeId msdt:dt="string">0x0101000F1C8B9E0EB4BE489F09807B2C53288F0054AD6EF48B9F7B45A142F8173F171BD10003D357F861E29844953D5CAA1D4D8A3A0084F0F9C7FCB65541A59990D173DA60FA</mso:ContentTypeId>
<mso:HtmlDesignAssociated msdt:dt="string">1</mso:HtmlDesignAssociated>
<mso:HtmlDesignConversionSucceeded msdt:dt="string">True</mso:HtmlDesignConversionSucceeded>
</mso:CustomDocumentProperties>
  ```

- **Registro del espacio de nombres de SharePoint** La etiqueta **<SPM>** ("marcado de SharePoint") proporciona una línea que registra un espacio de nombres de SharePoint.
    
  ```HTML
  
<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
  ```

- **Comentarios** Las etiquetas **<CS>** y **<CE>** (inicio del comentario y final del comentario) se pasan por alto durante el proceso de conversión. Estas etiquetas ayudan a analizar las líneas de marcado.
    
  ```HTML
  
<!--CS: Start Page Head Contents Snippet-->
…
<!--CE: End Page Head Contents Snippet-->

  <!--CS: Start Ribbon Snippet-->
…
<!--CE: End Ribbon Snippet-->

<!--CS: Start PlaceHolderMain Snippet-->
…
<!--CE: End PlaceHolderMain Snippet-->
  ```

- **Fragmentos de código** Las etiquetas **<MS>** y **<ME>** (inicio del marcado y final del marcado) marcan el comienzo y el final de un control de SharePoint o de un fragmento de código. Un fragmento de código es un control de SharePoint que agrega funcionalidad de SharePoint a su página. Puede agregar fragmentos de código por sí mismo mediante la Galería de fragmentos de código. Para más información, vea [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  ```HTML
  
<!--MS:<SharePoint:RobotsMetaTag runat="server">-->
        <!--ME:</SharePoint:RobotsMetaTag>-->
        <!--MS:<SharePoint:PageTitle runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
                <!--MS:<SharePoint:ProjectProperty Property="Title" runat="server">-->
                <!--ME:</SharePoint:ProjectProperty>-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:PageTitle>-->
        <!--MS:<SharePoint:StartScript runat="server">-->
        <!--ME:</SharePoint:StartScript>-->
        <!--MS:<SharePoint:CssLink runat="server" Version="15">-->
        <!--ME:</SharePoint:CssLink>-->
        <!--MS:<SharePoint:CacheManifestLink runat="server">-->
        <!--ME:</SharePoint:CacheManifestLink>-->
        <!--MS:<SharePoint:PageRenderMode runat="server" RenderModeType="Standard">-->
        <!--ME:</SharePoint:PageRenderMode>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="core.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="menu.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="callout.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="sharing.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="suitelinks.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:CustomJSUrl runat="server">-->
        <!--ME:</SharePoint:CustomJSUrl>-->
        <!--MS:<SharePoint:SoapDiscoveryLink runat="server">-->
        <!--ME:</SharePoint:SoapDiscoveryLink>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaPlaceHolderAdditionalPageHead" Container="false" runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
            <!--MS:<SharePoint:DelegateControl runat="server" ControlId="AdditionalPageHead" AllowMultipleControls="true">-->
            <!--ME:</SharePoint:DelegateControl>-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderBodyAreaClass" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--MS:<SharePoint:CssRegistration Name="Themable/corev15.css" runat="server">-->
        <!--ME:</SharePoint:CssRegistration>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaSPWebPartManager" runat="server">-->
            <!--MS:<WebPartPages:SPWebPartManager runat="server">-->
            <!--ME:</WebPartPages:SPWebPartManager>-->
        <!--ME:</SharePoint:AjaxDelta>-->
  ```

- **Bloques de vista previa** Las etiquetas **<PS>** y **<PE>** (inicio de la vista previa y fin de la vista previa) rodean una sección de código HTML que no debe editar porque esta sección afecta solo a la vista previa en tiempo de diseño. Estas secciones de vista previa son una instantánea en el tiempo del control de SharePoint que el fragmento de código está insertando. Una vista previa permite trabajar de forma más significativa en el archivo HTML en un editor HTML de cliente. Sin embargo, cambiar el contenido o aplicarle estilo en esa vista previa no tiene un efecto duradero en el archivo .master, que es el que SharePoint usa en realidad. Para aplicar estilos a un fragmento de código, tiene que identificar e invalidar los estilos de SharePoint con sus propias hojas de estilos CSS personalizadas.
    
  ```HTML
  
<!--PS: Start of READ-ONLY PREVIEW (do not modify) -->
<div class="DefaultContentBlock" style="background:rgb(0, 114, 198); color:white; width:100%; padding:8px; height:64px; overflow:hidden;">The SharePoint ribbon will be here when your file is either previewed on or applied to your site.</div>
<!--PE: End of READ-ONLY PREVIEW -->
  ```

- **identificadores de SharePoint** Dos de los fragmentos de código que se agregan al archivo HTML durante la conversión (el fragmento de código Contenido del encabezado de la página y la cinta de SharePoint) tienen un identificador de SharePoint asociado, o SID (00 y 02, respectivamente). Estos identificadores permiten acortar los fragmentos de código y hacer que el código HTML de la página sea más fácil de leer.
    
  ```HTML
  
<!--SID:00 -->

<!--SID:02 {Ribbon}-->
  ```


### Fragmentos de código que se agregan

Es importante conocer dos de los fragmentos de código que se agregan a su archivo HTML. Estos fragmentos se agregan automáticamente durante la conversión, pero no están disponibles para agregarlos desde la Galería de fragmentos de código.
  
    
    

- **La cinta** Para que los autores de contenido puedan crear páginas y contenido en su sitio de SharePoint, su página maestra necesita la cinta y la "navegación de conjunto", que es una novedad de SharePoint 2013. La cinta está incluida en un fragmento de código de optimización de la seguridad para que cuando un visitante explore su sitio, la cinta se muestre solo a los usuarios autenticados y no a los usuarios anónimos. Puede mover la cinta a una posición diferente de la página o aplicarle estilos invalidando las clases CSS predeterminadas, pero no recomendamos mover ni reorganizar los componentes (como el menú Acciones del sitio) incluidos dentro de la cinta.
    
  ```HTML
  
<!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AnonymousUsersOnly">-->
<!--MS:<wssucw:Welcome runat="server" EnableViewState="false">-->
<!--ME:</wssucw:Welcome>-->
<!--ME:</SharePoint:SPSecurityTrimmedControl>-->
  ```

- **ContentPlaceHolderMain** Al final de la etiqueta **<div id="s4-bodyContainer">**, antes de la etiqueta **</body>** de cierre, el proceso de conversión inserta un marcador de posición de contenido llamado **PlaceHolderMain**. Dentro de este fragmento de código está la etiqueta **<div>** amarilla de borde negro que aparece en la vista de diseño de su editor HTML, o en la vista previa del lado del servidor en el Administrador de diseño.
    
    Esta etiqueta **<div>** representa el área donde irá el contenido especificado por sus diseños de página y sus páginas. Debe mover el fragmento de código **PlaceHolderMain** al lugar de la página maestra que los diseños de página rellenarán (el área del diseño del sitio que no es igual en todas las páginas del sitio).
    


  ```HTML
  
<!--CS: Start PlaceHolderMain Snippet-->
                    <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                    <!--MS:<SharePoint:AjaxDelta ID="DeltaPlaceHolderMain" IsMainContent="true" runat="server">-->
                        <!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
                            <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
            This div, which you should delete, represents the content area that your Page Layouts and pages will fill. Design your Master Page around this content placeholder.
        
                            </div>
                        <!--ME:</asp:ContentPlaceHolder>-->
                    <!--ME:</SharePoint:AjaxDelta>-->
                    <!--CE: End PlaceHolderMain Snippet-->
  ```


## Ejemplos
<a name="Reference"> </a>

El siguiente es un ejemplo del marcado que se agrega a un archivo HTML después de convertirlo en una página maestra.
  
    
    

### Marcado agregado a la etiqueta <head>


```HTML

<head>
        <meta http-equiv="X-UA-Compatible" content="IE=10" />
        <!--CS: Start Page Head Contents Snippet-->
        <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SID:00 -->
        <meta name="GENERATOR" content="Microsoft SharePoint" />
        <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
        <meta http-equiv="Expires" content="0" />
        <!--MS:<SharePoint:RobotsMetaTag runat="server">-->
        <!--ME:</SharePoint:RobotsMetaTag>-->
        <!--MS:<SharePoint:PageTitle runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
                <!--MS:<SharePoint:ProjectProperty Property="Title" runat="server">-->
                <!--ME:</SharePoint:ProjectProperty>-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:PageTitle>-->
        <!--MS:<SharePoint:StartScript runat="server">-->
        <!--ME:</SharePoint:StartScript>-->
        <!--MS:<SharePoint:CssLink runat="server" Version="15">-->
        <!--ME:</SharePoint:CssLink>-->
        <!--MS:<SharePoint:CacheManifestLink runat="server">-->
        <!--ME:</SharePoint:CacheManifestLink>-->
        <!--MS:<SharePoint:PageRenderMode runat="server" RenderModeType="Standard">-->
        <!--ME:</SharePoint:PageRenderMode>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="core.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="menu.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="callout.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="sharing.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="suitelinks.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:CustomJSUrl runat="server">-->
        <!--ME:</SharePoint:CustomJSUrl>-->
        <!--MS:<SharePoint:SoapDiscoveryLink runat="server">-->
        <!--ME:</SharePoint:SoapDiscoveryLink>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaPlaceHolderAdditionalPageHead" Container="false" runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
            <!--MS:<SharePoint:DelegateControl runat="server" ControlId="AdditionalPageHead" AllowMultipleControls="true">-->
            <!--ME:</SharePoint:DelegateControl>-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderBodyAreaClass" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--MS:<SharePoint:CssRegistration Name="Themable/corev15.css" runat="server">-->
        <!--ME:</SharePoint:CssRegistration>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaSPWebPartManager" runat="server">-->
            <!--MS:<WebPartPages:SPWebPartManager runat="server">-->
            <!--ME:</WebPartPages:SPWebPartManager>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--CE: End Page Head Contents Snippet-->
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
        <!--DC:Business Solutions-->
        <link rel="stylesheet" href="css/style.css" type="text/css" charset="utf-8" />
        <!--[if lte IE 7]>
  <link rel="stylesheet" href="css/ie.css" type="text/css" charset="utf-8"/> 
 <![endif]-->
        <!--[if gte mso 9]><xml>
<mso:CustomDocumentProperties>
<mso:HtmlDesignFromMaster msdt:dt="string"></mso:HtmlDesignFromMaster>
<mso:HtmlDesignStatusAndPreview msdt:dt="string">http://[server_name]/sites/PubSite/_catalogs/masterpage/[site_name]/index.html, Conversion successful.</mso:HtmlDesignStatusAndPreview>
<mso:ContentTypeId msdt:dt="string">0x0101000F1C8B9E0EB4BE489F09807B2C53288F0054AD6EF48B9F7B45A142F8173F171BD10003D357F861E29844953D5CAA1D4D8A3A0084F0F9C7FCB65541A59990D173DA60FA</mso:ContentTypeId>
<mso:HtmlDesignAssociated msdt:dt="string">1</mso:HtmlDesignAssociated>
<mso:HtmlDesignConversionSucceeded msdt:dt="string">True</mso:HtmlDesignConversionSucceeded>
</mso:CustomDocumentProperties>
</xml><![endif]-->
    </head>

```


### Marcado agregado después de la etiqueta <body> de inicio


#### Fragmento de código de la cinta


```HTML

<!--CS: Start Ribbon Snippet-->
        <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="wssucw" TagName="Welcome" Src="~/_controltemplates/15/Welcome.ascx"%>-->
        <!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" HideFromSearchCrawler="true" EmitDiv="true">-->
            <div id="TurnOnAccessibility" style="display:none" class="s4-notdlg noindex">
                <a id="linkTurnOnAcc" href="#" class="ms-accessible ms-acc-button" onclick="SetIsAccessibilityFeatureEnabled(true);UpdateAccessibilityUI();document.getElementById('linkTurnOffAcc').focus();return false;">
                    <!--MS:<SharePoint:EncodedLiteral runat="server" text="&amp;lt;%$Resources:wss,master_turnonaccessibility%&amp;gt;" EncodeMethod="HtmlEncode">-->
                    <!--ME:</SharePoint:EncodedLiteral>-->
                </a>
            </div>
            <div id="TurnOffAccessibility" style="display:none" class="s4-notdlg noindex">
                <a id="linkTurnOffAcc" href="#" class="ms-accessible ms-acc-button" onclick="SetIsAccessibilityFeatureEnabled(false);UpdateAccessibilityUI();document.getElementById('linkTurnOnAcc').focus();return false;">
                    <!--MS:<SharePoint:EncodedLiteral runat="server" text="&amp;lt;%$Resources:wss,master_turnoffaccessibility%&amp;gt;" EncodeMethod="HtmlEncode">-->
                    <!--ME:</SharePoint:EncodedLiteral>-->
                </a>
            </div>
        <!--ME:</SharePoint:SPSecurityTrimmedControl>-->
        <div id="ms-designer-ribbon">
            <!--SID:02 {Ribbon}-->
            <!--PS: Start of READ-ONLY PREVIEW (do not modify) --><div class="DefaultContentBlock" style="background:rgb(0, 114, 198); color:white; width:100%; padding:8px; height:64px; overflow:hidden;">The SharePoint ribbon will be here when your file is either previewed on or applied to your site.</div><!--PE: End of READ-ONLY PREVIEW -->
        </div>
        <!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AnonymousUsersOnly">-->
            <!--MS:<wssucw:Welcome runat="server" EnableViewState="false">-->
            <!--ME:</wssucw:Welcome>-->
        <!--ME:</SharePoint:SPSecurityTrimmedControl>-->
        <!--CE: End Ribbon Snippet-->

```


#### Dos etiquetas <div> de SharePoint


```HTML

<div id="s4-workspace">
            <div id="s4-bodyContainer">

```


### Marcado agregado antes de la etiqueta </body> de cierre y dos etiquetas </div> de cierre


```HTML

<div data-name="ContentPlaceHolderMain">
                    <!--CS: Start PlaceHolderMain Snippet-->
                    <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                    <!--MS:<SharePoint:AjaxDelta ID="DeltaPlaceHolderMain" IsMainContent="true" runat="server">-->
                        <!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
                            <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
            This div, which you should delete, represents the content area that your Page Layouts and pages will fill. Design your Master Page around this content placeholder.
        
                            </div>
                        <!--ME:</asp:ContentPlaceHolder>-->
                    <!--ME:</SharePoint:AjaxDelta>-->
                    <!--CE: End PlaceHolderMain Snippet-->
                </div>

```


## Recursos adicionales
<a name="Additional"> </a>


-  [Información general sobre el Administrador de diseño de SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md)
    
  

