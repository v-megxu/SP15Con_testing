---
title: Erstellen von Websites für SharePoint
ms.prod: SHAREPOINT
ms.assetid: 3b372a63-7cdf-462a-abb4-750e611e967d
---


# Erstellen von Websites für SharePoint
Hier finden Sie Informationen zum neuen Websiteerstellungs- und Veröffentlichungsmodell für Websites in SharePoint 2013.
## Einführung in die Websiteveröffentlichung für Designer und Entwickler in SharePoint
<a name="SP15_BuildSitesForSP2013_IntroToSitePublishing"> </a>

SharePoint 2013 führt ein Websiteerstellungs- und Veröffentlichungsmodell zur Erstellung von Veröffentlichungswebsites ein. Mithilfe von Veröffentlichungswebsites können Sie Inhalte auf Intranet- oder Internetsites veröffentlichen. Veröffentlichungswebsites unterscheiden sich von anderen Typen von SharePoint-Websites wie Teamsites hauptsächlich aufgrund ihres Zwecks: Viele Benutzer lesen Inhalte auf Veröffentlichungswebsites, aber nur wenige leisten einen Beitrag, indem sie Inhalte aus einer oder mehreren Websitesammlungen hinzufügen, aktualisieren und löschen. Im Gegensatz dazu stehen Teamwebsites, an denen möglicherweise viele Benutzer zusammenarbeiten und zu den Inhalten beitragen.
  
    
    
Sie können die Websiteveröffentlichungsfunktionen von SharePoint 2013 verwenden, um Veröffentlichungswebsites, die bestimmte Geschäftsanforderungen erfüllen, zu erstellen, anzupassen und zu verwalten. Ob Sie nun ein professioneller Webdesigner mit Kenntnissen in HTML, CSS und JavaScript oder ein Entwickler sind, der SharePoint-Apps schreibt und benutzerdefinierten .NET-Code verwendet, um Websites und Farmlösungen zu erstellen: Sie können mithilfe von Websitefeatures in SharePoint 2013 alle Phasen des Inhaltslebenszyklus verwalten. Dazu zählen:
  
    
    

- **Authoring** und Wiederverwenden von Websiteinhalten
    
  
- **Branding** und Entwerfen des Aussehen und Verhaltens Ihrer Website
    
  
- **Managing metadata** - Sie können ein taxonomiegesteuertes Websitenavigationssystem erstellen.
    
  
- Problemloses **Publishing** von Inhalten in der aktuellen Websitesammlung oder Veröffentlichen von Inhalten in mehreren Websitesammlungen, auch über die Grenzen der Intranet- und Internetsite hinweg
    
  
- **Accessibility** - Sie können die Barrierefreiheit Ihrer veröffentlichten Websites verbessern.
    
  
Eine Zusammenfassung der Neuigkeiten für Designer und Entwickler von veröffentlichten Websites in SharePoint 2013 finden Sie unter  [Neuerung bei SharePoint 2013-Websiteentwicklung](what-s-new-with-sharepoint-2013-site-development.md).
  
    
    

## Erstellung, Entwurf und Branding in SharePoint
<a name="SP15_BuildSitesForSP2013_AuthoringDesignBranding"> </a>

SharePoint 2013 bietet einen neuen Ansatz für den Entwurf von Websites. Der Inhaltserstellungsworkflow wurde so überarbeitet, dass Sie mit jedem beliebigen Entwurfstool tolle Inhalte erstellen können. Um Ihre Website mit Ihrem Branding zu versehen, ohne benutzerdefinierten .NET-Code schreiben zu müssen, importieren Sie Entwurfselemente mithilfe des  [Entwurfs-Managers](overview-of-design-manager-in-sharepoint-2013.md). Mit dem Entwurfs-Manager können Sie auch eine HTML-basierte Gestaltungsvorlage erstellen, um das Chrome zu definieren, das von allen Seiten Ihrer Website verwendet wird, und Seitenlayouts zum Entwerfen von Seitenvorlagen erstellen. Wenn Sie benutzerdefinierten Code schreiben möchten, können Sie .NET server, .NET client (CSOM), Silverlight und JavaScript-Bibliotheken verwenden.
  
    
    
SharePoint 2013 bietet außerdem einen neuen Ansatz für Inhalte und deren Erstellung. Der Inhaltserstellungsworkflow wurde so überarbeitet, dass Sie mit jedem beliebigen Erstellungs- und Brandingtool tolle Inhalte erstellen können. Um Ihre Website mit Ihrem Branding zu versehen, ohne benutzerdefinierten ASP.NET-Code schreiben zu müssen, verwenden Sie den Entwurfs-Manager. Sie können Entwurfselemente importieren und eine HTML-basierte Gestaltungsvorlage erstellen, um die gemeinsamen Framingelemente, das Chrome, zu definieren, das alle Seiten und Seitenlayouts Ihrer Website verwenden. Wenn Sie benutzerdefinierten Code schreiben möchten, wenn Sie Ihre Website mit Ihrem Branding versehen, können Sie die Veröffentlichungs- und Taxonomiebibliotheken verwenden.
  
    
    

