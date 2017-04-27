---
title: Fragmentos de código del Administrador de diseño de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 68caef4c-5941-4a88-b34b-f88122801cef
---


# Fragmentos de código del Administrador de diseño de SharePoint 2013
Un fragmento de código es una representación HTML de un componente de SharePoint o un control como una barra de navegación o un elemento web. Con la Galería de fragmentos de código del Administrador de diseño, puede agregar rápidamente funcionalidad de SharePoint a la página principal HTML o al diseño de página.
## Introducción a los fragmentos de código y a la Galería de fragmentos
<a name="Introduction"> </a>

Después de convertir una página principal o crear un diseño de página, tiene una versión HTML de la página. Con la Galería de fragmentos de código, puede agregar rápidamente funcionalidad específica de SharePoint, como la búsqueda, la navegación o los paneles de canales de dispositivos al archivo HTML asociado a la página principal o al diseño de página. La Galería de fragmentos de código es una página del Administrador de diseño donde puede:
  
    
    

- Elegir un componente de SharePoint de los que están disponibles en la cinta.
    
  
- Configurar las propiedades para ese componente.
    
  
- Obtener una vista previa de su apariencia en el explorador.
    
  
- Copiar el fragmento de código HTML en el portapapeles para que se pueda pegar en la ubicación que quiera del archivo HTML.
    
  
La Galería de fragmentos de código muestra diferentes opciones en la cinta de opciones, dependiendo de si está editando una página principal o un diseño de página, por ejemplo, se muestran los controles de navegación de páginas principales; las zonas de elementos web y los controles de campo de página se muestran solamente para los diseños de página. Además, al editar un diseño de página, los campos de página que están disponibles dependen del tipo de contenido del diseño de página que está modificando.
  
    
    
Después de pegar un fragmento de código en el archivo HTML, obtiene una vista previa en tiempo de diseño del HTML proporcionado en el fragmento de código. También puede utilizar la vista previa del lado del servidor en el Administrador de diseño para ver cómo aparecerá el control en el sitio activo. La vista previa en tiempo de diseño puede incluir datos de ejemplo estáticos, pero la vista previa del lado servidor, si está disponible, utiliza datos activos. Por ejemplo, un control de navegación que dibuja vínculos de navegación de un conjunto de términos mostrará un conjunto de términos dinámicamente en la vista previa del lado servidor, pero la vista previa en tiempo de diseño tendrá una instantánea estática de los términos en el momento en el que se crea el fragmento de código. Sin embargo, los datos en directo no están disponibles en la vista previa del lado del servidor para algunos fragmentos de código, incluidos muchos elementos web. En este caso, la vista previa del lado servidor puede indicar **Vista previa no disponible**.
  
    
    

> **NOTA**
> Un fragmento de código contiene el código HTML que proporciona una vista previa en tiempo de diseño en su editor HTML, pero el marcado HTML contenido en los comentarios "vista previa de inicio" y "vista previa de finalización" no deben editarse ya que solo afecta a la vista previa en tiempo de diseño, no a la forma en que SharePoint representa finalmente ese fragmento de código. En su lugar, para aplicar un estilo al fragmento de código, normalmente tiene que identificar y reemplazar los estilos de SharePoint predeterminados que se aplican al fragmento de código. 
  
    
    


  
    
    

## Insertar un fragmento de código de la Galería de fragmentos de código
<a name="InsertSnippet"> </a>

La Galería de fragmentos de código muestra diferentes opciones dependiendo del archivo que está modificando. Por ejemplo, diseños de página diferentes tienen distintos conjuntos de campos de página a su disposición. Por este motivo, para desplazarse a la Galería de fragmentos de código, primero debe seleccionar una página principal o un diseño de página para editar.
  
    
    

### Para insertar un fragmento de código


1. Vaya a su sitio de publicación.
    
  
2. En la esquina superior derecha de la página, elija el engranaje Configuración y luego elija **Administrador de diseño**.
    
  
3. En el Administrador de diseño, en el panel de navegación izquierdo, elija **Editar páginas principales** o **Editar diseños de página**, en función del tipo de archivo que está editando.
    
  
4. Seleccione el nombre de la página principal o del diseño de página que quiere agregar a los fragmentos de código.
    
  
5. Para abrir la Galería de fragmentos de código, elija **Fragmentos de código** en la esquina superior derecha de la vista previa del lado del servidor.
    
  
6. En la cinta, en la ficha **Diseño**, seleccione el fragmento de código que quiere agregar a la página.
    
    Cuando selecciona un fragmento de código, la Galería de fragmentos de código se actualiza para que la página muestre una vista previa de ese fragmento de código, las propiedades disponibles para dicho fragmento de código y el fragmento de código HTML que se puede copiar en la página principal HTML o en el diseño de página.
    
  
