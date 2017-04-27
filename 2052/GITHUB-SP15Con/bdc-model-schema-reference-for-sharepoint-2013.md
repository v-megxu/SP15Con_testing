---
title: SharePoint 2013 的 BDC 模型架构引用
ms.prod: SHAREPOINT
ms.assetid: 979a5ffc-f033-4e72-b2d1-11d8cb1b294a
---



# SharePoint 2013 的 BDC 模型架构引用
包含针对 BDC 模型架构 (BDCMetadata.xsd) 的参考文档，您可以使用该文档在 SharePoint 2013 中创建外部内容类型。 
 [BDCMetadata.xsd](http://schemas.microsoft.com/windows/2007/BusinessDataCatalog)
  
    
    


## AccessControlEntry 元素
<a name="bkmk_AccessControlEntry"> </a>

包含为父元素指定访问权限的访问控制项 (ACE)。
  
    
    
请参阅  [Business Connectivity Services 安全性概述](http://technet.microsoft.com/zh-cn/library/ee661734%28office.14%29.aspx)，了解有关 Business Connectivity Services 和安全性的详细信息。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML

<AccessControlEntry Principal = "String"> </AccessControlEntry>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**属性**|**描述**|
|:-----|:-----|
|主体  <br/> |必需。  <br/> 具有此 ACE 的安全主体的名称。  <br/> 属性类型： **String** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [AccessControlEntry 中的 Right 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a2e4bd6c-2306-b657-7290-cc9c9b262911%28Office.15%29.aspx) <br/> |一个 **Right** 元素，指定安全主体的可用权限。 <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |包含此 ACE 的访问控制列表 (ACL)。  <br/> |
   

## AccessControlList 元素
<a name="bkmk_AccessControlList"> </a>

为父元素指定访问控制列表 (ACL)。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<AccessControlList></AccessControlList>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [AccessControlList 中的 AccessControlEntry 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/85e24489-0a6b-dfda-fb03-474fe7b0d947%28Office.15%29.aspx) <br/> |访问控制项 (ACE)。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Model 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> |包含业务应用程序中的外部内容类型的模型。  <br/> |
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |包含在模型中的 LobSystems。  <br/> |
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |外部内容类型。  <br/> |
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |外部内容类型的方法。  <br/> |
| [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> |一个关联。  <br/> |
| [MethodInstances 中的 MethodInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> |外部内容类型的方法实例。  <br/> |
   

## Action 元素
<a name="bkmk_Action"> </a>

指定外部内容类型支持的操作。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **Schema:** BDCMetadata
  
    
    
操作通过提供返回到外部系统的链接，在 SharePoint 2013 和 Office 2013 以及外部系统的用户界面之间架起沟通的桥梁。 
  
    
    
默认情况下，在 BDC 模型中对这些操作建模之后，Business Data Connectivity (BDC) 服务 会提供 **View Item**、 **Edit Item** 和 **Delete Item** 等操作。除了这些默认操作之外，还可以为要附加到外部内容类型的其他功能创建操作。例如，可使用各种操作执行一些简单的操作，如从"客户"外部内容类型向客户发送电子邮件或在浏览器中打开客户的主页。
  
    
    
操作会随外部内容类型一起出现。也就是说，在为某个外部内容类型定义一个操作后，该操作会在此外部内容类型出现的位置显示（无论是在外部列表、业务数据 Web 部件还是外部数据列中）。 
  
    
    



```XML
<Action Position = "Integer" IsOpenedInNewWindow = "Boolean" Url = "String" ImageUrl = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Action>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Position** <br/> |必需。  <br/> 此操作的建议位置位于该外部内容类型的其他操作之间。  <br/> 属性类型： **Integer** <br/> |
|**IsOpenedInNewWindow** <br/> |可选。  <br/> 指定是否在新的用户界面窗口中显示执行操作的结果。  <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**Url** <br/> |必需。  <br/> 调用该操作时要转到的 URL。此 URL 字符串是 .NET Framework 格式的字符串。每个格式说明符（例如 {0}）都对应一个 **Action** 参数。 <br/> 属性类型： **String** <br/> |
|**ImageUrl** <br/> |可选。  <br/> 该操作的图标图像的绝对路径或相对路径。图标图像应为 16x16 像素。  <br/> 属性类型： **String** <br/> |
|**Name** <br/> |必需。  <br/> 此操作的名称。  <br/> 属性类型： **String** <br/> |
|**DefaultDisplayName** <br/> |可选。  <br/> 此操作的默认显示名称。  <br/> 属性类型： **String** <br/> |
|**IsCached** <br/> |可选。  <br/> 指定是否频繁使用此操作。BDC 客户端运行时使用该属性来缓存此操作。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |此操作的本地化名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |此操作的属性。  <br/> |
| [Action 中的 ActionParameters 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/e14df901-621c-1851-db78-e99fd3cf31ae%28Office.15%29.aspx) <br/> |此操作的参数。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entity 中的 Actions 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/c5a6c08d-a3df-61db-3ce3-1e6837bbf221%28Office.15%29.aspx) <br/> |外部内容类型的操作列表。  <br/> |
   

## ActionParameter 元素
<a name="bkmk_ActionParameter"> </a>

指定基于 URL 的操作的参数。该参数定义如何使用特定于 **EntityInstance** 的数据来将某个操作的 URL 参数化。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    
基于 URL 的操作的 URL 属性可通过 **ActionParameter** 元素接收参数。
  
    
    

> **重要信息**
> **ActionParameters** 既可表示标识符值，也可表示与 **Entity** 的 **SpecificFinder** 中的 **TypeDescriptors** 相对应的值。当显示 **IdOrdinal** 属性时， **ActionParameter** 表示一个标识符值。该属性值指定 **ActionParameter** 所表示的值的标识符的索引。如果未指定 **IdOrdinal** 属性，则 **ActionParameter** 表示一个 **TypeDescriptor**，且 **Name** 属性指定所表示的类型描述符。将 **Name** 属性指定为 **Dotted Path**。 
  
    
    

 **ActionParameter** 元素接受以下属性。
  
    
    

> **重要信息**
> 属性区分大小写。 
  
    
    


**属性**


|**属性**|**类型**|**描述**|**必需。**|**默认值**|**限制/接受值**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**IdOrdinal** <br/> |**System.Int32** <br/> |指定 **ActionParameter** 是否表示标识符而不是字段。 <br/> |可选  <br/> |||
   



```XML
<ActionParameter Index = "Integer" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </ActionParameter>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Index** <br/> |必需。  <br/> 一个序号属性，用于指定此 **ActionParameter** 在 URL 中的其他 **ActionParameters** 中的位置。 <br/> 属性类型： **Integer** <br/> |
|**Name** <br/> |必需。  <br/> **ActionParameter** 的名称。 <br/> 属性类型： **String** <br/> |
|**DefaultDisplayName** <br/> |可选。  <br/> **ActionParameter** 的默认显示名称。 <br/> 属性类型： **String** <br/> |
|**IsCached** <br/> |可选。  <br/> 指定是否频繁使用此 **ActionParameter**。BDC 客户端运行时使用该属性来缓存此 **Action**。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**ActionParameter** 的本地化显示名。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**ActionParameter** 的属性。 <br/> |
   
 **父元素**
  
    
    


|****Element****|**描述**|
|:-----|:-----|
| [Action 中的 ActionParameters 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/e14df901-621c-1851-db78-e99fd3cf31ae%28Office.15%29.aspx) <br/> |包含此 **ActionParameter** 的 **ActionParameters** 元素。 <br/> |
   

## ActionParameters 元素
<a name="bkmk_ActionParameters"> </a>

指定操作的 **ActionParameters** 的列表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<ActionParameters></ActionParameters>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无。
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [ActionParameters 中的 ActionParameter 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/1f5fa96a-1bff-f007-984d-a644cbbb2648%28Office.15%29.aspx) <br/> |一个 **ActionParameter**。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Actions 中的 Action 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> |这些 **Action** 所属的 **ActionParameters**。  <br/> |
   

## Action 元素
<a name="bkmk_Actions"> </a>

指定外部内容类型的操作列表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Actions></Actions>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Actions 中的 Action 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> |外部内容类型的操作。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |这些操作所属的外部内容类型。  <br/> |
   

## Association 元素
<a name="bkmk_Association"> </a>

Association 元素链接系统内的相关外部内容类型。例如，某个客户在 AdventureWorks 系统中与某个销售订单关联：客户提交了销售订单。关联保留指向源外部内容类型和目标外部内容类型的指针，以及指向允许客户端从源外部内容类型获取目标外部内容类型的业务逻辑（ **MethodInstance**对象）的指针。 **Association** 的通道是对外部系统的方法调用。
  
    
    

  
    
    
 **命名空间：** http://schemas.microsoft.com/windows/2007/BusinessDataCatalog
  
    
    
 **架构：** BDCMetadata
  
    
    

> **重要信息**
> 属性区分大小写。 
  
    
    


**属性**


|**属性**|**类型**|**描述**|**必需**|**默认值**|**限制/接受值**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**HideOnProfilePage** <br/> |**System.Boolean** <br/> |指定是否应将相关外部内容类型添加到主外部内容类型的配置文件页面。  <br/> |可选  <br/> |||
   



```XML
<Association Type = "String" Default = "Boolean" ReturnParameterName = "String" ReturnTypeDescriptorName = "String" ReturnTypeDescriptorLevel = "Integer" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Association>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Type** <br/> |必需。  <br/> 指定关联类型的 **MethodInstanceType**。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|AssociationNavigator  <br/> |**MethodInstance** 是一个 **AssociationNavigator**。  <br/> |
|Associator  <br/> |**MethodInstance** 是一个 **Associator**。  <br/> |
|Disassociator  <br/> |**MethodInstance** 是一个 **Disassociator**。  <br/> |
|**BulkAssociatedIdEnumerator** <br/> |**MethodInstance** 是一个 **BulkAssociatedIdEnumerator**。  <br/> |
|**BulkAssociationNavigator** <br/> |**MethodInstance** 是一个 **BulkAssociationNavigator**。  <br/> |
   
|
|Default  <br/> |可选。  <br/> 指定关联是否为在包含外部内容类型中共享其类型的所有关联的默认项。如果设置为 **true**，则关联为在包含外部内容类型中共享其类型的所有关联的默认项。如果设置为 **false**，则关联不是在包含外部内容类型中共享其类型的所有关联的默认项。  <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|ReturnParameterName  <br/> |可选。  <br/> 包含关联 **ReturnTypeDescriptor** 的参数的名称。参数的 **Direction** 属性必须包含"Out"、"InOut"或"Return"值中的一个。 <br/> 属性类型： **String** <br/> |
|ReturnTypeDescriptorName  <br/> |可选。  <br/> 此属性已被弃用。请改用 **ReturnTypeDescriptorPath**。  <br/> 属性类型： **String** <br/> |
|ReturnTypeDescriptorLevel  <br/> |可选。  <br/> 此属性已被弃用。请改用 **ReturnTypeDescriptorPath**。  <br/> 属性类型： **Integer** <br/> |
|ReturnTypeDescriptorPath  <br/> |可选。  <br/> 关联的 **TypeDescriptor** 的虚线路径。 <br/> 属性类型： **String** <br/> |
|Name  <br/> |必需。  <br/> 关联名称。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |可选。  <br/> 关联的默认显示名称。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |可选。  <br/> 指定是否频繁使用此关联。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**LocalizedDisplayNames** 元素为关联指定已本地化名称的列表。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |Properties 元素指定关联的属性。  <br/> |
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**AccessControlList** 元素为关联指定一组访问权限。 <br/> |
| [Association 中的 SourceEntity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/19fb5f38-4e85-7fb0-2562-281b9a9ffbef%28Office.15%29.aspx) <br/> |**SourceEntity** 元素指定关联中的源外部内容类型。 <br/> |
| [Association 中的 DestinationEntity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/15c53c3b-888d-67c7-af7d-ef36922eeebc%28Office.15%29.aspx) <br/> |**DestinationEntity** 元素指定关联中的目标外部内容类型。 <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Method 中的 MethodInstances 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/dae3aeae-e72a-0b52-1348-f5e5cd31109f%28Office.15%29.aspx) <br/> |包含关联的 **MethodInstances** 元素。 <br/> |
   

## AssociationGroup 元素
<a name="bkmk_AssociationGroup"> </a>

指定 **AssociationGroup**。 **AssociationGroup** 是将相关的 **AssociationMethods** 关联在一起的构造结构。例如， **GetOrdersForCustomer**、 **GetCustomerForOrder** 和 **AssociateCustomerToOrder** 是处理客户与订单之间的相同关系的所有关联方法。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    
必须在 Entity 元素上定义 **AssociationGroup**，此元素作为未标记为 **Reverse** 的 **AssociationReferences** 的目标或标记为 Reverse 的 **AssociationReferences** 的源。
  
    
    



```XML
<AssociationGroup Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </AssociationGroup>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Name** <br/> |必需。  <br/> **AssociationGroup** 的名称。 <br/> 属性类型： **String** <br/> |
|**DefaultDisplayName** <br/> |可选。  <br/> **AssociationGroup** 的默认显示名称。 <br/> 属性类型： **String** <br/> |
|**IsCached** <br/> |可选。  <br/> 指定是否频繁使用 **AssociationGroup**。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**AssociationGroup** 的本地化名称。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**AssociationGroup** 的属性。 <br/> |
| [AssociationGroup 中的 AssociationReference 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/e32c5267-53b0-9ff0-6e9a-1cb00d9f1d57%28Office.15%29.aspx) <br/> |**AssociationGroup** 的 **AssociationReference**。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entity 中的 AssociationGroups 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b50c2648-daea-d8c0-039a-b95590b9924c%28Office.15%29.aspx) <br/> |包含此 **AssociationGroups** 的 **AssociationGroup** 元素。 <br/> |
   

## AssociationGroups 元素
<a name="bkmk_AssociationGroups"> </a>

指定 **AssociationGroup** 元素的列表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<AssociationGroups></AssociationGroups>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [AssociationGroups 中的 AssociationGroup 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> |一个 **AssociationGroup**。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |与此 **AssociationGroups** 元素相关的外部内容类型。 <br/> |
   

## AssociationReference 元素
<a name="bkmk_AssociationReference"> </a>

在 **AssociationGroup** 中指定 **AssociationReference**。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<AssociationReference EntityNamespace = "String" EntityName = "String" AssociationName = "String" Reverse = "Boolean"> </AssociationReference>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|EntityNamespace  <br/> |可选。  <br/> 用于定义 **Association** 的外部内容类型的命名空间。如果指定 **EntityName**，则 **EntityNamespace** 是必需的。 <br/> 属性类型： **String** <br/> |
|EntityName  <br/> |可选。  <br/> 用于定义 **Association** 的外部内容类型的命名空间。如果指定 **EntityNamespace**，则 **EntityName** 是必需的。 <br/> 属性类型： **String** <br/> |
|AssociationName  <br/> |必需。  <br/> **Association** 的名称。 <br/> 属性类型： **String** <br/> |
|反转  <br/> |可选。  <br/> 指定引用的 **Association** 已将其源和目标反转。这表示 **Association** 与同一 **AssociationGroup** 中的其他关联的工作方向相反。例如，如果 **AssociationGroup** 引用 **Association**"GetOrdersForCustomer"（它返回给定客户项目的订单项目），则 **AssociationGroup** 的工作方向为客户到订单。必须将引用另一个关联 "GetCustomerForOrder" 的另一个 **AssociationReference** 标记为反转，因为此关联的工作方向为订单到客户。 <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [AssociationGroups 中的 AssociationGroup 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> |此 **AssociationReference** 所属的 **AssociationGroup**。  <br/> |
   

## ConvertType 元素
<a name="bkmk_ConvertType"> </a>

指定将数据值的数据类型转换为另一种数据类型的规则。
  
    
    
 **Namespace:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **Schema:** BDCMetadata
  
    
    
Convert 元素指定将数据值的数据类型转换为另一种数据类型的规则。在按顺序应用规则时，此规则指定将数据值的数据类型转换为 BDCType 属性指定的数据类型。在反向应用规则时，此规则指定将数据值的数据类型转换为 **LOBType** 属性指定的数据类型。例如，此规则可以指定将从外部系统获取的日期值转换为将最终显示给用户的区域性和区域设置敏感的字符串，并将该字符串的更新值转换回与外部系统兼容的日期。
  
    
    

> **警告**
> **ConvertType** 不支持 **System.String** 和 **System.DateTime** 之间的非公历转换。
  
    
    




```XML
<ConvertType LOBType = "String" BDCType = "String"> </ConvertType>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|LOBType  <br/> |必需。  <br/> 反向应用规则时要将数据值转换为的数据类型。  <br/> 属性类型： **String** <br/> |
|BDCType  <br/> |必需。  <br/> 按顺序应用规则时要将数据值转换为的数据类型。  <br/> 属性类型： **String** <br/> |
|LOBLocale  <br/> |可选。  <br/> 从外部系统收到的数据的区域设置。  <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 中的 Interpretation 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/730f9590-ab40-85b8-eb97-8fd9d8e33c8a%28Office.15%29.aspx) <br/> |应用于 **TypeDescriptor** 所表示的数据结构中存储的数据的规则。 <br/> |
   

## DefaultValue 元素
<a name="bkmk_DefaultValue"> </a>

表示默认值。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<DefaultValue MethodInstanceName = "String" Type = "String"> </DefaultValue>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**MethodInstanceName** <br/> |必需。  <br/> 要将此 DefaultValue 应用于的 **MethodInstance** 的名称。 <br/> 属性类型： **String** <br/> |
|**Type** <br/> | 必需。 <br/>  默认值的数据类型。 <br/>  以下是此属性的可接受的值。 <br/> **System.Int16** <br/> **System.Int32** <br/> **System.Int64** <br/> **System.Single** <br/> **System.Double** <br/> **System.Decimal** <br/> **System.Boolean** <br/> **System.Byte** <br/> **System.UInt16** <br/> **System.UInt32** <br/> **System.UInt64** <br/> **System.Guid** <br/> **System.String** <br/> **System.DateTime** <br/>  任何其他可序列化的类型（例如，此处 `Type.IsSerializable == true`）  <br/>  属性类型： **String** <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 中的 DefaultValues 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/635295d1-0f85-6308-976b-d0cb483dece6%28Office.15%29.aspx)||
   

## DefaultValues 元素
<a name="bkmk_DefaultValues"> </a>

指定 **TypeDescriptor** 的 **DefaultValues** 列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<DefaultValues></DefaultValues>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [DefaultValues 中的 DefaultValue 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ddb67f64-6361-7b59-6724-4680484d585d%28Office.15%29.aspx) <br/> |**MethodInstance** 的 **TypeDescriptor** 的默认值。 <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> |这些 **TypeDescriptor** 所属的 **DefaultValues**。  <br/> |
   

## DestinationEntity 元素
<a name="bkmk_DestinationEntity"> </a>

指定 **Association** 中的目标外部内容类型。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<DestinationEntity Namespace = "String" Name = "String"> </DestinationEntity>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Namespace** <br/> |必需。  <br/> 实体命名空间的名称。  <br/> 属性类型： **String** <br/> |
|**Name** <br/> |必需。  <br/> 目标实体的名称。  <br/> 属性类型： **String** <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx)||
   

## Entities 元素
<a name="bkmk_Entities"> </a>

指定外部系统中的外部内容类型的类表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Entities></Entities>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |外部系统中的外部内容类型。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |外部系统。  <br/> |
   

## Entity 元素
<a name="bkmk_Entity"> </a>

指定外部内容类型。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Entity Namespace = "String" Version = "String" EstimatedInstanceCount = "Integer" DefaultOperationMode = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Entity>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Namespace** <br/> |必需。  <br/> 此外部内容类型所属的命名空间。  <br/> 属性类型： **String** <br/> > **注释**> 命名空间不应包含特殊字符" *****"。           |
|**Version** <br/> |必需。  <br/> 此外部内容类型的版本号。  <br/> 属性类型： **String** <br/> > **警告**> 当 BDC 模型发生更改时，必须增加外部内容类型的版本号。如果外部内容类型的结构发生更改，应增加主版本号。结构性更改的示例包括向 **SpecificFinder** 添加字段或更改标识符字段。如果更改不影响外部内容类型的结构（例如，添加 Creator 方法、更改连接信息或更改 **LobSystems** 和类型描述符的名称），应更改内部版本号和修订号。          |
|**EstimatedInstanceCount** <br/> |可选。  <br/> 外部系统包含的外部项的估计数目。  <br/> 默认值：10000  <br/> 属性类型： **Integer** <br/> |
|**DefaultOperationMode** <br/> |可选。  <br/> 指定在创建、删除、更新或读取外部项时与外部系统交互时的默认行为。  <br/> 默认值：Default  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|Online  <br/> |绕过所有操作的缓存的外部项，直接与外部系统交互。  <br/> |
|Cached  <br/> |直接针对缓存的外部项执行 **Create** 、 **Read** 、 **Update** 和 **Delete** 操作。对于 **Read** 操作，如果请求的外部项在缓存中可用，请使用缓存中的外部项。否则，绕过缓存从外部系统获取外部项，然后将它放置在缓存中以便以后使用。 <br/> |
|Offline  <br/> |只针对缓存的外部项执行 **Create** 、 **Read** 、 **Update** 和 **Delete** 操作。 <br/> |
|Default  <br/> |使用系统默认行为。如果环境支持缓存外部项，则使用缓存模式。  <br/> |
   
|
|名称  <br/> |必需。  <br/> 外部内容类型的名称。  <br/> 属性类型： **String** <br/> > **注释**> 外部内容类型的名称不应包含星号特殊字符" *****"。           |
|DefaultDisplayName  <br/> |可选。  <br/> 外部内容类型的默认显示名称。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |可选。  <br/> 指定此外部内容类型是否将经常使用。如果设置为 True，Business Data Connectivity (BDC) 服务 将在内存中缓存此外部内容类型。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |此外部内容类型的本地化显示名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |此外部内容类型的属性。  <br/> |
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |此外部内容类型的访问控制列表 (ACL)。  <br/> |
| [Entity 中的 Identifiers 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/6566cb43-4f9e-9a2e-7ec0-89057d7daacc%28Office.15%29.aspx) <br/> |外部内容类型的标识符。  <br/> |
| [Entity 中的 Methods 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/42a24b32-bd97-4067-2e25-681d876d29fd%28Office.15%29.aspx) <br/> |外部内容类型的方法。  <br/> |
| [Entity 中的 AssociationGroups 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b50c2648-daea-d8c0-039a-b95590b9924c%28Office.15%29.aspx) <br/> |外部内容类型的关联组。  <br/> |
| [Entity 中的 Actions 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/c5a6c08d-a3df-61db-3ce3-1e6837bbf221%28Office.15%29.aspx) <br/> |外部内容类型的操作。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystem 中的 Entities 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/fa121ed1-160a-03c9-df42-851ddc2528d5%28Office.15%29.aspx) <br/> |此外部系统中外部内容类型的列表。  <br/> |
   

## FilterDescriptor 元素
<a name="bkmk_FilterDescriptor"> </a>

指定方法的筛选器描述符。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<FilterDescriptor Type = "String" FilterField = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </FilterDescriptor>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|Type  <br/> |必需。  <br/> 筛选器描述符的类型。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|Limit  <br/> |查询外部系统时使用，它的值可以解释为调用所属方法时返回的外部项目 ( **EntityInstances**) 数目的限制。  <br/> |
|PageNumber  <br/> ||
|Wildcard  <br/> |查询外部系统时使用。它的值表示常规字符和通配符模式，该模式与一组 **EntityInstances** 的特定字段的值进行匹配。外部系统仅返回其字段值与指定模式匹配的那些 **EntityInstances**。  <br/> |
|UserContext  <br/> |查询外部系统时使用。它的值可以由任何客户端应用程序自动设置为调用外部系统的用户的标识。然后，外部系统可以使用该值进行授权并筛选返回的结果。  <br/> |
|UserCulture  <br/> ||
|Username  <br/> ||
|Password  <br/> ||
|LastId  <br/> ||
|SsoTicket  <br/> ||
|UserProfile  <br/> |查询外部系统时使用。它的值可以通过检查当前用户的配置文件获得。外部系统可以使用它的值筛选返回的结果。  <br/> |
|Comparison  <br/> |查询外部系统时使用。外部系统可以将 **ComparisonFilter** 值与一组 **EntityInstances** 的特定字段的值进行比较，并仅返回其字段值通过了比较测试的那些 **EntityInstances**。  <br/> |
|Timestamp  <br/> ||
|Input  <br/> |在调用外部系统中的操作时使用。外部系统可以使用 **InputFilter** 的值作为操作的其他参数。 <br/> |
|Output  <br/> |在调用外部系统中的操作时使用。 **ReturnTypeDescriptor** 不能捕获的其他操作结果可以作为 **InputOutputFilter** 的值进行检索。 <br/> |
|InputOutput  <br/> |在调用外部系统中的操作时使用。外部系统可以使用 **InputOutputFilter** 的值作为操作的其他参数， **ReturnTypeDescriptor** 不能捕获的其他操作结果可以作为 **InputOutputFilter** 的值进行检索。 <br/> |
|Batching  <br/> ||
|BatchingTermination  <br/> ||
|ActivityId  <br/> |**ActivityId** 在调用外部系统的操作时使用。它的值设置为表示当前操作上下文的 GUID。如果没有提供此类值，则此筛选器将生成随机 GUID。在 SharePoint Foundation 2010 中，此筛选器使用 **CorrelationID**。  <br/> |
   
|
|FilterField  <br/> |可选。  <br/> 属性类型： **String** <br/> |
|名称  <br/> |必需。  <br/> 筛选器描述符的名称。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |可选。  <br/> 筛选器描述符的默认显示名称。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |可选。  <br/> 指定是否经常使用此筛选器描述符。如果设置为 **true**，则 Business Data Connectivity (BDC) 服务 会在内存中缓存此筛选器描述符。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |此筛选器描述符的本地化显示名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |此筛选器描述符的属性。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Method 中的 FilterDescriptors 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/33d8e418-ddbb-e1ac-b145-836ed9f36e5c%28Office.15%29.aspx) <br/> |方法的筛选器描述符列表。  <br/> |
   

## FilterDescriptors 元素
<a name="bkmk_FilterDescriptors"> </a>

指定方法的筛选器描述符的列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<FilterDescriptors></FilterDescriptors>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [FilterDescriptors 中的 FilterDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/8ce0a852-38f9-75d2-8258-27c57418f53c%28Office.15%29.aspx) <br/> |筛选器描述符。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |此筛选器描述符列表所属的方法。  <br/> |
   

## Identifier 元素
<a name="bkmk_Identifier"> </a>

指定外部内容类型的标识符。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    

> **注释**
> Business Data Connectivity (BDC) 服务 支持将标识符映射到数据类型可为空的字段。不过，对于主标识符，BDC 会在这些标识符的值为 **null** 时引发错误。
  
    
    




```XML
<Identifier TypeName = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Identifier>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|TypeName  <br/> |必需。  <br/> 与标识符相对应的值的数据类型。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|System.Boolean  <br/> |一位。  <br/> |
|System.Byte  <br/> |一个介于 0 到 255 之间（含这两个值）的数字。  <br/> |
|System.Char  <br/> |一个 Unicode 字符。  <br/> |
|System.DateTime  <br/> |一个介于公元 1 年 1 月 1 日午夜 12:00:00 到公元 9999 年 12 月 31 日 11:59:59 P.M. 之间（含这两个值）的日期和时间，分辨率为 100 纳秒。  <br/> |
|System.Decimal  <br/> |一个介于 -79,228,162,514,264,337,593,543,950,335 到 +79,228,162,514,264,337,593,543,950,335 之间（含这两个值）的数字。  <br/> |
|System.Double  <br/> |一个介于 -1.79769313486232e308 到 +1.79769313486232e308 之间（含这两个值）的双精度数字，以及正零、负零、无穷大正数、无穷大负数和非数值 (NAN)。  <br/> |
|System.Guid  <br/> |一个 GUID。  <br/> |
|System.Int16  <br/> |一个介于 -32768 到 +32767 之间（含这两个值）的数字。  <br/> |
|System.Int32  <br/> |一个介于 0 到 4,294,967,295 之间（含这两个值）的数字。  <br/> |
|System.Int64  <br/> |一个介于 0 到 18,446,744,073,709,551,615 之间（含这两个值）的数字。  <br/> |
|System.SByte  <br/> |一个介于 -128 到 +127 之间（含这两个值）的数字。  <br/> |
|System.Single  <br/> |一个介于 -3.402823e38 到 +3.402823e38 之间（含这两个值）的单精度数字。  <br/> |
|System.String  <br/> |一个 Unicode 文本字符串。  <br/> |
|System.TimeSpan  <br/> |一个介于 -10675199 天 2 小时 48 分 5 秒 477 毫秒 580 微秒 800 纳秒到 +10675199 天 2 小时 48 分 5 秒 477 毫秒 580 微秒 800 纳秒之间（含这两个值）的持续时间，分辨率为 100 纳秒。  <br/> |
|System.UInt16  <br/> |一个介于 0 到 65535 之间（含这两个值）的数字。  <br/> |
|System.UInt32  <br/> |一个介于 0 到 4,294,967,295 之间（含这两个值）的数字。  <br/> |
|System.UInt64  <br/> |一个介于 0 到 18,446,744,709,551,615 之间（含这两个值）的数字。  <br/> |
   
|
|名称  <br/> |必需。  <br/> 标识符的名称。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |可选。  <br/> 标识符的默认显示名称。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |可选。  <br/> 指定是否频繁使用此标识符。如果设置为 **true**，则 Business Data Connectivity (BDC) 服务 将此标识符缓存到内存中。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |标识符的本地化显示名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |标识符的属性。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entity 中的 Identifiers 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/6566cb43-4f9e-9a2e-7ec0-89057d7daacc%28Office.15%29.aspx) <br/> |外部内容类型的标识符列表。  <br/> |
   

## Identifiers 元素
<a name="bkmk_Identifiers"> </a>

指定外部内容类型的标识符的列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Identifiers></Identifiers>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Identifiers 中的 Identifier 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/c4abf09b-10b6-0007-9214-35d5fe675be7%28Office.15%29.aspx) <br/> |指定标识符。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |包含此标识符列表的外部内容类型。  <br/> |
   

## Interpretation 元素
<a name="bkmk_Interpretation"> </a>

指定要应用于存储在由 **TypeDescriptor** 表示的数据结构中的数据的规则。这些规则通常专用于更改由外部系统返回的数据值，以便能更轻松地在用户界面中表示它们。在从外部系统获取数据值时，必须按照在 **Interpretation** 元素中指定规则的顺序来应用这些指定的规则。必须将第一个规则应用于从外部系统接收的数据值；后面的规则将应用于通过应用上一个规则所生成的数据值。在将数据值发送到外部系统时，必须按照在 **Interpretation** 元素中指定规则的顺序的相反顺序来应用这些指定的规则。必须将第一个规则应用于从用户接收的数据值；后面的规则将应用于通过应用上一个规则所生成的数据值。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Interpretation></Interpretation>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Interpretation 中的 ConvertType 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/c474cf2c-b631-f3c9-daf1-f05d3e0d385f%28Office.15%29.aspx) <br/> |一个 **ConvertType** 元素，它指定从一个数据类型到另一个数据类型的转换。 <br/> |
| [Interpretation 中的 NormalizeDateTime 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/bbae3bfa-0754-d576-2bee-1ac0e8508a57%28Office.15%29.aspx) <br/> |一个 **NormalizeDateTime** 元素，它指定从外部系统获得的值的日期和时间表示形式到另一种表示形式的转换。 <br/> |
|NormalizeString  <br/> |一个 **NormalizeString** 元素，它指定从外部系统获得的值的字符串表示形式到另一种表示形式的转换。 <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> |**TypeDescriptor** 元素。 <br/> |
   

## LobSystem 元素
<a name="bkmk_LobSystem"> </a>

表示外部数据源。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<LobSystem Type = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </LobSystem>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|类型  <br/> |**LobSystem** 的类型。 <br/> 必需。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|Database  <br/> |表示的外部数据源为数据库。  <br/> |
|DotNetAssembly  <br/> |表示的外部数据源为 .NET Framework 类的集合。  <br/> |
|Wcf  <br/> |表示的外部数据源为 WCF 服务端点。  <br/> |
|WebService  <br/> |表示的外部数据源为 Web 服务。已弃用，改用 Wcf。  <br/> |
|Custom  <br/> |表示的外部数据源实现了自定义连接器来管理连接和数据传输。  <br/> |
   
|
|名称  <br/> |**LobSystem** 的名称。 <br/> 必需。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |**LobSystem** 的默认显示名称。 <br/> 可选。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |指定是否频繁使用 **LobSystem**。如果频繁使用，则Business Data Connectivity (BDC) 服务 缓存 **LobSystem**。  <br/> 可选。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**LobSystem** 的本地化名称。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |指定 **LobSystem** 的属性。 <br/> |
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |指定 **LobSystem** 的访问控制列表 (ACL)。 <br/> |
| [LobSystem 中的 Proxy 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/8ec2e7b0-156f-ff4a-a87b-fe5764e4875b%28Office.15%29.aspx) <br/> |如果此元素不存在，则指定与生成的代理相同的用户提供的代理。  <br/> |
| [LobSystem 中的 LobSystemInstances 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/122e419a-0497-afdf-1117-a82ab429f3eb%28Office.15%29.aspx) <br/> |为此外部系统指定外部系统实例。  <br/> |
| [LobSystem 中的 Entities 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/fa121ed1-160a-03c9-df42-851ddc2528d5%28Office.15%29.aspx) <br/> |在此外部系统中指定外部内容类型。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Model 中的 LobSystems 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d9bf0ca9-fb79-e3a5-cc84-9510d93798cb%28Office.15%29.aspx) <br/> |在此模型中指定外部系统列表。  <br/> |
   

## LobSystemInstance 元素
<a name="bkmk_LobSystemInstance"> </a>

指定外部系统实例。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<LobSystemInstance Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </LobSystemInstance>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|名称  <br/> |必需。  <br/> 外部系统实例的名称。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |可选。  <br/> 外部系统实例的默认显示名称。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |可选。  <br/> 指定是否经常使用此外部系统实例。如果设置为 **true**，Business Data Connectivity (BDC) 服务 将缓存外部系统实例。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |此外部系统实例的本地化名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |此外部系统实例的属性。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystem 中的 LobSystemInstances 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/122e419a-0497-afdf-1117-a82ab429f3eb%28Office.15%29.aspx) <br/> |外部系统实例的列表。  <br/> |
   

