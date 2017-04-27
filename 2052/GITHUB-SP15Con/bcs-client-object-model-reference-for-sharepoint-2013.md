---
title: SharePoint 2013 的 BCS 客户端对象模型引用
ms.prod: SHAREPOINT
ms.assetid: fe7d12a3-6ea9-47f9-b69e-f66da9e661dc
---



# SharePoint 2013 的 BCS 客户端对象模型引用

  
    
    
![类库和引用](images/mod_icon_badge_reference.png)
  
    
    

  
    
    

  
    
    
了解可用于使用 SharePoint 2013 客户端对象模型创建客户端脚本以访问 Business Connectivity Services (BCS) 揭示的外部数据的对象。
以下对象可用于使用 SharePoint 2013 客户端对象模型创建客户端脚本以访问 Business Connectivity Services (BCS) 揭示的外部数据。向该客户端对象模型公开的 BCS 对象模型组件位于 Microsoft.SharePoint.Client.dll。
  
    
    


## Entity 对象
<a name="bkmk_Entity"> </a>

 **Entity** 对象实质上表示了数据基中的表。此处表示的方法和属性演示了通过使用客户端代码库可以处理的对象。但是，它们可以被已分离的客户端调用，如在使用 JavaScript Web 浏览器中。
  
    
    

**方法**


