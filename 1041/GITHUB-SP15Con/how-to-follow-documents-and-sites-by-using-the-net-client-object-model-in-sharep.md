---
title: 方法 SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする
ms.prod: SHAREPOINT
ms.assetid: 84366e01-4961-459d-8109-2f1d2d714353
---


# 方法: SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする
SharePoint Server 2013の .NET クライアント オブジェクト モデルを使用してコンテンツのフォロー機能を操作する方法について説明します。
## .NET クライアント オブジェクトを使用してコンテンツをフォローする方法
<a name="bk_intro"> </a>

SharePoint Server 2013 ユーザーは、ドキュメント、サイト、およびタグをフォローして、ニュースフィードのアイテムの更新情報を取得し、フォロー対象のドキュメントとサイトをすばやく開くことができます。アプリまたはソリューションで .NET クライアント オブジェクト モデルを使用すると、コンテンツのフォローを開始する、コンテンツのフォローを停止する、現在のユーザーの代理でコンテンツのフォローを受けるという処理を実行できます。この記事では, .NET クライアント オブジェクト モデルを使用して、ドキュメントとサイトでコンテンツのフォロー機能を使用する方法について説明します。
  
    
    
次のオブジェクトは、コンテンツのフォロー タスク用の主な API です。
  
    
    

-  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) には、フォロー対象アクターのユーザー一覧を管理するメソッドが用意されています。
    
  
-  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) は、クライアント側要求に応答してサーバーが返すドキュメント、サイト、またはタグを示します。
    
  
- サーバーに対するクライアント側要求で、 [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) にドキュメント、サイト、またはタグを指定します。
    
  
- サーバーに対するクライアント側要求で、 [Microsoft.SharePoint.Client.Social.SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) と [Microsoft.SharePoint.Client.Social.SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) にコンテンツ タイプを指定します。
    
  

> **メモ**
> ユーザー フォロー タスクにもこれらの API を使用しますが、 [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) から使用できる **GetSuggestions** メソッドと **GetFollowers** メソッドは、コンテンツではなくユーザーのフォローのみをサポートします。 [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) の詳細な使用方法については、「 [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)」と「 [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)」を参照してください。ユーザーのフォロー方法のコード例については、「 [方法: SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)」を参照してください。 
  
    
    


## SharePoint 2013 .NET クライアント オブジェクト モデルを使用してコンテンツのフォロー機能を使用するように開発環境をセットアップする場合の前提条件
<a name="bkmk_SetUpDevEnv"> </a>

.NET クライアント オブジェクト モデルを使用してドキュメントとサイトのコンテンツのフォロー機能を操作するコンソール アプリケーションを作成するには、次のものが必要です。
  
    
    

- SharePoint Server 2013 (個人用サイトが構成済みで、現在のユーザーの個人用サイトが作成済みで、ドキュメントが SharePoint ドキュメント ライブラリにアップロード済みであること)
    
  
- Visual Studio 2012
    
  
- ログオン ユーザーの User Profile Service アプリケーションに対する [ **フル コントロール**] アクセス許可
    
  

