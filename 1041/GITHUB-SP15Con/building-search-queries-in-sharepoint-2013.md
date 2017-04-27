---
title: SharePoint 2013 で検索クエリを作成する
ms.prod: SHAREPOINT
ms.assetid: c4372fcc-4574-4c81-a345-a1bb282ca8f7
---


# SharePoint 2013 で検索クエリを作成する
SharePoint Server 2013でクエリ規則や検索クエリを構築するためにサポートされる検索構文を学習します。
## SharePoint Server 2013で検索クエリを構築するためにサポートされる検索構文
<a name="SP15Buildquery_support"> </a>

SharePoint Server 2013の検索では、検索クエリを構築するためにキーワード クエリ言語 (KQL) および FAST クエリ言語 (FQL) の検索構文がサポートされます。
  
    
    
 **キーワード クエリ言語 (KQL)**
  
    
    
KQL は検索クエリ構築用の既定のクエリ言語です。KQL を使用して、SharePoint Search Service に渡す検索用語やプロパティ制限を指定します。
  
    
    
 **FAST クエリ言語 (FQL)**
  
    
    
FQL は、高度なクエリ演算子をサポートする構造化クエリ言語です。複雑なクエリを作成し、それをプログラムから SharePoint Search Service に渡す場合に FQL を使用できます。FQL は、エンド ユーザーに公開される目的で用意されていないため、既定では無効になっています。 
  
    
    
FQL を有効にするには、 **EnableFQL** プロパティを使用します。既定の検索先をコピーし、Search Service アプリケーション (SSA)、サイト コレクション、またはサイトのいずれかのレベルで、次のどちらかの方法を使用してクエリ変換文字列 `{?{searchTerms} -ContentClass=urn:content-class:SPSPeople}` を変更します。
  
    
    

- KQL フィルター  `-ContentClass:urn:content-class:SPSPeople` をクエリ変換から削除します。結果として、クエリ変換文字列は `{?{searchTerms}}` になります。
    
  
- クエリ変換文字列を、FQL の対応する文字列 ( `{?andnot({searchTerms},filter(contentclass:"urn:content-class:SPSPeople*"))}` など) に置き換えます。
    
  
検索先の詳細およびしくみについては、「 [検索先について](http://office.microsoft.com/en-us/support/sharepoint/sharepointsearch/understanding-result-sources-HA102848849.aspx)」および「 [SharePoint Server 2013 で検索先を構成する](http://technet.microsoft.com/ja-jp/library/jj683115%28v=office.15%29.aspx)」を参照してください。
  
    
    

## このセクションの内容
<a name="SP15Buildquery_support"> </a>


-  [キーワード クエリ言語 (KQL) 構文のリファレンス](keyword-query-language-kql-syntax-reference.md)
    
  
-  [FAST クエリ言語 (FQL) 構文のリファレンス](fast-query-language-fql-syntax-reference.md)
    
  
-  [SharePoint 2013 検索クエリ API を使用する](using-the-sharepoint-2013-search-query-apis.md)
    
  

## その他の技術情報
<a name="SP15Buildquery_addlresources"> </a>


-  [SharePoint 2013 の検索](search-in-sharepoint-2013.md)
    
  
-  [クエリ処理の概要 (SharePoint 2013)](http://technet.microsoft.com/ja-jp/library/jj219620%28v=office.15%29.aspx)
    
  
-  [SharePoint Server 2013 のクエリ変数](http://technet.microsoft.com/ja-jp/library/jj683123.aspx)
    
  

