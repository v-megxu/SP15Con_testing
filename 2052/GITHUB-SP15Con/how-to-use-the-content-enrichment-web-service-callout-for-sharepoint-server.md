---
title: 如何：对 SharePoint Server 使用内容扩充 Web 服务标注
ms.prod: SHAREPOINT
ms.assetid: d4e44498-9a3d-4f2f-b5ba-6ebef9971dcb
---


# 如何：对 SharePoint Server 使用内容扩充 Web 服务标注
了解如何在 SharePoint Server 2013 中实施内容扩充 Web 服务以在对已爬网项编制索引之前修改其托管属性。
SharePoint 2013 中的搜索功能允许开发人员向内容处理中添加自定义步骤以在对已爬网项编制索引之前修改其托管属性。此自定义步骤需要实施可扩充所处理项的托管属性的外部 Web 服务，即内容扩充 Web 服务；然后配置系统以调用此外部 Web 服务。
  
    
    

外部内容扩充 Web 服务的实施依赖  [Microsoft.Office.Server.Search.ContentProcessingEnrichment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.ContentProcessingEnrichment.aspx) 命名空间下的接口。
## 用于内容扩充 Web 服务的 Windows PowerShell Cmdlet
<a name="SP15_PowerShell_Cmdlets_Content_Enrichment"> </a>

使用以下 Windows PowerShell cmdlet 配置并启用内容扩充功能：
  
    
    

-  [Get-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/zh-cn/library/jj219783%28office.15%29.aspx)
    
  
-  [Set-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/zh-cn/library/jj219659%28office.15%29.aspx)
    
  
-  [Remove-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/zh-cn/library/jj219742%28office.15%29.aspx)
    
  
-  [New-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/zh-cn/library/jj219502%28office.15%29.aspx)
    
  
这些 Windows PowerShell cmdlet 使管理员能够配置以下内容：
  
    
    

- 要发送给外部 Web 服务的一组自定义托管属性。
    
  
- 外部 Web 服务要返回的一组自定义托管属性。
    
  
- 表示要对所处理的每一项执行的谓词的触发条件。如果使用触发条件，则仅当触发器的计算结果为 **true** 时才调用外部 Web 服务。如果没有使用任何触发条件，则将所有项发送给外部 Web 服务。
    
  
- **FailureMode**，允许 Web 服务使无法在内容扩充步骤中处理的项失败或使这些项通过而不进行任何修改。如果项处理失败，则不对它们编制索引，并向 ULS 日志中写入一条警告消息。
    
  
- **DebugMode**，允许快速制作外部 Web 服务的原型。启用后，外部 Web 服务将接收所有可用的托管属性。在 **DebugMode** 中，将忽略触发条件，并且还忽略 Web 服务的任何托管属性输出。
    
  
- 以二进制形式发送项的原始数据的 **SendRawData** 开关。当所需元数据多于可从项的分析版本中检索到的数据时，这很有用。
    
  
此外，还存在用于指定大小限制和超时的选项。有关可配置属性的完整列表，请参阅 [使用内容扩充 Web 服务标注进行自定义内容处理](custom-content-processing-with-the-content-enrichment-web-service-callout.md)。
  
    
    

## 对 SharePoint Server 2013 使用内容扩充 Web 服务标注的先决条件
<a name="SP15ContentEnrich_prereq"> </a>

若要完成此操作方法，您必须在开发环境中安装以下各项：
  
    
    

- SharePoint 2013 中的搜索功能
    
  
- Visual Studio 2010 或类似的与 .NET Framework 兼容的开发工具
    
  
- 对安装的 SharePoint Server 2013 的管理员权限
    
  
- 可在其上使用 IIS 承载服务的服务器
    
  
您还必须知道如何在 IIS 中创建网站并向其中部署服务
  
    
    

## 设置内容扩充服务项目
<a name="SP15ContentEnrich_setup"> </a>

在此步骤中，您将创建服务实施项目，然后将所需引用添加到该项目中。
  
    
    

### 创建内容扩充服务项目


