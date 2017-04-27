---
title: 如何：设置范围的值
keywords: how to,howdoi,howto,set range
f1_keywords:
- how to,howdoi,howto,set range
ms.prod: OFFICE365
ms.assetid: ccc7e204-f857-45a9-81ec-3a8484e6d454
---


# 如何：设置范围的值

Excel Web Services 公开将值设置到 Excel 工作簿中的四种方法： **SetCell**、 **SetCellA1**、 **SetRange** 和 **SetRangeA1**。 
  
    
    


> **注释**
> 对工作簿进行更改时例如，使用 Excel Web Services 将值设置为范围对工作簿的更改将仅为该特定会话保存。更改不会保存到原始工作簿中。当前工作簿会话结束时（例如，当您调用 **CloseWorkbook** 方法时，或当会话超时时），您所做的更改将丢失。> 如果您想将更改保存到工作簿，可以使用 **GetWorkbook** 方法，然后使用目标文件存储的 API 保存工作簿。有关详细信息，请参阅 [如何：获取整个工作簿或快照](how-to-get-an-entire-workbook-or-a-snapshot.md)和 [如何：保存工作簿](http://msdn.microsoft.com/library/feb74f7a-2d8f-4672-911b-de85f8852aea%28Office.15%29.aspx)。 
  
    
    


使用 **SetCell** 和 **SetCellA1** 方法设置单个单元格中的值。如果您尝试设置多个单元格中的值例如，通过传递范围引用（如"D3:G5"），或者传递大于单个单元格的指定范围，等等方法调用将失败。如果您想设置一系列单元格的值，请转为使用 **SetRange** 和 **SetRangeA1** 方法。
  
    
    

具有 A1 后缀（ **SetCellA1** 和 **SetRangeA1**）的方法使用与不具有 A1 后缀（ **SetCell** 和 **SetRange**）的方法不同的坐标系统。如果您想使用对单元格的 Excel 样式引用，例如范围引用（如 H8、A3:D5、Sheet2!A12:G18）或指定范围，您应使用具有 A1 后缀的方法。这些方法允许您传递工作表和范围的名称。如果您想使用数字坐标系统访问 Excel 范围，您应该使用不具有 A1 后缀的方法。当您的代码在一个循环中遍历单元格集时，或者当范围坐标作为算法的一部分动态计算时，使用范围坐标更简单。单元格的行和列坐标从 0 开始。因此，"0,0"将返回单元格 A1，如本示例中所示：


```cs

// Call the SetCell method to set a value, 8, into a cell.
// The cell is in the first row and first column; that is, cell A1.
xlservice.SetCell(sessionId, sheetName, 0, 0, 8);
```




```VB.net

' Call the SetCell method to set a value, 8, into a cell.
' The cell is in the first row and first column; that is, cell A1.
xlservice.SetCell(sessionId, sheetName, 0, 0, 8)
```

如果您从多个相邻的单元格获取值，您可能会考虑使用 **SetRange** 方法，而不是对 **SetCell** 方法进行多次调用。这会导致与服务器进行单个往返，而不是多个往返。因此，在某些情况下，通过使用 **SetRange** 方法而非 **SetCell** 方法，性能可能会大大改进。使用 **SetRange** 和 **SetRangeA1** 方法将值设置到单元格范围时，您使用一个对象数组（使用 C# 的 **object[]** 以及使用 Visual Basic .NET 的 **Object ()**）。对象数组实际上是一个交错数组；数组中的每个条目是代表单元格的另一个对象数组。有关交错数组的详细信息，请参阅 [交错数组（C# 编程指南）](http://go.microsoft.com/fwlink/?LinkId=65619) (http://msdn.microsoft.com/zh-cn/library/2s05feca.aspx)。
### 使用 SetCell 和 SetRange 方法设置值


1. 通过数字范围坐标，使用 **SetCell** 方法设置打开的工作簿中单元格的值：
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();
string sheetName = "Sheet2";

// Set the path to a workbook.
// The workbook must be in a trusted location.
string targetWorkbookPath = "http://myserver02/example/Shared%20Documents/Book1.xlsx";

// Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials;

// Call the open workbook, and point to the trusted 
// location of the workbook to open.
string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", out outStatus);

// Call the SetCell method to set the cell's value to 28.
// The cell is in the ninth row and second column, which is cell B9.
xlservice.SetCell(sessionId, sheetName, 8, 1, 28);
  ```


  ```
  
' Instantiate the Web service and make a status array object.
Dim xlservice As New ExcelService()
Dim outStatus() As Status
Dim rangeCoordinates As New RangeCoordinates()
Dim sheetName As String = "Sheet2"

' Set the path to a workbook.
' The workbook must be in a trusted location.
Dim targetWorkbookPath As String = "http://myserver02/example/Shared%20Documents/Book1.xlsx"

' Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials

' Call the open workbook, and point to the trusted 
' location of the workbook to open.
Dim sessionId As String = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus)

