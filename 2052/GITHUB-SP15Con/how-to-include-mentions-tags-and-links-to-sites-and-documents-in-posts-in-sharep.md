---
title: 如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接
ms.prod: SHAREPOINT
ms.assetid: 975da333-372b-4bf6-a3f4-7452db369f04
---


# 如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接
了解如何向微博帖子中添加  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 对象，以使其在 SharePoint Server 2013 好友动态订阅源中呈现为提及、标签或链接。
在好友动态订阅源中，最简单的帖子内容仅包含文本，但您也可以添加呈现为提及、标签的链接或指向网站、SharePoint 网站和文档的链接。为此，您可以将  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 对象添加到定义帖子的 [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) 属性中。帖子可以包含多个链接。
  
    
    


> **注释**
> 若要向帖子内容中添加嵌入图片、视频或文档，您可以将  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 对象添加到 [SocialPostCreationData.Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) 属性中。有关详细信息，请参阅 [如何：在 SharePoint Server 2013 中的文章中嵌入图像、视频和文档](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md)。 
  
    
    


本文所述 API 来自 .NET 客户端对象模型。但是，如果您使用的是诸如 JavaScript 对象模型的其他 API，则对象名称或相应的 API 可能有所不同。有关指向相关 API 文档的链接，请参阅 [其他资源](#bk_addresources)。
  
    
    


## 在 SharePoint Server 2013 中使用代码示例向帖子中添加链接的先决条件
<a name="bk_preReqs"> </a>

本文中的代码示例演示如何向微博帖子中添加链接。这些示例来自使用下列 SharePoint 程序集的控制台应用程序：
  
    
    

- Microsoft.SharePoint.Client
    
  
- Microsoft.SharePoint.Client.Runtime
    
  
- Microsoft.SharePoint.Client.UserProfilies
    
  
有关如何设置开发环境和创建控制台应用程序的说明，请参阅 [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)。
  
    
    

## 示例：在 SharePoint Server 2013 的帖子中包含指向网站、SharePoint 网站和文档的链接
<a name="bkmk_addLinks"> </a>

下面的代码示例发布包含指向网站、SharePoint 网站和文档的链接的帖子。它演示了如何：
  
    
    

- 创建代表这些链接的  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 对象。每个实例设置链接类型的 [SocialDataItemType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.aspx) 字段、链接的显示文本和链接 URI。
    
  
- 向帖子文本中添加占位符可指示应在何处呈现链接的显示文本。
    
  
- 将链接对象添加到用于创建帖子的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) 属性中。
    
  

> **注释**
> 当前，SharePoint Server 2013 采用相同的方法处理指向网站、SharePoint 网站和文档的链接，但对于 SharePoint 网站和文档，您最好分别选择  [Site](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Site.aspx) 类型和 [Document](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Document.aspx) 类型。
  
    
    

在好友动态订阅源中，单击指向网站、SharePoint 网站或文档的链接可在单独的浏览器窗口中打开项目。
  
    
    

> **注释**
> 运行代码前更改 URL 变量的占位符值。 
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace IncludeLinksInPost
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the actual values.
            const string serverUrl = "http://serverName/siteName/";
            const string websiteLinkUrl = "http://bing.com";
            const string siteLinkUrl = "http://serverName/siteName/";
            const string docLinkUrl = "http://serverName/Shared%20Documents/docName.txt";

            // Define the link to a website that you want to include in the post.
            SocialDataItem websiteLink = new SocialDataItem
            {
                ItemType = SocialDataItemType.Link,
                Text = "link to a website",
                Uri = websiteLinkUrl
            };

            // Define the link to a SharePoint site that you want to include in the post.
            SocialDataItem siteLink = new SocialDataItem
            {
                ItemType = SocialDataItemType.Site,
                Text = "link to a SharePoint site",
                Uri = siteLinkUrl
            };

            // Define the link to a document that you want to include in the post.
            SocialDataItem docLink = new SocialDataItem
            {
                ItemType = SocialDataItemType.Document,
                Text = "link to a document",
                Uri = docLinkUrl
            };

            // Add the links to the post's creation data.
            // Put placeholders ({n}) where you want the links to appear in the post text,
            // and then add the links to the post's content items.
            SocialPostCreationData postCreationData = new SocialPostCreationData();
            postCreationData.ContentText = "Check out this {0}, {1}, and {2}.";
            postCreationData.ContentItems = new SocialDataItem[3] { 
                    websiteLink, 
                    siteLink, 
                    docLink 
                };
            try
            {

                // Get the context and the SocialFeedManager instance.
                ClientContext clientContext = new ClientContext(serverUrl);
                SocialFeedManager feedManager = new SocialFeedManager(clientContext);

                // Publish the post. This is a root post to the user's feed, so specify
                // null for the targetId parameter.
                feedManager.CreatePost(null, postCreationData);
                clientContext.ExecuteQuery();
                Console.Write("The post was published.");
                Console.ReadLine();
            }
            catch (Exception ex)
            {
                Console.Write("Error publishing the post: " + ex.Message);
                Console.ReadLine();
            }
        }
    }
}

