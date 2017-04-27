---
title: Vorgehensweise führen Sie Dokumente, Websites und Tags mithilfe des REST-Diensts in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 989a5873-49f9-49e4-8d0f-439dde891cc2
---


# Vorgehensweise: führen Sie Dokumente, Websites und Tags mithilfe des REST-Diensts in SharePoint 2013
Erstellen von SharePoint gehosteten apps, die den REST-Dienst verwenden, um Inhalte (Dokumente, Websites und Tags) folgen und verfolgter Inhalte abzurufen.
## Wie verwende ich den REST-Dienst SharePoint Server 2013 Folgen von Inhalten aus?
<a name="bk_intro"> </a>

SharePoint Server 2013 Benutzer können Dokumente, Websites und zum Abrufen von Updates über die Artikel in die Newsfeeds und beobachteter Dokumente und Websites schnell zu öffnen Tags folgen. Sie können SharePoint Server 2013 REST-API in Ihrer app oder Lösung Folgen von Inhalten zu starten, beenden Folgen von Inhalten und Abrufen beobachteten Inhalte im Auftrag des aktuellen Benutzers.
  
    
    
Die folgenden REST-Ressourcen sind die primäre API zum Inhalt in der folgenden Aufgaben:
  
    
    

- **SocialRestFollowingManager** bietet Methoden zum Verwalten eines Benutzers Liste besuchter Akteure.
    
  
- **SocialActor** stellt ein Dokument, Website oder Tag, der der Server als Antwort auf eine Anforderung mithilfe der clientseitigen zurückgibt.
    
  
- **SocialActorInfo** gibt ein Dokument, Website oder Tag in clientseitige Anforderungen an den Server.
    
  
- **SocialActorType** und **SocialActorTypes** angeben von Inhaltstypen in clientseitige Anforderungen an den Server.
    
  
Inhalt in der folgenden Aufgaben mithilfe der REST-API, senden Sie HTTP **GET** und HTTP- **POST** Anfragen an den REST-Dienst. REST Endpoint URIs Aufgaben zum folgenden Inhalt mit der Ressource **SocialRestFollowingManager** ( `<siteUri>/_api/social.following`) beginnen und enden mit einer der folgenden Ressourcen:
  
    
    

- **follow** starten nach einem Dokument, Website oder tag
    
  
- **stopfollowing** zu einem Dokument, Website oder tag
    
  
- **isfollowed**, um herauszufinden, ob der Benutzer ein bestimmtes Dokument, eine Website oder ein Tag folgt
    
  
- **my/followed** abzurufenden beobachteter Dokumente, Websites und tags
    
  
- **my/followedcount** zum Abrufen der Anzahl beobachteter Dokumente, Websites und tags
    
  

> **HINWEIS**
> Sie verwenden diese Endpunkte auch für folgende Personen Aufgaben, aber die **followers** und **suggestions** Ressourcen, die vom nur nach Personen, die nicht von **SocialRestFollowingManager** -Support zur Verfügung. Weitere Informationen dazu, wie Sie **SocialRestFollowingManager**verwenden können finden Sie unter  [Folgen von Inhalten in SharePoint 2013](follow-content-in-sharepoint-2013.md) und [Folgen von Personen in SharePoint 2013](follow-people-in-sharepoint-2013.md).
  
    
    


## Voraussetzungen für die Erstellung einer SharePoint gehosteten app, die verwaltet beobachteten Inhalte mithilfe des REST-Diensts SharePoint 2013
<a name="bkmk_Prereqs"> </a>

In diesem Artikel wird davon ausgegangen, dass Sie die SharePoint-Add-In mithilfe einer Napa- oder Office 365-Entwicklerwebsite erstellen. Wenn Sie diese Entwicklungsumgebung verwenden, sind die Voraussetzungen bereits erfüllt.
  
    
    

> **HINWEIS**
> Wechseln Sie zur  [Einrichten einer Entwicklungsumgebung für SharePoint-Add-Ins in Office 365](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx) melden Sie sich für eine Entwicklerwebsite und Verwenden von Napa.
  
    
    

Wenn Sie nicht auf eine Office 365 Developer Site Napa verwenden, benötigen Sie die folgenden Anforderungen erfüllen, bevor Sie die SharePoint-Add-In bereitstellen können:
  
    
    

