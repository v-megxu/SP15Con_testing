---
title: SharePoint 2013 でのソーシャル機能の開発の概要
ms.prod: SHAREPOINT
ms.assetid: 8852ce36-8309-45a7-a141-2e10ac17a123
---



# SharePoint 2013 でのソーシャル機能の開発の概要
SharePoint 2013のソーシャル フィードとミニブログ投稿を使用したプログラミング、人とコンテンツ (ドキュメント、サイト、タグ) のフォロー、およびユーザー プロファイルの使用に関する概要を説明します。
 **この記事の内容**
  
    
    
 [アプリとソリューションでソーシャル機能を使用する方法](get-started-developing-with-social-features-in-sharepoint-2013.md#bk_HowToUseSocialFeatures)
  
    
    
 [開発環境の設定](get-started-developing-with-social-features-in-sharepoint-2013.md#DevEnvironment)
  
    
    
 [ソーシャル機能の開発シナリオ](get-started-developing-with-social-features-in-sharepoint-2013.md#DevScenarios)
  
    
    
 [ソーシャル機能を使ったプログラミングのハウツー](get-started-developing-with-social-features-in-sharepoint-2013.md#bk_GetStarted)
  
    
    
 [ソーシャル機能を使ったプログラミング用の API](get-started-developing-with-social-features-in-sharepoint-2013.md#SocialApis)
  
    
    
 [ソーシャル機能にアクセスするためのアプリのアクセス許可の要求](get-started-developing-with-social-features-in-sharepoint-2013.md#bkmk_AppPerms)
  
    
    
 [その他の技術情報](get-started-developing-with-social-features-in-sharepoint-2013.md#bk_AddResources)
  
    
    


## SharePoint 2013 アプリおよびソリューションでソーシャル機能を使用する方法
<a name="bk_HowToUseSocialFeatures"> </a>

ユーザーは SharePoint 2013 アプリおよびソリューションのソーシャル機能を使用して、他のユーザーとつながり、通信し、コラボレーションすることができます。また、重要なコンテンツと情報を検索し、追跡し、共有することができます。新しいソーシャル機能を追加するか、SharePoint 2013 で既に使用できる機能を拡張することができます。たとえば、共通の興味を持つユーザーを見つけてフォローできるアプリを作成する、フィード データのカスタム表示を作成する、カスタムのアクティビティをフィードに発行することができます。
  
    
    
この記事では、個人サイトやチーム サイトで見つける人物、フィード、およびフォロー機能に沿って説明します。コミュニティ サイトのフォーラム エクスペリエンスと評価モデルでは特定の API が公開されないため、SharePoint サイトを使用して、API 一覧を直接表示して機能を拡張できます。詳細については、「 [コミュニティ サイトの新機能](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md#bkmk_Collab)」を参照してください。
  
    
    
開発を始める前に、コードが実行される場所、コードが実行される SharePoint 環境、コードが提供する機能を把握しておく必要があります。これらの内容は、作成するアプリの種類と使用する API を選択するときに役立ちます。判断に役立つ情報については、「 [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)」、「 [SharePoint アドインと SharePoint ソリューションの比較](sharepoint-add-ins-compared-with-sharepoint-solutions.md)」、および「 [SharePoint アドインまたは SharePoint ソリューションの選択](deciding-between-sharepoint-add-ins-and-sharepoint-solutions.md)」を参照してください。
  
    
    

### 開発環境の設定
<a name="DevEnvironment"> </a>

ソーシャル機能を使用して開発を開始するには、次のことを行う必要があります:
  
    
    

- SharePoint Server 2013 または SharePoint Online
    
  
- Office Developer Tools for Visual Studio 2013
  
    
    
 ** または**
  
    
    
Napa を使った Visual Studio 2012 または Visual Studio 2013 (デベロッパー サイトの Office 365 の SharePoint ホスト型アプリの場合のみ)
    
  
詳細については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」と「 [SharePoint Server 2013 でソーシャル コンピューティング機能を構成する](http://technet.microsoft.com/ja-jp/library/fp161267%28v=office.15%29.aspx)」を参照してください。
  
    
    

### SharePoint 2013 でのソーシャル機能の開発シナリオ
<a name="DevScenarios"> </a>

ソーシャル機能の高度な開発シナリオには、ソーシャル フィード、人とコンテンツ (ドキュメント、サイト、タグ) のフォロー、ユーザー プロパティの使用などがあります。表 1 に、各シナリオや一般的なプログラミング タスクの機能にアクセスするために使用する主な API について説明された記事のリンクを示します。
  
    
    
表 1. ソーシャル機能シナリオの主な API とプログラミング タスクについて説明している記事
  
    
    

-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のユーザー プロファイルの操作](work-with-user-profiles-in-sharepoint-2013.md)
    
  

### SharePoint 2013 でのソーシャル機能を使ったプログラミングのハウツー
<a name="bk_GetStarted"> </a>

開発環境をセットアップし、シナリオを選択したら、ソーシャル機能のプログラミングを開始できます。表 1 に、ソーシャル機能を使用した基本的なプログラミング作業方法を示した記事へのリンクを示します。
  
    
    

**表 1. ソーシャル機能の開発シナリオの方法に関する記事**


|**機能エリア**|**説明**|
|:-----|:-----|
| [[方法] SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してソーシャル フィードに対する読み書きを行う](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-net-client-object.md) <br/> |.NET クライアント オブジェクト モデルを使用してソーシャル フィードの読み取り/書き込みを行うアプリケーションを作成するための詳細な手順を順番に説明します。  <br/> |
| [[方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md) <br/> |REST サービスを使用してソーシャル フィードの読み取り/書き込みを行うアプリケーションを作成するための詳細な手順を順番に説明します。  <br/> |
| [[方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md) <br/> |.NET クライアント オブジェクト モデルを使用して、マイクロブログの投稿を作成および削除する方法、およびソーシャル フィードを取得する方法を説明します。  <br/> |
| [[方法] SharePoint 2013 で JavaScript オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md) <br/> |JavaScript オブジェクト モデルを使用して、ミニブログの投稿を作成および削除する方法、およびソーシャル フィードを取得する方法を説明します。  <br/> |
| [[方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md) <br/> |**SocialDataItem** オブジェクトをミニブログの投稿に追加し、ソーシャル フィードにメンション、タグ、およびリンクとして表示する方法を説明します。 <br/> |
| [SharePoint Server 2013 で投稿にイメージ、ビデオ、ドキュメントを埋め込む方法](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md) <br/> |**SocialAttachment** オブジェクトをミニブログの投稿に追加し、ソーシャル フィードに埋め込み画像、ビデオ、およびドキュメントとして表示する方法を説明します。 <br/> |
| [方法: SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md) <br/> |.NET クライアント オブジェクト モデルを使用して、ユーザー フォロー機能を操作する方法を説明します。  <br/> |
| [SharePoint 2013 で JavaScript オブジェクト モデルを使用してユーザーをフォローする方法](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md) <br/> |JavaScript オブジェクト モデルを使用して、ユーザー フォロー機能を操作する方法を説明します。  <br/> |
| [方法: SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md) <br/> |.NET クライアント オブジェクト モデルを使用して、コンテンツ フォロー機能を操作する方法を説明します。  <br/> |
| [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md) <br/> |REST サービスを使用して、コンテンツ フォロー機能を操作する方法を説明します。  <br/> |
| [[方法] SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md) <br/> |.NET クライアント オブジェクト モデルを使用してユーザー プロファイル プロパティを取得する方法を説明します。  <br/> |
| [SharePoint 2013 で JavaScript オブジェクトモデルを使用して、ユーザー プロファイル プロパティを取得する方法](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md) <br/> |JavaScript オブジェクト モデルを使用して、ユーザー プロファイル プロパティを取得する方法を説明します。  <br/> |
| [[方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md) <br/> |サーバー オブジェクト モデルを使用して、ユーザー プロファイルとプロパティを作成、取得、および管理する方法を説明します。  <br/> |
   

### SharePoint 2013 ソーシャル機能を使用したプログラミングの API
<a name="SocialApis"> </a>

アプリとソリューションの SharePoint へのアクセス方法は異なりますが、SharePoint にアクセスした後のソーシャル API の使用方法は基本的に同じです。表 2 に、SharePoint 2013 でフィード、フォロー、およびユーザー プロファイル機能を使用したプログラミングの API と、サーバーのソース ファイルへのパスを示します。
  
    
    

**表 2. ソーシャル機能のプログラミング用 API**


|**API 名**|**ソースとパス**|
|:-----|:-----|
| [.NET クライアント オブジェクト モデル](http://msdn.microsoft.com/library/9cc3f70c-78ac-4d2d-b46e-77522ee5d937%28Office.15%29.aspx) <br/> |%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI の           Microsoft.SharePoint.Client.UserProfiles.dll  <br/> |
|Silverlight クライアント オブジェクト モデル  <br/> |%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin の           Microsoft.SharePoint.Client.UserProfiles.Silverlight.dll  <br/> |
|モバイル クライアント オブジェクト モデル  <br/> |%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\ClientBin の           Microsoft.SharePoint.Client.UserProfiles.Phone.dll <br/> |
| [JavaScript オブジェクト モデル](http://msdn.microsoft.com/library/95cb5427-8514-4e9a-8eee-7ed4b82ec01b%28Office.15%29.aspx) <br/> |%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS の           SP.UserProfiles.js  <br/> |
|REST (Representational State Transfer) サービス  <br/> | [http://<site url>/_api/social.feed](social-feed-rest-api-reference-for-sharepoint-2013.md)           [http://<site url>/_api/social.following](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)           [http://<site url>/_api/SP.UserProfiles.PeopleManager](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx#bk_PeopleManager) <br/> |
| [サーバー オブジェクト モデル](http://msdn.microsoft.com/library/87c5118c-ac0e-4bd9-a75f-7452a9eb0e41%28Office.15%29.aspx) <br/> |%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ISAPI の           Microsoft.Office.Server.UserProfiles.dll  <br/> |
   

> **メモ**
> Microsoft.Office.Server.UserProfiles アセンブリのすべてのサーバー側機能をクライアント API から使用できるわけではありません。 使用可能な API については、 [Microsoft.SharePoint.Client.Social](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.aspx) 名前空間と [Microsoft.SharePoint.Client.UserProfiles](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.aspx) 名前空間を参照してください。
  
    
    


## SharePoint アドインでソーシャル機能にアクセスするためのアプリ アクセス許可の要求
<a name="bkmk_AppPerms"> </a>

SharePoint アドインは、SharePoint リソースをインストールするユーザーが SharePoint リソースにアクセスするために必要なアクセス許可を要求する必要があります。たとえば、フィードに投稿するアプリの場合、フィードに対する **Write** (以上の) アクセス許可を要求する必要があります。アプリに必要なアクセス許可は、Visual Studio の AppManifest.xml、または Napa の [ **プロパティ**] ダイアログ ボックスで指定します。
  
    
    
アプリ アクセス許可の要求は SharePoint 展開を適用範囲としています。表 3 に、ソーシャル機能にアクセスするためのスコープ名 (および対応するスコープ URI) と使用可能な権限を示します。詳細については、「 [SharePoint 2013 でのアドインのアクセス許可](http://msdn.microsoft.com/library/5f7a8440-3c09-4cf8-83ec-c236bfa2d6c4%28Office.15%29.aspx)」、「 [SharePoint 2013 のアドイン承認ポリシーの種類](http://msdn.microsoft.com/library/124879c7-a746-4c10-96a7-da76ad5327f0%28Office.15%29.aspx)」、および「 [SharePoint 2013 でアプリの権限管理を計画する](http://technet.microsoft.com/ja-jp/library/jj219576%28office.15%29.aspx)」を参照してください。
  
    
    

**表 3. SharePoint Server 2013 のソーシャル機能に対するアプリ アクセス許可のスコープと使用可能な権限**


|**スコープ名**|**説明**|**使用可能な権限**|
|:-----|:-----|:-----|
|ユーザー プロファイル          ( `http://sharepoint/social/tenant`)  <br/> |すべてのユーザー プロファイルへのアクセスに使用するアクセス許可要求スコープ。プロファイル画像のみ変更できますが、ユーザー プロファイルのその他のプロパティはすべて SharePoint アドインに対して読み取り専用です。テナント管理者がインストールする必要があります。  <br/> |Read、Write、Manage、FullControl  <br/> |
|コア          ( `http://sharepoint/social/core`)  <br/> |ユーザーがフォローしているコンテンツと、ミニブログ機能で使用する共有メタデータにアクセスするためのアクセス許可要求スコープ。このスコープは、コンテンツのフォロー機能をサポートしている個人用サイトにのみ適用されます。アプリがその他の種類のサイトにインストールされる場合、テナント スコープを使用してください。  <br/> |Read、Write、Manage、FullControl  <br/> |
|ニュース フィード          ( `http://sharepoint/social/microfeed`)  <br/> |ユーザーのフィードまたはチームのフィードにアクセスするためのアクセス許可要求スコープ。このスコープは、ミニブログ機能をサポートしている個人用サイト、または **サイト フィード**機能がアクティブになっているチーム サイトに適用されます。アプリがその他の種類のサイトにインストールされる場合、テナント スコープを使用してください。  <br/> |Read、Write、Manage、FullControl  <br/> |
| `http://sharepoint/social/trimming` <br/> |この権限では、アプリに対するソーシャル フィードにセキュリティ トリミング コンテンツを表示するかどうかを決定するために使用するスコープが必要です。この高信頼許可が付与されない場合、一部のコンテンツ (アプリが権限を持たないドキュメントやサイトに関する操作) は、ユーザーに十分な権限がある場合でも、アプリに返されるフィード データから削除されます。この権限はアプリのマニフェスト ファイルに手動で追加する必要があります。  <br/> |Read、Write、Manage、FullControl  <br/> |
   

### アプリの権限を要求する際に考慮する必要がある項目

ソーシャル機能用のアプリ アクセス許可を指定する場合、次の考慮事項に留意する必要があります。
  
    
    

- Office ストア アプリに対して、 **FullControl** 権限を指定するアプリは許可されません。Office ストア アプリに対しては、 **Read**、 **Write**、および **Manage** 権限だけが許可されます。
    
  
- フィードとフォロー機能のアクセス許可を指定するには、コア、ニュース フィード、およびテナント ( `http://sharepoint/content/tenant`) のスコープを使用します。テナント スコープは、アプリがインストールされているテナント全体 (コアおよびニュース フィードのスコープを含む) を示します。そのため、アプリにテナント スコープで必要な権利が既に指定されている場合、コアまたはニュース フィードのスコープではアクセス許可を要求する必要はありません。
    
  
- 開発中に「SocialListNotFound : ソーシャル リストが個人用サイトに存在しません。」または「ファイルが見つかりません。」というメッセージが表示された場合は、テナント スコープを使用してください。コアまたはニュース フィードのスコープをアプリで使用する場合は、アプリ カタログからアプリを開いてアクセス許可をテストできます。
    
  
- コア スコープは、コンテンツのフォロー機能をサポートしている個人用サイトに適用されます。ニュース フィード スコープは、ミニブログ機能をサポートしている個人用サイト、または **サイト フィード**機能がアクティブになっているチーム サイトに適用されます。それ以外の種類のサイトにアプリをインストールする場合は、テナント スコープを使用する必要があります。「 [SharePoint アドインのテナントと展開スコープ](http://msdn.microsoft.com/library/1ceb3142-a7a5-453e-920f-5f953a79401a%28Office.15%29.aspx)」を参照してください。
    
  
- ユーザー プロファイル スコープの権限を要求するアプリはテナント管理者がインストールする必要があります。こうしたアプリを、SharePoint Online の Office 365 Small Business Premium バージョンにインストールすることはできません。
    
  
- ソーシャル機能およびミニブログ機能のライセンス要件または機能のアクティブ化要件が満たされていない場合は、アプリをインストールできないというメッセージがユーザーに表示されます。
    
  
- SharePoint 2013 の外部で起動されるアプリは、実行時にアクセス許可 ( **Full Control** を除く) を要求できます。詳細については、「 [SharePoint アドインの認証コード OAuth フロー](http://msdn.microsoft.com/library/e89e91c7-ea39-49b9-af5a-7f047a7e2ab7%28Office.15%29.aspx)」を参照してください。
    
  

## その他の技術情報
<a name="bk_AddResources"> </a>

 **概念に関する記事**
  
    
    

-  [SharePoint 2013 のソーシャルおよびコラボレーション機能](social-and-collaboration-features-in-sharepoint-2013.md)
    
  
-  [開発者向けの SharePoint 2013 のソーシャルおよびコラボレーション機能の新機能](what-s-new-for-developers-in-social-and-collaboration-features-in-sharepoint-201.md)
    
  
-  [SharePoint Server 2013 プレビューでソーシャル コンピューティングとグループ作業を計画する](http://technet.microsoft.com/ja-jp/library/ee662531%28office.15%29.aspx)
    
  
-  [SharePoint Server 2013 でソーシャル コンピューティング機能を構成する](http://technet.microsoft.com/ja-jp/library/fp161267%28v=office.15%29.aspx)
    
  
-  [SharePoint Server 2013 でのソーシャル コンピューティングの用語と概念](http://technet.microsoft.com/ja-jp/library/jj219804%28v=office.15%29.aspx)
    
  
 **参照ドキュメント**
  
    
    

-  [ソーシャル クライアント クラス ライブラリ](http://msdn.microsoft.com/library/9cc3f70c-78ac-4d2d-b46e-77522ee5d937%28Office.15%29.aspx)
    
  
-  [SP.UserProfiles.js JavaScript リファレンス](http://msdn.microsoft.com/library/80cf5436-6aa2-6f11-a782-66a04f6e2fb0%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのユーザーやコンテンツのフォローに関する REST API リファレンス](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [ユーザー プロファイル REST API リファレンス](http://msdn.microsoft.com/library/10757ed1-6e86-474f-89e0-6dec6aa66a2b%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 ソーシャル サーバー クラス ライブラリ](http://msdn.microsoft.com/library/87c5118c-ac0e-4bd9-a75f-7452a9eb0e41%28Office.15%29.aspx)
    
  
