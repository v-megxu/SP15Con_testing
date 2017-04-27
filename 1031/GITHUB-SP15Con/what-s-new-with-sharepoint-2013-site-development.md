---
title: Neuerung bei SharePoint 2013-Websiteentwicklung
ms.prod: SHAREPOINT
ms.assetid: ac1e9891-5ce9-4707-84e5-6e2fc02fda6b
---


# Neuerung bei SharePoint 2013-Websiteentwicklung
Informationen über das neue Erstellungs -und Veröffentlichungsmodell in SharePoint 2013 zur Veröffentlichung von Websites.
## Einführung in die Websiteerstellung für Designer und Entwickler in SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_IntroductionToSitePublishing"> </a>

SharePoint 2013 führt die folgenden Features neu ein. Sie unterstützen den Workflow einer ECM-Websiteerstellung (Enterprise Content Management) für Veröffentlichungssites.
  
    
    

### Clientprogrammierungsmodelle für die Entwicklung von Veröffentlichungssites

In SharePoint 2013 können Sie das .NET-Clientobjektmodell (CSOM), Silverlight und die JavaScript-Programmierungsmodelle zum Entwickeln von benutzerdefinierten Websites, Sitekomponenten, Branding-Elementen und Verhalten verwenden. Viele der für die .NET-Serverprogrammierung verfügbaren APIs finden Sie im entsprechenden .NET-Client (CSOM), in Silverlight und in JavaScript-Assemblys. In einigen Fällen sind die entsprechenden APIs auch in Windows Phone-Bibliotheken verfügbar.
  
    
    
