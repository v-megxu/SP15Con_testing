---
title: 如何：在 SharePoint 2013 中使用 REST 访问外部数据
ms.prod: SHAREPOINT
ms.assetid: 0663cc8c-a736-434d-9858-6ce12ce7f748
---


# 如何：在 SharePoint 2013 中使用 REST 访问外部数据
了解如何通过使用 Business Connectivity Services (BCS) 的代表性状态传输 (REST) URL 来访问来自 SharePoint 2013 的外部数据。
本文演示如何设置从开放式数据协议 (OData) 源检索数据的外部列表。
  
    
    


## 使用 REST 访问外部数据的先决条件
<a name="bkmk_Prerequisites"> </a>

若要通过使用 REST 访问来自 SharePoint 2013 的外部数据，您需要：
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
- 运行的 SharePoint 外接程序开发环境：按照 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)中的说明操作。
    
  
- 对公共 OData.org 创建器的访问权
    
  

### 在使用 REST 访问外部数据时要了解的核心概念

SharePoint 2013 REST 服务提供了使用专门构建的 URL 访问外部数据的方法。若要了解它的工作原理和使用方法，请参阅以下文章。
  
    
    

**表 1. SharePoint 2013 中的 REST 的核心概念**


|**文章标题**|**说明**|
|:-----|:-----|
| [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md) <br/> |了解如何使用 SharePoint 2013 REST 服务，它提供了可与现有客户端对象模型比较的 REST 编程接口。  <br/> |
| [开始使用 SharePoint 2013 REST 服务](get-to-know-the-sharepoint-2013-rest-service.md) <br/> |获得使用 SharePoint 2013 REST 服务来采用 REST 和 OData Web 协议标准访问和更新 SharePoint 数据的基础知识。  <br/> |
| [使用 SharePoint 2013 REST 服务](e1ff2979-1c16-4cb0-a57e-9168dfe20a7c.md) <br/> |了解如何按照 SharePoint 2013 数据结构在 REST 服务中的表示进行导航、通过 REST 服务对 SharePoint 项执行常见的 CRUD（创建、读取、更新和删除）操作、跨应用程序同步 SharePoint 项以及控制项并发性。  <br/> |
   

## 创建 SharePoint 外接程序以使用 REST 访问外部数据
<a name="bkmk_CreateApp"> </a>

下面的过程指导您设置 SharePoint 外接程序并配置网页以使用 REST 功能请求从外部数据源检索数据。
  
    
    

### 创建 SharePoint 外接程序


1. 打开 Visual Studio 2008。
    
  
2. 创建"SharePoint 2013 相关应用程序"项目。
    
  
3. 指定应用程序设置，包括应用程序名称、调试应用程序的网站 URL 以及您要如何承载应用程序（自动承载、提供程序承载、Sharepoint 承载）。有关承载选项的详细信息，请参阅  [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)。
    
  
4. 选择"完成"以创建应用程序。
    
  

### 生成外部内容类型


1. 在"解决方案资源管理器"中，打开项目的快捷菜单并选择"添加"、"外部数据源的内容类型"。
    
  
2. 在"指定 OData 源"页中，输入要连接到的 OData 服务的 URL。在本例中，使用  [http://www.odata.org/ecosystem](http://www.odata.org/ecosystem) 上发布的罗斯文 OData 源。将 OData 服务的 URL 设置为 `http://services.odata.org/Northwind/Northwind.svc/` 并为数据源提供名称。
    
    选择"下一步"。
    
  
3. 这将显示 OData 服务公开的数据实体的列表。选择"客户"实体。确保选中了"为所选数据实体创建列表实例(服务操作除外)"复选框。
    
  
4. 选择"完成"。
    
  

## 代码示例：将脚本和 HTML 添加到 Home.aspx 页面中
<a name="bkmk_AddUIelements"> </a>

此时，您具有将显示来自 Netflix OData 源的数据的外部内容类型和外部列表。 
  
    
    
下一个目标是修改您在创建应用程序时创建的 default.aspx 页面。您将添加一个容器来保存在该页面加载时执行的查询的结果。通过在发生页面加载事件时执行脚本，您确保在每次浏览该页面时执行脚本，并且生成的 REST 调用对罗斯文 OData 源执行以将记录添加到该页面中。
  
    
    

### 向 Default.aspx 页面中添加容器


1. 在"解决方案资源管理器"中，打开"页面"模块中的 Default.aspx 页面。
    
  
2. 将以下 **div** 元素添加到该页面中。
    
  ```HTML
  
<div id="displayDiv"></div>
  ```

3. 保存该页面。
    
  
最后，将在该页面加载时执行的代码添加到 App.js 文件中。
  
    
    

### 修改 App.js 文件以进行 REST 调用


1. 打开您的 SharePoint 项目的"脚本"模块中的 App.js 文件。
    
  
2. 将以下代码粘贴到该文件末尾。
    
  ```
  $(document).ready(function () {

    // Namespace
    window.AppLevelECT = window.AppLevelECT || {};

    // Constructor
    AppLevelECT.Grid = function (hostElement, surlWeb) {
        this.hostElement = hostElement;
        if (surlWeb.length > 0 &amp;&amp; surlWeb.substring(surlWeb.length - 1, surlWeb.length) != "/")
            surlWeb += "/";
        this.surlWeb = surlWeb;
    }

    // Prototype
    AppLevelECT.Grid.prototype = {

        init: function () {

            $.ajax({
                url: this.surlWeb + "_api/lists/getbytitle('Customer')/items?$select=BdcIdentity,CustomerID,ContactName",
                headers: {
                    "accept": "application/json",
                    "X-RequestDigest": $("#__REQUESTDIGEST").val()
                },
                success: this.showItems
            });
        },

        showItems: function (data) {
            var items = [];

            items.push("<table>");
            items.push('<tr><td>Customer ID</td><td>Customer Name</td></tr>');

            $.each(data.d.results, function (key, val) {
                items.push('<tr id="' + val.BdcIdentity + '"><td>' +
                    val.CustomerID + '</td><td>' +
                    val.ContactName + '</td></tr>');
            });

            items.push("</table>");

            $("#displayDiv").html(items.join(''));
        }
    }

    ExecuteOrDelayUntilScriptLoaded(getCustomers, "sp.js");
});

function getCustomers() {
    var grid = new AppLevelECT.Grid($("#displayDiv"), _spPageContextInfo.webServerRelativeUrl);
    grid.init();
}
  ```

按 F5 将应用程序部署到 SharePoint。浏览到应用程序中的 Default.aspx 页面，客户列表将显示在该页面上。
  
    
    

## 其他资源
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [开始使用 SharePoint 2013 REST 服务](get-to-know-the-sharepoint-2013-rest-service.md)
    
  
-  [使用 SharePoint 2013 REST 服务](e1ff2979-1c16-4cb0-a57e-9168dfe20a7c.md)
    
  
-  [SharePoint 2013 中外接程序范围的外部内容类型](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  

