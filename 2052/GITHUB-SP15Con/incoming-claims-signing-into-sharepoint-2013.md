---
title: 传入声明：登录到 SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 08c687aa-e485-4269-aea8-4333da3588a5
---


# 传入声明：登录到 SharePoint 2013

## 登录到 SharePoint

当用户登录到 SharePoint Server 时，将对用户的令牌进行验证并使用它登录到 SharePoint。用户的令牌是由声明提供程序颁发的安全令牌。
  
    
    

> **注释**
> 有关单个 SharePoint 场声明身份验证和场间 SharePoint 声明身份验证的信息，请参阅 TechNet 上的 [规划声明身份验证](http://technet.microsoft.com/zh-cn/library/cc262350.aspx)。 
  
    
    


### Windows 声明模式登录

在 Windows 声明模式登录中，通过协商 (NTLM/Kerberos) 使用集成 Windows 身份验证质询执行登录过程。但是，在创建  [WindowsIdentity](https://msdn.microsoft.com/library/System.Security.Principal.WindowsIdentity.aspx) 对象（表示 Windows 用户）后，SharePoint Server 会将 [WindowsIdentity](https://msdn.microsoft.com/library/System.Security.Principal.WindowsIdentity.aspx) 对象转换为 [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) 对象（表示基于声明的用户表示形式）。
  
    
    
SharePoint Server 然后进行声明扩充并处理由 SharePoint Server 颁发的结果令牌。这意味着 SharePoint Server 中的某些功能（例如，对服务应用程序和自定义声明提供程序的多用户支持）可以正常运行，即使客户端认为 SharePoint Server 处于本机 Windows 登录模式。Windows 声明模式登录体验是 SharePoint Server 中内置的默认登录。
  
    
    
所有声明登录类型都依赖于被动登录。被动登录是使用 Windows 质询执行的，不过是在通过 302 重定向转到的单独登录页中进行的。当启用了多个登录方法并且用户必须在受支持声明提供程序之间进行选择时，此模式非常有用。Win32 客户端必须支持在 Office 客户端实施的基于表单的身份验证。一些 Office 客户端遵循不同的协议。
  
    
    

### SAML 被动登录模式

在安全声明标记语言 (SAML) 被动登录中，当用户登录时，客户端（可能是网页）将被重定向到指定的声明提供程序（例如，Windows Live ID 声明提供程序）。当该声明提供程序对用户进行身份验证后，SharePoint Server 将获得声明提供程序提供的 SAML 令牌，处理 SAML 令牌，然后扩充声明。
  
    
    
对于基于 SAML 的声明提供程序（如 Active Directory 联合身份验证服务 (ADFS) 声明提供程序和 Windows Live ID 声明提供程序），使用 SAML 被动登录模式进行登录是唯一受支持的方式。SAML 被动登录是 SharePoint 联机标识模型。
  
    
    

> **注释**
> SAML 被动登录描述登录过程。当 Web 应用程序的登录配置为接受来自受信任登录提供程序的令牌时，这种类型的登录称为 SAML 被动登录。受信任登录提供程序是 SharePoint 信任的外部（即 SharePoint 的外部）安全令牌服务 (STS)。 
  
    
    

Win32 客户端必须支持在 Office 客户端实施的基于表单的身份验证。
  
    
    

### ASP.NET 成员资格和角色被动登录

在 ASP.NET 成员资格和角色被动登录中，登录通过将客户端重定向到承载 ASP.NET 登录控件的网页来执行。创建表示用户标识的标识对象后，SharePoint Server 会将它转换为  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) 对象（它表示用户基于声明的表示形式）。
  
    
    
SharePoint Server 然后进行声明扩充。Win32 客户端必须支持在 Office 客户端实施的基于表单的身份验证。
  
    
    

### Windows 经典模式登录

Windows 经典模式登录在此版本中已被弃用。在 Windows 经典模式登录中，通过协商 (NTLM/Kerberos) 使用集成 Windows 身份验证质询执行登录过程。不进行声明扩充，因此用户使用此模式登录时，一些功能（例如，对服务应用程序和自定义声明提供程序的多用户支持）不起作用。
  
    
    
一些服务应用程序可能还会要求使用声明模式以获得某些功能。
  
    
    

### 匿名访问

可以对 Web 应用程序启用匿名访问。Web 应用程序中网站的管理员可以选择允许匿名访问。如果匿名用户要获取对受保护资源的访问权限，他们可以单击登录按钮以提交其凭据。
  
    
    
SharePoint Server 然后进行声明扩充。Win32 客户端必须支持在 Office 客户端实施的基于表单的身份验证。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的基于声明的标识](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的声明提供程序](claims-provider-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建声明提供程序](how-to-create-a-claims-provider-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中部署声明提供程序](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

