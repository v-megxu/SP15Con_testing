---
title: Vorgehensweise Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: a76ab289-3256-45de-ac63-d5112a74e3c7
---


# Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013
Mithilfe des Entwurfs-Managers können Sie eine HTML-Datei in eine SharePoint 2013-Gestaltungsvorlage mit der Erweiterung ".master" konvertieren. Nach der Konvertierung werden die HTML-Datei und Gestaltungsvorlage miteinander verknüpft, sodass nach Bearbeiten und Speichern der HTML-Datei die Änderungen mit der zugeordneten Gestaltungsvorlage synchronisiert werden.
## Einführung in das Konvertieren in eine Gestaltungsvorlage
<a name="Introduction"> </a>

Mit dem Entwurfs-Manager können Sie eine HTML-Datei in eine SharePoint 2013-Gestaltungsvorlage mit der Erweiterung ".master" konvertieren. Nach der Konvertierung werden die HTML-Datei und Gestaltungsvorlage miteinander verknüpft, sodass nach Bearbeiten und Speichern der HTML-Datei die Änderungen mit der zugeordneten Gestaltungsvorlage synchronisiert werden.
  
    
    
Warum sollen Sie eine HTML-Datei konvertieren, anstatt eine Gestaltungsvorlage von Grund auf neu zu erstellen? In SharePoint 2013 funktionieren Gestaltungsvorlagen exakt wie in ASP.NET. Doch SharePoint verlangt außerdem, dass bestimmte für SharePoint spezifische Elemente wie Steuerelemente und Inhaltsplatzhalter auf der Seite vorhanden sein müssen, damit SharePoint die jeweilige Gestaltungsvorlage ordnungsgemäß rendern kann. Durch das Konvertieren einer HTML-Datei in eine voll funktionsfähige SharePoint-Gestaltungsvorlage mit dem Entwurfs-Manager müssen Sie nicht mit ASP.NET- oder SharePoint-spezifischem Markup vertraut sein. Stattdessen können Sie sich auf das Entwerfen Ihrer Website in HTML, CSS und JavaScript konzentrieren.
  
    
    
Beim Konvertieren einer HTML-Datei in eine Gestaltungsvorlage passiert Folgendes:
  
    
    

- Eine MASTER-Datei, die denselben Namen wie Ihre HTML-Datei hat, wird im Gestaltungsvorlagenkatalog erstellt.
    
  
- Das gesamte von SharePoint 2013 verlangte Markup wird der MASTER-Datei hinzugefügt, damit die Gestaltungsvorlage ordnungsgemäß gerendert wird.
    
  
- Markup wie Kommentare, **<div>**-Tags, Codeausschnitte und Inhaltsplatzhalter werden Ihrer ursprünglichen HTML-Datei hinzugefügt.
    
  
- Die HTML-Datei und Gestaltungsvorlage werden miteinander verknüpft, damit spätere Änderungen an der HTML-Datei mit der MASTER-Datei synchronisiert werden, sobald die HTML-Datei gespeichert wird.
    
  

> **HINWEIS**
> Die Synchronisierung erfolgt nur in eine Richtung. Änderungen an der HTML-Gestaltungsvorlage werden mit der zugeordneten MASTER-Datei synchronisiert. Doch wenn Sie die MASTER-Datei direkt bearbeiten, werden die Änderungen nicht mit der HTML-Datei synchronisiert. Jede HTML-Gestaltungsvorlage (und jedes HTML-Seitenlayout) hat die Eigenschaft **Zugeordnete Datei**, die standardmäßig auf **True** festgelegt ist und mit deren Hilfe die Verknüpfung und Synchronisierung zwischen Dateien eingerichtet wird.
  
    
    

Wenn Sie über ein Paar miteinander verknüpfter Dateien (HTML und MASTER) verfügen und Sie die MASTER-Datei bearbeiten, ohne die Verknüpfung zu unterbrechen, werden die Änderungen an der MASTER-Datei gespeichert. Doch Sie können die MASTER-Datei weder einchecken noch veröffentlichen, weshalb die Änderungen nicht auf sinnvolle Weise gespeichert werden. Bei Änderungen an der HTML-Datei wird die MASTER-Datei überschrieben. Wenn Sie die HTML-Datei einchecken oder veröffentlichen, überschreiben die Änderungen an der HTML-Datei alle Änderungen, die an der MASTER-Datei erfolgt sind. Die Änderungen an der MASTER-Datei gehen daraufhin verloren.
  
    
    
