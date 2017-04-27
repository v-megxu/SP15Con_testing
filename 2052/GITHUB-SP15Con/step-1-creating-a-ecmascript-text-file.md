---
title: 步骤 1：创建 ECMAScript 文本文件
ms.prod: SHAREPOINT
ms.assetid: f1c2b359-5b0d-467d-a863-6732e23863b9
---


# 步骤 1：创建 ECMAScript 文本文件

在本演练中，您将创建 ECMAScript (JavaScript, JScript) 文本文件。本演练假定您熟悉 JavaScript 中的编码。 
  
    
    


### 创建 ECMAScript 文本文件


1. 创建一个文本文件，并将它命名为 JSOM_FeedToContentEditor.txt。
    
  
2. 将以下脚本添加到 JSOM_FeedToContentEditor.txt 文件中。
    
    **示例代码提供者：** Vidya Joshi，Microsoft Corporation
    


  ```
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
 <head>Logging results:
 </head>
<body>
<div id='resultdiv'></div>
<script type="text/javascript">         

// Set the page event handlers for onload and unload.
if (window.attachEvent) 
{
    window.attachEvent("onload", Page_Load);
} 
else 
{
// For some browsers window.attachEvent does not exist.
    window.addEventListener("DOMContentLoaded", Page_Load, false);
}

// Load the page. 
function Page_Load() 
{
    Ewa.EwaControl.add_applicationReady(GetEwa);
}

function GetEwa()
{
    om =Ewa.EwaControl.getInstances().getItem(0);
    writelog('DomId:' + om.getDomElement().id,0);

    om.add_activeCellChanged(cellchanged);
    om.add_activeSelectionChanged(selChanged);
    om.add_gridSynchronized(gridSynchronized);
    om.add_workbookChanged(wbchanged);
    om.add_enteredCellEditing(editing);
}

function cellchanged(rangeArgs)
{
    writelog('Address:'+ rangeArgs.getRange().getAddressA1(),1);
    writelog('Value:' + rangeArgs.getFormattedValues(),1);
    writelog('Cell changed event triggered',0);
}

function selChanged(rangeArgs)
{
    writelog('Address:'+ rangeArgs.getRange().getAddressA1(),1);
    writelog('Value:' + rangeArgs.getFormattedValues(),1);
    writelog('Selection changed event triggered',0);
}

function gridSynchronized(res)
{
    writelog('WorkbookPath:' +om.getActiveWorkbook().getWorkbookPath(),1);
    writelog('grid synchronized',0);
}

function wbchanged(r)
{
    writelog('Workbook changed event triggered',0);
}

function editing(rangeArgs)
{
    writelog('Address:'+ rangeArgs.getRange().getAddressA1(),1);
    writelog('Value:' + rangeArgs.getFormattedValues(),1);
    writelog('Entered cell editing event triggered',0);
}

function writelog(output, indentLevel)
{
    output = output + "<br/>";
    document.getElementById('resultdiv').innerHTML = output + document.getElementById('resultdiv').innerHTML ;
}
</script>  
</body>
</html><html> 

  ```

3. 保存该文本文件。
    
  

### 将文本文件保存到受信任的文档库


1. 将您在上一步中创建的文本文件上载到受信任的 SharePoint 文档库。 
    
  
2. 记录文本文件的 URL。例如：
    
     `http://` _myserver_ `/Docs/Documents/JSOM_FeedToContentEditor.txt`
    
    在下一步中，您将需要此 URL 以馈送到内容编辑器 Web 部件中。
    
  

