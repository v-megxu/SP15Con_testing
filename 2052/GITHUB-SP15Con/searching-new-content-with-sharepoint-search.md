---
title: 使用 SharePoint Search 搜索新内容
ms.prod: SHAREPOINT
ms.assetid: 2a3a7d23-775a-4d95-9066-ebbd18c92ad4
---


# 使用 SharePoint Search 搜索新内容
了解如何使内容可供用户通过 SharePoint Server 2013 进行搜索。
## 使内容可在 SharePoint Server 2013 中进行搜索

SharePoint 2013 中的搜索功能提供了两种处理查询以返回搜索结果的方法­联合搜索和内容爬网。
  
    
    
 **联合搜索** 在此方法中，将为搜索服务器未进行爬网的内容返回搜索结果。查询将转发到一个外部内容存储库，该存储库的搜索引擎将处理此查询。随后，存储库的搜索引擎会将结果返回到搜索服务器。搜索服务器将格式化和呈现要显示在搜索结果页上的外部存储库中的结果。此方法提供了以下好处：
  
    
    

- 内容索引没有额外的容量要求，因为 SharePoint 2013 中的搜索功能不会对内容进行爬网。
    
  
- 可以利用存储库的现有搜索引擎。例如，可以联合到 Internet 搜索引擎来搜索 Web。
    
  
- 您可以为存储库的特定内容集优化内容存储库的搜索引擎，这样可为内容集提供更好的搜索效果。
    
  
- 可以访问已针对爬网进行保护但搜索查询可访问的存储库。
    
  
 **内容爬网** 以此种方法，根据用户的查询，结果将从 Search Service 应用程序的内容索引返回。内容索引包含 Search Service 应用程序进行爬网的内容，并包括每个内容项的文本内容和元数据。利用此方法，您可以：
  
    
    

- 按相关性对结果进行排序。
    
  
- 控制内容索引的更新频率。
    
  
- 指定对哪些元数据进行爬网。
    
  
- 对爬网内容执行一个备份操作。
    
  

## 本节内容


-  [SharePoint 2013 中的搜索连接器框架](search-connector-framework-in-sharepoint-2013.md)
    
  -  [增强 SharePoint 2013 中的搜索功能的 BDC 模型文件](enhancing-the-bdc-model-file-for-search-in-sharepoint-2013.md)
    
  
  -  [如何：在 SharePoint 2013 中对关联的外部内容类型进行爬网](how-to-crawl-associated-external-content-types-in-sharepoint-2013.md)
    
  
  -  [如何：在 SharePoint 2013 中对二进制大型对象 (BLOB) 进行爬网](how-to-crawl-binary-large-objects-blobs-in-sharepoint-2013.md)
    
  
  -  [如何：在 SharePoint 2013 中对关联的外部内容类型进行爬网](how-to-crawl-associated-external-content-types-in-sharepoint-2013.md)
    
  
  -  [如何：在 SharePoint 2013 中配置项目级安全性](how-to-configure-item-level-security-in-sharepoint-2013.md)
    
  

