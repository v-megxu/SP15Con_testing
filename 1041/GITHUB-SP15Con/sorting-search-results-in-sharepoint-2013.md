---
title: SharePoint 2013 での検索結果の並べ替え
ms.prod: SHAREPOINT
ms.assetid: 66af835e-2c8f-405e-8bed-cb1e5436e190
---



# SharePoint 2013 での検索結果の並べ替え

  
    
    
![概要情報トピック](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
SharePoint Server 2013 のクエリ オブジェクト モデルを使用することにより、プログラムを使用して検索結果を (ランクにより、管理プロパティ値により、数式により、またはランダムな順により) 並べ替えます。 
次の 4 つの方法で SharePoint Server 2013 の検索結果を並べ替えることができます。
  
    
    


-  [ランクによる検索結果の並べ替え](#SP15_Sort_search_resuilts_by_rank): 検索結果を関連性ランクによって並べ替えることを可能にします。
    
  
-  [管理プロパティ値による検索結果の並べ替え](#SP15_Sort_search_results_by_managed_property_value): 検索結果を 1 つ以上の管理プロパティ値に基づいて並べ替えることを可能にします。
    
  
-  [数式による検索結果の並べ替え](#SP15_Sort_search_results_by_formula): 検索結果をクエリ要求に指定した数式によって並べ替えることを可能にします。
    
  
-  [ランダムな順序での検索結果の並べ替え](#SP15_Sort_search_results_in_random_order): 検索結果をランダムな順で並べ替えること、または並べ替えの順序にランダムなコンポーネントを追加することができます。
    
  

この記事ではプログラムを使用して検索結果を並べ替える方法について説明します。SharePoint Server 2013 クエリ ルールを使用して検索結果を並べ替える方法については、以下の記事を参照してください。
  
    
    


-  [「クエリ ルールを管理する」の「ランク付けされた検索結果を変更する」](http://technet.microsoft.com/ja-jp/library/jj871676.aspx#BKMK_ChangeRankedSearchResults)
    
  
-  [「Web コンテンツ管理のクエリ ルールを作成する」の「ランク付けされた検索結果を変更する」](http://technet.microsoft.com/ja-jp/library/jj871014.aspx#BKMK_ChangeRankedSearchResults)
    
  

## クエリ要求で並べ替えを指定する方法
<a name="SP15_Specify_sorting_in_query_request"> </a>

クエリ オブジェクト モデルを使用するとき、 [KeywordQuery](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.aspx) クラスの [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) プロパティによって並べ替え仕様を指定することにより、並べ替え条件を選択できます。 [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) プロパティは、 [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) オブジェクトのコレクションを表すタイプ [SortCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortCollection.aspx) です。
  
    
    
 [Sort](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.aspx) オブジェクトには、検索結果を並べ替える方法を定義します。これには、検索結果を並べ替える基準となる値 ( [Property](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Property.aspx) ) と検索結果を並べ替える方向 ( [Direction](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.Sort.Direction.aspx) ) とが含まれます。方向はタイプ [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) で、昇順または降順を指定できます。
  
    
    
 [SortList](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.KeywordQuery.SortList.aspx) に複数の値が含まれる場合、それらの値が指定されている順序で並べ替えが実行されます。つまり、すべての **Sort** オブジェクトは 1 つの並べ替え順序レベルを表します。後続のレベルは、直前のレベルに基づいて調整された並べ替え結果を変更しませんが、直前のレベルでは並べ替えの値が同じであった複数の結果に対して、内部的な順序付けに影響を与えることがあります。
  
    
    
クエリ オブジェクト モデルとは別に、SharePoint Server 2013 には、クライアント アプリケーションやモバイル アプリケーションで検索インデックスをクエリするために使用できる、検索 REST サービスも備わっています。検索 REST サービスは、HTTP POST 要求と HTTP GET 要求の両方をサポートしています。それらの要求用に URI を構成する方法について詳しくは、「 [検索 REST サービスでクエリを実行する](sharepoint-search-rest-api-overview.md#bk_queryrest)」を参照してください。
  
    
    

## ランクによる検索結果の並べ替え
<a name="SP15_Sort_search_resuilts_by_rank"> </a>

既定では、検索結果は関連性のランクによって並べ替えられます。つまり、SharePoint Server 2013 は、検索結果セットの最上位に最も関連性の高い結果を配置します。ランクによって並べ替える場合、結果は常に降順で並べ替えられます。ただし、 [SortDirection()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Query.SortDirection.aspx) を使用して並べ替えの順序を昇順に変更することができます。
  
    
    
また、次の 2 つの方法のいずれかで、クエリ文字列内のランクの計算に影響を与えることができます。
  
    
    

-  [キーワード クエリ言語 (KQL) 構文のリファレンス](keyword-query-language-kql-syntax-reference.md) および [FAST クエリ言語 (FQL) 構文のリファレンス](fast-query-language-fql-syntax-reference.md) で使用可能な **XRANK** 演算子を使用する方法。 **XRANK** を使用して、特定のクエリ条件が満たされた場合に条件付きランク向上を適用できます。
    
  
- 動的ランクにおける関連性の重みを選択する方法。FQL を使用するとき、 **STRING** 演算子ごとに個別の関連性の重みを指定できます。
    
  

## 管理プロパティ値による検索結果の並べ替え
<a name="SP15_Sort_search_results_by_managed_property_value"> </a>

1 つ以上の管理プロパティの値に基づいて検索結果を並べ替えるようにし指定できます。つまり、SharePoint Server 2013 は、クエリに一致するすべての結果に基づいた並べ替えを実行します。
  
    
    
テキスト プロパティと数値プロパティに基づいて並べ替えることができます。テキスト プロパティの場合、標準のテキスト文字列の並べ替えに基づいて並べ替えられます。それに対して、数値プロパティ (タイプ  [DateTime](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.DateTime.aspx) の管理プロパティを含む) の場合、並べ替えは数値に基づいてなされます。
  
    
    

### 例

次の例では、 **Size** 管理プロパティを使用して検索結果を並べ替える方法を示します。
  
    
    

```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("Size", SortDirection.Descending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"] + " Size:" + result["Size"]);
    }
}
```

または、検索 REST API を使用して、以下の呼び出しで **Size** プロパティを使用することにより、検索結果を並べ替えることもできます。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='size:descending'
```


## 数式による検索結果の並べ替え
<a name="SP15_Sort_search_results_by_formula"> </a>

並べ替えの値を作成する数式を使用する並べ替えの仕様に基づいて、検索結果の並べ替えを指定することができます。
  
    
    
数式による並べ替えの機能は、検索結果を単一レベルと複数レベルで並べ替える機能の拡張機能です。この機能では、並べ替え条件として管理プロパティではなく数式を指定することができます。 
  
    
    
数式によって並べ替える機能を使用して、検索結果に含まれるアイテムごとに、算術演算を 1 つ以上の管理プロパティの値に適用できます。
  
    
    
以下の例は、検索結果の並べ替えを指定する数式を使用して実装できます。
  
    
    

- ドキュメントを分類するための K 近傍法。
    
  
- 地理的な距離を計算するためのユークリッド距離またはマンハッタン距離。
    
  
- 優先値。たとえば、ある管理プロパティ値が優先値からどれほど離れているかに基づいてドキュメントを並び替えるためなどに使用します。
    
  
数式による並べ替えの機能には、用語の頻度や類似性など、動的な統計ランク パラメーターのコントロールは含まれません。
  
    
    
数式は左から右に評価され、標準の算術演算子の優先順位が使用されます。つまり、関数とかっこで囲まれたグループが最初に評価され、乗算と除算の演算が次に実行され、加算と減算の演算が最後に実行されます。
  
    
    

> **重要**
> 数数式の最終結果は、32 ビットの符号付き整数型の値の範囲でなければなりません。そうでない場合、正確に並べ替えできないことがあります。 
  
    
    


### クエリでの並べ替えの数式の指定

クエリ要求の並べ替えの指定では、管理プロパティではなく、並べ替えの数式を指定します。
  
    
    
並べ替えの指定は、 `[formula:<sort-formula>]` の形式になります。
  
    
    
この形式で、 _<sort-formula>_ が並べ替えの数式です。
  
    
    

> **メモ**
> 角かっこは、並べ替えを指定する構文の一部です。 
  
    
    

既定での並べ替えの方向は降順です。数式が地理的な距離を指定する場合などは、値を昇順で並べ替える数式を使用することもできます。
  
    
    
次のコード例は、クエリ オブジェクト モデルを使用して、昇順で並べ替える数式により並べ替えを指定する方法を示しています。
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(2000-size)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

または、検索 REST API を使用して、次の呼び出しで **Size** プロパティを使用することにより、検索結果を並べ替えることもできます。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(2000-size)]:ascending'

```


### 並べ替えの数式での管理プロパティの使用

並べ替えの数式を、タイプ  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) 、 [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) 、および [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) の管理プロパティの値に適用できます。検索スキーマ内での指定の管理プロパティの並べ替えを有効にする必要があります。
  
    
    
タイプ  [Decimal](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Decimal.aspx) の管理対象プロパティの場合、値は数式の評価で使用される前に 10^(10 進数) 倍になります。
  
    
    
タイプ  [Datetime()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Datetime.aspx) の管理プロパティの場合、値は数式の評価で使用される前に、紀元前 29000 年 1 月 1 日以降の 100 ナノ秒の数に変換されます。その年には 366 日があります。
  
    
    

### 並べ替えの数式

表 1 では、並べ替えの数式で使用できる関数を示します。式にスペースを含めることはできません。
  
    
    

**表 1。数式の関数**


|**関数**|**説明**|
|:-----|:-----|
|**+** <br/> |加算を指定します。  <br/> |
|**-** <br/> |減算を指定します。  <br/> |
|* <br/> |乗算を指定します。  <br/> |
|**/** <br/> |除算を指定します。  <br/> > **メモ**> 既定では、ゼロによる除算の結果は例外となり、クエリはエラーで返されます。 **errtolast** 演算子を使用すると、クエリ エラーは回避されて、失敗したアイテムは結果セットの最後に配置されます。          |
|**rank** <br/> |アイテムの動的ランクを表す特別なキーワード。  <br/> 例:  `abs(rank-100)` は、ランク値 100 からの距離を並べ替え基準として使用します。 <br/> |
|**[0-9.]+** <br/> |数値を整数または倍精度の値で指定できることを示します。  <br/> 例: 503、3.14、5.4352262  <br/> |
|**[a-z0-9]+]** <br/> |関数名として認識されない文字シーケンスは管理プロパティ名として扱われるように指定します。検索スキーマ内での指定した管理プロパティの並べ替えを有効にする必要があります。  <br/> 例: 並べ替えの有効な **height** という名前の管理プロパティを定義できます。これにより、「height」を数式の中の式として使用できます。数式は **height** 管理プロパティの値を使用します。 <br/> |
|**( and )** <br/> |計算をグループ化して優先順位が正しくなるようにするために使用されます。  <br/> 例: 4*(3+2)  <br/> |
|**sqrt(n)** <br/> | _n_ の平方根。 <br/> |
|**exp(n)** <br/> | *pow(2.71828182846,n)*  と同等の指数関数。 <br/> |
|**log(n)** <br/> | _n_ の自然対数。 <br/> |
|**abs(n)** <br/> | _n_ の絶対値。 <br/> |
|**ceil(n)** <br/> | _n_ の切り上げ。つまり、 _n_ が整数ではない場合、切り上げて次の整数にします。 _n_ が整数の場合、 _n_ を使用します。 <br/> |
|**floor(n)** <br/> | _n_ の切り捨て。つまり、 _n_ が整数ではない場合、切り捨てて次の整数にします。 _n_ が整数の場合、 _n_ を使用します。 <br/> |
|**round(n)** <br/> | _n_ の最近接偶数への丸め。「銀行家の丸め」または「偶数丸め」とも呼ばれます。 <br/> |
|**sin(n)** <br/> | _n_ ラジアンの正弦。 <br/> |
|**cos(n)** <br/> | _n_ ラジアンの余弦。 <br/> |
|**tan(n)** <br/> | _n_ ラジアンの正接。 <br/> |
|**asin(n)** <br/> |ラジアンで表した  _n_ の逆正弦。 <br/> |
|**acos(n)** <br/> |ラジアンで表した  _n_ の逆余弦。 <br/> |
|**atan(n)** <br/> |ラジアンで表した  _n_ の逆正接。 <br/> |
|**pow(x,y)** <br/> | _x_ を _y_ 乗した値。 <br/> > **メモ**>  _y_ の値は実数でなければなりません。          |
|**atan2(y,x)** <br/> |正の x 軸と指定されたデカルト座標 (x, y) との間の角度 (ラジアン) に対する、2 つの引数を持つ逆正接。  <br/> |
|**bucket(b,n1,n2,…)** <br/> |指定された値の分布範囲で式に不連続の値を提供するために使用できる演算子。  <br/> 式  _b_ には、管理プロパティや他の数式を指定できます。引数 _n1, n2, …_ は、数値のしきい値を表します。任意の数のバケットのしきい値を指定することができます。 <br/> > **メモ**> 引数  _n1, n2, n3, …_ は、 `n1 < n2 < n3 < ...` の順序で配置します ( `n1 >= 0` とします)。          入力式  _b_ に対する指定の値は、指定された最近接の数値しきい値に切り下げされます。指定された最も低いしきい値よりも小さい場合は、結果の値が 0 になります。 <br/> |
|**errtolast(x)** <br/> |数式例外を処理する方法を制御するために使用できる演算子。 _x_ には任意の数式を指定できます。この数式を計算すると結果セット内のアイテムに算術例外 (ゼロによる除算など) が生じる場合は、指定された並べ替えの方向には関係なく、これらのアイテムが並べ替えリストの最後に示されます。 <br/> |
   

### 数式による並べ替えのパフォーマンス特性

並べ替えの数式を使用すると、数式の計算が、結果セット内のすべての一致するアイテムに適用されることになります。つまり、クエリ パフォーマンスが受ける影響は、クエリに一致するアイテムの数によって異なります。
  
    
    
多くの演算子を含む長い数式はより短い数式も処理時間が必要です。
  
    
    

### 地理的な距離のための数式による並べ替えの使用

数式による並べ替えを使用して距離に基づくランク付けを適用できます。そのためには、各アイテムの緯度と経度を表す管理プロパティを含めることが必要です。
  
    
    
たとえば、次の標準の数式のいずれかを使用できます。
  
    
    

- マンハッタン距離
    
  
- ユークリッド距離 (例 2 を参照)
    
  
- 半正矢関数の公式
    
  

> **重要**
> タイプ **Decimal** または **Float** の管理プロパティを使用して、緯度と経度の値を表します。
  
    
    


### 例

次の例では、クエリ オブジェクト モデルを使用して並べ替えの数式を指定する方法を示します。
  
    
    
 **例 1。** **height** 管理プロパティが 20 に最も近いアイテムを結果セットの先頭に配置します。
  
    
    



```cs

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:abs(20-height)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

または、検索 REST API を使用して、以下の呼び出しにより、 **height** 管理プロパティが 20 に最も近いアイテムを結果リストの先頭に配置することもできます。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[formula:abs(20-height)]:ascending
```

 **例 2。** 管理プロパティ **latitude**、 **longitude**、および **height** に指定された位置情報に基づく、指定の位置 (ユーザーの位置など) からの真の 3-D ユークリッド距離による並べ替え。以下の数式は、基本位置が 50/100/200 (緯度/経度/高さ) のときの 3-D ユークリッド距離を提供します。
  
    
    
 `sqrt(pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2))`
  
    
    
距離に基づく並べ替え (距離を数式内の他のパラメーターと組み合わせない) を適用する場合、 `sqrt()` コンポーネントは削除できます。これにより、並べ替え順序は変更されずに、クエリのパフォーマンスが向上します。
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:pow(50-latitude,2)+pow(100-longitude,2)+pow(200-height,2)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

 **例 3。** サイズの値を丸めてバケットにします。値を切り捨てて以下のいずれかにします: 0、5、15、50、100。最大の値が最初になるように並べ替えます。
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[formula:bucket(size,5,15,50,100)]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## ランダムな順序での検索結果の並べ替え
<a name="SP15_Sort_search_results_in_random_order"> </a>

クエリ結果のランダムな並べ替えを適用することや、ランダムなコンポーネントを結果の並べ替えに追加することができます。
  
    
    
ランダムな並べ替えは、次の形式で指定します。 `[random:seed=<seed>:hashfield=<managed property>]`
  
    
    

> **メモ**
> 角かっこは、並べ替え仕様構文の一部です。 
  
    
    

表 2 は、ランダムな並べ替えの仕様へのパラメーターについて説明しています。
  
    
    

**表 2. ランダムな並べ替えの仕様のパラメーター**


|**パラメーター**|**説明**|**必須**|
|:-----|:-----|:-----|
| _Seed_ <br/> |ランダムな値を生成するためのシード。  <br/> シード値は、ランダムな数値を生成する関数への入力です。このランダムな数値は、最後の並べ替えで使用されます。 _seed_ オプションだけを使用すると、ランダムに並べ替えられたクエリ結果セットが生成されます。同じクエリの並べ替え順序は (同じシードを使用するとき) インデックスの更新後に変更されることがあります。 <br/> |はい  <br/> |
| _Hashfield_ <br/> |乱数の生成のためにハッシュ値として使用される管理プロパティ。このパラメーターを使用すると、インデックスの更新後に、同じクエリの並べ替えの順序が (同じシードを使用するときは) 変化しないようにすることができます。  <br/> 管理プロパティはタイプ  [Integer](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.ManagedDataType.Integer.aspx) で、 [Sortable()](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Administration.Sortable.aspx) でなければなりません。この管理プロパティには、ランダム値や一意の値 (アイテムの処理ステージで値が決まるシーケンス番号など) を入力できます。 <br/> |いいえ  <br/> |
   
等しいクエリに対して同じシードを指定すると、アイテムは同じ順序で示されます。これにより、検索結果を参照する際に同じランダム順序が維持されるようにすることができます。クエリとクエリの間で誤ってインデックスを更新したときに同じランダム順序が維持されるようにするには、 _hashfield_ パラメーターを使用します。
  
    
    

### 例

次の例では、クエリ オブジェクト モデルを使用して、ランダムな並べ替えを指定する方法を示します。
  
    
    
 **例 1。** 結果セット全体をランダムな順序で並べ替えます。
  
    
    



```

using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=5432]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```

または、次の呼び出しで検索 REST API を使用して、結果セット全体をランダムな順序で並べ替えることもできます。
  
    
    



```HTML

http://localhost/_api/search/query?querytext='home'&amp;sortlist='[random:seed=5432]:ascending
```

 **例 2。** 結果セット全体をランダムな順序で並べ替えます。インデックスの切り替えが生じた場合でも、同じシードによる同じクエリでは同じランダム順序が維持されるようにします。 **hashvalue** というカスタム管理プロパティは、検索スキーマ内で使用可能であること、およびすべてのインデックス アイテムにランダムまたはシーケンスの数値が入力されることが必要です。
  
    
    



```cs
using (var context = new ClientContext("http://localhost"))
{
    var query = new KeywordQuery(context)
    {
        QueryText = "home"
    };
    query.SortList.Add("[random:seed=6543:hashfield=hashvalue]", SortDirection.Ascending);

    var executor = new SearchExecutor(context);
    var results = executor.ExecuteQuery(query);

    context.ExecuteQuery();

    foreach (var result in results.Value[0].ResultRows)
    { 
        Console.WriteLine(result["Title"]);
    }
}
```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 の検索](search-in-sharepoint-2013.md)
    
  
-  [キーワード クエリ言語 (KQL) 構文のリファレンス](keyword-query-language-kql-syntax-reference.md)
    
  
-  [FAST クエリ言語 (FQL) 構文のリファレンス](fast-query-language-fql-syntax-reference.md)
    
  
-  [SharePoint 検索 REST API の概要](sharepoint-search-rest-api-overview.md)
    
  
-  [クロールされたプロパティと管理プロパティの概要 (SharePoint Server 2013)](http://technet.microsoft.com/ja-jp/library/jj219630%28office.15%29.aspx)
    
  

  
    
    
