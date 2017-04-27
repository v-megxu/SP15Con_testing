---
title: [方法] SharePoint 2013 でクレーム プロバイダーを作成する
ms.prod: SHAREPOINT
ms.assetid: 8f3228ca-57fd-4253-a07d-abeb63298c58
---


# [方法] SharePoint 2013 でクレーム プロバイダーを作成する
クレーム拡張およびクレーム選択の要件を満たす SharePoint 2013 クレーム プロバイダーを作成および実装する方法を説明します。
クレーム プロバイダーはクレームを発行し、セキュリティ トークンにパッケージ化します。クレーム プロバイダーには、拡張と選択の 2 つのロールがあります。
  
    
    

クレーム拡張により、アプリケーションが追加のクレームをユーザーのトークンに拡張できます。たとえば、Window ベースのログインでは、Active Directory ディレクトリ サービスがすべてのユーザーのセキュリティ グループをユーザーの Windows トークンに拡張できます。クレーム ベースのログインでは、カスタマー リレーションシップ マネジメント (CRM) アプリケーションが CRM からロールを拡張できます。これらのクレームをユーザーのトークンに含めることで、そのクレームに対してリソースを承認できます。つまり、これらのクレームを使用して、特定のユーザーが特定のリソースにアクセスできるかどうかを決定できます。
クレームをユーザー選択ウィンドウ コントロールに表示するには、クレーム選択を使用します。クレーム選択を使用すると、たとえば、SharePoint サイトまたは SharePoint サービスのセキュリティを構成しているときに、アプリケーションのユーザー選択ウィンドウにクレームを表示できます。この機能により、クレームの検索、解決、およびわかりやすい表示を提供することができます。
  
    
    


> **メモ**
> クレーム選択機能を備えたユーザー選択ウィンドウは、"クレーム選択"と呼ばれることがあります。詳細については、「 [ユーザー選択ウィンドウとクレーム プロバイダーの計画](http://technet.microsoft.com/ja-jp/library/gg602063.aspx)」を参照してください。 
  
    
    

クレーム プロバイダーを記述するには、まず、 **SPClaimProvider** クラスから派生するクラスを作成します。
> **ヒント**
> **SPClaimProvider** クラスとそのメンバーに関するコード例と詳細については、「 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) 」を参照してください。ウォークスルー、ヒント、およびコード サンプルについては、「 [Claims and Security: Technical articles and code samples on MSDN](http://msdn.microsoft.com/library/f773fd4a-53ec-4656-bd08-e6c435e6f103%28Office.15%29.aspx)」を参照してください。 
  
    
    


## 必須の実装
<a name="SP15_HowToCreateClaimsProvider_ReqImplementations"> </a>

クレーム プロバイダーを記述するときの必須のメソッドとプロパティを次に示します。
  
    
    

### 必須

次の  [Name](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.Name.aspx) プロパティは必須です。名前は、ファーム全体で一意である必要があります。
  
    
    

```cs

public abstract String Name
      
```


### クレーム選択における必須要素

クレームをユーザー選択ウィンドウ コントロールに表示するには、クレーム選択を使用します。ユーザー選択ウィンドウ コントロールでクレーム選択を実装する必要がある場合は、 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) クラスの次のメソッドが必須です。
  
    
    

```cs

protected abstract void FillSchema(SPProviderSchema schema);
     protected abstract void FillClaimTypes(List<String> claimTypes);
     protected abstract void FillClaimValueTypes(List<String> claimValueTypes);
     protected abstract void FillEntityTypes(List<String> entityTypes);

```


### クレーム拡張における必須要素

追加のクレームをユーザーのセキュリティ トークンに含めることで、クレームを拡張します。クレームを拡張するには、 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) クラスで次のメソッドを実装する必要があります。
  
    
    

```cs

public abstract bool SupportsEntityInformation
      protected abstract void FillClaimsForEntity(Uri context, SPClaim entity, List<SPClaim> claims);

```


### クレーム選択の左ウィンドウに階層を表示するための必須要素

クレーム選択の左ウィンドウに階層を表示するには、 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) クラスで次のメソッドを実装する必要があります。
  
    
    

```cs

public abstract bool SupportsHierarchy
     protected abstract void FillHierarchy(Uri context, String[] entityTypes, String hierarchyNodeID, int numberOfLevels, bool includeEntityData, SPProviderHierarchyTree hierarchy);

```


### クレーム選択の入力コントロールでクレームを解決するための必須要素

クレーム選択の入力コントロールを使用してクレームを解決できるようにするには、 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) クラスで次のメソッドを実装する必要があります。
  
    
    

```cs

public abstract bool SupportsResolve
     protected abstract void FillResolve(Uri context, String[] entityTypes, String resolveInput, List<PickerEntity> resolved);
     protected abstract void FillResolve(Uri context, String[] entityTypes, SPClaim resolveInput, List<PickerEntity> resolved);

```


### クレーム選択でクレームを検索するための必須要素

クレーム選択でクレームを検索できるようにするには、 [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) クラスで次のプロパティとメソッドを実装する必要があります。
  
    
    

```cs

public abstract bool SupportsSearch
     protected abstract void FillSearch(Uri context, String[] entityTypes, String searchPattern, String hierarchyNodeID, int maxCount, SPProviderHierarchyTree searchTree);

```


## 便利なヘルパー メソッド
<a name="SP15_HowToCreateClaimsProvider_UsefulHelperMethod"> </a>

ヘルパー メソッドを実装することもできます。このヘルパー メソッドは、 [SPClaim](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaim.aspx) オブジェクトの作成に役立ちます。
  
    
    

### SPClaim オブジェクトの作成に役立つヘルパー メソッド

 [SPClaim](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaim.aspx) オブジェクトを作成するために実装できるヘルパー メソッドを次に示します。
  
    
    

```cs

protected SPClaim CreateClaim(String claimType, String value, String valueType)
```


## その他の技術情報
<a name="SP15_HowToCreateClaimsProvider_AdditionalResources"> </a>


-  [SharePoint 2013 でのクレームベース ID](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクレーム プロバイダー](claims-provider-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 でクレーム プロバイダーを展開する](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

