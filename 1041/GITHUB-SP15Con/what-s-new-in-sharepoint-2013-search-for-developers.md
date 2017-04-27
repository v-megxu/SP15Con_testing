---
title: 開発者向けの SharePoint 2013 検索の新機能
ms.prod: SHAREPOINT
ms.assetid: b8d69685-3612-421e-b011-50b4d580d461
---


# 開発者向けの SharePoint 2013 検索の新機能
SharePoint 2013の検索で開発者が使用できる新しい機能について説明します。
## オンライン、社内設置型、モバイル開発向けクエリ オブジェクト モデル機能にアクセスするためのクライアント オブジェクト モデルの検索
<a name="SPSearchnew_clientOM"> </a>

SharePoint 2013検索には、ほとんどのオンライン、社内設置型、モバイル開発向けクエリ オブジェクト モデル機能にアクセスできるようにするクライアント側オブジェクト モデル (CSOM) が含まれています。CSOM の検索を使用して、SharePoint 2013の検索結果を返すためにインストールされた SharePoint 2013のないマシンで実行するクライアント アプリケーションを作成できます。
  
    
    
CSOM の検索には、Microsoft .NET Framework マネージ クライアント オブジェクト モデル、JavaScript オブジェクト モデルが含まれており、SharePoint 2013に基づいて構築されています。まず、クライアント コードが SharePoint CSOM にアクセスします。次に、クライアント コードが CSOM の検索にアクセスします。 
  
    
    
.NET Framework マネージ CSOM の検索を使用するには、 [ClientContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.ClientContext.aspx) インスタンス (Microsoft.SharePoint.Client.dll の [Microsoft.SharePoint.Client](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.aspx) 名前空間にある) を取得する必要があります。次に、Microsoft.Office.Server.Search.Client.dll. の [Microsoft.SharePoint.Client.Search.Query](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.aspx) 名前空間にあるオブジェクト モデルを使用します。SharePoint CSOM の詳細については、「 [マネージ クライアント オブジェクト モデル](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)」を参照してください。CSOM へのエントリ ポイントである **ClientContext** オブジェクトの詳細については、「 [中心的オブジェクトであるクライアント コンテキスト](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)」を参照してください。
  
    
    
CSOM の検索は、JavaScript Object Notation (JSON) 内のサーバーから検索結果のデータを返します。検索結果のデータ用 JSON には、異なる結果セットを表示する  [ResultTable](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.ResultTable.aspx) オブジェクトから構成される [ResultTableCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Search.Query.ResultTableCollection.aspx) コレクションが含まれます。
  
    
    

## 削除される SQL 構文のサポート
<a name="SP15Searchnew_support"> </a>

