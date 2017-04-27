---
title: Anzeigevorlagen im SharePoint 2013-Entwurfs-Manager
ms.prod: SHAREPOINT
ms.assetid: 1a782bac-48ee-4baf-8751-0f943a306e0f
---


# Anzeigevorlagen im SharePoint 2013-Entwurfs-Manager
Hier finden Sie Informationen zu Anzeigevorlagen. Es wird erläutert, in welchem Zusammenhang diese mit Such-Webparts stehen, wie die Vorlagen strukturiert sind, wie Eigenschaften zugeordnet und Variablen und jQuery verwendet werden, und wie eine benutzerdefinierte Anzeigevorlage in SharePoint Server 2013 erstellt wird.
## Einführung in Anzeigevorlagen
<a name="bk_introduction"> </a>

Anzeigevorlagen in SharePoint Server 2013 sind in Webparts verwendete Vorlagen, die Suchtechnologien verwenden (in diesem Artikel als Such-Webparts bezeichnet), um die Ergebnisse einer Abfrage anzuzeigen, die an den Suchindex gestellt wurde. Anzeigevorlagen steuern, welche verwalteten Eigenschaften in den Suchergebnissen angezeigt werden, und wie sie im Webpart angezeigt werden. Jede Anzeigevorlage besteht aus zwei Dateien: einer HTML-Version der Anzeigevorlage, die Sie in Ihrem HTML-Editor bearbeiten können, und einer JS-Datei, die SharePoint verwendet.
  
    
    

> **HINWEIS**
> Nur Such-Webparts können Anzeigevorlagen verwenden. Das Inhaltsabfrage-Webpart ist nicht suchgesteuert und verwendet daher keine Anzeigevorlagen. 
  
    
    

Sie können vorhandene Anzeigevorlagen im Entwurfs-Manager anzeigen. Sie können sie aber nicht auf die gleiche Weise im Entwurfs-Manager erstellen, wie Sie Gestaltungsvorlagen und Seitenlayouts erstellen. Stattdessen gehen Sie folgendermaßen vor:
  
    
    

