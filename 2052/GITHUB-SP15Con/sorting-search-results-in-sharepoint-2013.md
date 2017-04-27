---
title: 在 SharePoint 2013 中对搜索结果进行排序
ms.prod: SHAREPOINT
ms.assetid: 66af835e-2c8f-405e-8bed-cb1e5436e190
---



# 在 SharePoint 2013 中对搜索结果进行排序

  
    
    
![概念概述主题](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
使用 SharePoint Server 2013 中的查询对象模型，按排名、托管属性值、公式表达式或随机顺序，以编程方式对搜索结果进行排序。 
您可以通过四种方式对 SharePoint Server 2013 的搜索结果进行排序：
  
    
    


-  [按排名对搜索结果进行排序](#SP15_Sort_search_resuilts_by_rank)：使您能够按相关性排名对搜索结果进行排序。
    
  
-  [按托管属性值对搜索结果进行排序](#SP15_Sort_search_results_by_managed_property_value)：使您能够基于一个或多个托管属性的值对搜索结果进行排序。
    
  
-  [按公式表达式对搜索结果进行排序](#SP15_Sort_search_results_by_formula)：使您能够按查询请求中指定的公式对搜索结果进行排序。
    
  
-  [按随机顺序对搜索结果进行排序](#SP15_Sort_search_results_in_random_order)：使您能够按随机顺序对查询结果进行排序，或者将一个随机组件添加到排序顺序。
    
  

本文重点介绍以编程方式对搜索结果进行排序。要了解如何使用 SharePoint Server 2013 查询规则对搜索结果进行排序，请参阅下列文章：
  
    
    


-  [在"管理查询规则"中更改排名搜索结果](https://technet.microsoft.com/zh-cn/library/jj871676.aspx#BKMK_ChangeRankedSearchResults)
    
  
-  [在"为 Web 内容管理创建查询规则"中更改排名搜索结果](https://technet.microsoft.com/zh-cn/library/jj871014.aspx#BKMK_ChangeRankedSearchResults)
    
  

## 如何在查询请求中指定排序
<a name="SP15_Specify_sorting_in_query_request"> </a>

当您使用查询对象模型时，您可以选择排序条件，方法是通过  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) 类的 [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) 属性提供排序规范。 [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) 属性的类型为 [SortCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortCollection.aspx) ，它代表 [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) 对象集合。
  
    
    
 [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) 对象定义了对搜索结果进行排序的方式；它包含您希望对搜索结果进行排序的值 ( [Property](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Property.aspx) ) 以及对结果排序的方向 ( [Direction](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Direction.aspx) )。方向的类型为 [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) ，可为升序或降序。
  
    
    
如果您在  [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) 中具有多个值，将按照值出现的先后顺序进行排序。这意味着每个 **Sort** 对象表示一个排序顺序级别。任何后续级别不会更改区别于之前结果的结果排序，但可能会影响具有之前级别的相同排序值的值排序。
  
    
    
除了查询对象模型外，SharePoint Server 2013 还提供搜索 REST 服务，您可以使用该服务查询客户端或移动应用程序中的搜索索引。搜索 REST 服务支持 HTTP POST 和 HTTP GET 请求。有关如何为这些请求构建 URI 的详细信息，请参阅 [使用搜索 REST 服务进行查询](sharepoint-search-rest-api-overview.md#bk_queryrest)。
  
    
    

## 按排名对搜索结果进行排序
<a name="SP15_Sort_search_resuilts_by_rank"> </a>

默认情况下，搜索结果按相关性排名进行排序。这意味着，SharePoint Server 2013 将相关性最高的结果放在搜索结果集顶部。如果按排名排序，结果将始终按降序排序，但是，您可以使用  [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) ，将排序顺序更改为升序。
  
    
    
您还可以通过以下两种方式之一影响查询字符串中的排名计算：
  
    
    

- 通过使用  [关键字查询语言 (KQL) 语法参考](keyword-query-language-kql-syntax-reference.md) 和 [FAST 查询语言 (FQL) 语法参考](fast-query-language-fql-syntax-reference.md) 中的 **XRANK** 运算符。如果满足特定的查询条件，您可以使用 **XRANK** 应用有条件的排名提升。
    
  
- 通过为动态排名选择相关性权重。使用 FQL 时，您可以为每个 **STRING** 运算符指定单个相关性权重。
    
  

## 按托管属性值对搜索结果进行排序
<a name="SP15_Sort_search_results_by_managed_property_value"> </a>

您可以根据一个或多个托管属性的值指定搜索结果排序。这意味着 SharePoint Server 2013 将根据匹配查询的所有结果进行排序。
  
    
    
您可以根据文本和数字属性进行排序。对于文本属性，排序将基于标准文本字符串排序。相反，对于数字属性（包括  [DateTime](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.DateTime.aspx) 类型的托管属性），排序基于数字值。
  
    
    

### 示例

以下示例说明如何使用 **Size** 托管属性对搜索结果进行排序。
  
    
    

```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("Size", SortDirection.Descending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"] + " Size:" + result["Size"]);
    }
}
```

或者，您可以使用搜索 REST API，通过在以下调用中使用 **Size** 属性来对搜索结果进行排序。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='size:descending'
```


## 按公式表达式对搜索结果进行排序
<a name="SP15_Sort_search_results_by_formula"> </a>

您可以基于使用数学公式创建排序值的排序规范指定搜索结果排序。
  
    
    
按公式排序功能是搜索结果的单级和多级排序功能的扩展。此功能使您可以将公式而不是托管属性指定为排序条件。 
  
    
    
通过使用按公式排序功能，您可以对查询结果中每个项目的一个或多个托管属性的执行执行数学运算。
  
    
    
下面是可以通过使用公式指定搜索结果排序来实施的示例：
  
    
    

- 使用 K-近邻法算法对文档进行分类。
    
  
- 使用欧几里得距离或曼哈顿距离计算地理距离。
    
  
- 使用首选值，根据指定托管属性值距离首选值的距离对文档进行排序。
    
  
按公式排序功能不包括对统计动态排名参数的控制，例如术语频率和邻近度。
  
    
    
公式从左到右求值，并且使用标准数学运算符优先级。即，函数和括号组首先求值，乘除运算稍后进行，加减运算最后进行。
  
    
    

> **重要信息**
> 公式的最终结果的值范围必须为 32 位有符号整数，否则排序可能不正确。 
  
    
    


### 在查询中指定排序公式

必须在查询请求的排序规范中指定排序公式，而不是托管属性。
  
    
    
排序规范的格式如下： `[formula:<sort-formula>]`
  
    
    
在该格式中， _<sort-formula>_ 是排序公式表达式。
  
    
    

> **注释**
> 方括号是排序规范语法的一部分。 
  
    
    

默认的排序方向为降序。您也可以使用按升序值排序的公式，例如，如果公式指定一个地理距离。
  
    
    
以下代码示例说明如何使用查询对象模型，指定按使用升序排序顺序的公式进行排序。
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(2000-size)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

或者，您可以使用搜索 REST API，通过在以下调用中使用 **Size** 属性来对搜索结果进行排序。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(2000-size)]:ascending'

```


### 在排序公式中使用托管属性

您可以对类型为  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) 、 [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) 和 [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) 的托管属性的值应用排序公式。您必须对搜索架构中的指定托管属性进行排序。
  
    
    
对于类型为  [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) 的更多托管属性，在用于公式求值之前，该值应乘以 10^（十进制位）。
  
    
    
对于类型为  [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) 的托管属性，自公元前 29000 年 1 月 1 日起，其值在用于公式求值之前已转换为 100 纳秒的数字。一年有 366 天。
  
    
    

### 排序公式表达式

表 1 列出了您可以用于排序公式表达式的函数。表达式不能包含空格。
  
    
    

**表 1. 排序公式表达式的函数**


|**函数**|**说明**|
|:-----|:-----|
|**+** <br/> |指定加法。  <br/> |
|**-** <br/> |指定减法。  <br/> |
|* <br/> |指定乘法。  <br/> |
|**/** <br/> |指定除法。  <br/> > **注释**> 默认情况下，除以零将导致异常，查询将返回错误。通过使用 **errtolast** 运算符，可以避免查询错误，而将失败的项目放在结果集末尾。          |
|**rank** <br/> |表示某个项目的动态排名的特殊关键字。  <br/> 示例： `abs(rank-100)` 将使用与排名值 100 的距离作为排序条件。 <br/> |
|**[0-9.]+** <br/> |指定可以指定为整数或双精度值的数字。  <br/> 示例：503、3.14、5.4352262  <br/> |
|**[a-z0-9]+]** <br/> |指定任何未被识别为函数名称的字符顺序将作为托管属性名称。您必须为搜索架构中的指定托管属性启用排序。  <br/> 示例：您必须在启用排序的前提下定义名为 **height** 的托管属性。这将使您可以使用"height"作为公式中的一个表达式。公式将使用 **height** 托管属性的值。 <br/> |
|**( and )** <br/> |用于分组计算，以确保优先级正确。  <br/> 示例：4*(3+2)  <br/> |
|**sqrt(n)** <br/> | _n_ 的平方根。 <br/> |
|**exp(n)** <br/> |相当于  *pow(2.71828182846,n)*  的指数函数。 <br/> |
|**log(n)** <br/> | _n_ 的自然对数。 <br/> |
|**abs(n)** <br/> | _n_ 的绝对值。 <br/> |
|**ceil(n)** <br/> | _n_ 的上限。即，如果 _n_ 不是整数，向上舍入到下一个整数。如果 _n_ 是整数，则使用 _n_。  <br/> |
|**floor(n)** <br/> | _n_ 的下限。即，如果 _n_ 不是整数，向下舍入到下一个整数。如果 _n_ 是整数，则使用 _n_。  <br/> |
|**round(n)** <br/> |将  _n_ 舍入到最近的偶数整数，也称为"四舍六入五成双"或"就近舍入"。 <br/> |
|**sin(n)** <br/> | _n_ 弧度的正弦函数。 <br/> |
|**cos(n)** <br/> | _n_ 弧度的余弦函数。 <br/> |
|**tan(n)** <br/> | _n_ 弧度的正切函数。 <br/> |
|**asin(n)** <br/> | _n_ 的反正弦（以弧度为单位）。 <br/> |
|**acos(n)** <br/> | _n_ 的反余弦（以弧度为单位）。 <br/> |
|**atan(n)** <br/> | _n_ 的反正切（以弧度为单位）。 <br/> |
|**pow(x,y)** <br/> | _x_ 的值按 _y_ 幂增加。 <br/> > **注释**>  _y_ 的值必须是一个实数。          |
|**atan2(y,x)** <br/> |正向 x 轴和指定的笛卡儿坐标 (x,y) 之间的角度的两参数反正切（以弧度为单位）。  <br/> |
|**bucket(b,n1,n2,…)** <br/> |可用于为表达式的指定值分布区范围提供离散值的运算符。  <br/> 表达式  _b_ 可以是托管属性或任何其他公式表达式。参数 _n1, n2, …_ 代表数字阈值。您可以指定任意数量的存储桶阈值。 <br/> > **注释**> 您必须按以下顺序排列参数  _n1, n2, n3, …_： `n1 < n2 < n3 < ...`，其中， `n1 >= 0`。           输入表达式  _b_ 的指定值向下舍入到最接近的指定数字阈值。如果低于最小的指定阈值，则结果值为零。 <br/> |
|**errtolast(x)** <br/> |可用于控制公式异常处理方式的运算符； _x_ 可以是任何公式表达式。如果此公式表达式的计算导致结果集中某个项目出现数学异常，例如除以零，这些项目将出现在排序列表的末尾，不论指定的排序方向是什么。 <br/> |
   

### 按公式排序的性能特征

使用排序公式意味着公式计算将应用于结果集中的所有匹配项。这意味着对查询性能的影响取决于与查询匹配的项的数目。
  
    
    
具有很多运算符的长公式需要的处理时间比短公式更多。
  
    
    

### 将按公式排序用于地理距离

您可以使用按公式排序进行基于距离的排名。这要求您将代表每个项目的纬度和经度的托管属性包含在内。
  
    
    
例如，您可以使用下列标准公式之一：
  
    
    

- 曼哈顿距离
    
  
- 欧几里得距离（请参见示例 2）
    
  
- 半正矢公式
    
  

> **重要信息**
> 使用类型为 **Decimal** 或 **Float** 的托管属性表示纬度和经度值。
  
    
    


### 示例

下列示例说明了如何使用查询对象模型指定排序公式。
  
    
    
 **示例 1.** 将 **height** 托管属性最接近 20 的项目放在结果列表顶部。
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(20-height)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

或者，您也可以通过以下调用，使用搜索 REST API 将 **height** 托管属性最接近 20 的项目放在结果列表顶部。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(20-height)]:ascending
```

 **示例 2.** 基于托管属性 **latitude**、 **longitude** 和 **height** 中提供的位置信息，按与指定位置（例如，用户的位置）的真正三维欧几里得距离排序。以下公式可得出三维欧几里得距离。假设基本位置为 50/100/200（维度/经度/高度）。
  
    
    
 `sqrt(pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2))`
  
    
    
如果您想应用基于距离的排序（而不是在公式中将距离与其他参数组合在一起），您可以删除  `sqrt()` 组件，因为它不会改变排序顺序，但可以改进查询性能。
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

 **示例 3.** 将大小的值舍入到存储桶，将值向下舍入到下列值之一：0、5、15、50、100；最大的值优先排序。
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:bucket(size,5,15,50,100)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## 按随机顺序对搜索结果进行排序
<a name="SP15_Sort_search_results_in_random_order"> </a>

您可以应用查询结果的随机排序，或者将随机组件添加到结果排序中。
  
    
    
随机排序规范的格式如下： `[random:seed=<seed>:hashfield=<managed property>]`
  
    
    

> **注释**
> 方括号是排序规范语法的一部分。 
  
    
    

表 2 介绍了随机排序规范的参数。
  
    
    

**表 2. 随机排序规范的参数**


|**参数**|**说明**|**必需**|
|:-----|:-----|:-----|
| _Seed_ <br/> |随机值生成的种子。  <br/> 种子是可生成随机数字的函数的输入。此随机数字用于最终排序。仅使用  _seed_ 选项将为您提供一个随机排序的查询结果集。相同查询的排序顺序（使用相同的种子时）在索引更新后可能会更改。 <br/> |是  <br/> |
| _Hashfield_ <br/> |用作随机生成的哈希值的托管属性。您可以使用此参数确保相同查询的排序顺序（使用相同的种子时）在索引更新后不会更改。  <br/> 托管属性必须为  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) 类型，且必须为 [Sortable()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.Sortable.aspx) 。您可以使用随机或唯一值填充此托管属性（例如，使用项目处理阶段填充的序列号）。 <br/> |否  <br/> |
   
通过为相同查询提供相同的种子，项目将按相同的顺序表示。这使您可以在对搜索结果分页时保持相同的随机顺序。如果您想在两次查询之间偶然发生索引更新时保持相同的随机顺序，请使用  _hashfield_ 参数。
  
    
    

### 示例

下列示例说明了如何使用查询对象模型指定随机排序。
  
    
    
 **示例 1.** 按随机顺序对整个结果集进行排序。
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=5432]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

或者，您可以通过以下调用，使用搜索 REST API 按随机顺序对整个结果集进行排序。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[random:seed=5432]:ascending
```

 **示例 2.** 按随机顺序对整个结果集进行排序。对使用相同种子的相同查询保持相同的随机顺序，即使发生索引切换也是如此。名为 **hashvalue** 的自定义托管属性必须在搜搜架构中可用，并且对所有索引项目填充随机或连续的数字值。
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=6543:hashfield=hashvalue]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的搜索](search-in-sharepoint-2013.md)
    
  
-  [关键字查询语言 (KQL) 语法参考](keyword-query-language-kql-syntax-reference.md)
    
  
-  [FAST 查询语言 (FQL) 语法参考](fast-query-language-fql-syntax-reference.md)
    
  
-  [SharePoint Search REST API 概述](sharepoint-search-rest-api-overview.md)
    
  
-  [SharePoint Server 2013 中的爬网和托管属性概述](https://technet.microsoft.com/zh-cn/library/jj219630%28office.15%29.aspx)
    
  

  
    
    
