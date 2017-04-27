---
title: アドイン スコープの外部コンテンツ タイプ (SharePoint 2013)
ms.prod: SHAREPOINT
ms.assetid: a34cbbba-dc38-4d3d-b796-d54b5848bdfb
---


# アドイン スコープの外部コンテンツ タイプ (SharePoint 2013)
SharePoint 2013 のアドイン レベルでインストールまたは範囲設定され、外部データ ソースを使用してデータ豊富な SharePoint アドイン を作成できる外部コンテンツ タイプについて説明します。
## SharePoint 2013 の、アドインを対象範囲とする外部コンテンツ タイプの概要
<a name="Appscopedect_overview"> </a>

SharePoint 2010 では、外部コンテンツ タイプをファーム レベルでのみインストールして使用できます。ファーム レベルでインストールするには、たとえ単純なアプリケーションでもアクセス権のために管理者が関与する必要があり、これが開発者にとって問題になることが少なくありません。
  
    
    
SharePoint 2013 では、アプリケーションは基本的に、アドインと呼ばれるより自律的な単位に隔離されます。アドインには、そのアプリケーションの実行に必要なリソースがすべて含まれています。この手法により、実行中のアプリケーションを他のアプリケーションから隔離できるようになります。このアーキテクチャには次のような利点があります。
  
    
    

- SharePoint 2013 の新しいアプリケーション モデルに沿ったアドインを作成できます。
    
  
- テナント管理者の関与なしに SAP、Netflix、独自仕様、およびその他の種類のデータからの外部データにアクセスするアドインを作成できます。
    
  
- 外部アプリケーションへのアクセスは Business Connectivity Services (BCS) によって管理され、他の SharePoint アプリケーションから使用できる統一された一貫性のあるインターフェイスが提供されます。
    
  
アドインを対象範囲とする外部コンテンツ タイプによって、アプリ内から外部データにアクセスできるようになります。
  
    
    

## アドインを対象範囲とする外部コンテンツ タイプを扱うための前提条件
<a name="Appscopedect_Prereq"> </a>

アドイン レベルで範囲設定された外部コンテンツ タイプを開発するための要件は次のとおりです。
  
    
    

- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2012
    
  
- SharePoint 2013
    
  
SharePoint 開発環境の設定については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」を参照してください。
  
    
    

### アドインを対象範囲とする外部コンテンツ タイプの基本概念

アドインを対象範囲とする外部コンテンツ タイプを扱う際に知っておく必要があるいくつかの基本概念を表 1 に示します。
  
    
    

**表 1. アドインを対象範囲とする外部コンテンツ タイプを理解するための基本概念**


