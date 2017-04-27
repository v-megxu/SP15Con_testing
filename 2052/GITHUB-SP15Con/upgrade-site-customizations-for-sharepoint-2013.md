---
title: 升级 SharePoint 2013 的网站自定义
ms.prod: SHAREPOINT
ms.assetid: 4b515860-69ae-4af8-8013-cd071c0ddca6
---


# 升级 SharePoint 2013 的网站自定义
了解从 SharePoint 2010 网站自定义升级到 SharePoint 2013 过程中的潜在问题并获取相关建议。
SharePoint 2013 对用户界面 (UI) 引入了重大更改，让您可以使用更快、更灵活的组件来自定义网站。但是，当您从 SharePoint 2010 升级时，您可能会遇到一些内置在 SharePoint 2013 中用于处理 UI 改进的新组件的问题
  
    
    

本文有助于 SharePoint 开发人员和负责管理从 SharePoint 2010 升级的人员发现升级后的潜在问题。
## 升级的一般建议

一般来说，我们建议您创建一个新的"评估"网站，在此网站上，您可以针对 SharePoint 2013 环境测试您的自定义并对其重新设计。有关创建评估网站集的详细信息，请参阅 [升级网站集](http://office.microsoft.com/zh-cn/office365-sharepoint-online-enterprise-help/upgrade-a-site-collection-HA102865473.aspx?CTT=5&amp;origin=HA104034491)。
  
    
    

### 升级自定义组件

表 1 列出了升级后可能出现的自定义组件问题和有关如何解决这些问题的信息。
  
    
    

**表 1. 受升级到 SharePoint 2013 的过程影响的自定义组件**


|**如果已对以下项进行了自定义**|**您可能会遇到以下问题**|
|:-----|:-----|
|CSS 样式  <br/> |在升级期间，您的网站将恢复到 default.master 页面提及过的 CSS 文件。因此，您对页面外观所做的任何自定义都将发生改变，页面会呈现出默认安装时提供的默认样式。  <br/> |
|主题  <br/> |对于 SharePoint 2010，您可能已创建了用于为整个网站定义企业品牌的自定义主题。您将其创建为 .thmx 文件，它们可上载至网站集，并可供管理员使用。  <br/> 在 SharePoint 2013 中，主题设置引擎经过了彻底的重新设计，变得更为灵活和强大，并可为将来的升级提供便利。这次重新设计的结果是，不支持将主题从 SharePoint 2010 升级到 SharePoint 2013，需要您在 SharePoint 2013 中重新创建这些主题。  <br/> |
|Web 模板  <br/> |SharePoint 2010 中引入了 Web 模板，用来提供一种打包功能、布局、样式和其他组件的方式，可供您在创建新的 Web 时使用。它们创建网站定义的功能相似，但您可以通过 Web 模板添加发布功能。  <br/> 由于 SharePoint 2013 中进行了更改，因此，您的自定义 Web 模板在升级后无法立即生效。  <br/> 若要查看 Web 模板中发生的更改并修复由此产生的问题，请参阅 [升级 SharePoint 2013 的 Web 模板](upgrade-web-templates-for-sharepoint-2013.md)，获取建议和最佳实践。  <br/> |
|母版页  <br/> |在升级期间，任何对已创建自定义母版页的引用都会恢复到 default.master 页。这可能会导致 SharePoint 因自定义页面引用了缺失组件而出现错误。  <br/> 若要修复这个问题，您必须更改对所有自定义母版页的引用。  <br/> |
   

## 其他资源
<a name="bk_addresources"> </a>


-  [规划网站集升级](https://technet.microsoft.com/zh-cn/library/ff191199.aspx)
    
  
-  [升级到 SharePoint 2013 时可能出现的外观方案问题](http://office.microsoft.com/zh-cn/office365-sharepoint-online-enterprise-help/branding-issues-that-may-occur-when-upgrading-to-sharepoint-2013-HA104052656.aspx?CTT=5&amp;origin=HA104034491)
    
  
-  [升级网站集](http://office.microsoft.com/zh-cn/office365-sharepoint-online-enterprise-help/upgrade-a-site-collection-HA102865473.aspx?CTT=5&amp;origin=HA104034491)
    
  
-  [网站集升级问题故障排除](http://office.microsoft.com/zh-cn/office365-sharepoint-online-enterprise-help/troubleshoot-site-collection-upgrade-issues-HA104037311.aspx?CTT=5&amp;origin=HA104034491)
    
  

