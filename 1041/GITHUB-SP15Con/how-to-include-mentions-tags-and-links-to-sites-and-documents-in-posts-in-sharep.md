---
title: [方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法
ms.prod: SHAREPOINT
ms.assetid: 975da333-372b-4bf6-a3f4-7452db369f04
---


# [方法] SharePoint Server 2013 でメンション、タグ、サイトおよびドキュメントへのリンクを投稿に含める方法
 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) オブジェクトをミニブログの投稿に追加する方法を説明します。これらは SharePoint Server 2013 のソーシャル フィードにメンション、タグ、またはリンクとしてレンダリングされます。
ソーシャル フィードでは、最も簡単な形式の投稿コンテンツにはテキストのみが含まれますが、メンション、タグ、または Web サイト、SharePoint サイト、およびドキュメントへのリンクとしてレンダリングされるリンクを追加することもできます。これを行うには、 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) オブジェクトを、投稿を定義する [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) プロパティに追加します。投稿には複数のリンクを含めることができます。
  
    
    


> **メモ**
> 埋め込みの画像、ビデオ、またはドキュメントを投稿のコンテンツに追加するには、 [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) オブジェクトを [SocialPostCreationData.Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) プロパティに追加します。詳細については、「 [SharePoint Server 2013 で投稿にイメージ、ビデオ、ドキュメントを埋め込む方法](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md)」を参照してください。 
  
    
    


この記事で説明する API は, .NET クライアント オブジェクト モデルのものです。ただし、JavaScript オブジェクト モデルなど別の API を使用する場合は、オブジェクト名または対応する API が異なることがあります。関連 API のドキュメントへのリンクは、「 [その他の技術情報](#bk_addresources)」を参照してください。
  
    
    


## SharePoint Server 2013 でリンクを投稿に追加するコード例を使用するための前提条件
<a name="bk_preReqs"> </a>

この記事のコード例は、リンクをミニブログの投稿に追加する方法を示しています。これらの例は、次の SharePoint アセンブリを使用するコンソール アプリケーションのものです。
  
    
    

- Microsoft.SharePoint.Client
    
  
- Microsoft.SharePoint.Client.Runtime
    
  
- Microsoft.SharePoint.Client.UserProfilies
    
  
開発環境を設定してコンソール アプリケーションを使用する方法の詳細については、「 [[方法] SharePoint 2013 で .NET クライアント オブジェクト モデルを使用して投稿の作成と削除、およびソーシャル フィードの取得を行う](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)」を参照してください。
  
    
    

## 例: SharePoint Server 2013 で Web サイト、SharePoint サイト、およびドキュメントへのリンクを投稿に含める
<a name="bkmk_addLinks"> </a>

次のコード例では、Web サイト、SharePoint サイト、およびドキュメントへのリンクを含む投稿を公開します。方法は次のとおりです。
  
    
    

- リンクを表す  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) オブジェクトを作成します。各インスタンスでリンク タイプ用の [SocialDataItemType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.aspx) フィールド、リンク用の表示テキスト、およびリンクの URI を設定します。
    
  
- リンクの表示テキストを表示する場所を示すプレースホルダーを投稿テキストに追加します。
    
  
- リンクオブジェクトを、投稿の作成に使用する  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) プロパティに追加します。
    
  

> **メモ**
> 現在、SharePoint Server 2013 では Web サイト、SharePoint サイト、およびドキュメントへのリンクは同じように扱われますが、ベスト プラクティスとしては、SharePoint サイトおよびドキュメントには  [Site](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Site.aspx) タイプおよび [Document](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Document.aspx) タイプを選択してください。
  
    
    

ソーシャル フィードで Web サイト、SharePoint サイト、またはドキュメントへのリンクをクリックすると、そのアイテムが別個のブラウザー ウィンドウで開きます。
  
    
    

> **メモ**
> コードを実行する前に、URL 変数のプレースホルダーの値を変更してください。 
  
    
    




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


## 例: SharePoint Server 2013 の投稿で他のユーザーにメンションを付ける
<a name="bkmk_addMention"> </a>

次のコード例では、ユーザーにメンションを付ける投稿を公開します。方法は次のとおりです。
  
    
    

- ユーザーへのリンクであるメンションを表す  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) オブジェクトを作成します。 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) で、 [SocialDataItemType.User](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.User.aspx) フィールドとメンションを付けるユーザーのアカウント名を指定します。アカウント名は、ユーザーのログインまたは電子メール アドレスを使用して設定できます。
    
  
- メンションを付けるユーザーの表示名を表示する場所を示すプレースホルダーを投稿テキストに追加します。
    
  
- 投稿の作成に使用される  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) プロパティに [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) を追加します。
    
  
ソーシャル フィードでメンションをクリックすると、メンションを付けるユーザーの [ **詳細情報**] ページにリダイレクトされます。
  
    
    

> **メモ**
> コードを実行する前に、変数 **serverURL** と **accountName** のプレースホルダーの値を変更してください。
  
    
    




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


## 例: SharePoint Server 2013 で投稿にタグを含める
<a name="bkmk_addTag"> </a>

次のコード例では、タグを含む投稿を公開します。方法は次のとおりです。
  
    
    

- タグを表す  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) オブジェクトを作成します。 [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) で、 [SocialDataItemType.Tag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Tag.aspx) フィールドとタグ名を指定します。タグ名には **#** 文字を含める必要があります。
    
  
- タグを表示する場所を示すプレースホルダーを投稿テキストに追加します。
    
  
- 投稿の作成に使用される  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) オブジェクトの [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) プロパティに [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) を追加します。
    
  
ソーシャル フィードでタグをクリックすると、タグの [ **詳細情報**] ページにリダイレクトされます。タグがまだ存在しない場合は、サーバーによって作成されます。
  
    
    

> **メモ**
> コードを実行する前に、変数 **serverURL** と **tagName** のプレースホルダーの値を変更してください。
  
    
    




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


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 でのソーシャル フィードの操作](work-with-social-feeds-in-sharepoint-2013.md)
    
  
- クライアント オブジェクト モデルの  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) および [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx)
    
  
- JavaScript オブジェクト モデルの  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) および [SocialDataItem](http://msdn.microsoft.com/library/757e7b62-66a6-b03f-0ff0-769a42eb2b4a%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 ソーシャル フィード REST API リファレンス](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
- サーバー オブジェクト モデルの  [SPSocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPostCreationData.aspx) および [SPSocialDataItem](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialDataItem.aspx)
    
  