Als Entwickler, der mit ASP.NET vertraut ist, können Sie nach Wunsch nur mit der MASTER-Datei arbeiten und die Verknüpfung zwischen den Dateien aufheben. Dazu wählen Sie im Entwurfs-Manager den Befehl **Eigenschaften bearbeiten** für die HTML-Datei aus und deaktivieren das Kontrollkästchen **Zugeordnete Datei**. Sie können später die Verknüpfung zwischen den Datei wieder aktivieren, indem Sie die Eigenschaften bearbeiten und dieses Kontrollkästchen aktivieren. In diesem Fall wird die MASTER-Datei erneut von der HTML-Datei überschrieben, und an der MASTER-Datei erfolgte Änderungen gehen verloren.
  
    
    

## Vorbereiten der HTML-Datei auf die Konvertierung
<a name="Prepare"> </a>

Vor der Konvertierung Ihrer HTML-Datei sollten Sie einige bewährte Methoden und Tipps befolgen:
  
    
    

- Berücksichtigen Sie das SharePoint-Seitenmodell. Weitere Informationen finden Sie unter  [Übersicht über das SharePoint 2013-Seitenmodell](overview-of-the-sharepoint-2013-page-model.md). Wenn Sie die HTML-Modelle Ihrer Website entwerfen, verfügen Sie wahrscheinlich über mehrere HTML-Dateien für verschiedene Seitentypen, so z. B. über eine Artikel- oder Kategorieseite, die Webparts enthält, mit denen eine Kategorie von Elementen in einem Katalog angezeigt wird. Doch nur eine HTML-Datei wird in eine Gestaltungsvorlage konvertiert. Eine HTML-Datei kann in eine Gestaltungsvorlage konvertiert werden, doch eine HTML-Datei kann nicht direkt in ein Seitenlayout umgewandelt werden, da für ein Seitenlayout Seitenfelder erforderlich sind.
    
  
- Vergewissern Sie sich, dass Ihre HTML-Datei XML-konform ist, da dies für eine ordnungsgemäße Konvertierung erforderlich ist. Leider setzt diese Anforderung einige HTML 5-Standards außer Kraft. Beispielsweise können Sie in HTML 5 **doctype** in Kleinschreibung angeben, doch in XML verlangt **doctype** Großschreibung. Außerdem müssen Sie **<form>**-Tags aus Ihrer HTML-Datei entfernen. Lassen Sie Ihre HTML-Datei am besten ein externes XML-Prüfprogramm durchlaufen, um XML-Fehler vor der Konvertierung auszumachen.
    
  
- Berücksichtigen Sie diese wichtigen Leitlinien für Ihre CSS-Verweise:
    
  - Fügen Sie dem **<head>**-Tag keine **<style>**-Blöcke hinzu, da diese Formate während der Konvertierung entfernt werden. Richten Sie stattdessen Verknüpfungen Ihrer HTML-Datei mit einer externen CSS-Datei ein.
    
  
  - Fügen Sie  `ms-design-css-conversion="no"` dem **<CSS link>**-Tag hinzu, wenn Sie eine Webschriftart verwenden.
    
  
  - Gehen Sie beim Anwenden von Formaten auf HTML-Tags wie **<body>**, **<div>** und **< img>** überlegt vor. Alles in Ihrem SharePoint-Entwurf einschließlich Menüband ist im **<body>**-Tag enthalten. Erwägen Sie bei Formaten, die Sie üblicherweise auf das **<body>**-Tag anwenden würden, diese stattdessen auf das **<div id="s4-bodyContainer">**-Tag anzuwenden. Dies ist ein Tag, das SharePoint 2013 für den Haupttextkörper der Seite verwendet. Außerdem verwendet SharePoint 2013 zahlreiche Bilder, der von den Formaten betroffen sind, die Sie auf das **<img>**-Tag anwenden.
    
  
  - Viele Designer gestalten die Navigation, indem Klassen auf die Elemente **<ul>** und **<li>** angewendet werden. Doch SharePoint 2013 verwendet ein dynamisches Navigationssteuerelement, das Sie Ihrer Gestaltungsvorlage über den Gestaltungsvorlagenkatalog hinzufügen können. SharePoint 2013-Navigationssteuerelemente verfügen über standardmäßig angewendete Formate, die Sie überschreiben müssen.
    
  
