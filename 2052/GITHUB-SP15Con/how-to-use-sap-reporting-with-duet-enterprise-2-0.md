---
title: 如何：在 Duet Enterprise 2.0 中使用 SAP 报告
ms.prod: SHAREPOINT
ms.assetid: a54c6cd2-2283-440d-af55-e98e3212caa1
---


# 如何：在 Duet Enterprise 2.0 中使用 SAP 报告

## 简介
<a name="bkmk_Introduction"> </a>

凭借 Duet Enterprise 2.0，您可以通过进行少量自定义，将 Duet 报告功能集成在 SharePoint 外接程序中。
  
    
    
为您的应用程序启用报告功能的秘诀是使用 Duet 安装的隐藏功能。您需要将此功能绑定到自定义功能，以便在应用程序实例化时，SAP 报告功能可适用于应用程序。
  
    
    

## 启用功能
<a name="bkmk_EnablingTheFeatures"> </a>

若要启用 Duet 报告功能，必须仔细遵循激活序列。
  
    
    

### 若要创建一个功能以添加应用程序范围的外部内容类型，请执行以下操作：


1. 在 Duet 报告应用程序内的"解决方案资源管理器"中，右键单击项目名称。选择"添加"、"外部数据源的内容类型"。单击"下一步"。
    
  
2. 输入作为 OData 源的 SAP 报告终端的 URL。
    
  
3. 选择"实体"，然后选择"完成"。
    
  
4. 打开新创建的外部内容类型以查看 LSI 属性。您会发现这些属性与服务器场范围的外部内容类型相同（ **ODataconnectionSettingsId** 除外）。
    
  

### 若要创建一个功能以启用隐藏的 Duet 功能，请执行以下操作：


1. 向项目添加另一个新功能。将标题命名为 **AddDuetReporting**。
    
    此功能依赖于 **AddReportingModel** 和 **DuetReportingForApps** 功能。
    
  
2. 将以下代码添加到" **元素**"文件。
    
  ```
  
<?xml version="1.0" encoding="utf-8"?>
<Feature xmlns="http://schemas.microsoft.com/sharepoint/" Title="AddDuetReporting" Id="6a55705c-af12-455a-914b-8cf3a31c820e" Scope="Web">
  <ActivationDependencies>
    <ActivationDependency FeatureId="e1fe41d3-7fc3-458f-9a66-6ecf6a39bb2c" FeatureTitle="AddReportingModel" />
    <ActivationDependency FeatureId="9b60ccba-ebfd-4e38-87c8-3dea9cc2680a" FeatureTitle="SAPReportingForApps" />
  </ActivationDependencies>
</Feature>

  ```

请注意，激活依赖项中的序列很重要。首先，您必须创建外部内容类型，然后激活 **SAPReportingForApps** 功能。此外，请注意第二个功能（ID： **9b60ccba-ebfd-4e38-87c8-3dea9cc2680a**）是 Duet Enterprise 2.0 的附带功能，但标记为隐藏。通过此方法，开发人员可以使用此功能，并且可以将 Duet 报告功能引入应用程序。
  
    
    
激活 **DuetReportingForApps** 功能后，将带来应用程序网站上的所有工件（报告列表、Lib、表单等）和自定义项，但是由于应用程序网站模板没有标准导航链接，应用程序开发人员需要添加自定义页面元素以引出 Duet 功能（例如，报告设置、库列表视图和表单）。开发人员应查阅报告功能的标准 Duet 文档，以了解有关功能及其 UI 元素的详细信息。开发人员可能选择为功能入口点构建自定义 UI，以更适合应用程序的常规主题。
  
    
    

## 查看结果
<a name="bkmk_ViewingTheResults"> </a>

若要查看默认报告设置页，请导航到： **~/Lists/ReportSetting/AllReportTemplate.aspx**。
  
    
    
若要查看报告文档库的默认视图，请导航到： **~/ReportsLib/Forms/AllItems.aspx**。
  
    
    

## 自定义报告
<a name="bkmk_CustomizingTheReports"> </a>

在应用程序中，开发人员还可以创建自己的自定义 UI（使用 HTML/JavaScript/Jquery 等），并使用 BCS CSOM 来构建更丰富的用户体验。下面的屏幕截图显示了一个类似的应用程序，其中基于自定义 HTML 的 UI 是借助于 OOB 工件和客户端 BCS API 构建。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [使用 Duet Enterprise 2.0 进行开发](developing-with-duet-enterprise-2-0.md)
    
  
-  [如何：在 SharePoint 2013 中从 OData 源创建外部内容类型](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [将 OData 源与 SharePoint 2013 中的 Business Connectivity Services 结合使用](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

