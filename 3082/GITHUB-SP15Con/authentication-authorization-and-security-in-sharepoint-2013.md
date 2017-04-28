---
title: Autenticación, autorización y seguridad en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8734790c-eb75-4d78-9604-7cc23b33b693
---


# Autenticación, autorización y seguridad en SharePoint 2013

## Novedades para autenticación, autorización y seguridad en SharePoint 2013
<a name="SP15_AuthenticationAuthorizationSecurity_WhatsNew"> </a>

A continuación se especifican algunas de las mejoras agregadas a SharePoint 2013. 
  
    
    

- Inicio de sesión del usuario
    
  - SharePoint 2013 continúa ofreciendo compatibilidad con los modos de notificaciones y autenticación clásico. La autenticación de notificaciones es la opción de autenticación predeterminada en SharePoint 2013. La autenticación de modo clásico está en desuso y solo puede administrarse con Windows PowerShell. Muchas de las funciones de SharePoint 2013 requieren el modo de notificaciones. 
    
  
  - El método **MigrateUsers** de SharePoint 2010 ahora está en desuso y ya no es la forma correcta para migrar cuentas. Para migrar cuentas, use el nuevo cmdlet Windows PowerShell denominado `Convert-SPWebApplication`. Para obtener más información, consulte  [Migrar del modo clásico a autenticaciones basadas en notificaciones en SharePoint 2013](http://technet.microsoft.com/es-es/library/gg251985.aspx).
    
  
  - Se elimina el requisito de registrar a los proveedores de notificaciones. Sin embargo, tiene que configurar previamente el tipo de notificaciones. Puede elegir los caracteres para el tipo de notificación y no hay ninguna obligación en el orden de los tipos de notificación.
    
  
  - SharePoint 2013 realiza el seguimiento de cookies de **FedAuth** en el nuevo servicio de caché distribuido mediante Windows Server AppFabric Caching.
    
  
  - Se proporciona un registro significativamente mayor para ayudar a solucionar los problemas de autenticación. 
    
  
- Autenticación de servicios y aplicaciones
    
  - En SharePoint 2013, ahora puede crear aplicaciones para SharePoint. Un Complemento de SharePoint tiene su propia identidad y está asociado con una entidad de seguridad, llamada entidad de seguridad de aplicación. Al igual que los usuarios y los grupos, una entidad de seguridad de aplicación tiene ciertos derechos y permisos. 
    
  
  - En SharePoint 2013, el servicio de token de seguridad (STS) de servidor a servidor proporciona tokens de acceso para la autenticación de servidor a servidor. El STS de servidor a servidor permite tokens para obtener acceso temporal a otros servicios de la aplicación, tales como Exchange Server 2013 y Microsoft Lync 2013, y aplicaciones de SharePoint 2013.
    
  

## Autenticación y autorización
<a name="SP15_AuthenticationAuthorizationSecurity_AuthenticationAndAuthorization"> </a>

SharePoint 2013 admite la seguridad para el acceso de usuario en los niveles de sitio web, lista, carpeta de lista o biblioteca y elemento. La administración de la seguridad se basa en roles en todos los niveles y proporciona una administración de seguridad uniforme en toda la plataforma de SharePoint 2013 con una interfaz de usuario basada en roles coherente y un modelo de objetos destinado a asignar permisos sobre los objetos. Por consiguiente, la seguridad de los niveles de lista, carpeta o elemento implementa el mismo modelo de usuario que la seguridad de nivel de sitio web, lo que facilita la administración de derechos de usuario y los derechos de grupo en todo el sitio web. SharePoint 2013 admite asimismo los permisos exclusivos para las carpetas y los elementos contenidos en las listas y las bibliotecas de documentos.
  
    
    

> **NOTA**
> Para obtener información sobre la autorización relacionada con Complementos de SharePoint, consulte  [Autorización y autenticación de complementos de SharePoint](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx). 
  
    
    

Por autorización se entiende el proceso mediante que SharePoint 2013 proporciona seguridad para sitios web, listas, carpetas o elementos al determinar los usuarios que pueden realizar acciones específicas en un objeto concreto. En el proceso de autorización se da por supuesto que el usuario ya se ha autenticado, proceso mediante que SharePoint 2013 identifica al usuario actual. SharePoint 2013 no implementa su propio sistema de autenticación o administración de identidades, sino que se basa en sistemas externos, ya sea una autenticación de Windows o una autenticación no basada en Windows.
  
    
    
SharePoint 2013 es compatible con los siguientes tipos de autenticación:
  
    
    

- **Windows:** se admiten todas las opciones de integración de autenticación de Internet Information Services (IIS) y de Windows, incluidas las opciones de autenticación básica, implícita, de certificados, Windows NT LAN Manager (NTLM) y Kerberos. La autenticación de Windows permite que IIS realice la autenticación para SharePoint 2013.
    
    Para obtener información sobre cómo iniciar sesión en SharePoint con el modo de notificaciones de Windows, consulte  [Notificaciones entrantes: inicio de sesión en SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md).
    
    > **IMPORTANTE**
    >  Para obtener información sobre la suspensión de la suplantación, consulte [Evitar la suplantación del usuario que realiza la llamada](http://msdn.microsoft.com/es-es/library/ff407852.aspx). 
- **Formularios de ASP.NET:** se admite el sistema de administración de identidades no basado en Windows que usa el sistema de autenticación acoplable basado en formularios de ASP.NET. Este modo permite que SharePoint 2013 funcione con una serie de sistemas de administración de identidades, incluidos los grupos o roles definidos externamente, como el protocolo ligero de acceso a directorios (LDAP) y los sistemas ligeros de administración de identidades de bases de datos. La autenticación de formularios permite que ASP.NET realice la autenticación para SharePoint 2013, lo que suele implicar la redirección a una página de inicio de sesión. En SharePoint 2013, los formularios de ASP.NET se admiten únicamente a través de la autenticación de notificaciones. Así, un proveedor de formularios deberá estar registrado en una aplicación web configurada para notificaciones.
    
    Para obtener información sobre el inicio de sesión en SharePoint mediante el inicio de sesión de rol pasivo y pertenencia ASP.NET, consulte  [Notificaciones entrantes: inicio de sesión en SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md).
    
  

> **NOTA**
> SharePoint 2013 no funciona con un proveedor de pertenencia que distingue mayúsculas de minúsculas, ya que usa el almacenamiento SQL que no distingue mayúsculas de minúsculas para todos los usuarios de la base de datos, con independencia del proveedor de pertenencia. 
  
    
    


## Autenticación e identidad basada en notificaciones
<a name="SP15_AuthenticationAuthorizationSecurity_ClaimsBasedIdentity"> </a>

La identidad basada en notificaciones es un modelo de identidad de SharePoint 2013 que incluye características como autenticación entre usuarios de sistemas de Windows y sistemas que no son de Windows, varios tipos de autenticación, autenticación más segura en tiempo real, un conjunto más amplio de tipos principales y delegación de identidad de usuario entre aplicaciones.
  
    
    
Cuando un usuario inicia sesión en SharePoint 2013, el token del usuario se valida y se usa después para iniciar sesión en SharePoint. El token del usuario es un token de seguridad emitido por un proveedor de notificaciones. Se admiten los siguientes modos de acceso o inicio de sesión:
  
    
    

- Inicio de sesión en modo de notificaciones de Windows (predeterminado)
    
  
- Inicio de sesión pasivo SAML
    
  
- Inicio de sesión pasivo de rol y pertenencia ASP.NET
    
  
- Inicio de sesión en modo clásico de Windows (en desuso en esta versión)
    
  

> **NOTA**
> Para obtener más información sobre cómo iniciar sesión en SharePoint y los diferentes modos de inicio de sesión, vea  [Notificaciones entrantes: inicio de sesión en SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md). 
  
    
    

Al crear aplicaciones para notificaciones, el usuario presenta una identidad en la aplicación como conjunto de notificaciones. Una notificación puede ser el nombre del usuario, otra podría ser una dirección de correo electrónico. La idea es que un sistema de identidad externa se configura para proporcionar a la aplicación toda la información que necesita sobre el usuario con cada solicitud, con la comprobación criptográfica de que los datos de identidad recibidos por la aplicación provienen de una fuente de confianza.
  
    
    
Con este modelo, el inicio de sesión único es mucho más sencillo y la aplicación deja de ser responsable de las siguientes acciones:
  
    
    

- Autenticación de usuarios
    
  
- Almacenamiento de cuentas de usuario y contraseñas
    
  
- Llamada a directorios de empresa para buscar detalles de identidad del usuario
    
  
- Integración con sistemas de identidad de otras plataformas o compañías
    
  
Bajo este modelo, la aplicación toma decisiones relacionadas con identidad en función de las notificaciones proporcionadas por el usuario. Esto puede ser cualquier cosa, desde la personalización sencilla de la aplicación con el nombre del usuario hasta la autorización del usuario para que obtenga acceso a recursos y características de alto nivel en la aplicación.
  
    
    

> **NOTA**
> Para obtener más información acerca de la identidad basada en notificaciones y los proveedores de notificaciones, vea  [Identidad y conceptos basados en notificaciones en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md) y [Proveedor de notificaciones en SharePoint 2013](claims-provider-in-sharepoint-2013.md). 
  
    
    


## Autenticación basada en formularios
<a name="SP15_AuthenticationAuthorizationSecurity_FormsBasedAuthentication"> </a>

La autenticación basada en formularios proporciona una administración de identidades personalizada en SharePoint 2013 mediante la implementación de un proveedor de pertenencia, que define las interfaces para identificar y autenticar a los usuarios individuales, y un administrador de roles, que define las interfaces para agrupar a los usuarios individuales en grupos lógicos o roles. En SharePoint 2013, un proveedor de pertenencia debe implementar el método  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) necesario. El proveedor de roles emplea el nombre de usuario para devolver una lista de roles a los que el usuario pertenece.
  
    
    
El proveedor de pertenencia es responsable de validar la información de credenciales con el método  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) (necesario ahora en SharePoint 2013), pero el servicio de token de seguridad (STS) crea el token de usuario real. El STS crea el token de usuario a partir del nombre de usuario validado por el proveedor de pertenencia y a partir del conjunto de pertenencias a grupos que se asocia con el nombre de usuario proporcionado por el proveedor de pertenencia.
  
    
    

