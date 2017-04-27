---
title: 手順 1 ECMAScript テキスト ファイルを作成する
ms.prod: OFFICE365
ms.assetid: f1c2b359-5b0d-467d-a863-6732e23863b9
---


# 手順 1: ECMAScript テキスト ファイルを作成する

このチュートリアルでは、ECMAScript (JavaScript, JScript) テキスト ファイルを作成します。このチュートリアルは、JavaScript のコーディングに習熟していることが前提です。 
  
    
    


### テキスト ファイル ECMAScript を作成するには


1. テキスト ファイルを作成して、JSOM_FeedToContentEditor.txt という名前を付けます。
    
  
2. ファイル JSOM_FeedToContentEditor.txt に次のスクリプトを追加します。
    
    **サンプル コードの提供者:** Vidya Joshi、Microsoft Corporation
    


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

3. テキスト ファイルを保存します。
    
  

### 信頼できるドキュメント ライブラリにテキスト ファイルを保存するには


1. 信頼できる SharePoint ドキュメント ライブラリに、前の手順で作成したテキスト ファイルをアップロードします。 
    
  
2. このテキスト ファイルへの URL をメモします。たとえば、次のようになります。
    
     `http://` _myserver_ `/Docs/Documents/JSOM_FeedToContentEditor.txt`
    
    次の手順で、コンテンツ エディターの Web パーツにこの URL を指定する必要があります。
    
  

