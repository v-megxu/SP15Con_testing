---
title: 如何：在 SharePoint 2013 中创建外接程序范围的外部内容类型
ms.prod: SHAREPOINT
ms.assetid: de4b50a3-84da-48ce-9ba0-fe06571e52a8
---


# 如何：在 SharePoint 2013 中创建外接程序范围的外部内容类型
了解如何创建可在 SharePoint 外接程序中安装、保护和使用的外部内容类型。
## 开发外接程序范围的外部内容类型的先决条件
<a name="bkmk_Prerequisites"> </a>

若要开始开发外接程序范围的外部内容类型，您需要：
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
- 通过 Internet 提供的已发布的 OData 服务
    
  
有关设置 SharePoint 开发环境的信息，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)。
  
    
    

## 创建外接程序范围的外部内容类型
<a name="bkmk_CreateECT"> </a>

下面的步骤演示如何基于开放式数据协议 (OData) 源创建外部内容类型以及如何修改它以将范围限定为您的 SharePoint 外接程序。
  
    
    

### 创建新的 SharePoint 外接程序


1. 打开 Visual Studio 2008。
    
  
2. 创建"SharePoint 2013 外接程序"项目。
    
  
3. 指定外接程序设置，包括外接程序名称、调试外接程序的网站 URL 以及您要如何托管外接程序（自动托管、提供程序托管或 Sharepoint 托管）。有关详细信息，请参阅  [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)。
    
  
4. 选择"完成"来创建应用程序。
    
  
有关创建 SharePoint 外接程序的完整步骤，请参阅以下内容：
  
    
    

-  [开始创建提供程序承载的 SharePoint 加载项](http://msdn.microsoft.com/library/3038dd73-41ee-436f-8c78-ef8e6869bf7b%28Office.15%29.aspx)
    
  
-  [如何：创建基本的 SharePoint 自动承载相关应用程序](http://msdn.microsoft.com/library/0572894d-c437-4b7d-8ac6-8405496e2145%28Office.15%29.aspx)
    
  
-  [开始创建 SharePoint 承载的 SharePoint 外接程序](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx)
    
  

### 生成外部内容类型


1. 在"解决方案资源管理器"中，打开项目的快捷菜单并选择"添加"、"外部数据源的内容类型"。
    
    这将启动一个向导，它可帮助您查找所选数据源并创建 BDC 模型。
    
  
2. 在"设置 OData 源"页上，输入要连接到的 OData 服务的 URL。URL 应类似于： `http://services.odata.org/Northwind/Northwind.svc/`。
    
    为您的 OData 源指定名称。
    
    > **注释**
      > 对于此示例，您将使用罗斯文服务，该服务可从位于 [开放式数据协议网站](http://www.odata.org)上的创建器列表中获取。 
3. 将出现一个列表，它显示 OData 服务公开的数据实体。选择其中一个或多个实体，然后选择"完成"。
    
  

### 部署外接程序范围的外部内容类型


- 按 F5 来编译项目并将项目文件上载到 SharePoint。
    
  

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中外接程序范围的外部内容类型](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
    
  
-  [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 中的外部内容类型](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的业务连续性服务入门](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  

