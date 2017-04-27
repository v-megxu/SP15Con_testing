---
title: 自定义 SharePoint 2013 中的搜索结果
ms.prod: SHAREPOINT
ms.assetid: 1b30f6df-643a-4570-ae5c-d3d8df5609b8
---


# 自定义 SharePoint 2013 中的搜索结果
了解在 SharePoint Server 2013 中如何对搜索结果集中的类似项目进行分组或删除其中的重复项，以便您能够以简洁且易读的方式显示这些结果。
在搜索结果中，对搜索结果集中的两个或更多个类似项目按组进行折叠可使用户更加轻松地查看显示内容。删除重复搜索结果是分组过程的一部分，即，将从结果集中删除相同或几乎相同的项目。根据 SharePoint 管理员设定的设置，用户日后可以展开搜索结果集并查看已折叠的各个结果。
  
    
    

下面是一些对搜索结果进行分组的方法示例：
- 重复项检测，从结果集中删除几乎完全相同的文档。
    
  
- 网站折叠，仅在结果集中显示在每个网站中找到的最相关项目。
    
  
- 文档集折叠，对于每个 SharePoint 文档库，仅显示其中一个符合搜索条件的项目。
    
  
通过在查询对象模型中使用下面的  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) 属性，您可以编程方式指定折叠或剪裁重复项的条件：
-  [CollapseSpecification](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.CollapseSpecification.aspx)
    
  
-  [TrimDuplicates](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.TrimDuplicates.aspx)
    
  
-  [TrimDuplicatesOnProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesOnProperty.aspx)
    
  
-  [TrimDuplicatesKeepCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesKeepCount.aspx)
    
  
-  [TrimDuplicatesIncludeId](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesIncludeId.aspx)
    
  

## 使用 CollapseSpecification 属性折叠类似的搜索结果
<a name="bk_collapse_specification"> </a>

 **CollapseSpecification** 属性可获取 _Spec_ 参数，该参数可以包含多个用逗号或空格分隔的字段，对这些字段进行统一计算即可指定一组折叠条件。
  
    
    
 **语法**
  
    
    
 `CollapseSpecification = Spec`
  
    
    
下表列出了  _Spec_ 参数的各个字段。
  
    
    

**表 1. Spec 参数字段**


|**参数中的元素**|**说明**|
|:-----|:-----|
| _Spec_ <br/> | `Subspec(<space>Subspec)*` <br/> |
| _Subspec_ <br/> | `Prop(','Prop)*[':'Dups]` <br/> |
| _Prop_ <br/> |一个有效的托管属性或托管属性的别名。 _Prop_ 不区分大小写。该托管属性必须可查询并且可排序或可细化。 <br/> |
| _Dups_ <br/> |一个指定要保留的项目数的整数。默认值为 1。  <br/> |
| _<space>_ <br/> |使用 **OR** 运算符可组合各个属性。 <br/> |
| _,_ <br/> |使用 **AND** 运算符可组合各个属性。 <br/> |
| _*_ <br/> |表示多个项目。  <br/> |
| _() or []_ <br/> |表示可选项目。  <br/> |
   
如果  _Spec_ 中的域用逗号分隔，则使用 **AND** 运算符组合各个域。当满足所有指定域条件时，将折叠相关项目。
  
    
    
相反，如果  _Spec_ 中的各个域是空格分隔，则使用包含 **AND** 运算符和 **OR** 运算符的表达式组合各个域（或 _Subspecs_）。例如，类似  `Category:3 Product:2` 这样的表达式会在内部转换为表达式 `(Category AND Product) OR (Category)`，其中每个域都带有计数器。因此，前一个域最多返回两项，后一个域最多返回三项。当满足部分指定域条件时，即会折叠相关项目。
  
    
    

### 使用 CollapseSpecification 的示例

下表显示了 Contoso 公司的产品目录。接下来的一组示例使用此目录演示 **CollapseSpecification** 属性如何工作。
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|Laptops  <br/> |WWI  <br/> |19W X0196 Black  <br/> |Computer 1  <br/> |
|Laptops  <br/> |Adventure Works  <br/> |12 M1201 Red  <br/> |Computer 2  <br/> |
|Laptops  <br/> |Adventure Works  <br/> |15.4W M1548 White  <br/> |Computer 3  <br/> |
|Laptops  <br/> |Proseware  <br/> |19 X910 Black  <br/> |Computer 4  <br/> |
|Laptops  <br/> |Proseware  <br/> |Laptop19 X910 Black  <br/> |Computer 5  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |2.33 XD233 Silver  <br/> |Computer 6  <br/> |
|Desktops  <br/> |WWI  <br/> |2.33 X2330 Black  <br/> |Computer 7  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |1.60 ED160 White  <br/> |Computer 8  <br/> |
|Desktops  <br/> |WWI  <br/> |3.0 M0300 Silver  <br/> |Computer 9  <br/> |
   

  
    
    

#### 示例：按 Category 分组

