---
title: 访问 SOAP API
keywords: soap
f1_keywords:
- soap
ms.prod: OFFICE365
ms.assetid: 36e8e3d5-83ac-4bd3-b556-1af132add3eb
---


# 访问 SOAP API

Excel Web Services 通过 HTTP 使用简单对象访问协议 (SOAP) 并充当客户端程序和 Excel Services 之间的通信接口。Web 服务中包含方法和一系列复杂类型的对象，通过他们您可以使用 Excel Web Services 的完整功能。若要调用服务，您必须引用 Excel Web Services Web Services 描述语言 (WSDL)。
  
    
    


## 引用 WSDL

若要成功调用 Web 服务，您必须了解如何访问服务、服务支持哪些操作、需要哪些参数，以及服务将返回什么。WSDL 提供了一个可由计算机读取和处理的 XML 文档，该文档中提供了以上信息。
  
    
    
Excel Web Services 终结点的 WSDL 可通过  `ExcelServices.asmx?wsdl` 来访问。WSDL 可由支持 SOAP 和 Web 服务的开发工具包来使用，如 Microsoft .NET Framework SDK。
  
    
    
以下示例演示了 Excel Web Services WSDL 文件的 URL 格式：
  
    
    
 `http://<server>/<customsite>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
如果您没有自定义网站，可以暂时使用以下 URL：
  
    
    
 `http://<server>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
建议您创建一个自定义网站，然后采用在 URL 格式中添加了自定义网站的 URL。
  
    
    
下表描述了 URL 中的每个元素。
  
    
    


|****URL element****|****Description****|
|:-----|:-----|
| _server_ <br/> |部署了 Microsoft SharePoint Server 2010 的服务器的名称。  <br/> |
| _customsite_ <br/> |服务器管理员创建的自定义 SharePoint Server 2010 网站。  <br/> |
| _<endpointname>.asmx_ <br/> |Web Service 终结点的名称。对于 Excel Web Services 为  `ExcelService.asmx`。  <br/> |
   
有关 WSDL 格式的详细信息，请参阅位于 http://www.w3.org/TR/wsdl 上的万维网联合会 (W3C) 规范。
  
    
    

## 另请参阅


#### 其他资源


  
    
    
 [步骤 1：创建 Web 服务客户端项目](step-1-creating-the-web-service-client-project.md)
  
    
    
 [步骤 2：添加 Web 引用](step-2-adding-a-web-reference.md)
  
    
    
 [步骤 3：访问 Web 服务](step-3-accessing-the-web-service.md)
  
    
    
 [步骤 4：构建和测试应用程序](step-4-building-and-testing-the-application.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
