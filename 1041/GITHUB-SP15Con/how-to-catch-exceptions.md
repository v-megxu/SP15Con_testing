---
title: 例外をキャッチする方法
keywords: errors,how to,howdoi,howto
f1_keywords:
- errors,how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: de5fdb67-201b-4d7a-90a8-99ab7e51ea4e
---


# 例外をキャッチする方法

例外が発生する可能性があるコードのセクションを try ブロックに配置するとともに、例外を処理するコードを catch ブロックに配置します。catch ステートメントの順序は重要です。例外が発生した場合、例外はスタックに渡され、各 catch ブロックは処理する機会を与えられます。例外を処理する必要がある catch ブロックは、例外の種類と catch ブロックで指定された例外名を照合して決定されます。たとえば、次の catch ブロックは Simple Object Access Protocol (SOAP) の例外をキャッチします。
  
    
    


```cs

catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Error Code: {0}", 
        e.SubCode.Code.Name);
    Console.WriteLine("SOAP Exception Message is: {0}", 
        e.Message);
}
```


```VB.net

Catch e As SoapException
    Console.WriteLine("SOAP Exception Error Code: {0}", e.SubCode.Code.Name)
    Console.WriteLine("SOAP Exception Message is: {0}", e.Message)
End Try
```

型固有の catch ブロックが存在しない場合は、汎用的な catch ブロックが存在する場合は例外をキャッチします。 たとえば、次のコードを追加することで汎用的な例外をキャッチできます。


```cs

catch (Exception e)
{
    Console.WriteLine("Exception Message: {0}", e.Message);
}
```




```VB.net

Catch e As Exception
    Console.WriteLine("Exception Message: {0}", e.Message)
End Try
```

特定の型の例外を対象とする catch ブロックは、一般的な例外の前に配置します。 共通言語ランタイムは、catch ブロックによってキャッチされなかった例外をキャッチします。ランタイムの構成次第で、デバッグのダイアログ ボックスが表示されるか、プログラムの実行が停止して例外情報のダイアログ ボックスが表示されます。デバッグについて、詳細は 「 [アプリケーションのデバッグとプロファイリング](http://go.microsoft.com/fwlink/?LinkId=64641)」(http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpguide/html/cpcondebuggingprofiling.asp) を参照してください。例外の処理方法について、詳細は「 [例外処理のベスト プラクティス](http://go.microsoft.com/fwlink/?LinkId=64480)」(http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpguide/html/cpconbestpracticesforhandlingexceptions.asp) を参照してください。
## 例


```cs

using System;
using System.Text;
using System.Web.Services.Protocols;
using ExcelWebService.myserver02;
namespace ExcelWebService
{
    class WebService
    {
        [STAThread]
        static void Main(string[] args)
        {
            // Instantiate the Web service and make a status array object
            ExcelService xlservice = new ExcelService();
            Status[] outStatus;
            RangeCoordinates rangeCoordinates = new RangeCoordinates();
            string sheetName = "Sheet1";

            // Set the path to the workbook to open.
            // TODO: Change the path to the workbook
            // to point to a workbook you have access to.
            // The workbook must be in a trusted location.
            // If workbookPath is a UNC path, the application 
            // must be on the same computer as the server.
            // string targetWorkbookPath = 
            // @"\\\\MyServer\\myxlfiles\\Formulas.xlsx";
            string targetWorkbookPath = 
            "http://myserver02/DocLib/Shared%20Documents/Basic1.xlsx";
            // Set credentials for requests
            xlservice.Credentials = 
               System.Net.CredentialCache.DefaultCredentials;

            try
            {
                // Call the OpenWorkbook method and point to the 
                // trusted location of the workbook to open.
                string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", out outStatus);
                Console.WriteLine("sessionID : {0}", sessionId);
                // Prepare object to define range coordinates, 
                // and call the GetRange method.
                rangeCoordinates.Column = 0;
                rangeCoordinates.Row = 0;
                rangeCoordinates.Height = 18;
                rangeCoordinates.Width = 10;

                object[] rangeResult1 = xlservice.GetRange(sessionId, sheetName, rangeCoordinates, false, out outStatus);
                Console.WriteLine("Total rows in range: " + rangeResult1.Length);

                Console.WriteLine("Sum in last column is: " + ((object[])rangeResult1[2])[3]);

               // Close the workbook. This also closes the session.
                xlservice.CloseWorkbook(sessionId);
            }
            catch (SoapException e)
            {
                Console.WriteLine("SOAP Exception Error Code: {0}", 
                    e.SubCode.Code.Name);
                Console.WriteLine("SOAP Exception Message is: {0}", 
                    e.Message);
            }

            catch (Exception e)
            {
                Console.WriteLine("Exception Message: {0}", e.Message);
            }
            Console.ReadLine();
        }
    }
}
```


```VB.net

Imports System
Imports System.Text
Imports System.Web.Services.Protocols
Imports ExcelWebService.myserver02
Namespace ExcelWebService
    Friend Class WebService
        <STAThread> _
        Shared Sub Main(ByVal args() As String)
            ' Instantiate the Web service and make a status array object
            Dim xlservice As New ExcelService()
            Dim outStatus() As Status
            Dim rangeCoordinates As New RangeCoordinates()
            Dim sheetName As String = "Sheet1"

            ' Set the path to the workbook to open.
            ' TODO: Change the path to the workbook
            ' to point to a workbook you have access to.
            ' The workbook must be in a trusted location.
            ' If workbookPath is a UNC path, the application 
            ' must be on the same computer as the server.
            ' string targetWorkbookPath = 
            ' @"\\\\MyServer\\myxlfiles\\Formulas.xlsx";
            Dim targetWorkbookPath As String = "http://myserver02/DocLib/Shared%20Documents/Basic1.xlsx"
            ' Set credentials for requests
            xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials

            Try
                ' Call the OpenWorkbook method and point to the 
                ' trusted location of the workbook to open.
                Dim sessionId As String = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", "en-US", outStatus)
                Console.WriteLine("sessionID : {0}", sessionId)
                ' Prepare object to define range coordinates, 
                ' and call the GetRange method.
                rangeCoordinates.Column = 0
                rangeCoordinates.Row = 0
                rangeCoordinates.Height = 18
                rangeCoordinates.Width = 10

                Dim rangeResult1() As Object = xlservice.GetRange(sessionId, sheetName, rangeCoordinates, False, outStatus)
                Console.WriteLine("Total rows in range: " &amp; rangeResult1.Length)

                Console.WriteLine("Sum in last column is: " &amp; (CType(rangeResult1(2), Object()))(3))

               ' Close the workbook. This also closes the session.
                xlservice.CloseWorkbook(sessionId)
            Catch e As SoapException
                Console.WriteLine("SOAP Exception Error Code: {0}", e.SubCode.Code.Name)
                Console.WriteLine("SOAP Exception Message is: {0}", e.Message)

            Catch e As Exception
                Console.WriteLine("Exception Message: {0}", e.Message)
            End Try
            Console.ReadLine()
        End Sub
    End Class
End Namespace
```


## 関連項目


#### タスク


  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
  
    
    
 [方法: Excel クライアントからサーバーへの保存](how-to-save-from-excel-client-to-the-server.md)
  
    
    
 [SubCode プロパティを使用してエラー コードをキャプチャする方法](how-to-use-the-subcode-property-to-capture-error-codes.md)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [SOAP 呼び出しのループバックおよび直接リンク](loop-back-soap-calls-and-direct-linking.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
