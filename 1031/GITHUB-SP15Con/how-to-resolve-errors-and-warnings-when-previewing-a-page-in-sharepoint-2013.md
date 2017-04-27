---
title: Vorgehensweise Beheben von Fehlern und Warnungen bei der Vorschau einer Seite in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 03f72f65-b22b-4304-be92-f44ce0619372
---


# Vorgehensweise: Beheben von Fehlern und Warnungen bei der Vorschau einer Seite in SharePoint 2013
Nach dem Konvertieren einer HTML-Datei in eine SharePoint 2013-Gestaltungsvorlage oder nach dem Erstellen eines Seitenlayouts können Sie eine Vorschau dieser Seite im Browser anzeigen. Bevor Sie eine Gestaltungsvorlage oder ein Seitenlayout in der Vorschau anzeigen können, müssen Sie jedoch alle Probleme beheben, die das Rendern der Seite in der serverseitigen Vorschau verhindern.
## Einführung in das Beheben von Fehlern der Vorschau
<a name="Introduction"> </a>

Nach dem Konvertieren einer HTML-Datei in eine SharePoint 2013-Gestaltungsvorlage oder nach dem Erstellen eines Seitenlayouts können Sie eine Vorschau dieser Seite im Browser anzeigen. Beim Bearbeiten und Speichern Ihrer HTML-Gestaltungsvorlage oder Ihres Seitenlayouts können Sie die Vorschau aktualisieren, um genau zu sehen, wie SharePoint 2013 die Seite rendert.
  
    
    
Die Vorschau im Entwurfs-Manager zeigt eine aktuelle serverseitige Vorschau. Somit verwenden alle Codeausschnitte oder Steuerelemente auf der Seite, wie Navigationssteuerelemente oder suchgesteuerte Webparts, Livedaten. Zudem können Sie bei der Vorschau einer Gestaltungsvorlage oder eines Seitenlayouts eine generische Vorschau dieser Datei auswählen oder ansehen, wie eine bestimmte Seite Ihrer Website mit dieser Gestaltungsvorlage oder diesem Seitenlayout gerendert wird. Die serverseitige Vorschau ist ein äußerst nützliches Tool, das die Vorschau zur Entwurfszeit in einem HTML-Editor ergänzt. Weitere Informationen finden Sie unter  [Vorgehensweise: ändern die Vorschauseite in SharePoint 2013-Design-Manager](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md).
  
    
    
Bevor Sie eine Gestaltungsvorlage oder ein Seitenlayout in der Vorschau anzeigen können, müssen Sie jedoch alle Probleme beheben, die das Rendern der Seite in der serverseitigen Vorschau verhindern. Wenn die serverseitige Vorschau nicht funktioniert, bedeutet dies, dass die Gestaltungsvorlage oder das Seitenlayout nach der Anwendung auf Ihre Website ebenfalls nicht funktioniert. Nach dem Konvertieren einer Gestaltungsvorlage oder nach dem Erstellen eines Seitenlayouts können Sie im Entwurfs-Manager auf den Dateinamen oder den Konvertierungsstatus klicken, um eine Vorschau der Datei anzuzeigen. Im Infobereich der Vorschauseite werden etwaige Warnungen oder Fehler angezeigt.
  
    
    
Hier finden Sie die Fehler und Warnungen, die bei der Vorschau auftreten können, und Hilfe für deren Behebung.
  
    
    

## HTML-Datei darf keine <form>-Tags enthalten
<a name="FormTags"> </a>


### Meldung

 **Ihre Gestaltungsvorlage verfügt über ein oder mehrere <FORM>-HTML-Tags. Damit Ihre Gestaltungsvorlage funktioniert, müssen die Tags entfernt werden (die Tag-Inhalte müssen Sie jedoch nicht entfernen).**
  
    
    

### Lösung

