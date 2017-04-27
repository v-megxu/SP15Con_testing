

# 在 SharePoint 应用程序中使用 SharePoint 2013 对象模型
您所在市场中可能尚未推出 Office 商店或 SharePoint 商店。
  
    
    
![概念概述主题](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
简要介绍使用 SharePoint 2013 对象模型来支持高级工作流开发方案。
 * **适用范围：*** 
  
    
    


|||
|:-----|:-----|
|**本文内容**          [使用工作流对象模型](#bk_usewfom)           [SharePoint 2013 工作流：SharePoint 应用程序中的工作流 OM](#bk_codesample)           [其他资源](#bk_addresources) <br/> |
  
    
    
![相关代码段和示例应用程序](images/mod_icon_links_samples.png)
  
    
    

  
    
    
 <br/>  [SharePoint 2013 工作流：在 SharePoint 应用程序中使用工作流对象模型](http://code.msdn.microsoft.com/SharePoint-2013-workflow-050f5211) <br/> |
   

## 使用工作流对象模型
<a name="bk_usewfom"> </a>

新的 SharePoint 2013 工作流对象模型支持高级方案，以利用新 SharePoint 工作流平台的功能。使用对象模型，您可以部署工作流和管理工作流实例，并且其支持将消息传递到工作流实例。
  
    
    
SharePoint 2013 工作流对象模型以多种形式提供。有 SharePoint Server 对象模型（属于托管 API）和客户端对象模型（或 CSOM）；也有 JavaScript 对象模型 (JSOM) 和 SharePoint 代表性状态传输 (REST) API。 
  
    
    
SharePoint 承载的应用程序可以使用 SharePoint JSOM 和 SharePoint REST API 来访问工作流对象模型。供应商承载的应用程序和自动承载的应用程序可以使用 SharePoint CSOM、SharePoint JSOM 以及 SharePoint REST API 来访问工作流对象模型。有关这些承载选项的详细信息，请参阅 [为开发和托管 SharePoint 外接程序选择模式](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)。
  
    
    
有关对您的编程任务选择最佳 API 的详细信息，请参阅 [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    

## SharePoint 2013 工作流：SharePoint 应用程序中的工作流 OM
<a name="bk_codesample"> </a>

"SharePoint 2013 工作流: SharePoint 应用程序中的工作流 OM" 代码示例是交互的寄宿于 SharePoint 的应用程序的示例，该应用程序使用 SharePoint 工作流 JSOM 将工作流定义部署到应用程序 Web 和"父级 Web"（即寄宿该应用程序的 SharePoint Web）。
  
    
    
您可以在以下位置找到代码示例： [SharePoint 2013 工作流：SharePoint 应用程序中的工作流 OM](http://code.msdn.microsoft.com/SharePoint-2013-workflow-050f5211).
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的工作流入门](get-started-with-workflows-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 工作流模板](sharepoint-2013-workflow-samples.md)
    
  
-  [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [使用 Visual Studio 开发 SharePoint 2013 工作流](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  