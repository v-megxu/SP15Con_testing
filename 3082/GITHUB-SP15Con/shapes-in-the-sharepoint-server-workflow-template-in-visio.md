---
title: Formas en la plantilla de flujo de trabajo de SharePoint Server en Visio
ms.prod: SHAREPOINT
ms.assetid: f35bdf5d-c102-4e2d-8a23-1d2df17155b9
---



# Formas en la plantilla de flujo de trabajo de SharePoint Server en Visio
Infórmese sobre las formas en la plantilla de flujo de trabajo de SharePoint 2013 en Visio 2013.
## Introducción
<a name="VSSPD_Shapes_Intro"> </a>

Este artículo recoge las formas contenidas en la plantilla de flujo de trabajo de SharePoint 2013 que hay en Visio 2013 y en el Diseñador visual de SharePoint Designer 2013. Cuando se abre la plantilla, también abre las galerías de símbolos de las acciones de flujo de trabajo de SharePoint 2013, las condiciones de flujo de trabajo de SharePoint 2013 y los terminadores de flujo de trabajo de SharePoint 2013. Muchas de las formas incluidas en las galerías de símbolos corresponden a determinadas acciones, condiciones u otras construcciones lógicas del Diseñador declarativo para compilar flujos de trabajo en SharePoint Designer 2013.
  
    
    

> **IMPORTANTE**
> La siguiente es una referencia sobre las acciones de flujo de trabajo que se admiten en SharePoint Designer 2013. La mayoría de estas acciones están disponibles en SharePoint Designer 2010, aunque una de ellas (Esperar al evento del elemento de lista) se ha revisado y mejorado en la versión actual. En esta versión, se han introducido 12 acciones nuevas y se han quitado 25. (Para ver la lista de las acciones, condiciones y bloques que se han quitado, vaya a  [Acciones del flujo de trabajo disponibles con el puente de interoperatividad del flujo de trabajo](workflow-actions-available-using-the-workflow-interop-bridge.md)). 
  
    
    


## Formas de acción
<a name="VSSDP_Actions"> </a>

En la tabla siguiente se recoge la lista de todas las formas contenidas en la galería de símbolos de acciones de SharePoint 2013 de la plantilla de flujo de trabajo de SharePoint 2013 que hay en Visio 2013.
  
    
    

> **NOTA**
> Se detallan todas las propiedades de las formas que aparecen en la tabla, así como una propiedad **Propiedades**. 
  
    
    



