---
title: Formas de Visio en SharePoint Designer 2013 Guía de referencia rápida (plataforma de flujo de trabajo de SharePoint 2010)
ms.prod: SHAREPOINT
ms.assetid: 51bc37fd-37de-4ad0-a75a-bdf7333bc80c
---



# Formas de Visio en SharePoint Designer 2013: Guía de referencia rápida (plataforma de flujo de trabajo de SharePoint 2010)
Puede crear un flujo de trabajo en Microsoft Visio Professional 2013 y luego exportarlo a Microsoft SharePoint Designer 2013. Esta guía identifica las formas de Visio que se usan para crear un flujo de trabajo.Use este artículo de referencia solo si está trabajando en SharePoint Designer 2013, pero desea seguir usando la plataforma de flujo de trabajo de SharePoint 2010.Las formas de la plataforma de flujo de trabajo de SharePoint 2010 se presentan en tres galerías de símbolos: **Acciones de flujo de trabajo de SharePoint 2010**, **Condiciones de flujo de trabajo de SharePoint 2010** y **Terminadores de flujo de trabajo de SharePoint 2010:**.
## Acciones de flujo de trabajo
<a name="section1"> </a>

Las acciones de flujo de trabajo son operaciones específicas que realiza dicho flujo de trabajo. Cada flujo de trabajo debe contener al menos una acción.
  
    
    
Las acciones de esta lista se organizan en categorías basándose en su área de la aplicación en un flujo de trabajo. Por ejemplo, las acciones que afectan el comportamiento de un elemento de lista se agrupan bajo **Acciones de lista** y las acciones relacionadas con conjuntos de documentos se agrupan bajo **Acciones del conjunto de documentos**. Las categorías de acciones son:
  
    
    

