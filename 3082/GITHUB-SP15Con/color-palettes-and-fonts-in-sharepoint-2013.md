---
title: Paletas de colores y fuentes de SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c17d375b-151f-48ae-ac32-f2ce9e68d63f
---


# Paletas de colores y fuentes de SharePoint 2013
Use esta referencia para definir la paleta de colores o la combinación de fuentes empleada en un sitio de SharePoint 2013.
## Paletas de colores
<a name="color"> </a>

Una paleta de colores es la combinación de colores que se utiliza en un sitio de SharePoint. La paleta de colores de un sitio de SharePoint se define en un archivo de paleta de colores. El archivo de vista previa de página maestra también usa ranuras de color para generar imágenes de miniatura y de vista previa de un sitio. A continuación se describe la estructura del archivo de paleta de colores y el archivo de vista previa de página maestra:
  
    
    

- **Archivo de paleta de colores (.spcolor)**
    
    Los archivos de paleta de colores se usan en el asistente **Cambiar la apariencia**, que permite a los usuarios cambiar el aspecto de su sitio mediante la interfaz de usuario de temas de SharePoint. En SharePoint 2013 hay instaladas 32 paletas de colores de forma predeterminada. También se pueden crear archivos de paleta de colores adicionales. En el siguiente ejemplo se muestra el formato de un archivo de paleta de colores.
    


  ```XML
  
<s:colorPalette isInverted="InvertedSetting" previewSlot1="Slot1" previewSlot2="Slot2" previewSlot3="Slot3" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:color name="ColorSlot" value="Color" />
    <!--additional color slots-->
</s:colorPalette>
  ```


    En un archivo de paleta de colores, se sustituyen los siguientes marcadores de posición:
    
  -  _InvertedSetting_ es un valor booleano. Suele ser **true** si la paleta de colores es texto claro sobre un fondo oscuro. Suele ser **false** si la paleta de colores es texto oscuro sobre un fondo claro.
    
  
  -  _Slot1_ es el nombre de la anotación de la ranura de color que se va a usar como primer bloque del icono de la paleta en el selector de la paleta de colores de la experiencia de creación de temas.
    
  
  -  _Slot2_ es el nombre de la anotación de la ranura de color que se va a usar como segundo bloque del icono de la paleta en el selector de la paleta de colores de la experiencia de creación de temas.
    
  
  -  _Slot3_ es el nombre de la anotación de la ranura de color que se va a usar como tercer bloque del icono de la paleta en el selector de la paleta de colores de la experiencia de creación de temas.
    
  
  -  _ColorSlot_ es el nombre de la anotación de la ranura de color que se está definiendo (por ejemplo, SiteTitle).
    
  
  -  _Color_ es el valor hexadecimal del color que se va a usar para la ranura de color especificada. Puede ser de 6 dígitos (RRGGBB) o de 8 (AARRGGBB). Si el valor hexadecimal es de 8 dígitos, los dos primeros representan el nivel de opacidad (00-FF, que se asigna a 0-255). Si el valor hexadecimal es de 6 dígitos, la opacidad predeterminada es 100 % o FF.
    
  

    Los archivos de paleta de colores se encuentran en la Galería de temas del sitio raíz, en la colección de sitios de la carpeta **15** (http:// _NombreDeLaColecciónDeSitios_/_catalogs/theme/15/). Para obtener acceso a la Galería de temas desde la interfaz de usuario de SharePoint, en la página **Configuración del sitio**, en **Galerías del diseñador web**, seleccione **Temas** y luego **15**.
    
  
- **Archivo de vista previa de página maestra (.preview)**
    
    Los archivos de vista previa de página maestra se usan para generar imágenes en miniatura y de vista previa cuando se emplea el asistente **Cambiar la apariencia**. Una página maestra debe tener un archivo de vista previa correspondiente para su empleo en el asistente **Cambiar la apariencia**. Un archivo de vista previa es un archivo con un formato especial que tiene secciones para la paleta de colores predeterminada, la combinación de fuentes predeterminada, el CSS con tokens y el HTML con tokens. Utiliza tokens de cadena para obtener el valor de las ranuras de color, los nombres de fuente y las cadenas localizadas de la IU. En el siguiente ejemplo se muestran las ranuras de color que se usan en el archivo de vista previa de página maestra.
    


  ```HTML
  
[ID] #dgp-pageContainer
{
    background-color: [T_THEME_COLOR_PAGEBACKGROUND];
    color: [T_THEME_COLOR_BODYTEXT];
    width: 100%;
    height:100%;     
    background-image: url('[T_IMAGE]');       
    background-size: cover;
    font-family: [T_BODY_FONT];   
}
  ```


    Para obtener más información, consulte  [Cómo: crear un archivo de vista previa de página maestra en SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  

> **SUGERENCIA**
> Puede usar la herramienta paleta de colores de SharePoint como ayuda para crear diseños de SharePoint. Puede  [descargar la herramienta paleta de colores de SharePoint](http://www.microsoft.com/en-us/download/details.aspx?id=38182) en el Centro de descarga de Microsoft.
  
    
    


### Asignación de ranuras de color
<a name="colorSlots"> </a>

En la tabla 1 se describen las ranuras de color disponibles y la ubicación del sitio de SharePoint en la que se utilizan.
  
    
    

> **NOTA**
>  Al hablar de elementos de navegación, se aplicapresionar a cuando un usuario hace clic o toca un elemento de navegación.Seleccionar se aplica a cuando un usuario ha ido hasta la página.>  A continuación se resume un flujo normal de acciones y la ranura de color que se aplica al vínculo de elemento de navegación en cada paso:>  El texto base de un vínculo de elemento de navegación: HeaderNavigationText>  El usuario pasa el cursor sobre el vínculo de elemento de navegación: HeaderNavigationHoverText>  El usuario hace clic en el vínculo de elemento de navegación, lo toca o lo elige: HeaderNavigationPressedText>  El usuario ha ido hasta la página elegida. La ranura de color que se aplica al elemento de navegación de la página en la que se encuentra el usuario: HeaderNavigationSelectedText
  
    
    


**Tabla 1. Ranuras de color**


|**Nombre de la anotación**|**Ubicación de la IU en la que se usa el color**|**Nombre del token**|
|:-----|:-----|:-----|
|BodyText  <br/> |Texto normal del cuerpo.  <br/> |[T_THEME_COLOR_BODYTEXT]  <br/> |
|SubtleBodyText  <br/> |Texto del cuerpo que debe ser más claro que el normal. Un ejemplo sería el texto de los metadatos.  <br/> |[T_THEME_COLOR_SUBTLEBODYTEXT]  <br/> |
|StrongBodyText  <br/> |Color del texto del cuerpo para aquel texto que debe destacar del texto normal del cuerpo.  <br/> |[T_THEME_COLOR_STRONGBODYTEXT]  <br/> |
|DisabledText  <br/> |Texto deshabilitado. Por ejemplo, elementos no disponibles de menús.  <br/> |[T_THEME_COLOR_DISABLEDTEXT]  <br/> |
|SiteTitle  <br/> |Color del texto del título de la página.  <br/> |[T_THEME_COLOR_SITETITLE]  <br/> |
|WebPartHeading  <br/> |Color del texto de los encabezados de elementos web.  <br/> |[T_THEME_COLOR_WEBPARTHEADING]  <br/> |
|ErrorText  <br/> |Color de error principal que se usa para el texto, los bordes y los fondos de error, según sea necesario.  <br/> |[T_THEME_COLOR_ERRORTEXT]  <br/> |
|AccentText  <br/> |Color del texto del cuerpo con énfasis.  <br/> |[T_THEME_COLOR_ACCENTTEXT]  <br/> |
|SearchURL  <br/> |Color del texto de la dirección URL que se encuentra en los resultados de búsqueda. También se emplea para resaltar nuevos elementos o notificaciones de estado correctas.  <br/> |[T_THEME_COLOR_SEARCHURL]  <br/> |
|Hyperlink  <br/> |Color del texto de los hipervínculos.  <br/> |[T_THEME_COLOR_HYPERLINK]  <br/> |
|HyperlinkFollowed  <br/> |Color del texto de los hipervínculos seguidos.  <br/> |[T_THEME_COLOR_HYPERLINKFOLLOWED]  <br/> |
|HyperlinkActive  <br/> |Color del hipervínculo al presionar.  <br/> |[T_THEME_COLOR_HYPERLINKACTIVE]  <br/> |
|CommandLinks  <br/> |Vínculos de comando grandes que deben ser un poco más claros que el texto del cuerpo por su tamaño.  <br/> |[T_THEME_COLOR_COMMANDLINKS]  <br/> |
|CommandLinksSecondary  <br/> |Color de vínculo de comando para aquellos vínculos que son más pequeños y por tanto tienen un color más fuerte para destacar.  <br/> |[T_THEME_COLOR_COMMANDLINKSSECONDARY]  <br/> |
|CommandLinksHover  <br/> |Color de vínculo de comando al pasar.  <br/> |[T_THEME_COLOR_COMMANDLINKSHOVER]  <br/> |
|CommandLinksPressed  <br/> |Color de vínculo de comando al presionar.  <br/> |[T_THEME_COLOR_COMMANDLINKSPRESSED]  <br/> |
|CommandLinksDisabled  <br/> |Color de vínculo de comando cuando el vínculo de comando está deshabilitado.  <br/> |[T_THEME_COLOR_COMMANDLINKSDISABLED]  <br/> |
|BackgroundOverlay  <br/> |Color de fondo principal que es visible entre la imagen de fondo opcional y el contenido de la página.  <br/> |[T_THEME_COLOR_BACKGROUNDOVERLAY]  <br/> |
|DisabledBackground  <br/> |Fondo de elementos deshabilitados como controles de explorador, por ejemplo, cuadro de entrada o de selección (excepto botones).  <br/> |[T_THEME_COLOR_DISABLEDBACKGROUND]  <br/> |
|PageBackground  <br/> |Color de fondo de la página. Aparece detrás de la imagen de fondo opcional.  <br/> |[T_THEME_COLOR_PAGEBACKGROUND]  <br/> |
|HeaderBackground  <br/> |Color de fondo de la zona de encabezado de la página.  <br/> |[T_THEME_COLOR_HEADERBACKGROUND]  <br/> |
|FooterBackground  <br/> |Color de fondo de la zona de pie de página de la página.  <br/> |[T_THEME_COLOR_FOOTERBACKGROUND]  <br/> |
|SelectionBackground  <br/> |Color de fondo de los elementos de lista seleccionados y los elementos de menú desplegable.  <br/> |[T_THEME_COLOR_SELECTIONBACKGROUND]  <br/> |
|HoverBackground  <br/> |Color de fondo de los elementos de lista y los elementos de menú desplegable al pasar.  <br/> |[T_THEME_COLOR_HOVERBACKGROUND]  <br/> |
|RowAccent  <br/> |Borde izquierdo con énfasis en elementos de lista seleccionados.  <br/> |[T_THEME_COLOR_ROWACCENT]  <br/> |
|StrongLines  <br/> |Bordes de controles de explorador al pasar.  <br/> |[T_THEME_COLOR_STRONGLINES]  <br/> |
|Lines  <br/> |Bordes de controles de explorador.  <br/> |[T_THEME_COLOR_LINES]  <br/> |
|SubtleLines  <br/> |Color de borde tenue. Por ejemplo, líneas de cuadrícula para edición incluida.  <br/> |[T_THEME_COLOR_SUBTLELINES]  <br/> |
|DisabledLines  <br/> |Color de borde para controles de explorador deshabilitados como cuadros de entrada y selección.  <br/> |[T_THEME_COLOR_DISABLEDLINES]  <br/> |
|AccentLines  <br/> |Color de borde con foco para controles de explorador seleccionados.  <br/> |[T_THEME_COLOR_ACCENTLINES]  <br/> |
|DialogBorder  <br/> |Color de borde de los cuadros de diálogo.  <br/> |[T_THEME_COLOR_DIALOGBORDER]  <br/> |
|Navigation  <br/> |Color del texto de los elementos de navegación horizontales y verticales.  <br/> |[T_THEME_COLOR_NAVIGATION]  <br/> |
|NavigationAccent  <br/> |Color del texto de un elemento de navegación horizontal seleccionado.  <br/> |[T_THEME_COLOR_NAVIGATIONACCENT]  <br/> |
|NavigationHover  <br/> |Color del texto de navegación al pasar. Se aplica a la navegación de nivel superior y al Inicio rápido en modo horizontal.  <br/> |[T_THEME_COLOR_NAVIGATIONHOVER]  <br/> |
|NavigationPressed  <br/> |Color del texto de un elemento de navegación al presionar. Se aplica a la navegación de nivel superior y al Inicio rápido en modo horizontal.  <br/> |[T_THEME_COLOR_NAVIGATIONPRESSED]  <br/> |
|NavigationHoverBackground  <br/> |Color de fondo de los elementos del Inicio rápido en modo vertical al pasar sobre el elemento de navegación.  <br/> |[T_THEME_COLOR_NAVIGATIONHOVERBACKGROUND]  <br/> |
|NavigationSelectedBackground  <br/> |Color de fondo de los elementos del Inicio rápido en modo vertical una vez seleccionado el elemento de navegación.  <br/> |[T_THEME_COLOR_NAVIGATIONSELECTEDBACKGROUND]  <br/> |
|EmphasisText  <br/> |Color del texto que aparece sobre fondo con énfasis.  <br/> |[T_THEME_COLOR_EMPHASISTEXT]  <br/> |
|EmphasisBackground  <br/> |Color de fondo con énfasis que aparece directamente detrás de texto con énfasis.  <br/> |[T_THEME_COLOR_EMPHASISBACKGROUND]  <br/> |
|EmphasisHoverBackground  <br/> |Color de fondo al pasar, para elementos que usan fondo con énfasis.  <br/> |[T_THEME_COLOR_EMPHASISHOVERBACKGROUND]  <br/> |
|EmphasisBorder  <br/> |Color del borde de los elementos que usan fondo con énfasis.  <br/> |[T_THEME_COLOR_EMPHASISBORDER]  <br/> |
|EmphasisHoverBorder  <br/> |Color del borde al pasar, para elementos que usan fondo con énfasis.  <br/> |[T_THEME_COLOR_EMPHASISHOVERBORDER]  <br/> |
|SubtleEmphasisText  <br/> |Texto que aparece sobre fondo con énfasis tenue.  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISTEXT]  <br/> |
|SubtleEmphasisCommandLinks  <br/> |Color de vínculo de comando para vínculos que aparecen sobre fondo con énfasis tenue.  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISCOMMANDLINKS]  <br/> |
|SubtleEmphasisBackground  <br/> |Fondo que aparece directamente detrás de texto con énfasis tenue.  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISBACKGROUND]  <br/> |
|TopBarText  <br/> |Color de texto y glifo del menú de bienvenida, los iconos de la barra de inicio rápido y las pestañas de la cinta cerradas.  <br/> |[T_THEME_COLOR_TOPBARTEXT]  <br/> |
|TopBarBackground  <br/> |Color de fondo de la barra superior, que se ve debajo y a la derecha de la navegación de conjunto.  <br/> |[T_THEME_COLOR_TOPBARBACKGROUND]  <br/> |
|TopBarHoverText  <br/> |Color de texto y glifo al pasar del menú de bienvenida, los iconos de la barra de inicio rápido y las pestañas de la cinta cerradas.  <br/> |[T_THEME_COLOR_TOPBARHOVERTEXT]  <br/> |
|TopBarPressedText  <br/> |Color de texto y glifo para cuando se presionan el menú de bienvenida, los iconos de la barra de inicio rápido o las pestañas de la cinta cerradas.  <br/> |[T_THEME_COLOR_TOPBARPRESSEDTEXT]  <br/> |
|HeaderText  <br/> |Color del texto base de cualquier elemento de la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERTEXT]  <br/> |
|HeaderSubtleText  <br/> |Texto auxiliar del cuadro de búsqueda cuando está en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERSUBTLETEXT]  <br/> |
|HeaderDisableText  <br/> |Texto del cuadro de búsqueda si este está deshabilitado y en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERDISABLETEXT]  <br/> |
|HeaderNavigationText  <br/> |Color del texto base de los vínculos de navegación de la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONTEXT]  <br/> |
|HeaderNavigationHoverText  <br/> |Color del texto de los vínculos de navegación de la zona del encabezado al pasar sobre ellos.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONHOVERTEXT]  <br/> |
|HeaderNavigationPressedText  <br/> |Color del texto de los vínculos de navegación de la zona del encabezado al presionarlos.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONPRESSEDTEXT]  <br/> |
|HeaderNavigationSelectedText  <br/> |Color del texto de los vínculos de navegación de la zona del encabezado una vez seleccionado el vínculo.  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONSELECTEDTEXT]  <br/> |
|HeaderLines  <br/> |Líneas del cuadro de búsqueda cuando está en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERLINES]  <br/> |
|HeaderStrongLines  <br/> |Líneas del cuadro de búsqueda al pasar cuando está en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERSTRONGLINES]  <br/> |
|HeaderAccentLines  <br/> |Líneas del cuadro de búsqueda con foco cuando está en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERACCENTLINES]  <br/> |
|HeaderSublteLines  <br/> |Líneas tenues dentro de la zona del encabezado. No se usa en el CSS predeterminado.  <br/> |[T_THEME_COLOR_HEADERSUBTLELINES]  <br/> |
|HeaderDisabledLines  <br/> |Líneas del cuadro de búsqueda si está deshabilitado en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERDISABLEDLINES]  <br/> |
|HeaderDisabledBackground  <br/> |Fondo del cuadro de búsqueda si está deshabilitado en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERDISABLEDBACKGROUND]  <br/> |
|HeaderFlyoutBorder  <br/> |Borde de los menús desplegables cuando se originan desde la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERFLYOUTBORDER]  <br/> |
|HeaderSiteTitle  <br/> |Color del texto del título del sitio si está en la zona del encabezado.  <br/> |[T_THEME_COLOR_HEADERSITETITLE]  <br/> |
|SuiteBarBackground  <br/> |Color de fondo de la navegación de conjunto.  <br/> |[T_THEME_COLOR_SUITEBARBACKGROUND]  <br/> |
|SuiteBarHoverBackground  <br/> |Color de fondo al pasar de la navegación de conjunto.  <br/> |[T_THEME_COLOR_SUITEBARHOVERBACKGROUND]  <br/> |
|SuiteBarText  <br/> |Color de texto y glifo de los elementos de la navegación de conjunto.  <br/> |[T_THEME_COLOR_SUITEBARTEXT]  <br/> |
|SuiteBarDisabledText  <br/> |Color de texto y glifo de los elementos de conjunto deshabilitados. No se usa en el CSS predeterminado.  <br/> |[T_THEME_COLOR_SUITEBARDISABLEDTEXT]  <br/> |
|ButtonText  <br/> |Color del texto de los botones.  <br/> |[T_THEME_COLOR_BUTTONTEXT]  <br/> |
|ButtonDisabledText  <br/> |Color del texto de los botones deshabilitados.  <br/> |[T_THEME_COLOR_BUTTONDISABLEDTEXT]  <br/> |
|ButtonBackground  <br/> |Color de fondo de los botones.  <br/> |[T_THEME_COLOR_BUTTONBACKGROUND]  <br/> |
|ButtonHoverBackground  <br/> |Color de fondo de los botones al pasar.  <br/> |[T_THEME_COLOR_BUTTONHOVERBACKGROUND]  <br/> |
|ButtonPressedBackground  <br/> |Color de fondo de los botones al ser presionados.  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBACKGROUND]  <br/> |
|ButtonDisabledBackground  <br/> |Color de fondo de los botones deshabilitados.  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBACKGROUND]  <br/> |
|ButtonBorder  <br/> |Color de borde de los botones.  <br/> |[T_THEME_COLOR_BUTTONBORDER]  <br/> |
|ButtonHoverBorder  <br/> |Color de borde de los botones al pasar.  <br/> |[T_THEME_COLOR_BUTTONHOVERBORDER]  <br/> |
|ButtonPressedBorder  <br/> |Color de borde de los botones al ser presionados.  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBORDER]  <br/> |
|ButtonDisabledBorder  <br/> |Color de borde de los botones que están deshabilitados.  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBORDER]  <br/> |
|ButtonGlyph  <br/> |Color de glifo de un glifo que aparece en un botón.  <br/> |[T_THEME_COLOR_BUTTONGLYPH]  <br/> |
|ButtonGlyphActive  <br/> |Color de glifo al pasar de un glifo que aparece en un botón.  <br/> |[T_THEME_COLOR_BUTTONGLYPHACTIVE]  <br/> |
|ButtonGlyphDisabled  <br/> |Color de glifo de un botón deshabilitado.  <br/> |[T_THEME_COLOR_BUTTONGLYPHDISABLED]  <br/> |
|TileText  <br/> |Texto que aparece sobre la capa de fondo del icono.  <br/> |[T_THEME_COLOR_TILETEXT]  <br/> |
|TileBackgroundOverlay  <br/> |Color de la capa de fondo de los iconos.  <br/> |[T_THEME_COLOR_TILEBACKGROUNDOVERLAY]  <br/> |
|ContentAccent1  <br/> |Primer color de énfasis que puede seleccionar un usuario en el selector de color del editor de texto enriquecido.  <br/> |[T_THEME_COLOR_CONTENTACCENT1]  <br/> |
|ContentAccent2  <br/> |Segundo color de énfasis que puede seleccionar un usuario en el selector de color del editor de texto enriquecido.  <br/> |[T_THEME_COLOR_CONTENTACCENT2]  <br/> |
|ContentAccent3  <br/> |Tercer color de énfasis que puede seleccionar un usuario en el selector de color del editor de texto enriquecido.  <br/> |[T_THEME_COLOR_CONTENTACCENT3]  <br/> |
|ContentAccent4  <br/> |Cuarto color de énfasis que puede seleccionar un usuario en el selector de color del editor de texto enriquecido.  <br/> |[T_THEME_COLOR_CONTENTACCENT4]  <br/> |
|ContentAccent5  <br/> |Quinto color de énfasis que puede seleccionar un usuario en el selector de color del editor de texto enriquecido.  <br/> |[T_THEME_COLOR_CONTENTACCENT5]  <br/> |
|ContentAccent6  <br/> |Sexto color de énfasis que puede seleccionar un usuario en el selector de color del editor de texto enriquecido.  <br/> |[T_THEME_COLOR_CONTENTACCENT6]  <br/> |
   

