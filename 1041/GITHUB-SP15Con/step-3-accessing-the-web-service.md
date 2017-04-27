---
title: 手順 3 Web サービスへのアクセス
ms.prod: SHAREPOINT
ms.assetid: d27f654d-242f-4f34-8385-be857c170532
---


# 手順 3: Web サービスへのアクセス

プロジェクトに Excel Web Services への参照を追加したところで、次の手順では、Web サービスのプロキシ クラスのインスタンスを作成します。こうすると、プロキシ クラスのメソッドを呼び出すことによって、Web サービスのメソッドにアクセスできます。アプリケーションがこれらのメソッドを呼び出すと、Visual Studio によって生成されたプロキシ クラスのコードが、アプリケーションと Web サービスの間の通信を処理します。 
  
    
    

最初に、Web サービスのプロキシ クラス ExcelWebService のインスタンスを作成します。次に、プロキシ クラスを使用して、いくつかの Web サービスのメソッドとプロパティを呼び出します。 
呼び出しを使用して、ブックを開き、セッション ID を取得し、既定の資格情報を渡し、範囲座標オブジェクトを定義し、範囲座標オブジェクトを使用する範囲を取得し、ブックを閉じ、SOAP 例外をキャッチします。
  
    
    


## Web サービスへのアクセス


### ディレクティブを追加するには


1. 前に Web 参照を追加した際、ExcelService という名前のオブジェクトが <yourProject>.<webReferenceName> という名前空間に作成されました。この例では、オブジェクトの名前は SampleApplication.ExcelWebService です。このチュートリアルでは、SOAP 例外をキャッチする方法も示します。これを行うには、 **System.Web.Services.Protocols** オブジェクトを使用します。名前空間 **System.Web.Services.Protocols** は、XML Web サービス クライアントと ASP.NET を使用して作成された XML Web サービスの間の通信中に、回線全体でデータの伝送に使用するプロトコルを定義するクラスで構成されています。
  
    
    
これらのオブジェクトの使用を促進するには、まず名前空間をディレクティブとして Class1.cs ファイルに追加します。このようにして、このディレクティブを使用する場合、名前空間内の型を完全修飾する必要はありません。 
    
  
2. これらのディレクティブを追加するには、次のコードを、Class1.cs ファイルのコードの先頭、 `using System:` の後に追加します。
    
  ```cs
  
using SampleApplication.ExcelWebService;
using System.Web.Services.Protocols;
  ```


  ```VB.net
  
Imports SampleApplication.ExcelWebService
Imports System.Web.Services.Protocols
  ```


### Web サービスを呼び出すには


1.  `static void Main(string[] args)` の左中かっこの後に次のコードを追加して、Web サービス プロキシ オブジェクトのインスタンス化と初期化を行います。
    
  ```cs
  
ExcelService es = new ExcelService();
  ```


  ```VB.net
  Dim es As New ExcelService()
  ```

2. 次のコードを追加して、状態の配列および範囲座標オブジェクトを作成します。
    
  ```cs
  Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();
  ```


  ```VB.net
  
Dim outStatus() As Status
Dim rangeCoordinates As New RangeCoordinates()
  ```

3. アクセスするワークシートを指すコードを追加します。この例では、ワークシートは「Sheet1」といいます。 コードに次を追加します。 
    
  ```cs
  
string sheetName = "Sheet1";
  ```


  ```VB.net
  Dim sheetName As String = "Sheet1"
  ```


    > **メモ**
      > 開くブックに、値を含む「Sheet1」というワークシートがあるようにしてください。あるいは、コード内の「Sheet1」を存在するワークシート名に変更することができます。 
4. 次のコードを追加して、開くブックを指すようにします。
    
  ```cs
  string targetWorkbookPath = "http://myserver02/example/Shared%20Documents/Book1.xlsx";
  ```


  ```VB.net
  Dim targetWorkbookPath As String = "http://myserver02/example/Shared%20Documents/Book1.xlsx"
  ```


    > **重要**
      > このチュートリアルで使用しているブックの場所に一致するようにブックのパスを変更します。 ブックが存在し、ブックの保存場所が信頼できる場所であるようにします。 ブックの場所を指す HTTP URL を使用すると、リモートでアクセスすることができます。 

    > **メモ**
      > Microsoft SharePoint Server 2010 のブックへのパスを取得するには、ブックを右クリックして、[ **ショートカットのコピー**] を選択します。あるいは、[ **プロパティ**] を選択して、ブックへのパスをそこからコピーすることもできます。 
