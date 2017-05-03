---
title: SharePoint 2013 でのクロスサイト発行
ms.prod: SHAREPOINT
ms.assetid: 33f49e69-c1d3-4a6e-8887-5df683cba022
---


# SharePoint 2013 でのクロスサイト発行

SharePoint 2013 ではクロスサイト発行機能が導入されており、複数のサイト コレクション間でコンテンツを再利用することができます。組み込みの検索機能を使用することで、発行のシナリオとアーキテクチャが有効になります。 最初に、SharePoint ファーム間でサイトを設計することで、イントラネットとインターネット間の境界をまたがるサイトが可能になります。
  
    
    

複数の発行サイト コレクションをフィードする 1 つの認証サイト コレクション、異なるドメイン、発行検索エンジンによるクロール、検索エンジン最適化 (SEO) が最適化された、1 つのサイトを検討します。クロスサイト発行により、コンテンツを展開することなく、このシナリオやその他の類似シナリオが可能になります。
クロスサイト発行は次のような一般的なシナリオを考慮して設計されています。
  
    
    


- 発行カタログとしての項目リストまたはページ ライブラリの共有
    
  
- 検索からのカタログの使用
    
  
- クロスサイト発行とバリエーション機能の結合して、共通認証サイト コレクションから認証多言語サイトを可能にする
    
  

## カタログ
<a name="SP15_CrossSitePublising_Catalog"> </a>

SharePoint 2013 で導入されたカタログは、発行サイトでの検索に利用する、共有されたリストまたはライブラリです。カタログによりコンテンツをサイト コレクション間で発行することができます。つまり、クロスサイト発行機能はカタログに依存します。カタログを使用して、ユーザーのサイト間またはイントラネット サイト、エクストラネット サイト、インターネット サイトの境界を越えてコンテンツの再利用ができます。定義済み検索クエリでは、カタログは検索でフラグが設定されます。「 [SharePoint 2013 のコンテンツ検索 Web パーツ](content-search-web-part-in-sharepoint-2013.md)」を使用してサイト コレクションをまたいだカタログに保存されたコンテンツを表示できます。
  
    
    

## クロスサイト発行を使用するタイミング
<a name="SP15_CrossSitePublising_WhenShouldIUseCrossSitePublishing"> </a>

クロスサイト発行が効果的ではない、あるいは適切ではないケースがあります。外部データ ソースがあり、それらに接続するかどうか、バリエーション、サイトの種類、検索データベースの実装、製品カタログの使用はすべて、そのケースの決定に影響を及ぼす要素です。表 1 はこれらの設計の注意事項についての詳細情報を示します。
  
    
    

**表 1. クロスサイト発行の設計の注意事項**


|**設計の注意事項**|**説明**|
|:-----|:-----|
|**ラグ タイム** <br/> |発行元がページを発行する時間とページがサイトに表示される時間が、ページを使用しているユーザーにとって長すぎる場合には、代わりにコンテンツを展開することが可能です。  <br/> |
|**検索データベースの実装** <br/> |検索データベースを外部データ ソースに接続し、外部 (SharePoint 以外の) コネクタを使用する場合には、クロスサイト発行は使用できません。ビジネス コネクティビティ サービス (BCS) を使用する場合は、クロスサイト発行を使用できます。  <br/> 検索エンジンと共にクロスサイト発行を使用することに、意味がない場合があります。計画中の検索データベースや、カスタム コードの実装もない状況では、クロスサイト発行を使用してソース サイトから直接インターネットに発行しないでください。  <br/> |
|**バリエーションの実装** <br/> |ページ ライブラリ、ドキュメント ライブラリ、いくつかの言語で使用可能な一般のリストを作成する基本的なバリエーション サイトを実装するときに、クロスサイト発行が役に立ちます。 バリエーション サイトで管理ナビゲーションや構造化ナビゲーションの実装を選択する場合にも同じことが言えます。  <br/> クロスサイト発行は特定のアーキテクチャでのみ機能します。たとえば、ソースの **SPSite** が他のバリエーション サイトやサイト コレクションからのデータを使用しない場合、クロスサイト発行を使用してバリエーションの **SPSite** からバリエーションが有効化された発行サイトへコンテンツを発行することができます。 <br/> |
|**カタログの実装** <br/> |製品カタログをサイト アーキテクチャに実装し、カタログをどのように実装するかは、クロスサイト発行が最も効果的で適切な選択になるかどうかに影響します。製品カタログを使用して多言語バリエーション サイトの設定をサポートし、それをインターネット サイトで公開している場合、クロスサイト発行を実装できます。  <br/> |
|**管理ナビゲーション** <br/> |クロスサイト発行は管理ナビゲーションと用語ストアのほとんどの実装で動作します。実装の中には、ナビゲーション メタデータ転送が期待どおりに機能しないこともあります。たとえば、あるバリエーション サイトがサイト バリエーションを動かすために他のバリエーション サイトのメタデータに依存しており、クロスサイト発行を使用して対象のサイトにコンテンツを発行する場合、ナビゲーション メタデータ転送は期待どおりに機能しないことがあります。  <br/> |
   

