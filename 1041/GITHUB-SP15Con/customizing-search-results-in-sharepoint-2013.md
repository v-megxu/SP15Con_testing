---
title: SharePoint 2013 での検索結果のカスタマイズ
ms.prod: SHAREPOINT
ms.assetid: 1b30f6df-643a-4570-ae5c-d3d8df5609b8
---


# SharePoint 2013 での検索結果のカスタマイズ
SharePoint Server 2013 の検索結果セットで、類似したアイテムのグループ化、または重複したアイテムの削除を行い、結果を簡潔に読みやすく表示できるようにする方法を説明します。
検索結果でグループ化を行うと、検索結果セットの中の 2 つ以上の類似したアイテムが折りたたまれ、ユーザーが読みやすい表示になります。検索結果の重複の削除はグループ化の一部であり、同一またはほぼ同一のアイテムが結果セットから削除されます。SharePoint 管理者が行った設定によっては、ユーザーが後で検索結果セットを展開し、折りたたまれた個々の結果を参照できる場合があります。
  
    
    

次に、検索結果をグループ化する方法の例を示します。
- 重複の検出。ほぼ同一のドキュメントは結果セットから削除されます。
    
  
- サイトの折りたたみ。各サイトで検出されたアイテムのうち最も関連したアイテムだけが結果セットに表示されます。
    
  
- ドキュメント セットの折りたたみ。SharePoint の各ドキュメント ライブラリに対してヒットしたものが 1 つだけが表示されます。
    
  
クエリ オブジェクト モデルの中で次の  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) プロパティを使用して、折りたたみ、または重複の削除をプログラム的に行う基準を指定できます。
-  [CollapseSpecification](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.CollapseSpecification.aspx)
    
  
-  [TrimDuplicates](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Query.TrimDuplicates.aspx)
    
  
-  [TrimDuplicatesOnProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesOnProperty.aspx)
    
  
-  [TrimDuplicatesKeepCount](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesKeepCount.aspx)
    
  
-  [TrimDuplicatesIncludeId](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.TrimDuplicatesIncludeId.aspx)
    
  

## CollapseSpecification プロパティを使用して、類似した検索結果を折りたたむ
<a name="bk_collapse_specification"> </a>

 **CollapseSpecification** プロパティは、コンマまたはスペースのどちらかで区切って複数のフィールドを含められる _Spec_ パラメーターをとります。まとめて評価される、これらのフィールドによって、折りたたみに使用する基準のセットを指定します。
  
    
    
 **構文**
  
    
    
 `CollapseSpecification = Spec`
  
    
    
次の表に、 _Spec_ パラメーターのフィールドの一覧を示します。
  
    
    

**表 1. Spec パラメーター フィールド**


|**パラメーターの要素**|**説明**|
|:-----|:-----|
| _Spec_ <br/> | `Subspec(<space>Subspec)*` <br/> |
| _Subspec_ <br/> | `Prop(','Prop)*[':'Dups]` <br/> |
| _Prop_ <br/> |有効な管理プロパティまたは管理プロパティの別名。 _Prop_ は大文字と小文字の区別をしません。管理プロパティはクエリを実行できる必要があり、並べ替えまたは絞り込みを実行できる必要があります。 <br/> |
| _Dups_ <br/> |保持するアイテムの数を指定する整数。既定値は 1 です。  <br/> |
| _<space>_ <br/> |プロパティは、 **OR** 演算子を使用して結合されます。 <br/> |
| _,_ <br/> |プロパティは、 **AND** 演算子を使用して結合されます。 <br/> |
| _*_ <br/> |さらにアイテムが続くことを示します。  <br/> |
| _() or []_ <br/> |オプションのアイテムを示します。  <br/> |
   
 _Spec_ のフィールドがコンマで区切られている場合、フィールドは **AND** 演算子を使用して結合されます。指定したフィールドすべてに一致すると、そのアイテムは折りたたまれます。
  
    
    
一方、 _Spec_ のフィールドがスペースで区切られている場合、 **AND** 演算子および **OR** 演算子を含む拡張を使用して、フィールド (または _Subspecs_) が結合されます。たとえば、 `Category:3 Product:2` のような式は、内部で変換されて、次の式 `(Category AND Product) OR (Category)` になり、それぞれがカウントされます。そのため、最大で前者が 2 つと後者が 3 つになります。指定したフィールドの一部と一致すると、アイテムは折りたたまれます。
  
    
    

### CollapseSpecification の使用例

次の表に、Contoso 社の製品カタログを示します。以下の一連の例では、このカタログを使用して、 **CollapseSpecification** プロパティがどのように動作するかを示します。
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|ノート PC  <br/> |WWI  <br/> |19W X0196 黒  <br/> |コンピューター 1  <br/> |
|ノート PC  <br/> |Adventure Works  <br/> |12 M1201 赤  <br/> |コンピューター 2  <br/> |
|ノート PC  <br/> |Adventure Works  <br/> |15.4W M1548 白  <br/> |コンピューター 3  <br/> |
|ノート PC  <br/> |Proseware  <br/> |19 X910 黒  <br/> |コンピューター 4  <br/> |
|ノート PC  <br/> |Proseware  <br/> |ノート PC 19 X910 黒  <br/> |コンピューター 5  <br/> |
|デスクトップ  <br/> |Adventure Works  <br/> |2.33 XD233 シルバー  <br/> |コンピューター 6  <br/> |
|デスクトップ  <br/> |WWI  <br/> |2.33 X2330 黒  <br/> |コンピューター 7  <br/> |
|デスクトップ  <br/> |Adventure Works  <br/> |1.60 ED160 白  <br/> |コンピューター 8  <br/> |
|デスクトップ  <br/> |WWI  <br/> |3.0 M0300 シルバー  <br/> |コンピューター 9  <br/> |
   

  
    
    

