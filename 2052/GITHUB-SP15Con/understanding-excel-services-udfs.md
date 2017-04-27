---
title: 了解 Excel Services UDF
ms.prod: OFFICE365
ms.assetid: a1567278-fac4-4b3b-a814-56f2376c1217
---


# 了解 Excel Services UDF

用户定义函数 (UDF) 是可以扩展 Excel 的计算和数据导入功能的自定义函数。开发人员创建自定义计算包，以提供：
  
    
    


- 未内置到 Excel 的函数。
    
  
- 内置函数的自定义实现。
    
  
- 对旧的或不受支持的数据源的自定义数据源，以及应用程序特定的数据流。
    
  

创建工作簿的用户可以通过公式从单元格调用 UDF例如，"=MyUdf(A1*3.42)"就像它们调用内置函数一样。
  
    
    

Excel Services UDF 使您可以使用单元格中的公式来调用使用托管代码编写并部署到 Microsoft SharePoint Server 2010 的自定义函数。您可以创建 UDF 以执行以下操作：
- 调用自定义数学函数。
    
  
- 从自定义数据源获取数据并插入到工作表中。
    
  
- 从 UDF 调用 Web 服务。
    
  

## 创建托管代码 UDF

创建 Excel Services 托管代码 UDF 的一种简便方法是使用 Microsoft Visual Studio 2005 类库模板。您将需要引用托管代码 UDF 项目中的 Excel Services UDF 动态链接库 (DLL)（名为 Microsoft.Office.Excel.Server.Udf.dll）。 
  
    
    
Microsoft.Office.Excel.Server.Udf.dll 已使用 Microsoft .NET Framework 2.0 进行编译。如果您使用 Visual Studio 2003 创建托管代码 UDF，您将无法引用 Microsoft.Office.Excel.Server.Udf.dll。使用 .NET Framework 旧版本创建的程序集无法引用使用 .NET Framework 2.0 创建的程序集。
  
    
    

### 必需属性

要使用类中的自定义函数作为 Excel Services UDF 类，必须使用 **Microsoft.Office.Excel.Server.Udf.UdfClass** 属性标记 UDF 类。UDF 程序集中任何未使用此属性标记的类将被 Excel Calculation Services 忽略。它们不会被视为 Excel Services UDF 类。
  
    
    
要使用类中的自定义函数作为 Excel Services UDF 方法，必须使用 **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性标记 UDF 方法。UDF 程序集中任何未使用此属性标记的方法将被 esecsshort 忽略，因为它们不会被视为 Excel Services UDF 方法。
  
    
    
 **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性具有 **IsVolatile** 特性。您可使用 **IsVolatile** 特性将 UDF 方法指定为易失性和或非易失性。 **IsVolatile** 特性使用布尔值。默认值为 **false**，这表示特定 UDF 方法为非易失性。
  
    
    

### Microsoft.Office.Excel.Server.Udf.dll 的位置

在已安装 SharePoint Server 2010 的计算机上，您可以在以下位置找到 Microsoft.Office.Excel.Server.Udf.dll 的副本：
  
    
    
 `[drive:]\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI`
  
    
    

## 安全性和部署


### 部署位置类型

UDF 程序集可以位于本地目录、全局程序集缓存或网络共享中。在服务器场方案中，本地目录路径在整个服务器场都必须相同。
  
    
    

### UDF 程序集的标识

您可以使用供 Excel Calculation Services 调用的程序集的完整路径或强名称来公开 UDF 程序集的标识。 
  
    
    
例如，可以使用：
  
    
    

- C:\\UDFs\\MySampleUdf.dll 
    
  
- \\\\MyNetworkServer\\UDFs\\MySampleUdf.dll
    
  
- CompanyName.Hierarchichal.MyUdfNamespace.MyUdfClassName.dll, Version=1.1.0.0, Culture=en, PublicKeyToken=e8123117d7ba9ae38
    
  

### 启用 UDF 程序集

UDF 程序集在默认情况下处于禁用状态。 
  
    
    
每个 Excel Services 受信任位置都有一个 **AllowUdfs** 标记。
  
    
    

> **注释**
> **AllowUdfs** 标记在 Excel Services"受信任文件位置"页面上使用 **User-defined functions allowed** 选项进行标记。要了解如何导航到"受信任文件位置"页面，请参阅 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)。 
  
    
    

 **AllowUdfs** 的默认值为 **false**。如果 **AllowUdfs** 值在特定的受信任位置设置为 **false**，该受信任位置的工作簿将不允许调用 UDF。 
  
    
    
要允许从特定受信任位置调用 UDF，应将 **AllowUdfs** 值设置为 **true**。
  
    
    
当会话在该受信任位置具有 UDF 调用的工作簿中启动时，如果 **AllowUdfs** 值为 **false**，UDF 调用将失败。会话启动后，如果您将 **AllowUdfs** 值更改为 **true**，UDF 调用也将失败。这是因为 **AllowUdfs** 标记的更改将在配置数据库更新后，在下一次会话生效。
  
    
    

### 允许运行 UDF 程序集

如果管理员希望允许运行 UDF 程序集，必须注册所有 UDF 程序集，并使工作簿可以调用 UDF，方法是将 **AllowUdfs** 标记在受信任位置设置为 **true**。
  
    
    

### 重新加载 UDF 程序集

要重新加载 UDF 程序集，您可以运行 **iisreset** 或重新启动 Excel Calculation Services 应用程序域。
  
    
    

> **警告**
> 重置 IIS 将结束所有当前会话。 > 有关详细信息，请参阅 [如何：启用 UDF](how-to-enable-udfs.md)。 
  
    
    

有关详细信息，请参阅 [从内存中卸载应用程序](http://go.microsoft.com/fwlink/?LinkId=65706) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/csvr2002/htm/cs_mmc_administering_myhj.asp)。
  
    
    

### UDF 程序集的默认代码访问安全权限

默认情况下，UDF 程序集在完全信任下运行。 
  
    
    

### 限制 UDF 程序集的代码访问安全权限

如果您不希望某个特定的 UDF 程序集使用完全信任权限运行，您必须明确限制其代码访问安全权限。您可以使用 .NET Framework 2.0 配置工具配置代码组并限制权限。 
  
    
    
开发人员还可以使用代码中的 **RequestMinimum** 和 **RequestOptional** 方法来确保 UDF 程序集未获取非必要的权限。
  
    
    
有关配置代码组以及 **RequestMinimum** 和 **RequestOptional** 方法的详细信息，请参阅 MSDN 上的以下文章：
  
    
    

-  [配置代码组使用.NET Framework 配置工具](http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true)
    
  
-  [代码访问安全实践](http://go.microsoft.com/fwlink/?LinkId=65465) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/dnnetsec/html/thcmch08.asp)
    
  

## 另请参阅


#### 任务


  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
  
    
    
 [如何：捕获异常](how-to-catch-exceptions.md)
  
    
    
 [如何：启用 UDF](how-to-enable-udfs.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [关于 Excel Services UDF 的常见问题](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [Excel Services 体系结构](excel-services-architecture.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services 最佳实践](excel-services-best-practices.md)
