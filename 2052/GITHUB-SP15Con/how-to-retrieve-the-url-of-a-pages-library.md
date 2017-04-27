---
title: 如何：检索页面库的 URL
ms.prod: SHAREPOINT
ms.assetid: d9922e4b-4948-4c4a-a8ca-1623168143a3
---


# 如何：检索页面库的 URL
了解如何在与当前上下文不同的网站集中为发布网站检索页面列表的 URL。
## 检索页面列表 URL 的核心概念
<a name="SP15_Core_Concepts_URL_MP"> </a>

为发布网站开发自定义应用程序时，您可能会注意到 [PublishingWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.PublishingWeb.aspx) 目标模型并没有显示在与当前上下文不同的网站集中为发布网站检索页面列表的 URL 的方法。尽管 **PublishingWeb** 类为已激活发布功能的实例封装 [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) 类，但是该类并用于实例化当前上下文之外的 **SPWeb** 对象。
  
    
    
如果您需要检索一个不同网页应用程序的页面列表 URL，您可以查询  [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) 属性。因为 [PublishingWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.PublishingWeb.aspx) 对象是一个发布网站的 [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) 对象，您可以查询 [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) 属性，然后将其内容写入控制台应用程序。如果控制台返回 `Key = vti_pageslistname, Value = {the URL to the Pages library}` 条目，则 *{页面库的 URL}*  就是页面列表 URL。
  
    
    

**表 1： 检索页面库 URL 的核心概念**


|**文章标题**|**说明**|
|:-----|:-----|
|页面库  <br/> |文档库包含发布网站的所有内容页面  <br/> |
| [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) <br/> |代表一个 SharePoint Foundation 网站。  <br/> |
| [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) <br/> |为当前网站获取一个带有元数据的  [SPPropertyBag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPPropertyBag.aspx) 对象。 <br/> |
| [SPPropertyBag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPPropertyBag.aspx) <br/> |存储包含自定义属性设置的任意键和值对。  <br/> |
| [PublishingWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.PublishingWeb.aspx) <br/> |为支持发布功能的 **SPWeb** 实例提供发布行为。 <br/> |
   

## 在与当前上下文不同的网站集中为发布网站检索页面列表的 URL
<a name="SP15_Code_URL_Pages_List"> </a>

此示例控制台应用程序访问  [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) 属性，循环访问网站集，并将键/值对写入控制台。
  
    
    

### 查询页面列表 URL 的 SPWeb.Properties 属性


1. 编写控制台应用程序。
    
  
2. 查看控制台中的输出。
    
  

## 示例： 查询页面列表 URL 的 SPWeb.Properties 属性
<a name="SP15_Example_SPWeb_Properties"> </a>

应用程序查询  [SPPropertyBag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPPropertyBag.aspx) 对象，循环访问字典条目，并将这些条目写入控制台。
  
    
    

```cs

using System;
using System.Collections;
using Microsoft.SharePoint;
using Microsoft.SharePoint.Utilities;

namespace Test
{
    class Program
    {
        static void Main(string[] args)
        {
            using (SPSite site = new SPSite("http://localhost"))
            {
                using (SPWeb web = site.OpenWeb())
                {
                    SPPropertyBag props = web.Properties;
                    foreach (DictionaryEntry de in props)
                    {
                        Console.WriteLine("Key = {0}, Value = {1}", de.Key, de.Value);
                    }
                }
            }
            Console.ReadLine();
        }
    }
}

```

此应用程序打印至控制台的输出会因网站的不同而异，但它外观可能类似于以下内容：
  
    
    



```

Key = vti_associatemembergroup, Value = 5
Key = vti_extenderversion, Value = 14.0.0.4016
Key = vti_associatevisitorgroup, Value = 4
Key = vti_associategroups, Value = 5;4;3
Key = vti_createdassociategroups, Value = 3;4;5
Key = vti_siteusagetotalbandwidth, Value = 547
Key = vti_siteusagetotalvisits, Value = 9
Key = vti_associateownergroup, Value = 3
Key = vti_defaultlanguage, Value = en-us
Key = vti_pageslistname, Value = {the URL to the Pages list}
```


## 其他资源
<a name="bk_addresources"> </a>


-  [为 SharePoint 构建网站](build-sites-for-sharepoint.md)
    
  

