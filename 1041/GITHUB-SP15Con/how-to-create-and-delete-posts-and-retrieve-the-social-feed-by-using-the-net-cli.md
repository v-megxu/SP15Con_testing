---
title: [方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う
ms.prod: SHAREPOINT
ms.assetid: c8d68632-1b55-454c-961a-f3ddad731bf6
---


# [方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う
SharePoint 2013 .NET クライアント オブジェクト モデルを使用して、マイクロブログの投稿を作成および削除する方法とソーシャル フィードを取得する方法を説明します。
## SharePoint Server 2013のソーシャル フィードとは
<a name="bk_intro"> </a>

SharePoint Server 2013では、ソーシャル フィードは、会話、マイクロブログの個々の投稿、または通知を表すスレッドのコレクションです。スレッドには、最初の投稿と返信の投稿のコレクションか含まれ、これらは、会話、マイクロブログの個々の投稿、または通知を表します。.NET クライアント オブジェクト モデルでは、フィードは  [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) オブジェクトで表され、スレッドは [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) オブジェクトで表され、投稿と返信は [SocialPost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPost.aspx) オブジェクトで表されます。.NET クライアント オブジェクト モデルで、フィード関連の主なタスクを実行するには、 [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) オブジェクトを使用する必要があります。この記事では、ソーシャル フィードの操作に .NET クライアント オブジェクト モデルを使用するコンソール アプリケーションを作成する方法について説明します。
  
    
    
 [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) の操作や、他の API を使用したソーシャル フィードの操作の詳細については、「 [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)」を参照してください。
  
    
    

## SharePoint 2013の .NET クライアント オブジェクト モデルを使用してソーシャル フィードを操作する開発環境をセットアップするための前提条件
<a name="bkmk_SetUpDevEnv"> </a>

.NET クライアント オブジェクト モデルを使用してソーシャル フィードを操作するコンソール アプリケーションを作成するには、以下のものが必要になります。
  
    
    

- 個人用サイトが構成済みで、現在のユーザー用の個人サイトとターゲット ユーザー用の個人サイトを作成済みであり、ターゲット ユーザーを現在のユーザーがフォローしていて、ターゲット ユーザーによる投稿がいくつかある SharePoint Server 2013
    
  
- Visual Studio 2012
    
  
- ログオン ユーザー用に、User Profile Service アプリケーションの [ **フル コントロール**] アクセス許可
    
  

> **メモ**
> SharePoint Server 2013 を実行するコンピューター上で開発しない場合は、SharePoint 2013 クライアント アセンブリを含む  [SharePoint クライアント コンポーネント](http://www.microsoft.com/en-us/download/details.aspx?id=35585) ダウンロードを入手してください。
  
    
    


## SharePoint 2013の .NET クライアント オブジェクト モデルを使用してソーシャル フィードを操作するコンソール アプリケーションを作成する
<a name="bk_createconsole"> </a>


1. Visual Studio を開いて、[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。
    
  
2. [ **新しいプロジェクト**] ダイアログ ボックスの上部にあるドロップダウン リストから [ **.NET Framework 4.5**] を選択します。
    
  
3. [ **テンプレート**] リストで、[ **Windows**] を選択し、[ **コンソール アプリケーション**] テンプレートを選択します。
    
  
4. プロジェクト名に「SocialFeedCSOM」という名前を付け、[ **OK**] をクリックします。
    
  
5. 以下のアセンブリに参照を追加します。
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. **Program** クラスの内容を以下のいずれかのシナリオのコード例で置き換えます。
    
  -  [ソーシャル フィードへの投稿と返信の公開](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_PubPosts)
    
  
  -  [ソーシャル フィードの取得](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_GetFeeds)
    
  
  -  [ソーシャル フィードからの投稿と返信の削除](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_DeletePosts)
    
  
7. コンソール アプリケーションをテストするには、[ **デバッグ**] メニューの [ **デバッグ開始**] をクリックします。
    
  

## コード例: SharePoint 2013の .NET クライアント オブジェクト モデルを使用した、ソーシャル フィードへの投稿と返信の公開
<a name="bkmk_PubPosts"> </a>

以下のコードは、現在のユーザーから投稿と返信の公開を行う例です。以下の操作の方法が記述されています。
  
    
    

- 投稿内容を定義する。この例では、投稿にリンクが含まれています。
    
  
-  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) メソッドを使用し、 **null** を _targetId_ パラメーターの値として渡すことで、現在のユーザーのフィードに投稿を公開する。
    
  
-  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) メソッドを使用して、現在のユーザーの [News](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.News.aspx) フィード タイプを取得する。
    
  
- フィードを反復処理して返信可能なすべてのスレッドを検出し、スレッドと投稿に関する情報を取得する。
    
  
-  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) メソッドを使用し、スレッド ID を _targetId_ パラメーターとして渡すことで、投稿に返信する。
    
  

