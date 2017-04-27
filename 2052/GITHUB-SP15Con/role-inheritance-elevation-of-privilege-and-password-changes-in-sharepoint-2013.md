---
title: SharePoint 2013 中的角色、继承、权限提升和密码更改
ms.prod: SHAREPOINT
ms.assetid: a72c6cad-9e3d-4d57-bf26-24cd1ad7f020
---


# SharePoint 2013 中的角色、继承、权限提升和密码更改

## 角色、角色定义和角色分配
<a name="SP15_RoleInheritance_Role"> </a>

角色由两部分组成：角色定义和角色分配。 
  
    
    
角色定义（或权限级别）是与角色关联的权限列表。权限是 SharePoint 网站中唯一可控制的操作。具有 **Read** 角色的用户可以浏览网站中的页面并查看列表中的项。不能使用权限直接管理用户权限。所有用户权限和组权限都是通过角色管理的。角色定义是绑定到特定对象的权限集合。角色定义（如， **Full Control**、 **Read**、 **Contribute**、 **Design** 或 **Limited Access**）界定在网站范围，并且在网站内的任何位置含义相同。但其在同一网站集内各网站之间的含义可能有所不同。角色定义还可以从父网站继承，就像可以继承权限一样。 
  
    
    
角色分配是角色定义、用户和组以及范围之间的关系（例如，某用户可能是列表 1 的读者，而另一个用户是列表 2 的读者）。通过角色分配表示的关系是使 SharePoint 2013 安全管理基于角色的关键。所有权限都通过角色来管理；您始终不能向用户直接分配权限，而只分配定义完善、一致且有意义的权限集合（角色定义）。通过角色分配向角色定义中添加或从中移除用户和组，以此来管理独有权限。
  
    
    
网站管理员可以使用"管理角色"页来自定义默认角色定义和创建其他自定义角色，该页列出了网站中可用的角色定义。
  
    
    

## 角色定义继承
<a name="SP15_RoleInheritance_RoleDefInheritance"> </a>

SharePoint 2013 支持继承角色定义，就像它支持继承权限那样，而取消角色定义继承也要求取消权限继承。
  
    
    
每个 SharePoint 对象都可以拥有自己的权限集，也可以从其父容器继承权限。SharePoint 2013 不支持部分继承，对象将继承其父级的所有权限，并且也可以拥有一些自己的权限。权限可以是独有的，也可以是继承的。SharePoint 2013 不支持定向继承。例如，对象只能从其父容器继承，而不能从某些其他对象或容器继承。
  
    
    
当网站继承角色定义时，这些角色是只读的，就像继承的网站中的只读权限一样。用户可通过链接导航到拥有唯一角色定义的父网站。所有新网站（包括拥有独有权限的网站）的默认设置都是从父网站继承角色定义。如果权限唯一，则角色定义可以还原为继承的角色定义，或编辑为本地角色定义。
  
    
    
根据如下规则，网站中的角色定义继承会影响权限继承：
  
    
    

- 不能继承权限，除非它还继承角色定义。
    
  
- 不能创建独有角色定义，除非它还创建独有权限。
    
  
- 不能还原为继承的角色定义，除非它也还原网站中的所有独有权限。现有权限依赖角色定义。
    
  
- 不能还原为继承的权限，除非它也还原为继承的角色定义。网站的权限始终与网站的角色定义关联。
    
  

## 管理用户标记
<a name="SP15_RoleInheritance_ManagingUserTokens"> </a>

SharePoint 从 SharePoint 数据库中提取用户标记信息。如果用户从未访问过该网站或者该用户的标记生成时间已远远超过 24 小时，则 SharePoint 会通过尝试刷新该用户所属的组列表来生成新的用户标记。 
  
    
    
如果用户帐户是一个 NT 帐户，则 SharePoint 将使用 **AuthZ** 接口来查询 **TokenGroups** 属性的 Active Directory 目录服务。如果 SharePoint 在 Extranet 模式下运行并且无权查询此属性的 Active Directory，则查询操作可能会失败。
  
    
    
如果用户帐户是一个成员资格用户，那么 SharePoint 会查询该用户所属的所有角色的 ASP.NET **RoleManager**。如果当前的可执行文件不具有适当的 .config 文件，该操作可能会失败。
  
    
    
