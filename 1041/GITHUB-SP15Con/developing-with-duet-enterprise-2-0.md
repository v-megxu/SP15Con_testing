---
title: Duet Enterprise 2.0 での開発
ms.prod: SHAREPOINT
ms.assetid: c3ef38aa-559e-4832-95c7-75e222c77624
---


# Duet Enterprise 2.0 での開発

## 概要
<a name="Overview"> </a>

Duet Enterprise 2.0 は Microsoft と SAP 間の共同の取り組みの最新バージョンであり、SharePoint ユーザーが SAP システムからのデータを操作できるようにします。また、SharePoint 2013 と SharePoint Online だけでなく SAP からのコンポーネントも結合します。開発者は、ユーザーが SAP システムからのデータを使い慣れた SharePoint 環境に取り込めるようにするコンポーネントを作成できるようになります。
  
    
    

## Duet Enterprise 2.0 の機能
<a name="Overview"> </a>

適切にインストールされ構成されていれば、Duet Enterprise 2.0 は次の機能を提供します。
  
    
    

- ビジネス データ Web パーツ、外部リスト、カスタム コンポーネントを使用すると、SharePoint 内で SAP システムのデータを操作できます。
    
  
- 組み込みコンポーネントを使用して、コードを使わずに SharePoint 2013 で SAP データを使用します。
    
  
- アプリ内で SAP レポート システムを使用します。
    
  
- Duet Enterprise 2.0 と共にインストールされる特別な Web パーツを使用して SAP 情報を SharePoint ページに追加します。
    
  
- アプリで SAP ワークフローを使用します。
    
  
- 開発者はクライアント側 JavaScript を使用して SAP 外部データを操作できます。
    
  
- 認証に OAuth を使用してデータをセキュリティで保護します。
    
  

## 開発環境を設定する
<a name="SettingUp"> </a>

Duet Enterprise 2.0 を使用した SharePoint アドインの開発の大部分は、普通の SharePoint アドインの作成とまったく同じです。ブラウザーベースの Napa Office 365 開発ツールを使用して作成および展開することも、Visual Studio を使用してアプリを拡張し、Visual Studio 統合開発環境の堅牢なフレームワーク内で作業することもできます。
  
    
    

## 外部コンテンツ タイプを追加する
<a name="AddingECT"> </a>

SAP システムに保管されている外部データにアクセスするには、外部コンテンツ タイプを追加する必要があります。SAP データは OData エンドポイントを通じて公開されるため、アプリ レベルを範囲とする  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) には Visual Studio にインストールされている自動生成ツールを使用できます。
  
    
    
次の手順に従って外部コンテンツ タイプを作成します。
  
    
    

### SAP OData エンドポイントから外部コンテンツ タイプを作成する


1. [ **ソリューション エクスプローラー**]で、プロジェクトのショートカット メニューを開き、[ **追加**]、[ **外部データ ソースのコンテンツ タイプ**] の順に選択します。
    
  
2. [ **OData ソースの指定**] ページで、Duet Enterprise ワークフロー サービスの URL を入力します。
    
  
3. OData ソースの名前を選択します。
    
  
4. 必要なエンティティを選択します。
    
  
5. [ **完了**] を選択します。
    
  
新たに作成された BDC モデルを見つけることができる、[外部コンテンツ タイプ] という名前の新しいフォルダーが Visual Studio によって作成されます。
  
    
    

## BDC モデルを構成する
<a name="ConfiguringProject"> </a>

プロジェクトを機能させるために最も重要なことは、 **ODataExtensionProvider** プロパティを BDC モデルに追加することです。このプロパティでは、アプリ コードの作成に必要な SAP 拡張機能を BCS に提供する拡張機能プロバイダーを定義します。
  
    
    
このサンプルでは、BDC モデルに追加されたプロパティを示しています。
  
    
    



```XML

<LobSystem Type="OData" Name="LOB_SYSTEM_NAME">
                     <Properties>
                          <Property Name="ODataServiceMetadataUrl" Type="System.String">
                               https://<DUET_METADATA_URL>:443/sap/opu/odata/sap/ 
                               ZANDY_PO_HEADER_SRV/$metadata</Property>
                          <Property Name="ODataServicesVersion" Type="System.String">2.0</Property>
                          <Property Name="ODataExtensionProvider" Type="System.String"> 
                               OBA.Server.Canary.ObaOdataServerExtensionProvider, 
                               OBA.Server.SSOProvider, 
                               Version=15.0.0.0, 
                               Culture=neutral, 
                               PublicKeyToken=71e9bce111e9429c</Property>
                          <Property Name="TraceHeader" Type="System.String">SAP-PASSPORT</Property>
                     </Properties>

```


## Duet スターター サービスを使用してカスタム アプリを開発する
<a name="UsingDuetStarterServices"> </a>

Duet Enterprise 2.0 は複数のスターター サービスを SharePoint 2013 サーバーのファイル システムにインストールします。既定のインストールでは、ファイルは C:\\Program Files\\Duet Enterprise\\2.0\\Solutions\\Starter Services にあります。次のファイルが含まれています。 
  
    
    

- OBACustomerWorkspace
    
  
- OBAOrderToCash
    
  
- OBAPortal
    
  
- OBAProductCenter
    
  
これらの各ソリューションには、WSP ファイル、ソリューションに加え、それらの実装に必要なその他の関連ファイルが含まれます。
  
    
    
これらのソリューションを使用すると、Duet Enterprise 2.0 で何を実行できるのか、開発パターンは何かを確認できますが、SharePoint アドイン での使用はサポートされません。
  
    
    

## その他のリソース
<a name="ConNavExample_resources"> </a>


-  [Duet Enterprise for SharePoint and SAP Server 2.0](http://technet.microsoft.com/ja-jp/library/ff972436.aspx)
    
  
-  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [#define VISUAL_STUDIO](http://msdn.microsoft.com/ja-jp/vstudio/default)
    
  
-  [Visual Studio (VSTO) で作成されたマネージ アドイン](http://msdn.microsoft.com/ja-jp/office/hh133430)
    
  