- Eine SharePoint 2013-Entwicklungsumgebung, die für die Anwendungsisolation konfiguriert ist. Wenn Sie Remote-Entwicklung, muss der Server Sideloading Apps Unterstützung oder müssen Sie die app auf einer Entwicklerwebsite installieren.
    
  
- Der Meine Website-Host konfiguriert ist, mit einer persönlichen Website für den aktuellen Benutzer erstellt.
    
  
- Visual Studio 2012 oder Visual Studio 2013 mit Office Developer Tools für Visual Studio 2013.
    
  
- Über ausreichende Berechtigungen für den angemeldeten Benutzer:
    
  - Lokale Administratorberechtigungen auf dem Entwicklungscomputer installiert.
    
  
  - Verwalten von Website und Erstellen von Unterwebsites von Benutzerberechtigungen für die SharePoint-Website, in dem Sie die app installieren möchten. Standardmäßig sind diese Berechtigungen nur für Benutzer über die Berechtigungsstufe Vollzugriff verfügen oder Personen in der Gruppe Websitebesitzer sind verfügbar.
    
  
  - Sie müssen als eine andere Person als das Systemkonto angemeldet sein. Das Systemkonto verfügt nicht über die Berechtigung, die app installieren.
    
  

> **HINWEIS**
> Finden Sie unter  [Einrichten einer lokalen Entwicklungsumgebung für SharePoint-Add-Ins](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx) Hinweise zum lokalen Setup (einschließlich wie das Kontrollkästchen Loopback deaktivieren, falls erforderlich).
  
    
    


  
    
    

## Erstellen Sie das SharePoint-Add-In-Projekt.
<a name="bkmk_CreateApp"> </a>


1. Klicken Sie auf Ihrer Entwicklerwebsite öffnen Sie Napa, und wählen Sie dann auf **Neues Projekt hinzufügen**.
    
  
2. Wählen Sie die Vorlage **App für SharePoint**, nennen Sie das Projekt, und wählen Sie dann auf die Schaltfläche **Erstellen**.
    
  
3. Legen Sie die Berechtigungen für Ihre app:
    
1. Wählen Sie die Schaltfläche " **Eigenschaften** " am unteren Rand der Seite.
    
  
2. Wählen Sie im Fenster **Eigenschaften** **Berechtigungen**.
    
  
3. Legen Sie **die Inhaltskategorie** **Write** Berechtigungen für den **Mandanten** Bereich.
    
  
4. Legen Sie in der Kategorie **für soziale Netzwerke** **Read** -Berechtigungen für den Bereich **Von Benutzerprofilen**.
    
  
5. Das Fenster **Eigenschaften** zu schließen.
    
  
4. Erweitern Sie den Knoten **Skripts**, wählen Sie die Datei App.js, und Ersetzen Sie den Inhalt durch den Code aus einem der folgenden Szenarien:
    
  -  [Starten Sie nach und nicht mehr Folgen eines Dokuments](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowDocs)
    
  
  -  [Starten Sie nach und nicht mehr folgen einer Website](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowSites)
    
  
  -  [Nach Starten Sie und beenden Sie einer Kategorie folgen](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowTags)
    
  
  -  [Abrufen von verfolgten Inhalt](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_GetFollowed)
    
  
5. Um die app ausgeführt werden soll, wählen Sie die Schaltfläche " **Projekt ausführen** " am unteren Rand der Seite.
    
  
6. Wählen Sie die Schaltfläche **Vertrauen sie** **Vertrauen Sie** Sie auf der Seite, die geöffnet wird. Die appseite wird geöffnet, und es wird der Code ausgeführt. Debuggen Sie die Seite, wählen die **F12**-Taste, und wählen Sie dann auf der Registerkarte **Skript** App.js aus.
    
  

## Codebeispiel: Starten Sie nach und nach einem Dokument mithilfe des REST-Diensts SharePoint 2013 beenden
<a name="bkmk_FollowDocs"> </a>

Das folgende Codebeispiel stellt den Inhalt der App.js-Datei und zeigt, wie Sie:
  
    
    

- Möchten Sie app-Webs URI aus der Abfragezeichenfolge erhalten, und erstellen Sie den  `<siteUri>/_api/social.following` Endpunkt-URI.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `isfollowed` , um herauszufinden, ob der aktuelle Benutzer bereits ein angegebenes Dokument folgt.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `follow` , um nach dem Dokument zu starten.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `stopfollowing` So beenden Sie nach dem Dokument.
    
  
- Lesen Sie die JSON-Antwort von der Anforderung  `isfollowed` und die Anforderung `follow` zurückgegeben. (Die Anforderung `stopfollowing` nicht nichts in der Antwort zurück.) Siehe [Beispiel JSON Antworten](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses).
    
  
Bevor Sie den Code ausführen müssen Sie zum Hochladen eines Dokuments und ändern den Platzhalterwert für die Variable **documentUrl** an die URL des Dokuments.
  
    
    