如果 SharePoint 不能从 Active Directory 或 **<roleManager>** 获取用户的组成员身份，则新生成的标记将只包含该用户的唯一安全 ID (SID)。不会引发任何异常，但会在 ULS 服务器日志中写入一项。同时会将新的标记写入 SharePoint 数据库，以便不会在 24 小时内重新生成该标记。
  
    
    
从 SharePoint 数据库或通过生成新标记获取一个全新的标记之后，SharePoint 会将时间戳设置为当前时间，然后将该标记返回给调用方，这可以保证该标记在 24 小时之内始终是新的。 
  
    
    
将  [SPUserToken](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserToken.aspx) 对象返回给调用方后, 调用方应负责确保不在该标记过期后使用它。您可以编写一个帮助实用程序，以便通过记录标记获取时间来跟踪标记过期期限，并比较当前时间和 [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) 之间的差值。
  
    
    
如果使用一个过期的标记创建 SharePoint 网站，则会引发异常。默认标记超时值为 24 小时。可以通过  [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) 获取该值。
  
    
    

## 特权提升
<a name="SP15_RoleInheritance_ElevationOfPrivilege"> </a>

特权提升是 Windows SharePoint Services 3.0 中增加的一项功能，可让您使用更高的特权级别在代码中以编程方式执行操作。利用  [SPSecurity.RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) 方法，您可以向在帐户上下文中运行一部分代码的委托提供高于当前用户的特权。
  
    
    
 **RunWithElevatedPrivileges** 的标准用法是：
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    // Do things by assuming the permission of the "system account".
});
```

通常，若要在 SharePoint 中执行操作，您必须获取新的  [SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.aspx) 对象才能使更改生效。例如：
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    using (SPSite site = new SPSite(web.Site.ID))
    {
       // Do things by assuming the permission of the "system account".
    }
});
```

尽管特权提升提供了一种用于管理安全性的有效方法，但是应谨慎使用。不应对具有低特权的用户公开直接、不受控制的机制，以避开为他们授予的权限。
  
    
    

> **重要信息**
> 如果传递给  [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) 的方法包含任何写入操作，则调用 [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) 之前，应该调用 [SPUtility.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.ValidateFormDigest.aspx) 或 [SPWeb.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.ValidateFormDigest.aspx) 。
  
    
    


## 自动更改密码
<a name="SP15_RoleInheritance_AutomaticPasswordChange"> </a>

利用自动更改密码功能，您可以更新和部署密码，而不必在多个帐户、服务和 Web 应用程序之间执行手动密码更新任务。这样就简化了 SharePoint 2013 中的密码管理工作。您可以使用自动更改密码功能确定密码是否即将过期以及使用加密性很强的长随机字符串重置密码。
  
    
    

### 管理帐户

使用管理帐户可以实现自动更改密码功能。管理帐户提高了安全性并可确保应用程序隔离。借助管理帐户，您可以：
  
    
    

- 配置自动更改密码功能以在服务器场中的所有服务上部署密码。
    
  
- 配置运行在 SharePoint 服务器场中应用程序服务器上的 SharePoint Web 应用程序和服务，以使用不同的域帐户。
    
  
- 将管理帐户映射到服务器场中的各种服务和 Web 应用程序。
    
  
- 在 Active Directory 域服务 (AD DS) 中创建多个帐户，然后在 SharePoint 中注册每个帐户。
    
  
您还可以注册管理帐户并使 SharePoint 2013 控制帐户密码。必须向用户通知计划的密码更改和相关服务中断，但是可以基于单独配置的密码重置计划在需要时自动重置 SharePoint 服务器场、Web 应用程序和各种服务使用的帐户，并在服务器场中对其进行部署。
  
    
    
可以使用  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx) 类执行的操作包括：
  
    
    

- 更改密码
    
  
- 设置密码更改计划
    
  
- 传播密码更改
    
  
- 查明上次更改密码的时间
    
  
- 强制执行密码最小长度
    
  
有关管理帐户 API 的详细信息，请参阅以下链接：
  
    
    

-  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx)
    
  
-  [SPManagedAccount.EventProcessingOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventProcessingOptions.aspx)
    
  
-  [SPManagedAccount.EventType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventType.aspx)
    
  

## 其他资源
<a name="SP15_RoleInheritance_AdditionalResources"> </a>


-  [SharePoint 2013 中的身份验证、授权和安全性](authentication-authorization-and-security-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的授权、用户、组和对象模型](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的基于声明的标识](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的基于声明的标识和概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的配置、管理和资源](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

