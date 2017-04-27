---
title: SharePoint 2013 のコンテンツ検索 Web パーツ
ms.prod: SHAREPOINT
ms.assetid: 6fb4bf41-0846-4dca-ad9e-906afdfd3d2b
---


# SharePoint 2013 のコンテンツ検索 Web パーツ

  
    
    
![概要情報トピック](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013の Content Search Web Part (CSWP) について確認します。
## Content Search Web Part (CSWP) のご紹介
<a name="SP15_CSWP_IntroducingCSWP"> </a>

Content Search Web Part (CSWP) は、SharePoint 2013で導入された Web パーツで、SharePoint ページに動的なコンテンツを表示するさまざまなスタイル オプションを使用できます。
  
    
    

## Content Search Web Part の動作
<a name="SP15_CSWP_HowCSWPWorks"> </a>

Content Search Web Part は、ユーザーがフォーマットしやすい方法で検索結果を表示します。各 Content Search Web Part は検索クエリに関連付けられており、その検索クエリの結果を表示します。
  
    
    
ユーザーは、表示テンプレートを使用してページ上の検索結果の外観を変更することができます。表示テンプレートは HTML および JavaScript のスニペットで、SharePoint から返される情報を表示します。表示される情報は JSON 形式でページに挿入されます。 
  
    
    

## Content Search Web Part (CSWP) または Content Query Web Part (CQWP) の使用
<a name="SP15_CSWP_WhenToUseCSWPorCQWP"> </a>

CSWP は、検索インデックスからあらゆるコンテンツを返すことができます。検索サービスに接続していて、インデックス処理された検索結果をページに表示する場合は、SharePoint 2013サイトで CSWP を使用します。 
  
    
    
CSWP は、コンテンツの最後のクロールと同じ新しさのコンテンツを返します。このため、頻繁にクロールを行うと、CSWP によって返されるコンテンツは、あまり頻繁にクロールを行わない場合よりも新しくなります。インスタント コンテンツまたは更新されたバージョンのコンテンツを表示する必要がある場合は、Content Query Web Part (CQWP) を使用します。
  
    
    
検索では、コンテンツのメジャー バージョンのみをクロールし、マイナー バージョンはクロールしません。コンテンツのマイナー バージョンを表示する場合は、CQWP を使用します。
  
    
    
一部のサイト コレクションの管理者は、サイトがインデックス処理されないようにマークしています。このようにマークされたコンテンツは CSWP で使用できません。インデックス処理されないようにマークされたサイトからの検索結果が必要な場合は、CQWP を使用します。
  
    
    

## その他の技術情報
<a name="SP15_CSWP_AdditionalResources"> </a>


-  [SharePoint 2013 でのマネージ ナビゲーション](managed-navigation-in-sharepoint-2013.md)
    
  
-  [開発者向けの SharePoint 2013 検索の新機能](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

