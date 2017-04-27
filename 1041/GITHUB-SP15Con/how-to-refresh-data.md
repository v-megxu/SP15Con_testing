---
title: データを更新する方法
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: 6cfd89ff-846e-486b-8f73-a109016813ab
---


# データを更新する方法

この例は、 **Refresh** メソッドを使用して、開いているブックで外部データ ソースから更新されたデータを取得する方法を示しています。 **Refresh** メソッドの Excel Web Services シグネチャは次のとおりです。
  
    
    


```cs

public Status[] Refresh (string sessionId, string connectionName)
```


```VB.net
Public Function Refresh(ByVal sessionId As String, ByVal connectionName As String) As Status()
End Function
```

Microsoft.Office.Excel.Server.WebServices.dll に直接リンクする場合、 **Refresh** メソッドのシグネチャは次のとおりです。


```cs

public void Refresh (string sessionId, string connectionName,
    out Status[] status)
```




```VB.net

Public Sub Refresh(ByVal sessionId As String, ByVal connectionName As String, <System.Runtime.InteropServices.Out()> ByRef status() As Status)
End Sub
```

引数  `connectionName` は、ブック Microsoft Office Excel 2007 の接続名です。ブック内の 1 つのデータ接続を更新するか、すべての接続を更新するには、 **Refresh** メソッドを使用します。これは、開くときに更新する機能なしに接続が作成されるときに特に便利です。接続を更新する際、接続を使用するデータとすべてのオブジェクトが更新されます。ブックですべての使用可能な接続を更新するには、接続名の引数として空の接続文字列または **null** を渡します。更新操作は、さらに確認したり、メッセージが表示されることなく、使用される認証の種類と無関係に試行されます。 **Refresh** メソッドについて、詳細は Excel Web Services のリファレンス ドキュメントを参照してください。
## 例

次のコードのサンプルは、Excel Web Services を使用して **Refresh** メソッドを呼び出す方法を示しています。この例の接続名は「MyInventoryConnection」です。
  
    
    

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

Microsoft.Office.Excel.Server.WebServices.dll に直接リンクする場合、同等のコードは次のとおりです。
  
    
    



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


## 関連項目


#### タスク


  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
  
    
    
 [方法: Excel クライアントからサーバーへの保存](how-to-save-from-excel-client-to-the-server.md)
  
    
    
 [方法: ブック全体またはスナップショットの取得](how-to-get-an-entire-workbook-or-a-snapshot.md)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [SOAP 呼び出しのループバックおよび直接リンク](loop-back-soap-calls-and-direct-linking.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
