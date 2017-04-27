---
title: 步骤 3：访问 Web 服务
ms.prod: SHAREPOINT
ms.assetid: d27f654d-242f-4f34-8385-be857c170532
---


# 步骤 3：访问 Web 服务

在项目中添加对 Excel Web Services 的引用后，下一步是创建 Web 服务代理类的实例。然后您可以通过调用代理类中的方法来访问 Web 服务的方法。当您的应用程序调用这些方法时，Visual Studio 生成的代理类代码将处理应用程序和 Web 服务之间的通信。 
  
    
    

首先创建 Web 服务代理类的实例 ExcelWebService。接下来您使用该代理类调用 Web 服务的多个方法和属性。 
您使用调用打开工作簿、获取会话 ID、传递默认凭据、定义范围协调对象、获取使用范围协调对象的范围、关闭工作簿以及捕获 SOAP 异常。
  
    
    


## 访问 Web 服务


### 添加指令


1. 当您在之前已添加 Web 引用时，它在名为 <yourProject>.<webReferenceName> 的命名空间中创建了一个名为 ExcelService 的对象。在本示例中，对象名为 SampleApplication.ExcelWebService。本演练还说明了如何捕获 SOAP 异常。为此，您可使用 **System.Web.Services.Protocols** 对象。 **System.Web.Services.Protocols** 命名空间由定义用于在 XML Web 服务客户端和使用 ASP.NET 创建的 XML Web 服务之间进行通信时，通过网络传送数据的协议的类组成。
  
    
    
为便于使用这些对象，您必须首先将命名空间作为指令添加到 Class1.cs 文件中。这样，如果您使用这些指令，您无需完全符合命名空间中的类型。 
    
  
2. 要添加这些指令，请将以下代码添加到 Class1.cs 文件中代码的开头，在  `using System:` 之后
    
  ```cs
  
using SampleApplication.ExcelWebService;
using System.Web.Services.Protocols;
  ```


  ```VB.net
  
Imports SampleApplication.ExcelWebService
Imports System.Web.Services.Protocols
  ```


### 调用 Web 服务


1. 在  `static void Main(string[] args)` 中的左括号之后添加以下代码，来实例化和初始化 Web 服务代理对象：
    
  ```cs
  
ExcelService es = new ExcelService();
  ```


  ```VB.net
  Dim es As New ExcelService()
  ```

2. 添加以下代码以创建状态数组和范围坐标对象：
    
  ```cs
  Status[] outStatus;
RangeCoordinates rangeCoordinates = new RangeCoordinates();
  ```


  ```VB.net
  
Dim outStatus() As Status
Dim rangeCoordinates As New RangeCoordinates()
  ```

3. 添加代码，以指向您要访问的工作表。在本示例中，工作表名为"Sheet1"。将以下内容添加到您的代码中： 
    
  ```cs
  
string sheetName = "Sheet1";
  ```


  ```VB.net
  Dim sheetName As String = "Sheet1"
  ```


    > **注释**
      > 确保您要打开的工作簿具有一个名为"Sheet1"、包含值的工作表。或者，您可以将代码中的"Sheet1"更改为工作表的名称。 
4.  `Add the following code to point to the workbook you want to open`：
    
  ```cs
  string targetWorkbookPath = "http://myserver02/example/Shared%20Documents/Book1.xlsx";
  ```


  ```VB.net
  Dim targetWorkbookPath As String = "http://myserver02/example/Shared%20Documents/Book1.xlsx"
  ```


    > **重要信息**
      > 更改工作簿路径，以匹配您在本演练中使用的工作簿的位置。确保该工作簿存在且该工作簿保存的位置是一个受信任的位置。使用 HTTP URL 指向工作簿的位置，将允许您对其进行远程访问。 

    > **注释**
      > 您可以获取 Microsoft SharePoint Server 2010 中工作簿的路径，方法是右键单击该工作簿，然后选择"复制快捷方式"。或者您可以选择"属性"并从属性中复制工作簿的路径。 
5. 添加以下代码以设置请求的凭据。 
    
    > **注释**
      > 您必须显式地设置凭据，即使您想使用默认凭据。 

  ```cs
  es.Credentials = System.Net.CredentialCache.DefaultCredentials;
  ```


  ```VB.net
  es.Credentials = System.Net.CredentialCache.DefaultCredentials
  ```

6. 添加以下代码以打开该工作簿，然后指向工作簿所在的受信任位置。将代码放置在 **try** 块中：
    
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

7. 添加以下代码，使某个对象做好定义范围坐标的准备，然后调用 **GetRange** 方法。代码还将显示范围中的总行数和特定范围中的值。
    
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

8. 添加代码以关闭工作簿并关闭当前会话。另外添加右括号以结束 **try** 块。
    
    > **重要信息**
      > 比较好的做法是在会话完成后关闭工作簿。这将关闭会话并释放资源。 

  ```cs
  
es.CloseWorkbook(sessionId);
}
  ```


  ```VB.net
  
es.CloseWorkbook(sessionId)
  ```

9. 添加 **catch** 块以捕获 SOAP 异常并显示异常消息：
    
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


## 完整代码

以下代码示例是上述步骤中所述 Class1.cs 示例文件中的完整代码。
  
    
    

> **重要信息**
> 根据需要对工作簿路径、工作表名称等进行更改。 
  
    
    


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


## 另请参阅


#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
#### 其他资源


  
    
    
 [步骤 1：创建 Web 服务客户端项目](step-1-creating-the-web-service-client-project.md)
  
    
    
 [步骤 2：添加 Web 引用](step-2-adding-a-web-reference.md)
  
    
    
 [步骤 4：构建和测试应用程序](step-4-building-and-testing-the-application.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
  
    
    
 [如何：使用脚本信任工作簿位置](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)
