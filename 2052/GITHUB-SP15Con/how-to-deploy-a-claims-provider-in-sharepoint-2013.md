---
title: 如何：在 SharePoint 2013 中部署声明提供程序
ms.prod: SHAREPOINT
ms.assetid: 3a5fcedc-aa9a-4ff4-95c0-0e0a7dea9d1f
---


# 如何：在 SharePoint 2013 中部署声明提供程序
了解如何使用功能基础结构并创建继承自  [SPClaimProviderFeatureReceiver](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProviderFeatureReceiver.aspx) 的类部署 SharePoint 2013 声明。
## 在安装过程中部署声明提供程序
<a name="SP15_HowToDeployClaimsProvider_DeployingClaimsSetup"> </a>

部署声明提供程序的最简单的方法是使用功能基础结构。为此，请首先定义一个功能和一个从  [SPClaimProviderFeatureReceiver](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProviderFeatureReceiver.aspx) 类派生的功能接收器，并重写基本属性。
  
    
    
以下是操作方法示例。
  
    
    



```cs

public class MyClaimProviderFeatureReceiver : SPClaimProviderFeatureReceiver
    {
        public override string ClaimProviderAssembly { get { return typeof(MyClaimProvider).Assembly.FullName; } }
        public override string ClaimProviderType { get { return typeof(MyClaimProvider).FullName; } }
        public override string ClaimProviderDisplayName
        {
            get
            {
                return StringResourceManager.GetString(MyLocalizedClaimProviderName);
            }
        }
        public override string ClaimProviderDescription
        {
            get
            {
                return StringResourceManager.GetString(MyLocalizedClaimProviderDescription);
            }
            }
    }
```


## 使用功能基础结构部署声明提供程序
<a name="SP15_HowToDeployClaimsProvider_DeployingClaimsFeature"> </a>

以下示例演示如何定义功能和从  [SPClaimProviderFeatureReceiver](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProviderFeatureReceiver.aspx) 派生的功能接收器，以及如何重写基本属性。
  
    
    

```cs

// Sample claims provider feature receiver class through which
// the sample claims provider registers itself 
// with the Microsoft.SharePoint.Administration.Claims.SPClaimProviderManager class.

using System;
using Microsoft.SharePoint.Administration;
using Microsoft.SharePoint.Administration.Claims;

namespace MySample.Sample.Server.SampleClaimsProvider
{
    /// <summary>
    /// The NameIdentifierClaimProviderFeatureReceiver class is a feature receiver class
    /// that registers the claims provider with the claims provider manager.
    /// </summary>
    
    [Microsoft.SharePoint.Security.SharePointPermission(System.Security.Permissions.SecurityAction.Demand, ObjectModel = true)]
    public sealed class NameIdentifierClaimProviderFeatureReceiver : SPClaimProviderFeatureReceiver
    {
        #region Private Methods
        /// <summary>
        /// Because use of base keyword can lead to unverifiable code inside a lambda expression, 
        /// this function is created as a wrapper for the base.FeatureActivated function.
        /// This function gets called in the following lambda expression.
        /// </summary>
        
        /// <param name="properties">Represents the properties of a feature activation.</param>
        /// <returns> void </returns>

        private void ExecBaseFeatureActivated(Microsoft.SharePoint.SPFeatureReceiverProperties properties)
        {
            base.FeatureActivated(properties);
        }
        #endregion Private Methods

        #region Public Method\\Properties
        /// <summary>
        /// Gets the fully qualified name of the MySample.Sample.Server.SampleClaimsProvider assembly.
        /// </summary>
        
        /// <returns>String representing fully qualified name of the MySample.Sample.Server.SampleClaimsProvider
        /// assembly.</returns>
        public override string ClaimProviderAssembly
        {
            get{ return typeof(SampleNameIdClaimProvider).Assembly.FullName; }
        }

        /// <summary>
        /// Gets the fully qualified name of the claims provider type, including the namespace of the type. 
        /// </summary>
        /// <returns>String representing the fully qualified name of the 
        ///SampleNameIdClaimProvider class.</returns>
        public override string ClaimProviderType
        {
            get{ return typeof(NameIdentifierClaimProvider).FullName; }
        }

        /// <summary>
        /// Gets the display name of the claims provider.
        /// </summary>
        
        /// <returns>String representing display name of the claim provider.</returns>
        public override string ClaimProviderDisplayName
        {
            get{ return "Sample NameId Claim Provider"; }
        }

        /// <summary>
        /// Gets the description about the claims provider. 
        /// </summary>
        
        /// <returns>String representing the description about the SampleClaimProvider.</returns>
        public override string ClaimProviderDescription
        {
            get
            {
                return "This feature adds SampleNameId claim type in the SAML token created by the STS.";
            }
        }

        /// <summary>
        /// This methods gets called after the activation of the feature.
        /// </summary>
        
        /// <param name="properties">Represents the properties of a feature activation<./param>
        /// <returns>void.</returns>
        public override void FeatureActivated(Microsoft.SharePoint.SPFeatureReceiverProperties properties)
        {     
            {
                ExecBaseFeatureActivated(properties);
            }            
        }
        #endregion Public Method\\Properties
    }
}

```


## 其他资源
<a name="SP15_HowToDeployClaimsProvider_AdditionalResources"> </a>


-  [SharePoint 2013 中的基于声明的标识](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的声明提供程序](claims-provider-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中创建声明提供程序](how-to-create-a-claims-provider-in-sharepoint-2013.md)
    
  