> **メモ**
> コードを実行する前に、 **serverUrl** 変数のプレースホルダーの値を変更してください。
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace SocialFeedCSOM
{
    class Program
    {
        static void Main(string[] args)
        {
            // Replace the following placeholder value with the target server URL.
            const string serverUrl = "http://serverName/";

            Console.Write("Type your post text:  ");

            // Create a link to include in the post.
            SocialDataItem linkDataItem = new SocialDataItem();
            linkDataItem.ItemType = SocialDataItemType.Link;
            linkDataItem.Text = "link";
            linkDataItem.Uri = "http://bing.com";

            // Define properties for the post.
            SocialPostCreationData postCreationData = new SocialPostCreationData();
            postCreationData.ContentText = Console.ReadLine() + " Plus a {0}.";
            postCreationData.ContentItems = new SocialDataItem[1] { linkDataItem };

            // Get the client context.
            ClientContext clientContext = new ClientContext(serverUrl);

            // Get the SocialFeedManager instance.
            SocialFeedManager feedManager = new SocialFeedManager(clientContext);

            // Publish the post. This is a root post, so specify null for the
            // targetId parameter. 
            feedManager.CreatePost(null, postCreationData); 
            clientContext.ExecuteQuery();

            Console.WriteLine("\\nCurrent user's newsfeed:");

            // Set parameters for the feed content that you want to retrieve.
            SocialFeedOptions feedOptions = new SocialFeedOptions();

            // Get the target owner's feed and then run the request on the server.
            ClientResult<SocialFeed> feed = feedManager.GetFeed(SocialFeedType.News, feedOptions);
            clientContext.ExecuteQuery();

            // Create a dictionary to store the Id property of each thread. This 
            // code example stores the Id so you can select a thread to reply to.
            Dictionary<int, string> idDictionary = new Dictionary<int, string>();

            // Iterate through each thread in the feed.
            for (int i = 0; i < feed.Value.Threads.Length; i++)
            {
                SocialThread thread = feed.Value.Threads[i];

                // Keep only the threads that can be replied to.
                if (thread.Attributes.HasFlag(SocialThreadAttributes.CanReply))
                {
                    idDictionary.Add(i, thread.Id);

                    // Get properties from the root post and thread.
                    // If a thread contains more than two replies, the server returns
                    // a thread digest that contains only the two most recent replies.
                    // To get all replies, call SocialFeedManager.GetFullThread.
                    SocialPost rootPost = thread.RootPost;
                    SocialActor author = thread.Actors[rootPost.AuthorIndex];
                    Console.WriteLine(string.Format("{0}. {1} said \\"{2}\\" ({3} replies)",
                        (i + 1), author.Name, rootPost.Text, thread.TotalReplyCount));
                }
            }
            Console.Write("\\nWhich thread number do you want to reply to?  ");

            string threadToReplyTo = "";
            int threadNumber = int.Parse(Console.ReadLine()) - 1;
            idDictionary.TryGetValue(threadNumber, out threadToReplyTo);

            Console.Write("Type your reply:  ");

            // Define properties for the reply. This example reuses the 
            // SocialPostCreationData object that was used to create a post.
            postCreationData.ContentText = Console.ReadLine();

            // Publish the reply and make the changes on the server.
            ClientResult<SocialThread> result = feedManager.CreatePost(threadToReplyTo, postCreationData);
            clientContext.ExecuteQuery();

            Console.WriteLine("\\nThe reply was published. The thread now has {0} replies.", result.Value.TotalReplyCount);
            Console.ReadLine();
         }
    }
}
```


## コード例: SharePoint 2013の .NET クライアント オブジェクト モデルを使用した、ソーシャル フィードの取得
<a name="bkmk_GetFeeds"> </a>

次のコード例では、現在のユーザーとターゲット ユーザーのフィードを取得します。以下の操作方法が記述されています。
  
    
    

-  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) メソッドを使用して、現在のユーザーの [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) 、 [News](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.News.aspx) 、および [Timeline](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Timeline.aspx) のフィード タイプを取得する。
    
  
-  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) メソッドを使用して、ターゲット ユーザーの [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) フィード タイプを取得する。
    
  
- フィードを反復処理して非参照スレッドをすべて検出し、それらのスレッドと投稿に関する情報を取得する。参照スレッドは、別のスレッドに関する情報を含む通知を表します。たとえば、誰かに関するユーザーのメンションが投稿内にあると、元の投稿へのリンクと投稿についての他のメタデータを含む  [MentionReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.MentionReference.aspx) 型のスレッドがサーバーによって生成されます。
    
  
フィード タイプの詳細については、「 [フィード タイプの概要](work-with-social-feeds-in-sharepoint-2013.md#bkmk_FeedTypes)」を参照してください。参照スレッドの詳細については、「 [SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)」を参照してください。
  
    
    

> **メモ**
> コードを実行する前に、変数 **serverUrl** と **targetUser** のプレースホルダーの値を変更してください。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace SocialFeedCSOM
{
    class Program
    {
        static string owner;
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the target
            // server URL and target thread owner.
            const string serverUrl = "http://serverName/";
            const string targetUser = "domainName\\\\userName";

            // Get the client context.
            ClientContext clientContext = new ClientContext(serverUrl);

            // Get the SocialFeedManager instance. 
            // Load the instance to get the Owner property.
            SocialFeedManager feedManager = new SocialFeedManager(clientContext);
            clientContext.Load(feedManager, f => f.Owner);

            // Set parameters for the feed content that you want to retrieve.
            SocialFeedOptions feedOptions = new SocialFeedOptions();
            feedOptions.MaxThreadCount = 10; // default is 20

            // Get all feed types for current user and get the Personal feed
            // for the target user.
            ClientResult<SocialFeed> personalFeed = feedManager.GetFeed(SocialFeedType.Personal, feedOptions);
            ClientResult<SocialFeed> newsFeed = feedManager.GetFeed(SocialFeedType.News, feedOptions);
            ClientResult<SocialFeed> targetUserFeed = feedManager.GetFeedFor(targetUser, feedOptions);

            // Change the sort order to optimize the Timeline feed results.
            feedOptions.SortOrder = SocialFeedSortOrder.ByCreatedTime;
            ClientResult<SocialFeed> timelineFeed = feedManager.GetFeed(SocialFeedType.Timeline, feedOptions);

            // Run the request on the server.
            clientContext.ExecuteQuery();

            // Get the name of the current user within this instance.
            owner = feedManager.Owner.Name;

            // Iterate through the feeds and write the content.
            IterateThroughFeed(personalFeed.Value, SocialFeedType.Personal, true);
            IterateThroughFeed(newsFeed.Value, SocialFeedType.News, true);
            IterateThroughFeed(timelineFeed.Value, SocialFeedType.Timeline, true);
            IterateThroughFeed(targetUserFeed.Value, SocialFeedType.Personal, false);

            Console.ReadKey(false);
        }

        // Iterate through the feed and write to the console window.
        static void IterateThroughFeed(SocialFeed feed, SocialFeedType feedType, bool isCurrentUserOwner)
        {
            SocialThread[] threads = feed.Threads;

            // If this is the target user's feed, get the user's name.
            // A user is the owner of all threads in his or her Personal feed.
            if (!isCurrentUserOwner)
            {
                SocialThread firstThread = threads[0];
                owner = firstThread.Actors[firstThread.OwnerIndex].Name;
            }
            Console.WriteLine(string.Format("\\n{0} feed type for {1}:", feedType.ToString(), owner));

            // Iterate through each thread in the feed.
            foreach (SocialThread thread in threads)
            {

                // Ignore reference thread types.
                if (thread.ThreadType == SocialThreadType.Normal)
                {

                    // Get properties from the root post and thread. 
                    // If a thread contains more than two replies, the server returns
                    // a thread digest that contains only the two most recent replies.
                    // To get all replies, call SocialFeedManager.GetFullThread.
                    SocialPost rootPost = thread.RootPost;
                    SocialActor author = thread.Actors[rootPost.AuthorIndex];
                    Console.WriteLine(string.Format("  - {0} posted \\"{1}\\" on {2}. This thread has {3} replies.",
                        author.Name, rootPost.Text, rootPost.CreatedTime.ToShortDateString(), thread.TotalReplyCount));
                }
            }
        }
    }
}
```