Weitere Informationen finden Sie in den Referenzhomepages zu Websites und Inhalten für  [.NET-Server](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx),  [.NET-Client](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx) und [JavaScript](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx). Sie können auch mit der  [-Referenzhomepage](http://msdn.microsoft.com/library/7940ba4e-f6f0-4bc0-b995-ceb2d358ca0d%28Office.15%29.aspx) beginnen, falls Sie ganz oben beginnen möchten und dann die Inhalte der einzelnen Programmierungsmodelle kennen lernen wollen.
  
    
    

### Verwenden von Veröffentlichungs- und Taxonomie-APIs im neuen SharePoint-App-Modell

Sie können benutzerdefinierten Client- und Servercode in SharePoint-Add-Ins schreiben und damit die SharePoint-Veröffentlichungs- und Taxonomiefunktionalität erweiterten. Diese steht den Benutzern auf der Benutzeroberfläche (UI) bereit. 
  
    
    
Einige Punkte bei der Entwicklung von Apps, die eine Websiteveröffentlichung verbessern, sind Umfragen, Kontoverwaltungs-Apps, eCommerce-Support, Apps, die soziale Funktionen und externe Daten in Veröffentlichungssites beinhalten, ausgelagerte zusätzliche Inhalte sowie mobile Begleit-Apps.
  
    
    

## Erstellungs-, Entwurfs- und Branding-Features
<a name="SP15_WhatsNewSiteDevelopment_AuthoringAndBranding"> </a>

SharePoint 2013 enthält Features und APIs für das Erstellen, Entwerfen, Branding und Erweitern Ihrer Website, des Websitedesigns, der Branding-Elemente und des Websiteverhaltens. 
  
    
    

### Entwurfs-Manager

In früheren SharePoint-Versionen benötigte das Branding einer Website spezielle technische Kenntnisse beispielsweise zu Inhaltsplatzhaltern auf der Masterseite oder wie eine Masterseite bestimmte Steuerelementformatklassen bereitstellt. SharePoint 2013 führt den  [Entwurfs-Manager](overview-of-design-manager-in-sharepoint-2013.md) ein, die neue Schnittstelle und zentraler Hub für die Verwaltung aller Branding-Aspekte auf Ihrer SharePoint-Website. Sie finden den Entwurfs-Manager auf der obersten Website Ihrer Websitesammlung. Er ist Teil der Websitesammlungsvorlage "Veröffentlichungsportal" in SharePoint 2013.
  
    
    
Mit dem Entwurfs-Manager können Sie Designobjekte für ein Branding von Websites Schritt für Schritt erstellen. Laden Sie Designobjekte (Bilder, HTML, CSS usw.) hoch, und erstellen Sie dann Ihre Masterseiten und Seitenlayouts. Sie könne Ihren Entwurf entweder in einem clientseitigen Codeeditor oder auf den Server während des Erstellvorgangs anzeigen. Weiterhin können Sie SharePoint-Komponenten und Menübandelemente über die Benutzeroberfläche des Entwurfs-Managers hinzufügen. Der Entwurfs-Manager generiert  [-Snippets](sharepoint-2013-design-manager-snippets.md) in HTML, die von jedem Webentwurfstool verwendet werden können. Er rendert HTML und ignoriert ASP.NET- und SharePoint-Markup (während hingegen SharePoint nur ASP.NET- und SharePoint-Markup rendert und HTML ignoriert).
  
    
    
Mit Ihren Kenntnissen in HTML, CSS und JavaScript können Sie Masterseiten in HTML entwerfen und HTML-Seitenlayouts in einem HTML-Editor Ihrer Wahl entwickeln. Für eine Verknüpfung Ihres Lieblingstools für Erstellung und Entwurf mit Ihrer SharePoint-Website,  [ordnen Sie ein Netzwerklaufwerk zu](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md) und bearbeiten dann die SharePoint-Datei wie eine lokale Datei. Nach Fertigstellung des Websitedesigns laden Sie die HTML- und die unterstützenden Dateien hoch und verwenden den Entwurfs-Manager zum [Konvertieren der HTML-Datei in eine ASP.NET-Masterseite (.master-Datei)](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md). Dann  [wenden Sie die Masterseite](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md) auf Ihre SharePoint-Website an. Mit dem Entwurfs-Manager [erstellen Sie ein neues Seitenlayout](how-to-create-a-page-layout-in-sharepoint-2013.md), und die HTML-Version der Seite wird automatisch mit der entsprechenden ASP.NET-Seite (.aspx-Datei) verknüpft, die SharePoint interpretieren kann. 
  
    
    
Nachdem Sie Ihre HTML-Dateien konvertiert haben, verfeinern Sie Ihren Entwurf im HTML-Editor, zeigen Ihre Dateien in einer Vorschau an und speichern sie. Immer wenn Sie HTML-Versionen der Masterseite oder der Seitenlayoutdateien speichern, aktualisiert SharePoint 2013 automatisch die damit verbundene SharePoint-Masterseite und die Seitenlayouts, um den Änderungen Rechnung zu tragen. 
  
    
    
Mit dem Entwurfs-Manager müssen Sie nur die HTML-Dateien bearbeiten. Sie können weiterhin benutzerdefinierte Masterseite und Seitenlayouts mit Ihren ASP.NET- und SharePoint-Entwicklungskenntnissen erstellen. Der Entwurfs-Manager befähigt Sie auch ohne große SharePoint-Entwicklerkenntnisse, großartige Websites zu entwerfen.
  
    
    
SharePoint 2013 beinhaltet auch HTML-Versionen mehrerer Masterseiten und Seitenlayouts, die Sie als Startvorlagen nutzen können. Wenn Sie mit diesen Dateien beginnen möchten, erstellen Sie eine Kopie der HTML-Seite (die verknüpfte ASP.NET-Datei wird automatisch verarbeitet), und bearbeiten Sie dann die HTML-Datei in der üblichen Weise. Sie können auch mit einer Basisvorlage beginnen, indem Sie die Option **Masterseite aus Minimalvorlage** verwenden, die dann selbsttätig die damit verbundene .master-Datei erstellt.
  
    
    

### Codeausschnittkatalog

SharePoint 2013 enthält viele einsatzbereite Komponenten, wie Webparts und Steuerelemente, die Sie Ihren Webseiten hinzufügen können. Beispiel: Sie fügen eine SharePoint-Komponente, wie ein Suchfeld oder ein Navigationssteuerelement, in die HTML-Masterseite ein, um somit schnell und einfach viel Funktionalität in Ihre Seiten einzubauen.
  
    
    
Im Menüband in der Gruppe **Codeausschnittkatalog** können Sie eine Komponente auswählen und ihre Eigenschaften konfigurieren, den Codeausschnitt aktualisieren, sowie den gerade generierten HTML-Codeausschnitt kopieren und in die HTML-Datei einfügen. Der HTML-Codeausschnitt ermöglicht Ihnen eine sehr getreue Vorschau der Komponente in der serverseitige Vorschau und im HTML-Editor Ihrer Wahl. Nach dem Hinzufügen von SharePoint-Komponenten in die HTML-Dateien können Sie diese mithilfe von CSS vollständig mit einem Branding versehen. Nachdem Sie SharePoint-Komponenten hinzugefügt und mit Branding versehen haben, werden die Änderungen automatisch - wie bei der Aktualisierung einer HTML-Datei - mit der verknüpften Masterseite oder dem Seitenlayout synchronisiert. Die HTML-Codeausschnitte werden automatisch in SharePoint-Komponenten konvertiert.
  
    
    
 Unabhängig davon, ob die HTML-Datei eine Masterseite oder ein Seitenlayout ist, zeigt der Codeausschnittkatalog die benötigten Komponenten an. Falls Sie nicht den benötigten Codeausschnitt entdecken, können Sie immer noch einen HTML-Codeausschnitt des ASP.NET-Markup erstellen und diesem zur HTML-Masterseite bzw. zum Seitenlayout hinzufügen.
  
    
    
Der Entwurfs-Manager generiert HTML-Codeausschnitte, die mit jedem Webentwurfstool verwendet werden können. Er rendert einfach nur HTML- und ignoriert ASP.NET- und SharePoint-Markup. SharePoint rendert nur ASP.NET- und SharePoint-Markup, ignoriert aber HTML.
  
    
    

### Gerätekanäle

Im Entwurfs-Manager erstellen Sie  [Gerätekanäle](sharepoint-2013-design-manager-device-channels.md) und ordnet diese dann mobilen Geräten oder Browsern mithilfe von Teilzeichenfolgen der einzelnen auf dem Gerät eingehenden Zeichenfolge des Benutzer-Agenten zu. Ein Gerät kann zu mehreren Kanälen gehören, und die Kanäle können somit eine Rangordnung haben. Beispiel: Wenn Sie Gerätekanäle für "Smartphones" und "Windows Phone 8" erstellen, können Sie die Kanäle ordnen, so dass die Geräte, mit Windows Phone 8 ausgeführt werden, einen speziell für sie reservierten Kanal bekommen, während andere Smartphones zum "Smartphones"-Kanal zugeordnet werden.
  
    
    
Nachdem Sie die Kanäle festgelegt haben, ordnen Sie dem Kanal eine Masterseite zu. Diese Masterseite verweist auf eine andere CSS-Datei als die Masterseite für den Standardkanal. Alle von Ihnen erstellten Seitenlayouts arbeiten mit alle von Ihnen erstellten Kanälen zusammen. Wenn Sie die Seitenlayoutentwürfe bei den Kanälen unterschiedlich entwerfen möchten, verwenden Sie das Steuerelement **Gerätekanalbereich**.
  
    
    
Veröffentlichungssites in SharePoint 2013 sind für eine mobile Entwicklung optimiert. Sie können mit dem Gerätekanalfeature Kanäle für mindestens ein Gerät definieren, um Ihnen eine Kontrolle darüber zu geben, wie Mobilgerätbenutzer die Benutzerfreundlichkeit Ihrer Website erfahren. Für eine bessere Optik, können Sie den einzelnen Kanälen eine alternative Masterseite zuweisen. Wählen Sie, ob Sie Teile eines Seitenlayouts in einen Kanal mit ein- oder ausschließen möchten, und sehen Sie in der Vorschau, wie der mobile Kanalentwurf während der Entwicklung fortschreitet. Gerätekanäle werden vor dem Hintergrund einer Suchmaschinenoptimierung (SEO) geplant. Passen Sie damit Look and Feel der vorhandenen Seiten an, um mobile Szenarien zu unterstützen.
  
    
    
Sie können Kanäle dafür einsetzen, dass bestimmte Renderings auf bestimmten Geräten erschienen; dies wird Kanäle erzwingen genannt. Dies ist bei mobilen Szenarien nützlich, wenn Sie ein Rendering geplant haben, das für ein bestimmtes mobiles Gerät optimiert ist.
  
    
    

### Steuerelement "Gerätekanalbereich"

"Gerätekanalbereich" ist ein neues Steuerelement, das Sie in das Seitenlayout mit aufnehmen können, um zu steuern, welche Inhalte in welchem Kanal gerendert werden sollen. Der Gerätekanalbereich ist ein Container, der einem oder mehreren Kanälen zugeordnet ist: Wenn mindestens einer dieser Kanäle während des Renderings der Seite aktiv ist, werden alle Inhalte des Gerätekanalbereichs gerendert. Über "Gerätekanalbereich" können Sie festlegen, wann ein bestimmter Inhalt für bestimmte Kanäle mit eingeschlossen werden soll.
  
    
    

### Anzeigevorlagen
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

Sie möchten möglicherweise Format und Darstellung der Suchergebnisse auf Ihrer Website steuern können. Verwenden Sie dazu Anzeigevorlagen, die die verfügbaren Optionen einer Anpassung der Suchergebnisse über die Benutzeroberfläche über die Zuordnung der anzuzeigenden vordefinierten Felder hinaus erweitern.
  
    
    
Es gibt drei Kontexte, wenn Sie Anzeigevorlagen mit Suchergebnissen verwenden möchten: eine Darstellungszuordnung der Gesamtstruktur der Suchergebnisse, eine Darstellung von gruppierten Ergebnissen und eine Darstellung der einzelnen Ergebnisse oder Elemente im Resultset. Diese Darstellungsarten werden "Steuerelementvorlage", "Gruppenvorlage" und "Elementvorlage" genannt.
  
    
    
Weitere Informationen zu Anzeigevorlagen finden Sie unter  [Anzeigevorlagen im SharePoint 2013-Entwurfs-Manager](sharepoint-2013-design-manager-display-templates.md).
  
    
    

### Bildwiedergaben
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

Mit  [Bildwiedergaben](sharepoint-2013-design-manager-image-renditions.md) können Sie hochgeladene Bilder in vordefinierten Größen, Breiten und Beschnitten anzeigen. Sie können mehrere Wiedergaben ein und derselben Quellbilddatei erstellen. Das heißt, Sie können die Anzeigemerkmale einmal festlegen und sie dann auf eine beliebige Anzahl Bilder anwenden. Beispiel: Eine Bildwiedergabe namens **Article_image** zeigt ein Bild in Vollbildgröße in einem Artikel an, während die Wiedergabe namens **Thumbnail_small** eine kleinere Version des Bildes in einem von Ihnen definierten Kontext anzeigt.
  
    
    
Bevor Sie Bildwiedergaben verwenden können, stellen Sie sicher, dass der BLOB-Cache auf dem Server aktiviert ist. Dies erfolgt über in den Internetinformationsdiensten (IIS) mit den Verwaltungstools. Suchen Sie dort nach der **web.config**-Datei, und aktivieren Sie den BLOB-Cache. Aktualisieren Sie die Seite, damit die Bildwiedergaben verfügbar sind. 
  
    
    

## Verwaltete Metadaten und Navigation in SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_MetadataAndNavigation"> </a>

Die in eingeführten Enterprise-Managed-Metadaten-Funktionen (EMM) wurden in SharePoint 2013 für mehr Leistung, leichteren Zugriff über die Benutzeroberfläche und taxonomiegesteuerte Navigation, die so genannte verwaltete Navigation, verbessert und erweitert.
  
    
    

### Verwaltete Navigation

Verwaltete Navigation ist die taxonomiegesteuerte Alternative zur herkömmlichen SharePoint-Navigationsfunktion, der strukturierten Navigation, die auf den SharePoint-Strukturen basiert. Die Funktion der  [verwalteten Navigation](managed-navigation-in-sharepoint-2013.md) ermöglicht Ihnen den Entwurf einer Websitenavigation, die über verwaltete Metadaten gesteuert wird. Verwalte Navigation erstellt SEO-optimierte URLs, die aus der verwalteten Navigationsstruktur abgeleitet werden. Da die verwaltete Navigation taxonomisch gesteuert wird, können Sie diese für den Entwurf der Websitenavigation in wichtigen Geschäftskonzepten verwenden, ohne die Struktur Ihrer Website oder Websitekomponenten ändern zu müssen.
  
    
    

### Inhaltssuche-Webpart
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

Mit dem  [Inhaltssuche-Webpart (CSWP)](content-search-web-part-in-sharepoint-2013.md) können Sie Suchdaten auf Ihren Seiten anzeigen. Der Webpart hat eine ähnliche Funktion wie die des Webparts für Inhaltsabfragen, aber seine Websitedesignziele sind andere. CSWP-Formatvorlagen können leichter angepasst werden als CQWP-Formatvorlagen. CSWP gibt clientseitige Ergebnisse im JSON-Format zurück. Sie können auf dem Server Ergebnisse mithilfe von Anzeigevorlagen anpassen.
  
    
    

### Weitere verwaltete Metadatenverbesserungen für Websites
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

SharePoint 2013 führt mehrere Verbesserungen bei verwalteten Metadaten-Benutzeroberflächen und Funktionen ein. Weitere Informationen finden Sie unter  [Verwaltete Metadaten und Navigation in SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md).
  
    
    

## Veröffentlichung von Inhalten in SharePoint 2013
<a name="SP15_WhatsNewSiteDevelopment_Publishing"> </a>

SharePoint 2013 bietet neue Features für das Veröffentlichen von Inhalten, mit denen Sie Veröffentlichungssites entwerfen können, die wiederum neue, flexiblere und komplexere Topologien und Szenarien unterstützen. 
  
    
    

### Designpakete

Wenn Sie ein erfahrener Webdesigner sind, möchten Sie vielleicht einen Entwurf in Ihrer eigenen Umgebung oder Websitesammlung erstellen und testen, bevor er in anderen Websitesammlungen installiert wird. Sollten Sie die websiteübergreifende Veröffentlichung zum Teilen von Inhalten in allen Websitesammlungen verwenden, können Sie denselben Entwurf als Paket auf jeder Website installieren.
  
    
    
In früheren SharePoint-Versionen mussten Sie, wenn Sie einen Entwurf erneut verwenden wollten, Visual Studio installiert haben, um ein SharePoint-Lösungspaket (.wsp-Datei) zu erstellen. Auf der Zielwebsite mussten Sie dann das Paket in den Lösungskatalog hochladen und dort ausführen. In SharePoint 2013 können Sie jetzt, nachdem Sie den Entwurf Ihrer Website abgeschlossen haben, im Entwurfs-Manager **Paket exportieren** wählen, um eine einzige .wsp-Datei, das so genannte [Designpaket](sharepoint-2013-design-manager-design-packages.md) zu exportieren. Beim Export eines Designpakets erstellt SharePoint 2013 automatisch ein Designpaket des gesamten Inhalts, den Sie im Masterseitenkatalog, in der Formatbibliothek, in der Designgalerie, in der Gerätkanalliste und in den Seiteninhaltstypen hinzugefügt oder geändert haben.
  
    
    

> **HINWEIS**
> Ein Designpaket enthält keine Seiten, Navigationseinstellungen oder den Terminologiespeicher. 
  
    
    

Designpakete überschreiben bei öffentlichen Office 365-Websites keine vorhandenen Dateien Bei der Installation eines Designpakets wird ein neuer Ordner im Masterseitenkatalog, in der Formatbibliothek und in der Designgalerie erstellt, in der die Designelemente isoliert sind. 
  
    
    
Wenn Sie ein Designpaket importieren, überschreiben die Designelemente des Pakets vorhandene Dateien. Die Designelement werden dann auf das aktuelle Design der Website angewendet. Die Standard- und Systemmasterseite der Website, das Design und die alternative CSS-Datei sind alle in den Dateien im Designpaket festgelegt. Ein Entwurf, der in einer Umgebung erstellt wurde, kann mit Designpaketen problemlos auf andere, separate Umgebungen angewendet werden.
  
    
    

### Kataloge

Websiteveröffentlichung in SharePoint 2013 führt Kataloge ein, mit deren Hilfe Sie Listen in Veröffentlichungssites einbinden können. Mit Katalogen können Inhalte in allen Websitesammlungen veröffentlicht werden. Die Funktionen der websiteübergreifenden Veröffentlichung hängen vom jeweiligen Katalog ab. Sie können Kataloge für eine Wiederverwendung von Inhalten auf allen Ihren Websites und grenzüberschreitend auf allen Ihren Intranetwebsites, Internetwebsites und Extranetwebsites verwenden. Kataloge sind bei vordefinierten Suchabfragen in der Suche gekennzeichnet. Sie können Inhalte in Katalogen in allen Websitesammlungen darstellen, wenn Sie dazu den [Inhaltssuche-Webpart (CSWP)](content-search-web-part-in-sharepoint-2013.md) verwenden. Außerdem können Sie benutzerdefinierten Code schreiben, um Kataloge zu befüllen, einen Produktkatalog mit einer Seite verknüpfen und individuelle Seiten mit benutzerdefiniertem Seitenlayout, Webparts und HTML-Inhalten, die ausschließlich im festgelegten Kontext erscheinen, verbessern.
  
    
    

### Clientseitige Steuerelementwiedergabe

Alle neuen Steuerelemente in SharePoint 2013 werden clientseitig wiedergegeben. Als Designer oder Entwickler können Sie steuern, wie Inhalte auf der Seite wiedergegeben werden sollen. Sie können außerdem zahlreiche Designtechniken verwenden, um das gewünschte Erscheinungsbild und Verhalten auf den veröffentlichten Seiten zu erzielen, indem Sie Features wie Inhaltssuche-Webparts und Anzeigevorlagen mit einschließen. Daten werden in einem clientseitigen JSON-Array in die Steuerelemente geschrieben. Inhalte zeigen Sie über JavaScript, CSS und Vorlagen an. 
  
    
    

### Websiteübergreifendes Veröffentlichen

Microsoft SharePoint 2013 führt ein websiteübergreifendes Veröffentlichungsfeature ein, mit dem Sie Inhalte in mehreren Websitesammlungen wiederverwenden können. Es verwendet integrierte Suchfunktionen, um Szenarien und Architekturen veröffentlichen zu können. Zum ersten Mal können Sie jetzt Websites farmübergreifend in SharePoint erstellen. Damit überbrücken Ihre Websites die Kluft zwischen Intranet und Internet. 
  
    
    
Verwenden Sie die Themenseitenfunktion, um die Benutzerfreundlichkeit der Startseite an Inhalte anzupassen, die websiteübergreifend veröffentlich werden. Verwenden Sie auch SEO-freundliche URLs für das Verwalten und eine leichtere Aufrechterhaltung der Websitestruktur in einer breiten Palette an Szenarien, einschließlich komplexer mehrsprachiger Websitetopologien.
  
    
    
Weitere Informationen zum websiteübergreifenden Veröffentlichen finden Sie in  [Szenario: Erstellen von SharePoint-Websites mit websiteübergreifender Veröffentlichung in SharePoint Server 2013](http://technet.microsoft.com/de-de/sharepoint/jj872721). Weitere Informationen zu den Entwicklungsoptionen für eine websiteübergreifende Veröffentlichung finden Sie unter  [Websiteübergreifende Veröffentlichung in SharePoint 2013](cross-site-publishing-in-sharepoint-2013.md).
  
    
    

### SEO-Verbesserungen

Viele Benutzer von Geschäftswebsites werden von großen Suchmaschinen wie Bing und seine Konkurrenten zu Geschäftswebsites im Internet umgeleitet. SharePoint 2013 umfasst Features, wie benutzerfreundliche URLs, Homepageumleitung, XML-Sitemaps, benutzerdefinierte SEO-Eigenschaften, mit denen Sie flexibel Browsertitel, **<Meta>**-Tagbeschreibungen, Schlüsselwörter und leichtverständliche URLs für mehrsprachige Websitevarianten festlegen können.
  
    
    
In Office 365 generiert die Websiteinfrastruktur innerhalb von 24 Stunden nach einer Websiteänderung eine aktualisierte XML-Sitemap. Dank der lokalen Installation können Sie die Aktualität Ihrer Sitemaps anpassen und festlegen, welche Suchmaschinen Microsoft für Sie pingen soll, wenn die Sitemap aktualisiert wird.
  
    
    
Das, was Ihre Freunde auf Facebook mögen, beeinflusst das, was Sie in den von Bing und anderen Suchmaschinen zurückgegebenen Suchergebnissen sehen. Sie können APIs in SharePoint 2013-Programmierungsmodellen verwenden, um eine Suchoptimierung für Ihre Website anzupassen.
  
    
    

### Analyse und Empfehlungen

Sie können nachverfolgen, wie Personen Veröffentlichungswebsites und deren Komponenten unter Zuhilfenahme des SharePoint 2013 Analytics-Features nutzen, das tief in die Suchmaschine integriert ist. Analytics befördert die Empfehlungsmöglichkeiten bei Inhalten und führt Berechnungen als verwaltete Eigenschaften in den Suchindex ein. Die Empfehlungen von Suchanalysen, wie Seitenaufrufe und eindeutige Elemente pro Tag, beeinflussen die Relevanz von Suchergebnissen.
  
    
    
Analytics anonymisiert Daten und macht alle 2 Wochen ein Rollup. Analytics löscht erst alle 2 Wochen, dann nach 3 Jahren jeden Monat, Ereignisse. Lebensdaueransichten bleiben immer erhalten. Der zuletzt angezeigte Inhalt wird zunächst geglättet, bevor Analytics Aggregatdaten in eine Berichtsdatenbank verschiebt. Für den Export von Daten aus der Berichtsdatenbank in Excel, für das Anpassen der Gewichtung von **View**-Ereignissen und für das Erstellen von benutzerdefinierten Ereignissen, einschließlich jener, die von JavaScript bereitgestellt werden, können Sie benutzerdefinierten Code verwenden.
  
    
    

### Varianten und mehrsprachige Websites

Sie können das Variationsfeature in SharePoint 2013 zum Erstellen von mehrsprachigen Websites oder anderen Websites verwenden, in denen Sie die Darstellung des Inhalts variieren möchten. Das Variationsfeature ist auf eine Websitesammlung beschränkt. Sie können zielsprachliche/lokale "Varianten" einer quellsprachlichen/lokalen Website als aktuelle Websites in derselben SharePoint-Websitesammlung erstellen. Varianten unterstützten benutzerfreundliche URLs sowie die Möglichkeit, Inhalte für eine Übersetzung durch Dritte in einem  [XLIFF-Dateiformat](the-xliff-interchange-file-format-in-sharepoint-2013.md) zu ex- und importieren. Sie können Beschriftungen, eine Seite für Übersetzung und Replizierung, eine Reihe von Listenelementen (wie Dokumentbibliotheken) und Navigationssteuerelemente in Ihr Exportpaket mit aufnehmen.
  
    
    

## Zusätzliche Ressourcen
<a name="SP15_WhatsNewSiteDevelopment_AdditionalResources"> </a>


-  [Ausführen grundlegender Vorgänge unter Verwendung von SharePoint 2013-Clientbibliothekscode](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [Ausführen grundlegender Vorgänge unter Verwendung von JavaScript-Bibliothekscode in SharePoint 2013](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
-  [Vorgehenweise: Anpassen der Seitenlayouts für eine katalogbasierte Website in SharePoint 2013](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: ändern die Vorschauseite in SharePoint 2013-Design-Manager](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [Vorgehensweise: Beheben von Fehlern und Warnungen bei der Vorschau einer Seite in SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)
    
  
-  [Übersicht über Designs für SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Verwaltete Metadaten und Navigation in SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md)
    
  
-  [What's new in SharePoint 2013-Suche für Entwickler](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

