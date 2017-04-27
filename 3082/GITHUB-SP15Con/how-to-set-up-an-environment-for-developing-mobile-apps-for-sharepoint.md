---
title: Cómo Configurar un entorno de desarrollo de aplicaciones móviles para SharePoint
ms.prod: SHAREPOINT
ms.assetid: acaf556d-e20d-478d-8c59-2efd8efb9dcb
---


# Cómo: Configurar un entorno de desarrollo de aplicaciones móviles para SharePoint
Obtenga información sobre los requisitos del sistema y la configuración de un entorno de desarrollo para proyectos de movilidad de SharePoint.
Una configuración mínima para trabajar con proyectos de movilidad de SharePoint requiere un servidor que ejecute SharePoint 2013 (o una cuenta de SharePoint Online) y un entorno de desarrollo en un sistema operativo cliente independiente. Los sistemas operativos cliente (como Windows 7) no admiten la instalación de SharePoint 2013 y, al mismo tiempo, los sistemas operativos del servidor (como Windows Server 2008) no admiten la instalación de las herramientas necesarias para el desarrollo de Windows Phone.
  
    
    


## Proyectos de desarrollo de Windows Phone y SharePoint Server
<a name="SP15Setupmobile_winphone"> </a>

Para crear y probar aplicaciones de Windows Phone que interactúan con SharePoint, es necesario tener acceso a un servidor que ejecuta SharePoint 2013 o una cuenta de SharePoint Online, y también tener suficientes permisos en los sitios y las listas que se desean usar en las soluciones. Se recomienda usar una instalación de SharePoint Server que está dedicada a la prueba y el desarrollo como servidor de destino mientras desarrolla sus proyectos. Use SharePoint Server en un entorno de producción como servidor de destino después de que la solución haya superado las pruebas suficientes.
  
    
    
