---
title: SharePoint 2013 での認証、承認、およびセキュリティ
ms.prod: SHAREPOINT
ms.assetid: 8734790c-eb75-4d78-9604-7cc23b33b693
---


# SharePoint 2013 での認証、承認、およびセキュリティ

## SharePoint 2013 の認証、承認、およびセキュリティの新機能
<a name="SP15_AuthenticationAuthorizationSecurity_WhatsNew"> </a>

以下に、SharePoint 2013 に追加された強化機能をいくつか挙げます。 
  
    
    

- ユーザー サインイン
    
  - SharePoint 2013は、クレーム認証とクラシック認証の両方の認証モードを引き続きサポートします。クレーム認証は SharePoint 2013の既定の認証オプションです。クラシックモード認証は使用されなくなり、Windows PowerShell の使用によってのみ管理できます。SharePoint 2013の多くの機能でクレームモードを使用する必要があります。 
    
  
  - SharePoint 2010 の **MigrateUsers** メソッドは使用されなくなり、アカウントを移行するための正しい手段ではなくなりました。アカウントを移行するには、 `Convert-SPWebApplication` という Windows PowerShell の新しいコマンドレットを使用します。詳細については、「 [SharePoint 2013 でクラシックモードからクレームベース認証に移行する](http://technet.microsoft.com/ja-jp/library/gg251985.aspx)」を参照してください。
    
  
  - クレーム プロバイダーを登録するための要件は除外されています。ただし、クレームの種類を事前に設定しておく必要があります。クレームの種類の文字を選択でき、クレームの種類の順序に制約はありません。
    
  
  - SharePoint 2013は、Windows Server AppFabric キャッシュ機能を使用して、新しい分散キャッシュ サービスの **FedAuth** クッキーを追跡します。
    
  
  - 認証の問題のトラブルシューティングに役立つように、以前よりもはるかに多くのログが提供されます。 
    
  
- サービスおよびアプリケーションの認証
    
  - SharePoint 2013では、SharePoint 用のアプリケーションを作成できるようになりました。SharePoint アドインには独自の ID があり、アプリ プリンシパルというセキュリティ プリンシパルと関連付けられています。ユーザーやグループと同様に、アプリ プリンシパルにも特定のアクセス許可および権限があります。 
    
  
  - SharePoint 2013では、サーバー間のセキュリティ トークン サービス (STS) がサーバー間認証用のアクセス トークンを提供します。サーバー間の STS は、一時アクセス トークンを有効にして、Exchange Server 2013および Microsoft Lync 2013 などの他のアプリケーション サービスや、SharePoint 2013用アプリケーションへのアクセスを可能にします。
    
  

## 認証および承認
<a name="SP15_AuthenticationAuthorizationSecurity_AuthenticationAndAuthorization"> </a>

SharePoint 2013では、Web サイト、リスト、リスト フォルダーやライブラリ フォルダー、およびアイテムのレベルでユーザー アクセスのセキュリティがサポートされます。セキュリティ管理はすべてのレベルでロールに基づいており、SharePoint 2013 プラットフォーム全体に対して一貫したセキュリティ管理を提供します。オブジェクトに対する権限の割り当てには、一貫性のあるロール ベースのユーザー インターフェイスとオブジェクト モデルが使用されます。結果として、リスト レベル、フォルダー レベル、またはアイテム レ ベルのセキュリティに、Web サイト レベルのセキュリティと同じユーザー モデルが実装され、Web サイト全体でのユーザー権限とグループ権限の管理が容易になります。また、SharePoint 2013では、リスト ライブラリとドキュメント ライブラリに含まれるフォルダーとアイテムに対する一意な権限もサポートされます。
  
    
    

> **メモ**
> SharePoint アドインの詳細については、「 [SharePoint アドインの承認と認証](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx)」を参照してください。 
  
    
    

承認とは、あるオブジェクトに対して特定のアクションを実行できるどのユーザーを決定することによって SharePoint 2013が Web サイト、リスト、フォルダー、またはアイテムのセキュリティを保護するプロセスです。承認プロセスでは、ユーザーが認証済みであることを前提としています。認証とは、SharePoint 2013が現在のユーザーを識別するプロセスです。SharePoint 2013では、認証や ID 管理に独自のシステムを実装しておらず、代わりに外部システム (Windows 認証または Windows 以外の認証) に依存しています。
  
    
    
SharePoint 2013では、以下の種類の認証をサポートしています。
  
    
    

- **Windows:** 基本、ダイジェスト、証明書、NTLM (Windows NT LAN Manager)、および Kerberos を含めたすべての Internet Information Services (IIS) と Windows 認証の統合オプションがサポートされています。Windows 認証では、IIS を使用して SharePoint 2013の認証を実行できます。
    
    Windows クレーム モードを使用した SharePoint へのサインインについては、「 [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)」を参照してください。
    
    > **重要**
      >  偽装の中断の詳細については、「 [呼び出し元ユーザーの偽装を一時中断しないようにする](http://msdn.microsoft.com/ja-jp/library/ff407852.aspx)」を参照してください。 
- **ASP.NET フォーム:** プラグ可能な ASP.NET フォーム ベースの認証システムを使用する、Windows 以外の ID 管理システムがサポートされています。このモードでは、SharePoint 2013はライトウェイト ディレクトリ アクセス プロトコル (LDAP)、ライトウェイト データベース ID 管理システムなど、外部に定義されたグループまたはロールを含めたさまざまな ID 管理システムを操作できます。フォーム認証では、ASP.NET を使用して SharePoint 2013の認証を実行できます。多くの場合、ログオン ページにリダイレクトすることになります。SharePoint 2013では、ASP.NET フォームはクレーム認証でのみサポートされています。フォーム プロバイダーは、クレーム用に構成された Web アプリケーション内に登録する必要があります。
    
    ASP.NET メンバーシップおよびロール パッシブ サインインを使用した SharePoint へのサインインについては、「 [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)」を参照してください。
    
  

> **メモ**
> SharePoint 2013では、大文字と小文字を区別するメンバーシップ プロバイダーの操作をサポートしておらず、メンバーシップ プロバイダーに関係なく、データベース内のすべてのユーザーに対して大文字と小文字を区別しない SQL ストレージが使用されます。 
  
    
    


## クレーム ベースの ID および認証
<a name="SP15_AuthenticationAuthorizationSecurity_ClaimsBasedIdentity"> </a>

クレームベース ID は SharePoint 2013の ID モデルで、Windows ベース システムと Windows 以外のベース システムにまたがるユーザーの認証、複数種類の認証方式、リアルタイム認証の強化、プリンシパルの種類の拡充、アプリケーション間でのユーザー ID 委任など、さまざまな機能が含まれます。
  
    
    
ユーザーが SharePoint 2013にサインインするときに、ユーザーのトークンが検証され、そのトークンを使用して SharePoint にサインインします。ユーザーのトークンは、クレーム プロバイダーによって発行されるセキュリティ トークンです。サポートされているサインインあるいはアクセス モードは以下のとおりです。
  
    
    

- Windows クレームモードでのサインイン (既定)
    
  
- SAML パッシブ サインイン モード
    
  
- ASP.NET メンバーシップおよびロール パッシブ サインイン
    
  
- Windows クラシックモード サインイン (このリリースでは非推奨)
    
  

> **メモ**
> SharePoint へのサインインおよびさまざまなサインイン モードの詳細については、「 [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)」を参照してください。 
  
    
    

クレームを処理できるアプリケーションを構築する場合、ユーザーはアプリケーションに一連のクレームとして ID を提示します。クレームはそれぞれ、ユーザー名、電子メール アドレスなどです。このしくみの基本にあるのは、何らかの外部 ID システムが構成され、そこからアプリケーションに対して、ユーザーに関するすべての必要な情報 (および、受け取った ID データが信頼できる提供元から得られたものであることを示す暗号化済みの証拠) が個々の要求と共に提供されるという考え方です。
  
    
    
このモデルでは、シングル サインオンの実現が非常に容易になり、ユーザーのアプリケーションは以下の点を考慮する必要がなくなります。
  
    
    

- ユーザーの認証
    
  
- ユーザー アカウントおよびパスワードの保存
    
  
- ユーザー ID の詳細を検索するために企業のディレクトリを呼び出す
    
  
- その他のプラットフォームあるいは企業の ID システムとの統合
    
  
このモデルでは、アプリケーションはユーザーによって提供されたクレームに基づいて、ID に関連する判断をします。これには、ユーザーの名前による簡単なアプリケーションの個人用設定から、アプリケーションのより高度な機能およびリソースにアクセスするためのユーザー認証に至るまで、幅広い用途が含まれます。
  
    
    

> **メモ**
> クレーム ベースの ID とクレーム プロバイダーの詳細については、「 [SharePoint 2013 のクレームベース ID と概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)」と「 [SharePoint 2013 のクレーム プロバイダー](claims-provider-in-sharepoint-2013.md)」を参照してください。 
  
    
    


## フォーム ベース認証
<a name="SP15_AuthenticationAuthorizationSecurity_FormsBasedAuthentication"> </a>

フォームベースの認証では、メンバーシップ プロバイダーとロール マネージャーを実装することによって SharePoint 2013でのカスタム ID 管理を提供します。メンバーシップ プロバイダーは個別のユーザーを識別および認証するためのインターフェイスを定義し、ロール マネージャーは個別のユーザーを論理グループまたはロールにグループ化するためのインターフェイスを定義します。SharePoint 2013 では、メンバーシップ プロバイダーが、必須の  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) メソッドを実装する必要があります。ユーザー名が指定されると、ロール プロバイダー システムは、そのユーザーが属するロールのリストを返します。
  
    
    
メンバーシップ プロバイダーは、 [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx) メソッドを使用して資格情報を検証します (SharePoint 2013では必須)。ただし、実際のユーザー トークンは、セキュリティ トークン サービス (STS) によって作成されます。STS は、メンバーシップ プロバイダーによって検証されたユーザー名、およびメンバーシップ プロバイダーによって提供されるユーザー名に関連付けられている一連のグループ メンバーシップからユーザー トークンを作成します。
  
    
    

> **メモ**
> STS の詳細については、「 [SharePoint 2013 のクレームベース ID と概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)」を参照してください。 
  
    
    

ロール マネージャーはオプションです。カスタムの認証システムがグループをサポートしない場合、ロール マネージャーは不要です。SharePoint 2013では、URL ゾーン ( [SPUrlZone](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPUrlZone.aspx) ) ごとにメンバーシップ プロバイダーとロール マネージャーを 1 つずつサポートします。ASP.NET フォームのロールには、権限の継承は関連付けられていません。代わりに、SharePoint 2013では、そのポリシーと承認によって権限をフォームのロールに割り当てます。SharePoint 2013では、フォーム ベースの認証はクレーム ベース ID モデルに統合されています。追加拡張によって URL ゾーンごとに 1 つのロール プロバイダーという制限を回避する必要がある場合は、クレーム プロバイダーを利用できます。
  
    
    

> **メモ**
> クレーム ベースの ID とクレーム プロバイダーの詳細については、「 [SharePoint 2013 のクレームベース ID と概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)」と「 [SharePoint 2013 のクレーム プロバイダー](claims-provider-in-sharepoint-2013.md)」を参照してください。 
  
    
    

ASP.NET メンバーシップおよびロール パッシブ サインインでは、クライアントを、ASP.NET ログイン コントロールがホストされている Web ページにリダイレクトすることによってサインインが行われます。ユーザー ID を示す ID オブジェクトが作成されたら、そのオブジェクトは、SharePoint 2013でユーザーのクレームベースの表現を表す  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) オブジェクトに変換されます。
  
    
    

