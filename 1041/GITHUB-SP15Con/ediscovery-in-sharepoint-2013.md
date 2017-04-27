---
title: SharePoint 2013 の eDiscovery
ms.prod: SHAREPOINT
ms.assetid: 45cb324a-75f5-444d-a0fa-5c223df19016
---


# SharePoint 2013 の eDiscovery
SharePoint 2013 の電子情報開示機能について説明します。電子情報開示を使用することにより、訴訟者は電子形式の情報を見つけることができます。
## SharePoint 2013 の電子情報開示について
<a name="SP15_eDiscoveryInSP_IntroductionToeDiscovery"> </a>

電子情報開示は、レコード管理者と訴訟者が電子形式のコンテンツを検出する仕組みのことです。通常、電子情報開示では、ラップトップ、電子メール サーバー、ファイル サーバー、および他のソースに散在するドキュメント、Web サイト、および電子メール メッセージを検索し、訴訟の条件を満たすコンテンツを収集および処理する必要があります。
  
    
    
SharePoint Server 2010 において、Microsoft は保留リストと電子情報開示機能を追加しており、SharePoint の任意のサイトを保留にすることが可能になりました。レコード管理者は、ドキュメント、ページ、およびリストの各アイテムを保留状態にすることができ、これによりユーザーが削除したり編集したりすることはできなくなります。Exchange 2010 には、法的情報保留をメールボックスに入れ、複数のメールボックスにわたって検索を実施し、Windows PowerShell コマンドレットを使用してメールボックスをエクスポートする機能が組み込まれています。
  
    
    
SharePoint 2013 および の電子情報開示には、検出のコストおよび複雑さを軽減する新しい仕組みが取り入れられています。それらは以下のとおりです。
  
    
    

- **電子情報開示センター**。SharePoint ファームおよび Exchange サーバーにわたって Exchange および SharePoint に格納されているコンテンツの保持、検索、およびエクスポートを管理するために使用される中央の SharePoint サイトです。
    
  
- **SharePoint インプレース保持**。SharePoint サイト全体を保持します。インプレース保持では、サイト内のすべてのドキュメント、ページ、およびリスト アイテムを保護しますが、ユーザーは保持されたコンテンツを引き続き編集および削除することができます。 
    
  
- **Exchange インプレース保持**。Exchange メールボックスを保持します。インプレース保持では、SharePoint サイトの保持に使用される同じ UI と API により、すべてのメールボックスのコンテンツを保護します。
    
  
- **クエリ ベースの保持**により、ユーザーは、1 つ以上の Exchange メールボックスと SharePoint サイトにクエリ フィルターを適用し、保持されるコンテンツを制限できます。
    
  

## SharePoint 2013 での電子情報開示の仕組み
<a name="SP15_eDiscoveryInSP_HoweDiscoveryWorks"> </a>

電子情報開示では、Search Service アプリケーション (SSA) を使用して SharePoint ファームをクロールします。SSA は多くの方法で構成できますが、最も一般的なのは、複数の SharePoint ファームをクロールする中央の検索サービスを使用する方法です。この 1 つの検索サービスを使用してすべての SharePoint コンテンツをクロールするか、特定の領域 (たとえば、ヨーロッパのすべての SharePoint コンテンツ) をクロールすることができます。
  
    
    
SharePoint ファームをクロールするため、まず検索では、サービス アプリケーション プロキシを使用してそのファームに接続します。電子情報開示センターは、プロキシ接続を使用して、他の SharePoint ファームの SharePoint サイトに保持情報を送信します。
  
    
    

## 前提条件
<a name="SP15_eDiscoveryInSP_Prerequisites"> </a>

SharePoint Server電子情報開示機能を展開する前に、組織の Search Service アプリケーション インフラストラクチャを計画してください。たとえば、特定の SharePoint サイト セットをクロールする別個の SSA が 2 つある場合は、SSA ごとに 1 つの電子情報開示センターが必要です。
  
    
    

## サイトのホールド
<a name="SP15_eDiscoveryInSP_SiteHolds"> </a>

SharePoint は、サイト レベルでコンテンツを保持します。サイトを保持する場合は、そのリスト、ライブラリ、およびサブサイトが保持されます。ルート サイト コレクションを保持する場合は、そのサイト コレクションのすべてのドキュメント、ページ、リスト、およびサブサイトが保持されます。
  
    
    
サイトをホールドするには、電子情報開示センターで情報開示ケースを作成します。ケースは、特定の訴訟に関連付けられているクエリ、コンテンツ、および保持情報すべてのコンテナーです。ケースの作成後は、情報開示セットを作成してサイトを指定します。そのサイトを検証するには、サイトの URL アドレスを入力します。
  
    
    
インプレース ホールドは、探索検索が完了する時点で存在しているコンテンツを保持することによって機能します。コンテンツ アイテムが編集または削除されると、電子情報開示は、そのアイテムのコピーを、コンテンツが変更された SharePoint サイトのアイテム保管ライブラリと呼ばれる特定のドキュメント ライブラリに配置します。サイト コレクション管理者の権限または Web アプリケーションの権限を持っている Search Indexer とユーザーのみが、アイテム保管ライブラリにアクセスできます。これらの権限を持たないほとんどのユーザーは、このライブラリを見ることができず、存在することやコンテンツがそこにコピーされたということは分かりません。
  
    
    