- Berücksichtigen Sie diese potenziellen Probleme beim Benennen von Dateien:
    
  - Wenn Sie über **Index.html** und **Index.htm** verfügen, haben diese Dateien dieselbe MASTER-Datei.
    
  
  - Wenn Sie über **Design/Index.html** und **Design/SubDesign/Index.html** verfügen, können diese Dateien in eigene, getrennte MASTER-Dateien konvertiert werden. Sie werden jedoch im Entwurfs-Manager in der Gestaltungsvorlagenliste als **Index.html** angezeigt. Um sie eindeutig zu machen, klicken Sie für jede Datei auf die Schaltfläche mit den Auslassungszeichen, um den vollständigen Pfad anzuzeigen.
    
  
- Wenn Sie ein JavaScript-Widget hinzufügen, vergewissern Sie sich, dass sich das Starttag **<script>** in einer eigenen Zeile befindet.
    
  ```
  
<script>
(function( …

  ```


    Geben Sie die Tags nicht in der gleichen Zeile ein (siehe unten).
    


  ```
  
<Script> (function( …
  ```

- Ein Verweis auf die JQuery-Bibliothek (ein externer Verweis) muss sich vor dem **</head>**-Tag befinden.
    
  

## Konvertieren der HTML-Datei in eine Gestaltungsvorlage
<a name="Convert"> </a>

Bevor Sie eine HTML-Datei konvertieren, müssen Sie zunächst alle Ihre Entwurfsdateien samt Ihrer HTML-Datei hochladen. Weitere Informationen finden Sie unter  [Gewusst wie: Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

### So konvertieren Sie die HTML-Datei in eine Gestaltungsvorlage


1. Wechseln Sie zu Ihrer Veröffentlichungswebsite.
    
  
2. Wählen Sie in der rechten oberen Ecke der Seite **Einstellungen** und dann **Entwurfs-Manager**.
    
  
3. Wählen Sie im Entwurfs-Manager im linken Navigationsbereich **Gestaltungsvorlagen bearbeiten**.
    
  
4. Wählen Sie **Konvertieren einer HTML-Datei in eine SharePoint-Gestaltungsvorlage**.
    
  
5. Wählen Sie im Dialogfeld **Ein Objekt auswählen** die HTML-Datei aus, die Sie konvertieren möchten.
    
    > **HINWEIS**
      > Wenn Sie Ihre Entwurfsdateien hochladen, sollten Sie alle Dateien im Zusammenhang mit einem einzelnen Entwurf in einem eigenen Ordner im Gestaltungsvorlagenkatalog ablegen. Wenn Sie Ihren Entwurfsordner auf das zugeordnete Netzwerklaufwerk kopieren, behält der Gestaltungsvorlagenkatalog Ihre angelegte Ordnerstruktur bei. 
6. Wählen Sie **Einfügen**.
    
    An dieser Stelle konvertiert SharePoint 2013 Ihre HTML-Datei in eine MASTER-Datei mit demselben Namen.
    
    Im Entwurfs-Manager wird Ihre HTML-Datei nun mit der Spalte **Status** mit einem von zwei möglichen Status angezeigt:
    
  - Fehler
    
  
  - **Konvertierung erfolgreich**
    
  
7. Öffnen Sie den Link in der Spalte **Status**, um eine Vorschau der Datei und etwaige Fehler oder Warnungen zur Gestaltungsvorlage anzuzeigen.
    
    Fehler
    
    Weitere Informationen zum Beheben von Fehlern und Warnungen finden Sie unter  [Vorgehensweise: Beheben von Fehlern und Warnungen bei der Vorschau einer Seite in SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md).
    
    Weitere Informationen zur Vorschau der Gestaltungsvorlage mit unterschiedlichen Seiten finden Sie unter  [Vorgehensweise: ändern die Vorschauseite in SharePoint 2013-Design-Manager](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md).
    
    Auf der Vorschauseite befindet sich rechts oben auch der Link **Codeausschnitt**, über den der Codeausschnittkatalog geöffnet wird, in dem Sie beginnen können, statische oder Modellsteuerelemente in Ihrem Entwurf durch dynamische SharePoint-Steuerelemente zu ersetzen. Weitere Informationen finden Sie unter  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md).
    
  
