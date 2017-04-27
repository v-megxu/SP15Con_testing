---
title: 如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站
ms.prod: SHAREPOINT
ms.assetid: 84366e01-4961-459d-8109-2f1d2d714353
---


# 如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站
了解如何通过 SharePoint Server 2013 .NET 客户端对象模型使用关注内容功能。
## 如何使用 .NET 客户端对象模型关注内容？
<a name="bk_intro"> </a>

SharePoint Server 2013 用户可以关注文档、网站和标签，以在其新闻源中获取关于项目的更新，并快速打开关注的文档和网站。您可以在应用程序或解决方案中使用 .NET 客户端对象模型，以开始和停止关注内容，并代表当前用户获取关注的内容。本文向您演示了如何创建一个通过 .NET 客户端对象模型对文档和网站使用关注内容功能的控制台应用程序。
  
    
    
以下对象是用于关注内容任务的主要 API：
  
    
    

-  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) 提供了用于管理用户的已关注好友列表的方法。
    
  
-  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 表示服务器响应客户端请求时返回的文档、网站或标记。
    
  
-  [SocialActorInfo](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorInfo.aspx) 指定客户端对服务器的请求中的文档、网站或标记。
    
  
-  [Microsoft.SharePoint.Client.Social.SocialActorType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorType.aspx) 和 [Microsoft.SharePoint.Client.Social.SocialActorTypes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActorTypes.aspx) 指定客户端对服务器的请求中的内容类型。
    
  

> **注释**
> 也可以将这些 API 用于关注好友任务，但  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) 中提供的 **GetSuggestions** 和 **GetFollowers** 方法仅支持关注好友，而不支持关注内容。有关如何使用 [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) 的详细信息，请参阅 [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)和 [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)。有关演示如何关注好友的代码示例，请参阅 [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)。 
  
    
    


## 设置通过 SharePoint 2013 .NET 客户端对象模型使用关注内容功能的开发环境的先决条件
<a name="bkmk_SetUpDevEnv"> </a>

若要创建一个通过 .NET 客户端对象模型对文档和网站使用关注内容功能的控制台应用程序，您将需要具备以下条件：
  
    
    

- 配置有"我的网站"、为当前用户创建有"我的网站"以及具有上载到 SharePoint 文档库的文档的 SharePoint Server 2013
    
  
- Visual Studio 2008
    
  
- 对所登录用户的 User Profile Service 应用程序具有"完全控制"访问权限
    
  

> **注释**
> 如果没有在运行 SharePoint Server 2013 的计算机上进行开发，请下载包含 SharePoint 2013 客户端程序集的  [SharePoint 客户端组件](http://www.microsoft.com/en-us/download/details.aspx?id=35585)。 
  
    
    


## 创建一个控制台应用程序以用于通过 SharePoint 2013 .NET 客户端对象模型使用关注内容功能
<a name="bkmk_CreateConsoleApp"> </a>


1. 在 Visual Studio 中，依次选择"文件"、"新建"、"项目"。
    
  
2. 在"新建项目"对话框中，从该对话框顶部的下拉列表中选择".NET Framework 4.5"。
    
  
3. 在"模板"列表中，选择"Windows"、然后选择"控制台应用程序"模板。
    
  
4. 将项目命名为 FollowContentCSOM，然后选择"确定"按钮。
    
  
5. 添加对以下程序集的引用：
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. 将 **Program** 类的内容替换为以下其中一个方案的代码示例：
    
  -  [开始和停止关注内容](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md#bkmk_FollowContent)
    
  
  -  [获取当前用户关注的内容](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md#bkmk_GetFollowed)
    
  
7. 若要测试控制台应用程序，请在菜单栏上，依次选择"调试"和"开始调试"。
    
  

## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型开始和停止关注内容
<a name="bkmk_FollowContent"> </a>

以下代码示例使当前用户开始关注或停止关注某目标项目。该代码示例演示如何：
  
    
    

- 使用  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) 方法检查当前用户是否正在关注特定文档或网站。
    
  
- 使用  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) 方法开始关注文档或网站。
    
  
- 使用  [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) 方法停止关注文档或网站。
    
  
- 使用  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) 方法获取当前用户正在关注的文档或网站的个数。
    
  
此代码示例使用由  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) 方法返回的 [SocialFollowResult](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowResult.aspx) 对象确定是开始关注目标项目还是停止关注目标项目。
  
    
    

> **注释**
> 在运行代码之前，请先更改 **serverUrl** 和 **contentUrl** 变量的占位符值。若要使用网站替代文档，请使用被注释掉的变量。
  
    
    




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


## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型获取关注的内容
<a name="bkmk_GetFollowed"> </a>

以下代码示例获取当前用户正在关注的文档和网站并获取有关用户的关注内容状态的信息。该代码示例演示如何：
  
    
    

- 使用  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) 方法检查当前用户是否正在关注目标文档和网站。
    
  
- 使用  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) 方法获取当前用户正在关注的文档和网站的个数。
    
  
- 使用  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) 方法获取当前用户正在关注的文档和网站。
    
  
- 循环访问内容组并获取每项的名称、内容 URI 和 URI。
    
  

> **注释**
> 在运行代码之前，请先更改 **serverUrl**, **docContentUrl** 和 **siteContentUrl** 变量的占位符值。
  
    
    


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


## 其他资源
<a name="bkmk_AddtionalResources"> </a>


-  [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md)
    
  

