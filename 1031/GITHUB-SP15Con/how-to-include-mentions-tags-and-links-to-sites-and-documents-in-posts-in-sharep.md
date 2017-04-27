---
title: Vorgehensweise erwähnt, Kategorien und Links zu Seiten und Dokumenten in Beiträge im SharePoint Server 2013 einschließen
ms.prod: SHAREPOINT
ms.assetid: 975da333-372b-4bf6-a3f4-7452db369f04
---


# Vorgehensweise: erwähnt, Kategorien und Links zu Seiten und Dokumenten in Beiträge im SharePoint Server 2013 einschließen
In diesem Artikel erfahren Sie, wie Sie Mikroblogbeiträgen  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) -Objekte hinzufügen, die als Erwähnungen, Tags oder Links in sozialen Feeds für SharePoint Server 2013 gerendert werden.
In einem Feed für soziale Netzwerke die einfachste Form der Post-Inhalte nur Text enthält, aber Sie können auch Links, die als erwähnungen, Tags oder Links zu Websites, SharePoint-Websites und Dokumenten Rendern hinzufügen. Zu diesem Zweck fügen Sie  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) -Objekte der [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das im Beitrag definiert. Beiträge können mehrere Links enthalten.
  
    
    


> **HINWEIS**
> Um eingebettete Bilder, Videos und Dokumente ein Beitrag Inhalt hinzuzufügen, fügen Sie ein  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) -Objekt an die [SocialPostCreationData.Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) -Eigenschaft. Weitere Informationen finden Sie unter [Vorgehensweise: Bilder, Videos und Dokumente in Bereitstellungen von SharePoint Server 2013 einbetten](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md).
  
    
    


Die in diesem Artikel beschriebene API hat ihren Ursprung des Clientobjektmodells .NET. Jedoch, wenn Sie eine andere API verwenden, möglicherweise wie die JavaScript-Objektmodell, den zu verwendenden Objektnamen oder die dazugehörige API abweichen. Links zur Dokumentation für verwandte APIs finden Sie unter  [Zusätzliche Ressourcen](#bk_addresources) .
  
    
    


## Voraussetzung für die Verwendung der Codebeispiele Links auf einen Beitrag in SharePoint Server 2013 hinzufügen
<a name="bk_preReqs"> </a>

Die Codebeispiele in diesem Artikel zeigen, wie Links Microblog Beiträge hinzugefügt. In diesen Beispielen werden von konsolenanwendungen, die die folgenden SharePoint-Assemblys verwenden:
  
    
    

- Microsoft.SharePoint.Client
    
  
- Microsoft.SharePoint.Client.Runtime
    
  
- Microsoft.SharePoint.Client.UserProfilies
    
  
Weitere Informationen zum Einrichten Ihrer Entwicklungsumgebung und Erstellen einer Konsolenanwendung finden Sie unter  [Vorgehensweise: Erstellen und Löschen von Beiträge und Abrufen des für soziale Netzwerke-Feed mithilfe des clientobjektmodells .NET SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md).
  
    
    

## Beispiel: Enthalten Sie Links zu Websites, SharePoint-Websites und Dokumenten in einer POST-Anforderung in SharePoint Server 2013
<a name="bkmk_addLinks"> </a>

Im folgenden Codebeispiel wird veröffentlicht einen Beitrag, der Links zu einer Website und einer SharePoint-Website zu einem Dokument enthält. Außerdem wird gezeigt, wie Sie:
  
    
    

- Erstellen Sie  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) -Objekten, die Links darstellen. Jede Instanz wird das Feld [SocialDataItemType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.aspx) für den Link, der Anzeigetext für den Link, und den Link URI festgelegt.
    
  
- Hinzufügen von Platzhaltern für den Post-Text um anzugeben, wo Anzeigetext für den Link angezeigt werden soll.
    
  
- Fügen Sie die Link-Objekten der  [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das zum Erstellen der POST-Anforderung verwendet wird.
    
  

> **HINWEIS**
> Wählen derzeit SharePoint Server 2013 Handles Links zu Websites, SharePoint-Websites und Dokumenten in die gleiche Weise, aber es empfiehlt sich, die  [Site](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Site.aspx) und [Document](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Document.aspx) Typ für SharePoint-Websites und Dokumenten.
  
    
    

In den Feed für soziale Netzwerke wird das Element in einem separaten Browserfenster geöffnet, wenn Sie auf den Link auf eine Website, eine SharePoint-Website oder ein Dokument.
  
    
    

> **HINWEIS**
> Ändern Sie die Platzhalterwerte für die URL-Variablen vor dem Ausführen des Codes.
  
    
    




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


## Beispiel: Erwähnen Sie eine Person in einem Beitrag in SharePoint Server 2013
<a name="bkmk_addMention"> </a>

Im folgenden Codebeispiel wird veröffentlicht einen Beitrag, der einen Benutzer erwähnt. Außerdem wird gezeigt, wie Sie:
  
    
    

- Erstellen Sie ein  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) -Objekt, um einen Vermerk darstellen, der eine Verknüpfung zu einem Benutzer ist. Die [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) gibt das [SocialDataItemType.User](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.User.aspx) -Feld und die weiter oben erwähnt Person Kontonamen. Sie können den Kontonamen mithilfe der Anmeldename der Person oder e-Mail-Adresse festlegen.
    
  
- Hinzufügen eines Platzhalters für den Post-Text um anzugeben, wo der weiter oben erwähnt Person Anzeigename angezeigt werden soll.
    
  
- Fügen Sie der  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) der [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das zum Erstellen der POST-Anforderung verwendet wird.
    
  
In den Feed für soziale Netzwerke leitet durch Klicken auf einen Hinweis auf die weiter oben erwähnt Person **zur** Seite.
  
    
    

> **HINWEIS**
> Ändern Sie die Platzhalterwerte für die Variablen **serverURL** und **accountName** vor dem Ausführen des Codes.
  
    
    




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


## Beispiel: Ein Tag in einer POST-Anforderung in SharePoint Server 2013 einschließen
<a name="bkmk_addTag"> </a>

Im folgenden Codebeispiel wird veröffentlicht einen Beitrag, der ein Tag enthält. Außerdem wird gezeigt, wie Sie:
  
    
    

- Erstellen Sie ein  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) -Objekt, um das Tag darstellen. Die [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) gibt das Feld [SocialDataItemType.Tag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItemType.Tag.aspx) und der Tagname, die ein **#** Zeichen enthalten muss.
    
  
- Hinzufügen eines Platzhalters für den Post-Text um anzugeben, wo das Tag angezeigt werden soll.
    
  
- Fügen Sie der  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) der [ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das zum Erstellen der POST-Anforderung verwendet wird.
    
  
In den Feed für soziale Netzwerke leitet durch Klicken auf ein Tag zu dem Tag **zur** Seite. Wenn das Tag nicht bereits vorhanden ist, der Server wird erstellt.
  
    
    

> **HINWEIS**
> Ändern Sie die Platzhalterwerte für die Variablen **serverURL** und **tagName** vor dem Ausführen des Codes.
  
    
    




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


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) und [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) in die Clientobjektmodelle
    
  
-  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) und [SocialDataItem](http://msdn.microsoft.com/library/757e7b62-66a6-b03f-0ff0-769a42eb2b4a%28Office.15%29.aspx) im JavaScript-Objektmodell
    
  
-  [REST-API-Referenz für sozialen Feed für SharePoint 2013](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SPSocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPostCreationData.aspx) und [SPSocialDataItem](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialDataItem.aspx) im Server-Objektmodell
    
  