1. 在 Visual Studio 中，在菜单栏上选择"文件"、"新建"、"项目"。
    
  
2. 在"项目类型"中，在"Visual C#"下选择"WCF"。
    
  
3. 在"模板"下，选择"WCF 服务应用程序"。在"名称"字段中，键入"ContentProcessingEnrichmentService"，然后选择"确定"按钮。
    
  
4. 删除自动生成的 **Service1** 类和 **Service1** 接口。
    
  

### 将引用添加到内容扩充服务项目中


1. 在"项目"菜单上，选择"添加引用"。
    
  
2. 选择"浏览"并找到 SharePoint 安装文件夹中  _安装路径_\\Microsoft Office Servers\\15.0\\Search\\Applications\\External 下的 **Microsoft.Office.Server.Search.ContentProcessingEnrichment** 程序集。
    
    > **注释**
      > 如果 SharePoint 安装在非开发计算机的计算机上，请将该程序集复制到开发计算机中并从那里引用它。 

## 创建内容扩充服务
<a name="SP15ContentEnrich_createservice"> </a>

内容处理扩充服务必须实现  [Microsoft.Office.Server.Search.ContentProcessingEnrichment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.ContentProcessingEnrichment.aspx) 命名空间中的 **IContentProcessingEnrichmentService** 接口。本节中的代码示例是此接口的基本实现。
  
    
    
实现需要通过外部 Web 服务接收的每一项的两个托管属性： **Author** 和 **Filename**。 **Author** 是 **String** 对象的列表， **Filename** 是 **String** 对象。
  
    
    
 **IContentProcessingEnrichmentService** 实现将原始二进制数据写入磁盘上的临时位置，使用 **Filename** 作为文件名。然后，将新名称添加到作者列表中并返回到内容处理组件。
  
    
    

### 为内容扩充服务创建类文件


1. 在"项目"菜单上，选择"添加新项"。
    
  
2. 在"已安装的模板"中的"Visual C#"下，选择"Web"，然后选择"WCF 服务"。
    
  
3. 键入 **ContentProcessingEnrichmentService.svc**，然后选择"添加"。
    
  
4. 删除所创建的"IContentProcessingEnrichmentService.cs"接口。
    
  

### 修改 ContentProcessingEnrichmentService 类中的默认代码


1. 将类开头的现有 **using** 指令替换为以下 **using** 指令。
    
  ```cs
  
using System;
using System.Collections.Generic;
using System.IO;
using Microsoft.Office.Server.Search.ContentProcessingEnrichment;
using Microsoft.Office.Server.Search.ContentProcessingEnrichment.PropertyTypes;

  ```

2. 删除 **DoWork** 方法。
    
  

### 实现 IContentProcessingEnrichmentService 接口方法


1. 在类中添加以下代码来定义所需常量和成员。
    
  ```cs
  
// Defines the name of the managed property 'Filename'.
private const string FileNameProperty = "Filename";

// Defines the name of the managed property 'Author'
private const string AuthorProperty = "Author";

// Defines the temporary directory where binary data will be stored.
private const string TempDirectory = @"C:\\Temp";

// Defines the error code for managed properties with an unexpected type.
private const int UnexpectedType = 1;

// Defines the error code for encountering unexpected exceptions.
private const int UnexpectedError = 2;

private readonly ProcessedItem processedItemHolder = new ProcessedItem
{ 
   ItemProperties = new List<AbstractProperty>()
};
  ```

