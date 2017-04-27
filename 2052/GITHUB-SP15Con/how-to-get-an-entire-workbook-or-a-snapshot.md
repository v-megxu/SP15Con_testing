---
title: 如何：获取整个工作簿或快照
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: 39115503-8352-4589-87f4-cfa9c07260b6
---


# 如何：获取整个工作簿或快照

本示例说明如何使用 Excel Web Services，来获取整个工作簿、整个文件的快照或仅可查看工作表或对象的快照。如果您想保存最新工作簿的副本、将其存储在某个位置或发送给某人，等等，获取工作簿或快照将非常有用。
  
    
    

快照是由 Excel Calculation Services 生成的工作簿，它显示了 Excel Services 会话中的工作簿的最新状态。有些快照（称为"已发布项目快照"）仅包含作者在将文件保存到服务器时选择为可查看的 Excel 文件部分内容。快照包含原始文件的布局和格式以及 Excel Calculation Services 计算的最新值，但不包含 Excel 公式或外部数据连接。Excel Services 打开服务器上的 Excel 文件、刷新数据源并计算所有 Excel 公式。当用户或应用程序请求快照时，Excel Services 将生成快照并通过 Web 服务 API 将其发回。
您可以获取已保存到服务器的工作簿的快照，即使您没有权限访问服务器上的实际文件。
  
    
    

您使用 Web 服务的 **GetWorkbook** 方法获取整个工作簿或其中一种快照类型。例如，以下代码将返回整个 Excel 工作簿的快照。它使用 **WorkbookType.FullSnapshot** 枚举作为 **GetWorkbook** 方法中的第二个参数。


```cs

byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, out status);
```




```VB.net
Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, status)
```

 **GetWorkbook** 方法将以与加载到会话中的字节数组相同的 Excel 文件格式返回一个字节数组。要获取 Excel 工作簿作者在将工作簿从 Excel 保存到服务器时选择为可查看的项目的快照，请使用如下所示的 **WorkbookType.PublishedItemsSnapshot** 枚举：


```cs
byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.PublishedItemsSnapshot, out status);
```




```VB.net
Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, status)
```

要获取处于最新会话状态的整个工作簿的快照，请使用 **WorkbookType.FullWorkbook** 枚举：


```cs
byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);
```




```VB.net
Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, status)
```

