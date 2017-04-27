---
title: 将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用
ms.prod: SHAREPOINT
ms.assetid: 7a87e5bf-4428-4055-b113-7665a93e7326
---


# 将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用
了解如何基于 OData 源开始创建外部内容类型和在 SharePoint 2013 或 Office 2013 组件中使用该数据。
## OData 和 OData 连接器
<a name="SP15getstartedOdata_whatisodata"> </a>

利用开放式数据协议 (OData)，您可以通过特别构造的 URL 访问数据源（例如，数据库）。这允许连接到组织内承载的数据源并使用该数据源的简化方法 。
  
    
    
OData 是使用 HTTP、Atom 和 JavaScript 对象表示法 (JSON) 的协议，使开发人员能够编写与数量不断增加的数据源通信的应用程序。Microsoft 支持创建此标准作为启用应用程序与可从 Web 访问的数据存储之间的数据交换的方法。
  
    
    
新 OData 连接器 使 SharePoint 能够与 OData 提供程序通信。
  
    
    
在 SharePoint 2013 中，Business Connectivity Services (BCS) 可与 OData 源或创建器 通信，而无需对 OData 源编码。创建器通过 Web 服务以结构化方法公开其数据。某些创建器可能允许更新基础数据，而某些创建器可能仅允许读访问。为了公布哪些操作可用，创建器在指定 URL 端点处建立了服务文档。SharePoint 已经是 OData 的创建器。SharePoint 列表数据作为 OData 源向具有相应权限的任何用户公开。
  
    
    

### OData 创建器的示例
<a name="ExamplesOfODataProducers"> </a>

下面是 OData 的实现的一些示例。这些应用程序和服务通过 OData 协议公开其数据。
  
    
    

- SharePoint Foundation 2010
    
  
- SharePoint Server 2010
    
  
- SQL Azure
    
  
- Microsoft Azure 表存储
    
  
- Microsoft Azure 市场
    
  
-  SQL Server Reporting Services
    
  
- Microsoft Dynamics CRM 2011
    
  
- Windows Live
    
  
有关 OData 服务的创建器的列表，请参阅 [开放式数据协议网站](http://www.odata.org/ecosystem)。
  
    
    

## 使用 BCS OData 连接器的先决条件
<a name="SP15GetstartedOdata_prereq"> </a>

若要开发基于 OData 的外部内容类型，您将需要以下各项：
  
    
    

- Visual Studio 2008
    
  
- SharePoint 2013
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
有关如何设置开发环境的信息，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

## 为 OData 数据源创建外部内容类型
<a name="SP15GetstartedOdata_creatingECT"> </a>

必须在 SharePoint 内创建外部内容类型，SharePoint 才可使用特定 OData 创建器公开的内容。与所有 SharePoint 外部内容类型一样，它包含连接外部系统和与其通信所需的所有连接信息。
  
    
    
创建使用 OData 数据源的外部内容类型与创建任何外部内容类型类似。可使用 Visual Studio 2008 自动生成 OData 外部内容类型。创建外部内容类型时，仅提供 OData 源的代表性状态传输 (REST) 端点。有关详细信息，请参阅 [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)。
  
    
    

## 本节内容
<a name="SP15GetstartedOdata_inthissect"> </a>


-  [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [如何：创建用作 BCS 外部系统的 OData 数据服务](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md)
    
  
-  [如何：在 SharePoint 2013 中使用 OData 数据源创建外部列表](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md)
    
  

## 其他资源
<a name="SP15GetstartedOdata_addres"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的 Business Connectivity Services 程序员参考](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  

