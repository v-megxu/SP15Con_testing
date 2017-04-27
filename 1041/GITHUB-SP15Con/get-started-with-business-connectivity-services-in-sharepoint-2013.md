---
title: SharePoint 2013 の Business Connectivity Services の概要
ms.prod: SHAREPOINT
ms.assetid: c6bf3db0-db79-4b13-9834-891d24b2c9e5
---



# SharePoint 2013 の Business Connectivity Services の概要
Business Connectivity Services (BCS) が SharePoint 2013 ソリューションの開発者に提供する機能の基本と、さまざまなタイプのソリューションで BCS の使用を開始する方法を学習します。
## Business Connectivity Services とは


|||
|:-----|:-----|
|Business Connectivity Services (BCS) は、Office SharePoint Server 2007 でリリースされたビジネス データ カタログの進化形として SharePoint Server 2010 で導入されました。BCS により、外部でホストされるデータを SharePoint 2013で処理できます。使用可能なソースには、データベース、Web サービス、Windows Communication Foundation (WCF) サービス、Open Data Protocol (OData) ソース、およびカスタム .NET アセンブリを使用してアクセスされるその他の独自データが含まれます。 [![設定開始](images/mod_icon_getstartbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatDoYouNeed) [![開始](images/mod_icon_dobox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_WhatCanYouDo) [![詳細を見る](images/mod_icon_startbox.gif)          ](get-started-with-business-connectivity-services-in-sharepoint-2013.md#SP15GettingStartedBCS_LearnMore)|
**ビデオを見る: SharePoint 2013 Business Connectivity Services と OData サービスの概要**

  
    
    

  
    
    
![ビデオ](images/mod_icon_video.png)
  
    
    

  
    
    

  
    
    
|
   
動的な作業環境では、インフォメーション ワーカーは、たとえば次のような、別のソフトウェア世界に存在するデータにアクセスする必要があります。
  
    
    

- 企業のリソース計画 (ERP) アプリケーションや顧客リソース管理 (CRM) アプリケーションなどの、組織の企業アプリケーションに存在する構造化データ
    
  
- Microsoft Office にあるようなビジネス生産性アプリケーション、チームとグループ作業のアプリケーション (SharePoint など)、および Web 2.0 サービス (インターネット アプリケーション、Wiki、ブログ、ソーシャル ネットワーキング サイトなど) に存在する非構造化データ
    
  
大部分のインフォメーション ワーカーは、作業時間の大半を生産性アプリケーション (Microsoft Office 環境など) で費やしますが、使用する企業アプリケーションやグループ作業ソフトウェアおよびサービスに、その環境を統合する方法が必要になることもあります。SharePoint 2013では BCS によってその機能が提供されます。
  
    
    

## Business Connectivity Services の基礎知識
<a name="SP15GettingStartedBCS_WhatDoYouNeed"> </a>

BCS による開発を開始するには、次のものが必要です。
  
    
    

- SharePoint 2013
    
  
- Visual Studio
    
  
- Office Developer Tools for Visual Studio 2012
    
    または
    
  
- SharePoint Designer
    
  
開発環境をセットアップする方法については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」を参照してください。
  
    
    

### Business Connectivity Services の基本

次の表は、BCS ソリューションの開発を開始するために理解しておく必要がある中心概念を示しています。
  
    
    

**表 1. BCS を理解するための中心概念**


|**記事**|**説明**|
|:-----|:-----|
| [Entity Data Model キーの概念](http://msdn.microsoft.com/ja-jp/library/ee382840.aspx) <br/> |Entity Data Model (EDM) では、エンティティ型、アソシエーション型、およびプロパティという 3 つの主要概念を使用してデータ構造を記述します。 これらは、EDM の実装においてデータ構造を記述する上で最も重要な概念です。  <br/> |
| [Web アプリケーションのセキュリティに関する基本的な対策](http://msdn.microsoft.com/ja-jp/library/zdh19h94%28VS.100%29.aspx) <br/> |安全な Web アプリケーションを作成することは、非常に大きな課題です。 安全な Web アプリケーションを作成するためには、セキュリティの脆弱性を理解する必要があります。 さらに、Windows オペレーティング システム, .NET Framework、および ASP.NET の各セキュリティ機能を理解しておく必要があります。 そして最後に、これらのセキュリティ機能を使用して各種の脅威に対抗するための方法を理解することが必要です。  <br/> |
| [WCF Data Services](http://msdn.microsoft.com/ja-jp/data/odata.aspx) <br/> |WCF Data Services (従来の ADO.NET Data Services) は、Web 用 OData サービスの作成と使用を可能にします。  <br/> |
| [Open Data Protocol (OData)](http://www.odata.org) <br/> |OData は URL によってデータにアクセスするための業界標準プロトコルです。基本的には、HTTP プロトコルの上部に配置され、既存の HTTP 語法を使用した読み書きの機能を提供します。  <br/> |
| [Internet Information Services](http://www.iis.net/) <br/> |Internet Information Services (IIS) は SharePoint が実行されるプラットフォームです。Web サイトの作成方法、仮想ディレクトリ、Web サービス、URL、Web セキュリティ、および IIS に関連した他のテクノロジについて理解する必要があります。  <br/> |
| [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md) <br/> |外部コンテンツ タイプは、それによって表される外部システムを記述するものです。SharePoint にインポートするときに再利用可能で、SharePoint Designer 2013、Outlook 2013、Web パーツ、外部リスト、およびカスタムのクライアント アプリケーションを使用して複雑なコード不要のソリューションを作成するために使用できます。  <br/> |
| [SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md) <br/> |SharePoint 2013は、慎重に生成された URL によってすべてのオブジェクトにアクセスする能力を備えています。BCS は同じ機能を提供するように拡張されています。  <br/> |
   

## Business Connectivity Services でできること
<a name="SP15GettingStartedBCS_WhatCanYouDo"> </a>

BCS を使用すると、多くの異なるソースから情報を SharePoint に取り込むことができます。たとえば、外部 SQL Server データベース、従来の Web サービス、WCF サービス、独自システム、および OData サービスからデータを取り込むことができます。
  
    
    

**表 2. Business Connectivity Services を使用して作業するための基本的なタスク**


|**タスク**|**説明**|
|:-----|:-----|
| [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md) <br/> |Business Connectivity Services (BCS) 外部コンテンツ タイプの作成について学習します。  <br/> |
| [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) <br/> |OData ソースに基づく外部コンテンツ タイプを作成して SharePoint または Office コンポーネントでそのデータの使用を開始するために必要な情報を見つけます。  <br/> |
| [[方法] 外部イベント レシーバーの作成](how-to-create-external-event-receivers.md) <br/> |外部リストへの接続が可能で、リストが表す外部データの更新時に実行される、イベント レシーバーの作成の背後にある概念について学習します。  <br/> |
| [方法: アドイン スコープの外部コンテンツ タイプを作成する (SharePoint 2013 )](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md) <br/> |アプリ レベルでインストールまたは範囲設定され、外部データ ソースを使用するデータが豊富なアプリを開発者が作成できるようにする、外部コンテンツ タイプの作成方法について学習します。  <br/> |
| [[方法] SharePoint 2013 のクライアント コード ライブラリを使用して外部データにアクセスする](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md) <br/> |SharePoint 2013 クライアント オブジェクト モデルを使用して SharePoint 2013で BCS を処理する方法について学習します。  <br/> |
   

## レベルアップ: Business Connectivity Services についての追加情報
<a name="SP15GettingStartedBCS_LearnMore"> </a>

BCS の基本概念を習得すると、より高度な機能を使用して多くの強力なソリューションを構築できます。
  
    
    

**表 3. BCS での高度な概念**


|**トピック**|**説明**|
|:-----|:-----|
| [BCS 外部システムとして使用する OData データ サービスを作成する方法](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md) <br/> |基礎となるデータが変更されたときに OData を使用して SharePoint 2013に通知を送る、インターネット アドレスの指定が可能な WCF サービスの作成方法について学習します。これらの通知は、外部リストに接続されたイベントをトリガーするために使用されます。  <br/> |
| [SharePoint 2013 BDC モデル スキーマ リファレンス](bdc-model-schema-reference-for-sharepoint-2013.md) <br/> |BDC モデルのスキーマに関する参考情報を見つけます。  <br/> |
| [SharePoint 2013 BCS クライアント オブジェクト モデル リファレンス](bcs-client-object-model-reference-for-sharepoint-2013.md) <br/> |Business Connectivity Services (BCS) によって公開される外部データに SharePoint 2013 クライアント オブジェクト モデルを使用してアクセスするクライアント側スクリプトの作成に使用できるオブジェクトの概要を理解します。  <br/> |
| [SharePoint 2013 BCS REST API リファレンス](bcs-rest-api-reference-for-sharepoint-2013.md) <br/> |OData ソースへのアクセスとその操作に使用される Representational State Transfer (REST) URI の生成に関する参考情報を見つけます。  <br/> |
   

## その他の技術情報
<a name="SP15GettingStartedBCS_LearnMore"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Open Data Protocol Web サイト](http://www.odata.org/)
    
  
-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の外部イベントおよびアラート](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [アドイン スコープの外部コンテンツ タイプ (SharePoint 2013)](add-in-scoped-external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