```

// Replace the documentUrl placeholder value before you run the code.
var documentUrl = "https://domain.sharepoint.com/Shared%20Documents/fileName.docx";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the document.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the document.');
                stopFollowDocument();
            }
            else {
                alert('The user is currently NOT following the document.');
                followDocument();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a document.
// The request body includes a SocialActorInfo object that represents
// the document to follow.
// The success function reads the response from the REST service.
function followDocument() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the document. ',
                1 : 'The user is already following the document. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a document.
// The request body includes a SocialActorInfo object that represents
// the document to stop following.
function stopFollowDocument() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the document.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## Codebeispiel: Starten Sie nach und nach einer Website mithilfe des REST-Diensts SharePoint 2013 beenden
<a name="bkmk_FollowSites"> </a>

Das folgende Codebeispiel stellt den Inhalt der App.js-Datei und zeigt, wie Sie:
  
    
    

- Möchten Sie app-Webs URI aus der Abfragezeichenfolge erhalten, und erstellen Sie den  `<siteUri>/_api/social.following` Endpunkt-URI.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `isfollowed` , um herauszufinden, ob der aktuelle Benutzer eine angegebene Website bereits folgen.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `follow` , um nach der Website zu starten.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `stopfollowing` So beenden Sie nach der Website.
    
  
- Lesen Sie die JSON-Antwort von der Anforderung  `isfollowed` und die Anforderung `follow` zurückgegeben. (Die Anforderung `stopfollowing` nicht nichts in der Antwort zurück.) Siehe [Beispiel JSON Antworten](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses).
    
  
Bevor Sie den Code ausführen ändern Sie den Platzhalterwert für die Variable **siteUrl** entsprechend die Website, die Sie folgen möchten. Verwenden Sie das Format **http://server/siteCollection/site** für eine Website in einer Websitesammlung. Führen Sie eine Website über eine beliebige Seite oder eine Bibliothek an diesem Standort. Wenn die Website eine Vorlage verwendet wird, die nicht unterstützt erhalten (wie meine Website-Host oder einer persönlichen Website) folgen einen **UnsupportedSite** -Fehler (Fehlercode 10) Sie.
  
    
    



```

// Replace the siteUrl placeholder value before you run the code.
var siteUrl = "https://domain.sharepoint.com";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the site.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the site.');
                stopFollowSite();
            }
            else {
                alert('The user is currently NOT following the site.');
                followSite();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a site.
// The request body includes a SocialActorInfo object that represents
// the site to follow.
// The success function reads the response from the REST service.
function followSite() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the site. ',
                1 : 'The user is already following the site. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a site.
// The request body includes a SocialActorInfo object that represents
// the site to stop following.
function stopFollowSite() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the site.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## Codebeispiel: nach starten und Beenden einer Kategorie mithilfe des REST-Diensts SharePoint 2013 folgen
<a name="bkmk_FollowTags"> </a>

Das folgende Codebeispiel stellt den Inhalt der App.js-Datei und zeigt, wie Sie:
  
    
    

- Möchten Sie app-Webs URI aus der Abfragezeichenfolge erhalten, und erstellen Sie den  `<siteUri>/_api/social.following` Endpunkt-URI.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `isfollowed` , um herauszufinden, ob der aktuelle Benutzer ein angegebenes Tag bereits folgen.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `follow` , um die Kategorie folgen zu starten.
    
  
- Erstellen Sie und senden Sie eine **POST** -Anforderung an den Endpunkt `stopfollowing` So beenden Sie die Kategorie folgen.
    
  
- Lesen Sie die JSON-Antwort von der Anforderung  `isfollowed` und die Anforderung `follow` zurückgegeben. (Die Anforderung `stopfollowing` nicht nichts in der Antwort zurück.) Weitere Informationen finden Sie unter [Beispiel JSON Antworten](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses).
    
  
Ändern Sie den Platzhalterwert für die Variable **tagGuid** vor dem Ausführen des Codes die GUID der vorhandene Tags. Die Taxonomie-API, die Sie verwenden, um ein Tag aus der **HashTagsTermSet** abzurufen keine REST-Schnittstelle, daher Sie in das Clientobjektmodell .NET oder das JavaScript-Objektmodell verwenden müssen. Ein Beispiel finden Sie unter [So rufen Sie die GUID eines Tags auf der Basis des Namens des Tags mithilfe des JavaScript-Objektmodells ab](follow-content-in-sharepoint-2013.md#bk_getTagGuid) .
  
    
    



```

// Replace the tagGuid placeholder value before you run the code.
var tagGuid = "19a4a484-c1dc-4bc5-8c93-bb96245ce928";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the tag.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the tag.');
                stopFollowTag();
            }
            else {
                alert('The user is currently NOT following the tag.');
                followTag();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a tag.
// The request body includes a SocialActorInfo object that represents
// the tag to follow.
// The success function reads the response from the REST service.
function followTag() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the tag. ',
                1 : 'The user is already following the tag. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a tag.
// The request body includes a SocialActorInfo object that represents
// the tag to stop following.
function stopFollowTag() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the tag.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## Get-Codebeispiel Hochladen von Inhalten mithilfe des REST-Diensts SharePoint 2013
<a name="bkmk_GetFollowed"> </a>

Das folgende Codebeispiel stellt den Inhalt der App.js-Datei und zeigt, wie Sie:
  
    
    

- Möchten Sie app-Webs URI aus der Abfragezeichenfolge erhalten, und erstellen Sie den  `<siteUri>/_api/social.following` Endpunkt-URI.
    
  
- Erstellen Sie und senden Sie eine **GET** -Anforderung an den Endpunkt `my/followedcount` , um die Anzahl der Inhalte abzurufen, die der aktuelle Benutzer folgt.
    
  
- Erstellen Sie und senden Sie eine **GET** -Anforderung an den Endpunkt `my/followed` , um den Inhalt abzurufen, den der aktuelle Benutzer folgt.
    
  
- Lesen Sie die JSON-Antwort von der Anforderungen zurückgegeben. Siehe  [Beispiel JSON Antworten](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses).
    
  

```

var followingManagerEndpoint;
var followedCount;

// Get the SPAppWebUrl parameter from the query string and build
// the following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl)+ "/_api/social.following";
    getMyFollowedCount();
} );

