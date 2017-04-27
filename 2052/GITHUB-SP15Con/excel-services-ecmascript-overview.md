---
title: Excel Services ECMAScript 概述
ms.prod: SHAREPOINT
ms.assetid: f8c1be86-df19-44c3-a3bc-c0da2b80df10
---


# Excel Services ECMAScript 概述

在 Microsoft SharePoint Server 2010 中，Excel Services 新增了对 ECMAScript (JavaScript, JScript) 的支持。JavaScript 使用 Excel Services 启用了一系列新解决方案。 
  
    
    

Excel Services 中的 JavaScript 对象模型使开发人员可以自动执行和自定义页面上的 Excel Web Access Web 部件控件并与其交互。通过 JavaScript 对象模型，您可以构建与页面上的一个或多个 Excel Web Access Web 部件控件交互的混合解决方案及其他集成解决方案。它还允许您向工作簿及相关代码中添加更多功能。
通过使用 JavaScript 对象模型，可以检测并响应用户与 Excel Web Access Web 部件的交互，并以编程方式与一个或多个 Excel Web Access Web 部件交互。
  
    
    


## 使用 ECMAScript 对象模型

要使用 Excel Services 中的 JavaScript 对象模型，您将 JavaScript 代码插入到包含 Excel Web Access Web 部件的页面。这可以通过使用内容编辑器 Web 部件或通过直接编辑 .aspx 页面，将代码添加到 Web 部件页面来完成。
  
    
    
Excel Services 中的 JavaScript 对象模型允许开发人员执行以下操作： 
  
    
    

- 访问工作簿中的项目，如范围、表、数据透视表、图表和工作表。
    
  
- 使用范围或指定范围从单元格设置并检索值。
    
  
- 当用户更改活动选择或活动单元格时或当用户开始编辑单元格时触发事件。
    
  
- 滚动到其他区域并切换显示的工作表或指定项目。 
    
  
有关详细信息，请参阅以下链接：
  
    
    

- 有关 Excel Services 中的 JavaScript 对象模型的详细信息，请参阅  [Ewa](http://msdn.microsoft.com/library/6fe73191-3213-b986-1ad6-2c3b918a2241%28Office.15%29.aspx) 命名空间参考文档。
    
  
- 有关如何使用内容编辑器 Web 部件与 Excel Services 中的 JavaScript 对象模型交互的示例，请参阅 [演练：使用内容编辑器 Web 部件进行开发](walkthrough-developing-using-the-content-editor-web-part.md)。
    
  

## ECMAScript .js 文件位置

JavaScript 对象模型的 Minified .js 文件安装在 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS 目录中。文件名为 EwaMoss.js。
  
    
    
有关如何使用 .aspx 页面或 .js 文件内的 JavaScript 对象模型的基本信息，请参阅 [为 ECMAScript 设置应用程序页](http://msdn.microsoft.com/library/48582a0b-f787-4868-8298-958717ec8ff8%28Office.15%29.aspx)。
  
    
    

