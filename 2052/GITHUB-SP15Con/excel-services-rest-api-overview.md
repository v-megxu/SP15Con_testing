---
title: Excel Services REST API 概述
ms.prod: SHAREPOINT
ms.assetid: 5872f311-e180-4578-ac80-2519c1081951
---


# Excel Services REST API 概述

Excel Services 中的 REST API 是 Microsoft SharePoint Server 2010 中的新增功能。通过使用 REST API，您可以直接通过 URL 访问工作簿的各个部分或元素。
  
    
    


> **注释**
> Excel Services REST API 可本地应用于 SharePoint 2013 和 SharePoint 2016。对于 Office 365 教育版、商业版和企业版帐户，请使用作为  [Microsoft Graph](http://graph.microsoft.io/zh-cn/docs/api-reference/v1.0/resources/excel) 终结点一部分的 Excel REST API。
  
    
    


REST 服务基于以下两个要求：
  
    
    


- 用于查找联网资源的寻址方案
    
  
- 用于返回这些资源的表示形式的方法
    
  
REST 服务以资源为中心。在 REST 中，数据分为多种资源，每种资源指定一个 URL，并对资源执行标准操作，这将启用创建、检索、更新和删除等操作。
> **注释**
> 有关 REST 服务与自定义 Web 服务之间区别的详细信息，请参阅 [自定义服务或 REST 服务](http://msdn.microsoft.com/zh-cn/magazine/dd882522.aspx)。 
  
    
    

Excel Services REST API 使用 HTTP 标准中指定的操作，对 Excel 工作簿启用操作。这提供了访问和操纵 Excel Services 内容一种更简单的灵活、安全的机制。Excel Services REST API 的内置发现机制还使开发人员和用户可以手动或以编程方式浏览工作簿的内容，方法是提供包含特定工作簿中的元素相关信息的  [Atom](http://tools.ietf.org/html/rfc4287) 馈送。您可以通过 REST API 访问的一些资源示例包括图表、数据透视表和表。使用 REST API 提供的 Atom 馈送是获取所需数据一种更简单的方式。馈送包含可遍历的元素，这些元素使任何代码段均可发现工作簿中存在的元素。有关访问 REST 服务和获取 Excel Services 中 REST 服务的示例 URI 的信息，请参阅 [基本 URI 结构和路径](basic-uri-structure-and-path.md)和 [Excel Services REST API 的示例 URI](sample-uri-for-excel-services-rest-api.md)。
