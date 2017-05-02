---
title: SharePoint 2013 中的身份验证、授权和安全性
ms.prod: SHAREPOINT
ms.assetid: 8734790c-eb75-4d78-9604-7cc23b33b693
---


# SharePoint 2013 中的身份验证、授权和安全性

## SharePoint 2013 中有关身份验证的新增内容
<a name="SP15_AuthenticationAuthorizationSecurity_WhatsNew"> </a>

以下是添加到 SharePoint 2013 中的一些新增内容： 
  
    
    

- 用户登录
    
  - SharePoint 2013 继续为声明和经典身份验证模式提供支持。声明身份验证是 SharePoint 2013 中的默认身份验证选项。经典模式的身份验证已弃用，并且仅可通过使用 Windows PowerShell 加以管理。SharePoint 2013 中的许多功能都需要声明模式。 
    
  
  - SharePoint 2010 中的 **MigrateUsers** 方法现已弃用，它不再是迁移帐户的正确方式。要迁移帐户，请使用称为 `Convert-SPWebApplication` 的新 Windows PowerShell cmdlet。有关详细信息，请参阅 [在 SharePoint 2013 中从经典模式身份验证迁移到基于声明的身份验证](http://technet.microsoft.com/zh-cn/library/gg251985.aspx)。
    
  
  - 注册声明提供程序的要求已取消。但是，您必须预先配置声明类型。您可以为声明类型选择字符，并且对于声明类型的顺序没有强制要求。
    
  
  - SharePoint 2013 使用 Windows Server AppFabric Caching 跟踪新的分布式缓存服务中的 **FedAuth** cookie。
    
  
  - 提供了更多的日志记录以便有助于对身份验证问题进行疑难解答。 
    
  
- 服务和应用程序身份验证
    
  - 在 SharePoint 2013中，现在您可以创建适用于 SharePoint 的应用程序。SharePoint 外接程序 具有其自身的身份，并且与安全主体（亦称 应用程序主体）关联。与用户和组一样，应用程序主体拥有某些特定的许可权限和权利。 
    
  
  - 在 SharePoint 2013中，服务器到服务器的安全令牌服务 (STS) 为服务器到服务器的身份验证提供访问令牌。服务器到服务器 STS 可让临时访问令牌访问其他应用程序服务（如 Exchange Server 2013 和 Microsoft Lync 2013）及SharePoint 2013 的应用程序。
    
  

## 身份验证和授权
<a name="SP15_AuthenticationAuthorizationSecurity_AuthenticationAndAuthorization"> </a>

SharePoint 2013 支持用户在网站、列表、列表或库文件夹及项级别的访问安全性。安全管理在所有级别都是基于角色的，通过一致的基于角色的用户界面和分配有关对象的许可权限的对象模型在整个 SharePoint 2013 平台提供连贯的安全管理。因此，列表级别、文件夹级别或项级别的安全性实现了与网站级别的安全性相同的用户模型，使其更易于管理整个网站的用户权限和组权限。SharePoint 2013 还支持对于包含在列表和文档库内的文件夹和项的唯一许可权限。
  
    
    

> **注释**
> 有关与 SharePoint 外接程序相关的授权信息，请参阅  [SharePoint 外接程序的授权和身份验证](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx)。 
  
    
    

授权是指通过其 SharePoint 2013 可通过确定哪些用户可以对给定对象指定特定操作来为网站、列表、文件夹或项提供安全性的流程。 授权流程假定用户已经过身份验证（指通过其 SharePoint 2013 识别当前用户的流程）。SharePoint 2013 不实现其自身的身份验证或身份管理系统，而是依赖外部系统（Windows 身份验证或非 Windows 身份验证）。
  
    
    
SharePoint 2013 支持以下类型的身份验证：
  
    
    

- **Windows：** 所有 Internet 信息服务 (IIS) 和 Windows 身份验证集成选项（包括 Basic、Digest、Certificates、Windows NT LAN 管理器 (NTLM) 和 Kerberos）均受到支持。 Windows 身份验证允许 IIS 为 SharePoint 2013 执行身份验证。
    
    有关使用 Windows 声明模式登录到 SharePoint 的信息，请参阅 [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)。
    
    > **重要信息**
      >  有关挂起模拟的信息，请参阅 [避免挂起调用者模拟](http://msdn.microsoft.com/zh-cn/library/ff407852.aspx)。 
- **ASP.NET 表单：** 支持使用可插入的基于 ASP.NET 表单的身份验证系统的非 Windows 身份管理系统。此模式可让 SharePoint 2013 处理各种身份管理系统，包括外部定义的组或角色，如轻型目录访问协议 (LDAP) 和轻型数据库身份管理系统。表单身份验证可让 ASP.NET 为 SharePoint 2013 执行身份验证，通常涉及重定向到登录页。在 SharePoint 2013 中，ASP.NET 表单仅在声明身份验证下受到支持。必须在为声明配置的 Web 应用程序内注册表单提供程序。
    
    有关使用 ASP.NET 成员资格和角色被动登录来登录到 SharePoint 的信息，请参阅 [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)。
    
  

> **注释**
> SharePoint 2013 不支持使用区分大小写的成员资格提供程序。它对数据库中的所有用户使用不区分大小写的 SQL 存储，而不考虑成员资格提供程序。 
  
    
    


## 基于声明的身份和身份验证
<a name="SP15_AuthenticationAuthorizationSecurity_ClaimsBasedIdentity"> </a>

基于声明的身份是 SharePoint 2013 中的身份模型。该模型的功能包括对基于 Windows 的系统和不基于 Windows 系统中的用户的身份验证、多身份验证类型、更强的实时身份验证、一组更广泛的主体类型和应用程序之间的用户身份委派。
  
    
    
用户登录到 SharePoint 2013 时，将对用户的令牌进行验证，然后用于登录到 SharePoint。用户的令牌是由声明提供程序颁发的安全令牌。以下是受支持的登录或访问模式：
  
    
    

- Windows 声明模式登录（默认状态下）
    
  
- SAML 被动登录模式
    
  
- ASP.NET 成员资格和角色被动登录
    
  
- Windows 经典模式登录（此版本中已弃用）
    
  

> **注释**
> 有关登录到 SharePoint 和不同登录模式的详细信息，请参阅 [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)。 
  
    
    

当您构建声明感知应用程序时，用户会以一组声明的形式向您的应用程序提供标识。其中一个声明可能是用户名，另一个可能是电子邮件地址。意在所配置的外部身份系统可给予您的应用程序其所需的有关用户每次请求的所有信息，以及您的应用程序收到的身份数据来自受信任的来源的密码保证。
  
    
    
在该模型下，单一登录更容易实现，并且您的应用程序不再负责执行下列任务：
  
    
    

- 对用户进行身份验证
    
  
- 存储用户帐户和密码
    
  
- 调用企业目录以查找用户标识详细信息
    
  
- 与来自其他平台或公司的标识系统集成
    
  
在该模型下，您的应用程序基于用户提供的声明做出与标识相关的决定。决策可以是使用用户的名字的简单应用程序个性化，也可以是授权用户访问应用程序中更高价值的功能和资源等等。
  
    
    

> **注释**
> 有关基于声明的标识和声明提供程序的详细信息，请参阅 [SharePoint 2013 中的基于声明的标识和概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)和 [SharePoint 2013 中的声明提供程序](claims-provider-in-sharepoint-2013.md)。 
  
    
    


## 基于表单的身份验证
<a name="SP15_AuthenticationAuthorizationSecurity_FormsBasedAuthentication"> </a>

在 SharePoint 2013 中，基于表单的身份验证通过实现成员资格提供程序和角色管理器来提供自定义身份管理，前者定义用于标识各个用户并对其进行身份验证的接口，而后者定义将各个用户分组到逻辑组或角色的接口。在 SharePoint 2013 中，成员资格提供程序必须实现必需的  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) 方法。给定用户名后，角色提供程序系统将返回该用户所属的角色列表。
  
    
    
成员资格提供程序负责通过使用  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) 方法（现在 SharePoint 2013 中有要求）来验证凭据信息。但是实际用户令牌由安全令牌服务 (STS) 创建。STS 从成员资格提供程序所验证的用户名和与成员资格提供程序所提供的用户名关联的组成员资格集合创建用户令牌。
  
    
    