|**Forma en Visio 2013 y el Diseñador visual de SharePoint Designer 2013**|**Acción en el Diseñador declarativo de SharePoint Designer 2013**|**Propiedades en el Diseñador visual de SharePoint Designer 2013**|**Descripción**|
|:-----|:-----|:-----|:-----|
|Agregar un comentario  <br/> |**Agregar un comentario** <br/> |**Comentario** <br/> |Permite dejar comentarios informativos en el diseñador de flujos de trabajo para referencia. Esto resulta de especial utilidad cuando hay otros usuarios colaborando en el flujo de trabajo.  <br/> |
|Agregar hora a la fecha  <br/> |**Agregar hora a la fecha** <br/> |**Meses** <br/> **Días** <br/> **Horas** <br/> **Minutos** <br/> **Fecha** <br/> **Resultado** <br/> |Agrega una hora concreta en minutos, horas, días o meses a una fecha, y almacena el valor de resultado como una variable. La fecha puede ser la actual, una concreta o una búsqueda. El valor "Fecha actual" devuelve medianoche UTC.  <br/> |
|Asignar una tarea  <br/> |**Asignar una tarea** <br/> |**Configuración de la tarea** <br/> **Resultado de la tarea** <br/> **Id. del elemento de tarea** <br/> |Asigna una tarea de flujo de trabajo a un usuario y establece una fecha de vencimiento para la finalización de la tarea.  <br/> |
|Llamar al servicio web HTTP  <br/> |**Llamar al servicio web HTTP** <br/> |**Solicitud HTTP** <br/> **Parámetros** <br/> **Variable del contenido de respuesta** <br/> **Variable del encabezado de respuesta** <br/> **Variable del código de respuesta** <br/> |Funciona como llamada de método a un servicio web HTTP.  <br/> > **NOTA**> La compilación actual admite llamadas de SharePoint solo a servicios HTTP **anónimos** y solo usando tipos de valor devuelto y parámetros **string**. Además, no se admiten elementos XML compuestos. Actualmente, solo ofrecemos compatibilidad con ASMX clásico, no para el servicio WCG.           |
|Proteger elemento  <br/> |**Proteger elemento** <br/> |**Elemento** <br/> **Comentario** <br/> |Protege un elemento que está desprotegido. Solo se pueden proteger los elementos de una biblioteca de documentos.  <br/> > **PRECAUCIóN**> Si intenta proteger un elemento que no está desprotegido, el flujo de trabajo se bloquea.           |
|Desproteger elemento  <br/> |**Desproteger elemento** <br/> |**Elemento** <br/> |Desprotege un elemento. El flujo de trabajo comprueba que el elemento esté protegido antes de desproteger un documento. Solo se pueden desproteger elementos de una biblioteca de su sitio.  <br/> > **PRECAUCIóN**> Si intenta desproteger un elemento que no está protegido, el flujo de trabajo se bloquea.           |
|Copiar documento  <br/> |**Copiar documento** <br/> |**Documento** <br/> **Biblioteca** <br/> |Copia un documento de la lista actual en otra lista de la biblioteca de documentos.  <br/> |
|Contar elementos en un diccionario  <br/> |**Contar elementos en un diccionario** <br/> |**Diccionario** <br/> **Variable de resultado** <br/> |Cuenta el número de elementos que hay en una variable de diccionario.  <br/> |
|Crear proyecto a partir del elemento actual  <br/> |**Crear proyecto a partir del elemento actual** <br/> |**Tipo de proyecto empresarial** <br/> |Toma el elemento actual y crea un nuevo proyecto en el sitio de PWA de la granja de servidores de SharePoint.  <br/> |
|Crear elemento de lista  <br/> |**Crear elemento de lista** <br/> |**Elemento** <br/> **Variable de resultado** <br/> |Crea un nuevo elemento de lista en la lista que especifique. Puede proporcionar los campos y valores del nuevo elemento. Puede usar esta acción siempre que quiera crear un nuevo elemento con información concreta.  <br/> |
|Eliminar elemento  <br/> |**Eliminar elemento** <br/> |**Elemento** <br/> |Elimina un elemento.  <br/> > **NOTA**> Esta acción finaliza en el equipo que ejecuta el motor de flujo de trabajo del Administrador de flujos de trabajo y produce una excepción **System.InvalidOperationException**. No hay ninguna solución.           |
|Descartar elemento desprotegido  <br/> |**Descartar elemento desprotegido** <br/> |**Elemento** <br/> |Descarta los cambios y vuelve a proteger el elemento si está desprotegido y se han hecho cambios en él.  <br/> > **PRECAUCIóN**> Si intenta proteger un elemento que no está desprotegido, el flujo de trabajo se bloquea.           |
|Realizar el cálculo  <br/> |**Realizar el cálculo** <br/> |**OperandoIzqda** <br/> **Operador** <br/> **OperandoDcha** <br/> **Para** <br/> |Realiza un cálculo aritmético y almacena el valor de resultado en una variable.  <br/> > **NOTA**> En SharePoint 2013, esta acción solo admite el tipo numérico **Double**. No se admiten enteros. No se admite el empleo del operador "+" (concatenación) para cadenas.           |
|Extraer subcadena de final de cadena  <br/> |**Extraer subcadena de final de cadena** <br/> |**Número de caracteres** <br/> **Cadena** <br/> **Resultado** <br/> |Copia un número especificado de caracteres a partir del final de una cadena y almacena el resultado en una variable.  <br/> |
|Extraer subcadena de índice de cadena  <br/> |**Extraer subcadena de índice de cadena** <br/> |**Cadena** <br/> **Índice** <br/> **Resultado** <br/> |Copia una subcadena a partir de un índice especificado en la cadena y coloca el valor en una variable.  <br/> > **NOTA**> Aunque el valor de índice que hay en la compilación actual de Vista previa técnica de SharePoint Designer es de base cero, los valores de SharePoint Designer 2010 se indexaron a partir de 1.           |
|Extraer subcadena de principio de cadena  <br/> |**Extraer subcadena de principio de cadena** <br/> |**Número de caracteres** <br/> **Cadena** <br/> **Resultado** <br/> |Copia un número especificado de caracteres a partir del principio de una cadena y almacena el resultado en una variable.  <br/> |
|Extraer subcadena de cadena de índice con longitud  <br/> |**Extraer subcadena de cadena de índice con longitud** <br/> |**Cadena** <br/> **Índice** <br/> **Número de caracteres** <br/> **Resultado** <br/> |Copia una subcadena compuesta por un número especificado de caracteres a partir de un índice especificado en la cadena y coloca el valor en una variable.  <br/> > **NOTA**> Aunque el valor de índice que hay en la compilación actual de Vista previa técnica de SharePoint Designer es de base cero, los valores de SharePoint Designer 2010 se indizaron a partir de 1.           |
|Encontrar intervalo entre fechas  <br/> |**Encontrar intervalo entre fechas** <br/> |**Unidades** <br/> **Fecha de inicio** <br/> **Fecha de finalización** <br/> **Resultado** <br/> |Calcula el intervalo de tiempo en minutos, horas o días entre dos fechas y almacena el resultado en una variable.  <br/> |
|Encontrar subcadena en cadena  <br/> |**Encontrar subcadena en cadena** <br/> |**Subcadena** <br/> **Cadena** <br/> **Resultado** <br/> |Encuentra una subcadena concreta dentro de una cadena y devuelve el índice de la posición inicial de la subcadena.  <br/> |
|Obtener elemento del diccionario  <br/> |**Obtener elemento del diccionario** <br/> |**Nombre de elemento de la ruta de acceso** <br/> **Diccionario** <br/> **Variable de resultado** <br/> |Devuelve un elemento concreto de una variable de diccionario.  <br/> |
|Registrar en el historial  <br/> |**Registrar en el historial** <br/> |**Mensaje** <br/> |Escribe un mensaje de una lista de elementos de mensaje predefinidos en el historial del flujo de trabajo.  <br/> |
|Detener durante  <br/> |**Detener durante** <br/> |**Días** <br/> **Horas** <br/> **Minutos** <br/> |Hace que un flujo de trabajo deje de ejecutarse durante un intervalo de tiempo concreto en días, horas y minutos.  <br/> |
|Detener hasta fecha  <br/> |**Detener hasta fecha** <br/> |**Fecha** <br/> |Hace que un flujo de trabajo deje de ejecutarse hasta una fecha y una hora especificadas.  <br/> |
|Sustituir subcadena en cadena  <br/> |**Sustituir subcadena en cadena** <br/> |**Buscar cadena** <br/> **Sustituir cadena** <br/> **Cadena** <br/> **Resultado** <br/> |Sustituye una subcadena concreta por otra.  <br/> |
|Enviar correo electrónico  <br/> |**Enviar correo electrónico** <br/> |**Correo electrónico** <br/> |Envía automáticamente un mensaje de correo que contiene un mensaje predeterminado a un usuario o grupo cuando se produce un evento de flujo de trabajo determinado.  <br/> > **IMPORTANTE**> Si el sitio no está agregado a la lista Sitios de confianza, los mensajes de correo se enrutan a la carpeta Correo no deseado de Outlook.           |
|Establecer campo en elemento actual  <br/> |**Establecer campo en elemento actual** <br/> |**Campo** <br/> **Valor** <br/> |Establece un campo del elemento actual en un valor.  <br/> |
|Configurar parte de la hora del campo Fecha y hora  <br/> |**Configurar parte de la hora del campo Fecha y hora** <br/> |**Horas** <br/> **Minutos** <br/> **Fecha** <br/> **Resultado** <br/> |Crea una marca de tiempo y almacena el valor de resultado en una variable. Puede establecer el tiempo en horas y minutos, y agregar una fecha actual, una concreta o una búsqueda.  <br/> |
|Establecer estado del flujo de trabajo  <br/> |**Establecer estado del flujo de trabajo** <br/> |**Estado** <br/> |Establece el estado del flujo de trabajo.  <br/> |
|Establecer variable de flujo de trabajo  <br/> |**Establecer variable de flujo de trabajo** <br/> |**Variable** <br/> **Valor** <br/> |Establece una variable de flujo de trabajo en un valor. También puede usar esta acción si quiere que el flujo de trabajo asigne datos a una variable.  <br/> |
|Iniciar un flujo de trabajo de lista  <br/> |**Iniciar un flujo de trabajo de lista** <br/> |**Nombre de la asociación** <br/> **Entradas** <br/> **Elemento** <br/> |Inicia un flujo de trabajo de lista de SharePoint 2010.  <br/> > **NOTA**>  "Iniciar un flujo de trabajo de lista" tiene los problemas siguientes:>  No se puede usar como parámetro el campo de tipo "Asignaciones" si el flujo de trabajo de 2010 tiene una acción TaskProcess.>  Si se hacen varias llamadas al mismo flujo de trabajo de 2010, el resultado serán varios orígenes de datos en la función de búsqueda de flujos de trabajo de 2013. Estos orígenes de trabajo serán todos iguales.>  Los nombres de variables de 2013 no pueden contener caracteres especiales como '?' y '#'. Si un flujo de trabajo de 2010 contiene caracteres especiales, se convertirán en código hexadecimal en el flujo de trabajo de 2013.          |
|Iniciar un flujo de trabajo de sitio  <br/> |**Iniciar un flujo de trabajo de sitio** <br/> |**Nombre de la asociación** <br/> **Parámetros** <br/> |Inicia un flujo de trabajo de lista de SharePoint 2010.  <br/> > **NOTA**>  "Iniciar un flujo de trabajo de lista" tiene los problemas siguientes:>  No se puede usar como parámetro el campo de tipo "Asignaciones" si el flujo de trabajo de 2010 tiene una acción TaskProcess.>  Si se hacen varias llamadas al mismo flujo de trabajo de 2010, el resultado serán varios orígenes de datos en la función de búsqueda de flujos de trabajo de 2013. Estos orígenes de trabajo serán todos iguales.>  Los nombres de variables de 2013 no pueden contener caracteres especiales como '?' y '#'. Si un flujo de trabajo de 2010 contiene caracteres especiales, se convertirán en código hexadecimal en el flujo de trabajo de 2013.          |
|Iniciar un proceso de tarea  <br/> |**Iniciar un proceso de tarea** <br/> |**Configuración del proceso** <br/>  Resultado del proceso <br/> |Crea tareas en varios usuarios y permite que se lleven a través de un proceso personalizado.  <br/> |
|Traducir documento  <br/> |**Traducir documento** <br/> |**Documento** <br/> **Idioma** <br/> **Biblioteca de documentos** <br/> |Traduce un documento a un idioma concreto.  <br/> > **NOTA**> Exige una aplicación de servicio de traducción automática preconfigurada.           |
|Recortar cadena  <br/> |**Recortar cadena** <br/> |**Cadena** <br/> **Resultado** <br/> |Quita los espacios en blanco del principio y el final de una cadena.  <br/> |
|Actualizar elemento de lista  <br/> |**Actualizar elemento de lista** <br/> |**Elemento** <br/> |Actualiza un elemento de lista. Puede especificar los campos y los nuevos valores de esos campos.  <br/> |
|Esperar al evento del elemento de lista  <br/> |**Esperar al evento del elemento de lista** <br/> |**Evento** <br/> **Elemento relacionado** <br/> |[Versión mejorada de acción de Office 2010]. Detiene la instancia actual del flujo de trabajo para esperar a un evento de elemento de lista concreto. Esta acción escucha a dos eventos: **ItemUpdated** y **ItemAdded**.  <br/> |
|Esperar cambio de campo  <br/> |**Esperar cambio de campo** <br/> |**Campo** <br/> **Valor** <br/> |Espera a que un campo del elemento actual sea igual a un valor determinado.  <br/> |
|Establecer campo de Project  <br/> |**Establecer campo de Project** <br/> |**Campo** <br/> **Valor** <br/> |Establece un valor para un campo concreto en Project Server.  <br/> > **NOTA**> Esta acción exige que el proyecto esté protegido. Si no lo está, el flujo de trabajo finalizará y los usuarios no podrán abrir ese proyecto en Project Web App.           |
|Establecer estado de fase de Project  <br/> |**Establecer estado de fase de Project** <br/> |**Estado de fase** <br/> **Información de versión** <br/> |Establece el estado de la fase de Project.  <br/> > **NOTA**> Si se desprotege un proyecto actual, se produce una excepción.           |
|Establecer campo de estado en lista de ideas  <br/> |**Establecer campo de estado en lista de ideas** <br/> |**Estado** <br/> |Actualiza el estado en el elemento de lista original asociado al proyecto actual.  <br/> |
|Esperar a evento de Project  <br/> |**Esperar a evento de Project** <br/> |**Nombre del evento** <br/> |Espera a un evento concreto de Project.  <br/> |
   

