---
title: 使用 SharePoint 2013 中的社交功能开始进行开发
ms.prod: SHAREPOINT
ms.assetid: 8852ce36-8309-45a7-a141-2e10ac17a123
---



# 使用 SharePoint 2013 中的社交功能开始进行开发
开始使用 SharePoint 2013 好友动态订阅源和微博帖子进行编程、关注好友和内容（文档、网站和标签），并使用用户配置文件。
 **在本文中**
  
    
    
 [我如何使用应用程序和解决方案中的社交功能？](get-started-developing-with-social-features-in-sharepoint-2013.md#bk_HowToUseSocialFeatures)
  
    
    
 [设置开发环境](get-started-developing-with-social-features-in-sharepoint-2013.md#DevEnvironment)
  
    
    
 [社交功能的开发方案](get-started-developing-with-social-features-in-sharepoint-2013.md#DevScenarios)
  
    
    
 [使用社交功能编程的方法](get-started-developing-with-social-features-in-sharepoint-2013.md#bk_GetStarted)
  
    
    
 [用于使用社交功能编程的 API](get-started-developing-with-social-features-in-sharepoint-2013.md#SocialApis)
  
    
    
 [用于访问社交功能的应用程序权限请求](get-started-developing-with-social-features-in-sharepoint-2013.md#bkmk_AppPerms)
  
    
    
 [其他资源](get-started-developing-with-social-features-in-sharepoint-2013.md#bk_AddResources)
  
    
    


## 我如何能够使用 SharePoint 2013 应用程序和解决方案中的社交功能？
<a name="bk_HowToUseSocialFeatures"> </a>

SharePoint 2013 应用程序和解决方案中的社交功能可以帮助人员相互联系、沟通和协作以及查找、跟踪和共享重要的内容和信息。你可以添加新的社交功能或扩展 SharePoint 2013 中已有的功能。例如，你可以创建一个应用程序使你能够查找和关注与你有共同兴趣的人，创建源数据的自定义可视化，或将自定义活动发布到源。
  
    
    
本文介绍的功能与人员、源和个人网站与工作组网站上的以下功能相关。社区网站提供的丰富的论坛体验和信誉模型并不公开某个特定 API，因此你可以直接使用 SharePoint 网站并列出 API 来扩展该功能。有关详细信息，请参阅 [新建社区网站功能](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bkmk_Collab)。
  
    
    
在开始开发之前，你应知道你的代码将在什么位置运行、在什么 SharePoint 环境中运行以及它将提供什么功能。这些因素将帮助你选择要创建的应用程序类型和要使用的 API。有关可以帮助你决策的信息，请参阅 [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)、 [SharePoint 加载项与 SharePoint 解决方案比较](sharepoint-add-ins-compared-with-sharepoint-solutions.md)和 [在 SharePoint 加载项和 SharePoint 解决方案之间做出决定](deciding-between-sharepoint-add-ins-and-sharepoint-solutions.md)。
  
    
    

### 设置开发环境
<a name="DevEnvironment"> </a>

要开始使用社交功能进行开发，你需要：
  
    
    

- SharePoint Server 2013 或 SharePoint Online
    
  
- 使用 Visual Studio 2013 Office 开发人员工具
  
    
    
 ** 或**
  
    
    
Napa 的 Visual Studio 2008 或 Visual Studio 2013（仅用于开发 Office 365 开发人员网站上的 SharePoint 托管的应用程序）
    
  
要获取更多指南，请参阅 [设置 SharePoint 2013 的常规开发环境](set-up-a-general-development-environment-for-sharepoint-2013.md)和 [在 SharePoint Server 2013 中配置社会计算功能](http://technet.microsoft.com/zh-cn/library/fp161267%28v=office.15%29.aspx)。
  
    
    

### SharePoint 2013 中社交功能的开发方案
<a name="DevScenarios"> </a>

社交功能的高级开发方案包括使用好友动态订阅源、关注他人和内容（文档、网站及标记）和使用用户属性。表 1 包含文章链接，这些文章介绍了用于访问每一种方案的功能的主要 API 和常见编程任务。
  
    
    
下列文章介绍用于特定开发方案的主要 API 和编程任务：
  
    
    

-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)
    
  
-  [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中使用用户配置文件](work-with-user-profiles-in-sharepoint-2013.md)
    
  

### 在 SharePoint 2013 中使用社交功能编程的方法
<a name="bk_GetStarted"> </a>

在你设置好开发环境并选择了方案后，你可以开始使用社交功能进行编程。表 1 包含文章链接，这些文章说明如何使用社交功能执行基本的编程任务。
  
    
    

**表 1. 使用社交功能开发的操作方法文章**


|**功能区域**|**说明**|
|:-----|:-----|
| [如何：了解通过使用 SharePoint 2013 中的 .NET 客户端对象模型读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-net-client-object.md) <br/> |执行多个详细步骤，使用 .NET 客户端对象模型创建可以读取和写入好友动态订阅源的应用程序。  <br/> |
| [如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md) <br/> |执行多个详细步骤，使用 REST 服务创建可以读取和写入好友动态订阅源的应用程序。  <br/> |
| [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md) <br/> |了解如何使用 .NET 客户端对象模型创建和删除微博帖子以及检索好友动态订阅源。  <br/> |
| [如何：使用 SharePoint 2013 中的 JavaScript 对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md) <br/> |了解如何使用 JavaScript 对象模型来创建和删除微博文章以及检索好友动态订阅源。  <br/> |
| [如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md) <br/> |了解如何将 **SocialDataItem** 对象添加到微博帖子中，这些帖子在好友动态订阅源中显示为提及、标记或链接。 <br/> |
| [如何：在 SharePoint Server 2013 中的文章中嵌入图像、视频和文档](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md) <br/> |了解如何将 **SocialAttachment** 对象添加到微博帖子中，这些帖子在好友动态订阅源中显示为嵌入式图片、视频或文档。 <br/> |
| [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md) <br/> |了解如何通过 .NET 客户端对象模型使用关注好友功能。  <br/> |
| [如何：在 SharePoint 2013 中使用 JavaScript 对象模型关注好友](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md) <br/> |了解如何通过 JavaScript 对象模型使用关注好友功能。  <br/> |
| [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md) <br/> |了解如何通过 .NET 客户端对象模型使用关注内容功能。  <br/> |
| [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md) <br/> |了解如何通过 REST 服务使用关注内容功能。  <br/> |
| [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |了解如何使用 .NET 客户端对象模型检索用户配置文件属性。  <br/> |
| [如何：在 SharePoint 2013 中使用 JavaScript 对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |了解如何使用 JavaScript 对象模型检索用户配置文件属性。  <br/> |
| [如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |学习如何使用服务器对象模型创建、检索和管理用户配置文件及其属性。  <br/> |
   

### 使用 SharePoint 2013 社交功能进行编程的 API
<a name="SocialApis"> </a>

虽然应用程序和解决方案以不同的方式访问 SharePoint，但在你访问 SharePoint 后，你将以基本相同的方式使用 API。表 2 显示了对源、关注和SharePoint 2013 中的用户配置文件功能进行编程的 API 以及服务器上源文件的路径。
  
    
    

**表 2. 用于对社交功能编程的 API**


|**API 名称**|**源和路径**|
|:-----|:-----|
| [.NET 客户端对象模型](http://msdn.microsoft.com/library/9cc3f70c-78ac-4d2d-b46e-77522ee5d937%28Office.15%29.aspx) <br/> |Microsoft.SharePoint.Client.UserProfiles.dll          位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
|Silverlight 客户端对象模型  <br/> |Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll          位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
|移动设备客户端对象模型  <br/> |Microsoft.SharePoint.Client.UserProfiles.Phone.dll          位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin  <br/> |
| [JavaScript 对象模型](http://msdn.microsoft.com/library/95cb5427-8514-4e9a-8eee-7ed4b82ec01b%28Office.15%29.aspx) <br/> |SP.UserProfiles.js          位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS  <br/> |
|代表性状态传输 (REST) 服务  <br/> | [http://<网站 url>/_api/social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md)           [http://<网站 url>/_api/social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)           [http://<网站 url>/_api/SP.UserProfiles.PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> |
| [服务器对象模型](http://msdn.microsoft.com/library/87c5118c-ac0e-4bd9-a75f-7452a9eb0e41%28Office.15%29.aspx) <br/> |Microsoft.Office.Server.UserProfiles.dll          位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI  <br/> |
   

> **注释**
> 并不是客户端 API 中 Microsoft.Office.Server.UserProfiles 程序集中的所有服务器端功能均可供使用。若要查看哪些 API 可供使用，请参阅  [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) 命名空间和 [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) 命名空间。
  
    
    


## 访问 SharePoint 外接程序社交功能的应用程序权限请求
<a name="bkmk_AppPerms"> </a>

SharePoint 外接程序必须向安装用户请求访问 SharePoint 资源所需的权限。例如，发布到源的应用程序应请求该源的 **Write** 权限（最低要求）。您在 Visual Studio 中的 AppManifest.xml 文件或 Napa 中的"属性"对话框中指定您的应用程序所需的权限。
  
    
    
应用程序权限请求局限于 SharePoint 部署环境。表 3 显示了用于访问社交功能的范围名称（和相应的范围 URI）以及可用权限。有关详细信息，请参阅  [SharePoint 2013 中的外接程序权限](http://msdn.microsoft.com/library/5f7a8440-3c09-4cf8-83ec-c236bfa2d6c4%28Office.15%29.aspx)、 [SharePoint 2013 中的外接程序授权策略类型](http://msdn.microsoft.com/library/124879c7-a746-4c10-96a7-da76ad5327f0%28Office.15%29.aspx)以及 [在 SharePoint 2013 中规划应用程序权限管理](http://technet.microsoft.com/zh-cn/library/jj219576%28office.15%29.aspx)。
  
    
    

**表 3. SharePoint Server 2013 中社交功能的应用程序权限范围和可用权限**


|**范围名称**|**说明**|**可用的权限**|
|:-----|:-----|:-----|
|用户配置文件           ( `http://sharepoint/social/tenant`)  <br/> |用于访问所有用户配置文件的权限请求范围。只能更改配置文件图片；对于 SharePoint 外接程序，所有其他用户配置文件属性为只读。必须由租户管理员安装。  <br/> |读取、写入、管理、完全控制  <br/> |
|核心           ( `http://sharepoint/social/core`)  <br/> |用于访问用户关注的内容和微博功能使用的共享元数据的权限请求范围。此范围仅适用于支持关注内容的个人网站。如果应用程序安装在任何其他类型的网站上，则使用租户范围。  <br/> |读取、写入、管理、完全控制  <br/> |
|新闻源           ( `http://sharepoint/social/microfeed`)  <br/> |用于访问用户源或团队源的权限请求范围。此范围适用于支持微博的个人网站或适用于激活"网站源"功能的工作组网站。如果应用程序安装在任何其他类型的网站上，则使用租户范围。  <br/> |读取、写入、管理、完全控制  <br/> |
| `http://sharepoint/social/trimming` <br/> |此权限请求范围用于确定是否在应用程序的社交源中显示经过安全修整的内容。如果未授予这种高信任权限，有些内容（例如应用程序没有权限的文件和网站的相关活动）将从返回到应用程序的源数据中修整掉，即使用户有足够的权限也是如此。必须手动将此权限添加到应用程序的清单文件中。  <br/> |读取、写入、管理、完全控制  <br/> |
   

### 你在请求应用程序权限时，需要考虑的内容

在指定社交功能的应用程序权限时，你应了解以下注意事项：
  
    
    

- 不允许为 Office 商店 应用程序指定 **FullControl** 权限。仅允许为 Office 商店 应用程序指定 **Read**、 **Write** 和 **Manage** 权限。
    
  
- 你可以使用核心、新闻源或租户 ( `http://sharepoint/content/tenant`) 范围来指定源和关注功能的权限。租户范围表示在其中安装应用程序的整个租赁，它包括核心和新闻源范围。因此，如果你的应用程序已指定它在租户范围内需要的权限，你就不需要请求核心或新闻源范围的权限。
    
  
- 在开发期间，如果你得到一条"SocialListNotFound: 你的个人网站中没有好友动态列表"或"未找到文件"消息，请使用租户范围。如果你希望在应用程序中使用核心或新闻源范围，可以通过从应用程序目录中打开应用程序来测试权限。
    
  
- 核心范围适用于支持关注内容的个人网站。新闻源范围适用于支持微博的个人网站或适用于启用"网站源"功能的工作组网站。如果应用程序将安装到任何其他类型的网站中，则你必须使用租户范围。请参阅  [SharePoint 外接程序的租赁和部署范围](http://msdn.microsoft.com/library/1ceb3142-a7a5-453e-920f-5f953a79401a%28Office.15%29.aspx)。
    
  
- 请求用户配置文件范围的权限的应用程序必须由租户管理员安装，不能在 SharePoint Online 的 Office 365 小型企业高级版中安装。
    
  
- 如果不符合社交和微博功能的许可或功能启用要求，则用户会收到一条消息，指示无法安装该应用程序。
    
  
- 在 SharePoint 2013 外部启动的应用程序可以发出对权限（ **Full Control** 除外）的临时请求。有关详细信息，请参阅 [SharePoint 外接程序的身份验证代码 OAuth 流](http://msdn.microsoft.com/library/e89e91c7-ea39-49b9-af5a-7f047a7e2ab7%28Office.15%29.aspx)。
    
  

## 其他资源
<a name="bk_AddResources"> </a>

 **概念文章**
  
    
    

-  [SharePoint 2013 中的社交和协作功能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的社交和协作功能的面向开发人员的新增内容](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md)
    
  
-  [规划 SharePoint 2013 中的社会计算和协作](http://technet.microsoft.com/zh-cn/library/ee662531%28office.15%29.aspx)
    
  
-  [在 SharePoint Server 2013 中配置社会计算功能](http://technet.microsoft.com/zh-cn/library/fp161267%28v=office.15%29.aspx)
    
  
-  [SharePoint Server 2013 中的社会计算术语和概念](http://technet.microsoft.com/zh-cn/library/jj219804%28v=office.15%29.aspx)
    
  
 **参考文档**
  
    
    

-  [社交客户端类库](http://msdn.microsoft.com/library/9cc3f70c-78ac-4d2d-b46e-77522ee5d937%28Office.15%29.aspx)
    
  
-  [SP.UserProfiles.js JavaScript 参考](http://msdn.microsoft.com/library/80cf5436-6aa2-6f11-a782-66a04f6e2fb0%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [用户配置文件 REST API 引用](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 社交服务器类库](http://msdn.microsoft.com/library/87c5118c-ac0e-4bd9-a75f-7452a9eb0e41%28Office.15%29.aspx)
    
  
