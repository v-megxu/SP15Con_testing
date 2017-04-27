---
title: Vorgehensweise Bewerbung Ausschnitte unter Verwendung von CSS SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: d18d07b6-1a6b-4589-a65c-932b67cef595
---


# Vorgehensweise: Bewerbung Ausschnitte unter Verwendung von CSS SharePoint 2013
Um einen Ausschnitt formatieren, außer Kraft setzen die Standardarten mit benutzerdefinierten CSS. Können CSS-IDs und Elementauswahlen überschreiben alle die Standardarten, die auf Elemente angewendet, oder Sie können einem HTML-Editor oder einem Tool wie die F12-Entwicklertools in Internet Explorer verwenden, zu identifizieren und bestimmte Standardformatvorlagen zu überschreiben.
## Einführung in das Formatieren von Ausschnitten mit CSS
<a name="Introduction"> </a>

Nachdem Sie einer HTML-Gestaltungsvorlage konvertieren oder eine HTML-Seitenlayout erstellen, können Sie die Seite in der Vorschau des Entwurfs-Manager serverseitige Vorschau. Vorschau auf der Seite können Sie navigieren Sie zu Codeausschnittkatalog und klicken Sie dann Kopieren von Ausschnitten in Ihre HTML-Datei. Ein Ausschnitt ist eine HTML-Darstellung eines SharePoint-Steuerelements, wie ein Steuerelement der oberen Navigationsleiste oder das Suchfeld.
  
    
    
Nachdem Sie einen Ausschnitt in der HTML-Datei in Ihrer zugeordnetes Laufwerk kopieren und speichern Sie die Änderungen, können Sie die serverseitige Vorschau der HTML-Datei finden Sie unter Darstellung des Steuerelements aktualisieren. Codeausschnitte enthalten Markup, das eine Vorschau zur Entwurfszeit in Ihre HTML-Editor Wahl bereitstellt, aber dieses Markup sollte nicht bearbeitet werden, da es schreibgeschützt ist und hat keine Auswirkung auf das Rendern des Steuerelements auf dem Server. Im Gegensatz dazu die serverseitige Vorschau Vorschau vollständig übereinstimmende mit Livedaten, sofern verfügbar - beispielsweise ein Navigationssteuerelement aktuellen Navigationsstruktur der Website mit live-Daten aus der Datenquelle, beispielsweise eine SharePoint-Terminologiespeicher für die verwaltete Navigation angezeigt wird.
  
    
    

