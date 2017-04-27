---
title: 如何：在 SharePoint 2013 中使用 OData 数据源创建外部列表
ms.prod: SHAREPOINT
ms.assetid: 601fbfce-a0c6-43dd-8398-540d094c083c
---


# 如何：在 SharePoint 2013 中使用 OData 数据源创建外部列表
了解如何以编程方式创建外部列表，以及如何将其绑定到 SharePoint 2013 中基于 OData 的外部内容类型。
虽然高级用户或 SharePoint 管理员将可能使用 SharePoint Designer 2013 创建外部列表，但开发人员将对使用其专业工具 Visual Studio 2008 和 Visual Studio 2012 Office 开发人员工具创建外部列表的能力感兴趣。这样，他们可以更灵活地添加功能和将包括用于稍后部署的 Business Connectivity Services (BCS) 功能的解决方案打包到一个或多个主机环境中。
  
    
    


## 创建外部列表的先决条件
<a name="bkmk_Prereqs"> </a>

从 OData 源创建外部列表需要下面的组件：
  
    
    

- Visual Studio 2008
    
  
- SharePoint 2013
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
- 基于 OData 源的已发布外部内容类型：有关说明，请参阅 [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)。
    
  
有关设置 SharePoint 开发环境的信息，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

### 创建外部列表的核心概念

下面的文章提供有关 SharePoint 外接程序信息和创建外部列表的其他背景信息。
  
    
    

**表 1. 外部列表的核心概念**


|**文章标题**|**说明**|
|:-----|:-----|
| [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |了解 Business Connectivity Services 以及如何在 SharePoint 2013 中公开外部数据。  <br/> |
| [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |了解 SharePoint 2013 中的新应用程序模型，利用该模型，可以为最终用户创建易于使用的小解决方案。  <br/> |
| [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx) <br/> |了解可承载 SharePoint 外接程序的不同方法。  <br/> |
   

## 新建一个外部列表
<a name="bkmk_CreateNewVList"> </a>

以下过程演示如何新建外部列表、如何将其绑定到基于 OData 的外部内容类型，以及如何使用 Visual Studio 2008 发布到 SharePoint 2013。
  
    
    

> **注释**
> 第一个步骤假设已成功创建外部内容类型，如 [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)中所述。 
  
    
    


### 自动添加外部列表


1. 如果您只是希望向您的项目中添加反映您的外部内容类型中包含的内容的简单列表，则可使用 Visual Studio 2008 自动生成工具。该列表在创建外部内容类型时创建。在您选中自动生成过程的第二个步骤（"选择数据实体"步骤）中出现的"为所选数据实体创建列表实例(服务操作除外)"复选框时，向导将为您选择的每个实体创建 XML 声明并添加新外部内容类型。
    
  
2. 按 F5 可部署项目，此外，还可部署新列表。
    
  
出于测试目的，您可能想要修改 AppManifest.xml 文件，以便应用程序的起始页是您刚才创建的列表。 
  
    
    

### 修改 AppManifest.xml 文件


1. 使用 XML 编辑器打开 AppManifest.xml 文件。
    
  
2. 查找 <StartPage> 标记。
    
  
3. 将该值更改为  `~appWebUrl/Lists/Employees`。
    
  
4. 保存所做的更改。
    
  

### 发布项目


- 按 F5 部署项目和外部列表。 
    
    打开 Web 浏览器并导航到您新建的列表。
    
  

## 其他资源
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [如何：创建基本的 SharePoint 自动承载相关应用程序](http://msdn.microsoft.com/library/0572894d-c437-4b7d-8ac6-8405496e2145%28Office.15%29.aspx)
    
  
-  [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

