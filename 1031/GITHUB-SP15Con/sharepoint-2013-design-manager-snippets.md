---
title: Codeausschnitte des SharePoint 2013-Entwurfs-Managers
ms.prod: SHAREPOINT
ms.assetid: 68caef4c-5941-4a88-b34b-f88122801cef
---


# Codeausschnitte des SharePoint 2013-Entwurfs-Managers
Ein Codeausschnitt ist eine HTML-Darstellung einer SharePoint-Komponente oder eines Steuerelements, wie beispielsweise eine Navigationsleiste oder ein Webpart. Mithilfe des Codeausschnittkatalogs im Entwurfs-Manager können Sie Ihrer HTML-Gestaltungsvorlage oder dem Seitenlayout schnell SharePoint-Funktionen hinzufügen.
## Einführung in Codeausschnitte und den Codeausschnittkatalog
<a name="Introduction"> </a>

Nachdem Sie eine Gestaltungsvorlage konvertiert oder ein Seitenlayout erstellt haben, verfügen Sie über eine HTML-Version der betreffenden Seite. Über den Codeausschnittkatalog können Sie der HTML-Datei, die der Gestaltungsvorlage oder dem Seitenlayout zugeordnet ist, schnell bestimmte SharePoint-Funktionen, wie Such-, Navigations- oder Gerätekanalbereiche hinzufügen. Der Codeausschnittkatalog ist eine Seite im Entwurfs-Manager, auf der Sie folgende Möglichkeiten haben:
  
    
    

- Auswählen einer SharePoint-Komponente aus den im Menüband verfügbaren Komponenten
    
  
- Konfigurieren der Eigenschaften für diese Komponente
    
  
- Anzeigen einer Vorschau im Browser
    
  
- Kopieren des HTML-Codeausschnitts in die Zwischenablage, damit Sie den Codeausschnitt an der gewünschten Stelle in der HTML-Datei einfügen können
    
  
Im Menüband werden verschiedene Optionen des Codeausschnittkatalogs angezeigt, je nachdem, ob Sie eine Gestaltungsvorlage oder ein Seitenlayout bearbeiten. Beispielsweise werden Navigationssteuerelemente nur für Gestaltungsvorlagen angezeigt, und Webpartzonen und Seitenfeld-Steuerelemente werden nur für Seitenlayouts angezeigt. Wenn Sie ein Seitenlayout bearbeiten, richten sich die verfügbaren Seitenfelder zudem nach dem Inhaltstyp des Seitenlayouts, das Sie bearbeiten.
  
    
    
Nachdem Sie einen Codeausschnitt in die HTML-Datei eingefügt haben, erhalten Sie eine Vorschau des im Codeausschnitt angegebenen HTML-Codes zur Entwurfszeit. Sie können auch über die serverseitige Vorschau im Entwurfs-Manager sehen, wie das Steuerelement auf der Livewebsite dargestellt wird. Die Vorschau zur Entwurfszeit enthält möglicherweise statische Beispieldaten, während in der serverseitigen Vorschau ggf. verfügbare Livedaten verwendet werden. Bei einem Navigationssteuerelement, das Navigationslinks aus einem Ausdruckssatz bezieht, werden diese Ausdrücke in der serverseitigen Vorschau dynamisch angezeigt. Die Vorschau zur Entwurfszeit hingegen enthält eine statische Momentaufnahme der Ausdrücke zu dem Zeitpunkt der Erstellung des Codeausschnitts. Livedaten sind in der serverseitigen Vorschau für einige Codeausschnitte, darunter zahlreiche Webparts, nicht verfügbar. In einem solchen Fall erhalten Sie in der serverseitigen Vorschau die Meldung **Vorschau nicht verfügbar**.
  
    
    

> **HINWEIS**
> Ein Codeausschnitt enthält HTML-Code, über den Sie im HTML-Editor eine Vorschau zur Entwurfszeit erhalten. Der HTML-Code in den Kommentaren "Vorschau starten" und "Vorschau beenden" sollte jedoch nicht bearbeitet werden, da er sich nur auf die Vorschau zur Entwurfszeit auswirkt und nicht darauf, wie SharePoint den Codeausschnitt letztlich rendert. Zum Gestalten des Codeausschnitts müssen Sie stattdessen in der Regel die auf den Codeausschnitt angewendeten standardmäßigen SharePoint-Formatvorlagen ermitteln und außer Kraft setzen. 
  
    
    


  
    
    

