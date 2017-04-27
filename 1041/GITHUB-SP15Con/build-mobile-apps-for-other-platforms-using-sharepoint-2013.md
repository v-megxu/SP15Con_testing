---
title: SharePoint 2013 を使用して他のプラットフォーム用のモバイル アプリを構築する
ms.prod: SHAREPOINT
ms.assetid: 017df869-44fb-4ffe-82fb-4654e01329ad
---


# SharePoint 2013 を使用して他のプラットフォーム用のモバイル アプリを構築する
Representational State Transfer (REST) を使用して、任意のプラットフォーム向けの SharePoint 2013 モバイル アプリを作成する方法を説明します。
近年、モバイル デバイスの性能と使いやすさがますます高まっています。業務に必要な情報やアプリケーションへのアクセスには、ノート PC、ネットブック、タブレット PC、および携帯電話が使われています。また、モバイル デバイス用のアプリケーション開発も、従来より簡単になっています。こうしたことから、ビジネス プロセスにクライアント アプリケーションを統合するビジネス シナリオの要求がますます増えています。この記事では、SharePoint 2013 にモバイル クライアント アプリを統合する方法を説明します。モバイル アプリを作成して、どんな場所からでも SharePoint コンテンツを参照し、SharePoint リストおよびライブラリに接続してデータにアクセスできます。
  
    
    

SharePoint 2013 と対話するモバイル アプリの開発には、オープン プロトコルを使用してアクセスできる一般のサービスを使用できます。SharePoint Foundation 2010 では、クライアント オブジェクト モデルが導入されました。これにより、開発者は, .NET Framework、Microsoft Silverlight、または JavaScript から任意の Web プログラミング テクノロジを使用して、SharePoint とリモート通信ができるようになりました。SharePoint 2013 では、ちょうどクライアント オブジェクト モデルに相当する Representational State Transfer (REST) サービスを導入します。SharePoint 2013 では、クライアント オブジェクト モデルのほぼすべての API に対応する REST エンドポイントがあります。このため、開発者は、REST Web 要求をサポートするテクノロジを使用して SharePoint オブジェクト モデルとリモートで対話できます。モバイル アプリケーション開発に使用する、どんなプログラミング言語でも REST を使用できます。
SharePoint 2013 で提供される REST インターフェイスを使用すると、基本的な作成、読み取り、更新、および削除 (CRUD) の操作を実行できます。REST では、その他の SharePoint クライアント API で利用可能なすべての SharePoint エンティティおよび操作が公開されます。REST を使用する 1 つのメリットは、SharePoint 2013 ライブラリまたはクライアント アセンブリに参照を追加する必要がないことです。Web、リスト、リスト アイテムなどの SharePoint エンティティを取得したり更新したりするには、代わりに適切なエンドポイントに HTTP 要求を実行します。SharePoint 2013 REST インターフェイスとそのアーキテクチャの概要について詳しくは、「 [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)」を参照してください。
  
    
    


## SharePoint 2013 の REST エンドポイント
<a name="BuildMobileAppsInSharePoint2013ForNonWindowsPhone_REST_EndpointsInSharePoint2013"> </a>

SharePoint 2013 に組み込まれている REST 機能を使用する場合は、必要なクライアント オブジェクト モデルの API に対応する Open Data Protocol (OData) 標準を使用して REST 対応の HTTP 要求を構成できます。client.svc Web サービスは HTTP 要求を処理し、Atom または JavaScript Object Notation (JSON) の形式で適切な応答を返します。クライアント アプリケーションは、その応答を解析する必要があります。図 1 に SharePoint REST アーキテクチャの概要を示します。
  
    
    

**図 1. SharePoint REST のアーキテクチャ**

  
    
    

  
    
    
![SharePoint REST のアーキテクチャ](images/SP15Con_BuildSharePointAppsForMobileDevices_Fig2.png)
  
    
    
SharePoint 2013 REST サービスのエンドポイントは、SharePoint クライアント オブジェクト モデルの型およびメンバーに対応します。HTTP 要求を使用することによって、これらの REST エンドポイントを使って、リストやサイトなどの SharePoint 成果物に対して典型的な CRUD 操作を行うことができます。
  
    
    
