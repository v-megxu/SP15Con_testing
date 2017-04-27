---
title: SharePoint 2013 でのロール、継承、権限の昇格、およびパスワードの変更
ms.prod: SHAREPOINT
ms.assetid: a72c6cad-9e3d-4d57-bf26-24cd1ad7f020
---


# SharePoint 2013 でのロール、継承、権限の昇格、およびパスワードの変更

## ロール、ロール定義、ロール割り当て
<a name="SP15_RoleInheritance_Role"> </a>

ロールは、ロール定義とロールの割り当てという 2 つの部分で構成されます。 
  
    
    
ロール定義 (アクセス許可レベル) は、ロールに関連する権限のリストです。権限は、SharePoint Web サイト内で一意に管理できます。たとえば、 **Read** ロールを持つユーザーは、Web サイトのページを参照し、リスト内のアイテムを表示できます。ユーザーのアクセス権は、権限を使用して直接管理されることはありません。すべてのユーザー権限およびグループ権限は、ロールによって管理されます。ロール定義とは、特定のオブジェクトに結び付けられた権限のコレクションです。ロール定義 ( **Full Control**、 **Read**、 **Contribute**、 **Design**、 **Limited Access** など) は、Web サイトを対象範囲とし、Web サイトのどの場所でも同じことを意味しますが、何を意味するかは同じサイト コレクション内のサイト間で異なります。親 Web サイトから権限を継承できるのと同じように、ロール定義を継承することもできます。
  
    
    
ロールの割り当ては、ロール定義、ユーザーとグループ、対象範囲間の関係です (たとえば、リスト 1 でのリーダーとリスト 2 でのリーダーは、異なるユーザーになる場合があります)。ロールの割り当てによって表される関係は、SharePoint 2013 のセキュリティ管理をロール ベースで行うためのキーとなります。すべての権限はロールによって管理されます。権限をユーザーに直接割り当てることはありません。明確で一貫性のある権限の有用なコレクション (ロール定義) を割り当てます。ロールの割り当てによってロール定義にユーザーやグループの追加または削除を行うことで、固有の権限を管理します。
  
    
    
Web サイトの管理者は、既定のロール定義をカスタマイズし、[ロールの管理] ページを使用して独自のロールを新たに作成できます。[ロールの管理] ページには、サイトで利用できるロール定義が表示されます。
  
    
    

## ロール定義の継承
<a name="SP15_RoleInheritance_RoleDefInheritance"> </a>

SharePoint 2013 は、権限の継承と同じように、ロール定義の継承をサポートします。また、ロール定義の継承を停止するには、権限の継承も停止する必要があります。
  
    
    
SharePoint の各オブジェクトには、独自の権限を設定するか、親コンテナーから権限を継承することができます。SharePoint 2013 では、オブジェクトが親の権限をすべて継承し、独自の権限の一部も保持するというような部分的な継承はサポートされません。権限は、固有の権限を設定するか、継承するかのどちらかになります。SharePoint 2013 では、指定継承はサポートされません。たとえば、オブジェクトは親コンテナーからのみ継承することができ、他のオブジェクトやコンテナーから継承することはできません。
  
    
    
Web サイトがロール定義を継承する場合、継承した Web サイトでは、ロールは読み取り専用の権限と同じように読み取り専用になります。ユーザーは、リンクを介して固有のロール定義を保持する親サイトに移動できます。すべての新しい Web サイトの既定の設定は、固有の権限を持つサイトの場合でも、親 Web サイトからロール定義を継承することです。権限が固有の場合は、継承したロール定義に戻すか、ローカル ロール定義として編集することができます。
  
    
    
Web サイトでのロール定義の継承は、以下のルールに従って権限の継承に適用されます。
  
    
    

- ロール定義も継承しない限り、権限を継承することはできません。
    
  
- 固有の権限も作成しない限り、固有のロール定義を作成することはできません。
    
  
- Web サイト内の固有の権限をすべて取り消さない限り、継承したロール定義に戻すことはできません。既存の権限は、ロール定義に依存します。
    
  
- 継承したロール定義に戻さない限り、継承した権限に戻すことはできません。Web サイトの権限は、その Web サイトのロール定義に常に結び付けられます。
    
  

## ユーザー トークンの管理
<a name="SP15_RoleInheritance_ManagingUserTokens"> </a>

SharePoint では、SharePoint データベースからユーザー トークン情報を取得します。ユーザーがサイトに一度もアクセスしていない場合、またはユーザーのトークンが 24 時間以上前に生成されている場合は、SharePoint はそのユーザーが属するグループのリストを更新することによって新しいユーザー トークンを生成します。 
  
    
    
ユーザー アカウントが NT アカウントの場合、SharePoint は **AuthZ** インターフェイスを使用して、ActiveDirectory ディレクトリ サービスに対して **TokenGroups** プロパティのクエリを実行します。SharePoint がエクストラネット モードで実行されており、Active Directory に対してこのプロパティのクエリを実行する権限を持っていない場合、このクエリは失敗します。
  
    
    
ユーザー アカウントがメンバーシップ ユーザーの場合、SharePoint は ASP.NET **RoleManager** に対して、ユーザーが属するすべてのロールについてクエリを実行します。現在の実行可能ファイル用の適切な .config ファイルがない場合、このクエリは失敗します。
  
    
    
SharePoint が Active Directory または **<roleManager>** からユーザーのグループ メンバーシップを取得できない場合、新しく生成されるトークンには、ユーザーの一意のセキュリティ ID (SID) だけが含まれることになります。例外がスローされることはありませんが、ULS サーバー ログにエントリが書き込まれます。新しいトークンは、24 時間以内に再生成されないように SharePoint データベースにも書き込まれます。
  
    
    
