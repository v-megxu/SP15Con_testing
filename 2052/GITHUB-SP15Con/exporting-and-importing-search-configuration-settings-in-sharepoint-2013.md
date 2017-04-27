---
title: 在 SharePoint 2013 中导出和导入搜索配置设置
ms.prod: SHAREPOINT
ms.assetid: d00679a3-ffa2-4281-ad8b-70fc2c4a14e2
---


# 在 SharePoint 2013 中导出和导入搜索配置设置
获取向您显示如何导出和导入自定义搜索配置设置的代码示例。这些配置包括所有的自定义查询规则、结果资源、结果类型、排序模型和网站搜索设置。SharePoint 通过  [Microsoft.Office.Server.Search.Portability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.aspx) 名称空间公开这一功能。您也可以从一个搜索服务应用程序（SSA）中导出自定义搜索配置设置，并把这些设置导入到站点集和网站中。 
> **注释**
> 您不能将自定义所搜配置设置导进 SSA，或是导出默认搜索配置设置。 
  
    
    


## 导出搜索配置设置
<a name="SP15_exporting_search_configuration"> </a>

以下代码将显示如何使用  [SearchConfigurationPortability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.SearchConfigurationPortability.aspx) 导出您网站的搜索配置设置。这一代码使用示例网站 _http://yoursite/sites/publishing1_，您可以将其替换成自己的网站。 _fileName_ 指存储搜索配置设置的文件； _owner_ 规定了获取搜索配置设置的 [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) 水平。
  
    
    

```

private static void Export(string fileName)
{
    SPSite site = new SPSite("http://yoursite/sites/publishing1");
    SearchConfigurationPortability conf = new SearchConfigurationPortability(site);
    SearchObjectOwner owner = new SearchObjectOwner(SearchObjectLevel.SPWeb, site.OpenWeb());
    var buff = conf.ExportSearchConfiguration(owner);
    File.WriteAllText(fileName, buff);
    site.Close();
}
```


## 导入搜索配置设置
<a name="SP15_importing_search_configuration"> </a>

以下代码将显示如何使用  [SearchConfigurationPortability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.SearchConfigurationPortability.aspx) 从一个文件中导入搜索配置设置，并替换规定站点 _http://yoursite/sites/publishing1_ 上现有的搜索设置。 _fileName_ 指存储搜索配置设置的文件； _owner_ 规定了获取搜索配置设置的 [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) 水平。
  
    
    

```cs

private static void Import(string fileName)
{
    SPSite site = new SPSite("http://yoursite/sites/publishing1");
    SearchConfigurationPortability conf = new SearchConfigurationPortability(site);
    SearchObjectOwner owner = new SearchObjectOwner(SearchObjectLevel.SPWeb, site.OpenWeb());
    conf.ImportSearchConfiguration(owner, File.ReadAllText(fileName));
    site.Close();
}

```


## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的搜索](search-in-sharepoint-2013.md)
    
  
-  [在 SharePoint Server 2013 中导出和导入自定义搜索配置设置](http://technet.microsoft.com/zh-cn/library/jj871675.aspx)
    
  

  
    
    

