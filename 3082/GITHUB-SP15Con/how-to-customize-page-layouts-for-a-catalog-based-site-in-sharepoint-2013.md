---
title: Procedimientos Personalizar diseños de página para un sitio basado en catálogos en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 21d8db99-73b3-4429-b6cb-04e375af9f55
---


# Procedimientos: Personalizar diseños de página para un sitio basado en catálogos en SharePoint 2013
Aprenda a crear y personalizar diseños de páginas de categorías y de páginas de elementos de catálogo para un sitio de publicación entre sitios de SharePoint Server 2013.
## Requisitos previos para crear y personalizar los diseños de páginas para un sitio basado en catálogos
<a name="bk_prereqs"> </a>

Para poder seguir los pasos de este ejemplo, es necesario lo siguiente:
  
    
    

- Un editor de HTML
    
  
- Un entorno de publicación entre sitios de SharePoint Server 2013
    
  
Para obtener información sobre cómo configurar un entorno de publicación entre sitios de SharePoint, consulte  [Configuración de publicaciones entre sitios en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj656774.aspx).
  
    
    

### Conceptos básicos para crear y personalizar los diseños de página para un sitio basado en catálogos

En la tabla 1 se enumeran artículos útiles que pueden ayudarle a comprender los conceptos y los pasos implicados en la creación y la personalización de diseños de página para un sitio basado en catálogos.
  
    
    

**Tabla 1. Conceptos básicos para crear y personalizar los diseños de página para un sitio basado en catálogos**


|**Título del artículo**|**Descripción**|
|:-----|:-----|
| [Información general sobre la publicación entre sitios en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj635883.aspx) <br/> |Obtenga información sobre cómo usar la publicación entre sitios y los elementos web de búsqueda para crear sitios de SharePoint de Internet, intranet y extranet adaptables.  <br/> |
| [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) <br/> |Obtenga información sobre cómo crear diseños de página en SharePoint Server 2013.  <br/> |
| [Cómo: resolver errores y advertencias durante la vista previa de una página en SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md) <br/> |Obtenga información sobre cómo resolver los problemas que impiden que la vista previa del servidor presente la página.  <br/> |
| [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md) <br/> |Obtenga información sobre cómo usar fragmentos de código para agregar la funcionalidad de SharePoint a la página HTML principal o al diseño de página.  <br/> |
   

## Introducción a los diseños de páginas de categorías y los diseños de páginas de elementos de catálogo
<a name="bk_introduction"> </a>

Las páginas de categorías y las páginas de elementos de catálogo son diseños que puede usar para mostrar contenido de catálogo de forma coherente en las distintas páginas de un sitio. De modo predeterminado, SharePoint Server 2013 puede crear automáticamente un diseño de página de categorías y un diseño de página de elementos de catálogo por cada conexión a un catálogo. Las páginas basadas en estos diseños se crean en la biblioteca de páginas de un sitio de publicación al conectar el sitio a un catálogo. Para obtener más información sobre los diseños de página, vea  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md). Para obtener más información sobre las características específicas de los diseños de páginas de categorías y diseños de páginas de elementos de catálogo, consulte  [Información general sobre la publicación entre sitios en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj635883.aspx).
  
    
    
De forma predeterminada, los diseños de páginas de categorías y los diseños de páginas de elementos de catálogo se crean automáticamente cuando un sitio de publicación se conecta con un catálogo. También puede usar el Administrador de diseño para crear diseños de páginas de categorías y diseños de páginas de elementos de catálogo que se pueden seleccionar cuando se conecta un sitio de publicación con un catálogo, o cuando se configura el conjunto de términos de navegación en un sitio de publicación.
  
    
    

## Crear un diseño de página de categorías
<a name="bk_createCategoryPage"> </a>