## Einfügen eines Codeausschnitts aus dem Codeausschnittkatalog
<a name="InsertSnippet"> </a>

Im Codeausschnittkatalog werden verschiedene Optionen angezeigt. Dies richtet sich nach der Datei, die Sie bearbeiten. Beispielsweise sind für verschiedene Seitenlayouts verschiedene Gruppen von Seitenfeldern verfügbar. Um zum Codeausschnittkatalog zu navigieren, müssen Sie daher zunächst eine Gestaltungsvorlage oder ein Seitenlayout auswählen, die bzw. das bearbeitet werden soll.
  
    
    

### So fügen Sie einen Codeausschnitt ein


1. Wechseln Sie zu Ihrer Veröffentlichungswebsite.
    
  
2. Wählen Sie in der rechten oberen Ecke der Seite das Zahnradsymbol für Einstellungen und dann **Entwurfs-Manager** aus.
    
  
3. Wählen Sie im Entwurfs-Manager im linken Navigationsbereich **Gestaltungsvorlagen bearbeiten** oder **Seitenlayouts bearbeiten** aus, je nachdem, welchen Dateityp Sie bearbeiten.
    
  
4. Wählen Sie den Namen der Gestaltungsvorlage oder des Seitenlayouts aus, der bzw. dem Sie Codeausschnitte hinzufügen möchten.
    
  
5. Wählen Sie zum Öffnen des Codeausschnittkatalogs in der serverseitigen Vorschau in der rechten oberen Ecke **Codeausschnitte** aus.
    
  
6. Wählen Sie im Menüband auf der Registerkarte **Entwurf** den Codeausschnitt aus, den Sie der Seite hinzufügen möchten.
    
    Wenn Sie einen Codeausschnitt auswählen, wird der Codeausschnittkatalog aktualisiert. Auf der Seite werden dann eine Vorschau des Codeausschnitts, die für den Codeausschnitt verfügbaren Eigenschaften sowie der HTML-Codeausschnitt, den Sie in die HTML-Gestaltungsvorlage oder das Seitenlayout kopieren können, angezeigt.
    
  
7. Klicken Sie auf der rechten Seite des Codeausschnittkatalogs unter **Infos zu dieser Komponente** auf Abschnittsüberschriften, oder wählen Sie diese aus, um Gruppen von Eigenschaften zu erweitern oder zu reduzieren und anschließend alle gewünschten benutzerdefinierten Eigenschaften zu konfigurieren.
    
    Die Eigenschaften, die für den Hauptzweck des Codeausschnitts am wichtigsten sind, werden im obersten Abschnitt mit der Bezeichnung "Wichtig" angezeigt. Dies sind die wesentlichen Eigenschaften, die Sie verstehen müssen, wenn Sie Codeausschnitte verwenden.
    
    
    
    > **HINWEIS**
      > Wenn das Eigenschaftenraster über eine Kopfzeile verfügt, die mit AjaxDelta endet, sollten Sie diese Eigenschaften ignorieren, da sie für die Steuerelemente im Zusammenhang mit der minimalen Downloadstrategie gelten, die für Gestaltungsvorlagen und Seitenlayouts, die über den Entwurfs-Manager erstellt werden, deaktiviert ist. 
8. Wählen Sie nach dem Konfigurieren von Eigenschaften **Aktualisieren** aus. Dadurch werden sowohl die Vorschau als auch der HTML-Codeausschnitt links auf der Seite aktualisiert, sodass das Markup Ihre benutzerdefinierten Einstellungen widerspiegelt. Sie können jederzeit **Zurücksetzen** auswählen, um alle Eigenschaften auf ihre Standardeinstellungen zurückzusetzen.
    
  
9. Wählen Sie auf der linken Seite des Codeausschnittkatalogs unter **HTML-Code** die Option **In Zwischenablage kopieren** aus.
    
  
10. Öffnen Sie im HTML-Editor das zugeordnete Netzlaufwerk auf dem Computer, und öffnen Sie dann die HTML-Datei für die Gestaltungsvorlage oder das Seitenlayout, der bzw. dem Sie den Codeausschnitt hinzufügen.
    
  
11. Fügen Sie den Codeausschnitt in der HTML-Datei an der Stelle ein, an der das Markup angezeigt werden soll.
    
    Jeder Codeausschnitt enthält HTML-Code, der eine visuelle Vorschau der Komponente und der Beispieldaten zur Verfügung stellt. Diesen HTML-Code sollten Sie für die schreibgeschützte Vorschau innerhalb der Tags **<!--PS>** und **<!--PE>** nicht bearbeiten, da sich dieses Markup nur auf die Vorschau des Codeausschnitts zur Entwurfszeit auswirkt und nicht darauf, wie der Codeausschnitt auf der Livewebsite angezeigt wird.
    
  
