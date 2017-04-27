---
title: Arbeiten mit dem Objektmodell von Excel Services JavaScript
ms.prod: SHAREPOINT
ms.assetid: 06219071-a7c1-4f54-b07f-7b7001592330
---


# Arbeiten mit dem Objektmodell von Excel Services JavaScript

Wenn Sie Code, die das JavaScript-Objektmodell (JSOM) verwendet schreiben, es gibt zwei Szenarien, in denen der Code ausgeführt werden kann: auf einer Seite SharePoint 2013; oder auf einer Hostwebseite enthält, die eine eingebettete -Arbeitsmappe, die auf Microsoft OneDrive gespeichert ist. In diesem Artikel werden den Hauptunterschied zwischen den beiden Szenarien, die erheblich beeinträchtigen, wie Sie Code schreiben.
  
    
    


## Mithilfe der Excel Services-JSOM

Tabelle 1 sind die Unterschiede zwischen den beiden Szenarien zur Verfügung, wenn Sie Code schreiben, die die JSOM verwendet.
  
    
    

**In Tabelle 1. Szenarien für Excel Services JSOM**


|**Ort**|**Beschreibung**|
|:-----|:-----|
|**OneDrive** <br/> |In diesem Szenario betten Sie eine Arbeitsmappe, die in der Hostwebseite mithilfe des Elements HTML < Div > auf OneDrive gespeichert ist. Klicken Sie dann fügen Sie Code in die Seite, die die eingebettete Arbeitsmappe interagiert. <br/> |
|**SharePoint** <br/> |In diesem Szenario müssen Sie eine SharePoint-Seite von SharePoint 2013 verarbeitet. Sie fügen ein -Webpart in der SharePoint-Seite, die eine Arbeitsmappe enthält, die in einem vertrauenswürdigen Speicherort gespeichert ist. Klicken Sie dann fügen Sie Code in der SharePoint-Seite, die mit der -Webpart interagiert. <br/> |
   
