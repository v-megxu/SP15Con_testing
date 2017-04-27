---
title: SharePoint 2013 のトリガー表現構文
ms.prod: SHAREPOINT
ms.assetid: d50536f6-d02e-4060-9286-634dfd06206c
---


# SharePoint 2013 のトリガー表現構文
SharePoint Server 2013の Web サービス呼び出しを構成するためのトリガー条件の作成に使用できるトリガー表現について説明します。 
## トリガー表現の構文で使用する要素
<a name="SP15triggerex_elements"> </a>

トリガー表現に使用できる要素には次のものがあります。
  
    
    

- 演算子
    
  
- マネージ プロパティ値へのアクセス
    
  
- リテラル
    
  
- 関数
    
  
- 定数
    
  

> **メモ**
> " **Null**" という文字列は **Null** 値のために予約されています。
  
    
    


## トリガー表現の構文の演算子
<a name="SP15triggerex_operators"> </a>

表 1 に、トリガー記述言語でサポートされる演算子を優先順位の高い順に示します。同じカテゴリにある演算子の優先順位は同じです。いくつかの演算子は、2 種類の構文をとります。
  
    
    

**表 1. トリガー記述言語でサポートされる演算子**


|**カテゴリ**|**表現**|**説明**|
|:-----|:-----|:-----|
|単項演算子  <br/> |-  <br/> !, NOT  <br/> |算術否定  <br/> 論理否定  <br/> |
|乗算演算子  <br/> |*  <br/> /  <br/> %, mod  <br/> |乗算  <br/> 除算  <br/> 剰余  <br/> |
|加算演算子  <br/> |+  <br/> -  <br/> &amp;  <br/> |加算  <br/> 減算  <br/> 文字列の結合  <br/> |
|関係演算子  <br/> |=, ==  <br/> !=, <>  <br/> <  <br/> >  <br/> <=  <br/> >=  <br/> |等しい  <br/> 等しくない  <br/> より少ない  <br/> より大きい  <br/> 以下  <br/> 以上  <br/> |
|論理 AND  <br/> |&amp;&amp;, AND  <br/> |論理的 AND  <br/> |
|論理 OR  <br/> |||, OR  <br/> |論理的 OR  <br/> |
   

## マネージ プロパティ値へのアクセス
<a name="SP15triggerex_managed"> </a>

クロールされたアイテム内の管理プロパティは、名前で参照されます。この場合、名前は引用符 ("") で囲まず、大文字と小文字が区別されます。
  
    
    

## トリガー表現のリテラル
<a name="SP15triggerex_literals"> </a>

 **String**、 **Int32**、 **Double**、および **Boolean**のデータ型はリテラルとして表現されます。
  
    
    

## トリガー表現の関数
<a name="SP15triggerex_functions"> </a>

数学関数 ( `Floor` など) から、特定のデータ型で使用する関数 ( `Lists` など) まで、さまざまな関数が幅広く用意されています。これらの関数は単独で使用することも、ネスト化することもできます。
  
    
    

-  `bool? ListContains<T>(IList<T> list, T obj)`
    
  
-  `int? Count<TElement>(IList<TElement> list)`
    
  
-  `TElement Item<TElement>(IList<TElement> list, int? index)`
    
  
-  `bool IsInsideRange(DateTime? date, long? fromTicks, long? toTicks)`
    
  
-  `DateTime Now()`
    
  
-  `DateTime? ToDate(string date, string format)`
    
  
-  `int? Day(DateTime? date)`
    
  
-  `int? DayOfWeek(DateTime? date)`
    
  
-  `int? DayOfYear(DateTime? date)`
    
  
-  `int? GetDatePart(DateTime? date, DatePartConstant datePartConstant)`
    
  
-  `int? Hour(DateTime? date)`
    
  
-  `int? Minute(DateTime? date)`
    
  
-  `int? Month(DateTime? date)`
    
  
-  `int? Quarter(DateTime? date)`
    
  
-  `int? Second(DateTime? date)`
    
  
-  `int? Year(DateTime? date)`
    
  
-  `long? GetDateDiff(DateTime? occursFirst, DateTime? occursLast, DatePartConstant datePartConstant)`
    
  
-  `string Extension(string arg)`
    
  
-  `string FileName(string arg)`
    
  
-  `string FileName(string arg, bool? excludeExtension)`
    
  
-  `bool IsNull(object value)`
    
  
-  `bool? IsDate(string input, string format)`
    
  
-  `object IfThenElse(bool? condition, object thenBranch, object elseBranch)`
    
  
-  `decimal? Ceiling(decimal? number)`
    
  
-  `decimal? Floor(decimal? number)`
    
  
-  `double? Ceiling(double? number)`
    
  
-  `double? Floor(double? number)`
    
  
-  `double? Sqrt(double? number)`
    
  
-  `bool? Contains(string arg, string contained)`
    
  
-  `bool? EndsWith(string arg, string suffix)`
    
  
-  `bool? IsMatch(string input, string pattern)`
    
  
-  `bool? IsMatch(string input, string pattern, int? start, RegexOptionConstant options)`
    
  
-  `bool? IsMatch(string input, string pattern, RegexOptionConstant options)`
    
  
-  `bool? IsNullOrEmpty(string input)`
    
  
-  `bool? StartsWith(string arg, string prefix)`
    
  
-  `int? IndexOf(string arg, string toFind)`
    
  
-  `int? IndexOfRegex(string input, string regex)`
    
  
-  `int? LastIndexOf(string arg, string toFind)`
    
  
-  `int? Length(string arg)`
    
  
-  `string Match(string input, string pattern)`
    
  
-  `string Match(string input, string pattern, int? start, int? length, RegexOptionConstant options)`
    
  
-  `string Match(string input, string pattern, int? start, RegexOptionConstant options)`
    
  
-  `string Match(string input, string pattern, RegexOptionConstant options)`
    
  
-  `string Substring(string arg, int? start)`
    
  
-  `string Substring(string arg, int? start, int? length)`
    
  
-  `string ToLower(string arg)`
    
  
-  `string Trim(string value)`
    
  

## トリガー表現の定数
<a name="SP15triggerex_constants"> </a>

特定の関数で使用できる 2 つの定数セットとして、 **DatePartConstant** と **RegexOptionConstant** があります。表 2 に、これらの定数の 2 つの例と、使用できる条件を示します。
  
    
    

**表 2. SharePoint 2013でのトリガー表現の定数と使用**


|**定数のグループ**|**使用例**|**使用法**|
|:-----|:-----|:-----|
|**DatePartConstant** <br/> |**Day**、 **Month**、 **Year**、 **Hour**、 **Minute**、 **Second**.  <br/> |**GetDatePart** 関数とともに <br/> |
|**RegexOptionConstant** <br/> |**IgnoreCase** <br/> |**IsMatch**、 **Match**、 **ReplaceRegex**、および **IndexOfRegex** 関数とともに <br/> |
   

## その他の技術情報
<a name="SP15triggerex_addresources"> </a>


-  [コンテンツ エンリッチメント Web サービス呼び出しによるカスタム コンテンツ処理](custom-content-processing-with-the-content-enrichment-web-service-callout.md)
    
  
-  [方法: SharePoint Server でコンテンツ エンリッチメント Web サービス呼び出しを使用する](how-to-use-the-content-enrichment-web-service-callout-for-sharepoint-server.md)
    
  

  
    
    

