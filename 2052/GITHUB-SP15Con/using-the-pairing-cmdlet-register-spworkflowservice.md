---
title: 使用配对 cmdlet Register-SPWorkflowService
ms.prod: SHAREPOINT
ms.assetid: 91fca6c2-60ca-4177-8560-2b310dac0e2c
---



# 使用配对 cmdlet Register-SPWorkflowService
了解如何使用 cmdlet **Register-SPWorkflowService** 成功将 SharePoint Server 2013 与工作流管理器配对。
安装和配置 Microsoft SharePoint Server 2013 以支持工作流开发需要将 SharePoint Server 2013 与工作流管理器的安装进行"配对"。在大多数情况下，使用包含在 SharePoint 安装中的 cmdlet **Register-SPWorkflowService** 可以很容易完成配对。
  
    
    

重要的是，此 cmdlet 并非对每个配对方案都有用。 **Register-SPWorkflowService** 仅在以下配对方案中可用：
- SharePoint Server 2013 和工作流管理器共同位于服务器框上的"一台计算机"服务器场。
    
  
- SharePoint Server 2013 和工作流管理器共同位于三个计算机上的"三台计算机"服务器场。（在单独计算机上搜索需要添加第四台计算机，也需要添加工作流管理器 HA。如果需要后者，则必须将它安装在所有的三台计算机上。
    
  
- "三台计算机"SharePoint Server 2013 场与一个没有共同放置在一起的工作流管理器服务器场配对。
    
  
还要注意的是， **Register-SPWorkflowService** 使用当前用户的凭据。
## Cmdlet 设计


****


|**详细信息**|**说明**|
|:-----|:-----|
|Verb  <br/> |注册  <br/> |
|Noun  <br/> |SPWorkflowService  <br/> |
|Description  <br/> |将一个 sps15short 场与一个工作流管理器场配对。您必须对每个场运行一次此 cmdlet。在运行此 cmdlet 之前，您必须将 CA 根证书安装在机器证书存储区和 SharePoint 证书存储区中。为此，需要使用 cmdlet **New-SPTrustedRootAuthority**。（请参见以下说明。）  <br/> |
|Output type  <br/> |无。  <br/> |
|Syntax  <br/> | `Register-SPWorkflowService -SPSite <URI or GUID representing an SPSite object> -WorkflowHostUri <workflow service endpoint URL> -ScopeName <string> [-PartitionMode] [-AllowOAuthHttp] [-Force]` <br/> |
   

## Cmdlet 参数



|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|SPSite          （必须）  <br/> |**SPSitePipeBind** <br/> |在用作配对端点的 SharePoint Server 场上的长久网站集的 URL。从此 URL 可以推断出用于配对的信息。  <br/> |
|WorkflowHostUri          （必须）  <br/> |String  <br/> |用于配对的工作流管理器端点的 URL。提供工作流主机 URI 以及端口号。  <br/> |
|ScopeName  <br/> |String  <br/> |工作流服务要用于标识已配对 SharePoint Server 场的名称。默认值是"SharePoint"。如果尝试将多个 SharePoint 场与一个工作流管理器场配对，您只需指定此参数。  <br/> |
|PartitionMode  <br/> |SwitchParameter  <br/> |此参数仅适用于多租户 SharePoint 场。分区模式要针对每个 SharePoint 服务指定。请注意，在运行此 cmdlet 之后，您可以在 SharePoint 场中创建多租户；因此，cmdlet 无法从现有 SharePoint 场状态中隐式推断出此参数的值。  <br/> |
|AllowOAuthHttp  <br/> |SwitchParameter  <br/> |使 OAuth 与元数据通过 HTTP 进行交换。这在测试中很有用，但在生产模式中没有用。只有在将 SharePoint 配置为支持 HTTP 时才可以使用此参数。不必将工作流管理器配置为使用 HTTP。  <br/> |
|Force  <br/> |SwitchParameter  <br/> |强制使用  _ScopeName_ 参数来创建范围，或更新与同一 _ScopeName_ 对应的范围。如果没有指定，且存在同名的范围，cmdlet 将抛出一个错误。 <br/> |
   

## 示例


```

PS> Register-SPWorkflowService -SPSite "https://myserver/mysitecollection" -WorkflowHostUri "http://workflow.example.com:12291" -ScopeName "SharePoint2" -PartitionMode -AllowOAuthHttp  -Force
```


## 其他资源
<a name="bk_addresources"> </a>


-  [安装和配置 SharePoint Server 2013 的工作流](http://technet.microsoft.com/zh-cn/library/jj658588.aspx)
    
  
-  [视频系列：在 SharePoint Server 2013 中安装和配置工作流](http://technet.microsoft.com/zh-cn/library/dn201724.aspx)
    
  
-  [Workflow Manager 1.0](http://msdn.microsoft.com/zh-cn/library/jj193528%28Azure.10%29)
    
  