12. Um die serverseitige Vorschau des Codeausschnitts anzuzeigen, speichern Sie die HTML-Datei, um die Änderungen mit der zugeordneten Datei ASP.NET zu synchronisieren. Aktualisieren Sie dann die serverseitige Vorschau im Entwurfs-Manager.
    
    Anders als bei der Vorschau zur Entwurfszeit wird das Steuerelement in der serverseitigen Vorschau so angezeigt, wie es von SharePoint gerendert wird.
    
  

## Überblick über das Markup eines HTML-Codeausschnitts
<a name="UnderstandMarkup"> </a>

Ein Codeausschnitt enthält vier Basisabschnitte:
  
    
    

- **Kopfzeile** mit Starttags **<div>** und **<!--CS>** (ausgenommen benutzerdefinierte ASP.NET-Codeausschnitte, die nicht in ein **<div>**-Tag verpackt sind)
    
  
- **SharePoint-Markup**, bei dem Codeausschnitte in **<!--MS>**-Starttags und **<!--ME>**-Endtags eingeschlossen sind
    
  
- **HTML-Vorschau** eingeschlossen in **<!--PS>**-Starttags und **<!--PE>**-Endtags
    
  
- **Fußzeile** mit schließenden **<!--CE>**- und **</div>**-Tags
    
  
Alle Abschnitte eines Codeausschnitts, mit Ausnahme der HTML-Vorschau, sind in HTML-Kommentare eingeschlossen, um Interaktionen mit dem Dokumentobjektmodell (Document Object Model, DOM) und vorhandenen Formatierungen zu vermeiden. Ein Codeausschnitt beginnt mit dem Namen einer Komponente und enthält dann das eigentliche ASP.NET-Markup, eine HTML-Vorschau zum Rendern zur Entwurfszeit sowie die Endtags. Das ASP.NET-Markup ist auskommentiert, doch SharePoint entfernt die Kommentartags und verwendet dieses Markup, wenn die HTML-Datei mit der MASTER-Datei oder der ASPX-Datei synchronisiert wird. Wenn Sie ASP.NET kennen, können Sie dieses Markup im Codeausschnitt anpassen.
  
    
    
Als Beispiel ist nachfolgend das Standardmarkup für einen Bearbeitungsmodusbereich darstellt. Dabei handelt es sich einfach um einen Container, der unter bestimmten Bedingungen andere Inhalte und Steuerelemente anzeigt.
  
    
    

### Kopfzeile


```HTML

<div data-name="EditModePanelShowInEdit">
    <!--CS: Start Edit Mode Panel Snippet-->
```


### SharePoint-Markup


```HTML

<!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### HTML-Vorschau


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
        <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Edit Mode Panel Properties.
    
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
```


### Fußzeile


```HTML

<!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Edit Mode Panel Snippet-->
</div>
```

Nachfolgend finden Sie das Standardmarkup für einen Codeausschnitt für die obere Navigationsleiste. Dies ist komplexer, da dieser Codeausschnitt verschiedene Steuerelemente enthält, von denen einige ineinander geschachtelt sind, einschließlich einer Datenquelle für die Navigationsausdrücke, einem Stellvertretungs-Steuerelement und einem Inhaltsplatzhalter.
  
    
    

> **HINWEIS**
> Einige der Steuerelemente, wie beispielsweise der Inhaltsplatzhalter, enthalten leere Tags für eine HTML-Vorschau, da das Element keine visuelle Darstellung auf der Seite benötigt. 
  
    
    


### Kopfzeile


```HTML

<div data-name="TopNavigationNoFlyoutWithStartNode">
<!--CS: Start Top Navigation Snippet-->    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### SharePoint-Markup


```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<SharePoint:AjaxDelta ID="DeltaTopNavigation" BlockElement="true" CssClass="ms-displayInline ms-core-navigation ms-dialogHidden" runat="server">-->
```


### HTML-Vorschau


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint-Markup


```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
```


### HTML-Vorschau


```HTML
<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<span style="display:none">
<table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow">
<tr><td nowrap="nowrap">
<span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span>
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint-Markup


