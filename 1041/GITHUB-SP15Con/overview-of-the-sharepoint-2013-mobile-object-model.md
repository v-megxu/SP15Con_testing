---
title: SharePoint 2013 モバイル オブジェクト モデルの概要
ms.prod: SHAREPOINT
ms.assetid: 72319846-d02d-49e7-b830-48eb8f5715cb
---


# SharePoint 2013 モバイル オブジェクト モデルの概要
SharePoint 2013および Windows Phone 7.5 の統合ソリューションの開発に使用される SharePoint 2013 サーバー オブジェクト モデルおよび Silverlight クライアント オブジェクト モデルの新しいパブリック クラスについて確認します。
## モバイル Silverlight 向けクライアント オブジェクト モデル
<a name="SP15OM_ClientOM"> </a>

このセクションのすべてのクラスは **Microsoft.SharePoint.Client** 名前空間に含まれます。このセクションの API 以外にも、「SharePoint モバイル向けサーバー オブジェクト モデル」セクションのほとんどのクラスとメンバーはクライアント オブジェクト モデルで呼び出し可能です。"SP" で始まるクラスについては、クライアント オブジェクト モデル名では "SP" が削除されます。それ以外については、クライアント オブジェクト モデル名が明示されています。メンバー名は別途の記述がない限り、クライアント オブジェクト モデルでも同じです。
  
    
    

### AlternateUrl クラス

Web アプリケーションの代替 URL およびその適用先のゾーンを表します。
  
    
    

```cs

public class AlternateUrl
```


#### プロパティ

 **Uri** (読み取り専用)
  
    
    
代替 URL の URI を取得します。
  
    
    



```cs
public String Uri
```

 **UrlZone** (読み取り専用)
  
    
    
代替 URL のゾーンを取得します。
  
    
    



```
public UrlZone UrlZone
```

