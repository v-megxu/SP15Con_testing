---
title: Procedimiento para habilitar las UDF
keywords: how to,howdoi,howto,UDF list
f1_keywords:
- how to,howdoi,howto,UDF list
ms.prod: SHAREPOINT
ms.assetid: 8c1af2eb-bb22-45e1-82de-a2b4b53d7a26
---


# Procedimiento para habilitar las UDF

Cada ubicación de confianza de Servicios de Excel en el proveedor de servicios compartidos (SSP) tiene una marca **AllowUdfs**. 
  
    
    


> **NOTA**
> La marca **AllowUdfs** se indica mediante la opción **Funciones definidas por el usuario permitidas** de la página de ubicación de archivos de confianza de Excel Services.
  
    
    


El valor predeterminado de **AllowUdfs** es **false**. Si el valor de **AllowUdfs** está establecido en **false** en una ubicación de confianza determinada, los libros de esa ubicación de confianza no tienen permiso para llamar a las UDF.
  
    
    

Para permitir llamadas a las UDF desde una ubicación de confianza determinada, establezca el valor **AllowUdfs** en **true**.Si el valor **AllowUdfs** es **false** cuando se inicia una sesión en un libro que tiene llamadas a UDF en esta ubicación de confianza, se producirá un error en las llamadas a las UDF. Si cambia el valor **AllowUdfs** a **true** después de iniciar la sesión, también se producirá un error en las llamadas a las UDF. Esto se debe a que los cambios en el identificador **AllowUdfs** surtirán efecto en la siguiente sesión, tras la actualización de la base de datos de configuración.Esto se puede solucionar si reinicia la sesión, por ejemplo, seleccionando **Volver a cargar el libro** en Excel Web Access.
> **PRECAUCIóN**
> Si elige restablecer Microsoft Internet Information Services (IIS) en su lugar, se finalizarán todas las sesiones actuales. 
  
    
    


## Habilitar las UDF

Para realizar los pasos siguientes, necesita un equipo con Microsoft SharePoint Server 2010 instalado.
  
    
    

### Para habilitar las UDF


1. En el menú **Inicio**, haga clic en **Todos los programas**. 
    
  
2. Elija **Microsoft Office Server** y haga clic en **Administración central de SharePoint**. 
    
  
3. En Inicio rápido, haga clic en el vínculo del Proveedor de servicios compartidos (SSP), por ejemplo, "ServiciosCompartidos1", para ver la página inicial Servicios compartidos de ese SSP en particular.
    
  
4. Bajo **Configuración de Excel Services**, haga clic en **Funciones definidas por el usuario**. 
    
  
5. En la página Funciones definidas por el usuario de Excel Services, haga clic en **Agregar función definida por el usuario** para abrir la página Ensamblado de funciones definidas por el usuario de Excel Services.
    
  
6. En el cuadro **Ensamblado**, escriba la ruta de acceso al ensamblado del archivo UDF. Por ejemplo, C:\\MyUdfFolder\\MyUdf.dll.
    
  
7. Bajo **Ubicación del ensamblado**, haga clic en **Archivo local**.
    
    > **NOTA**
      > La opción **Archivo local** se reemplazará por **Ruta del archivo** en futuras versiones de Servicios de Excel. Si ve **Ruta del archivo**, selecciónela en su lugar. 
8. Debajo de **Habilitar ensamblado**, la casilla **Ensamblado habilitado** debe estar seleccionada de forma predeterminada.
    
  
9. Haga clic en **Aceptar**.
    
  

## Permitir llamadas a las UDF


### Para permitir llamadas a las UDF desde un libro


1. Abra la página para agregar ubicaciones de archivos de confianza de Excel Services (si va a agregar una nueva ubicación de confianza) o la página de edición de ubicación de archivos de confianza de Excel Services (si va a editar una ubicación de confianza existente). 
    
    > **NOTA**
      > Para obtener más información acerca de cómo convertir una ubicación en ubicación de confianza, consulte  [How to: Trust a Location](how-to-trust-a-location.md). 
2. Debajo de **Permitir funciones definidas por el usuario**, seleccione **Funciones definidas por el usuario permitidas** para permitir que se pueda llamar a las UDF desde los libros almacenados en esta ubicación de confianza.
    
  
3. Haga clic en **Aceptar**.
    
  

## Vea también


#### Tareas


  
    
    
 [Step 3: Deploying and Enabling UDFs](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [How to: Create a UDF That Calls a Web Service](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [How to: Trust a Location](how-to-trust-a-location.md)
#### Conceptos


  
    
    
 [Walkthrough: Developing a Managed-Code UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Frequently Asked Questions About Excel Services UDFs](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [Understanding Excel Services UDFs](understanding-excel-services-udfs.md)
  
    
    
 [Excel Services Alerts](excel-services-alerts.md)
  
    
    
 [Excel Services Known Issues and Tips](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services Best Practices](excel-services-best-practices.md)