- Öffnen Sie Ihr  [dem Gestaltungsvorlagenkatalog zugeordnetes Netzwerklaufwerk](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
    
  
- Öffnen Sie einen der vier Ordner im Ordner **Anzeigevorlagen**.
    
    > **HINWEIS**
      > Welchen Ordner Sie auswählen, hängt vom Typ der Anzeigevorlage ab, die Sie verwenden möchten. Wenn Ihre Website z. B. websiteübergreifendes Veröffentlichen verwendet, kopieren Sie eine Anzeigevorlage aus dem Ordner **Inhalts-Webparts**. Weitere Informationen finden Sie unter  [Referenz der Anzeigevorlagen in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj944947.aspx). 
- Kopieren Sie die HTML-Datei für eine vorhandene Anzeigevorlage, die derjenigen ähnelt, die Sie erstellen möchten. Der genaue Speicherort, an den Sie die Datei kopieren, ist nicht wichtig, solange sich dieser im **Gestaltungsvorlagenkatalog** befindet.
    
  
- Öffnen und ändern Sie Ihre Kopie in einem HTML-Editor.
    
  
Wenn Sie eine vorhandene Anzeigevorlage als Ausgangspunkt für eine neue Anzeigevorlage verwenden, können Sie von den hilfreichen Informationen zum Anpassungsprozess in den Kommentaren der Standardanzeigevorlagen profitieren, und Sie verfügen über einen Rahmen für einfache Aufgaben wie das Zuordnen von Eingabefeldern. Außerdem ist durch diese Vorgehensweise sichergestellt, dass Ihre Vorlagen die richtige grundlegende Seitenstruktur verwenden.
  
    
    
Wenn Sie durch Kopieren der HTML-Datei für eine vorhandene Anzeigevorlage im Ordner **Anzeigevorlagen** im **Gestaltungsvorlagenkatalog** eine Anzeigevorlage erstellen, gilt Folgendes:
  
    
    

- Am Speicherort, an den Sie die HTML-Datei kopieren, wird eine JS-Datei mit dem gleichen Namen erstellt.
    
  
- Sämtliches Markup, das SharePoint Server 2013 benötigt, wird der JS-Datei hinzugefügt, sodass die Anzeigevorlage korrekt angezeigt wird.
    
  
- Die HTML-Datei und die JS-Datei werden verknüpft, sodass spätere Änderungen an der HTML-Datei mit der JS-Datei synchronisiert werden, wenn die HTML-Datei gespeichert wird.
    
  

> **HINWEIS**
> Die Synchronisierung erfolgt nur in eine Richtung. Änderungen an der HTML-Anzeigevorlage werden mit der verknüpften JS-Datei synchronisiert. Anders als bei Gestaltungsvorlagen und Seitenlayouts können Sie beim Arbeiten mit Anzeigevorlagen nicht nur mit der JS-Datei arbeiten, indem Sie die Verknüpfung zwischen den Dateien aufheben. Sie müssen sämtliches HTML und JavaScript in die HTML-Datei eingeben. 
  
    
    


## Grundlegendes zum Zusammenhang von Anzeigevorlagen und Such-Webparts
<a name="bk_DTandSWP"> </a>

Es gibt grundsätzlich zwei Arten von Anzeigevorlagen:
  
    
    

- **Steuerelementvorlagen** bestimmen die allgemeine Struktur der Präsentation der Ergebnisse. Sie umfassen Listen, Listen mit Paging und Diaschauen.
    
  
- **Elementvorlagen** bestimmen die Anzeige jedes Ergebnis im Satz. Sie umfassen Bilder, Text, Video und andere Elemente.
    
  
Weitere Informationen zu diesen und anderen Anzeigevorlagen finden Sie unter  [Referenz der Anzeigevorlagen in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj944947.aspx).
  
    
    
Nachdem Sie einer Seite ein Such-Webpart (wie z. B. das Inhaltssuche-Webpart) hinzugefügt haben, wählen Sie zum Konfigurieren des Webparts sowohl eine Steuerelementvorlage als auch eine Elementanzeigevorlage aus (siehe Abbildung 1).
  
    
    

**Abbildung 1. Toolbereich des Inhaltssuche-Webparts**

  
    
    

  
    
    
![Toolbereich des Inhaltssuche-Webparts](images/115_content_search_web_part_tool_pane.gif)
  
    
    
Die Steuerelementvorlage stellt HTML bereit, um das allgemeine Layout so zu strukturieren, wie die Suchergebnisse präsentiert werden sollen. So stellt die Steuerelementvorlage möglicherweise das HTML für eine Kopfzeile und Beginn und Ende einer Liste bereit. Die Steuerelementvorlage wird im Webpart nur einmal gerendert.
  
    
    
Die Elementanzeigevorlage stellt HTML bereit, das die Anzeige jedes Elements im Ergebnissatz bestimmt. So stellt die Elementanzeigevorlage möglicherweise das HTML für ein Listenelement bereit, das ein Bild und drei Zeilen Text enthält, die unterschiedlichen verwalteten Eigenschaften zugeordnet sind, die mit dem Element verknüpft sind. Die Elementanzeigevorlage wird für jedes Element im Ergebnissatz einmal gerendert. Wenn der Ergebnissatz zehn Elemente enthält, erstellt die Anzeigevorlage daher ihren HMTL-Abschnitt zehnmal.
  
    
    
Wenn die Steuerelement- und die Elementanzeigevorlage auf diese Art und Weise zusammen verwendet werden, wird ein zusammenhängender HTML-Block erstellt, der im Webpart gerendert wird (siehe Abbildung 2).
  
    
    

**Abbildung 2. Kombinierte HTML-Ausgabe einer Steuerelementanzeigevorlage und einer Elementanzeigevorlage**

  
    
    

  
    
    
![Kombinierte HTML-Ausgabe einer Steuerelementanzeigevorlage und einer Elementanzeigevorlage](images/sp15Con_CreateDisplayTemplateSP2013_Figure02.png)
  
    
    
Weitere Informationen zu Anzeigevorlagen finden Sie in Artikel  [Übersicht über das SharePoint 2013-Seitenmodell](overview-of-the-sharepoint-2013-page-model.md) im Abschnitt "Suchgesteuerte Webparts und Anzeigevorlagen".
  
    
    

## Grundlegendes zur Anzeigevorlagenstruktur
<a name="bk_DTstructure"> </a>

Die HTML-Datei, die für eine Anzeigevorlage verwendet wird, ist ein vollständiges HTML-Dokument, stellt aber keine vollständige HTML-Webseite dar. SharePoint wandelt die Teile der HTML-Anzeigevorlagendatei in JavaScript um. In diesem Abschnitt werden die vier wichtigsten Abschnitte einer Anzeigevorlage beschrieben.
  
    
    

### Titel-Tag

Der Text im **<title>**-Tag in einer Anzeigevorlagendatei wird als der Anzeigename im Abschnitt **Anzeigevorlagen** des Webpart-Bearbeitungsbereichs verwendet, wenn sich das Such-Webpart im Bearbeitungsmodus befindet. Das folgende Beispiel bezieht sich auf die Elementanzeigevorlage mit dem Namen "Item_Picture3Lines.html":
  
    
    

```HTML

<title>Picture on left, 3 lines on right</title>
```


### Header-Eigenschaften

Direkt nach dem **<title>**-Tag findet sich ein Satz benutzerdefinierter Elemente, die mit folgendem Markup versehen sind:
  
    
    

```HTML
<!--[if gte mso 9]><xml>
<mso:CustomDocumentProperties>
…
</mso:CustomDocumentProperties>
</xml><![endif]-->

```

Diese Elemente und deren Eigenschaften liefern der SharePoint-Umgebung wichtige Informationen zur Anzeigevorlage. Tabelle 1 beschreibt die benutzerdefinierten Eigenschaften, die in Anzeigevorlagen verwendet werden.
  
    
    

> **HINWEIS**
> Nicht alle benutzerdefinierten Eigenschaften werden in jeder Anzeigevorlage verwendet. Außerdem können einige Eigenschaften geändert werden, indem die Eigenschaften der Anzeigevorlagendatei im Entwurfs-Manager bearbeitet werden. 
  
    
    


**Tabelle 1. Liste der CustomDocumentProperties-Einträge**


|**Eigenschaft**|**Beschreibung**|
|:-----|:-----|
|**TemplateHidden** <br/> |Boolescher Wert, der angibt, ob die Anzeigevorlage in der Liste verfügbarer Vorlagen im Webpart ausgeblendet werden soll. Dieser Wert kann in den Eigenschaften der Anzeigevorlagendatei geändert werden.  <br/> |
|**ManagedPropertyMapping** <br/> |Ordnet Felder, die von Suchergebniselemente verfügbar gemacht werden, für JavaScript verfügbaren Eigenschaften zu. Wird nur in Elementvorlagen verwendet.  <br/> |
|**MasterPageDescription** <br/> |Liefert eine benutzerfreundliche Beschreibung der Anzeigevorlage. Diese wird Benutzern in der SharePoint-Bearbeitungsumgebung angezeigt. Dieser Wert kann in den Eigenschaften der Anzeigevorlagendatei geändert werden.  <br/> |
|**ContentTypeId** <br/> |Die ID des mit der Anzeigevorlage verknüpften Inhaltstyps.  <br/> |
|**TargetControlType** <br/> |Gibt den Kontext an, in dem die Anzeigevorlage verwendet wird. Dieser Wert kann in den Eigenschaften der Anzeigevorlagendatei geändert werden.  <br/> |
|**HtmlDesignAssociated** <br/> |Boolesche Wert, der angibt, ob mit einer HTML-Anzeigevorlagendatei eine JS-Datei verknüpft ist.  <br/> |
|**HtmlDesignConversionSucceeded** <br/> |Gibt an, ob der Konvertierungsprozess erfolgreich war. Dieser Wert wird der Datei von SharePoint automatisch hinzugefügt und wird nur in benutzerdefinierten Anzeigevorlagen verwendet.  <br/> |
|**HtmlDesignStatusAndPreview** <br/> |Enthält die URL zur HTML-Datei und den Text für die Spalte **Status** (entweder **Konvertierung erfolgreich** oder **Warnungen und Fehler**). Dieser Wert wird der Datei von SharePoint automatisch hinzugefügt und wird nur in benutzerdefinierten Anzeigevorlagen verwendet.  <br/> |
   

### Skriptblock
<a name="bk_scriptblock"> </a>

Innerhalb des **<body>**-Tags sehen Sie das folgende **<script>**-Tag:
  
    
    

```HTML

<script>
     $includeLanguageScript(this.url, "~sitecollection/_catalogs/masterpage/Display Templates/Language Files/{Locale}/CustomStrings.js");
</script>
```

Diese Zeile ist standardmäßig in allen Anzeigevorlagen enthalten. Sie können im **<script>**-Tag weitere Codezeilen hinzufügen, um CSS-Dateien oder andere JavaScript-Dateien außerhalb der Ihrer zentralen HTML-Anzeigevorlagendatei zu referenzieren. Tabelle 2 enthält Beispiele dafür, wie Sie andere Ressourcen einschließen.
  
    
    

**Tabelle 2. Beispiele für das Einschließen externer Ressourcen in das <Skript>-Tag**


|**Wenn Sie Folgendes einschließen möchten:**|**Verwenden Sie den folgenden Code:**|
|:-----|:-----|
|Eine JavaScript-Datei, die Teil der aktuellen Websitesammlung ist  <br/> | `$includeScript(this.url, "~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/MyScripts.js");` <br/> |
|Eine externe JavaScript-Datei  <br/> | `$includeScript(this.url, "http://www.contoso.com/ExternalScript.js");` <br/> |
|Eine CSS-Datei, die Teil der aktuellen Websitesammlung ist  <br/> | `$includeCSS(this.url, "~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/MyCSS.css");` <br/> |
|Eine CSS-Datei, die sich an einem zur aktuellen Anzeigevorlage relativen Speicherort befindet  <br/> | `$includeCSS(this.url,"../../MyStyles/MyCSS.css");` <br/> |
   

> **HINWEIS**
> Wenn für Elemente im Gestaltungsvorlagenkatalog eine **Inhaltsgenehmigung** erforderlich ist, müssen alle Ressourcendateien (einschließlich CSS- und JS-Dateien) veröffentlicht werden, bevor sie für Gestaltungsvorlagen und Seitenlayouts verfügbar sind. Weitere Informationen finden Sie unter [Festlegen einer Genehmigungsanforderung für Elemente in einer Websiteliste oder -bibliothek](http://office.microsoft.com/de-de/sharepoint-help/require-approval-of-items-in-a-site-list-or-library-HA102853936.aspx?CTT=1). 
  
    
    


### DIV-Block
<a name="bk_scriptblock"> </a>

Dem **<script>**-Tag folgt ein **<div>**-Tag mit einer ID. Die ID für dieses **<div>**-Tag stimmt standardmäßig mit dem Namen der HTML-Datei überein. HTML oder Code, den die Anzeigevorlage bereitstellen soll, muss in dieses **<div>**-Tag eingeschlossen werden. Das Tag selbst wird jedoch nicht in das Markup eingeschlossen, das zur Laufzeit auf der Webseite gerendert wird. 
  
    
    

> **HINWEIS**
> Wenn Sie dem HTML-Block, der zur Laufzeit auf der Seite gerendert wird, eine CSS-Formatvorlage oder eine ID zuweisen möchten, können Sie im ersten **<div>**-Tag ein neues Tag hinzufügen. Sie können auch dem HTML, das die Variable  `_#= ctx.RenderGroups(ctx) =#_` in der Steuerelementvorlage umgibt, eine CSS-Formatvorlage oder eine ID zuweisen. Die Variable `_#= ctx.RenderGroups(ctx) =#_` wird zum Rendern des HTML verwendet, das die Abfrageergebnisse umgibt, die von der Elementvorlage gerendert werden.
  
    
    

Im ersten **<div>**-Tag befindet sich Code innerhalb von Kommentarblöcken, der mit **<!--#_** beginnt und mit **_#-->** endet. Sie verwenden JavaScript-Code innerhalb dieser Blöcke und HTML außerhalb der Blöcke. Mit diesen Blöcken können Sie auch das HTML mit Bedingungsanweisungen steuern. Verwenden Sie dazu einen Kommentarblock mit der Bedingungsanweisung und einer öffnenden Klammer, gefolgt vom HTML, gefolgt von einem anderen Kommentarblock mit der schließenden Klammer. Im folgenden Beispiel wird das Anchortag auf der Seite nur gerendert, wenn der Wert für das **linkURL**-Objekt nicht leer ist.
  
    
    



```HTML

<!--#_
if(!linkURL.isEmpty)
{
_#-->
     <a class="cbs-pictureImgLink" href="_#= linkURL =#_" title="_#= $htmlEncode(line1.defaultValueRenderer(line1)) =#_" id="_#= pictureLinkId =#_">
<!--#_
}
_#-->

```


## Zuordnen von Eingabeeigenschaften und Abrufen der Werte
<a name="bk_mapproperties"> </a>

Der Kopfzeilenbereich einer Elementanzeigevorlage weist eine benutzerdefinierte Dokumenteigenschaft namens **ManagedPropertyMapping** auf. Diese Eigenschaft ordnet die verwalteten Eigenschaften, die von der Suche verwendet werden, Werten zu, die von der Anzeigevorlage verwendet werden können. Die Eigenschaft ist eine durch Kommas getrennte Werteliste im folgenden Format: ' _Anzeigename der Eigenschaft_'{ _Eigenschaftsname_}:' _verwaltete Eigenschaft_'. Beispiel:  `'Picture URL'{Picture URL}:'PublishingImage;PictureURL;PictureThumbnailURL'`.
  
    
    
Im Folgenden wird das Format näher erläutert:
  
    
    

-  _Anzeigename der Eigenschaft_ ist der Eigenschaftsname, der im Bearbeitungsbereich des Webparts angezeigt wird, wenn die Anzeigevorlage ausgewählt wird.
    
  
-  _Eigenschaftsname_ ist ein Bezeichner, der lokalisierte Zeichenfolgeressourcen verwendet, um den Namen der verwalteten Eigenschaft nachzuschlagen. Er verwendet auch den Wert, der im Menü mit den Webparteinstellungen im Abschnitt **Eigenschaftszuordnungen** angezeigt wird. Wenn Sie die Einstellungen für ein Webpart bearbeiten, können Sie diesen Wert ändern, um zu ändern, welche verwaltete Eigenschaft mit dem im Webpart angezeigten Feld verknüpft wird.
    
  
-  _verwaltete Eigenschaft_ ist eine Zeichenfolge einer oder mehrerer verwalteter Eigenschaften, die durch Strichpunkte getrennt sind. Zur Laufzeit wird diese Liste von links nach rechts gelesen, und der erste Wert, der mit dem Namen einer verwalteten Eigenschaft des aktuellen Suchelements übereinstimmt, wird diesem Slot zugeordnet. Dadurch können Sie einen Anzeigenamen schreiben, der mit mehreren Elementtypen verwendet werden kann, und der bei Vorhandensein kompatibler Eigenschaften konsistentes Rendering verwenden kann.
    
  
Nachdem Sie eine Eigenschaft zugeordnet haben, können Sie mit folgendem Code deren Wert in Skript abrufen:  `var pictureURL = $getItemValue(ctx, "Picture URL");`
  
    
    
Der zweite Parameter, der an **$getItemValue()** übergeben wird, muss dem Anzeigenamen der Eigenschaft in einfachen Anführungszeichen entsprechen, der im **ManagedPropertyMapping**-Element verwendet wird. In diesem Beispiel ist **Picture URL** der Eigenschaftsname, der an **$getItemValue()** übergeben wird.
  
    
    
Dieser Code gibt ein Wertinformationsobjekt zurück ( **valueInfoObj**). Dieses Objekt enthält eine Rohdarstellung des Eingabewerts, zusammen mit dem Wert, auf den eine Standardcodierung angewendet wurde.
  
    
    
Sie können Variablen innerhalb der Abschnitte von JavaScript verwenden, wie Sie das normalerweise tun würden, um Variablen zu bearbeiten und HTML-Zeichenfolgen zu erstellen, die zur Laufzeit auf der Seite gerendert werden. Um Variablen zu referenzieren, die im Skript direkt im HTML deklariert wurden, müssen Sie allerdings das folgende Format verwenden: _#=  _variableName_ =#_. Um z. B. die Variable **pictureURL** als den Wert für ein Bild zu verwenden, müssen Sie den folgenden HTML-Code verwenden: `<img src="_#= pictureURL =#_" />`
  
    
    

## Verwenden von jQuery mit Anzeigevorlagen
<a name="bk_jQuery"> </a>

Sie können für Ihre Anzeigevorlagen jQuery verwenden. Beachten Sie dabei allerdings folgende zwei Punkte:
  
    
    

- Um die jQuery-Bibliotheken in Ihre Anzeigevorlage einzuschließen, befolgen Sie die im Abschnitt  [Skriptblock](#bk_scriptblock) weiter oben in diesem Artikel beschriebenen Anweisungen.
    
  
- Wenn Sie ID-Auswahlen in jQuery verwenden, erstellen Sie eine Variable für die ID mit dem folgenden Code:  `var containerQueryId = '#' + '_#= containerId =#_';`
    
    Verwenden Sie den folgenden Code, um die Auswahl in jQuery zu referenzieren:  `$('_#= containerQueryId =#_')`
    
  

## Erstellen einer Anzeigevorlage
<a name="bk_createDT"> </a>

Bevor Sie mithilfe des folgenden Verfahrens eine Anzeigevorlage erstellen können, müssen Sie ein zugeordnetes Netzwerklaufwerk haben, das auf den **Gestaltungsvorlagenkatalog** verweist. Weitere Informationen finden Sie unter [Gewusst wie: Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

### So erstellen Sie eine Anzeigevorlage


1. Öffnen Sie mithilfe von Windows Explorer das auf den **Gestaltungsvorlagenkatalog** verweisende zugeordnete Netzwerklaufwerk.
    
  
2. Öffnen Sie den Ordner **Anzeigevorlagen**, und öffnen Sie dann den Ordner **Inhalts-Webparts**.
    
  
3. Kopieren Sie die HTML-Datei für eine Anzeigevorlage, die derjenigen ähnelt, die Sie erstellen möchten. Eine Liste der Standardanzeigevorlagen mit entsprechenden Beschreibungen finden Sie unter  [Referenz der Anzeigevorlagen in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj944947.aspx).
    
    Nun kopiert SharePoint Server 2013 die HTML-Datei in eine JS-Datei mit dem gleichen Namen. Wenn die kopierte HTML-Datei z. B. "Item_Picture3Line_copy.html" heißt, wird auch eine entsprechende JS-Datei mit dem Namen "Item_Picture3Lines_copy.js" erstellt. Wenn Sie die Datei umbenennen, wird auch der Name der entsprechenden JS-Datei geändert.
    
  
4. Um die Anzeigevorlage anzupassen, bearbeiten Sie die HTML-Datei auf dem Server. Verwenden Sie zum Öffnen und Bearbeiten der HTML-Datei auf dem zugeordneten Laufwerk einen HTML-Editor. Immer wenn Sie die HTML-Datei speichern, werden die Änderungen mit der entsprechenden JS-Datei synchronisiert.
    
  
5. Wechseln Sie zu Ihrer Veröffentlichungswebsite.
    
  
6. Wählen Sie in der rechten oberen Ecke der Seite **Einstellungen** und dann **Entwurfs-Manager**.
    
  
7. Wählen Sie im Entwurfs-Manager im linken Navigationsbereich **Anzeigevorlagen bearbeiten** aus. Ihre HTML-Datei wird nun mit der Spalte **Status** angezeigt, die einen der zwei Status aufweist:
    
  - **Warnungen und Fehler**
    
  
  - **Konvertierung erfolgreich**
    
  

    > **HINWEIS**
      > Sie können nicht wie bei Gestaltungsvorlagen und Seitenlayouts die Vorschauseite verwenden, um eine serverseitige Livevorschau Ihrer Anzeigevorlage anzuzeigen. Um eine Vorschau der Anzeigevorlage anzuzeigen, müssen Sie einer Seite ein Inhaltssuche-Webpart hinzufügen und dann die Anzeigevorlage im Bearbeitungsbereich des Inhaltssuche-Webparts anwenden. Weist die Anzeigevorlage Fehler auf, zeigt das Inhaltssuche-Webpart eine Fehlermeldung an. Fehler müssen behoben werden, bevor die Anzeigevorlage korrekt angezeigt werden kann. 
8. Bearbeiten Sie zur Behebung von Fehlern die HTML-Datei auf dem Server. Verwenden Sie zum Öffnen und Bearbeiten der HTML-Datei auf dem zugeordneten Laufwerk einen HTML-Editor. Speichern Sie die Anzeigevorlage, und laden Sie dann die Seite mit dem Inhaltssuche-Webpart, welche die Anzeigevorlage verwendet, neu.
    
  

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Übersicht über den Entwurfs-Manager in SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Entwickeln des Website-Designs in SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Design Manager - Branding- und Designfunktionen](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