UrlZone クラスは、サーバー オブジェクト モデルの SPUrlZone のクライアント オブジェクト モデル バージョンです。詳細については、「 [Microsoft SharePoint 2010 SDK へようこそ](http://msdn.microsoft.com/ja-jp/library/ee557253.aspx)」を参照してください。
  
    
    

### AuthenticationCompletedEventArgs クラス

 **AuthenticationCompleted** イベントに関するデータを提供します。
  
    
    

```cs
public sealed class AuthenticationCompletedEventArgs : AsyncCompletedEventArgs

```


#### コンストラクター

AuthenticationCompletedEventArgs クラスの新しいインスタンスを初期化します。
  
    
    

```cs

public AuthenticationCompletedEventArgs(Exception error, bool canceled, HttpStatusCode userState)
```

 **パラメーター**
  
    
    

-  _error_ は、認証試行で例外が発生した場合の Exception オブジェクトです。
    
  
-  _canceled_ は、認証試行が成功または失敗する前に取り消された場合に true となります。
    
  
-  _userState_ は、サーバーから返される HttpStatusCode です。
    
  

#### プロパティ

 **HttpStatusCode** (読み取り専用)
  
    
    
認証試行後にサーバーから返されるステータスを取得します。
  
    
    



```cs
public HttpStatusCode HttpStatusCode
```


### AuthenticationStatus 列挙

認証試行の現在の状態を指定します。
  
    
    

- **NotStarted**
    
  
- **InProgress**
    
  
- **CompletedSuccess**
    
  
- **CompletedException**
    
  

### Authenticator クラス

SharePoint Web サイトのユーザーを認証する方法を提供します。
  
    
    

```
public class Authenticator : ICredentials
```


#### コンストラクター

クラスの新しいインスタンスを初期化します。
  
    
    

```cs
public Authenticator()

public Authenticator(Uri uagServerUrl)
```

 **パラメーター**
  
    
    
 _uagServerUrl_ は United Access Gateway (UAG) サーバーの絶対 URL です。
  
    
    



```cs

public Authenticator(string userName, string password)
```

 **パラメーター**
  
    
    
 _userName_ は資格情報の名前です。
  
    
    
 _password_ は資格情報のパスワードです。
  
    
    



```cs
public Authenticator(string userName, string password, string domain)
```

 **パラメーター**
  
    
    
 _userName_ は資格情報の名前です。
  
    
    
 _password_ は資格情報のパスワードです。
  
    
    
 _domain_ は資格情報を検証するドメインまたはコンピューターの名前です。通常は現在のユーザーのドメインです。
  
    
    



```cs
public Authenticator(string userName, string password, Uri uagServerUrl)
```

 **パラメーター**
  
    
    
 _userName_ は資格情報の名前です。
  
    
    
 _password_ は資格情報のパスワードです。
  
    
    
 _uagServerUrl_ は United Access Gateway (UAG) サーバーの絶対 URL です。
  
    
    



```cs
public Authenticator(string userName, string password, string domain, Uri uagServerUrl)
```

 **パラメーター**
  
    
    
 _userName_ は資格情報の名前です。
  
    
    
 _password_ は資格情報のパスワードです。
  
    
    
 _domain_ は資格情報を検証するドメインまたはコンピューターの名前です。通常は現在のユーザーのドメインです。
  
    
    
 _uagServerUrl_ は United Access Gateway (UAG) サーバーの絶対 URL です。
  
    
    

#### メソッド

 **ClearAllApplicationSettings**
  
    
    
キヤッシュからすべての Cookie、資格情報、UAG 設定をクリアします。
  
    
    



```cs
public static void ClearAllApplicationSettings
```

 **ClearAllCookies**
  
    
    
保存された Cookie をすべてクリアし、すべての **Authenticator** オブジェクトの **Status** プロパティを **NotStarted** に設定します。
  
    
    



```cs
public static void ClearAllCookies()
```

 **ClearAllCredentials**
  
    
    
キャッシュからすべての資格情報をクリアし、すべての **Authenticator** オブジェクトの **Status** プロパティを **NotStarted** に設定します。
  
    
    



```cs
public static void ClearAllCredentials()
```

 **GetCredential**
  
    
    
指定された URI および認証の種類の資格情報オブジェクトを取得します。
  
    
    



```
public NetworkCredential GetCredential(Uri uri, string authType)
```

 **パラメーター**
  
    
    

-  _uri_ はクライアント認証の提供先の URI (ポートを含む) です。
    
  
-  _authType_ は要求された認証の種類です。
    
  
このメソッドは匿名認証にのみ使用します。 _authType_ が "Basic" ではない場合、空のオブジェクトが返されます。 **NetworkCredential** クラスの詳細については、「 [NetworkCredential クラス](http://msdn.microsoft.com/ja-jp/library/system.net.networkcredential.aspx)」を参照してください。
  
    
    
 **IsRequestUnauthorized**
  
    
    
Cookie または資格情報が無効のため認証要求が失敗した場合、true が返されます。
  
    
    



```cs
public static bool IsRequestUnauthorized(ClientRequestFailedEventArgs failedEventArgs)
```


#### プロパティ

 **AllowSmartRouting**
  
    
    
スマート ルーティングが有効にされているかどうかのインジケーターを取得または設定します。
  
    
    



```
public bool AllowSmartRouting
```

スマート ルーティングが有効にされている場合、 **Authenticator** オブジェクトは SharePoint および UAG サーバーを実行しているサーバーへの接続を試み、先に応答した方を通信チャネルとして使用します。UAG サーバーが存在しない場合、このプロパティは無視されます。既定値は **true** です。 **false** に設定すると、常に UAG サーバーが使用されます。
  
    
    
 **AuthenticatorMode**
  
    
    
認証モードを取得または設定します。
  
    
    



```cs
public ClientAuthenticationMode AuthenticationMode
```

 **ClientAuthenticationMode** 列挙の詳細については、このドキュメントの後述する項を参照してください。
  
    
    
 **CookieCachingEnabled**
  
    
    
Cookie をキャッシュに保存するかどうかのインジケーターを取得または設定します。
  
    
    



```
public bool CookieCachingEnabled
```

Cookie のキャッシュを有効にする場合、ある時点で Cookie の有効期限が切れることを考慮に入れておいてください。 **ExecuteQueryAsync** が呼び出された場合に Cookie の期限が切れていると、呼び出しが失敗し、エラー用コールバックが実行されます。このため、このプロパティを true に設定する場合は、このような事態にキャッシュをクリアするエラー用コールバックにコードを追加する必要があります。下の例の `execQueryArgs` は、 **ExecuteQueryAsync** のエラー用コールバックで渡される **ClientRequestFailedEventArgs** 型に属するものです。
  
    
    



```cs
if (Authenticator.IsRequestUnauthorized(execQueryArgs))
{
    (sender as Authenticator).ClearCookies();
}
```

 **CredentialCachingEnabled**
  
    
    
資格情報をキャッシュに保存するかどうかのインジケーターを取得または設定します。
  
    
    



```cs

public bool CredentialCachingEnabled
```

 **Domain**
  
    
    
資格情報のドメインまたはコンピューターを取得または設定します。通常は、現在のユーザーのドメインです。
  
    
    



```cs
public string Domain
```

このプロパティに新しい値を設定すると、 **Status** プロパティは NotStarted に設定されます。
  
    
    
 **NavigateBackAfterAuthentication**
  
    
    
ログイン ページから前のページにユーザーを戻すかどうかのインジケーターを取得または設定します。
  
    
    



```cs
public bool NavigateBackAfterAuthentication
```

 **Password**
  
    
    
資格情報用のパスワードを取得または設定します。
  
    
    



```cs
public string Password
```

このプロパティに新しい値を設定すると、 **Status** プロパティは **NotStarted** に設定されます。
  
    
    
 **PromptOnFailure**
  
    
    
初回認証に失敗した場合に、名前およびパスワードの入力をユーザーに求めるかどうかのインジケーターを取得または設定します。
  
    
    



```cs
public bool PromptOnFailure
```

 **Status** (読み取り専用)
  
    
    
認証試行のステータスを取得します。
  
    
    



```cs
public AuthenticationStatus Status
```

 **AuthenticationStatus** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    
 **UagServerUrl**
  
    
    
UAG サーバーの URL を取得または設定します。
  
    
    



```cs
public Uri UagServerUrl
```

 **UserName**
  
    
    
資格情報のユーザー名を取得または設定します。
  
    
    



```cs
public string UserName
```

このプロパティに新しい値を設定すると、 **Status** プロパティは **NotStarted** に設定されます。
  
    
    

#### イベント

 **AuthenticationCompleted**
  
    
    
認証試行が完了すると、成功したかどうかに関係なく発生します。
  
    
    



```cs
public event EventHandler<AuthenticationCompletedEventArgs> AuthenticationCompleted;
```


### ClientAuthenticationMode 列挙

 **Authenticator** オブジェクトの認証モードを指定します。これは既存の列挙ですが、新しい値、 **BrowserBasedAuthentication** が追加されました。
  
    
    


|**既定値**||
|:-----|:-----|
|**FormsAuthentication** <br/> |フォーム ベースの認証モードを表します。  <br/> |
|**Anonymous** <br/> |匿名アクセス モードを表します。  <br/> |
|**BrowserBasedAuthentication** <br/> |Microsoft Office Forms Based Authentication (MSOFBA) モードを表します。  <br/> |
   

### ODataAuthenticator クラス

SharePoint Web サイトのユーザーを認証する方法を提供します。
  
    
    

```cs
public class ODataAuthenticator : Authenticator
```


#### コンストラクター

コンストラクターは親クラスのコンストラクターと同じです。詳細については、このドキュメントで前述した Authenticator クラスを参照してください。
  
    
    

#### メソッド

 **Authenticate**
  
    
    
指定された Web サイトに対してユーザーを認証します。
  
    
    



```cs
public new void Authenticate(Uri serverUrl)
```

親クラスに同じ名前の内部メソッドがあるため、 `new` キーワードが使用されます。
  
    
    

#### プロパティ

 **CookieContainer** (読み取り専用)
  
    
    
Web サイトへの要求用に Cookie のコンテナーを取得します。
  
    
    



```cs
public new CookieContainer CookieContainer
```

親クラスに同じ名前の内部メソッドがあるため、 `new` キーワードが使用されます。
  
    
    
 **ResolvedUrl** (読み取り専用)
  
    
    
 **ODataAuthenticator** が使用されている場合、SharePoint を実行中のサーバーとの通信に使用する URL を取得します。この値は、UAG サーバーで公開されている URL になるか、または **AllowSmartRouting** プロパティが true の場合、 **Authenticate** メソッドの呼び出し後に先に SharePoint イントラネット URL が応答した場合は、その URL になります。
  
    
    



```cs
public Uri ResolvedUrl
```


### ServerSettings クラス

Web サイトを含む Web アプリケーションの代替 URL を取得する方法を提供します。
  
    
    

```cs
public static class ServerSettings
```


#### メソッド

 **GetAlternateUrls**
  
    
    
指定された Web サイトの代替 URL を取得します。
  
    
    



```cs
public static ClientObjectList<AlternateUrl> GetAlternateUrls(ClientRuntimeContext context)
```

 **Parameters**
  
    
    
 _context_ は、現在のクライアント コンテキストを表すオブジェクトです。
  
    
    
 **AlternateUrl** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    

## SharePoint モバイル向けサーバー オブジェクト モデル
<a name="SP15OM_ServerOM"> </a>

このセクションのすべてのクラスは **Microsoft.SharePoint** 名前空間に含まれます。明示される場合を除き、これらはすべて、クライアント オブジェクト モデルでも使用できます。"SP" で始まるクラスについては、クライアント オブジェクト モデル名では "SP" が削除されます。 それ以外については、クライアント オブジェクト モデル名が明示されています。 メンバー名は別途の記述がない限り、クライアント オブジェクト モデルでも同じです。
  
    
    

### GeolocationFieldControl クラス

(クライアント オブジェクト モデルでは使用できません。) 
  
    
    
 **SPFieldGeolocation** フィールドの表示をコントロールします。この型のオブジェクトは、 **SPFieldGeolocation** オブジェクトの **FieldRenderingControl** プロパティの値として使用されます。
  
    
    



```cs
public class GeolocationFieldControl : BaseFieldControl
```

このクラスに関連して、表示モード用と新規および編集モード用の 2 つのレンダリング テンプレートが存在します。それらはファイル %SHAREPOINTROOT%\\TEMPLATE\\ControlTemplates\\DefaultTemplates.ascx に定義されています。
  
    
    

#### フィールド

新規および編集モードでフィールドを表示するのに、次の記述が使用されます。
  
    
    

```cs
protected TextBox m_latitudeBox;
protected TextBox m_longitudeBox;
protected Label m_longitudeLabel;
protected Label m_latitudeLabel;
```


#### メソッド

このクラスでは非派生のパブリック プロパティが実装されていません。次の表に示すように、いくつかの派生メソッドの標準のオーバーライドが存在します。
  
    
    


|**メソッド**|**オーバーライド対象**|
|:-----|:-----|
|CreateChildControls  <br/> |表示モード用の JavaScript マップ コントロールなど、子コントロールを作成します。  <br/> |
|Focus  <br/> |経度テキストボックスの子コントロールにフォーカスを与えます。  <br/> |
|OnPreRender  <br/> |base メソッドを呼び出します。  <br/> |
|Validate  <br/> |ユーザー インターフェイス (UI) に出現する緯度および経度の値を検証します。ここでは基礎となる **SPFieldGeolocatonValue** オブジェクトの **Longitude** および **Latitude** プロパティは検証されないため、ユーザーが UI でこれらの値を 1 つ以上変更し、その変更をまだ保存していない場合は一致しなくなります。 <br/> |
   

#### プロパティ

このクラスでは非派生のパブリック プロパティが実装されていません。次の表に示すように、いくつかの派生プロパティの標準のオーバーライドが存在します。
  
    
    


|**プロパティ**|**オーバーライド対象**|
|:-----|:-----|
|CssClass  <br/> |親実装と同じように動作します。  <br/> |
|DefaultTemplateName  <br/> |"GeolocationField" を返します。  <br/> |
|DisplayTemplateName  <br/> |"GeolocationDisplayField" を返します。  <br/> |
|Value  <br/> |**SPFieldGeolocationValue** オブジェクトを使用して表示される値を取得または設定します。 <br/> |
   

### SPFieldGeolocation クラス

経度、緯度、高度で定義される地球上の位置を保持するフィールド (列) を表します。
  
    
    

```cs

public class SPFieldGeolocation : SPField
```

このクラスに関連して、 **Geolocation** フィールド型が % _SHAREPOINTROOT%_\\TEMPLATE\\XML\\fldtypes.xml に定義されています。
  
    
    

#### コンストラクター (オーバーロード)

 **SPFieldGeolocation** クラスの新しいインスタンスを初期化します。
  
    
    

```cs
public SPFieldGeolocation(SPFieldCollection fields, string fieldName)
public SPFieldGeolocation(SPFieldCollection fields, string fieldName, string displayName)
```

 **パラメーター**
  
    
    

-  _fields_ は、新しいフィールド型のオブジェクトが追加される、フィールド型のコレクションです。
    
  
-  _fieldName_ は、新しいフィールド型の内部名です。
    
  
-  _displayName_ は、新しいフィールド型のフレンドリ名です。
    
  

#### メソッド

 **GetFieldValueForClientRender**
  
    
    
クライアントに表示できるようフィールドの値を取得します。
  
    
    



```cs

public override object GetFieldValueForClientRender(SPItem item, SPControlMode mode)
```

パラメーター
  
    
    

-  _item_ は現在のリスト アイテムです。
    
  
-  _mode_ は現在のレンダリング モード (新規作成、編集、表示など) です。
    
  
 **GetJsonClientFormFieldSchema**
  
    
    
フィールド スキーマを JavaScript Object Notation (JSON) として取得します。
  
    
    



```cs
public override Dictionary<string, object> GetJsonClientFormFieldSchema(SPControlMode mode)
```

 **パラメーター**
  
    
    
 _mode_ は現在のレンダリング モード (新規作成、編集、表示など) です。
  
    
    
 **ValidateAndParseValue**
  
    
    
指定されたリスト アイテムが Null でないことを確認し、文字列が Open Geospatial Consortium (OGC) 標準に準拠して構成されていることを確認して、それを **SPFieldGeolocationValue** 型にキャスト可能なオブジェクトとして返します。
  
    
    



```cs
public override object ValidateAndParseValue(SPListItem item, string value)
```

 **パラメーター**
  
    
    

-  _item_ はリスト アイテムで、その値で更新されます。
    
  
-  _value_ は地理位置情報の値を文字列で表したものです。
    
  
次のメソッドは、SharePoint 2010 に存在した継承メソッドの標準のオーバーライドです。 次の表に、このクラスに固有の情報を示します。
  
    
    


|**メソッド**|**オーバーライド対象**|
|:-----|:-----|
|GetFieldValue(String s)  <br/> |指定された値を SPFieldGeolocationValue にキャスト可能なオブジェクトとして返します。  <br/> |
|GetFieldValueAsText(Object o)  <br/> |GetValidatedString をラップします。  <br/> |
|GetValidatedString(Object o)  <br/> |指定された値が Open Geospatial Consortium (OGC) 標準に準拠して構成されていることを確認し、それを文字列として返します。  <br/> |
   

#### プロパティ

 **JSLink**
  
    
    
 **SPFieldGeolocation** 型のフィールドを表示するJavaScript ファイルの名前を取得または設定します。
  
    
    

> **メモ**
> JSLink プロパティは、アンケート リストやイベント リストではサポートされません。SharePoint の予定表は、イベント リストです。 
  
    
    




```cs
public override string JSLink
```

既定値は "clienttemplates.js|Geolocationfieldtemplate.js|sp.map.js" です。
  
    
    
 **FieldRenderingMobileWebControl**
  
    
    
フィールドを表示する **SPMobileGeolocationField** オブジェクトを取得します。
  
    
    



```cs
public override SPMobileBaseFieldControl FieldRenderingMobileControl
```

このプロパティは以前の **FieldRenderingMobileControl** に代わるものです。
  
    
    
残りのプロパティは、SharePoint 2010 に存在した継承プロパティの標準のオーバーライドです。 次の表に、このクラスに固有の情報を示します。
  
    
    


|**プロパティ**|**オーバーライド対象**|
|:-----|:-----|
|FieldValueType  <br/> |**typeof(SPFieldGeolocationValue)** を返します。 <br/> |
|FieldRenderingControl  <br/> |**GeolocationFieldControl** オブジェクトを返します。 <br/> |
|Filterable  <br/> |**false** を返します。 <br/> |
|Sortable  <br/> |**false** を返します。 <br/> |
|(現在使用されていません)  <br/> FieldRenderingMobileControl  <br/> |**SPMobileGeolocationField** オブジェクトを返します。 <br/> |
   

### SPFieldGeolocationValue クラス

経度、緯度、高度で定義される地球上の位置を表します。
  
    
    

```cs
public class SPFieldGeolocationValue : SPFieldGeographyValue
```


#### コンストラクター (オーバーロード)

 **SPFieldGeolocationValue** クラスの新しいインスタンスを初期化します。
  
    
    

```cs
public SPFieldGeolocationValue()
public SPFieldGeolocationValue(string fieldValue)
public SPFieldGeolocationValue(double latitude, double longitude)
public SPFieldGeolocationValue(double latitude, double longitude, double altitude, double measure)

```

 **パラメーター**
  
    
    

-  _fieldValue_ は次の Well-Known Text (WKT) 形式のいずれかで表される文字列です。
    
  - "Point( _longitude_ _latitude_)"。 _longitude_ と _latitude_ は 1 つまたは複数の数字の文字列です。オプションでピリオドを 1 つ含めることができます (ピリオドは小数点として解釈されます)。また、オプションで、先頭をハイフンにできます (マイナス記号として解釈されます)。
    
  
  - "Point( _longitude_ _latitude_ _altitude_ _measure_)"。 _longitude_、 _latitude_、 _altitude_、および  _measure_ は、1 つまたは複数の数字の文字列です。オプションでピリオドを 1 つ含めることができます (ピリオドは小数点として解釈されます)。また、オプションで、先頭をハイフンにできます (マイナス記号として解釈されます)。
    
  
-  _latitude_ は緯度で、-90.0 ～ 90.0 である必要があります。
    
  
-  _longitude_ は経度で、-180.0 ～ 180.0 である必要があります。
    
  
-  _altitude_ は高度です。
    
  
-  _measure_ は場所についての代替の指定内容です。詳細については、このセクションで後述する **Measure** プロパティを参照してください。
    
  

#### メソッド

 **ToString**
  
    
    
このオーバーライドは、 **Altitude** または **Measure** プロパティに非 Null 値が指定されているかどうかに基づいて、次のいずれかを返します。
  
    
    

- Altitude にも Measure にも非 Null 値が指定されていない場合:
    
    "Point( _longitude_ _latitude_)"。 _longitude_ と _latitude_ は 1 つまたは複数の数字の文字列です。オプションでピリオドを 1 つ含めることができます (ピリオドは小数点として解釈されます)。また、オプションで、先頭をハイフンにできます (マイナス記号として解釈されます)。
    
  
- その他の場合 ( **Altitude** または **Measure** の少なくとも 1 つに非 Null 値が指定されている場合):
    
    "Point(longitude latitude altitude measure)"。 _longitude_、 _latitude_、 _altitude_、および  _measure_ は 1 つまたは複数の数字の文字列です。オプションでピリオドを 1 つ含めることができます (ピリオドは小数点として解釈されます)。また、オプションで、先頭をハイフンにできます (マイナス記号として解釈されます)。 **Altitude** または **Measure** のいずれかに非 Null 値が指定されていない場合は、 **WellKnownText** プロパティの値に "0" としてレポートされますが、その逆は成立しません。 **Altitude** または **Measure** のいずれかが "0" であるとレポートされても、非 Null 値が指定されなかったためなのか "0" が指定されたためなのかわからないからです。
    
  



```cs

public override string ToString()
```

 **ToWellKnownText**
  
    
    
 **ToString** をラップします。
  
    
    



```cs
public string ToWellKnownText()
```


#### プロパティ

 **Altitude**
  
    
    
場所の高度を取得または設定します。このプロパティの使用はオプションです。想定される測定単位 (メートルなど) およびゼロ点 (海抜、地心など) はユーザー定義です。
  
    
    



```cs
public double Altitude
```

 **Latitude**
  
    
    
場所の緯度を取得または設定します。
  
    
    



```cs
public double Latitude
```

値は -90.0 ～ 90.0 である必要があります。
  
    
    
 **Longitude**
  
    
    
場所の経度を取得または設定します。
  
    
    



```cs
public double Longitude
```

値は -180.0 ～ 180.0 である必要があります。
  
    
    
 **Measure**
  
    
    
場所について、ユーザー定義の代替の指定内容を取得または設定します。たとえば、場所がマイルストーン マーカーの付いた幹線道路にある場合、このプロパティはその場所に最も近いマイルストーンの数を保持するのに使用できます。場所が番号で識別されるキャンプ場を持つ公共のキャンプ エリアにある場合、このプロパティは最も近いキャンプ場の数を保持するのに使用できます。プロパティの意味論はすべてユーザー定義であり、その使用は任意です。
  
    
    



```cs
public double Measure
```


### SPFieldType 列挙

次の新しい値がこの列挙に追加されました。
  
    
    

```cs
Geolocation
```


### SPPhoneNotificationContent クラス

電話通知のコンテンツを表すクラスのための基本クラスです。派生クラスは、コンテンツ保持のため 1 つ以上のフィールドまたはプロパティを宣言し、コンテンツをバイト配列に変換するため **PreparePayload** メソッドを実装する必要があります。
  
    
    

```cs
public abstract class SPPhoneNotificationContent
```


#### メソッド

 **PreparePayload**
  
    
    
派生クラスで実装される場合は、コンテンツを、回線を通じて通知サービスに送られるバイト配列に変換します。既定の実装がないため、派生クラスがこのメソッドを実装する必要があります。
  
    
    



```cs
protected internal abstract byte[] PreparePayload();
```


#### プロパティ

 **NotificationType** (読み取り専用)
  
    
    
コンテンツを表す通知の種類 (タイル、トーストなど) を取得します。
  
    
    



```cs
public SPPhoneNotificationType NotificationType

```

 **SPPhoneNotificationType** の詳細については、このドキュメントの後述する項を参照してください。
  
    
    
 **SubscriberType** (読み取り専用)
  
    
    
購読者のデバイスの種類を取得します (Windows Phone など)。
  
    
    



```cs

public SPPhoneNotificationSubscriberType SubscriberType
```

 **SPPhoneNotificationSubscriberType** の詳細については、このドキュメントの後述する項を参照してください。
  
    
    

### SPPhoneNotificationResponse クラス

通知の送信試行の結果を表します。
  
    
    

```cs
public class SPPhoneNotificationResponse
```


#### メソッド

 **Create**
  
    
    
 **SPPhoneNotificationResponse** オブジェクトを作成します。
  
    
    



```cs
public static SPPhoneNotificationResponse
Create(SPPhoneNotificationSubscriberType subscriberType, 
SPPhoneNotificationType notificationType, HttpWebResponse response)
```

 **パラメーター**
  
    
    

-  _subscriberType_ は Windows Phone 7.5 などのデバイスです。
    
  
-  _notificationType_ は通知の種類 (トースト、タイルなど) です。
    
  
-  _response_ はサーバーで生成された HTTP 応答オブジェクトです。
    
  
 **SPPhoneNotificationSubscriberType** および **SPPhoneNotificationType** の詳細については、このドキュメントの後述する項を参照してください。
  
    
    

#### プロパティ

 **NotificationType** (読み取り専用)
  
    
    
通知の種類 (トースト、タイルなど) を取得します。
  
    
    



```cs

public SPPhoneNotificationType NotificationType
```

SPPhoneNotificationType の詳細については、このドキュメントの後述する項を参照してください。
  
    
    
 **ServiceToken** (読み取り専用)
  
    
    
通知で使用された通知サービスのトークンを取得します。
  
    
    



```cs
public string ServiceToken
```

 **StatusCode** (読み取り専用)
  
    
    
HTTP ステータス コードを取得します。 **HttpStatusCode** 値の文字列バージョンです。
  
    
    



```cs
public string StatusCode
```

 **SubscriberType**
  
    
    
通知の送信先のデバイスの種類を取得または設定します。
  
    
    



```cs
public SPPhoneNotificationSubscriberType SubscriberType
```

 **SPPhoneNotificationSubscriberType** の詳細については、このドキュメントの後述する項を参照してください。
  
    
    
 **TimeStamp** (読み取り専用)
  
    
    
通知の UTC 時間です。
  
    
    



```cs
public DateTime Timestamp
```


### SPPhoneNotificationSubscriber クラス

サーバー側 SharePoint アプリケーションによって発行される通知の購読者を表すクラスのための基本クラスです。
  
    
    

```cs
public abstract class SPPhoneNotificationSubscriber
```


#### メソッド

Notify
  
    
    
エラー チェックを実行したうえで、指定された通知コンテンツを購読者に送信します。
  
    
    



```cs
public SPPhoneNotificationResponse Notify(SPPhoneNotificationContent notificationContent)
```

 **パラメーター**
  
    
    
 _notificationContent_ は通知を起動したイベントに関する情報です。
  
    
    
このメソッドはオーバーライドできません。抽象メソッド **NotifyInternal** をラップし、 **NotifyInternal** が呼び出されると特定のエラー チェックが実行されるようにします。
  
    
    
 **SPPhoneNotificationContent** クラスと **SPPhoneNotificationResponse** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    
 **NotifyInternal**
  
    
    
派生クラスでオーバーライドされる場合は、指定された通知コンテンツを購読者に送信します。
  
    
    



```cs
protected abstract SPPhoneNotificationResponse NotifyInternal(SPPhoneNotificationContent notificationContent);
```

 **パラメーター**
  
    
    
 _notificationContent_ は通知を起動したイベントに関する情報です。
  
    
    
 **SPPhoneNotificationContent** クラスと **SPPhoneNotificationResponse** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    
 **ToString**
  
    
    
オブジェクトの選択されたプロパティを文字列として返します。
  
    
    



```cs
public override string ToString()
```

既定の実装には **ParentWeb**、 **ApplicationTag**、および **DeviceAppInstanceId** プロパティが含まれます。
  
    
    
Update
  
    
    
(変更された可能性のある) **SPPhoneNotificationSubscriber** オブジェクトを Web サイトの購読者ストアに保存します。
  
    
    



```cs
public void Update()
```

 **ValidateSubscriberProperties**
  
    
    
派生クラスで実装される場合は、オブジェクトの選択されたプロパティを検証します。
  
    
    



```cs
protected abstract void ValidateSubscriberProperties();
```


#### プロパティ

 **CustomArgs**
  
    
    
通知購読の状態を表すユーザー設定引数の文字列を取得または設定します。この文字列は、さまざまな種類の通知の通知購読者を区別するためのアプリケーション ロジックで使用することができます。
  
    
    



```cs
public string CustomArgs
```

 **DeviceAppInstanceId** (読み取り専用)
  
    
    
電話またはその他のモバイル デバイス上のアプリケーションの特定のインスタンスの ID を取得します。
  
    
    



```cs
public Guid DeviceAppInstanceId
```

 **LastModifiedTimeStamp** (読み取り専用)
  
    
    
購読者が最後に変更された日時を取得します。
  
    
    



```cs
public DateTime LastModifiedTimeStamp
```

 **RegistrationTimeStamp** (読み取り専用)
  
    
    
購読者が通知に登録した日時を取得します。
  
    
    



```cs
public DateTime RegistrationTimeStamp
```

 **ServiceToken**
  
    
    
チャネル URI など、通知サービスで必要な配信チャネル情報を取得または設定します。
  
    
    



```cs
public string ServiceToken
```

 **SubscriberType** (読み取り専用)
  
    
    
Windows Phone 7 など、デバイスの種類を取得します。
  
    
    



```cs
public SPPhoneNotificationSubscriberType SubscriberType
```

 **SPPhoneNotificationSubscriberType** クラスの詳細については、このドキュメントの後述する項を参照してください。
  
    
    
 **User** (読み取り専用)
  
    
    
通知に登録したユーザーを取得します。
  
    
    



```cs
public SPUser User
```


### SPPhoneNotificationSubscriberCollection クラス

通知購読者のコレクションです。コレクション オブジェクトは **Int32** インデクサーを使用します。
  
    
    

```cs
public sealed class SPPhoneNotificationSubscriberCollection : SPBaseCollection
```


#### プロパティ

 **Count**
  
    
    
コレクション内のアイテムの数を取得します。
  
    
    



```cs
public override int Count
```


### SPPhoneNotificationSubscriberType 列挙

通知の受け取りが可能なデバイスの種類を指定します。
  
    
    


|**通知**|**デバイス**|
|:-----|:-----|
|||
|**WP7** <br/> |Windows Phone 7.5  <br/> |
|**Custom** <br/> |Windows Phone 7.5 以外の任意のデバイス  <br/> |
   

### SPPhoneNotificationType 列挙

通知の種類を指定します。
  
    
    


|||
|:-----|:-----|
|**None** <br/> ||
|**Tile** <br/> ||
|**Toast** <br/> ||
|**Raw** <br/> ||
   

### SPWeb クラス

次のメンバーがこのクラスに追加されました。
  
    
    

#### メソッド

 **DoesPhoneNotificationSubscriberExist**
  
    
    
現在のユーザーが、指定されたアプリケーションの指定されたインスタンスの購読者であるかどうかを示す値を取得します。
  
    
    



```cs
public bool DoesPhoneNotificationSubscriberExist(Guid deviceAppInstanceId)
```

 **GetPhoneNotificationSubscriber**
  
    
    
Web サイトの通知購読者ストア リストから、指定されたアプリケーションおよび電話 ID を持つ通知購読者を取得します。
  
    
    



```cs
public SPPhoneNotificationSubscriber GetPhoneNotificationSubscriber(Guid deviceAppInstanceId)
```

 **パラメーター**
  
    
    
 _deviceAppInstanceId_ は特定の電話またはデバイス上のアプリケーション インスタンスの ID です。
  
    
    
 **SPPhoneNotificationSubscriber** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    
 **GetPhoneNotificationSubscribers** (オーバーロード)
  
    
    
Web サイトの通知購読者ストア リストから、通知購読者のコレクションを取得します。オプションで、電話アプリケーションの ID と、ユーザーまたはいくつかのユーザー設定の引数のいずれかに対してフィルタリングを実行できます。
  
    
    



```cs
public SPPhoneNotificationSubscriberCollection GetPhoneNotificationSubscribers(string customArgs)
```


> **メモ**
> クライアント オブジェクト モデルの名前は **GetPhoneNotificationSubscribersByArgs** です。
  
    
    




```cs
public SPPhoneNotificationSubscriberCollection GetPhoneNotificationSubscribers(string user)

```


> **メモ**
> クライアント オブジェクト モデルの名前は **GetPhoneNotificationSubscribersByUser** です。
  
    
    

 **パラメーター**
  
    
    

-  _customArgs_ は一部の通知対応アプリケーションで使用可能な追加のユーザー設定情報です。
    
  
-  _user_ は通知に登録したユーザーです。
    
  
 **SPPhoneNotificationSubscriberCollection** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    
 **RegisterPhoneNotificationSubscriber**
  
    
    
通知を受信できるよう電話に電話アプリケーションを登録します。
  
    
    



```cs

public SPPhoneNotificationSubscriber RegisterPhoneNotificationSubscriber(SPPhoneNotificationSubscriberType subscriberType, Guid deviceAppInstanceId, string serviceToken)
```

 **パラメーター**
  
    
    

-  _subscriberType_ は Windows Phone 7 などのデバイスの種類です。
    
  
-  _deviceAppInstanceId_ は特定の電話またはデバイス上のアプリケーション インスタンスの ID です。
    
  
-  _serviceToken_ は購読者に通知を送信する通知サービスで使用されるトークンです。
    
  
 **SPPhoneNotificationSubscriberType** の詳細については、このドキュメントの前述の項を参照してください。
  
    
    
 **UnregisterPhoneNotificationSubscriber**
  
    
    
電話上の電話アプリケーションの登録を解除し、通知を受信しないようにします。
  
    
    



```cs
public void UnregisterPhoneNotificationSubscriber(Guid deviceAppInstanceId)
```

 **パラメーター**
  
    
    
 _deviceAppInstanceId_ は特定の電話またはデバイス上のアプリケーション インスタンスの ID です。
  
    
    

#### プロパティ

 **PhoneNotificationSubscribers** (読み取り専用)
  
    
    
Web サイトの購読者ストアに存在するすべての電話通知購読者のコレクションを取得します。
  
    
    



```cs
public SPPhoneNotificationSubscriberCollection PhoneNotificationSubscribers
```

 **SPPhoneNotificationSubscriberCollection** クラスの詳細については、このドキュメントの前述の項を参照してください。
  
    
    

### WP7NotificationTileContent クラス

タイル通知のコンテンツを表します。
  
    
    

```cs
public sealed class WP7NotificationTileContent : SPPhoneNotificationContent
```


#### コンストラクター

WP7NotificationTileContent クラスの新しいインスタンスを初期化します。
  
    
    

```cs
public WP7NotificationTileContent()
```


#### メソッド

 **PreparePayload**
  
    
    
コンテンツを、回線を通じて通知サービスに送られる **Byte** 配列に変更します。
  
    
    



```cs
protected internal override byte[] PreparePayload();
```


#### プロパティ

 **Count**
  
    
    
通知のカウントを取得または設定します。-1 ～ 99 に設定する必要があります (-1 と 99 を含む)。
  
    
    



```cs
public int Count
```

このプロパティを -1 に設定すると、タイル上のカウントが変更されません。
  
    
    
 **Title**
  
    
    
タイル通知のタイトルを取得または設定します。
  
    
    



```cs
public string Title
```

 **BackgroundImagePath**
  
    
    
タイルの背景画像へのパスを取得または設定します。
  
    
    



```cs
public string BackgroundImagePath
```

 **BackBackgroundImagePath**
  
    
    
反転タイルの裏面の背景画像を取得または設定します。
  
    
    



```cs
public string BackBackgroundImagePath
```

 **BackContent**
  
    
    
反転タイルの裏面のコンテンツを取得または設定します。
  
    
    



```cs
public string BackContent
```

 **BackTitle**
  
    
    
反転タイルの裏面に表示されるタイトルを取得または設定します。
  
    
    



```cs
public string BackTitle
```

 **TileId**
  
    
    
タイルの ID を取得または設定します。
  
    
    



```cs
public string TileId
```


### WP7NotificationToastContent クラス

トースト通知のコンテンツを表します。
  
    
    

```cs
public sealed class WP7NotificationToastContent : SPPhoneNotificationContent
```


#### コンストラクター

WP7NotificationToastContent クラスの新しいインスタンスを初期化します。
  
    
    

```cs
public WP7NotificationToastContent()
```


#### メソッド

 **PreparePayload**
  
    
    
コンテンツを、回線を通じて通知サービスに送られる **Byte** 配列に変更します。
  
    
    



```cs
protected internal override byte[] PreparePayload();
```


#### プロパティ

 **Message**
  
    
    
トースト通知のメッセージを取得または設定します。
  
    
    



```cs
public string Message
```

 **Title**
  
    
    
トースト通知のタイトルを取得または設定します。
  
    
    



```cs
public string Title
```

 **Param**
  
    
    
ユーザーがトースト通知に応答する場合に受信アプリケーションに渡されるユーザー設定データを取得または設定します。
  
    
    



```cs
public string Param
```

このプロパティを使用して、URL や名前と値の組のセットなどの情報を受信アプリケーションに渡すことができます。
  
    
    

### WP7NotificationRawContent クラス

Raw 通知のコンテンツを表します。
  
    
    

```cs
public sealed class WP7NotificationRawContent : SPPhoneNotificationContent
```


#### コンストラクター

WP7NotificationRawContent クラスの新しいインスタンスを初期化します。
  
    
    

```cs
public WP7NotificationRawContent()
```


#### メソッド

 **PreparePayload**
  
    
    
コンテンツを、回線を通じて通知サービスに送られるバイト配列に変更します。
  
    
    



```cs
protected internal override byte[] PreparePayload();
```


#### プロパティ

 **Message**
  
    
    
Raw 通知のメッセージを取得または設定します。
  
    
    



```cs
public string Message
```


### WP7PhoneNotificationResponse クラス

Windows Phone 7 購読者への通知送信の試行結果を表します。
  
    
    

```cs
public WP7PhoneNotificationResponse(SPPhoneNotificationType notificationType, HttpWebResponse response)
```

 **パラメーター**
  
    
    

-  _notificationType_ は通知の種類 (トースト、タイルなど) です。
    
  
-  _response_ はサーバーで生成された HTTP 応答オブジェクトです。
    
  
 **SPPhoneNotificationType** の詳細については、このドキュメントの前述の項を参照してください。
  
    
    

#### プロパティ

 **NotificationStatus** (読み取り専用)
  
    
    
成功、失敗などの通知ステータスを取得します。
  
    
    



```cs
public string NotificationStatus
```

 **DeviceConnectionStatus** (読み取り専用)
  
    
    
通知時点のデバイスのステータスを取得します。
  
    
    



```cs
public string DeviceConnectionStatus
```

 **SubscriptionStatus** (読み取り専用)
  
    
    
通知時点のデバイスの購読ステータスです。
  
    
    



```cs
public string SubscriptionStatus
```

 **MessageId** (読み取り専用)
  
    
    
通知で送信されたメッセージの ID を取得します。
  
    
    



```
public string MessageId
```


## その他の技術情報
<a name="SP15MobileOM_addlresources"> </a>


-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [[方法] Windows Phone 用 SharePoint 2013 アプリでプッシュ型通知を構成および使用する](how-to-configure-and-use-push-notifications-in-sharepoint-2013-apps-for-windows.md)
    
  
-  [SharePoint 2013 でロケーションとマップ機能を組み込む](integrating-location-and-map-functionality-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 モバイル クライアント認証オブジェクト モデルの概要](overview-of-the-sharepoint-2013-mobile-client-authentication-object-model.md)
    
  