8. Bearbeiten zum Korrigieren von Fehlern die HTML-Datei, die sich direkt auf dem Server befindet, mithilfe eines HTML-Editors, mit dem Sie die HTML-Datei auf dem zugeordneten Laufwerk öffnen und bearbeiten können. Bei jeder Speicherung der HTML-Datei werden Änderungen mit der zugeordneten MASTER-Datei synchronisiert.
    
  
9. Nach erfolgreicher Vorschau Ihrer Gestaltungsvorlage sehen Sie das **<div>**-Tag, das Ihrer HTML-Datei hinzugefügt wird. Sie müssen ggf. einen Bildlauf nach unten auf der Seite durchführen, um das **<div>**-Tag zu sehen.
    
    Dieses **<div>**-Tag ist der Hauptinhaltsblock. Es befindet sich im Inhaltsplatzhalter **ContentPlaceHolderMain**. Wenn ein Benutzer zur Laufzeit Ihre Website durchstöbert und eine Seite anfordert, wird dieser Inhaltsplatzhalter mit Inhalten aus einem Seitenlayout gefüllt, das Inhalte in einem übereinstimmenden Inhaltsbereich enthält. Sie müssen dieses **<div>**-Tag an der Stelle positionieren, an der Ihre Seitenlayouts in der Gestaltungsvorlage angezeigt werden sollen.
    
    Wenn Ihre HTML-Datei statische oder Modellinhalte im Textkörper der Seite enthält, leiten Sie nun das Entfernen dieser statischen Inhalte aus der HTML-Gestaltungsvorlage ein, und Sie wenden diese Formate auf andere Elemente des SharePoint-Seitenmodells an, z. B. Seitenlayouts, Seitenfeld-Steuerelemente, Codeausschnitte und Anzeigevorlagen. Ein Beispiel finden Sie unter  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  

## Grundlegendes zur HTML-Datei nach der Konvertierung
<a name="Understand"> </a>

Wenn Sie eine HTML-Datei in eine Gestaltungsvorlage konvertieren, werden der HTML-Datei viele Markupzeilen hinzugefügt. Sie können einen Großteil dieses Markups getrost ignorieren, denn das meiste davon wird nicht im endgültigen Markup Ihrer Website enthalten sein, wenn Sie den Quellcode im Browser anzeigen. Doch dieses Markup ist wichtig für das Konvertieren Ihrer HTML-Datei in die MASTER-Datei, die SharePoint tatsächlich verwendet. Jedes Mal, wenn sie eine Änderung an Ihrer HTML-Datei speichern, ermöglicht dieses SharePoint-Markup, dass dieselbe Änderung im Hintergrund an der zugeordneten MASTER-Datei erfolgt.
  
    
    
Das hinzugefügte Markup enthält Tags vor und im **<head>**-Tag, Codeausschnitte und Inhaltsplatzhalter. Das meiste Markup befindet sich innerhalb von Kommentartags. Immer wenn Sie eine Änderung an der HTML-Datei speichern, entfernt der Konvertierungsprozess die Kommentare, um das enthaltene ASP.NET-Markup zu verwenden.
  
    
    

### Arten von Markup

Es folgt eine Übersicht der Arten von Markup, die der HTML-Datei hinzugefügt werden:
  
    
    