## Formas de condición
<a name="VSSPD_Conditions"> </a>

En la tabla siguiente se recoge la lista de todas las formas contenidas en la galería de símbolos de condiciones de SharePoint 2013 que hay en la plantilla de flujo de trabajo de SharePoint 2013.
  
    
    


|**Forma en Visio 2013 y el Diseñador visual de SharePoint Designer 2013**|**Acción en el Diseñador declarativo de SharePoint Designer 2013**|**Propiedades en el Diseñador visual de SharePoint Designer 2013**|**Descripción**|
|:-----|:-----|:-----|:-----|
|Si un valor es igual a otro valor  <br/> |**Si un valor es igual a otro valor** <br/> |**Valor** <br/> **Operando** <br/> **Valor** <br/> |Compara dos valores. Se puede especificar si los valores deben ser iguales o no.  <br/> |
|La persona es un usuario válido de SharePoint  <br/> |**La persona es un usuario válido de SharePoint** <br/> |**Usuario** <br/> |Comprueba si un usuario determinado está registrado o pertenece a un grupo del sitio de SharePoint.  <br/> |
|Omitir fase del proyecto  <br/> |**Omitir fase del proyecto** <br/> |ND  <br/> |Esta condición comprueba si la función de omitir a fase se ha activado en el servidor para la instancia actual de flujo de trabajo.  <br/> |
   

