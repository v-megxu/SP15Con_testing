---
title: 如何：使用 SubCode 属性捕获错误代码
keywords: how to,howdoi,howto,subcode
f1_keywords:
- how to,howdoi,howto,subcode
ms.prod: SHAREPOINT
ms.assetid: 8ce4d5b2-111b-49e7-9d07-8c2c586221ec
---


# 如何：使用 SubCode 属性捕获错误代码

当 Excel Services 中发生错误时，=Excel Services 将在 SOAP 异常中生成错误。为了使开发人员更容易捕获特定的错误条件，Excel Calculation Services 警报具有一个相关的错误代码。Excel Web Services 将使用= **SoapException** 类中的属性返回错误。
  
    
    

以下示例说明如何使用 **SoapException** 类的 [SubCode](http://msdn.microsoft.com/library/frlrfSystemWebServicesProtocolsSoapExceptionClassSubCodeTopic.aspx) 属性 (http://msdn.microsoft.com/zh-cn/library/system.web.services.protocols.soapexception.subcode.aspx) 来捕获错误代码。
> **注释**
> 要使用 **SubCode** 属性，您必须使用 Microsoft Visual Studio 2005。 **SubCode** 属性在 Visual Studio 的早期版本中不存在。
  
    
    

有关错误代码的列表，请参阅  [Excel Services 错误代码](excel-services-error-codes.md)。
### 使用 SOAP 时捕获错误代码


1. 添加对 Excel Web Services 的 Web 引用后，使用指令添加以下内容，确保您的完整命名空间无需符合 **SoapException** 类即可使用它：
    
  ```cs
  
using System.Web.Services.Protocols;
  ```


  ```VB.net
  Imports System.Web.Services.Protocols
  ```

2. 要使用 **SubCode** 属性捕获 Excel Services 错误代码，您必须使用 SOAP12 协议版本。实例化 Excel Web Services 属性类之后，如下所示设置 SOAP 协议版本：
    
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

3. 要使用 **SubCode** 属性捕获错误代码，请将 SOAP 异常捕获块添加会您的代码，例如：
    
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


### 使用直接链接时捕获错误代码


1. 在直接链接方案中，您无需添加对 Excel Web Services 的 Web 引用。但是，您需要添加对 **System.Web.Services** 命名空间的引用。
    
  
2. 添加引用后，将以下 **using** 指令添加到您的代码中，确保您的完整命名空间无需符合 **SoapException** 类即可使用它：
    
  ```cs
  
using System.Web.Services.Protocols;
  ```


  ```VB.net
  Imports System.Web.Services.Protocols
  ```

3. 与使用 SOAP over HTTP 不同，在直接链接方案中，您无需设置 SOAP 协议版本。 
    
  
4. 要使用 **SubCode** 属性捕获错误代码，请将 SOAP 异常捕获块添加会您的代码，例如：
    
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


## 示例

以下程序（控制台应用程序）使用 **SubCode** 属性捕获错误代码。程序根据捕获的错误代码采取不同操作。例如，您可能无意中传递了一个不存在的工作表名称，导致触发 SOAP 异常。在这种情况下，将返回以下 SOAP 异常消息：
  
    
    

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


## 可靠编程

确保您添加了有权访问的 Excel Web Services 网站的 Web 引用。将  `using SubCodeExample;` 语句更改为指向您引用的 Web 服务站点。
  
    
    
此外，根据需要对工作簿路径、工作表名称等进行更改。
  
    
    

## 另请参阅


#### 任务


  
    
    
 [如何：捕获异常](how-to-catch-exceptions.md)
  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
  
    
    
 [如何：从 Excel 客户端保存到服务器](how-to-save-from-excel-client-to-the-server.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
