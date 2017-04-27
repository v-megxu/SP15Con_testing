---
title: Procedimiento para recuperar propiedades de perfil de usuario mediante el modelo de objetos de JavaScript en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c6e1ca38-134f-428a-8d21-b8b2615b161b
---


# Procedimiento para recuperar propiedades de perfil de usuario mediante el modelo de objetos de JavaScript en SharePoint 2013
Obtenga información para la recuperación de propiedades de usuario y propiedades de perfil de usuario mediante programación con el modelo de objetos de JavaScript de SharePoint 2013.
## Qué son las propiedades de usuario y las propiedades de perfil de usuario de SharePoint 2013
<a name="bkmk_WhatIs"> </a>

Las propiedades de usuario y las propiedades de perfil de usuario proporcionan información sobre los usuarios de SharePoint, como nombre para mostrar, correo electrónico, tratamiento y otra información empresarial y personal. En las API de cliente, el acceso a estas propiedades se realiza desde el objeto  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) y su propiedad [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx). La propiedad  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) contiene todas las propiedades de perfil de usuario, pero el objeto [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) contiene las propiedades de uso común (como [accountName](http://msdn.microsoft.com/library/ad1551bf-dad8-d54e-880a-8a4388fad44e%28Office.15%29.aspx),  [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx) y [email](http://msdn.microsoft.com/library/74302f73-aaf6-920b-0605-812b0dbf4568%28Office.15%29.aspx)) cuyo acceso es más sencillo.
  
    
    
El objeto  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) incluye los siguientes métodos que se pueden usar para recuperar propiedades de usuario y propiedades de perfil de usuario mediante el modelo de objetos de JavaScript:
  
    
    

- El método  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) y el método [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) devuelven un objeto [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx).
    
  
- El método  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) y el método [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) devuelven los valores de las propiedades de perfil de usuario que especifique.
    
  
Las propiedades de perfil de usuario de las API cliente son de solo lectura (excepto la imagen del perfil, que se puede cambiar mediante el método  [PeopleManager.setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx)). Si quiere cambiar otras propiedades de perfil de usuario, tiene que usar el modelo de objetos de servidor. Para obtener más información sobre el trabajo con perfiles de usuario, consulte  [Trabajar con perfiles de usuario en SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md).
  
    
    

> **NOTA**
> El objeto de cliente  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) no contiene todas las propiedades de usuario que tiene la versión de servidor. No obstante, la versión de cliente proporciona los métodos para crear un sitio personal para el usuario actual. Para recuperarlo, use el método [ProfileLoader.getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx). 
  
    
    


## Requisitos previos para configurar el entorno de desarrollo a fin de recuperar propiedades de usuario mediante el modelo de objetos de JavaScript de SharePoint 2013
<a name="bk_Prereqs"> </a>

Para crear una página de aplicación que use el modelo de objetos de JavaScript para recuperar propiedades de usuario, necesita:
  
    
    

- SharePoint Server 2013 con perfiles creados para el usuario actual y un usuario de destino
    
  
- Visual Studio 2012
    
  
- Office Developer Tools para Visual Studio 2013
    
  
- Permisos de conexión **Control total** para obtener acceso a la aplicación del servicio Perfil de usuario del usuario actual
    
  

## Crear la página de aplicación en Visual Studio 2012
<a name="bk_CreateAppPage"> </a>


1. En el servidor con SharePoint Server 2013, abra Visual Studio y elija **Archivo**, **Nuevo**, **Proyecto**.
    
  
2. En el cuadro de diálogo **Nuevo proyecto**, seleccione **.NET Framework 4.5** en la lista desplegable situada en la parte superior del cuadro de diálogo.
    
  
3. En la lista **Plantillas**, expanda **Office/SharePoint**, elija la categoría **Soluciones de SharePoint** y luego la plantilla **Proyecto de SharePoint 2013**.
    
  
4. Ponga al proyecto el nombre UserProfilesJSOM y luego elija el botón **Aceptar**.
    
  
5. En el cuadro de diálogo **Asistente para la personalización de SharePoint**, escriba la dirección URL del sitio de SharePoint de destino, elija **Implementar como solución de granja de servidores** y luego el botón **Finalizar**.
    
  
6. En el **Explorador de soluciones**, abra el menú contextual del proyecto UserProfilesJSOM y agregue una carpeta asignada "Layouts" de SharePoint.
    
  
7. En la carpeta **Layouts**, abra el menú contextual de la carpeta UserProfilesJSOM y agregue una nueva página de aplicación de SharePoint llamadaUserProfiles.aspx.
    
    > **NOTA**
      > En los ejemplos de código de este artículo se define el código personalizado del marcado de página pero no se usa el archivo de clases tras el código que crea Visual Studio para la página. 
