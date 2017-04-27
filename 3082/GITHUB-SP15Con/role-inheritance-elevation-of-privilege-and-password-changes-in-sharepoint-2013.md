---
title: Rol, herencia, elevación de privilegios y cambios de contraseña en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: a72c6cad-9e3d-4d57-bf26-24cd1ad7f020
---


# Rol, herencia, elevación de privilegios y cambios de contraseña en SharePoint 2013

## Roles, definiciones de roles y asignaciones de roles
<a name="SP15_RoleInheritance_Role"> </a>

Un rol consta de dos partes: una definición de roles y una asignación de roles. 
  
    
    
La definición de roles, o nivel de permiso, es la lista de los derechos asociada al rol. Un derecho es una acción que se puede controlar de forma exclusiva en un sitio web de SharePoint. Por ejemplo, un usuario con el rol **Read** puede examinar páginas en el sitio web y ver elementos de listas. Los permisos de usuario nunca se administran directamente mediante derechos. Todos los permisos de grupo y usuario se administran mediante roles. Una definición de roles es una colección de derechos enlazados a un objeto específico. Las definiciones de roles (por ejemplo, **Full Control**, **Read**, **Contribute**, **Design** o **Limited Access**) se encuentran en el ámbito del sitio web y tienen el mismo significado en cualquier lugar del sitio web, si bien sus significados pueden diferir en los sitios de la misma colección de sitios. Al igual que los permisos, las definiciones de roles también se pueden heredar desde el sitio web primario. 
  
    
    
La asignación de roles es la relación entre la definición de roles, los usuarios y grupos y el ámbito (por ejemplo, un usuario puede ser un lector de la lista 1, mientras que otro usuario es un lector de la lista 2). La relación expresada mediante la asignación de roles constituye la clave para hacer que la administración de seguridad de SharePoint 2013 se base en roles. Todos los permisos se administran mediante roles; nunca se asignan derechos directamente a un usuario, sino solo colecciones de derechos significativos (definiciones de roles) bien definidas y coherentes. Los permisos únicos se administran agregando o eliminando usuarios y grupos de las definiciones de roles a través de asignaciones de roles.
  
    
    
El administrador del sitio web puede personalizar las definiciones de roles predeterminadas y crear más roles personalizados mediante la página Administrar roles, donde se enumeran las definiciones de roles disponibles en el sitio.
  
    
    

## Herencia de definiciones de roles
<a name="SP15_RoleInheritance_RoleDefInheritance"> </a>

SharePoint 2013 admite la herencia de definiciones de roles de forma similar al modo en que admite la herencia de permisos. Para dividir la herencia de las definiciones de roles, es necesario dividir la herencia de permisos.
  
    
    
Cada objeto de SharePoint puede tener su propio conjunto de permisos o heredarlo de su contenedor primario. SharePoint 2013 no admite la herencia parcial, donde un objeto hereda todos los permisos de su elemento primario y tiene además algunos permisos propios. Los permisos se heredan o son únicos. SharePoint 2013 no admite la herencia dirigida; así, un objeto solo puede heredar de su contenedor primario y no de otros objetos o contenedores.
  
    
    
Cuando un sitio web hereda definiciones de roles, los roles son de solo lectura, al igual que los permisos de solo lectura de un sitio web heredado. El usuario dispondrá de un vínculo para navegar al sitio primario que contiene las definiciones de roles únicas. El valor predeterminado para todos los sitios web nuevos, incluso los que tienen permisos únicos, es heredar las definiciones de roles del sitio web primario. Si los permisos son únicos, las definiciones de roles pueden revertirse a definiciones de roles heredadas o editarse como definiciones de roles locales.
  
    
    
La herencia de la definición de roles en un sitio web incide en la herencia de permisos según las siguientes reglas:
  
    
    

- No se pueden heredar permisos a menos que también se hereden definiciones de funciones.
    
  
- No se pueden crear definiciones de funciones únicas a menos que también se creen permisos únicos.
    
  
- No se puede revertir a definiciones de roles heredadas a menos que también se reviertan todos los permisos únicos del sitio web. Los permisos existentes dependen de las definiciones de roles.
    
  
- No se puede revertir a permisos heredados a menos que también se revierta a definiciones de roles heredadas. Los permisos para un sitio web siempre dependen de las definiciones de roles de dicho sitio.
    
  

## Administración de tokens de usuario
<a name="SP15_RoleInheritance_ManagingUserTokens"> </a>

SharePoint recopila información de tokens de usuario de la base de datos de SharePoint. Si el usuario nunca ha visitado el sitio o si el token del usuario se generó hace más de 24 horas, SharePoint genera un nuevo token de usuario intentando actualizar la lista de grupos a los que pertenece el usuario. 
  
    
    
Si la cuenta de usuario es una cuenta de NT, SharePoint usa la interfaz **AuthZ** con el fin de consultar el servicio de directorio de Active Directory para la propiedad **TokenGroups**. Esto puede producir un error si SharePoint se ejecuta en un modo de extranet y no tiene permiso para consultar Active Directory para esta propiedad.
  
    
    
Si la cuenta de usuario es un usuario de pertenencia, SharePoint consulta **RoleManager** de ASP.NET para todos los roles a los que pertenece el usuario. Esto puede producir un error si no hay un archivo .config adecuado para el archivo ejecutable actual.
  
    
    
Si SharePoint no puede obtener la pertenencia a grupos del usuario desde Active Directory o **<roleManager>**, el token recién generado contiene solo el identificador de seguridad (SID) único del usuario. No se produce ninguna excepción, pero se escribe una entrada en el registro de servidor de ULS. El nuevo token también se escribe en la base de datos de SharePoint para que no se vuelva a generar en 24 horas.
  
    
    
