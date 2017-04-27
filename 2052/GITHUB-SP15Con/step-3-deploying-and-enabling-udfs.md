---
title: 步骤 3：部署和启用 UDF
ms.prod: SHAREPOINT
ms.assetid: 1e5e2a0a-041a-481c-a18b-578562a60e24
---


# 步骤 3：部署和启用 UDF

在此步骤中，您将执行以下操作：
  
    
    


1. 将您在 [步骤 2：创建托管代码 UDF](step-2-creating-a-managed-code-udf.md) 中创建的 SampleUdf.dll 部署到已安装 Microsoft SharePoint Server 2010 的计算机上的一个文件夹中。
    
  
2. 允许从特定的受信任位置调用用户定义函数 (UDF)，例如，受信任的"共享文档"位置。 
    
  
3. 启用 SampleUdf.dll。
    
  

## 部署 UDF


### 部署 UDF


1. 在要部署 UDF 的计算机的本地驱动器上创建一个名为"UDFs"的文件夹。例如，"C:\\UDFs"。
    
  
2. 复制 SampleUdf.dll 程序集。
    
  
3. 将 SampleUdf.dll 保存在"C:\\UDFs"中。 
    
  

## 信任位置


### 信任位置


1. 在"开始"菜单中，单击"所有程序"。 
    
  
2. 指向"Microsoft SharePoint 2010 产品"，然后单击"SharePoint 管理中心"。 
    
  
3. 在"应用程序管理"下，单击"管理服务应用程序"。
    
  
4. 在"管理服务应用程序"页面上，单击"Excel Services 应用程序"。
    
  
5. 在"Excel Services 应用程序"页面上，单击"受信任文件位置"。
    
  
6. 在"受信任文件位置"页面上，单击"添加受信任文件位置"。 
    
  
7. 在"添加受信任文件位置"页面上的"地址"中，键入您将保存工作簿的位置例如， _http://MyServer002/Shared%20Documents_。 
    
  
8. 在"位置类型"下，单击相应的位置类型。在本示例中，选择 Microsoft SharePoint Foundation。
    
  
9. 在"信任子级"下选择"受信任的子级"以信任子库或目录。
    
  
10. 在"允许用户定义函数"下，选择"允许的用户定义函数"，以允许从存储在此受信任位置的工作簿中调用 UDF。
    
  
11. 单击"确定"。
    
  

## 启用 UDF

要执行下列步骤，您需要一台已安装 SharePoint Server 2010 的计算机。
  
    
    

### 启用 UDF


1. 执行上一过程（信任位置）中的步骤 1 到步骤 3，以显示 SSP 的"共享服务"主页。
    
  
2. 在"Excel Services 设置"下，单击"用户定义函数程序集"。 
    
  
3. 在"Excel Services 用户定义函数"页面中，单击"添加用户定义函数"打开 Excel ****Services"添加用户定义函数程序集"页面。
    
  
4. 在"程序集"框中，键入 SampleUdf.dll 程序集的路径。在此示例中为  _C:\\UDFs\\SampleUdf.dll_。
    
  
5. 在"程序集位置"下，单击"文件路径"。
    
  
6. 在"启用程序集"下，"程序集已启用"复选项默认已选中。
    
  
7. 单击"确定"。
    
  

## 可靠编程

在调用 UDF 的工作簿中启动会话时，如果 **AllowUdfs** 值为 **false**，UDF 调用将失败。 
  
    
    

> **注释**
> **AllowUdfs** 标记使用"允许用户定义函数"选项表示（参阅"信任位置"一节中的步骤 9）。
  
    
    

会话启动后，如果您将 **AllowUdfs** 值更改为 **true**，UDF 调用将失败。这是因为 **AllowUdfs** 标记的更改将在下次会话中生效。您可以通过重置 Microsoft Internet Information Services (IIS) 解决此问题。重置 IIS 将重新加载 UDF。
  
    
    
有关重置 IIS 的详细信息，请参阅 [如何：启用 UDF](how-to-enable-udfs.md)。
  
    
    

## 另请参阅


#### 任务


  
    
    
 [步骤 1：创建项目并添加 UDF 引用](step-1-creating-a-project-and-adding-a-udf-reference.md)
  
    
    
 [步骤 2：创建托管代码 UDF](step-2-creating-a-managed-code-udf.md)
  
    
    
 [步骤 4：从单元格测试和调用 UDF](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [如何：启用 UDF](how-to-enable-udfs.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