SharePoint 2013-Seiten werden bereits in ein **<form>**-Tag eingeschlossen, damit ASP.NET Postbacks ausführen kann (insbesondere enthält eine SharePoint 2013-Gestaltungsvorlage das **<SharePoint:SharePointForm>**-Tag, das beim Rendern einer verknüpften Inhaltsseite ein tatsächliches **<form>**-Tag erstellt). Somit bedeutet die Aufnahme eines **<form>**-Tags in Ihre Gestaltungsvorlage oder Ihr Seitenlayout, dass das endgültige Rendering der Seite geschachtelte **<form>**-Tags enthalten würde, was in HTML nicht zulässig ist. Löschen Sie in Ihrem HTML-Editor alle **<form>**-Tags, speichern Sie die Seite, und aktualisieren Sie dann die Vorschau.
  
    
    
Soll das Seitenlayout ein **<form>**-HTML-Tag enthalten, sollten Sie das Formular in einen Inhaltsplatzhalter mit der ID **PlaceHolderUtilityContent** einschließen. Dazu fügen Sie Ihrem HTML-Seitenlayout folgenden Code hinzu:
  
    
    



```HTML

<!--CS: Start Create Snippets From Custom ASP.NET Markup Snippet-->
<!--SPM:<SharePoint:AjaxDelta id="DeltaPlaceHolderUtilityContent" runat="server">-->
<!--SPM:<asp:ContentPlaceHolder id="PlaceHolderUtilityContent" runat="server" />-->
<!--SPM:</SharePoint:AjaxDelta>-->
<!--CE: End Create Snippets From Custom ASP.NET Markup Snippet-->
```

Sie können Ihrer Seite auch das HTML-Formularwebpart oder das InfoPath-Formularwebpart aus dem Codeausschnittkatalog hinzufügen. Weitere Informationen finden Sie unter  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md).
  
    
    

## HTML-Datei muss XML-konform sein
<a name="XMLCompliant"> </a>


### Meldung

 **Für XML-Kompatibilität benötigt SharePoint HTML-Dateien. Ihre Datei ist nicht XML-kompatibel, wahrscheinlich aufgrund von Tageigenschaften ohne Anführungszeichen, fehlenden Endtags oder ungültigen Eigenschaften in den Tags. {Art des Fehlers, Ort des Fehlers}. Aufgetreten bei: {Zeit}.**
  
    
    

### Lösung

Für die Konvertierung einer HTML-Datei in die entsprechende ASP.NET-Datei muss die HTML-Datei XML-konform sein. Dieser Fehler gibt bestimmtes Markup in der HTML-Datei an, das nicht XML-kompatibel ist. Führen Sie die HTML-Datei über eine XML-Bestätigung aus, beheben Sie etwaige Probleme mit Ihrem HTML-Editor, speichern Sie die Datei und aktualisieren Sie dann die Vorschau.
  
    
    

> **HINWEIS**
> Diese Anforderung setzt einige HTML 5-Normen außer Kraft. Beispielsweise können Sie den Dokumenttyp (doctype) in HTML 5 in Kleinschreibung angeben, während er in XML in Großbuchstaben geschrieben sein muss. 
  
    
    


  
    
    

## HTML-Datei enthält problematisches Markup
<a name="ProblematicMarkup"> </a>


### Meldung

 **SharePoint kann diese Datei nicht analysieren, höchstwahrscheinlich aufgrund eines falsch formatierten SharePoint-Ausschnitts. Das Markup an folgender Position verursacht Probleme. Bearbeiten Sie das Markup manuell, um es zu reparieren, oder ersetzen Sie es durch einen neuen Ausschnitt aus dem Codeausschnittkatalog. {Art des Fehlers, Ort des Fehlers}. Aufgetreten bei: {Zeit}.**
  
    
    

### Lösung