|**記事**|**説明**|
|:-----|:-----|
| [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md) <br/> |BCS 外部コンテンツ タイプを作成する方法を説明します。  <br/> |
| [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |エンドユーザー向けの小型で使いやすいソリューションであるアドインを作成できる、SharePoint 2013 の新しいアドイン モデルについて説明します。  <br/> |
| [SharePoint ホスト型の SharePoint アドインの作成を始める](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx) <br/> |Office Developer Tools for Visual Studio 2012 を使用して基本的な SharePoint ホスト型アドインを作成する方法を説明します。  <br/> |
   

## アドインを対象範囲とする外部コンテンツ タイプでできること
<a name="Appscopedect_Tasks"> </a>

アドインを対象範囲とする外部コンテンツ タイプを追加する主な目的は、個別のアドインから外部データにアクセスできるようにすることです。これにより、次のようなことが可能になります。 
  
    
    

- 外部コンテンツ タイプへのアクセスを特定のアプリに制限する。
    
  
- アプリ内に外部コンテンツ タイプを展開する。
    
  

### アドインを対象範囲とする外部コンテンツ タイプの作成
<a name="Appscopedect_createect"> </a>

ファイル ベースのメタデータ カタログの概念は SharePoint 2010 で導入されました。これによって、外部コンテンツ タイプの定義に必要な XML が含まれるファイルを指定できます。このファイルは WSP パッケージ内で展開でき、対象範囲となっているアプリケーションにのみ関係します。このメタデータ ファイルを使用することにより、外部コンテンツ タイプをアドイン レベルに制限できます。
  
    
    
SharePoint 2013 では **SPListDataSource** が変更されて、アプリケーションの範囲を示すプロパティが追加されています。
  
    
    
このクラスは、 **SPList** と外部リストを関連付けることができます。関連付けられた **SPList** を使用して、エンティティ フィールドとデータを取得します。 **SPListDataSource** のインスタンスを **HasExternalDataSource** プロパティから取得します。 **HasExternalDataSource** が null ではない場合、 **SPList** オブジェクトのデータは SharePoint 2013 外にあります。
  
    
    
アドインを対象範囲とする外部コンテンツ タイプを追加するときは、このプロパティを **Add-in** に設定します。
  
    
    
 **MetadataCatalogFileName** プロパティを使用して、外部コンテンツ タイプの定義を含む BDC モデル ファイルを定義します。このプロパティは宣言的に定義することもプログラムによって定義することもできますが、SharePoint ユーザー インターフェイス (UI) で定義することはできません。
  
    
    
次の例は、 **MetadataCatalogFileName** プロパティを宣言的に設定する方法を示しています。
  
    
    



```XML

<DataSource>
  <Property Name="Entity" Value="Customer" />
  <Property Name="EntityNamespace" Value="SAP" />
  <Property Name="LobSystemInstanceName" Value="SAPClient1" />
  <Property Name="SpecificFinder" Value="ReadCustomer" />
  <Property Name=" MetadataCatalogFileName" Value="BDCMetadata.bdcm" />
</DataSource>
```


> **メモ**
> サイト管理者は App-Scoped-ECT (アプリを対象範囲とする外部コンテンツ タイプ) を使用するアドインをインストールできますが、アプリに BCS 接続を使用する権限を付与できるのは、SiteCollection 管理者だけです。 
  
    
    


### アドインを対象範囲とする外部コンテンツ タイプを WSP ファイルのカスタム フィーチャーで展開する
<a name="Appscopedect_deployect"> </a>

WSP ファイルに BDC モデルを含めて展開できます。次の例は、アプリに BDC モデルを含める方法を示しています。
  
    
    

```XML

<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <BdcModel Path="BDCMetadata.bdcm">
  </BdcModel>
</Elements>

```


> **重要**
> 各アドインに含めることができる BDC モデル ファイルは 1 つだけです。この例ではファイル名が BDCMetadata.bdcm になっていますが、BDC モデル ファイルの **Path** 属性のファイル名と一致していれば、モデル ファイルは実際にはどのような名前でもかまいません。
  
    
    


> **メモ**
> アドインを対象範囲とする外部コンテンツ タイプに使用できるのは Open Data Protocol (OData) 接続のみです。 
  
    
    


### 外部システムにセキュリティ資格情報を設定する
<a name="Appscopedect_deployect"> </a>

セキュリティ保護されている外部システムのデータにアクセスするため、適切な資格情報を使用して BDC モデルを設定する必要があります。
  
    
    
次の例は、アプリの Elements.xml ファイルを変更することによって、アドインを対象範囲とする外部コンテンツ タイプの外部システムにセキュリティ資格情報を設定する方法を示しています。
  
    
    



```XML

<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <BdcModel Path="BDCMetadata.bdcm">
    <LobSystem Name="SAP">
       <LobSystemInstance Name="SAPInst" RequireCredentials="true" CredentialsDescription="Credentials to connect to SAP"/>
    </LobSystem>
    <LobSystem Name="SQL">
       <LobSystemInstance Name="App Database" DataSource="SQL-Azure" RequireCredentials="true" />
    </LobSystem>
  </BdcModel>
</Elements>

```


## このセクションの内容
<a name="Appscopedect_inthissection"> </a>


-  [方法: アドイン スコープの外部コンテンツ タイプを作成する (SharePoint 2013 )](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [方法: SharePoint 2013 で REST を使用して外部データにアクセスする](how-to-access-external-data-with-rest-in-sharepoint-2013.md)
    
  

## その他のリソース
<a name="Appscopedect_Addres"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Business Connectivity Services プログラマー リファレンス](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の外部イベントおよびアラート](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