> **注释**
> 有关 STS 的详细信息，请参阅  [SharePoint 2013 中的基于声明的标识和概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)。 
  
    
    

角色管理器是可选的。如果自定义身份验证系统不支持组，就不需要角色管理器。SharePoint 2013 在每个 URL 区域 ( [SPUrlZone](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPUrlZone.aspx) ) 支持一个成员资格提供程序和一个角色管理器。 ASP.NET 表单角色没有与其关联的固有权限。相反，SharePoint 2013 通过其策略和授权向表单角色分配权限。在 SharePoint 2013 中，基于表单的身份验证与基于声明的身份模型相集成。如果您需要额外增大以绕过每个 URL 区域具有一个角色提供程序的限制，您可以依赖声明提供程序。
  
    
    

> **注释**
> 有关基于声明的标识和声明提供程序的详细信息，请参阅 [SharePoint 2013 中的基于声明的标识和概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)和 [SharePoint 2013 中的声明提供程序](claims-provider-in-sharepoint-2013.md)。 
  
    
    

在 ASP.NET 成员资格和角色被动登录中，登录是通过将客户端重定向到承载 ASP.NET 登录控件的 Web 页进行的。创建了表示用户身份的身份对象后，SharePoint 2013 会将其转换成  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) 对象（该对象是基于声明的用户表现形式）。
  
    
    

> **注释**
> 有关登录到 SharePoint 中的详细信息，请参阅 [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)。 
  
    
    

SharePoint 2013 使用标准 ASP.NET 角色提供程序界面来收集有关当前用户的组信息。就身份验证而言，角色和组是同一回事：一种将用户分组成逻辑集合以便进行授权的方式。每个 ASP.NET 角色都被 SharePoint 2013 视作一个域组。 
  
    
    
有关 ASP.NET 提供的可插入身份验证框架的信息，请参阅 ASP.NET 开发人员文档。
  
    
    

> **注释**
> 有关基于表单的身份验证的详细信息，请参阅  [SharePoint 产品和技术中的表单身份验证（第 1 部分）：简介](http://msdn.microsoft.com/library/e5efd4d7-b369-49f0-a6f7-431d21daff20%28Office.15%29.aspx)。 
  
    
    


## 其他资源
<a name="SP15_AuthenticationAuthorizationSecurity_AdditionalResources"> </a>


-  [SharePoint 2013 中的授权、用户、组和对象模型](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的角色、继承、权限提升和密码更改](role-inheritance-elevation-of-privilege-and-password-changes-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的基于声明的标识](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的基于声明的标识和概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的配置、管理和资源](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

