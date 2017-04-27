---
title: 从移动和本机设备应用程序访问 SharePoint
ms.prod: SHAREPOINT
ms.assetid: 42014171-5ee5-421d-9cde-413efc3aecef
---


# 从移动和本机设备应用程序访问 SharePoint
了解如何从移动应用程序和其他本机设备应用程序以及外部 Web 应用程序访问 SharePoint。
SharePoint 外接程序、服务器场解决方案 和无代码 沙盒解决方案 均从 SharePoint 内运行，但其他平台上的应用程序也可以访问 SharePoint 客户端 API。
  
    
    


> **重要信息**
> 要在任何平台上进行测试和调试，您需要具有 **Office 365 上的一个开发人员帐户** 。详细信息： [在 Office 365 上设置 SharePoint 加载项的开发环境](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx) 或 [在现有 Office 365 订阅中创建开发人员网站](http://msdn.microsoft.com/library/2ec857d5-dc6f-4cf6-ba45-adc845ef2a25%28Office.15%29.aspx)。 
  
    
    


## 非 Microsoft 移动和本机设备应用程序

非 Microsoft 设备应用程序（包括移动应用程序） **针对 SharePoint 数据的 CRUD 操作使用 SharePoint REST/OData API** 。
  
    
    

- 请参阅 [开始使用 SharePoint 2013 REST 服务](get-to-know-the-sharepoint-2013-rest-service.md)了解一些基础知识。
    
  
- 有关完整参考，请参阅  [SharePoint 2013 的 REST API 引用](http://msdn.microsoft.com/library/3514e753-19f9-4b41-a1ae-f35c5ffc17d2%28Office.15%29.aspx)。
    
  
有关如何为任何平台创建移动应用程序的详细信息，请参阅 [使用 SharePoint 2013 为其他平台生成移动应用程序](build-mobile-apps-for-other-platforms-using-sharepoint-2013.md)。
  
    
    

## 访问 SharePoint 的 Windows Phone 应用程序
<a name="WinPhone"> </a>

Windows Phone 应用程序可以使用以下项目之一：
  
    
    

- 专为 Windows Phone 设备设计的 .NET SharePoint 客户端对象模型 (CSOM) 版本。
    
  
- SharePoint REST/OData API。
    
  
 这些移动应用程序可以利用 SharePoint 中对 Microsoft 推送通知服务和新地理位置字段类型的支持。
  
    
    
有关创建可访问 SharePoint 的 Windows Phone 应用程序的详细信息，请参阅 [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)。
  
    
    

## 不从 SharePoint 启动的 Web 应用程序
<a name="WinPhone"> </a>

不从 SharePoint 启动的 Web 应用程序并非严格意义上的"SharePoint 外接程序"，尽管他们在 MSDN 和其他文档中有时算作 SharePoint 外接程序。这些应用程序包括但不仅限于从 Office 365 应用程序启动程序和 Office 外接程序启动的应用程序，以及直接从浏览器运行的任何 Web 应用程序。
  
    
    
您可以在 ASP.NET 平台或非 Microsoft 堆栈上构建这些应用程序。如果在非 Microsoft 堆栈上构建 Web 应用程序，它将通过 REST/OData API 执行 CRUD 操作，就像非 Microsoft 设备应用程序一样。如果您在 ASP.NET 上构建，则它 **可以使用 SharePoint CSOM 或 REST/OData API** 。
  
    
    
根据 OAuth 身份验证代码流，这些应用程序 **将使用 Azure 控制服务 (ACS) 颁发的访问令牌获取对 SharePoint 数据的授权访问权限** 。有关详细信息，请参阅 [SharePoint 外接程序的身份验证代码 OAuth 流](http://msdn.microsoft.com/library/e89e91c7-ea39-49b9-af5a-7f047a7e2ab7%28Office.15%29.aspx)。
  
    
    

