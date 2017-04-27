---
title: 步骤 4：从单元格测试和调用 UDF
ms.prod: OFFICE365
ms.assetid: d3e6aa72-2eb8-4b4b-a0eb-273486890d00
---


# 步骤 4：从单元格测试和调用 UDF

在本步骤中，您将测试您在之前的步骤中创建、部署和启用的 SampleUdf.dll 程序集。要测试用户定义函数 (UDF)，您需执行以下操作：
  
    
    


1. 创建一个工作簿，它具有指定范围以及调用 SampleUdf.dll 中的函数的公式。
    
  
2. 将工作簿保存到作为受信任位置的 SharePoint 文档库。
    
    > **注释**
      > 假定您已经创建 SharePoint 文档库并将其设为受信任的位置。有关如何信任某个位置的信息，请参阅 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md) 中的"信任位置"部分。
3. 更改参数以重新计算工作簿。
    
  

## 测试 UDF


### 从单元格调用 UDF


1. 启动 Microsoft Office Excel 2007。
    
  
2. 在单元格 A1 中，键入公式以调用 SampleUdf.dll 中的  `MyDouble` 函数。 `MyDouble` 函数的参数类型为 **double**。在本示例中，您将从单元格 B1 中获取参数。在单元格 A1 中，键入 =MyDouble(B1)。
    
    > **注释**
      > 公式在 Excel 中将计算为"#NAME?"。仅当工作簿显示在 Excel Services 中时，才会计算公式。 

    > **注释**
      > 您可以在客户端和服务器上运行 UDF。稍后在 MSDN 上的发表的一篇文章将解释详细信息。为简单起见，此处将省略。 
3. 在单元格 B1 中，键入数字 8。
    
  
4. 将单元格 B1 设为指定范围。首先单击"公式"选项卡，然后单击单元格 B1 将其选中。在"公式"选项卡上的"指定单元格"组中，单击"指定范围"。在"新建名称"对话框的"名称"框中，键入"MyDoubleParam"。
    
  
5. 在单元格 A2 中，键入公式以调用  `ReturnDateTimeToday` 函数。键入=ReturnDateTimeToday()。
    
  
6. 在单元格 A3 中，键入公式以调用  `ReturnDateTimeToday` 函数。键入=ReturnDateTimeToday()。接下来，右键单击单元格 A3 以显示菜单。单击"格式化单元格"。
    
  
7. 在"格式化单元格"对话框的"数字"选项卡上，选择"日期"。从"类型"列表中选择日期格式类型例如，*3/4/2001。
    
  
8. 单击"确定"。
    
  
9. 将工作簿保存到本地驱动器上的所选位置。将工作簿命名为"TestSampleUdf.xlsx"。 
    
  

### 保存到 Excel Services


1. 单击"Microsoft Office 按钮"，指向"另存为"，然后单击"为 Excel Services 保存"。 
    
  
2. 在"另存为"对话框中，单击"Excel Services"。
    
  
3. 在"Excel Services 选项"对话框中的"显示"选项卡上，确保"整个工作簿"处于选中状态。
    
  
4. 单击"参数"。 
    
  
5. 在"添加参数"列表中，选中"MyDoubleParam"复选框。
    
  
6. 单击"确定"。您现在应该会在"参数"列表中看到"MyDoubleParam"。
    
  
7. 单击"确定"。
    
  
8. 在"另存为"对话框中，确保"保存后在我的浏览器中打开此工作簿"复选框处于选中状态。
    
  
9. 在"文件名"框中，键入您想在其中存储此工作簿的受信任 SharePoint 文档库的路径。例如， _http://MyServer002/Shared%20Documents/TestSampleUdf.xlsx_。
    
  
10. 单击"保存"。您应该会在 Excel Web Access 中看到 TestSampleUdf.xlsx。在单元格 A1 中，您应该会看到数字"72"，因为单元格 B1 * 9 = 8 * 9，即 72。在单元格 A2 中，您应该会看到一个数字。在单元格 A3 中，您应该会看到当前日期。 
    
    > **注释**
      > 在单元格 A2 中，数字表示自 1/1/1900（如果您启用了"使用 1904 日期系统"，则为 1/1/1904）起的天数。这是 Excel 在内部表示日期的方式。 

### 更改参数以测试 UDF


1. 在"参数"窗格中，您应该会看到单元格 B1 的指定范围即"MyDoubleParam"。 
    
  
2. 您可以更改单元格 B1 中的值，方法是在"MyDoubleParam"旁边的框中键入一个数字。例如，如果您键入 3 并单击"应用"，Excel Services 将重新计算工作簿。单元格 A1 将包含"27"而非"72"。
    
  

## 另请参阅


#### 任务


  
    
    
 [步骤 1：创建项目并添加 UDF 引用](step-1-creating-a-project-and-adding-a-udf-reference.md)
  
    
    
 [步骤 2：创建托管代码 UDF](step-2-creating-a-managed-code-udf.md)
  
    
    
 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