## Combinaciones de fuentes
<a name="font"> </a>

Las fuentes se definen en la combinación de fuentes (archivo .spfont) y la vista previa de página maestra (archivo .preview) de un sitio determinado de SharePoint. La combinación de fuentes define las fuentes que se usan en cuatro zonas: título, navegación, encabezado y cuerpo. En SharePoint 2013 se incluyen siete combinaciones de fuentes. Es posible crear combinaciones de fuentes adicionales. Los archivos de combinación de fuentes se encuentran en la subcarpeta **15** de la Galería de temas del sitio raíz de la colección de sitios (http:// _NombreDeLaColecciónDeSitios_/_catalogs/theme/15/). Para obtener acceso a la Galería de temas desde la interfaz de usuario de SharePoint, en la página **Configuración del sitio**, en **Galerías del diseñador web**, seleccione **Temas** y luego **15**.
  
    
    
En el siguiente ejemplo se describe el formato de un archivo .spfont.
  
    
    



```XML

<?xml version="1.0" encoding="utf-8"?>
<s:fontScheme name="FontSchemeName" previewSlot1="Slot1" previewSlot2="Slot2" xmlns:s="http://schemas.microsoft.com/sharepoint/">
  <s:fontSlots>
    <s:fontSlot name="FontSlotName">
      <s:latin typeface="LatinScriptFont" />
      <s:ea typeface="EAScriptFont"/>
      <s:cs typeface="CSFont" />
      <s:font script="Language" typeface="ScriptFont" />
      <!--Additional fonts-->
  </s:fontSlots>
  <!--Additional font slots-->
</s:fontScheme>
```

En un archivo .spfont, se sustituyen los siguientes marcadores de posición:
  
    
    

-  _FontSchemeName_ es el nombre de la combinación de fuentes.
    
  
-  _Slot1_ es el nombre de la ranura de fuente que se desea usar como primer bloque del icono de fuente en el selector de combinaciones de fuentes en el asistente **Cambiar la apariencia**.
    
  
-  _Slot2_ es el nombre de la ranura de fuente que se desea usar como segundo bloque del icono de fuente en el selector de combinaciones de fuentes en el asistente **Cambiar la apariencia**.
    
  
-  _FontSlotName_ es el nombre de la ranura de fuente que se está definiendo (por ejemplo, title).
    
  
-  _LatinScriptFont_ es la fuente que se va a usar en caligrafías latinas. Esta fuente también es la fuente de reserva. Es decir, es la fuente que se utiliza para un idioma que no tiene una caligrafía definida explícitamente en la combinación de fuentes.
    
    > **NOTA**
      > Para usar fuentes web en la combinación de fuentes, tiene que proporcionar información adicional. Para obtener más información, consulte la sección  [Fuentes web](#webFont) de este artículo.
-  _EAScriptFont_ es la fuente que se usa en caligrafías del este de Asia. SharePoint no usa en este momento el elemento **<s:ea>**, pero el elemento **<s:ea>** aún es necesario en la combinación de fuentes.
    
  
-  _CSFont_ es la fuente que se usa en caligrafías complejas. SharePoint no usa en este momento el elemento **<s:cs>**, pero el elemento **<s:cs>** aún es necesario en la combinación de fuentes.
    
  
-  _Language_ es la caligrafía del idioma.
    
  
-  _ScriptFont_ es la fuente que se usa para la caligrafía del idioma especificada.
    
  
En el siguiente ejemplo se muestra una parte de un archivo .spfont.
  
    
    



```XML

<s:fontScheme name="Georgia" previewSlot1="title" previewSlot2="body" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:fontSlots>
        <s:fontSlot name="title">
            <s:latin typeface="Georgia"/>
            <s:ea typeface=""/>
            <s:cs typeface="Segoe UI Light" />
            <s:font script="Arab" typeface="Tahoma" />
            <s:font script="Deva" typeface="Mangal" />
            <s:font script="Grek" typeface="Segoe UI Light" />
            <s:font script="Hang" typeface="Malgun Gothic" />
            <s:font script="Hans" typeface="Microsoft YaHei" />
            <s:font script="Hant" typeface="Microsoft JhengHei" />
            <s:font script="Hebr" typeface="Tahoma" />
            <s:font script="Hira" typeface="Meiryo" />
            <s:font script="Thai" typeface="Tahoma" />
            <s:font script="Armn" typeface="Tahoma" />
            <s:font script="Beng" typeface="Vrinda" />
            <s:font script="Cher" typeface="Plantagenet Cherokee" />
            <s:font script="Ethi" typeface="Nyala" />
            <s:font script="Geor" typeface="Sylfaen" />
            <s:font script="Gujr" typeface="Shruti" />
            <s:font script="Guru" typeface="Raavi" />
            <s:font script="Knda" typeface="Tunga" />
            <s:font script="Khmr" typeface="DaunPenh" />
            <s:font script="Laoo" typeface="DokChampa" />
            <s:font script="Mlym" typeface="Kartika" />
            <s:font script="Mymr" typeface="Myanmar Text" />
            <s:font script="Orya" typeface="Kalinga" />
            <s:font script="Sinh" typeface="Iskoola Pota" />
            <s:font script="Syrc" typeface="Estrangelo Edessa" />
            <s:font script="Taml" typeface="Latha" />
            <s:font script="Telu" typeface="Gautami" />
            <s:font script="Thaa" typeface="MV Boli" />
            <s:font script="Tibt" typeface="Cordia New" />
            <s:font script="Yiii" typeface="Microsoft Yi Baiti" />
        </s:fontSlot>
…
```

SharePoint 2013 incluye compatibilidad con las fuentes web. Para usar fuentes web en la combinación de fuentes, tiene que proporcionar información adicional. Para obtener más información, consulte la sección  [Fuentes web](#webFont) de este artículo.
  
    
    

### Fuentes web seguras
<a name="websafeFont"> </a>

Las fuentes web seguras son un conjunto de fuentes ampliamente usadas y disponibles en la mayoría de los dispositivos de forma predeterminada. Para especificar una fuente web segura en la combinación de fuentes, incluya el nombre de la fuente en el atributo **typeface** de la ranura de fuente. En el siguiente ejemplo se muestra una fuente web segura usada en una combinación de fuentes.
  
    
    

```XML

<s:fontSlot name="title">
  <s:latin typeface="Georgia"/>
…
</s:fontSlot>
```


### Fuentes web
<a name="webFont"> </a>

Las fuentes web son fuentes disponibles en Internet. Cuando un usuario ve un sitio que usa fuentes web, el explorador web descarga los archivos de fuente necesarios junto con el resto de la página. Para especificar una fuente web, tiene que proporcionar la dirección URL de los archivos de fuente web en cuatro formatos de fuente (para la compatibilidad entre exploradores) y una imagen en miniatura pequeña y grande para presentar los nombre de fuente en el selector de combinaciones de fuentes.
  
    
    
En el siguiente ejemplo se describe la información necesaria para usar una fuente web en un elemento **<s:latin>**.
  
    
    



```XML

<s:latin typeface="FontName"
  eotsrc="EotFile"
  woffsrc="WoffFile"
  ttfsrc="TtfFile"
  svgsrc="SvgFile"
  largeimgsrc="LargeImgFile"
  smallimgsrc="SmallImgFile" />

```

En este ejemplo de uso de una fuente web, se deben sustituir los siguientes marcadores de posición:
  
    
    

-  _FontName_ es el nombre de la fuente web.
    
  
-  _EotFile_ es la dirección URL relativa del archivo de fuente Embedded Open Type.
    
  
-  _WoffFile_ es la dirección URL relativa del archivo de fuente Web Open Font.
    
  
-  _TtfFile_ es la dirección URL relativa del archivo de fuente TrueType.
    
  
-  _SvgFile_ es la dirección URL relativa del archivo de fuente Scalable Vector Graphics.
    
  
-  _LargeImgFile_ es la dirección URL relativa de la imagen en miniatura grande que se desea usar en el selector de combinaciones de fuentes.
    
  
-  _SmallImgFile_ es la dirección URL relativa de la imagen en miniatura pequeña que se desea usar en el selector de combinaciones de fuentes.
    
  

### Ranuras de fuente
<a name="fontSlot"> </a>

En la tabla 1 se describen las ranuras de fuente disponibles y la ubicación de la página en la que se utilizan.
  
    
    

**Tabla 1. Ranuras de fuente**


|**Nombre de ranura de fuente**|**Descripción**|
|:-----|:-----|
|title  <br/> |Se usa para el título de la página.  <br/> |
|navigation  <br/> |Se usa para los elementos de navegación horizontales y verticales de la página.  <br/> |
|large-heading  <br/> |Se usa para el encabezado H1.  <br/> |
|heading  <br/> |Se usa para los encabezados H2 y H3, los títulos de elementos web, los títulos de cuadros de diálogo y los títulos de llamadas.  <br/> |
|small-heading  <br/> |Se usa para encabezados H4.  <br/> |
|large-body  <br/> |Se usa para el texto de cuerpo grande (15 y 19 píxeles).  <br/> |
|body  <br/> |Fuente base que se usa en cualquier otro lugar de la página.  <br/> |
   

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Introducción a los temas para SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Procedimiento para implementar un tema personalizado en SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [Actualizar de CSS y temas personalizados a SharePoint 2013](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [Cómo: crear un archivo de vista previa de página maestra en SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [Blog del equipo de SharePoint: presuma de estilo con los temas de SharePoint](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [Capacidades de personalización de marca y diseño de SharePoint 2013 Design Manager](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

  
    
    

