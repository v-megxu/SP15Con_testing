---
title: 为 SharePoint 创建混合连接应用程序
ms.prod: SHAREPOINT
ms.assetid: 311f036e-3442-4497-b35e-442b665462d3
---


# 为 SharePoint 创建混合连接应用程序
了解为 SharePoint 2013 混合连接解决方案开发和部署应用程序的过程。
## SharePoint 2013 和 SharePoint Online 中的混合连接
<a name="bk_hybridconnectivity"> </a>

随着企业开始使用 SharePoint Online，它们需要一种能够安全公开大量专有数据的方法。为了帮助应对这一挑战，SharePoint 2013 引入了混合连接。
  
    
    
Business Connectivity Services (BCS) 混合连接功能可使 SharePoint 2013 使用企业防火墙内部位于本地并受到多种身份验证形式保护的数据。使用混合连接功能，SharePoint Online 可以通过 Web 安全地访问此数据，就如同数据位于同一内部网络一样。一旦配置了混合连接，用户就可以使用在企业基础架构内部受保护的数据。他们可以根据自己在 SharePoint 2013 中获得的权限访问和操作数据。
  
    
    
有关如何配置有效混合解决方案的完整说明，请参阅  [SharePoint Server 2013 的混合](http://technet.microsoft.com/zh-cn/library/jj838715.aspx)。本文章系列将引导您了解配置数据源、反向代理、搜索、安全、网络以及对其他建立端到端方案所需一切的所有要求。
  
    
    

> **警告**
> 若要配置混合 SharePoint 环境，您需要将专业技能和重要实践经验与 SharePoint Server 2013、SharePoint Online 以及相关产品和技术相结合。在设计和部署混合环境时，我们建议您通过 Microsoft 咨询服务获得技术指导和支持。 > 有关详细信息，请参阅  [Microsoft 服务](http://www.microsoft.com/zh-cn/microsoftservices/deploy.aspx)。 
  
    
    

为了让您能够通过 BCS 和混合连接创建一个可以使用内部数据源数据的应用程序，本文假定您已经按照程序配置了您的混合环境。
  
    
    

## 创建混合连接应用程序
<a name="bkmk_CreatingHybridConnectivityApps"> </a>

创建一个混合 SharePoint 外接程序与创建任何 SharePoint 外接程序在本质上是相同的。
  
    
    
按照这些步骤创建一个混合应用程序：
  
    
    

-  [准备数据源](#bkmk_PrepareDataSource)
    
  
-  [创建一个 SharePoint 外接程序](#bkmk_CreateAnApp)
    
  
-  [创建一个外部内容类型](#bkmk_CreateECT)
    
  
-  [部署混合应用程序](#bkmk_DeployHybridApp)
    
  

### 准备数据源
<a name="bkmk_PrepareDataSource"> </a>

大部分时候，数据源已就位并在为任意数量的业务应用程序提供服务。但是，数据可能只能在企业安全基础架构内部提供。如果您的数据位于企业防火墙内部的服务器上，或者通过其他一些方式保护，则下一步就要将数据显示给同样位于防火墙内部的 BCS。将一个网络设备配置为将来自 SharePoint Online 的调用转换到内部 SharePoint 场。此设备被称为"反向代理"，它允许云中的 SharePoint 外接程序调用防火墙内部的 BCS。BCS 就在那里处理所有的数据连接。
  
    
    
为使此数据对 BCS 可用，您需要将它公开为一个 OData 源。为此，创建一个可承载服务并允许 BCS 通过 OData 和代表性状态传输 (REST) 端点与该数据源通信的 Internet Information Services (IIS) 网站。
  
    
    
要创建一个 OData 端点，您需要按照下列步骤创建 Windows Communication Foundation (WCF) 数据服务。
  
    
    

### 创建一个 WCF 数据服务


1. 创建一个至少能运行 Microsoft .NET Framework 4 的 IIS 网站。使用基本身份验证来保证此网站的安全。
    
    > **注释**
      > 不必将 SharePoint 安装在此服务器上。事实上，为了实现简单和高效，最好不要将 SharePoint 安装在承载 WCF 数据服务的服务器上。 
2. 在 Visual Studio 2008 中使用"ASP.NET 空 Web 应用程序"模板新建一个项目。
    
  
3. 在"解决方案资源管理器"中添加一个新的"ADO.NET 实体数据模型"。
    
  
4. 选择"实体数据模型向导"中的"从数据库生成"选项。
    
  
5. 选择现有的连接，或新建一个连接。
    
  
6. 提供 URL 和连接安全信息。
    
  
7. 选择要包括在模型中的项目，并选择"完成"。
    
  
8. 再次在"解决方案资源管理器"中使用 Visual Studio 模板添加一个新的"WCF 数据服务"。
    
  
9. 对数据服务命名，并选择"下一步"。
    
    此时，会创建实体模型，而且刚刚生成的类将包括在您的项目中。
    
  
10. 使用刚刚创建的实体模型类名替换  `/* TODO: put your data source class name here */`，并指定您要授予权限的那些实体，以此设置所创建实体的安全性。
    
  
有关如何设置的完整教程，请参见以下内容： 
  
    
    

-  [OData 入门第 1 部分：构建一个 OData 服务](http://msdn.microsoft.com/zh-cn/data/gg601462)
    
  
-  [快速入门（WCF 数据服务）](http://msdn.microsoft.com/zh-cn/library/cc668796.aspx)
    
  

### 创建一个 SharePoint 外接程序
<a name="bkmk_CreateAnApp"> </a>

在这里，我们做出的一个假设是您正在企业防火墙内部开发您的应用程序。这代表着这样一个场景：在某公司工作的开发人员有一台处于安全基础架构保护之下的计算机，它一直开发和测试应用程序，直到做好部署的准备为止。这简化了连接 Visual Studio 中数据源的过程，并使用 Visual Studio 2013 Office 开发人员工具 在下一步中自动生成外部内容类型。
  
    
    

### 新建一个应用程序


1. 在安装有 Visual Studio 2013 Office 开发人员工具 和 SharePoint 2013 的开发计算机上打开 Visual Studio 2008。
    
  
2. 新建 SharePoint 相关应用程序。
    
  
3. 指定应用程序的名称、要承载用于测试的网站的本地 SharePoint URL，以及希望承载应用程序的方式。选择"完成"。
    
  

### 创建一个外部内容类型
<a name="bkmk_CreateECT"> </a>

要将 BDC 模型或外部内容类型添加到您的项目中，请执行以下操作。
  
    
    

### 添加外部内容类型的步骤


1. 在您的新项目仍处于打开状态的情况下，打开解决方案的快捷菜单，选择"添加"、"用于外部数据源的内容类型" 。
    
  
2. 向导的第一个页面用来指定数据服务的 URL。在"指定 OData 源"页上，输入要连接的 OData 服务的 URL。URL 应类似于： **http://services.odata.org/Northwind/Northwind.svc/** 。
    
  
3. 为您的 OData 源选择一个名称，然后选择"下一步"。
    
  
4. 将出现一个由 OData 服务公开的数据实体列表。请确保选中"创建所选数据实体的列表实例"复选框。 
    
  
5. 选择其中一个或多个实体，然后选择"完成"。
    
  
6. 在部署之前，您需要执行的最后一项操作是修改新建的外部内容类型文件中的 URL。
    
    在 XML 编辑器中打开 .ect 文件。
    
  
7. 修改  `ODataServiceMetadataUrl` 属性，指向允许通过反向代理访问的 URL。
    
  
8. 使用允许通过反向代理访问的 URL 修改  `ODataServiceUrl` 属性。
    
  
有关如何添加基于 OData 的外部内容类型的信息，请参阅 [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)。
  
    
    

### 部署混合应用程序
<a name="bkmk_DeployHybridApp"> </a>

当开始要部署应用程序时，您有一些选择。您可以使用 F5 部署将其直接部署到租赁，也可以使用 Visual Studio 的发布功能将其打包以创建一个 .app 文件。可将此文件提供给 SharePoint Online 租户管理员并将其上载。
  
    
    
有关部署 SharePoint 外接程序的详细信息，请参阅以下资源： 
  
    
    

-  [部署和安装SharePoint 外接程序：方法和选项](http://msdn.microsoft.com/library/d15a74a7-3c10-485a-9885-7ef11aaa0d90%28Office.15%29.aspx)
    
  
-  [使用 Visual Studio 发布 SharePoint 外接程序](http://msdn.microsoft.com/library/8137d0fa-52e2-4771-8639-60af80f693bb%28Office.15%29.aspx)
    
  
您还可以采用为外部内容类型创建的 BDCM 文件，并提取用于应用程序之上各级别的内容。具体演示见 [如何：将外接程序范围的外部内容类型转换为租户范围](how-to-convert-an-add-in-scoped-external-content-type-to-tenant-scoped.md)中。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint Server 2013 的混合](http://technet.microsoft.com/zh-cn/library/jj838715.aspx)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [使用 Visual Studio 发布 SharePoint 外接程序](http://msdn.microsoft.com/library/8137d0fa-52e2-4771-8639-60af80f693bb%28Office.15%29.aspx)
    
  

