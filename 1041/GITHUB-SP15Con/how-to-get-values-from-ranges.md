---
title: 範囲から値を取得する方法
keywords: get range,how to,howdoi,howto
f1_keywords:
- get range,how to,howdoi,howto
ms.prod: OFFICE365
ms.assetid: ab2c0f60-b7df-46a1-9105-eb85ce817431
---


# 範囲から値を取得する方法

Excel Web Services は、Excel ブックから値を取得する 4 つのメソッド ( **GetCell**、 **GetCellA1**、 **GetRange**、 **GetRangeA1**) を公開します。 
  
    
    

 **GetCell** メソッドと **GetCellA1** メソッドは、1 つのセルの値を返します。複数のセルを要求 (たとえば、「B1:E2」などの範囲参照、または 1 つのセルより大きい名前付き範囲を渡すなどして) すると、メソッドの呼び出しは失敗します。セルの範囲から値を取得する場合は、代わりに **GetRange** メソッドまたは **GetRangeA1** メソッドを使用します。
A1 サフィックス付きのメソッド ( **GetCellA1** および **GetRangeA1**) は、A1 サフィックスが付かないメソッド ( **GetCell** および **GetRange**) とは異なる座標系を使用します。範囲参照 (例: H8、A3:D5、Sheet2!A12:G18) や名前付き範囲ようなセルに対する Excel 形式の参照を使用する場合、A1 サフィックス付きのメソッドを使用する必要があります。これらのメソッドにより、目的のシート名および範囲のアドレスを渡すことができます。ほとんどの場合は、抽象化上の理由から、Excel 形式の参照より、名前付き範囲を使用することをお勧めします。
  
    
    

数値座標系を使用して Excel の範囲にアクセスする場合は、A1 サフィックスが付かないメソッドを使用する必要があります。ループ内で一連のセルを反復処理するコードがある場合、または範囲座標がアルゴリズムの一部として動的に計算される場合は、範囲座標を使うほうが簡単です。セルの行および列の座標はゼロ (0) ベースです。このため、次の例のとおり、「0,0」はセル A1 を返します。


```cs

// Call the GetCell method to retrieve a value from a cell.
// The cell is in the first row and first column; that is, cell A1
object[] rangeResult2 = xlservice.GetCell(sessionId, sheetName, 0, 0, true, out outStatus);
```




```VB.net

' Call the GetCell method to retrieve a value from a cell.
' The cell is in the first row and first column; that is, cell A1
Dim rangeResult2() As Object = xlservice.GetCell(sessionId, sheetName, 0, 0, True, outStatus)
```

複数の隣接するセルから値を取得する場合、 **GetCell** メソッドに対して複数の呼び出しをするのではなく、 **GetRange** メソッドを使用することを検討してください。そうすると、サーバーとのやり取りが複数回ではなく 1 回で済みます。このため、場合によっては、 **GetCell** メソッドの代わりに **GetRange** メソッドを使うことで、パフォーマンスが著しく向上することがあります。 **GetRange** メソッドおよび **GetRangeA1** メソッドを使用してセルの範囲を取得すると、オブジェクト配列 (C# の場合 **object[]**、Visual Basic .NET の場合 **Object ()**) が返されます。実際、オブジェクト配列はジャグ配列です。返される配列内の各エントリは、セルを表すオブジェクトからなる別の配列です。ジャグ配列について、詳細は「 [ジャグ配列 (C# プログラミング ガイド)](http://msdn.microsoft.com/ja-jp/library/2s05feca.aspx)」(http://msdn.microsoft.com/ja-jp/library/2s05feca.aspx) を参照してください。 
### GetCell メソッドおよび GetRange メソッドを使用して値を取得するには


1. 数値範囲座標を使用して、開いているブック内の 1 つのセルから値を取得するには、 **GetCell** メソッドを使用します。たとえば次のようにします。
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
string sheetName = "Sheet2";

// Set the path to a workbook.
// The workbook must be in a trusted location.
string targetWorkbookPath = "http://myserver02/example/Shared%20Documents/Book1.xlsx";

// Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials;

// Call the open workbook, and point to the trusted 
// location of the workbook to open.
string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", out outStatus);

// Call the GetCell method to retrieve a value from a cell.
// The cell is in the first row and ninth column.
object[] rangeResult2 = xlservice.GetCell(sessionId, sheetName, 0, 8, false, out outStatus);
  ```


  ```VB.net
  
' Instantiate the Web service and make a status array object.
Dim xlservice As New ExcelService()
Dim outStatus() As Status
Dim sheetName As String = "Sheet2"

' Set the path to a workbook.
' The workbook must be in a trusted location.
Dim targetWorkbookPath As String = "http://myserver02/example/Shared%20Documents/Book1.xlsx"

' Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials

' Call the open workbook, and point to the trusted 
' location of the workbook to open.
Dim sessionId As String = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus)