2. 为 **ProcessItem** 方法添加以下代码。
    
  ```cs
  
public ProcessedItem ProcessItem(Item item)
{
   processedItemHolder.ErrorCode = 0;
   processedItemHolder.ItemProperties.Clear();
   try
   {
      // Iterate over each property received and locate the two properties we
      // configured the system to send.
      foreach (var property in item.ItemProperties)
      {
         // Check if this is the author property.
         if (property.Name.Equals(AuthorProperty, StringComparison.Ordinal))
         {
            var author = property as Property<List<string>>;
            if (author == null)
            {
               // The author property was not of the expected type.
               // Update the error code and return. 
                  processedItemHolder.ErrorCode = UnexpectedType;
                  return processedItemHolder;
            }
               // Adding a new author to the list so it will become searchable.      
                  author.Value.Add("ExampleService");
                  processedItemHolder.ItemProperties.Add(author);
         }
         else if (property.Name.Equals(FileNameProperty, StringComparison.Ordinal))
         {
            var filename = property as Property<string>;
            if (filename == null)
            {
               // The file name property was not of the expected type.
               // Update error code and return.
                  processedItemHolder.ErrorCode = UnexpectedType;
                  return processedItemHolder;
            }
            if (!string.IsNullOrEmpty(filename.Value))
            {
               var fullFilePath = string.Join(char.ToString(Path.DirectorySeparatorChar), TempDirectory, filename.Value);
               if (item.RawData != null)
               {   
                  var outputFile = File.Create(fullFilePath);
                  using (var writer = new BinaryWriter(outputFile))
                  {
                     writer.Write(item.RawData);
                  }
               }
            }
         }
      }
   }
   catch (Exception)
   { 
      processedItemHolder.ErrorCode = UnexpectedError;
   } return processedItemHolder;
}
  ```

3. 修改 **web.config** 以接受最大大小为 8 MB 的消息，并将 **readerQuotas** 配置为足够大的值。
    
  
4. 在 **<system.serviceModel>** 中添加以下代码。
    
  ```XML
  
<bindings>
   <basicHttpBinding>
   <!-- The service will accept a maximum blob of 8 MB. -->
      <binding maxReceivedMessageSize = "8388608">
         <readerQuotas maxDepth="32"
          maxStringContentLength="2147483647"
          maxArrayLength="2147483647"   
          maxBytesPerRead="2147483647"   
          maxNameTableCharCount="2147483647" />  
             <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
  ```

生成项目并将它部署到 IIS 网站。
  
    
    

## 配置 SharePoint Server 2013
<a name="SP15ContentEnrich_configure"> </a>

打开 SharePoint Management Shell，然后输入以下 Windows PowerShell cmdlet 序列。
  
    
    

```

$ssa = Get-SPEnterpriseSearchServiceApplication
$config = New-SPEnterpriseSearchContentEnrichmentConfiguration
$config.Endpoint = http://Site_URL/ContentEnrichmentService.svc
$config.InputProperties = "Author", "Filename"
$config.OutputProperties = "Author"
$config.SendRawData = $True
$config.MaxRawDataSize = 8192
Set-SPEnterpriseSearchContentEnrichmentConfiguration -SearchApplication
$ssa -ContentEnrichmentConfiguration $config
```

Windows PowerShell cmdlet 序列帮助您首先使用  [New-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/zh-cn/library/jj219502%28office.15%29.aspx) cmdlet 创建配置对象。然后使配置对象指向您的服务实现；最好使用 `http://localhost:808` 作为 _Site_URL_。
  
    
    
将所处理的每一项的托管属性 **Author** 和 **Filename** 发送给您的服务。另外，您已通知 Web 服务客户端服务将输出单个托管属性 **Author**。除了托管属性外，Web 服务客户端还配置为发送项的原始数据并对数据大小施加限制。最后， [Set-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/zh-cn/library/jj219659%28office.15%29.aspx) cmdlet 用于存储整个配置。在此 cmdlet 返回后，配置将变为活动状态，爬网组件将对其下一个爬网过程使用此配置。
  
    
    
完成此操作后，您可以开始对网站进行完全爬网。如果服务正确运行，则您应该能够监视承载网站的服务器上的临时文件夹中写入磁盘的文档。
  
    
    
以后可以使用以下 Windows PowerShell cmdlet 来移除配置。
  
    
    



```

Remove-SPEnterpriseSearchContentEnrichmentConfiguration -SearchApplication $ssa
```


## 其他资源
<a name="SP15ContentEnrich_addresources"> </a>


-  [启动、暂停、继续或停止爬网](http://technet.microsoft.com/zh-cn/library/jj219814%28office.15%29.aspx)
    
  
-  [配置 SharePoint 2013 中的搜索功能](configure-search-in-sharepoint-2013.md)
    
  
-  [使用内容扩充 Web 服务标注进行自定义内容处理](custom-content-processing-with-the-content-enrichment-web-service-callout.md)
    
  