> **NOTA**
> Para más información sobre STS, consulte  [Identidad y conceptos basados en notificaciones en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md). 
  
    
    

El administrador de roles es opcional. De este modo, si un sistema de autenticación personalizada no admite grupos, no es necesario ningún administrador de roles. SharePoint 2013 admite un proveedor de pertenencia y un administrador de roles por zona URL (  [SPUrlZone](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPUrlZone.aspx) ). Los roles de formularios de ASP.NET no tienen derechos inherentes asociados. En su lugar, SharePoint 2013 asigna derechos a las roles de formularios mediante sus directivas y autorización. En SharePoint 2013, la autenticación basada en formularios se integra en el modelo de identidades basado en notificaciones. Si necesita un mayor aumento para soslayar el límite de un proveedor de roles por zona URL, puede basarse en proveedores de notificaciones.
  
    
    

> **NOTA**
> Para obtener más información acerca de la identidad basada en notificaciones y los proveedores de notificaciones, vea  [Identidad y conceptos basados en notificaciones en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md) y [Proveedor de notificaciones en SharePoint 2013](claims-provider-in-sharepoint-2013.md). 
  
    
    

En el inicio de sesión de rol pasivo y pertenencia ASP.NET, el inicio de sesión ocurre al redireccionar el cliente a una página web en la que los controles del inicio de sesión ASP.NET están hospedados. Una vez creado el objeto de identidad que representa una identidad de usuario, SharePoint 2013 lo convierte en un objeto  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) (que representa una identidad basada en notificaciones de un usuario).
  
    
    