> **HINWEIS**
> Weitere Informationen zum Zuordnen eines Netzlaufwerks finden Sie unter  [Gewusst wie: Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

Standardmäßig erben Snippets ihre Formatvorlagen aus Stylesheets wie corev15.css SharePoint 2013. Um einen Ausschnitt formatieren möchten, müssen Sie diese Standardformatvorlagen mit Ihrer benutzerdefinierten CSS-außer Kraft setzen. Zu diesem Zweck können Sie folgende Aktionen ausführen:
  
    
    

- Verwenden Sie die CSS-IDs und Elementauswahlen vollständig überschreiben die Standardarten, auf die ausgewählten Elemente angewendet.
    
  
- Verwenden Sie ein browserbasiertes Tool wie die F12-Entwicklertools in Internet Explorer, um den Standardformatvorlagen in der serverseitigen Vorschau im Entwurfs-Manager zu überprüfen, und identifizieren Sie bestimmte Formatvorlagen außer Kraft gesetzt.
    
  
- Verwenden Sie der Features von HTML-Editor, um die Standardarten, in der nur-Lese-Vorschau des einen Ausschnitt zu überprüfen, und identifizieren Sie bestimmte Formatvorlagen außer Kraft gesetzt.
    
  
Um der Standardarten ermitteln Sie mithilfe der Entwicklertools für in Internet Explorer, sollten Sie verwenden die serverseitige Vorschau im Entwurfs-Manager zum Anzeigen Ihrer HTML-Gestaltungsvorlage oder das Seitenlayout, drücken Sie die **F12**, starten Sie die Entwicklertools, wählen Sie im Menü **Suchen**, und wählen Sie dann auf **Select-Element durch Klicken auf**. So können Sie auf Elemente auf der Seite und finden Sie unter genau welche Formatvorlagen zur außer Kraft setzen, indem Sie die benutzerdefinierten Stylesheets, die HTML-Seite oder Seite Layout enthält Links zu master CSS hinzufügen.
  
    
    
Die Standardstylesheets SharePoint 2013 enthalten viele Formatvorlagen, die bestimmte Formatvorlagen identifiziert eine Herausforderung ermöglichen können. Als Alternative zu browserbasierte Tools und je nach Ihrem HTML-Editor können Sie einfacher, Ihre HTML-Datei den Codeausschnitt Codeausschnittkatalog kopiert, und klicken Sie dann den HTML-Editor verwenden, um die Formatvorlagen zu identifizieren. Wenn Sie **Update** auswählen, und Sie dann **in die Zwischenablage kopieren wählen**, enthält der Ausschnitt im Codeausschnittkatalog eine HTML-Vorschau das Snippet. Nachdem Sie den Codeausschnitt in Ihre HTML-Datei kopiert haben, können Sie in der Vorschau schreibgeschützt in den Codeausschnitt verwendeten Formatvorlagen überprüfen. Auf diese Weise werden Sie einen Teil der Standardarten analysieren.
  
    
    
Je nach den Codeausschnitt und den Umfang der einer Anpassung sollten Sie die CSS-IDs und Elementauswahlen verwenden, um vollständig überschreiben alle der Standardarten, anstatt bestimmte Standardformatvorlagen außer Kraft gesetzt. Im folgenden Beispiel wird veranschaulicht, wie diese Methode verwenden, um benutzerdefinierte Formate auf der oberen Navigationsleiste Ausschnitt anwenden.
  
    
    

## Beispiel: Formatieren des oberen Navigationsleiste Ausschnitts
<a name="Example"> </a>

Der oberen Navigationsleiste Ausschnitt ist eine der am häufigsten verwendeten Ausschnitte, daher ist es auch eine der am häufigsten mit Branding Ausschnitte. In einer Website SharePoint 2013 können Sie eine Option, um die verwaltete Navigation verwenden auswählen, sodass ein Terminologiespeicher der Datenquelle für den Ausschnitt der oberen Navigationsleiste wird. Auf diese Weise können Sie das Tool Terminologiespeicherverwaltung in den **Websiteeinstellungen** hinzufügen oder Löschen von Ausdrücken Navigation und die Navigation Taxonomie verwalten, die von der oberen Navigationsleiste Ausschnitt angezeigt wird.
  
    
    
In diesem Beispiel verwendet die Website verwalteten Navigation, damit das Steuerelement der oberen Navigationsleiste der Einträge aus einem Terminologiespeicher abruft. Es ist eine Ebene von Flyouts, die angezeigt werden, wenn Sie über einen Ausdruck Navigation auf oberster Ebene, beispielsweise **Computer** bewegen. In diesem Abschnitt wird gezeigt, wie diese benutzerdefinierte Formate die SharePoint-Standardarten überschreiben.
  
    
    

### Beispiel 1: Navigation < Div > aus der HTML-Datei eines Modells

Bevor Sie beim Entwerfen der HTML-Modell für die Masterseite Entwurfs-Manager verwenden, wahrscheinlich verwenden HTML- und CSS-Sie ein Element der oberen Navigationsleiste funktionale entwerfen. In diesem Beispiel HTML verwendet eine grundlegende Struktur für der oberen Navigationsleiste: ein **<div>** -Element mit einer ID und den Namen, eine Liste für die Einträge der Navigation auf oberster Ebene und eine geschachtelte Liste für jede flyoutmenü Untermenü.
  
    
    

```HTML

<div id="navigation" class="msax-Navigation">
   <ul>
      <li><a href="#">Cameras</a>
         <ul>
            <li><a href="#">Camcorders</a></li>
            <li><a href="#">Digital cameras</a></li>
            <li><a href="#">Disposable cameras</a></li>
            <li><a href="#">Film cameras</a></li>
         </ul>
      </li>
      <li><a href="#">Computers</a>
         <ul>
            <li><a href="#">Desktops</a></li>
            <li><a href="#">Laptops</a></li>
            <li><a href="#">Netbooks</a></li>
            <li><a href="#">Tablets</a></li>
         </ul>
      </li>
      <li><a href="#">Media</a>
         <ul>
            <li><a href="#">Movies</a></li>
            <li><a href="#">Music</a></li>
            <li><a href="#">TV shows </a></li>
            <li><a href="#">Video games </a></li>
         </ul>
      </li>
      <li></li>
   </ul>
</div>

```


### Beispiel 2: Navigation < Div >, mit benutzerdefinierten CSS

Zum Überschreiben SharePoint-Formatvorlagen in der Datei Modell HTML include standard Link zu Ihrer CSS-Datei  `(<link rel="stylesheet" type="text/css" href="URLtoYourCustomCSSFile"/>`) unmittelbar vor dem schließenden-Tag **</head>**.
  
    
    
