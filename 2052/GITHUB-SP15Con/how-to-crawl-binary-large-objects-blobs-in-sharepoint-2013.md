---
title: 如何：在 SharePoint 2013 中对二进制大型对象 (BLOB) 进行爬网
ms.prod: SHAREPOINT
ms.assetid: 99b3dd51-1651-4300-a2de-33681f4cc258
---


# 如何：在 SharePoint 2013 中对二进制大型对象 (BLOB) 进行爬网
了解如何修改数据库 BCS 索引连接器的 BDC 模型文件，以启用 SharePoint 2013 中的搜索功能爬网程序对存储在 SQL Server 数据库中的二进制大型对象 (BLOB) 进行爬网。
## 对 BLOB 数据进行爬网
<a name="HowToCrawlBlobs_CrawlingBlobData"> </a>

Business Data Connectivity (BDC) 服务 支持读取 BLOB 数据类型，这对于从外部系统流式传输 BLOB 数据非常有用。为此，您需要确保包含外部数据的数据库设置为支持读取该数据类型。然后将 **StreamAccessor** 方法添加到外部内容源的 BCS 索引连接器的 BDC 模型文件。
  
    
    

## 为 BLOB 数据配置 SQL Server 数据库表
<a name="HowToCrawlBlobs_ConfiguringSQL"> </a>

Microsoft SQL Server 数据库表必须具有一列，用于指定 BLOB 数据的扩展名或 MIME 类型。如果数据库表架构不具有包含此信息的列，则必须将此列添加到架构中。下表包含一个具有此列的数据库表架构示例以及存储在该数据库表中的此列的示例值。
  
    
    

**表 1. 示例数据库表架构**


|**列名称**|**数据类型**|
|:-----|:-----|
|Id  <br/> |Int  <br/> |
|DisplayName  <br/> |nvarchar(50)  <br/> |
|扩展名  <br/> |nvarchar(50)  <br/> |
|数据  <br/> |varbinary(MAX)  <br/> |
|ContentType  <br/> |nvarchar(MAX)  <br/> |
   

**表 2. 示例数据库表值**


|**Id**|**显示名称**|**扩展名**|**数据**|**Content Type**|
|:-----|:-----|:-----|:-----|:-----|
|1  <br/> |文件1  <br/> |.docx  <br/> |0x504B…  <br/> |application/vnd.openxmlformats-officedocument.wordprocessingml.document  <br/> |
|2  <br/> |文件2  <br/> |.doc  <br/> |0xD…  <br/> |application/msword  <br/> |
|3  <br/> |文件3  <br/> |.txt  <br/> |OxE…  <br/> |text/plain  <br/> |
   

## 修改 BDC 模型文件，以便对 BLOB 数据进行爬网
<a name="HowToCrawlBlobs_BDCModelFile"> </a>