```HTML

<!--MS:<Template_Controls>-->
<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
```


### SharePoint-Markup


```HTML

<!--ME:</asp:SiteMapDataSource>-->
<!--ME:</Template_Controls>-->
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>
```


### SharePoint-Markup


```HTML

<!--MS:<asp:ContentPlaceHolder ID="PlaceHolderTopNavBar" runat="server">-->
<!--MS:<SharePoint:AspMenu ID="TopNavigationMenu" runat="server" EnableViewState="false" DataSourceID="topSiteMap" AccessKey="&amp;#60;%$Resources:wss,navigation_accesskey%&amp;#62;" UseSimpleRendering="true" UseSeparateCss="false" Orientation="Horizontal" StaticDisplayLevels="2" AdjustForShowStartingNode="false" MaximumDynamicDisplayLevels="0" SkipLinkText="">-->
```


### HTML-Vorschau


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" />
<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
<ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
<li class="static">
<a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1">
<span class="additional-background ms-navedit-flyoutArrow">
<span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div>
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint-Markup


```HTML

<!--ME:</SharePoint:AspMenu>-->
<!--ME:</asp:ContentPlaceHolder>-->
```


### HTML-Vorschau


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint-Markup


```HTML

<!--ME:</SharePoint:AjaxDelta>-->
```


### Fußzeile


```HTML
<!--CE: End Top Navigation Snippet-->
</div>
```


### Arten von Markup

Es folgt eine Übersicht über die Arten von Markup, die in einem Codeausschnitt enthalten sind.
  
    
    
 **Registrierung eines SharePoint-Namespace** SPM ("SharePoint-Markup") gibt eine Zeile zur Registrierung eines SharePoint-Namespace an.
  
    
    



```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
```

 **Kommentare** CS und CE ("Kommentaranfang" und "Kommentarende") dienen zur Analyse der Markupzeilen.
  
    
    



```HTML
<!--CS: Start Top Navigation Snippet-->
…
<!--CE: End Top Navigation Snippet-->

```

 **Codeausschnitte** MS und ME ("Markupanfang" und "Markupende") bestimmen den Anfang und das Ende eines SharePoint-Steuerelements oder -Codeausschnitts. Einige Codeausschnitte, wie das Menüband oder das obige Steuerelement für die obere Navigationsleiste, enthalten verschiedene Steuerelemente, die in einem einzelnen Codeausschnitt geschachtelt sind.
  
    
    



```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
…
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>

<!--MS:<Template_Controls>-->
…
<!--ME:</Template_Controls>-->

<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
…
<!--ME:</asp:SiteMapDataSource>-->

```

 **Vorschaublöcke** PS und PE ("Vorschauanfang" und "Vorschauende") umgeben einen HTML-Codeabschnitt, den Sie nicht bearbeiten sollten. Diese Vorschauabschnitte sind eine Momentaufnahme des SharePoint-Steuerelements, das der Codeausschnitt einfügt. Mithilfe einer Vorschau können Sie in einem HTML-Editor auf Clientseite eine HTML-Datei besser bearbeiten. Doch das Ändern des Inhalts oder der Formatierung innerhalb dieser Vorschau hat keine bleibenden Auswirkungen auf die MASTER-Datei, die SharePoint letztlich nutzt. Zum Formatieren eines Codeausschnitts müssen Sie die SharePoint-Formate bestimmen und mit eigenen benutzerdefinierten CSS überschreiben.
  
    
    



```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><span style="display:none"><table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow"><tr><td nowrap="nowrap"><span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span><!--PE: End of READ-ONLY PREVIEW-->

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" /><div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox"><ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static"><li class="static"><a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1"><span class="additional-background ms-navedit-flyoutArrow"><span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div><!--PE: End of READ-ONLY PREVIEW-->
```


## Weitere Ressourcen
<a name="Resources"> </a>


-  [Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: hinzufügen einen Ausschnitt Bearbeiten Modus Systemsteuerung SharePoint 2013](how-to-add-an-edit-mode-panel-snippet-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Hinzufügen von Ausschnitt glätten Sicherheit in SharePoint 2013](how-to-add-a-security-trim-snippet-in-sharepoint-2013.md)
    
  

