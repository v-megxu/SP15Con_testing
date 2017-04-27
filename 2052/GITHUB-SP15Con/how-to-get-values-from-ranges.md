---
title: 如何：从范围获取值
keywords: get range,how to,howdoi,howto
f1_keywords:
- get range,how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: ab2c0f60-b7df-46a1-9105-eb85ce817431
---


# 如何：从范围获取值

Excel Web Services 公开从 Excel 工作簿获取值的四种方法： **GetCell**、 **GetCellA1**、 **GetRange** 和 **GetRangeA1**。 
  
    
    

 **GetCell** 和 **GetCellA1** 方法返回单个单元格的值。如果您尝试请求多个单元格例如，通过传递范围引用（如"B1:E2"），或者传递大于单个单元格的指定范围，等等方法调用将失败。如果您想检索一系列单元格的值，请转为使用 **GetRange** 和 **GetRangeA1** 方法。
具有 A1 后缀（ **GetCellA1** 和 **GetRangeA1**）的方法使用与不具有 A1 后缀（ **GetCell** 和 **GetRange**）的方法不同的坐标系统。如果您想使用对单元格的 Excel 样式引用，例如范围引用（如 H8、A3:D5、Sheet2!A12:G18）或指定范围，您应使用具有 A1 后缀的方法。这些方法允许您传递所需的工作表名称和范围地址。在大多数情况下，出于抽象考虑，使用指定范围而非 Excel 样式引用是一个好办法。
  
    
    

如果您想使用数字坐标系统访问 Excel 范围，您应该使用不具有 A1 后缀的方法。当您的代码在一个循环中遍历单元格集时，或者当范围坐标作为算法的一部分动态计算时，使用范围坐标更简单。单元格的行和列坐标从 0 开始。因此，"0,0"将返回单元格 A1，如本示例中所示：


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

如果您从多个相邻的单元格获取值，您可能会考虑使用 **GetRange** 方法，而不是对 **GetCell** 方法进行多次调用。这会导致与服务器进行单个往返，而不是多个往返。因此，在某些情况下，通过使用 **GetRange** 方法而非 **GetCell** 方法，性能可能会大大改进。使用 **GetRange** 和 **GetRangeA1** 方法获取单元格范围时，将向您返回一个对象数组（使用 C# 的 **object[]** 以及使用 Visual Basic .NET 的 **Object ()**）。对象数组实际上是一个交错数组。您在数组中收到的每个条目将是代表单元格的另一个对象数组。有关交错数组的详细信息，请参阅 [交错数组（C# 编程指南）](http://msdn.microsoft.com/zh-cn/library/2s05feca.aspx) (http://msdn.microsoft.com/zh-cn/library/2s05feca.aspx)。
### 使用 GetCell 和 GetRange 方法获取值


1. 通过数字范围坐标，使用 **GetCell** 方法从打开的工作簿的单元格中获取值；例如：
    
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

2. 通过数字范围坐标，使用 **GetRange** 方法从打开的工作簿的范围中获取值。
    
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


### 使用 GetCellA1 和 GetRangeA1 方法获取值


1. 通过 Excel"A1"范围规范，使用 **GetCellA1** 方法从打开的工作簿的单元格中获取值；例如：
    
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

2. 通过 Excel"A1"范围规范，使用 **GetRangeA1** 方法从打开的工作簿的范围中获取值。以下代码示例请求 2x3 范围，即两行乘以三列。然后代码将遍历返回的每一行并检索每一行包含的三个单元格。即，在第一次迭代中：
    
  - rangeResult [0] 返回单元格 B2 中的值
    
  
  - rangeResult [1] 返回单元格 C2 中的值
    
  
  - rangeResult [2] 返回单元格 D2 中的值
    
    在第二次迭代：
    
  
  - rangeResult [0] 返回单元格 B3 中的值
    
  
  - rangeResult [1] 返回单元格 C3 中的值
    
  
  - rangeResult [2] 返回单元格 D3 中的值
    
  

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


## 另请参阅


#### 任务


  
    
    
 [如何：指定范围地址和工作表名称](how-to-specify-a-range-address-and-sheet-name.md)
  
    
    
 [如何：设置范围的值](how-to-set-values-of-ranges.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
