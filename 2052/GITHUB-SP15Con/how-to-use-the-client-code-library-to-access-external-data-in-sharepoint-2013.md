---
title: 如何：使用客户端代码库访问 SharePoint 2013 中的外部数据
ms.prod: SHAREPOINT
ms.assetid: c280ae92-c52b-4658-b0f3-805fb215ef8e
---


# 如何：使用客户端代码库访问 SharePoint 2013 中的外部数据
学习如何在 SharePoint 2013 中使用基于浏览器的脚本将 SharePoint 2013 客户端对象模型用于 Business Connectivity Services (BCS) 对象。
本文说明如何建立一个在 SharePoint 2013 中使用客户端对象模型从开放数据协议源 (OData) 检索数据的外部列表。
  
    
    


## 使用 SharePoint 2013 客户端对象模型访问外部数据的先决条件
<a name="bkmk_Prerequisites"> </a>

以下是能够使用 SharePoint 客户端对象模型开发应用程序的要求：
  
    
    

- SharePoint 2013
    
  
- Visual Studio 2008
    
  
- Visual Studio 2012 Office 开发人员工具
    
  
- 功能 SharePoint 外接程序 开发环境：遵循 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)中的说明。
    
  
- 访问公共 OData.org 程序
    
  

### 了解何时使用 SharePoint 2013 客户端对象模型访问外部数据的核心概念

SharePoint 2013 客户端对象模型提供一种使用类似于服务器端 API 的客户端调用来访问外部数据的方法。要了解其工作原理以及工作方式，请参阅表 1 中的文章。
  
    
    

**表 1. 使用客户端对象模型的核心概念**


|**文章**|**说明**|
|:-----|:-----|
| [使用 SharePoint 2013 客户端库代码完成基本操作](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx) <br/> |学习如何编写代码以使用 SharePoint 2013 .NET Framework 客户端对象模型 (CSOM) 执行基本操作。  <br/> |
   

## 创建 SharePoint 外接程序 以使用客户端对象模型访问外部数据
<a name="bkmk_CreateApp"> </a>

下面的过程显示如何建立 SharePoint 外接程序 和配置网页，以使用客户端对象模型方法和对象提出从外部数据源检索数据的请求。
  
    
    

### 创建 SharePoint 外接程序 的步骤


1. 打开 Visual Studio 2008。
    
  
2. 创建"SharePoint 2013 应用程序"项目。
    
  
3. 指定应用程序设置，包括应用程序名称、调试应用程序的网站 URL，以及您希望的应用程序承载方式（自动承载、供应商承载、SharePoint 承载）。有关承载选项的详细信息，请参阅  [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)。
    
  
4. 单击"完成"创建应用程序。
    
  

### 生成外部内容类型的步骤


1. 在"解决方案资源管理器"中，打开项目的快捷菜单，然后依次选择"添加"、"外部数据源的内容类型"。
    
  
2. 在"指定 OData 源"向导中，输入要连接到的 OData 服务的 URL。在本示例中，您将使用  [http://www.odata.org/ecosystem](http://www.odata.org/ecosystem) 上发布的 Northwind OData 源。将.OData 服务的 URL 设置为 `http://services.odata.org/Northwind/Northwind.svc/`
    
    为数据源指定一个名词，然后选择"下一步"。
    
  
3. 随即将显示 OData 服务所暴露实体的列表。选择"客户"实体。确保选中"为所选数据实体创建列表实例（服务操作除外）"复选框。
    
  
4. 选择"完成"。
    
  

## 代码示例：将脚本和 HTML 添加到 Default.aspx 页
<a name="bkmk_AddUIelements"> </a>

此时，您将拥有外部内容类型以及外部列表，可以显示 Netflix OData 源中的数据。 
  
    
    
下一个目标是修改您在创建应用程序时创建的 default.aspx 页。您可以添加一个容器保存对页面加载执行查询的结果。通过在进行页面加载事件时执行脚本，可以确保在每次浏览页面时执行该脚本，并将对 Netflix OData 源进行后续客户端对象模型调用，以对该页添加结果。 
  
    
    

### 向 Default.aspx 页添加容器的步骤


1. 在"解决方案资源管理器"中，打开位于"页"中的 Default.aspx 页。
    
  
2. 将以下 **div** 元素添加到页：
    
  ```HTML
  
<div id="displayDiv"></div>
  ```

3. 保存页面。
    
  
最后，将代码添加到进行页面加载时执行的 App.js 文件。
  
    
    

### 修改 App.js 文件以进行客户端对象模型调用的步骤


1. 打开 SharePoint 项目"脚本"模块中 App.js 文件。
    
  
2. 将以下代码粘贴到文件末尾。
    
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

按 F5 将应用程序部署到 SharePoint。浏览到应用程序中的 Default.aspx 页面，页面上会出现客户列表。
  
    
    

## 其他资源
<a name="bkmk_Addresources"> </a>


-  [SharePoint 2013 中的 Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中使用具有外部数据的客户端对象模型入门](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 的 BCS 客户端对象模型引用](bcs-client-object-model-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 Business Connectivity Services 的新增功能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 客户端库代码完成基本操作](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  