// Get the count of content that the current user is following.
// The "types=14" parameter specifies all content types
// (documents = 2 + sites = 4 + tags = 8).
function getMyFollowedCount() {
    $.ajax( {
        url: followingManagerEndpoint + "/my/followedcount(types=14)",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: function (data) { 
            followedCount = data.d.FollowedCount;
            getMyFollowedContent();
        },
        error: requestFailed
    } );
}

// Get the content that the current user is following.
// The "types=14" parameter specifies all content types
// (documents = 2 + sites = 4 + tags = 8).
function getMyFollowedContent() {
    $.ajax( {
        url: followingManagerEndpoint + "/my/followed(types=14)",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: followedContentRetrieved,
        error: requestFailed
    });
}

// Parse the JSON data and iterate through the collection.
function followedContentRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
    var types = {
        1: "document",
        2: "site",
        3: "tag" 
    };
 
    var followedActors = jsonObject.d.Followed.results; 
    var followedList = "You're following " + followedCount + " items:";
    for (var i = 0; i < followedActors.length; i++) {
        var actor = followedActors[i];
        followedList += "<p>The " + types[actor.ActorType] + ": \\"" +
        actor.Name + "\\"</p>";
    } 
    $("#message").html(followedList); 
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## Beispiel von JSON Antworten für folgende inhaltsanforderungen
<a name="bk_exampleResponses"> </a>

Standardmäßig gibt des REST-Diensts Antworten, die mithilfe des Atom-Protokolls formatiert sind, aber Sie können das JSON-Format mithilfe von HTTP-Headers **Accept** anfordern (zum Beispiel: `"accept":"application/json;odata=verbose"`). Die Antwortdaten werden als Zeichenfolge zurückgegeben, und können die **JSON.stringify** und **JSON.parse** konvertiert die Zeichenfolge in ein Objekt, wie in den vorherigen Codebeispielen dargestellt.
  
    
    
Betrachten Sie um einen von der REST-Dienst im Debugmodus zurückgegebenen Fehler beheben die **responseText** -Eigenschaft, wie die **requestFailed** Rückruffunktionen in den vorherigen Beispielen gezeigt aus. Sie können auch die Korrelations-ID für die Server-ULS-Protokoll aus einem Netzwerksniffer oder HTTP-Debugger, wie beispielsweise Fiddler abrufen. Die Korrelations-ID ist die gleiche wie die-ID in der HTTP-Antwort.
  
    
    

