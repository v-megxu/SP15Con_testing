---
title: 增强 SharePoint 2013 中的搜索功能的 BDC 模型文件
ms.prod: SHAREPOINT
ms.assetid: 3c67b1cf-5fca-4805-a1b5-c9ac1ff8aede
---


# 增强 SharePoint 2013 中的搜索功能的 BDC 模型文件
了解适用于 BCS 索引连接器（对 SharePoint 2013 中的搜索功能 进行爬网外部数据）的 BDC 元数据中的属性。
## BDC 模型文件的搜索属性
<a name="SearchBDCModelProperties_SearchProperties"> </a>

搜索 中的连接器框架可让您对外部数据进行爬网，以便通过 BCS 索引连接器用在搜索结果中。可由 BCS 索引连接器使用爬网程序以便与外部数据源通信。在爬网时间，爬网程序调用 BCS 索引连接器以便从外部系统捕获数据，并将其传递回该爬网程序。 
  
    
    
BCS 索引连接器组成如下：
  
    
    


  
    
    
> **BDC 模型文件** 文件（向外部系统和数据结构提供连接信息）。
    
  

  
    
    
> **连接器** 组件（包括连接到外部系统和分析访问 URL 和 BCS 标识符的代码）。
    
  
BDC 元数据模型包括适用于 搜索 的多个属性，这些属性中某些必须支持 BCS 索引连接器。 
  
    
    
下表描述了适用于 搜索 BDC 模型属性。
  
    
    

**表 1. BDC 模型文件的搜索属性**