首先，按 **Category** 对各项进行分组，并显示每组中的前两项（因此为 `"Category:2"`）。然后，针对每个 **Category**，显示相应数量的唯一的（因此为"Product:1"） **Products**。
  
    
    
 **语法**
  
    
    
 `CollapseSpecification="Category:2 Product:1"`
  
    
    
应返回下面的结果。
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|Laptops  <br/> |WWI  <br/> |19W X0196 Black  <br/> |Computer 1  <br/> |
|Laptops  <br/> |Adventure  <br/> |12 M1201 Red  <br/> |Computer 2  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |2.33 XD233 Silver  <br/> |Computer 6  <br/> |
|Desktops  <br/> |WWI  <br/> |2.33 X2330 Black  <br/> |Computer 7  <br/> |
   
通过下面的代码可使用 **CollapseSpecification** 属性折叠搜索结果。
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
        {
            QueryText = "Title:Computer",
            CollapseSpecification = "Category:3 Product:1",
        };

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    {
        Console.WriteLine(result["Title"]);
    }
}

```


#### 示例：按 Category 和 Product 进行分组

首先，按 **Category** 和 **Product** 对项目进行分组。然后，显示每种唯一的组合。
  
    
    
 **语法**
  
    
    
 `CollapseSpecification="Category,Product:1"`
  
    
    
应返回下面的结果。
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|Laptops  <br/> |WWI  <br/> |19W X0196 Black  <br/> |Computer 1  <br/> |
|Laptops  <br/> |Adventure Works  <br/> |12 M1201 Red  <br/> |Computer 2  <br/> |
|Laptops  <br/> |Proseware  <br/> |19 X910 Black  <br/> |Computer 4  <br/> |
|Desktops  <br/> |Adventure Works  <br/> |2.33 XD233 Silver  <br/> |Computer 6  <br/> |
|Desktops  <br/> |WWI  <br/> |2.33 X2330 Black  <br/> |Computer 7  <br/> |
   

## 使用 TrimDuplicates 属性剪裁重复的搜索结果
<a name="bk_trim_duplicates"> </a>

使用 **TrimDuplicates** 可指定是否从结果集中剪裁掉重复的搜索结果。 **TrimDuplicates** 默认设置为 **true**。
  
    
    
如果将 **TrimDuplicates** 与 **TrimDuplicatesOnProperty** 或 **CollapseSpecification**（首选）结合使用， **TrimDuplicates** 将设置为 **false**。
  
    
    
 **语法**
  
    
    
 `TrimDuplicates = <$true | $false>`
  
    
    

### 使用 TrimDuplicatesOnProperty 属性剪裁重复的搜索结果
<a name="bk_trim_duplicates_on_property"> </a>

使用 **TrimDuplicatesOnProperty** 可指定是否使用非默认托管属性作为剪裁重复项的基础。默认值为 **DocumentSignature** 托管属性。该托管属性必须为 **Integer** 或 **String** 类型。通过使用表示项目分组的托管属性，您可以使用该功能折叠字段。
  
    
    
 **语法**
  
    
    
 `TrimDuplicatesOnProperty = <managed property>`
  
    
    

> **注释**
> 在 SharePoint Server 2013 中，应尽可能使用 **CollapseSpecification**。 **TrimDuplicatesOnProperty** 仅用于实现向后兼容。
  
    
    


### 使用 TrimDuplicatesKeepCount 属性剪裁重复的搜索结果
<a name="bk_trim_duplicates_keep_count"> </a>

当 **TrimDuplicates** 设置为 **true** 时，可使用 **TrimDuplicatesKeepCount** 指定要保留的文档数目。如果 **TrimDuplicates** 基于可用作组标识符的托管属性（例如网站 ID），则您可以控制每组返回多少个结果。所返回的项目在每个组中具有最高动态排名。
  
    
    
 **语法**
  
    
    
 `TrimDuplicatesKeepCount = <number>`
  
    
    

### 使用 TrimDuplicatesIncludeId 属性检索重复的搜索结果
<a name="bk_trim_duplicates_include_id"> </a>

当 **TrimDuplicates** 设置为 **true**，以及 **TrimDuplicatesOnProperty** 或 **CollapseSpecification** 设置为 **false** 时，可使用 **TrimDuplicatesIncludeId** 检索文档的重复项。
  
    
    
可使用文档 ID ( _docid_) 检索特定文档的重复项。
  
    
    
 **语法**
  
    
    
 `TrimDuplicatesIncludeId = <docid>`
  
    
    

> **注释**
> FAST Search Server 2010 for SharePoint 中的  _fcoid_ 托管属性在 SharePoint Server 2013 中已替换为 _docid_ 托管属性。
  
    
    


## 其他资源
<a name="bk_addresources"> </a>


-  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx)
    
  
-  [SharePoint 2013 中的搜索架构概述](http://technet.microsoft.com/zh-cn/library/jj219669%28office.15%29.aspx)
    
  

  
    
    

