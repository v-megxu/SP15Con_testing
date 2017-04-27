---
title: 範囲の値を設定する方法
keywords: how to,howdoi,howto,set range
f1_keywords:
- how to,howdoi,howto,set range
ms.prod: SHAREPOINT
ms.assetid: ccc7e204-f857-45a9-81ec-3a8484e6d454
---


# 範囲の値を設定する方法

Excel Web Services では、Excel ブックに値を設定する 4 つのメソッド ( **SetCell**、 **SetCellA1**、 **SetRange**、 **SetRangeA1**) を公開しています。 
  
    
    


> **メモ**
> Excel Web Services を使用して範囲に対して値を設定するなど、ブックに対して変更を行う際、ブックへの変更はその特定のセッションでのみ保持されます。変更は保存されたり、元のブックに保存されることはありません。現在のブックのセッションが終了 (例:えば、 **CloseWorkbook** メソッドを呼び出したり、セッションがタイムアウトした場合) すると、行われた変更は失われます。> ブックに対して行った変更を保存するには、 **GetWorkbook** メソッドを使用してから、保存先のファイル ストアの API を使用してブックを保存します。詳細は、「 [方法: ブック全体またはスナップショットの取得](how-to-get-an-entire-workbook-or-a-snapshot.md)」および「 [[方法] ブックを保存する](http://msdn.microsoft.com/library/feb74f7a-2d8f-4672-911b-de85f8852aea%28Office.15%29.aspx)」を参照してください。 
  
    
    


 **SetCell** メソッドおよび **SetCellA1** メソッドを使用して、1 つのセルに値を設定します。たとえば、「D3:G5」などの範囲参照または 1 つのセルより大きい名前付き範囲を渡すなどしてセルの範囲に値を設定しようとすると、メソッドの呼び出しは失敗します。セルの範囲に値を設定する場合は、代わりに **SetRange** メソッドおよび **SetRangeA1** メソッドを使用します。
  
    
    

A1 サフィックス付きのメソッド ( **SetCellA1** および **SetRangeA1**) は、A1 サフィックスが付かないメソッド ( **SetCell** および **SetRange**) とは異なる座標系を使用します。範囲参照 (例: H8、A3:D5、Sheet2!A12:G18) などの Excel 形式のセル参照や名前付き範囲を使用する場合、A1 サフィックス付きのメソッドを使用する必要があります。これらのメソッドにより、シートと範囲の名前を渡すことができます。数値座標系を使用して Excel の範囲にアクセスする場合は、A1 サフィックスが付かないメソッドを使用する必要があります。ループ内で一連のセルを反復処理するコードがある場合、または範囲座標がアルゴリズムの一部として動的に計算される場合は、範囲座標を使うほうが簡単です。セルの行および列の座標はゼロ (0) ベースです。このため、次の例のとおり、「0,0」はセル A1 を返します。


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

複数の隣接するセルから値を取得する場合、 **SetCell** メソッドに対して複数の呼び出しをするのではなく、 **SetRange** メソッドを使用することを検討してください。そうすると、サーバーとのやり取りが複数回ではなく 1 回で済みます。このため、場合によっては、 **SetCell** メソッドの代わりに **SetRange** メソッドを使うことで、パフォーマンスが著しく向上することがあります。 **SetRange** メソッドおよび **SetRangeA1** メソッドを使用してセルの範囲に値を設定する場合、オブジェクト配列 (C# の場合 **object[]**、Visual Basic .NET の場合 **Object ()**) を使用します。実際、オブジェクト配列はジャグ配列です。配列内の各エントリは、セルを表す別のオブジェクト配列です。ジャグ配列について、詳細は「 [ジャグ配列 (C# プログラミング ガイド)](http://go.microsoft.com/fwlink/?LinkId=65619) (http://msdn.microsoft.com/ja-jp/library/2s05feca.aspx) を参照してください。
### SetCell メソッドおよび SetRange メソッドを使用して値を設定するには


1. 開いているブック内のセルに数値範囲座標を使用して値を設定するには、 **SetCell** メソッドを使用します。
    
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

2. 開いているブック内の範囲に数値範囲座標を使用して値を設定するには、 **SetRange** メソッドを使用します。
    
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


### SetCellA1 メソッドおよび SetRangeA1 メソッドを使用して値を設定するには


1. 開いているブック内のセルに Excel の 「A1」範囲指定を使用して値を設定するには、 **SetCellA1** メソッドを使用します。
    
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

2. 開いているブック内の範囲にExcel の 「A1」範囲指定を使用して値を設定するには、 **SetRangeA1** メソッドを使用します。
    
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


## 関連項目


#### タスク


  
    
    
 [範囲のアドレスとシート名を指定する方法](how-to-specify-a-range-address-and-sheet-name.md)
  
    
    
 [範囲から値を取得する方法](how-to-get-values-from-ranges.md)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
