---
title: Mensajes de error comunes durante el desarrollo de flujos de trabajo de SharePoint
ms.prod: SHAREPOINT
ms.assetid: e9bf6878-c722-4b1f-b5b5-b302ae0ea4da
---


# Mensajes de error comunes durante el desarrollo de flujos de trabajo de SharePoint
Una lista de mensajes de error comunes que pueden surgir durante el desarrollo de flujos de trabajo de SharePoint y una orientación para solucionar el problema subyacente.
## Errores comunes de flujo de trabajo de SharePoint

Aunque esta lista no cubre todos los posibles errores que pueden surgir durante el desarrollo de flujos de trabajo de SharePoint, sí incluye aquellos que tienen más probabilidad de aparecer.
  
    
    

-  [Se agotó el tiempo de espera para que se completara la solicitud de ejecución de código de espacio aislado dentro del proceso de trabajo.](#bkmk_error01)
    
  
-  [Se sobrepasó el tiempo de espera para que se completara una solicitud dentro del appdomain de espacio aislado.](#bkmk_error02)
    
  
-  [El proceso de trabajo que ejecuta esta solicitud se ha finalizado porque superaba el recurso {0}.](#bkmk_error03)
    
  
-  [No se pudo ejecutar este flujo de trabajo porque se produjo un error en una solución de espacio aislado.](#bkmk_error04)
    
  
-  [No se pudo ejecutar este flujo de trabajo porque se produjo un error en el espacio aislado: No se pudo obtener un proceso del grupo de procesos.](#bkmk_error05)
    
  
-  [No se pudo ejecutar este flujo de trabajo porque se produjo un error en el espacio aislado: El proceso de trabajo del código de espacio aislado se cerró de forma inesperada.](#bkmk_error06)
    
  
-  [No se puede enviar el mensaje de correo electrónico. Compruebe que la configuración de correo electrónico saliente del servidor tiene los valores correctos.](#bkmk_error07)
    
  
-  [El flujo de trabajo no pudo actualizar el elemento, posiblemente porque una o más columnas del elemento requieren otro tipo de información.](#bkmk_error08)
    
  
-  [Error en la operación de flujo de trabajo porque la búsqueda de flujo de trabajo no encontró ningún elemento coincidente.](#bkmk_error09)
    
  
-  [El flujo de trabajo no pudo crear el elemento de lista porque falta el nombre de archivo o no es válido.](#bkmk_error10)
    
  
-  [Error de coerción: No se pueden transformar los datos de búsqueda de entrada en el tipo solicitado.](#bkmk_error11)
    
  
-  [Error en el flujo de trabajo porque la acción requiere que el documento esté desprotegido.](#bkmk_error12)
    
  
-  [Se han encontrado errores al compilar el flujo de trabajo. Los archivos de flujo de trabajo se han guardado pero no se pueden ejecutar. Se ha producido un error inesperado en el servidor al asociar el flujo de trabajo.](#bkmk_error13)
    
  

### Se agotó el tiempo de espera para que se completara la solicitud de ejecución de código de espacio aislado dentro del proceso de trabajo.
<a name="bkmk_error01"> </a>

Mismo problema y misma solución que el siguiente elemento, "Se sobrepasó el tiempo de espera para que se completara una solicitud dentro del appdomain de espacio aislado".
  
    
    

### Se sobrepasó el tiempo de espera para que se completara una solicitud dentro del appdomain de espacio aislado.
<a name="bkmk_error02"> </a>

Estos dos errores se producen por el mismo problema, se sobrepasó el tiempo de espera predeterminado para que se ejecute la acción de flujo de trabajo. El tiempo de espera predeterminado es de 30 segundos.
  
    
    
Puede cambiar el valor del tiempo de espera en instalaciones locales, pero no se puede cambiar en instalaciones de SharePoint Online. Para evitar este error en instalaciones de SharePoint Online, debe modificar el código para que las acciones en el proceso de trabajo o en appdomain estén limitadas a menos de 30 segundos.
  
    
    
Para modificar el tiempo de espera en una instalación local, ejecute el siguiente comando de Windows PowerShell. Tenga en cuenta que el código de ejemplo restablece el tiempo de espera a 60 segundos, pero puede usar otro valor.
  
    
    



```

Add-pssnapin microsoft.sharepoint.powershell
   $userCodeSvc = [Microsoft.SharePoint.Administration.SPUserCodeService]::Local
   #change to 60 second timeout
   $userCodeSvc.WorkerProcessExecutionTimeout = 60 
   $userCodeSvc.Update()
```


### El proceso de trabajo que ejecuta esta solicitud se ha finalizado porque superaba el recurso {0}.
<a name="bkmk_error03"> </a>

En la cadena de error, el valor de  `{0}` es un marcador de posición para el recurso específico cuyo umbral se ha superado. Para solucionar este problema, debe modificar el código para que no supere el umbral del recurso. Los valores de estos recursos están documentados en [Límites de uso de recursos en las soluciones de espacio aislado en SharePoint 2010](http://msdn.microsoft.com/es-es/library/gg615462%28v=office.14%29.aspx).
  
    
    

### No se pudo ejecutar este flujo de trabajo porque se produjo un error en una solución de espacio aislado.
<a name="bkmk_error04"> </a>

El código de flujo de trabajo produjo una excepción no controlada. Para resolver este error, es necesario depurar y revisar el código de espacio aislado.
  
    
    

### No se pudo ejecutar este flujo de trabajo porque se produjo un error en el espacio aislado: No se pudo obtener un proceso del grupo de procesos.
<a name="bkmk_error05"> </a>

Hay un error en la configuración del espacio aislado. Para obtener información sobre cómo configurar una solución de espacio aislado, vea  [Soluciones de espacio aislado en SharePoint](http://msdn.microsoft.com/es-es/library/ee536577%28v=office.14%29.aspx).
  
    
    

### No se pudo ejecutar este flujo de trabajo porque se produjo un error en el espacio aislado: El proceso de trabajo del código de espacio aislado se cerró de forma inesperada.
<a name="bkmk_error06"> </a>

Hay un error en la configuración del espacio aislado. Para obtener información sobre cómo configurar una solución de espacio aislado, vea  [Soluciones de espacio aislado en SharePoint](http://msdn.microsoft.com/es-es/library/ee536577%28v=office.14%29.aspx).
  
    
    

### No se puede enviar el mensaje de correo electrónico. Compruebe que la configuración de correo electrónico saliente del servidor tiene los valores correctos.
<a name="bkmk_error07"> </a>

Existen dos problemas importantes que se deben tener en cuenta a la hora de solucionar problemas de correo electrónico. Tanto en las instalaciones locales como de SharePoint Online, asegúrese de que todas las direcciones en las líneas **Para:** y **Cc:** son direcciones de correo electrónico válidas. En las instalaciones locales, asegúrese de que los valores de configuración del correo electrónico en el servidor están configurados correctamente.
  
    
    
Revise lo siguiente para asegurarse de que ha configurado correctamente los correos electrónicos entrantes y salientes.
  
    
    

-  [Guía para la implementación de Microsoft SharePoint 2013](http://download.microsoft.com/download/1/F/6/1F6D3BE4-1174-4320-A1D1-C0E2681CCCF3/Deployment-guide-for-SharePoint-2013.pdf)
    
  
-  [Cómo configurar los correos electrónicos entrantes y salientes en SharePoint Server](http://blogs.msdn.com/b/pareshg/archive/2010/04/23/how-to-configure-incoming-and-outgoing-emails-in-sharepoint-server-2010.aspx)
    
  

### El flujo de trabajo no pudo actualizar el elemento, posiblemente porque una o más columnas del elemento requieren otro tipo de información.
<a name="bkmk_error08"> </a>

Este error normalmente es resultado de una de las dos siguientes situaciones:
  
    
    

- Se ha quitado o cambiado uno de los campos de la lista, pero no se ha actualizado el flujo de trabajo para que tenga en cuenta el cambio y, por tanto, está intentando establecer un valor para el campo anterior. Debe comprobar todas las acciones **Actualizar elemento de lista** del flujo de trabajo y asegurarse de que establecen los valores apropiados para los campos y que esos campos existen en la lista.
    
  
- Hay un error de tipo de datos en el que el flujo de trabajo intenta establecer un valor en un campo del elemento de lista con el tipo de datos incorrecto. Debe confirmar que la operación **Devolver campo como** en su búsqueda es del tipo de datos correcto.
    
  

### Error en la operación de flujo de trabajo porque la búsqueda de flujo de trabajo no encontró ningún elemento coincidente.
<a name="bkmk_error09"> </a>

Esto indica que hay un error en la lógica del flujo de trabajo. Compruebe que se selecciona la lista y el campo correctos en la búsqueda.
  
    
    

### El flujo de trabajo no pudo crear el elemento de lista porque falta el nombre de archivo o no es válido.
<a name="bkmk_error10"> </a>

Esto indica que hay un error en la lógica del flujo de trabajo. Asegúrese de que el nombre de archivo especificado en el campo **Ruta de acceso y nombre** es un nombre de archivo válido. Las razones más comunes por las que el nombre de un archivo no es válido son una extensión de archivo que falta o es incorrecta, o una cadena de un archivo/ruta de acceso demasiado larga y que supera el número de caracteres permitido.
  
    
    

### Error de coerción: No se pueden transformar los datos de búsqueda de entrada en el tipo solicitado.
<a name="bkmk_error11"> </a>

Se produjo un error en la operación al convertir valores entre tipos de datos incompatibles (por ejemplo, al convertir una cadena aleatoria en un valor de fecha y hora). Debe comprobar la configuración de **Devolver campo como** en la búsqueda para asegurarse de que es un tipo de dato válido para los datos esperados.
  
    
    

### Error en el flujo de trabajo porque la acción requiere que el documento esté desprotegido.
<a name="bkmk_error12"> </a>

Debe desproteger el elemento mediante la acción **Desproteger elemento** antes de utilizar la acción **Actualizar elemento**.
  
    
    

### Se han encontrado errores al compilar el flujo de trabajo. Los archivos de flujo de trabajo se han guardado pero no se pueden ejecutar. Se ha producido un error inesperado en el servidor al asociar el flujo de trabajo.
<a name="bkmk_error13"> </a>

Para obtener más información sobre este error, vea el  [artículo con id. 2557533 de Microsoft Knowledge Base](http://support.microsoft.com/kb/2557533) ( `http://support.microsoft.com/kb/2557533`).
  
    
    

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Procedimientos recomendados de desarrollo de flujo de trabajo de SharePoint](sharepoint-workflow-development-best-practices.md)
    
  
-  [Desarrollar de flujos de trabajo de SharePoint 2013 mediante Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

