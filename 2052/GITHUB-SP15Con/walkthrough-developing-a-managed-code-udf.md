---
title: 演练：开发托管代码 UDF
ms.prod: SHAREPOINT
ms.assetid: e6a00833-0606-4a7d-91c3-b89a6e340348
---


# 演练：开发托管代码 UDF

本演练说明使用 Microsoft Visual C# 开发 Excel Services 用户定义函数的过程。
  
    
    

在本演练中，您将学习如何：
- 使用 Microsoft Visual Studio 2005 类库项目模板创建项目
    
  
- 添加对 Microsoft.Office.Excel.Server.Udf.dll 的引用。
    
  
- 编写用于 Excel Services 的 UDF。
    
  
- 创建从单元格调用自定义函数的工作簿。
    
  
- 在 Excel Services 中测试并运行 UDF。
    
  

## 必备组件

要完成本演练，您将需要： 
  
    
    

- Microsoft SharePoint Server 2010。 
    
    > **注释**
      > 在服务器上获取所有所需信息最简单的方法是，执行基本的独立安装。您首先需要添加的是受信任位置。 
- Excel。
    
  
- Visual Studio 或与 Microsoft .NET Framework 兼容的相似开发工具。
    
  
- 启用运行 UDF 程序集。
    
  
- 存储工作簿且允许工作簿调用 UDF 的受信任 SharePoint 文档库，方法是将 **AllowUdfs** 值设置为 **true**。 
    
  
- 调用存储在受信任 SharePoint 文档库中的 UDF 的示例工作簿。 
    
  
- 查看工作簿并将其发布到 SharePoint 文档库的权限。 
    
    > **注释**
      > 有关设置权限的详细信息，请参阅 Windows SharePoint Services 3.0 文档。 
- 使用 Excel 创建工作簿。
    
  
- 将工作簿另存为 .xlsx 或 .xlsb 文件。
    
    > **注释**
      > 有关如何信任某个位置、如何启用 UDF 以及如何设置 **AllowUdfs** 标记的详细信息，请参阅 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)。 

## 另请参阅


#### 任务


  
    
    
 [步骤 1：创建项目并添加 UDF 引用](step-1-creating-a-project-and-adding-a-udf-reference.md)
  
    
    
 [步骤 2：创建托管代码 UDF](step-2-creating-a-managed-code-udf.md)
  
    
    
 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [步骤 4：从单元格测试和调用 UDF](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