Der Hauptunterschied zwischen dem Schreiben von Code für die zwei Szenarien ist, wie Sie einen Verweis auf das  [Ewa.EwaControl](http://msdn.microsoft.com/library/6e441406-d67a-0da9-f996-71f4e4b4c144%28Office.15%29.aspx) -Objekt abrufen. Da die **[Ewa.EwaControl]** den Einstiegspunkt für das JavaScript-Objektmodell ist, müssen Sie einen Verweis auf die Arbeit mit der JSOM möchten.
  
    
    

### Abrufen eines Verweises auf das Objekt EwaControl (SharePoint)

Beim Schreiben von Code, der mit einer -Webpart auf einer SharePoint-Seite interagiert, erhalten Sie einen Verweis auf das **[Ewa.EwaControl]** -Objekt mithilfe der Methode [Ewa.EwaControlCollection.getItem(index)](http://msdn.microsoft.com/library/11dd3a65-f914-4b34-bbaf-0206c8153d2b%28Office.15%29.aspx), wie im folgenden Codebeispiel dargestellt.
  
    
    

```

<script type="text/javascript">
var ewa = null;

// Add event handler for onload event.
if (window.attachEvent) 
{ 
    window.attachEvent("onload", ewaOmPageLoad);    
} 
else 
{ 
    window.addEventListener("DOMContentLoaded", ewaOmPageLoad, false); 
}
// Add event handler for applicationReady event.
function ewaOnPageLoad()
{
    if (typeof (Ewa) != "undefined")
    {
Ewa.EwaControl.add_applicationReady(ewaApplicationReady);
    }
    else
    {
alert("Error - the EWA is not loaded.");
    }
    // Add additional page load code here.
}

function ewaApplicationReady()
{
    // Get a reference to the Excel Services Web Part.
    ewa = Ewa.EwaControl.getInstances().getItem(0);

    // Add other initialization logic here.
}

// Add your code here.
    </script>
```


### Abrufen eines Verweises auf das Objekt EwaControl (OneDrive )

Wenn Sie Code schreiben, der mit einer eingebetteten Arbeitsmappe interagiert, die auf OneDrive gespeichert ist, erhalten Sie einen Verweis auf das Objekt **[Ewa.EwaControl]** über [AsyncResult](http://msdn.microsoft.com/library/1da51396-834c-d85b-a9b0-ce21e4329946%28Office.15%29.aspx) -Objekts. Das **[AsyncResult]** -Objekt wird als einzelnen Parameter an die Rückrufmethode übergeben, die Sie in der statischen [Ewa.EwaControl.loadEwaAsync](http://msdn.microsoft.com/library/a7ee4d6d-5472-b942-c78e-b368d30bcb0e%28Office.15%29.aspx) -Methode angeben. Wenn der Rückruf aufgerufen wird, ist ein Verweis auf das Objekt **[Ewa.EwaControl]** im **[AsyncResult]** -Objekt enthalten. Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen Verweis auf das Objekt **[Ewa.EwaControl]** über das **[AsyncResult]** -Objekt abrufen.
  
    
    

```

<div id="myExcelDiv" style="width: 402px; height: 346px"></div>
<script type="text/javascript" src="http://r.office.microsoft.com/r/rlidExcelWLJS?v=1&amp;kip=1"></script>
<script type="text/javascript">
    /*
    * This code uses the Microsoft Office Excel JavaScript object model to programmatically insert the
    * Excel Web App into a div with id=myExcelDiv. The full API is documented at
    * http://msdn.microsoft.com/en-us/library/hh315812.aspx. There you can find out how to programmatically get
    * values from your Excel file and how to use the rest of the object model. 
    */

    // Use this file token to reference Book1.xlsx in the Excel APIs
    // Replace the the placeholder for the  filetoken with your value
    var fileToken = " XXXXXXXXXXXXXXXXXXXXXX/XXXXXXXXXXXXXXXXXXX/";
    var ewa = null;

    // Run the Excel load handler on page load.
    if (window.attachEvent)
    {
        window.attachEvent("onload", loadEwaOnPageLoad);
    } else
    {
        window.addEventListener("DOMContentLoaded", loadEwaOnPageLoad, false);
    }

    function loadEwaOnPageLoad()
    {
        var props = {
            uiOptions: {
                showGridlines: false,
                showRowColumnHeaders: false,
                showParametersTaskPane: false
            },
            interactivityOptions: {
                allowTypingAndFormulaEntry: false,
                allowParameterModification: false,
                allowSorting: false,
                allowFiltering: false,
                allowPivotTableInteractivity: false
            }
        };
        // Embed workbook using loadEwaAsync
        Ewa.EwaControl.loadEwaAsync(fileToken, "myExcelDiv", props, onEwaLoaded);
    }

    function onEwaLoaded(asyncResult)
    { 
        if (asyncResult.getSucceeded())
        {
            // Use the AsyncResult.getEwaControl() method to get a reference to the EwaControl object
            ewa = asyncResult.getEwaControl();
            …
        }
        else
        {
            alert("Async operation failed!");
        }
        // ...
    }    
</script>
```


### Schlussbemerkung

Schreiben eine Lösung, die das JavaScript-Objektmodell verwendet ist im Grunde gleich, ob die Lösung auf SharePoint 2013 oder auf einer Hostwebseite ausgeführt wird. Der Hauptunterschied ist, wie Sie einen Verweis auf das **[Ewa.EwaControl]** -Objekt abrufen. Nachdem Sie einen Verweis auf das Objekt **[Ewa.EwaControl]** haben, werden der Rest des Codes, den Sie schreiben nahezu identisch für beide Szenarien.
  
    
    

## Zusätzliche Ressourcen
<a name="SP15DevKitchenCon_AnatomyofanappSignupsheets_Additionalresources"> </a>


-  [Verwenden der Excel Services-JavaScript-API zum Arbeiten mit eingebetteten Excel-Arbeitsmappen](http://msdn.microsoft.com/en-us/library/hh315812.aspx)
    
  
-  [Ewa.EwaControl.loadEwaAsync](http://msdn.microsoft.com/library/a7ee4d6d-5472-b942-c78e-b368d30bcb0e%28Office.15%29.aspx)
    
  
-  [Ewa.EwaControlCollection.getItem(index)](http://msdn.microsoft.com/library/11dd3a65-f914-4b34-bbaf-0206c8153d2b%28Office.15%29.aspx)
    
  

