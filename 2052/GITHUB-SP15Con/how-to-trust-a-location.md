---
title: 如何：信任位置
keywords: how to,howdoi,howto,trusted location
f1_keywords:
- how to,howdoi,howto,trusted location
ms.prod: OFFICE365
ms.assetid: 0f396c0b-f578-4d1a-9e6b-a75f352265ab
---


# 如何：信任位置

您想要访问的工作簿必须放在受信任位置，否则调用以打开工作簿将失败。本示例说明如何使用 SharePoint 管理中心页面信任位置。 
  
    
    

您还可以使用 Windows PowerShell 信任位置。有关详细信息，请参阅  [TechNet](http://technet.microsoft.com/zh-cn/library/ee428287%28v=office.14%29.aspx) 上的 Microsoft SharePoint Server 2010 IT Pro 和管理文档。
> **提示**
> 有关管理改进的详细信息，或者要查看"受信任文件位置"页面的屏幕截图，请参阅博客文章  [SharePoint 2010 中的 Excel Services 管理改进](http://blogs.msdn.com/excel/archive/2009/11/16/excel-services-in-sharepoint-2010-administration-improvements.aspx)。 
  
    
    


### 信任位置


1. 在"开始"菜单中，单击"所有程序"。 
    
  
2. 指向"Microsoft SharePoint 2010 产品"，然后单击"SharePoint 2010 管理中心"。 
    
  
3. 在 SharePoint 2010 管理中心页面上，在"应用程序管理"下单击"管理服务应用程序"。
    
  
4. 在"管理服务应用程序"页面上，单击"Excel Services 应用程序"。
    
  
5. 在"管理 Excel Services 应用程序"页面上，单击"受信任文件位置"。 
    
  
6. 在"Excel Services 应用程序受信任文件位置"页面上，单击"添加受信任文件位置"。 
    
  
7. 在"Excel Services 应用程序添加受信任文件位置"页面上的"地址"文本框中，键入用于保存您的工作簿的位置例如，http:// _MyServer002_/Shared%20Documents。 
    
  
8. 在"位置类型"下，单击相应的位置类型。在此示例中，选择"SharePoint Foundation"。
    
  
9. 如果您想要信任子库或目录，在"信任子级"下选择"受信任的子级"。
    
  
10. 单击"确定"。
    
  

## 另请参阅


#### 任务


  
    
    
 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [如何：从 Excel 客户端保存到服务器](how-to-save-from-excel-client-to-the-server.md)
#### 概念


  
    
    
 [Excel Services 警告](excel-services-alerts.md)
#### 其他资源


  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