Para poder crear o personalizar un diseño de página de categorías, recomendamos que cree una unidad de red asignada que dirija a la **Galería de páginas maestras**. Para obtener más información, consulte  [Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    
La forma más sencilla de crear un diseño de página de categorías es dejar que SharePoint cree automáticamente el diseño de página cuando el sitio de publicación se conecta con un catálogo y, después, personalizar el diseño de página de categorías existente para cambiar el marcado según lo requiera el diseño de página. También puede crear un nuevo diseño de página de categorías desde cero mediante el Administrador de diseño.
  
    
    

### Para personalizar un diseño de página de categorías existente creado automáticamente por SharePoint


1. En el Explorador de Windows, abra la unidad de red asignada a la Galería de páginas maestras.
    
  
2. Para personalizar un diseño de página de categorías, edite el archivo HTML que reside directamente en el servidor mediante el editor HTML para abrir y editar el archivo HTML en la unidad asignada. Cada vez que guarde el archivo HTML, los cambios se sincronizarán con el archivo .aspx asociado.
    
  
3. Reemplace el marcado de dentro del marcador de posición de contenido que tiene **id="PlaceHolderMain"** por el marcado que quiera usar en el diseño de página.
    
    > **IMPORTANTE**
      > Debe conservar el marcado del fragmento de código de búsqueda de contenido para que la página de categorías pueda mostrar los resultados de la búsqueda. 
4. Para configurar y copiar el código HTML de los fragmentos de código que quiere agregar a la página, siga los pasos del 1 al 11 de la sección "Insertar un fragmento de código de la Galería de fragmentos de código" del artículo  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
5. Realice los cambios necesarios en el marcado y guarde el archivo.
    
  
6. Siga los pasos del 9 al 11 de la sección "Crear un diseño de página" del artículo  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para comprobar el estado del archivo, obtener una vista previa del diseño de página y corregir los errores.
    
  

### Para crear un diseño de página de categorías mediante el Administrador de diseño


1. Siga los pasos del 1 al 6 de la sección "Crear un diseño de página" del artículo  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  
2. En el paso 7, elija el tipo de contenido **Página de artículo**.
    
  
3. Elija **Aceptar**.
    
    En este momento, SharePoint crea un archivo HTML y un archivo .aspx con el mismo nombre.
    
    En el Administrador de diseño, el archivo HTML aparece ahora con una columna **Estado** que muestra uno de dos estados:
    
  - Errores
    
  
  - **Conversión correcta**
    
  
4. En el Explorador de Windows, abra la unidad de red asignada a la Galería de páginas maestras.
    
  
5. Para personalizar el diseño de página de categorías, edite el archivo HTML que reside directamente en el servidor mediante el editor HTML para abrir y editar el archivo HTML en la unidad asignada. Cada vez que guarde el archivo HTML, los cambios se sincronizarán con el archivo .aspx asociado.
    
  
6. En la etiqueta **<head>**, reemplace el marcador de posición de contenido que tiene **id="PlaceHolderPageTitle"** por:
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

7. Buscar el marcador de posición de contenido que tiene **id="PlaceHolderPageTitleInTitleArea"** y reemplácelo por:
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitleInTitleArea" runat="server">-->
<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

8. Reemplace el marcado de dentro del marcador de posición de contenido que tiene **id="PlaceHolderMain"** por el marcado que quiera usar en el diseño de página.
    
  
9. Para configurar y copiar el código HTML del fragmento de código de búsqueda de contenido y de cualquier otro fragmento de código que quiera agregar a la página, siga los pasos del 1 al 11 de la sección "Insertar un fragmento de código de la Galería de fragmentos de código" del artículo  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
    > **NOTA**
      > Al agregar el fragmento de código de búsqueda de contenido al diseño de página, asegúrese de cambiar la consulta para que use el origen de resultados que se creó cuando conectó el sitio de publicación con un catálogo. Para obtener más información, consulte  [Configuración de orígenes de resultados para la administración de contenido web en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj715262.aspx). 
10. Realice los cambios necesarios en el marcado y guarde el archivo.
    
  
11. Siga los pasos del 9 al 11 de la sección "Crear un diseño de página" del artículo  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para comprobar el estado del archivo, obtener una vista previa del diseño de página y corregir los errores.
    
  

## Descripción del marcado en el diseño de página de categorías HTML
<a name="bk_CategoryPageMarkup"> </a>

Cuando se crea un diseño de página, se crea un archivo .aspx que SharePoint usará y se agrega marcado HTML a la versión HTML del diseño de página. Los diseños de páginas de categorías tienen componentes de marcado que se agregan al diseño de página en función de la característica de publicación de colecciones entre sitios y que son exclusivos de los diseños de páginas de categorías. Al editar el diseño de página de categorías HTML en el editor de HTML, podría resultarle útil comprender parte de este marcado.
  
    
    

### Título de página de la ventana del explorador

El componente que aparece dentro del marcador de posición de contenido con **id="PlaceHolderPageTitle"** contiene el marcado que le indica a SharePoint que use una propiedad de término como título de página en la ventana del explorador, en lugar de usar el valor de campo de página estándar. El código siguiente muestra el marcado para el título de página de la ventana del explorador.
  
    
    

```HTML

<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
```


### Título de página

El componente que aparece dentro del marcador de posición de contenido con **id="PlaceHolderPageTitleInTitleArea"** contiene el marcado que le indica a SharePoint que use una propiedad de término como título de la página, en lugar de usar el fragmento de código **SPTitleBreadcrumb** y el valor de campo de título de página estándar. El código siguiente muestra el marcado para el título de página.
  
    
    

```HTML

<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->"
```


### Fragmento de código de búsqueda de contenido

Los componentes que aparecen detrás del fragmento de contenido de página, dentro del marcador de posición de contenido con **id="PlaceHolderMain"**, contienen el marcado para un fragmento de código de zona de elementos web que contiene cuatro zonas de elementos web. La primera zona de elementos web contiene un fragmento de código de búsqueda de contenido que muestra un elemento web de búsqueda de contenido en la página. Este fragmento de código también contiene información que ayuda a que el elemento de web de búsqueda de contenido consulte un origen de resultados y muestre los resultados en la página. Las tres últimas zonas de elementos web están vacías. Si elige crear su propio diseño de página de categorías, debe incluir el marcado para el fragmento de código de búsqueda de contenido en el archivo HTML del diseño de página. El código siguiente muestra el marcado para el fragmento de código de búsqueda de contenido. Reemplace  _ResultSourceID_ por el GUID del origen del resultado y reemplace _CatalogURL_ por la dirección URL del catálogo.
  
    
    

> **NOTA**
> SharePoint genera aleatoriamente los GUID para **ID** y **__WebPartId** cuando los fragmentos de código se agregan al diseño de página.
  
    
    


```HTML
<!--
CS: Start Content Search Snippet-->
<!--SPM:<%@Register Tagprefix="a781102493" Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<a781102493:ContentBySearchWebPart runat="server" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;&amp;#34;,&amp;#34;SourceID&amp;#34;
:&amp;#34;ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;
{'Tag':'{Term.IDWithChildren}','Scope':'CatalogURL'}&amp;#34;}" ResultsPerPage="3" RenderTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Control_ListWithPaging.js" 
ItemTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Item_PictureOnTop.js" SelectedPropertiesJson="[&amp;#34;WorkId&amp;#34;,&amp;#34;Rank&amp;#34;,&amp;#34;Title&amp;#34;,&amp;#34;Author&amp;#34;,&amp;#34;
Size&amp;#34;,&amp;#34;Path&amp;#34;,&amp;#34;Description&amp;#34;,&amp;#34;Write&amp;#34;,&amp;#34;CollapsingStatus&amp;#34;,&amp;#34;
HitHighlightedSummary&amp;#34;,&amp;#34;HitHighlightedProperties&amp;#34;,&amp;#34;ContentClass&amp;#34;,&amp;#34;
PictureThumbnailURL&amp;#34;,&amp;#34;ServerRedirectedURL&amp;#34;,&amp;#34;ServerRedirectedEmbedURL&amp;#34;,&amp;#34;
ServerRedirectedPreviewURL&amp;#34;,&amp;#34;FileExtension&amp;#34;,&amp;#34;ContentTypeId&amp;#34;,&amp;#34;ParentLink&amp;#34;,&amp;#34;
ViewsLifeTime&amp;#34;,&amp;#34;ViewsRecent&amp;#34;,&amp;#34;SectionNames&amp;#34;,&amp;#34;SectionIndexes&amp;#34;,&amp;#34;
SiteLogo&amp;#34;,&amp;#34;SiteDescription&amp;#34;,&amp;#34;deeplinks&amp;#34;,&amp;#34;importance&amp;#34;]" ShouldHideControlWhenEmpty="True" FrameType="None" SuppressWebPartChrome="False" Description="$Resources:Microsoft.Office.Server.Search,CBS_Description;" IsIncluded="True" 
ZoneID="" PartOrder="0" FrameState="Normal" AllowRemove="True" AllowZoneChange="True" 
AllowMinimize="True" AllowConnect="True" AllowEdit="True" AllowHide="True" IsVisible="True" 
DetailLink="" HelpLink="" HelpMode="Modeless" Dir="Default" PartImageSmall="" IsIncludedFilter="" ExportControlledProperties="True" ConnectionID="00000000-0000-0000-0000-000000000000" ID="g_54e35103_6f29_4dd9_b93b_8d4c863834af" ChromeType="None" ExportMode="All" __MarkupType="vsattributemarkup" __WebPartId="54e35103-6f29-4dd9-b93b-8d4c863834af" 
WebPart="true" Height="" Width="" Title="$Resources:cms,WebPartZoneTitle_Dynamic;">-->
<!--ME:</a781102493:ContentBySearchWebPart>-->
<!--CE: End Content Search Snippet-->

```


## Crear un diseño de página de elementos de catálogo
<a name="bk_createCatItemPage"> </a>

Para poder crear o personalizar un diseño de página de elementos de catálogo, recomendamos que cree una unidad de red asignada que dirija a la Galería de páginas maestras. Para obtener más información, consulte  [Procedimiento para asignar una unidad de red a la Galería de páginas maestras de SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    
Al igual que en el caso del diseño de página de categorías, la forma más sencilla de crear un diseño de página de elementos de catálogo es dejar que SharePoint cree automáticamente el diseño de página cuando el sitio de publicación se conecta con un catálogo y, después, personalizar el diseño de página de elementos de catálogo existente para agregar el marcado adicional que requiera el diseño de página. También puede crear un diseño de página de elementos de catálogo desde cero mediante el Administrador de diseño.
  
    
    

### Para personalizar un diseño de página de elementos de catálogo existente creado automáticamente por SharePoint


1. En el Explorador de Windows, abra la unidad de red asignada a la Galería de páginas maestras.
    
  
2. Para personalizar un diseño de página de elementos de catálogo, edite el archivo HTML que reside directamente en el servidor mediante el editor HTML para abrir y editar el archivo HTML en la unidad asignada. Cada vez que guarde el archivo HTML, los cambios se sincronizarán con el archivo .aspx asociado.
    
  
3. Dentro del marcador de posición de contenido que tiene **id="PlaceHolderMain"**, agregue el marcado que quiera usar en el diseño de página.
    
  
4. Elimine los fragmentos de código que no quiera usar en el diseño de página y mueva los fragmentos restantes a lugares del marcado en los que quiera que aparezcan los valores de propiedad.
    
    > **PRECAUCIóN**
      > De forma predeterminada, se agrega al diseño de página un fragmento de código de zona de elementos web que contiene un fragmento de código de reutilización de elementos de catálogo. Este fragmento de código contiene el proveedor de datos que devuelve los resultados de la consulta que usan los demás fragmentos de código de la página. Recomendamos que conserve el fragmento de código de reutilización de elementos de catálogo en este fragmento de código de zona de elementos web predeterminado. (Puede mover el fragmento de código de reutilización de elementos de catálogo fuera de la zona de elementos web y puede cambiar la propiedad que muestra, pero debe conservar el fragmento de código de reutilización de elementos de catálogo en el diseño de página). Para obtener más información, vea  [Campos de página](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields) más adelante en este artículo.
5. Para configurar y copiar el fragmento de código HTML de los fragmentos de código que quiere usar en la página, siga los pasos del 1 al 11 de la sección "Insertar un fragmento de código de la Galería de fragmentos de código" del artículo  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
6. Realice los cambios necesarios en el marcado y guarde el archivo.
    
  
7. Siga los pasos del 9 al 11 de la sección "Crear un diseño de página" del artículo  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para comprobar el estado del archivo, obtener una vista previa del diseño de página y corregir los errores.
    
  

### Para crear un diseño de página de elementos de catálogo mediante el Administrador de diseño


1. Siga los pasos del 1 al 6 de la sección "Crear un diseño de página" del artículo  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  
2. En el paso 7, elija **Catálogo remoto** y después seleccione el catálogo que contiene los datos que van a aparecer en la página.
    
  
3. Elija **Aceptar**.
    
    En este momento, SharePoint crea un archivo HTML y un archivo .aspx con el mismo nombre.
    
    En el Administrador de diseño, el archivo HTML aparece ahora con una columna **Estado** que muestra uno de dos estados:
    
  - Errores
    
  
  - **Conversión correcta**
    
  
4. En el Explorador de Windows, abra la unidad de red asignada a la Galería de páginas maestras.
    
  
5. Para personalizar el diseño de página de elementos de catálogo, edite el archivo HTML que reside directamente en el servidor mediante el editor HTML para abrir y editar el archivo HTML en la unidad asignada. Cada vez que guarde el archivo HTML, los cambios se sincronizarán con el archivo .aspx asociado.
    
  
6. Dentro del marcador de posición de contenido que tiene **id="PlaceHolderMain"**, agregue el marcado que quiera usar en el diseño de página.
    
  
7. Elimine los fragmentos de código que no quiera usar en el diseño de página y mueva los fragmentos restantes a lugares del marcado en los que quiera que aparezcan los valores de propiedad.
    
    > **PRECAUCIóN**
      > De forma predeterminada, se agrega al diseño de página un fragmento de código de zona de elementos web que contiene un fragmento de código de reutilización de elementos de catálogo. Este fragmento de código contiene el proveedor de datos que devuelve los resultados de la consulta que usan los demás fragmentos de código de la página. Recomendamos que conserve el fragmento de código de reutilización de elementos de catálogo en este fragmento de código de zona de elementos web predeterminado. (Puede mover el fragmento de código de reutilización de elementos de catálogo fuera de la zona de elementos web y puede cambiar la propiedad que muestra, pero debe conservar el fragmento de código de reutilización de elementos de catálogo en el diseño de página). Para obtener más información, vea  [Campos de página](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields) más adelante en este artículo.
8. Para configurar y copiar el fragmento de código HTML de los fragmentos de código que quiere usar en la página, siga los pasos del 1 al 11 de la sección "Insertar un fragmento de código de la Galería de fragmentos de código" del artículo  [Fragmentos de código del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
9. Realice los cambios necesarios en el marcado y guarde el archivo.
    
  
10. Siga los pasos del 9 al 11 de la sección "Crear un diseño de página" del artículo  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para comprobar el estado del archivo, obtener una vista previa del diseño de página y corregir los errores.
    
  

## Descripción del marcado en el diseño de página de elementos de catálogo HTML
<a name="bk_CatItemMarkup"> </a>

Cuando se crea un diseño de página, se crea un archivo .aspx que SharePoint usará y se agrega marcado HTML a la versión HTML del diseño de página. Los diseños de páginas de elementos de catálogo tienen componentes de marcado que se agregan al diseño de página en función de la característica de publicación de colecciones entre sitios y que son exclusivos de los diseños de páginas de elementos de catálogo. Al editar el diseño de página de elementos de catálogo HTML en el editor de HTML, podría resultarle útil comprender parte de este marcado.
  
    
    

### Título de página de la ventana del explorador

El componente que aparece dentro del marcador de posición de contenido con **id="PlaceHolderPageTitle"** contiene un fragmento de código de reutilización de elementos de catálogo que le indica a SharePoint que use el nombre del elemento de catálogo como título de página en la ventana del explorador, en lugar de usar el valor de campo de título de página estándar. El código siguiente muestra el marcado para el título de página de la ventana del explorador.
  
    
    

> **NOTA**
> SharePoint genera aleatoriamente los GUID para **ID** y **__WebPartId** cuando los fragmentos de código se agregan al diseño de página.
  
    
    


```HTML

<!--CS: [Title] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_863912c1_c849_46dc_8781_2920ee2bc83f" __WebPartId="{863912c1-c849-46dc-8781-2920ee2bc83f}">-->
<!--SPM:<RenderFormat>-->
<!--DC:Renders value from search without any additional formatting.-->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->

```


### Campos de página
<a name="bk_pagefields"> </a>

Los componentes que aparecen dentro del marcador de posición de contenido con **id="PlaceHolderMain"** contienen fragmentos de código para los campos **Title**, **Page Content** y **Catalog-Item URL**. Puede eliminar del diseño de página cualquiera de estos fragmentos de código. El código siguiente muestra el marcado para estos campos de página.
  
    
    

```HTML

<div>
    <!--CS: Start Page Field: Title Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldTextField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
        <!--MS:<PageFieldTextField:TextField FieldName="fa564e0f-0c70-4ab9-b863-0177e6ddd247" 
runat="server">-->
        <!--ME:</PageFieldTextField:TextField>-->
    <!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Page Field: Title Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Page Content Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldRichHtmlField:RichHtmlField FieldName="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" runat="server">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
            <div id="ctl02_label" style="display:none">Page Content</div>
            <div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label">
                <div align="left" class="ms-formfieldcontainer">
                    <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                        <span class="ms-formfieldlabel" nowrap="nowrap">Page Content</span>
                    </div>
                    <div class="ms-formfieldvaluecontainer">
                        <div class="ms-rtestate-field">Page Content field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
                    </div>
                </div>
            </div>
        <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
    <!--CE: End Page Field: Page Content Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Catalog-Item URL Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldCatalogSourceFieldControl" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl FieldName="75772bbf-0c25-4710-b52c-7b78344ad136" runat="server">-->
    <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
        <div align="left" class="ms-formfieldcontainer">
            <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                <span class="ms-formfieldlabel" nowrap="nowrap">Catalog-Item URL</span>
            </div>
            <div class="ms-formfieldvaluecontainer">
                <a href="http://www.example.com">Link to sample web site.</a>
            </div>
        </div>
    <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl>-->
    <!--CE: End Page Field: Catalog-Item URL Snippet-->
</div>

```

Si el diseño de página de elementos de catálogo se creó automáticamente cuando el sitio de publicación se conectó con un catálogo, o si se creó seleccionando un catálogo remoto durante la creación del diseño de página, el diseño de página también contendrá un fragmento de código de zona de elementos web que contiene un fragmento de código de reutilización de elementos de catálogo que registra un proveedor de datos para la página. El fragmento de código de reutilización de elementos de catálogo contiene una propiedad **UseSharedDataProvider** que está establecida en **False**. Puede eliminar del diseño de página el fragmento de código de zona de elementos web, pero debe conservar el fragmento de código de reutilización de elementos de catálogo en el marcado del diseño de página para que la página muestre los elementos de catálogo. Cuando cree una página que use este diseño de página, puede configurar el elemento web para que quede oculto cuando un usuario vea la página.
  
    
    

> **IMPORTANTE**
> Si crea un nuevo diseño de página de elementos de catálogo y elige un tipo de contenido en un lugar de un catálogo remoto, debe incluir un fragmento de código de reutilización de elementos de catálogo en el diseño de página. El código siguiente muestra el marcado para el fragmento de código de reutilización de elementos de catálogo tal y como aparece en el fragmento de código de zona de elementos web. Reemplace  _ManagedPropertyName_ por el nombre de la propiedad administrada que se va a mostrar, reemplace _ResultSourceID_ por el GUID del origen de resultados y reemplace _CatalogURL_ por la dirección URL del catálogo.
  
    
    




```HTML

<div>
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="cc1"  Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
    <!--MS:<WebPartPages:WebPartZone runat="server" Title="&amp;#60;%$Resources:cms,WebPartZoneTitle_Body%&amp;#62;" AllowPersonalization="False" FrameType="TitleBarOnly" ID="Body" Orientation="Vertical">-->
        <!--MS:<ZoneTemplate>-->
            <!--CS: [ManagedPropertyName] Start Catalog-Item Reuse Snippet-->
            <!--DC:To render the search property using a rendering template, change the "UseServerSideRenderFormat" property to "False".-->
            <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" AddSEOPropertiesFromSearch="True" LogAnalyticsViewEvent="True" UseSharedDataProvider="False" OverwriteResultPath="False" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;ListItemID:{URLTOKEN.1}&amp;#34;,&amp;#34;SourceID&amp;#34;:&amp;#34; ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;{&amp;#39;Scope&amp;#39;:&amp;#39;  CatalogURL&amp;#39;,&amp;#39;Tag&amp;#39;:&amp;#39;{Term}&amp;#39;}&amp;#34;}" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;ManagedPropertyName&amp;#34;]" Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" MissingAssembly="Cannot import this Web Part." ID="g_d63eebe7_207f_4e8c_9566_7381acc80cc7" __WebPartId="{d63eebe7-207f-4e8c-9566-7381acc80cc7}">-->
            <!--SPM:<RenderFormat>-->
            <!--DC:Renders value from search without any additional formatting.-->
            <!--SPM:</RenderFormat>-->
            <!--SPM:</cc1:CatalogItemReuseWebPart>-->
        <!--ME:</ZoneTemplate>-->
    <!--ME:</WebPartPages:WebPartZone>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

Si el diseño de página de elementos de catálogo se creó automáticamente cuando el sitio de publicación se conectó con un catálogo, o si se creó seleccionando un catálogo remoto durante la creación del diseño de página, el resto de la página contendrá fragmentos de código de reutilización de elementos de catálogo que se corresponden con las propiedades administradas del catálogo del sitio de creación. Estas propiedades administradas muestran los detalles del elemento de catálogo específico que se muestra mediante el diseño de página de elementos de catálogo. Estos fragmentos de código de reutilización de elementos de catálogo aparecen fuera de la zona de elementos web y se presentan directamente en la página cuando se selecciona un elemento en una página de categorías. En la tabla 2 se enumeran las propiedades administradas que se incluyen automáticamente en el diseño de página de elementos de catálogo.
  
    
    

> **NOTA**
> Algunas de las propiedades administradas solo se incluyen si el catálogo es una biblioteca de páginas. La columna **Usada por** de la tabla 2 indica las propiedades administradas que usan una biblioteca de páginas y una lista, y aquellas que solamente usa una biblioteca de páginas.
  
    
    


**Tabla 2. Fragmentos de código de reutilización de elementos de catálogo de las propiedades administradas predeterminadas**


|**Propiedad administrada**|**Descripción**|**Usada por**|
|:-----|:-----|:-----|
|**AuthorOWSUSER** <br/> |Nombre del usuario que creó la página.  <br/> |Solo la biblioteca de páginas  <br/> |
|**CreatedOWSDATE** <br/> |Fecha de creación de la página o elemento de lista.  <br/> |Biblioteca de páginas y lista  <br/> |
|**EditorOWSUSER** <br/> |Nombre del usuario que modificó por última vez la página o el elemento de lista.  <br/> |Biblioteca de páginas y lista  <br/> |
|**ListItemID** <br/> |Identificador de la página o el elemento de lista.  <br/> |Biblioteca de páginas y lista  <br/> |
|**ModifiedOWSDATE** <br/> |Fecha de la última modificación de la página o el elemento de lista.  <br/> |Biblioteca de páginas y lista  <br/> |
|**PublishingContactOWSUSER** <br/> |Contacto es una columna de sitio creada por la característica de publicación. Se usa en el tipo de contenido de página como la persona o el grupo de contacto de la página.  <br/> |Solo la biblioteca de páginas  <br/> |
|**PublishingIsFurlPageOWSBOOL** <br/> |Valor booleano que indica si la página está asociada a una dirección URL descriptiva.  <br/> |Solo la biblioteca de páginas  <br/> |
|**PublishingPageContentOWSHTML** <br/> |Contenido HTML de la página.  <br/> |Solo la biblioteca de páginas  <br/> |
|**PublishingPageLayoutOWSURLH** <br/> |Dirección URL del diseño de página que se usó para crear la página.  <br/> |Solo la biblioteca de páginas  <br/> |
|**Title** <br/> |Título de la página o el elemento de lista.  <br/> |Biblioteca de páginas y lista  <br/> |
   
Las propiedades administradas de las columnas personalizadas que agregue a la biblioteca de páginas o la lista también se incluyen en los fragmentos de código de reutilización de elementos de catálogo. El nombre de propiedad administrada variará según el tipo de columna de sitio que se use al crear la columna de sitio. Para obtener más información, consulte  [Propiedades administradas creadas automáticamente en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj613136.aspx) e [Información general sobre el esquema de búsqueda en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj219669.aspx).
  
    
    

> **IMPORTANTE**
> La columna de sitio **Page Image** de una biblioteca de páginas se asigna a la propiedad administrada **PublishingImage**. Sin embargo, la propiedad administrada **PublishingImage** no se incluye automáticamente en el diseño de página de elementos de categoría. Para incluir la imagen en el diseño de página, debe agregar un fragmento de código de reutilización de elementos de catálogo para la propiedad administrada **PublishingImage**. Use el siguiente código HTML para agregar un fragmento de código de reutilización de elementos de catálogo para mostrar el valor de la propiedad administrada **PublishingImage** en el diseño de página. Reemplace _UniqueID_ por un GUID único para cada instancia del fragmento de código.
  
    
    




```HTML

<div>
<!--CS: [PublishingImage] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingImage&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_UniqueID" __WebPartId="{UniqueID}">-->
<!--SPM:<RenderFormat>-->
<!--SPM:<Format Type="HTML"> -->
<!--SPM:<Picture>-->True<!--SPM:</Picture>-->
<!--SPM:</Format> -->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

Si crea un nuevo diseño de página de elementos de catálogo mediante el Administrador de diseño y elige un tipo de contenido en un lugar de un catálogo remoto, puede agregar fragmentos de código de reutilización de elementos de catálogo en la página mediante la Galería de fragmentos. El código siguiente muestra el marcado para los fragmentos de código de reutilización de elementos de catálogo para las propiedades administradas **Title**, **PublishingPageContentOWSHTML**, **CreatedOWSDATE** y **owstaxIdPageCategory**.
  
    
    

> **NOTA**
> SharePoint genera aleatoriamente los GUID para **ID** y **__WebPartId** cuando los fragmentos de código se agregan al diseño de página.
  
    
    




```HTML

<div>
    <!--CS: [Title] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_0dc23bb8_8d34_4f9f_8085_5a6ac286cb9e" 
__WebPartId="{0dc23bb8-8d34-4f9f-8085-5a6ac286cb9e}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [PublishingPageContentOWSHTML] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingPageContentOWSHTML&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_25253a49_a9a6_4277_bf9d_416961024cee" 
__WebPartId="{25253a49-a9a6-4277-bf9d-416961024cee}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [CreatedOWSDATE] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;CreatedOWSDATE&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." 
ID="g_4e1f180b_12f8_4e50_84d7_c72b0ee3793f" 
__WebPartId="{4e1f180b-12f8-4e50-84d7-c72b0ee3793f}">-->
    <!--SPM:<RenderFormat>-->
    <!--SPM:<Format Type="DateTime"> -->
    <!--DC:To render Date and Time, change this value to False.-->
    <!--SPM:<DateOnly>-->True<!--SPM:</DateOnly>-->
    <!--SPM:</Format> -->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [owstaxIdPageCategory] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;owstaxIdPageCategory&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_22e39e9d_1b25_42c7_bf2a_7ebca37616d4" 
__WebPartId="{22e39e9d-1b25-42c7-bf2a-7ebca37616d4}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```


## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Desarrollar el diseño del sitio en SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Información general sobre el Administrador de diseño de SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Información general sobre el modelo de páginas de SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [Cómo crear un diseño de página en SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Plantillas para mostrar del Administrador de diseño de SharePoint 2013](sharepoint-2013-design-manager-display-templates.md)
    
  

