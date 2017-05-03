---
title: SharePoint 2013 中的跨站点发布
ms.prod: SHAREPOINT
ms.assetid: 33f49e69-c1d3-4a6e-8887-5df683cba022
---


# SharePoint 2013 中的跨站点发布

SharePoint 2013 介绍了让您能重复使用跨多个网站集的内容的跨网站发布功能。它使用内置的搜索功能启用发布方案和架构。首先，您可设计跨 SharePoint 场的网站，以使您的网站在 Intranet 和 Internet之间的边界进行扩展。
  
    
    

考虑某站点含有提供多个发布网站集的创作网站集，并含有不同的域名，公共搜索引擎对这些域名进行了爬网且都针对搜索引擎优化 (SEO) 进行了优化。跨网站发布启用了此方案和其他类似于它的方案，不会要求您使用内容部署。
跨网站发布设计了某些场景的方案，包括：
  
    
    


- 共享项列表或网页库作为发布目录
    
  
- 使用搜索中的目录
    
  
- 将跨网站发布和变体功能相结合以启用公共创作网站集中的创作多语言站点
    
  

## 目录
<a name="SP15_CrossSitePublising_Catalog"> </a>

SharePoint 2013 中引入的目录包括一个列表或一个库，它被均分以搜索发布网站上的工作流。利用目录，可以在网站集中发布（跨网站发布功能依赖于目录）内容。可以使用目录来实际重新使用跨网站和跨 Intranet 站点、Extranet 站点和 Internet 站点间的边界的内容。对于预定义的搜索查询，目录被标记在搜索中。可以通过使用  [SharePoint 2013 中的内容搜索 Web 部件](content-search-web-part-in-sharepoint-2013.md) 将存储在网站集的目录中的内容置于表面。
  
    
    

## 应何时使用跨网站发布？
<a name="SP15_CrossSitePublising_WhenShouldIUseCrossSitePublishing"> </a>

某些情况下，跨网站发布无效或不合适。您是否拥有外部数据源、您如何连接它们、变体、站点类型、搜索数据库实现以及产品目录的使用都是影响您的决定的因素。表 1 提供了有关这些设计注意事项的详细信息。
  
    
    

**表 1. 跨网站发布的设计注意事项**


|**设计注意事项**|**说明**|
|:-----|:-----|
|"延隔时间"  <br/> |如果某作者发布一个网页和它出现在网站上间的延迟对于某个依赖它的人而言太长，那么您可能需要考虑使用内容部署来替代。  <br/> |
|"搜索数据库实现"  <br/> |如果您将搜索数据库连接到某外部数据源，且您使用外部（非 SharePoint)连接器，那么您不能使用跨网站发布。如果您使用业务连接服务 (BCS)，那么您可以使用跨网站发布。  <br/> 一起使用跨网站发布和搜索数据库在某些情况下有用，但在某些情况下没有用。您不应该使用跨网站发布以一个不在计划或自定义代码实现中包括搜索数据库的方式将源站点直接发布到 Internet。  <br/> |
|"变体实现"  <br/> |如果您正在实现使得页库、文档库和常规列表以多种语言均可用的基本变体站点，则跨网站发布有用。如果您选择在变体站点上实现托管的导航或结构化导航，跨网站发布也有用。  <br/> 跨网站发布只为某些体系结构工资。例如，如果资源 **SPSite** 没有使用来自另一个变体站点或网站集的数据，那么您可以使用跨网站发布将来自变体 **SPSite** 中的内容发布到含已启用变体的发布网站上。 <br/> |
|"目录实现"  <br/> |您是否将该产品目录实施到您的站点体系结构以及您如何实施它可能会影响跨网站发布是否是最有效或最合适的选择。如果您正在使用该产品目录以支持多语言变体站点配置且正发布到 Internet 站点，那么您可以实施跨网站发布。  <br/> |
|管理导航  <br/> |跨网站发布与托管导航和术语库的多数实现一起使用。在某些实现中，导航元数据转换可能不会如预期一样工作。例如，当某一变体站点依赖于另一个变体站点的元数据来驱动站点导航，而且您使用跨网站发布将内容发布到目标站点上时，导航元数据转换便可能不会如预期一样工作。  <br/> |
   