一般に、以下のことが行われます。
  
    
    

- 読み取り操作を表すエンドポイントが HTTP **GET** コマンドにマップされる。
    
  
- 更新操作を表すエンドポイントが HTTP **POST** コマンドにマップされる。
    
  
- 更新または挿入操作を表すエンドポイントが HTTP **PUT** コマンドにマップされる。
    
  
使用する HTTP 要求を選択する際、次の点についても考慮する必要があります。
  
    
    

- **POST** を使用してリストやサイトなどの成果物を作成します。SharePoint 2013 REST サービスは、コレクションを表すエンドポイントにオブジェクト定義を含める **POST** コマンドの送信をサポートしています。
    
  
- **POST** 操作では、必須ではないプロパティはすべて既定値に設定されます。 **POST** 操作の一部として読み取り専用プロパティを設定すると、サービスによって例外が返されます。
    
  
- 既存の SharePoint オブジェクトを更新する場合は、 **PUT**、 **PATCH**、および **MERGE** 操作を使用します。オブジェクト プロパティ **set** 操作を表すサービス エンドポイントは、すべて **PUT** 要求と **MERGE** 要求の両方をサポートします。 **MERGE** 要求の場合、プロパティの設定は省略できます。明示的に設定しないプロパティは、現在のプロパティが保持されます。ただし、 **PUT** コマンドの場合は、プロパティを明示的に設定しないと、既定のプロパティが設定されます。さらに、HTTP **PUT** コマンドを使用したオブジェクトの更新で設定可能なプロパティをすべて設定しなかった場合には、REST サービスから例外が返されます。
    
  
- 特定のエンドポイント URL に対して HTTP の **DELETE** コマンドを実行すると、そのエンドポイントが表す SharePoint オブジェクトを削除できます。リスト、ファイル、リスト アイテムなど、再利用可能なオブジェクトについては、結果的に **Recycle** 操作になります。詳細については、「 [SharePoint 2013 REST サービスの概要](get-to-know-the-sharepoint-2013-rest-service.md)」を参照してください。
    
  

## SharePoint に対するユーザーの認証
<a name="BuildMobileAppsInSharePoint2013ForNonWindowsPhone_AuthenticatingNonWindowsAppForSharePoint"> </a>