## Veröffentlichen von Websites, Clientobjektmodell-Programmierung und das neue SharePoint-App-Modell
<a name="SP15_BuildSitesForSP2013_PublishingSites"> </a>

Sie können das neue .NET-Clientobjektmodell (CSOM) verwenden, um SharePoint-Apps mit dem Modell für SharePoint-Add-Ins zu entwickeln. Sie können viele der APIs verwenden, die auch für .NET-Serverprogrammierung in den .NET-Clientobjektmodellen verfügbar sind, die .NET client-, Silverlight-, JavaScript- und in einigen Fällen Windows Phone-Entwicklung unterstützen. Ideen für die Entwicklung von Apps für Websites sind etwa Umfragen, Kontoverwaltungs-Apps, E-Commerce-Support, Integration sozialer Features und externer Daten in Veröffentlichungswebsites, Hinzufügen outgesourcter Inhalte und mobile Begleit-Apps.
  
    
    

## Seitenmodell für die Veröffentlichung von Websites
<a name="SP15_BuildSitesForSP2013_PageModel"> </a>

SharePoint 2013 enthält ein Seitenmodell für Veröffentlichungswebsites. Das Seitenmodell umfasst Gestaltungsvorlagen, Seitenlayouts und andere Komponenten, die die Struktur, die Inhalte, das Aussehen und das Verhalten Ihrer Website wiedergeben. Weitere Informationen finden Sie unter  [Übersicht über das SharePoint 2013-Seitenmodell](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Gestaltungsvorlagen und Seitenlayouts
<a name="SP15_BuildSitesForSP2013_MasterAndLayout"> </a>

Eine Gestaltungsvorlage ist die Hauptvorlage, welche die gemeinsam verwendeten strukturellen Elemente Ihrer Website definiert: das Chrome. Alle Seiten der Website verwenden diese Elemente gemeinsam, welche die Bereiche der Seite definieren, in denen Seitenlayoutinhalte angezeigt werden.
  
    
    
Seitenlayouts werden von einzelnen Seiten eines bestimmten Typs verwendet. Sie werden mit Anordnungen von Seitenfeldern aufgefüllt. Diese Seiten definieren einzelne Elemente auf der Seite. Einzelne Seiten basieren auf Seitenlayouts und werden in Ihrem Webbrowser entweder durch benutzerdefinierten Code oder dadurch erstellt, wie die Benutzer der Website die Felder der Seite ausfüllen. Weitere Informationen zum Seitenmodell in SharePoint 2013 finden Sie unter  [Übersicht über das SharePoint 2013-Seitenmodell](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Clientseitige Rendering-Steuerelemente
<a name="SP15_BuildSitesForSP2013_ClientSideRendering"> </a>

Alle neuen Steuerelemente in SharePoint 2013 werden gerendert. Daten werden in die Steuerelemente in einem clientseitigen JSON-Array geschrieben, und Sie können Inhalte mithilfe von JavaScript, CSS und Vorlagen anzeigen. Als Webdesigner oder -entwickler können Sie steuern, wie Inhalte auf der Seite gerendert werden, und Sie können mithilfe von Features wie dem  [Inhaltssuche-Webpart in SharePoint 2013](content-search-web-part-in-sharepoint-2013.md) und Anzeigevorlagen verschiedene Entwurfstechniken verwenden, um auf Ihren veröffentlichten Seiten das gewünschte Aussehen und Verhalten zu erhalten.
  
    
    

## Websites und mobile Geräte
<a name="SP15_BuildSitesForSP2013_SitesAndMobile"> </a>

Veröffentlichungswebsites in SharePoint 2013 sind für die Entwicklung mobiler Websites optimiert. Sie können Kanäle für ein oder mehrere Geräte (Gerätekanäle) definieren und für jeden Kanal eine alternative Gestaltungsvorlage und damit einzigartige strukturelle Elemente oder Chrome zuweisen. Sie können in einem Kanal Teile eines beliebigen Seitenlayouts ein- oder ausschließen, und während der Entwicklung in der Vorschau anzeigen, wie das mobile Kanaldesign verarbeitet wird.
  
    
    

## Metadaten und Navigation in SharePoint
<a name="SP15_BuildSitesForSP2013_MetadataNav"> </a>

In Microsoft SharePoint Server 2010 eingeführte verwaltete Metadatenfunktionen wurden in SharePoint 2013 verbessert und erweitert. Sie bieten jetzt eine bessere Leistung, leichteren Zugriff über die Benutzeroberfläche und taxonomiegesteuerte Navigation, die als verwaltete Navigation bezeichnet wird. Sie können zur Erstellung Ihrer Websitenavigation verwaltete Navigation oder auf der SharePoint-Websitestruktur basierte Navigation, die alsstrukturierte Navigation bezeichnet wird, verwenden. Weitere Informationen zur verwalteten Navigation finden Sie unter [Verwaltete Metadaten und Navigation in SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md) und [Verwaltete Navigation in SharePoint 2013](managed-navigation-in-sharepoint-2013.md).
  
    
    

## Veröffentlichung von Inhalten in SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingContent"> </a>

SharePoint 2013 bietet die folgenden neuen Inhaltsveröffentlichungsfeatures, mit denen Sie Veröffentlichungswebsites entwickeln können, die neue, flexiblere und komplexere Topologien und Szenarios mit größerer Barrirefreiheit unterstützen.
  
    
    

### Kataloge

SharePoint 2013 führt Kataloge ein, die Sie zum Veröffentlichen von Inhalten über Websitesammlungen hinweg verwenden können. Für Features zur websiteübergreifenden Veröffentlichung sind Kataloge erforderlich. Sie können sie verwenden, um Inhalte auf Ihren Websites und außerhalb der Grenzen zwischen Ihren Intranet- und Internetsites wiederzuverwenden. Für vordefinierte Suchanfragen werden Kataloge in der Suche markiert. Sie können in Katalogen gespeicherte Inhalte mithilfe des [Inhaltssuche-Webpart in SharePoint 2013](content-search-web-part-in-sharepoint-2013.md) in mehreren Websitesammlungen bereitstellen.
  
    
    

### Websiteübergreifendes Veröffentlichen

SharePoint 2013 führt ein neues Feature zur websiteübergreifenden Veröffentlichung ein, um Inhalte in mehreren Websitesammlungen wiederzuverwenden. Es verwendet integrierte Suchfunktionen, um Veröffentlichungsszenarios und -architekturen zu ermöglichen. Zum ersten Mal können Sie SharePoint-Farmen übergreifende Websites entwerfen, sodass Ihre Websites die Grenzen zwischen Intranets und dem Internet überspannen. Sie können das CSWP verwenden, um Suchdaten anzuzeigen, die aus verschiedenen Websites und Websitesammlungen veröffentlicht werden.
  
    
    

### Variationen und mehrsprachige Websites

Sie können das Variationsfeature in SharePoint 2013 zum Erstellen von mehrsprachigen Websites oder anderen Websites verwenden, in denen Sie die Darstellung des Inhalts variieren möchten. Das Variationsfeature ist auf eine Websitesammlung beschränkt. Sie können zielsprachliche/lokale "Varianten" einer quellsprachlichen/lokalen Website als aktuelle Websites in derselben SharePoint-Websitesammlung erstellen. Varianten unterstützten benutzerfreundliche URLs sowie die Möglichkeit, Inhalte für eine Übersetzung durch Dritte in einem  [XLIFF-Dateiformat](the-xliff-interchange-file-format-in-sharepoint-2013.md) zu ex- und importieren. Sie können Beschriftungen, eine Seite für Übersetzung und Replizierung, eine Reihe von Listenelementen (wie Dokumentbibliotheken) und Navigationssteuerelemente in Ihr Exportpaket mit aufnehmen.
  
    
    

### Barrierefreie Websites

Sie können das Variationsfeature in SharePoint 2013 verwenden, um barrierefreie Websites oder andere Websites zu erstellen, wenn Sie die Präsentation Ihrer Inhalte für Benutzer mit unterschiedlichen Anforderungen im Zusammenhang mit Barrierefreiheit anpassen möchten. SharePoint 2013 stellt einen "Zugriffsfreundlicheren Modus" bereit, der durch Öffnen einer SharePoint-Webseite und Drücken der TAB-Taste bis zu dem Link "Aktivieren des zugriffsfreundlicheren Modus" aktiviert werden kann. Dieses Feature erstellt die Webseite in standardmäßigen HTML-Code neu, wodurch sie für Bildschirmleseprogramme leichter zu lesen ist. Indem Sie sicherstellen, dass Benutzer die TAB-Taste drücken können, um auf diesen Link zu fokussieren, können Sie eine zugriffsfreundlichere Version Ihrer SharePoint-Webseite erstellen. Dies umfasst JavaScript-basierte Dropdownmenüs, die in Hyperlinklisten konvertiert werden, und Objekte werden in einfacheres HTML konvertiert, damit Bildschirmleseprogramme den Inhalt verstehen. 
  
    
    

## Zusätzliche Ressourcen
<a name="SP15_BuildSitesForSP2013_AdditionalResources"> </a>


-  [Optimieren von SharePoint-Website zur Barrierefreiheit](optimize-sharepoint-site-accessibility.md)
    
  
-  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md)
    
  
-  [Neuerung bei SharePoint 2013-Websiteentwicklung](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [Übersicht über die minimale Strategie herunterladen](minimal-download-strategy-overview.md)
    
  
-  [Ändern von SharePoint-Komponenten für MDS](modify-sharepoint-components-for-mds.md)
    
  
-  [Serverklassenbibliothek für Websites und Inhalte für SharePoint 2013](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)
    
  
-  [Clientklassenbibliothek für Websites und Inhalte](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx)
    
  

