---
title: SharePoint 2013 中的业务连续性服务入门
ms.prod: SHAREPOINT
ms.assetid: c6bf3db0-db79-4b13-9834-891d24b2c9e5
---



# SharePoint 2013 中的业务连续性服务入门
了解 Business Connectivity Services (BCS) 为 SharePoint 2013 解决方案开发人员提供了哪些基础知识，以及如何在各种类型的解决方案中使用 BCS。
## 什么是 Business Connectivity Services？


|||
|:-----|:-----|
|Business Connectivity Services (BCS) 是在SharePoint Server 2010 中作为业务数据目录改进版在 Office SharePoint Server 2007 中发布而引入的。BCS 使 SharePoint 2013 可以使用外部托管的数据。可能的源包括数据库、Web 服务、Windows Communication Foundation (WCF) 服务、开放式数据协议 (OData) 源和其他使用自定义 .NET 程序集访问的专有数据。 [![开始设置](images/mod_icon_getstartbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatDoYouNeed) [![开始工作](images/mod_icon_dobox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatCanYouDo) [![了解详细信息](images/mod_icon_startbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_LearnMore)|
**观看视频：SharePoint 2013 Business Connectivity Services 和 OData 服务概述**

  
    
    

  
    
    
![视频](images/mod_icon_video.png)
  
    
    

  
    
    

  
    
    
|
   
在动态工作区中，信息工作者需要访问位于不同软件领域的数据，例如：
  
    
    

- 存在于组织的企业应用程序（例如企业资源计划 (ERP) 和客户资源管理 (CRM) 应用程序）中的结构化数据。
    
  
- 业务效率应用程序（例如 Microsoft Office 中的那些应用程序）、工作组和协作应用程序（例如 SharePoint）以及 Web 2.0 服务（例如 Internet 应用程序、Wiki、博客和社交网站）中的非结构化数据。
    
  
虽然大多数信息工作者在效率应用程序（例如 Microsoft Office 环境）上花费了大量工作时间，他们也需要一种方法将企业应用程序、协作软件及其服务集成在一起。BCS 的 SharePoint 2013 可以做到这点。
  
    
    

## 开始使用 Business Connectivity Services
<a name="SP15GettingStartedBCS_WhatDoYouNeed"> </a>

若要开始开发 BCS，您需要以下内容：
  
    
    

- SharePoint 2013
    
  
- Visual Studio
    
  
- Visual Studio 2012 Office 开发人员工具
    
    或
    
  
- SharePoint Designer
    
  
有关如何设置开发环境的信息，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

### Business Connectivity Services 基础

下表重点介绍了开发 BCS 解决方案所需了解的核心概念。
  
    
    

**表 1. 有助于理解 BCS 的核心概念**


|**文章**|**说明**|
|:-----|:-----|
| [实体数据模型关键概念）](http://msdn.microsoft.com/zh-cn/library/ee382840.aspx) <br/> |实体数据模型 (EDM) 使用三个关键概念来描述数据的结构：实体类型、关联类型和属性。这些都是描述任何 EDM 的实现中的数据结构的最重要的概念。  <br/> |
| [Web 应用程序的基本安全实施策略](http://msdn.microsoft.com/zh-cn/library/zdh19h94%28VS.100%29.aspx) <br/> |创建安全的 Web 应用程序这个话题内容非常广泛。您需要对它进行研究以便了解安全漏洞。您还需要熟悉 Windows 操作系统的安全设施, .NET Framework 和 ASP.NET。最后，您需要了解如何使用这些安全功能来应对威胁。  <br/> |
| [WCF 数据服务](http://msdn.microsoft.com/zh-cn/data/odata.aspx)（http://msdn.microsoft.com/zh-cn/data/odata.aspx）  <br/> |WCF 数据服务以前称为 ADO.NET DATA SERVICES，它使用户能够为 Web 创建和使用 OData 服务。  <br/> |
| [开放式数据协议 (OData)](http://www.odata.org)（http://www.odata.org）  <br/> |OData 是通过 URL 访问数据的行业标准协议。它通常位于 HTTP 协议的上层，提供使用现有的 HTTP 谓词的读写功能。  <br/> |
| [Internet Information Services](http://www.iis.net/) <br/> |Internet Information Services (IIS) 是SharePoint 运行的平台。您应该了解如何创建网站、虚拟目录、Web 服务、URL、Web 安全性信息，以及其他与 IIS 相关的技术。  <br/> |
| [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md) <br/> |外部内容类型对其代表的外部系统进行说明。将其导入 SharePoint 后可重复使用，也可用于使用 SharePoint Designer 2013、Outlook 2013、Web 部件、外部列表和自定义客户端应用程序一起创建复杂的免费代码解决方案。  <br/> |
| [在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md) <br/> |SharePoint 2013 可以通过精心构造的 URL 访问所有对象。对 BCS 进行扩展可提供相同功能。  <br/> |
   

## Business Connectivity Services 有哪些功能？
<a name="SP15GettingStartedBCS_WhatCanYouDo"> </a>

使用 BCS，您可以将信息从不同的源传递到 SharePoint。例如，您可将外部 SQL Server 数据库、传统的 Web 服务、WCF 服务、专有系统和 OData 服务的数据导入。
  
    
    

**表 2. 使用 Business Connectivity Services 的基本任务**


|**任务**|**说明**|
|:-----|:-----|
| [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md) <br/> |了解如何创建 Business Connectivity Services (BCS) 外部内容类型。  <br/> |
| [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |找到开始创建基于 OData 源的外部内容类型和在 SharePoint 或 Office 组件中使用该数据所需的信息。  <br/> |
| [如何：创建外部事件接收器](how-to-create-external-event-receivers.md) <br/> |了解创建可连接到外部列表的事件接收器所代表的概念，以及列表中所示外部数据更新时事件接收器将执行的操作。  <br/> |
| [如何：在 SharePoint 2013 中创建外接程序范围的外部内容类型](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md) <br/> |了解如何创建在应用程序级别安装或扩展的外部内容类型，它使开发人员能够使用外部数据的源创建丰富的数据应用程序。  <br/> |
| [如何：使用客户端代码库访问 SharePoint 2013 中的外部数据](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |了解如何使用 SharePoint 2013 客户端对象模型来处理SharePoint 2013 中的 BCS。  <br/> |
   

## 除基础知识以外：了解更多有关 Business Connectivity Services 的信息
<a name="SP15GettingStartedBCS_LearnMore"> </a>

当您掌握了 BCS 的基本概念时，您可以使用更高级的功能构建多种功能强大的解决方案类型。
  
    
    

**表 3. BCS 中的高级概念**


|**主题**|**说明**|
|:-----|:-----|
| [如何：创建用作 BCS 外部系统的 OData 数据服务](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md) <br/> |了解如何创建 Internet 寻址 WCF 服务，该服务在基本数据更改时使用 OData 向 SharePoint 2013 发送通知。这些通知用于触发连接到外部列表的事件。  <br/> |
| [SharePoint 2013 的 BDC 模型架构引用](bdc-model-schema-reference-for-sharepoint-2013.md) <br/> |查找 BDC 模型架构的参考文档。  <br/> |
| [SharePoint 2013 的 BCS 客户端对象模型引用](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |获取使用 SharePoint 2013 客户端对象模型创建客户端脚本的对象汇总，以访问 Business Connectivity Services (BCS) 公开的外部数据。  <br/> |
| [SharePoint 2013 的 BCS REST API 引用](bcs-rest-api-reference-for-sharepoint-2013.md) <br/> |找到用于访问和操作 OData 源的构建具象状态传输 (REST) URI 的参考信息。  <br/> |
   

## 其他资源
<a name="SP15GettingStartedBCS_LearnMore"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [开放式数据协议网站](http://www.odata.org/)（http://www.odata.org/）
    
  
-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的外部事件和警告](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中外接程序范围的外部内容类型](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