SharePoint でモバイル アプリを認証するのに、MS-OFBA プロトコルを使用できます。詳細については、「 [[MS-OFBA]: Office フォーム ベースの認証プロトコル仕様](http://msdn.microsoft.com/library/30c7bbe9-b284-421f-b866-4e7ed4866027%28Office.15%29.aspx)」を参照してください。プロトコル クライアントは、Cookie を格納および送信するように構成されます。プロトコル クライアントは、リモート プロトコル サーバーを信頼し、1 つ以上の HTTP Cookie としてユーザーの ID を設定します。ユーザーの ID が確立された後、クライアントは以降の各 HHT 要求とともに各 Cookie を送信します。
  
    
    
ユーザーが SharePoint 2013 にサインインするときに、ユーザーのトークンが検証され、ユーザーはそのトークンを使用して SharePoint にサインインします。ユーザーのトークンは、ID プロバイダーによって発行されるセキュリティ トークンです。SharePoint 2013 でサポートされる認証には、いくつか種類があります。詳細については、「 [SharePoint 2013 での認証、承認、およびセキュリティ](authentication-authorization-and-security-in-sharepoint-2013.md)」を参照してください。ユーザーの認証に、REST インターフェイスを使用できます。承認プロセスは、認証済みの承認対象 (アプリ、またはアプリが動作を代理するユーザー) が特定の操作を行う権限、または特定のリソース (たとえば、リストや SharePoint ドキュメント フォルダー) にアクセスする権限を持っているかどうかを検査します。
  
    
    
OData を使用すると、特別に構成された URL の参照によってデータベースなどのデータ ソースにアクセスできます。これにより、組織内でホストされているデータ ソースに簡単に接続したり操作したりできます。OData は HTTP、Atom、JavaScript Object Notation (JSON) を使用するプロトコルで、開発者は増加し続けるデータ ソースと対話するアプリケーションを記述できるようになります。Microsoft では、Web からアクセス可能なアプリケーションとデータ ストアとの間でデータ交換を実現する方法として、この標準の作成をサポートしています。新しい OData コネクタは、SharePoint と OData プロバイダーとの対話を実現します。詳細については、「 [Open Data Protocol](http://www.odata.org/)」を参照してください。
  
    
    
次のコードは、基本の認証またはフォーム ベース認証に REST エンドポイントを使用して、SharePoint 2013 に対してアプリを認証する方法を示しています。次のコード例は C# で記述されていますが、他の任意のプログラミング言語を使用して、プラットフォーム要件のとおりに、HTTP 要求を作成できます。
  
    
    



```cs

string SharePointUrl = "https://Target SharePoint site";

private void AuthenticateToSharePoint(object sender, RoutedEventArgs e)
{
    ODataAuthenticator odataAt = new ODataAuthenticator("<Username>", "<password>");
    odataAt.CookieCachingEnabled = true;
    odataAt.AuthenticationCompleted += new EventHandler<AuthenticationCompletedEventArgs>(odataAt_AuthenticationCompleted);
    odataAt.Authenticate(new Uri(SharePointUrl, UriKind.Absolute));
}

void odataAt_AuthenticationCompleted(object sender, AuthenticationCompletedEventArgs e)
{
    HttpWebRequest endpointRequest = (HttpWebRequest)HttpWebRequest.Create(SharePointUrl.ToString() + "/_api/web/lists");
    endpointRequest.Method = "GET";
    endpointRequest.Accept = "application/json;odata=verbose";
          endpointRequest.CookieContainer = (sender as ODataAuthenticator).CookieContainer;
    
    endpointRequest.BeginGetResponse(new AsyncCallback((IAsyncResult res) =>
    {
        HttpWebRequest webReq = res.AsyncState as HttpWebRequest;
        WebResponse response = webReq.EndGetResponse(res);

        HttpWebResponse httpResponse = response as HttpWebResponse;
        HttpStatusCode code = httpResponse.StatusCode;
        this.Dispatcher.BeginInvoke(() =>
        {
            MessageBox.Show(code.ToString());
        });
    }), endpointRequest);
}

```

エンドポイントに対して **HttpWebrequest** を認証するには、まず、 **ODataAuthenticator** クラスで SharePoint に対して認証する必要があります。 **Authenticate** メソッドを呼び出す前に、 **ODataAuthenticator** オブジェクトを **AuthenticationCompleted** イベントに登録します。
  
    
    
 **OnAuthenticationCompleted** イベント内で認証された後、 **ODataAuthenticator** オブジェクト上で **CookieContainer** プロパティを使用できます。このオブジェクトを **HttpWebRequest** オブジェクトに添付して、SharePoint に対して REST 呼び出しを認証できます。
  
    
    

## REST を使用して SharePoint リスト アイテムを操作する
<a name="BuildMobileAppsInSharePoint2013ForNonWindowsPhone_WorkingWithTheSharePointListItemUsingREST"> </a>

次の例は、リストのアイテムをすべて **取得** する方法を示しています。
  
    
    

```

url: http://site url/_api/web/lists/GetByTitle('Test')/items
method: GET
headers:
// MS-OFBA protocol returns a cookie.
  Cookie: cookie


    accept: "application/json;odata=verbose" or "application/atom+xml"

```

次の例は、特定のリスト アイテムを **取得** する方法を示しています。
  
    
    



```

url: http://site url/_api/web/lists/GetByTitle('Test')/items(item id)
method: GET
headers:
    
// MS-OFBA protocol return a cookie.
  Cookie: cookie
    accept: "application/json;odata=verbose" or "application/atom+xml"

```

次の XML は、XML コンテンツ タイプを要求したときに返されるリスト アイテム プロパティの例を示しています。
  
    
    



```XML

<content type="application/xml">
        <m:properties>
        <d:FileSystemObjectType m:type="Edm.Int32">0</d:FileSystemObjectType>
        <d:Id m:type="Edm.Int32">1</d:Id>
        <d:ID m:type="Edm.Int32">1</d:ID>
        <d:ContentTypeId>0x010049564F321A0F0543BA8C6303316C8C0F</d:ContentTypeId>
        <d:Title>an item</d:Title>
        <d:Modified m:type="Edm.DateTime">2012-07-24T22:47:26Z</d:Modified>
        <d:Created m:type="Edm.DateTime">2012-07-24T22:47:26Z</d:Created>
        <d:AuthorId m:type="Edm.Int32">11</d:AuthorId>
        <d:EditorId m:type="Edm.Int32">11</d:EditorId>
        <d:OData__UIVersionString>1.0</d:OData__UIVersionString>
        <d:Attachments m:type="Edm.Boolean">false</d:Attachments>
        <d:GUID m:type="Edm.Guid">eb6850c5-9a30-4636-b282-234eda8b1057</d:GUID>
    </m:properties>
</content>
```

次の例は、リスト アイテムを **作成** する方法を示しています。
  
    
    

> **メモ**
> この操作を実行するには、リストの **ListItemEntityTypeFullName** プロパティを知っていて、それを HTTP 要求本文の **type** の値として渡す必要があります。
  
    
    




```

url: http://site url/_api/web/lists/GetByTitle('Test')/items
method: POST
body: { '__metadata': { 'type': 'SP.Data.TestListItem' }, 'Title': 'Test'}
headers:
    
// MS-OFBA protocol returns a cookie.
  Cookie: cookie
     X-RequestDigest = form digest value
    accept: "application/json;odata=verbose"
    content-type: "application/json;odata=verbose"
    content-length:length of post body
```

次の例は、リスト アイテムを **更新** する方法を示しています。
  
    
    

> **メモ**
> この操作を実行するには、リストの **ListItemEntityTypeFullName** プロパティを知っていて、それを HTTP 要求本文の **type** の値として渡す必要があります。
  
    
    




```

url: http://site url/_api/web/lists/GetByTitle('Test')/items(item id)
method: POST
body: { '__metadata': { 'type': 'SP.Data.TestListItem' }, 'Title': 'TestUpdated'}
headers:
// MS-OFBA protocol returns a cookie.
  Cookie: cookie
     X-RequestDigest = form digest value
    "IF-MATCH": etag or "*"
    "X-HTTP-Method":"MERGE",
    accept: "application/json;odata=verbose"
    content-type: "application/json;odata=verbose"
    content-length:length of post body
```

次の例は、リスト アイテムを **削除** する方法を示しています。
  
    
    



```

url: http://site url/_api/web/lists/GetByTitle('Test')/items(item id)
method: POST
headers:
// MS-OFBA protocol returns a cookie.
  Cookie: cookie
     X-RequestDigest = form digest value
    "IF-MATCH": etag or "*"
    "X-HTTP-Method":"DELETE"

```

詳細については、「 [SharePoint 2013 REST エンドポイントを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/e3000415-50a0-426e-b304-b7de18f2f7d9%28Office.15%29.aspx)」を参照してください。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [SharePoint 2013 REST サービスを使用する](e1ff2979-1c16-4cb0-a57e-9168dfe20a7c.md)
    
  
-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  
-  [SharePoint 2013 REST サービスの概要](get-to-know-the-sharepoint-2013-rest-service.md)
    
  
-  [SharePoint 2013 で C# および JavaScript を使用して REST 呼び出しを実行する](http://www.microsoft.com/resources/msdn/ja-jp/office/media/video/video.mdl?cid=sdc&amp;from=mscomsdc&amp;videoid=4e4cc094-ff69-405b-852f-2ac7c41293c5)
    
  
-  [SharePoint 2013 で C# および JavaScript を使用して REST 呼び出しを実行するデモ](http://www.microsoft.com/resources/msdn/ja-jp/office/media/video/video.mdl?cid=sdc&amp;from=mscomsdc&amp;videoid=b1e7c9c5-0f62-4a78-bb7b-8e283c86145c)
    
  
-  [Open Data Protocol](http://www.odata.org//)
    
  
-  [SharePoint アドインの承認と認証](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/ja-jp/download/details.aspx?id=35471)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 8](http://www.microsoft.com/ja-jp/download/details.aspx?id=36818)
    
  

