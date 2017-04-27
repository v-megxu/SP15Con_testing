---
title: 方法 SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする
ms.prod: SHAREPOINT
ms.assetid: 0fdb7ca5-d408-4256-b52b-886c4bc3b5b8
---


# 方法: SharePoint 2013 で .NET クライアント オブジェクト モデルを使用してユーザーをフォローする
SharePoint Server 2013 .NET クライアント オブジェクト モデルを使用してユーザー フォロー機能を操作する方法を説明します。
## SharePoint Server 2013でユーザー フォロー機能を使用する理由

SharePoint Server 2013 では、ユーザーが他のユーザーをフォローすると、そのユーザーのニュースフィードにフォロー対象ユーザーの投稿とアクティビティが表示されます。ユーザー フォロー機能を使用して関心のある人たちに焦点を当てることで、アプリまたはソリューションの適合度 (関連性) を高めることができます。.NET クライアント オブジェクト モデルでは、フォロー対象ユーザーが  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) オブジェクトで表現されます。.NET クライアント オブジェクト モデルにおける中心的なユーザー フォロー タスクを実行するには、 [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) オブジェクトを使用します。この記事では, .NET クライアント オブジェクト モデルを使用してユーザー フォロー機能を操作する方法について説明します。
  
    
    

> **メモ**
> ここでは  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) に焦点を当てています。なぜなら、ここにユーザーとコンテンツをフォローするための中心的な機能がまとめられているからです。ただし、 [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) オブジェクトには、 [AmIFollowedBy(String)](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.AmIFollowedBy.aspx) メソッド、他のユーザーのフォロー状態を取得するメソッドなど、ユーザーをフォローするための追加的な機能が含まれています。
  
    
    


## SharePoint 2013 .NET クライアント オブジェクト モデルを使用してユーザー フォロー機能を操作するための開発環境をセットアップするための前提条件

.NET クライアント オブジェクト モデルを使用してユーザー フォロー機能を操作するコンソール アプリケーションを作成するには、以下のものが必要です。
  
    
    

- 個人用サイトが構成され、現在のユーザーおよび対象ユーザーについてユーザー プロファイルおよび個人用サイトが作成されている SharePoint Server 2013
    
  
- Visual Studio 2012
    
  
- ログオン ユーザーの User Profile Service アプリケーションに対する [ **フル コントロール**] アクセス許可
    
  

> **メモ**
> 開発作業をしているコンピューターで SharePoint Server 2013 が実行されていない場合は、SharePoint 2013 のクライアント アセンブリが含まれている  [SharePoint クライアント コンポーネント](http://www.microsoft.com/en-us/download/details.aspx?id=35585)のダウンロードを入手してください。 
  
    
    


## Visual Studio 2012 でのコンソール アプリケーションの作成
<a name="bkmk_CreateConsoleApp"> </a>


1. Visual Studio を開き、[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。
    
  
2. [ **新しいプロジェクト**] ダイアログ ボックスで、上部のドロップダウン リストから [ **.NET Framework 4.5**] を選択します。
    
  
3. [ **テンプレート**] ボックスの一覧で、[ **Windows**] を選択し、[ **コンソール アプリケーション**] テンプレートを選択します。
    
  
4. プロジェクトの名前を FollowPeopleCSOM にして、[ **OK**] をクリックします。
    
  
5. 次のアセンブリへの参照を追加します。
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. **Program** クラスの内容を次のどちらかのシナリオのコード例に置き換えます。
    
  -  [ユーザーのフォローを開始または停止する](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md#bkmk_FollowPeople)
    
  
  -  [フォロワーとフォロー対象ユーザーを取得する](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md#bkmk_GetFollowednFollowers)
    
  
7. コンソール アプリケーションをテストするには、メニュー バーの [ **デバッグ**] を選択し、[ **デバッグ開始**] をクリックします。
    
  

## コード例: SharePoint 2013 .NET クライアント オブジェクト モデルを使用してユーザーのフォローを開始または停止する
<a name="bkmk_FollowPeople"> </a>

次のコード例では、現在のユーザーに対象ユーザーのフォローを開始または停止させます。このコード例では、以下の方法を示しています。
  
    
    

-  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) メソッドを使用して、現在のユーザーが対象ユーザーをフォローしているかどうかを確認します。
    
  
-  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) メソッドを使用して、現在のユーザーがフォローしている人数を取得します。
    
  
-  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) メソッドを使用して、対象ユーザーのフォローを開始します。
    
  
-  [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) メソッドを使用して、対象ユーザーのフォローを停止します。
    
  
このコード例では、 [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) メソッドによって返される [SocialFollowResult](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowResult.aspx) オブジェクトを使用して、対象ユーザーのフォローを開始するか停止するかを決定します。
  
    
    

> **メモ**
> コードを実行する前に、 **serverUrl** 変数と **targetUser** 変数のプレースホルダーの値を変更してください。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace FollowPeopleCSOM
{
    class Program
    {
        static ClientContext clientContext;
        static SocialFollowingManager followingManager;
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the target
            // server URL and target user.
            const string serverUrl = "http://serverName";
            const string targetUser = "domainName\\\\userName";

            // Get the client context.
            clientContext = new ClientContext(serverUrl);

            // Get the SocialFeedManager instance.
            followingManager = new SocialFollowingManager(clientContext);

            // Create a SocialActorInfo object to represent the target user.
            SocialActorInfo actorInfo = new SocialActorInfo();
            actorInfo.AccountName = targetUser;

            // Find out whether the current user is following the target user.
            ClientResult<bool> isFollowed = followingManager.IsFollowed(actorInfo);

            // Get the information from the server.
            clientContext.ExecuteQuery();

            Console.WriteLine("Was the current user following the target user? {0}\\n", isFollowed.Value);
            Console.Write("Initial count: ");

            // Get the current count of followed people.
            WriteFollowedCount();

            // Try to follow the target user. If the result is OK, then
            // the request succeeded.
            ClientResult<SocialFollowResult> result = followingManager.Follow(actorInfo);
            clientContext.ExecuteQuery();

            // If the result is AlreadyFollowing, then stop following 
            // the target user.
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

            // Get the updated count of followed people.
            Console.Write("Updated count: ");
            WriteFollowedCount();
            Console.ReadKey();
        }

        // Get the count of the people who the current user is following.
        static void WriteFollowedCount()
        {
            ClientResult<int> followedCount = followingManager.GetFollowedCount(SocialActorTypes.Users);
            clientContext.ExecuteQuery();
            Console.WriteLine("The current user is following {0} people.", followedCount.Value);
        }
    }
}

