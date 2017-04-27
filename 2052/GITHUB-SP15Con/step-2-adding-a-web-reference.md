---
title: 步骤 2：添加 Web 引用
ms.prod: SHAREPOINT
ms.assetid: e9175863-ddb4-4750-847d-d53cb59b33cb
---


# 步骤 2：添加 Web 引用

Web 服务发现是客户端查找 Web 服务并获取其服务说明的过程。Visual Studio 中的 Web 服务发现过程包括按照预先确定的算法，直接查询网站。此过程的目标是查找服务说明，即使用 Web Services 描述语言 (WSDL) 的 XML 文档。
  
    
    

服务说明描述了哪些服务可用以及如何与这些服务交互。没有服务说明，便无法以编程方式与 Web 服务交互。
您的应用程序必须具有与 Web 服务进行通信，并在运行时找到它的方法。在 Web 服务的项目中添加 Web 引用可执行此操作，方法是生成与 Web 服务交互并提供 Web 服务本地表示形式的代理类。有关详细信息，请参阅 Microsoft Visual Studio 2005 文档中的"Web 引用和生成 XML Web 服务代理"。
  
    
    


## 添加 Web 引用


1. 在"项目"菜单上单击"添加 Web 引用"。
    
  
2. 在"添加 Web 引用"对话框的"URL"框中，键入 URL 以获取 Excel Web Services 的服务说明，例如  `http://<server>/<customsite>/_vti_bin/excelservice.asmx` 或 `http://<server>/_vti_bin/excelservice.asmx`。然后单击"执行"检索 Web 服务的相关信息。
    
    > **注释**
      > 您也可以打开"解决方案资源管理器"窗格中的"添加 Web 引用"对话框，方法是右键单击"引用"并选择"添加 Web 引用"。 
3. 在"Web 引用名称"框中，将 Web 引用重命名为 ExcelWebService。
    
  
4. 单击"添加引用"以添加对目标 Web 服务的 Web 引用。 
    
  
5. Visual Studio 下载服务说明并生成在您的应用程序和 Excel Web Services 之间充当接口的代理类。 
    
  
6. 有关详细信息，请参阅 [访问 SOAP API](accessing-the-soap-api.md)。
    
  

## 另请参阅


#### 概念


  
    
    
 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)
#### 其他资源


  
    
    
 [步骤 1：创建 Web 服务客户端项目](step-1-creating-the-web-service-client-project.md)
  
    
    
 [步骤 3：访问 Web 服务](step-3-accessing-the-web-service.md)
  
    
    
 [步骤 4：构建和测试应用程序](step-4-building-and-testing-the-application.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
