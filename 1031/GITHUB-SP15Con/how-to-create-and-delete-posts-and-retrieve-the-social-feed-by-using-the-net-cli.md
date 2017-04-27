---
title: Vorgehensweise Erstellen und Löschen von Beiträge und Abrufen des für soziale Netzwerke-Feed mithilfe des clientobjektmodells .NET SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c8d68632-1b55-454c-961a-f3ddad731bf6
---


# Vorgehensweise: Erstellen und Löschen von Beiträge und Abrufen des für soziale Netzwerke-Feed mithilfe des clientobjektmodells .NET SharePoint 2013
In diesem Artikel erfahren Sie, wie Sie mithilfe des .NET-Clientobjektmodells in SharePoint 2013 Mikroblogbeiträge erstellen und löschen und soziale Feeds abrufen.
## Was sind thematischer Feeds in SharePoint Server 2013 ?
<a name="bk_intro"> </a>

In SharePoint Server 2013 ist ein für soziale Netzwerke Feed eine Auflistung von Threads, die von Unterhaltungen, einzelne Microblog Beiträge oder Benachrichtigungen darstellen. Threads einen Stammbeitrag und eine Auflistung von Antwort Beiträge enthalten, und sie Unterhaltungen, einzelne Microblog Beiträge oder Benachrichtigungen darstellen. Im .NET Client-Objektmodell Feeds  [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) Objekte dargestellt werden, werden durch [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) Objekte dargestellt und Beiträgen und Antworten werden durch [SocialPost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPost.aspx) Objekte dargestellt. Informationen zum Core feedbezogene Aufgaben im Objektmodell von .NET Client ausführen, verwenden Sie das [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) -Objekt. In diesem Artikel erfahren Sie, wie Sie eine Konsolenanwendung erstellen, die des Clientobjektmodells .NET zum Arbeiten mit sozialen Feeds verwendet.
  
    
    
Weitere Informationen zum Arbeiten mit  [SocialFeedManager](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.aspx) oder Informationen zur Verwendung von anderen APIs mit sozialen Feeds arbeiten finden Sie unter [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md).
  
    
    

## Voraussetzungen für das Einrichten Ihrer Entwicklungsumgebung sozialen Feeds mithilfe des Clientobjektmodells für SharePoint 2013.NET entwickelt
<a name="bkmk_SetUpDevEnv"> </a>

Um eine Konsolenanwendung erstellen, die des Clientobjektmodells .NET zum Arbeiten mit sozialen Feeds verwendet, benötigen Sie Folgendes:
  
    
    

- SharePoint Server 2013 mit Meine Website konfiguriert, mit persönlichen Websites, die für den aktuellen Benutzer und einen Zielbenutzer erstellt, mit dem aktuellen Benutzer nach der Zielbenutzer und mit ein paar Beiträge, die von den Zielbenutzer geschrieben
    
  
- Visual Studio 2012
    
  
- **Vollzugriff auf die Benutzerprofildienst-Anwendung für den angemeldeten Benutzer**
    
  

