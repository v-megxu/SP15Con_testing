---
title: SharePoint 2013 のマネージ メタデータとナビゲーション
ms.prod: SHAREPOINT
ms.assetid: b66d4ec1-a2ef-49cc-8ca5-a6b516bff02e
---


# SharePoint 2013 のマネージ メタデータとナビゲーション

  
    
    
![概要情報トピック](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013のエンタープライズ メタデータ管理 (EMM) およびナビゲーション機能について説明します。
## 開発者向け SharePoint 2013 の管理されたメタデータ機能拡張
<a name="SP15_ManagedMetadataAndNav_ManagedMetadataFeatureEnhancements"> </a>

管理されたメタデータを使用して、特定の、詳細なビジネスの必要を満たす分類およびタグ付け戦略を構築できます。SharePoint 2013では、基本的な管理されたメタデータ API セットが拡張され、より多くの機能とシナリオ サポートを提供します。
  
    
    

## 管理されたメタデータ API 向け .NET クライアント オブジェクト モデル (CSOM) のサポート
<a name="SP15_ManagedMetadataAndNav_CSOMSupport"> </a>

SharePoint 2013 CSOM は分類のカスタマイズおよび開発をサポートします。分類は .NET クライアント (CSOM)、Silverlight、および JavaScript プログラミング モデルで使用できます。分類を使用しての開発は, .NET サーバー プログラミング モデルでの開発と論理的に類似しています。コンテンツの読み取りが作成や管理よりも一般的なシナリオをサポートするために、CSOM ソリューションを開発すると便利な場合があります。CSOM を使用して、SharePoint Online のようなクラウド シナリオで、または社内で使用できるシナリオのサブセット用の分類の使用を有効にする必要があります。
  
    
    
分類機能を使用する Visual Studio で新しい CSOM プロジェクトを作成する際は、以下の参照を設定してください。
  
    
    

- Microsoft.SharePoint.Client.dll
    
  
- Microsoft.SharePoint.Client.Runtime.dll
    
  
- Microsoft.SharePoint.Client.Taxonomy.dll
    
  
CSOM でのカスタマイズの開発は, .NET サーバー分類ソリューションの開発に非常に類似しています。セッションに必要な **TaxonomySession** オブジェクトと **TermStore** オブジェクト、 **Group** オブジェクト、 **TermSet** オブジェクト、および **Term** オブジェクトへの参照を取得します。
  
    
    

### コードの例: 分類 CSOM での基本操作
<a name="SP15_ManagedMetadataAndNav_ExampleBasicOperations"> </a>

以下のコードの例を使用して、分類 CSOM での基本操作を完了できます。最初の例では **Group** オブジェクト、 **TermSet** オブジェクト、および **Term** オブジェクトを作成します。2 番目の例では、 **Group** オブジェクトを繰り返し、そのコンテンツを書き込みます。
  
    
    

```cs

       private void CreateColorsTermSet(string siteUrl)
        {
           ClientContext clientContext = new ClientContext(siteUrl);
 
           TaxonomySession taxonomySession = TaxonomySession.GetTaxonomySession(clientContext);
            clientContext.Load(taxonomySession,
                ts => ts.TermStores.Include(
                    store => store.Name,
                    store => store.Groups.Include(
                        group => group.Name
                        )
                    )
                );
            clientContext.ExecuteQuery();
 
           if( taxonomySession != null )
            {
               TermStore termStore = taxonomySession.GetDefaultSiteCollectionTermStore();
               if (termStore != null)
                {
                   //
                   //  Create group, termset, and terms.
                   //
                   TermGroup myGroup = termStore.CreateGroup("MyGroup",Guid.NewGuid());
                   TermSet myTermSet = myGroup.CreateTermSet("Color",Guid.NewGuid(), 1033);
                    myTermSet.CreateTerm("Red", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Orange", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Yellow", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Green", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Blue", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Purple", 1033,Guid.NewGuid());
 
                    clientContext.ExecuteQuery();
                }
            }
        }
 
       private void DumpTaxonomyItems(string siteUrl)
        {
           ClientContext clientContext = new ClientContext(siteUrl);
 
           //
           // Load up the taxonomy item names.
           //
            TaxonomySession taxonomySession =TaxonomySession.GetTaxonomySession(clientContext);
           TermStore termStore = taxonomySession.GetDefaultSiteCollectionTermStore();
            clientContext.Load(termStore,
                    store => store.Name,
                    store => store.Groups.Include(
                        group => group.Name,
                        group => group.TermSets.Include(
                            termSet => termSet.Name,
                            termSet => termSet.Terms.Include(
                                term => term.Name)
                        )
                    )
            );
            clientContext.ExecuteQuery();
 
 
           //
           //Writes the taxonomy item names.
           //
           if( taxonomySession != null )
            {
               if (termStore != null)
                {
                   foreach( TermGroup groupin termStore.Groups)
                    {
                       Console.WriteLine("Group " + group.Name);
 
                       foreach( TermSet termSetin group.TermSets )
                        {
                           Console.WriteLine("TermSet " + termSet.Name);
 
                            foreach(Term term in termSet.Terms)
                            {
                               //Writes root-level terms only.
                               Console.WriteLine("Term " + term.Name);
                            }
                        }
                    }
                }
            }
 
        }

```


  
    
    

## ピン止め
<a name="SP15_ManagedMetadataAndNav_Pinning"> </a>

Microsoft SharePoint Server 2010 で、ユーザーは用語階層の他の場所で用語 (および再利用された用語の下に入れ子になっているすべての用語) を再利用できました。これらの用語が再利用された後、それらは修正され、用語が再利用されたあらゆる場所で変更が表示されました。SharePoint 2013には用語のピン止めが導入されています。 固定された用語は再利用される用語と同様、読み取られる場合を除き、用語が再利用される場所で変更できません。例については、「 [[方法] SharePoint 2013 で用語セット内を移動するために用語を固定するコードを使用する](how-to-use-code-to-pin-terms-to-navigation-term-sets-in-sharepoint-2013.md)」を参照してください。
  
    
    

  
    
    

## 管理されたメタデータの列の種類用データ シート ビューのサポート
<a name="SP15_ManagedMetadataAndNav_DatasheetViewSupport"> </a>

SharePoint 2013では、データシート ビュー機能が変更されました。現在、データシートはダブルクリックの操作を使用して、グリッド編集用の標準ビューを開きます。個別アイテムを編集する際に使用できるものと同じ機能を使用して、メタデータ列を編集できます。これには列の背後にある用語セットへのアクセスも含まれます。この機能により、データシート編集のために個別アイテムを編集する際に使用できるメタデータ修正機能が実現されます。
  
    
    

## 管理されたナビゲーション
<a name="SP15_ManagedMetadataAndNav_ManagedNav"> </a>

管理されたナビゲーションは、用語と共にアイテムをタグ付けしたり、用語ストアの用語を管理したりする機能などの管理メタデータ機能を使用して、高度にカスタマイズされたサイト ナビゲーションを提供します。SharePoint インフラストラクチャによって異なる構造化されたナビゲーションも、SharePoint 2013で引き続き使用できます。
  
    
    

## わかりやすい URL
<a name="SP15_ManagedMetadataAndNav_FriendlyURLs"> </a>

わかりやすい URL とは、ウェルカム ページを含むほとんどの SharePoint 発行ページのアドレス バーに表示される短い URL 形式のことです。それらは SEO フレンドリであり、検索結果に表示されます。 
  
    
    

## 新しいシナリオ向けサポート
<a name="SP15_ManagedMetadataAndNav_SupportForNewScenarios"> </a>

用語ストア マネージャーは、 のより柔軟で力強い管理メタデータ機能に基づく用語使用モデルを拡張し、展開できます。
  
    
    

- 別のサイト コレクションにリンクし、他のサイトを表示します。Managed Metadata Service に接続される他のサイト コレクションで使用可能な用語を設定する場合は、 **global term set** を作成します。特定のサイト コレクションが Managed Metadata Service に保存される場合にのみ使用できるプライベート用語セットを作成する場合は、 **local term set** を作成します。
    
  
- 特定の用語セットの範囲外のキーワードの使用からユーザーをブロックします。
    
  
- 自動翻訳や柔軟性のある LCID 向けサポートを含め、追加の多言語サポートを取得します。 
    
  

## カスタム サイト定義を扱う際にサポートされないシナリオ
<a name="SP15_ManagedMetadataAndNav_UnsupportedScenarios"> </a>


- SharePoint 2013 は、分類フィールド (管理されたメタデータ サイト列) を XML 定義により宣言して作成することをサポートしていません。
    
  
- SharePoint 2013 は、サイト テンプレートで分類フィールド (管理されたメタデータ サイト列) を使用することをサポートしていません。
    
  
- 詳細については、Microsoft サポート記事 #898631「 [サポート対象とサポート非対象のシナリオ](http://support2.microsoft.com/default.aspx?scid=kb;JA-JP;898631
)」を参照してください。
    
  

## その他の技術情報
<a name="SP15_ManagedMetadataAndNav_AdditionalResources"> </a>


-  [SharePoint 2013 でのマネージ ナビゲーション](managed-navigation-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のコンテンツ検索 Web パーツ](content-search-web-part-in-sharepoint-2013.md)
    
  

