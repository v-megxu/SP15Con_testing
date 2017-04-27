---
title: 环回 SOAP 调用和直接链接
ms.prod: SHAREPOINT
ms.assetid: bffc6565-636f-40d4-ba17-2511070ba5db
---


# 环回 SOAP 调用和直接链接

如果您在 Microsoft SharePoint Foundation 内编写代码，例如自定义 Web 部件、自定义 aspx 页面等，您应直接调用 Microsoft.Office.Excel.Server.WebServices.dll。您可通过直接链接到 Microsoft.Office.Excel.Server.WebServices.dll 执行此操作。 
  
    
    

使用简单对象访问协议 (SOAP) 从 Web 服务器与同一 Web 服务器通信也称为使用环回 SOAP 调用。强烈建议您不要尝试使用环回 SOAP 调用。如果您在 SharePoint Foundation 中编写代码，您不应使用 SOAP 调用 Excel Web Services。您应该转为在本地链接到 Microsoft.Office.Excel.Server.WebServices.dll，并像调用任何本地程序集一样进行调用。
## Microsoft.Office.Excel.Server.WebServices.dll 的位置

您可以在以下位置之一查找 Microsoft.Office.Excel.Server.WebServices.dll：
  
    
    

-  _[drive:]_\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI
    
  
- 全局程序集缓存 
    
  

## 添加对 Microsoft.Office.Excel.Server.WebServices.dll 的引用

要直接链接到项目中的 Microsoft.Office.Excel.Server.WebServices.dll 并从您的代码进行调用，您可以添加对它的引用。在已安装 Microsoft SharePoint Server 2010 的计算机上，使用 Microsoft Visual Studio 中的"添加引用"对话框执行以下操作之一： 
  
    
    

- 从".NET"选项卡的"组件名称"列表中选择"Excel Web Services"。 
    
  
- 浏览到 Microsoft.Office.Excel.Server.WebServices.dll，位于以下位置：
  
    
    
 _[drive:]_\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI
    
  

## 另请参阅


#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
