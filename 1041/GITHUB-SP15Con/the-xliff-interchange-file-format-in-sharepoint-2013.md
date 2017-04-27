---
title: SharePoint 2013 での XLIFF 交換ファイル形式
ms.prod: SHAREPOINT
ms.assetid: 660c0f07-7030-4576-957e-b9f2cd0fa895
---


# SharePoint 2013 での XLIFF 交換ファイル形式
スキーマ リファレンス情報や XML の例など、XLIFF 交換ファイル形式の SharePoint 2013 実装に関する情報を取得します。
## SharePoint 2013 での XLIFF 交換ファイル形式の実装

SharePoint 2013 では、XML ローカリゼーション交換ファイル形式 (XLIFF) アプリケーションによってバリエーション機能および翻訳サービス機能をサポートしています。SharePoint Server は XLIFF を使用することでファイルおよびそのコンテンツに関する情報を SharePoint Server から翻訳者へ、翻訳者が容易に理解できる形式で転送します。
  
    
    
SharePoint Server の HTML ページが XLIFF 形式に抽出されるとき、SharePoint 2013 は OASIS 発行の  [HTML の XLIFF 1.2 プレゼンテーションガイド](http://docs.oasis-open.org/xliff/v1.2/xliff-profile-html/xliff-profile-html-1.2-cd02.mdl) に準拠します。万が一変更されていない SharePoint Server CDATA コンテンツが転送されても XLIFE に表示される翻訳可能な要素とコード要素との組み合わせを削除できるように、SharePoint 2013 は、SharePoint 2013 に確実に統合される XLIFF 完全準拠の XLIFF ドキュメントを生成する機能と一緒に配信されます。 `sharepointservernv` から XLIFE 形式で XML ファイルをエクスポートした場合、翻訳者が受信するデータはクリーンで、すぐに翻訳できる状態です。
  
    
    
この記事では、OASIS 発行の XLIFE オープン スタンダード ドキュメントのバージョン 1.2 に定義されている特定の XLIFE 要素と属性の、具体的な SharePoint Server 実装について記載しています。具体的な XLIFF 要素および属性については、「 [XLIFF 1.2 仕様](http://docs.oasis-open.org/xliff/xliff-core/xliff-core.mdl)」を参照してください。
  
    
    

  
    
    

**表 1 SharePoint 2013 で注目すべき XLIFF 要素と属性**


|**要素**|**属性**|**メモ**|
|:-----|:-----|:-----|
|Xml  <br/> | `version` <br/>  `encoding` <br/> |XML バージョンとエンコーディングを宣言します。  <br/> |
|Xliff  <br/> | `version` <br/>  `xmlns` <br/> | `version` 属性とスキーマ検証メカニズムを含みます。 <br/> |
|File  <br/> | `original` <br/>  `source-language` <br/>  `target-language` <br/>  `datatype` <br/>  `tool-id` <br/> |元のソース ファイルに対応します。この中で、 は、機械翻訳ツールと人による翻訳ツールの両方で使用されるソース言語とターゲット言語 ( `source-language` と `target-language`) を含むバリエーション機能からの 1 つのページ GUID です。  <br/>  `original` 属性には、元のソース コンテンツを識別する場合に使用する GUID が含まれます。インポートを確実に成功させるために、この値は変えないでください。 <br/>  `datatype` 属性も、すべての SharePoint ページに HTML 形式で **File** 要素に格納されます。 <br/>  `tool-id` 属性は、XLIFE ファイルを生成したツールを識別する GUID です。 <br/> |
|Header  <br/> |||
|Tool  <br/> | `tool-id` <br/>  `tool-name` <br/> |XLIFF ファイルを生成したツールを識別します。  <br/> |
|Note  <br/> ||XLIFF ファイルを処理するローカライザー、開発者、またはその他の関係者にとって有用と考えられる情報を含みます。  <br/>  `note` 要素値は によって生成されます。 `note` 属性には、コンテキストを提供するコンテンツの場所およびタイプを識別する GUID が含まれます。 <br/> |
|Body  <br/> |||
|Trans-unit  <br/> | `id` <br/>  `datatype` <br/> | `id` 属性には、インポートの場所を識別する GUID が含まれます。 <br/>  `datatype` 属性では、 **trans-unit** 要素に含まれるデータの型を定義します。使用可能な `datatype` 属性値の一覧については、XLIFF オープン スタンダード ドキュメントを参照してください。 <br/> |
|Source  <br/> ||多くの場合、HTML コンテンツには維持することが必要なマークアップが含まれます。このため、SharePoint 2013 は、 [HTML の XLIFF 1.2 プレゼンテーション ガイド](http://docs.oasis-open.org/xliff/v1.2/xliff-profile-html/xliff-profile-html-1.2-cd02.mdl)に定義されているタグを使用して HTML コンテンツ内のマークアップをラップします。  <br/> |
|Target  <br/> |ph (オプション)  <br/> bpt (オプション)  <br/> ept (オプション)  <br/> sub (オプション)  <br/> |多くの場合、HTML コンテンツには維持することが必要なマークアップが含まれます。このため、SharePoint 2013 は、 [HTML の XLIFF 1.2 プレゼンテーション ガイド](http://docs.oasis-open.org/xliff/v1.2/xliff-profile-html/xliff-profile-html-1.2-cd02.mdl)に定義されているタグを使用して HTML コンテンツ内のマークアップをラップします。  <br/> |
|Bin-unit  <br/> ||SharePoint 2013 に格納されているファイルは、XLIFE を使用したローカライズにおいて、 **bin-unit** 要素を介して送信できます。このファイルは、 [SharePoint 2013: XLIFF ファイルでの bin-unit 要素の抽出および挿入](http://code.msdn.microsoft.com/SharePoint-2013-Extract-fe686878)のコード サンプルを使用することにより、元のファイル形式に戻すことができます。  <br/> |
|Bin-source  <br/> |||
|Bin-target  <br/> |||
|Internalfile  <br/> |form  <br/> ||
   

## 例: SharePoint 2013 からの XLIFE マークアップ

XLIFF 交換ファイル形式の XML ドキュメントに関する以下の例では、標準内に定義されている要素および属性の一部を SharePoint 2013 で実装する方法について示します。 
  
    
    

```XML

<?xml version="1.0" encoding="utf-8"?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2">
  <file original="ce2b8e40-b802-4196-b6cb-93e63eb4bb42" source-language="en-US" target-language="fr-CA" datatype="html">
    <header>
      <note>type=ListItem</note>
      <note>translatorType=Vendor</note>
      <note>packageGroupId=fb98837d-c4e0-48f1-9e59-874b61802cda</note>
      <note>webId=1c013046-821b-40d7-a1e0-689dd920f37d</note>
      <note>listId=58b11f3f-6549-47c5-bf13-a2dc4dfa03b3</note>
      <note>url=Pages/Type-or-edit-text-in-a-different-language.aspx</note>
      <note>sourceVersion=2</note>
    </header>
<body>
      <trans-unit id="fa564e0f-0c70-4ab9-b863-0177e6ddd247" datatype="plaintext">
        <source>Type or edit text in a different language</source>
        <note>fieldTitle=Title</note>
      </trans-unit>
      <trans-unit id="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" datatype="html">
        <source>
          <bpt id="1">&amp;lt;strong&amp;gt;</bpt>When you want to type documents in different languages, you can change your keyboard layout language--the language-specific characters typed when keyboard keys are pressed--so that you can type the special characters for each language. 
  <ept id="1">&amp;lt;/strong&amp;gt;</ept>
        </source>
        <note>fieldTitle=Page Content</note>
      </trans-unit>
    </body>
  </file>

```


  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 機能の追加](add-sharepoint-2013-capabilities.md)
    
  
- コード例:  [SharePoint 2013: SharePoint 2013: XLIFF ファイルでの bin-unit 要素の抽出および挿入](http://code.msdn.microsoft.com/SharePoint-2013-Extract-fe686878)
    
  
-  [SharePoint 2013 の機械翻訳サービス](machine-translation-services-in-sharepoint-2013.md)
    
  

  
    
    