> **NOTA**
> Para más información acerca de cómo iniciar sesión en SharePoint, consulte  [Notificaciones entrantes: inicio de sesión en SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md). 
  
    
    

SharePoint 2013 usa la interfaz de proveedor de roles estándar de ASP.NET para recopilar la información de grupo del usuario actual. Por lo que respecta a la autenticación, los roles y los grupos son iguales: un método de agrupación de usuarios en conjuntos lógicos de cara a la autorización. Cada rol de ASP.NET se trata como un grupo de dominio en SharePoint 2013. 
  
    
    
Para obtener información sobre el marco de autenticación acoplable proporcionado por ASP.NET, consulte Nuevas características de seguridad en ASP.NET.
  
    
    

> **NOTA**
> Para más información sobre la autenticación basada en formularios, consulte  [Autenticación de formularios en productos y tecnologías de SharePoint (parte 1): Introducción](http://msdn.microsoft.com/library/e5efd4d7-b369-49f0-a6f7-431d21daff20%28Office.15%29.aspx). 
  
    
    


## Recursos adicionales
<a name="SP15_AuthenticationAuthorizationSecurity_AdditionalResources"> </a>


-  [Autorización, usuarios, grupos y el modelo de objetos de SharePoint 2013](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [Rol, herencia, elevación de privilegios y cambios de contraseña en SharePoint 2013](role-inheritance-elevation-of-privilege-and-password-changes-in-sharepoint-2013.md)
    
  
-  [Identidad basada en notificaciones en SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Identidad y conceptos basados en notificaciones en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [Configuración, administración y recursos en SharePoint 2013](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