8. Abra el menú contextual de la página UserProfiles.aspx y elija **Establecer como elemento de inicio**.
    
  
9. En el marcado de la página UserProfiles.aspx, pegue el siguiente código dentro de las etiquetas "Main" **asp:Content**. Este código agrega un control **span** que muestra los resultados de la consulta, los controles **SharePoint:ScriptLink** que hacen referencia a los archivos de la biblioteca de clases de JavaScript de SharePoint y las etiquetas **script** que van a contener la lógica personalizada.
    
  ```HTML
  
<span id="results"></span><br />
<SharePoint:ScriptLink ID="ScriptLink1" name="SP.js" runat="server"
    ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:ScriptLink ID="ScriptLink2" name="SP.UserProfiles.js" runat="server"
    ondemand="false" localizable="false" loadafterui="true" />
<script type="text/javascript">

    // Replace this comment with the code for your scenario.

</script>

  ```

10. Para agregar lógica para recuperar propiedades de perfil de usuario, sustituya el comentario entre las etiquetas **script** por el ejemplo de código de uno de los siguientes escenarios:
    
  -  [Recuperar propiedades de perfil de usuario del objeto PersonProperties y su propiedad userProfileProperties](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_examplePersonPropsObj)
    
  
  -  [Recuperar un conjunto de propiedades de perfil de usuario mediante el método getUserProfilePropertiesFor](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_exampleGetUPMethod)
    
  
11. Para probar la página de aplicación, en la barra de menús, elija **Depurar**, **Iniciar depuración**. Si se le pide que modifique el archivo web.config, elija el botón **Aceptar**.
    
  

## Ejemplo de código: recuperación de propiedades de perfil de usuario del objeto PersonProperties y su propiedad userProfileProperties en el modelo de objetos de JavaScript de SharePoint 2013.
<a name="bk_examplePersonPropsObj"> </a>

En el siguiente ejemplo de código se muestra cómo obtener propiedades de perfil de usuario de un usuario de destino mediante consulta al objeto  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) y su propiedad [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx). Muestra cómo:
  
    
    

- Obtener el objeto  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) que representa al usuario de destino mediante el método [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx). (Para obtener el objeto  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) del usuario actual, use el método [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx)).
    
  
- Obtener una propiedad directamente del objeto  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx). En este ejemplo se obtiene la propiedad  [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx).
    
  
- Obtener una propiedad de la propiedad  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) del objeto [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx). En este ejemplo se obtiene la propiedad **Department**.
    
  

> **NOTA**
> Pegue el siguiente código entre las etiquetas **script** que agregó al archivo UserProfiles.aspx en el procedimiento [Crear la página de aplicación](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage). Sustituya el valor del marcador de posición  `domainName\\\\userName` antes de ejecutar el código. (En este ejemplo de código no se usa el archivo de clases tras el código).
  
    
    