SharePoint Server 2013のカスタム検索ソリューションでは、 [SharePoint 検索の SQL 構文のリファレンス](http://msdn.microsoft.com/ja-jp/library/ee558869.aspx) はサポートされません。SharePoint 2013 の検索は、カスタム検索ソリューション用 FQL 構文および KQL 構文をサポートしています。クエリ サーバー オブジェクト モデル、クライアント オブジェクト モデル、および REST 検索サービスを含む任意の技術を使用して、カスタム検索ソリューションの SQL 構文を使用することはできません。SharePoint サーバーの以前のバージョンで作成されたクエリ サーバー オブジェクト モデルおよびクエリ Web サービスで SQL 構文を使用するカスタム検索ソリューションは、SharePoint Server 2013にアップグレードすると機能しません。これらのアプリケーション経由で送信されたクエリはエラーを返します。FQL 構文および KQL 構文の使用に関する詳細については、「 [キーワード クエリ言語 (KQL) 構文のリファレンス](keyword-query-language-kql-syntax-reference.md)」および「 [FAST クエリ言語 (FQL) 構文のリファレンス](fast-query-language-fql-syntax-reference.md)」を参照してください。
  
    
    

## クライアント アプリケーションからのクエリのリモート実行用 REST 検索サービス
<a name="SP15Searchnew_support"> </a>

SharePoint Server 2013には、Representational State Transfer (REST) サービスが含まれます。それにより、REST Web 要求をサポートする任意の技術を使用して、クライアント アプリケーションからの SharePoint 2013検索サービスに対するクエリをリモートで実行できます。REST 検索サービスでは 2 つのエンドポイントが公開されます。それは、 **query** と **suggest** で、 **GET** および **POST** 操作の両方をサポートします。結果は XML または JSON 形式のどちらかで返されます。
  
    
    
以下はサービス用アクセス ポイントです:  `http://server/_api/search/`。URL のサイトを次のように特定することもできます:  `http://server/site/_api/search/`。検索サービスはサイト コレクション全体から結果を返すので、同じ結果がサービスにアクセスする両方の方法のために返されます。
  
    
    
次のとおりに、client.svc を参照してサービスにアクセスする URL を使用することもできます:  `http://server/_vti_bin/client.svc/search/`。ただし、 `_api` の使用が優先規則となっています。
  
    
    
次のアクセス ポイントを使用して、サービス メタデータにアクセスします: 
  
    
    
 `http://server/_api/$metadata`
  
    
    
SharePoint 2013の REST サービスの一般的な情報については、「 [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)」を参照してください。
  
    
    

## SharePoint 検索クエリ Web サービスの廃止
<a name="SP15Searchnew_support"> </a>

クエリ Web サービス (パス  `http://server/site/_vti_bin/search.asmx` にある) は、SharePoint 2013では使用されなくなります。新しいアプリケーションを記述する場合は、この推奨されていない機能を使用しないようにしてください。代わりに、新しいクエリ CSOM またはクエリ REST サービスを使用してください。既存のアプリケーションを変更する場合は、この機能に関する依存関係を削除するよう強く推奨します。
  
    
    

## SharePoint 検索クエリオブジェクト モデルの機能強化
<a name="SP15Searchnew_support"> </a>

クエリ プロパティは検索クエリについての情報を提供します。SharePoint 2013検索では、プロパティ バッグがクエリおよび結果クラスに追加され、ユーザー定義のクエリ プロパティが有効になりました。次のように、1 つのクエリ クラスのプロパティを経由して既存のクエリ プロパティにアクセスできます。 
  
    
    
 `KeywordQuery.EnableStemming`
  
    
    
または、次のようにプロパティ バッグを使用できます。 
  
    
    
 `KeywordQuery.Properties["EnableStemming"]`
  
    
    
次のように、プロパティ バッグを使用してのみユーザー定義プロパティにアクセスできます: 
  
    
    
 `KeywordQuery.Properties["UserDefinedProperty"]`
  
    
    
SharePoint 2013検索には、以下のような新しいクエリ プロパティを含め、プロパティ バッグのクエリ プロパティが含まれます。
  
    
    

- **BypassResultTypes** 検索結果アイテムの種類がクエリの結果に対して返されるかどうかを指定します。 **true** を指定して結果の種類なしを返します。それ以外の場合は **false**。
    
  
- **EnableInterleaving** 実行しているクエリ ルールの処理によって生成された結果セットかどうかを指定し、元のクエリ用の結果セットと組み合わされている結果ブロックを追加します。 **true** を指定して生成された結果セットと元の結果セットを組み合わせます。それ以外の場合は **false**。
    
  
- **EnableQueryRules** クエリ ルールがこのクエリに対してオンになっているかどうかを指定します。 **true** を指定して、クエリ向けクエリ ルールを有効にします。それ以外の場合は **false**。
    
  
クエリ ルールの条件として、ユーザー定義プロパティを含め、プロパティ バッグで任意のプロパティを指定できます。クエリ ルールを使用して、ユーザーにとって重要な種類のクエリの検索の操作性をカスタマイズします。クエリがクエリ ルールで指定されている条件を満たしているとき、ルールがアクションを指定して、関連付けられた検索結果の関連性を向上させます。 
  
    
    

## キーワード クエリ言語の機能拡張
<a name="SP15Searchnew_support"> </a>

SharePoint 2013にはキーワード クエリ言語の改良が含まれており、それらはこのセクションで説明します。 
  
    
    

### NEAR 演算子の向上

SharePoint Server 2010 では、 **NEAR** 演算子が最大トークン距離である **8** を暗黙に定義し、入力トークンの順序を保持しました。SharePoint 2013では、 **NEAR** 演算子はトークンの順序を保持しなくなりました。また、 **NEAR** 演算子は最大トークン距離を示すオプション パラメーターを受け取ります。ただし、既定値は **8** のままです。以前の動作を使用する必要がある場合は、代わりに **ONEAR** を使用します。
  
    
    
以下の例に示すように、 **NEAR** 演算子をプロパティ制限の式で使用できます。
  
    
    
 `"acquisition" NEAR "debt"`
  
    
    
トークンの最大距離が **8** の場合、このトークンは、トークン "acquisition" および "debt" が同じドキュメント内に表示されるアイテムと一致します (値が提供されていない場合は、既定値の _n_)。トークンの順序は一致には重要ではありません。
  
    
    
より短いトークン距離を必要とする場合、次のように指定できます。
  
    
    
 `"acquisition" NEAR(n=3) "debt"`
  
    
    
最大トークン距離が **3** の場合、このクエリは 2 つのトークン "acquisition" と "debt" が同じドキュメント内に表示されるアイテムと一致します。トークンの順序は一致には重要ではありません。
  
    
    

### 新しい ONEAR 演算子

 **ONEAR** 演算子は、順序指定付きの近い機能を提供します。最大トークン距離を示すオプション パラメーターを受け取ります。既定値は **8** です。
  
    
    
 **ONEAR** 演算子は入力表現の順序を保持します。順序なしの近接については、 **NEAR** を使用してください。
  
    
    
以下の例に示すように、プロパティ制限の式で **ONEAR** 演算子を使用できます。
  
    
    
 `"acquisition" ONEAR "debt"`
  
    
    
最大トークン距離が **8** の場合、このクエリは 2 つのトークン "acquisition" および "debt" が同じドキュメント内に表示されるアイテムと一致します (値が提供されていない場合は、既定値の _n_)。
  
    
    
より短いトークン距離を必要とする場合、次のように指定できます。
  
    
    
 `"acquisition" ONEAR(n=3) "debt"`
  
    
    
最大トークン距離が **3** の場合、このクエリは 2 つのトークン "acquisition" と "debt" が同じドキュメント内に表示されるアイテムと一致します。トークンの順序が返されるアイテムに対して一致する必要があります。
  
    
    

### 新しい XRANK 演算子

SharePoint Server 2010 では、 **XRANK** 演算子は FAST クエリ言語 (FQL) でのみ使用できました。SharePoint 2013では、新しく強力な **XRANK** 演算子が導入されています。
  
    
    
The **XRANK** 演算子は動的ランク制御を提供します。この演算子は、クエリに一致するアイテムを変更せずに、特定の用語出現回数に基づいてアイテムの動的ランクをアップします。
  
    
    

## 検索結果 UI カスタマイズ用の豊富な結果フレームワーク
<a name="SP15Searchnew_support"> </a>

SharePoint 2013検索には、検索結果のユーザー インターフェイス (UI) の表示形式 (外観) のカスタマイズを容易にする新しい結果フレームワークが含まれています。検索結果の表示方法を変更するためにカスタム XSLT を書き込む代わりに、ディスプレイ テンプレートおよび結果の種類を使用して、結果の重要な種類の表示形式をカスタマイズできます。
  
    
    

### 表示テンプレート

表示テンプレートは、HTML、CSS、および JavaScript を使用して、表示レイアウトと結果の種類の動作を定義します。HTML エディターを使用して、既存のディスプレイ テンプレートをカスタマイズ、またはディスプレイ テンプレートを作成し、それらをディスプレイ テンプレート ギャラリーにアップロードできます。
  
    
    

### 結果の種類

結果の種類は以下のコレクションに基づく検索結果の設定表示方法を定義します。
  
    
    

- **ルール** 指定された条件に基づいて、結果の種類をいつ適用するかを判断します。等号、比較、論理演算子を使用してルール条件を結合できます。
    
  
- **プロパティ** 結果用管理プロパティのリストを判断します。管理プロパティをディスプレイ テンプレートにマップする前に、管理プロパティをリストに追加する必要があります。
    
  
- **表示テンプレート** 結果の種類の表示レイアウトを判断します。
    
  
管理者は、サイト レベルまたはサービス アプリケーション レベルで結果の種類を作成し、管理できます。カスタムのコーディングは必要ありません。
  
    
    

## コネクタ フレームワークの機能拡張
<a name="SP15Searchnew_support"> </a>

SharePoint 2013検索により、コネクタ フレームワークを使用してクロールされるカスタム外部データ ソースに保存されているコンテンツ用クレーム情報を取得できます。
  
    
    
コネクタ フレームワークは向上した例外キャプチャとログも提供し、コネクタ フレームワークの上部に構築されているカスタム コネクタを使用しているコンテンツ ソースをクロールする際に発生するエラーのトラブルシューティングをサポートします。コネクタ フレームワークの詳細については、「 [SharePoint 2013 の検索コネクタ フレームワーク](search-connector-framework-in-sharepoint-2013.md)」を参照してください。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint Search を使用して新しいコンテンツを検索する](searching-new-content-with-sharepoint-search.md)
    
  
-  [SharePoint 2013 で検索を構成する](configure-search-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 で検索クエリを作成する](building-search-queries-in-sharepoint-2013.md)
    
  
-  [方法: SharePoint Server の検索結果でカスタム セキュリティ トリマーを使用する](how-to-use-a-custom-security-trimmer-for-sharepoint-server-search-results.md)
    
  

