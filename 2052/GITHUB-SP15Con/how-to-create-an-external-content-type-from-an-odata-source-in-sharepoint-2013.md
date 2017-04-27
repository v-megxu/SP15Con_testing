---
title: 如何：在 SharePoint 2013 中从 OData 源创建外部内容类型
ms.prod: SHAREPOINT
ms.assetid: bc60ea49-c44e-4531-af62-06b8cf77d35d
---


# 如何：在 SharePoint 2013 中从 OData 源创建外部内容类型
学习如何使用 Visual Studio 2008 来发现已发布的 OData 源和创建可在 SharePoint 2013 的 Business Connectivity Services (BCS) 中使用的可重用外部内容类型。
## 创建基于 OData 的外部内容类型的先决条件
<a name="bkmk_Prerequisites"> </a>

要从开放数据协议 (OData) 源创建外部内容类型，您将需要以下内容：
  
    
    

- SharePoint 2013 实例
    
  
- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
- 可通过 Internet 获取的已发布 OData 服务。
    
  
有关如何设置您 SharePoint 开发环境的信息，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

> **注释**
> SharePoint Designer 2013 不能用于根据 OData 源自动生成 BDC 模型。您可以改用 Visual Studio 2008。 
  
    
    


### 使用 OData 外部内容类型的核心概念

下文提供有关 SharePoint 2013 中 OData 和 OData 连接器的背景信息。
  
    
    

**表 1. OData 外部内容类型的核心概念**


|**文章标题**|**描述**|
|:-----|:-----|
| [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |基于 OData 源创建外部内容类型入门，以及学习如何在 SharePoint 或 Office 组件中使用该数据。  <br/> |
| [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md) <br/> |了解 BCS 外部内容类型以及开始在 SharePoint 2013 中创建外部内容类型所需的内容。  <br/> |
   

## 创建基于 OData 的外部内容类型
<a name="bkmk_CreatingODataECT"> </a>

以下步骤显示如何使用 Visual Studio 2008 来创建基于 OData 源的外部内容类型。
  
    
    

### 创建新 SharePoint 外接程序 的步骤


1. 在 Visual Studio 2008 中，创建新的 **SharePoint 2013 应用程序**项目，位于"SharePoint 2013 模板"节点下。
    
  
2. 对项目命名，然后选择"确定"。
    
  
3. 要指定 SharePoint 设置，请输入您应用程序的名称以及您将根据其进行调试的 SharePoint 2013 服务器的 URL。
    
  
4. 选择"完成" 。
    
  
创建项目后，对 OData 源使用新的自动生成工具，并将 OData 源的 BDC 模型添加到应用程序。
  
    
    

### 添加新 BDC 模型的步骤


1. 在"解决方案资源管理器"中，打开项目的快捷菜单，然后依次选择"添加"、"外部数据源的内容类型"。
    
    这将启动一个向导，以帮助您发现选定的数据源和创建 BDC 模型。
    
  
2. 向导的第一页用于收集数据服务的 URL。在"指定 OData 源"页上，输入要连接到的 OData 服务的 URL。URL 的格式应类似于： `http://services.odata.org/Northwind/Northwind.svc/`。
    
    > **注释**
      > 您将显示罗斯文服务，该服务可从 [开放式数据协议网站](http://www.odata.org/ecosystem#liveservices)上找到的创建器列表中获取。 
3. 为您的 OData 源选择一个名称，然后选择"下一步"。
    
  
4. 数据实体列表在 OData 服务出现时暴露。请选择其中一个或多个实体，然后选择"完成"。
    
  

### 查看实体结构的步骤


- 请注意，Visual Studio 创建了一个名为 External Content Types 的新文件夹。在该文件夹中，您将找到具有您的新数据源名称的子文件夹。如果您进一步展开此文件夹，您将看到代表您所选实体的项。若要查看实体及其类型的图形列表，请打开要查看的 **ect** 文件。
    
    您还可以通过在 XML 编辑器中打开 ect 文件查看实体的 XML。
    
  

## 使用 OData 源的流访问器
<a name="bkmk_UseStreamAccessor"> </a>

使用以下代码，您即可以访问 OData 连接器可以使用的数据流。
  
    
    

```cs

/*Invoke  Stream Accessor Method */
        internal void ExecuteStreamAccessorMethod(IEntityInstance entityInstance, string streamAccessorName)
        {
            this.Log.Comment("ExecuteStreamAccessorMethod enter");
            this.Log.Comment("streamAccesor method" + streamAccessorName);
            IStreamableField isf = entityInstance.GetStreamableField(streamAccessorName);
            Stream resStream = isf.GetData();
            using (BinaryReader reader = new BinaryReader(resStream))
            {
                using (FileStream fs = File.Create(@"C:\\" + entityInstance.GetIdentity().GetIdentifierValues()[0] + ".jpg"))
                {
                    int bytesRead = 0;
                    do
                    {
                        int nrBytes = 80 * 1000 * 1000;
                        byte[] streamData = new byte[nrBytes];
                        bytesRead = reader.Read(streamData, 0, nrBytes);
                        this.Log.Comment("Total Bytes Read - " + bytesRead);
                        if (bytesRead > 0)
                        {
                            fs.Write(streamData, 0, bytesRead);
                        }
                    } while (bytesRead > 0);
                }
            }
            isf.Dispose();
            this.Log.Comment("ExecuteStreamAccessorMethod Exit" );
        }
```


## 后续步骤
<a name="bkmk_Next"> </a>

构建外部内容类型后，您可以通过使用内置对象（外部列表、业务数据 Web 部件或自定义代码）将其用于显示 SharePoint 的内部数据。
  
    
    
有关详细信息，请参阅 [如何：在 SharePoint 2013 中使用 OData 数据源创建外部列表](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md).
  
    
    

## 其他资源
<a name="bkmk_Addres"> </a>


-  [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  

