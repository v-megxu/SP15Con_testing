---
title: 在 SharePoint 2013 中生成场解决方案
ms.prod: SHAREPOINT
ms.assetid: 96c32f08-ad93-49af-b8d0-9d194a48cc79
---


# 在 SharePoint 2013 中生成场解决方案
概览有关使用服务器场解决方案开发、封装并将管理扩展部署到 SharePoint 2013 中的文档。
## 什么是服务器场解决方案？
<a name="WhatAreFarmSolutions"> </a>

不同于其他 Windows 应用程序和平台，SharePoint 2013 具有其自己的将扩展安装到 SharePoint 管理功能的系统。不会涉及 MSI 文件或 ClickOnce 技术。相反，扩展中的程序集、XML 和其他文件将被绑定到一个名为解决方案包的文件。解决方案包具有基于 .cab 的格式，但是为 .wsp 的文件扩展名。该包可包含"SharePoint 功能"及其所有子组件和"功能"中未部署的某些类型的组件。服务器场管理员将这些包上载到服务器场范围的存储位置，在该位置可以部署这些包并且可激活其"功能"。
  
    
    
不同于 SharePoint 外接程序，服务器场解决方案包含部署到 SharePoint 服务器并调用 SharePoint 服务器对象模型的代码。这些程序集总是以完全信任状态运行。而且，除了 SharePoint 外接程序中"功能"的网站作用域外，服务器场解决方案中"功能"的作用域还涉及网站集、Web 应用程序或整个服务器场。 服务器场解决方案的这些方面有时使得服务器场管理员不愿意安装它们，除非它们来自知名和受信任的来源。为此，主要供最终用户使用的 SharePoint 扩展应作为 SharePoint 外接程序（而不是服务器场解决方案）开发。服务器场解决方案应用于自定义 SharePoint 管理功能，如自定义计时器作业、自定义 Windows PowerShell cmdlet 和扩展管理中心。有关 SharePoint 外接程序的好处和使用服务器场解决方案的详细信息，请参阅 [SharePoint 加载项与 SharePoint 解决方案比较](sharepoint-add-ins-compared-with-sharepoint-solutions.md)。
  
    
    

## 针对服务器场解决方案的开发人员文档指南
<a name="Guide"> </a>

自从 SharePoint 2010 以来，服务器场解决方案的开发一直很少发生改变，因此本节包含指向 SharePoint 2010 SDK 的链接。为了避免混淆，使用 SharePoint 2010 SDK 开发 SharePoint 2013 时始终切记以下几点：
  
    
    

- 在 SharePoint 2010 SDK 中你将看到很多对"沙盒解决方案"的引用。具有自定义代码的沙盒解决方案在 SharePoint 2013 中已弃用。"无代码"沙盒解决方案仍然可行。
    
  
- 我们建议服务器场解决方案主要用于 SharePoint 2010 中不适用的管理扩展。因此，SharePoint 2010 SDK 中的许多示例和其他文档可能是有关作为服务器场解决方案部署的最终用户扩展。
    
  
- SharePoint 2010 SDK 中的术语"服务器端"或"服务器代码"是指调用 SharePoint 服务器对象模型的代码。这些术语 *不是*  指在远程 Web 服务器（即，SharePoint 服务器场外部的 Web 服务）上运行的代码。在 SharePoint 2010 和 SharePoint 2013 中，从远程 Web 服务器调用 SharePoint 的代码始终使用一个 SharePoint *客户端*  对象模型。在 SharePoint 2010 SDK 中，此类代码将被成为"客户端侧"或"客户端代码"。
    
  
- SharePoint 2010 的服务器场解决方案中的程序集可用自定义访问安全 (CAS) 策略部署。SharePoint 2013 中将忽略此类策略；SharePoint 2013 的服务器场解决方案中的所有程序集都以完全受信任状态运行。
    
  

### 封装和部署

封装、安装、更新和本地化服务器场解决方案 的基本原理在 [解决方案概述](http://msdn.microsoft.com/library/1983cab9-4b29-494a-a62a-0f8e83908744%28Office.15%29.aspx)和 [场解决方案](http://msdn.microsoft.com/library/845f7524-b9ff-412b-aa29-3afacda91100%28Office.15%29.aspx) 节点中有说明。有关开发特定 SharePoint 组件以便纳入服务器场解决方案中的内容在 SharePoint 2010 SDK 的相关节点中有说明。服务器场解决方案中的大多数组件应封装在一个或多个"SharePoint 功能"中。有关设计和创建"功能"的信息，请参阅 SharePoint 2010 SDK 的 [使用功能](http://msdn.microsoft.com/library/ce5f5ce5-1429-439e-9261-2c4ba9788cc1%28Office.15%29.aspx)节点。.
  
    
    

### 管理扩展

有关扩展 SharePoint 服务器场中的管理功能的指导载于 SharePoint 2010 SDK 的  [Windows SharePoint Services 管理](http://msdn.microsoft.com/library/cdcc1b8a-4144-446f-b471-03d4a754a8ab%28Office.15%29.aspx)节点。在该节点中，你可以找到有关扩展管理中心、创建自定义 Windows PowerShell cmdlets、自定义升级和迁移、自定义备份以及自定义 SharePoint 事件日志记录的说明。第一节中说明了如何自定义测量 SharePoint 服务器场的运行状况和性能的系统。有关创建自定义计时器作业的说明，请参阅 [如何：在所有 Web 服务器上运行代码](http://msdn.microsoft.com/library/1bbb11b4-a342-4bed-9e7a-b8b13edd0ccc%28Office.15%29.aspx)。
  
    
    

## 本节中
<a name="Guide"> </a>

本节中的主题介绍了 SharePoint 解决方案的开发方法 *已经*  发生怎样的改变。
  
    
    

-  [如何：使用客户端呈现自定义字段类型](how-to-customize-a-field-type-using-client-side-rendering.md)
    
  
-  [SharePoint 2013 中的 URL 和标记](urls-and-tokens-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 解决方案中的虚拟目录](virtual-directories-in-sharepoint-2013-solutions.md)
    
  

## 其他资源
<a name="SP15buildfarm_addlresources"> </a>


-  [SharePoint 2013 中的编程模型](programming-models-in-sharepoint-2013.md)
    
  

