---
title: SharePoint 2013 中的外部内容类型
ms.prod: SHAREPOINT
ms.assetid: 11d7adb5-5388-4517-ae03-beb7be1c6981
---


# SharePoint 2013 中的外部内容类型
了解您可以使用外部内容类型做什么，以及开始在 SharePoint 2013 中创建它们需要什么。
## 什么是外部内容类型？
<a name="SP15ectoverview_what"> </a>

外部内容类型是 Business Connectivity Services (BCS) 的一个核心概念。外部内容类型在 BCS 提供的功能和服务中广泛使用，它们是对连接信息和数据定义以及要应用于特定类别的外部数据的行为的可重用的元数据说明。
  
    
    
利用外部内容类型，您可以从一个中心位置管理和重用业务实体（例如客户或订单）的元数据和行为，并且用户可以通过更有意义的方式与该外部数据和流程进行交互。
  
    
    
以下是使用外部内容类型的一些好处：
  
    
    

- **提供可重用性：**外部内容类型是业务实体的可重用数据定义。在创建外部内容类型后，可将其与 BCS 中的任何演示功能一起使用，以提供与外部数据交互的丰富用户体验。
    
  
- **封装外部系统的复杂性：**利用外部内容类型，信息工作人员无需处理外部系统的复杂性（例如，无需了解连接信息和代码接口）即可汇编业务解决方案。在创建一个外部内容类型后，任何用户可按所需方式使用该类型（前提是，这些用户有权执行该操作和访问该外部数据）。不过，用户无需了解有关外部数据的位置或外部数据的连接方式的任何信息。
    
  
- **提供内置 Office 和 SharePoint 行为：**外部内容类型为外部数据和服务提供了 Office 项目类型行为（例如，Outlook中的联系人、任务和日历，Word 中的文档以及 SharePoint Workspace 中的列表）；SharePoint 行为（例如，列表、Web 部件和配置文件页）；和功能（例如，搜索或脱机工作的能力），以便用户能够在其熟悉的工作环境中工作，而无需查找数据或了解不同的（和专有）用户界面并与之交互。
    
  
- **帮助提供更安全的访问：**外部内容类型符合外部系统和 SharePoint 产品与技术的实现的安全性。可通过配置 SharePoint 中的安全性来完全控制哪些用户访问哪些数据。
    
  
- **简化维护：**因为外部内容类型创建一次便可由不同情况下的多个解决方案使用，所以可轻松管理它们。例如，可以在一个中心位置管理其访问权限以及连接和数据定义。
    
  
- **启用外部数据搜索：**可从 Intranet 门户使用 SharePoint Server 搜索功能来查找有关特定外部内容类型（例如 Customer）的信息。SharePoint Server 搜索功能直接从外部系统检索数据。因此，用户无需获得批准或安装单独的应用程序即可获取其所需信息。
    
  
- **启用脱机工作：**可在 Outlook 2013 中脱机使用外部内容类型。Business Connectivity Services (BCS) 提供了丰富的缓存和脱机工作功能，并支持基于缓存的操作。即使当用户处于脱机状态或服务器连接缓慢、不稳定或不可用时，用户仍可无缝且高效地操作外部数据。当与服务器的连接可用时，将同步对缓存业务实体执行的读取/写入操作。
    
  

## 使用 BCS 外部内容类型的先决条件
<a name="SP15ectoverview_prereq"> </a>

要开始创建外部内容类型，您将需要以下内容：
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
    或
    
  
- SharePoint Designer 2013
    
  
若要设置用于创建外部内容类型的开发环境，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

## 外部内容类型可实现哪些功能？
<a name="SP15ectoverview_whattodo"> </a>

当将 SharePoint 配置为与外部系统进行通信时，您可以使用外部内容类型创建下列对象来提供基础数据：
  
    
    

- **外部列表**
    
    外部列表允许以访问 SharePoint 列表数据的相同方式访问外部系统中的数据。外部列表使用外部内容类型作为其数据源。通过外部列表，您可以使用已定义的与外部内容类型有关的元数据来创建具有外部数据并外观和执行方式与任何其他 SharePoint 列表类似的 SharePoint 列表。
    
    您还可以在 Outlook 2013 中脱机使用外部列表。这样，您便可以像处理本机 Outlook项目类型（例如联系人、任务和公告）一样处理外部数据，并在 Office 客户端应用程序中使用外部数据。
    
    如果外部系统允许，并且已按外部内容类型相应地进行了建模，则外部列表可以写回到外部系统。这表示用户可以直接从中编辑外部数据。对列表中的项进行的任何更改都将自动与外部系统同步。另外，通过使用列表中的"刷新数据"按钮，您可以自动同步并从外部系统中获取更新后的数据。
    
  
- **外部数据列**
    
    外部数据列使用户能够将外部内容类型的数据添加到标准 SharePoint 列表中。就像外部列表一样，外部数据列可以显示在 Business Connectivity Services (BCS) 中建模的任何外部内容类型的数据。
    
  
- **业务数据 Web 部件**
    
    SharePoint 2013 提供了五个不同的 Web 部件来使用外部数据：业务数据列表、业务数据项目、业务数据项目生成器、业务数据相关列表以及业务数据操作。
    
  
- **外部内容类型选取器**
    
    外部内容类型选取器为用户提供选取和解析功能。您可以为用户应能够从可用外部内容类型的列表中选取外部内容类型的方案在表单或页面中嵌入选取器。 
    
  
- **外部项选取器**
    
    外部项选取器为服务器上和富客户端 Office 应用程序中的外部项提供选取和解析功能。您可以针对用户应能够在其中选取外部项（例如从客户列表中选取客户）的方案，在表单或页面中嵌入选取器。 
    
  
- **配置文件页**
    
    配置文件页是 SharePoint 2013 中提供的 SharePoint 页面，显示有关外部项的详细信息。与任何其他 SharePoint Web 部件页 一样，您可以自定义此页面以显示外部项的详细信息。
    
  
- **自定义页面和应用程序**
    
    您可以使用 SharePoint 2013 可编程性选项，如 SharePoint 对象模型、客户端对象模型和表示性状态传输器 (REST) URL。
    
  
表 1 包含说明使用外部内容类型的任务示例。
  
    
    

**表 1. 使用外部内容类型的基本任务**


|**任务**|**说明**|
|:-----|:-----|
| [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |了解如何使用 Visual Studio 2008 发现一个已发布的 OData 源，并创建可重用的外部内容类型以在 SharePoint 2013Business Connectivity Services (BCS) 中使用。  <br/> |
| [如何：在 SharePoint 2013 中为 SQL Server 创建外部内容类型](how-to-create-external-content-types-for-sql-server-in-sharepoint-2013.md) <br/> |了解如何基于 SQL Server 数据库创建外部内容类型。  <br/> |
   

## 其他资源
<a name="SP15ectoverview_addres"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建外接程序范围的外部内容类型](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中为 SQL Server 创建外部内容类型](how-to-create-external-content-types-for-sql-server-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  

