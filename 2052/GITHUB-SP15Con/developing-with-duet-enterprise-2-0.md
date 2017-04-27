---
title: 使用 Duet Enterprise 2.0 进行开发
ms.prod: SHAREPOINT
ms.assetid: c3ef38aa-559e-4832-95c7-75e222c77624
---


# 使用 Duet Enterprise 2.0 进行开发

## 概述
<a name="Overview"> </a>

Duet Enterprise 2.0 是 Microsoft 和 SAP 之间协作努力的最新版本，目的是让 SharePoint 用户能够处理来自 SAP 系统的数据。该版本结合了来自 SAP 及 SharePoint 2013 和 SharePoint Online 的组件。通过该版本，开发人员可以创建组件，以允许用户将 SAP 系统中的数据带入熟悉的 SharePoint 环境。
  
    
    

## Duet Enterprise 2.0 的功能
<a name="Overview"> </a>

正确安装和配置后，Duet Enterprise 2.0 将提供以下功能：
  
    
    

- 您可以通过使用业务数据 Web 部件、外部列表和自定义组件，在 SharePoint 中处理 SAP 系统的数据。
    
  
- 通过使用内置组件，在 SharePoint 2013 中使用 SAP 数据，而无需任何代码。
    
  
- 在应用程序中使用 SAP 报告系统。
    
  
- 使用通过 Duet Enterprise 2.0 安装的特殊 Web 部件将 SAP 信息添加到 SharePoint 页面
    
  
- 在应用程序中使用 SAP 工作流。
    
  
- 开发人员可以使用客户端 JavaScript 与 SAP 外部数据进行交互。
    
  
- 使用 OAuth 进行身份验证以保护数据安全。
    
  

## 设置开发环境
<a name="SettingUp"> </a>

在极大程度上，使用 Duet Enterprise 2.0 开发SharePoint 外接程序 与创建标准SharePoint 外接程序完全相同。您可以使用基于浏览器的 Napa Office 365 开发工具 工具来创建和部署，或者可以使用 Visual Studio 来扩展应用程序并在 Visual Studio 集成开发环境的可靠框架中使用。
  
    
    

## 添加外部内容类型
<a name="AddingECT"> </a>

为了访问托管在 SAP 系统中的外部数据，您必须添加一个外部内容类型。由于 SAP 数据通过 OData 终结点公开，因此安装在 Visual Studio 中的自动生成工具可用于 [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)（在应用程序级别范围内）。
  
    
    
按照以下步骤创建外部内容类型：
  
    
    

### 从 SAP OData 终结点创建外部内容类型


1. 在"解决方案资源管理器"中，打开项目的快捷菜单并选择"添加"、"外部数据源的内容类型"。
    
  
2. 在"指定 OData 源"页上，输入 Duet Enterprise 工作流服务的 URL。
    
  
3. 选择您的 OData 源的名称。
    
  
4. 选择需要的实体。
    
  
5. 选择"完成"。
    
  
Visual Studio 将创建名为"外部内容类型"的新文件夹，从中可找到新创建的 BDC 模型。
  
    
    

## 配置 BDC 模型
<a name="ConfiguringProject"> </a>

让项目正常工作的最重要一点是向 BDC 模型添加 **ODataExtensionProvider** 属性。此属性定义了向 BCS 提供创建应用程序代码所需 SAP 扩展的扩展提供程序。
  
    
    
以下示例显示了添加到 BDC 模型的属性：
  
    
    



```XML

<LobSystem Type="OData" Name="LOB_SYSTEM_NAME">
                     <Properties>
                          <Property Name="ODataServiceMetadataUrl" Type="System.String">
                               https://<DUET_METADATA_URL>:443/sap/opu/odata/sap/ 
                               ZANDY_PO_HEADER_SRV/$metadata</Property>
                          <Property Name="ODataServicesVersion" Type="System.String">2.0</Property>
                          <Property Name="ODataExtensionProvider" Type="System.String"> 
                               OBA.Server.Canary.ObaOdataServerExtensionProvider, 
                               OBA.Server.SSOProvider, 
                               Version=15.0.0.0, 
                               Culture=neutral, 
                               PublicKeyToken=71e9bce111e9429c</Property>
                          <Property Name="TraceHeader" Type="System.String">SAP-PASSPORT</Property>
                     </Properties>

```


## 使用 Duet 简易版服务开发自定义应用程序
<a name="UsingDuetStarterServices"> </a>

Duet Enterprise 2.0 向 SharePoint 2013 服务器上的文件系统安装了几个简易版服务。在默认安装中，文件位于 C:\\Program Files\\Duet Enterprise\\2.0\\Solutions\\Starter Services。其中包括： 
  
    
    

- OBACustomerWorkspace
    
  
- OBAOrderToCash
    
  
- OBAPortal
    
  
- OBAProductCenter
    
  
每个解决方案包括 WSP 文件、解决方案和实现这些解决方案所需的其他支持文件。
  
    
    
这些解决方案可用于了解通过 Duet Enterprise 2.0 可以完成的操作及使用的开发模式，但不支持用于 SharePoint 外接程序 中。
  
    
    

## 其他资源
<a name="ConNavExample_resources"> </a>


-  [适用于 SharePoint 和 SAP Server 2.0 的 Duet Enterprise](http://technet.microsoft.com/zh-cn/library/ff972436.aspx)
    
  
-  [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Visual Studio 开发人员中心](http://msdn.microsoft.com/zh-cn/vstudio/default)
    
  
-  [使用 Visual Studio 的 Office 开发](http://msdn.microsoft.com/zh-cn/office/hh133430)
    
  