## Formas de terminador
<a name="VSSPD_Terminators"> </a>

En la tabla siguiente se recoge la lista de todas las formas contenidas en la galería de símbolos de terminadores de SharePoint 2013 que hay en la plantilla de flujo de trabajo de SharePoint 2013.
  
    
    


|**Forma en Visio 2013 y el Diseñador visual de SharePoint Designer 2013**|**Acción en el Diseñador declarativo de SharePoint Designer 2013**|**Propiedades en el Diseñador visual de SharePoint Designer 2013**|**Descripción**|
|:-----|:-----|:-----|:-----|
|Inicio  <br/> |ND  <br/> |ND  <br/> |Inicia el flujo de trabajo. Todos los diagramas de flujo de trabajo de SharePoint 2013 deben tener una sola forma Inicio.  <br/> |
|Fase  <br/> |**Fase** <br/> |ND  <br/> |Contiene diversas formas y puede incluir bifurcaciones. Todas las acciones del flujo de trabajo deben estar contenidas en una fase. Las formas de fase se ven usando formas de contenedor. Un forma de fase exige que se agreguen una forma Entrar y otra Salir a los bordes del contenedor para definir las rutas de acceso de entrada y salir de la fase.  <br/> Para más información, vea la sección titulada "Fases, bucles y pasos" del artículo  [Desarrollo de flujos de trabajo en SharePoint Designer y Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Paso  <br/> |**Paso** <br/> |ND  <br/> |Representa una serie agrupada de acciones secuenciales. Los pasos deben estar contenidos en una fase. Una forma de paso también debe tener las formas Entrar y Salir, que se agregan cuando la forma se coloca en el lienzo.  <br/> Para más información, vea la sección titulada "Fases, bucles y pasos" del artículo  [Desarrollo de flujos de trabajo en SharePoint Designer y Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Fase simple  <br/> |**Fase** <br/> |ND  <br/> |Agrega fases nuevas al nivel superior del flujo de trabajo cuando se está en la vista de fases de Visio 2013.  <br/> |
|Bucle n veces  <br/> |**Bucle n veces** <br/> |**Contador de bucle** <br/> |Define una serie de formas conectadas que se ejecutarán como un bucle volviendo de la última forma de la serie a la primera hasta que el bucle se haya ejecutado un cierto número de veces. Al igual que las fases, los bucles se representan con una forma de contenedor que incluye las formas Entrar y Salir.  <br/> Para más información, vea la sección titulada "Fases, bucles y pasos" del artículo  [Desarrollo de flujos de trabajo en SharePoint Designer y Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Bucle con condición  <br/> |**Bucle con condición** <br/> |**Contador de bucle** <br/> |El bucle se repite hasta que se cumple cierta condición.  <br/> |
|Iniciar acción paralela  <br/> |**Bloque paralelo** <br/> |ND  <br/> ||
|Finalizar acción paralela  <br/> |**Bloque paralelo** <br/> |ND  <br/> ||
   

## Recursos adicionales
<a name="VSSPD_Additional"> </a>


-  [Desarrollo de flujos de trabajo en SharePoint Designer y Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [Referencia rápida sobre acciones de flujo de trabajo (plataforma de flujo de trabajo de SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Guía de formas de plantillas de flujo de trabajo de SharePoint](http://office.microsoft.com/es-es/visio-help/sharepoint-workflow-template-shapes-guide-HA101903894.aspx)
    
  
-  [Centro para desarrolladores de SharePoint](http://msdn.microsoft.com/es-es/sharepoint/default.aspx)
    
  
-  [Centro para desarrolladores de Visio](http://msdn.microsoft.com/es-es/office/aa905478)
    
  
