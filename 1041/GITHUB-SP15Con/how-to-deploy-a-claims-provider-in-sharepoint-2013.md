---
title: [方法] SharePoint 2013 でクレーム プロバイダーを展開する
ms.prod: SHAREPOINT
ms.assetid: 3a5fcedc-aa9a-4ff4-95c0-0e0a7dea9d1f
---


# [方法] SharePoint 2013 でクレーム プロバイダーを展開する
機能のインフラストラクチャを使用し、 [SPClaimProviderFeatureReceiver](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProviderFeatureReceiver.aspx) から継承するクラスを作成することによって、SharePoint 2013 クレーム プロバイダーを展開する方法を説明します。
## セットアップの一環としてクレーム プロバイダーを展開する
<a name="SP15_HowToDeployClaimsProvider_DeployingClaimsSetup"> </a>

クレーム プロバイダーを最も簡単に展開するには、機能のインフラストラクチャを使用します。これを行うためにはまず [SPClaimProviderFeatureReceiver](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProviderFeatureReceiver.aspx) クラスから派生する機能レシーバーを定義し、基本プロパティを上書きします。
  
    
    
次に、これを行う方法の例を示します。
  
    
    



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


## 機能インフラストラクチャを使用してクレーム プロバイダーを展開する
<a name="SP15_HowToDeployClaimsProvider_DeployingClaimsFeature"> </a>

以下のサンプルでは、 [SPClaimProviderFeatureReceiver](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProviderFeatureReceiver.aspx) から派生した機能および機能レシーバーを定義し、基本プロパティを上書きする方法を示します。
  
    
    

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


## その他の技術情報
<a name="SP15_HowToDeployClaimsProvider_AdditionalResources"> </a>


-  [SharePoint 2013 でのクレームベース ID](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクレーム プロバイダー](claims-provider-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 でクレーム プロバイダーを作成する](how-to-create-a-claims-provider-in-sharepoint-2013.md)
    
  