Dieser Fehler wird angezeigt, wenn ein Problem mit einem SharePoint-Ausschnitt in Ihrer HTML-Datei auftritt. Zur Behebung des Fehlers machen Sie die Änderung rückgängig, die den Fehler verursacht hat, oder ersetzen Sie den problematischen Codeausschnitt durch einen neuen, entweder aus dem Codeausschnittkatalog oder aus einer anderen Gestaltungsvorlage oder Seitenlayoutdatei, die eine funktionierende Version des Ausschnitts enthält. Nach dem Reparieren oder Ersetzen des Codeausschnitts speichern Sie die Seite in Ihrem HTML-Editor, und aktualisieren Sie dann die Vorschau.
  
    
    

## Gestaltungsvorlage für ein Seitenlayout wurde geändert
<a name="PageLayoutChanged"> </a>


### Meldung

 **Diese Gestaltungsvorlage des Seitenlayouts hat sich geändert, was auf Ihrer Website zu Inkonsistenzen führt. Klicken Sie hier, um die Bereiche Ihres Seitenlayouts zu ändern, die Bereiche der Gestaltungsvorlage repräsentieren.**
  
    
    

### Lösung

Damit ein Seitenlayout mit einer bestimmten Gestaltungsvorlage funktioniert, müssen beide den gleichen Satz von Inhaltsplatzhaltern enthalten. Wenn Sie ein Seitenlayout basierend auf einer bestimmten Gestaltungsvorlage erstellen und dann diese HTML-Gestaltungsvorlage bearbeiten, wird diese Meldung angezeigt. Auch wenn Sie wissen, dass durch Änderungen an der Gestaltungsvorlage keine Inhaltsplatzhalter hinzugefügt oder entfernt wurden, sollten Sie die Inhaltsbereiche des Seitenlayouts aktualisieren, um eine Vorschau aller Änderungen der Gestaltungsvorlage anzuzeigen, die sich auf das Seitenlayout auswirken.
  
    
    

## Zurücksetzen der Vorschau
<a name="ResetPreview"> </a>


### Meldung

 **Bei Ihrer Gestaltungsvorlage (Ihrem Seitenlayout) sind keine Warnungen oder Fehler vorhanden. Setzen Sie die Vorschau auf den ursprünglichen Zustand zurück.**
  
    
    

### Erläuterung

Diese Meldung bestätigt, dass keine Fehler oder Probleme beim Konvertierungsprozess aufgetreten sind. Allerdings können Sie bei der Vorschau einer Seite von dieser bestimmten Seite weg navigieren oder die Vorschau auf andere Weise ändern. In diesem Fall können Sie im Meldungsbereich immer **Vorschau zurücksetzen** auswählen. Dadurch wird die Vorschau aktualisiert, sodass die gerade bearbeitete Gestaltungsvorlage bzw. das bearbeitete Seitenlayout und die in der Option **Vorschau-Seite ändern** in der oberen linken Ecke ausgewählte Seite verwendet werden.
  
    
    

## Ändern der Vorschauseite
<a name="ChangePreviewPage"> </a>


### Meldung

 **In der Vorschau wird derzeit die Gestaltungsvorlage (das Seitenlayout) ohne Inhalt angezeigt. Über das Menü oben können Sie die Seite in der Vorschau ändern.**
  
    
    

### Erläuterung

Diese Meldung wird angezeigt, wenn Sie keine SharePoint 2013-Liveseite verwenden, um eine Vorschau der Gestaltungsvorlage oder des Seitenlayouts anzuzeigen. Wenn Sie z. B. ein Seitenlayout in der Vorschau anzeigen, können Sie in der linken oberen Ecke auf **Vorschau-Seite ändern** klicken und dann eine bestimmte Inhaltsseite für die Vorschau mit dem Seitenlayout auswählen. So können Sie das Seitenlayout mit tatsächlichem Seiteninhalt in den Seitenfeldern anzeigen. Wenn die Vorschau nur die Positionen von **ContentPlaceHolderMain** oder Seitenfeldern anzeigen soll, können Sie mit **Vorschau-Seite ändern** jederzeit wieder in eine generische Vorschau wechseln.
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Entwickeln des Website-Designs in SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: ändern die Vorschauseite in SharePoint 2013-Design-Manager](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md)
    
  

