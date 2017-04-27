---
title: 如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源
ms.prod: SHAREPOINT
ms.assetid: c8d68632-1b55-454c-961a-f3ddad731bf6
---


# 如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源
学习如何使用 SharePoint 2013 .NET 客户端对象模型创建和删除微博帖子及检索好友动态订阅源。
## 在 SharePoint Server 2013 中，什么是好友动态？
<a name="bk_intro"> </a>

在 SharePoint Server 2013 中，好友动态订阅源指代表对话、单条微博帖子或通知的线索的集合。线索包括根帖和回帖集合，并且其代表对话、单条微博帖子或通知。在 .NET 客户端对象模型中，订阅源用  [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) 对象表示，线索用 [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) 对象表示，帖子和回复用 [SocialPost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPost.aspx) 对象表示。要在 .NET 客户端对象模型中执行与订阅源相关的核心任务，请使用 [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) 对象。在本文中，我们将向您展示如何创建使用 .NET 客户端对象模型来处理好友动态订阅源的控制台应用程序。
  
    
    
有关使用  [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) 的详细信息或使用其他 API 来处理好友动态订阅源的信息，请参阅 [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)。
  
    
    

## 设置开发环境以使用 SharePoint 2013 .NET 客户端对象模型来处理好友动态订阅源的先决条件
<a name="bkmk_SetUpDevEnv"> </a>

要创建使用 .NET 客户端对象模型来处理好友动态订阅源的控制台应用程序，您将需要：
  
    
    

- 配置了我的网站、为当前用户和目标用户创建了个人网站、当前用户跟随目标用户、目标用户编写了几条帖子的 SharePoint Server 2013
    
  
- Visual Studio 2008
    
  
- 登录用户 User Profile service 应用程序的"完全控制"访问权限
    
  

> **注释**
> 如果您不是在运行 SharePoint Server 2013 的计算机上开发，则下载包含 SharePoint 2013 客户端程序集的  [SharePoint 客户端组件](http://www.microsoft.com/en-us/download/details.aspx?id=35585)。 
  
    
    


## 创建通过使用 SharePoint 2013 .NET 客户端模型处理好友动态订阅源的控制台应用程序
<a name="bk_createconsole"> </a>


1. 打开 Visual Studio，然后依次选择"文件"、"新建"、"项目"。
    
  
2. 在"新建项目"对话框中，从对话框顶部的下拉列表中选择".NET Framework 4.5"。
    
  
3. 在"模板"列表中，选择"Windows"，然后选择"控制台应用程序"模板。
    
  
4. 将项目命名为 SocialFeedCSOM，然后选择"确定"按钮。
    
  
5. 将引用添加到以下程序集：
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. 将 **Program** 类的内容替换为以下其中一个方案的代码示例：
    
  -  [发布帖子和回复好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_PubPosts)
    
  
  -  [检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_GetFeeds)
    
  
  -  [删除好友动态订阅源中的帖子和回复](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_DeletePosts)
    
  
7. 要测试控制台应用程序，请在菜单栏上，依次选择"调试"、"开始调试"。
    
  

## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型发布文章和回复到好友动态
<a name="bkmk_PubPosts"> </a>

下面的代码示例发布当前用户的帖子和回复。它演示了如何：
  
    
    

- 定义文章内容。 此示例包括了该文章中的一个链接。
    
  
- 使用  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) 方法并将 **null** 作为 _targetId_ 参数传递将帖子发布到当前用户的订阅源
    
  
- 使用  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) 方法获取当前用户的 [News](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.News.aspx) 订阅源类型。
    
  
- 循环访问该订阅源，找出所有可以回复的线索并获取线索和帖子的相关信息。
    
  
- 通过使用  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) 方法并将线索标识符作为 _targetId_ 参数传递来回复帖子。
    
  

> **注释**
> 运行代码前更改 **serverUrl** 变量的占位符值。
  
    
    


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


## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型检索好友动态订阅源
<a name="bkmk_GetFeeds"> </a>

以下代码示例检索了当前用户和目标用户的动态。 它显示如何：
  
    
    

- 使用  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) 方法获取当前用户的 [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) 、 [News](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.News.aspx) 和 [Timeline](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Timeline.aspx) 订阅源类型。
    
  
- 使用  [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) 方法获取目标用户的 [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) 订阅源类型。
    
  
- 循环访问订阅源以查找所有非引用线索并获取有关线索和文章的信息。引用线索表示包含有关另一个线索的信息的通知。例如，如果用户在帖子中提到某人，则服务器将生成包含指向原帖和帖子其他元数据的链接的  [MentionReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.MentionReference.aspx) 类型线索。
    
  
有关订阅源类型的详细信息，请参阅 [订阅源类型概览](work-with-social-feeds-in-sharepoint-2013.md#bkmk_FeedTypes)。有关引用线索的详细信息，请参阅 [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)。
  
    
    

> **注释**
> 运行代码前更改 **serverUrl** 和 **targetUser** 变量的占位符值。
  
    
    




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


## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型删除好友动态订阅源中的帖子和回复
<a name="bkmk_DeletePosts"> </a>

下面的代码示例删除当前用户个人订阅源中的帖子或回复。它显示如何：
  
    
    

- 使用  [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) 方法获取当前用户的 [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) 订阅源类型。
    
  
- 循环访问订阅源中的线索，以获取根帖和回复的相关信息。
    
  
- 使用  [DeletePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.DeletePost.aspx) 方法删除根帖、回复或线索（删除根帖将删除整个线索）。
    
  

> **注释**
> 运行代码前更改 **serverUrl** 变量的占位符值。
  
    
    


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


## 后续步骤
<a name="bkmk_DeletePosts"> </a>

 [如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
  
    
    

## 其他资源
<a name="bk_addResources"> </a>


-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 JavaScript 对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)
    
  
-  [如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [SharePoint Server 2013 好友动态订阅源中的引用线索和摘要线索](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  

