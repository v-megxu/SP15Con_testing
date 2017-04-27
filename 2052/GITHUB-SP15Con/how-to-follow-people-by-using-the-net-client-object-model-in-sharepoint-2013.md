---
title: 如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友
ms.prod: SHAREPOINT
ms.assetid: 0fdb7ca5-d408-4256-b52b-886c4bc3b5b8
---


# 如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注好友
了解如何通过 SharePoint Server 2013 .NET 客户端对象模型使用关注好友功能。
## 为什么在 SharePoint Server 2013 中使用关注好友功能？

在 SharePoint Server 2013 中，当用户关注了某人之后，被关注人的帖子和活动将显示在用户的新闻源中。通过使用"关注好友"功能来关注用户所关心的人，可以提高应用程序或解决方案的相关性。在 .NET 客户端对象模型中，您所关注的好友由  [SocialActor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialActor.aspx) 对象表示。若要在 .NET 客户端对象模型中执行"关注好友"的核心任务，请使用 [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) 对象。本文将说明如何通过 .NET 客户端对象模型使用以下"关注好友"功能。
  
    
    

> **注释**
> 我们之所以注重  [SocialFollowingManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.aspx) 是因为它融合了关注好友和内容的核心功能。但是， [PeopleManager](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PeopleManager.aspx) 对象还包含关注好友的其他功能，如可获取其他用户的以下状态的 [AmIFollowedBy(String)](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.UserProfiles.PeopleManager.AmIFollowedBy.aspx) 方法。
  
    
    


## 设置通过 SharePoint 2013 .NET 客户端对象模型使用关注好友功能的开发环境的先决条件

若要创建一个通过 .NET 客户端对象模型使用关注好友功能的控制台应用程序，您将需要具备以下条件：
  
    
    

- 配置有"我的网站"以及为当前用户和目标用户创建有用户配置文件和个人网站的 SharePoint Server 2013
    
  
- Visual Studio 2008
    
  
- 对所登录用户的 User Profile Service 应用程序具有"完全控制"访问权限
    
  

> **注释**
> 如果您没有在运行 SharePoint Server 2013 的计算机上进行开发，请下载包含 SharePoint 2013 客户端程序集的  [SharePoint 客户端组件](http://www.microsoft.com/en-us/download/details.aspx?id=35585)。 
  
    
    


## 在 Visual Studio 2008 中创建控制台应用程序
<a name="bkmk_CreateConsoleApp"> </a>


1. 打开 Visual Studio，依次选择"文件"、"新建"、"项目"。
    
  
2. 在"新建项目"对话框中，从对话框顶部的下拉列表中选择".NET Framework 4.5"。
    
  
3. 在"模板"列表中，选择"Windows"，然后选择"控制台应用程序"模板。
    
  
4. 将项目命名为 FollowPeopleCSOM，然后选择"确定"按钮。
    
  
5. 添加对以下程序集的引用：
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. 将 **Program** 类的内容替换为以下其中一个方案的代码示例：
    
  -  [开始和停止关注好友](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md#bkmk_FollowPeople)
    
  
  -  [获取粉丝和被关注人](how-to-follow-people-by-using-the-net-client-object-model-in-sharepoint-2013.md#bkmk_GetFollowednFollowers)
    
  
7. 若要测试控制台应用程序，请在菜单栏上，依次选择"调试"和"开始调试"。
    
  

## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型开始或停止关注好友
<a name="bkmk_FollowPeople"> </a>

以下代码示例使当前用户开始关注或停止关注某目标用户。该代码示例演示如何：
  
    
    

- 使用  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) 方法检查当前用户是否正在关注某目标用户。
    
  
- 使用  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) 方法获得当前用户所关注好友的个数。
    
  
- 使用  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) 方法开始关注目标用户。
    
  
- 使用  [StopFollowing](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.StopFollowing.aspx) 方法停止关注目标用户。
    
  
此代码示例使用由  [Follow](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.Follow.aspx) 方法返回的 [SocialFollowResult](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowResult.aspx) 对象确定是开始关注目标用户还是停止关注目标用户。
  
    
    

> **注释**
> 在运行代码之前，请先更改 **serverUrl** 和 **targetUser** 变量的占位符值。
  
    
    




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


## 代码示例：使用 SharePoint 2013 .NET 客户端对象模型获取粉丝和被关注人
<a name="bkmk_GetFollowednFollowers"> </a>

以下代码示例可获取当前用户正在关注的人，获取当前用户关注的人，并获取有关当前用户的"关注好友"状态的信息。该代码示例演示如何：
  
    
    

- 使用  [IsFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.IsFollowed.aspx) 方法检查当前用户是否正在关注某目标用户。
    
  
- 使用  [GetFollowedCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowedCount.aspx) 方法获得当前用户所关注好友的个数。
    
  
- 使用  [GetFollowed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowed.aspx) 方法获取当前用户正在关注的好友。
    
  
- 使用  [GetFollowers](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFollowingManager.GetFollowers.aspx) 方法获取正在关注当前用户的人员。
    
  
- 循环访问一组好友并获得每个人的显示名称、个人 URI 和照片 URI。
    
  

> **注释**
> 在运行代码之前，请先更改 **serverUrl** 和 **targetUser** 变量的占位符值。
  
    
    


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


## 其他资源
<a name="bkmk_AdditionalResources"> </a>


-  [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)
    
  
-  [如何：在 SharePoint 2013 中使用 JavaScript 对象模型关注好友](how-to-follow-people-by-using-the-javascript-object-model-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  

