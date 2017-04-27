---
title: SharePoint 2013 の Business Connectivity Services で OData ソースを使用する
ms.prod: SHAREPOINT
ms.assetid: 7a87e5bf-4428-4055-b113-7665a93e7326
---


# SharePoint 2013 の Business Connectivity Services で OData ソースを使用する
OData ソースに基づく外部コンテンツ タイプの作成を開始する方法と、そのデータを SharePoint 2013または Office 2013 コンポーネントで使用する方法について確認します。
## OData および OData コネクタ
<a name="SP15getstartedOdata_whatisodata"> </a>

Open Data Protocol (OData) を使用すると、特別に構成された URL の参照によってデータベースなどのデータ ソースにアクセスできます。これにより、組織内でホストされているデータ ソースに簡単に接続したり操作したりできます。
  
    
    
OData は HTTP、Atom、JavaScript Object Notation (JSON) を使用するプロトコルで、開発者は増加し続けるデータ ソースと対話するアプリケーションを記述できるようになります。Microsoft では、Web からアクセス可能なアプリケーションとデータ ストアとの間でデータ交換を実現する方法として、この標準の作成をサポートしています。
  
    
    
新しい "OData コネクタ" は、SharePoint と OData プロバイダーとの対話を実現します。
  
    
    
SharePoint 2013の Business Connectivity Services (BCS) は、OData ソースに直接コードを記述することなく OData ソースまたは "プロデューサー" と対話できます。プロデューサーは Web サービスを介し、構造化された方法でデータを公開します。土台となるデータの更新を許可するプロデューサーもあれば、読み取りアクセスのみを許可するプロデューサーもあります。プロデューサーはどの操作が使用可能であるかを知らせるため、特定の URL エンドポイントにサービス ドキュメントを保持します。SharePoint は既に OData のプロデューサーになっています。SharePoint リスト データは適切な権限を持つ顧客に対して OData ソースとして公開されます。
  
    
    

### OData プロデューサーの例
<a name="ExamplesOfODataProducers"> </a>

次に、OData 実装の例をいくつか示します。これらのアプリケーションおよびサービスは OData プロトコルを介してデータを公開します。
  
    
    

- SharePoint Foundation 2010
    
  
- SharePoint Server 2010
    
  
- SQL Azure
    
  
- Microsoft Azure Table Storage
    
  
- Microsoft Azure Marketplace
    
  
-  SQL Server Reporting Services
    
  
- Microsoft Dynamics CRM 2011
    
  
- Windows Live
    
  
OData サービスのプロデューサーの一覧については、「 [Open Data Protocol の Web サイト](http://www.odata.org/ecosystem)」を参照してください。
  
    
    

## BCS OData コネクタ使用の前提条件
<a name="SP15GetstartedOdata_prereq"> </a>

OData ベースの外部コンテンツ タイプを開発するには、次のものが必要です。
  
    
    

- Visual Studio 2012
    
  
- SharePoint 2013
    
  
- Office Developer Tools for Visual Studio 2012
    
  
開発環境の設定方法については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」を参照してください。
  
    
    

## OData データ ソース向け外部コンテンツ タイプの作成
<a name="SP15GetstartedOdata_creatingECT"> </a>

特定の OData プロデューサーにより公開されたデータを SharePoint で使用できるようにするには、SharePoint 内に外部コンテンツ タイプを作成する必要があります。すべての SharePoint 外部コンテンツ タイプと同様に、この外部コンテンツ タイプには、外部システムとの接続と対話に必要なあらゆる接続情報が含まれています。
  
    
    
OData データ ソースを使用する外部コンテンツ タイプを作成する方法は、どの外部コンテンツ タイプでも同様です。Visual Studio 2012 を使用すると自動的に OData 外部コンテンツ タイプが作成されます。外部コンテンツ タイプの作成時に、OData ソースの Representational State Transfer (REST) エンドポイントを指定するだけです。詳細については、「 [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)」を参照してください。
  
    
    

## このセクションの内容
<a name="SP15GetstartedOdata_inthissect"> </a>


-  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [BCS 外部システムとして使用する OData データ サービスを作成する方法](how-to-create-an-odata-data-service-for-use-as-a-bcs-external-system.md)
    
  
-  [[方法] SharePoint 2013 で OData データ ソースを使用して外部リストを作成する](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md)
    
  

## その他の技術情報
<a name="SP15GetstartedOdata_addres"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Business Connectivity Services プログラマー リファレンス](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  

