---
title: 使用 Excel Services JavaScript 对象模型
ms.prod: SHAREPOINT
ms.assetid: 06219071-a7c1-4f54-b07f-7b7001592330
---


# 使用 Excel Services JavaScript 对象模型

在编写使用 JavaScript 对象模型 (JSOM) 的代码时，可采用以下两种方案：即，您的代码可以运行在 SharePoint 2013 页面上；或者运行在包含嵌入式 工作簿（存储在 Microsoft OneDrive 中）的主机网页上。本文讨论这两种显著影响您的代码编写方式的方案之间的主要不同之处。
  
    
    


## 使用 Excel Services JSOM

表 1 列出了在编写使用 JSOM 的代码时可采用的两种方案之间的不同之处。
  
    
    

**表 1. Excel Services JSOM 方案**


|**位置**|**说明**|
|:-----|:-----|
|**OneDrive** <br/> |在该方案中，可使用 HTML <div> 元素将存储在 OneDrive 中的工作簿嵌入主机网页中。然后，您可以在该页面中包括与该嵌入式工作簿交互的代码。  <br/> |
|**SharePoint** <br/> |在该方案中，您具有一个由 SharePoint 2013 提供服务的 SharePoint 页面。您可以将一个包含存储在 受信任位置的工作簿的 Web 部件插入该 SharePoint 页面中。然后，您可以在该 SharePoint 页面中包含与此 Web 部件交互的代码。  <br/> |
   
针对这两种方案编写代码的主要不同之处在于，您如何获取对  [Ewa.EwaControl](http://msdn.microsoft.com/library/6e441406-d67a-0da9-f996-71f4e4b4c144%28Office.15%29.aspx) 对象的引用。因为 **[Ewa.EwaControl]** 是访问 JavaScript 对象模型的入口点，所以您必须获取其引用方式，然后才能使用 JSOM。
  
    
    

### 获取对 EwaControl 对象 (SharePoint) 的引用

在编写可与 SharePoint 页面中的 Web 部件交互的代码时，您使用  [Ewa.EwaControlCollection.getItem(index)](http://msdn.microsoft.com/library/11dd3a65-f914-4b34-bbaf-0206c8153d2b%28Office.15%29.aspx) 方法获取对 **[Ewa.EwaControl]** 对象的引用，如以下代码示例所示。
  
    
    

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


### 获取对 EwaControl 对象 (OneDrive) 的引用

在编写可与存储在 OneDrive 中的嵌入式工作簿交互的代码时，您通过  [AsyncResult](http://msdn.microsoft.com/library/1da51396-834c-d85b-a9b0-ce21e4329946%28Office.15%29.aspx) 对象获取对 **[Ewa.EwaControl]** 对象的引用。 **[AsyncResult]** 对象作为单独参数传递给您在 [Ewa.EwaControl.loadEwaAsync](http://msdn.microsoft.com/library/a7ee4d6d-5472-b942-c78e-b368d30bcb0e%28Office.15%29.aspx) 静态方法中指定的回调方法。在调用该回调时，对 **[Ewa.EwaControl]** 对象的引用包括在 **[AsyncResult]** 对象中。下面的代码示例演示如何通过 **[AsyncResult]** 对象获取对 **[Ewa.EwaControl]** 对象的引用。
  
    
    

```

<div id="myExcelDiv" style="width: 402px; height: 346px"></div>
<script type="text/javascript" src="http://r.office.microsoft.com/r/rlidExcelWLJS?v=1&amp;kip=1"></script>
<script type="text/javascript">
    /*
    * This code uses the Microsoft Office Excel JavaScript object model to programmatically insert the
    * Excel Web App into a div with id=myExcelDiv. The full API is documented at
    * http://msdn.microsoft.com/zh-cn/library/hh315812.aspx. There you can find out how to programmatically get
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


### 结论

无论使用 JavaScript 对象模型的解决方案运行在 SharePoint 2013 上，还是运行在主机网页上，编写该解决方案的方法基本上相同。主要不同之处在于您如何获取对 **[Ewa.EwaControl]** 对象的引用。在获取对 **[Ewa.EwaControl]** 对象的引用后，要编写的代码的其余部分对于这两种方案来说几乎是相同的。
  
    
    

## 其他资源
<a name="SP15DevKitchenCon_AnatomyofanappSignupsheets_Additionalresources"> </a>


-  [使用 Excel Services JavaScript API 来处理嵌入的 Excel 工作簿](http://msdn.microsoft.com/zh-cn/library/hh315812.aspx)
    
  
-  [Ewa.EwaControl.loadEwaAsync](http://msdn.microsoft.com/library/a7ee4d6d-5472-b942-c78e-b368d30bcb0e%28Office.15%29.aspx)
    
  
-  [Ewa.EwaControlCollection.getItem(index)](http://msdn.microsoft.com/library/11dd3a65-f914-4b34-bbaf-0206c8153d2b%28Office.15%29.aspx)
    
  