在您确认数据库表包含 BLOB 数据的扩展名或 MIME 类型信息之后，可使用 Microsoft SharePoint Designer 创建基于包含 BLOB 数据的表的外部内容类型。然后，您可以创建所有操作。有关详细信息，请参阅 [如何：创建外部内容类型](http://msdn.microsoft.com/library/811b458c-e209-46df-ba02-8db02bc658db%28Office.15%29.aspx)和 [如何：基于 SQL Server 表创建外部内容类型](http://msdn.microsoft.com/library/5c42a679-d71d-46c6-aabc-d63c6cad3846%28Office.15%29.aspx)。 
  
    
    
创建 BLOB 外部内容类型后，您即可修改 BDC 模型文件以启用爬网。您无法在 SharePoint Designer 中进行这些修改。因此，您必须导出 BDC 模型文件，并使用 XML 编辑器手动进行这些修改。
  
    
    

### 导出 BLOB 外部内容类型的 BDC 模型文件


1. 在 SharePoint Designer 中，单击左侧导航中的"外部内容类型"，以显示该网站的服务应用程序的 BDC 元数据存储中定义的外部内容类型。
    
  
2. 在"外部内容类型"列表中，选择"BLOB"外部内容类型。然后单击服务器功能区上的"导出 BDC 模型"。
    
  
3. 在"BDC 模型名称"文本框中键入一个名称，然后单击"确定"。
    
  
4. 选择您希望保存 BDC 模型 (.bdcm) 文件的位置，然后单击"保存"。
    
  

### 启用对 BLOB 外部内容类型的爬网


1. 在 XML 编辑器中，打开您在上一节中创建的 BDC 模型文件。
    
  
2. 创建一个可返回 BLOB 字段的新方法。您应为此方法定义一个 **StreamAccessor** 类型方法实例，如下面的示例所示。
    
    > **注释**
      > 此示例中的表名称为"Attachment"。 

  ```XML
  
<Method Name="GetData">
  <Properties>
    <Property Name="RdbCommandText" Type="System.String">SELECT Data FROM [dbo].[Attachment] WHERE [Id] = @Id </Property>
    <Property Name="RdbCommandType" Type="System.Data.CommandType, System.Data, Version=2.0.0.0, Culture=neutral, 
      PublicKeyToken=b77a5c561934e089">Text</Property>
  </Properties>
  <Parameters>
    <Parameter Direction="In" Name="@Id">
      <TypeDescriptor TypeName="System.Int32" IdentifierName="Id" Name="Id" />
    </Parameter>
    <Parameter Name="StreamData" Direction="Return">
      <TypeDescriptor TypeName="System.Data.IDataReader, System.Data, 
        Version=2.0.3600.0, Culture=neutral, 
        PublicKeyToken=b77a5c561934e089" 
        IsCollection="true" Name="DataReaderTypeDescriptorName">
        <TypeDescriptors>
          <TypeDescriptor TypeName="System.Data.IDataRecord, System.Data, 
            Version=2.0.3600.0, 
            Culture=neutral, 
            PublicKeyToken=b77a5c561934e089" 
            Name="DataRecordTypeDescriptorName">
            <TypeDescriptors>
              <TypeDescriptor TypeName="System.Data.SqlTypes.SqlBytes, System.Data, 
                Version=2.0.3600.0, 
                Culture=neutral, 
                PublicKeyToken=b77a5c561934e089" Name="Data" />
            </TypeDescriptors>
          </TypeDescriptor>
        </TypeDescriptors>
      </TypeDescriptor>
     </Parameter>
    </Parameters>
  <MethodInstances>
    <MethodInstance Name="DataAccessor" 
      Type="StreamAccessor" 
      ReturnParameterName="StreamData" 
      ReturnTypeDescriptorName="Data">
      <Properties>
<!-- If extension field is available-->
        <Property Name="Extension" Type="System.String">Extension</Property>
<!--If MimeType is available-->
        <Property Name="ContentType" Type="System.String">ContentType</Property>
<!--If attachments is to be displayed in profile pages, add the following property-->
        <Property Name="MimeTypeField" Type="System.String">ContentType</Property>
      </Properties>
    </MethodInstance>
  </MethodInstances>
</Method>
  ```


    如果所有 BLOB 的 MIME 类型都是相同的，则可以将上一示例中的代码行 
  
    
    
 `<Property Name="ContentType" Type="System.String">ContentType</Property>`
  
    
    
 替换为下面的代码行：
  
    
    
 `<Property Name=" ContentType " Type="System.String">application/vnd.openxmlformats-officedocument.wordprocessingml.document</Property>`
    
  
3. 使用 Business Connectivity Services 服务应用程序管理用户界面重新导入模型文件。 
    
  
4. 为外部内容类型创建内容源。
    
  
5. 对内容源启动完全爬网。 
    
  

## 其他资源
<a name="SP15Crawlblobs_addlresources"> </a>


-  [SharePoint 2013 中的搜索连接器框架](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [如何：创建外部内容类型](http://msdn.microsoft.com/library/811b458c-e209-46df-ba02-8db02bc658db%28Office.15%29.aspx)
    
  
-  [XML 代码段：为 StreamAccessor 方法建模](http://msdn.microsoft.com/library/bd60cc2e-f7f6-421c-9d2a-60e8512b9893%28Office.15%29.aspx)
    
  

