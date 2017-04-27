---
title: SubCode プロパティを使用してエラー コードをキャプチャする方法
keywords: how to,howdoi,howto,subcode
f1_keywords:
- how to,howdoi,howto,subcode
ms.prod: SHAREPOINT
ms.assetid: 8ce4d5b2-111b-49e7-9d07-8c2c586221ec
---


# SubCode プロパティを使用してエラー コードをキャプチャする方法

Excel Services は、Excel Services で発生するエラーに基づいて、SOAP 例外でエラーを生成します。開発者が特定のエラーの条件をキャッチしやすくするため、Excel Calculation Services の警告にはエラー コードが関連付けられています。Excel Web Services は、 **SoapException** クラスのプロパティを使用してエラーを返します。
  
    
    

次の使用例は、 **SoapException** クラスの [SubCode](http://msdn.microsoft.com/library/frlrfSystemWebServicesProtocolsSoapExceptionClassSubCodeTopic.aspx) プロパティ (http://msdn.microsoft.com/ja-jp/library/system.web.services.protocols.soapexception.subcode.aspx) を使用してエラー コードをキャプチャする方法を示します。
> **メモ**
> **SubCode** プロパティを使えるようにするには、Microsoft Visual Studio 2005 を使用する必要があります。 **SubCode** プロパティは、これより前のバージョンの Visual Studio には存在しません。
  
    
    

エラー コードの一覧については、「 [Excel Services のエラー コード](excel-services-error-codes.md)」を参照してください。
### SOAP の使用時にエラー コードをキャプチャするには


1. Web 参照を Excel Web Services に追加した後、完全な名前空間で修飾しなくても **SoapException** クラスを使用できるように、ディレクティブを使用して以下を追加します。
    
  ```cs
  
using System.Web.Services.Protocols;
  ```


  ```VB.net
  Imports System.Web.Services.Protocols
  ```

2. **SubCode** プロパティを使用して Excel Services のエラー コードをキャプチャするには、SOAP12 プロトコル バージョンを使用する必要があります。Excel Web Services プロキシ クラスにインスタンスを作成した後、次のように SOAP プロトコル バージョンを設定します。
    
  ```cs
  // Instantiate the Web service.
 ExcelService xlservice = new ExcelService();

// Set the SOAP protocol version.           
xlservice.SoapVersion = SoapProtocolVersion.Soap12;
  ```


  ```VB.net
  
' Instantiate the Web service.
 Dim xlservice As New ExcelService()

' Set the SOAP protocol version.           
xlservice.SoapVersion = SoapProtocolVersion.Soap12
  ```

3. **SubCode** プロパティを使用してエラー コードをキャッチするには、たとえば次のように、SOAP 例外の catch ブロックをコードに追加します。
    
  ```cs
  
catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Message: {0}", e.Message);
    Console.WriteLine("SOAP Exception Error Code: {0}", 
        e.SubCode.Code.Name);
}
  ```


  ```VB.net
  
Catch e As SoapException
    Console.WriteLine("SOAP Exception Message: {0}", e.Message)
    Console.WriteLine("SOAP Exception Error Code: {0}", e.SubCode.Code.Name)
End Try
  ```


### 直接リンクの使用時にエラー コードをキャプチャするには


1. 直接リンクのシナリオでは、Excel Web Services に Web 参照を追加する必要はありません。ただし、 **System.Web.Services** の名前空間への参照を追加する必要があります。
    
  
2. 参照を追加したら、完全な名前空間で修飾しなくても **SoapException** クラスを使用できるように、次の **using** ディレクティブをコードに追加します。
    
  ```cs
  
using System.Web.Services.Protocols;
  ```


  ```VB.net
  Imports System.Web.Services.Protocols
  ```

3. 直接リンクのシナリオでは、SOAP over HTTP を使用するのとは異なり、SOAP プロトコルのバージョンを設定する必要がありません。 
    
  
4. **SubCode** プロパティを使用してエラー コードをキャッチするには、たとえば次のように、SOAP 例外の catch ブロックをコードに追加します。
    
  ```cs
  catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Message: {0}", e.Message);
    Console.WriteLine("SOAP Exception Error Code: {0}", 
        e.SubCode.Code.Name);
}
  ```


  ```VB.net
  
Catch e As SoapException
    Console.WriteLine("SOAP Exception Message: {0}", e.Message)
    Console.WriteLine("SOAP Exception Error Code: {0}", e.SubCode.Code.Name)
End Try
  ```


## 例

次のプログラム (コンソール アプリケーション) では、 **SubCode** プロパティを使用してエラー コードをキャプチャします。プログラムは、キャッチしたエラー コードに基づいて異なる対応をします。たとえば、意図的に存在しないシート名を渡して SOAP 例外をトリガーすることができます。この場合は、次の SOAP 例外メッセージが返されます。
  
    
    

```

The sheet that was requested could not be found. Please try a different one.
```


```cs
using System;
using System.Collections.Generic;
using System.Text;
using System.Web.Services.Protocols;
using System.Threading;
using SubCodeExample;

namespace SubCodeExample
{
    class Program
    {
        static void Main(string[] args)
        {
            if (args.Length != 3)
            {
                Console.WriteLine("This program requires 3 parameters - 
                    workbook, sheet and cell");
            }
            string workbookUrl = args[0];
            string sheetName = args[1];
            string cellRange = args[2];

            const string DataRefreshError = 
                "ExternalDataRefreshFailed";
            const string InvalidSheetNameError = "InvalidSheetName";
            const string FileOpenNotFound = "FileOpenNotFound";

            string sessionId = null;
            MyXlServices.ExcelService service = null;
            try
            {
                MyXlServices.Status[] status;
                service = new 
                    SubCodeExample.MyXlServices.ExcelService();
                service.SoapVersion = SoapProtocolVersion.Soap12;
                service.Credentials = 
                    System.Net.CredentialCache.DefaultCredentials;
                sessionId = service.OpenWorkbook(workbookUrl, "", "", 
                    out status);

                object result = service.GetCellA1(sessionId, sheetName, 
                    cellRange, true, out status);
                Console.WriteLine("GetCell result was:{0}", result);

                int retries = 3;
                while (retries > 0)
                {
                    try
                    {
                        service.Refresh(sessionId, "");
                    }
                    catch (SoapException soapException)
                    {
                        bool rethrow = true;
                        if (soapException.SubCode.Code.Name == 
                            DataRefreshError)
                        {
                            if (retries > 1)
                            {
                                Console.WriteLine("Error when 
                                    refreshing. Retrying...");
                                Thread.Sleep(5000);
                                rethrow = false;
                            }
                        }
                        if (rethrow) throw;
                    }
                    retries--;
                }
                
            }
            catch (SoapException exception)
            {
                string subCode = exception.SubCode.Code.Name;
                if (subCode == FileOpenNotFound)
                {
                    Console.WriteLine("The workbook could not be found. 
                        Change the first argument to be 
                        a valid file name.");
                }
                else if (subCode == DataRefreshError)
                {
                    Console.WriteLine("Could not refresh 
                        the workbook.");
                }
                else if (subCode == InvalidSheetNameError)
                {
                    Console.WriteLine("The sheet that was requested 
                        could not be found. Please try 
                        a different one.");
                }
                else
                {
                    Console.WriteLine("Unknown error code returned from 
                        Excel Services:{0}", subCode);
                }
            }
            
            catch (Exception)
            {
                Console.WriteLine("Unknown exception was raised.");
            }
            finally
            {
                if (service != null &amp;&amp; 
                    !String.IsNullOrEmpty(sessionId))
                {
                    try
                    {
                        service.CloseWorkbook(sessionId);
                    }
                    catch
                    {
                    }
                }
            }
        }
    }
}

```


```VB.net

Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Web.Services.Protocols
Imports System.Threading
Imports SubCodeExample

Namespace SubCodeExample
    Friend Class Program
        Shared Sub Main(ByVal args() As String)
            If args.Length <> 3 Then
                Console.WriteLine("This program requires 3 parameters - workbook, sheet and cell")
            End If
            Dim workbookUrl As String = args(0)
            Dim sheetName As String = args(1)
            Dim cellRange As String = args(2)

            Const DataRefreshError As String = "ExternalDataRefreshFailed"
            Const InvalidSheetNameError As String = "InvalidSheetName"
            Const FileOpenNotFound As String = "FileOpenNotFound"

            Dim sessionId As String = Nothing
            Dim service As MyXlServices.ExcelService = Nothing
            Try
                Dim status() As MyXlServices.Status
                service = New SubCodeExample.MyXlServices.ExcelService()
                service.SoapVersion = SoapProtocolVersion.Soap12
                service.Credentials = System.Net.CredentialCache.DefaultCredentials
                sessionId = service.OpenWorkbook(workbookUrl, "", "", status)

                Dim result As Object = service.GetCellA1(sessionId, sheetName, cellRange, True, status)
                Console.WriteLine("GetCell result was:{0}", result)

                Dim retries As Integer = 3
                Do While retries > 0
                    Try
                        service.Refresh(sessionId, "")
                    Catch soapException As SoapException
                        Dim rethrow As Boolean = True
                        If soapException.SubCode.Code.Name = DataRefreshError Then
                            If retries > 1 Then
                                Console.WriteLine("Error when refreshing. Retrying...")
                                Thread.Sleep(5000)
                                rethrow = False
                            End If
                        End If
                        If rethrow Then
                            Throw
                        End If
                    End Try
                    retries -= 1
                Loop

            Catch exception As SoapException
                Dim subCode As String = exception.SubCode.Code.Name
                If subCode = FileOpenNotFound Then
                    Console.WriteLine("The workbook could not be found. Change the first argument to be a valid file name.")
                ElseIf subCode = DataRefreshError Then
                    Console.WriteLine("Could not refresh the workbook.")
                ElseIf subCode = InvalidSheetNameError Then
                    Console.WriteLine("The sheet that was requested could not be found. Please try a different one.")
                Else
                    Console.WriteLine("Unknown error code returned from Excel Services:{0}", subCode)
                End If

            Catch e1 As Exception
                Console.WriteLine("Unknown exception was raised.")
            Finally
                If service IsNot Nothing AndAlso (Not String.IsNullOrEmpty(sessionId)) Then
                    Try
                        service.CloseWorkbook(sessionId)
                    Catch
                    End Try
                End If
            End Try
        End Sub
    End Class
End Namespace
```


## 堅牢なプログラミング

アクセスできる Excel Web Services サイトに対して必ず Web 参照を追加するようにします。参照している Web サービス サイトを指すように  `using SubCodeExample;` ステートメントを変更します。
  
    
    
加えて、必要に応じてブックのパス、シート名などを変更します。
  
    
    

## 関連項目


#### タスク


  
    
    
 [例外をキャッチする方法](how-to-catch-exceptions.md)
  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
  
    
    
 [方法: Excel クライアントからサーバーへの保存](how-to-save-from-excel-client-to-the-server.md)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [SOAP 呼び出しのループバックおよび直接リンク](loop-back-soap-calls-and-direct-linking.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