```


## コード例: SharePoint 2013 .NET クライアント オブジェクト モデルを使用してフォロワーとフォロー対象ユーザーを取得する
<a name="bkmk_GetFollowednFollowers"> </a>

次のコード例では、現在のユーザーがフォローしているユーザーを取得し、現在のユーザーによってフォローされているユーザーを取得して、現在のユーザーのユーザー フォロー状態に関する情報を取得します。
  
    
    

-  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) メソッドを使用して、現在のユーザーが対象ユーザーをフォローしているかどうかを確認します。
    
  
-  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) メソッドを使用して、現在のユーザーがフォローしている人数を取得します。
    
  
-  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) メソッドを使用して、現在のユーザーがフォローしているユーザーを取得します。
    
  
-  [GetFollowers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowers.aspx) メソッドを使用して、現在のユーザーをフォローしているユーザーを取得します。
    
  
- ユーザーのグループを反復処理して、各ユーザーの表示名、個人 URI、および画像 URI を取得します。
    
  

> **メモ**
> コードを実行する前に、 **serverUrl** 変数と **targetUser** 変数のプレースホルダーの値を変更してください。
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace FollowPeopleCSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the target
            // server URL and target user.
            const string serverUrl = "http://serverName";
            const string targetUser = "domainName\\\\userName";

            // Get the client context.
            ClientContext clientContext = new ClientContext(serverUrl);
            
            // Get the SocialFeedManager instance.
            SocialFollowingManager followingManager = new SocialFollowingManager(clientContext);

            // Create a SocialActorInfo object to represent the target user.
            SocialActorInfo actorInfo = new SocialActorInfo();
            actorInfo.AccountName = targetUser;

            // Find out whether the current user is following the target user.
            ClientResult<bool> isFollowed = followingManager.IsFollowed(actorInfo);

            // Get the count of people who the current user is following.
            ClientResult<int> followedCount = followingManager.GetFollowedCount(SocialActorTypes.Users);

            // Get the people who the current user is following.
            ClientResult<SocialActor[]> followedResult = followingManager.GetFollowed(SocialActorTypes.Users);

            // Get the people who are following the current user.
            ClientResult<SocialActor[]> followersResult = followingManager.GetFollowers();

            // Get the information from the server.
            clientContext.ExecuteQuery();

            // Write the results to the console window.
            Console.WriteLine("Is the current user following the target user? {0}\\n", isFollowed.Value);
            Console.WriteLine("People who the current user is following: ({0} count)", followedCount.Value);
            IterateThroughPeople(followedResult.Value);
            Console.WriteLine("\\nPeople who are following the current user:");
            IterateThroughPeople(followersResult.Value);
            Console.ReadKey();
        }

        // Iterate through the people and get each person's display
        // name, personal URI, and picture URI.
        static void IterateThroughPeople(SocialActor[] actors)
        {
            foreach (SocialActor actor in actors)
            {
                Console.WriteLine("  - {0}", actor.Name);
                Console.WriteLine("\\tPersonal URI: {0}", actor.PersonalSiteUri);
                Console.WriteLine("\\tPicture URI: {0}", actor.ImageUri);
            }
        }
    }
}

```


## その他の技術情報
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 で他のユーザーをフォローする](follow-people-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 で JavaScript オブジェクト モデルを使用してユーザーをフォローする方法](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md)
    
  
-  [方法: SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してドキュメントとサイトをフォローする](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  

