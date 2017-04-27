---
title: 如何：在 SharePoint 2013 中对关联的外部内容类型进行爬网
ms.prod: SHAREPOINT
ms.assetid: 187ec42e-f749-4e22-abef-1df604143063
---


# 如何：在 SharePoint 2013 中对关联的外部内容类型进行爬网
了解如何使用 Business Data Connectivity (BDC) 服务 元数据模型中特定于搜索的属性对关联进行爬网，以及您可以启用的不同用户体验。
## 对关联的外部内容类型进行爬网
<a name="HowToCrawlAssociations_CrawlingAssociatedExternalTypes"> </a>

利用 Microsoft Business Connectivity Services (BCS)，您可以链接两个相关的外部内容类型，通过该链接，您可以获取相关外部内容。例如，您可以基于外键从两个基于 SQL Server 数据库表的外部内容类型获取外部内容。这种链接两个相关外部内容类型的概念称为 *关联*  。有关关联的详细信息，请参阅 [在外部内容类型之间添加关联](http://msdn.microsoft.com/library/791e95ab-9b3c-413b-be12-bd0e59962c93%28Office.15%29.aspx)。 
  
    
    
在 搜索连接器框架的上下文中，关联的源外部内容类型称为父外部内容类型。搜索爬网程序可通过以下两种方式对与父级关联的外部内容类型进行爬网：作为附件或作为子级。这些外部内容类型关联会影响以下方面：
  
    
    

- 用户体验
    
  
- 增量爬网
    
  
- 处理爬网删除
    
  

### 外部内容类型关联中的用户体验影响

子外部内容类型具有自己的搜索结果 URL 和配置文件页（如果已创建配置文件页）。搜索结果 URL 是用户在子外部内容类型数据中搜索某词语时显示的 URL。 
  
    
    
附件的外部内容类型没有自己的搜索结果 URL。因此，如果用户在附件外部项中搜索某词语，则改为显示父外部内容类型的 URL。您可将此 URL 设置为父级配置文件页 URL。父外部内容类型的配置文件页将显示关联导航器公开的附件外部内容类型中的所有字段。
  
    
    

### 外部内容类型关联中的增量爬网影响

如果子外部项的时间戳更改，则针对基于时间戳的增量爬网，对子外部项进行重新爬网和更新。 
  
    
    
对于附件外部内容类型，父外部项的时间戳解释为附件外部项的时间戳。这表示仅在父外部项的时间戳更改时，增量爬网才会选取附件外部项中的任何更改。
  
    
    

### 外部内容类型关联中的处理爬网删除影响

处理爬网删除时，如果将父外部内容类型从索引中删除，则 搜索爬网程序将从索引中删除关联的附件外部内容类型及子外部内容类型。
  
    
    

## 对关联的外部内容类型附件进行爬网
<a name="HowToCrawlAssociations_CrawlingAttachments"> </a>

若要标记一个关联以便将其作为附件进行爬网，则向 **Association** 方法实例添加 **AttachmentAccessor** 属性，如下所示。
  
    
    

```XML

<Association Name="AttachmentsNavigate Association" Type="AssociationNavigator" ...>
    <Properties>
        <Property Name="ForeignFieldMappings" Type="System.String">....... </Property>
        <Property Name="AttachmentAccessor" Type="System.String">x</Property>
    </Properties>
    <SourceEntity Namespace="ParentExternalContentType" Name="Parent" />
    <DestinationEntity Namespace="AttachmentExternalContentType" Name="Attachment External Content Type" />
</Association>
```


> **注释**
> 您可以为 **AttachmentAccessor** 属性指定任意值；搜索不会检查该值。
  
    
    


## 将关联的外部内容类型作为子外部内容类型进行爬网
<a name="HowToCrawlAssociations_CrawlingChildExternalTypes"> </a>

若要标记一个关联以便将其作为子外部内容类型进行爬网，则向 **Association** 方法实例添加 **DirectoryLink** 属性，如下所示。
  
    
    

```XML

<Association Name="ChildrenNavigator Association" Type="AssociationNavigator" ...>
    <Properties>
        <Property Name="DirectoryLink" Type="System.String">x</Property>
    </Properties>
    <SourceEntity Namespace="ParentExternalContentType" Name="Parent" />
    <DestinationEntity Namespace="ChildExternalContentType" Name="Child External Content Type" />
</Association>
```


> **注释**
> 您可以为 **DirectoryLink** 属性指定任意值；搜索不会检查该值。
  
    
    


## 其他资源
<a name="SP15crawlects_addlresources"> </a>


-  [SharePoint 2013 中的搜索连接器框架](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [在外部内容类型之间添加关联](http://msdn.microsoft.com/library/791e95ab-9b3c-413b-be12-bd0e59962c93%28Office.15%29.aspx)
    
  
-  [MethodInstances 中的 Association 元素（BDCMetadata 架构）](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx)
    
  
-  [步骤 4（可选）：定义关联](http://msdn.microsoft.com/library/6bc55f46-459a-4986-8744-8c6c5f45097b%28Office.15%29.aspx)
    
  