記憶域の容量を最小限に抑えて効率を最大化するような方法でコンテンツを保持するため、電子情報開示では書き込み時コピーを使用し、同じ情報を持つ同一のコピーを管理します。ホールドされるほとんどのコンテンツは変更されることがないため、そのコピーを作成して領域を使用する理由はありません。代わりに、インプレース保持では、アイテムが削除された場合か、保持の開始後にアイテムが初めて変更された後にのみ、アイテムのコピーを作成します。ドキュメントが再び変更された場合、電子情報開示では、現在のチェックインまたは削除されたバージョンと、ドキュメントが最初に保持されたときのバージョンのみを維持します。
  
    
    
複数のホールドが 1 つのサイトに配置されると、最初のホールドですでにコピーされているとしても、ドキュメントの次の編集が再びコピーされます。
  
    
    

## 電子情報開示のプログラミング モデル
<a name="SP15_eDiscoveryInSP_eDiscoveryProgrammingModel"> </a>

SharePoint 2013 は Microsoft .NET サーバー プログラミング モデルを提供します。これを利用し、電子情報開示機能が組み込まれたカスタム ソリューションとアプリを構築できます。表 1 は **Microsoft.Office.Server.Discovery** 名前空間のタイプを一覧表示にしたものです。
  
    
    

**表 1. 電子情報開示の種類**


|**型**|**説明**|
|:-----|:-----|
| [Case](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Case.aspx) <br/> |電子情報開示のケースを表します。ケースは、指定の  [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) オブジェクトと関連付けられ、指定日付または特定のアクションをもって終了できます。ケースにはソース グループ、場所、メールボックス、カストディアン、保存された検索、指定 ID のエクスポート設定、クエリ、この **Case** オブジェクトのすべてのソース グループ、カストディアン、場所の一覧を含めることができます。 <br/> |
| [Custodian](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Custodian.aspx) <br/> |電子情報開示ケースのレコード保持の担当者を表します。  <br/> |
| [CustodianCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.CustodianCollection.aspx) <br/> |**Custodian** オブジェクトのコレクションを表します。 <br/> |
| [DiscoveryDuplicateSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.DiscoveryDuplicateSourceCollection.aspx) <br/> |**Source** オブジェクトの値が一意でないときにスローされる例外。 <br/> |
| [DiscoveryException](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.DiscoveryException.aspx) <br/> |電子情報開示 API に固有の例外であり、メッセージを受け取ります。また内部的な例外を受け取ることもできます。  <br/> |
| [Export](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Export.aspx) <br/> |特定の **Case** オブジェクトに関連付けられるエクスポートを表します。 **Export** オブジェクトは **T:Microsoft.SharePoint.SPListItem** オブジェクトから構築できます。 **SavedSearch** オブジェクトを **Export** オブジェクトに追加したり、オプションの権利を管理したり、 **Export** オブジェクトをダウンロードしたりできます。 <br/> |
| [ExportCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.ExportCollection.aspx) <br/> |**Export** オブジェクトのコレクションを表します。 <br/> |
| [ExportStatus](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.ExportStatus.aspx) <br/> |エクスポートのステータスを表します。エクスポートの開始、未開始、完了、エラーありの完了を示します。  <br/> |
| [SavedSearch](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SavedSearch.aspx) <br/> |保存された電子情報開示検索を表します。 **SavedSearch** オブジェクトはコピー、削除、更新できます。保存された検索に関連付けられている統計は更新できます。検索の絞り込み、Exchange 2013 の絞り込み、ソース ID、ソース グループ ID、クエリ、フィルターを **SavedSearch** オブジェクトに関連付けることができます。 <br/> |
| [SavedSearchCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SavedSearchCollection.aspx) <br/> |**SavedSearch** オブジェクトのコレクションを表します。 <br/> |
| [Source](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Source.aspx) <br/> |電子情報開示操作に使用されるデータ ソースのタイプを表します。 **Source** オブジェクトは特定の **Case** オブジェクト、ある型のデータ ソース、フィルターをパラメーターとして受け取ります (つまり、ソースを識別するコンテナーの部分または完全な仕様)。保存ステータス、SharePoint によりインデックスが付けられるソースの場所、ソースがメールボックスであるかどうかなど、ソースに関する情報を返すことができます。 <br/> |
| [SourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceCollection.aspx) <br/> |**Source** オブジェクトのコレクションを表します。 <br/> |
| [SourceGroup](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceGroup.aspx) <br/> |**Source** オブジェクトのグループを表します。 <br/> |
| [SourceGroupCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceGroupCollection.aspx) <br/> |**SourceGroup** オブジェクトのコレクションを表します。 <br/> |
| [SourceManagementType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceManagementType.aspx) <br/> |ソースを管理するスケールを表します。オプションにはソース、ソース グループ、すべてのコンテンツが含まれます。  <br/> |
| [SourceType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceType.aspx) <br/> |ソースのタイプを表します。ソース タイプには Exchange 2013、SharePoint Server の現行バージョンと旧バージョンの両方、ファイル共有が含まれます。  <br/> |
| [SourceValidation](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceValidation.aspx) <br/> |ソースが有効かどうかを示します。  <br/> |
   

## その他の技術情報
<a name="SP15_eDiscoveryInSP_AdditionalResources"> </a>


-  [SharePoint 2013 eDiscovery およびコンプライアンスの新機能](what-s-new-in-sharepoint-2013-ediscovery-and-compliance.md)
    
  
-  [SharePoint 2013 のクライアント ライブラリ コードを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  

