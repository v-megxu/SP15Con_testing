---
title: Complementos para SharePoint comparadas con las soluciones de SharePoint
ms.prod: SHAREPOINT
ms.assetid: 0e9efadb-aaf2-4c0d-afd5-d6cf25c4e7a8
---


# Complementos para SharePoint comparadas con las soluciones de SharePoint
Obtenga información sobre cuándo desarrollar su extensión de SharePoint 2013 como una Complemento de SharePoint y cuándo desarrollarla como una solución de granja de servidores SharePoint o un solución de espacio aislado sin código.
 * **Hace referencia a:*** 
  
    
    

Este artículo compara los casos de uso de Complementos de SharePoint, soluciones de granja de servidores y soluciones de espacio aislado sin código (NCSS).
- Las nuevas Complementos de SharePoint son extensiones independientes que pueden incluir lógica basada en la nube y datos, componentes de SharePoint y scripts de cliente, pero no código administrado personalizado que se ejecute en servidores SharePoint. Se instalan desde Tienda Office o un catálogo de complementos de la organización y se pueden instalar en conjuntos de servidores en el nivel local o en Microsoft SharePoint Online. Para obtener información general sobre Complementos de SharePoint, consulte  [Complementos de SharePoint](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx).
    
  
- SharePointsoluciones de granja de servidores son paquetes de componentes de SharePoint que se cargan en una galería de toda la granja de servidores desde donde se pueden instalar. No se pueden distribuir a través de la Tienda Office y no pueden instalarse en SharePoint Online. Pueden incluir código administrado personalizado que se ejecuta en la granja de servidores de SharePoint. Para obtener más información sobre los conceptos básicos de soluciones de granja de servidores, consulte  [Introducción a las soluciones](http://msdn.microsoft.com/library/1983cab9-4b29-494a-a62a-0f8e83908744%28Office.15%29.aspx) y [Soluciones de granja de servidores](http://msdn.microsoft.com/library/845f7524-b9ff-412b-aa29-3afacda91100%28Office.15%29.aspx).
    
  
- NCSS también son paquetes de componentes de SharePoint, pero se cargan en una galería de la colección de sitios desde donde se pueden instalar. Se pueden instalar en granjas de servidores locales o en SharePoint Online, pero no se pueden distribuir a través de Tienda Office. Pueden incluir prácticamente los mismos tipos de componentes descriptivos que Complementos de SharePoint y, al igual que los complementos, pueden tener JavaScript pero no código administrado personalizado que se ejecute en los servidores de SharePoint. Las diferencias en los sistemas de implementación de complementos y NCSS hacen de NCSS una mejor opción de desarrollo para una pequeña lista de escenarios. Para obtener información sobre soluciones de espacio aislado, consulte  [Soluciones de espacio aislado en SharePoint 2010](https://technet.microsoft.com/es-es/library/ee721992%28v=office.14%29.aspx).
    
  

> **IMPORTANTE**
> Aún se puede desarrollar soluciones de espacio aislado que solo contenga marcado declarativo y JavaScript, que llamamos soluciones de espacio aislado sin código (NCSS), aunque se dejó de usar el código administrado personalizado dentro de solución de espacio aislado. Se introdujo el nuevo modelo de complemento de SharePoint como sustitución en esos escenarios que requieren el uso de código administrado. El modelo de complemento se desvincula del producto principal de SharePoint en el tiempo de ejecución del complemento y esto permite mucha más flexibilidad y ofrece la capacidad para ejecutar el código en el entorno que prefiera. Sabemos que nuestros clientes hicieron inversiones en código soluciones de espacio aislado y se eliminará progresivamente de forma responsable. El código soluciones de espacio aislado existente seguirá funcionando en granjas de servidores de SharePoint locales en el futuro. Dada la naturaleza dinámica de los servicios en línea, se determinarán necesidades de asistencia técnica para el soluciones de espacio aislado codificado en SharePoint Online en función de la demanda de los clientes. Se sigue ofreciendo asistencia técnica de NCSS. Todas las inversiones futuras estarán destinadas a hacer un nuevo modelo de complementos de SharePoint más avanzado y eficaz. En consecuencia, se recomienda que los nuevos desarrollos usen el nuevo modelo de complemento siempre que sea posible. En escenarios donde se debe desarrollar una solución de granja de servidores o solución de espacio aislado codificada, se recomienda diseñarla para que pueda evolucionar rápidamente hacia un modelo de desarrollo más flexible. 
  
    
    


## Desarrollar un complemento siempre que sea posible
<a name="AppWhenYouCan"> </a>

El consejo más importante que podemos proporcionarle es que desarrolle una Complemento de SharePoint en lugar de una solución de granja de servidores o NCSS siempre que sea posible. Complementos de SharePoint tiene las siguientes ventajas sobre las soluciones clásicas:
  
    
    

- Proporciona a los usuarios el proceso de detección, compra e instalación más sencillo.
    
  
- Ofrece a los administradores las extensiones de SharePoint más seguras.
    
  
- Proporciona el sistema de venta y marketing más sencillo basado en un almacén de complementos en línea de Microsoft.
    
  
- Aumenta la flexibilidad en el desarrollo de actualizaciones futuras.
    
  
- Maximiza la capacidad de aprovechar las ventajas de las aptitudes de programación existentes sin SharePoint.
    
  
- Integra recursos basados en la nube de forma más flexible y más sencilla.
    
  
- Le permite tener permisos distintos de los permisos del usuario que ejecuta el complemento.
    
  
- Le permite usar estándares entre plataformas, como HTML, REST, OData, JavaScript y OAuth.
    
  
- Le permite aprovechar la biblioteca de JavaScript entre dominios SharePoint para tener acceso a datos de SharePoint. Como alternativa, puede usar un servicio de token seguro proporcionado por Microsoft, compatible con OAuth o usar certificados digitales para obtener autorización para datos de SharePoint.
    
  

## Diseñar complementos o NCSS para usuarios finales y diseñar soluciones de granja de servidores para administradores
<a name="SPAppVsClassic_Overview"> </a>

Complementos de SharePoint y NCSS usan uno de los modelos de objetos de cliente de SharePoint o extremos REST para tener acceso a contenido y componentes de SharePoint. Estos clientes de API permiten extensiones SharePoint que están diseñadas para usuarios finales. ("Usuarios finales", en este contexto, son los administradores de colecciones de sitios, los propietarios del sitio web y los miembros del sitio web). El modelo de objetos de servidor tiene API adicionales que permiten extensiones de programación de administración, configuración y seguridad de SharePoint. Incluyen extensiones de administración central, comandos personalizados de Windows PowerShell, trabajos del temporizador y copias de seguridad personalizadas. Para obtener más información sobre los tipos de extensiones administrativas que puede desarrollar, consulte  [Administración de Windows SharePoint Services](http://msdn.microsoft.com/library/cdcc1b8a-4144-446f-b471-03d4a754a8ab%28Office.15%29.aspx). Estas extensiones administrativas se implementan en características SharePoint que tienen una granja de servidores, una aplicación web o un ámbito de colecciones de sitios. Los administradores de la granja de servidores también instalan soluciones de granja de servidores de SharePoint, aunque el inquilino y los administradores de colecciones de sitios pueden instalar complementos y NCSS.
  
    
    
El modelo de objetos de servidor también tiene una API para crear, leer, actualizar y eliminar (CRUD) operaciones en listas, bibliotecas y sitios web, y para operaciones en otros componentes de SharePoint. Esto significa que el modelo de objetos de servidor se puede usar para extensiones que diseñadas para usuarios finales, pero, por los motivos indicados en la sección anterior, las soluciones de granja de servidores normalmente no son la mejor opción para dichas extensiones. Por lo tanto, no es ninguna sorpresa que soluciones de granja de servidores no se pueda instalar en Microsoft SharePoint Online. Ya que Microsoft controla toda la administración de SharePoint Online, no es necesario para extensiones administrativas. Para obtener más información sobre los diferentes conjuntos de API en SharePoint y dónde se superponen, consulte  [Elegir el conjunto de API correcto en SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    
Los modelos de objetos de cliente y los extremos REST no duplican las API administrativas del modelo de objetos de servidor. Además, ya que ni una Complemento de SharePoint ni un NCSS puede contener código personalizado que se ejecute en servidores de SharePoint, no pueden llamar a estas API administrativas. Además, todas las funciones de Complementos de SharePoint deben tener ámbito de sitio web y las características en NCSS tienen colecciones de sitios o ámbito de sitio web. Por lo tanto, una extensión de SharePoint administrativa no es realmente posible con una Complemento de SharePoint o NCSS. Por lo tanto, el segundo principio, pero no una regla absoluta, es que los complementos y NCSS son para los usuarios finales y las soluciones de granja de servidores son para administradores.
  
    
    

## Diseñar NCSS para extensiones de tipo plantilla y personalización de marcas
<a name="SPAppVsClassic_Overview"> </a>

Puede encontrar un pequeño número de escenarios de desarrollo de SharePoint para el que el modelo de complementos no es adecuado, pero en el que tampoco se puede implementar una solución de granja de servidores, quizás porque la solución deba ser instalable en SharePoint Online o tiene que poder instalarla un administrador de colecciones de sitios. De estos escenarios, existen dos grandes categorías que se superponen.
  
    
    

- **Personalización de marca:**SharePoint los usuarios, a menudo, quieren dar a sus sitos de SharePoint, e incluso a sus sitios de SharePoint Online, una apariencia personalizada con sus propios colores, estilos, diseños y logotipos. Generalmente, esto es más fácil de hacer con NCSS que con Complementos de SharePoint. Una Complemento de SharePoint tiene control mediante declaración sobre el aspecto únicamente de su propia web del complemento. Para la Web del host, mediante declaración solo se pueden agregar botones de la cinta y elementos del menú (y elementos del complemento). Otros cambios en una web de host o en su colección de sitios primaria, el arrendamiento, en el nivel local o en la aplicación web SharePoint deben realizarse con código o con un script que use uno de los modelos de objetos de cliente de SharePoint. Por ejemplo, los nuevos iconos o los archivos CSS tienen que implementarse mediante programación. Este código podría ejecutarse desde el propio complemento después de instalarlo o podría ejecutarse en el controlador de eventos de la instalación del complemento. Esto conllevaría una cantidad considerable de trabajo para crear este código. Además, el complemento necesitaría permisos de ámbito de la colección de sitios para cambiar cualquier sitio web fuera de su propia web del complemento y web del host, y necesitaría permisos de ámbito de inquilino para cambiar algo más que su colección de sitios primaria. Sin embargo, un NCSS de personalización de marca se puede implementar y activar en cualquier colección de sitios y podría consistir exclusivamente en solo unos pocos componentes declarativos. 
    
    > **NOTA**
      > Tenga en cuenta que las soluciones de granja de servidores de SharePoint son potencialmente más eficaces que cualquier NCSS o Complementos de SharePoint de personalización de marca, pero no son una opción en SharePoint Online. 
- **Extensiones "como plantilla":** supongamos que necesita crear una extensión de administración de SharePoint para el análisis de colaboración y la solución de crisis empresariales. La extensión incluye varios tipos de listas personalizados, flujos de trabajo sin código y otros componentes de SharePoint, todos combinados en una WebTemplate personalizada. Supongamos que empaqueta e implementa la extensión como un NCSS. Después de activar la característica de la solución, los usuarios pueden crear una subweb de administración de crisis de su sitio web de SharePoint siempre que se produzca una crisis. Puede rellenar el sitio web con datos específicos de la crisis. Por otro lado, podría implementar la misma extensión que Complemento de SharePoint con exactamente el mismo conjunto de componentes de SharePoint. Cuando se instala el complemento en el sitio del grupo, se crea inmediatamente la subred (conocida como la "web del complemento"). De nuevo, los usuarios rellenan el sitio web con los datos relevantes.
    
    Ahora, ¿qué sucede cuando se produce una segunda crisis? Si implementa la extensión como un NCSS, los usuarios pueden crear simplemente otro subweb desde su WebTemplate personalizada. Sin embargo, si implementa la extensión como un Complemento de SharePoint, los usuarios tienen un problema. No se puede instalar una segunda instancia del mismo complemento en su sitio web primario. En una web de host solo puede instalarse una instancia de un complemento. Lo mejor que puede hacer es crear un subsitio del sitio web primario que sirva como una ubicación a otra instancia del complemento para instalarse. Cuando se instala el complemento, se crea una nueva web del complemento, que es una subsubred del sitio web primario, para los componentes del complemento. Esta comparación muestra un principio general, pero no absoluto: las extensiones SharePointcon un carácter de "como plantilla", es decir, un conjunto reutilizable de componentes que se deben configurar para cada caso de uso específico, pero que naturalmente tienen varias instancias asociadas al mismo sitio web de SharePoint, que se ajusten mejor al modelo de desarrollo de NCSS que al modelo de complementos. En este ejemplo, el elemento variable es la crisis, pero es fácil imaginar extensiones SharePoint como plantilla en el que las instancias varían por región, fecha o cualquier número de características.
    
  
Para obtener información sobre cómo ampliar las posibilidades de Complementos de SharePoint, consulte  [Usar controladores de eventos de complemento con cuidado](#AppEventHandlers) y [Complementos que crean extensiones](#ExtensionFactories).
  
    
    

## Hacer cosas como lo haría un complemento
<a name="Questions"> </a>

Como se ha mencionado anteriormente, el código personalizado que se ejecuta en los servidores de SharePoint no se permiten en Complementos de SharePoint. Esto  *no*  es una limitación importante. Simplemente significa que la lógica empresarial personalizada "baja" al dispositivo cliente o "sube" a la nube. En cualquier caso, puede usar el [servicio REST/OData de SharePoint](http://msdn.microsoft.com/library/f60ed19e-9840-4f39-911e-4676751a2f6b%28Office.15%29.aspx) para tener acceso a sitios, listas y otros datos de SharePoint. Puede tener acceso de forma remota a datos de SharePoint a través de [modelos de objetos de cliente de.NET Framework, Silverlight o JavaScript de SharePoint](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Por último, en Windows Phone, puede tener acceso a SharePoint a través del modelo de objetos de SharePointWindows Phone. Para obtener más información sobre los distintos conjuntos de API en SharePoint 2013, consulte  [Elegir el conjunto de API correcto en SharePoint 2013](choose-the-right-api-set-in-sharepoint-2013.md).
  
    
    
Un punto similar es que las características de Complementos de SharePoint no pueden tener colecciones de sitios, aplicación de web o ámbito de granja de servidores. Sin embargo, no tiene que ceder a los elementos de la interfaz de usuario o la funcionalidad. Esto significa que la implementación del componente sale de SharePoint a un cliente o una aplicación web remota o una base de datos remota.
  
    
    
En la siguiente tabla se enumeran los componentes de SharePoint que no se pueden implementar en una Complemento de SharePoint y describe la "forma en que un complemento" obtiene la misma funcionalidad.
  
    
    


|**Si quiere la funcionalidad de...**|**... pruebe estos enfoques.**|
|:-----|:-----|
|Elementos web personalizados  <br/> |Una Complemento de SharePoint puede tener páginas remotas que contienen elementos web personalizados. Otra opción es mostrar una página de una aplicación web remota en un elemento del complemento en una página del sitio de SharePoint. La página remota puede tener básicamente los mismos controles de interfaz de usuario y la misma funcionalidad que un elemento web. Para obtener más información, consulte  [Crear elementos del complemento para instalar con el complemento para SharePoint](http://msdn.microsoft.com/library/a2664289-6c56-4cb1-987a-22367fad55eb%28Office.15%29.aspx).  <br/> |
|Receptores de eventos y receptores de características  <br/> |Una Complemento de SharePoint puede contener receptores de eventos remotos funcionalmente equivalentes. Para obtener más información, consulte  [Controlar eventos en los complementos de SharePoint](http://msdn.microsoft.com/library/c050d056-8548-4496-a053-016779d723d9%28Office.15%29.aspx).  <br/> |
|Tipos de campo personalizados (columna)  <br/> |Un complemento puede implementar un nuevo campo (columna) basado en uno de los  [tipos de campo existentes](http://msdn.microsoft.com/es-es/library/microsoft.sharepoint.spfieldtype.aspx%28Office.15%29.aspx). Los tipos de campo  [calculado](http://msdn.microsoft.com/library/8703373d-bb55-4132-8c5f-37a41c383f81%28Office.15%29.aspx) y [procesado](http://msdn.microsoft.com/es-es/library/microsoft.sharepoint.spfieldcomputed.aspx%28Office.15%29.aspx) son especialmente flexibles. Otra opción es presentar los datos en una página web remota con controles personalizados o cuadrículas. <br/> |
|Servicios web personalizados creados en SharePoint  [Service Application Framework](http://msdn.microsoft.com/library/6d0300d2-5b5c-4477-a9e2-17594aea5a7d%28Office.15%29.aspx) <br/> |Puede desarrollar sus servicios web personalizados como servicios remotos.  <br/> |
|Páginas de aplicación  <br/> |Una Complemento de SharePoint puede incluir páginas remotas que están disponibles en cada sitio web en el que está instalado el complemento. Un complemento también puede usar cualquiera de los elementos web de SharePoint integrados en páginas del sitio.  <br/> |
   
Algunos componentes de SharePoint, que se enumeran a continuación, se usan en escenarios de usuario final, pero no tienen equivalente en el modelo de complementos de SharePoint y no se pueden implementar en NCSS. En estos casos, debe usar soluciones de granja de servidores.
  
    
    

- **Definiciones de sitios personalizadas**, pero las WebTemplates personalizadas, que son funcionalmente similares a las definiciones de sitio, están disponibles en NCSS y en Complementos de SharePoint. Para obtener más información, consulte  [Trabajar con plantillas y definiciones](http://msdn.microsoft.com/library/1edf6d4d-eddb-4cb5-9034-ed394e8a3e01%28Office.15%29.aspx).
    
  
- **Delegar controles**. Para obtener más información, consulte  [Control delegado (creación de plantillas de control)](http://msdn.microsoft.com/library/e979328d-4985-4ed6-9085-7ff32a998dfc%28Office.15%29.aspx).
    
  
- **Temas personalizados**
    
  
- **Grupos de acción personalizados y ocultación de acción personalizada**
    
  
- **Controles de usuario (archivos .ascx)**. Realmente ningún escenario los requiere.
    
  

### Usar controladores de eventos de complemento con cuidado
<a name="AppEventHandlers"> </a>

Puede solucionar algunas de las limitaciones de Complementos de SharePoint mediante la creación de controladores de eventos de complemento instalado, complemento actualizado y desinstalación del complemento. Estos controladores son servicios web que se hospedan en servidores web fuera de la granja de servidores de SharePoint, posiblemente en la nube. Pueden usar el modelo de objetos de cliente de SharePoint o las API de REST, para realizar operaciones CRUD en componentes de SharePoint, incluidos componentes en la Web del host. En teoría, podría usar tales controladores para solucionar algunas restricciones de implementación en elementos de **personalización de marca** y **extensiones de tipo plantilla**, como se explicó anteriormente. Sin embargo, se recomienda usar estos controladores solo como último recurso, cuando no exista ninguna otra manera de proporcionar a los clientes la funcionalidad que requiere el caso de uso. Al decidir si va a crear un controlador, tenga en cuenta lo siguiente:
  
    
    

- La implementación mediante programación en la Web del host requiere que el complemento solicite el permiso Control total a la Web del host. No se pueden vender complementos que requieran este nivel de permisos a través de la Tienda Office.
    
  
- La implementación de componentes en el sitio web del host tiende a reducir las ventajas de seguridad de poner componentes de SharePoint en una web del complemento con su propio dominio.
    
  
- El código de implementación exhaustivo necesita una gran cantidad de trabajo para crear y depurar en comparación con el marcado de implementación descriptivo que se puede usar para los componentes de la web del complemento y en NCSS.
    
  
- Hay algunas prácticas recomendadas que se deben seguir en la creación de controladores de eventos de complemento. El código debe incluir lógica de reversión para deshacer todo que lo hizo si encuentra un error. También debe alertar sobre la infraestructura de SharePoint del error, para que la infraestructura pueda deshacer todo lo que hizo.
    
  
- Los controladores de eventos de complemento no son posibles con el tipo de Complemento de SharePoint conocido como hospedado en SharePoint.
    
  
Para obtener más información sobre los controladores de eventos de complemento, consulte el nodo de SDK  [Controlar eventos en los complementos de SharePoint](http://msdn.microsoft.com/library/c050d056-8548-4496-a053-016779d723d9%28Office.15%29.aspx). Para obtener información sobre la lógica de reversión, consulte la sección **Agregar lógica de reversión al controlador** del tema [Crear un controlador para el evento de actualización en complementos de SharePoint](http://msdn.microsoft.com/library/0fa088c5-54c6-482c-84ed-51c4f77c4127%28Office.15%29.aspx) El último tema está escrito en el contexto del evento de complemento actualizado, pero los principios básicos se aplican a todos los controladores de eventos de complemento.
  
    
    

### Complementos que crean extensiones
<a name="ExtensionFactories"> </a>

Otra forma de usar el modelo de objetos de cliente de SharePoint, o su API de REST, para resolver los problemas de implementación del componente con Complementos de SharePoint, es introducir el código CRUD en el complemento, en lugar de en un controlador de eventos de complemento. El complemento se convierte en un tipo de fábrica para un tipo de extensión personalizada. Por ejemplo, un complemento hospedado en SharePoint podría usar el modelo de objetos de SharePointJavaScript para realizar la implementación y otras operaciones de CRUD en la Web de host o en otro lugar en el arrendamiento o en la Web de la aplicación. Para ver otro ejemplo, consulte la sección **Introducción rápida al aprovisionamiento remoto** de [Técnicas de aprovisionamiento del sitio y aprovisionamiento remoto en SharePoint 2013](http://blogs.msdn.com/b/vesku/archive/2013/08/23/site-provisioning-techniques-and-remote-provisioning-in-sharepoint-2013.aspx), que describe cómo se usa una Complemento de SharePoint hospedada por el proveedor para proporcionar una subweb realiza el aprovisionamiento de subweb predefinido del tipo SharePoint. Sin embargo, hay mucha reinvención de la rueda y, por lo tanto, una gran cantidad de trabajo de creación de una Complemento de SharePoint de fábrica. Además, este tipo de complemento no se puede vender a través de la Tienda Office porque el complemento requiere Control total de la web del host.
  
    
    

## Recursos adicionales
<a name="bk_addresources"> </a>


-  [Modelos de programación en SharePoint 2013](programming-models-in-sharepoint-2013.md)
    
  
-  [Uso de soluciones](http://msdn.microsoft.com/library/0da0518c-24eb-48e0-89bd-21282fdeef94%28Office.15%29.aspx)
    
  