- **Dokumenteigenschaften** Das **<mso>**-Tag enthält SharePoint-Metadaten, einschließlich Informationen zur Datei selbst und einiger Eigenschaften, die für die erfolgreiche Konvertierung in die MASTER-Datei benötigt werden.
    
  ```HTML
  
<mso:CustomDocumentProperties>
<mso:HtmlDesignFromMaster msdt:dt="string"></mso:HtmlDesignFromMaster>
<mso:HtmlDesignStatusAndPreview msdt:dt="string">http://[server_name]/sites/PubSite/_catalogs/masterpage/[site_name]/index.html, Conversion successful.</mso:HtmlDesignStatusAndPreview>
<mso:ContentTypeId msdt:dt="string">0x0101000F1C8B9E0EB4BE489F09807B2C53288F0054AD6EF48B9F7B45A142F8173F171BD10003D357F861E29844953D5CAA1D4D8A3A0084F0F9C7FCB65541A59990D173DA60FA</mso:ContentTypeId>
<mso:HtmlDesignAssociated msdt:dt="string">1</mso:HtmlDesignAssociated>
<mso:HtmlDesignConversionSucceeded msdt:dt="string">True</mso:HtmlDesignConversionSucceeded>
</mso:CustomDocumentProperties>
  ```

- **Registrierung eines SharePoint-Namespace** Das **<SPM>**-Tag ("SharePoint-Markup") bietet eine Zeile zur Registrierung eines SharePoint-Namespace.
    
  ```HTML
  
<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
  ```

- **Kommentare** Die Tags **<CS>** und **<CE>** ("Kommentaranfang" und "Kommentarende") werden während des Konvertierungsprozesses ignoriert. Diese Tags dienen zur Analyse der Markupzeilen.
    
  ```HTML
  
<!--CS: Start Page Head Contents Snippet-->
…
<!--CE: End Page Head Contents Snippet-->

  <!--CS: Start Ribbon Snippet-->
…
<!--CE: End Ribbon Snippet-->

<!--CS: Start PlaceHolderMain Snippet-->
…
<!--CE: End PlaceHolderMain Snippet-->
  ```

- **Codeausschnitte** Die Tags **<MS>** und **<ME>** ("Markupanfang" und "Markupende") bestimmen den Anfang und das Ende eines SharePoint-Steuerelements oder -Codeausschnitts. Ein Codeausschnitt ist ein SharePoint-Steuerelement, das Ihrer Seite SharePoint-Funktionalität hinzufügt. Über den Codeausschnittkatalog können Sie selbst Codeausschnitte hinzufügen. Weitere Informationen finden Sie unter [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md).
    
  ```HTML
  
<!--MS:<SharePoint:RobotsMetaTag runat="server">-->
        <!--ME:</SharePoint:RobotsMetaTag>-->
        <!--MS:<SharePoint:PageTitle runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
                <!--MS:<SharePoint:ProjectProperty Property="Title" runat="server">-->
                <!--ME:</SharePoint:ProjectProperty>-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:PageTitle>-->
        <!--MS:<SharePoint:StartScript runat="server">-->
        <!--ME:</SharePoint:StartScript>-->
        <!--MS:<SharePoint:CssLink runat="server" Version="15">-->
        <!--ME:</SharePoint:CssLink>-->
        <!--MS:<SharePoint:CacheManifestLink runat="server">-->
        <!--ME:</SharePoint:CacheManifestLink>-->
        <!--MS:<SharePoint:PageRenderMode runat="server" RenderModeType="Standard">-->
        <!--ME:</SharePoint:PageRenderMode>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="core.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="menu.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="callout.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="sharing.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="suitelinks.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:CustomJSUrl runat="server">-->
        <!--ME:</SharePoint:CustomJSUrl>-->
        <!--MS:<SharePoint:SoapDiscoveryLink runat="server">-->
        <!--ME:</SharePoint:SoapDiscoveryLink>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaPlaceHolderAdditionalPageHead" Container="false" runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
            <!--MS:<SharePoint:DelegateControl runat="server" ControlId="AdditionalPageHead" AllowMultipleControls="true">-->
            <!--ME:</SharePoint:DelegateControl>-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderBodyAreaClass" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--MS:<SharePoint:CssRegistration Name="Themable/corev15.css" runat="server">-->
        <!--ME:</SharePoint:CssRegistration>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaSPWebPartManager" runat="server">-->
            <!--MS:<WebPartPages:SPWebPartManager runat="server">-->
            <!--ME:</WebPartPages:SPWebPartManager>-->
        <!--ME:</SharePoint:AjaxDelta>-->
  ```

