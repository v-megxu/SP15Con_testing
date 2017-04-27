---
title: 从网页中删除 Excel 交互式视图
ms.prod: SHAREPOINT
ms.assetid: 407b3aa3-7286-462b-905f-811a3b7f3f1c
---


# 从网页中删除 Excel 交互式视图

Excel 交互式视图功能已被禁用。如果您在网页中插入了 Excel 交互式视图，您可以从网页的 HTML 中删除按钮的  `<script>` 标记和占位符 `<a>` 标记，以将其删除。
  
    
    

要删除  `<script>` 标记，请搜索并删除以下 HTML。


```HTML

<script src="http://r.office.microsoft.com/r/rlidExcelButton?v=1&amp;amp;kip=1" type="text/javascript"></script>
```

要删除占位符  `<a>` 标记，请在 HTML 中查找位于任何 <table> 元素前面的 <a> 标记。因为 <a> 标记可自定义，请解析 HTML 的第一部分字符串，以查找按钮的所有实例。


```HTML
<a href="#" name="MicrosoftExcelButton" data-xl-tableTitle="" data-xl-buttonStyle="Standard" data-xl-fileName="Book1" data-xl-attribution="" ></a>
```


## 解决方法

作为替代方法，我们建议您 [将 Excel 嵌入到网页中](https://support.office.com/en-au/article/Share-it-Embed-an-Excel-workbook-on-your-blog-804e1845-5662-487e-9b38-f96307144081?ui=en-US&amp;rs=en-AU&amp;ad=AU)。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的 Excel Services](excel-services-in-sharepoint-2013.md)
    
  
-  [将 Excel 工作簿嵌入到博客中](https://support.office.com/en-au/article/Share-it-Embed-an-Excel-workbook-on-your-blog-804e1845-5662-487e-9b38-f96307144081?ui=en-US&amp;rs=en-AU&amp;ad=AU)
    
  