## コード例: SharePoint 2013の .NET クライアント オブジェクト モデルを使用した、ソーシャル フィードからの投稿と返信の削除
<a name="bkmk_DeletePosts"> </a>

次のコードは、現在のユーザーの個人フィードから投稿または返信を削除する例です。以下の操作方法が記述されています。
  
    
    

-  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) メソッドを使用して、現在のユーザーの [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) フィード タイプを取得する。
    
  
- フィード内のスレッドを反復処理し、最初の投稿と返信に関する情報を取得する。
    
  
-  [DeletePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.DeletePost.aspx) メソッドを使用して、最初の投稿、返信、またはスレッドを削除する (最初の投稿を削除するとスレッド全体が削除される)。
    
  

> **メモ**
> コードを実行する前に、 **serverUrl** 変数のプレースホルダーの値を変更してください。
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace SocialFeedCSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder value with the target SharePoint server.
            const string serverUrl = "http://serverName/";

            // Get the client context.
            ClientContext clientContext = new ClientContext(serverUrl);

            // Get the SocialFeedManager instance.
            SocialFeedManager feedManager = new SocialFeedManager(clientContext);

            Console.WriteLine("\\nCurrent user's personal feed:");

            // Set the parameters for the feed content that you want to retrieve.
            SocialFeedOptions feedOptions = new SocialFeedOptions();

            // Get the target owner's feed (posts and activities) and
            // then run the request on the server.
            ClientResult<SocialFeed> feed = feedManager.GetFeed(SocialFeedType.Personal, feedOptions);
            clientContext.ExecuteQuery();

            // Create a dictionary to store the Id property of each post and
            // reply. This code example stores the Id so you can select a post
            // or a reply to delete.
            Dictionary<int, string> idDictionary = new Dictionary<int, string>();

            // Iterate through each thread in the feed.
            for (int i = 0; i < feed.Value.Threads.Length; i++)
            {
                SocialThread thread = feed.Value.Threads[i];
                SocialPost rootPost = thread.RootPost;

                // Only keep posts that can be deleted.
                if (rootPost.Attributes.HasFlag(SocialPostAttributes.CanDelete)) 
                {
                    idDictionary.Add(i, rootPost.Id);

                    Console.WriteLine(string.Format("{0}. \\"{1}\\" has {2} replies.",
                        (i + 1), rootPost.Text, thread.TotalReplyCount));

                    // Get the replies.
                    // If a thread contains more than two replies, the server returns
                    // a thread digest that contains only the two most recent replies.
                    // To get all replies, call SocialFeedManager.GetFullThread.
                    if (thread.TotalReplyCount > 0)
                    {
                        foreach (SocialPost reply in thread.Replies)
                        {

                            // Only keep replies that can be deleted.
                            if (reply.Attributes.HasFlag(SocialPostAttributes.CanDelete)) 
                            {
                                i++;
                                idDictionary.Add(i, reply.Id);

                                SocialActor author = thread.Actors[reply.AuthorIndex];
                                Console.WriteLine(string.Format("\\t{0}. {1} replied \\"{2}\\"",
                                    (i + 1), author.Name, reply.Text));
                            }
                        }
                    }
                }
            }
            Console.Write("\\nEnter the number of the post or reply to delete. "
                + "(If you choose a root post, the whole thread is deleted.)");
            string postToDelete = "";
            int postNumber = int.Parse(Console.ReadLine()) - 1;
            idDictionary.TryGetValue(postNumber, out postToDelete);

            // Delete the reply and make the changes on the server.
            ClientResult<SocialThread> result = feedManager.DeletePost(postToDelete);
            clientContext.ExecuteQuery();

            // DeletePost returns digest thread if the deleted post is not the
            // root post. If it is the root post, the whole thread is deleted
            // and DeletePost returns null.
            if (result.Value != null)
            {
                SocialThread threadResult = result.Value;
                Console.WriteLine("\\nThe reply was deleted. The thread now has {0} replies.", threadResult.TotalReplyCount);
            }
            else
            {
                Console.WriteLine("\\nThe post and thread were deleted.");
            }
            Console.ReadKey(false);
        }
    }
}
```


## 次の手順
<a name="bkmk_DeletePosts"> </a>

 [[方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
  
    
    

## その他の技術情報
<a name="bk_addResources"> </a>


-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 で JavaScript オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)
    
  
-  [[方法] SharePoint 2013 の REST サービスを使用してソーシャル フィードに対する読み書きを行う](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [SharePoint Server 2013 ソーシャル フィードでの参照スレッドおよびダイジェスト スレッド](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  