- **Vorschaublöcke** Die Tags **<PS>** und **<PE>** ("Vorschauanfang" und "Vorschauende") umgeben einen HTML-Codeabschnitt, den Sie nicht ändern sollten, da er sich nur auf die Vorschau zur Entwurfszeit auswirkt. Diese Vorschauabschnitte sind eine Momentaufnahme des SharePoint-Steuerelements, das der Codeausschnitt einfügt. Mithilfe einer Vorschau können Sie in einem HTML-Editor auf Clientseite eine HTML-Datei besser bearbeiten. Doch das Ändern des Inhalts oder der Formatierung innerhalb dieser Vorschau hat keine bleibenden Auswirkungen auf die MASTER-Datei, die SharePoint letztlich nutzt. Zum Formatieren eines Codeausschnitts müssen Sie die SharePoint-Formate bestimmen und mit eigenen benutzerdefinierten CSS überschreiben.
    
  ```HTML
  
<!--PS: Start of READ-ONLY PREVIEW (do not modify) -->
<div class="DefaultContentBlock" style="background:rgb(0, 114, 198); color:white; width:100%; padding:8px; height:64px; overflow:hidden;">The SharePoint ribbon will be here when your file is either previewed on or applied to your site.</div>
<!--PE: End of READ-ONLY PREVIEW -->
  ```

- **SharePoint-IDs** Zwei der Codeausschnitte, die Ihrer HTML-Datei während der Konvertierung hinzugefügt werden (der Codeausschnitt "Seitenkopfinhalte" und das SharePoint-Menüband), haben eine zugeordnete SharePoint-ID bzw. SID (00 bzw. 02). Diese IDs ermöglichen das Kürzen der Codeausschnitte und vereinfachen das Lesen des HTML-Codes auf der Seite.
    
  ```HTML
  
<!--SID:00 -->

<!--SID:02 {Ribbon}-->
  ```


### Hinzugefügte Codeausschnitte

Wichtig ist es, die beiden Codeausschnitte zu kennen, die Ihrer HTML-Datei hinzugefügt werden. Diese Codeausschnitte werden während der Konvertierung automatisch hinzugefügt. Sie stehen jedoch nicht zum Hinzufügen über den Codeausschnittkatalog zur Verfügung.
  
    
    

- **Das Menüband** Damit Inhaltsautoren Seiten und Inhalte auf Ihrer SharePoint-Website erstellen können, benötigt Ihre Gestaltungsvorlage das Menüband und die in SharePoint 2013 neue "Suitenavigation". Das Menüband ist in einem Codeausschnitt mit Einschränkung aus Sicherheitsgründen enthalten, sodass, wenn ein Benutzer Ihre Website durchstöbert, das Menüband nur authentifizierten Benutzern und anonymen Benutzern nicht angezeigt wird. Sie können das Menüband an eine andere Position auf der Seite verschieben oder es durch Überschreiben der CSS-Standardklassen formatieren. Jedoch wird das Verschieben oder Neuanordnen der Komponenten (z. B. des Menüs **Websiteaktionen**), die sich auf dem Menüband befinden, nicht empfohlen.
    
  ```HTML
  
<!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AnonymousUsersOnly">-->
<!--MS:<wssucw:Welcome runat="server" EnableViewState="false">-->
<!--ME:</wssucw:Welcome>-->
<!--ME:</SharePoint:SPSecurityTrimmedControl>-->
  ```

