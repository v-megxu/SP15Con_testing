---
title: SharePoint 2013 中的 Visio Services
ms.prod: SHAREPOINT
ms.assetid: ed8c5d12-e17d-4ceb-b195-601c26824370
---



# SharePoint 2013 中的 Visio Services
Microsoft SharePoint Server 2013 中的 Visio Services 使您能够下载、显示 Visio .vsdx 和 .vsdm 文件以及 Microsoft SharePoint Server 2013 和 Microsoft SharePoint Online 上的 Visio Web 绘图 (.vdw)，它还能使您和它们以编程的方式相交互。 .
## SharePoint Server 2013 的 Visio 服务中什么是新的？
<a name="visserv15_WhatsNew"> </a>

Microsoft SharePoint Server 2013 中的 Visio Services 和 Microsoft SharePoint Online 包含了许多新功能，其中包括支持新的 Microsoft Visio 2013 文件格式、支持 Microsoft Business Connectivity Services (BCS) 数据源，和对注释的编程访问。
  
    
    

### 新文件格式
<a name="vis15_WhatsNew_NewFF"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|Visio 2013 介绍了一种的文件格式 (.vsdx), 它基于"开放数据包约定"(OPC) 标准（ISO 29500，第二部分）和上一个 Visio XML 文件格式 (.vdx) 中的 XML 元素。它是压缩的，类似于用于其他 应用程序的文件格式的基于 XML 的文件格式。  <br/> 使用该新的文件格式，您可以将 Visio 2013 绘图直接保存到 SharePoint Server 或 SharePoint Online 库，无需将该文件发布为 Visio Web 绘图 (.vdw)。即使如此，Visio Services 仍可以读取和显示 Visio Web 绘图文件。  <br/> Visio Services 保留了在浏览器中显示 Visio Web 绘图 (.vdw) 格式的能力。它现在还呈现了新的 Visio 绘图 (.vsdx) 和 Visio 启用宏的 (.vsdm) 格式。  <br/> Visio ServicesECMAScript (JavaScript, JScript) 对象模型包含了一种新的 API 以支持这种新的文件格式： [Vwa.VwaControl.getDiagramFileType 方法](http://msdn.microsoft.com/library/fd8ca95f-a3be-4000-bce8-3aaf1f48148c%28Office.15%29.aspx)。该方法返回了来自指示 Visio Web Access Web 部件中显示的文件是 Visio 绘图 (.vsdx) 还是 Visio Web 绘图 (.vdw) 的  [Vwa.DiagramFileType 枚举](http://msdn.microsoft.com/library/dd2f8a5d-a54b-44bd-a458-02efdcba0201%28Office.15%29.aspx) 的值。 <br/> 有关 Visio 2013 中的新文件格式的详细信息，请参阅 [Visio 文件格式 (.vsdx) 简介](http://msdn.microsoft.com/library/69736f40-8f67-46c2-abf6-82dffecb2274%28Office.15%29.aspx)。  <br/> > **注释**> 新的 Visio 文件（.vsdx 和 .vsdm）只已光栅格式显示在 Visio Services 上。使用 Silverlight 也可以显示 Visio Web 绘图 (.vdw)。           |
   

### 支持 Business Connectivity Services (BCS) data
<a name="vis15_WhatsNew_BCS"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|现在，可以将 Visio 2013 图标连接到使用 SharePoint Server 2013 服务器和 SharePoint Online 中的 Microsoft Business Connectivity Services (BCS) 创建的外部列表上。Visio Services 具有数据更新时刷新 Visio 图表的能力。  <br/> > **注释**> Visio Services 不支持 SQL、SQL Azure、OLEDC、ODBC 和自定义数据提供程序作为 SharePoint Online 中的数据源。           |
   

### 评论功能
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|Visio 2013 包含了一种新的评论功能框架。现在可以将评论与特定形状或页进行关联。Visio Services 包括了 JavaScript API 以检索图表中的评论。  <br/> 有关 Visio ServicesJavaScript 对象模型中的评论功能 API 的详细信息，请参阅  [VwaPage.getPageComments 方法](http://msdn.microsoft.com/library/d1e7740c-e0fa-4823-b2b6-14551bb84c36%28Office.15%29.aspx) 和 [VwaShape.getComments 方法](http://msdn.microsoft.com/library/fcdec9c2-a503-4315-b048-033cd5ac09dd%28Office.15%29.aspx) 主题。 <br/> |
   

### 扩展重新计算
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|现在，Visio Services 可以重新计算 ShapeSheet 中的公式。除了刷新"数据图形"以外，Visio Services 还可以刷新所有含数据的形状和依赖于数据的图像。大多数 ShapeSheet 功能都支持重新计算。  <br/> |
   

### 改进的错误处理
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|当数据刷新错误出现在 Visio Services 显示的 Visio 绘图中时，该显示将恢复该图表的静态图像。Visio Services 在错误消息中还提供了更多可操作的消息。  <br/> |
   

### 安全存储身份验证
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|以前，SQL 数据基等外部数据源的"身份验证设置"只能通过 Microsoft Excel 中的实用工具进行配置。现在，使用 Visio 2013，用户可以直接从 Visio 客户端配置已连接图表的数据，这就使得能在 Visio Services 中刷新数据源。  <br/> |
   

## Visio Services JavaScript 对象模型
<a name="visserv15_JSOM"> </a>


|||
|:-----|:-----|
|![云中的行为注释](images/mod_icon_incloud.gif)           <br/>![本地行为注释](images/mod_icon_onpremises.gif)|Visio Services 的 JavaScript 对象模型中的  [Vwa 命名空间](http://msdn.microsoft.com/library/b67939fa-d3db-41ff-8864-eabd318ba7c4%28Office.15%29.aspx) 让您能够对 Visio Web Access Web 部件中显示的 Visio 绘图进行编程访问。使用 JavaScript 对象模型，您可以访问有关图表、页和形状的数据、形状超链接和形状边界框属性。通过此访问，您可以创建突出显示形状、在图表上放置覆盖、回应图表和鼠标事件并更改视区的平移和缩放属性的混合 Web 应用程序。 <br/> 有关将 Visio Web Access Web 部件添加到 SharePoint 页并使用 Visio 2013 中的 JavaScript API 对该页进行编程的详细信息，请参阅 [自定义 Visio Web Access Web 部件中的 Visio Web 绘图](http://msdn.microsoft.com/zh-cn/library/ff394649.aspx)。  <br/> |
   

## Visio 服务类库
<a name="visserv15_Mref"> </a>


|||
|:-----|:-----|
|![本地行为注释](images/mod_icon_onpremises.gif)|您可以使用 Visio Services 类库，在  [Microsoft.Office.Visio.Server](https://msdn.microsoft.com/library/Microsoft.Office.Visio.Server.aspx) 命名空间中生成自定义 Visio Services 数据提供程序。这些数据提供程序允许您以编程地方式刷新派生自寄宿在 Visio 2013 站点上的 SharePoint Server 2013 图表中的自定义数据源的数据。 <br/> 有关创建自定义数据提供程序和生成完整的端到端解决方案的详细信息，请参阅 [使用 Visio 服务创建自定义数据提供程序](http://msdn.microsoft.com/zh-cn/library/ff394595.aspx)。  <br/> |
   

## 其他资源
<a name="visserv15_Additional"> </a>


-  [Microsoft.Office.Visio.Server](https://msdn.microsoft.com/library/Microsoft.Office.Visio.Server.aspx)
    
  
-  [Vwa 命名空间](http://msdn.microsoft.com/library/b67939fa-d3db-41ff-8864-eabd318ba7c4%28Office.15%29.aspx)
    
  
-  [使用 Visio Services 服务创建自定义数据提供程序](http://msdn.microsoft.com/zh-cn/library/ff394595.aspx)
    
  
-  [自定义 Visio Web Access Web 部件中的 Visio Web 绘图](http://msdn.microsoft.com/zh-cn/library/ff394649.aspx)
    
  
-  [Visio 中面向开发人员的新增功能](http://msdn.microsoft.com/library/7e3fb858-0ab8-bd2e-217c-c85b10d79785%28Office.15%29.aspx)
    
  
- 有关针对最终用户的 vis15short 中的一系列功能，请参阅 [Visio 中什么是新的？](http://office.microsoft.com/zh-cn/HA102749364.aspx)。
    
  