5. 次のコードを追加して、要求の資格情報を設定します。 
    
    > **メモ**
      > 既定の資格情報を使用する場合でも、資格情報を明示的に設定する必要があります。 

  ```cs
  es.Credentials = System.Net.CredentialCache.DefaultCredentials;
  ```


  ```VB.net
  es.Credentials = System.Net.CredentialCache.DefaultCredentials
  ```

6. 次のコードを追加して、ブックを開き、ブックが配置されている信頼できる場所を指定します。このコードは **try** ブロックに配置します。
    
  ```cs
  try
{
string sessionId = es.OpenWorkbook(targetWorkbookPath, "en-US", 
    "en-US", out outStatus);
  ```


  ```VB.net
  
Try
Dim sessionId As String = es.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus)
  ```

7. 次のコードを追加して、範囲座標を定義し、 **GetRange** メソッドを呼び出すオブジェクトを準備します。このコードは、範囲内の行数の合計と、特定の範囲の値を出力することもします。
    
  ```cs
  
rangeCoordinates.Column = 3;
rangeCoordinates.Row = 9;
rangeCoordinates.Height = 18;
rangeCoordinates.Width = 12;

object[] rangeResult1 = es.GetRange(sessionId, sheetName,
    rangeCoordinates, false, out outStatus);
Console.WriteLine("Total rows in range: " + rangeResult1.Length);
Console.WriteLine("Value in range is: " + ((object[])rangeResult1[5])[2]);
  ```


  ```VB.net
  
rangeCoordinates.Column = 3
rangeCoordinates.Row = 9
rangeCoordinates.Height = 18
rangeCoordinates.Width = 12

Dim rangeResult1() As Object = es.GetRange(sessionId, sheetName, rangeCoordinates, False, outStatus)
Console.WriteLine("Total rows in range: " &amp; rangeResult1.Length)
Console.WriteLine("Value in range is: " &amp; (CType(rangeResult1(5), Object()))(2))
  ```

8. ブックを閉じ、現在のセッションを閉じるコードを追加します。また、 **try** ブロックを終了する右中かっこを追加します。
    
    > **重要**
      > セッションの使用が完了したら、ブックを閉じることをお勧めします。これにより、セッションがクローズし、リソースが解放されます。 

  ```cs
  
es.CloseWorkbook(sessionId);
}
  ```


  ```VB.net
  
es.CloseWorkbook(sessionId)
  ```

9. SOAP 例外をキャッチし、例外メッセージを出力する **catch** ブロックを追加します。
    
  ```cs
  catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As SoapException
    Console.WriteLine("SOAP Exception Message: {0}", e.Message)
End Try
  ```


## コードを完成する

次のコードのサンプルは、前の手順で説明した使用例のファイル Class1.cs 内の完全なコードです。
  
    
    

> **重要**
> ブックのパスやシート名などは、適宜変更してください。 
  
    
    


