---
title: Referenz Threads und Digest-Threads in SharePoint Server 2013 für soziale Netzwerke RSS-feeds
ms.prod: SHAREPOINT
ms.assetid: 58e68fb2-ba40-4861-912f-355e119a1c41
---


# Referenz Threads und Digest-Threads in SharePoint Server 2013 für soziale Netzwerke RSS-feeds
Informationen Sie zu Referenz und Digest-Threads, die Threadtypen sind, die in der Auflistung der Threads enthalten sein können, die einen sozialen Feeds im SharePoint Server 2013 bilden.
Wenn Sie einen Feed für soziale Netzwerke abrufen, gibt SharePoint Server 2013 ein  [SocialFeed](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeed.aspx) -Objekt, das die Auflistung der [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) -Objekte enthält, die den Feed bilden. Unterhaltungen, einzelne Microblog Beiträge und Benachrichtigungen, enthalten Ereignisse und Threads verweisen, können diese Threads darstellen. Threads, die Unterhaltungen darstellen können als Digest Threads vom Server zurückgegeben werden.
  
    
    


> **HINWEIS**
> Die API, die in diesem Artikel verwiesen hat ihren Ursprung des Clientobjektmodells .NET. Entsprechende Objekte in anderen APIs können jedoch abweichen. Links zu anderen verwandten APIs finden Sie unter  [Zusätzliche Ressourcen](#bk_addresources) .
  
    
    


## Was sind Verweis Threads im SharePoint Server 2013 sozialen Feeds?
<a name="bk_whatAreRefThreads"> </a>

Wenn ein Benutzer "gefällt mir" einen Beitrag, erwähnt eine Person in einen Beitrag Antworten auf eine Nachricht wird oder ein Tag in einer POST-Anforderung enthält, generiert SharePoint Server 2013 einen Thread Verweis. Verweis Threads weisen zwei Eigenschaften, mit denen Sie Informationen über den referenzierten Thread get oder post:  [ThreadType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.ThreadType.aspx) und [PostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.PostReference.aspx) .
  
    
    
Sie können einen Verweis Thread durch ihre-Eigenschaft  [ThreadType](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.ThreadType.aspx) identifizieren die eine der in Tabelle 1 aufgeführten Werte zurückgeben kann.
  
    
    

**In Tabelle 1. Typen von Verweis thread**


|**Verweistyp**|**Beschreibung**|
|:-----|:-----|
| [LikeReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.LikeReference.aspx) **** <br/> |Ein Verweis auf einen Beitrag, den ein Benutzer "gefällt mir". <br/> |
| [MentionReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.MentionReference.aspx) <br/> |Ein Verweis auf einen Beitrag, der einen Benutzer erwähnt. <br/> |
| [ReplyReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.ReplyReference.aspx) <br/> |Ein Verweis auf eine Antwort. <br/> |
| [TagReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.TagReference.aspx) <br/> |Ein Verweis auf ein Beitrag, der ein Tag enthält. <br/> |
| [Normal](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadType.Normal.aspx) <br/> |Ein Verweis-Thread. <br/> |
   
Die  [PostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.PostReference.aspx) -Eigenschaft gibt ein [SocialPostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostReference.aspx) -Objekt, das Informationen über den Thread enthält, die das Ereignis ausgelöst hat. Mindestens enthält sie die ID des Quellthreads, die Sie dann mit der [SocialFeedManager.GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) -Methode verwenden können, den Thread abrufen, wenn es noch vorhanden ist.
  
    
    
 [SocialPostReference](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialPostReference.aspx) kann auch eine Kopie der Quelle Beitrag oder Thread enthalten. Diese Verfügbarkeit hängt davon ab, die Feedtyp sowie die Threadtyp und die Einschränkung aus Sicherheitsgründen. Enthält die Referenz einen Beitrag oder Thread, diese Objekte stellen Momentaufnahmen des Post oder Threads zum Zeitpunkt des Ereignisses dar.
  
    
    
Nicht alle feedbezogene Aktivitäten werden in den Feed als Referenz Threads gebucht. Beispielsweise sind folgende Benachrichtigungen (beispielsweise wenn eine Person nach einem Standort gestartet wird) nicht Verweis Threads.
  
    
    

> **HINWEIS**
> SharePoint Server 2013 schneidet automatisch Sicherheit für Inhalte auf automatisch generierte Beiträge und für den Zugriff auf die Website in alle Beiträge, die auf einer Website feed weitergeleitet werden. Jedoch können Sie dem Attribut **SecurityUris** Sicherheit trim erschienen verwenden durch Angabe einer URL. Benutzer, die keinen Zugriff auf die URL empfangen keine Beitrags.
  
    
    

Antworten, like und weisen Sie darauf hin, dass die Verweise auf unbestimmte Zeit in persönliche Feed des Benutzers gespeichert sind. Tag Verweise werden in der verteilten Cache gespeichert, damit sie vorübergehend gespeichert werden. Weitere Informationen zum Zwischenspeichern finden Sie unter  [Übersicht über mikrobloggingfeatures, Feeds und den verteilten Cachedienst in SharePoint Server 2013](http://technet.microsoft.com/en-us/library/jj219700%28v=office.15%29.aspx#cache).
  
    
    

## Was sind Digest Threads im SharePoint Server 2013 sozialen Feeds?
<a name="bk_whatAreDigests"> </a>

Ein Digest-Thread stellt eine kompakte Version einer Unterhaltung - enthält des Threads Stamm Post und zwei neuesten Antworten. Sie können einen Digest-Thread identifizieren, indem Sie überprüfen, ob der Thread das  [IsDigest](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThreadAttributes.IsDigest.aspx) -Attribut in der [Attributes](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.Attributes.aspx) -Eigenschaft angewendet. Um herauszufinden, ob ein Thread mehr als zwei Threads hat, überprüfen Sie die [TotalReplyCount](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.TotalReplyCount.aspx) -Eigenschaft.
  
    
    
Zum Optimieren der Leistung, wenn ein Thread mehr als zwei Antworten enthält, gibt der Server einen Digest-Thread zurück. Wenn Sie alle Antworten für einen Thread abrufen möchten, rufen Sie die  [SocialFeedManager.GetFullThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialFeedManager.GetFullThread.aspx) -Methode, und übergeben Sie die Thread-ID
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Arbeiten mit sozialen Feeds in SharePoint 2013](work-with-social-feeds-in-sharepoint-2013.md)
    
  
-  [SocialThread](https://msdn.microsoft.com/library/Microsoft.SharePoint.Client.Social.SocialThread.aspx) im .NET Client-Objektmodell
    
  
-  [SocialThread](http://msdn.microsoft.com/library/46aa4beb-d708-f20e-471e-626c8a7efab7%28Office.15%29.aspx) im JavaScript-Objektmodell
    
  
-  [SPSocialThread](https://msdn.microsoft.com/library/Microsoft.Office.Server.Social.SPSocialThread.aspx) im Server-Objektmodell
    
  

