---
title: 在 SharePoint 2013 中将 OData 与 Excel Services REST 一起使用
ms.prod: SHAREPOINT
ms.assetid: 8a20225a-323c-4420-bbb4-eef60aed4b42
---


# 在 SharePoint 2013 中将 OData 与 Excel Services REST 一起使用
SharePoint Server 2010 引入了 REST API 以用于获取和设置存储在 SharePoint 文档库的 Excel 工作簿中的信息。SharePoint Server 2013 添加了一个新的方式以请求使用开放数据协议 (OData) 的 Excel Services 中的数据（您可以使用开放数据协议 (OData) 获取有关 Excel Services 资源的信息）。这种新服务主要依赖现有的 Excel Services REST API。本主题提供有关在 Excel Services 中使用 OData 的高级概述。
> **注释**
> Excel Services REST API 可本地应用于 SharePoint 2013 和 SharePoint 2016。对于 Office 365 教育版、商业版和企业版帐户，请使用作为  [Microsoft Graph](http://graph.microsoft.io/zh-cn/docs/api-reference/v1.0/resources/excel
) 终结点一部分的 Excel REST API。
  
    
    


## 什么是 OData？
<a name="xlsWhatIsOdata"> </a>

OData 是一种用于查询和更新数据的开放式 Web 协议。它使用 RESTful 方法从 Web 上的资源返回数据。也就是，您使用包含查询参数的 URI 来获取有关特定资源的信息。
  
    
    
有关 OData 的详细信息，请参阅 [开放数据协议规范](http://www.odata.org)的网站。
  
    
    

## 如何将 OData 与 Excel Services 结合使用？
<a name="xlsHowUseOdata"> </a>

在 Excel Services 情况下，您使用 OData 获取有关存储在 SharePoint 库的工作簿中表（包括查询表）的信息。OData 服务会以 XML Atom 格式的形式返回您所请求的数据。
  
    
    

### 对 Excel Services 进行 OData 请求的语法
<a name="xlsOdataSyntax"> </a>

SharePoint 以可从中请求信息的单独资源的形式公开每个工作簿。在此版本的 SharePoint Server 中，您只能从工作簿的表中获取数据。
  
    
    
若要从某个 Excel 工作簿中获取数据，您需要构建一个指向该工作簿、指定要从该工作簿获得哪些数据以及如何布置该数据的 URL。例如，若要获取有关存储在名为 Documents 的文件夹下的 SharePoint 库中名为 ProductSales.xlsx 的工作簿中 Table1 的信息，您可以使用如下 URL。
  
    
    
http://<serverName>/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1
  
    
    
有关如何使用 OData 从存储在 SharePoint Server 中的 Excel 工作簿请求信息的详细信息，请参阅 [使用 OData 从 SharePoint Server 请求 Excel 工作簿数据](requesting-excel-workbook-data-from-sharepoint-server-using-odata.md)。
  
    
    

## OData 返回的数据
<a name="xlsOdataReturnData"> </a>

当您对 Excel Services 进行 OData 请求时，它会返回 Atom 格式的 XML。Atom 格式是在 OData 的 Excel Services 实现中唯一受支持的格式。例如，下面显示了一个对名为 WindowsPhoneComparison.xlsx 的工作簿中第一个表（名为 Table1）的第一行的 OData 请求。
  
    
    
http://<serverName>/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/odata/Table1
  
    
    
然后，Excel Services 返回以下代码中所示的 Atom XML。
  
    
    



```XML

<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<entry xml:base="http://{serverName}/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/OData" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" m:etag="W/&amp;quot;datetime'0001-01-01T00%3A00%3A00'&amp;quot;" xmlns="http://www.w3.org/2005/Atom">
  <id>http://{serverName}/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/OData/Table1(0)</id>
  <title type="text"></title>
  <updated>0001-01-01T00:00:00-08:00</updated>
  <author>
    <name />
  </author>
  <link rel="edit" title="Table1Item" href="/Table1(0)" />
  <category term="ExcelServices.Table1Item" scheme="http://schemas.microsoft.com/ado/2007/08/dataservices/scheme" />
  <content type="application/xml">
    <m:properties>
      <d:Phone>Samsung Focus</d:Phone>
      <d:sizeweight m:type="Edm.Double">4</d:sizeweight>
      <d:camera m:type="Edm.Double">2.5</d:camera>
      <d:battery m:type="Edm.Double">3</d:battery>
      <d:memory m:type="Edm.Double">3</d:memory>
      <d:speed m:type="Edm.Double">3</d:speed>
      <d:style m:type="Edm.Double">3</d:style>
      <d:callquality m:type="Edm.Double">3</d:callquality>
      <d:overall m:type="Edm.Double">3</d:overall>
      <d:excelRowID m:type="Edm.Int32">0</d:excelRowID>
    </m:properties>
  </content>
</entry>

```


## 结论
<a name="xlsOdataReturnData"> </a>

OData 提供了一种从存储在 SharePoint 中的 Excel 工作簿获取数据的简单方法。使用基于诸如 HTTP 和 REST 的 Web 标准的简单易行的语法，OData 可以让您快速且轻松地从 Excel 工作簿中获取数据。
  
    
    

## 其他资源
<a name="xlsOdataAddRes"> </a>


-  [Excel Services 中面向开发人员的新增功能](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [使用 OData 从 SharePoint Server 请求 Excel 工作簿数据](requesting-excel-workbook-data-from-sharepoint-server-using-odata.md)
    
  
-  [OData 规范文档](http://www.odata.org)
    
  