|**名称**|**元数据对象**|**描述**|
|:-----|:-----|:-----|
|ShowInSearchUI  <br/> |模型  <br/> |指定模型文件中的 **LobSystemInstance** 元素应显示在搜索用户界面中。忽略自定义连接器的此值。 <br/> |
|InputUriProcessor  <br/> |LobSystem  <br/> |首先指定处理输入 URL 的名称，然后将其传递到连接器。应用到 .NET 和自定义 BCS 索引连接器。有关详细信息，请参阅  [创建自定义索引连接器](http://msdn.microsoft.com/library/ec2df34d-178c-4ae1-a2b0-a6af04ee57bd%28Office.15%29.aspx)。  <br/> |
|OutputUriProcessor  <br/> |LobSystem  <br/> |首先指定处理输出 URL 的类的名称，然后将其从连接器 传递到搜索系统。应用到 .NET 和自定义 BCS 索引连接器。有关详细信息，请参阅  [创建自定义索引连接器](http://msdn.microsoft.com/library/ec2df34d-178c-4ae1-a2b0-a6af04ee57bd%28Office.15%29.aspx)。  <br/> |
|SystemUtilityTypeName  <br/> |LobSystem  <br/> |指定实现 **StructuredRepositorySystemUtility** 类的类的名称。应用到自定义 BCS 索引连接器。有关详细信息，请参阅 [创建自定义索引连接器](http://msdn.microsoft.com/library/ec2df34d-178c-4ae1-a2b0-a6af04ee57bd%28Office.15%29.aspx)。  <br/> |
|标题  <br/> |实体  <br/> |指定要在搜索结果中显示的外部内容类型的标题。  <br/> |
|DefaultLocale  <br/> |实体  <br/> |指定区域设置字符串。您可以通过使用 **LCIDField** 属性或 **CultureField** 属性重写此值。. <br/> |
|RootFinder  <br/> |方法  <br/> |指定 **Finder** 方法用于枚举要爬网的项。例如，连接到数据库时，这可能是要对其进行爬网的 **SELECT** 语句或表的列表。 <br/> |
|DirectoryLink  <br/> |方法  <br/> |指定 BCS 应导航关联。需要分层爬网而言。  <br/> |
|DeletedCountField  <br/> |方法  <br/> |指定已删除的计数值。除非此属性包含大于零的整数，否则将其忽略。  <br/> |
|WindowsSecurityDescriptorField  <br/> |方法  <br/> |指定该项的 Windows Security 描述器。如果未指定，调用 **GetSecurityDescriptor** 方法。如果未定义 **GetSecurityDescriptor**，则将所有外部项分配给"每个人"访问控制列表 (ACL)。  <br/> |
|AuthorField  <br/> |方法  <br/> |指定要在搜索结果中显示的作者姓名。  <br/> |
|DisplayUriField  <br/> |方法  <br/> |指定要在搜索结果中显示的 URL。如果已指定此 URL，则该属性将重写 BCS 提供的配置文件 URL。如果未指定此 URL，则在搜索结果中显示的该 URL 开头为 **bdc3://** （并且不被浏览器识别）。 <br/> |
|LastModifiedTimeStampField  <br/> |方法  <br/> |指定要在搜索结果中显示的外部项的时间戳。此值还用于增量爬网。  <br/> |
|DescriptionField  <br/> |方法  <br/> |指定要在搜索结果中显示的说明。  <br/> |
|LCIDField  <br/> |方法  <br/> |指定 **DescriptionField** 的区域设置 ID (LCID)。如果未指定此 ID，则使用默认的分词系统。 <br/> |
|CultureField  <br/> |方法  <br/> |指定 **DescriptionField** 的区域性。 <br/> |
|扩展名  <br/> |方法  <br/> |指定可爬网流的文件扩展名。如果未指定，则默认扩展名为 **.txt** 。 <br/> |
|MimeType  <br/> |方法  <br/> |指定可爬网流的 MIME 类型。如果未指定，则默认扩展名为 **.txt** 。如果同时指定了 **Extension** 字段和 **MimeType** 字段，则使用 **MimeType** 字段中指定的值。 <br/> |
|UseClientCachingForSearch  <br/> |方法  <br/> |指定在枚举的过程中，爬网程序是否执行缓存。如果对内容进行缓存，则爬网程序将不会在其对单个项目执行爬网时返回到内容源。  <br/> |
|EnumerateIdsOnly  <br/> |FilterDescriptor  <br/> |指定是否只返回 **IDEnumerator** 中的 ID。 <br/> |
|CrawlStartTime  <br/> |FilterDescriptor  <br/> |包含上一次爬网的开始时间。  <br/> |
|SynchronizationCookie  <br/> |FilterDescriptor  <br/> |指定外部内容源在爬网后返回一个 Cookie，该 Cookie 会在下次枚举调用期间由索引连接器重新发送。外部内容源使用该 Cookie 来确定自上次爬网后已发生更改的内容。此属性将与 **ChangedIDEnumerator** 和 **DeletedIDEnumerator** 方法实例一起使用。 <br/> |
|属性  <br/> |TypeDescriptor  <br/> | 指定用于搜索属性的 **struct** 数组。其中包括： <br/> **PropertyName** <br/> **PropertyValue** <br/> **PropertyCulture** <br/> |
|Text  <br/> |TypeDescriptor  <br/> | 指定用于搜索附件的 **struct** 数组。包括： <br/> **TextExtension** <br/> **TextContentType** <br/> **TextValue** <br/> |
   

## 更改 BDC 模型文件以在爬网外部数据时提高性能
<a name="SearchBDCModelProperties_Performance"> </a>

在您想为要搜索的外部系统创建 BDC 模型文件时，您可以增强该模型文件以在爬网外部系统时优化系统。此部分描述了为提高性能以修改 BDC 模型文件的方法。
  
    
    

### 检索大规模数据时使用内联属性 I/O

通常，如果为某一项返回的数据是大规模的，则应使用以下专用方法之一来检索数据，而不是使用 **SpecificFinder** 方法返回数据：
  
    
    

- 在传递安全访问控制列表 (ACL) 时使用 **BinarySecurityDescriptorAccessor** 方法，而不使用 **WindowsSecurityDescriptor** 属性。
    
  
- 传递数据流时使用 **StreamAccessor** 方法。
    
  
除非网络延迟很高，否则相比额外访问外部系统带来的成本来说，性能改进通常要更好一些。
  
    
    

### 对外部系统进行爬网时枚举优化

每次调用外部系统时枚举的项数不要超过 100,000 个。长时间运行的枚举可能会导致间歇性中断，并阻止爬网完成。建议您的 BDC 模型将数据构造成可单独枚举的逻辑文件夹，如以下示例所示。 
  
    
    
该示例演示对包含一百万行但 ColumnA 中包含一组固定值的数据库表进行枚举。在此方案中，您可以将 ColumnA 视为外部内容类型，并使用以下 SQL 语句为这组值编写一个枚举器。 
  
    
    



```

SELECT DISTINCT( ISNULL(ColumnA,'unknown')) as ColumnA  FROM table
```

接下来，使用以下 SQL 语句定义特定查找器。 
  
    
    



```
SELECT DISTINCT( ISNULL(ColumnA,'unknown')) as ColumnA  FROM table where ColumnA = @Value
```

最后，必须定义关联导航操作，如下所示。 
  
    
    



```
Select * from table where ColumnA=@value
```

任何方法都应在 2 分钟内开始返回结果，否则爬网程序将取消调用。例如，使用 **LIKE** 子句的复杂 SQL 语句可能需要 2 分钟以上的时间才能完成，这将导致爬网程序取消调用。
  
    
    

### 使用 UseClientCachingForSearch 属性提高爬网速度

 **UseClientCachingForSearch** 属性通过在枚举期间缓存项来提高完全爬网的速度。当实现基于更改日志的增量爬网时，也推荐使用此属性，因为它能提高增量爬网速度。
  
    
    

> **重要信息**
> 如果各项平均大于 30 KB，则不设置此属性，因为这将会导致大量缓存丢失，性能也会下降。 
  
    
    


## BDC 模型文件中的安全性
<a name="SearchBDCModelProperties_Security"> </a>

如果存储库使用 NTLM 身份验证，则建议您指定 PassThrough 身份验证进行爬网。
  
    
    
由于前端 Web 服务器中存在多跃点委派问题，因此配置文件页可能要求您使用 安全存储服务。如果您遇到此问题，则可以通过创建两个类似的 **LobSystemInstance** 实例，优化爬网，同时仍然允许配置文件页。第一个实例应使用 安全存储服务 身份验证中的凭据。该示例不应包含 **ShowInSearchUI** 属性。第二个实例应使用 PassThrough 身份验证，还应包含 **ShowInSearchUI** 属性。配置文件页使用第一个 **LobSystemInstance** 实例，而爬网程序使用第二个实例。
  
    
    

> **注释**
> 这要求您在 **LobSystemInstance** 级别而不是在 **LobSystem** 级别设置 **ShowInSearchUI** 属性。
  
    
    


## 其他资源
<a name="SP15enhanceBDC_addlresources"> </a>


-  [SharePoint 2013 中的搜索连接器框架](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [BDC 模型基础结构](http://msdn.microsoft.com/library/2818ebdd-6cda-4d8f-82b2-7fde9fbf2633%28Office.15%29.aspx)
    
  
-  [创作 BDC 模型](http://msdn.microsoft.com/library/170d1cfd-cf19-4162-b79f-ba6d3b4ad23b%28Office.15%29.aspx)
    
  
-  [为 SharePoint 2013 中的 BCS 设置开发环境](setting-up-a-development-environment-for-bcs-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint Designer 为自定义连接器创建 BDC 模型文件](http://msdn.microsoft.com/library/8f239482-0c82-4b60-817d-b0c4392e7e2e%28Office.15%29.aspx)
    
  