Para obtener información sobre la instalación y configuración de SharePoint 2013, consulte la documentación de la sección  [Productos de SharePoint](http://technet.microsoft.com/es-es/library/ee428287.aspx) de Microsoft TechNet Library. Para obtener información sobre el uso de SharePoint Online en las soluciones de desarrollo, visite el [Centro de recursos para desarrolladores de SharePoint Online ](http://msdn.microsoft.com/es-es/sharepoint/gg153540.aspx).
  
    
    
Para los ejemplos de código que se incluyen en esta documentación, se supone que un desarrollador que trabaja con el ejemplo tiene o puede obtener permisos suficientes en listas y sitios de SharePoint para que pueda agregar, editar y eliminar datos.
  
    
    

## Configuración de un entorno de desarrollo de clientes para proyectos de movilidad de SharePoint
<a name="SP15Setupmobile_configure"> </a>

Para desarrollar Complementos de SharePoint para su uso en dispositivos Windows Phone, debe configurar las herramientas de desarrollo en un equipo que ejecuta un sistema operativo cliente, y no un sistema operativo del servidor.
  
    
    

### Configuración de Windows Phone SDK 8.0

Para desarrollar Complementos de SharePoint para su uso en Windows Phone 8, debe configurar las herramientas de desarrollo en un equipo que ejecuta versiones de cliente de Windows 8 o Windows 8 Pro de 64 bits (x 64). El emulador de Windows Phone 8 requiere Windows 8 Pro y un procesador que admita SLAT (traducción de direcciones de segundo nivel).
  
    
    

1. En un equipo con un sistema operativo cliente compatible, instale  [Windows Phone SDK 8.0](http://www.microsoft.com/es-es/download/details.aspx?id=35471). El Kit de desarrollo de software (SDK) de Windows Phone 8.0 le ofrece las herramientas que necesita para desarrollar aplicaciones y juegos para Windows Phone 8 y Windows Phone 7.5.
    
    Windows Phone SDK 8.0 es un completo entorno de desarrollo que puede usar para crear aplicaciones y juegos para Windows Phone 8.0 y Windows Phone 7.5. El SDK de Windows Phone dispone de una edición independiente de Visual Studio Express 2012 para Windows Phone o puede funcionar como complemento de Visual Studio 2012 Professional, Premium o Ultimate. Con el SDK, puede usar sus conocimientos de programación y el código que ya tiene para generar aplicaciones administradas o con código nativo. Asimismo, el SDK contiene varios emuladores y herramientas adicionales para generar perfiles y probar la aplicación de Windows Phone en condiciones reales.
    
    > **NOTA**
      > Si el equipo se ajusta a los requisitos del sistema operativo y del hardware pero no a los del emulador de Windows Phone 8, se instalará y ejecutará Windows Phone SDK 8.0. Sin embargo, el emulador de Windows Phone 8 no funcionará y no se podrán implementar ni probar aplicaciones en él. Para obtener información sobre los requisitos del sistema para ejecutar el emulador de Windows Phone, consulte el  [programa de instalación y requisitos del sistema para el emulador de Windows Phone](http://msdn.microsoft.com/es-es/library/ff626524). 
2. Instale  [Microsoft SharePoint SDK para Windows Phone 8](http://www.microsoft.com/es-es/download/details.aspx?id=36818).
    
    El SDK de SharePoint para Windows Phone instala dos plantillas de Silverlight para Windows Phone (además de las que instala el SDK de Windows Phone): la plantilla Aplicación vacía de SharePoint para Windows Phone y la plantilla Aplicación de lista de SharePoint para Windows Phone. El SDK también instala las bibliotecas CSOM de SharePoint, una biblioteca de autenticación y las plantillas de proyecto de Windows Phone, y ahora es compatible con la autenticación NTLM. Puede usar las API y las plantillas integradas para crear aplicaciones de Windows Phone 8 en SharePoint 2013.
    
    Además, el SDK de SharePoint para Windows Phone instala varios ensamblados auxiliares de tiempo de ejecución (en  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v8.0\\Libraries` para una instalación estándar).
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **NOTA**
      > Actualmente, las plantillas del SDK de SharePoint para Windows Phone solo están disponibles para proyectos de C#. 
Para obtener más información acerca de las plantillas en el SDK de SharePoint para Windows Phone, consulte  [Información de plantillas de aplicaciones de SharePoint 2013 para Windows Phone en Visual Studio](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md).
  
    
    

### Configuración de Windows Phone SDK 7.1

Para desarrollar Complementos de SharePoint para su uso en Windows Phone 7, debe configurar las herramientas de desarrollo en un equipo que ejecuta Windows 7 (de 32 o 64 bits) o Windows Vista Service Pack 2 (de 32 o 64 bits). El Kit de desarrollo de software (SDK) de Windows Phone 7.1 no es compatible con Windows Server 2008 ni con Windows XP.
  
    
    

1. En un equipo con un sistema operativo cliente compatible, instale  [Windows Phone SDK 7.1](http://www.microsoft.com/es-es/download/details.aspx?id=27570).
    
    > **NOTA**
      > Una versión anterior del SDK de Windows Phone se llamaba Windows Phone Developer Tools. 

    El SDK de Windows Phone instala Microsoft Visual Studio 2010 Express para Windows Phone, el emulador de Windows Phone, XNA Game Studio y Microsoft Expression Blend para Windows Phone. Visual Studio 2010 Express para Windows Phone es un entorno de desarrollo adecuado para la mayoría de soluciones de Windows Phone. También puede usar Visual Studio 2010 Professional como entorno de desarrollo preferido, pero aún deberá instalar el SDK de Windows Phone, que instala los complementos necesarios para Visual Studio. (Actualmente, el SDK de Windows Phone no es compatible con Visual Studio 2012).
    
    Para obtener información sobre los requisitos adicionales del sistema e instrucciones para instalar el SDK de Windows Phone, consulte  [Instalación del SDK de Windows Phone](http://msdn.microsoft.com/es-es/library/ff402530). Para obtener información acerca de los requisitos del sistema para ejecutar el emulador de Windows Phone, consulte  [programa de instalación y requisitos del sistema para el emulador de Windows Phone](http://msdn.microsoft.com/es-es/library/ff626524).
    
  
2. Instale  [Microsoft SharePoint SDK para Windows Phone 7.1](http://www.microsoft.com/es-es/download/details.aspx?id=30476).
    
    El SDK de SharePoint para Windows Phone instala dos plantillas de Silverlight para Windows Phone (además de las que instala el SDK de Windows Phone): la plantilla Aplicación vacía de SharePoint para Windows Phone y la plantilla Aplicación de lista de SharePoint para Windows Phone.
    
    Además, el SDK de SharePoint para Windows Phone instala varios ensamblados auxiliares de tiempo de ejecución (en  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v7.1\\Libraries` para una instalación estándar).
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **NOTA**
      > Actualmente, las plantillas del SDK de SharePoint para Windows Phone solo están disponibles para proyectos de C#. 
Para obtener más información acerca de las plantillas en el SDK de SharePoint para Windows Phone, consulte  [Información de plantillas de aplicaciones de SharePoint 2013 para Windows Phone en Visual Studio](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md).
  
    
    

## Recursos adicionales
<a name="SP15Setupmobile_addlresources"> </a>


-  [Creación de aplicaciones de Windows Phone con acceso a SharePoint 2013](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/es-es/download/details.aspx?id=35471)
    
  
-  [Microsoft SharePoint SDK para Windows Phone 8](http://www.microsoft.com/es-es/download/details.aspx?id=36818)
    
  
-  [Windows Phone SDK 7.1](http://www.microsoft.com/es-es/download/details.aspx?id=27570)
    
  
-  [Microsoft SharePoint SDK para Windows Phone 7.1](http://www.microsoft.com/es-es/download/details.aspx?id=30476)
    
  