> **メモ**
> 開発作業をしているコンピューターで SharePoint Server 2013 が実行されていない場合は、SharePoint 2013 のクライアント アセンブリが含まれている  [SharePoint クライアント コンポーネント](https://www.microsoft.com/en-us/download/details.aspx?id=35585)のダウンロードを入手してください。 
  
    
    


## SharePoint 2013の .NET クライアント オブジェクト モデルを使用してコンテンツのフォロー機能を操作するコンソール アプリケーションの作成
<a name="bkmk_CreateConsoleApp"> </a>


1. Visual Studio で、[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。
    
  
2. [ **新しいプロジェクト**] ダイアログ ボックスで、上部のドロップダウン リストから [ **.NET Framework 4.5**] を選択します。
    
  
3. [ **テンプレート**] ボックスの一覧で、[ **Windows**] を選択し、[ **コンソール アプリケーション**] テンプレートを選択します。
    
  
4. プロジェクトの名前を FollowContentCSOM に設定して、[ **OK**] をクリックします。
    
  
5. 次のアセンブリへの参照を追加します。
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. **Program** クラスの内容を次のどちらかのシナリオのコード例に置き換えます。
    
  -  [コンテンツのフォローを開始および停止する](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md#bkmk_FollowContent)
    
  
  -  [現在のユーザーのフォロー対象のコンテンツを取得する](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md#bkmk_GetFollowed)
    
  
7. コンソール アプリケーションをテストするには、メニュー バーの [ **デバッグ**] を選択し、[ **デバッグ開始**] をクリックします。
    
  

## コード例: SharePoint 2013の .NET クライアント オブジェクト モデルを使用して、コンテンツのフォローを開始および停止する
<a name="bkmk_FollowContent"> </a>

次のコード例では、現在のユーザーによる対象アイテムのフォローを開始または停止します。次の操作を行う方法を示します。
  
    
    

-  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) メソッドを使用して、現在のユーザーが特定のドキュメントまたはサイトをフォローしているかどうかを確認します。
    
  
-  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) メソッドを使用して、ドキュメントまたはサイトのフォローを開始します。
    
  
-  [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) メソッドを使用して、ドキュメントまたはサイトのフォローを停止します。
    
  
-  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) メソッドを使用して、現在のユーザーがフォローしているドキュメントまたはサイトの数を取得します。
    
  
このコード例では、 [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) メソッドによって返される [SocialFollowResult](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowResult.aspx) オブジェクトを使用して、対象アイテムのフォローを開始するか停止するかを判断します。
  
    
    

> **メモ**
> コードを実行する前に、 **serverUrl** 変数と **contentUrl** 変数のプレースホルダーの値を変更してください。ドキュメントの代わりにサイトを使用するには、コメント アウトされている変数を使用します。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace FollowContentCSOM
{
    class Program
    {
        static ClientContext clientContext;
        static SocialFollowingManager followingManager;
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the URL of the target
            // server and target document (or site).
            const string serverUrl = "http://serverName";
            const string contentUrl = @"http://serverName/libraryName/fileName";
            const SocialActorType contentType = SocialActorType.Document;
            // Do not use a trailing '/' for a subsite.
            //const string contentUrl = @"http://serverName/subsiteName"; 
            //const SocialActorType contentType = SocialActorType.Site;

            // Get the client context.
            clientContext = new ClientContext(serverUrl);

            // Get the SocialFeedManager instance.
            followingManager = new SocialFollowingManager(clientContext);

            // Create a SocialActorInfo object to represent the target item.
            SocialActorInfo actorInfo = new SocialActorInfo();
            actorInfo.ContentUri = contentUrl;
            actorInfo.ActorType = contentType;

            // Find out whether the current user is following the target item.
            ClientResult<bool> isFollowed = followingManager.IsFollowed(actorInfo);

            // Get the information from the server.
            clientContext.ExecuteQuery();

            Console.WriteLine("Was the current user following the target {0}? {1}\\n",
                actorInfo.ActorType.ToString().ToLower(), isFollowed.Value);
            Console.Write("Initial count: ");

            // Get the current count of followed items.
            WriteFollowedCount(actorInfo.ActorType);

            // Try to follow the target item. If the result is OK, then
            // the request succeeded.
            ClientResult<SocialFollowResult> result = followingManager.Follow(actorInfo);
            clientContext.ExecuteQuery();

            // If the result is AlreadyFollowing, then stop following 
            // the target item.
            if (result.Value == SocialFollowResult.AlreadyFollowing)
            {
                followingManager.StopFollowing(actorInfo);
                clientContext.ExecuteQuery();
            }

            // Handle other SocialFollowResult return values.
            else if (result.Value == SocialFollowResult.LimitReached
                || result.Value == SocialFollowResult.InternalError)
            {
                Console.WriteLine(result.Value);
            }

            // Get the updated count of followed items.
            Console.Write("Updated count: ");
            WriteFollowedCount(actorInfo.ActorType);
            Console.ReadKey();
        }

        // Get the count of the items that the current user is following.
        static void WriteFollowedCount(SocialActorType type)
        {

            // Set the parameter for the GetFollowedCount method, and
            // handle the case where the item is a site. 
            SocialActorTypes types = SocialActorTypes.Documents;
            if (type != SocialActorType.Document)
            {
                types = SocialActorTypes.Sites;
            }

            ClientResult<int> followedCount = followingManager.GetFollowedCount(types);
            clientContext.ExecuteQuery();
            Console.WriteLine("{0} followed {1}", followedCount.Value, types.ToString().ToLower());
        }
    }
}
```


## コード例: SharePoint 2013の .NET クライアント オブジェクト モデルを使用して、フォロー対象のコンテンツを取得する
<a name="bkmk_GetFollowed"> </a>

次のコード例では、現在のユーザーがフォローしているドキュメントとサイトを取得し、ユーザーのコンテンツのフォロー状況に関する情報を取得します。次の操作を行う方法を示します。
  
    
    

-  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) メソッドを使用して、現在のユーザーが対象のドキュメントとサイトをフォローしているかどうかを確認します。
    
  
-  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) メソッドを使用して、現在のユーザーがフォローしているドキュメントとサイトの数を取得します。
    
  
-  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) メソッドを使用して、現在のユーザーがフォローしているドキュメントとサイトを取得します。
    
  
- コンテンツのグループに対して反復処理を行い、各アイテムの名前、コンテンツ URI、および URI を取得します。
    
  

> **メモ**
> コードを実行する前に、 **serverUrl** 変数、 **docContentUrl** 変数、および **siteContentUrl** 変数のプレースホルダーの値を変更してください。
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace FollowContentCSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the URLs of
            // the target server, document, and site.
            const string serverUrl = "http://serverName";
            const string docContentUrl = @"http://serverName/libraryName/fileName";
            const string siteContentUrl = @"http://serverName/subsiteName"; // do not use a trailing '/' for a subsite

            // Get the client context.
            ClientContext clientContext = new ClientContext(serverUrl);

            // Get the SocialFollowingManager instance.
            SocialFollowingManager followingManager = new SocialFollowingManager(clientContext);

            // Create SocialActorInfo objects to represent the target 
            // document and site.
            SocialActorInfo docActorInfo = new SocialActorInfo();
            docActorInfo.ContentUri = docContentUrl;
            docActorInfo.ActorType = SocialActorType.Document;
            SocialActorInfo siteActorInfo = new SocialActorInfo();
            siteActorInfo.ContentUri = siteContentUrl;
            siteActorInfo.ActorType = SocialActorType.Site;

            // Find out whether the current user is following the target
            // document and site.
            ClientResult<bool> isDocFollowed = followingManager.IsFollowed(docActorInfo);
            ClientResult<bool> isSiteFollowed = followingManager.IsFollowed(siteActorInfo);

            // Get the count of documents and sites that the current
            // user is following.
            ClientResult<int> followedDocCount = followingManager.GetFollowedCount(SocialActorTypes.Documents);
            ClientResult<int> followedSiteCount = followingManager.GetFollowedCount(SocialActorTypes.Sites);

            // Get the documents and the sites that the current user
            // is following.
            ClientResult<SocialActor[]> followedDocResult = followingManager.GetFollowed(SocialActorTypes.Documents);
            ClientResult<SocialActor[]> followedSiteResult = followingManager.GetFollowed(SocialActorTypes.Sites);

            // Get the information from the server.
            clientContext.ExecuteQuery();

            // Write the results to the console window.
            Console.WriteLine("Is the current user following the target document? {0}", isDocFollowed.Value);
            Console.WriteLine("Is the current user following the target site? {0}", isSiteFollowed.Value);
            if (followedDocCount.Value > 0)
            {
                IterateThroughContent(followedDocCount.Value, followedDocResult.Value);
            } if (followedSiteCount.Value > 0)
            {
                IterateThroughContent(followedSiteCount.Value, followedSiteResult.Value);
            }
            Console.ReadKey();
        }

        // Iterate through the items and get each item's display
        // name, content URI, and absolute URI.
        static void IterateThroughContent(int count, SocialActor[] actors)
        {
            SocialActorType actorType = actors[0].ActorType;
            Console.WriteLine("\\nThe current user is following {0} {1}s:", count, actorType.ToString().ToLower());
            foreach (SocialActor actor in actors)
            {
                Console.WriteLine("  - {0}", actor.Name);
                Console.WriteLine("\\tContent URI: {0}", actor.ContentUri);
                Console.WriteLine("\\tURI: {0}", actor.Uri);
            }
        }
    }
}
```


## その他の技術情報
<a name="bkmk_AddtionalResources"> </a>


-  [SharePoint 2013 でのコンテンツのフォロー](follow-content-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 で REST サービスを使用して、ドキュメント、サイト、タグをフォローする方法](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)
    
  
-  [方法: SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)
    
  

