---
title: Excel Services JavaScript オブジェクト モデルを操作する
ms.prod: SHAREPOINT
ms.assetid: 06219071-a7c1-4f54-b07f-7b7001592330
---


# Excel Services JavaScript オブジェクト モデルを操作する

 の JavaScript オブジェクト モデル (JSOM) を使用するコードを記述する場合、コードを実行できるシナリオは 2 つあります。1 つは SharePoint 2013 のページ上です。もう 1 つは、Microsoft OneDrive 上に格納された ブックを埋め込んだホスト Web ページ上です。この記事では、コードの記述方法に大きな影響を及ぼす、2 つのシナリオの主な違いについて説明します。
  
    
    


## Excel Services JSOM を使用する

表 1 では、 JSOM を使用するコードを記述するときに利用できる 2 つのシナリオの違いを一覧にしています。
  
    
    

**表 1. Excel Services JSOM のシナリオ**


|**場所**|**説明**|
|:-----|:-----|
|**OneDrive** <br/> |このシナリオでは、OneDrive上に保存されているブックを、HTML <div> 要素を使用してホスト Web ページに埋め込みます。その後、埋め込んだブックを操作するコードをページに含めます。  <br/> |
|**SharePoint** <br/> |このシナリオでは、SharePoint 2013 によって SharePoin ページが提供されます。 の信頼できる場所に格納されたブックを含む SharePoint ページに、 Web パーツを挿入します。その後、 Web パーツを操作する SharePoint ページに、コードを含めます。  <br/> |
   
2 つのシナリオで記述するコードの主な違いは、 [Ewa.EwaControl](http://msdn.microsoft.com/library/6e441406-d67a-0da9-f996-71f4e4b4c144%28Office.15%29.aspx) オブジェクトへの参照を取得する方法です。 **[Ewa.EwaControl]** は JavaScript オブジェクト モデルへのエントリ ポイントなので、Ewa.EwaControl への参照を取得して、 JSOM を操作する必要があります。
  
    
    

### EwaControl オブジェクトへの参照を取得する (SharePoint)

SharePoint ページ上で Web パーツを操作するコードを記述する場合、次のコード例に示すように、 [Ewa.EwaControlCollection.getItem(index)](http://msdn.microsoft.com/library/11dd3a65-f914-4b34-bbaf-0206c8153d2b%28Office.15%29.aspx) メソッドを使用して、 **[Ewa.EwaControl]** オブジェクトへの参照を取得します。
  
    
    

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


### EwaControl オブジェクトへの参照を取得する (OneDrive)

OneDrive 上に保存された埋め込みブックを操作するコードを記述する場合、 [AsyncResult](http://msdn.microsoft.com/library/1da51396-834c-d85b-a9b0-ce21e4329946%28Office.15%29.aspx) オブジェクトを使って **[Ewa.EwaControl]** オブジェクトへの参照を取得します。 **[AsyncResult]** オブジェクトは、 [Ewa.EwaControl.loadEwaAsync](http://msdn.microsoft.com/library/a7ee4d6d-5472-b942-c78e-b368d30bcb0e%28Office.15%29.aspx) 静的メソッドで指定するコールバック メソッドへの単一パラメーターとして渡します。コールバックが起動されると、 **[Ewa.EwaControl]** オブジェクトへの参照が **[AsyncResult]** オブジェクトに入ります。以下のコード例は、 **[AsyncResult]** オブジェクトを使って **[Ewa.EwaControl]** オブジェクトへの参照を取得する方法を示しています。
  
    
    

```

<div id="myExcelDiv" style="width: 402px; height: 346px"></div>
<script type="text/javascript" src="http://r.office.microsoft.com/r/rlidExcelWLJS?v=1&amp;kip=1"></script>
<script type="text/javascript">
    /*
    * This code uses the Microsoft Office Excel JavaScript object model to programmatically insert the
    * Excel Web App into a div with id=myExcelDiv. The full API is documented at
    * http://msdn.microsoft.com/ja-jp/library/hh315812.aspx. There you can find out how to programmatically get
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


### まとめ

 JavaScript オブジェクト モデルを使用するソリューションの記述は、そのソリューションを実行するのが SharePoint 2013上か、ホスト Web ページ上かにかかわらず、基本的に同じです。主な違いは、 **[Ewa.EwaControl]** オブジェクトへの参照を取得する方法です。 **[Ewa.EwaControl]** オブジェクトへの参照を取得していれば、それ以外の記述コードはどちらのシナリオでもほとんど同じです。
  
    
    

## その他の技術情報
<a name="SP15DevKitchenCon_AnatomyofanappSignupsheets_Additionalresources"> </a>


-  [埋め込まれた Excel ブックの操作で Excel Services JavaScript API を使用](http://msdn.microsoft.com/ja-jp/library/hh315812.aspx)
    
  
-  [Ewa.EwaControl.loadEwaAsync](http://msdn.microsoft.com/library/a7ee4d6d-5472-b942-c78e-b368d30bcb0e%28Office.15%29.aspx)
    
  
-  [Ewa.EwaControlCollection.getItem(index)](http://msdn.microsoft.com/library/11dd3a65-f914-4b34-bbaf-0206c8153d2b%28Office.15%29.aspx)
    
  

