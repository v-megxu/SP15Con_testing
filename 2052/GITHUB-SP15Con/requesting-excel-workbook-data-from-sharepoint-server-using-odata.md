---
title: 使用 OData 从 SharePoint Server 请求 Excel 工作簿数据
ms.prod: SHAREPOINT
ms.assetid: 2f846e96-6c9e-4ed2-9602-4081ad0ab135
---



# 使用 OData 从 SharePoint Server 请求 Excel 工作簿数据

> **注释**
> Excel Services REST API 可本地应用于 SharePoint 2013 和 SharePoint 2016。对于 Office 365 教育版、商业版和企业版帐户，请使用作为  [Microsoft Graph](http://graph.microsoft.io/zh-cn/docs/api-reference/v1.0/resources/excel
) 终结点一部分的 Excel REST API。
  
    
    

OData 使用 URL 请求资源中的信息。你使用查询选项以特定方式生成 URL 以返回正在请求的信息。以下 URL 显示了典型 OData 请求的外观。
http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$top=20
  
    
    

此示例 OData 请求已进行结构化，它将获取名为 Table1 的表中的前 20 行，该表位于存储在 contoso1 服务器上的 Documents 文件夹中的工作簿 ProductSales.xlsx 中。此 URL 使用系统查询选项 **$top** 指定要返回的行数。仔细查看此 URL，您会发现它由三个部分构成：服务根 URI；资源路径；以及查询选项。
## 服务根 URI

此 URL 的起始部分称作服务根，它对于您向 SharePoint 2013 服务器发起的每个 OData 请求保持一致（服务器的名称除外）。它包括存储工作簿的 SharePoint 服务器的名称以及路径 _vti_bin/ExcelRest.aspx，如下面的示例所示。
  
    
    
http://contoso1/_vti_bin/ExcelRest.aspx
  
    
    

## 资源路径

此 URL 的第二个部分包含 Excel 工作簿的路径，并指定这是一个 OData 请求。
  
    
    
/Documents/ProductSales.xlsx/OData
  
    
    

## 系统查询选项

此 URL 的第三部分提供了针对请求的系统查询选项。查询选项始终以美元符号 ($) 开头并将作为查询参数追加到 URI 的末尾。在此示例中，请求针对的是名为 Table1 的表中的前 20 行。
  
    
    
/Table1?$top=20
  
    
    
系统查询选项提供了获取资源中的特定数据的方式。Excel Services OData 实现支持下面一节中列出的大量查询选项。
  
    
    

## 系统查询选项
<a name="xlsSystemQueryOptions"> </a>

Excel Services OData 实现支持大量标准 OData 系统查询选项。这些查询选项是 OData 请求的核心，因为您将使用这些选项指定要从资源中获取的数据。下表列出了 Excel Services OData 实现当前支持的系统查询选项。
  
    
    

**表 1. Excel Services OData 系统查询选项**


|****系统查询选项****|****说明****|
|:-----|:-----|
|/<tableName>  <br/> |返回由 <tableName> 指定的表的所有行，其中 <tableName> 是 Excel 工作簿中包含要检索的行的表的名称。  <br/> > **重要信息**> 此形式的 OData 请求一次返回的行数不会超过 500。每 500 个行构成一页。若要获取包含 500 个行以上的表中的其他页中的行，请使用 **$skiptoken** 查询选项（见下方内容）。          以下示例最多返回 ProductSales.xlsx 工作簿中的 Table1 中的第 500 行及其之前的所有行。  <br/> |
|**$metadata** <br/> |返回指定工作簿中的所有可用表以及每个表中所有行的类型信息。  <br/> 以下示例返回 ProductSales.xlsx 工作簿中的表以及这些表的类型信息。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/$metadata  <br/> |
|**$orderby** <br/> |返回指定表中的行，这些行按 **$orderby** 指定的值进行排序。 <br/> 以下示例返回 ProductSales.xlsx 工作簿中的 Table1 中的所有行，这些行按 Name 列进行排序。  <br/> > **注释**> **$orderby** 的默认值为升序。          http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$orderby=Name  <br/> |
|**$top** <br/> |返回表中的 N 个行，其中 N 是由 **$top** 的值指定的数字。 <br/> 以下示例返回 ProductSales.xlsx 工作簿中的 Table1 中的前 5 个行，这些行按 Name 列进行排序。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$orderby=Name&amp;$top=5  <br/> |
|**$skip** <br/> |跳过 N 个行（其中 N 是由 **$skip** 的值指定的数字），然后返回表的剩余行。 <br/> 以下示例返回 ProductSales.xlsx 工作簿中的 Table1 中的第 5 行后面的所有剩余行。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skip=5  <br/> |
|**$skiptoken** <br/> |寻找第 N 行（其中 N 是由 **$skiptoken** 的值指示的行顺序位置），然后返回从第 N + 1 行开始的所有剩余行。由于集合是从 0 开始的，因此第 2 行由 $skiptoken=1 指示。 <br/> 以下示例返回 ProductSales.xlsx 工作簿中的 Table1 中的第 2 行后面的所有剩余行。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skiptoken=1  <br/> 还可以使用 **$skiptoken** 查询选项获取表中第一页后的包含 500 个行以上的页面中的行。以下示例说明如何从包含 500 个行以上的表中获取第 500 行及其后面的行。 <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skiptoken=499  <br/> |
|**$filter** <br/> |返回满足由 **$filter** 的值指定的条件的行的子集。有关可与 **$filter** 一起使用的运算符和函数集的详细信息，请参阅 OData [文档](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/)。  <br/> 以下示例仅返回其 Price 列的值大于 100 的行。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$filter=Price gt 100  <br/> |
|**$format** <br/> |Atom XML 格式是唯一受支持的值，且是 **$format** 查询选项的默认值。 <br/> |
|**$select** <br/> |返回 **$select** 指定的实体。 <br/> 以下示例选择 ProductSales.xlsx 工作簿中的 Table1 中的 Name 列。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$select=Name  <br/> |
|**$inlinecount** <br/> | 返回指定表中的行数。 <br/>  $ **inlinecount** 只能使用以下 2 个值之一。 <br/> **allpages** - 返回表中所有行的计数。 <br/> **none** - 不包含表中的行的计数。 <br/>  以下示例返回 ProductSales.xlsx 工作簿中的 Table1 中的总行数的计数。 <br/>  http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$inlinecount=allpages <br/> |
   

## 其他资源
<a name="xlsAdditionalResources"> </a>


-  [在 SharePoint 2013 中将 OData 与 Excel Services REST 一起使用](using-odata-with-excel-services-rest-in-sharepoint-2013.md)
    
  
-  [Excel Services 中面向开发人员的新增功能](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [OData 规范文档](http://www.odata.org)
    
  