## LobSystemInstances 元素
<a name="bkmk_LobSystemInstances"> </a>

指定外部系统实例的列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<LobSystemInstances></LobSystemInstances>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystemInstances 中的 LobSystemInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a0c37891-ef4f-58af-445c-5ff4d5ad6cef%28Office.15%29.aspx) <br/> |外部系统实例。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |外部系统。  <br/> |
   

## LobSystems 元素
<a name="bkmk_LobSystems"> </a>

指定模型的 **LobSystem** 元素的列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<LobSystems></LobSystems>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |指定外部系统的 **LobSystem**。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Model 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> |应用程序定义（BDC 模型）。  <br/> |
   

## LocalizedDisplayName 元素
<a name="bkmk_LocalizedDisplayName"> </a>

指定本地化名称。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<LocalizedDisplayName LCID = "Integer"> </LocalizedDisplayName>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|LCID  <br/> |必需。  <br/> 语言代码标识符 (LCID)。  <br/> 属性类型： **Integer** <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |包含此 **LocalizedDisplayNames** 的 **LocalizedDisplayName** 元素。 <br/> |
   

## LocalizedDisplayNames 元素
<a name="bkmk_LocalizedDisplayNames"> </a>

指定 **MetadataObject** 的本地化名称的列表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<LocalizedDisplayNames></LocalizedDisplayNames>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LocalizedDisplayNames 中的 LocalizedDisplayName 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/93fb80ef-6347-b463-da90-4980d872678e%28Office.15%29.aspx) <br/> |本地化名称。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Model 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> ||
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> ||
| [LobSystemInstances 中的 LobSystemInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a0c37891-ef4f-58af-445c-5ff4d5ad6cef%28Office.15%29.aspx) <br/> ||
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> ||
| [Identifiers 中的 Identifier 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/c4abf09b-10b6-0007-9214-35d5fe675be7%28Office.15%29.aspx) <br/> ||
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> ||
| [FilterDescriptors 中的 FilterDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/8ce0a852-38f9-75d2-8258-27c57418f53c%28Office.15%29.aspx) <br/> ||
| [Parameters 中的 Parameter 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/811cad0b-ba71-8be0-0765-3e0dec18a0d3%28Office.15%29.aspx) <br/> ||
| [TypeDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> ||
| [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> ||
| [MethodInstances 中的 MethodInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> ||
| [AssociationGroups 中的 AssociationGroup 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> ||
| [Actions 中的 Action 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> ||
| [ActionParameters 中的 ActionParameter 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/1f5fa96a-1bff-f007-984d-a644cbbb2648%28Office.15%29.aspx) <br/> ||
   

## MetadataObject 元素
<a name="bkmk_MetadataObject"> </a>

 **命名空间：**
  
    
    
 **架构：**
  
    
    



```XML

```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
 **子元素**
  
    
    
 **父元素**
  
    
    

## Method 元素
<a name="bkmk_Method"> </a>

指定外部内容类型的方法。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Method IsStatic = "Boolean" LobName = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Method>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|IsStatic  <br/> |可选。  <br/> 指定执行此方法时是否需要一个外部项 ( **EntityInstance**) 来充当执行上下文。如果设置为 **true**，则此方法表示一个静态方法，它不需要特定的 **EntityInstance** 来提供执行上下文。如果设置为 **false**，则此方法表示一个实例方法，它需要一个 **EntityInstance** 来提供执行上下文。 <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
|LobName  <br/> |可选。  <br/> 外部系统中定义的由此方法表示的操作的名称。  <br/> 属性类型： **String** <br/> |
|名称  <br/> |必需。  <br/> 此方法的名称。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |可选。  <br/> 方法的默认显示名称。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |可选。  <br/> 指定是否频繁使用此方法。如果设置为 **true**，则 Business Data Connectivity (BDC) 服务 将此方法缓存到内存中。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |此方法的本地化显示名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |此方法的属性。  <br/> |
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |此方法的访问控制列表 (ACL)。  <br/> |
| [Method 中的 FilterDescriptors 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/33d8e418-ddbb-e1ac-b145-836ed9f36e5c%28Office.15%29.aspx) <br/> |此方法的筛选器描述符。  <br/> |
| [Method 中的 Parameters 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/343f4c25-e122-1a4c-2b80-bb8f25e3cc82%28Office.15%29.aspx) <br/> |此方法的参数。一个方法不能有多个返回参数。  <br/> |
| [Method 中的 MethodInstances 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/dae3aeae-e72a-0b52-1348-f5e5cd31109f%28Office.15%29.aspx) <br/> |此方法的方法实例。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entity 中的 Methods 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/42a24b32-bd97-4067-2e25-681d876d29fd%28Office.15%29.aspx) <br/> |外部内容类型的方法列表。  <br/> |
   

## MethodInstance 元素
<a name="bkmk_MethodInstance"> </a>

指定 **MethodInstance**。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    
在 BDC 模型中，以下两种情况会导致在运行时出现  [InvalidOperationException](http://msdn.microsoft.com/library/frlrfSystemInvalidOperationExceptionClassTopic.aspx)：
  
    
    

- 两个 **SpecificFinder** 方法实例，它们返回相同的字段集。
    
  
- 两个 **SpecificFinder** 方法实例，它们具有相同数量的字段并与另一个方法实例（如 **Finder**）共享相同数量的字段。
    
  



```XML
<MethodInstance Type = "Strig" Default = "Boolean" ReturnParameterName = "String" ReturnTypeDescriptorName = "String" ReturnTypeDescriptorLevel = "Integer" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </MethodInstance>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Type** <br/> |必需。  <br/> 指定 **MethodInstance** 的类型。 <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|Finder  <br/> |一种 **MethodInstance** 类型，可调用它以返回包含特定 **Entity** 的零个或多个 **EntityInstances** 的集合。 **Finder** 输入由包含 **Finder** 的 **Method** 中包含的 **FilterDescriptors** 定义。 <br/> |
|SpecificFinder  <br/> |一种 **MethodInstance** 类型，可调用它以返回特定 **Entity**（给定其 **EntityInstanceId**）的特定 **EntityInstance**。 **SpecificFinder** 输入由与 **Entity** 关联的 **Identifiers** 定义和排序。 <br/> |
|GenericInvoker  <br/> |一种 **MethodInstance** 类型，可调用它以便在外部系统中执行特定任务。 **GenericInvoker** 输入和输出因 **Method** 而异。 <br/> |
|IdEnumerator  <br/> |一种 **MethodInstance** 类型，可调用它以返回表示特定 **Entity** 的 **EntityInstances** 的标识的 **Field** 值。 **IdEnumerator** 输入是由 **FilterDescriptors** 定义的，后者包含在包含用于获取 ID 列表的 **IdEnumerator** 的方法中，这些 ID 是可搜索的每个实体的唯一键。此方法实例在 SharePoint Server 中启用了外部数据搜索。 <br/> |
|ChangedIdEnumerator  <br/> |一种 **MethodInstance** 类型，可调用它以检索经指定时间后在外部系统中修改过的 **EntityInstances** 的 **EntityInstanceIds**。  <br/> |
|DeletedIdEnumerator  <br/> |一种 **MethodInstance** 类型，可调用它以检索经指定时间后从外部系统中删除的 **EntityInstances** 的 **EntityInstanceIds**。  <br/> |
|Scalar  <br/> |一个 **MethodInstance**，它返回可在外部系统中调用的单一值。例如，可使用标量方法实例从外部系统获取到目前为止实现的总销售额。 **Entities** 具有零个或多个标量方法实例。 <br/> |
|AccessChecker  <br/> |一种 **MethodInstance** 类型，可调用它以检索调用安全主体拥有的针对每个 **EntityInstances** 集合（由指定的 **EntityInstanceIds** 标识）的权限。 <br/> |
|Creator  <br/> |一种 **MethodInstance** 类型，可调用它以创建 **EntityInstance**。创建 **EntityInstance** 所需的字段集合称为"生成器视图"。 <br/> |
|Deleter  <br/> |一种 **MethodInstance** 类型，可调用它以删除具有指定的 **EntityInstanceId** 的 **EntityInstance**。  <br/> |
|Updater  <br/> |一种 **MethodInstance** 类型，可调用它以更新由指定的 **EntityInstanceId** 标识的 **EntityInstance**。更新 **EntityInstance** 所需的字段集合称为"更新程序视图"。更改其值前应先传递这些值的字段的集合称为"预更新程序视图"。 <br/> |
|StreamAccessor  <br/> |一种 **MethodInstance** 类型，可调用它以检索采用字节数据流形式的 **EntityInstance** 的字段。 <br/> |
|BinarySecurityDescriptorAccessor  <br/> |一种 **MethodInstance** 类型，可调用它以从外部系统检索字节序列。特定于系统的字节序列描述一组安全主体以及每个安全主体拥有的针对 **EntityInstance**（由指定的 **EntityInstanceId** 标识）的关联权限。 <br/> |
|BulkSpecificFinder  <br/> |一种 **MethodInstance** 类型，可调用它以返回 **Entity** 的一组特定的 **EntityInstances**（给定一组相应的 **EntityInstanceIds**）。  <br/> |
|BulkIdEnumerator  <br/> |一种 **MethodInstance** 类型，可调用它以检索有关对应于给定标识的外部项的最少信息。此方法实例可用于优化缓存数据的同步。此方法应仅返回对应于给定 **Identities** 的外部项的标识和版本信息，调用的应用程序可将这些标识与本地版本进行比较以确定是否有任何项发生了更改，如果有，则请求更改的外部项以更新缓存数据。 <br/> |
   
|
|**Default** <br/> |可选。  <br/> 指定 **MethodInstance** 是否为所有 **MethodInstances**（它们在包含外部内容类型 ( **Entity**) 中共享其类型）中的默认值。  <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**ReturnParameterName** <br/> |可选。  <br/> **Parameter**（它包含 **MethodInstance** 的 **ReturnTypeDescriptor**）的名称。 **Parameter** 的 **Direction** 属性必须是具有 **Out**、 **InOut** 或 **Return** 值的 **ParameterDirection** 属性。 <br/> 必须为所有类型的 **MethodInstances**（ **GenericInvoker**、 **Creator**、 **Deleter** 和 **Updater** 除外）指定此属性。 <br/> 属性类型： **String** <br/> |
|**ReturnTypeDescriptorLevel** <br/> |可选。  <br/> 此属性已被弃用。请改用 **ReturnTypeDescriptorPath**。  <br/> 属性类型： **Integer** <br/> |
|**ReturnTypeDescriptorPath** <br/> |可选。  <br/> 关联的 **TypeDescriptor** 的虚线路径。 <br/> 属性类型： **String** <br/> |
|**Name** <br/> |必需。  <br/> 指定 **MethodInstance** 的名称。 <br/> 属性类型： **String** <br/> |
|**DefaultDisplayName** <br/> |可选。  <br/> 指定 **MethodInstance** 的默认显示名称。 <br/> 属性类型： **String** <br/> |
|**IsCached** <br/> |可选。  <br/> 指定是否频繁使用 **MethodInstance**。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**MethodInstance** 的本地化显示名称。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**MethodInstance** 的属性。 <br/> |
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**MethodInstance** 访问控制列表 (ACL)。 <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Method 中的 MethodInstances 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/dae3aeae-e72a-0b52-1348-f5e5cd31109f%28Office.15%29.aspx) <br/> |包含此 **MethodInstances** 的 **MethodInstance** 元素。 <br/> |
   

## MethodInstances 元素
<a name="bkmk_MethodInstances"> </a>

指定某个方法的关联和方法实例的列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<MethodInstances></MethodInstances>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> |一个关联。  <br/> |
| [MethodInstances 中的 MethodInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> |一个方法实例。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |此方法实例所属的方法。  <br/> |
   

## Methods 元素
<a name="bkmk_Methods"> </a>

指定外部内容类型的方法的列表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Methods></Methods>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |指定方法。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |此方法列表所属的外部内容类型。  <br/> |
   

## Model 元素
<a name="bkmk_Model"> </a>

指定表示应用程序定义的根元素。模型定义由外部应用程序包含的外部内容类型。 
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Model Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Model>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|名称  <br/> |**Model** 的名称。 <br/> 必需。  <br/> 属性类型： **String** <br/> |
|DefaultDisplayName  <br/> |**Model** 的默认显示名称。 <br/> 可选。  <br/> 属性类型： **String** <br/> |
|IsCached  <br/> |指定是否频繁使用 **Model**。如果设置为 **true**，则 Business Data Connectivity (BDC) 服务 缓存 **Model**。  <br/> 可选。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**Model** 的本地化名称。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**Model** 的属性。 <br/> |
| [AccessControlList 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**Model** 的访问控制列表 (ACL)。 <br/> |
| [Model 中的 LobSystems 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d9bf0ca9-fb79-e3a5-cc84-9510d93798cb%28Office.15%29.aspx) <br/> |包含在此 **Model** 内部的 **LobSystems**。  <br/> |
   
 **父元素**
  
    
    
无
  
    
    

## NormalizeDateTime 元素
<a name="bkmk_NormalizeDateTime"> </a>

指定用于将日期和时间值的表示形式转换为另一种表示形式的规则。例如，此规则可指定将以协调世界时 (UTC) 表示的值转换为本地时区。 
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<NormalizeDateTime LobDateTimeMode = "String"> </NormalizeDateTime>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**LobDateTimeMode** <br/> |必需。  <br/> 指定要应用的转换。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|UTC  <br/> |从外部系统收到的值为 UTC（协调世界时）。如果收到的值为 **Local**，则它将转换为 UTC。BDC 将 UTC 发送给外部系统。  <br/> |
|Local  <br/> |从外部系统收到的值为 **Local**。如果从外部系统收到的值为 **Local**，则它将转换为 UTC。BDC 将 **Local** 发送给外部系统。 <br/> |
|Unspecified  <br/> |外部系统发送的值具有 Unspecified 种类。BDC 通过将该种类覆盖为 UTC 来假定值采用 UTC。BDC 将 UTC 值作为 Unspecified 种类发送给外部系统。  <br/> |
   
|
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 中的 Interpretation 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/730f9590-ab40-85b8-eb97-8fd9d8e33c8a%28Office.15%29.aspx) <br/> |一个 **Interpretation** 元素，指定要应用于存储在 **TypeDescriptor** 所表示的数据结构中的数据的规则。 <br/> |
   

## NormalizeString 元素
<a name="bkmk_NormalizeString"> </a>

指定方法的参数。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML

```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
 **子元素**
  
    
    
 **父元素**
  
    
    

## Parameter 元素
<a name="bkmk_Parameter"> </a>

指定方法的参数。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Parameter Direction = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Parameter>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|方向  <br/> |必需。  <br/> 参数的方向。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|In  <br/> |所表示的 **Parameter** 为输入参数。 <br/> |
|Out  <br/> |所表示的参数为输出参数。  <br/> |
|InOut  <br/> |所表示的参数为输入和输出参数。在 C# 中，这些对应于" **ref**"。  <br/> |
|Return  <br/> |所表示的参数为返回参数。  <br/> |
   
|
|**Name** <br/> |必需。  <br/> 参数的名称。  <br/> 属性类型： **String** <br/> |
|**DefaultDisplayName** <br/> |可选。  <br/> 参数的默认显示名称。  <br/> 属性类型： **String** <br/> |
|**IsCached** <br/> |可选。  <br/> 指定是否频繁使用 **Parameter**。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |参数的本地化名称。  <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |参数的属性。  <br/> |
| [TypeDescriptor](http://msdn.microsoft.com/library/30e38d7f-af18-20ec-45ab-0bece071ce67.aspx) <br/> |参数的根类型描述符。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Method 中的 Parameters 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/343f4c25-e122-1a4c-2b80-bb8f25e3cc82%28Office.15%29.aspx) <br/> |包含此参数的 **Parameters** 元素。 <br/> |
   

## Parameters 元素
<a name="bkmk_Parameters"> </a>

指定某个方法的参数的列表。
  
    
    

  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Parameters></Parameters>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Parameters 中的 Parameter 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/811cad0b-ba71-8be0-0765-3e0dec18a0d3%28Office.15%29.aspx) <br/> |一个参数。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |这些参数所属的方法。  <br/> |
   

## Properties 元素
<a name="bkmk_Properties"> </a>

指定元数据对象的属性列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Properties></Properties>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Properties 中的 Property 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/2e6e8d5d-ef3b-c536-f3d1-ad2039b92c24%28Office.15%29.aspx) <br/> |指定一个属性。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [Model 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> ||
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> ||
| [LobSystemInstances 中的 LobSystemInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a0c37891-ef4f-58af-445c-5ff4d5ad6cef%28Office.15%29.aspx) <br/> ||
| [Entities 中的 Entity 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> ||
| [Identifiers 中的 Identifier 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/c4abf09b-10b6-0007-9214-35d5fe675be7%28Office.15%29.aspx) <br/> ||
| [Methods 中的 Method 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> ||
| [FilterDescriptors 中的 FilterDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/8ce0a852-38f9-75d2-8258-27c57418f53c%28Office.15%29.aspx) <br/> ||
| [Parameters 中的 Parameter 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/811cad0b-ba71-8be0-0765-3e0dec18a0d3%28Office.15%29.aspx) <br/> ||
| [TypeDescriptor](http://msdn.microsoft.com/library/30e38d7f-af18-20ec-45ab-0bece071ce67.aspx) <br/> ||
| [TypeDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> ||
| [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> ||
| [MethodInstances 中的 MethodInstance 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> ||
| [AssociationGroups 中的 AssociationGroup 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> ||
| [Actions 中的 Action 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> ||
| [ActionParameters 中的 ActionParameter 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/1f5fa96a-1bff-f007-984d-a644cbbb2648%28Office.15%29.aspx) <br/> ||
   

## Property 元素
<a name="bkmk_Property"> </a>

指定元数据对象的属性的名称和类型。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Property Name = "String" Type = "String"> </Property>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**Name** <br/> |必需。  <br/> 指定该属性的名称。  <br/> 属性类型： **String** <br/> |
|**Type** <br/> |必需。  <br/> 指定该属性的数据类型。  <br/> 属性类型： **String** <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |包含此属性的 **Properties** 元素。 <br/> |
   

## Proxy 元素
<a name="bkmk_Proxy"> </a>

如果此元素不存在，则指定与生成的代理相同的用户提供的代理。这用于通过消除代理生成开销来提高性能。若要指定连接到外部系统的自定义业务逻辑，必须使用 .NET 连接程序集类型外部系统。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Proxy></Proxy>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [LobSystems 中的 LobSystem 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |此代理应用于的 **LobSystem** 元素。 <br/> |
   

## Right 元素
<a name="bkmk_Right"> </a>

指定访问控制条目 (ACE) 的单个访问权限。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<Right BdcRight = "String"> </Right>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|BdcRight  <br/> |必需。  <br/> 拥有权限的安全主体可用的权限。  <br/> 下表列出了该属性可能的值。  <br/> |**值**|**描述**|
|:-----|:-----|
|无  <br/> |无权限。  <br/> |
|Execute  <br/> |表示的安全主体具有调用 **MethodInstance** 的权限。 <br/> |
|Edit  <br/> |表示的安全主体具有更改元数据对象的属性或它与其他元数据对象的关系的权限。  <br/> |
|SetPermissions  <br/> |表示的安全主体具有更改元数据对象的一组权限的权限。  <br/> |
|SelectableInClients  <br/> |表示的安全主体具有选择此权限引用的元数据对象的权限。如果用户没有此权限，则该元数据对象无法选择。  <br/> |
   
|
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [AccessControlList 中的 AccessControlEntry 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/85e24489-0a6b-dfda-fb03-474fe7b0d947%28Office.15%29.aspx) <br/> |包含此权限的 **AccessControlEntry** 元素。 <br/> |
   

## SourceEntity 元素
<a name="bkmk_SourceEntity"> </a>

指定 **Association** 的源外部内容类型。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<SourceEntity Namespace = "String" Name = "String"> </SourceEntity>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|命名空间  <br/> |必需。  <br/> 作为包含此元素的 **Association** 源的外部内容类型的命名空间。 <br/> 属性类型：String  <br/> |
|名称  <br/> |必需。  <br/> 作为包含此元素的 **Association** 源的外部内容类型的名称。 <br/> 属性类型： **String** <br/> |
   
 **子元素**
  
    
    
无
  
    
    
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> |包含此元素的 **Association**。  <br/> |
   

## TypeDescriptor 元素
<a name="bkmk_TypeDescriptor"> </a>

指定 **TypeDescriptor**。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<TypeDescriptor TypeName = "String" LobName = "String" IdentifierEntityNamespace = "String" IdentifierEntityName = "String" IdentifierName = "String" ForeignIdentifierAssociationName = "String" ForeignIdentifierAssociationEntityName = "String" ForeignIdentifierAssociationEntityNamespace = "String" AssociatedFilter = "String" IsCollection = "Boolean" ReadOnly = "Boolean" CreatorField = "Boolean" UpdaterField = "Boolean" PreUpdaterField = "Boolean" Significant = "Boolean" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </TypeDescriptor>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    


|**特性**|**描述**|
|:-----|:-----|
|**TypeName** <br/> |必需。  <br/> 由 **TypeDescriptor** 表示的数据结构的数据类型的标识符。 <br/> 属性类型： **String** <br/> |
|**LobName** <br/> |可选。  <br/> 由 **TypeDescriptor** 表示的数据结构。此属性的默认值是 **TypeDescriptor** 的名称。例如，名为"CN1A"的业务线 (LOB) 系统数据结构可以由 **Name** 属性等于"Customer Name"的 **TypeDescriptor** 表示（如果此 **TypeDescriptor** 的 **LobName** 属性等于"CN1A"）。 <br/> 属性类型： **String** <br/> |
|**IdentifierEntityNamespace** <br/> |可选。  <br/> 包含 **TypeDescriptor** 引用的标识符的外部内容类型的命名空间。如果 **TypeDescriptor** 没有引用 **Identifier**，则此属性肯定不存在。当此属性存在时， **IdentifierEntityName** 和 **IdentifierName** 属性也必须存在。此属性的默认值是包含方法（其所含参数包含 **TypeDescriptor**）的外部内容类型的命名空间。  <br/> 属性类型： **String** <br/> |
|**IdentifierEntityName** <br/> |可选。  <br/> **Entity**（包含 **TypeDescriptor** 引用的 **Identifier**）的名称。如果 **TypeDescriptor** 没有引用 **Identifier**，则此属性肯定不存在。当此属性存在时， **IdentifierEntityNamespace** 和 **IdentifierName** 属性也必须存在。此属性的默认值是包含 **Method**（其所含 **Parameter** 包含 **TypeDescriptor**）的 **Entity** 的名称。 <br/> 属性类型： **String** <br/> |
|**IdentifierName** <br/> |可选。  <br/> 由 **TypeDescriptor** 引用的 **Identifier** 的名称。如果 **TypeDescriptor** 没有引用 **Identifier**，则此属性肯定不存在。  <br/> 属性类型： **String** <br/> |
|**ForeignIdentifierAssociationName** <br/> |可选。  <br/> 由 **TypeDescriptor** 引用的 **Association** 的名称。如果 **TypeDescriptor** 没有引用 **Association**，则此属性肯定不存在。当此属性存在时， **IdentifierName** 属性也必须存在。当此 **TypeDescriptor** 引用的 **Identifier** 与 **Association** 相关且 **Identifier** 包含在 **Association** 的源 **Entity** 中时，必须指定 **ForeignIdentifierAssociationName** 属性。 <br/> 属性类型： **String** <br/> |
|**ForeignIdentifierAssociationEntityName** <br/> |可选。  <br/> **Entity**（包含 **TypeDescriptor** 引用的 **Association**）的名称。如果 **TypeDescriptor** 没有引用 **Association**，则此属性肯定不存在。当此属性存在时， **ForeignIdentifierAssociationEntityNamespace** 和 **ForeignIdentifierAssociationName** 属性也必须存在。此属性的默认值是包含 **Method**（其所含 **Parameter** 包含 **TypeDescriptor**）的 **Entity** 的名称。 <br/> 属性类型： **String** <br/> |
|**ForeignIdentifierAssociationEntityNamespace** <br/> |可选。  <br/> **Entity**（包含 **TypeDescriptor** 引用的 **Association**）的命名空间。如果 **TypeDescriptor** 没有引用 **Association**，则此属性肯定不存在。当此属性存在时， **ForeignIdentifierAssociationEntityName** 和 **ForeignIdentifierAssociationName** 属性也必须存在。此属性的默认值是包含 **Method**（其所含 **Parameter** 包含 **TypeDescriptor**）的 **Entity** 的命名空间。 <br/> 属性类型： **String** <br/> |
|**AssociatedFilter** <br/> |可选。  <br/> 与 **TypeDescriptor** 关联的 **FilterDescriptor** 的名称。如果 **TypeDescriptor** 没有与 **FilterDescriptor** 关联，则此属性肯定不存在。 <br/> 属性类型： **String** <br/> |
|**IsCollection** <br/> |可选。  <br/> 指定 **TypeDescriptor** 是表示单个数据结构还是数据结构集合。 <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**ReadOnly** <br/> |可选。  <br/> 指定是否可以修改由 **TypeDescriptor** 表示的数据结构所存储的数据。如果包含 **TypeDescriptor** 的 **Parameter** 的 **Direction** 属性值为"In"，则无法指定此属性。 <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**CreatorField** <br/> |可选。  <br/> 指定 **TypeDescriptor** 是否表示类型为 **Creator** 的 **MethodInstances** 的字段，该方法实例包含在 **Method**（其所含 **Parameter** 包含 **TypeDescriptor**）中。  <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**UpdaterField** <br/> |可选。  <br/> 指定 **TypeDescriptor** 是否表示类型为 **Updater** 的 **MethodInstances** 的字段，该方法实例包含在 **Method**（其所含 **Parameter** 包含 **TypeDescriptor**）中。在指定此属性时，不能指定 **PreUpdaterField** 属性。 <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**PreUpdaterField** <br/> |可选。  <br/> 指定由 **TypeDescriptor** 表示的数据结构是否存储从外部系统接收的类型为 **Updater** 的 **MethodInstances** 的字段的最新数据值。在指定此属性时，不能指定 **UpdaterField** 属性。 <br/> 默认值： **false** <br/> 属性类型： **Boolean** <br/> |
|**Significant** <br/> |可选。  <br/> 指定在计算哈希代码或比较数据结构中存储的值时，是否包含由此 **TypeDescriptor** 表示的数据结构所存储的值。例如，在确定某个记录是否已修改时，可以考虑表示客户的姓氏的 **TypeDescriptor**，因此它很重要。而在确定某个记录是否已修改时，表示最近一次修改客户记录的日期的 **TypeDescriptor** 通常不在考虑范围内，因此它不重要。 <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
|**Name** <br/> |必需。  <br/> **TypeDescriptor** 的名称。 <br/> 属性类型： **String** <br/> > **注释**> **TypeDescriptor** 的名称不得包含左斜线 ("/")、句号 (".") 或左方括号 ("[") 的特殊字符。          |
|**DefaultDisplayName** <br/> |可选。  <br/> **TypeDescriptor** 的显示名称。 <br/> 属性类型： **String** <br/> |
|**IsCached** <br/> |可选。  <br/> 指定是否频繁使用 **TypeDescriptor**。  <br/> 默认值： **true** <br/> 属性类型： **Boolean** <br/> |
   
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [MetadataObject 中的 LocalizedDisplayNames 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**TypeDescriptor** 的本地化名称。 <br/> |
| [MetadataObject 中的 Properties 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**TypeDescriptor** 的属性。 <br/> 当 **TypeDescriptor** 的类型是 **System.String** 时， **Properties** 元素可以包含类型为 **System.Int32** 的 **Property**，其 **Name** 属性设置为 **Size**。 **Property** 的值指定由此 **TypeDescriptor** 描述的数据结构的值的最大预期字符串长度。 <br/> |
| [TypeDescriptor 中的 Interpretation 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/730f9590-ab40-85b8-eb97-8fd9d8e33c8a%28Office.15%29.aspx) <br/> |针对 **TypeDescriptor** 表示的数据结构所存储的数据的规则 <br/> |
| [TypeDescriptor 中的 DefaultValues 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/635295d1-0f85-6308-976b-d0cb483dece6%28Office.15%29.aspx) <br/> |**TypeDescriptor** 的默认值。 <br/> |
| [TypeDescriptor 中的 TypeDescriptors 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/322b2d3f-c92d-3c24-9f22-07b56396275b%28Office.15%29.aspx) <br/> |**TypeDescriptor** 的子 **TypeDescriptors**。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 中的 TypeDescriptors 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/322b2d3f-c92d-3c24-9f22-07b56396275b%28Office.15%29.aspx)||
   

## TypeDescriptors 元素
<a name="bkmk_TypeDescriptors"> </a>

指定父 TypeDescriptor 的 **TypeDescriptors** 列表。
  
    
    
 **命名空间：** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **架构：** BDCMetadata
  
    
    



```XML
<TypeDescriptors></TypeDescriptors>
```

如下章节中介绍了属性、子元素和父元素。
  
    
    
 **属性**
  
    
    
无
  
    
    
 **子元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> |一个 **TypeDescriptor**。  <br/> |
   
 **父元素**
  
    
    


|**元素**|**描述**|
|:-----|:-----|
| [TypeDescriptor 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> ||
| [TypeDescriptor](http://msdn.microsoft.com/library/30e38d7f-af18-20ec-45ab-0bece071ce67.aspx) <br/> ||
   

## 其他资源
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 的 BDC 模型架构更改](changes-in-the-bdc-model-schema-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的 Business Connectivity Services 程序员参考](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
