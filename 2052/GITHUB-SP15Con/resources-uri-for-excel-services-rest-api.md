---
title: Excel Services REST API 的资源 URI
ms.prod: OFFICE365
ms.assetid: 79f95305-ec9e-4842-b937-85f66ced98e4
---


# Excel Services REST API 的资源 URI

您可以使用 Excel Services 中的 REST API 直接链接到实体。
  
    
    


> **注释**
> Excel Services REST API 可本地应用于 SharePoint 2013 和 SharePoint 2016。对于 Office 365 教育版、商业版和企业版帐户，请使用作为  [Microsoft Graph](http://graph.microsoft.io/zh-cn/docs/api-reference/v1.0/resources/excel
) 终结点一部分的 Excel REST API。
  
    
    


## 基 REST URL

下面是指向工作簿中特定元素的 REST URL 的示例。
  
    
    

```

http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>/<ResourceLocation>
```

相对 REST URL 与基 REST URL 相反。下面是指向特定工作簿的基 REST URL 的示例。
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>
```

例如，如果下面的文档库中有一个名为"sampleWorkbook.xlsx"的工作簿：
  
    
    



```
http://<ServerName>/Docs/Documents/sampleWorkbook.xlsx
```

该工作簿的基 REST URL 为：
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx
```


## 资源 URI

表 1 显示了 Excel Services REST API 中的所有可访问资源。要访问特定资源，请将资源位置附加到工作簿的基 REST URL。
  
    
    

**表 1. Excel Services REST API 中的可访问资源**


|****资源位置****|****格式****|****示例****|****注释****|
|:-----|:-----|:-----|:-----|
|/model  <br/> |Atom（默认值）  <br/> |/model  <br/> |返回 Atom 馈送，其中包含 Excel Services REST API 支持的资源。支持的资源包括范围、图表、表和数据透视表。  <br/> |
|/model  <br/> |workbook  <br/> |/model?$format=workbook  <br/> |这是工作簿。支持的工作簿格式为 xlsx、xlsb 和 xlsm。  <br/> |
|/model/Ranges  <br/> |Atom（默认值）  <br/> |/model/Ranges?$format=atom  <br/> |Atom 馈送，列出了工作簿中的所有指定范围。  <br/> |
|/model/Ranges('[Name]')  <br/> |HTML（默认值）  <br/> |/model/Ranges('MyRange')?$format=html  <br/> |所请求范围的 HTML 片段。  <br/> |
|/model/Ranges('[Name]')  <br/> |Atom  <br/> |/model/Ranges('MyRange')?$format=atom  <br/> |包含范围内数据的 XML 表示形式的 Atom 条目。  <br/> |
|/model/Charts  <br/> |Atom（默认值）  <br/> |/model/Charts?$format=atom  <br/> |Atom 馈送，列出了工作簿中的所有图表。  <br/> |
|/model/Charts('[Name]')  <br/> |Image（默认值）  <br/> |/model/Charts('MyChart')?$format=image  <br/> |图表的图像。图像为可移植网络图形 (PNG) 格式。  <br/> |
|/model/Tables  <br/> |Atom（默认值）  <br/> |/model/Tables?$format=atom  <br/> |Atom 馈送，列出了工作簿中的所有可用表。  <br/> |
|/model/Tables('[Name]')  <br/> |HTML（默认值）  <br/> |/model/Tables('MyTable')?$format=html  <br/> |所请求表的 HTML 片段。  <br/> |
|/model/Tables('[Name]')  <br/> |Atom  <br/> |/model/Tables('MyTable')?$format=atom  <br/> |包含表内数据的 XML 表示形式的 Atom 条目。  <br/> |
|/model/PivotTables  <br/> |Atom（默认值）  <br/> |/model/PivotTables?$format=atom  <br/> |Atom 馈送，列出了工作簿中的所有可用数据透视表。  <br/> |
|/model/PivotTables('[Name]')  <br/> |HTML（默认值）  <br/> |/model/PivotTables('MyPivotTable)?$format=html  <br/> |所请求数据透视表的 HTML 片段。  <br/> |
|/model/PivotTables('[Name]')  <br/> |Atom  <br/> |/model/PivotTables('MyPivotTable')?$format=atom  <br/> |包含表数据透视内数据的 XML 表示形式的 Atom 条目。  <br/> |
   

> **注释**
> Excel Services 将 URL 中可以包含的区域数限制为 10 个。如果您在 URL 中包括 10 个以上区域，您将收到错误，指示该服务不可用。 
  
    
    


## 另请参阅


#### 概念


  
    
    
 [基本 URI 结构和路径](basic-uri-structure-and-path.md)
