---
title: 升级 SharePoint 2013 的 Web 模板
ms.prod: SHAREPOINT
ms.assetid: 69048e4c-6d6d-4e4e-b74c-7c72ae444354
---


# 升级 SharePoint 2013 的 Web 模板
了解升级自定义 SharePoint 2010 Web 模板，以在自助服务升级后用于 SharePoint 2013 中。
SharePoint 2013 明显改变了用于呈现 SharePoint 网站外观的基础组件。对于针对 SharePoint 2010 中默认组件进行的自定义设置，这些新变化涉及样式、页面布局、母版页和主题。
  
    
    

本文提供了关于更新 Web 模板以用于新框架的指南。
## 自助服务网站升级后可能出现的行为

将服务器从 SharePoint 2010 升级至 2013 时，网站集管理员会看到一个链接，他们可以通过此链接逐步升级网站，或者同时升级网站集中的所有网站。然后，用户可以升级并测试那些包含自定义的网站。升级后用户可能会遇到的一些问题包括：
  
    
    

- 应用到网站的外观方案发生变化或全部丢失。
    
  
- 自定义组件无法正确呈现
    
  
- 页面根本不呈现，并且用户收到来自 SharePoint 的未知错误。
    
  
- 默认启用的功能在升级后禁用。
    
  

## 升级网站的建议

升级网站时，我们通常建议您使用评估网站来安装组件并测试兼容性和性能。
  
    
    
以下部分详细介绍了 Web 模板中需要更新的内容。
  
    
    

### 更新母版页引用

升级至 SharePoint 2013 后，Web 模板中包含的任何自定义母版页引用将会被设置为名称为 **seattle.master** 的默认母版页。如果您对 SharePoint 2010 中的默认母版页进行了自定义设置，则需要将引用更改为该自定义页面，以便显示自定义项。
  
    
    

### 更新可用功能

在将网站更新为使用 SharePoint 2013 Web 模板时，默认附加到模板的功能将被删除。因此，升级后 Web 模板的可用功能将会减少。
  
    
    
要将默认功能重新添加到模板，您必须修改 Web 模板的 Onet.xml 文件，其中包含功能列表。要将默认功能重新添加到模板，请执行以下操作：
  
    
    

### 将默认功能重新添加到 Web 模板


1. 打开包含您要更新的 Web 模板的 Visual Studio 项目。
    
  
2. 在"解决方案资源管理器"中，找到项目中的 Onet.xml 文件。
    
  
3. 在 XML 编辑器中打开 Onet.xml。
    
  
4. 确保表 1 中的每个功能都包含在 **WebFeatures** 部分中。
    
   **表 1. 默认 Web 模板功能**