Beachten Sie in diesen Beispielen HTML- und CSS-Folgendes:
  
    
    

- Navigation Einträge werden normal über das Format  `.msax-Navigation ul li` anstatt direkt auf die Tags **<ul>** oder **<li>** Klassen anwenden.
    
  
- Formatvorlagen verwendet die Syntax  `.msax-Navigation ul li` anstelle von `.msax-Navigation ul>li` , da codeausschnittmarkup dazwischenliegende **<div>** Tags zwischen den ausgewählten Elementen enthalten kann.
    
  
- Die HTML-Modell enthält ein leeres **<li></li>** -Element als der letzte Eintrag, der der obersten Ebene **<ul>**. Dies liegt daran, mit der verwalteten Navigation eingeschaltet, SharePoint hinzugefügt einen Befehl **Links bearbeiten** als letzten Eintrag der Navigation auf oberster Ebene und endgültige Site in der Regel muss nicht auf diese Option angezeigt. Das CSS-Beispiel wird die `.msax-Navigation ul li:last-child` wählen Sie diesen Eintrag, und legen Sie den Display-Wert auf `none`verwendet. Das leere **<li></li>** -Element in der HTML-Datei ist eine temporäre Ersatz für den Standardeintrag **Links bearbeiten**. Achten Sie auf dieses Element endgültigen **<li>**, wenn Ihre Website verwendet die verwaltete Navigation und Ihre CSS eine beliebige `li:last-child` Auswahlen verwendet.
    
  



```HTML

.msax-Navigation {
margin: 10px 0px; top: 0px; position: relative;
z-index:200;
}
.msax-Navigation a {
margin: 0px; padding: 0px; border: 0px currentColor;
}
.msax-Navigation ul {
list-style: none; margin: 0px; padding: 0px; font-size: 16px; z-index:200;
}
.msax-Navigation ul li {
padding: 10px; display: inline-block; position: relative; z-index:200;
}
.msax-Navigation ul li:first-child {
margin: 0px;
}
.msax-Navigation ul li:last-child {
margin: 0px; padding: 0px; display: none;
}
.msax-Navigation ul li a.selected, .msax-Navigation ul li.selected {
background-color: rgb(58,60,62) !important;
color:rgb(255,255,255) !important;
}
.msax-Navigation ul li a {
width: 100%; color: rgb(58,60,62); font-size: 16px;
}
.msax-Navigation ul li:hover {
background-color: rgb(58,60,62);
color:rgb(255,255,255) !important;
}
.msax-Navigation ul li a:hover {
text-decoration: none;
color:rgb(255,255,255) !important;
}
.msax-Navigation li ul {
left: 0px; top: 35px; display: none; position: absolute; min-width: 100px; box-shadow: 5px 5px 10px 0px rgb(0,0,0); background-color: rgb(58,60,62);
}
.msax-Navigation li:hover ul {
display: block; z-index: 150;
}
.msax-Navigation li li {
margin: 0px; padding: 5px 10px 5px 0px; border-top-width: 0px; display: block; min-width: 100px;
}
.msax-Navigation li li:last-child {
margin: 0px; padding: 5px 10px 5px 0px; border-top-width: 0px; display: block; min-width: 100px;
}
.msax-Navigation li li a {
width: 100%; padding-left: 10px; display: block; color:rgb(255,255,255) !important;
}
.msax-Navigation li li:hover {
background-color: rgb(120, 120, 120);
}

```