|**方法**|**方法签名**|**说明**|
|:-----|:-----|:-----|
|**Create** <br/> | `Identity Create(FieldValueDictionary fieldValues, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**FindSpecificDefault** <br/> | `EntityInstance FindSpecificDefault(Identity identity, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**FindspecificByBdcIDDefault** <br/> | `EntityInstance FindSpecific(Identity identity, string specificFinderName, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**FindSpecificByBdcID** <br/> | `EntityInstance FindSpecificByBdcIDDefault(string BdcIdentity, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**GetCreatorView** <br/> | `EntityInstance FindSpecificByBdcID(string BdcIdentity, string specificFinderName,LobSystemInstance LobSystemInstanceName)` <br/> ||
|**GetDefaultSpecificFinderView** <br/> | `View GetCreatorView(string methodInstanceName)` <br/> ||
|**GetSpecificFinderView_Client** <br/> | `View GetDefaultSpecificFinderView()` <br/> ||
|**GetUpdaterView_Client** <br/> | `View GetSpecificFinderView_Client( string specificFinderName)` <br/> ||
|**GetIdentifiers** <br/> | `View GetUpdaterView_Client(string updaterName)` <br/> ||
|**GetIdentifiers()** <br/> |||
   

**属性**


|**属性**|**说明**|
|:-----|:-----|
| `long EstimatedInstanceCount { get; }` <br/> |获取此种外部内容类型的预期外部项的数量。  <br/> |
| `string Name { get; }` <br/> |获取元数据对象的名称。  <br/> |
| `string Namespace { get; }` <br/> |获取给定数据类的命名空间。  <br/> |
| `int GetIdentifierCount()` <br/> ||
   

## EntityInstance 方法
<a name="bkmk_EntityInstance"> </a>


**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**Delete** <br/> |无效  <br/> |删除外部项  <br/> |
|**FromXml** <br/> |无效  <br/> |设置此种来自指定 XML 的词典中的值。  <br/> **方法签名**          `FromXml(string xml)` <br/> |
|**GetIdentity** <br/> |标识  <br/> |获取此外部项的标识。  <br/> |
|**Delete** <br/> |无效  <br/> |删除该外部项。  <br/> |
|**ToXml** <br/> |字符串  <br/> |检索 XML 格式的值。  <br/> |
|**Update** <br/> |无效  <br/> |提交对外部项进行的更改。  <br/> |
   

  
    
    

**属性**


|**属性**|**返回类型**|**说明**|
|:-----|:-----|:-----|
| `this[string fieldDotNotation] { get; set; }` <br/> |对象  <br/> |获取或设置点标记所值的字段的值。  <br/> |
| `RelatedSpecificFinderName { get; }` <br/> |字符串  <br/> ||
   

## EntityView 方法
<a name="bkmk_entityview"> </a>

指定"实体"数据的自定义视图
  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**GetDefaultValues_Client()** <br/> |**FieldValueDictionary** <br/> |获取包含此视图的默认值的字段值词典。  <br/> |
|**GetXmlSchema()** <br/> |**string** <br/> |获取该视图的 XML 架构。  <br/> |
|**GetType(string fieldDotNotation)** <br/> |**string** <br/> |获取指定字段的类型。  <br/> |
|**GetType(string fieldDotNotation)** <br/> |**TypeDescriptor** <br/> |获取与给定点标记相对应的 **TypeDescriptor** 对象。 <br/> |
   

**属性**


|**属性**||**说明**|
|:-----|:-----|:-----|
| `Fields { get; }` <br/> |**FieldCollection** <br/> |获取该视图中的字段的集合。  <br/> |
| `Name { get; }` <br/> |**string** <br/> |获取 **View** 对象的名称。 <br/> |
| `RelatedSpecificFinderName { get; }` <br/> |**string** <br/> |检索此视图连接到的特定的查找程序 **MethodInstance** 的名称。 <br/> |
   

## LobSystem 方法
<a name="bkmk_LobSystem"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**GetLobSystemInstances()** <br/> |**void** <br/> |获取 LOB 系统实例的列表。  <br/> |
|**Name** <br/> |**void** <br/> |获取 **LobSystem** 的名称。 <br/> |
   

**属性**


|**属性**|**说明**|
|:-----|:-----|
|无。  <br/> ||
   

## LobSystemInstance 方法
<a name="bkmk_LobSystemInstance"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|无。  <br/> |**void** <br/> ||
   

**属性**


|**属性**|**说明**|
|:-----|:-----|
|无。  <br/> ||
   

## Identifier 方法
<a name="bkmk_Identifier"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**ContainsLocalizedDisplayName** <br/> |**bool** <br/> |确定该元数据对象是否包含本地化的显示名称。  <br/> |
|**GetDefaultDisplayName** <br/> |**string** <br/> |返回默认显示名称。  <br/> |
|**GetLocalizedDisplayName** <br/> |**string** <br/> |返回本地化的显示名称。  <br/> |
   

**属性**


|**属性**|**返回类型**|**说明**|
|:-----|:-----|:-----|
| `IdentifierType {get;}` <br/> |**string** <br/> |返回标识符的类型。  <br/> |
| `Name {get;}` <br/> |**string** <br/> |获取该标识符的名称。  <br/> |
   

## IdentifierCollection 方法
<a name="bkmk_IdentifierCollection"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel.Collections** <br/> |**SP.BusinessData.Collections** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|无。  <br/> |**void** <br/> ||
   

**属性**


|**属性**|**说明**|
|:-----|:-----|
|无。  <br/> ||
   

## Identify 方法
<a name="bkmk_Identity"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**构造函数**


|**构造函数**|**说明**|
|:-----|:-----|
| `public Identity (Object[] identifierValues)` <br/> |使用一组标识符值构造该类的新实例。  <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**Serialize** <br/> |**string** <br/> |获取该标志的字符串表示。  <br/> |
   

**属性**


|**属性**|**返回类型**|**说明**|
|:-----|:-----|:-----|
| `IdentifierCount { get; }` <br/> |**int** <br/> |返回标识符的数量。  <br/> |
| `IsTemporary { get; }` <br/> |**bool** <br/> |检查该标识是否是暂时的。  <br/> |
| `this[int identifierIndex] { get; }` <br/> |**Object** <br/> |检索给定索引处的元素。CSOM 不支持基于 INT 的索引。基于字符串的访问器为了相同的目的实现。  <br/> |
| `TemporaryId { get; }` <br/> |**Guid** <br/> |返回该标识的临时部分。  <br/> |
   

## FieldValueDictionary 方法
<a name="bkmk_FieldValueDictionary"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**FromXml** <br/> |**void** <br/> |设置此种来自指定 XML 的词典中的值。  <br/> |
|**GetCollectionSize** <br/> |INT  <br/> |返回点标记所指的集合的大小。  <br/> |
|**ToXml** <br/> |字符串  <br/> |检索 XML 格式的值。  <br/> |
   

**属性**


|**属性**|**说明**|
|:-----|:-----|
| `Object this[string fieldDotNotation] { get; set; }` <br/> |获取或设置点标记所值的字段的值。  <br/> |
   

## EntityFieldCollection 方法
<a name="bkmk_EntityFieldCollection"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|无。  <br/> |**void** <br/> ||
   

**属性**


|**属性**|**说明**|
|:-----|:-----|
|无。  <br/> ||
   

## EntityField 方法
<a name="bkmk_Entityfield"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**方法**


|**方法**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|无。  <br/> |无效  <br/> ||
   

**属性**


|**属性**|**返回类型**|**只读**|**说明**|
|:-----|:-----|:-----|:-----|
|**ContainsLocalizedDisplayName** <br/> |**Boolean** <br/> |是  <br/> |确定该字段是否包含本地化的显示名称。  <br/> |
|**DefaultDisplayName** <br/> |**string** <br/> |是  <br/> |检索该字段的默认显示名称。  <br/> |
|**GetLocalizedDisplayName** <br/> |**string** <br/> ||检索该字段的本地化显示名称。  <br/> |
|**Name** <br/> |**string** <br/> |是  <br/> |检索该字段的名称。  <br/> |
   

## TypeDescriptor 类
<a name="bkmk_TypeDescriptor"> </a>


  
    
    

**命名空间**


|**托管**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**方法**


|**方法**|**返回类型**|**只读**|**说明**|
|:-----|:-----|:-----|:-----|
|**ContainsLocalizedDisplayName()** <br/> |**Boolean** <br/> |是  <br/> |确定该类型描述符是否包含本地化的显示名称。  <br/> |
|**GetLocalizedDisplayName()** <br/> |**string** <br/> |是  <br/> |返回本地化的显示名称。  <br/> |
|**GetDefaultDisplayName()** <br/> |**string** <br/> ||返回默认显示名称。  <br/> |
   

**属性**


|**属性**|**返回类型**|**说明**|
|:-----|:-----|:-----|
|**Name** <br/> |字符串  <br/> |检索该字段的名称。  <br/> |
|**TypeName** <br/> |字符串  <br/> |检索此类型描述符表示的数据类型的名称。  <br/> |
|**IsReadOnly** <br/> |Boolean  <br/> |确定此类型描述符是否表示只读数据结构。  <br/> |
|**ContainsReadOnly** <br/> |Boolean  <br/> |确定此类型描述符或其某个子级是否表示只读数据结构。  <br/> |
|**IsCollection** <br/> |Boolean  <br/> |确定所描述的类型是否表示集合数据结构。  <br/> |
   

## 接口
<a name="bkmk_Interfaces"> </a>

命名空间为 **Microsoft.BusinessData.MetadataModel**。
  
    
    


|**接口**|**说明**|
|:-----|:-----|
|**IMetadataCatalog** <br/> |该入口指向了 BDC 对象模型。使用该服务器上的 **DatabaseBasedMetadataCatalog**。  <br/> |
|**ILobSystem** <br/> |获取有关外部系统的详细情况。  <br/> |
|**IEntity** <br/> |BDC 元数据库中的外部内容类型。  <br/> |
|**IMethod** <br/> |可以在外部内容类型上执行的操作。  <br/> |
|**IEntityInstance** <br/> |实体实例（也称作外部项）是从 BDC 中的外部系统返回的单个项。  <br/> **IEntityInstance** 接口提取了基本数据源并阐明了必须学习特定于应用程序的编码范例的客户端；这使得它们能通过单一、简单的方式访问所有业务数据。通过使用 **IEntityInstance** 接口，您可以使用数据基中的一行数据，就和使用 Web 服务返回的复杂的 .NET Framework 结构的方法一样。 <br/> BDC 中实体实例上附加了特殊的语义。例如，它可以知道该行的哪个字段或哪些字段表示该实体实例的标识符，它还能使您在该实体实例上调用 **GetAssociated**、 **GetIdentifierValues** 和 **Execute** 等方法。 <br/> |
|**IEntityInstanceEnumerator** <br/> |枚举器可用于读取外部项集合中的数据，但是不能用于修改基础集合。 **IEntityInstanceEnumerator** 支持流式处理，因此，当后端应用程序返回大量数据时，它非常有用。 <br/> |
   

## Client Object model FAQ
<a name="bkmk_ClientObjectModelFAQ"> </a>


- **Does the <Method> tag need to be included in a CAML query when querying an external list**
    
    No. 
    
  
- **Do all fields in the external list need to be specified in the CAML query?**
    
    Using the ViewXML tag in the BDC model, the developer can specify only those fields that are required and the CSOM APIs for Lists will return only those fields.
    
  

## 其他资源
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 的 Business Connectivity Services 程序员参考](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的 .NET 客户端 API 引用](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx)
    
  
-  [在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
-  [如何：使用客户端代码库访问 SharePoint 2013 中的外部数据](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
