---
title: SharePoint Server 2013 で投稿にイメージ、ビデオ、ドキュメントを埋め込む方法
ms.prod: SHAREPOINT
ms.assetid: 9927b9e7-daea-4261-80fa-4cc25f489e22
---


# SharePoint Server 2013 で投稿にイメージ、ビデオ、ドキュメントを埋め込む方法
 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) オブジェクトをミニブログの投稿に追加する方法を説明します。これらは SharePoint Server 2013 のソーシャル フィードに埋め込みのピクチャ、ビデオ、およびドキュメントとしてレンダリングされます。
ソーシャル フィードには、投稿のコンテンツの最も簡単な形式にはテキストのみが含まれますが、埋め込みのピクチャ、ビデオ、ドキュメントを追加することもできます。これを実行するには、投稿を定義する  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) プロパティを使用します。投稿には、 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) オブジェクトで表す 1 つの添付ファイルを含めることができます。
  
    
    


> **メモ**
> 投稿のコンテンツに説明、タグ、またはリンクを追加するには、 [SocialPostCreationData.ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) プロパティに [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) オブジェクトを追加します。詳細については、「 [[方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)」を参照してください。 
  
    
    


この記事で説明する API は, .NET クライアント オブジェクト モデルのものです。JavaScript オブジェクト モデルなど別の API を使用する場合は、オブジェクト名または対応する API が異なることがあります。関連 API のドキュメントへのリンクは、「 [その他の技術情報](#bk_addresources)」を参照してください。
  
    
    


## 添付ファイルを投稿に追加するコード例を使用するための前提条件
<a name="bk_preReqs"> </a>

この記事のコード例は、イメージ、ビデオ、およびドキュメントの添付ファイルをミニブログの投稿に追加する方法を示しています。これらの例は、次の SharePoint アセンブリを使用するコンソール アプリケーションのものです。
  
    
    

- Microsoft.SharePoint.Client
    
  
- Microsoft.SharePoint.Client.Runtime
    
  
- Microsoft.SharePoint.Client.UserProfilies
    
  
この記事の例を使用するには、イメージ、ビデオ、およびドキュメントをアップロードする必要があります。ビデオの例を使用するには、サーバーでビデオ機能が有効にされており、ビデオ ファイルがアセット ライブラリに保存されている必要があります。社内環境でドキュメントの例を使用するには、環境に Office Online が構成されている必要があります。詳細については、「 [SharePoint Server 2013 でデジタル アセット ライブラリを計画する](http://technet.microsoft.com/ja-jp/library/ee414275.aspx)」および「 [Office Online を使用するための SharePoint 2013 の構成](http://technet.microsoft.com/ja-jp/library/ff431687.aspx)」を参照してください。
  
    
    
開発環境を設定してコンソール アプリケーションを作成する方法の詳細については、「 [[方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)」を参照してください。
  
    
    

## 例: SharePoint Server 2013 で投稿にイメージを埋め込む
<a name="bkmk_addImage"> </a>

次のコード例では、埋め込みイメージを含む投稿を公開しています。次の操作方法を示しています。
  
    
    

- イメージを表す  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) オブジェクトを作成します。 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) は、 [SocialAttachmentKind.Image](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachmentKind.Image.aspx) フィールドとイメージ ファイルの URI を指定します。
    
  
- イメージ オブジェクトを、投稿の作成に使用する  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) プロパティに追加します。
    
  
コードを実行する前に、URL 変数のプレースホルダーの値を変更してください。
  
    
    



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


## SharePoint Server 2013 で投稿にビデオを埋め込む
<a name="bkmk_addVideo"> </a>

次のコード例では、埋め込みビデオを含む投稿を公開しています。次の操作方法を示しています。
  
    
    

-  [SocialFeedManager.GetPreview](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetPreview.aspx) メソッドを使用して、ビデオ添付ファイルを表す [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) オブジェクトを取得します。
    
  
- ビデオ添付ファイルを、投稿の作成に使用する  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) プロパティに追加します。
    
  
この例では、サーバーでビデオ機能が有効にされており、ビデオ ファイルがアセット ライブラリにアップロードされている必要があります。詳細については、 [コード例を使用するための前提条件](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md#bk_preReqs)を参照してください。
  
    
    
コードを実行する前に、URL 変数のプレースホルダーの値を変更してください。
  
    
    



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


## 例: SharePoint Server 2013 で投稿にドキュメントを埋め込む
<a name="bkmk_addDoc"> </a>

次のコード例では、埋め込みドキュメントを含む投稿を公開しています。次の操作方法を示しています。
  
    
    

-  [SocialFeedManager.GetPreview](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetPreview.aspx) メソッドを使用して、ドキュメント添付ファイルを表す [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) オブジェクトを取得します。
    
  
- ドキュメント添付ファイルを、投稿の作成に使用する  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) プロパティに追加します。
    
  
社内環境でこの例を使用するには、環境が Office Online を使用するように設定されている必要があります。 詳細については、 [コード例を使用するための前提条件](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md#bk_preReqs)を参照してください。または「 [[方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)」に説明するように、ドキュメントへのリンクを投稿できます。
  
    
    
コードを実行する前に、URL 変数のプレースホルダーの値を変更してください。
  
    
    



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


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
    
  
- クライアント オブジェクト モデルの  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) および [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx)
    
  
- JavaScript オブジェクト モデルの  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) および [SocialAttachment](http://msdn.microsoft.com/library/dfdee790-a1b0-19c8-0e92-5a6e058ba4db%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
- サーバー オブジェクト モデルの  [SPSocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPostCreationData.aspx) および [SPSocialAttachment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialAttachment.aspx)
    
  