|**DisplayName**|**功能 ID**|
|:-----|:-----|
|AccSvcAddAccessApp  <br/> |d2b9ec23-526b-42c5-87b6-852bd83e0364  <br/> |
|AnnouncementsList  <br/> |00bfea71-d1ce-42de-9c63-a44004ce0104  <br/> |
|BaseWeb  <br/> |99fe402e-89a0-45aa-9163-85342e865dc8  <br/> |
|BizAppsListTemplates  <br/> |065c78be-5231-477e-a972-14177cc5b3c7  <br/> |
|ContactsList  <br/> |00bfea71-7e6d-4186-9ba8-c047ac750105  <br/> |
|ContactsList  <br/> |00bfea71-7e6d-4186-9ba8-c047ac750105  <br/> |
|CustomList  <br/> |00bfea71-de22-43b2-a848-c05709900100  <br/> |
|DataConnectionLibrary  <br/> |00bfea71-dbd7-4f72-b8cb-da7ac0440130  <br/> |
|DataSourceLibrary  <br/> |00bfea71-f381-423d-b9d1-da7a54c50110  <br/> |
|DiscussionsList  <br/> |00bfea71-6a49-43fa-b535-d15c05500108  <br/> |
|DocumentLibrary  <br/> |00bfea71-e717-4e80-aa17-d0c71b360101  <br/> |
|EventsList  <br/> |00bfea71-ec85-4903-972d-ebe475780106  <br/> |
|EventsList  <br/> |00bfea71-ec85-4903-972d-ebe475780106  <br/> |
|ExternalList  <br/> |00bfea71-9549-43f8-b978-e47e54a10600  <br/> |
|FollowingContent  <br/> |a7a2793e-67cd-4dc1-9fd0-43f61581207a  <br/> |
|GanttTasksList  <br/> |00bfea71-513d-4ca0-96c2-6a47775c0119  <br/> |
|GettingStarted  <br/> |4aec7207-0d02-4f4f-aa07-b370199cd0c7  <br/> |
|GridList  <br/> |00bfea71-3a1d-41d3-a0ee-651d11570120  <br/> |
|HierarchyTasksList  <br/> |f9ce21f8-f437-4f7e-8bc6-946378c850f0  <br/> |
|IPFSWebFeatures  <br/> |f9ce21f8-f437-4f7e-8bc6-946378c850f0  <br/> |
|IssuesList  <br/> |00bfea71-5932-4f9c-ad71-1557e5751100  <br/> |
|LinksList  <br/> |00bfea71-5932-4f9c-ad71-1557e5751100  <br/> |
|MBrowserRedirect  <br/> |d95c97f3-e528-4da2-ae9f-32b3535fbb59  <br/> |
|MDSFeature  <br/> |87294c72-f260-42f3-a41b-981a2ffce37a  <br/> |
|MobilityRedirect  <br/> |f41cc668-37e5-4743-b4a8-74d1db3fd8a4  <br/> |
|MySiteMicroBlog  <br/> |ea23650b-0340-4708-b465-441a41c37af7  <br/> |
|NoCodeWorkflowLibrary  <br/> |00bfea71-f600-43f6-a895-40c0de7b0117  <br/> |
|PictureLibrary  <br/> |00bfea71-52d4-45b3-b544-b1c71b620109  <br/> |
|PremiumWeb  <br/> |0806d127-06e6-447a-980e-2e90b03101b8  <br/> |
|PromotedLinksList  <br/> |192efa95-e50c-475e-87ab-361cede5dd7f  <br/> |
|ReportListTemplate  <br/> |2510d73f-7109-4ccc-8a1c-314894deeb3a  <br/> |
|SiteFeed  <br/> |15a572c6-e545-4d32-897a-bab6f5846e18  <br/> |
|SiteFeedController  <br/> |5153156a-63af-4fac-b557-91bd8c315432  <br/> |
|SurveysList  <br/> |00bfea71-eb8a-40b1-80c7-506be7590102  <br/> |
|TaskListNewsFeed  <br/> |ff13819a-a9ac-46fb-8163-9d53357ef98d  <br/> |
|TasksList  <br/> |00bfea71-a83e-497e-9ba0-7a5c597d0107  <br/> |
|TeamCollab  <br/> |00bfea71-4ea5-48d4-a4ad-7ea5c011abe5  <br/> |
|WebPageLibrary  <br/> |00bfea71-c796-4402-9f2f-0eb9a6e71b18  <br/> |
|WikiPageHomePage  <br/> |00bfea71-d8fe-4fec-8dad-01c19a6e4053  <br/> |
|WorkflowHistoryList  <br/> |00bfea71-4ea5-48d4-a4ad-305cf7030140  <br/> |
|workflowProcessList  <br/> |00bfea71-2d77-4a75-9fca-76516689e21a  <br/> |
|WorkflowServiceStore  <br/> |2c63df2b-ceab-42c6-aeff-b3968162d4b1  <br/> |
|WorkflowTask  <br/> |57311b7a-9afd-4ff0-866e-9393ad6647b1  <br/> |
|XmlFormLibrary  <br/> |00bfea71-1e1d-4562-b56a-f05371bb0115  <br/> |
   
5. 保存所做的更改，并像通常一样部署。
    
  

> **注释**
> 您可能还需要在管理中心实用程序中激活这些功能。 
  
    
    


## 其他资源
<a name="bk_addresources"> </a>


-  [升级 SharePoint 2013 的网站自定义](upgrade-site-customizations-for-sharepoint-2013.md)
    
  
-  [SharePoint 2010 和 Web 模板](http://blogs.msdn.com/b/vesku/archive/2010/10/14/sharepoint-2010-and-web-templates.aspx)
    
  
-  [规划网站集升级](https://technet.microsoft.com/zh-cn/library/ff191199.aspx)
    
  
-  [在 SharePoint 2013 中规划网站集升级](http://technet.microsoft.com/zh-cn/library/ff191199.aspx)
    
  

  
    
    

