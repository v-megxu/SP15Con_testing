---
title: SharePoint 2013 の検索用 BDC モデル ファイルを強化する
ms.prod: SHAREPOINT
ms.assetid: 3c67b1cf-5fca-4805-a1b5-c9ac1ff8aede
---


# SharePoint 2013 の検索用 BDC モデル ファイルを強化する
BDC メタデータ モデルのプロパティについて説明します。これらのプロパティは、SharePoint 2013 の検索 で外部データをクロールできるようにする BCS インデックス コネクタに適用されます。
## BDC モデル ファイルの検索プロパティ
<a name="SearchBDCModelProperties_SearchProperties"> </a>

検索 でのコネクタ フレームワークにより、外部データをクロールして、BCS インデックス コネクタによってそのデータを検索結果で使用可能にすることができます。BCS インデックス コネクタは、外部データ ソースとの通信でクローラーが使用します。クローラーは、クロール時に BCS インデックス コネクタを呼び出して外部システムからデータを取得し、そのデータを元のクローラーに渡します。 
  
    
    
BCS インデックス コネクタの構成要素は以下のとおりです。
  
    
    


  
    
    
> **BDC モデル ファイル** 外部システムへの接続情報とデータ構造を提供するファイルです。
    
  

  
    
    
> **コネクタ** 外部システムに接続し、アクセス URL と BCS 識別子を解析するコードが含まれているコンポーネントです。
    
  
BDC メタデータ モデルには 検索 に適用可能なプロパティがいくつか組み込まれており、その多くは BCS インデックス コネクタ クロールをサポートするために必要とされます。 
  
    
    
次の表に、検索 に適用される BDC モデル プロパティの説明を示します。
  
    
    

**表 1. BDC モデル ファイルの検索プロパティ**


