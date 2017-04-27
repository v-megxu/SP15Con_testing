---
title: Excel Services 警告
keywords: errors
f1_keywords:
- errors
ms.prod: SHAREPOINT
ms.assetid: a4e7030b-05c2-484e-b21f-46cba937b803
---


# Excel Services 警告

Excel Web Services 针对 Web 服务中发生的错误以及 Excel Calculation Services 返回的错误发出警告。
  
    
    

通过以下方式公开错误：
- Excel 计算错误的返回方式与它们在 Excel 中的显示方式类似即作为单元格错误值，例如 #VALUE!。当您调用 **GetCell** 或 **GetRange** 方法和请求格式化的值时，您将收到 # 样式错误字符串。如果您请求未格式化的值，您将收到枚举错误代码。有关详细信息，请参阅本主题后面的 [错误代码](#excel-services-alerts_errorcodes)部分。
    
  
- 如果在处理其中一种 Web 服务方法时发生错误，而导致方法无法成功完成，错误将公开为简单对象访问协议 (SOAP) 异常。您可以并且应该捕获代码中的此错误。这些类型的错误也称为"停止"警告。
    
  
- 确保不要阻止方法返回作为方法参数一部分的正常结果，尤其是作为输出参数。这些类型的错误视为非关键性错误。错误作为输出参数而非异常的一部分返回的原因是，抛出异常将使代码偏离正常的执行路径，这是非关键性错误不希望发生的。检查这些错误为可选操作。这些类型的错误也称为"继续"警告。
    
  

## 警告类型

有两种类型的警告："停止"和"继续"。
  
    
    

### "停止"警告

"停止"警告会导致当前操作停止。这意味着工作簿将在执行当前操作之前回滚到其状态。"停止"警告公开为 SOAP 异常。
  
    
    

### "继续"警告

"继续"警告通常为警告或非关键性错误。当 Excel Calculation Services 抛出"继续"警告时，操作继续。这些警告返回为输出参数具有多个警告字段的结构。有关详细信息，请参阅 **Microsoft.Office.Excel.Server.WebServices** 命名空间中的 **Status** 类参考主题。
  
    
    

## 要捕获的异常

您应该捕获您知道用户可能导致的 Excel Calculation Services 特定错误。例如，如果您的应用程序提示用户键入工作簿路径，用户可能会键入错误的路径或者选择一个不存在的工作簿。您无法控制用户类型，但可以控制用户无意中拼错工作簿文件名时的用户体验。
  
    
    
您应该捕获代码中的 SOAP 异常（即"停止"警告）。对于"继续"警告，调用代码可能会选择忽略或检查警告信息。
  
    
    

## 错误代码
<a name="excel-services-alerts_errorcodes"> </a>

为捕获特定的错误条件，Excel Calculation Services 警告具有关联的错误代码。然后 Web 服务将使用 **SoapException** 类中的属性返回错误。
  
    
    
有关详细信息，请参阅 Microsoft .NET Framework SDK 文档中的"SoapException 类"主题。
  
    
    

## 异常处理
<a name="excel-services-alerts_errorcodes"> </a>

如果您的应用程序（即您的 SOAP 客户端）向 Web 服务发送一个服务无法处理的请求，服务将向客户端返回 SOAP 异常。处理 Excel Web Services 抛出的异常是您开发的应用程序的一个重要部分，因为您可以在发生错误时向用户返回具体的信息。异常处理也有助于改进当应用程序中发生意外事件时的用户体验。
  
    
    
有关异常处理的一般信息，请参阅 Microsoft .NET Framework SDK 文档中的"处理和抛出异常"。
  
    
    

## 另请参阅
<a name="excel-services-alerts_errorcodes"> </a>


#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 错误代码](excel-services-error-codes.md)
#### 其他资源


  
    
    
 [步骤 3：访问 Web 服务](step-3-accessing-the-web-service.md)
  
    
    
 [步骤 4：构建和测试应用程序](step-4-building-and-testing-the-application.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
