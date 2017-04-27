---
title: Vorgehensweise Bilder, Videos und Dokumente in Bereitstellungen von SharePoint Server 2013 einbetten
ms.prod: SHAREPOINT
ms.assetid: 9927b9e7-daea-4261-80fa-4cc25f489e22
---


# Vorgehensweise: Bilder, Videos und Dokumente in Bereitstellungen von SharePoint Server 2013 einbetten
In diesem Artikel erfahren Sie, wie Sie Mikroblogbeiträgen  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) -Objekte hinzufügen, die als eingebettete Bilder, Videos und Dokumente in sozialen Feeds für SharePoint Server 2013 gerendert werden.
In einem Feed für soziale Netzwerke die einfachste Form der Post-Inhalte nur Text enthält, aber Sie können auch die eingebetteten Grafiken, Videos und Dokumente hinzufügen. Zu diesem Zweck verwenden Sie die  [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) -Eigenschaft auf das [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekt, das im Beitrag definiert. Beiträge können eine Anlage enthalten, die durch ein [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) -Objekt dargestellt wird.
  
    
    


> **HINWEIS**
> Um eine Erwähnung, Tag oder Link ein Beitrag Inhalt hinzuzufügen, fügen Sie ein  [SocialDataItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialDataItem.aspx) -Objekt an die [SocialPostCreationData.ContentItems](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.ContentItems.aspx) -Eigenschaft. Weitere Informationen finden Sie unter [Vorgehensweise: erwähnt, Kategorien und Links zu Seiten und Dokumenten in Beiträge im SharePoint Server 2013 einschließen](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md).
  
    
    


Die in diesem Artikel beschriebene API hat ihren Ursprung des Clientobjektmodells .NET. Wenn Sie eine andere API verwenden, kann beispielsweise die JavaScript-Objektmodell, den zu verwendenden Objektnamen oder die dazugehörige API abweichen. Links zur Dokumentation für verwandte APIs finden Sie unter  [Zusätzliche Ressourcen](#bk_addresources) .
  
    
    


## Voraussetzung für die Verwendung der Codebeispiele zum Hinzufügen von Anlagen auf einen Beitrag
<a name="bk_preReqs"> </a>

Die Codebeispiele in diesem Artikel wird gezeigt, wie hinzuzufügende Bild, video und Dokument Anlagen Microblog sendet. In diesen Beispielen werden über eine Konsolenanwendung, die die folgenden Assemblys SharePoint verwendet:
  
    
    

- Microsoft.SharePoint.Client
    
  
- Microsoft.SharePoint.Client.Runtime
    
  
- Microsoft.SharePoint.Client.UserProfilies
    
  
Um die Beispiele in diesem Artikel zu verwenden, müssen Sie ein Bild, Video und ein Dokument hochladen. Das video Beispiel verwenden zu können, muss die Videofunktion auf dem Server aktiviert werden, und die Videodatei muss in einer Objektbibliothek gespeichert werden. Um das Dokumentbeispiel in einer lokalen Umgebung zu verwenden, muss Office Online in der Umgebung konfiguriert sein. Weitere Informationen finden Sie unter  [Planen digitaler Objektbibliotheken in SharePoint Server 2013](http://technet.microsoft.com/en-us/library/ee414275.aspx) und [Konfigurieren von SharePoint 2013 mit Office Online](http://technet.microsoft.com/en-us/library/ff431687.aspx).
  
    
    
Weitere Informationen zum Einrichten Ihrer Entwicklungsumgebung und Erstellen einer Konsolenanwendung finden Sie unter  [Vorgehensweise: Erstellen und Löschen von Beiträge und Abrufen des für soziale Netzwerke-Feed mithilfe des clientobjektmodells .NET SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md).
  
    
    

## Beispiel: Einbetten eines Bilds in einer POST-Anforderung in SharePoint Server 2013
<a name="bkmk_addImage"> </a>

Im folgenden Codebeispiel wird veröffentlicht einen Beitrag, der ein eingebettetes Bild enthält. Außerdem wird gezeigt, wie Sie:
  
    
    

- Erstellen Sie ein  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) -Objekt, das das Bild darstellt. Die [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) gibt das Feld [SocialAttachmentKind.Image](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachmentKind.Image.aspx) und den URI der Bilddatei an.
    
  
- Fügen Sie das Image-Objekt an die  [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das zum Erstellen der POST-Anforderung verwendet wird.
    
  
Ändern Sie die Platzhalterwerte für die URL-Variablen vor dem Ausführen des Codes.
  
    
    



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


## Einbetten eines Videos in einem Beitrag in SharePoint Server 2013
<a name="bkmk_addVideo"> </a>

Im folgenden Codebeispiel wird veröffentlicht einen Beitrag, der ein eingebettetes Video enthält. Außerdem wird gezeigt, wie Sie:
  
    
    

- Rufen Sie das  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) -Objekt, das video Attachment-Objekt darstellt, mithilfe der [SocialFeedManager.GetPreview](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetPreview.aspx) -Methode.
    
  
- Fügen Sie das video Attachment-Objekts die  [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das zum Erstellen der POST-Anforderung verwendet wird.
    
  
Dieses Beispiel erfordert die Videofunktionen in einer Objektbibliothek hochgeladen werden auf dem Server und die Videodatei aktiviert werden soll. Finden Sie unter der  [Voraussetzung für die Verwendung in den Codebeispielen](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md#bk_preReqs) für Weitere Informationen.
  
    
    
Ändern Sie die Platzhalterwerte für die URL-Variablen vor dem Ausführen des Codes.
  
    
    



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


## Beispiel: Einbetten eines Dokuments in einem Beitrag in SharePoint Server 2013
<a name="bkmk_addDoc"> </a>

Im folgenden Codebeispiel wird veröffentlicht einen Beitrag, der ein eingebettetes Dokument enthält. Außerdem wird gezeigt, wie Sie:
  
    
    

- Ruft das  [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) -Objekt, das die Anlage Dokument darstellt, mithilfe der [SocialFeedManager.GetPreview](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetPreview.aspx) -Methode.
    
  
- Fügen Sie die Dokument-Anlage an die  [Attachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.Attachment.aspx) -Eigenschaft des [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) -Objekts, das zum Erstellen der POST-Anforderung verwendet wird.
    
  
Um in diesem Beispiel wird in einer lokalen Umgebung zu verwenden, muss Ihre Umgebung für die Verwendung von Office Online konfiguriert werden. Finden Sie unter der  [Voraussetzung für die Verwendung in den Codebeispielen](how-to-embed-images-videos-and-documents-in-posts-in-sharepoint-server-2013.md#bk_preReqs) für Weitere Informationen. Andernfalls können Sie eine Verknüpfung mit dem Dokument buchen, wie in [Vorgehensweise: erwähnt, Kategorien und Links zu Seiten und Dokumenten in Beiträge im SharePoint Server 2013 einschließen](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)beschrieben.
  
    
    
Ändern Sie die Platzhalterwerte für die URL-Variablen vor dem Ausführen des Codes.
  
    
    



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


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: erwähnt, Kategorien und Links zu Seiten und Dokumenten in Beiträge im SharePoint Server 2013 einschließen](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
    
  
-  [SocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostCreationData.aspx) und [SocialAttachment](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialAttachment.aspx) in die Clientobjektmodelle
    
  
-  [SocialPostCreationData](http://msdn.microsoft.com/library/f0e1fa3e-6fc9-48e0-5570-92091abfef33%28Office.15%29.aspx) und [SocialAttachment](http://msdn.microsoft.com/library/dfdee790-a1b0-19c8-0e92-5a6e058ba4db%28Office.15%29.aspx) im JavaScript-Objektmodell
    
  
-  [REST-API-Referenz für sozialen Feed für SharePoint 2013](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [SPSocialPostCreationData](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialPostCreationData.aspx) und [SPSocialAttachment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialAttachment.aspx) im Server-Objektmodell
    
  