SharePoint は、SharePoint データベースから新しいトークンを取得した後、または新しいトークンを生成して取得した後に、タイムスタンプを現在の時刻に設定し、そのトークンを呼び出し元に返します。これにより、トークンが 24 時間有効となるよう保証されます。
  
    
    
 [SPUserToken](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserToken.aspx) オブジェクトが呼び出し元に返されたら、トークンが期限切れになってから使用しないように呼び出し元が注意する必要があります。トークンを取得した時刻を記録してトークンの有効期限を追跡し、現在の時刻と [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) との差を比較するヘルパー ユーティリティを作成できます。
  
    
    
期限切れになったトークンを使用して SharePoint Web サイトを作成すると、例外がスローされます。トークンの既定のタイムアウト値は 24 時間です。トークンのタイムアウト値には、 [SPWebService.TokenTimeout](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebService.TokenTimeout.aspx) からアクセスできます。
  
    
    

## 権限の昇格
<a name="SP15_RoleInheritance_ElevationOfPrivilege"> </a>

Windows SharePoint Services 3.0 に追加された機能である権限の昇格を使用すると、本来より高いレベルの権限を使用して、操作をコード形式でプログラム的に実行できます。 [SPSecurity.RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) メソッドにより、現在のユーザーよりも高い権限を持つアカウントのコンテキストでコードのサブセットを実行する権限を委任できます。
  
    
    
以下は、 **RunWithElevatedPrivileges** の標準的な使用方法です。
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    // Do things by assuming the permission of the "system account".
});
```

多くの場合、SharePoint 内で操作を行うには、新しい  [SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.aspx) オブジェクトを取得して、変更を有効にする必要があります。次に例を示します。
  
    
    



```cs

SPSecurity.RunWithElevatedPrivileges(delegate()
{
    using (SPSite site = new SPSite(web.Site.ID))
    {
       // Do things by assuming the permission of the "system account".
    }
});
```

権限の昇格を使用すると、強力な方法で詳細にセキュリティを管理できますが、この機能を使用する場合は十分注意する必要があります。権限の低いユーザーに対しては、本来与えられた権限を超えるような直接的な無制限のメカニズムを公開しないでください。
  
    
    

> **重要**
>  [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) に渡されたメソッドに書き込み操作が含まれる場合、 [SPUtility.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.ValidateFormDigest.aspx) または [SPWeb.ValidateFormDigest()](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.ValidateFormDigest.aspx) のどちらかの呼び出しが行われる前に、 [RunWithElevatedPrivileges](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity.RunWithElevatedPrivileges.aspx) への呼び出しを行う必要があります。
  
    
    


## パスワードの自動変更
<a name="SP15_RoleInheritance_AutomaticPasswordChange"> </a>

パスワードの自動変更機能を使用すると、パスワードを自動的に更新および展開できます。複数のアカウント、サービス、および Web アプリケーションにわたるパスワード更新作業を手動で行う必要はありません。これにより、SharePoint 2013でのパスワード管理が行いやすくなります。このパスワードの自動変更機能を使用すると、パスワードの期限が近付いているかどうか、および暗号化された強力で長いランダム文字列を使用してパスワードをリセットするかどうかを決定できます。
  
    
    

### 管理アカウント

パスワードの自動変更機能は、管理アカウントを使用して実装します。管理アカウントによりセキュリティが向上し、アプリケーションが確実に切り離されます。管理アカウントを使用すると、次のことができます。
  
    
    

- パスワードがファーム内のすべてのサービスにわたって展開されるように、パスワードの自動変更機能を構成する。
    
  
- 他のドメイン アカウントを使用するように、SharePoint ファームのアプリケーション サーバーで実行されている SharePoint Web アプリケーションおよびサービスを構成する。
    
  
- 管理アカウントを、ファーム内のさまざまなサービスおよび Web アプリケーションにマップする。
    
  
- Active Directory ドメイン サービス (AD DS) で複数のアカウントを作成し、SharePoint で各アカウントを登録する。
    
  
管理アカウントを登録して SharePoint 2013 を有効にし、アカウント パスワードを制御することもできます。予定されているパスワード変更およびそれに伴うサービス中断についてユーザーに通知する必要がありますが、SharePoint ファーム、Web アプリケーション、およびさまざまなサービスによって使用されているアカウントは、個別に構成されたパスワード リセット スケジュールに基づいて、必要に応じてファーム内で自動的にリセットおよび展開できます。
  
    
    
 [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx) クラスを使用して行うことができる作業を次に示します。
  
    
    

- パスワードの変更
    
  
- パスワード変更スケジュールの設定
    
  
- パスワード変更の反映
    
  
- 前回パスワードが変更された時期の特定
    
  
- パスワードの最小文字数の設定
    
  
管理アカウント API の詳細については、次のリンクを参照してください。
  
    
    

-  [SPManagedAccount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.aspx)
    
  
-  [SPManagedAccount.EventProcessingOptions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventProcessingOptions.aspx)
    
  
-  [SPManagedAccount.EventType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPManagedAccount.EventType.aspx)
    
  

## その他の技術情報
<a name="SP15_RoleInheritance_AdditionalResources"> </a>


-  [SharePoint 2013 での認証、承認、およびセキュリティ](authentication-authorization-and-security-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の認証、ユーザー、グループ、およびオブジェクト モデル](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのクレームベース ID](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクレームベース ID と概念](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 での構成、管理、およびリソース](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

