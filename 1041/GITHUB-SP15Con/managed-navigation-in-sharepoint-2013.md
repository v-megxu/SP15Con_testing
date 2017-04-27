---
title: SharePoint 2013 でのマネージ ナビゲーション
ms.prod: SHAREPOINT
ms.assetid: c9da5011-3c73-4b83-8e00-e7a03a71ed02
---


# SharePoint 2013 でのマネージ ナビゲーション

  
    
    
![概要情報トピック](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013での分類に基づく管理ナビゲーション機能について説明します。
## 管理ナビゲーションの概要
<a name="SP15_ManagedNav_Introducing"> </a>

優れた設計のナビゲーションは、サイトの訪問者に、Web サイトが提供するビジネス、製品、サービスに関する多くの情報を提供します。ナビゲーションの基盤となる分類を更新することで、サイトのナビゲーションをプロセスで再作成せずに、ビジネスは変更を推進し、維持することができます。SharePoint 2013では、管理ナビゲーション機能を使用して、管理されたメタデータに基づくサイト ナビゲーションを設計でき、管理ナビゲーション構造による SEO フレンドリな URL を作成することができます。管理ナビゲーションは、SharePoint の構造に基づいた従来の SharePoint ナビゲーション機能 (構造化ナビゲーション) に代わるものです。管理ナビゲーションは分類に基づくため、サイトやサイト コンポーネントの構造を変更せずに、重要なビジネス コンセプトに沿ったサイト ナビゲーションを設計するために使用することができます。
  
    
    

## 管理ナビゲージョンの動作の仕組み
<a name="SP15_ManagedNav_HowManagedNavWorks"> </a>

管理ナビゲーションは、ページを動的に生成するためのフレームワークです。関連付けられた SEO フレンドリな URL を提供します。生成された各ページは、ナビゲーションの階層に表示されます。分類のカテゴリごとに個別にページを作成しなくても、フレームワークで提供されるテンプレートと継承メカニズムを使用して、各ナビゲーション リンクのランディング ページを作成することができます。トピック ページの機能を使用して、ランディング ページの動作をカスタマイズすることができます。
  
    
    
管理ナビゲーション API が SharePoint 2013の分類ライブラリと公開ライブラリに含まれています。タームセットやターム ストアなどの管理されたメタデータ コンポーネントを使用して、分類に基づくナビゲーションをサイトで実現できます。.NET サーバー クラス ライブラリ、 [Microsoft.SharePoint.Publishing.Navigation](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.Navigation.aspx) 名前空間には、ターム、ターム セット、および [Microsoft.SharePoint.Taxonomy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Taxonomy.aspx) ナビゲーション名前空間内の **Term** クラスと **TermSet** クラスをミラーリングする他のクラス オブジェクトが含まれており、これらのメタデータ項目をナビゲーション要素に関連付けるために特に設計されたメソッドとプロパティを提供します。 [TaxonomySiteMapNode](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.Navigation.TaxonomySiteMapNode.aspx) などの他のクラスを使用して、サイト マップのノードやサイトのナビゲーションの他の部分など、サイト ナビゲーションのさまざまな要素をメタデータに追加できます。管理ナビゲーションのキャッシングとコンテキストを有効にする他のクラスも備わっています。
  
    
    
分類に基づくナビゲーション リンクは、グローバル ナビゲーションに表示できます。グローバル ナビゲーションは、必ず 1 つ以上のレイヤーを含むナビゲーション レイヤーで、通常は、サイトのトップに表示され、最上位のコンテンツ カテゴリを表します。通常、ページの左側に表示される現在のナビゲーション コントロールにこれらのリンクを表示することもできます。現在のナビゲーション コントロールには、グローバル ナビゲーションで選択されたカテゴリのすぐ下の階層 (そのカテゴリに属するリンクのセット) が表示されます。
  
    
    

## フレンドリ URL と管理ナビゲーション プロバイダー
<a name="SP15_ManagedNav_FriendlyURLs"> </a>

はじめて SharePoint 2013 サイトを閲覧したときに、URL の形式が変更されていることに気がつきます。 `/Pages/default.aspx` でアドレスが拡張される代わりに、ページの URL の末尾には、 `/` のみが付いています。管理ナビゲーションは、サイト、カテゴリ、およびアイテム ページにわたって一貫したフレンドリ URL のスキームを提供します。
  
    
    
管理ナビゲーション プロバイダーがこの動作を実現します。管理ナビゲーション プロバイダーを使用するサイトのルートに移動すると、ブラウザーに読み込まれて表示されるページはサイトのウェルカム ページの設定によって制御されますが、表示される URL (および検索結果で表示される URL) は、この分かりやすい形式に書き換えられます。
  
    
    
サイトのウェルカム ページを含むすべてのページに、フレンドリ URL を表示させることができます。サイトの構成によって、ほとんどのページに自動的にフレンドリ URL が表示されるようにできます。フレンドリ URL は各国語にローカライズできます。
  
    
    

## 管理ナビゲーション API
<a name="SP15_ManagedNav_ManagedNavAPIs"> </a>

SharePoint 2013では、分類用 API によって新しいメソッドとプロパティがいくつか提供されます。これらを使用して、サイト ナビゲーションのシナリオの用途に合わせてターム、ターム セット、およびターム ストアの他のメタデータ要素をカスタマイズすることができます。これらの API は .NET クライアント, .NET サーバー、Silverlight、および JavaScript のプログラミング モデルで使用できます。
  
    
    

## コード例: .NET クライアント オブジェクト モデル (CSOM) API を使用した、管理ナビゲーションのカスタマイズ
<a name="SP15_ManagedNav_CustomizingManagedNavWithNETCSOM"> </a>

分類に .NET クライアント オブジェクト モデルを使用するときに、現在のサイトのコレクションにターム ストアが存在する場合は、新しいナビゲーション ターム セットを作成するか、既存のターム セットを利用して管理ナビゲーションをサポートするターム セットに変えることができます。
  
    
    

  
    
    



```cs

///Create a navigation term set.
public class NavigationTermSetTests
    {
      public void CreateNavigationTermSet()
              {
               ClientContext clientContext = new ClientContext(TestConfig.ServerUrl);
            
                 TaxonomySession taxonomySession = TaxonomySession.GetTaxonomySession(clientContext);
                 taxonomySession.UpdateCache();

                 clientContext.Load(taxonomySession, ts => ts.TermStores);
                 clientContext.ExecuteQuery();

                 if (taxonomySession.TermStores.Count == 0)
                 throw new InvalidOperationException("The Taxonomy Service is offline or missing");

                 TermStore termStore = taxonomySession.TermStores[0];
                 clientContext.Load(termStore, 
                 ts => ts.Name, 
                 ts => ts.WorkingLanguage);

                 // Does the TermSet object already exist?
                 TermSet existingTermSet;

                 // Handles an error that occurs if the return value is null.
                 ExceptionHandlingScope exceptionScope = new ExceptionHandlingScope(clientContext);
             using (exceptionScope.StartScope())
                 {
                 using (exceptionScope.StartTry())
                 {
                 existingTermSet = termStore.GetTermSet(TestConfig.NavTermSetId);
                 }
                 using (exceptionScope.StartCatch())
                {
                }
                }
                clientContext.ExecuteQuery();

                if (!existingTermSet.ServerObjectIsNull.Value)
                {
                Log("CreateNavigationTermSet(): Deleting old TermSet");
                existingTermSet.DeleteObject();
                termStore.CommitAll();
                clientContext.ExecuteQuery();
                }

                Log("CreateNavigationTermSet(): Creating new TermSet");

               // Creates a new TermSet object.
            TermGroup siteCollectionGroup = termStore.GetSiteCollectionGroup(clientContext.Site, 
                createIfMissing: true);
            TermSet termSet = siteCollectionGroup.CreateTermSet("Navigation Demo", TestConfig.NavTermSetId, 
                termStore.WorkingLanguage);

            termStore.CommitAll();
            clientContext.ExecuteQuery();

            NavigationTermSet navTermSet = NavigationTermSet.GetAsResolvedByWeb(clientContext,
                termSet, clientContext.Web, "GlobalNavigationTaxonomyProvider");

            navTermSet.IsNavigationTermSet = true;
            navTermSet.TargetUrlForChildTerms.Value = "~site/Pages/Topics/Topic.aspx";

            termStore.CommitAll();
            clientContext.ExecuteQuery();

            NavigationTerm term1 = navTermSet.CreateTerm("Term 1", NavigationLinkType.SimpleLink, Guid.NewGuid());
            term1.SimpleLinkUrl = "http://www.bing.com/";

            Guid term2Guid = new Guid("87FAA433-4E3E-4500-AA5B-E04330B12ACD");
            NavigationTerm term2 = navTermSet.CreateTerm("Term 2", NavigationLinkType.FriendlyUrl,
                term2Guid);

            NavigationTerm childTerm = term2.CreateTerm("Term 2 child", NavigationLinkType.FriendlyUrl, Guid.NewGuid());

            childTerm.GetTaxonomyTerm().TermStore.CommitAll();
            clientContext.ExecuteQuery();
}


```


## コード例: .NET サーバー オブジェクト モデル API を使用した管理ナビゲーションのカスタマイズ
<a name="SP15_ManagedNav_CustomizingManagedNavNETServerObjectModel"> </a>

 [Microsoft.SharePoint.Taxonomy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Taxonomy.aspx) と [Microsoft.SharePoint.Publishing.Navigation](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.Navigation.aspx) の名前空間に .NET サーバーの分類クラスとメソッドを使用して、新しいナビゲーション ターム セットを作成することができます。
  
    
    

  
    
    



```cs

///Create a navigation term set.
using (SPSite site = new SPSite(TestConfig.ServerUrl))
            {
                using (SPWeb web = site.OpenWeb())
                {
                    TaxonomySession taxonomySession = new TaxonomySession(site, updateCache: true);

                    /// Use the first TermStore object in the list.
                    if (taxonomySession.TermStores.Count == 0)
                        throw new InvalidOperationException("The Taxonomy Service is offline or missing");

                    TermStore termStore = taxonomySession.TermStores[0];

                    /// Does the TermSet object already exist?
                    TermSet existingTermSet = termStore.GetTermSet(TestConfig.NavTermSetId);
                    if (existingTermSet != null)
                    {
                        Log("CreateNavigationTermSet(): Deleting old TermSet");
                        existingTermSet.Delete();
                        termStore.CommitAll();
                    }

                    Log("CreateNavigationTermSet(): Creating new TermSet");

                    /// Create a new TermSet object.
                    Group siteCollectionGroup = termStore.GetSiteCollectionGroup(site);
                    TermSet termSet = siteCollectionGroup.CreateTermSet("Navigation Demo", TestConfig.NavTermSetId);

                    NavigationTermSet navTermSet = NavigationTermSet.GetAsResolvedByWeb(termSet, web,
                        StandardNavigationProviderNames.GlobalNavigationTaxonomyProvider);

                    navTermSet.IsNavigationTermSet = true;
                    navTermSet.TargetUrlForChildTerms.Value = "~site/Pages/Topics/Topic.aspx";

                    NavigationTerm term1 = navTermSet.CreateTerm("Term 1", NavigationLinkType.SimpleLink);
                    term1.SimpleLinkUrl = "http://www.bing.com/";

                    Guid term2Guid = new Guid("87FAA433-4E3E-4500-AA5B-E04330B12ACD");
                    NavigationTerm term2 = navTermSet.CreateTerm("Term 2", NavigationLinkType.FriendlyUrl,
                        term2Guid);

                    /// Verify that the NavigationTermSetView is being applied correctly.
                    Assert.AreEqual(web.ServerRelativeUrl + "/term-2", term2.GetResolvedDisplayUrl(null).ToString());

                    string expectedTargetUrl = web.ServerRelativeUrl 
                        + "/Pages/Topics/Topic.aspx?TermStoreId=" + termStore.Id.ToString() 
                        + "&amp;TermSetId=" + TestConfig.NavTermSetId.ToString()
                        + "&amp;TermId=" + term2Guid.ToString();
                    Assert.AreEqual(expectedTargetUrl, term2.GetResolvedTargetUrl(null, null).ToString());

                    NavigationTerm childTerm = term2.CreateTerm("Term 2 child", NavigationLinkType.FriendlyUrl);
                    Assert.AreEqual(web.ServerRelativeUrl + "/term-2/term-2-child", childTerm.GetResolvedDisplayUrl(null).ToString());

                    /// Commit changes.
                    childTerm.GetTaxonomyTerm().TermStore.CommitAll();
                }
            }
```


## その他の技術情報
<a name="SP15_ManagedNav_AdditionalResources"> </a>


-  [SharePoint 2013 のコンテンツ検索 Web パーツ](content-search-web-part-in-sharepoint-2013.md)
    
  

