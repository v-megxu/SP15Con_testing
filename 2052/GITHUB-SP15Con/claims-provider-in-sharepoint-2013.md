---
title: SharePoint 2013 中的声明提供程序
ms.prod: SHAREPOINT
ms.assetid: 5918d5b6-5fd6-4f41-9473-a15b1491d056
---


# SharePoint 2013 中的声明提供程序

## 声明提供程序

SharePoint Server 中的声明提供程序可发布声明并将声明打包到安全令牌（即用户令牌）中。当用户登录到 SharePoint Server 时，将对用户的令牌进行验证并使用它登录到 SharePoint。
  
    
    
SharePoint 中的声明提供程序具有两大功能：扩大和选取。
  
    
    

> **注释**
> 有关如何创建声明提供程序的信息，请参阅  [如何：在 SharePoint 2013 中创建声明提供程序](how-to-create-a-claims-provider-in-sharepoint-2013.md)。 
  
    
    


### 声明扩大

对于扩大功能，声明提供程序会在登录过程中使用声明来扩大用户令牌。利用声明扩大功能，应用程序可将其他声明扩展到用户令牌中。例如，利用基于 Windows 的登录，Active Directory 目录服务可将某个用户的所有安全组扩展到该用户的 Windows 令牌中。利用基于声明的登录，客户关系管理 (CRM) 应用程序可从 CRM 数据库扩大职责。通过将这些声明包含在用户的令牌中，可根据这些声明来授予资源的访问权。也就是说，可使用这些资源来确定某个特定用户是否能访问特定资源。
  
    
    

### 声明选取

对于选取功能，声明提供程序会提供用于在人工选取器中列出、解析、搜索和友好显示声明的功能。利用声明选取功能，应用程序可将声明显示到人工选取器中，例如在配置 SharePoint 网站或 SharePoint 服务的安全性时。 
  
    
    

## 声明提供程序使用方案

声明提供程序可用于解析不同的方案。以下是一些可使用声明提供程序解析的方案示例。
  
    
    

### 列出、解析和搜索

SharePoint Server 包含内置的声明提供程序，可用于列出、解析和搜索内置身份验证提供程序。以下是内置身份验证提供程序的示例：Windows Active Directory、基于表单的身份验证和受信任的安全声明标记语言 (SAML) 令牌颁发者（即 安全令牌服务 (STS)）。 
  
    
    
对于受信任的 SAML 令牌颁发者，SharePoint Server 不提供列出或搜索功能。当用户输入某个值时，SharePoint Server 总是会解析该值。这意味着，如果您输入 adam@contoso.com，则人工选取器会接受该值。这是因为，尚未制定用于指定 STS 如何解析、实施搜索或列出声明值的行业标准。
  
    
    
用户可以重写内置声明提供程序来实现自定义搜索、名称解析和列出功能。在诸如使用受信任的 SAML 令牌颁发者这样的方案中，这将很有用。
  
    
    

### 已验证用户或所有用户声明

SharePoint Server 包含一些特定的内置声明提供程序，它们支持对诸如已验证用户 这样的概念的使用。这也称作所有用户 声明。通过此方案，可以从给定身份验证提供程序向所有用户授权。
  
    
    

> **注释**
> 身份验证提供程序可以是 Windows Active Directory、基于表单的身份验证或受信任的 SAML 令牌颁发者（即 STS）。 
  
    
    

SharePoint Server 还包含一类系统声明提供程序，可添加分类服务使用的某些内部声明。例如，该提供程序可添加服务器场标识和应用程序池帐户。
  
    
    

### 向原始令牌添加声明

此外，可使用某些内置声明提供程序从原始"令牌"添加声明。将"令牌"一词用引号引起的原因是，某些身份验证提供程序（如基于表单的身份验证，即 ASP.NET 成员资格和角色提供程序）不提供实际令牌。在此情况下，请从概念上考虑该令牌。
  
    
    
可能必须向用户的原始声明令牌添加其他声明。在此方案中，可能需要声明提供程序。例如，可能需要使用声明提供程序向用户的原始声明令牌添加 SAP 角色。
  
    
    

### 并非来自原始令牌的标识

假定存在以下方案：您的系统对人工选取和令牌声明有一些特定的要求。在此方案中，您知道基于 Microsoft .NET Passport 唯一 ID (PUID) 和原始用户的用户标识。但与该用户相关的信息并非来自原始用户令牌，而是来自您的自定义 Active Directory。您还具有未包含在原始用户令牌（由 Windows Live ID 颁发）中的一些其他的 Active Directory 组，该用户可能属于这些组。在此方案中，可以构建一个声明提供程序以满足系统特定的需求。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的基于声明的标识](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建声明提供程序](how-to-create-a-claims-provider-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中部署声明提供程序](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

