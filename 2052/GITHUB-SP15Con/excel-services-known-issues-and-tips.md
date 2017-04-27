---
title: Excel Services 已知问题和提示
ms.prod: SHAREPOINT
ms.assetid: b4a41437-4f00-4f88-8510-627fa0252004
---


# Excel Services 已知问题和提示

下面是用于处理 Excel Services 的已知问题和提示。
  
    
    


## Excel Web Service


### 查看 WSDL 位置

您可以在服务器上导航到以下 URL，以查看 Excel Web Services Web Services 描述语言 (WSDL) 页面： `http://<server>/<customsite>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
如果您没有自定义网站，您可以通过使用以下 URL 来查看 WSDL：
  
    
    
 `http://<server>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
有关详细信息，请参阅 [访问 SOAP API](accessing-the-soap-api.md)。
  
    
    

### 了解 Excel Web Services 和命名空间

下面是 Excel Web Services 和命名空间：
  
    
    

- 包含所有 API 方法的单个 Web 服务对象： **ExcelService**
    
  
- 架构命名空间： `http://schemas.microsoft.com/office/excel/server/webservices`
    
  
- Web 服务页面名称：ExcelService.asmx
    
  

### 在本地链接或链接到 Web 服务

在某些方案中，您应该直接链接到 Microsoft.Office.Excel.Server.WebServices.dll 并像访问任何本地程序集一样对其进行访问，而非通过 SOAP over HTTP 调用 Web 服务。 
  
    
    
有关何时使用直接链接的详细信息和指南，请参阅 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)。
  
    
    

### 了解无效字符

如果工作簿单元格包含在 XML 响应中无效的字符，调用 **GetCell** 和 **GetRange** 方法将失败。
  
    
    
例如，如果单元格包含具有 16 进制值 0x1、0x2 ... 0x8 的字符，ASP.NET 解析器将抛出异常，指示写入到 XML 响应的字符的值无效：
  
    
    
 **System.InvalidOperationException：客户端找到响应内容类型"text/html; charset=utf-8"，但预期值为"text/xml"。请求失败，并返回错误消息：-- <html> <head> <title>' ', hexadecimal value 0x01, is an invalid character.</title>**
  
    
    
这是预期行为。定义哪些字符在有效 XML 响应中被允许的 XML 规范指定 16 进制值 0x1、0x2 ... 0x8 为无效的 XML 字符：
  
    
    
 **Char ::= #x9 | #xA | #xD | [#x20-#xD7FF] | [#xE000-#xFFFD] | [#x10000-#x10FFFF] /* 任何 Unicode 字符，不包括替代块 FFFE 和 FFFF。*/**
  
    
    
