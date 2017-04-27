---
title: 如何：在 SharePoint Server 2013 中的文章中嵌入图像、视频和文档
ms.prod: SHAREPOINT
ms.assetid: 9927b9e7-daea-4261-80fa-4cc25f489e22
---


# 如何：在 SharePoint Server 2013 中的文章中嵌入图像、视频和文档
了解如何将  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 对象添加到微博文章，它们将呈现为 SharePoint Server 2013 好友动态订阅源中的嵌入式图片、视频和文档。
在好友动态订阅源中，形式最简单的帖子内容仅包含文本，但是您也可以添加嵌入式图片、视频或文档。为此，您可以针对定义帖子的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象使用 [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) 属性。帖子可以包含一个附件，由 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 对象表示。
  
    
    


> **注释**
> 若要向帖子内容中添加提及、标签或链接，您可以将  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) 对象添加到 [SocialPostCreationData.ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) 属性中。有关详细信息，请参阅 [如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)。 
  
    
    


本文所述的 API 来自 .NET 客户端对象模型。如果您使用的是 JavaScript 对象模型等其他 API，则对象名称或相应 API 可能有所不同。有关指向相关 API 文档的链接，请参阅 [其他资源](#bk_addresources)。
  
    
    


## 使用代码示例向帖子添加附件的先决条件
<a name="bk_preReqs"> </a>

本文的代码示例演示了如何将图像、视频和文档附件添加到微博帖子中。这些示例来自使用以下 SharePoint 程序集的控制台应用程序：
  
    
    

- Microsoft.SharePoint.Client
    
  
- Microsoft.SharePoint.Client.Runtime
    
  
- Microsoft.SharePoint.Client.UserProfilies
    
  
若要使用本文中的示例，您需要上载图像、视频和文档。若要使用视频示例，服务器必须启用视频功能，并且视频文件必须存储在资产库中。若要在本地环境中使用文档示例，必须在该环境中配置 Office Online。有关详细信息，请参阅 [在 SharePoint Server 2013 中规划数字资产库](http://technet.microsoft.com/zh-cn/library/ee414275.aspx)和 [配置 SharePoint 2013 以使用 Office Online](http://technet.microsoft.com/zh-cn/library/ff431687.aspx)。
  
    
    
有关如何设置开发环境和创建控制台应用程序的说明，请参阅 [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型创建和删除帖子以及检索好友动态订阅源](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)。
  
    
    

## 示例：在 SharePoint Server 2013 的帖子中嵌入图像
<a name="bkmk_addImage"> </a>

以下代码示例发布了一个包含嵌入式图像的帖子。它演示了如何执行以下操作：
  
    
    

- 创建代表图像的  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 对象。 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 指定了图像文件的 [SocialAttachmentKind.Image](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachmentKind.Image.aspx) 字段和 URI。
    
  
- 将图像对象添加到用于创建帖子的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) 属性。
    
  
运行代码前更改 URL 变量的占位符值。
  
    
    



```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace EmbedImageInPost
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace the following placeholder values with the actual values.
            const string serverUrl = "http://serverName/siteName/";
            const string imageUrl = "http://serverName/Shared%20Documents/imageName.jpg";

            // Define the image attachment that you want to embed in the post.
            SocialAttachment attachment = new SocialAttachment()
            {
                AttachmentKind = SocialAttachmentKind.Image,
                Uri = imageUrl
            };

            // Define properties for the post and add the attachment.
            SocialPostCreationData postCreationData = new SocialPostCreationData();
            postCreationData.ContentText = "Look at this!";
            postCreationData.Attachment = attachment;

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


## 在 SharePoint Server 2013 的帖子中嵌入视频
<a name="bkmk_addVideo"> </a>

以下代码示例发布了一个包含嵌入式视频的帖子。它演示了如何执行以下操作：
  
    
    

- 通过使用  [SocialFeedManager.GetPreview](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetPreview.aspx) 方法获取代表视频附件的 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 对象。
    
  
- 将视频附件添加到用于创建帖子的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) 属性。
    
  
本示例需要服务器启用视频功能，并将视频文件上载到资产库。有关详细信息，请参阅 [使用代码示例的先决条件](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md#bk_preReqs)。
  
    
    
运行代码前更改 URL 变量的占位符值。
  
    
    



```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace EmbedVideoInPost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Replace the following placeholder values with the actual values.
            const string serverUrl = "http://serverName/siteName/";
            const string videoUrl = "http://serverName/Asset%20Library/fileName?Web=1";

            try
            {

                // Get the context and the SocialFeedManager instance.
                ClientContext clientContext = new ClientContext(serverUrl);
                SocialFeedManager feedManager = new SocialFeedManager(clientContext);

                // Get the video attachment from the server.
                ClientResult<SocialAttachment> attachment = feedManager.GetPreview(videoUrl);
                clientContext.ExecuteQuery();

                // Define properties for the post and add the attachment.
                SocialPostCreationData postCreationData = new SocialPostCreationData();
                postCreationData.ContentText = "Look at this!";
                postCreationData.Attachment = attachment.Value;

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


## 示例：在 SharePoint Server 2013 的帖子中嵌入文档
<a name="bkmk_addDoc"> </a>

以下代码示例发布了一个包含嵌入式文档的帖子。它演示了如何执行以下操作：
  
    
    

- 通过使用  [SocialFeedManager.GetPreview](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetPreview.aspx) 方法获取代表文档附件的 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) 对象。
    
  
- 将文档附件添加到用于创建帖子的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 对象的 [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) 属性。
    
  
若要在本地环境中使用本示例，该环境必须配置为使用 Office Online。有关详细信息，请参阅 [使用代码示例的先决条件](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md#bk_preReqs)。或者，您可以按照 [如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)所述，发布一个指向文档的链接。
  
    
    
运行代码前更改 URL 变量的占位符值。
  
    
    



```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.SharePoint.Client;
using Microsoft.SharePoint.Client.Social;

namespace EmbedDocumentInPost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Replace the following placeholder values with the actual values.
            const string serverUrl = "http://serverName";
            const string documentUrl = "http://serverName/Shared%20Documents/fileName.docx";

            try
            {

                // Get the context and the SocialFeedManager instance.
                ClientContext clientContext = new ClientContext(serverUrl);
                SocialFeedManager feedManager = new SocialFeedManager(clientContext);

                // Get the document attachment from the server.
                ClientResult<SocialAttachment> attachment = feedManager.GetPreview(documentUrl);
                clientContext.ExecuteQuery();

                // Define properties for the post and add the attachment.
                SocialPostCreationData postCreationData = new SocialPostCreationData();
                postCreationData.ContentText = "Post with a document.";
                postCreationData.Attachment = attachment.Value;

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
    
  
-  [如何：在 SharePoint Server 2013 中的帖子中包括有关记录、标签以及网站和文档链接](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
    
  
- 客户端对象模型中的  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) 和 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx)
    
  
- JavaScript 对象模型中的  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) 和 [SocialAttachment](http://msdn.microsoft.com/library/dfdee790-a1b0-19c8-0e92-5a6e058ba4db%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
- 服务器对象模型中的  [SPSocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPostCreationData.aspx) 和 [SPSocialAttachment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialAttachment.aspx)
    
  