-  [Acciones principales](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1a) Son las acciones más utilizadas en un flujo de trabajo.
    
  
-  [Acciones del conjunto de documentos](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1e) Por lo general, estas acciones se usan en flujos de trabajo asociados a una biblioteca de documentos o al tipo de contenido del documento.
    
  
-  [Acciones de lista](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1b) Estas acciones realizan operaciones en los elementos de lista.
    
  
-  [Acciones relacionales](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1d) La única acción de esta categoría busca un administrador de usuarios y almacena esa información en una variable.
    
  
-  [Acciones de tareas](visio-shapes-in-sharepoint-designer-2013-a-quick-reference-guide-sharepoint-2010.md#section1c) Estas acciones están asociadas con la aprobación, los comentarios y las operaciones de formularios.
    
  

> **IMPORTANTE**
> La mayoría de formas de acciones que puede insertar en un flujo de trabajo de SharePoint en Visio requieren configuración adicional cuando el flujo de trabajo se importa en SharePoint Designer. En Visio, recuerde usar la característica de comentarios de cada forma de acción para especificar la configuración o la configuración de la acción. 
  
    
    


### Acciones principales
<a name="section1a"> </a>

Son las acciones utilizadas con más frecuencia y pueden usarse en cualquier tipo de flujo de trabajo o paso.
  
    
    

****


|**Forma de acción de Visio**|**Acción correspondiente en SharePoint Designer**|**Descripción de la acción**|
|:-----|:-----|:-----|
|![Agregar un comentario](images/spd15-addcomment-visio.JPG)|Esta acción de Visio es igual a la acción **Agregar un comentario** en SharePoint Designer 2013 y se muestra como: <br/>![Agregar comentario](images/spd15-addcomment-txt.JPG)    > **NOTA**> Los comentarios permanecen visibles cuando el flujo de trabajo se exporta a Visio.           |**Agregar un comentario** <br/> Use esta acción para dejar comentarios informativos en el diseñador de flujo de trabajo como referencia. Esto es especialmente útil cuando hay otros usuarios que colaboran en la creación del flujo de trabajo. Por ejemplo, si una variable del flujo de trabajo actual no tiene un nombre descriptivo, use esta acción para agregar un comentario con el fin de indicar qué hace la variable del flujo de trabajo.  <br/> |
|![Agregar hora a la fecha](images/spd15-addtimetodate-visio.JPG)|Esta acción de Visio es igual a la acción **Agregar hora a la fecha** en SharePoint Designer 2013 y se muestra como: <br/>![Agregar hora a la fecha](images/spd15-addtimetodate-txt.JPG)|**Agregar hora a la fecha** <br/> Use esta acción para agregar una hora concreta en minutos, horas, días, meses o años a una fecha y almacenar el valor de resultado como una variable. La fecha puede ser una fecha actual, una fecha específica o una búsqueda.  <br/> |
|![Realizar el cálculo](images/spd15-docalc-visio.JPG)|Esta acción de Visio es igual a la acción **Realizar cálculo** en SharePoint Designer 2013 y se muestra como: <br/>![Realizar el cálculo](images/spd15-docalc-txt.JPG)|**Realizar cálculo** <br/> Use esta acción para realizar un cálculo, como agregar, restar, multiplicar o dividir dos valores y almacenar el valor de resultado en una variable.  <br/> |
|![Registrar en lista de historial](images/spd15-LogHist-visio.JPG)|Esta acción de Visio es igual que la acción **Registrar en lista de historial** en SharePoint Designer 2013 y se muestra como: <br/>![Registrar en lista de historial](images/spd15-LogHist-txt.JPG)|**Registrar en lista de historial** <br/> Use esta acción para registrar un mensaje sobre el flujo de trabajo en su lista de historial. Un mensaje puede ser un resumen de un evento de flujo de trabajo o nada significativo sobre el flujo de trabajo. La lista de historial de flujo de trabajo puede ser útil para solucionar problemas con el flujo de trabajo.  <br/> |
|![Detener durante](images/spd15-PauseDuration-visio.JPG)|Esta acción de Visio es igual que la acción **Detener durante** en SharePoint Designer 2013 y se muestra como: <br/>![Detener durante](images/spd15-PauseDuration-txt.JPG)|**Detener durante** <br/> Use esta acción para detener el flujo de trabajo durante un tiempo concreto en días, horas o minutos.  <br/> > **NOTA**> El tiempo de retraso determina el intervalo de trabajos del temporizador, que tiene un valor predeterminado de cinco minutos.           |
|![Detener hasta fecha](images/spd15-PauseDate-visio.JPG)|Esta acción de Visio es igual que la acción **Detener hasta fecha** en SharePoint Designer 2013 y se muestra como: <br/>![Detener hasta fecha](images/spd15-PauseDate-txt.JPG)|**Detener hasta fecha** <br/> Use esta acción para detener el flujo de trabajo hasta una fecha determinada. Puede agregar una fecha actual, una fecha específica o una búsqueda.  <br/> |
|![Configurar parte de la hora del campo Fecha y hora](images/spd15-SetTimePortion-visio.JPG)|Esta acción de Visio es igual que la acción ** Establecer la parte de hora del campo Fecha y hora** en SharePoint Designer 2013 y se muestra como: <br/>![Configurar parte de la hora del campo Fecha y hora](images/spd15-SetTimePortion-txt.JPG)|**Establecer la parte de hora del campo Fecha y hora** <br/> Use esta acción para crear una marca de tiempo y almacenar el valor de resultado en una variable. Puede establecer el tiempo en horas y minutos y agregar una fecha actual, la fecha específica o una búsqueda.  <br/> |
|![Establecer estado del flujo de trabajo](images/spd15-SetWFStatus-visio.JPG)| Esta acción de Visio es igual que la acción **Establecer estado de flujo de trabajo** en SharePoint Designer 2013 y se muestra como: <br/>![Establecer estado del flujo de trabajo](images/spd15-SetWFStatus-txt.JPG) No se puede cambiar el nombre ni eliminar un valor de estado una vez que se ha creado. Sin embargo, no es necesario usarlo. <br/>  Un estado personalizado es aplicable al flujo de trabajo actual y no se puede usar en otro flujo de trabajo <br/>  Un flujo de trabajo no puede usar los valores de estado personalizados que defina en la acción si la acción se utiliza dentro de un paso de suplantación. <br/> |**Establecer estado de flujo de trabajo** <br/> Use esta acción para establecer el estado del flujo de trabajo. Las opciones predeterminadas son **Cancelado**, **Aprobado** y **Rechazado**.  <br/> Puede escribir un nuevo valor de estado en la lista desplegable de la acción. Una vez que escriba un valor de estado, la entrada se agrega automáticamente a la lista desplegable.  <br/> Si la acción **Establecer estado de flujo de trabajo** es el último paso del flujo de trabajo donde también se ha utilizado un valor personalizado, puede ver su valor predeterminado en la columna **Estado** de la lista al finalizar o pausar el flujo de trabajo. <br/> |
|![Establecer variable de flujo de trabajo](images/spd15-SetWFVar-visio.JPG)|Esta acción de Visio es igual que la acción **Establecer variable de flujo de trabajo** en SharePoint Designer 2013 y se muestra como: <br/>![Establecer variable de flujo de trabajo](images/spd15-SetWFVar-txt.JPG)|**Establecer variable de flujo de trabajo** <br/> Use esta acción para establecer una variable de flujo de trabajo en un valor. Utilice esta acción cuando quiera que el flujo de trabajo asigne datos a una variable.  <br/> |
|![Detener flujo de trabajo](images/spd15-StopWF-visio.JPG)|Esta acción de Visio es igual que la acción **Eliminar elemento** en SharePoint Designer 2013 y se muestra como: <br/>![Detener flujo de trabajo](images/spd15-StopWF-txt.JPG)|**Detener flujo de trabajo** <br/> Use esta acción para detener la instancia actual del flujo de trabajo y registrar un mensaje en la lista **Historial del flujo de trabajo**. El mensaje que se especifique en la acción aparecerá en la columna **Descripción** del historial de flujo de trabajo tras la finalización del flujo de trabajo. <br/> |
   

### Acciones de lista
<a name="section1b"> </a>

Estas acciones se usan en los elementos de lista.
  
    
    

****


|**FORMA DE ACCIÓN DE VISIO**|**ACCIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA ACCIÓN**|
|:-----|:-----|:-----|
|![Agregar permisos de elementos de lista](images/spd15-AddListItemPerms-visio.JPG)|Esta acción de Visio es igual que la acción **Agregar permisos de elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Agregar permisos a elemento](images/spd15-AddListItemPerms-txt.JPG)    > **NOTA**> Esta acción solo está disponible dentro de un paso de suplantación.           |**Agregar permisos de elemento de lista** <br/> Esta acción concede niveles de permisos específicos para un elemento a usuarios específicos.  <br/> |
|![Proteger elemento](images/spd15-CheckInItem-visio.JPG)|Esta acción de Visio es igual que la acción **Proteger elemento** en SharePoint Designer 2013 y se muestra como: <br/>![Proteger elemento](images/spd15-CheckInItem-txt.JPG)|**Proteger elemento** <br/> Esta acción protege un elemento desprotegido.  <br/> > **NOTA**> Solo puede proteger elementos de una biblioteca de documentos.           |
|![Desproteger elemento](images/spd15-CheckOutItem-visio.JPG)|Esta acción de Visio es igual que la acción **Desproteger elemento** en SharePoint Designer 2013 y se muestra como: <br/>![Desproteger elemento](images/spd15-CheckOutItem-txt.JPG)|**Desproteger elemento** <br/> Use esta acción para desproteger un elemento. El flujo de trabajo comprueba si el elemento está protegido antes de desproteger un documento.  <br/> > **NOTA**> Solo puede desproteger elementos de una biblioteca en su sitio.           |
|![Copiar elemento de lista](images/spd15-CopyListItem-visio.JPG)|Esta acción de Visio es igual que la acción **Copiar elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Copiar elemento de lista](images/spd15-CopyListItem-txt.JPG)|**Copiar elemento de lista** <br/> Use esta acción para copiar un elemento de lista en otra lista. Si hay un documento en el elemento de lista, el flujo de trabajo también copia el documento en la lista de destino.  <br/> > **IMPORTANTE**> Debe tener al menos una columna similar en las listas de origen y de destino.           |
|![Crear elemento de lista](images/spd15-CreateListItem-visio.JPG)|Esta acción de Visio es igual que la acción **Crear elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Crear elemento de lista](images/spd15-CreateListItem-txt.JPG)|**Crear elemento de lista** <br/> Use esta acción para crear un nuevo elemento de lista en la lista que especifique. Puede suministrar los campos y valores del nuevo elemento.  <br/> Puede usar esta acción siempre que desee un nuevo elemento que se creará con información específica.  <br/> > **NOTA**> La variable de resultado es el identificador del elemento creado en la lista.           |
|![Eliminar elemento](images/spd15-DeleteItem-visio.JPG)|Esta acción de Visio es igual que la acción **Eliminar elemento** en SharePoint Designer 2013 y se muestra como: <br/>![Eliminar elemento](images/spd15-DeleteItem-txt.JPG)|**Eliminar elemento** <br/> Use esta acción para eliminar un elemento.  <br/> |
|![Descartar desprotección de elemento](images/spd15-DiscardItem-visio.JPG)|Esta acción de Visio es igual que la acción **Descartar desprotección de elemento** en SharePoint Designer 2013 y se muestra como: <br/>![Descartar desprotección de elemento](images/spd15-DiscardItem-txt.JPG)|**Descartar desprotección de elemento** <br/> Use esta acción si un elemento está desprotegido, se han realizado cambios en él y desea descartar los cambios y comprobar el elemento de nuevo.  <br/> |
|![Heredar permisos de elementos de lista](images/spd15-InheritListItemPerms-visio.JPG)|Esta acción de Visio es igual que la acción **Heredar permisos principales de elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Heredar permisos de elementos de lista](images/spd15-InheritListItemPerms-txt.JPG)    > **NOTA**> Esta acción solo está disponible en un paso de suplantación.           |**Heredar permisos de elemento de lista** <br/> Si el elemento tiene permisos únicos, puede usar esta acción para hacer que el elemento herede los permisos principales de la lista.  <br/> |
|![Quitar permisos de elementos de lista](images/spd15-RmListItemPerms-visio.JPG)|Esta acción de Visio es igual que la acción **Quitar permisos de elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Quitar permisos de elementos de lista](images/spd15-RmListItemPerms-txt.JPG)    > **NOTA**> Esta acción solo está disponible en un paso de suplantación.           |**Quitar permisos de elemento de lista** <br/> Esta acción quita los permisos de un elemento para usuarios específicos.  <br/> |
|![Reemplazar permisos de elemento de lista](images/spd15-ReplaceListItemPerms-visio.JPG)|Esta acción de Visio es igual que la acción **Reemplazar permisos de elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Reemplazar permisos de elemento de lista](images/spd15-ReplaceListItemPerms-txt.JPG)    > **NOTA**> Esta acción solo está disponible en un paso de suplantación.           |**Reemplazar permisos de elemento de lista** <br/> Reemplaza los permisos actuales de un artículo con los nuevos permisos que especifique en la acción.  <br/> |
|![Establecer estado de aprobación del contenido](images/spd15-SetContentApprovalStatus-visio.JPG)|Esta acción de Visio es igual que la acción **Establecer estado de aprobación de contenido** en SharePoint Designer 2013 y se muestra como: <br/>![Establecer estado de aprobación del contenido](images/spd15-SetContentApprovalStatus-txt.JPG)    > **NOTA**> Aprobación de contenido debe estar habilitada en la lista para usar esta acción.           
|**Establecer estado de aprobación de contenido** <br/> Si se ha habilitado aprobación de contenido en la lista, use esta acción para establecer el campo de estado de aprobación de contenido en un valor Aprobado, Rechazado o Pendiente. Puede escribir un estado personalizado en la acción.  <br/> > **NOTA**> La acción **Establecer estado de aprobación de contenido** funciona en el elemento actual que actúa el flujo de trabajo, por lo tanto, la acción no está disponible en un flujo de trabajo de sitio.          |
|![Establecer campo en elemento actual](images/spd15-SetFieldCurrItem-visio.JPG)|Esta acción de Visio es igual que la acción **Establecer campo en elemento actual** en SharePoint Designer 2013 y se muestra como: <br/>![Establecer campo en elemento actual](images/spd15-SetFieldCurrItem-txt.JPG)|**Establecer campo en elemento actual** <br/> Use la acción para establecer un campo en el elemento actual para un valor.  <br/> > **NOTA**> Si desea pausar el flujo de trabajo hasta que cambie el valor del campo, en su lugar use la acción **Esperar cambio de campo en elemento actual**.           La acción **Establecer campo en elemento actual** no debe utilizarse en un flujo de trabajo de sitio. <br/> |
|![Actualizar elemento de lista](images/spd15-UpdateListItem-visio.JPG)|Esta acción de Visio es igual que la acción **Actualizar elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Actualizar elemento de lista](images/spd15-UpdateListItem-txt.JPG)|**Actualizar elemento de lista** <br/> Use esta acción para actualizar un elemento de lista. Puede especificar los campos y los nuevos valores de esos campos.  <br/> |
|![Esperar cambio de campo en elemento actual](images/spd15-Wait4FieldChange-visio.JPG)|Esta acción de Visio es igual que la acción **Esperar cambio de campo en elemento actual** en SharePoint Designer 2013 y se muestra como: <br/>![Esperar cambio de campo](images/spd15-Wait4FieldChange-txt.JPG)|**Esperar cambio de campo en elemento actual** <br/> Esta acción detiene el flujo de trabajo hasta que el campo en elemento actual ha cambiado a un nuevo valor.  <br/> > **NOTA**> Si desea que el flujo de trabajo cambie el valor del campo, en lugar de que el flujo de trabajo espere a que cambie el campo, utilice la acción **Establecer campo en elemento actual** en su lugar.          |
   

