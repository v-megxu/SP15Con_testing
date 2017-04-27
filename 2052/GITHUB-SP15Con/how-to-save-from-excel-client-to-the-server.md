---
title: 如何：从 Excel 客户端保存到服务器
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: OFFICE365
ms.assetid: 28716ba5-0774-44df-833b-0034d2c63319
---


# 如何：从 Excel 客户端保存到服务器

此示例演示如何：
  
    
    


1. 创建具有可编辑范围的工作簿。
    
  
2. 将工作簿保存到作为受信任位置的 SharePoint 文档库。
    
    > **注释**
      > 假定您已经创建 SharePoint 文档库并将其设为受信任的位置。有关详细信息，请参阅 [如何：信任位置](how-to-trust-a-location.md)。 
3. 使用 Excel Web Access 中的参数窗格更改工作簿中的值。
    
  

## 将工作簿保存到 Excel Services


### 创建具有可编辑范围的工作簿


1. 启动 Excel。
    
  
2. 在单元格 A1 中，键入 8。
    
  
3. 在单元格 A2 中，键入 =3*A1。
    
  
4. 要将单元格 A1 设为在 Excel Web Access 中可编辑，您必须首先将单元格 A1 设为在指定范围内： 
    
1. 单击"公式"选项卡，然后单击单元格"A1"将其选中。
    
  
2. 在"公式"选项卡的"定义的名称"组中，单击"定义名称"。
    
  
3. 在"新名称"对话框的"名称"文本框中，键入"MyAOneParam"。
    
  

### 保存到 Excel Services


1. 在"文件"菜单上，单击"保存并发送"，然后单击"保存到 SharePoint"。 
    
  
2. 在"保存到 SharePoint"对话框中，单击"发布选项"。
    
  
3. 在"发布选项"对话框中的"显示"选项卡上，确保"整个工作簿"处于选中状态。
    
  
4. 在"参数"选项卡上，单击"添加"。
    
  
5. 在"添加参数"列表中，选中"MyAOneParam"复选框。
    
  
6. 单击"确定"。您现在应该会在"参数"列表中看到"MyAOneParam"。
    
  
7. 单击"确定"关闭"发布选项"对话框。
    
  
8. 在"保存到 SharePoint"对话框中，单击"另存为"。
    
  
9. 在"另存为"对话框中，确保"在浏览器中使用 Excel 打开"复选框处于选中状态。
    
  
10. 在"文件名"文本框中，键入您想在其中存储此工作簿的受信任 SharePoint 文档库的路径。例如，http:// _MyServer002_/Shared%20Documents/TestParam.xlsx。
    
  
11. 单击"保存"。您应该会在 Excel Web Access 中看到 TestParam.xlsx。 
    
  

### 使用参数更改值


1. 在"参数"窗格中，您应该会看到单元格"A1"的指定范围即"MyAOneParam"。 
    
  
2. 您可以通过在"MyAOneParam"旁边的文本框中键入一个数字，更改单元格"A1"和单元格"A2"中的值。例如，如果您键入 10 并单击"应用"，单元格"A1"将变为"10"，单元格"A2"变为"30"。
    
  

## 另请参阅


#### 任务


  
    
    
 [如何：保存到服务器以准备用于编程访问](how-to-save-to-the-server-to-prepare-for-programmatic-access.md)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
