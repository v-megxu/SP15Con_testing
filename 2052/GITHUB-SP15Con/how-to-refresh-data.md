---
title: 如何：刷新数据
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: 6cfd89ff-846e-486b-8f73-a109016813ab
---


# 如何：刷新数据

本示例说明如何使用 **Refresh** 方法，从打开的工作簿的外部数据源中检索更新后的数据。 **Refresh** 方法的 Excel Web Services 签名如下所示：
  
    
    


```cs

public Status[] Refresh (string sessionId, string connectionName)
```


```VB.net
Public Function Refresh(ByVal sessionId As String, ByVal connectionName As String) As Status()
End Function
```

如果您直接链接到 Microsoft.Office.Excel.Server.WebServices.dll， **Refresh** 方法的签名为：


```cs

public void Refresh (string sessionId, string connectionName,
    out Status[] status)
```




```VB.net

Public Sub Refresh(ByVal sessionId As String, ByVal connectionName As String, <System.Runtime.InteropServices.Out()> ByRef status() As Status)
End Sub
```

 `connectionName` 参数是指 Microsoft Office Excel 2007 工作簿中的连接名称。您可以使用 **Refresh** 方法刷新工作簿中的单个数据连接，或者刷新所有连接。如果连接是使用打开时刷新功能创建的，这尤其有用。刷新连接时，将刷新使用该连接的数据和所有对象。要刷新工作簿中的所有可用连接，您需为连接名称参数传入一个空连接字符串或 **null**。不论使用的身份验证类型如何，都会尝试执行刷新操作，而没有进一步确认或提示。有关 **Refresh** 方法的详细信息，请参阅 Excel Web Services 参考文档。
## 示例

下面的代码示例说明如何使用 Excel Web Services 来调用 **Refresh** 方法。本示例中的连接名称为"MyInventoryConnection"：
  
    
    

```cs

// Instantiate the Web service.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();
string sheetName = "Sheet3";

// Set the path to the workbook to open.
// TODO: Change the path to the workbook
// to point to a workbook you have access to.
// The workbook must be in a trusted location.
string targetWorkbookPath = 
    http://myserver02/example/Shared%20Documents/Book1.xlsx";
            
// Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials;

// Call open workbook, and point to the trusted   
// location of the workbook to open.
string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", out outStatus);
 
// Prepare object to define range coordinates.
rangeCoordinates.Column = 0;
rangeCoordinates.Row = 0;
rangeCoordinates.Height = 8;
rangeCoordinates.Width = 10;

// Set the cell located in the first row and 
// ninth column to 300.
xlservice.SetCell(sessionId, sheetName, 0, 8, 300); 
xlservice.Refresh(sessionId, "MyInventoryConnection");
```


```VB.net

' Instantiate the Web service.
Dim xlservice As New ExcelService()
Dim outStatus() As Status
Dim rangeCoordinates As New RangeCoordinates()
Dim sheetName As String = "Sheet3"

' Set the path to the workbook to open.
' TODO: Change the path to the workbook
' to point to a workbook you have access to.
' The workbook must be in a trusted location.
' Set credentials for requests.
Dim targetWorkbookPath As String = http: xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials 'myserver02/example/Shared%20Documents/Book1.xlsx";

' Call open workbook, and point to the trusted   
' location of the workbook to open.
Dim sessionId As String = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus)

' Prepare object to define range coordinates.
rangeCoordinates.Column = 0
rangeCoordinates.Row = 0
rangeCoordinates.Height = 8
rangeCoordinates.Width = 10

' Set the cell located in the first row and 
' ninth column to 300.
xlservice.SetCell(sessionId, sheetName, 0, 8, 300)
xlservice.Refresh(sessionId, "MyInventoryConnection")
```

如果您直接链接到 Microsoft.Office.Excel.Server.WebServices.dll，等效的代码为：
  
    
    



```

// Instantiate the ExcelService class.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();
string sheetName = "Sheet3";

// Set the path to the workbook to open.
// TODO: Change the path to the workbook
// to point to a workbook you have access to.
// The workbook must be in a trusted location.
string targetWorkbookPath = 
    http://myserver02/example/Shared%20Documents/Book1.xlsx";
            
// Call the open workbook, and point to the trusted 
// location of the workbook to open.
string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", out outStatus);
                
// Set the cell located in the first row and 
// ninth column to 300.
xlservice.SetCell(sessionId, sheetName, 0, 8, 300, out outStatus); 
xlservice.Refresh(sessionId, "MyInventoryConnection", out outStatus);

byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);

// Write the resulting Excel file to stdout 
// as a binary stream.
BinaryWriter binaryWriter = 
    new BinaryWriter(Console.OpenStandardOutput());
binaryWriter.Write(workbook);
binaryWriter.Close();
...
...

```




```VB.net

' Instantiate the ExcelService class.
Dim xlservice As New ExcelService()
Dim outStatus() As Status
Dim rangeCoordinates As New RangeCoordinates()
Dim sheetName As String = "Sheet3"

' Set the path to the workbook to open.
' TODO: Change the path to the workbook
' to point to a workbook you have access to.
' The workbook must be in a trusted location.
' Call the open workbook, and point to the trusted 
' location of the workbook to open.
Dim targetWorkbookPath As String = http: String sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus) 'myserver02/example/Shared%20Documents/Book1.xlsx";

' Set the cell located in the first row and 
' ninth column to 300.
xlservice.SetCell(sessionId, sheetName, 0, 8, 300, outStatus)
xlservice.Refresh(sessionId, "MyInventoryConnection", outStatus)

Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, status)

' Write the resulting Excel file to stdout 
' as a binary stream.
Dim binaryWriter As New BinaryWriter(Console.OpenStandardOutput())
binaryWriter.Write(workbook)
binaryWriter.Close()
...
...

```


## 另请参阅


#### 任务


  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
  
    
    
 [如何：从 Excel 客户端保存到服务器](how-to-save-from-excel-client-to-the-server.md)
  
    
    
 [如何：获取整个工作簿或快照](how-to-get-an-entire-workbook-or-a-snapshot.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
