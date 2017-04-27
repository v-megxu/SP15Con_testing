---
title: Excel Web Services 的新增功能
ms.prod: OFFICE365
ms.assetid: cb342e94-0308-4608-b027-b73ebe8107b0
---


# Excel Web Services 的新增功能

本主题列出了添加到 Excel Web Services 的新类型和成员。
  
    
    


## Excel Web Services 增强

Excel Web Services 在 Microsoft SharePoint Server 2010 中得到扩展和增强。在 SharePoint Server 2010 中，您可以编程方式编辑和保存工作簿。此外，Excel Web Services 现在支持在 SharePoint Server 2010 中的编辑会话中打开工作簿。在此场景中，您可以在其他用户共同创作工作簿的同时编辑工作簿。
  
    
    
有关 Excel Web Services API 的详细信息以及有关新方法、枚举和类型的更详细备注，请参阅 **Microsoft.Office.Excel.Server.WebServices**。
  
    
    

### 新方法

下面是添加到 Excel Web Services 的新方法，按字母顺序排列： 
  
    
    

- **GetChartImageUrl** 获取工作簿中的图表或数据透视图图像文件的 URL 值。
    
  
- **GetPublishedItemNames** 获取工作簿中已发布项目的列表。
    
  
- **GetSheetNames** 获取工作簿中存在的所有工作表名称的列表。
    
  
- **OpenWorkbookForEditing** 打开工作簿以进行编辑。
    
  
- **SaveWorkbook** 将工作簿保存为原始格式（.xlsx, .xlsb, .xlsm）。
    
  
- **SaveWorkbookCopy** 使用不同的文件名保存工作簿和/或将工作簿保存到不同的 SharePoint 文档库。
    
  
- **SetCalculationOptions** 更改工作簿的计算模式设置。
    
  
- **SetParameters** 设置单个 Web Service 调用的多个已发布参数。
    
  
此外：
  
    
    

- 现在您可以使用设定值方法设置公式。
    
  
- SharePoint Server 2010 中的 Excel Web Services 支持动态范围。
    
  

### 新枚举

下面是添加到 Excel Web Services 的新枚举，按字母顺序排列：
  
    
    

- **ItemType** 指示返回的项的类型。
    
  
- **SheetType** 指示返回的表的类型。
    
  
- **SheetVisibility** 指示返回的表是否可见。
    
  
- **SaveOptions** 指定是否要覆盖现有的未锁定文件。
    
  
- **WorkbookCalculation** 定义工作簿的计算模式设置。
    
  

### 新类型

下面是添加到 Excel Web Services 的新类型，按字母顺序排列：
  
    
    

- **ParameterInfo** 获取或设置参数的名称和值。
    
  
- **SheetInfo** 包含有关工作簿中工作表的信息。
    
  
- **Size** 定义图表图像的高度和宽度。
    
  
- **WorkbookItem** 显示工作簿中的已命名项目。
    
  

## 另请参阅


#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