```

var personProperties;

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(getUserProperties, 'SP.UserProfiles.js');

function getUserProperties() {

    // Replace the placeholder value with the target user's credentials.
    var targetUser = "domainName\\\\userName";

    // Get the current client context and PeopleManager instance.
    var clientContext = new SP.ClientContext.get_current();
    var peopleManager = new SP.UserProfiles.PeopleManager(clientContext);

    // Get user properties for the target user.
    // To get the PersonProperties object for the current user, use the
    // getMyProperties method.
    personProperties = peopleManager.getPropertiesFor(targetUser);

    // Load the PersonProperties object and send the request.
    clientContext.load(personProperties);
    clientContext.executeQueryAsync(onRequestSuccess, onRequestFail);
}

// This function runs if the executeQueryAsync call succeeds.
function onRequestSuccess() {

    // Get a property directly from the PersonProperties object.
    var messageText = " \\"DisplayName\\" property is "
        + personProperties.get_displayName();

    // Get a property from the UserProfileProperties property.
    messageText += "<br />\\"Department\\" property is "
        + personProperties.get_userProfileProperties()['Department'];
    $get("results").innerHTML = messageText;
}

// This function runs if the executeQueryAsync call fails.
function onRequestFail(sender, args) {
    $get("results").innerHTML = "Error: " + args.get_message();
}
```


## Ejemplo de código: recuperación de un conjunto de propiedades de perfil de usuario mediante el método getUserProfilePropertiesFor del modelo de objetos de JavaScript de SharePoint 2013
<a name="bk_exampleGetUPMethod"> </a>

En el siguiente ejemplo de código se recuperan los valores de un conjunto especificado de propiedades de perfil de usuario de un usuario de destino mediante el método  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx). Muestra cómo:
  
    
    

- Crear un objeto  [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx) que especifica el usuario de destino y las propiedades de perfil de usuario que se van a recuperar. En este ejemplo se obtienen las propiedades **PreferredName** y **Department**.
    
  
- Obtener los valores de las propiedades especificadas mediante el método  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) y el paso del objeto [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx). (Para recuperar el valor de una única propiedad de perfil de usuario, use el método  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx)).
    
  
- Obtener los valores de la matriz devuelta de valores de propiedad.
    
  

> **NOTA**
> Pegue el siguiente código entre las etiquetas **script** que agregó al archivo UserProfiles.aspx en el procedimiento [Crear la página de aplicación](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage). Sustituya el valor del marcador de posición  `domainName\\\\userName` antes de ejecutar el código. (En este ejemplo de código no se usa el archivo de clases detrás del código).
  
    
    


```

var userProfileProperties;

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(getUserProperties, 'SP.UserProfiles.js');

function getUserProperties() {

    // Replace the placeholder value with the target user's credentials.
    var targetUser = "domainName\\\\userName";

    // Get the current client context and PeopleManager instance.
    var clientContext = new SP.ClientContext.get_current();
    var peopleManager = new SP.UserProfiles.PeopleManager(clientContext);

    // Specify the properties to retrieve and target user for the 
    // UserProfilePropertiesForUser object.
    var profilePropertyNames = ["PreferredName", "Department"];
    var userProfilePropertiesForUser = 
        new SP.UserProfiles.UserProfilePropertiesForUser(
            clientContext,
            targetUser,
            profilePropertyNames);

    // Get user profile properties for the target user.
    // To get the value for only one user profile property, use the
    // getUserProfilePropertyFor method.
    userProfileProperties = peopleManager.getUserProfilePropertiesFor(
        userProfilePropertiesForUser);

    // Load the UserProfilePropertiesForUser object and send the request.
    clientContext.load(userProfilePropertiesForUser);
    clientContext.executeQueryAsync(onRequestSuccess, onRequestFail);
}

// This function runs if the executeQueryAsync call succeeds.
function onRequestSuccess() {
    var messageText = "\\"PreferredName\\" property is " 
        + userProfileProperties[0];
    messageText += "<br />\\"Department\\" property is " 
        + userProfileProperties[1];
    $get("results").innerHTML = messageText;
}

// This function runs if the executeQueryAsync call fails.
function onRequestFail(sender, args) {
    $get("results").innerHTML = "Error: " + args.get_message();
}
```


## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Trabajar con perfiles de usuario en SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [Recuperar propiedades de perfil de usuario usando el modelo de objetos de cliente .NET en SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Cómo trabajar con perfiles de usuario y perfiles de organización con el modelo de objetos del servidor en SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [SP.UserProfiles espacio de nombres (sp.userprofiles)](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx)
    
  