' Call the SetCell method to set the cell's value to 28.
' The cell is in the ninth row and second column, which is cell B9.
xlservice.SetCell(sessionId, sheetName, 8, 1, 28)

  ```

2. 通过数字范围坐标，使用 **SetRange** 方法设置打开的工作簿范围中的值：
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();

...
private void Form1_Load(object sender, EventArgs e)
{
...
...
//Prepare object to define range coordinates
//and call the GetRange method.
//startCol, startRow, startHeight, and startWidth
//get their values from user input.
rangeCoordinates.Column = (int)startCol.Value;
rangeCoordinates.Row = (int)startRow.Value;
rangeCoordinates.Height = (int)startHeight.Value;
rangeCoordinates.Width = (int)startWidth.Value;
...
...
}
private void SetRangeButton_Click(object sender, EventArgs e)
{
object[] values = new object[rangeCoordinates.Height];
string[] fieldValues =    
    SetRangeTextBox.Text.Split((",").ToCharArray());

if (fieldValues.Length != rangeCoordinates.Height * 
rangeCoordinate.Width)
    {
        throw new Exception("The number of inputs (" + 
            fieldValues.Length + ") does not match" +
            " the product of Height (" +             rangeCoordinates.Height + ") and Width (" + 
            rangeCoordinates.Width + ")");
    }

for (int i = 0; i < rangeCoordinates.Height; i++)
    {
        object[] currentRow = 
            new object[rangeCoordinates.Width];
        for (int j = 0; j < rangeCoordinates.Width; j++)
        {
            currentRow[j] = fieldValues[i *             rangeCoordinates.Width + j];
        }
        values[i] = currentRow;
    }

SetStatusText("Waiting for SetRange...");
outStatus = xlservice.SetRange(
    sessionID, SheetNameTextBox.Text, 
    rangeCoordinates, values);
}
catch (SoapException exc)
{
StopTimer("SetRange");
GenerateErrorMessage("SetRange", exc);
}
catch (Exception exc)
{
StopTimer("SetRange");
GenerateToolErrorMessage("While calling SetRange", exc);
}
}

  ```


  ```VB.net
  
' Instantiate the Web service and make a status array object.
Private xlservice As New ExcelService()
Private outStatus() As Status
Private rangeCoordinates As New RangeCoordinates()

...
Private Sub Form1_Load(ByVal sender As Object, ByVal e As EventArgs)
...
...
'Prepare object to define range coordinates
'and call the GetRange method.
'startCol, startRow, startHeight, and startWidth
'get their values from user input.
rangeCoordinates.Column = CInt(Fix(startCol.Value))
rangeCoordinates.Row = CInt(Fix(startRow.Value))
rangeCoordinates.Height = CInt(Fix(startHeight.Value))
rangeCoordinates.Width = CInt(Fix(startWidth.Value))
...
...
End Sub
Private Sub SetRangeButton_Click(ByVal sender As Object, ByVal e As EventArgs)
Dim values(rangeCoordinates.Height - 1) As Object
Dim fieldValues() As String = SetRangeTextBox.Text.Split((",").ToCharArray())

If fieldValues.Length <> rangeCoordinates.Height * rangeCoordinate.Width Then
        Throw New Exception("The number of inputs (" &amp; fieldValues.Length &amp; ") does not match" &amp; " the product of Height (" &amp; rangeCoordinates.Height &amp; ") and Width (" &amp; rangeCoordinates.Width &amp; ")")
End If

For i As Integer = 0 To rangeCoordinates.Height - 1
        Dim currentRow(rangeCoordinates.Width - 1) As Object
        For j As Integer = 0 To rangeCoordinates.Width - 1
            currentRow(j) = fieldValues(i * rangeCoordinates.Width + j)
        Next j
        values(i) = currentRow
Next i
Try
SetStatusText("Waiting for SetRange...")
outStatus = xlservice.SetRange(sessionID, SheetNameTextBox.Text, rangeCoordinates, values)
Catch exc As SoapException
StopTimer("SetRange")
GenerateErrorMessage("SetRange", exc)
Catch exc As Exception
StopTimer("SetRange")
GenerateToolErrorMessage("While calling SetRange", exc)
End Try
End Sub
  ```