仅当用户具有文件的打开权限时， **WorkbookType.FullWorkbook** 选项才可用；如果用户只有仅查看权限，调用将失败。在某些情况下，您的代码需要保存 **GetWorkbook** 调用的结果。有关如何保存工作簿的讨论，请参阅示例 [如何：保存工作簿](http://msdn.microsoft.com/library/feb74f7a-2d8f-4672-911b-de85f8852aea%28Office.15%29.aspx)。有关 **GetWorkbook** 方法和 **WorkbookType** 枚举的详细信息，请参阅 Excel Web Services 参考文档。
## 示例

以下程序（控制台应用程序）接收到一个命令行参数，即服务器上的工作簿的路径。程序调用 Web 服务以打开服务器上的工作簿并获取快照。然后它将写入到标准输出，使您可以将其重定向到新的快照文件。 
  
    
    

```cs
using System;
using System.IO;
using System.Text;
using System.Web.Services.Protocols;
// TODO: Change the using GetSnapshot.myServer02 statement 
// to point to the Web service you are referencing.
using GetSnapshot.myServer02;

namespace GetSnapshot
{
    class ExcelServicesSnapshot
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length < 1)
                {
                    Console.Error.WriteLine("Command line arguments should be: GetSnapshot [workbook_path] > [snapshot_filename]");
                    return;
                }
                // Instantiate the Web service and 
                // create a status array object.
                ExcelService xlService = new ExcelService();
                Status[] status;
                
                xlService.Timeout = 600000;
                // Set credentials for requests.
                // Use the current user's logon credentials.
                xlService.Credentials =   
                    System.Net.CredentialCache.DefaultCredentials;
                 
                // Open the workbook, then call GetWorkbook 
                // and close the session.
                string sessionId = xlService.OpenWorkbook(args[0], "en-US", "en-US", out status);
                byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.PublishedItemsSnapshot, out status);
                // byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);
                // byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, out status);

                // Close the workbook. This also closes the session.
                status = xlService.CloseWorkbook(sessionId);

                // Write the resulting Excel file to stdout 
                // as a binary stream.
                BinaryWriter binaryWriter = new BinaryWriter(Console.OpenStandardOutput());
                binaryWriter.Write(workbook);
                binaryWriter.Close();
            }

            catch (SoapException e)
            {
                Console.WriteLine("SOAP Exception Message: {0}", e.Message);
            }

            catch (Exception e)
            {
                Console.WriteLine("Exception Message: {0}", e.Message);
            }   
        } 
    }
}
```


```VB.net

Imports System
Imports System.IO
Imports System.Text
Imports System.Web.Services.Protocols
' TODO: Change the using GetSnapshot.myServer02 statement 
' to point to the Web service you are referencing.
Imports GetSnapshot.myServer02

Namespace GetSnapshot
    Friend Class ExcelServicesSnapshot
        Shared Sub Main(ByVal args() As String)
            Try
                If args.Length < 1 Then
                    Console.Error.WriteLine("Command line arguments should be: GetSnapshot [workbook_path] > [snapshot_filename]")
                    Return
                End If
                ' Instantiate the Web service and 
                ' create a status array object.
                Dim xlService As New ExcelService()
                Dim status() As Status

                xlService.Timeout = 600000
                ' Set credentials for requests.
                ' Use the current user's logon credentials.
                xlService.Credentials = System.Net.CredentialCache.DefaultCredentials

                ' Open the workbook, then call GetWorkbook 
                ' and close the session.
                Dim sessionId As String = xlService.OpenWorkbook(args(0), "en-US", "en-US", status)
                Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.PublishedItemsSnapshot, status)
                ' byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);
                ' byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, out status);

                ' Close the workbook. This also closes the session.
                status = xlService.CloseWorkbook(sessionId)

                ' Write the resulting Excel file to stdout 
                ' as a binary stream.
                Dim binaryWriter As New BinaryWriter(Console.OpenStandardOutput())
                binaryWriter.Write(workbook)
                binaryWriter.Close()

            Catch e As SoapException
                Console.WriteLine("SOAP Exception Message: {0}", e.Message)

            Catch e As Exception
                Console.WriteLine("Exception Message: {0}", e.Message)
            End Try
        End Sub
    End Class
End Namespace
```

使用以下命令行和参数运行 GetSnapshot 应用程序： 
  
    
    



```

GetSnapshot.exe [workbook_path] > [snapshot_filename]
```

例如： 
  
    
    



```
C:\\>GetSnapshot.exe http://myServer02/reports/reports/OriginalWorkbook.xlsx > SnapshotCopy.xlsx
```

如果您使用前面的命令行示例，GetSnapshot 工具会将新的文件放置在"C:\\"目录中。
  
    
    

> **注释**
> 要获取快照的工作簿必须位于受信任位置。 
  
    
    


## 可靠编程

确保您添加了有权访问的 Excel Web Services 网站的 Web 引用。将  `using GetSnapshot.myServer02;` 语句更改为指向您引用的 Web 服务站点。
  
    
    

## 另请参阅


#### 任务


  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
#### 其他资源


  
    
    
 [步骤 1：创建 Web 服务客户端项目](step-1-creating-the-web-service-client-project.md)
  
    
    
 [步骤 2：添加 Web 引用](step-2-adding-a-web-reference.md)
  
    
    
 [步骤 3：访问 Web 服务](step-3-accessing-the-web-service.md)
  
    
    
 [步骤 4：构建和测试应用程序](step-4-building-and-testing-the-application.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