- **ContentPlaceHolderMain** Beim Konvertierungsprozess wird unten im **<div id="s4-bodyContainer">**-Tag vor dem schließenden **</body>**-Tag der Inhaltsplatzhalter **PlaceHolderMain** eingefügt. Innerhalb dieses Codeausschnitts befindet sich ein gelbes **<div>**-Tag mit schwarzem Rand, das in der Entwurfsansicht Ihres HTML-Editors oder in der serverseitigen Vorschau im Entwurfs-Manager angezeigt wird.
    
    Dieses **<div>**-Tag stellt den Bereich dar, in den der von Ihren Seitenlayouts und Seiten angegebene Inhalt eingefügt wird. Sie müssen den Codeausschnitt **PlaceHolderMain** an die Stellen in Ihrer Gestaltungsvorlage verschieben, die durch Ihre Seitenlayouts gefüllt werden, d. h. in den Bereich Ihres Websiteentwurfs, der auf allen Seiten Ihrer Website nicht identisch ist.
    


  ```HTML
  
<!--CS: Start PlaceHolderMain Snippet-->
                    <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                    <!--MS:<SharePoint:AjaxDelta ID="DeltaPlaceHolderMain" IsMainContent="true" runat="server">-->
                        <!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
                            <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
            This div, which you should delete, represents the content area that your Page Layouts and pages will fill. Design your Master Page around this content placeholder.
        
                            </div>
                        <!--ME:</asp:ContentPlaceHolder>-->
                    <!--ME:</SharePoint:AjaxDelta>-->
                    <!--CE: End PlaceHolderMain Snippet-->
  ```


## Beispiele
<a name="Reference"> </a>

Es folgt ein Beispiel des Markups, das einer HTML-Datei hinzugefügt wird, nachdem sie in eine Gestaltungsvorlage konvertiert wurde.
  
    
    

### Dem <head>-Tag hinzugefügtes Markup


```HTML

<head>
        <meta http-equiv="X-UA-Compatible" content="IE=10" />
        <!--CS: Start Page Head Contents Snippet-->
        <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SID:00 -->
        <meta name="GENERATOR" content="Microsoft SharePoint" />
        <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
        <meta http-equiv="Expires" content="0" />
        <!--MS:<SharePoint:RobotsMetaTag runat="server">-->
        <!--ME:</SharePoint:RobotsMetaTag>-->
        <!--MS:<SharePoint:PageTitle runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
                <!--MS:<SharePoint:ProjectProperty Property="Title" runat="server">-->
                <!--ME:</SharePoint:ProjectProperty>-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:PageTitle>-->
        <!--MS:<SharePoint:StartScript runat="server">-->
        <!--ME:</SharePoint:StartScript>-->
        <!--MS:<SharePoint:CssLink runat="server" Version="15">-->
        <!--ME:</SharePoint:CssLink>-->
        <!--MS:<SharePoint:CacheManifestLink runat="server">-->
        <!--ME:</SharePoint:CacheManifestLink>-->
        <!--MS:<SharePoint:PageRenderMode runat="server" RenderModeType="Standard">-->
        <!--ME:</SharePoint:PageRenderMode>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="core.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="menu.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="callout.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="sharing.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="suitelinks.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:CustomJSUrl runat="server">-->
        <!--ME:</SharePoint:CustomJSUrl>-->
        <!--MS:<SharePoint:SoapDiscoveryLink runat="server">-->
        <!--ME:</SharePoint:SoapDiscoveryLink>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaPlaceHolderAdditionalPageHead" Container="false" runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
            <!--MS:<SharePoint:DelegateControl runat="server" ControlId="AdditionalPageHead" AllowMultipleControls="true">-->
            <!--ME:</SharePoint:DelegateControl>-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderBodyAreaClass" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--MS:<SharePoint:CssRegistration Name="Themable/corev15.css" runat="server">-->
        <!--ME:</SharePoint:CssRegistration>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaSPWebPartManager" runat="server">-->
            <!--MS:<WebPartPages:SPWebPartManager runat="server">-->
            <!--ME:</WebPartPages:SPWebPartManager>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--CE: End Page Head Contents Snippet-->
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
        <!--DC:Business Solutions-->
        <link rel="stylesheet" href="css/style.css" type="text/css" charset="utf-8" />
        <!--[if lte IE 7]>
  <link rel="stylesheet" href="css/ie.css" type="text/css" charset="utf-8"/> 
 <![endif]-->
        <!--[if gte mso 9]><xml>
<mso:CustomDocumentProperties>
<mso:HtmlDesignFromMaster msdt:dt="string"></mso:HtmlDesignFromMaster>
<mso:HtmlDesignStatusAndPreview msdt:dt="string">http://[server_name]/sites/PubSite/_catalogs/masterpage/[site_name]/index.html, Conversion successful.</mso:HtmlDesignStatusAndPreview>
<mso:ContentTypeId msdt:dt="string">0x0101000F1C8B9E0EB4BE489F09807B2C53288F0054AD6EF48B9F7B45A142F8173F171BD10003D357F861E29844953D5CAA1D4D8A3A0084F0F9C7FCB65541A59990D173DA60FA</mso:ContentTypeId>
<mso:HtmlDesignAssociated msdt:dt="string">1</mso:HtmlDesignAssociated>
<mso:HtmlDesignConversionSucceeded msdt:dt="string">True</mso:HtmlDesignConversionSucceeded>
</mso:CustomDocumentProperties>
</xml><![endif]-->
    </head>

```


