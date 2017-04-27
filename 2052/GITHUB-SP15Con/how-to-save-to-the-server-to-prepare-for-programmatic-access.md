---
title: 如何：保存到服务器以准备用于编程访问
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: OFFICE365
ms.assetid: 80b34a29-3d40-4d11-9ba1-b4886ffcfd42
---


# 如何：保存到服务器以准备用于编程访问

本示例说明如何将 Excel 工作簿保存到服务器以准备进行编程访问。步骤如下：
  
    
    


1. 创建具有指定范围的工作簿。
    
  
2. 将工作簿保存到受信任的 SharePoint 库位置。 
    
    > **注释**
      > 假定您已经创建 SharePoint 文档库并将其设为受信任的位置。有关详细信息，请参阅 [如何：信任位置](how-to-trust-a-location.md)。 
3. 使用 Excel Web Services **SetCellA1** 方法，以编程方式指定工作表、指定范围和单元格值的值。值作为参数传递即 _args [1]_ 和 _args [2]_：
    
  ```cs
  
status = xlServices.SetCellA1(sessionId, String.Empty, args[1], args[2]);
  ```


  ```VB.net
  status = xlServices.SetCellA1(sessionId, String.Empty, args(1), args(2))
  ```


您可以使用 Web 表单或从命令行指定  _args [1]_ 和 _args [2]_ 的值：
  
    
    




```
GetSnapshot.exe http://MyServer002/MyTrustedDocumentLibrary/TestMyParam.xlsx MyParam28 > MySnapshot.xlsx 
```

在本示例中， _args [1]_ 为 **MyParam**， **args [2]** 为 _28_， _GetSnapshot.exe_ 是您创建的应用程序的名称。要查找示例程序，请参阅 [如何：获取整个工作簿或快照](how-to-get-an-entire-workbook-or-a-snapshot.md)。
### 创建指定范围


1. 启动 Excel。
    
  
2. 将 **Sheet1** 重命名为MyParamSheet。
    
  
3. 在单元格 B2 中，键入 20。
    
  
4. 在单元格 B3 中，键入 =2+B2。
    
  
5. 将单元格 B3 设为粗体。
    
  
6. 将单元格设为 B2 指定范围： 
    
1. 在功能区中，单击"公式"选项卡，然后单击单元格"B2"将其选中。
    
  
2. 在"指定名称"组中，单击"定义名称"。
    
  
3. 在"新名称"对话框的"名称"文本框中，键入"MyParam"。
    
  
7. 将工作簿保存到本地驱动器上的所选位置。将工作簿命名为 TestMyParam.xlsx。 
    
  

### 保存到 SharePoint 库


1. 在"文件"菜单上，单击"保存并发送"，然后单击"保存到 SharePoint"。 
    
  
2. 在"保存到 SharePoint"对话框中，单击"发布选项"。
    
  
3. 在"发布选项"对话框中的"显示"选项卡上，确保"整个工作簿"处于选中状态。
    
  
4. 单击"参数"。 
    
  
5. 单击"添加"。
    
  
6. 在"添加参数"列表中，您应该会看到"MyParam"。选中"MyParam"复选框。
    
  
7. 单击"确定"。您现在应该会在"参数"列表中看到"MyParam"。
    
  
8. 单击"确定"。
    
  
9. 在"保存到 SharePoint"对话框中，单击"另存为"。
    
  
10. 在"另存为"对话框中，取消选中"在浏览器中使用 Excel 打开"复选框。
    
  
11. 在"文件名"框中，键入您想在其中存储此工作簿的受信任 SharePoint 文档库的路径。例如，http:// _MyServer002_/MyDocumentLibrary/TestParam.xlsx。
    
  
12. 单击"保存"。
    
  

### 以编程方式指定值


1. 下面是 Excel Web Services 中 **SetCellA1** 方法的签名：
    
  ```cs
  public void SetCellA1 (
string sessionId,
string sheetName,
string rangeName,
Object cellValue,
Out Status[] status
)
  ```


  ```VB.net
  
Public Sub SetCellA1(ByVal sessionId As String,
              ByVal sheetName As String, 
             ByVal rangeName As String, 
             ByVal cellValue As Object, 
             Out ByVal status() As Status)
End Sub
  ```


    将工作表、指定范围和单元格值的值设置为 **SetCellA1** 方法，如下所示：
    


  ```cs
  
// Set a value into a cell.
status = xlSrv.SetCellA1(sessionId, String.Empty, args[1], args[2]);

  ```

2. 在上面的代码中： 
    
  -  _args [1]_ 是指定范围的名称。在本示例中为"MyParam"。
    
  
  -  _args [2]_ 是您要在单元格中设置的值。值将在其中设置的单元格是名为"MyParam"的 _args [1]_ 中的命名范围。
    
  
3. 如果您使用命令行，可以如下所示传递参数：
    
     `GetSnapshot.exe http://` _MyServer002_ `/` _MyTrustedDocumentLibrary_ `/TestMyParam.xlsx MyParam 28 > MySnapshot.xlsx`
    
  
4. 如果您生成工作簿的快照，您将看到： 
    
  - 单元格 B2（具有指定范围"MyParam"）现在的值为您通过程序传递的值，即"28"。
    
  
  - 单元格 B3 的值为新计算的值"30"。
    
  
  - 单元格 B3 不显示原始公式，即"=2+B2"。
    
  
  - 单元格 B3 保留字体格式，即粗体。
    
  

> **注释**
> 有关快照的详细信息，请参阅 [如何：获取整个工作簿或快照](how-to-get-an-entire-workbook-or-a-snapshot.md)。有关 **SetCellA1** 方法的详细信息，请参阅 Excel Web Services 参考文档。Web 服务的命名空间为 [Microsoft.Office.Excel.Server.WebServices](https://msdn.microsoft.com/library/Microsoft.Office.Excel.Server.WebServices.aspx) 。
  
    
    


## 另请参阅


#### 任务


  
    
    
 [如何：从 Excel 客户端保存到服务器](how-to-save-from-excel-client-to-the-server.md)
#### 引用


  
    
    
 [Microsoft.Office.Excel.Server.WebServices](https://msdn.microsoft.com/library/Microsoft.Office.Excel.Server.WebServices.aspx)
#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [环回 SOAP 调用和直接链接](loop-back-soap-calls-and-direct-linking.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
