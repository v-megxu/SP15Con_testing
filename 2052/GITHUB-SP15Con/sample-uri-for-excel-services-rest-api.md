---
title: Excel Services REST API 的示例 URI
ms.prod: SHAREPOINT
ms.assetid: 4ebe1da2-9861-416f-bef1-4a62599efe2e
---


# Excel Services REST API 的示例 URI

本主题列出了 Excel Services 中代表性状态传输 (REST) 服务命令的示例 URI。
  
    
    


> **注释**
> Excel Services REST API 可本地应用于 SharePoint 2013 和 SharePoint 2016。对于 Office 365 教育版、商业版和企业版帐户，请使用作为  [Microsoft Graph](http://graph.microsoft.io/zh-cn/docs/api-reference/v1.0/resources/excel
) 终结点一部分的 Excel REST API。
  
    
    


## Excel Services 中 REST 命令的示例 URI

在以下示例中，每个 URI 引用一个名为  *sampleWorkbook.xlsx*  的工作簿。
  
    
    

- sampleWorkbook.xlsx 文件包含指定范围和图表。
    
  
- sampleWorkbook.xlsx 文件保存到受信任的 SharePoint 文档库中。在此示例中，sampleWorkbook.xlsx 所在位置的路径为：
    
  ```
  
http://<ServerName>/Docs/Documents/sampleWorkbook.xlsx
  ```


### 示例 URI

Excel Services 中 REST 服务的 .aspx 页面为：
  
    
    

```
http://<ServerName>/_vti_bin/ExcelRest.aspx

```

下面是使用 Excel Services 中的 REST 服务访问 sampleWorkbook.xlsx 工作簿的示例 URI。
  
    
    

- 工作簿的顶级模型（仅当前版本中的范围和图表）：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model

  ```

- 获取完整的工作簿：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model?$format=workbook

  ```

- 返回范围（默认为 html）。下面的两个 URI 示例是等效的：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|G5')

  ```


  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|G5')?$format=html
  ```

- 获取指定范围：
    
  ```
  http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('nameOfTheNamedRange')

  ```

- 返回 Atom XML 馈送：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model?$format=atom

  ```

- 设置单元格并返回它：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|G5')?Ranges('Sheet1!C3')=demo

  ```

- 获取图表：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('Chart 1')

  ```

- 设置值并获取图表：
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('Chart%201')?Ranges('Sheet1!A1')=5.5

  ```