### Beispiel 3: Read-only Vorschau auf der oberen Navigationsleiste Ausschnitt

Nachdem Ihre benutzerdefinierten Formatvorlagen in Ihre HTML-Modell implementiert werden und Sie ein Element der oberen Navigationsleiste funktionsfähig haben, führen Sie die üblichen Schritte:
  
    
    

1. Zuordnen eines Netzlaufwerks.
    
  
2. Hochladen Sie Design-Dateien.
    
  
3. Konvertieren der HTML-Datei in eine Gestaltungsvorlage
    
  
4. Anzeigen der Vorschau und beheben Sie etwaige Probleme.
    
  
5. Fügen Sie den Codeausschnitt der oberen Navigationsleiste der HTML-Gestaltungsvorlage, mithilfe des Katalogs Ausschnitt.
    
  
Im Codeausschnittkatalog Wenn Sie die Eigenschaften der oberen Navigationsleiste Ausschnitt konfigurieren, beachten Sie Folgendes:
  
    
    

- **Wichtig** Sie im Abschnitt am Anfang stellen Sie alle Änderungen nicht an die **CssClass** -Eigenschaft.
    
  
- Nehmen Sie keine Änderungen an Eigenschaften unter der Überschrift **AjaxDelta**, da diese Eigenschaften auf die MDS-Eigenschaften, die von SharePoint verwendet beziehen, um den HTML-Codeausschnitt in den entsprechenden ASP.NET Ausschnitt zu konvertieren. Dies gilt für alle Codeausschnitt, nicht nur auf der oberen Navigationsleiste Ausschnitt.
    
  
- Wenn Sie beabsichtigen, außer Kraft setzen die SharePoint-Standardarten, im Codeausschnittkatalog im Abschnitt **Behavior** unter **AspMenu** (möglicherweise gibt es mehrere **Behavior** Abschnitt der Codeausschnitt enthält mehr als ein Steuerelement, beispielsweise ein stellvertretungs-Steuerelement), legen Sie **ClientIDMode** auf **Static**. Wenn Sie **ClientIDMode** auf den Standardwert festgelegt lassen verändert festlegen, **Inherit**, den Codeausschnitt angewendete CSS Klassen basierend auf die Sortierung von Ausschnitten auf der Seite. Weitere Informationen zu **ClientIDMode**finden Sie unter  [Control.ClientIDMode-Eigenschaft](http://msdn.microsoft.com/en-us/library/system.web.ui.control.clientidmode.aspx).
    
    Standardmäßig verwendet das Steuerelement der oberen Navigationsleiste beispielsweise Standardattribute für SharePoint-ID wie **zz5_TopNavigationMenu** und **zz6_RootAspMenu**. **ClientIDMode** **Static**ändern, stellen Sie es möglich, diese Standard-IDs als Auswahlen in eigene CSS verwenden, um die standardmäßige SharePoint-Formatvorlagen außer Kraft setzen.
    
  
- Einige Eigenschaften sind bereits so konfiguriert, dass den oberen Navigationsleiste Ausschnitt einfacher aufgrund der Eliminierung der dynamischen CSS- und JavaScript Standardverhalten branding stellen - beispielsweise standardmäßig **UseSimpleRendering** **True** festgelegt ist und **MaximumDynamicDisplayLevels** auf **0**festgelegt ist. Weitere Informationen zu bestimmten Eigenschaften von der oberen Navigationsleiste Ausschnitt finden Sie unter  [Eigenschaften AspMenu](http://msdn.microsoft.com/en-us/library/ms412476.aspx) und [Eigenschaften im Menü](http://msdn.microsoft.com/en-us/library/282668a1.aspx).
    
  
Nach der Konfiguration des oberen Navigationsleiste Ausschnitts im Codeausschnittkatalog wählen Sie **Update**, und wählen Sie dann **in die Zwischenablage kopieren**. Klicken Sie in der HTML-Gestaltungsvorlage löschen Sie den Inhalt der Navigation-  `<div id="navigation" class="msax-Navigation">` , die das Modell-Steuerelement (Löschen nur der Inhalt des **<div>** -Tags nicht die **<div>** selbst markieren) enthält, und kopieren Sie den Codeausschnitt in der Navigation **<div>**. Bei Bedarf neu zu positionieren Navigation, **<div>**, in der Regel nur nach dem Beginn des Tags  `<div id="s4-bodyContainer">` jedoch vor der **<div>**, `PlaceHolderMain`enthält.
  
    
    
Einfache Vergleich mit den HTML-Code der Navigation **<div>** oben enthält im folgende Beispiel den Navigationsbereich **<div>** Teil der oberen Navigationsleiste Ausschnitt. Beachten Sie, dass dies nicht der gesamte Ausschnitt ist.
  
    
    



```HTML

<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
     <ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
          <li class="static">
          <a accesskey="1" class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Cameras</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/camcorders" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Camcorders</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/digital-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Digital cameras</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/disposable-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Disposable cameras</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/film-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Film cameras</span></span></a></li>
          </ul>
          </li>
          <li class="static">
          <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Computers</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/desktops" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Desktops</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/laptops" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Laptops</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/netbooks" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Netbooks</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/tablets" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Tablets</span></span></a></li>
          </ul>
          </li>
          <li class="static">
          <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Media</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/movies" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Movies</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/music" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Music</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/tv-shows" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">TV shows</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/video-games" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Video games</span></span></a></li>
          </ul>
          </li>
          <li class="static ms-verticalAlignTop ms-listMenu-editLink ms-navedit-editArea">
          <span id="zz7_TopNavigationMenu_NavMenu_Edit" class="ms-navedit-editSpan">
          <a id="zz7_TopNavigationMenu_NavMenu_EditLinks" class="ms-navedit-editLinksText" href="#" onclick="g_QuickLaunchMenu = null; EnsureScriptParams('quicklaunch.js', 'QuickLaunchInitEditMode', 'zz7_TopNavigationMenu', 2, 0, 0, ''); cancelDefault(event); return false;">
          <span class="ms-displayInlineBlock">
          <span class="ms-navedit-editLinksIconWrapper ms-verticalAlignMiddle">
          <img class="ms-navedit-editLinksIcon" src="/_layouts/15/images/spcommon.png?rev=23" /></span><span class="ms-metadata ms-verticalAlignMiddle">Edit Links</span></span></a><span id="zz7_TopNavigationMenu_NavMenu_Loading" class="ms-navedit-menuLoading ms-hide"><a id="zz7_TopNavigationMenu_NavMenu_GearsLink" href="#" onclick="HideGears(); return false;" title="This animation indicates the operation is in progress. Click to remove this animated image."><img id="zz7_TopNavigationMenu_NavMenu_GearsImage" src="/_layouts/15/images/loadingcirclests16.gif?rev=23" /></a></span><div id="zz7_TopNavigationMenu_NavMenu_ErrorMsg" class="ms-navedit-errorMsg">
          </div>
          </span></li>
     </ul>
</div>

```

Anstatt nur benutzerdefinierte Formate verwenden, können Sie ein Szenario haben, wo Sie gerade eine bestimmte Formatvorlage außer Kraft setzen möchten. Um den Knoten **Bearbeiten Links** ausblenden möchten, können Sie beispielsweise eine benutzerdefinierte Formatvorlage erstellen, die die Standard-Id **zz7_TopNavigationMenu_NavMenu_Edit** wird verwendet, um die Anzeige auf `none`eingestellt.
  
    
    

## Zusätzliche Ressourcen
<a name="Additional"> </a>


-  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md)
    
  
-  [Übersicht über den Entwurfs-Manager in SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Entwickeln des Website-Designs in SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  