### Acciones de tareas
<a name="section1c"> </a>

Las acciones de esta categoría pertenecen a los elementos de tareas. Estas acciones se aplican únicamente a los sitios de SharePoint que ejecutan SharePoint Server 2013.
  
    
    

****


|**FORMA DE ACCIÓN DE VISIO**|**ACCIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA ACCIÓN**|
|:-----|:-----|:-----|
|![Asignar un formulario a un grupo](images/spd15-AssignForm2Grp-visio.JPG)|Esta acción de Visio es igual que la acción **Asignar un formulario a un grupo** en SharePoint Designer 2013 y se muestra como: <br/>![Asignar un formulario a un grupo](images/spd15-AssignForm2Grp-txt.JPG)|**Asignar un formulario a un grupo** <br/> Use esta acción para crear un formulario de tareas personalizado con campos personalizados.  <br/> Puede usar esta acción para asignar una tarea a uno o más participantes o grupos donde se les solicita realizar sus tareas. Los participantes proporcionan sus respuestas en los campos formulario de tareas personalizados y, cuando se realicen con la tarea, haga clic en **Realizar tarea** en el formulario. <br/> |
|![Asignar un elemento de tarea](images/spd15-AssignToDoItem-visio.JPG)|Esta acción de Visio es igual que la acción **Asignar un formulario a un grupo** en SharePoint Designer 2013 y se muestra como: <br/>![Asignar un elemento de tarea](images/spd15-AssignToDoItem-txt.JPG)|**Asignar un elemento de tarea** <br/> Use esta acción para asignar una tarea a cada uno de los participantes, pidiéndoles realizar sus tareas y luego, cuando hayan terminado, haga clic en botón **Realizar tarea** en el formulario de tareas. <br/> |
|![Recopilar datos de un usuario](images/spd15-CollectDataFrUser-visio.JPG)|Esta acción de Visio es igual que la acción **Recopilar datos de un usuario** en SharePoint Designer 2013 y se muestra como: <br/>![Recopilar datos de un usuario](images/spd15-CollectDataFrUser-txt.JPG)|**Recopilar datos de un usuario** <br/> Use esta acción para asignar una tarea al participante, pidiéndole que proporcione la información necesaria en un formulario de tareas personalizado y luego haga clic en el botón **Realizar tarea** en el formulario de tareas. <br/> Esta acción tiene una cláusula de salida, es decir, el flujo de trabajo almacena la información devuelta por la acción en una variable correspondiente. El identificador del elemento de tarea completada de la acción del elemento de lista se almacena en la variable collect.  <br/> |
|![Iniciar proceso de aprobación](images/spd15-StartApprovalProc-visio.JPG)|Esta acción de Visio es igual que la acción **Iniciar proceso de aprobación** en SharePoint Designer 2013 y se muestra como: <br/>![Iniciar el proceso de aprobación del conjunto de documentos](images/spd15-StartApprovalProc-txt.JPG)|**Iniciar proceso de aprobación** <br/> Use esta acción para enrutar un documento para su aprobación. Los aprobadores pueden aprobar o rechazar el documento, reasignar la tarea de aprobación o solicitar cambios.  <br/> Puede asignar tareas a participantes internos y externos de la acción. Un participante externo puede ser un empleado de la organización que no es un usuario de la colección de sitios o cualquiera de fuera de la organización.  <br/> |
|![Iniciar proceso de comentarios](images/spd15-StartFeedback-visio.JPG)|Esta acción de Visio es igual que la acción **Iniciar proceso de comentarios** en SharePoint Designer 2013 y se muestra como: <br/>![Iniciar proceso de comentarios](images/spd15-StartFeedback-txt.JPG)|**Iniciar proceso de comentarios** <br/> Use esta acción para asignar elementos de tarea para comentarios a los usuarios en un orden específico, serie o en paralelo. El valor predeterminado es paralelo. Los usuarios o los participantes de la tarea también pueden reasignar una tarea a otros usuarios. Cuando termine, los usuarios pueden hacer clic en el botón **Enviar comentarios** para indicar la finalización de la tarea. <br/> Puede asignar tareas a participantes internos y externos de la acción. Un participante externo puede ser un empleado de la organización que no es un usuario de la colección de sitios o cualquiera de fuera de la organización.  <br/> |
|![Iniciar proceso de tarea personalizado](images/spd15-StartCustomTask-visio.JPG)|Esta acción de Visio es igual que la acción **Iniciar proceso de tarea personalizado** en SharePoint Designer 2013 y se muestra como: <br/>![Iniciar proceso de tarea personalizado](images/spd15-StartCustomTask-txt.JPG)|**Iniciar proceso de tarea personalizado** <br/> La acción **Iniciar proceso de tarea personalizado** es una plantilla de proceso de aprobación que puede usar si otras acciones de aprobación no satisfacen sus necesidades. <br/> |
   