```cs

using System;
using SampleApplication.ExcelWebService;
using System.Web.Services.Protocols;

namespace SampleApplication
{
    class Class1
    {
        [STAThread]
        static void Main(string[] args)
        {            
            // Instantiate the Web service and create a status array object and range coordinate object
            ExcelService es = new ExcelService();
            Status[] outStatus;
            RangeCoordinates rangeCoordinates = new RangeCoordinates();
            
string sheetName = "Sheet1";
            // Using workbookPath this way will allow 
            // you to call the workbook remotely.
            // TODO: change the workbook path to 
            // point to workbook in a trusted location
            // that you have access to 
            string targetWorkbookPath = "http://myserver02/example/Shared%20Documents/Book1.xlsx";
//you can also use .xlsb files, for example, //"http://myserver02/example/Shared%20Documents/Book1.xlsb";

            // Set credentials for requests
            es.Credentials = System.Net.CredentialCache.DefaultCredentials;
            //Console.WriteLine("Cred: {0}", es.Credentials);
            try
            {
                // Call open workbook, and point to the trusted   
                // location of the workbook to open.
                string sessionId = es.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", out outStatus);
                // Console.WriteLine("sessionID : {0}", sessionId);

                // Prepare object to define range coordinates
                // and the GetRange method.
                rangeCoordinates.Column = 3;
                rangeCoordinates.Row = 9;
                rangeCoordinates.Height = 18;
                rangeCoordinates.Width = 12;

                object[] rangeResult1 = es.GetRange(sessionId, sheetName, rangeCoordinates, false, out outStatus);
                Console.WriteLine("Total Rows in Range: " + rangeResult1.Length);
                Console.WriteLine("Value in range is: " + ((object[])rangeResult1[5])[3]); 
        
                // Close workbook. This also closes session.
                es.CloseWorkbook(sessionId);
            }
            catch (SoapException e)
            {
                Console.WriteLine("SOAP Exception Message: {0}", e.Message);
            }
            // catch (Exception e)
//            {
//                Console.WriteLine("Exception Message: {0}", e.Message);
//            }
//            Console.ReadLine();
        }
    }
}
     
```


```VB.net

Imports System
Imports SampleApplication.ExcelWebService
Imports System.Web.Services.Protocols

Namespace SampleApplication
    Friend Class Class1
        <STAThread> _
        Shared Sub Main(ByVal args() As String)
            ' Instantiate the Web service and create a status array object and range coordinate object
            Dim es As New ExcelService()
            Dim outStatus() As Status
            Dim rangeCoordinates As New RangeCoordinates()

Dim sheetName As String = "Sheet1"
            ' Using workbookPath this way will allow 
            ' you to call the workbook remotely.
            ' TODO: change the workbook path to 
            ' point to workbook in a trusted location
            ' that you have access to 
            Dim targetWorkbookPath As String = "http://myserver02/example/Shared%20Documents/Book1.xlsx"
'you can also use .xlsb files, for example, //"http://myserver02/example/Shared%20Documents/Book1.xlsb";

            ' Set credentials for requests
            es.Credentials = System.Net.CredentialCache.DefaultCredentials
            'Console.WriteLine("Cred: {0}", es.Credentials);
            Try
                ' Call open workbook, and point to the trusted   
                ' location of the workbook to open.
                Dim sessionId As String = es.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus)
                ' Console.WriteLine("sessionID : {0}", sessionId)

                ' Prepare object to define range coordinates
                ' and the GetRange method.
                rangeCoordinates.Column = 3
                rangeCoordinates.Row = 9
                rangeCoordinates.Height = 18
                rangeCoordinates.Width = 12

                Dim rangeResult1() As Object = es.GetRange(sessionId, sheetName, rangeCoordinates, False, outStatus)
                Console.WriteLine("Total Rows in Range: " &amp; rangeResult1.Length)
                Console.WriteLine("Value in range is: " &amp; (CType(rangeResult1(5), Object()))(3))

                ' Close workbook. This also closes session.
                es.CloseWorkbook(sessionId)
            Catch e As SoapException
                Console.WriteLine("SOAP Exception Message: {0}", e.Message)
            ' Catch e As Exception
            '    Console.WriteLine("Exception Message: {0}", e.Message)
            End Try
            'Console.ReadLine()
        End Sub
    End Class
End Namespace
```


## 関連項目


#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
#### その他の技術情報


  
    
    
 [ステップ 1: Web サービス クライアント プロジェクトを作成する](step-1-creating-the-web-service-client-project.md)
  
    
    
 [手順 2: Web 参照を追加する](step-2-adding-a-web-reference.md)
  
    
    
 [手順 4: アプリケーションのビルドとテストを行う](step-4-building-and-testing-the-application.md)
  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
  
    
    
 [[方法] スクリプトを使用してブックの場所を信頼する](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)
