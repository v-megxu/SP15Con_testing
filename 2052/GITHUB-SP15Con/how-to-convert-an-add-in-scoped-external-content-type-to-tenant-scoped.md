---
title: 如何：将外接程序范围的外部内容类型转换为租户范围
ms.prod: SHAREPOINT
ms.assetid: 35c5d670-e402-4641-b3c5-6f61ae1ec69b
---


# 如何：将外接程序范围的外部内容类型转换为租户范围
了解如何使用 Visual Studio 2012 自动生成工具来创建基于 OData 的外部内容类型，并将其导入到 Business Connectivity Services (BCS) 元数据存储区，以便在整个租户工作区中都能使用它。
BDC 模型是外部数据源的复杂 XML 定义。定义 BCS 的外部内容类型时会使用这些定义。它们很难通过手动方式构建，因此，我们使用 Visual Studio 2008 和 Visual Studio 2012 Office 开发人员工具构建了一些能够自动生成这些文件的工具。有了这些工具，您就可以使用 Visual Studio 发布创建一个 .app 包，然后打开该包来提取模型文件。
  
    
    


## 从 Visual Studio 外接程序包中提取 BDC 模型文件

下列步骤显示了如何创建基于 OData 的外部内容类型，然后将其导入到 BCS 元数据存储区，以便在整个租户工作区中使用它。
  
    
    

### 从 OData 源中创建一个 BDC 模型文件


1. 在 Visual Studio 2008 中，创建一个"SharePoint 2013 外接程序"项目。
    
  
2. 指定外接程序设置，包括外接程序名称、调试外接程序的网站 URL 以及您要如何托管外接程序（"自动托管"、"提供程序托管"或"SharePoint 托管"）。有关详细信息，请参阅  [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)。
    
  
3. 选择"完成"来创建应用程序。
    
  
4. 在"解决方案资源管理器"中，打开项目的快捷菜单并选择"添加"、"外部数据源的内容类型"。
    
    这将启动一个向导，它可帮助您查找所选数据源并创建 BDC 模型。
    
  
5. 在"设置 OData 源"页上，输入要连接到的 OData 服务的 URL。URL 应类似于： `http://services.odata.org/Northwind/Northwind.svc/`。
    
    为您的 OData 源指定名称。
    
    > **注释**
      > 对于此示例，您将使用罗斯文服务，该服务可从位于 [开放式数据协议网站](http://www.odata.org)上的创建器列表中获取。 
6. 将出现一个列表，它显示 OData 服务公开的数据实体。选择其中一个或多个实体，然后选择"完成"。
    
  

### 将外接程序范围的外部内容类型部署为一个外接程序包


1. 在 Visual Studio 中的"生成"菜单上，选择"发布"。
    
  
2. 对该包命名，在您的本地硬盘驱动器上指定保存位置，然后选择"完成"。
    
  

### 从 .app 包中提取模型文件


1. 打开创建 .app 包所在的文件夹。
    
  
2.  将文件名称扩展名从.app 更改为.zip。
    
  
3. 将 ZIP 包解压到本地文件夹中。
    
  
4. 打开解压缩的文件夹，找到 WSP 文件。
    
  
5. 将 WSP 文件移动到另一个位置。
    
  
6. 将这个文件上的 .wsp 文件扩展名更改为 .cab。
    
  
7. 打开这个 .cab 文件，您就会找到 Bdcmodel.bdcm 文件。
    
  
8. 将该 Bdcmodel.bdcm 文件保存到另一个位置。
    
  

### 使用 SharePoint 管理中心页面导入模型文件


1. 打开 SharePoint Online 或 SharePoint 2013 本地管理中心页面。
    
  
2. 选择"管理服务应用程序"。
    
  
3. 选择"Business Data Connectivity Service"。
    
  
4. 选择服务器功能区上的"导入"链接。
    
  
5. 选择"浏览"按钮，指定您提取 .bdcm 文件所在的位置。
    
  
6. 保持默认设置，然后选择"导入"。
    
  

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建外接程序范围的外部内容类型](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [开放式数据协议](http://www.odata.org)（http://www.odata.org）
    
  

  
    
    

