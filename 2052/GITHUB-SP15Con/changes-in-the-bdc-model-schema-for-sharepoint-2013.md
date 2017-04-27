---
title: SharePoint 2013 的 BDC 模型架构更改
ms.prod: SHAREPOINT
ms.assetid: 882ea867-9acb-4313-99c9-865a523b72fd
---


# SharePoint 2013 的 BDC 模型架构更改
了解 SharePoint 2013 中有关 BDC 模型架构的更改。
对在 SharePoint 2013 中创建 BDC 模型的架构 (BDCMetadata.xsd) 的更改量相对较小。但是这些更改对 Business Connectivity Services (BCS) 的功能集有重大影响。
  
    
    

有关 BDCMetadata 架构的详细信息，请参阅 [SharePoint 2013 的 BDC 模型架构引用](bdc-model-schema-reference-for-sharepoint-2013.md)。
## 对 BDCMetadata.xsd 中复杂类型元素的更改
<a name="bkmk_ChangesToElements"> </a>

下表显示了对 BDCMetadata 架构中的顶级元素进行了何种更改。
  
    
    

**表 1. 新的复杂类型**


|**元素**|**描述**|
|:-----|:-----|
|IndividuallySecurableMetadataObject  <br/> |用于指定指定的 **MetadataObject** 能够以显式方式（而不是通过与其父级关联）确保安全。 <br/> |
|MetadataObject  <br/> |用于存储连接到外部数据源的连接周围的其他元数据。  <br/> |
   

## 对 BDCMetadata.xsd 中简单类型元素的更改
<a name="bkmk_ChangesToSimpleTypes"> </a>

下表列出了对每个元素的特性所做出的更改。
  
    
    

**表 2. 对简单类型的更改**


|**元素**|**描述**|
|:-----|:-----|
|无更改  <br/> ||
   

## 对 BDCMetadata.xsd 中特性的更改
<a name="bkmk_ChangesToAttributes"> </a>

下表列出了对每个元素的特性的更改。
  
    
    

**表 3. 对特性的更改**


|**特性**|**父级**|**描述**|
|:-----|:-----|:-----|
|无更改  <br/> |||
   

## 其他资源
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的 Business Connectivity Services 程序员参考](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的 BDC 模型架构引用](bdc-model-schema-reference-for-sharepoint-2013.md)
    
  