## 如何设置目录？
<a name="SP15_CrossSitePublising_WhenShouldIUseCrossSitePublishing"> </a>

类别页面和目录项目页面都是页面布局，可将其用于跨网站一致地显示构造的目录内容。SharePoint 2013 使你能够为 SharePoint 2013 及更高版本创建并自定义页面布局。有关详细信息，请参阅 [在 SharePoint 2013 中为基于目录的网站自定义页面布局](https://msdn.microsoft.com/zh-cn/library/office/dn144674.aspx
)。
  
    
    

## 跨网站发布 API
<a name="SP15_CrossSitePublising_CrossSitePublishingAPIs"> </a>

SharePoint 2013 介绍了您可以用来支持您的代码中的跨网站发布实现的类。 这些 API 在 .NET 服务器发布库中可用。 使用它们可以自定义 SharePoint 2013 如何共享作为目录的列表以供内容重用或如何使用搜索中的目录。您可以使用自定义代码中的以下类的成员以支持跨网站发布任务：
  
    
    

- 使用 **PublishingCatalogUtility** 类以检索一系列可用目录、获取有关目录和其状态的信息、获取有关可连接到目录上的列表和库的信息并启动或停止共享目录。
    
    
    


  ```cs
  
  /// Retrieve available catalogs.
  public static List<CatalogConnectionSettings> GetPublishingCatalogs(SPSite site, int startRow, int numberOfRows, string filterText, out int totalNumberOfCatalogs)
  ```


    
    


  ```cs
  
  ///Get catalog information that is saved for a list.
  public static bool GetCatalogConfiguration(SPList list, out CatalogShareSettings catalogSettings, out string selectedTaxonomyField)
  ```


    
    


  ```cs
  
  ///Stop sharing a list or library as a publishing catalog for cross-publishing content reuse.
  public static void UnPublishCatalog(SPList list)
  ```

- 使用 **CatalogCollectionManager** 类以使用搜索中的目录。了解目录具有的到搜索的连接，并获取其信息。从目录的内部集合中添加或删除某个目录，排列某操作以在调用 **Update** 方法时将已配置用于重写 URL 的连接加入队列。
    
    
    


  ```cs
  
  /// Add catalog or site source into the internal CatalogInfo collection, but the source is not persisted into the property bag.
  public void AddCatalogConnection(CatalogConnectionSettings catalogInfo)
  ```


    
    


  ```cs
  
  /// Queues an Add operation to add a connection configured to rewrite URLs. The connection is added to the store when the Update method is called.
  public void AddCatalogConnection(CatalogConnectionSettings catalogInfo, 
  string[] orderedPropertiesForUrlRewrite,
  string webUrl, 
  string catalogTaxonomyManagedProperty,
  bool isManualRule)
  ```


    
    


  ```cs
  
  /// Update existing catalog/site source in the internal CatalogInfo collection. Edits are not committed until the Update method is called.
  public void UpdateCatalogConnection(CatalogConnectionSettings catalogInfo)
  ```


    
    


  ```cs
  
  /// Remove a catalog or site source. Deletion is not committed until the Update method is called.
  public void DeleteCatalogConnection(string catalogPath)
  ```


    
    


  ```cs
  
  /// Determine whether a connection exists to this source from the site.
  public bool Contains(string catalogPath)
  ```


    
    


  ```cs
  
  /// Get the settings for a catalog connected to this site.
  public CatalogConnectionSettings GetCatalogConnectionSettings(string catalogPath)
  ```


## 其他资源
<a name="bk_addresources"> </a>


-  [发布 SharePoint 2013 网站](publish-sharepoint-2013-sites.md)
    
  