## カタログの設定方法
<a name="SP15_CrossSitePublising_WhenShouldIUseCrossSitePublishing"> </a>

カテゴリ ページおよびカタログ アイテム ページは、構造化されたカタログ コンテンツをサイト全体で同じように表示するために使用できるページ レイアウトです。SharePoint 2013 を使用すると、SharePoint Server 2013 以降のページ レイアウトを作成およびカスタマイズできます。詳細については、「 [SharePoint 2013 でカタログベースのサイトのページ レイアウトをカスタマイズする方法](https://msdn.microsoft.com/ja-jp/library/office/dn144674.aspx
)」を参照してください。
  
    
    

## クロスサイト発行の API
<a name="SP15_CrossSitePublising_CrossSitePublishingAPIs"> </a>

SharePoint 2013 にはクロスサイト発行の実装をサポートするためにコードへ使用できるクラスが導入されています。これらの API は .NET サーバー公開ライブラリで利用することができます。これらの API を使用して、SharePoint 2013 がコンテンツの再利用のためにカタログとしてリストを共有する方法や、検索でカタログを使用する方法をカスタマイズします。次のクラスのメンバーをカスタム コードで使用して、クロスサイト発行タスクをサポートします。
  
    
    

- **PublishingCatalogUtility** クラスを使用し、利用可能なカタログのリストの取得、カタログ情報とステータス情報の取得、カタログに接続できるリストとライブラリについての情報の取得、カタログ共有の開始と停止を行います。
    
    
    


  ```cs
  
  /// Retrieve available catalogs.
  public static List<CatalogConnectionSettings> GetPublishingCatalogs(SPSite site, int startRow, int numberOfRows, string filterText, out int totalNumberOfCatalogs)
  ```


    
    


  ```cs
  
  ///Get catalog information that is saved for a list.
  public static bool GetCatalogConfiguration(SPList list, out CatalogShareSettings catalogSettings, out string selectedTaxonomyField)
  ```


    
    


  ```cs
  
  ///Stop sharing a list or library as a publishing catalog for cross-publishing content reuse.
  public static void UnPublishCatalog(SPList list)
  ```

- **CatalogCollectionManager** クラスを使用し、検索で取得したカタログを使用します。カタログが検索に使用する接続を把握し、その接続についての情報を取得します。カタログの内部コレクションにカタログの追加または削除を行い、 **Update** メソッドが呼び出されたときに URL を書き換える設定がされた接続をキューに登録する操作をキューに入れます。
    
    
    


  ```cs
  
  /// Add catalog or site source into the internal CatalogInfo collection, but the source is not persisted into the property bag.
  public void AddCatalogConnection(CatalogConnectionSettings catalogInfo)
  ```


    
    


  ```cs
  
  /// Queues an Add operation to add a connection configured to rewrite URLs. The connection is added to the store when the Update method is called.
  public void AddCatalogConnection(CatalogConnectionSettings catalogInfo, 
  string[] orderedPropertiesForUrlRewrite,
  string webUrl, 
  string catalogTaxonomyManagedProperty,
  bool isManualRule)
  ```


    
    


  ```cs
  
  /// Update existing catalog/site source in the internal CatalogInfo collection. Edits are not committed until the Update method is called.
  public void UpdateCatalogConnection(CatalogConnectionSettings catalogInfo)
  ```


    
    


  ```cs
  
  /// Remove a catalog or site source. Deletion is not committed until the Update method is called.
  public void DeleteCatalogConnection(string catalogPath)
  ```


    
    


  ```cs
  
  /// Determine whether a connection exists to this source from the site.
  public bool Contains(string catalogPath)
  ```


    
    


  ```cs
  
  /// Get the settings for a catalog connected to this site.
  public CatalogConnectionSettings GetCatalogConnectionSettings(string catalogPath)
  ```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 サイトの発行](publish-sharepoint-2013-sites.md)
    
  