> **HINWEIS**
> Wenn Sie nicht auf dem Computer entwickeln, die SharePoint Server 2013 ausgeführt wird, rufen Sie das  [SharePoint-Clientkomponenten](http://www.microsoft.com/en-us/download/details.aspx?id=35585) herunterladen, das SharePoint 2013 Clientassemblys enthält.
  
    
    


## Erstellen Sie eine Konsolenanwendung, das mit sozialen Feeds mithilfe des Clientobjektmodells für SharePoint 2013.NET
<a name="bk_createconsole"> </a>


1. Öffnen Sie Visual Studio, und wählen Sie **Datei**, **Neu**, **Projekt**.
    
  
2. Wählen Sie im Dialogfeld **Neues Projekt** aus der Dropdownliste oben im Dialogfeld die Option **.NET Framework 4.5**.
    
  
3. Klicken Sie in der Liste **Vorlagen** wählen Sie **Windows**, und wählen Sie dann die Vorlage **Konsolenanwendung**.
    
  
4. Nennen Sie das Projekt SocialFeedCSOM, und wählen Sie dann auf die Schaltfläche **OK**.
    
  
5. Fügen Sie Verweise auf die folgenden Assemblys hinzu:
    
  - **Microsoft.SharePoint.Client**
    
  
  - **Microsoft.SharePoint.ClientRuntime**
    
  
  - **Microsoft.SharePoint.Client.UserProfiles**
    
  
6. Ersetzen Sie die Inhalte der **Program**-Klasse durch das Codebeispiel aus einem der folgenden Szenarien:
    
  -  [Veröffentlichen von Beiträgen und Antworten Sie den Feed für soziale Netzwerke](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_PubPosts)
    
  
  -  [Abrufen von sozialen feeds](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_GetFeeds)
    
  
  -  [Delete-Beiträgen und Antworten aus dem sozialen feed](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md#bkmk_DeletePosts)
    
  
7. Wählen Sie zum Testen der Konsolenanwendung, klicken Sie auf der Menüleiste **Debuggen**, **Debuggen starten** aus.
    
  

## Codebeispiel: Veröffentlichen von Beiträgen und Antworten auf die Nutzung von sozialen Netzwerken feed mithilfe des Clientobjektmodells für SharePoint 2013.NET
<a name="bkmk_PubPosts"> </a>

Im folgenden Codebeispiel wird veröffentlicht ein Beitrag und aus dem aktuellen Benutzer eine Antwort. Außerdem wird gezeigt, wie Sie:
  
    
    

- Nach Inhalt definiert. Dieses Beispiel enthält einen Link in der POST-Anforderung.
    
  
- Veröffentlichen Sie einen Post-Feed des aktuellen Benutzers mithilfe der  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) -Methode und übergeben **null** als _targetId_ -Parameter.
    
  
- Rufen Sie die  [News](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.News.aspx) feed Typ für den aktuellen Benutzer mithilfe der [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) -Methode.
    
  
- Durchlaufen Sie den Feed, erhalten alle Threads, die beantwortet werden können und Abrufen von Informationen zu Threads und Beiträge.
    
  
- Antworten Sie auf einen Beitrag mithilfe der  [CreatePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.CreatePost.aspx) -Methode und die Thread-ID als _targetId_ -Parameter übergeben.
    
  

> **HINWEIS**
> Ändern Sie den Platzhalterwert für die Variable **serverUrl**, bevor Sie den Code ausführen.
  
    
    


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


## Codebeispiel: Abrufen von sozialen Feeds mithilfe des Clientobjektmodells für SharePoint 2013.NET
<a name="bkmk_GetFeeds"> </a>

Im folgenden Codebeispiel werden die Feeds für den aktuellen Benutzer und einen Zielbenutzer abgerufen. Außerdem wird gezeigt, wie Sie:
  
    
    

- Rufen Sie die  [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) , [News](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.News.aspx) und [Timeline](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Timeline.aspx) feed Typen für den aktuellen Benutzer mithilfe der [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) -Methode.
    
  
- Rufen Sie die  [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) feed Typ für einen Zielbenutzer mithilfe der [GetFeedFor](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeedFor.aspx) -Methode.
    
  
- Durchlaufen Sie die Feeds, um alle Threads im nicht-Verweis zu suchen und Abrufen von Informationen zu Threads und Beiträge. Verweis Threads darstellen Benachrichtigungen, die Informationen zu einem anderen Thread enthalten. Wenn ein Benutzer eine Person in einem Beitrag erwähnen, generiert der Server eine  [MentionReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.MentionReference.aspx) -Thread, der den Link zur ursprünglichen Beitrags und andere Metadaten zu dem Beitrag enthält geben.
    
  
Weitere Informationen zu den feed Typen finden Sie unter  [Übersicht über feed Typen](work-with-social-feeds-in-sharepoint-2013.md#bkmk_FeedTypes). Weitere Informationen zu Verweis Threads finden Sie unter  [Referenz Threads und Digest-Threads in SharePoint Server 2013 für soziale Netzwerke RSS-feeds](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md).
  
    
    

> **HINWEIS**
> Ändern Sie die Platzhalterwerte für die Variablen **serverUrl** und **targetUser** vor dem Ausführen des Codes.
  
    
    




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


## Codebeispiel: Delete Beiträgen und Antworten von den Feed für soziale Netzwerke mithilfe des Clientobjektmodells für SharePoint 2013.NET
<a name="bkmk_DeletePosts"> </a>

Im folgenden Codebeispiel wird Löscht ein Beitrag oder eine Antwort von persönlichen Feed des aktuellen Benutzers. Außerdem wird gezeigt, wie Sie:
  
    
    

- Rufen Sie die  [Personal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedType.Personal.aspx) feed Typ für den aktuellen Benutzer mithilfe der [GetFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFeed.aspx) -Methode.
    
  
- Durchlaufen Sie die Threads im Feed zum Abrufen von Informationen zu den Stammbeitrag und Antworten.
    
  
- Löschen einer Stamm Post, Antwort oder Thread mithilfe der  [DeletePost](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.DeletePost.aspx) -Methode (einen Stammbeitrag löschen Löscht den gesamten Thread).
    
  

> **HINWEIS**
> Ändern Sie den Platzhalterwert für die Variable **serverUrl**, bevor Sie den Code ausführen.
  
    
    


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


## Nächste Schritte
<a name="bkmk_DeletePosts"> </a>

 [Vorgehensweise: erwähnt, Kategorien und Links zu Seiten und Dokumenten in Beiträge im SharePoint Server 2013 einschließen](how-to-include-mentions-tags-and-links-to-sites-and-documents-in-posts-in-sharep.md)
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addResources"> </a>


-  [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen und Löschen von Beiträgen und sozialen Feed abrufen, indem Sie mit der JavaScript-Objektmodell in SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md)
    
  
-  [Vorgehensweise: Lesen und Schreiben der sozialen Feed mithilfe des REST-Diensts in SharePoint 2013](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [Referenz Threads und Digest-Threads in SharePoint Server 2013 für soziale Netzwerke RSS-feeds](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  