|**名前**|**メタデータ オブジェクト**|**説明**|
|:-----|:-----|:-----|
|ShowInSearchUI  <br/> |Model  <br/> |**LobSystemInstance** 要素を検索ユーザー インターフェイスに表示するよう指定します。この値は、カスタム コネクタについては無視されます。 <br/> |
|InputUriProcessor  <br/> |LobSystem  <br/> |入力 URL をコネクタに渡す前にその入力 URL を処理するクラスの名前を指定します。詳細については、「 [カスタム インデックス コネクタの作成](http://msdn.microsoft.com/library/ec2df34d-178c-4ae1-a2b0-a6af04ee57bd%28Office.15%29.aspx)」を参照してください。  <br/> |
|OutputUriProcessor  <br/> |LobSystem  <br/> |出力 URL をコネクタから検索システムに渡す前にその出力 URL を処理するクラスの名前を指定します。.NET およびカスタム BCS インデックス コネクタに適用されます。詳細については、「 [カスタム インデックス コネクタの作成](http://msdn.microsoft.com/library/ec2df34d-178c-4ae1-a2b0-a6af04ee57bd%28Office.15%29.aspx)」を参照してください。  <br/> |
|SystemUtilityTypeName  <br/> |LobSystem  <br/> |**StructuredRepositorySystemUtility** クラスを実装するクラスの名前を指定します。カスタム BCS インデックス コネクタに適用されます。詳細については、「 [カスタム インデックス コネクタの作成](http://msdn.microsoft.com/library/ec2df34d-178c-4ae1-a2b0-a6af04ee57bd%28Office.15%29.aspx)」を参照してください。  <br/> |
|Title  <br/> |Entity  <br/> |検索結果に表示する外部コンテンツ タイプのタイトルを指定します。  <br/> |
|DefaultLocale  <br/> |Entity  <br/> |ロケール文字列を指定します。この値は、 **LCIDField** プロパティまたは **CultureField** プロパティを使用して無効にできます。 <br/> |
|RootFinder  <br/> |Method  <br/> |クロールするアイテムを列挙するために使用する **Finder** メソッドを指定します。たとえば、データベースに接続する場合、これは **SELECT** ステートメントかクロールするテーブルのリストになります。 <br/> |
|DirectoryLink  <br/> |Method  <br/> |BCS が関連付けの間を移動するように指定します。階層クロールに必要です。  <br/> |
|DeletedCountField  <br/> |Method  <br/> |削除された数の値を指定します。このプロパティは、ゼロより大きい整数が指定されていない場合は無効にされます。  <br/> |
|WindowsSecurityDescriptorField  <br/> |Method  <br/> |アイテムの Windows セキュリティ記述子を指定します。指定しない場合は、 **GetSecurityDescriptor** メソッドが呼び出されます。 **GetSecurityDescriptor** が定義されていない場合は、すべての外部アイテムに Everyone アクセス制御リスト (ACL) が割り当てられます。 <br/> |
|AuthorField  <br/> |Method  <br/> |検索結果に表示する作成者名を指定します。  <br/> |
|DisplayUriField  <br/> |Method  <br/> |検索結果に表示する URL を指定します。指定した場合、このプロパティは BCS によって提供されるプロファイル ページの URL を無効にします。指定しなかった場合、検索結果に表示される URL は **bdc3://** で始まり、ブラウザーによって認識されません。 <br/> |
|LastModifiedTimeStampField  <br/> |Method  <br/> |検索結果に表示する外部アイテムのタイムスタンプを指定します。この値は、増分クロールでも使用されます。  <br/> |
|DescriptionField  <br/> |Method  <br/> |検索結果に表示する説明を指定します。  <br/> |
|LCIDField  <br/> |Method  <br/> |**DescriptionField** のロケール ID (LCID) を指定します。指定しない場合は、既定のワード ブレーカーが使用されます。 <br/> |
|CultureField  <br/> |Method  <br/> |**DescriptionField** のカルチャを指定します。 <br/> |
|Extension  <br/> |Method  <br/> |クロール可能なストリームのファイル名拡張子を指定します。指定しない場合の既定の拡張子は、 **.txt** です。 <br/> |
|MimeType  <br/> |Method  <br/> |クロール可能なストリームの MIME の種類を指定します。指定しない場合の既定の拡張子は、 **.txt** です。 **Extension** フィールドと **MimeType** フィールドの両方が指定されている場合は、 **MimeType** フィールドで指定した値が使用されます。 <br/> |
|UseClientCachingForSearch  <br/> |Method  <br/> |列挙中、クローラーがコンテンツをキャッシュするかどうかを指定します。コンテンツがキャッシュされる場合、クローラーは、個々のアイテムをクロールするときにコンテンツ ソースにもう一度トリップしません。  <br/> |
|EnumerateIdsOnly  <br/> |FilterDescriptor  <br/> |**IDEnumerator** で ID のみを返すかどうかを指定します。 <br/> |
|CrawlStartTime  <br/> |FilterDescriptor  <br/> |最後のクロールの開始時刻を格納します。  <br/> |
|SynchronizationCookie  <br/> |FilterDescriptor  <br/> |外部コンテンツ ソースがクロール後に Cookie を返すように指定します。その Cookie は、次の列挙呼び出しのときにインデックス コネクタによって再送信されます。外部コンテンツ ソースは Cookie を使用して、最後のクロール以降に何が変更されたかを判断します。このプロパティは、 **ChangedIDEnumerator** および **DeletedIDEnumerator** メソッド インスタンスと一緒に使用されます。 <br/> |
|Property  <br/> |TypeDescriptor  <br/> | プロパティの検索で使用される **struct** 配列を指定します。次の要素で構成されます。 <br/> **PropertyName** <br/> **PropertyValue** <br/> **PropertyCulture** <br/> |
|Text  <br/> |TypeDescriptor  <br/> | 添付ファイルの検索で使用される **struct** 配列を指定します。次の要素で構成されます。 <br/> **TextExtension** <br/> **TextContentType** <br/> **TextValue** <br/> |
   

## BDC モデル ファイルを変更して外部データをクロールするときのパフォーマンスを向上させる
<a name="SearchBDCModelProperties_Performance"> </a>

検索用に有効にする外部システムの BDC モデル ファイルを作成する場合は、そのモデル ファイルを拡張して、外部システムのクロール時のパフォーマンスを最適化することができます。このセクションでは、BDC モデル ファイルを変更してパフォーマンスを向上させる方法について説明します。
  
    
    

### 大規模データの取得時にインライン プロパティ I/O を使用する

一般に、アイテムについて返されるデータの一部が大規模な場合は、 **SpecificFinder** メソッドを使用してデータを返す代わりに、次の特殊化されたメソッドを使用してデータを取得する必要があります。
  
    
    

- セキュリティ アクセス制御リスト (ACL) を渡す場合は、 **WindowsSecurityDescriptor** プロパティの代わりに **BinarySecurityDescriptorAccessor** メソッドを使用します。
    
  
- ストリームを渡す場合は、 **StreamAccessor** メソッドを使用します。
    
  
ネットワークの待機時間が長くない限り、通常望ましいのは、外部システムへの余分なトリップでかかるコストよりも、パフォーマンスの向上です。
  
    
    

### 外部システムをクロールするときの列挙の最適化

外部システムの 1 回の呼び出しで、100,000 を超えるアイテムを列挙しないでください。列挙を長時間実行すると、断続的な中断が発生し、クロールが完了しない可能性があります。以下の例に示すように、BDC モデルで、個々に列挙できる論理フォルダーにデータを構築することをお勧めします。 
  
    
    
この例では、ColumnA に固定の値セットがある 100 万行のデータベース テーブルに対して列挙を実行します。このシナリオでは、ColumnA を外部コンテンツ タイプと見なし、以下の SQL ステートメントを使用して、この値セットの列挙子を記述できます。 
  
    
    



```

SELECT DISTINCT( ISNULL(ColumnA,'unknown')) as ColumnA  FROM table
```

次に、以下の SQL ステートメントを使用して特定のファインダーを定義します。 
  
    
    



```
SELECT DISTINCT( ISNULL(ColumnA,'unknown')) as ColumnA  FROM table where ColumnA = @Value
```

最後に、以下のように関連付けナビゲーション操作を定義する必要があります。 
  
    
    



```
Select * from table where ColumnA=@value
```

任意のメソッドで 2 分以内に結果を返し始める必要があります。そうでない場合、クローラーは呼び出しを中止します。たとえば、 **LIKE** 句を使用する複雑な SQL ステートメントは、完了するまでに 2 分を超えるため、クローラーは呼び出しを中止します。
  
    
    

### UseClientCachingForSearch プロパティでクロール速度を向上させる

 **UseClientCachingForSearch** プロパティは、列挙中にアイテムをキャッシュすることにより、フル クロールの速度を上げます。変更ログに基づく増分クロールを実装するときにも、このプロパティを使用することをお勧めします。これによって増分クロールの速度が上がります。
  
    
    

> **重要**
> アイテムの大きさが平均で 30 キロバイトを超える場合は、このプロパティを設定しないでください。設定すると、非常に多くのキャッシュ不足が発生し、パフォーマンス向上が見込めなくなります。 
  
    
    


## BDC モデル ファイルのセキュリティ
<a name="SearchBDCModelProperties_Security"> </a>

リポジトリで NTLM 認証を使用する場合、クロールに PassThrough 認証を指定することをお勧めします。
  
    
    
プロファイル ページでは、フロントエンド Web サーバーからのマルチ ホップ委任の問題が原因で、Secure Store Service を使用しなければならない場合があります。この問題が発生した場合は、2 つの類似した **LobSystemInstance** インスタンスを作成することによって、プロファイル ページを許可しながら、クロールを最適化できます。最初のインスタンスでは、Secure Store Service 認証からの資格情報を使用する必要があります。このインスタンスには **ShowInSearchUI** プロパティを含めないでください。2 番目のインスタンスでは PassThrough 認証を使用し、 **ShowInSearchUI** プロパティを含めます。プロファイル ページでは最初の **LobSystemInstance** インスタンスを使用し、クローラーは 2 番目のインスタンスを使用します。
  
    
    

> **メモ**
> これには、 **ShowInSearchUI** プロパティを、 **LobSystem** レベルの代わりに **LobSystemInstance** レベルで設定する必要があります。
  
    
    


## その他の技術情報
<a name="SP15enhanceBDC_addlresources"> </a>


-  [SharePoint 2013 の検索コネクタ フレームワーク](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [BDC モデル インフラストラクチャ](http://msdn.microsoft.com/library/2818ebdd-6cda-4d8f-82b2-7fde9fbf2633%28Office.15%29.aspx)
    
  
-  [BDC モデルの作成](http://msdn.microsoft.com/library/170d1cfd-cf19-4162-b79f-ba6d3b4ad23b%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 の BCS 開発環境のセットアップ](setting-up-a-development-environment-for-bcs-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint Designer を使用してカスタムコネクタの BDC モデル ファイルを作成する](http://msdn.microsoft.com/library/8f239482-0c82-4b60-817d-b0c4392e7e2e%28Office.15%29.aspx)
    
  