> **メモ**
> SharePoint へのサインインの詳細については、「 [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)」を参照してください。 
  
    
    

SharePoint 2013では標準の ASP.NET ロール プロバイダー インターフェイスを使用して、現在のユーザーのグループ情報を収集します。認証目的としては、ロールとグループは同じものです。どちらも承認用の論理セットにユーザーをグループ化するための方法です。それぞれの ASP.NET ロールは、SharePoint 2013によってドメイン グループとして扱われます。 
  
    
    
ASP.NET によって提供されるプラグ可能な認証フレームワークについては、「ASP.NET developer documentation」を参照してください。
  
    
    

> **メモ**
> フォーム ベース認証の詳細については、「 [SharePoint 製品とテクノロジのフォーム認証 (パート 1): 概要](http://msdn.microsoft.com/library/e5efd4d7-b369-49f0-a6f7-431d21daff20%28Office.15%29.aspx)」を参照してください。 
  
    
    


## その他の技術情報
<a name="SP15_AuthenticationAuthorizationSecurity_AdditionalResources"> </a>


-  [SharePoint 2013 の認証、ユーザー、グループ、およびオブジェクト モデル](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのロール、継承、権限の昇格、およびパスワードの変更](role-inheritance-elevation-of-privilege-and-password-changes-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのクレームベース ID](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクレームベース ID と概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 での構成、管理、およびリソース](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

