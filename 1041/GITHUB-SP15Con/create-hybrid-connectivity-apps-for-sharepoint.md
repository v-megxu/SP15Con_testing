---
title: SharePoint 用のハイブリッド接続アプリを作成する
ms.prod: SHAREPOINT
ms.assetid: 311f036e-3442-4497-b35e-442b665462d3
---


# SharePoint 用のハイブリッド接続アプリを作成する
SharePoint 2013 ハイブリッド接続ソリューション用のアプリを開発および展開するプロセスについて説明します。
## SharePoint 2013 および SharePoint Online でのハイブリッド接続
<a name="bk_hybridconnectivity"> </a>

企業は SharePoint Online の使用に移行するときに、大量の独自データを安全にセキュリティで保護して公開する方法が必要です。この課題の解決を支援するために、SharePoint 2013 ではハイブリッド接続が導入されました。
  
    
    
Business Connectivity Services (BCS) ハイブリッド接続機能により、SharePoint 2013 では社内に保管されているデータ、企業ファイアウォールの内側にあるデータ、および種々の認証フォームでセキュリティ保護されているデータを使用できます。ハイブリッド接続の機能を使用すると、SharePoint Online はこのデータがまるで同じ内部ネットワーク上にあるかのように、Web を介してこのデータに安全にアクセスできます。ハイブリッド接続が構成されると、ユーザーは企業のインフラストラクチャ内でセキュリティ保護されたデータを使用できるようになります。ユーザーは SharePoint 2013 で付与されているアクセス許可に従ってデータへのアクセスおよびデータの操作を行うことができます。
  
    
    