### Hinter dem <body>-Anfangstag hinzugefügtes Markup


#### Codeausschnitt des Menübands


```HTML

<!--CS: Start Ribbon Snippet-->
        <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="wssucw" TagName="Welcome" Src="~/_controltemplates/15/Welcome.ascx"%>-->
        <!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" HideFromSearchCrawler="true" EmitDiv="true">-->
            <div id="TurnOnAccessibility" style="display:none" class="s4-notdlg noindex">
                <a id="linkTurnOnAcc" href="#" class="ms-accessible ms-acc-button" onclick="SetIsAccessibilityFeatureEnabled(true);UpdateAccessibilityUI();document.getElementById('linkTurnOffAcc').focus();return false;">
                    <!--MS:<SharePoint:EncodedLiteral runat="server" text="&amp;lt;%$Resources:wss,master_turnonaccessibility%&amp;gt;" EncodeMethod="HtmlEncode">-->
                    <!--ME:</SharePoint:EncodedLiteral>-->
                </a>
            </div>
            <div id="TurnOffAccessibility" style="display:none" class="s4-notdlg noindex">
                <a id="linkTurnOffAcc" href="#" class="ms-accessible ms-acc-button" onclick="SetIsAccessibilityFeatureEnabled(false);UpdateAccessibilityUI();document.getElementById('linkTurnOnAcc').focus();return false;">
                    <!--MS:<SharePoint:EncodedLiteral runat="server" text="&amp;lt;%$Resources:wss,master_turnoffaccessibility%&amp;gt;" EncodeMethod="HtmlEncode">-->
                    <!--ME:</SharePoint:EncodedLiteral>-->
                </a>
            </div>
        <!--ME:</SharePoint:SPSecurityTrimmedControl>-->
        <div id="ms-designer-ribbon">
            <!--SID:02 {Ribbon}-->
            <!--PS: Start of READ-ONLY PREVIEW (do not modify) --><div class="DefaultContentBlock" style="background:rgb(0, 114, 198); color:white; width:100%; padding:8px; height:64px; overflow:hidden;">The SharePoint ribbon will be here when your file is either previewed on or applied to your site.</div><!--PE: End of READ-ONLY PREVIEW -->
        </div>
        <!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AnonymousUsersOnly">-->
            <!--MS:<wssucw:Welcome runat="server" EnableViewState="false">-->
            <!--ME:</wssucw:Welcome>-->
        <!--ME:</SharePoint:SPSecurityTrimmedControl>-->
        <!--CE: End Ribbon Snippet-->

```


#### Zwei SharePoint <div>-Tags


```HTML

<div id="s4-workspace">
            <div id="s4-bodyContainer">

```


### Vor dem schließenden </body>-Tag und zwei schließenden </div>-Tags hinzugefügtes Markup


```HTML

<div data-name="ContentPlaceHolderMain">
                    <!--CS: Start PlaceHolderMain Snippet-->
                    <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                    <!--MS:<SharePoint:AjaxDelta ID="DeltaPlaceHolderMain" IsMainContent="true" runat="server">-->
                        <!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
                            <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
            This div, which you should delete, represents the content area that your Page Layouts and pages will fill. Design your Master Page around this content placeholder.
        
                            </div>
                        <!--ME:</asp:ContentPlaceHolder>-->
                    <!--ME:</SharePoint:AjaxDelta>-->
                    <!--CE: End PlaceHolderMain Snippet-->
                </div>

```


## Zusätzliche Ressourcen
<a name="Additional"> </a>


-  [Übersicht über den Entwurfs-Manager in SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md)
    
  

