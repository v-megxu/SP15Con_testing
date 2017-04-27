---
title: 步骤 1：创建项目并添加 UDF 引用
ms.prod: OFFICE365
ms.assetid: 4c6f1279-28df-45af-8488-42a6573d526d
---


# 步骤 1：创建项目并添加 UDF 引用

在此步骤中，您将创建项目，并添加对 Microsoft.Office.Excel.Server.Udf.dll 的引用。 
  
    
    


## 创建项目

以下项目使用 Microsoft Visual Studio 2005。
  
    
    

> **注释**
> 根据您在 Visual Studio 集成开发环境 (IDE) 中使用的设置，创建项目的过程可能略有不同。 
  
    
    


### 创建项目


1. 启动 Visual Studio。
    
  
2. 在"文件"菜单上，指向"新建"，然后单击"项目"。此时将显示"新建项目"对话框。 
    
  
3. 在"项目类型"窗格中，选择"Visual C# 项目"。
    
  
4. 在"模板"窗格中，单击"类库"。
    
  
5. 在"名称"框中，键入"SampleUdf"。
    
  
6. 在"位置"框中，键入您想保存项目的路径，或者单击"浏览"导航到该文件夹。
    
  
7. 单击"确定"。您的新项目将显示在"解决方案资源管理器"中。您将看到一个默认名称为 Class1.cs 的文件已添加到您的项目中。
    
  
8. 您应该在 Class1.cs 文件中看到以下代码：
    
  ```cs
  
using System;
using System.Collections.Generic;
using System.Text;

namespace SampleUdf
{
    public class Class1
    {
    }
}
  ```


  ```VB.net
  
Imports System
Imports System.Collections.Generic
Imports System.Text

Namespace SampleUdf
Public Class Class1
End Class
End Namespace
  ```


## 添加引用

以下步骤演示如何查找 Microsoft.Office.Excel.Server.Udf.dll 以及如何添加对它的引用。 
  
    
    

### 添加引用


1. 在"项目"菜单上单击"添加引用"。
    
  
2. 在"添加引用"对话框中的".NET"选项卡上，选择"Excel Services UDF Framework"。
    
    > **注释**
      > 您也可以打开"解决方案资源管理器"中的"添加引用"对话框，方法是右键单击"引用"并选择"添加引用"。 
3. 单击"确定"。
    
    > **注释**
      > 上述步骤假定您正在已安装 Microsoft SharePoint Server 2010 的计算机上构建项目。在已安装 SharePoint Server 2010 的计算机上，您可以在以下位置找到 Microsoft.Office.Excel.Server.Udf.dll 的副本： > [drive:]\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI 

## 另请参阅


#### 任务


  
    
    
 [步骤 2：创建托管代码 UDF](step-2-creating-a-managed-code-udf.md)
  
    
    
 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [步骤 4：从单元格测试和调用 UDF](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
