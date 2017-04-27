---
title: SharePoint 2013 中外接程序范围的外部内容类型
ms.prod: SHAREPOINT
ms.assetid: a34cbbba-dc38-4d3d-b796-d54b5848bdfb
---


# SharePoint 2013 中外接程序范围的外部内容类型
了解安装在或范围限定在 SharePoint 2013 中的外接程序级别并使您能够使用外部数据源创建数据丰富的 SharePoint 外接程序的外部内容类型。
## SharePoint 2013 中外接程序范围的外部内容类型概述
<a name="Appscopedect_overview"> </a>

在 SharePoint 2010 中，您只能在服务器场级别安装并使用外部内容类型。这通常会给开发人员带来问题，因为即使对于简单的应用程序，管理员也必须参与，因为在服务器场级别安装需要访问权限。
  
    
    
在 SharePoint 2013 中，应用程序基本上被隔离到称为"外接程序"的自治程度更高的单元中。外接程序包含其运行所需的所有资源。此方法使运行的应用程序能够独立于其他应用程序。此体系结构的好处如下：
  
    
    

- 您可以创建符合 SharePoint 2013 的新应用程序模型的外接程序。
    
  
- 您可以创建访问来自 SAP、Netflix 和所有者的外部数据以及其他类型的数据的外接程序，而无需租户管理员参与。
    
  
- 通过 Business Connectivity Services (BCS) 维护对外部应用程序的访问，它提供了可供其他 SharePoint 应用程序使用的一致且统一的接口。
    
  
外接程序范围的外部内容类型在应用程序中提供了对外部数据的访问。
  
    
    

## 使用外接程序范围的外部内容类型的先决条件
<a name="Appscopedect_Prereq"> </a>

以下是开发范围限定在外接程序级别的外部内容类型的要求：
  
    
    

- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
- SharePoint 2013
    
  
有关设置 SharePoint 开发环境的信息，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

### 外接程序范围的外部内容类型要点

表 1 包含您在使用外接程序范围的外部内容类型时应熟悉的一些核心概念。
  
    
    

**表 1. 用于了解外接程序范围的外部内容类型的核心概念**


|**文章**|**说明**|
|:-----|:-----|
| [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md) <br/> |了解如何创建 BCS 外部内容类型。  <br/> |
| [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |了解 SharePoint 2013 中的新外接程序模型，您可以使用它创建外接程序，即面向最终用户的小巧、易用的解决方案。  <br/> |
| [开始创建 SharePoint 承载的 SharePoint 外接程序](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx) <br/> |了解如何通过使用 Visual Studio 2012 Office 开发人员工具来创建基本的 SharePoint 托管的外接程序。  <br/> |
   

## 使用外接程序范围的外部内容类型可以做什么？
<a name="Appscopedect_Tasks"> </a>

添加外接程序范围的外部内容类型的主要原因是提供对来自单个外接程序的外部数据的访问。这允许您执行以下操作： 
  
    
    

- 将对外部内容类型的访问限制为特定应用程序。
    
  
- 将外部内容类型部署在应用程序中。
    
  

### 创建外接程序范围的外部内容类型
<a name="Appscopedect_createect"> </a>

SharePoint 2010 中引入了基于文件的元数据目录的概念。它使您能够指定包含定义外部内容类型所需的 XML 的文件。此文件可部署在 WSP 包中，并仅与它的范围所限定在的应用程序相关。通过使用此元数据文件，可将外部内容类型限制为外接程序级别。
  
    
    
在 SharePoint 2013 中， **SPListDataSource** 经修改添加了指示应用程序范围的属性。
  
    
    
该类充当 **SPList** 和外部列表之间的桥梁。使用相关 **SPList** 可检索实体域和数据。从 **HasExternalDataSource** 属性中可检索 **SPListDataSource** 实例。如果 **HasExternalDataSource** 不为空，则 **SPList** 对象的数据是 SharePoint 2013 的外部数据。
  
    
    
当您希望添加外接程序范围的外部内容类型时，此属性将设置为 **Add-in**。
  
    
    
 **MetadataCatalogFileName** 属性用于定义包含外部内容类型定义的 BDC 模型文件。此属性可以通过声明方式或编程方式进行定义，但不在 SharePoint 用户界面 (UI) 中。
  
    
    
下面的示例演示如何以声明方式设置 **MetadataCatalogFileName** 属性。
  
    
    



```XML

<DataSource>
  <Property Name="Entity" Value="Customer" />
  <Property Name="EntityNamespace" Value="SAP" />
  <Property Name="LobSystemInstanceName" Value="SAPClient1" />
  <Property Name="SpecificFinder" Value="ReadCustomer" />
  <Property Name=" MetadataCatalogFileName" Value="BDCMetadata.bdcm" />
</DataSource>
```


> **注释**
> 网站管理员可以安装使用应用程序范围内 ECT 的外接程序，但只有 SiteCollection 管理员可以授予应用程序使用 BCS 连接的权限。 
  
    
    


### 将外接程序范围的外部内容类型部署在 WSP 文件中的自定义功能中
<a name="Appscopedect_deployect"> </a>

您可以将 BDC 模型包括在 WSP 文件中以进行部署。下面的示例演示如何将 BDC 模型包括在应用程序中。
  
    
    

```XML

<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <BdcModel Path="BDCMetadata.bdcm">
  </BdcModel>
</Elements>

```


> **重要信息**
> 每个外接程序只能包括一个 BDC 模型文件。虽然此示例中的文件名为 BDCMetadata.bdcm，但模型文件实际上可以是您选择的任何名称，只要该文件名与 BDC 模型文件的 **Path** 属性中的文件名匹配即可。
  
    
    


> **注释**
> 外接程序范围的外部内容类型仅允许开放式数据协议 (OData) 连接。 
  
    
    


### 为外部系统设置安全凭据
<a name="Appscopedect_deployect"> </a>

为了访问安全的外部系统上的数据，必须使用适当的凭据配置 BDC 模型。
  
    
    
下面的示例演示如何通过修改应用程序的 Elements.xml 文件，为外接程序范围的外部内容类型中的外部系统设置安全凭据。
  
    
    



```XML

<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <BdcModel Path="BDCMetadata.bdcm">
    <LobSystem Name="SAP">
       <LobSystemInstance Name="SAPInst" RequireCredentials="true" CredentialsDescription="Credentials to connect to SAP"/>
    </LobSystem>
    <LobSystem Name="SQL">
       <LobSystemInstance Name="App Database" DataSource="SQL-Azure" RequireCredentials="true" />
    </LobSystem>
  </BdcModel>
</Elements>

```


## 本节内容
<a name="Appscopedect_inthissection"> </a>


-  [如何：在 SharePoint 2013 中创建外接程序范围的外部内容类型](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中使用 REST 访问外部数据](how-to-access-external-data-with-rest-in-sharepoint-2013.md)
    
  

## 其他资源
<a name="Appscopedect_Addres"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的 Business Connectivity Services 程序员参考](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的外部事件和警告](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