7. En el lado derecho de la Galería de fragmentos de código, en **Acerca de este componente**, haga clic o seleccione los encabezados de sección para expandir o contraer los grupos de propiedades y luego configure las opciones personalizadas que quiera.
    
    Las propiedades más importantes para el propósito principal del fragmento de código aparecen en la sección superior con el nombre Importante. Estas son las propiedades claves que debe conocer al usar un fragmento de código.
    
    
    
    > **NOTA**
      > Si la cuadrícula de propiedades tiene un encabezado que termina con AjaxDelta, debe omitir estas propiedades porque se aplican a los controles relacionados con la Estrategia de descarga mínima, que está deshabilitado para las páginas principales y para los diseños de página creados con el Administrador de diseño. 
8. Después de configurar las propiedades, elija **Actualizar**. Esto actualiza la vista previa y el fragmento de código HTML del lado izquierdo de la página, para que el marcado refleje la configuración personalizada. Siempre puede elegir **Restablecer** para devolver todas las propiedades a sus valores predeterminados.
    
  
9. En el lado izquierdo de la Galería de fragmentos de código, en **Fragmento de código HTML**, elija **Copiar al Portapapeles**.
    
  
10. En su editor HTML, abra la unidad de red asignada en su equipo y luego abra el archivo HTML de la página principal o del diseño de página al que quiere agregar el fragmento de código.
    
  
11. En el archivo HTML, pegue el fragmento de código en el lugar donde quiere que aparezca el marcado.
    
    Cada fragmento de código contiene código HTML que proporciona una vista previa de los datos de ejemplo y los componentes. No debe modificar este código HTML en la vista previa de solo lectura dentro de la etiquetas **<!--PS>** y **<!--PE>** porque este marcado afecta solo a la vista previa en tiempo de diseño del fragmento de código, no a cómo se mostrará el fragmento de código en el sitio activo.
    
  
12. Para ver la vista previa de servidor del fragmento de código, guarde el archivo HTML para sincronizar los cambios en el archivo ASP.NET asociado y luego actualice la vista previa del lado del servidor en el Administrador de diseño.
    
    A diferencia de la vista previa en tiempo de diseño, la vista previa del lado del servidor muestra el control representado por SharePoint.
    
  

## Comprender el marcado en un fragmento de código HTML
<a name="UnderstandMarkup"> </a>

Un fragmento de código contiene cuatro secciones básicas:
  
    
    

- **Encabezado**, con etiquetas inicial **<div>** y **<!--CS>** (excepto los fragmentos de código ASP.NET personalizados, que no se ajustan en una etiqueta **<div>**)
    
  
- **Marcado de SharePoint**, donde se incluyen los fragmentos de código en etiquetas **<!--MS>** inicial y **<!--ME>** final
    
  
- **Vista previa HTML**, entre etiquetas **<!--PS>** inicial y **<!--PE>** final etiquetas
    
  
- **Pie de página**, con etiquetas de cierre **<!--CE>** y **</div>**
    
  
Todas las secciones de un fragmento de código, excepto la vista previa HTML, se incluyen en los comentarios HTML para evitar las interacciones con el modelo de objetos de documento (DOM) y estilo existente. Un fragmento de código comienza con el nombre de un componente y luego incluye su marcado ASP.NET real, una vista previa HTML para la representación en tiempo de diseño y, después, etiquetas finales. El marcado ASP.NET está comentado, pero SharePoint quita las etiquetas de comentario y este marcado se utiliza cuando el archivo HTML se sincroniza con el archivo .master o aspx. Si sabe ASP.NET, puede personalizar este formato en el fragmento de código.
  
    
    
El ejemplo siguiente es el marcado predeterminado para un Panel de modo de edición que simplemente es un contenedor que muestra condicionalmente otro contenido y controles.
  
    
    

### Encabezado


```HTML

<div data-name="EditModePanelShowInEdit">
    <!--CS: Start Edit Mode Panel Snippet-->
```


### Marcado de SharePoint


```HTML

<!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### Vista previa HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
        <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Edit Mode Panel Properties.
    
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
```


### Pie de página


```HTML

<!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Edit Mode Panel Snippet-->
</div>
```

Lo siguiente es el marcado predeterminado para un fragmento de código de navegación de la parte superior, que es más complejo porque este fragmento de código contiene varios controles diferentes, con algunas anidados dentro de otros, como un origen de datos para los términos de navegación, un control delegado y un marcador de posición de contenido.
  
    
    

> **NOTA**
> Algunos de los controles, como el marcador de posición de contenido, contienen etiquetas vacías para una vista previa de HTML porque ese elemento requiere una representación visual de la página. 
  
    
    


### Encabezado