### Acciones relacionales
<a name="section1d"> </a>

La acción de esta categoría busca el administrador de un usuario y almacena dicha información en una variable. Esta acción solo se aplica a los sitios de SharePoint ejecuta SharePoint Server 2013.
  
    
    

****


|**FORMA DE ACCIÓN DE VISIO**|**ACCIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA ACCIÓN**|
|:-----|:-----|:-----|
|![Buscar el administrador de un usuario](images/spd15-LookupMgr4User-visio.JPG)|Esta acción de Visio es igual que la acción **Buscar administrador de un usuario** en SharePoint Designer 2013 y se muestra como: <br/>![Buscar el administrador de un usuario](images/spd15-LookupMgr4User-txt.JPG)|**Buscar administrador de un usuario** <br/> Use esta acción para buscar el administrador de un usuario. El valor de resultado luego se almacena en una variable.  <br/> > **NOTA**> Para que esta acción funcione correctamente, debe ejecutar el servicio de perfiles de usuario en SharePoint.           |
   

### Acciones del conjunto de documentos
<a name="section1e"> </a>

Algunas acciones de flujo de trabajo solo están disponibles cuando el flujo de trabajo está asociado a una biblioteca de documentos, como documentos compartidos, o para el tipo de contenido del documento.
  
    
    

