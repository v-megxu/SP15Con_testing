---
title: SharePoint 2013 BDC モデル スキーマ リファレンス
ms.prod: SHAREPOINT
ms.assetid: 979a5ffc-f033-4e72-b2d1-11d8cb1b294a
---



# SharePoint 2013 BDC モデル スキーマ リファレンス
SharePoint 2013の外部コンテンツ タイプの作成に使用できる BDC モデル スキーマ (BDCMetadata.xsd) の参照情報を含みます。 
 [BDCMetadata.xsd](http://schemas.microsoft.com/windows/2007/BusinessDataCatalog)
  
    
    


## AccessControlEntry 要素
<a name="bkmk_AccessControlEntry"> </a>

親要素のアクセス権を指定するアクセス制御エントリ (ACE) を含みます。
  
    
    
Business Connectivity Services とセキュリティの詳細については、「  [Business Connectivity Services のセキュリティの概要](http://technet.microsoft.com/ja-jp/library/ee661734%28office.14%29.aspx)」を参照してください。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML

<AccessControlEntry Principal = "String"> </AccessControlEntry>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Principal  <br/> |必ず指定します。  <br/> この ACE を持つセキュリティ プリンシパルの名前。  <br/> 属性の型: **String** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [AccessControlEntry の Right 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a2e4bd6c-2306-b657-7290-cc9c9b262911%28Office.15%29.aspx) <br/> |セキュリティ プリンシパルで利用できる権限を指定する **Right** 要素。 <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |この ACE を含むアクセス制御リスト (ACL)。  <br/> |
   

## AccessControlList 要素
<a name="bkmk_AccessControlList"> </a>

親要素のアクセス制御リスト (ACL) を指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<AccessControlList></AccessControlList>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [AccessControlList の AccessControlEntry 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/85e24489-0a6b-dfda-fb03-474fe7b0d947%28Office.15%29.aspx) <br/> |アクセス制御エントリ (ACE)。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Model 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> |ビジネス アプリケーションで外部コンテンツ タイプを含んでいるモデル。  <br/> |
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |モデルに含まれている LobSystem。  <br/> |
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |外部コンテンツ タイプ。  <br/> |
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのメソッド。  <br/> |
| [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> |関連付け。  <br/> |
| [MethodInstances の MethodInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのメソッド インスタンス。  <br/> |
   

## Action 要素
<a name="bkmk_Action"> </a>

外部コンテンツ タイプによってサポートされるアクションを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **Schema:**BDCMetadata
  
    
    
外部システムにリンクをすることによって SharePoint 2013、Office 2013、および外部システムのユーザー インターフェイス間のギャップを埋めるアクション。 
  
    
    
既定で、Business Data Connectivity (BDC) Service は、 **View Item**、 **Edit Item**、および **Delete Item** などのアクションを、BDC モデルでこれらの操作をモデル化した後で、実行します。これらの既定のアクションに加えて、外部コンテンツ タイプに追加するために、その他の機能を持つアクションを作成することができます。たとえば、Customer 外部コンテンツ タイプから、顧客に電子メール メッセージを送信する、あるいはブラウザーで顧客のホーム ページを開くなどのシンプルなアクションを実行することができます。
  
    
    
アクションは、外部コンテンツ タイプを伴います。つまり、外部コンテンツ タイプのためのアクションを定義すると、外部リスト、ビジネス データ Web パーツ、あるいは外部データ列であるかにかかわらず、外部コンテンツ タイプを表示した場所に必ずそのアクションが表示されます。 
  
    
    



```XML
<Action Position = "Integer" IsOpenedInNewWindow = "Boolean" Url = "String" ImageUrl = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Action>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Position** <br/> |必ず指定します。  <br/> この外部コンテンツ タイプのその他のアクションの中で、このアクションの推奨の位置。  <br/> 属性の型: **Integer** <br/> |
|**IsOpenedInNewWindow** <br/> |省略可能。  <br/> アクションを実行した結果が、新しいユーザー インターフェイス ウィンドウで表示されるかどうかを指定します。  <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**Url** <br/> |必ず指定します。  <br/> アクションが呼び出されたときの移動先の URL。URL 文字列は .NET Framework 形式の文字列です。各書式指定子 ({0} など) は **Action** パラメーターに対応します。 <br/> 属性の型: **String** <br/> |
|**ImageUrl** <br/> |省略可能。  <br/> アクションのアイコン イメージの絶対または相対パス。アイコン イメージは 16x16 ピクセルにします。  <br/> 属性の型: **String** <br/> |
|**Name** <br/> |必ず指定します。  <br/> このアクションの名前です。  <br/> 属性の型: **String** <br/> |
|**DefaultDisplayName** <br/> |省略可能。  <br/> このアクションの既定の表示名。  <br/> 属性の型: **String** <br/> |
|**IsCached** <br/> |省略可能。  <br/> このアクションが頻繁に使用されるかどうかを指定します。このアクションは、BDC Client Runtime がこのアクションをキャッシュするために使用します。  <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |アクションのローカライズされた名前。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |アクションのプロパティ。  <br/> |
| [Action の ActionParameters 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/e14df901-621c-1851-db78-e99fd3cf31ae%28Office.15%29.aspx) <br/> |アクションのパラメーター。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entity の Actions 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/c5a6c08d-a3df-61db-3ce3-1e6837bbf221%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのアクションのリスト。  <br/> |
   

## ActionParameter 要素
<a name="bkmk_ActionParameter"> </a>

URL ベース アクションのパラメーターを指定します。 **EntityInstance** 固有のデータを使用してアクションの URL をパラメーター化する方法を定義します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    
URL ベース アクションの URL 属性は、 **ActionParameter** 要素を使用してパラメーターを取得できます。
  
    
    

> **重要**
> **ActionParameters** は、識別子の値、または **Entity** の **SpecificFinder** 内の **TypeDescriptors** に対応する値を表すことができます。 **IdOrdinal** プロパティが存在する場合、 **ActionParameter** は識別子値を表します。プロパティの値は、この **ActionParameter** が表す値を持つ識別子のインデックスを指定します。 **IdOrdinal** プロパティが指定されていない場合、 **ActionParameter** は **TypeDescriptor** を表します。このとき、 **Name** 属性は、どの型記述子を表すかを指定します。 **Name** 属性は、 **Dotted Path** として指定されます。
  
    
    

 **ActionParameter** 要素では、以下のプロパティを使用できます。
  
    
    

> **重要**
> プロパティでは大文字と小文字が区別されます。 
  
    
    


**プロパティ**


|**プロパティ**|**型**|**説明**|**必ず指定します。**|**既定値**|**制限/使用する値**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**IdOrdinal** <br/> |**System.Int32** <br/> |**ActionParameter** がフィールドではなく識別子を表す場合に指定します。 <br/> |省略可能。  <br/> |||
   



```XML
<ActionParameter Index = "Integer" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </ActionParameter>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Index** <br/> |必ず指定します。  <br/> URL 内の **ActionParameters** の中で、この **ActionParameter** の位置を示す順序属性。 <br/> 属性の型: **Integer** <br/> |
|**Name** <br/> |必ず指定します。  <br/> **ActionParameter** の名前。 <br/> 属性の型: **String** <br/> |
|**DefaultDisplayName** <br/> |省略可能。  <br/> **ActionParameter** の既定の表示名。 <br/> 属性の型: **String** <br/> |
|**IsCached** <br/> |省略可能。  <br/> この **ActionParameter** が頻繁に使用されるかどうかを指定します。この属性は、BDC Client Runtime がこの **Action** をキャッシュするために使用します。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**ActionParameter** ローカライズされた表示名。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**ActionParameter** のプロパティ。 <br/> |
   
 **親要素**
  
    
    


|****Element****|**説明**|
|:-----|:-----|
| [Action の ActionParameters 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/e14df901-621c-1851-db78-e99fd3cf31ae%28Office.15%29.aspx) <br/> |**ActionParameters** を含む **ActionParameter** 要素。 <br/> |
   

## ActionParameters 要素
<a name="bkmk_ActionParameters"> </a>

アクションの **ActionParameters** のリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<ActionParameters></ActionParameters>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし。
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [ActionParameters の ActionParameter 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/1f5fa96a-1bff-f007-984d-a644cbbb2648%28Office.15%29.aspx) <br/> |**ActionParameter**。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Actions の Action 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> |これらの **Action** が所属する **ActionParameters**。  <br/> |
   

## Actions 要素
<a name="bkmk_Actions"> </a>

外部コンテンツ タイプのアクションのリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Actions></Actions>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Actions の Action 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのアクション。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |これらのアクションが所属する外部コンテンツ タイプ。  <br/> |
   

## Association 要素
<a name="bkmk_Association"> </a>

関連付け要素は、システム内の関連する外部コンテンツ タイプにリンクします。たとえば、顧客が注文を行う状況であれば、顧客は AdventureWorks システムの販売注文に関連付けられます。関連付けは接続元および接続先の外部コンテンツ タイプへのポインターと、クライアントが接続先の外部コンテンツタイプを接続元の外部コンテンツ タイプから取得できるようにするビジネス ロジック ( **MethodInstance** オブジェクト) へのポインターを保持します。 **Association** のトラバーサルは、外部システム上のメソッドの呼び出しです。
  
    
    

  
    
    
 **名前空間:** http://schemas.microsoft.com/windows/2007/BusinessDataCatalog
  
    
    
 **スキーマ:** BDCMetadata
  
    
    

> **重要**
> プロパティでは大文字と小文字が区別されます。 
  
    
    


**プロパティ**


|**プロパティ**|**型**|**説明**|**必須**|**既定値**|**制限/使用する値**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**HideOnProfilePage** <br/> |**System.Boolean** <br/> |関連する外部コンテンツ タイプが、マスター外部コンテンツ タイプのプロファイル ページに追加されるかどうかを指定します。  <br/> |省略可能。  <br/> |||
   



```XML
<Association Type = "String" Default = "Boolean" ReturnParameterName = "String" ReturnTypeDescriptorName = "String" ReturnTypeDescriptorLevel = "Integer" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Association>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Type** <br/> |必ず指定します。  <br/> 関連付けの型を指定する **MethodInstanceType**。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|AssociationNavigator  <br/> |**MethodInstance** は **AssociationNavigator** です。 <br/> |
|Associator  <br/> |**MethodInstance** は **Associator** です。 <br/> |
|Disassociator  <br/> |**MethodInstance** は **Disassociator** です。 <br/> |
|**BulkAssociatedIdEnumerator** <br/> |**MethodInstance** は **BulkAssociatedIdEnumerator** です。 <br/> |
|**BulkAssociationNavigator** <br/> |**MethodInstance** は **BulkAssociationNavigator** です。 <br/> |
   
|
|Default  <br/> |省略可能  <br/> 含まれる外部コンテンツ タイプ内で型を共有するすべての関連付けで、関連付けが既定値かどうかを指定します。 **true** に設定されている場合、含まれる外部コンテンツ タイプ内で型を共有するすべての関連付けで、関連付けが既定値になります。 **false** に設定されている場合は、関連付けは既定値ではありません。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|ReturnParameterName  <br/> |省略可能。  <br/> 関連付けの **ReturnTypeDescriptor** を含むパラメーターの名前。パラメーターの **Direction** 属性には、"Out"、"InOut"、または "Return" のどれかが含まれている必要があります。 <br/> 属性の型: **String** <br/> |
|ReturnTypeDescriptorName  <br/> |省略可能。  <br/> これは非推奨になっています。代わりに **ReturnTypeDescriptorPath** を使用します。 <br/> 属性の型: **String** <br/> |
|ReturnTypeDescriptorLevel  <br/> |省略可能。  <br/> これは非推奨になっています。代わりに **ReturnTypeDescriptorPath** を使用します。 <br/> 属性の型: **Integer** <br/> |
|ReturnTypeDescriptorPath  <br/> |省略可能。  <br/> 関連付けの **TypeDescriptor** のドット パス。 <br/> 属性の型: **String** <br/> |
|Name  <br/> |必ず指定します。  <br/> 関連付けの名前。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |省略可能。  <br/> 関連付けの既定の表示名。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |省略可能。  <br/> この関連付けが頻繁に使用されるかどうかを指定します。  <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**LocalizedDisplayNames** 要素は、関連付け用のローカライズされた名前のリストです。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |Properties 要素は、関連付けのプロパティを指定します。  <br/> |
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**AccessControlList** 要素は、関連付けへのアクセス権のセットを指定します。 <br/> |
| [Association の SourceEntity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/19fb5f38-4e85-7fb0-2562-281b9a9ffbef%28Office.15%29.aspx) <br/> |**SourceEntity** 要素は、関連付けにおける接続元外部コンテンツ タイプを指定します。 <br/> |
| [Association の DestinationEntity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/15c53c3b-888d-67c7-af7d-ef36922eeebc%28Office.15%29.aspx) <br/> |**DestinationEntity** 要素は、関連付けにおける接続先外部コンテンツ タイプを指定します。 <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Method の MethodInstances 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/dae3aeae-e72a-0b52-1348-f5e5cd31109f%28Office.15%29.aspx) <br/> |この関連付けを含む **MethodInstances** 要素。 <br/> |
   

## AssociationGroup 要素
<a name="bkmk_AssociationGroup"> </a>

 **AssociationGroup** を指定します。 **AssociationGroup** は、関連する **AssociationMethods** を結び付けるコンストラクトです。たとえば、 **GetOrdersForCustomer**、 **GetCustomerForOrder**、および **AssociateCustomerToOrder** は、顧客と注文の間の同じ関係を対象とする関連付けメソッドです。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    
 **AssociationGroup** は、 **Reverse** としてマークされていない **AssociationReferences** の参照先であるエンティティ要素、または Reverse としてマークされている **AssociationReferences** の参照元であるエンティティ要素で定義する必要があります。
  
    
    



```XML
<AssociationGroup Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </AssociationGroup>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Name** <br/> |必ず指定します。  <br/> **AssociationGroup** の名前。 <br/> 属性の型: **String** <br/> |
|**DefaultDisplayName** <br/> |省略可能。  <br/> **AssociationGroup** の既定の表示名です。 <br/> 属性の型: **String** <br/> |
|**IsCached** <br/> |省略可能。  <br/> **AssociationGroup** が頻繁に使用されるかどうかを指定します。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**AssociationGroup** のローカライズされた名前。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**AssociationGroup** のプロパティ。 <br/> |
| [AssociationGroup の AssociationReference 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/e32c5267-53b0-9ff0-6e9a-1cb00d9f1d57%28Office.15%29.aspx) <br/> |**AssociationGroup** の **AssociationReference**。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entity の AssociationGroups 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b50c2648-daea-d8c0-039a-b95590b9924c%28Office.15%29.aspx) <br/> |**AssociationGroup** を含む **AssociationGroups** 要素。 <br/> |
   

## AssociationGroups 要素
<a name="bkmk_AssociationGroups"> </a>

 **AssociationGroup** 要素のリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<AssociationGroups></AssociationGroups>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [AssociationGroups の AssociationGroup 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> |**AssociationGroup**。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |この **AssociationGroups** 要素が関連付けられている外部コンテンツ タイプ。 <br/> |
   

## AssociationReference 要素
<a name="bkmk_AssociationReference"> </a>

 **AssociationGroup** に **AssociationReference** を指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<AssociationReference EntityNamespace = "String" EntityName = "String" AssociationName = "String" Reverse = "Boolean"> </AssociationReference>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|EntityNamespace  <br/> |省略可能。  <br/> **Association** が定義された外部コンテンツ タイプの名前空間。 **EntityName** が指定されている場合、 **EntityNamespace** が必要です。 <br/> 属性の型: **String** <br/> |
|EntityName  <br/> |省略可能。  <br/> **Association** が定義された外部コンテンツ タイプの名前。 **EntityNamespace** が指定されている場合、 **EntityName** が必要です。 <br/> 属性の型: **String** <br/> |
|AssociationName  <br/> |必ず指定します。  <br/> **Association** の名前。 <br/> 属性の型: **String** <br/> |
|Reverse  <br/> |省略可能。  <br/> 参照された **Association** の対応元と対応先が反転していることを指定します。これは、同じ **AssociationGroup** のその他の関連付けに対して、 **Association** が反対の方向に機能していることを示します。たとえば、 **AssociationGroup** が **Association** "GetOrdersForCustomer" を参照する場合は、特定の Customer アイテムのための Order アイテムを返すため、 **AssociationGroup** は Customer から Order の方向になります。別の関連付け "GetCustomerForOrder" を参照するもう 1 つの **AssociationReference** は、関連付けが Order から Customer の方向になるため、反転としてマークを付ける必要があります。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [AssociationGroups の AssociationGroup 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> |この **AssociationReference** が所属する **AssociationGroup**。  <br/> |
   

## ConvertType 要素
<a name="bkmk_ConvertType"> </a>

データ値のデータ型を別のデータ型に変換するためのルールを指定します。
  
    
    
 **Namespace:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **Schema:** BDCMetadata
  
    
    
Convert 要素では、データ値のデータ型を別のデータ型に変換するためのルールを指定します。ルールが順番どおりに適用される場合は、このルールでは、BDCType 属性に指定したデータ型に変換されるデータ値のデータ型を指定します。ルールが逆の順序で適用される場合は、このルールでは、 **LOBType** 属性に指定したデータ型に変換されるデータ値のデータ型を指定します。たとえば、このルールでは、外部システムから取得した日付値を最終的にユーザーに表示されるカルチャとロケールに依存する文字列に変換すること、その文字列の更新された値を外部システムと互換性のある日付に変換することを指定できます。
  
    
    

> **注意**
> **ConvertType** では、 **System.String** と **System.DateTime** の間の変換についてグレゴリオ暦以外の暦をサポートしていません。
  
    
    




```XML
<ConvertType LOBType = "String" BDCType = "String"> </ConvertType>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|LOBType  <br/> |必ず指定します。  <br/> ルールが逆の順序で適用される場合にデータ値の変換先となるデータ型。  <br/> 属性の型: **String** <br/> |
|BDCType  <br/> |必ず指定します。  <br/> ルールが順番どおりに適用される場合にデータ値の変換先となるデータ型。  <br/> 属性の型: **String** <br/> |
|LOBLocale  <br/> |省略可能。  <br/> 外部システムから受け取るデータのロケール。  <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor の Interpretation 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/730f9590-ab40-85b8-eb97-8fd9d8e33c8a%28Office.15%29.aspx) <br/> |**TypeDescriptor** で表されるデータ構造に格納されているデータに適用するルール。 <br/> |
   

## DefaultValue 要素
<a name="bkmk_DefaultValue"> </a>

既定値を表します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<DefaultValue MethodInstanceName = "String" Type = "String"> </DefaultValue>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**MethodInstanceName** <br/> |必ず指定します。  <br/> この DefaultValue が適用される **MethodInstance** の名前。 <br/> 属性の型: **String** <br/> |
|**Type** <br/> | 必ず指定します。 <br/>  既定値のデータ型。 <br/>  次に、この属性で使用できる値を示します。 <br/> **System.Int16** <br/> **System.Int32** <br/> **System.Int64** <br/> **System.Single** <br/> **System.Double** <br/> **System.Decimal** <br/> **System.Boolean** <br/> **System.Byte** <br/> **System.UInt16** <br/> **System.UInt32** <br/> **System.UInt64** <br/> **System.Guid** <br/> **System.String** <br/> **System.DateTime** <br/>  その他のシリアル化が可能な任意の型 ( `Type.IsSerializable == true` である場合など) <br/>  属性の型: **String** <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor の DefaultValues 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/635295d1-0f85-6308-976b-d0cb483dece6%28Office.15%29.aspx)||
   

## DefaultValues 要素
<a name="bkmk_DefaultValues"> </a>

 **TypeDescriptor** の **DefaultValues** のリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<DefaultValues></DefaultValues>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [DefaultValues の DefaultValue 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ddb67f64-6361-7b59-6724-4680484d585d%28Office.15%29.aspx) <br/> |**MethodInstance** の **TypeDescriptor** の既定値。 <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> |これらの **TypeDescriptor** が所属する **DefaultValues**。  <br/> |
   

## DestinationEntity 要素
<a name="bkmk_DestinationEntity"> </a>

 **Association** 内で、接続先の外部コンテンツ タイプを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<DestinationEntity Namespace = "String" Name = "String"> </DestinationEntity>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Namespace** <br/> |必ず指定します。  <br/> エンティティ名前空間の名前。  <br/> 属性の型: **String** <br/> |
|**Name** <br/> |必ず指定します。  <br/> 接続先エンティティの名前。  <br/> 属性の型: **String** <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx)||
   

## Entities 要素
<a name="bkmk_Entities"> </a>

外部システムで外部コンテンツ タイプのリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Entities></Entities>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |外部システムでの外部コンテンツ タイプ。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |外部システム。  <br/> |
   

## Entity 要素
<a name="bkmk_Entity"> </a>

外部コンテンツ タイプを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Entity Namespace = "String" Version = "String" EstimatedInstanceCount = "Integer" DefaultOperationMode = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Entity>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Namespace** <br/> |必ず指定します。  <br/> この外部コンテンツ タイプが所属する名前空間。  <br/> 属性の型: **String** <br/> > **メモ**> 名前空間には特殊文字のアスタリスク " *****" を使用しないでください。           |
|**Version** <br/> |必ず指定します。  <br/> この外部コンテンツ タイプのバージョン番号。  <br/> 属性の型: **String** <br/> > **注意**> BDC モデルが変更される場合は、外部コンテンツ タイプのバージョン番号を増やす必要があります。外部コンテンツ タイプの構造が変更される場合は、メジャー番号を増やす必要があります。構造の変更には、 **SpecificFinder** へのフィールドの追加や、識別子フィールドの変更があります。たとえば Creator メソッドの追加、接続情報の変更、 **LobSystems** の名前と型記述子の変更など、変更によって外部コンテンツ タイプの構造が影響を受けない場合は、ビルド番号とリビジョン番号を変更する必要があります。          |
|**EstimatedInstanceCount** <br/> |省略可能。  <br/> 外部システムに含まれる推定の外部アイテム数。  <br/> 既定値: 10000  <br/> 属性の型: **Integer** <br/> |
|**DefaultOperationMode** <br/> |省略可能。  <br/> 外部アイテムの作成、削除、更新、または読み取り時に外部システムを操作するときの既定の動作を指定します。  <br/> 既定値: Default  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|Online  <br/> |すべての操作でキャッシュされた外部アイテムを回避し、外部システムを直接操作します。  <br/> |
|Cached  <br/> |キャッシュされた外部アイテムに対して、 **作成** 、 **読み取り** 、 **更新** 、および **削除** 操作を直接実行します。 **読み取り** 操作の場合、要求された外部アイテムがキャッシュにある場合は、キャッシュ内の外部アイテムを使用します。それ以外の場合は、キャッシュを回避して、外部システムから外部アイテムを取得し、後で使用するためにキャッシュに格納します。 <br/> |
|オフライン  <br/> |キャッシュされた外部アイテムに対してのみ、 **作成** 、 **読み取り** 、 **更新** 、および **削除** 操作を実行します。 <br/> |
|Default  <br/> |システムの既定の動作を使用します。使用環境で外部アイテムのキャッシュがサポートされている場合は、キャッシュ モードを使用します。  <br/> |
   
|
|Name  <br/> |必ず指定します。  <br/> 外部コンテンツ タイプの名前。  <br/> 属性の型: **String** <br/> > **メモ**> 外部コンテンツ タイプの名前には、特殊文字のアスタリスク " *****" を使用しないでください。           |
|DefaultDisplayName  <br/> |省略可能。  <br/> 外部コンテンツ タイプの既定の表示名。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |省略可能。  <br/> この外部コンテンツ タイプの使用頻度が高いかどうかを指定します。true に設定されている場合、Business Data Connectivity (BDC) Service はこの外部コンテンツ タイプをメモリにキャッシュします。  <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |この外部コンテンツ タイプのローカライズされた表示名。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |この外部コンテンツ タイプのプロパティ。  <br/> |
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |この外部コンテンツ タイプのアクセス制御リスト (ACL)。  <br/> |
| [Entity の Identifiers 要素 (BDCMetadata スキーマ) ](http://msdn.microsoft.com/library/6566cb43-4f9e-9a2e-7ec0-89057d7daacc%28Office.15%29.aspx) <br/> |外部コンテンツ タイプの識別子。  <br/> |
| [Entity のMethods 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/42a24b32-bd97-4067-2e25-681d876d29fd%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのメソッド。  <br/> |
| [Entity の AssociationGroups 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b50c2648-daea-d8c0-039a-b95590b9924c%28Office.15%29.aspx) <br/> |外部コンテンツ タイプの関連付けグループ。  <br/> |
| [Entity の Actions 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/c5a6c08d-a3df-61db-3ce3-1e6837bbf221%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのアクション。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystem の Entities 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/fa121ed1-160a-03c9-df42-851ddc2528d5%28Office.15%29.aspx) <br/> |この外部システムの外部コンテンツ タイプのリスト。  <br/> |
   

## FilterDescriptor 要素
<a name="bkmk_FilterDescriptor"> </a>

メソッドのフィルター記述子を指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<FilterDescriptor Type = "String" FilterField = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </FilterDescriptor>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Type  <br/> |必ず指定します。  <br/> フィルター記述子の種類。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|Limit  <br/> |外部システムのクエリの間に使用され、その値は属するメソッドが呼び出されたときに返される外部アイテム ( **EntityInstances**) の数に対する制限として解釈されます。  <br/> |
|PageNumber  <br/> ||
|Wildcard  <br/> |外部システムのクエリの間に使用されます。その値は、一連の **EntityInstances** の特定のフィールドの値に対して一致する通常文字とワイルドカード文字のパターンを表します。外部システムは、フィールドの値が指定されたパターンと一致する **EntityInstances** のみを返します。 <br/> |
|UserContext  <br/> |外部システムのクエリの間に使用されます。その値は、外部システムを呼び出しているユーザーの ID に、任意のクライアント アプリケーションで自動的に設定できます。その後、この値は、外部システムによって、承認および返される結果のフィルター処理に使用できます。  <br/> |
|UserCulture  <br/> ||
|Username  <br/> ||
|Password  <br/> ||
|LastId  <br/> ||
|SsoTicket  <br/> ||
|UserProfile  <br/> |外部システムのクエリの間に使用されます。その値は、現在のユーザーのプロファイルを調べることで取得できます。外部システムは、この値を、返される結果のフィルター処理に使用できます。  <br/> |
|Comparison  <br/> |外部システムのクエリの間に使用されます。外部システムは、 **ComparisonFilter** の値と、一連の **EntityInstances** の特定のフィールドの値を比較し、フィールドの値が比較テストに合格した **EntityInstances** のみを返すことができます。 <br/> |
|Timestamp  <br/> ||
|Input  <br/> |外部システムの操作を呼び出すときに使用されます。外部システムは、 **InputFilter** の値を操作に対する追加引数として使用できます。 <br/> |
|Output  <br/> |外部システムの操作を呼び出すときに使用されます。 **ReturnTypeDescriptor** では取得できない操作の他の結果を、 **InputOutputFilter** の値として取得できます。 <br/> |
|InputOutput  <br/> |外部システムの操作を呼び出すときに使用されます。外部システムは、 **InputOutputFilter** の値を操作に対する追加引数として使用し、 **ReturnTypeDescriptor** では取得できない操作の他の結果を **InputOutputFilter** の値として取得できます。 <br/> |
|Batching  <br/> ||
|BatchingTermination  <br/> ||
|ActivityId  <br/> |**ActivityId** は、外部システムの操作を呼び出すときに使用されます。その値は、現在の操作コンテキストを表す GUID に設定されます。そのような値が使用できない場合、このフィルターはランダムな GUID を生成します。SharePoint Foundation 2010 では、このフィルターは **CorrelationID** を使用します。 <br/> |
   
|
|FilterField  <br/> |省略可能。  <br/> 属性の型: **String** <br/> |
|Name  <br/> |必ず指定します。  <br/> フィルター記述子の名前。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |省略可能。  <br/> フィルター記述子の既定の表示名。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |省略可能。  <br/> このフィルター記述子が頻繁に使用されるかどうかを指定します。 **true** に設定されると、Business Data Connectivity (BDC) Service はこのフィルター記述子をメモリにキャッシュします。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |このフィルター記述子のローカライズされた表示名。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |このフィルター記述子のプロパティ。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Method の FilterDescriptors 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/33d8e418-ddbb-e1ac-b145-836ed9f36e5c%28Office.15%29.aspx) <br/> |メソッドのフィルター記述子のリスト。  <br/> |
   

## FilterDescriptors 要素
<a name="bkmk_FilterDescriptors"> </a>

メソッドのフィルター記述子のリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<FilterDescriptors></FilterDescriptors>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [FilterDescriptors の FilterDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/8ce0a852-38f9-75d2-8258-27c57418f53c%28Office.15%29.aspx) <br/> |フィルター記述子です。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |フィルター記述子のリストが属するメソッドです。  <br/> |
   

## Identifier 要素
<a name="bkmk_Identifier"> </a>

外部コンテンツ タイプの識別子を指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    

> **メモ**
> Business Data Connectivity (BDC) Service では、null 許容型のフィールドに識別子をマッピングできます。ただし、主識別子の場合、この識別子の値が **null** のときに BDC によってエラーが発行されます。
  
    
    




```XML
<Identifier TypeName = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Identifier>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|TypeName  <br/> |必ず指定します。  <br/> 識別子に対応する値のデータ型。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|System.Boolean  <br/> |ビット。  <br/> |
|System.Byte  <br/> |0 から 255 までの数値。  <br/> |
|System.Char  <br/> |Unicode 文字。  <br/> |
|System.DateTime  <br/> |西暦 1 年 1 月 1 日深夜 12:00:00 から西暦 9999 年 12 月 31 日 11:59:59 P.M. までの日付と時刻。  <br/> |
|System.Decimal  <br/> |- 79,228,162,514,264,337,593,543,950,335 から 79,228,162,514,264,337,593,543,950,335 までの数値。  <br/> |
|System.Double  <br/> |－ 1.79769313486232e308 から 1.79769313486232e308 までの倍精度浮動小数点数、正のゼロ、負のゼロ、正の無限大、負の無限大、および非数 (NaN)。  <br/> |
|System.Guid  <br/> |GUID。  <br/> |
|System.Int16  <br/> |- 32768 から 32767 までの数値。  <br/> |
|System.Int32  <br/> |0 から 4,294,967,295 までの数値。  <br/> |
|System.Int64  <br/> |0 から 18,446,744,073,709,551,615 までの数値。  <br/> |
|System.SByte  <br/> |- 128 から 127 までの数値。  <br/> |
|System.Single  <br/> |- 3.402823e38 から 3.402823e38 までの単精度浮動小数点数。  <br/> |
|System.String  <br/> |Unicode テキストの文字列。  <br/> |
|System.TimeSpan  <br/> |100 ナノ秒の精度で、- 10675199 日 2 時間 48 分 5 秒 477 ミリ秒 580 マイクロ秒 800 ナノ秒から 10675199 日 2 時間 48 分 5 秒 477 ミリ秒 580 マイクロ秒 800 ナノ秒までの期間。  <br/> |
|System.UInt16  <br/> |0 から 65535 までの数値。  <br/> |
|System.UInt32  <br/> |0 から 4,294,967,295 までの数値。  <br/> |
|System.UInt64  <br/> |0 から 18,446,744,709,551,615 までの数値。  <br/> |
   
|
|Name  <br/> |必ず指定します。  <br/> 識別子の名前。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |省略可能。  <br/> 識別子の既定の表示名。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |省略可能。  <br/> この識別子が頻繁に使用されるかどうかを指定します。 **true** に設定すると、Business Data Connectivity (BDC) Service ではこの識別子がメモリにキャッシュされます。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |識別子のローカライズされた表示名。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |識別子のプロパティ。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entity の Identifiers 要素 (BDCMetadata スキーマ) ](http://msdn.microsoft.com/library/6566cb43-4f9e-9a2e-7ec0-89057d7daacc%28Office.15%29.aspx) <br/> |外部コンテンツ タイプの識別子のリスト。  <br/> |
   

## Identifiers 要素
<a name="bkmk_Identifiers"> </a>

外部コンテンツ タイプの識別子のリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Identifiers></Identifiers>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Identifiers の Identifier 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/c4abf09b-10b6-0007-9214-35d5fe675be7%28Office.15%29.aspx) <br/> |識別子を指定します。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |この識別子のリストを含む外部コンテンツ タイプです。  <br/> |
   

## Interpretation 要素
<a name="bkmk_Interpretation"> </a>

 **TypeDescriptor** によって表されるデータ構造に格納されたデータに適用するルールを指定します。通常、このルールを指定して、外部システムから返されたデータ値を変更し、ユーザー インターフェイスでそのデータ値を簡単に表すことができるようにします。外部システムからデータ値を取得するときは、指定したルールは、 **Interpretation** 要素に指定した順序で適用される必要があります。1 番目のルールは、外部システムから受信したデータ値に適用される必要があります。連続するルールは、前のルールの適用結果のデータ値に適用されます。外部システムにデータ値を送信するときは、指定したルールは、 **Interpretation** 要素に指定した逆の順序で適用される必要があります。1 番目のルールは、ユーザーから受信したデータ値に適用される必要があります。連続するルールは、前のルールの適用結果のデータ値に適用されます。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Interpretation></Interpretation>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Interpretation の ConvertType 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/c474cf2c-b631-f3c9-daf1-f05d3e0d385f%28Office.15%29.aspx) <br/> |データ型を別のデータ型に変換することを指定する **ConvertType** 要素。 <br/> |
| [Interpretation の NormalizeDateTime 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/bbae3bfa-0754-d576-2bee-1ac0e8508a57%28Office.15%29.aspx) <br/> |外部システムから取得した値の日時表記を別の表記に変換することを指定する **NormalizeDateTime** 要素。 <br/> |
|NormalizeString  <br/> |外部システムから取得した値の文字列表記を別の表記に変換することを指定する **NormalizeString** 要素。 <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> |**TypeDescriptor** 要素。 <br/> |
   

## LobSystem 要素
<a name="bkmk_LobSystem"> </a>

外部データ ソースを表します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<LobSystem Type = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </LobSystem>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Type  <br/> |**LobSystem** のプロパティ。 <br/> 必ず指定します。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|Database  <br/> |表している外部データ ソースはデータベースです。  <br/> |
|DotNetAssembly  <br/> |表している外部データ ソースは .NET Framework クラスのセットです。  <br/> |
|Wcf  <br/> |表している外部データ ソースは WCF サービスのエンドポイントです。  <br/> |
|WebService  <br/> |表している外部データ ソースは Web サービスです。これは非推奨になっています。代わりに Wcf を使用します。  <br/> |
|Custom  <br/> |表している外部データ ソースには、接続とデータ転送を管理するために実装されたカスタム コネクタがあります。  <br/> |
   
|
|Name  <br/> |**LobSystem** の名前。 <br/> 必ず指定します。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |**LobSystem** の既定の表示名です。 <br/> 省略可能。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |**LobSystem** が頻繁に使用されるかどうかを指定します。頻繁に使用される場合、Business Data Connectivity (BDC) Service は **LobSystem** をキャッシュします。 <br/> 省略可能。  <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**LobSystem** のローカライズされた名前。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**LobSystem** のプロパティを指定します。 <br/> |
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**LobSystem** のアクセス制御リスト (ACL) を指定します。 <br/> |
| [LobSystem の Proxy 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/8ec2e7b0-156f-ff4a-a87b-fe5764e4875b%28Office.15%29.aspx) <br/> |この要素が存在しない場合に生成されるプロキシと同一のユーザー指定のプロキシを指定します。  <br/> |
| [LobSystem の LobSystemInstances 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/122e419a-0497-afdf-1117-a82ab429f3eb%28Office.15%29.aspx) <br/> |この外部システムの外部システム インスタンスを指定します。  <br/> |
| [LobSystem の Entities 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/fa121ed1-160a-03c9-df42-851ddc2528d5%28Office.15%29.aspx) <br/> |この外部システムの外部コンテンツ タイプを指定します。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Model の LobSystems 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d9bf0ca9-fb79-e3a5-cc84-9510d93798cb%28Office.15%29.aspx) <br/> |このモデルの外部システムのリストを指定します。  <br/> |
   

## LobSystemInstance 要素
<a name="bkmk_LobSystemInstance"> </a>

外部システム インスタンスを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<LobSystemInstance Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </LobSystemInstance>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Name  <br/> |必ず指定します。  <br/> 外部システム インスタンスの名前。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |省略可能。  <br/> 外部システム インスタンスの既定の表示名。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |省略可能。  <br/> この外部システム インスタンスの使用頻度が高いかどうかを指定します。 **true** に設定されている場合は、Business Data Connectivity (BDC) Service は外部システム インスタンスをキャッシュします。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |この外部システム インスタンスのローカライズされた名前。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |この外部システム インスタンスのプロパティ。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystem の LobSystemInstances 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/122e419a-0497-afdf-1117-a82ab429f3eb%28Office.15%29.aspx) <br/> |外部システム インスタンスのリスト。  <br/> |
   

## LobSystemInstances 要素
<a name="bkmk_LobSystemInstances"> </a>

外部システム インスタンスのリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<LobSystemInstances></LobSystemInstances>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystemInstances の LobSystemInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a0c37891-ef4f-58af-445c-5ff4d5ad6cef%28Office.15%29.aspx) <br/> |外部システムのインスタンス。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |外部システム。  <br/> |
   

