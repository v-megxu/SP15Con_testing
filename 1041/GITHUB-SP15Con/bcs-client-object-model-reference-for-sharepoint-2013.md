---
title: SharePoint 2013 BCS クライアント オブジェクト モデル リファレンス
ms.prod: SHAREPOINT
ms.assetid: fe7d12a3-6ea9-47f9-b69e-f66da9e661dc
---



# SharePoint 2013 BCS クライアント オブジェクト モデル リファレンス

  
    
    
![クラス ライブラリおよびリファレンス](images/mod_icon_badge_reference.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013のクライアント オブジェクト モデルを使用して Business Connectivity Services (BCS)によって公開された外部データにアクセスするクライアント側スクリプトを作成するために利用できるオブジェクトについて説明します。
以下のオブジェクトは、SharePoint 2013 クライアント オブジェクト モデルを使用して、Business Connectivity Services (BCS)によって公開されている外部データにアクセスするクライアント側スクリプトを作成するために使用できます。クライアント オブジェクト モデルに公開されている CS オブジェクト モデル コンポーネントは Microsoft.SharePoint.Client.dll に配置されています。
  
    
    


## Entity オブジェクト
<a name="bkmk_Entity"> </a>

 **Entity** オブジェクトは、基本的にデータベースのテーブルに表されます。ここで示したメソッドとプロパティは、クライアントコード ライブラリを使用して操作できるオブジェクトです。これらの各呼び出しがそれぞれサーバー オブジェクト モデルの呼び出しに直接対応します。ただし、これらは、JavaScript を使用した Web ブラウザーなどの接続を切り離したクライアントによって呼び出すことができます。
  
    
    

**メソッド**


|**メソッド**|**メソッド シグネチャ**|**説明**|
|:-----|:-----|:-----|
|**Create** <br/> | `Identity Create(FieldValueDictionary fieldValues, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**FindSpecificDefault** <br/> | `EntityInstance FindSpecificDefault(Identity identity, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**FindspecificByBdcIDDefault** <br/> | `EntityInstance FindSpecific(Identity identity, string specificFinderName, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**FindSpecificByBdcID** <br/> | `EntityInstance FindSpecificByBdcIDDefault(string BdcIdentity, LobSystemInstance lobSystemInstanceName)` <br/> ||
|**GetCreatorView** <br/> | `EntityInstance FindSpecificByBdcID(string BdcIdentity, string specificFinderName,LobSystemInstance LobSystemInstanceName)` <br/> ||
|**GetDefaultSpecificFinderView** <br/> | `View GetCreatorView(string methodInstanceName)` <br/> ||
|**GetSpecificFinderView_Client** <br/> | `View GetDefaultSpecificFinderView()` <br/> ||
|**GetUpdaterView_Client** <br/> | `View GetSpecificFinderView_Client( string specificFinderName)` <br/> ||
|**GetIdentifiers** <br/> | `View GetUpdaterView_Client(string updaterName)` <br/> ||
|**GetIdentifiers()** <br/> |||
   

**プロパティ**


|**プロパティ**|**説明**|
|:-----|:-----|
| `long EstimatedInstanceCount { get; }` <br/> |この外部コンテンツ タイプの予想された外部アイテムの数を取得します。  <br/> |
| `string Name { get; }` <br/> |メタデータ オブジェクトの名前を取得します。  <br/> |
| `string Namespace { get; }` <br/> |所定のデータ クラスの名前空間を取得します。  <br/> |
| `int GetIdentifierCount()` <br/> ||
   

## EntityInstance メソッド
<a name="bkmk_EntityInstance"> </a>


**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**Delete** <br/> |(非推奨)  <br/> |外部アイテムを削除します。  <br/> |
|**FromXml** <br/> |(非推奨)  <br/> |指定した XML からの値をこの辞書に設定します。  <br/> **メソッド シグネチャ**          `FromXml(string xml)` <br/> |
|**GetIdentity** <br/> |Identity  <br/> |この外部アイテムの ID を取得します  <br/> |
|**Delete** <br/> |(非推奨)  <br/> |外部アイテムを削除します。  <br/> |
|**ToXml** <br/> |文字列  <br/> |XML 形式の値を取得します。  <br/> |
|**Update** <br/> |(非推奨)  <br/> |外部アイテムに加えた変更を送信します。  <br/> |
   

  
    
    

**プロパティ**


|**プロパティ**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
| `this[string fieldDotNotation] { get; set; }` <br/> |オブジェクト  <br/> |ドット表記によって参照されたフィールド値を取得または設定します。  <br/> |
| `RelatedSpecificFinderName { get; }` <br/> |文字列  <br/> ||
   

## EntityView メソッド
<a name="bkmk_entityview"> </a>

 **Entity** データのカスタマイズされたビューを指定します。
  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**GetDefaultValues_Client()** <br/> |**FieldValueDictionary** <br/> |このビューの既定値を含むフィールド値の辞書を取得します。  <br/> |
|**GetXmlSchema()** <br/> |**string** <br/> |ビューの XML スキーマを取得します。  <br/> |
|**GetType(string fieldDotNotation)** <br/> |**string** <br/> |指定したフィールドの型を取得します。  <br/> |
|**GetType(string fieldDotNotation)** <br/> |**TypeDescriptor** <br/> |所定のドット表記に対応した **TypeDescriptor** オブジェクトを取得します。 <br/> |
   

**プロパティ**


|**プロパティ**||**説明**|
|:-----|:-----|:-----|
| `Fields { get; }` <br/> |**FieldCollection** <br/> |ビュー内のフィールドのコレクションを取得します。  <br/> |
| `Name { get; }` <br/> |**string** <br/> |この **View** オブジェクトの名前を取得します。 <br/> |
| `RelatedSpecificFinderName { get; }` <br/> |**string** <br/> |このビューと連携する特定のファインダー **MethodInstance** の名前を取得します。 <br/> |
   

## LobSystem メソッド
<a name="bkmk_LobSystem"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**GetLobSystemInstances()** <br/> |**void** <br/> |LOB システム インスタンスのリストを取得します。  <br/> |
|**Name** <br/> |**void** <br/> |**LobSystem** の名前を取得します。 <br/> |
   

**プロパティ**


|**プロパティ**|**説明**|
|:-----|:-----|
|なし。  <br/> ||
   

## LobSystemInstance メソッド
<a name="bkmk_LobSystemInstance"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|なし。  <br/> |**void** <br/> ||
   

**プロパティ**


|**プロパティ**|**説明**|
|:-----|:-----|
|なし。  <br/> ||
   

## Identifier メソッド
<a name="bkmk_Identifier"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**ContainsLocalizedDisplayName** <br/> |**bool** <br/> |メタデータ オブジェクトにローカライズされた表示名を含めるかどうかを指定します。  <br/> |
|**GetDefaultDisplayName** <br/> |**string** <br/> |既定の表示名を返します。  <br/> |
|**GetLocalizedDisplayName** <br/> |**string** <br/> |ローカライズされた表示名を返します。  <br/> |
   

**プロパティ**


|**プロパティ**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
| `IdentifierType {get;}` <br/> |**string** <br/> |識別子の型を返します。  <br/> |
| `Name {get;}` <br/> |**string** <br/> |識別子の名前を返します。  <br/> |
   

## IdentifierCollection メソッド
<a name="bkmk_IdentifierCollection"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel.Collections** <br/> |**SP.BusinessData.Collections** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|なし。  <br/> |**void** <br/> ||
   

**プロパティ**


|**プロパティ**|**説明**|
|:-----|:-----|
|なし。  <br/> ||
   

## Identity メソッド
<a name="bkmk_Identity"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**コンストラクター**


|**コンストラクター**|**説明**|
|:-----|:-----|
| `public Identity (Object[] identifierValues)` <br/> |識別子の値の配列を使用してクラスの新しいインスタンスを構築します。  <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**Serialize** <br/> |**string** <br/> |ID の文字列表現を取得します。  <br/> |
   

**プロパティ**


|**プロパティ**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
| `IdentifierCount { get; }` <br/> |**int** <br/> |識別子の数を返します。  <br/> |
| `IsTemporary { get; }` <br/> |**bool** <br/> |ID が一時的なものかどうか調べます。  <br/> |
| `this[int identifierIndex] { get; }` <br/> |**Object** <br/> |所定のインデックスの要素を返します。CSOM は int ベースのインデックス作成をサポートしません。同じ用途で文字列ベースのアクセサーが実装されています。  <br/> |
| `TemporaryId { get; }` <br/> |**Guid** <br/> |ID の一時的な部分を返します。  <br/> |
   

## FieldValueDictionary メソッド
<a name="bkmk_FieldValueDictionary"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**FromXml** <br/> |**void** <br/> |指定した XML からの値をこの辞書に設定します。  <br/> |
|**GetCollectionSize** <br/> |int  <br/> |ドット表記によって参照されたコレクションのサイズを返します。  <br/> |
|**ToXml** <br/> |文字列  <br/> |XML 形式の値を取得します。  <br/> |
   

**プロパティ**


|**プロパティ**|**説明**|
|:-----|:-----|
| `Object this[string fieldDotNotation] { get; set; }` <br/> |ドット表記によって参照されたフィールドの値を取得または設定します。  <br/> |
   

## EntityFieldCollection メソッド
<a name="bkmk_EntityFieldCollection"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|なし。  <br/> |**void** <br/> ||
   

**プロパティ**


|**プロパティ**|**説明**|
|:-----|:-----|
|なし。  <br/> ||
   

## EntityField メソッド
<a name="bkmk_Entityfield"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.Runtime** <br/> |**SP.BusinessData.Runtime** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|なし。  <br/> |(非推奨)  <br/> ||
   

**プロパティ**


|**プロパティ**|**戻り値の型**|**読み取り専用**|**説明**|
|:-----|:-----|:-----|:-----|
|**ContainsLocalizedDisplayName** <br/> |**Boolean** <br/> |○  <br/> |フィールドにローカライズされた表示名を含めるかどうかを指定します。  <br/> |
|**DefaultDisplayName** <br/> |**string** <br/> |○  <br/> |フィールドの既定の表示名を取得します。  <br/> |
|**GetLocalizedDisplayName** <br/> |**string** <br/> ||フィールドのローカライズされた表示名を取得します。  <br/> |
|**Name** <br/> |**string** <br/> |○  <br/> |フィールドの名前を取得します。  <br/> |
   

## TypeDescriptor クラス
<a name="bkmk_TypeDescriptor"> </a>


  
    
    

**名前空間**


|**マネージ型**|**JavaScript**|
|:-----|:-----|
|**Microsoft.BusinessData.MetadataModel** <br/> |**SP.BusinessData** <br/> |
   

**メソッド**


|**メソッド**|**戻り値の型**|**読み取り専用**|**説明**|
|:-----|:-----|:-----|:-----|
|**ContainsLocalizedDisplayName()** <br/> |**Boolean** <br/> |○  <br/> |型記述子にローカライズされた表示名を含めるかどうかを指定します。  <br/> |
|**GetLocalizedDisplayName()** <br/> |**string** <br/> |○  <br/> |ローカライズされた表示名を返します。  <br/> |
|**GetDefaultDisplayName()** <br/> |**string** <br/> ||既定の表示名を返します。  <br/> |
   

**プロパティ**


|**プロパティ**|**戻り値の型**|**説明**|
|:-----|:-----|:-----|
|**Name** <br/> |文字列  <br/> |フィールドの名前を取得します。  <br/> |
|**TypeName** <br/> |文字列  <br/> |この型記述子によって表されたデータ型の名前を取得します。  <br/> |
|**IsReadOnly** <br/> |ブール型  <br/> |この型記述子で読み取り専用のデータ構造を表すかどうかを指定します。  <br/> |
|**ContainsReadOnly** <br/> |ブール型  <br/> |この型記述子または子の 1 つで読み取り専用のデータ構造を表すかどうかを指定します。  <br/> |
|**IsCollection** <br/> |ブール型  <br/> |記述された型でコレクション データ構造を表すかどうかを指定します。  <br/> |
   

## インターフェイス
<a name="bkmk_Interfaces"> </a>

名前空間は **Microsoft.BusinessData.MetadataModel** です。
  
    
    


|**インターフェイス**|**説明**|
|:-----|:-----|
|**IMetadataCatalog** <br/> |BDC オブジェクト モデルへのエントリ ポイント。サーバー上の **DatabaseBasedMetadataCatalog** を使用します。 <br/> |
|**ILobSystem** <br/> |外部システムに関する詳細情報を含みます。  <br/> |
|**IEntity** <br/> |BDC Metadata Store 内の外部 コンテンツ タイプ。  <br/> |
|**IMethod** <br/> |外部 コンテンツ タイプに実行できる操作。  <br/> |
|**IEntityInstance** <br/> |エンティティ インスタンス (外部アイテムとも呼ばれる) は、BDC 内の外部システムから返される 1 つのアイテムです。  <br/> The **IEntityInstance** インターフェイスは、基盤となるデータ ソースを抽象化し、クライアントがアプリケーション固有のコーディング方法を識別しなくても済むようにします。これにより、1 つのシンプルな方法ですべてのデータにアクセスすることができます。 **IEntityInstance** インターフェイスを使用することで、Web サービスによって返された複雑な .NET Framework 構造を操作するのとまったく同じように、データベースのデータの行を操作することができます。 <br/> BDC 内のエンティティ インスタンスには、特殊なセマンティクスが付けられています。たとえば、行のどのフィールドがエンティティ インスタンスの識別子を表しているかを識別することができ、エンティティ インスタンス上に **GetAssociated**、 **GetIdentifierValues**、および **Execute**の各メソッドを呼び出すことができます。  <br/> |
|**IEntityInstanceEnumerator** <br/> |列挙子を使用して、外部アイテム コレクション内のデータを読むことはできますが、それを使用して基盤となるコレクションに変更を加えることはできません。 **IEntityInstanceEnumerator** はストリーミングをサポートしています。したがって、バックエンド アプリケーションが膨大な量のデータを返す場合は、非常に有効です。 <br/> |
   

## クライアント オブジェクト モデルに関する FAQ
<a name="bkmk_ClientObjectModelFAQ"> </a>


- **外部リストをクエリする場合、<Method> タグを CAML クエリに含める必要はありますか?**
    
    必要ありません。 
    
  
- **CAML クエリでは、外部リストのすべてのフィールドを指定する必要がありますか?**
    
    BDC モデルの ViewXML タグを使用すると、開発者は必須のフィールドのみを指定でき、リスト用の CSOM API はこれらのフィールドのみを返します。
    
  

## その他の技術情報
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 Business Connectivity Services プログラマー リファレンス](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 .NET クライアント API リファレンス](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 のクライアント コード ライブラリを使用して外部データにアクセスする](how-to-use-the-client-code-library-to-access-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
