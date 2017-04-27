---
title: 如何：捕获异常
keywords: errors,how to,howdoi,howto
f1_keywords:
- errors,how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: de5fdb67-201b-4d7a-90a8-99ab7e51ea4e
---


# 如何：捕获异常

您将可能抛出异常的代码部分放置在 try 块中，将处理异常的代码block 放置在 catch 块中。捕获语句的顺序非常重要。当发生异常时，它将放弃堆栈，且每个 catch 块都有机会处理异常。通过将异常类型与 catch 块中指定的异常名称相匹配，来确定应处理异常的 catch 块。例如，下列 catch 块可捕获简单对象访问协议 (SOAP) 异常：
  
    
    


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

如果不存在类型特定的 catch 块，常规 catch 块（如果有）将捕获到异常。例如，您可以通过添加以下代码来捕获常规异常：


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

您将针对特定类型的异常的 catch 块放置在常规异常前面。 公共语言运行时捕获 catch 块未捕获到的异常。根据运行时的配置方式，将显示调试对话框，或者程序将通知执行并显示包含异常信息的对话框。有关调试的信息，请参阅 [调试和分析应用程序](http://go.microsoft.com/fwlink/?LinkId=64641) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpguide/html/cpcondebuggingprofiling.asp)。有关如何处理异常的详细信息，请参阅 [处理异常的最佳实践](http://go.microsoft.com/fwlink/?LinkId=64480) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpguide/html/cpconbestpracticesforhandlingexceptions.asp)。
## 示例


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


## 另请参阅


#### 任务


  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
  
    
    
 [如何：从 Excel 客户端保存到服务器](how-to-save-from-excel-client-to-the-server.md)
  
    
    
 [如何：使用 SubCode 属性捕获错误代码](how-to-use-the-subcode-property-to-capture-error-codes.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