### 使用 SetCellA1 和 SetRangeA1 方法设置值


1. 通过 Excel"A1"范围规范，使用 **SetCellA1** 方法设置打开的工作簿中单元格的值：
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;

xlservice.SetCellA1(sessionId, String.Empty, "InterestRateParam", 8);
  ```


  ```VB.net
  
' Instantiate the Web service and make a status array object.
Dim xlservice As New ExcelService()
Dim outStatus() As Status

xlservice.SetCellA1(sessionId, String.Empty, "InterestRateParam", 8)
  ```

2. 通过 Excel"A1"范围规范，使用 **SetRangeA1** 方法从打开的工作簿的范围中获取值：
    
  ```cs
  
// Instantiate the Web service and make a status array object.
ExcelService xlservice = new ExcelService();
Status[] outStatus;
...

void SetRangeA1Button_ServerClick(object sender, EventArgs e)
{
    int height, width;
    CalculateHeightAndWidth(RangeNameTextBox5.Value.Trim(), 
        out height, out width);

    object[] values = new object[height];
    string[] fieldValues = 
        RangeValuesTextBox1.Value.Split((",").ToCharArray());
    if (fieldValues.Length != height * width)
    {
        throw new Exception("The number of inputs (" + 
            fieldValues.Length + ") does not match" +
            " the product of Height (" + height + ") and 
            Width (" + width + ")");
    }

    for (int i = 0; i < height; i++)
    {
        object[] currentRow = new object[width];
        for (int j = 0; j < width; j++)
        {
            currentRow[j] = fieldValues[i * width + j];
        }
        values[i] = currentRow;
    }
    try
    {
        xlservice.SetRangeA1(SessionIDTextBox.Value, 
            SheetNameTextBox1.Value,RangeNameTextBox5.Value,
            values, out outStatus);
    }
    catch (SoapException exc)
    {
        ExceptionTextBox1.Value = exc.Message;
    }

}
  ```


  ```VB.net
  
' Instantiate the Web service and make a status array object.
Private xlservice As New ExcelService()
Private outStatus() As Status
...

Private Sub SetRangeA1Button_ServerClick(ByVal sender As Object, ByVal e As EventArgs)
    Dim height, width As Integer
    CalculateHeightAndWidth(RangeNameTextBox5.Value.Trim(), height, width)

    Dim values(height - 1) As Object
    Dim fieldValues() As String = RangeValuesTextBox1.Value.Split((",").ToCharArray())
    If fieldValues.Length <> height * width Then
        Throw New Exception("The number of inputs (" &amp; fieldValues.Length &amp; ") does not match" &amp; " the product of Height (" &amp; height &amp; ") and Width (" &amp; width &amp; ")")
    End If

    For i As Integer = 0 To height - 1
        Dim currentRow(width - 1) As Object
        For j As Integer = 0 To width - 1
            currentRow(j) = fieldValues(i * width + j)
        Next j
        values(i) = currentRow
    Next i
    Try
        xlservice.SetRangeA1(SessionIDTextBox.Value, SheetNameTextBox1.Value,RangeNameTextBox5.Value, values, outStatus)
    Catch exc As SoapException
        ExceptionTextBox1.Value = exc.Message
    End Try

End Sub
  ```


## 另请参阅


#### 任务


  
    
    
 [如何：指定范围地址和工作表名称](how-to-specify-a-range-address-and-sheet-name.md)
  
    
    
 [如何：从范围获取值](how-to-get-values-from-ranges.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
