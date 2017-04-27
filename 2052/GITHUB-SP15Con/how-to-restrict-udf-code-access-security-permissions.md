---
title: 如何：限制 UDF 代码访问安全权限
keywords: cas,how to,howdoi,howto,UDF list
f1_keywords:
- cas,how to,howdoi,howto,UDF list
ms.prod: SHAREPOINT
ms.assetid: 4f022e0d-1fe3-4fab-b41f-82a0d628f77c
---


# 如何：限制 UDF 代码访问安全权限

如果您不希望某个特定的用户定义函数 (UDF) 程序集使用完全信任权限运行，您必须明确限制其代码访问安全权限。您可以使用 .NET Framework 2.0 配置工具配置代码组并限制权限。 
  
    
    

例如，假设您有一个 UDF 程序集包含多个方法。其中一个 UDF 方法执行自定义计算，同一程序集中的另一个 UDF 方法调用 Web 服务以获取股票报价。因为您的用户仅使用调用第一种（计算）方法的 Excel 工作簿，您可能需要禁用程序集的 Web 访问权限，以提高安全性。 
您的 UDF 程序集安装在服务器上的文件夹 C:\\UdfAssemblies\\CalcAndWebAccessUdf.dll 中。由于程序集位于与 Microsoft SharePoint Server 2010 相同的计算机上，当 Excel Calculation Services 加载 UDF 程序集时，它将加载到 MyComputer 区域。默认情况下，MyComputer 区域完全受信任。这意味着 UDF 程序集被授予了完全信任权限。 
  
    
    

要锁定 UDF 程序集使其不具备 Web 访问权限，您必须执行以下步骤，明确限制它被授予的权限：
1. 在计算机级别，在 My_Computer_Zone 下创建一个基于 URL 的新代码组。将代码组的范围设定为该特定程序集并创建自定义权限集。
    
  
2. 配置自定义代码组属性，使您的策略级别仅具有与自定义代码组相关的权限集。当 Excel Calculation Services 加载位于同一计算机的 UDF 程序集时，程序集将加载到 MyComputer 区域。这意味着，默认情况下，UDF 程序集被授予了完全信任权限。当自定义权限集与完全信任权限集交叉时，结果将为完全信任。要使策略仅具有与自定义代码组相关的权限集中的权限，您必须启用属性"此策略级别仅具有与此代码组相关的权限集中的权限"。
    
  
有关配置代码组的详细信息，请参阅 MSDN 上的以下文章：
-  [配置代码组使用.NET Framework 配置工具](http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true)
    
  
-  [代码访问安全实践](http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/dnnetsec/html/thcmch08.asp) (http://msdn.microsoft.com/library/default.asp?url=/library/zh-cn/dnnetsec/html/thcmch08.asp)
    
  

### 创建新的代码组


1. 单击"开始"，指向"所有程序"，指向"管理工具"，然后单击"Microsoft .NET Framework 2.0 配置"。 
    
    这将启动".NET 2.0 Framework 配置"工具。
    
  
2. 在左侧窗格中，展开"我的电脑"节点，然后展开"运行时安全策略"节点。
    
  
3. 展开"计算机"节点。
    
  
4. 展开"代码组"节点。
    
  
5. 展开"All_Code"节点。
    
  
6. 展开"My_Computer_Zone"节点。右键单击"My_Computer_Zone"，然后选择"新建"显示"识别新的代码组"对话框。
    
  
7. 选择"创建新的代码组"。
    
  
8. 在"名称"字段中，键入新代码组的名称，例如 RestrictWebAccessUdf。
    
  
9. 单击"下一步"。
    
  
10. 要将代码组范围限定为特定的 UDF 程序集，请从"选择此代码组的条件类型"中选择"URL"。 
    
    这将显示"URL"字段。
    
  
11. 在"URL"字段中，键入您想限制其 Web 访问权限的 UDF 程序集的路径，例如，C:\\UdfAssemblies\\CalcAndWebAccessUdf.dll。
    
  
12. 单击"下一步"。
    
  
13. 选择"新建权限集"，然后单击"下一步"。
    
  
14. 在"名称"字段中，键入权限集的名称，例如，AssemblyExecutionCustomPermissionSet。
    
  
15. 单击"下一步"。
    
  
16. 要向您的 UDF 程序集授予"程序集执行"权限，请从"程序集权限"列表中选择"安全"，然后单击"添加"。 
    
    这将显示"权限设置"对话框。
    
  
17. 选择"组合下列安全权限"。
    
  
18. 选择"启用程序集执行"。
    
  
19. 单击"确定"，然后单击"下一步"。
    
  
20. 单击"完成"。 
    
    您应该会看到您的新自定义代码组出现在"My_Computer_Zone"节点下（在本示例中为"RestrictWebAccessUdf"）。
    
  

### 确保权限集已执行


1. 在"My_Computer_Zone"节点下，右键单击新的自定义代码组（在本示例中为"RestrictWebAccessUdf"），然后选择"属性"。 
    
  
2. 在"常规"选项卡上，选中"此策略级别仅具有与此代码组相关的权限集中的权限"复选框。
    
  
3. 单击"应用"，然后单击"确定"。
    
    > **注释**
      > 如果由于无法发出 Web 服务调用导致 UDF 方法抛出异常，您应该会在调用 UDF 的 Excel 公式中收到"#VALUE!"错误。 

    > **注释**
      >  如果您想启用 UDF 程序集的 Web 访问权限以进行测试，您必须在自定义权限集中添加相应的权限。为此，请在"新建代码组"过程的步骤 11 中，选择"Web 访问权限"。

## 另请参阅


#### 任务


  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [如何：启用 UDF](how-to-enable-udfs.md)
  
    
    
 [如何：从 UDF 访问外部数据源](how-to-access-an-external-data-source-from-a-udf.md)
  
    
    
 [如何：使用 SharePoint Foundation 解决方案部署 UDF](how-to-deploy-udfs-using-sharepoint-foundation-solutions.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [关于 Excel Services UDF 的常见问题](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