```HTML

<div data-name="TopNavigationNoFlyoutWithStartNode">
<!--CS: Start Top Navigation Snippet-->    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### Marcado de SharePoint


```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<SharePoint:AjaxDelta ID="DeltaTopNavigation" BlockElement="true" CssClass="ms-displayInline ms-core-navigation ms-dialogHidden" runat="server">-->
```


### Vista previa HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### Marcado de SharePoint


```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
```


### Vista previa HTML


```HTML
<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<span style="display:none">
<table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow">
<tr><td nowrap="nowrap">
<span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span>
<!--PE: End of READ-ONLY PREVIEW-->
```


### Marcado de SharePoint


```HTML

<!--MS:<Template_Controls>-->
<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
```


### Marcado de SharePoint


```HTML

<!--ME:</asp:SiteMapDataSource>-->
<!--ME:</Template_Controls>-->
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>
```


### Marcado de SharePoint


```HTML

<!--MS:<asp:ContentPlaceHolder ID="PlaceHolderTopNavBar" runat="server">-->
<!--MS:<SharePoint:AspMenu ID="TopNavigationMenu" runat="server" EnableViewState="false" DataSourceID="topSiteMap" AccessKey="&amp;#60;%$Resources:wss,navigation_accesskey%&amp;#62;" UseSimpleRendering="true" UseSeparateCss="false" Orientation="Horizontal" StaticDisplayLevels="2" AdjustForShowStartingNode="false" MaximumDynamicDisplayLevels="0" SkipLinkText="">-->
```


### Vista previa HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" />
<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
<ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
<li class="static">
<a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1">
<span class="additional-background ms-navedit-flyoutArrow">
<span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div>
<!--PE: End of READ-ONLY PREVIEW-->
```


### Marcado de SharePoint


```HTML

<!--ME:</SharePoint:AspMenu>-->
<!--ME:</asp:ContentPlaceHolder>-->
```


### Vista previa HTML


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### Marcado de SharePoint


```HTML

<!--ME:</SharePoint:AjaxDelta>-->
```


### Pie de página


```HTML
<!--CE: End Top Navigation Snippet-->
</div>
```


### Tipos de marcado

Este es un desglose de los tipos de marcado que se incluyen en un fragmento de código.
  
    
    
 **Registro del espacio de nombres de SharePoint** SPM ("marcado de SharePoint") indica una línea que registra un espacio de nombres de SharePoint.
  
    
    



```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
```

 **Comentarios** CS y CE ("Inicio de comentario" y "Fin de comentario") le ayudarán a analizar las líneas de marcado.
  
    
    



```HTML
<!--CS: Start Top Navigation Snippet-->
…
<!--CE: End Top Navigation Snippet-->

```

 **Fragmentos de código** MS y ME ("Inicio de marcado" y "Fin de marcado") indican el principio y el final de un control de SharePoint o de un fragmento de código. Algunos fragmentos de código, como la cinta o el control de navegación de la parte superior anterior, contienen varios controles anidados en un único fragmento de código.
  
    
    



```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
…
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>

<!--MS:<Template_Controls>-->
…
<!--ME:</Template_Controls>-->

<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
…
<!--ME:</asp:SiteMapDataSource>-->

```

 **Vista previa de bloques** PS y PE ("Inicio de vista previa" y "Fin de vista previa") alrededor de una sección de código HTML que no debe editar. Estas secciones de vista previa son una instantánea en el momento en el que el control de SharePoint se inserta en ese fragmento de código. Una vista previa permite trabajar con mayor sentido en el archivo HTML en un editor HTML del lado del cliente. Sin embargo, cambiar el contenido o el estilo de la vista previa no tiene ningún efecto definitivo en el archivo. master, que es lo que en última instancia usa SharePoint. Para aplicar el estilo de un fragmento de código, debe identificar y reemplazar los estilos de SharePoint con su propia CSS personalizada.
  
    
    



```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><span style="display:none"><table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow"><tr><td nowrap="nowrap"><span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span><!--PE: End of READ-ONLY PREVIEW-->

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" /><div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox"><ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static"><li class="static"><a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1"><span class="additional-background ms-navedit-flyoutArrow"><span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div><!--PE: End of READ-ONLY PREVIEW-->
```


## Recursos adicionales
<a name="Resources"> </a>


-  [Cómo convertir un archivo HTML en una página maestra en SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Cómo: agregar un fragmento de código de Panel de modo de edición en SharePoint 2013](how-to-add-an-edit-mode-panel-snippet-in-sharepoint-2013.md)
    
  
-  [Cómo: agregar un fragmento de código de recorte de seguridad en SharePoint 2013](how-to-add-a-security-trim-snippet-in-sharepoint-2013.md)
    
  