****


|**FORMA DE ACCIÓN DE VISIO**|**ACCIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA ACCIÓN**|
|:-----|:-----|:-----|
|![Enviar aprobación para el conjunto de documentos](images/spd15-SendApproval4DocSet-visio.JPG)|Esta acción de Visio es igual que la acción **Iniciar proceso de aprobación de conjunto de documentos** en SharePoint Designer 2013 y se muestra como: <br/>![Iniciar el proceso de aprobación del conjunto de documentos](images/spd15-SendApproval4DocSet-txt.JPG)|**Enviar aprobación para el conjunto de documentos** <br/> Use esta acción para iniciar el proceso de aprobación para un conjunto de documentos.  <br/> |
|![Enviar conjunto de documentos al repositorio](images/spd15-SendDocSet2Repos-visio.JPG)|Esta acción de Visio es igual que la acción **Enviar conjunto de documentos al repositorio** en SharePoint Designer 2013 y se muestra como: <br/>![Enviar conjunto de documentos al repositorio](images/spd15-SendDocSet2Repos-txt.JPG)|**Enviar conjunto de documentos al repositorio** <br/> Use esta acción para mover o copiar el conjunto de documentos al repositorio de documentos. Un repositorio de documentos puede ser una biblioteca del sitio de SharePoint o un sitio independiente como el centro de documentos, que redirige los registros a un destino específico según las reglas que defina.  <br/> |
|![Enviar documento a repositorio](images/spd15-SendDoc2Repos-visio.JPG)|Esta acción de Visio es igual que la acción **Enviar documento a repositorio** en SharePoint Designer 2013 y se muestra como: <br/>![Enviar documento a repositorio](images/spd15-SendDoc2Repos-txt.JPG)|**Enviar documento a repositorio** <br/> Use esta acción para mover o copiar un documento a un repositorio de documentos. Un repositorio de documentos puede ser una biblioteca del sitio de SharePoint o un sitio independiente como el centro de documentos, que redirige los registros a un destino específico según las reglas que defina.  <br/> |
|![Establecer estado de aprobación de contenido del conjunto de documentos](images/spd15-SetContentApprStatus-visio.JPG)|Esta acción de Visio es igual que la acción **Establecer estado de aprobación de contenido del conjunto de documentos** en SharePoint Designer 2013 y se muestra como: <br/>![Establecer estado de aprobación de contenido del conjunto de documentos](images/spd15-SetContentApprStatus4DocSet-txt.JPG)|**Establecer estado de aprobación de contenido para el conjunto de documentos** <br/> Use esta acción para establecer la aprobación del contenido de un conjunto de documentos en **Aprobado**, **Rechazado** o **Pendiente**.  <br/> |
   