動作中のハイブリッド ソリューションを構成する方法の詳細については、 [SharePoint Server 2013 のハイブリッド](http://technet.microsoft.com/ja-jp/library/jj838715.aspx) を参照してください。この一連の記事では、エンドツーエンド シナリオを設定するのに必要なデータ ソース、リバース プロキシ、検索、セキュリティ、ネットワーキング、およびその他のすべての項目を構成する要件について順を追って説明します。
  
    
    

> **注意**
> ハイブリッド SharePoint 環境を構成するには、専門的なスキルと、SharePoint Server 2013、SharePoint Online、関連する製品および技術での豊富な実務経験との両方が必要です。ハイブリッド環境の設計および展開中に技術的なガイダンスとサポートを提供する Microsoft のコンサルティング サービスのご利用をお勧めします。 <br/> 詳細については、 [Microsoft Services](http://www.microsoft.com/en-us/microsoftservices/deploy.aspx)を参照してください。 
  
    
    

BCS およびハイブリッド接続経由で内部データ ソースから取得したデータを使用するアプリを作成できるようにするために、この記事ではハイブリッド環境を構成する手順が実行済みであることを前提とします。
  
    
    

## ハイブリッド接続アプリの作成
<a name="bkmk_CreatingHybridConnectivityApps"> </a>

ハイブリッド SharePoint アドイン を作成することは、実質的には SharePoint アドイン を作成することと同じです。
  
    
    
以下の手順に従ってハイブリッド アプリを作成します。
  
    
    

-  [データ ソースの準備](#bkmk_PrepareDataSource)
    
  
-  [SharePoint アドイン の作成](#bkmk_CreateAnApp)
    
  
-  [外部コンテンツ タイプの作成](#bkmk_CreateECT)
    
  
-  [ハイブリッド アプリの展開](#bkmk_DeployHybridApp)
    
  

### データ ソースの準備
<a name="bkmk_PrepareDataSource"> </a>

大抵の場合、データ ソースはすでに配置されており、さまざまなビジネス アプリケーションに対応しています。しかし、そのデータは、企業のセキュリティ インフラストラクチャの内部からしか利用することができません。データが企業ファイアウォールの内側にあるサーバー上に存在する場合、またはデータが他の方法でセキュリティ保護されている場合、そのデータを BCS (これもまた、ファイアウォールの内側に設置されている) に公開するには、以下の手順が必要です。ネットワーク デバイスを設定して、SharePoint Online からの呼び出しを内部の SharePoint ファームに変換します。このデバイスは「リバース プロキシ」と呼ばれ、クラウドに配置された SharePoint アドイン の、ファイアウォールの内側に配置された BCS への呼び出しが可能になります。BCS はそこからのすべてのデータ接続を処理します。
  
    
    
このデータを BCS で利用できるようにするには、データを OData ソースとして公開する必要があります。そのためには、インターネット インフォメーション サービス (IIS) Web サイトを作成し、このサイトでサービスをホストし、OData および Representational State Transfer (REST) エンドポイントを介して、BCS がデータ ソースと通信できるようにします。
  
    
    
OData エンドポイントを作成するには、以下の手順に従って、Windows Communication Foundation (WCF) データ サービスを作成する必要があります。
  
    
    

### WCF データ サービスを作成するには


1. Microsoft .NET Framework 4 以降で動作する IIS Web サイトを作成します。基本的な認証を使用してサイトをセキュリティ保護します。
    
    > **メモ**
      > このサーバーに SharePoint がインストールされている必要はありません。実際には、簡単にするためおよびパフォーマンスのために、WCF データ サービスをホストするサーバーには SharePoint がインストールされていないのが望ましいです。 
2. Visual Studio 2012 で、[ **ASP.NET 空の Web アプリケーション**] テンプレートを使用して新しいプロジェクトを作成します。
    
  
3. [ **ソリューション エクスプローラー**] で、新しい [ **ADO.NET エンティティ データ モデル**] を追加します。
    
  
4. [ **Entity Data Model ウィザード**] の [ **データベースから生成**] オプションを選択します。
    
  
5. 既存の接続を選択するか、新しい接続を作成します。
    
  
6. URL および接続セキュリティ情報を設定します。
    
  
7. モデルに含めるアイテムを選択し、[ **完了**] を選択します。
    
  
8. 再び、[ **ソリューション エクスプローラー**] で、Visual Studio テンプレートを使用して新しい [ **WCF データ サービス**] を追加します。
    
  
9. データ サービスに名前を付けて、[ **次へ**] を選択します。
    
    この時点で、エンティティ モデルが作成され、結果として生成されたクラスがプロジェクトに取り込まれます。
    
  
10. 作成されたエンティティにセキュリティを設定します。そのためには、 `/* TODO: put your data source class name here */` を先ほど作成したエンティティ モデルのクラス名で置き換え、アクセス許可を付与するエンティティを指定します。
    
  
これを設定するための完全なチュートリアルについては、以下を参照してください。 
  
    
    

-  [OData の基礎知識 パート 1: OData サービスの構築](http://msdn.microsoft.com/ja-jp/data/gg601462)
    
  
-  [クイック スタート (WCF Data Services)](http://msdn.microsoft.com/ja-jp/library/cc668796.aspx)
    
  

### SharePoint アドイン の作成
<a name="bkmk_CreateAnApp"> </a>

ここで設定する前提条件の 1 つは、企業ファイアウォールの内側でアプリを開発しているというものです。この前提条件では、企業で働いている開発者のコンピューターはセキュリティ インフラストラクチャの内側に配置され、アプリの展開準備が整うまで開発とテストを実施するというシナリオが示されます。これにより、Visual Studio からデータ ソースへの接続のプロセスが簡略化され、次の手順で Office Developer Tools for Visual Studio 2013 を使用して外部コンテンツ タイプを自動的に生成します。
  
    
    

### 新しいアプリを作成するには


1. Office Developer Tools for Visual Studio 2013 および SharePoint 2013 がインストールされている開発用コンピューター上で Visual Studio 2012 を開きます。
    
  
2. SharePoint 用の新しいアプリを作成します。
    
  
3. アプリの名前と、テスト用のサイトをホストするローカル SharePoint URL と、アプリのホスト方法を指定し、[ **完了**] を選択します。
    
  

### 外部コンテンツ タイプの作成
<a name="bkmk_CreateECT"> </a>

BDC モデルまたは外部コンテンツ タイプをプロジェクトに追加するには、以下の手順に従ってください。
  
    
    

### 外部コンテンツ タイプを追加するには


1. 新しいプロジェクトが引き続き開いている状態で、ソリューションのショートカット メニューを開き、[ **追加**]、[ **外部データ ソースのコンテンツ タイプ**] の順に選択します。
    
  
2. ウィザードの最初のページでは、データ サービスの URL を指定します。 [ **OData ソースの指定**] ページでは、接続先の OData サービスの URL を入力します。 URL は、 **http://services.odata.org/Northwind/Northwind.svc/** のようになります。
    
  
3. OData ソースの名前を選択して、[ **次へ**] をクリックします。
    
  
4. OData サービスにより公開されているデータ エンティティの一覧が表示されます。 [ **選択されたデータ エンティティ用のリスト インスタンスを作成する**] チェック ボックスがオンになっていることを確認します。 
    
  
5. 1 つ以上のエンティティを選択し、[ **完了**] を選択します。
    
  
6. 展開前の最後に、新たに作成した外部コンテンツ タイプ ファイル内の URL を変更することが必要です。
    
    XML エディターで .ect ファイルを開きます。
    
  
7. リバース プロキシ経由のアクセスを許可する URL を指すように、 `ODataServiceMetadataUrl` プロパティを変更します。
    
  
8.  `ODataServiceUrl` プロパティを、リバース プロキシ経由のアクセスを許可する URL で変更します。
    
  
OData ベースの外部コンテンツ タイプを追加する方法の詳細については、「 [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)」を参照してください。
  
    
    

### ハイブリッド アプリの展開
<a name="bkmk_DeployHybridApp"> </a>

アプリを展開する段階になると、いくつかの選択肢があります。F5 展開を使用してアプリを直接テナントに展開することも、Visual Studio の発行機能を使用してアプリをパッケージ化し, .app ファイルを作成することもできます。このファイルを SharePoint Online テナント管理者に提供し、アップロードすることができます。
  
    
    
SharePoint アドイン の展開については、以下の情報を参照してください。 
  
    
    

-  [SharePoint アドインの展開とインストール: 方法とオプション](http://msdn.microsoft.com/library/d15a74a7-3c10-485a-9885-7ef11aaa0d90%28Office.15%29.aspx)
    
  
-  [Visual Studio を使用して SharePoint アドインを公開する](http://msdn.microsoft.com/library/8137d0fa-52e2-4771-8639-60af80f693bb%28Office.15%29.aspx)
    
  
また、外部コンテンツ タイプ用に作成された BDCM ファイルを取得し、それを展開してアプリの任意のレベルで使用されるようにすることもできます。この方法は、「 [方法: アドイン スコープの外部コンテンツ タイプをテナント スコープに変換する](how-to-convert-an-add-in-scoped-external-content-type-to-tenant-scoped.md)」で説明されています。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint Server 2013 のハイブリッド](http://technet.microsoft.com/ja-jp/library/jj838715.aspx)
    
  
-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Visual Studio を使用して SharePoint アドインを公開する](http://msdn.microsoft.com/library/8137d0fa-52e2-4771-8639-60af80f693bb%28Office.15%29.aspx)
    
  