### Beispielantwort für den Endpunkt folgen

Als Reaktion auf Anfragen an den Endpunkt  `follow` mithilfe der clientseitigen gibt der REST-Dienst einen **SocialFollowResult** -Wert, der angibt, ob die Anforderung **Follow** erfolgreich war.
  
    
    
Die folgende Antwort stellt den Status **AlreadyFollowing** dar.
  
    
    



```

{"d":{"Follow":1}}
```

Tabelle 1 zeigt **SocialFollowResult** Statuscodes und deren Werte an.
  
    
    

**In Tabelle 1. SocialFollowResult Codes und Werte**

|||
|:-----|:-----|
|0 <br/> |**OK**. Der aktuelle Benutzer ist nun den Akteur folgen. <br/> |
|1 <br/> |**AlreadyFollowing**. Der aktuelle Benutzer ist den Akteur bereits folgen. <br/> |
|2 <br/> |**LimitReached**. Fehler bei der Anforderung, da ein internes Limit erreicht wurde. <br/> |
|3 <br/> |**InternalError**. Fehler bei der Anforderung aufgrund eines internen Fehlers. <br/> |
   

> **HINWEIS**
> Der REST-Dienst zurückgeben keine Antwort für die Anforderung **StopFollowing**. Es gibt `{"d":{"StopFollowing":null}}`zurück.
  
    
    


### Beispielantwort für den Endpunkt IsFollowed

Als Reaktion auf Anfragen an den Endpunkt  `isfollowed` mithilfe der clientseitigen gibt der REST-Dienst einen **bool** -Wert, der angibt, ob der aktuelle Benutzer den angegebenen Akteur folgt.
  
    
    
Die folgende Antwort gibt an, dass der aktuelle Benutzer nicht das angegebene Dokument, eine Website oder ein Tag folgt.
  
    
    



```
{"d":{"IsFollowed":false}}
```


### Beispielantwort für den Endpunkt Meine/besuchter

Als Reaktion auf Anfragen an den Endpunkt  `my/followed` mithilfe der clientseitigen gibt der REST-Dienst ein Array von **SP.Social.SocialActor** -Objekten, die Dokumenten, Websites und Tags, die der aktuelle Benutzer folgt darstellen.
  
    
    
Die folgende Antwort stellt eine besuchter Dokument, Website und Tag. Die Anforderung gibt die Arten von Inhalt enthalten.
  
    
    



```
{"d":{"Followed":{"results":[
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":1
    "CanFollow":true
    "ContentUri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"2.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.
      51bbb5d8e214457ba794669345d23040.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"snippets.txt"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"00000000-0000-0000-0000-000000000000"
    "Title":null
    "Uri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
  }
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":2
    "CanFollow":true
    "ContentUri":"https://domain.sharepoint.com:443/"
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"8.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.
      089f4944a6374a64b52b7af5ba140392.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"Developer Site"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"00000000-0000-0000-0000-000000000000"
    "Title":null
    "Uri":"https://domain.sharepoint.com:443/"
  }
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":3
    "CanFollow":true
    "ContentUri":null
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"16.00000000000000000000000000000000.00000000000000000000000000000000.
      19a4a484c1dc4bc58c93bb96245ce928.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"#someTag"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928"
    "Title":null
    "Uri":"https://domain-my.sharepoint.com:443/_layouts/15/HashTagProfile.aspx?
      TermID=19a4a484-c1dc-4bc5-8c93-bb96245ce928"
  }
]}}}
```


### Beispielantwort für den Endpunkt Meine/FollowedCount

Als Reaktion auf Anfragen an den Endpunkt  `my/followedcount` mithilfe der clientseitigen gibt der REST-Dienst einen **Int32** -Wert, der die Gesamtzahl der angegebenen Actor Typen darstellt, die der aktuelle Benutzer folgt.
  
    
    
Die folgende Antwort stellt eine Anzahl von drei beobachteter Dokumente, Websites und/oder Tags dar. Die Anforderung gibt die Arten von Inhalt enthalten.
  
    
    



```

{"d":{"FollowedCount":3}}
```


## Zusätzliche Ressourcen
<a name="bkmk_AddtionalResources"> </a>


-  [Folgen von Inhalten in SharePoint 2013](follow-content-in-sharepoint-2013.md)
    
  
-  [REST-API-Referenz zum Folgen von Personen und Inhalten für SharePoint 2013](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Führen Sie Dokumente und Websites mit .NET Client-Objektmodell in SharePoint 2013](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  

