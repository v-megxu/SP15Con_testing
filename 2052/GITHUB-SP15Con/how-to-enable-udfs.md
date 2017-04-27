---
title: 如何：启用 UDF
keywords: how to,howdoi,howto,UDF list
f1_keywords:
- how to,howdoi,howto,UDF list
ms.prod: SHAREPOINT
ms.assetid: 8c1af2eb-bb22-45e1-82de-a2b4b53d7a26
---


# 如何：启用 UDF

共享服务提供程序 (SSP) 中的每个 Excel Services 受信任位置都有一个 **AllowUdfs** 标记。
  
    
    


> **注释**
> **AllowUdfs** 标记使用"Excel Services 受信任的文件位置"页面上的"允许用户定义函数"选项表示。
  
    
    


 **AllowUdfs** 的默认值为 **false**。如果 **AllowUdfs** 值在特定的受信任位置设置为 **false**，该受信任位置的工作簿将不允许调用 UDF。 
  
    
    

要允许从特定受信任位置调用 UDF，应将 **AllowUdfs** 值设置为 **true**。当会话在该受信任位置具有 UDF 调用的工作簿中启动时，如果 **AllowUdfs** 值为 **false**，UDF 调用将失败。会话启动后，如果您将 **AllowUdfs** 值更改为 **true**，UDF 调用也将失败。这是因为 **AllowUdfs** 标记的更改将在配置数据库更新后，在下一次会话生效。您可以通过重新启动该会话来解决此问题例如，通过在 Excel Web Access 中选择"重新加载工作簿"。
> **警告**
> 如果您选择改为重置 Microsoft Internet Information Services (IIS)，它将结束所有当前会话。 
  
    
    


## 启用 UDF

要执行下列步骤，您需要一台已安装 Microsoft SharePoint Server 2010 的计算机。
  
    
    

### 启用 UDF


1. 在"开始"菜单中，单击"所有程序"。 
    
  
2. 指向"Microsoft Office Server"，然后单击"SharePoint 管理中心"。 
    
  
3. 在快速启动栏中，单击共享服务提供程序 (SSP) 链接例如，"SharedServices1"以查看该特定 SSP 的共享服务主页。
    
  
4. 在"Excel Services 设置 "下，单击"用户定义函数"。 
    
  
5. 在"Excel Services 用户定义函数"页面中，单击"添加用户定义函数"打开 Excel Services"添加用户定义函数程序集"页面。
    
  
6. 在"程序集"框中，键入 UDF 程序集的路径。例如，C:\\MyUdfFolder\\MyUdf.dll。
    
  
7. 在"程序集位置"下，单击"本地文件"。
    
    > **注释**
      > 在 Excel Services 的将来版本中，"本地文件"选项将替换为"文件路径"。如果您看到"文件路径"，请改为选择此选项。 
8. 在"启用程序集"下，"程序集已启用"复选项默认已选中。
    
  
9. 单击"确定"。
    
  

## 允许 UDF 调用


### 允许从工作簿调用 UDF


1. 打开 Excel Services"添加受信任的文件位置"页面（如果您添加新的受信任位置）或"编辑受信任的文件位置"页面（如果您编辑现有的受信任位置）。 
    
    > **注释**
      > 有关信任位置的详细信息，请参阅 [如何：信任位置](how-to-trust-a-location.md)。 
2. 在"允许用户定义函数"下，选择"允许的用户定义函数"，以允许从存储在此受信任位置的工作簿中调用 UDF。
    
  
3. 单击"确定"。
    
  

## 另请参阅


#### 任务


  
    
    
 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [关于 Excel Services UDF 的常见问题](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services 最佳实践](excel-services-best-practices.md)