' Call the GetCell method to retrieve a value from a cell.
' The cell is in the first row and ninth column.
Dim rangeResult2() As Object = xlservice.GetCell(sessionId, sheetName, 0, 8, False, outStatus)
  ```

2. 数値範囲座標を使用して、開いているブック内の範囲から値を取得するには、 **GetRange** メソッドを使用します。
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();
string sheetName = "Sheet1";
...
// Prepare object to define range coordinates
// and call the GetRange method.
// startCol, startRow, startHeight, and startWidth
// get their value from user input.
rangeCoordinates.Column = (int)startCol.Value;
rangeCoordinates.Row = (int)startRow.Value;
rangeCoordinates.Height = (int)startHeight.Value;
rangeCoordinates.Width = (int)startWidth.Value;
...
object[] rangeResult1s = xlservice.GetRange(sessionId, sheetName, rangeCoordinates, false, out outStatus);
foreach (object[] x in rangeResult1s)
{
    foreach (object y in x)
    {
        Console.WriteLine(String.Format("{0}",  y));
    }
}
  ```


  ```VB.net
  
' Instantiate the Web service and make a status array object.
Dim xlservice As New ExcelService()
Dim outStatus() As Status
Dim rangeCoordinates As New RangeCoordinates()
Dim sheetName As String = "Sheet1"
...
' Prepare object to define range coordinates
' and call the GetRange method.
' startCol, startRow, startHeight, and startWidth
' get their value from user input.
rangeCoordinates.Column = CInt(Fix(startCol.Value))
rangeCoordinates.Row = CInt(Fix(startRow.Value))
rangeCoordinates.Height = CInt(Fix(startHeight.Value))
rangeCoordinates.Width = CInt(Fix(startWidth.Value))
...
Dim rangeResult1s() As Object = xlservice.GetRange(sessionId, sheetName, rangeCoordinates, False, outStatus)
For Each x As Object() In rangeResult1s
    For Each y As Object In x
        Console.WriteLine(String.Format("{0}", y))
    Next y
Next x
  ```


### GetCellA1 メソッドおよび GetRangeA1 メソッドを使用して値を取得するには


1. Excel 形式の 「A1」範囲指定を使用して、開いているブック内の 1 つのセルから値を取得するには **GetCellA1** メソッドを使用します。たとえば次のようにします。
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
string sheetName = "Sheet2";

object[] rangeResult = xlservice.GetCellA1(sessionId, sheetName, "MonthlyPayment", true, out outStatus);
  ```


  ```VB.net
  
' Instantiate the Web service and make a status array object.
Dim xlservice As New ExcelService()
Dim outStatus() As Status
Dim sheetName As String = "Sheet2"

Dim rangeResult() As Object = xlservice.GetCellA1(sessionId, sheetName, "MonthlyPayment", True, outStatus)
  ```

2. Excel 形式の 「A1」範囲指定を使用して、開いているブック内の範囲から値を取得するには、 **GetRangeA1** メソッドを使用します。次のコードの例では、2x3 の範囲、つまり 2 行 と 3 列を要求しています。コードは、返される各行をループ処理して、各行に含まれる 3 つのセルを取得します。つまり、反復処理の 1 回目では、
    
  - rangeResult [0] はセル B2 の値を返します
    
  
  - rangeResult [1] はセル C2 の値を返します
    
  
  - rangeResult [2] はセル D2 の値を返します
    
    反復処理の 2 回目では、
    
  
  - rangeResult [0] はセル B3 の値を返します
    
  
  - rangeResult [1] はセル C3 の値を返します
    
  
  - rangeResult [2] はセル D3 の値を返します
    
  

  ```cs
  
object[] rangeResults = xlservice.GetRangeA1(sessionId, "Sheet1", "B2:D3", true, out outStatus);
foreach (object[] rangeResult in rangeResults)
{
    Console.WriteLine(String.Format("{0} | {1} | {2}", 
        rangeResult[0], rangeResult[1], rangeResult[2]));
}

  ```


  ```VB.net
  
Dim rangeResults() As Object = xlservice.GetRangeA1(sessionId, "Sheet1", "B2:D3", True, outStatus)
For Each rangeResult As Object() In rangeResults
    Console.WriteLine(String.Format("{0} | {1} | {2}", rangeResult(0), rangeResult(1), rangeResult(2)))
Next rangeResult
  ```


## 関連項目


#### タスク


  
    
    
 [範囲のアドレスとシート名を指定する方法](how-to-specify-a-range-address-and-sheet-name.md)
  
    
    
 [範囲の値を設定する方法](how-to-set-values-of-ranges.md)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
