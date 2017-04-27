---
title: Desarrollo de flujos de trabajo en SharePoint Designer y Visio
ms.prod: SHAREPOINT
ms.assetid: 496780d5-47d6-4a43-bf14-70aefb8d820c
---


# Desarrollo de flujos de trabajo en SharePoint Designer y Visio
Información sobre cómo usar Visio 2013 y SharePoint Designer 2013 para crear y publicar flujos de trabajo en un sitio SharePoint 2013 sin necesidad de código.
## Introducción
<a name="VSSPD_Intro"> </a>

Visio 2013 y SharePoint Designer 2013 hacen que a los analistas de negocios, consultores de procesos y profesionales de TI les resulte fácil colaborar y crear flujos de trabajo . Tanto Visio Professional 2013 como el Diseñador visual en SharePoint Designer 2013 proporcionan una buena representación de flujos de trabajo en un formato que los programadores y las personas que no saben de programación pueden entender por igual.
  
    
    

> **NOTA**
> Para obtener orientación sobre cómo instalar y configurar SharePoint Server 2013 y el servidor de Administrador de flujos de trabajo, consulte  [Configuración de flujos de trabajo en SharePoint Server 2013](http://technet.microsoft.com/es-es/library/jj658586.aspx). 
  
    
    

Con el uso de Visio 2013, puede crear visualmente un flujo de trabajo de SharePoint, exportar el flujo de trabajo a SharePoint Designer 2013, y después publicar ese flujo de trabajo en un sitio de SharePoint. Una vez que se crea el flujo de trabajo en Visio 2013, debe exportarse a SharePoint Designer 2013. Después, un propietario de sitio de SharePoint o profesional de TI agrega parámetros al flujo de trabajo con el editor de texto del flujo de trabajo o el nuevo Diseñador de flujo de trabajo visual, que es un control ActiveX de Visio 2013 hospedado en SharePoint Designer 2013. Una vez que se completa el flujo de trabajo, puede publicarse en el sitio de SharePoint.
  
    
    
Esto es ideal para analistas de negocios y consultores de procesos que ya están familiarizados con diagramas de flujo en Visio, porque les permite diseñar un flujo de trabajo que representar lógica de negocios. La persona que diseña el flujo de trabajo puede concentrarse exclusivamente en las necesidades de inteligencia empresarial (BI) del flujo de trabajo sin tener que ser un experto en flujos de trabajo declarativos.
  
    
    

## Acerca de la creación de flujos de trabajo de SharePoint en Visio 2013 y SharePoint Designer 2013
<a name="VSSPD_About"> </a>

Visio 2013 incluye una plantilla Flujo de trabajo de SharePoint 2013 que puede usarse para crear flujos de trabajo de SharePoint 2013. La plantilla Flujo de trabajo de SharePoint 2013 está asociada con tres galerías de símbolos: Acciones de flujo de trabajo de SharePoint 2013, Condiciones de flujo de trabajo de SharePoint 2013 y Terminadores de flujo de trabajo de SharePoint 2013. Las formas de estas tres galerías de símbolos corresponden a acciones y condiciones específicas que se pueden usar dentro de un flujo de trabajo de SharePoint 2013. Para crear un flujo de trabajo, solo arrastre las formas en el lienzo de dibujo en Visio 2013 para modelar la lógica de negocio detrás del flujo de trabajo.
  
    
    

### Fases, bucles y pasos

Los flujos de trabajo en SharePoint Designer 2013 ahora incluyen las nociones de fases, bucles ypasos. Los autores de flujos de trabajo pueden agrupar una cantidad de acciones y condiciones individuales como una sola unidad para definir el proceso con más claridad. Por ejemplo, podría existir una fase o un paso Aprobación o Solicitar comentarios. Dentro de esa fase o ese paso, se ubicarían todas las acciones necesarias para el proceso. La fase o el paso en sí mismos podrían ser un nodo de un flujo de trabajo más grande y permitirían que un visor viera el estado de esa fase como una totalidad, en lugar de un conjunto de acciones individuales.
  
    
    
La plantilla Flujo de trabajo de SharePoint 2013 que se incluye en Visio 2013 también usa fases, bucles y pasos como bloques de creación lógicos para crear un flujo de trabajo. 
  
    
    

> **IMPORTANTE**
> Como consecuencia de las diferencias subyacentes entre la plantilla Flujo de trabajo de Microsoft SharePoint 2010 y la plantilla Flujo de trabajo de SharePoint 2013, no puede usar formas de una plantilla dentro de un diagrama creado por la otra. Únicamente las formas de las galerías de símbolos Acciones de flujo de trabajo de SharePoint 2013, Condiciones de flujo de trabajo de SharePoint 2013 y Terminadores de flujo de trabajo de SharePoint 2013 pueden usarse para crear un flujo de trabajo de SharePoint 2013. 
  
    
    


### Formas de fase

Una fase puede contener cualquier cantidad de formas y puede incluir bifurcación. Pero, puede existir una sola ruta adentro de una fase (y un paso) y una ruta afuera. Todas las acciones del flujo de trabajo deben estar contenidas en una fase. Las formas de fase se visualizan con formas de contenedor. Una forma Fase necesita que se agreguen una forma Entrada y Salida a los bordes del contenedor para definir las rutas adentro y afuera de la fase. Visio 2013 y el Diseñador visual en SharePoint Designer 2013 agregan las formas Entrada y Salida por usted cuando suelta por primera vez el contenedor.
  
    
    
Las fases también tienen las siguientes reglas:
  
    
    

- Todos los diagramas deben tener al menos una fase. Una fase, completa con formas Entrada, Salida e Iniciar están presentes como parte de la plantilla Flujo de trabajo de SharePoint 2013 predeterminada.
    
  
- Cuando agrega una nueva fase al lienzo de dibujo, Visio 2013 agrega conectores de Iniciar y Finalizar cuando se suelta la fase.
    
  
- Las fases no pueden tener ningún conector entrando o saliendo excepto a través de las formas Entrada y Salida.
    
  
- No es posible anidar los contenedores de fase. Si desea anidar otro subproceso dentro de una fase, use un paso.
    
  
- Las formas Detener flujo de trabajo pueden existir dentro de una fase.
    
  
- Se necesita una fase Iniciar explícita fuera de la fase para el diagrama completo. En cambio, no se necesita una forma Finalizar explícita fuera de la fase.
    
  
- En el nivel superior, el flujo de trabajo puede contener solo fases, formas condicionales y terminadores Iniciar y Finalizar. Todas las demás formas deben estar contendidas dentro de una fase.
    
  

### Formas de bucle

Los bucles son una serie de formas conectadas que se iniciarán como bucle, volviendo de la última forma de la serie a la primera, hasta que se satisfaga una condición. 
  
    
    
Al igual que las fases, los bucles se representan con una forma de contenedor que incluye una forma Entrar y Salir (agregada cuando se suelta la forma en el lienzo de dibujo). Una forma de Bucle también necesita que se agregue una forma Entrada y Salida a los bordes del contenedor para definir las rutas adentro y afuera del bucle.
  
    
    
Visio 2013 y SharePoint Designer 2013 admiten dos tipos de bucles: bucle  *n*  veces y bucle hasta que *valor1*  sea igual a *valor2*  .
  
    
    
Los bucles también deben respetar las siguientes reglas:
  
    
    

- Los bucles deben estar dentro de una fase, y las fases no pueden estar dentro de un bucle.
    
  
- Los pasos pueden estar dentro de un bucle.
    
  
- Los bucles pueden tener solo un punto de entrada y uno de salida.
    
  

### Formas de paso

Los pasos representan una serie agrupada de acciones en secuencia. Los pasos deben estar contenidos en una fase. Una forma de paso también debe tener una forma Entrada y Salida para definir las rutas adentro y afuera de la forma. Ambas formas se agregan de manera predeterminada cuando la forma se suelta en el lienzo.
  
    
    

## Creación de un flujo de trabajo en Visio 2013
<a name="VSSPD_Creating"> </a>

Todas las formas maestras de las galerías de símbolos de Flujo de trabajo de SharePoint 2013 corresponden a acciones, condiciones y otras construcciones lógicas dentro de un flujo de trabajo de SharePoint 2013. Para crear un flujo de trabajo, puede arrastrar formas sobre el lienzo de dibujo, al igual que cualquier otro diagrama de flujo en Visio. Después de finalizar con la creación del flujo de trabajo en Visio 2013, guarde el flujo de trabajo para que SharePoint Designer 2013 pueda abrirlo.
  
    
    
Para abrir la plantilla Flujo de trabajo de SharePoint 2013 en Visio 2013, haga lo siguiente:
  
    
    

### Para abrir la plantilla Flujo de trabajo de SharePoint 2013 en Visio 2013


1. Abra Visio 2013.
    
  
2. Elija **Nuevo**.
    
  
3. Dentro de **Categorías de plantillas**, elija **Diagrama de flujo**.
    
  
4. En **Elegir una plantilla**, elija **Flujo de trabajo de SharePoint 2013** y después elija **Crear**.
    
    Se abre la plantilla y el lienzo de dibujo ya aparece relleno con las formas Iniciar y Fase. La forma Fase contiene una forma Entrada y una Salida, unidas por un solo conector.
    
  
Con la plantilla Flujo de trabajo de SharePoint 2013 abierta, arrastre acciones, condiciones y otras formas en el lienzo de dibujo para diseñar un flujo de trabajo. Para más información sobre formas individuales y su significado, vea el artículo  [Formas en la plantilla de flujo de trabajo de SharePoint Server en Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md).
  
    
    

> **SUGERENCIA**
>  A la hora de diseñar un flujo de trabajo, recuerde las siguientes consideraciones adicionales:>  Para crear rápidamente un flujo de trabajo, arrastre las formas de acción y condición en el conector interno que está contenido en nuevas formas de fase. Visio 2013 divide automáticamente el conector en conectores adicionales, conservando el flujo de trabajo conectado desde la forma Entrada a la forma Salida.>  No use ninguna forma de una galería de símbolos que no sean las galerías de símbolos Acciones de flujo de trabajo de SharePoint 2013, Condiciones de flujo de trabajo de SharePoint 2013 y Terminadores de flujo de trabajo de SharePoint 2013. Use solo la herramienta Conector proporcionada por la plantilla Flujo de trabajo de SharePoint 2013 para agregar conexiones entre formas. Ninguna otra forma de conector es válida dentro de un flujo de trabajo de SharePoint 2013.>  Las formas de acción, los pasos y bucles siempre deben estar contenidos dentro de una forma Fase. Algunas formas condicionales pueden estar fuera de una fase.>  Una forma Fase debe tener exactamente una forma Entrada y una forma Salida. El subproceso de flujo de trabajo contenido dentro de la fase debe empezar con la forma Entrada y finalizar con la forma Salida.>  Una forma de condición debe tener dos conectores que salen de la forma, uno con la etiqueta "Sí" y el otro con la etiqueta "No". Puede hacer clic con el botón secundario en un conector para elegir **Sí** o **No**. >  Un flujo de trabajo debe tener solo una forma Iniciar. Esta forma debe estar fuera de una fase.>  Usted agrega texto a formas en el flujo de trabajo, pero el texto de la forma no afecta al flujo de trabajo.
  
    
    


  
    
    
Validar el flujo de trabajo en Visio 2013 es similar a validar cualquier otro diagrama conectado: Visio comprueba el diagrama contra un conjunto de reglas y devuelve una lista de errores que se encontraron en el diagrama. Vea el artículo  [Solución de problemas de errores de validación de flujo de trabajo de SharePoint Server en Visio](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md) para obtener información sobre la resolución de problemas de validación.
  
    
    

### Para validar un flujo de trabajo de SharePoint 2013 en Visio 2013


1. En la pestaña **Proceso**, en el grupo **Validación de diagramas**, elija **Comprobar diagrama**.
    
  
2. Si se encuentra algún error en el flujo de trabajo, se abre el panel **Problemas** debajo del diagrama. Elija cada elemento en la lista para seleccionar la forma en el diagrama que causó el error.
    
  
3. Resuelva cada uno de los errores de validación que se indican en la lista **Problemas**. Una vez que se hayan abordado todos los errores, elija nuevamente **Comprobar diagrama**. Para más información sobre la resolución de problemas de validación en Visio 2013, vea el artículo  [Solución de problemas de errores de validación de flujo de trabajo de SharePoint Server en Visio](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md).
    
  
4. Si no se encontró ningún error en el flujo de trabajo, Visio muestra un mensaje indicando que la validación de diagramas se completó sin que se encuentren problemas.
    
  
Una vez que el flujo de trabajo se valida correctamente en Visio 2013, puede guardar el archivo e importarlo en SharePoint Designer 2013. A diferencia de la plantilla Flujo de trabajo de Microsoft SharePoint 2010, puede guardar una copia del diagrama Flujo de trabajo de SharePoint 2013 como formato de archivo predeterminado (.vsdx) de Visio 2013 y SharePoint Designer 2013 puede abrir el archivo. 
  
    
    
Use el siguiente procedimiento para guardar un flujo de trabajo de SharePoint 2013 en Visio 2013 como un archivo .vsdx de Visio 2013 que puede abrirse en SharePoint Designer 2013:
  
    
    

### Para guardar un flujo de trabajo en Visio 2013


1. Elija **Archivo** y después haga clic en **Guardar como**.
    
  
2. Dentro de **Guardar como**, elija **Guardar** y después elija **Examinar**.
    
  
3. En el cuadro de diálogo **Guardar como**, seleccione una ubicación para guardar el archivo y escriba el nombre del archivo (" Mi flujo de trabajo de SP").
    
  
4. Elija **Guardar**.
    
  

## Personalización y publicación de un flujo de trabajo en SharePoint Designer 2013
<a name="VSSPD_Customizing"> </a>

Una vez que haya creado la lógica de negocios subyacente para un flujo de trabajo de SharePoint 2013 en Visio 2013 y guardado el diagrama, podrá abrir el archivo .vsdx de Visio en SharePoint Designer 2013 y empezar a personalizar el flujo de trabajo para su sitio de SharePoint 2013. El paquete de archivo .vsdx contiene documentos XML que SharePoint Designer 2013 puede traducir en flujos de trabajo.
  
    
    
Use el siguiente procedimiento para abrir un sitio de SharePoint 2013 en SharePoint Designer 2013:
  
    
    

### Para abrir un sitio de SharePoint 2013 en SharePoint Designer 2013


1. Abra SharePoint Designer 2013.
    
  
2. Dentro de **Abrir sitio de SharePoint**, elija **Abrir sitio**.
    
  
3. En el cuadro de diálogo **Abrir sitio**, seleccione el sitio que desea abrir.
    
  
4. Elija **Abrir**.
    
  
Una vez que se abre el sitio de SharePoint 2013, puede abrir el diagrama .vsdx de Visio 2013 dentro de SharePoint Designer 2013.
  
    
    

### Para abrir un flujo de trabajo Visio Professional 2013 en SharePoint Designer 2013


1. Elija **Archivo** y después elija **Agregar elemento**.
    
  
2. Para crear un Flujo de trabajo de lista, haga lo siguiente:
    
1. Dentro de **Flujos de trabajo**, elija **Flujo de trabajo de lista**.
    
  
2. En el panel de la izquierda dentro de **Flujo de trabajo de lista**, escriba el nombre del flujo de trabajo (Mi primer flujo de trabajo de SP2013) y seleccione la lista en el sitio donde desea publicar el flujo de trabajo.
    
  
3. En la lista **Elija la plataforma del flujo de trabajo para el nuevo flujo de trabajo**, seleccione **Flujo de trabajo de SharePoint 2013**.
    
  
4. Elija **Crear**.
    
  
3. Para crear un Flujo de trabajo de sitio, haga lo siguiente:
    
1. Dentro de **Flujos de trabajo**, elija **Flujo de trabajo de sitio**.
    
  
2. En el panel de la izquierda, dentro de **Flujo de trabajo de sitio**, escriba el nombre del flujo de trabajo (Mi primer flujo de trabajo de SP2013).
    
  
3. En la lista **Elija la plataforma del flujo de trabajo para el nuevo flujo de trabajo**, seleccione **Flujo de trabajo de SharePoint 2013**.
    
  
4. Elija **Crear**.
    
  
4. En la pestaña **Flujo de trabajo**, en el grupo **Administrar**, elija **Configuración de flujo de trabajo**.
    
  
5. En la pestaña **Configuración de flujo de trabajo**, en el grupo **Administrar**, elija **Importar desde Visio**.
    
  
6. En el cuadro de diálogo **Importar flujo de trabajo de dibujo de Visio**, vaya hasta la ubicación donde se encuentra el archivo .vsdx.
    
  
7. Seleccione el archivo que desee abrir (Mi flujo de trabajo de SP) y después elija **Abrir**.
    
  
Cuando abre un archivo .vsdx en SharePoint Designer 2013, el archivo se muestra en el Diseñador visual, un control ActiveX de Visio hospedado dentro de SharePoint Designer. El diagrama de Visio 2013 retiene todas las formas y el texto de forma que se creó en Visio. 
  
    
    

> **NOTA**
> Para cambiar entre el Diseñador visual y el Diseñador declarativo en SharePoint Designer 2013, en la pestaña **Flujo de trabajo** del grupo **Administrar**, elija **Vistas**. Este proceso puede tardar un momento, ya que SharePoint Designer 2013 valida el flujo de trabajo y después convierte la información del flujo de trabajo de un formato a otro. Durante este proceso, tendrá lugar otra validación de nivel de forma. Si se detecta algún error en el diagrama, se mostrará en un panel de error en la parte inferior del lienzo (igual que en Visio) 
  
    
    

Las formas que se muestran en el Diseñador visual también tienen Etiquetas de acción (indicadas con un icono de tipo configuración de flujo de trabajo que aparece en la parte inferior izquierda de la forma). Cuando elige una Etiqueta de acción, un menú desplegable muestra los atributos de esa acción o condición en el flujo de trabajo y propiedad **Propiedades**. Estas propiedades definirán los valores de parámetros que se usarán para esa acción: las listas de las que se extraerán los elementos, el operador de cálculo que se usará, o la dirección de correo electrónico a la que se enviará un mensaje. Cuando elige una propiedad que se muestra en la lista, aparece un cuadro de diálogo en el que puede personalizar la configuración de esa propiedad. 
  
    
    
Por ejemplo, la forma **Enviar un correo electrónico** tiene dos propiedades asociadas: **Crear correo electrónico** y **Propiedades**. Cuando elige **Crear correo electrónico**, aparece un cuadro de diálogo **Definir mensaje de correo electrónico** en el que puede crear el mensaje que la acción enviará. Si elige **Propiedades**, aparece un cuadro de diálogo **Enviar propiedades de un correo electrónico** que muestra todos los parámetros de esa acción.
  
    
    

> **NOTA**
> Para más información sobre acciones individuales, formas y sus propiedades, vea los artículos  [Formas en la plantilla de flujo de trabajo de SharePoint Server en Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md) y [Referencia rápida sobre acciones de flujo de trabajo (plataforma de flujo de trabajo de SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md). 
  
    
    

Una vez que establece las propiedades dentro del flujo de trabajo y está listo para la publicación, primero asegúrese de comprobar si hay errores en el flujo de trabajo de SharePoint Designer 2013. Cuando elige **Publicar** en la pestaña **Diseñador visual** de la cinta, SharePoint Designer 2013 comprueba automáticamente si hay errores en el flujo de trabajo. Si lo desea, también puede iniciar manualmente la comprobación de errores.
  
    
    
Use el siguiente procedimiento para comprobar el flujo de trabajo de SharePoint 2013 en SharePoint Designer 2013:
  
    
    

### Para comprobar manualmente si hay errores en un flujo de trabajo en SharePoint Designer 2013


1. En la pestaña **Diseñador visual** del grupo **Guardar**, elija **Buscar errores**.
    
  
2. Si se encuentra algún error en el flujo de trabajo, se abre el panel **Problemas** debajo del lienzo del Diseñador visual. Elija cada elemento en la lista para seleccionar la acción, la condición, el conector, el terminador o el contenedor del flujo de trabajo que causó el error.
    
  
3. Resuelva todos los errores de validación de la lista **Problemas**. Una vez que se hayan solucionado, elija nuevamente **Buscar errores**. 
    
  
4. Si no se encontró ningún error en el flujo de trabajo, SharePoint Designer muestra un mensaje que indica que no se encontraron problemas en el flujo de trabajo.
    
  
Una vez que el flujo de trabajo fue comprobado y no se encontraron problemas, puede publicar el flujo de trabajo en la lista de SharePoint. Para publicar el flujo de trabajo desde SharePoint Designer 2013, en la pestaña **Diseñador visual** del grupo **Guardar**, elija **Publicar**. Si hay errores durante el proceso de publicación, SharePoint Designer 2013 regresa al Diseñador visual y muestra los errores en el panel **Problemas**.
  
    
    

## Recursos adicionales
<a name="VSSPD_Additional"> </a>

Para más información, consulte los siguientes recursos:
  
    
    

-  [Referencia rápida sobre acciones de flujo de trabajo (plataforma de flujo de trabajo de SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Formas en la plantilla de flujo de trabajo de SharePoint Server en Visio](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)
    
  
-  [Solución de problemas de errores de validación de flujo de trabajo de SharePoint Server en Visio](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)
    
  
-  [Creación, importación y exportación de flujos de trabajo de SharePoint en Visio 2010](http://office.microsoft.com/en-us/HA101888007.aspx)
    
  
-  [Centro para desarrolladores de SharePoint](http://msdn.microsoft.com/es-es/sharepoint/default.aspx)
    
  
-  [Centro para desarrolladores de Visio](http://msdn.microsoft.com/es-es/office/aa905478)
    
  

