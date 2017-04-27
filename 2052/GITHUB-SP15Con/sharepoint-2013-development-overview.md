---
title: SharePoint 2013 开发概述
ms.prod: SHAREPOINT
ms.assetid: f86e2695-4d7a-4fc5-bc23-689de96c4b06
---


# SharePoint 2013 开发概述
SharePoint 2013 是 SharePoint 外接程序 和 服务器场解决方案 的开发平台。熟悉 SharePoint 2013 的功能以开始开发。
## SharePoint 2013 开发平台的介绍
<a name="bk_introduction"> </a>

SharePoint 2013 是一个用于在提出大范围需求的不同范围中生成加载项和解决方案的通用开发平台。SharePoint 2013 开发人员文档 从开发的功能、技术、性能和模型这些方面指导您，它们是用来区分 SharePoint 2013 为开发平台的。我们的开发人员文档指引您写入第一个加载项的必备事件、开始使用该平台、用自己的代码创建、使用 SharePoint 2013 资源并与其相交互。我们提供了有关 SharePoint 概念、循序渐进帮助任务指南和代码示例的有深度的文章，以帮助您更快更容易地生成 SharePoint 外接程序和 SharePoint 解决方案。
  
    
    

## 您可以使用 SharePoint 2013 进行哪种类型的开发？
<a name="bk_whatkinds"> </a>

熟悉 SharePoint 的开发人员清楚，他们可以生成扩展核心 SharePoint 功能的服务器端场解决方案。SharePoint 2013 提供了一个新的灵活的开发模型您可以使用 SharePoint 2013 创建利用 JavaScript、OAuth 和 OData 等标准 Web 技术的SharePoint 外接程序。SharePoint 2013 向您提供了可以与 SharePoint 资源和大范围的宿主选项相交互的功能。这种新的 SharePoint 外接程序 开发模型让您能够生成利用 SharePoint 功能并在云中而不是 SharePoint 场中运行的加载项。此中灵活的开发模型和标准 Web 技术集成一起使得 SharePoint 开发工作更像您可能已经正在进行的其他种类的 Web 开发。
  
    
    
 **SharePoint 外接程序 开发**
  
    
    
以下章节可以帮组您了解 SharePoint 外接程序并帮助您确定它们对于您而言是否是好的选择。
  
    
    

-  [SharePoint 加载项与 SharePoint 解决方案比较](sharepoint-add-ins-compared-with-sharepoint-solutions.md)
    
  
 **移动性功能开发的 SharePoint 解决方案和加载项**
  
    
    
如果您想开发 服务器场解决方案，您可以利用社会应用程序、远程数据源集成 (Business Connectivity Services) 和移动设备开发等功能。从  [SharePoint 2013 中面向开发人员的新增功能](what’s-new-for-developers-in-sharepoint-2013.md)中的指南开始。
  
    
    
以下部分介绍了如何创建 SharePoint 2013 的移动设备解决放啊。
  
    
    

-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [如何：使用导航和事件日志记录 REST 界面构建搜索驱动移动应用程序](how-to-build-search-driven-mobile-apps-with-the-navigation-and-event-logging-res.md)
    
  
以下部分提供了有关可用于 服务器场解决方案 的 SharePoint 2013 功能的信息。
  
    
    

-  [为 SharePoint 构建网站](build-sites-for-sharepoint.md)
    
  
-  [添加 SharePoint 2013 功能](add-sharepoint-2013-capabilities.md)
    
  

## 设置开发环境并开始开发
<a name="bk_getstarted"> </a>

 **移动性功能开发的 SharePoint 解决方案和加载项**
  
    
    
表 1 演示了设置开发环境和开始利用新功能以使用 SharePoint 2013 生成 服务器场解决方案 的资源。
  
    
    

  
    
    

**表 1. 帮助您开始开发 SharePoint 服务器场解决方案 的资源**


|**主题**|**说明**|
|:-----|:-----|
| [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md) <br/> |包含了有关如何安装 SharePoint 2013 开发环境的组件的循序渐进的说明。  <br/> |
| [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md) <br/> |介绍了 SharePoint 2013 提供的几组 API，包括服务器对象模型、各种客户端对象模型和 REST/OData Web 服务。  <br/> |
| [SharePoint 2013 中面向开发人员的新增功能](what’s-new-for-developers-in-sharepoint-2013.md) <br/> |提供了到有关 SharePoint 2013 中的新功能的网关。  <br/> |
| [SharePoint 2013 中的编程模型](programming-models-in-sharepoint-2013.md) <br/> |提供了您可以使用 SharePoint 2013 创建的各种类型的 SharePoint 开发项目的概述。  <br/> |
| [添加 SharePoint 2013 功能](add-sharepoint-2013-capabilities.md) <br/> |提供了到有关在您的解决方案中使用 SharePoint 2013 的功能的详细信息的网关。  <br/> |
   
 **SharePoint 外接程序 开发**
  
    
    
如果您要开始开发 SharePoint 外接程序，请首先思考您可能要生成的加载项的类型、您要包括的技术和您要使用的宿主选项。
  
    
    
当我们知道您要创建的 SharePoint 外接程序 的类型，我们将提供指南帮组您将它们和合适的开发环境相匹配。表 2 演示了设置您的 SharePoint 开发环境和开始创建加载项的资源。
  
    
    

**表 2. 帮助您启动 SharePoint 外接程序 开发的资源**


|**主题**|**说明**|
|:-----|:-----|
|||
| [在 Office 365 上设置 SharePoint 加载项的开发环境](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx) <br/> |阐释了如何注册并使用 Office 365 开发人员网站以供开发 SharePoint 外接程序。  <br/> |
| [设置 SharePoint 加载项的本地开发环境](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx) <br/> |阐释如何设置 SharePoint 2013 的本机的、内部的安装并配置它，以供开发 SharePoint 外接程序。  <br/> |
| [开始创建提供程序承载的 SharePoint 加载项](http://msdn.microsoft.com/library/3038dd73-41ee-436f-8c78-ef8e6869bf7b%28Office.15%29.aspx) <br/> |包含了如何创建单独寄宿在 SharePoint 2013 网站的基本 SharePoint 外接程序 的循序渐进说明。  <br/> |
| [开始创建 SharePoint 承载的 SharePoint 外接程序](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx) <br/> |包含了如何创建寄宿在 SharePoint 2013 网站的基本 SharePoint 外接程序 的循序渐进说明。  <br/> |
   

## 其他资源
<a name="bk_additionalresources"> </a>


-  [SharePoint 2013 中的辅助功能](accessibility-in-sharepoint-2013.md)
    
  
-  [Protocol handler error due to deprecated interface in SharePoint 2016](protocol-handler-error-due-to-deprecated-interface-in-sharepoint-2016.md)
    
  
-  [SharePoint 2013 的 .NET 服务器 API 引用](http://msdn.microsoft.com/library/fb8a82f1-9239-49ae-89f3-ce1385fb28b5%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 的 .NET 客户端 API 引用](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx)
    
  

  
    
    