有关详细信息，请参阅  [W3C 可扩展标记语言 (XML) 规范](http://www.w3.org/TR/REC-xml) (http://www.w3.org/TR/REC-xml#NT-Char)。
  
    
    

### 保存工作簿

对工作簿进行更改时例如，使用 Excel Web Services 将值设置为范围对工作簿的更改将仅为该特定会话保存。更改不会保存到原始工作簿中。当前工作簿会话结束时（例如，当您调用 **CloseWorkbook** 方法时，或当会话超时时），您所做的更改将丢失。
  
    
    
如果您想将更改保存到工作簿，可以使用 **GetWorkbook** 方法，然后使用目标文件存储的 API 保存工作簿。有关详细信息，请参阅 [如何：获取整个工作簿或快照](how-to-get-an-entire-workbook-or-a-snapshot.md)和 [如何：保存工作簿](http://msdn.microsoft.com/library/feb74f7a-2d8f-4672-911b-de85f8852aea%28Office.15%29.aspx)。
  
    
    

### 了解 Excel Web Services 代理类的URL 属性

请勿对您想要打开的工作簿的位置使用 Excel Web Services 代理的 **Url** 属性。由 Visual Studio 生成的 Web 服务代理类的 **Url** 属性可获取或设置客户端请求的 XML Web 服务的基 URL。如果使用 Excel Web Services，则通常：
  
    
    
 `http://<server name>/_vti_bin/ExcelService.asmx`
  
    
    
要指定工作簿的位置，请使用 **OpenWorkbook** 方法而非 **Url** 属性，如以下代码示例中所示。
  
    
    



```

//Instantiate the web service and make a status array object.
ExcelService xlservice = new ExcelService();
string sheetName = "Sheet1";         

//Set the path to the workbook to open.
//TODO: Change the path to the workbook
 //to point to a workbook you have access to.
//The workbook must be in a trusted location.
string targetWorkbookPath = 
   "http://myserver02/example/Shared%20Documents/Book1.xlsx";

//Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials;

//Call the open workbook, and point to the trusted   
//location of the workbook to open.
string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", 
    "en-US", out outStatus);
                
```

有关详细信息，请参阅  [WebClientProtocol.Url 属性](http://go.microsoft.com/fwlink/?LinkId=64908) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpref/html/frlrfSystemWebServicesProtocolsWebClientProtocolClassUrlTopic.asp)。
  
    
    

## 了解安全性


### 使用工作簿权限

请注意下列有关工作簿权限的问题：
  
    
    

- Excel Web Services 使用 Microsoft SharePoint Foundation 授权架构验证调用者是否有权调用 SharePoint Foundation 网站（即 Excel Web Services 所在的网站）上的 API（即进行 Web 服务调用）。如果调用者没有"使用远程 API"的权限，Excel Web Services 将返回"HTTP 401 (未授权)"错误，并记录"API 授权失败"事件。Excel Web Services 仅对作为 SOAP 调用发起的调用执行这些授权检查。从在本地链接到 Microsoft.Office.Excel.Server.WebServices.dll 的应用程序发起的调用不视为远程调用，因此无需进行授权检查。但是，如果从本地链接到 Microsoft.Office.Excel.Server.WebServices.dll 的应用程序本身是 SOAP 服务并处理服务的 SOAP 调用，Excel Web Services 调用看起来将类似于 SOAP 调用（尽管应用程序直接链接到 Microsoft.Office.Excel.Server.WebServices.dll）。在这种情况下，Excel Web Services 将执行授权检查。
    
  
- 要获取整个工作簿（例如，通过调用使用  `WorkbookType.FullWorkbook` 属性的 **GetWorkbook** 方法），调用者需要具备工作簿的"打开"权限或文件共享的"读取"权限。
    
  
- 调用 **GetApiVersion** 方法无需权限。
    
  
- 对于除凭据以外的其余 Excel Web Services 方法，调用者需要具备工作簿的"查看"权限（在 SharePoint Foundation 中）或"读取"权限（在文件共享中）。
    
  

### 受信任位置

您想在 Excel Services 中打开的工作簿必须位于受信任位置。否则 Excel Web Services 调用以打开工作簿将失败。
  
    
    
有关如何信任某个位置的信息，请参阅 [如何：信任位置](how-to-trust-a-location.md)和 [如何：使用脚本信任工作簿位置](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)。
  
    
    

## Visual Studio


### Microsoft Visual Studio 代理行为

当 Microsoft Visual Studio 为调用 Excel Web Services 的客户端项目创建代理类时，将具有以下行为： 
  
    
    
如果方法没有返回值和一个或多个 **out** 参数，第一个 **out** 参数将变为返回值。即，代理类中的方法在方法签名中将少一个 **out** 参数。但签名将具有返回值，且其类型和内容是过去第一个 **out** 参数的类型和内容。
  
    
    
受影响的 Excel Web Services 方法包括：
  
    
    

- **Calculate**
    
  
- **CalculateA1**
    
  
- **CalculateWorkbook**
    
  
- **CancelRequest**
    
  
- **CloseWorkbook**
    
  
- **GetSessionInformation**
    
  
- **Refresh**
    
  
- **SetCell**
    
  
- **SetCellA1**
    
  
- **SetRange**
    
  
- **SetRangeA1**
    
  

## Excel Services 用户定义函数


### 首先检查全局程序集缓存，然后检查本地文件夹

根据 Microsoft .NET Framework 的设计，将加载全局程序集缓存中的程序集，而非本地文件夹中的同一程序集。公共语言运行时将首先在全局程序集缓存中查找程序集，然后搜索本地文件夹。
  
    
    
因此，如果程序集已安装在全局程序集缓存中且位于 UDF 列表中但被禁用（或已从 UDF 列表中删除），且同一程序集已安装在本地文件夹中并启用，仍将加载并使用全局程序集缓存中的程序集，而非本地文件夹中的同一程序集。
  
    
    
这不会影响已修改程序集版本（意味着程序集不再相同）的升级方案。
  
    
    

## 常规


### 不会保持 Sharedstring.xml 中的字符串顺序

Excel Services 不会保持工作簿共享字符串表中字符串的原始顺序（Microsoft Office Excel XML 格式 文件中的 Sharedstrings.xml 部分）。例如，执行以下步骤：
  
    
    

1. 使用 Excel 打开文件。 
    
  
2. 将文件保存为 .xlsx 格式。 
    
  
3. 将文件上载到属于受信任位置的文档库。
    
  
4. 使用 Excel Web Access 在文档库中打开文件。
    
  
5. 单击"在 Excel 中打开"。
    
  
6. 将文件保存为 .xlsx 格式。
    
  
如果将在步骤 2 中创建的 Sharedstrings.xml 文件与在步骤 6 中创建的相比较，您会发现 Sharedstrings.xml 部分的顺序可能有所不同。
  
    
    
编写应用程序时不应假定共享字符串表中的字符串顺序是固定的。例如，您不能将共享字符串表替换为现有的本地化翻译表。您必须调整为共享字符串表中字符串的新顺序。
  
    
    

## 另请参阅


#### 任务


  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
#### 概念


  
    
    
 [Excel Services 最佳实践](excel-services-best-practices.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 体系结构](excel-services-architecture.md)
  
    
    
 [受支持和不受支持的功能](supported-and-unsupported-features.md)
  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 博客、论坛和资源](excel-services-blogs-forums-and-resources.md)