## Condiciones de flujo de trabajo
<a name="section2"> </a>

Una condición de flujo de trabajo es una ramificación en el flujo de trabajo. La condición de flujo de trabajo compara la entrada con un valor especificado. Si coinciden, el flujo de trabajo sigue una rama, si no es así, sigue la rama de otra.
  
    
    

> **IMPORTANTE**
> La mayoría de las formas de condición que puede insertar en un flujo de trabajo de SharePoint en Visio requieren configuración adicional cuando se importa el flujo de trabajo en SharePoint Designer. En Visio, recuerde usar la característica de comentarios de cada forma de condición para especificar los criterios de decisión de la condición. 
  
    
    


### Condiciones generales

En esta sección se describen las condiciones que están disponibles en SharePoint Designer 2013de lista y flujos de trabajo de lista reutilizables, independientemente de la lista o el tipo de contenido asociado con el flujo de trabajo.
  
    
    

****


|**FORMA DE CONDICIÓN DE VISIO**|**CONDICIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA CONDICIÓN**|
|:-----|:-----|:-----|
|![Comparar origen de datos](images/spd15-CompareDataSrc-visio.JPG)|Esta condición de Visio es la mismo que la condición **Si cualquier valor es igual al valor** en SharePoint Designer 2013 y se muestra como: <br/>![Si cualquier valor es igual al valor](images/spd15-CompareDataSrc-txt.JPG)|**Comparar origen de datos** <br/> Esta condición compara dos valores. Puede especificar si los valores deben ser iguales o distintos.  <br/> |
|![Comparar campo del documento](images/spd15-CompareDocField-visio.JPG)|Esta condición de Visio es igual que la condición **Si el campo de elemento actual es igual al valor** en SharePoint Designer 2013 y se muestra como: <br/>![Si el campo del elemento actual es igual que el valor](images/spd15-CompareDocField-txt.JPG)|**Comparar campo del documento** <br/> Esta condición comprueba un campo con un valor que especifique. Puede especificar si los valores deben ser iguales o distintos.  <br/> |
|![Creado por una persona específica](images/spd15-CreatedBySpecPerson-visio.JPG)|Esta condición de Visio es igual que la condición **Creado por una persona especificada** en SharePoint Designer 2013 y se muestra como: <br/>![Si lo creó una persona específica](images/spd15-CreatedBySpecPerson-txt.JPG)|**Creado por una persona especificada** <br/> Esta condición comprueba si el elemento fue creado por un usuario específico. El usuario se puede especificar como una dirección de correo electrónico, como olivier@contoso.com o seleccionar usuarios de SharePoint, Exchange o Active Directory.  <br/> > **NOTA**> La dirección de correo electrónico y el nombre de usuario distinguen mayúsculas y minúsculas. Se recomienda que seleccione una dirección de correo electrónico o un nombre de usuario para ayudar a garantizar el uso de mayúsculas y minúsculas. Si escribe una dirección de correo electrónico o un nombre de usuario, debe coincidir con las mayúsculas y minúsculas de la cuenta. Por ejemplo, si creó contoso\\molly no se evaluará como true si la cuenta de usuario es Contoso\\Molly.           |
|![Creado en un intervalo de fechas determinado](images/spd15-CreatedInSpecDateSpan-visio.JPG)|Esta condición de Visio es igual que la condición **Creado en un intervalo de fechas específico** en SharePoint Designer 2013 y se muestra como: <br/>![Si se creó en un intervalo de fechas determinado](images/spd15-CreatedInSpecDateSpan-txt.JPG)|**Creado en el intervalo de fechas determinado** <br/> Esta condición comprueba si el elemento se creó entre las fechas especificadas. Puede usar la fecha actual, una fecha específica o una búsqueda.  <br/> |
|![Modificado por una persona específica](images/spd15-ModifiedBySpecPerson-visio.JPG)|Esta condición de Visio es igual que la condición **Modificado por una persona específica** en SharePoint Designer 2013 y se muestra como: <br/>![Si lo modificó una persona específica](images/spd15-ModifiedBySpecPerson-txt.JPG)|**Modificado por una persona específica** <br/> Utilice esta condición para comprobar si un elemento ha sido modificado por un usuario especificado. El usuario se puede especificar como una dirección de correo electrónico, como olivier@contoso.com o seleccionar usuarios de SharePoint, Exchange o Active Directory.  <br/> > **NOTA**> La dirección de correo electrónico y el nombre de usuario distinguen mayúsculas y minúsculas. Se recomienda que seleccione una dirección de correo electrónico o un nombre de usuario para ayudar a garantizar el uso de mayúsculas y minúsculas. Si escribe una dirección de correo electrónico o un nombre de usuario, debe coincidir con las mayúsculas y minúsculas de la cuenta. Por ejemplo, si creó contoso\\molly no se evaluará como true si la cuenta de usuario es Contoso\\Molly.           |
|![Modificado en un intervalo de fechas determinado](images/spd15-ModifiedInSpecDateSpan-visio.JPG)|Esta condición de Visio es igual que la condición **Modificado en un intervalo de fechas determinado** en SharePoint Designer 2013 y se muestra como: <br/>![Si se modificó en un intervalo de fechas determinado](images/spd15-ModifiedInSpecDateSpan-txt.JPG)|**Modificado en un intervalo de fechas determinado** <br/> Esta condición comprueba si un elemento se ha modificado entre las fechas especificadas. Puede usar la fecha actual, una fecha específica o una búsqueda.  <br/> |
|![El campo de título contiene palabras clave](images/spd15-TitleFieldKeywords-visio.JPG)|Esta condición de Visio es igual que la condición **El campo de título contiene palabras clave** en SharePoint Designer 2013 y se muestra como: <br/>![Si el campo de título contiene palabras clave](images/spd15-TitleFieldKeywords-txt.JPG)|**El campo de título contiene palabras clave** <br/> Esta condición comprueba si el campo **Título** de un elemento contiene una palabra específica. Puede especificar la palabra clave en el generador de cadenas, que puede ser un valor estático, una cadena dinámica o una combinación, o insertar una búsqueda en un campo o variable. <br/> > **NOTA**> No puede buscar más de una palabra clave en la condición **El campo de título contiene palabras clave**. Sin embargo, puede usar operadores lógicos como**||**(or) o **&amp;&amp;** (and.          |
   

### Condiciones del conjunto de documentos

Algunas condiciones de flujo de trabajo solo están disponibles cuando el flujo de trabajo está asociado a una biblioteca de documentos, como documentos compartidos o para el tipo de contenido del documento.
  
    
    


|**FORMA DE CONDICIÓN DE VISIO**|**CONDICIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA CONDICIÓN**|
|:-----|:-----|:-----|
|![El tamaño de archivo se encuentra en un rango específico](images/spd15-FileSzInSpecRange-visio.JPG)|Esta condición de Visio es el misma que la condición **El archivo tiene un tamaño comprendido en un intervalo de kilobytes determinado** en SharePoint Designer 2013 y se muestra como: <br/>![El tamaño de archivo se encuentra en un rango específico](images/spd15-FileSzInSpecRange-txt.JPG)|**El tamaño de archivo se encuentra en un rango específico** <br/> Esta condición comprueba si el tamaño del archivo de un documento se encuentra entre los tamaños especificados, en kilobytes. La condición no incluye los tamaños especificados en la evaluación. Puede especificar un número o usar una búsqueda para el primer y segundo tamaño en la condición.  <br/> |
|![El archivo es de un tipo específico](images/spd15-FileIsSpecType-visio.JPG)|Esta condición de Visio es igual que la condición **El tipo de archivo es un tipo determinado** en SharePoint Designer 2013 y se muestra como: <br/>![El archivo es de un tipo específico](images/spd15-FileIsSpecType-txt.JPG)|**El archivo es de un tipo específico** <br/> Esta condición comprueba si el tipo de archivo del elemento actual es del tipo especificado, por ejemplo, docx. Puede especificar el tipo de archivo como una cadena o usar una búsqueda.  <br/> |
   

### Condiciones de lista


  
    
    

****


|**FORMA DE CONDICIÓN DE VISIO**|**CONDICIÓN CORRESPONDIENTE EN SHAREPOINT DESIGNER**|**DESCRIPCIÓN DE LA CONDICIÓN**|
|:-----|:-----|:-----|
|![Comprobar permisos de usuario exactos](images/spd15-ChkExactUserPerms-visio.JPG)|Esta condición de Visio es igual que la condición **Comprobar niveles de permisos de elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Comprobar niveles de permiso de elementos de lista](images/spd15-ChkExactUserPerms-txt.JPG)|**Comprobar permisos de usuario exactos** <br/> Esta condición comprueba que el usuario especificado tiene el nivel de permiso mínimos necesarios.  <br/> |
|![Comprobar permisos de usuario](images/spd15-ChkUserPerms-visio.JPG)|Esta condición de Visio es igual que la condición **Comprobar permisos de elemento de lista** en SharePoint Designer 2013 y se muestra como: <br/>![Comprobar permisos de elementos de lista](images/spd15-ChkUserPerms-txt.JPG)|**Comprobar permiso de usuario** <br/> Esta condición comprueba si el usuario especificado tiene los permisos mínimos necesarios.  <br/> |
   

## Terminadores de flujo de trabajo
<a name="section3"> </a>

En Visio, cada flujo de trabajo debe comenzar con un terminador de inicio (
  
    
    
![Iniciar](images/spd15-WFStart-icon.JPG)
  
    
    
) y finalizan con un terminador Detener (
  
    
    
![Detener](images/spd15-WFStop-icon.JPG)
  
    
    
). En un flujo de trabajo determinado solo puede utilizarse un tipo de terminador. Los terminadores son necesarios cuando se crea un flujo de trabajo de SharePoint en Visio > para que el flujo de trabajo pueda pasar la validación y se pueda exportar. Los terminadores de flujo de trabajo no se utilizan en SharePoint Designer.
  
    
    

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Novedades en flujos de trabajo para SharePoint 2013](what-s-new-in-workflows-for-sharepoint-2013.md)
    
  
-  [Introducción a los flujos de trabajo de SharePoint 2013](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [Desarrollo de flujos de trabajo en SharePoint Designer y Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  

  
    
    