## LobSystems 要素
<a name="bkmk_LobSystems"> </a>

モデルの **LobSystem** 要素のリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<LobSystems></LobSystems>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |外部システムを指定する **LobSystem** 要素。 <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Model 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> |アプリケーション定義 (BDC モデル)。  <br/> |
   

## LocalizedDisplayName 要素
<a name="bkmk_LocalizedDisplayName"> </a>

ローカライズされた名前を指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<LocalizedDisplayName LCID = "Integer"> </LocalizedDisplayName>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|LCID  <br/> |必ず指定します。  <br/> 言語コード識別子 (LCID)。  <br/> 属性の型: **Integer** <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**LocalizedDisplayNames** を含む **LocalizedDisplayName** 要素。 <br/> |
   

## LocalizedDisplayNames 要素
<a name="bkmk_LocalizedDisplayNames"> </a>

 **MetadataObject** のローカライズされた名前のリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<LocalizedDisplayNames></LocalizedDisplayNames>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LocalizedDisplayNames の LocalizedDisplayName 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/93fb80ef-6347-b463-da90-4980d872678e%28Office.15%29.aspx) <br/> |ローカライズされた名前。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Model 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> ||
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> ||
| [LobSystemInstances の LobSystemInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a0c37891-ef4f-58af-445c-5ff4d5ad6cef%28Office.15%29.aspx) <br/> ||
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> ||
| [Identifiers の Identifier 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/c4abf09b-10b6-0007-9214-35d5fe675be7%28Office.15%29.aspx) <br/> ||
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> ||
| [FilterDescriptors の FilterDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/8ce0a852-38f9-75d2-8258-27c57418f53c%28Office.15%29.aspx) <br/> ||
| [Parameters の Parameter 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/811cad0b-ba71-8be0-0765-3e0dec18a0d3%28Office.15%29.aspx) <br/> ||
| [TypeDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> ||
| [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> ||
| [MethodInstances の MethodInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> ||
| [AssociationGroups の AssociationGroup 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> ||
| [Actions の Action 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> ||
| [ActionParameters の ActionParameter 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/1f5fa96a-1bff-f007-984d-a644cbbb2648%28Office.15%29.aspx) <br/> ||
   

## MetadataObject 要素
<a name="bkmk_MetadataObject"> </a>

 **名前空間:**
  
    
    
 **スキーマ:**
  
    
    



```XML

```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
 **子要素**
  
    
    
 **親要素**
  
    
    

## Method 要素
<a name="bkmk_Method"> </a>

外部コンテンツ タイプのメソッドを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Method IsStatic = "Boolean" LobName = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Method>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|IsStatic  <br/> |省略可能。  <br/> このメソッドを実行するために、外部アイテム ( **EntityInstance**) を実行用のコンテキストとして使用する必要があるかどうかを指定します。 **true** を設定すると、このメソッドは静的メソッドとなり、実行用のコンテキストを提供する特定の **EntityInstance** を必要としません。 **false** に設定すると、このメソッドはインスタンス メソッドとなり、実行用のコンテキストを提供する **EntityInstance** を必要とします。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
|LobName  <br/> |省略可能。  <br/> このメソッドによって表される外部システムに定義されている操作の名前です。  <br/> 属性の型: **String** <br/> |
|Name  <br/> |必ず指定します。  <br/> このメソッドの名前です。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |省略可能。  <br/> このメソッドの既定の表示名です。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |省略可能。  <br/> このメソッドが頻繁に使用されるかどうかを指定します。 **true** に設定すると、Business Data Connectivity (BDC) Service ではこのメソッドがメモリにキャッシュされます。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |このメソッドのローカライズされた表示名です。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |このメソッドのプロパティです。  <br/> |
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |このメソッドのアクセス制御リスト (ACL) です。  <br/> |
| [Method の FilterDescriptors 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/33d8e418-ddbb-e1ac-b145-836ed9f36e5c%28Office.15%29.aspx) <br/> |このメソッドのフィルター記述子です。  <br/> |
| [Method の Parameters 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/343f4c25-e122-1a4c-2b80-bb8f25e3cc82%28Office.15%29.aspx) <br/> |このメソッドのパラメーターです。メソッドが 1 つ以上の戻り値パラメーターを持つことはできません。  <br/> |
| [Method の MethodInstances 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/dae3aeae-e72a-0b52-1348-f5e5cd31109f%28Office.15%29.aspx) <br/> |このメソッドのメソッド インスタンスです。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entity のMethods 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/42a24b32-bd97-4067-2e25-681d876d29fd%28Office.15%29.aspx) <br/> |外部コンテンツ タイプのメソッドのリストです。  <br/> |
   

## MethodInstance 要素
<a name="bkmk_MethodInstance"> </a>

 **MethodInstance** を指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    
BDC モデル内の次の 2 つのケースでは、実行時に  [InvalidOperationException](https://msdn.microsoft.com/library/system.invalidoperationexception%28v=vs.110%29.aspx) が発生します。
  
    
    

- 同じフィールド セットを返す 2 つの **SpecificFinder** メソッド インスタンス。
    
  
- 同じ数のフィールドを保有し、同じ数のフィールドを別のメソッド インスタンス ( **Finder** など) と共有する 2 つの **SpecificFinder** メソッド インスタンス。
    
  



```XML
<MethodInstance Type = "Strig" Default = "Boolean" ReturnParameterName = "String" ReturnTypeDescriptorName = "String" ReturnTypeDescriptorLevel = "Integer" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </MethodInstance>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Type** <br/> |必ず指定します。  <br/> **MethodInstance** の型を指定します。 <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|Finder  <br/> |特定の **Entity** の **EntityInstances** のゼロ以上のコレクションを返すために呼び出すことができる **MethodInstance** の 1 つ。 **Finder** 入力は、 **Finder** を含む **Method** に含まれる **FilterDescriptors** によって定義されます。 <br/> |
|SpecificFinder  <br/> |**EntityInstanceId** が与えられたときに、特定の **Entity** の特定の **EntityInstance** を返すために呼び出すことができる **MethodInstance** の 1 つ。 **SpecificFinder** 入力は、 **Entity** に関連付けられた **Identifiers** によって定義され、並べられます。 <br/> |
|GenericInvoker  <br/> |外部システムで特定のタスクを実行するために呼び出すことができる **MethodInstance** の 1 つ。 **GenericInvoker** の入力と出力は、 **Method** に固有です。 <br/> |
|IdEnumerator  <br/> |特定の **Entity** の **EntityInstances** の ID を表す **Field** 値を返すために呼び出すことができる **MethodInstance** の 1 つ。 **IdEnumerator** の入力は、ID のリスト (検索可能なエンティティごとに一意) を取得する **IdEnumerator** を含むメソッドに含まれた **FilterDescriptors** によって定義されます。このメソッド インスタンスによって、SharePoint Server での外部データ検索が可能になります。 <br/> |
|ChangedIdEnumerator  <br/> |指定された時間後に外部システムで変更された **EntityInstances** の **EntityInstanceIds** を取得するために呼び出すことができる **MethodInstance** の 1 つ。 <br/> |
|DeletedIdEnumerator  <br/> |指定された時間後に外部システムから削除された **EntityInstances** の **EntityInstanceIds** を取得するために呼び出すことができる **MethodInstance** の 1 つ。 <br/> |
|Scalar  <br/> |外部システムで呼び出せる単一の値を返す **MethodInstance** の 1 つ。たとえば、現在までの販売額の合計を外部システムから取得するためにスカラー メソッド インスタンスを使用することができます。 **Entities** は、ゼロ以上のスカラー メソッド インスタンスを持っています。 <br/> |
|AccessChecker  <br/> |指定された **EntityInstanceIds** によって識別される **EntityInstances** のコレクションのそれぞれの呼び出しセキュリティ プリンシパルが持つ権限を取得するために呼び出すことができる **MethodInstance** の 1 つ。 <br/> |
|Creator  <br/> |**EntityInstance** を作成するために呼び出すことができる **MethodInstance** の 1 つ。 **EntityInstance** を作成するために必要な一連のフィールドは、クリエイター ビューと呼ばれます。 <br/> |
|Deleter  <br/> |指定された **EntityInstanceId** で **EntityInstance** を削除するために呼び出すことができる **MethodInstance** の 1 つ。 <br/> |
|Updater  <br/> |指定された **EntityInstanceId** によって識別される **EntityInstance** を更新するために呼び出すことができる **MethodInstance** の 1 つ。 **EntityInstance** を更新するために必要な一連のフィールドは、アップデーター ビューと呼ばれます。変更される前に、値が渡される必要がある一連のフィールドは、プリアップデーター ビューと呼ばれます。 <br/> |
|StreamAccessor  <br/> |バイトのデータ ストリームの形で **EntityInstance** のフィールドを取得するために呼び出すことができる **MethodInstance** の 1 つ。 <br/> |
|BinarySecurityDescriptorAccessor  <br/> |外部システムからバイトのシーケンスを取得するために呼び出すことができる **MethodInstance** の 1 つ。システム固有のバイト シーケンスは、一連のセキュリティ プリンシパルと、それぞれのセキュリティ プリンシパルが、指定された **EntityInstanceId** によって識別される **EntityInstance** に対して持つ、対応する権限を示します。 <br/> |
|BulkSpecificFinder  <br/> |対応する一連の **EntityInstanceIds** に対して、 **Entity** の、一連の特定の **EntityInstances** を返すよう呼び出すことができる **MethodInstance** の 1 つ。 <br/> |
|BulkIdEnumerator  <br/> |特定の ID に対応する外部アイテムについて、最小限の情報を取得するために呼び出すことができる **MethodInstance** の 1 つ。このメソッド インスタンスは、キャッシュされたデータの同期を最適化するために使用することができます。このメソッドは、特定の **Identities** に対応する外部アイテムの ID とバージョン情報のみを返す必要があります。呼び出し側のアプリケーションは、ローカル バージョンと比較し、変更がされている場合は、キャッシュされたデータを更新するために変更された外部アイテムを要求します。 <br/> |
   
|
|**Default** <br/> |省略可能。  <br/> 含有する外部コンテンツ タイプ ( **Entity**) 内で型を共有するすべての **MethodInstances** で **MethodInstance** を既定とするかどうかを指定します。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**ReturnParameterName** <br/> |省略可能。  <br/> **MethodInstance** の **ReturnTypeDescriptor** を含む **Parameter** の名前。 **Parameter** の **Direction** 属性は、 **Out**、 **InOut**、または **Return** の値を持つ **ParameterDirection** 属性である必要があります。 <br/> この属性は、 **GenericInvoker**、 **Creator**、 **Deleter**、および **Updater** を除き、 **MethodInstances** のすべての型に対して指定する必要があります。 <br/> 属性の型: **String** <br/> |
|**ReturnTypeDescriptorLevel** <br/> |省略可能。  <br/> これは非推奨になっています。代わりに **ReturnTypeDescriptorPath** を使用します。 <br/> 属性の型: **Integer** <br/> |
|**ReturnTypeDescriptorPath** <br/> |省略可能。  <br/> 関連付けの **TypeDescriptor** のドット パス。 <br/> 属性の型: **String** <br/> |
|**Name** <br/> |必ず指定します。  <br/> **MethodInstance** の名前を指定します。 <br/> 属性の型: **String** <br/> |
|**DefaultDisplayName** <br/> |省略可能。  <br/> **MethodInstance** の既定の表示名を指定します。 <br/> 属性の型: **String** <br/> |
|**IsCached** <br/> |省略可能。  <br/> **MethodInstance** が頻繁に使用されるかどうかを指定します。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**MethodInstance** のローカライズされた表示名。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**MethodInstance** のプロパティ。 <br/> |
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**MethodInstance** のアクセス制御リスト (ACL)。 <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Method の MethodInstances 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/dae3aeae-e72a-0b52-1348-f5e5cd31109f%28Office.15%29.aspx) <br/> |**MethodInstances** を含む **MethodInstance** 要素。 <br/> |
   

## MethodInstances 要素
<a name="bkmk_MethodInstances"> </a>

メソッドの関連付けとメソッド インスタンスのリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<MethodInstances></MethodInstances>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> |関連付け。  <br/> |
| [MethodInstances の MethodInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> |メソッド インスタンス。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |このメソッド インスタンスが属しているメソッド。  <br/> |
   

## Methods 要素
<a name="bkmk_Methods"> </a>

外部コンテンツ タイプのメソッドのリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Methods></Methods>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |メソッドを指定します。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> |このメソッドのリストが属する外部コンテンツ タイプです。  <br/> |
   

## Model 要素
<a name="bkmk_Model"> </a>

アプリケーション定義を表すルート要素を指定します。モデルでは、外部アプリケーションに含まれている外部コンテンツ タイプを定義します。 
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Model Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Model>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Name  <br/> |**Model** の名前。 <br/> 必ず指定します。  <br/> 属性の型: **String** <br/> |
|DefaultDisplayName  <br/> |**Model** の既定の表示名です。 <br/> 省略可能。  <br/> 属性の型: **String** <br/> |
|IsCached  <br/> |**Model** が頻繁に使用されるかどうかを指定します。これを **true** に設定すると、 **Model** は Business Data Connectivity (BDC) Service によってキャッシュされます。 <br/> 省略可能。  <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**Model** のローカライズされた名前。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**Model** のプロパティ。 <br/> |
| [AccessControlList 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/b7f97740-5d2c-f91a-1028-10e2890d4a99%28Office.15%29.aspx) <br/> |**Model** のアクセス制御リスト (ACL)。 <br/> |
| [Model の LobSystems 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d9bf0ca9-fb79-e3a5-cc84-9510d93798cb%28Office.15%29.aspx) <br/> |この **Model** に含まれている **LobSystems**。  <br/> |
   
 **親要素**
  
    
    
なし
  
    
    

## NormalizeDateTime 要素
<a name="bkmk_NormalizeDateTime"> </a>

日付と時刻の値の表現を別の表現に変換するときに使用するルールを指定します。たとえば、このルールでは、協定世界時 (UTC) で表されている値を現地のタイム ゾーンに変換できます。 
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<NormalizeDateTime LobDateTimeMode = "String"> </NormalizeDateTime>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**LobDateTimeMode** <br/> |必ず指定します。  <br/> 適用する変換を指定します。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|UTC  <br/> |外部システムから受信する値は UTC (協定世界時) です。受信した値が **Local** の場合、UTC に変換されます。BDC は、UTC を外部システムに送信します。 <br/> |
|Local  <br/> |外部システムから受信する値は **Local** です。外部システムから受信した値が **Local** の場合、UTC に変換されます。BDC は、 **Local** を外部システムに送信します。 <br/> |
|Unspecified  <br/> |外部システムから送信される値の種類は Unspecified です。BDC では、UTC になるようにこの種類を上書きして、値は UTC で表されているとみなします。BDC は、UTC の値を Unspecified 種類として外部システムに送信します。  <br/> |
   
|
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor の Interpretation 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/730f9590-ab40-85b8-eb97-8fd9d8e33c8a%28Office.15%29.aspx) <br/> |**TypeDescriptor** で表されるデータ構造に格納されているデータに適用するルールを指定する **Interpretation** 要素。 <br/> |
   

## NormalizeString 要素
<a name="bkmk_NormalizeString"> </a>

メソッドのパラメーターを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML

```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
 **子要素**
  
    
    
 **親要素**
  
    
    

## Parameter 要素
<a name="bkmk_Parameter"> </a>

メソッドのパラメーターを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Parameter Direction = "String" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </Parameter>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Direction  <br/> |必ず指定します。  <br/> パラメーターの方向です。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|In  <br/> |表される **Parameter** は入力パラメーターです。 <br/> |
|Out  <br/> |表されるパラメーターは出力パラメーターです。  <br/> |
|InOut  <br/> |表されるパラメーターは、入力パラメーターと出力パラメーターです。C# では、" **ref**" に相当します。  <br/> |
|Return  <br/> |表されるパラメーターは戻り値パラメーターです。  <br/> |
   
|
|**Name** <br/> |必ず指定します。  <br/> パラメーターの名前です。  <br/> 属性の型: **String** <br/> |
|**DefaultDisplayName** <br/> |省略可能。  <br/> パラメーターの既定の表示名です。  <br/> 属性の型: **String** <br/> |
|**IsCached** <br/> |省略可能。  <br/> **Parameter** が頻繁に使用されるかどうかを指定します。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |パラメーターのローカライズされた名前です。  <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |パラメーターのプロパティです。  <br/> |
| [TypeDescriptor](http://msdn.microsoft.com/library/30e38d7f-af18-20ec-45ab-0bece071ce67.aspx) <br/> |パラメーターの Root 型記述子です。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Method の Parameters 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/343f4c25-e122-1a4c-2b80-bb8f25e3cc82%28Office.15%29.aspx) <br/> |このパラメーターを含む **Parameters** 要素です。 <br/> |
   

## Parameters 要素
<a name="bkmk_Parameters"> </a>

メソッドのパラメーターのリストを指定します。
  
    
    

  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Parameters></Parameters>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Parameters の Parameter 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/811cad0b-ba71-8be0-0765-3e0dec18a0d3%28Office.15%29.aspx) <br/> |パラメーター。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> |これらのパラメーターが所属するメソッド。  <br/> |
   

## Properties 要素
<a name="bkmk_Properties"> </a>

メタデータ オブジェクトのプロパティのリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Properties></Properties>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Properties の Property 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/2e6e8d5d-ef3b-c536-f3d1-ad2039b92c24%28Office.15%29.aspx) <br/> |プロパティを指定します。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [Model 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d7823090-b20d-2c96-c359-081c055d0e65%28Office.15%29.aspx) <br/> ||
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> ||
| [LobSystemInstances の LobSystemInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a0c37891-ef4f-58af-445c-5ff4d5ad6cef%28Office.15%29.aspx) <br/> ||
| [Entities の Entity 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/a8455bc4-12d8-85e0-146e-5d1d8579e1f5%28Office.15%29.aspx) <br/> ||
| [Identifiers の Identifier 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/c4abf09b-10b6-0007-9214-35d5fe675be7%28Office.15%29.aspx) <br/> ||
| [Methods の Method 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/70e87a9e-4959-0a7b-3f37-ddec36473ff4%28Office.15%29.aspx) <br/> ||
| [FilterDescriptors の FilterDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/8ce0a852-38f9-75d2-8258-27c57418f53c%28Office.15%29.aspx) <br/> ||
| [Parameters の Parameter 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/811cad0b-ba71-8be0-0765-3e0dec18a0d3%28Office.15%29.aspx) <br/> ||
| [TypeDescriptor](http://msdn.microsoft.com/library/30e38d7f-af18-20ec-45ab-0bece071ce67.aspx) <br/> ||
| [TypeDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> ||
| [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> ||
| [MethodInstances の MethodInstance 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/577ff9d0-706b-be7d-af5b-883e137cada8%28Office.15%29.aspx) <br/> ||
| [AssociationGroups の AssociationGroup 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/db30622e-3c2b-2735-9360-a702196cbcff%28Office.15%29.aspx) <br/> ||
| [Actions の Action 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/f58b96c0-77a8-69d3-8710-fff03d4970b9%28Office.15%29.aspx) <br/> ||
| [ActionParameters の ActionParameter 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/1f5fa96a-1bff-f007-984d-a644cbbb2648%28Office.15%29.aspx) <br/> ||
   

## Property 要素
<a name="bkmk_Property"> </a>

メタデータ オブジェクトのプロパティの名前と型を指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Property Name = "String" Type = "String"> </Property>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**Name** <br/> |必ず指定します。  <br/> プロパティの名前を指定します。  <br/> 属性の型: **String** <br/> |
|**Type** <br/> |必ず指定します。  <br/> プロパティのデータ型を指定します。  <br/> 属性の型: **String** <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |このプロパティを含む **Properties** 要素。 <br/> |
   

## Proxy 要素
<a name="bkmk_Proxy"> </a>

この要素が存在しない場合に生成されるプロキシと同一のユーザー提供のプロキシを指定します。これは、プロキシ生成によるオーバーヘッドを削減してパフォーマンスを向上させるために使用されます。外部システムに接続するカスタム ビジネス ロジックを指定するには, .NET Connectivity Assembly タイプの外部システムを使用する必要があります。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Proxy></Proxy>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [LobSystems の LobSystem 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/d4e58d7d-a628-8093-97fe-7c3136e8f6f2%28Office.15%29.aspx) <br/> |このプロキシが適用される **LobSystem** 要素。 <br/> |
   

## Right 要素
<a name="bkmk_Right"> </a>

アクセス制御エントリ (ACE) に対して 1 つのアクセス許可を指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<Right BdcRight = "String"> </Right>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|BdcRight  <br/> |必ず指定します。  <br/> 権限を保持するセキュリティ プリンシパルで利用できるアクセス許可。  <br/> 次の表に、この属性で使用できる値を示します。  <br/> |**値**|**説明**|
|:-----|:-----|
|なし  <br/> |アクセス許可がありません。  <br/> |
|Execute  <br/> |表されるセキュリティ プリンシパルには、 **MethodInstance** を起動するアクセス許可があります。 <br/> |
|Edit  <br/> |表されるセキュリティ プリンシパルには、メタデータ オブジェクトの属性、または他のメタデータ オブジェクトとの関係を変更するアクセス許可があります。  <br/> |
|SetPermissions  <br/> |表されるセキュリティ プリンシパルには、メタデータ オブジェクトのアクセス許可セットを変更するアクセス許可があります。  <br/> |
|SelectableInClients  <br/> |表されるセキュリティ プリンシパルには、この権限が参照するメタデータ オブジェクトを選択するためのアクセス許可があります。ユーザーがこのアクセス許可を持っていない場合は、メタデータは選択できません。  <br/> |
   
|
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [AccessControlList の AccessControlEntry 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/85e24489-0a6b-dfda-fb03-474fe7b0d947%28Office.15%29.aspx) <br/> |この権限を含む **AccessControlEntry** 要素。 <br/> |
   

## SourceEntity 要素
<a name="bkmk_SourceEntity"> </a>

 **Association** のソースの外部コンテンツタイプを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<SourceEntity Namespace = "String" Name = "String"> </SourceEntity>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|Namespace  <br/> |必ず指定します。  <br/> この要素を含む **Association** のソースである外部コンテンツ タイプの名前空間。 <br/> 属性の型: String  <br/> |
|Name  <br/> |必ず指定します。  <br/> この要素を含む **Association** のソースである外部コンテンツ タイプの名前。 <br/> 属性の型: **String** <br/> |
   
 **子要素**
  
    
    
なし
  
    
    
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MethodInstances の Association 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx) <br/> |この要素を含む **Association**。  <br/> |
   

## TypeDescriptor 要素
<a name="bkmk_TypeDescriptor"> </a>

 **TypeDescriptor** を指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<TypeDescriptor TypeName = "String" LobName = "String" IdentifierEntityNamespace = "String" IdentifierEntityName = "String" IdentifierName = "String" ForeignIdentifierAssociationName = "String" ForeignIdentifierAssociationEntityName = "String" ForeignIdentifierAssociationEntityNamespace = "String" AssociatedFilter = "String" IsCollection = "Boolean" ReadOnly = "Boolean" CreatorField = "Boolean" UpdaterField = "Boolean" PreUpdaterField = "Boolean" Significant = "Boolean" Name = "String" DefaultDisplayName = "String" IsCached = "Boolean"> </TypeDescriptor>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    


|**属性**|**説明**|
|:-----|:-----|
|**TypeName** <br/> |必ず指定します。  <br/> **TypeDescriptor** によって表されるデータ構造のデータ型の識別子。 <br/> 属性の型: **String** <br/> |
|**LobName** <br/> |省略可能。  <br/> **TypeDescriptor** によって表されるデータ構造。この属性の既定値は、 **TypeDescriptor** の名前です。たとえば、基幹業務 (LOB) システムの "CN1A" と言う名前のデータ構造は、 **TypeDescriptor** の **LobName** 属性が "CN1A" と等しい場合、 **Name** 属性が "Customer Name" と等しい **TypeDescriptor** によって表すことができます。 <br/> 属性の型: **String** <br/> |
|**IdentifierEntityNamespace** <br/> |省略可能。  <br/> **TypeDescriptor** が参照する識別子を含む外部コンテンツ タイプの名前空間。 **TypeDescriptor** が **Identifier** を参照しない場合、この属性は不要です。この属性が存在する場合、 **IdentifierEntityName** 属性と **IdentifierName** 属性も必要です。この属性の既定値は、 **TypeDescriptor** を含むパラメーターを持つメソッドがある外部コンテンツ タイプの名前空間です。 <br/> 属性の型: **String** <br/> |
|**IdentifierEntityName** <br/> |省略可能。  <br/> **TypeDescriptor** が参照する **Identifier** を含む **Entity** の名前です。 **TypeDescriptor** が **Identifier** を参照しない場合、この属性は不要です。この属性が存在する場合、 **IdentifierEntityNamespace** 属性と **IdentifierName** 属性も必要です。この属性の既定値は、 **TypeDescriptor** を含む **Parameter** を持つ **Method** がある **Entity** の名前です。 <br/> 属性の型: **String** <br/> |
|**IdentifierName** <br/> |省略可能。  <br/> **TypeDescriptor** によって参照される **Identifier** の名前。 **TypeDescriptor** が **Identifier** を参照しない場合、この属性は不要です。 <br/> 属性の型: **String** <br/> |
|**ForeignIdentifierAssociationName** <br/> |省略可能。  <br/> **TypeDescriptor** によって参照される **Association** の名前。 **TypeDescriptor** が **Association** を参照しない場合、この属性は不要です。この属性が存在する場合は、 **IdentifierName** 属性も必要です。この **TypeDescriptor** によって参照される **Identifier** が **Association** に関連していて、 **Identifier** が **Association** のソース **Entity** に含まれている場合は、 **ForeignIdentifierAssociationName** 属性を指定する必要があります。 <br/> 属性の型: **String** <br/> |
|**ForeignIdentifierAssociationEntityName** <br/> |省略可能。  <br/> **TypeDescriptor** によって参照される **Association** を含む **Entity** の名前。 **TypeDescriptor** が **Association** を参照しない場合、この属性は不要です。この属性が存在する場合は、 **ForeignIdentifierAssociationEntityNamespace** 属性と **ForeignIdentifierAssociationName** 属性も必要です。この属性の既定値は、 **TypeDescriptor** を含む **Parameter** を持つ **Method** がある **Entity** の名前です。 <br/> 属性の型: **String** <br/> |
|**ForeignIdentifierAssociationEntityNamespace** <br/> |省略可能。  <br/> **TypeDescriptor** によって参照される **Association** を含む **Entity** の名前空間。 **TypeDescriptor** が **Association** を参照しない場合、この属性は不要です。この属性が存在する場合は、 **ForeignIdentifierAssociationEntityName** 属性と **ForeignIdentifierAssociationName** 属性も必要です。この属性の既定値は、 **TypeDescriptor** を含む **Parameter** を持つ **Method** がある **Entity** の名前空間です。 <br/> 属性の型: **String** <br/> |
|**AssociatedFilter** <br/> |省略可能。  <br/> **TypeDescriptor** に関連付けられた **FilterDescriptor** の名前。 **TypeDescriptor** が **FilterDescriptor** に関連付けられていない場合、この属性は不要です。 <br/> 属性の型: **String** <br/> |
|**IsCollection** <br/> |省略可能。  <br/> **TypeDescriptor** が、単一のデータ構造を表すか、データ構造の集まりを表すかを指定します。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**ReadOnly** <br/> |省略可能。  <br/> **TypeDescriptor** が表すデータ構造で格納されたデータが変更可能かどうかを指定します。 **TypeDescriptor** を含む **Parameter** の **Direction** 属性値が "In" の場合は、この属性を指定する必要はありません。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**CreatorField** <br/> |省略可能。  <br/> **TypeDescriptor** が、 **TypeDescriptor** を含む **Parameter** を持つ **Method** に含まれる **Creator** タイプの **MethodInstances** のフィールドを表すかどうかを指定します。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**UpdaterField** <br/> |省略可能。  <br/> **TypeDescriptor** が、 **TypeDescriptor** を含む **Parameter** を持つ **Method** に含まれる **Updater** タイプの **MethodInstances** のフィールドを表すかどうかを指定します。この属性が指定されている場合、 **PreUpdaterField** 属性を指定する必要はありません。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**PreUpdaterField** <br/> |Optional.  <br/> **TypeDescriptor** が表すデータ構造が、 **Updater** タイプの **MethodInstances** 用のフィールドの外部システムから受信された最新のデータ値を格納するかどうかを指定します。この属性が指定されている場合、 **UpdaterField** 属性を指定する必要はありません。 <br/> 既定値: **false** <br/> 属性の型: **Boolean** <br/> |
|**Significant** <br/> |省略可能。  <br/> この **TypeDescriptor** が表すデータ構造で格納されたデータが、ハッシュ コードの計算や、データ構造に格納された値の比較に含められるかどうかを指定します。たとえば、レコードが変更されたかどうかを判断するとき、そしてそれが重要な場合は、顧客の姓を表す **TypeDescriptor** が考慮されます。それに対して、レコードが変更されたかどうかを判断するとき、そしてそれが重要でない場合は、顧客レコードが最後に変更された日付を表す **TypeDescriptor** は、通常、考慮されません。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
|**Name** <br/> |必ず指定します。  <br/> **TypeDescriptor** の名前。 <br/> 属性の型: **String** <br/> > **メモ**> **TypeDescriptor** の名前には、スラッシュ ("/")、ピリオド (".")、左かっこ ("[") の特殊文字は使用できません。          |
|**DefaultDisplayName** <br/> |省略可能。  <br/> **TypeDescriptor** の表示名。 <br/> 属性の型: **String** <br/> |
|**IsCached** <br/> |省略可能。  <br/> **TypeDescriptor** が頻繁に使用されるかどうかを指定します。 <br/> 既定値: **true** <br/> 属性の型: **Boolean** <br/> |
   
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [MetadataObject の LocalizedDisplayNames 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/3202aecf-f98f-20cb-1fdd-f3a054cb24aa%28Office.15%29.aspx) <br/> |**TypeDescriptor** のローカライズされた名前。 <br/> |
| [MetadataObject の Properties 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/9901904f-96ee-0cbb-64a9-c2aad9d72128%28Office.15%29.aspx) <br/> |**TypeDescriptor** のプロパティ。 <br/> **TypeDescriptor** の型が **System.String** の場合は、 **Properties** 要素に、 **System.Int32** 型の **Property** を、 **Name** 属性を **Size** に設定して含めることができます。 **Property** の値では、この **TypeDescriptor** によって記述されるデータ構造値の予想される最長文字列を指定します。 <br/> |
| [TypeDescriptor の Interpretation 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/730f9590-ab40-85b8-eb97-8fd9d8e33c8a%28Office.15%29.aspx) <br/> |**TypeDescriptor** が表すデータ構造で格納されるデータのルール。 <br/> |
| [TypeDescriptor の DefaultValues 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/635295d1-0f85-6308-976b-d0cb483dece6%28Office.15%29.aspx) <br/> |**TypeDescriptor** の既定値。 <br/> |
| [TypeDescriptor の TypeDescriptors 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/322b2d3f-c92d-3c24-9f22-07b56396275b%28Office.15%29.aspx) <br/> |**TypeDescriptor** の子 **TypeDescriptors**。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor の TypeDescriptors 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/322b2d3f-c92d-3c24-9f22-07b56396275b%28Office.15%29.aspx)||
   

## TypeDescriptors 要素
<a name="bkmk_TypeDescriptors"> </a>

親 TypeDescriptor の **TypeDescriptors** のリストを指定します。
  
    
    
 **名前空間:** `http://schemas.microsoft.com/windows/2007/BusinessDataCatalog`
  
    
    
 **スキーマ:** BDCMetadata
  
    
    



```XML
<TypeDescriptors></TypeDescriptors>
```

以下のセクションで、属性、子要素、親要素について説明します。
  
    
    
 **属性**
  
    
    
なし
  
    
    
 **子要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> |**TypeDescriptor**。  <br/> |
   
 **親要素**
  
    
    


|**要素**|**説明**|
|:-----|:-----|
| [TypeDescriptor 要素 (BDCMetadata スキーマ)](http://msdn.microsoft.com/library/ae423de8-c13b-aea5-d47b-17ef786fb5a7%28Office.15%29.aspx) <br/> ||
| [TypeDescriptor](http://msdn.microsoft.com/library/30e38d7f-af18-20ec-45ab-0bece071ce67.aspx) <br/> ||
   

## その他の技術情報
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 の BDC モデル スキーマの変更点](changes-in-the-bdc-model-schema-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でクライアント オブジェクト モデルと外部データを使用する方法の概要](get-started-using-the-client-object-model-with-external-data-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Business Connectivity Services プログラマー リファレンス](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
