---
title: 方法 SharePoint 2013 で関連付けられた外部コンテンツ タイプをクロールする
ms.prod: SHAREPOINT
ms.assetid: 187ec42e-f749-4e22-abef-1df604143063
---


# 方法: SharePoint 2013 で関連付けられた外部コンテンツ タイプをクロールする
関連付けをクロールするために Business Data Connectivity (BDC) Service メタデータ モデル内の検索固有プロパティを使用する方法と、有効にできるさまざまなユーザー エクスペリエンスについて説明します。
## 関連付けられた外部コンテンツ タイプのクロール
<a name="HowToCrawlAssociations_CrawlingAssociatedExternalTypes"> </a>

Microsoft Business Connectivity Services (BCS) では 2 つの関連する外部コンテンツ タイプをリンクして、関連する外部コンテンツを取得できます。たとえば、外部キーに基づく 2 つの SQL Server データベース テーブルベースの外部コンテンツ タイプから外部コンテンツを取得できます。2 つの関連する外部コンテンツ タイプをリンクするという概念は、 *関連付け*  と呼ばれます。関連付けの詳細については、「 [外部コンテンツ タイプの間に関連付けを追加する](http://msdn.microsoft.com/library/791e95ab-9b3c-413b-be12-bd0e59962c93%28Office.15%29.aspx)」を参照してください。 
  
    
    
検索 コネクタ フレームワークでは、関連付けのソース外部コンテンツ タイプは親の外部コンテンツ タイプと呼ばれます。検索 クローラーは、親に関連付けられている外部コンテンツ タイプを添付ファイルまたは子として 2 つの方法でクロールできます。これらの外部コンテンツ タイプの関連付けは、以下に影響します。
  
    
    

- ユーザー エクスペリエンス
    
  
- 増分クロール
    
  
- クロールの削除処理
    
  

### 外部コンテンツ タイプの関連付けによるユーザー エクスペリエンスへの影響

子の外部コンテンツ タイプには独自の検索結果 URL とプロファイル ページ (プロファイル ページが作成されている場合) があります。検索結果 URL は、ユーザーが子の外部コンテンツ タイプ データ内で用語を検索する場合に表示される URL です。 
  
    
    
添付ファイルの外部コンテンツ タイプには、独自の検索結果 URL はありません。そのため、ユーザーが添付ファイルの外部アイテム内で用語を検索すると、親の外部コンテンツ タイプの URL が表示されます。この URL を、親のプロファイル ページ URL に設定できます。親の外部コンテンツ タイプのプロファイル ページには、関連付けのナビゲーターによって表示される添付ファイルの外部コンテンツ タイプのフィールドがすべて表示されます。
  
    
    

### 外部コンテンツ タイプの関連付けによる増分クロールへの影響

子の外部アイテムのタイムスタンプが変更されると、タイムスタンプベースの増分クロールのために、子の外部アイテムが再クロールされて更新されます。 
  
    
    
添付ファイルの外部コンテンツ タイプについては、親の外部アイテムのタイムスタンプが添付ファイルの外部アイテムのタイムスタンプとして解釈されます。つまり、親の外部アイテムのタイムスタンプが変更された場合に限り、添付ファイルの外部アイテムの変更が増分クロールによってピックアップされます。
  
    
    

### 外部コンテンツ タイプの関連付けによるクロール削除処理への影響

クロール削除を処理するとき、インデックスから親の外部コンテンツ タイプが削除される場合、検索 クローラーは関連付けられた添付ファイルの外部コンテンツ タイプと子の外部コンテンツ タイプをインデックスから削除します。
  
    
    

## 関連付けられた外部コンテンツ タイプの添付ファイルのクロール
<a name="HowToCrawlAssociations_CrawlingAttachments"> </a>

添付ファイルとしてクロールされるように関連付けをマークするには、以下のように、 **AttachmentAccessor** プロパティを **Association** メソッド インスタンスに追加します。
  
    
    

```XML

<Association Name="AttachmentsNavigate Association" Type="AssociationNavigator" ...>
    <Properties>
        <Property Name="ForeignFieldMappings" Type="System.String">....... </Property>
        <Property Name="AttachmentAccessor" Type="System.String">x</Property>
    </Properties>
    <SourceEntity Namespace="ParentExternalContentType" Name="Parent" />
    <DestinationEntity Namespace="AttachmentExternalContentType" Name="Attachment External Content Type" />
</Association>
```


> **メモ**
> **AttachmentAccessor** プロパティに任意の値を指定できます。検索 では、この値は検証されません。
  
    
    


## 子の外部コンテンツ タイプとして関連付けられた外部コンテンツ タイプのクロール
<a name="HowToCrawlAssociations_CrawlingChildExternalTypes"> </a>

子の外部コンテンツ タイプとしてクロールされるように関連付けをマークするには、次のように、 **DirectoryLink** プロパティを **Association** メソッド インスタンスに追加します。
  
    
    

```XML

<Association Name="ChildrenNavigator Association" Type="AssociationNavigator" ...>
    <Properties>
        <Property Name="DirectoryLink" Type="System.String">x</Property>
    </Properties>
    <SourceEntity Namespace="ParentExternalContentType" Name="Parent" />
    <DestinationEntity Namespace="ChildExternalContentType" Name="Child External Content Type" />
</Association>
```


> **メモ**
> **DirectoryLink** プロパティには任意の値を指定できます。検索 では、この値は検証されません。
  
    
    


## その他の技術情報
<a name="SP15crawlects_addlresources"> </a>


-  [SharePoint 2013 の検索コネクタ フレームワーク](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [外部コンテンツ タイプの間に関連付けを追加する](http://msdn.microsoft.com/library/791e95ab-9b3c-413b-be12-bd0e59962c93%28Office.15%29.aspx)
    
  
-  [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx)
    
  
-  [手順 4 (省略可能) : 関連付けを定義する](http://msdn.microsoft.com/library/6bc55f46-459a-4986-8744-8c6c5f45097b%28Office.15%29.aspx)
    
  

