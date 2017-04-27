---
title: Vorgehensweise Erstellen und Löschen von Beiträgen und sozialen Feed abrufen, indem Sie mit der JavaScript-Objektmodell in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: e8c21960-6ea0-43c0-821e-2db2a0ecec90
---



# Vorgehensweise: Erstellen und Löschen von Beiträgen und sozialen Feed abrufen, indem Sie mit der JavaScript-Objektmodell in SharePoint 2013
In diesem Artikel erfahren Sie, wie Sie mithilfe des SharePoint 2013 JavaScript-Objektmodells Mikroblogbeiträge erstellen und löschen und soziale Feeds abrufen.
 * **Gilt für:*** 
  
    
    


||
|:-----|
|**In diesem Artikel**          [Codebeispiel: Veröffentlichen von Beiträgen und Antworten auf die Nutzung von sozialen Netzwerken feed mithilfe der SharePoint 2013 JavaScript-Objektmodells](#bkmk_PubPosts)           [Codebeispiel: Abrufen von sozialen Feeds mithilfe des SharePoint 2013 JavaScript-Objektmodells](#bkmk_GetFeeds)           [Codebeispiel: Delete Beiträge und Antworten von den Feed für soziale Netzwerke mithilfe der SharePoint 2013 JavaScript-Objektmodells](#bkmk_DeletePosts)                     [Was thematischer Feeds sind?](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_intro)           [Voraussetzungen für das Einrichten Ihrer Entwicklungsumgebung](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_SetUpDevEnv)           [Erstellen der Anwendungsseite](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp)           [Veröffentlichen Beiträgen und Antworten Sie den Feed für soziale Netzwerke](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_PubPosts)           [Abrufen thematischer Feeds](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_GetFeeds)           [Löschen Beiträgen und Antworten aus dem sozialen Feed](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_DeletePosts)           [Zusätzliche Ressourcen](#bk_addResources)|
   

## Was sind thematischer Feeds in SharePoint Server 2013 ?
<a name="bk_intro"> </a>

In SharePoint Server 2013 ist ein für soziale Netzwerke Feed eine Auflistung von Threads, die von Unterhaltungen, einzelne Microblog Beiträge oder Benachrichtigungen darstellen. Threads enthalten ein Stammbeitrag und eine Auflistung von Antwort Beiträge. Im Objektmodell JavaScript Feeds werden durch  [SocialFeed](http://msdn.microsoft.com/library/356c5475-2fd6-a655-c271-5d7f21af45e2%28Office.15%29.aspx) Objekte dargestellt, werden durch [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx) Objekte dargestellt und Post und-Antworten werden durch [SocialPost](http://msdn.microsoft.com/library/a761ce71-d3d7-420a-1e06-962674124dfa%28Office.15%29.aspx) Objekte dargestellt. Informationen zum Core feedbezogene Aufgaben ausführen zu können, verwenden Sie das [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) -Objekt. In diesem Artikel erfahren Sie, wie Sie zum Erstellen einer Anwendungsseite, die das JavaScript-Objektmodell zum Arbeiten mit sozialen Feeds verwendet.
  
    
    
For more information about working with  [SocialFeedManager](http://msdn.microsoft.com/library/651fdf0f-841d-88f9-1e07-fcb3ad8c9410%28Office.15%29.aspx) or for information about using other APIs to work with social feeds, see [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md).
  
    
    

## Voraussetzungen für das Einrichten Ihrer Entwicklungsumgebung thematischer Feeds im Objektmodell von SharePoint 2013 JavaScript entwickelt
<a name="bkmk_SetUpDevEnv"> </a>

Zum Erstellen einer Anwendungsseite, die das JavaScript-Objektmodell zum Arbeiten mit sozialen Feeds verwendet, benötigen Sie:
  
    
    

- SharePoint Server 2013 mit Meine Website konfiguriert als öffentlich mit persönlichen Websites, die für den aktuellen Benutzer und einen Zielbenutzer erstellt, mit dem aktuellen Benutzer nach der Zielbenutzer und mit ein paar Beiträge, die von den Zielbenutzer geschrieben
    
  
- Visual Studio 2012 oder Visual Studio 2013 mit Office Developer Tools für Visual Studio 2013
    
  
- **Vollzugriff auf die Benutzerprofildienst-Anwendung und die Berechtigungen zum Bereitstellen einer Farmlösung des angemeldeten Benutzers**
    
  
- Über ausreichende Berechtigungen für das Anwendungspoolkonto greifen Sie auf die Inhaltsdatenbank von Meine Websites-Webanwendung
    
  

## Erstellen einer Anwendungsseite, das mit sozialen Feeds mithilfe der SharePoint 2013 JavaScript-Objektmodells
<a name="bk_CreateApp"> </a>


1. Öffnen Sie Visual Studio, und wählen Sie **Datei**, **neu**, **Projekt**.
    
  
2. Wählen Sie im Dialogfeld **Neues Projekt** aus der Dropdownliste oben im Dialogfeld die Option **.NET Framework 4.5**.
    
  
3. In der Liste der **Vorlagen** erweitern Sie **Office SharePoint**, wählen Sie die Kategorie **SharePoint-Lösungen** und wählen Sie dann die Vorlage **SharePoint 2013-Projekts**.
    
  
4. Nennen Sie das Projekt SocialFeedJSOM, und wählen Sie dann auf die Schaltfläche **OK**.
    
  
5. Klicken Sie im **Assistenten zum Anpassen von SharePoint**-Dialogfeld Wählen Sie **als Farmlösung bereitstellen**, und wählen Sie dann auf die Schaltfläche **Fertig stellen**.
    
  
6. Im **Projektmappen-Explorer** das Kontextmenü für das ProjektSocialFeedJSOM öffnen, und fügen Sie eine SharePoint "Layouts" Ordner zugeordnet.
    
  
7. Klicken Sie im Ordner **Layouts** öffnen Sie das Kontextmenü für den OrdnerSocialFeedJSOM , und fügen Sie eine neue SharePoint-Anwendungsseite namensSocialFeed.aspx.
    
    > **HINWEIS**
      > Die Codebeispiele in diesem Artikel legen benutzerdefinierten Code im Seitenmarkup verwenden jedoch kein Code-Behind-Klasse, Visual Studio für die Seite erstellt.
8. Öffnen Sie das Kontextmenü für die Seite SocialFeed.aspx, und wählen Sie **als Startelement festlegen**.
    
  
9. Definieren Sie im Markup für die Seite SocialFeed.aspx-Steuerelementen in den "Main" **asp:Content** -Tags, wie im folgenden Code dargestellt.
    
  ```HTML
  
<table width="100%" id="tblPosts"></table><br/>
<button id="btnDelete" type="button"></button><br />
<span id="spanMessage" style="color: #FF0000;"></span>
  ```


    > **HINWEIS**
      > Diese Steuerelemente können nicht in jedem Szenario verwendet werden. Beispielsweise verwendet das Szenario "Veröffentlichen Beiträgen und Antworten" nur das **span** -Steuerelement.
10. Nach dem schließenden **span** markieren, fügen Sie **SharePoint:ScriptLink** -Steuerelemente, ein Steuerelement **SharePoint:FormDigest** und **script** -Tags, wie im folgenden Code dargestellt. Die Tags **SharePoint:ScriptLink** verweisen auf die Bibliothek Klassendateien, die das Objektmodell JavaScript definieren, das Sie für die Entwicklung von Meine Website - soziale Netzwerke verwenden können. Das **SharePoint:FormDigest** -Tag generiert einen Nachrichtenhash für die Sicherheitsüberprüfung bei Bedarf von Operationen, die den Inhalt zu aktualisieren.
    
  ```HTML
  
<SharePoint:ScriptLink ID="ScriptLink1" name="SP.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:ScriptLink ID="ScriptLink2" name="SP.UserProfiles.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:FormDigest id="FormDigest" runat="server"/>
<script type="text/javascript">

    // Replace this comment with the code for your scenario.

</script>

  ```

11. Um die Logik für die Arbeit mit Feeds hinzuzufügen, ersetzen Sie den Kommentar zwischen den Tags **script** durch das Codebeispiel aus einem der folgenden Szenarien:
    
  -  [Veröffentlichen von Beiträgen und Antworten auf den Feed für soziale Netzwerke](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_PubPosts)
    
  
  -  [Rufen thematischer Feeds ab](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_GetFeeds)
    
  
  -  [Delete-Beiträgen und Antworten aus dem sozialen feed](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bkmk_DeletePosts)
    
  
12. Wählen Sie zum Testen der Anwendungsseite in der Menüleiste **Debuggen**, **Debuggen starten** aus. Wenn Sie aufgefordert werden, ändern Sie die Datei "Web.config", und wählen Sie die Schaltfläche **OK**.
    
    Wenn die Antwort die Ausfall Callback-Methode aufruft, legen Sie einen Haltepunkt in der Methode und fügen Sie eine Überwachung auf dem **args** -Objekt hinzu oder Überprüfen Sie die ULS-Protokolle und der Ereignisanzeige Weitere Informationen.
    
  

## Codebeispiel: Veröffentlichen von Beiträgen und Antworten auf die Nutzung von sozialen Netzwerken feed mithilfe der SharePoint 2013 JavaScript-Objektmodells
<a name="bkmk_PubPosts"> </a>

Im folgenden Codebeispiel wird veröffentlicht ein Beitrag und einer Antwort. Außerdem wird gezeigt, wie Sie:
  
    
    

- Definieren Sie nach Inhalt. Dieses Beispiel enthält einen Link in der POST-Anforderung.
    
  
- Veröffentlichen Sie einen Post-Feed des aktuellen Benutzers mithilfe der **createPost** -Methode und übergeben **null** als _targetId_ -Parameter.
    
  
- Antworten Sie auf einen Beitrag mithilfe der **createPost** -Methode und die Thread-ID als _targetId_ -Parameter übergeben.
    
  

> **HINWEIS**
> Fügen Sie den folgenden Code zwischen den **script** -Tags, die Sie in der Prozedur [Erstellen der Anwendungsseite](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp) hinzugefügt.
  
    
    


```

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(PublishPost, 'SP.UserProfiles.js');

// Declare global variables.
var clientContext;
var feedManager;
var resultThread;

function PublishPost() {

    // Initialize the current client context and the SocialFeedManager instance.
    clientContext = SP.ClientContext.get_current();
    feedManager = new SP.Social.SocialFeedManager(clientContext);

    // Create a link to include in the post.
    var linkDataItem = new SP.Social.SocialDataItem();
    linkDataItem.set_itemType(SP.Social.SocialDataItemType.link);
    linkDataItem.set_text('link');
    linkDataItem.set_uri('http://bing.com');
    var socialDataItems = [ linkDataItem ];

    // Create the post content.
    var postCreationData = new SP.Social.SocialPostCreationData();
    postCreationData.set_contentText('The text for the post, which contains a {0}.');
    postCreationData.set_contentItems(socialDataItems);

    // Publish the post. Pass null for the "targetId" parameter because this is a root post.
    resultThread = feedManager.createPost(null, postCreationData);
    clientContext.executeQueryAsync(PublishReply, PostFailed);
    }
function PublishReply(sender, args) {

    // Create the reply content.
    var postCreationData = new SP.Social.SocialPostCreationData();
    postCreationData.set_contentText('The text for the reply.');

    // Publish the reply.
    resultThread = feedManager.createPost(resultThread.get_id(), postCreationData);
    clientContext.executeQueryAsync(PostSucceeded, PostFailed);
}
function PostSucceeded(sender, args) {
    $get("spanMessage").innerText = 'The post and reply were published.';
}
function PostFailed(sender, args) {
    $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
}

```


## Codebeispiel: Abrufen von sozialen Feeds mithilfe des SharePoint 2013 JavaScript-Objektmodells
<a name="bkmk_GetFeeds"> </a>

Im folgenden Codebeispiel werden die Feeds für den aktuellen Benutzer und einen Zielbenutzer abgerufen. Außerdem wird gezeigt, wie Sie:
  
    
    

- Rufen Sie die **Personal**, **News**und **Timeline** feed Typen für den aktuellen Benutzer mithilfe der **getFeed** -Methode.
    
  
- Rufen Sie die **Personal** feed Typ für einen Zielbenutzer mithilfe der **getFeedFor** -Methode.
    
  
- Durchlaufen Sie die Feeds, um alle Threads im nicht-Verweis zu suchen und Abrufen von Informationen zu Threads und Beiträge. Verweis Threads darstellen Benachrichtigungen, die Informationen zu einem anderen Thread enthalten. Wenn ein Benutzer eine Person in einem Beitrag erwähnt wird, generiert der Server beispielsweise ein **MentionReference**-Thread, der den Link zur ursprünglichen Beitrags und andere Metadaten zu dem Beitrag enthält geben.
    
  
For more information about feed types, see  [Übersicht über Feedtypen in der Meine Website - soziale Netzwerke-API](work-with-social-feeds-in-sharepoint-2013.md#bkmk_FeedTypes). For more information about reference threads, see  [Referenz Threads und Digest-Threads in SharePoint Server 2013 für soziale Netzwerke RSS-feeds](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md).
  
    
    

> **HINWEIS**
> Fügen Sie den folgenden Code zwischen den **script** -Tags, die Sie in der Prozedur [Erstellen der Anwendungsseite](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp) hinzugefügt. Ändern Sie dann den Platzhalterwert für die Variable **targetUser** vor dem Ausführen des Codes.
  
    
    




```cs

// Replace the placeholder value with the account name of the target user.
var targetUser = 'domainName\\\\userName';

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(GetFeeds, 'SP.UserProfiles.js');

// Declare global variables.
var clientContext;
var feedManager;
var personalFeed;
var newsFeed;
var timelineFeed;
var targetUserFeed;

function GetFeeds() {

    // Initialize the current client context and the SocialFeedManager instance.
    clientContext = SP.ClientContext.get_current();
    feedManager = new SP.Social.SocialFeedManager(clientContext);

    // Set parameters for the feed content that you want to retrieve.
    var feedOptions = new SP.Social.SocialFeedOptions();
    feedOptions.set_maxThreadCount(10); // default is 20

    // Get all feed types for current user and get the Personal feed
    // for the target user.
    personalFeed = feedManager.getFeed(SP.Social.SocialFeedType.personal, feedOptions);
    newsFeed = feedManager.getFeed(SP.Social.SocialFeedType.news, feedOptions);
    targetUserFeed = feedManager.getFeedFor(targetUser, feedOptions);

    // Change the sort order to optimize the Timeline feed results.
    feedOptions.set_sortOrder(SP.Social.SocialFeedSortOrder.byCreatedTime); 
    timelineFeed = feedManager.getFeed(SP.Social.SocialFeedType.timeline, feedOptions);

    clientContext.load(feedManager);
    clientContext.executeQueryAsync(CallIterateFunctionForFeeds, RequestFailed);
}
function CallIterateFunctionForFeeds() {
    IterateThroughFeed(personalFeed, "Personal", true);
    IterateThroughFeed(newsFeed, "News", true);
    IterateThroughFeed(timelineFeed, "Timeline", true); 
    IterateThroughFeed(targetUserFeed, "Personal", false);
}
function IterateThroughFeed(feed, feedType, isCurrentUser) {
    tblPosts.insertRow().insertCell();
    var feedHeaderRow = tblPosts.insertRow();
    var feedOwner = feedManager.get_owner().get_name();

    // Iterate through the array of threads in the feed.
    var threads = feed.get_threads();
    for (var i = 0; i < threads.length ; i++) {
        var thread = threads[i];
        var actors = thread.get_actors();

        if (i == 0) {

            // Get the name of the target user for the feed header row. Users are 
            // owners of all threads in their Personal feed.
            if (!isCurrentUser) {
                feedOwner = actors[thread.get_ownerIndex()].get_name();
            }
            feedHeaderRow.insertCell().innerText = feedType.toUpperCase() + ' FEED FOR '
                + feedOwner.toUpperCase();
        }

        // Use only Normal-type threads and ignore reference-type threads. (SocialThreadType.Normal = 0)
        if (thread.get_threadType() == 0) {

            // Get the root post's author, content, and number of replies.
            var post = thread.get_rootPost();
            var authorName = actors[post.get_authorIndex()].get_name();
            var postContent = post.get_text();
            var totalReplies = thread.get_totalReplyCount();

            var postRow = tblPosts.insertRow();
            postRow.insertCell().innerText = authorName + ' posted \\"' + postContent
                + '\\" (' + totalReplies + ' replies)';

            // If there are any replies, iterate through the array and
            // get the author and content. 
            // If a thread contains more than two replies, the server
            // returns a thread digest that contains only the two most
            // recent replies. To get all replies, call the 
            // SocialFeedManager.getFullThread method.
            if (totalReplies > 0) {
                var replies = thread.get_replies();

                for (var j = 0; j < replies.length; j++) {
                    var replyRow = tblPosts.insertRow();

                    var reply = replies[j];
                    replyRow.insertCell().innerText = '  - ' + actors[reply.get_authorIndex()].get_name()
                        + ' replied \\"' + reply.get_text() + '\\"';
                }
            }
        }
    }
}
function RequestFailed(sender, args) {
    $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
}
```


## Codebeispiel: Delete Beiträge und Antworten von den Feed für soziale Netzwerke mithilfe der SharePoint 2013 JavaScript-Objektmodells
<a name="bkmk_DeletePosts"> </a>

Im folgenden Codebeispiel wird Löscht ein Beitrag oder eine Antwort. Außerdem wird gezeigt, wie Sie:
  
    
    

- Rufen Sie die **News** feed Typ für den aktuellen Benutzer mithilfe der **getFeed** -Methode.
    
  
- Durchlaufen Sie die Beiträge und Antworten in den Feed zum Abrufen der **id** -Eigenschaft, mit denen Sie die Beitrag oder eine Antwort zu löschen.
    
  
- Löschen einer Stammbeitrag oder eine Antwort mithilfe der **deletePost** -Methode (einen Stammbeitrag löschen Löscht den gesamten Thread).
    
  

> **HINWEIS**
> Fügen Sie den folgenden Code zwischen den **script** -Tags, die Sie in der Prozedur [Erstellen der Anwendungsseite](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-javascr.md#bk_CreateApp) hinzugefügt. In diesem Beispiel wird vorausgesetzt, dass der aktuelle Benutzer Newsfeed mindestens einen Post enthält.
  
    
    


```cs

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(GetFeeds, 'SP.UserProfiles.js');

// Declare global variables.
var clientContext;
var feedManager;
var feed;
var postOrReplyToDelete;

function GetFeeds() {

    // Initialize the current client context and the SocialFeedManager instance.
    clientContext = SP.ClientContext.get_current();
    feedManager = new SP.Social.SocialFeedManager(clientContext);

    // Set parameters for the feed content that you want to retrieve.
    var feedOptions = new SP.Social.SocialFeedOptions();
    feedOptions.set_maxThreadCount(10); // default is 20

    // Get all the News feed type for current user.
    feed = feedManager.getFeed(SP.Social.SocialFeedType.news, feedOptions);
    clientContext.executeQueryAsync(IterateThroughFeed, RequestFailed);
}
function IterateThroughFeed() {

    // Iterate through the array of threads in the feed.
    var threads = feed.get_threads();
    for (var i = 0; i < threads.length ; i++) {
        var thread = threads[i];
        var actors = thread.get_actors();

        // Get the root post's author, content, and number of replies.
        var post = thread.get_rootPost();

        var authorName = actors[post.get_authorIndex()].get_name();
        var postContent = post.get_text();
        var totalReplies = thread.get_totalReplyCount();

        var postRow = tblPosts.insertRow();
        postRow.insertCell().innerText = authorName + ' posted \\"' + postContent
            + '\\" (' + totalReplies + ' replies)';
        postOrReplyToDelete = post.get_id();

        // If there are any replies, iterate through the array and
        // get the author and content.
            // If a thread contains more than two replies, the server
            // returns a thread digest that contains only the two most
            // recent replies. To get all replies, call the 
            // SocialFeedManager.getFullThread method.
        if (totalReplies > 0) {
            var replies = thread.get_replies();
            for (var j = 0; j < replies.length; j++) {
                var replyRow = tblPosts.insertRow();

                var reply = replies[j];
                replyRow.insertCell().innerText = '  - ' + actors[reply.get_authorIndex()].get_name()
                    + ' replied \\"' + reply.get_text() + '\\"';
                postOrReplyToDelete = reply.get_id();
            }
        }

        // Initialize button properties.
        $get("btnDelete").onclick = function () { DeletePostOrReply(); };
        $get("btnDelete").innerText = 'Click to delete the last post or reply';
    }
}

// Delete the last post or reply listed on the page.
function DeletePostOrReply() {
    feedManager.deletePost(postOrReplyToDelete);
    clientContext.executeQueryAsync(DeleteSucceeded, RequestFailed);
}
function DeleteSucceeded(sender, args) {
    $get("spanMessage").innerText = 'The post or reply was deleted. Refresh the page to see your changes.';
}
function RequestFailed(sender, args) {
    $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
}
```


## Zusätzliche Ressourcen
<a name="bk_addResources"> </a>


-  [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [SP. Social-Namespace (sp.userprofiles)](http://msdn.microsoft.com/library/43d47f01-c085-0e77-bd01-48bcb7d5bb35%28Office.15%29.aspx)
    
  
-  [Vorgehensweise: Erstellen und Löschen von Beiträge und Abrufen des für soziale Netzwerke-Feed mithilfe des clientobjektmodells .NET SharePoint 2013](how-to-create-and-delete-posts-and-retrieve-the-social-feed-by-using-the-net-cli.md)
    
  
-  [Vorgehensweise: Lesen und Schreiben der sozialen Feed mithilfe des REST-Diensts in SharePoint 2013](how-to-learn-to-read-and-write-to-the-social-feed-by-using-the-rest-service-in-s.md)
    
  
-  [Referenz Threads und Digest-Threads in SharePoint Server 2013 für soziale Netzwerke RSS-feeds](reference-threads-and-digest-threads-in-sharepoint-server-2013-social-feeds.md)
    
  
