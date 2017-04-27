---
title: 步骤 2：添加内容编辑器和 Excel Services Web 部件
ms.prod: SHAREPOINT
ms.assetid: c9c66843-fd77-4a0d-a512-d936d15d4429
---


# 步骤 2：添加内容编辑器和 Excel Services Web 部件

创建 ECMAScript (JavaScript, JScript) 文本文件并将其保存在受信任的位置之后，下一步是创建 Web 部件页面，并将内容编辑器 Web 部件和 Excel Services Web 部件添加到该页面。 
  
    
    

接下来，使用您添加到页面的 Excel Services Web 部件显示工作簿。 
### 添加内容编辑器 Web 部件和 Excel Services Web 部件


1. 创建新的 Web 部件页面。 
    
  
2. 将内容编辑器 Web 部件添加到您刚刚创建的 Web 部件页面。
    
  
3. 将您在 [步骤 1：创建 ECMAScript 文本文件](step-1-creating-a-ecmascript-text-file.md)中创建的文本文件的 URL 添加到内容编辑器 Web 部件中。您可通过添加您在 [步骤 1：创建 ECMAScript 文本文件](step-1-creating-a-ecmascript-text-file.md)中上载到受信任位置的文本文件的 URL 来执行此操作。 
    
    例如： 
    
     `http://` _myserver_ `/Docs/Documents/JSOM_FeedToContentEditor.txt`
    
  
4. 将 Excel Services Web 部件添加到页面。
    
  

### 运行 ECMAScript 示例


1. 将工作簿上载到受信任的文档库。使用"修改共享 Web 部件"菜单显示 Excel Services Web 部件任务窗格。在"工作簿显示"部分的"工作簿"字段中，键入您希望 Excel Services Web 部件加载和显示的工作簿的 URL。例如： 
    
     `http://` _myserver_ `/Docs/Documents/WorkbookToDisplay.xlsx`
    
  
2. 尝试单击不同的单元格并观察内容编辑器 **div** 中填充的单元格值。
    
  

