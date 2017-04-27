---
title: Excel Services REST API 中不受支持的功能
ms.prod: OFFICE365
ms.assetid: 4139901f-255b-4556-b8c8-3d986a07c587
---


# Excel Services REST API 中不受支持的功能

第一版的 Excel Services REST API 不支持每个 Excel 功能。 
  
    
    


> **注释**
> Excel Services REST API 可本地应用于 SharePoint 2013 和 SharePoint 2016。对于 Office 365 教育版、商业版和企业版帐户，请使用作为  [Microsoft Graph](http://graph.microsoft.io/zh-cn/docs/api-reference/v1.0/resources/excel
) 终结点一部分的 Excel REST API。
  
    
    


下面是当前在 Excel Services REST API 中不受支持或不工作的一些更为重要功能的部分列表：
  
    
    


- **没有浮动图表。** 如果范围包含图表，且您通过 REST 请求范围，您将仅获得范围。
    
  
- **没有迷你图，没有图标条件格式。** 当前不支持。
    
  
- **与 EWA 不是完美像素。** REST 生成的 HTML 与 Excel Web Access 生成的 HTML 非常接近。但是，Excel Services REST API 无法访问 Excel Web Access 可以访问的级联样式表 (CSS) 元素。Excel Services REST API 返回 HTML 片段。HTML 片段必须为自我包含。
    
  
- **在表中没有区别。** 当将表作为 Atom 进行请求以查看单元格或数据是否为列标题、总计数据或常规数据时，在表中并无区别。即，没有区别来指定单元格或数据是标头还是总计数据，还是只是常规数据。整个表的所有表格单元格均同等对待。
    
  
- **URL 的大小限制。** URL 的大小限制为 2000 个字符左右。这意味着，如果您的工作簿中具有大量参数，您可能无法设置所有参数，尤其是当工作簿位于文件夹结构深处时。
    
  
- **特殊字符。** 不支持"?"和"#"等特殊字符。要正确引用包含特殊字符的工作表名称，基准准则是当引用包含特殊字符的工作表的公式时，"查看 Excel 客户端执行的操作"并遵循此示例。
    
  