Después de que SharePoint obtenga un nuevo token, ya sea desde la base de datos de SharePoint o creando un nuevo token, SharePoint establece la marca de tiempo en la hora actual y, a continuación, la devuelve al autor de la llamada. Esto garantiza que el token esté actualizado durante 24 horas.
  
    
    
Después de que se devuelva el objeto  [SPUserToken](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserToken.aspx) al autor de la llamada, es responsabilidad del autor de la llamada no usar el token después de haya expirado. Puede escribir una utilidad auxiliar para realizar el seguimiento de la expiración del token mediante la grabación de la hora en que obtiene el token y comparar la diferencia con la hora actual en [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) .
  
    
    
Si se usa un token expirado para crear un sitio web de SharePoint, se produce una excepción. El valor predeterminado de tiempo de espera de los tokens es de 24 horas. Se puede tener acceso a él a través de  [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) .
  
    
    

## Elevación de privilegios
<a name="SP15_RoleInheritance_ElevationOfPrivilege"> </a>

La elevación de privilegios, una característica que se agregó en Windows SharePoint Services 3.0, le permite realizar acciones mediante programación en el código usando un mayor nivel de privilegios. El método  [SPSecurity.RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) le permite proporcionar un delegado que ejecuta un subconjunto de código en el contexto de una cuenta con privilegios superiores a los del usuario actual.
  
    
    
A continuación se muestra un uso estándar de **RunWithElevatedPrivileges**.
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    // Do things by assuming the permission of the "system account".
});
```

Con frecuencia, para realizar acciones en SharePoint, debe obtener un nuevo objeto  [SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.aspx) para que los cambios tengan efecto. Por ejemplo:
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    using (SPSite site = new SPSite(web.Site.ID))
    {
       // Do things by assuming the permission of the "system account".
    }
});
```

Aunque la elevación de privilegios ofrece una técnica eficaz para administrar la seguridad, se debe usar con cuidado. No debería exponer mecanismos directos y sin control a usuarios con privilegios bajos que les permitan eludir los permisos que se les han concedido.
  
    
    

> **IMPORTANTE**
> Si el método que se pasa a  [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) incluye alguna operación de escritura, la llamada a [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) debe ir precedida por una llamada a [SPUtility.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.ValidateFormDigest.aspx) o a [SPWeb.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.ValidateFormDigest.aspx) .
  
    
    


## Cambios de contraseña automáticos
<a name="SP15_RoleInheritance_AutomaticPasswordChange"> </a>

La característica de cambio de contraseña automático le permite actualizar e implementar contraseñas sin tener que realizar tareas de actualización manual de contraseñas en varias cuentas, servicios y aplicaciones web. Esto hace que resulte más sencillo administrar las contraseñas en SharePoint 2013. Puede usar la característica de cambio de contraseña automático para determinar si una contraseña está a punto de expirar, y también para restablecer la contraseña mediante una cadena aleatoria larga y criptográficamente segura.
  
    
    

### Cuenta administrada

Las cuentas administradas se usan para implementar la característica de cambio de contraseña automático. Las cuentas administradas mejoran la seguridad y garantizan el aislamiento de aplicaciones. Con las cuentas administradas, puede:
  
    
    

- Configurar la característica de cambio de contraseña automático para implementar contraseñas en todos los servicios de una granja de servidores.
    
  
- Configurar los servicios y aplicaciones web de SharePoint, que se ejecutan en servidores de aplicaciones en una granja de servidores de SharePoint, para usar diferentes cuentas de dominio.
    
  
- Asignar cuentas administradas a diversos servicios y aplicaciones web en una granja de servidores.
    
  
- Crear varias cuentas en los servicios de dominio de Active Directory (AD DS) y, a continuación, registrar cada una de estas cuentas en SharePoint.
    
  
También puede registrar cuentas administradas y habilitar SharePoint 2013 para controlar las contraseñas de las cuentas. Se debe notificar a los usuarios acerca de los cambios de contraseña planeados y de las interrupciones de servicio relacionadas, pero las cuentas que se usan en una granja de servidores de SharePoint, las aplicaciones web y varios servicios se pueden restablecer automáticamente e implementarse dentro de la granja de servidores según sea necesario, en función de programaciones de restablecimiento de contraseñas configuradas de manera individual.
  
    
    
Entre las operaciones en cuya ejecución puede usar la clase  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx) están:
  
    
    

- Cambiar contraseña
    
  
- Establecer una programación del cambio de contraseña
    
  
- Propagar el cambio de contraseña
    
  
- Averiguar cuándo se modificó por última vez una contraseña
    
  
- Exigir una longitud mínima de contraseña
    
  
Para obtener más información acerca de la API de cuentas administradas, consulte los siguientes vínculos:
  
    
    

-  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx)
    
  
-  [SPManagedAccount.EventProcessingOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventProcessingOptions.aspx)
    
  
-  [SPManagedAccount.EventType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventType.aspx)
    
  

## Recursos adicionales
<a name="SP15_RoleInheritance_AdditionalResources"> </a>


-  [Autenticación, autorización y seguridad en SharePoint 2013](authentication-authorization-and-security-in-sharepoint-2013.md)
    
  
-  [Autorización, usuarios, grupos y el modelo de objetos de SharePoint 2013](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [Identidad basada en notificaciones en SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Identidad y conceptos basados en notificaciones en SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [Configuración, administración y recursos en SharePoint 2013](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