#### 例: Category によるグループ化

まず、 **Category** に基づいてアイテムをグループ化し、グループごとに上位 2 つ (つまり `"Category:2"`) を表示します。次に、各 **Category** について、対応する数の一意な (つまり "Product:1" の) **Products** を表示します。
  
    
    
 **構文**
  
    
    
 `CollapseSpecification="Category:2 Product:1"`
  
    
    
これにより次のような結果が戻ります。
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|ノート PC  <br/> |WWI  <br/> |19W X0196 黒  <br/> |コンピューター 1  <br/> |
|ノート PC  <br/> |Adventure  <br/> |12 M1201 赤  <br/> |コンピューター 2  <br/> |
|デスクトップ  <br/> |Adventure Works  <br/> |2.33 XD233 シルバー  <br/> |コンピューター 6  <br/> |
|デスクトップ  <br/> |WWI  <br/> |2.33 X2330 黒  <br/> |コンピューター 7  <br/> |
   
 **CollapseSpecification** プロパティを使用して検索結果を折りたたむには、次のコードを使用します。
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
        {
            QueryText = "Title:Computer",
            CollapseSpecification = "Category:3 Product:1",
        };

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    {
        Console.WriteLine(result["Title"]);
    }
}

```


#### 例: Category および Product によるグループ化

まず、 **Category** および **Product** に基づいてアイテムをグループ化します。次に、独特の組合せをそれぞれ表示します。
  
    
    
 **構文**
  
    
    
 `CollapseSpecification="Category,Product:1"`
  
    
    
これにより次のような結果が戻ります。
  
    
    


|**Category**|**Product**|**Variant**|**Title**|
|:-----|:-----|:-----|:-----|
|ノート PC  <br/> |WWI  <br/> |19W X0196 黒  <br/> |コンピューター 1  <br/> |
|ノート PC  <br/> |Adventure Works  <br/> |12 M1201 赤  <br/> |コンピューター 2  <br/> |
|ノート PC  <br/> |Proseware  <br/> |19 X910 黒  <br/> |コンピューター 4  <br/> |
|デスクトップ  <br/> |Adventure Works  <br/> |2.33 XD233 シルバー  <br/> |コンピューター 6  <br/> |
|デスクトップ  <br/> |WWI  <br/> |2.33 X2330 黒  <br/> |コンピューター 7  <br/> |
   

## TrimDuplicates プロパティを使用して、重複した検索結果を取り除く
<a name="bk_trim_duplicates"> </a>

 **TrimDuplicates** を使用して、結果セットから重複した検索結果を取り除くかどうかを指定します。既定では **TrimDuplicates** は **true** です。
  
    
    
 **TrimDuplicates** を **TrimDuplicatesOnProperty** または、望ましくは **CollapseSpecification** と共に使用する場合、 **TrimDuplicates** は **false** に設定されます。
  
    
    
 **構文**
  
    
    
 `TrimDuplicates = <$true | $false>`
  
    
    

### TrimDuplicatesOnProperty プロパティを使用して、重複した検索結果を取り除く
<a name="bk_trim_duplicates_on_property"> </a>

 **TrimDuplicatesOnProperty** を使用して、既定以外の管理プロパティを、重複の削除の基準として使用するかどうかを指定します。既定値は、 **DocumentSignature** 管理プロパティです。管理プロパティは **Integer** 型または **String** 型である必要があります。アイテムのグループ化を表す管理プロパティを使用して、この機能をフィールドの折りたたみに使用できます。
  
    
    
 **構文**
  
    
    
 `TrimDuplicatesOnProperty = <managed property>`
  
    
    

> **メモ**
> SharePoint Server 2013 では、可能な限り、 **CollapseSpecification** を使用してください。 **TrimDuplicatesOnProperty** は下位互換性のためだけに利用できます。
  
    
    


### TrimDuplicatesKeepCount プロパティを使用して、重複した検索結果を取り除く
<a name="bk_trim_duplicates_keep_count"> </a>

 **TrimDuplicates** が **true** の場合、 **TrimDuplicatesKeepCount** を使用して、保持するドキュメントの数を指定します。 **TrimDuplicates** が、グループ ID (たとえば、サイト ID) として使用できる管理プロパティに基づいている場合、グループごとに戻す結果の数を制御できます。戻されるアイテムは、各グループ内で最も動的ランクの高いものです。
  
    
    
 **構文**
  
    
    
 `TrimDuplicatesKeepCount = <number>`
  
    
    

### TrimDuplicatesIncludeId プロパティを使用して、重複した検索結果を取得する
<a name="bk_trim_duplicates_include_id"> </a>

 **TrimDuplicates** が **true** で、 **TrimDuplicatesOnProperty** または **CollapseSpecification** が **false** に設定されている場合、 **TrimDuplicatesIncludeId** を使用して、重複したドキュメントを取得します。
  
    
    
特定のドキュメントの重複を取得するには、ドキュメント ID ( _docid_) を使用します。
  
    
    
 **構文**
  
    
    
 `TrimDuplicatesIncludeId = <docid>`
  
    
    

> **メモ**
> FAST Search Server 2010 for SharePoint の  _fcoid_ 管理プロパティは、SharePoint Server 2013 で _docid_ 管理プロパティに置き換わりました。
  
    
    


## その他の技術情報
<a name="bk_addresources"> </a>


-  [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx)
    
  
-  [SharePoint Server 2013 の検索スキーマの概要](http://technet.microsoft.com/ja-jp/library/jj219669%28office.15%29.aspx)
    
  

  
    
    