```


## 示例：在 SharePoint Server 2013 的帖子中提及某人
<a name="bkmk_addMention"> </a>

以下代码示例发布了一个提及某用户的帖子。它演示了如何：
  
    
    

- 创建代表提及的  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 对象，即指向某用户的链接。 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 指定 [SocialDataItemType.User](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.User.aspx) 字段和被提及人员的帐户名。您可以通过使用该人员的登录名或电子邮件地址设置帐户名。
    
  
- 向帖子文本中添加占位符可指示应在何处呈现被提及人员的显示名称。
    
  
- 将  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 添加到用于创建帖子的 [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) 属性中。
    
  
在好友动态订阅源中，单击某个提及可重定向到被提及人员的"关于"页面。
  
    
    

> **注释**
> 运行代码前更改 **serverURL** 和 **accountName** 变量的占位符值。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace IncludeMentionInPost
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the actual values.
            const string serverUrl = "http://serverName/siteName/";
            const string accountName = @"domain\\name or email address";

            // Define the mention link that you want to include in the post.
            SocialDataItem userMentionLink = new SocialDataItem
            {
                ItemType = SocialDataItemType.User,
                AccountName = accountName
            };

            // Add the mention to the post's creation data.
            // Put a placeholder ({0}) where you want the mention to appear in the post text,
            // and then add the mention to the post's content items.
            SocialPostCreationData postCreationData = new SocialPostCreationData();
            postCreationData.ContentText = "{0} does great work!";
            postCreationData.ContentItems = new SocialDataItem[1] { userMentionLink, };

            try
            {

                // Get the context and the SocialFeedManager instance.
                ClientContext clientContext = new ClientContext(serverUrl);
                SocialFeedManager feedManager = new SocialFeedManager(clientContext);

                // Publish the post. This is a root post to the user's feed, so specify
                // null for the targetId parameter.
                feedManager.CreatePost(null, postCreationData);
                clientContext.ExecuteQuery();
                Console.Write("The post was published.");
                Console.ReadLine();
            }
            catch (Exception ex)
            {
                Console.Write("Error publishing the post: " + ex.Message);
                Console.ReadLine();
            }
        }
    }
}

```


## 示例：在 SharePoint Server 2013 的帖子中包含标签
<a name="bkmk_addTag"> </a>

以下代码示例发布了一个包含标签的帖子。它演示了如何：
  
    
    

- 创建代表标签的  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 对象。 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 指定 [SocialDataItemType.Tag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Tag.aspx) 字段和标签名称，后者必须包含 **#** 字符。
    
  
- 向帖子文本中添加占位符可指示应在何处呈现标签。
    
  
- 将  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 添加到用于创建帖子的 [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) 属性中。
    
  
在好友动态订阅源中，单击标签可重定向到该标签的"关于"页面。如果该标签尚不存在，则服务器会创建它。
  
    
    

> **注释**
> 运行代码前更改 **serverURL** 和 **tagName** 变量的占位符值。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace IncludeTagInPost
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the actual values.
            const string serverUrl = "http://serverName/siteName/";
            const string tagName = "#" + "tagName";

            // Define the link to a tag that you want to include in the post. If the tag is new, the
            // server adds it to the tags collection.
            SocialDataItem tagLink = new SocialDataItem
            {
                ItemType = SocialDataItemType.Tag,
                Text = tagName
            };

            // Add the tag to the post's creation data.
            // Put a placeholder ({0}) where you want the tag to appear in the post text,
            // and then add the tag to the post's content items.
            SocialPostCreationData postCreationData = new SocialPostCreationData();
            postCreationData.ContentText = "I like {0}.";
            postCreationData.ContentItems = new SocialDataItem[1] { tagLink };

            try
            {

                // Get the context and the SocialFeedManager instance.
                ClientContext clientContext = new ClientContext(serverUrl);
                SocialFeedManager feedManager = new SocialFeedManager(clientContext);

                // Publish the post. This is a root post to the user's feed, so specify
                // null for the targetId parameter.
                feedManager.CreatePost(null, postCreationData);
                clientContext.ExecuteQuery();
                Console.Write("The post was published.");
                Console.ReadLine();
            }
            catch (Exception ex)
            {
                Console.Write("Error publishing the post: " + ex.Message);
                Console.ReadLine();
            }
        }
    }
}

```


## 其他资源
<a name="bk_addresources"> </a>


-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  
- 客户端对象模型中的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 和 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx)
    
  
- JavaScript 对象模型中的  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) 和 [SocialDataItem](http://msdn.microsoft.com/library/757e7b62-66a6-b03f-0ff0-769a42eb2b4a%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
- 服务器对象模型中的  [SPSocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPostCreationData.aspx) 和 [SPSocialDataItem](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialDataItem.aspx)
    
  

