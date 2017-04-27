---
title: 如何：在 SharePoint 2013 中创建声明提供程序
ms.prod: SHAREPOINT
ms.assetid: 8f3228ca-57fd-4253-a07d-abeb63298c58
---


# 如何：在 SharePoint 2013 中创建声明提供程序
了解如何创建和实现满足声明增加和声明选取的要求的 SharePoint 2013 声明提供程序。
声明提供程序发布声明并将其封装到安全令牌中。声明提供程序具有两种角色：增加和选取。
  
    
    

声明增加可让应用程序将其他声明增加到用户令牌中。例如，使用基于 Windows 的登录，Active Directory 目录服务可将用户的所有安全组增加到该用户的 Windows 令牌中。使用基于声明的登录，客户关系管理 (CRM) 应用程序可从 CRM 数据库增加角色。通过将这些声明加入用户的令牌中，可以根据这些声明授权资源。也就是说，可使用这些资源来确定某个特定用户是否能访问特定资源。
通过声明选取，可在人员选取器控件中显示声明。声明选取可让应用程序在人员选取器中呈现声明，例如配置 SharePoint 站点或 SharePoint 服务的安全性时。此功能可让您实现对声明的搜索、解析和友好显示。
  
    
    


> **注释**
> 具有声明选取功能的人员选取器有时称为声明选取器。有关详细信息，请参阅 [人员选取器和声明提供程序规划](http://technet.microsoft.com/zh-cn/library/gg602063.aspx)。 
  
    
    

若要编写声明提供程序，应首先创建一个从 **SPClaimProvider** 类派生的类。
> **提示**
> 有关代码示例和 **SPClaimProvider** 类及其成员的详细信息，请参阅 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 。有关演练、提示和代码示例，请参阅 [声明和安全：MSDN 上的技术文章和代码示例](http://msdn.microsoft.com/library/f773fd4a-53ec-4656-bd08-e6c435e6f103%28Office.15%29.aspx)。 
  
    
    


## 要求的实现
<a name="SP15_HowToCreateClaimsProvider_ReqImplementations"> </a>

以下是编写声明提供程序时必需的方法和属性。
  
    
    

### 必需

以下  [Name](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.Name.aspx) 属性是必需属性。名称在服务器场中应为唯一。
  
    
    

```cs

public abstract String Name
      
```


### 声明选取器的必需方法

通过声明选取，可在人员选取器控件中显示声明。如果要在人员选取器控件中实现声明选取， [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 类中的以下方法是必需方法。
  
    
    

```cs

protected abstract void FillSchema(SPProviderSchema schema);
     protected abstract void FillClaimTypes(List<String> claimTypes);
     protected abstract void FillClaimValueTypes(List<String> claimValueTypes);
     protected abstract void FillEntityTypes(List<String> entityTypes);

```


### 声明增加的必需方法

在用户的安全令牌中包含其他声明时，即为增加声明。如果要增加声明，您必须实现  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 类中的以下方法。
  
    
    

```cs

public abstract bool SupportsEntityInformation
      protected abstract void FillClaimsForEntity(Uri context, SPClaim entity, List<SPClaim> claims);

```


### 在声明选取器的左窗格上显示层次结构的必需方法

如果要在声明选取器的左窗格上显示层次结构，您必须实现  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 类中的以下方法。
  
    
    

```cs

public abstract bool SupportsHierarchy
     protected abstract void FillHierarchy(Uri context, String[] entityTypes, String hierarchyNodeID, int numberOfLevels, bool includeEntityData, SPProviderHierarchyTree hierarchy);

```


### 在声明选取器的键入控件中解析声明的必需方法

如果希望能够使用声明选取器的键入控件解析声明，您必须实现  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 类中的以下方法。
  
    
    

```cs

public abstract bool SupportsResolve
     protected abstract void FillResolve(Uri context, String[] entityTypes, String resolveInput, List<PickerEntity> resolved);
     protected abstract void FillResolve(Uri context, String[] entityTypes, SPClaim resolveInput, List<PickerEntity> resolved);

```


### 在声明选取器中搜索声明的必需属性和方法

如果希望能够在声明选取器中搜索声明，您必须实现  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 类中的以下属性和方法。
  
    
    

```cs

public abstract bool SupportsSearch
     protected abstract void FillSearch(Uri context, String[] entityTypes, String searchPattern, String hierarchyNodeID, int maxCount, SPProviderHierarchyTree searchTree);

```


## 有用的帮助程序方法
<a name="SP15_HowToCreateClaimsProvider_UsefulHelperMethod"> </a>

您还可以实现帮助程序方法来帮助创建  [SPClaim](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaim.aspx) 对象。
  
    
    

### 用于创建 SPClaim 对象的有用帮助程序方法

以下是您可以实现以帮助创建  [SPClaim](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaim.aspx) 对象的一个帮助程序方法。
  
    
    

```cs

protected SPClaim CreateClaim(String claimType, String value, String valueType)
```


## 其他资源
<a name="SP15_HowToCreateClaimsProvider_AdditionalResources"> </a>


-  [SharePoint 2013 中的基于声明的标识](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的声明提供程序](claims-provider-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中部署声明提供程序](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

