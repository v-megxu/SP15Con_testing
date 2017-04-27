---
title: Gewusst wie Anwenden von Formatvorlagen auf Seitenfelder in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: e227613d-0e4d-4312-924d-bb55e1fe4293
---


# Gewusst wie: Anwenden von Formatvorlagen auf Seitenfelder in SharePoint 2013
In einem Seitenlayout können Sie Formate auf ein Seitenfeld anwenden. Diese Formate werden dann auf alle Inhalte angewendet, die von Inhaltsautoren hinzugefügt werden, wenn sie eine Seite mithilfe dieses Seitenlayouts erstellen. Darüber hinaus stehen Ihnen weitere Optionen zur Verfügung, mit denen Sie steuern können, wie Inhalte in einem RichHtmlField-Seitenfeld formatiert werden.
## Einführung in das Anwenden von Formatvorlagen für Seitenfelder
<a name="Introduction"> </a>

Als Designer benötigen Sie die ultimative Kontrolle über die Positionierung und Formatierung von Seitenfeldern in einem Seitenlayout und auf allen Seiten, die mit diesem Seitenlayout erstellt wurden. Wenn Inhaltsautoren Seiten von einem Browser erstellen, können sie Seitenfelder auf der Seite nicht verschieben oder die von Ihnen angegebenen Formatvorlagen überschreiben. So wird sichergestellt, dass Ihr Branding über alle Seiten der Website konsistent bleibt.
  
    
    
Wenn Sie Formatvorlagen auf Seitenfelder anwenden, gibt es zwei grundlegende Kategorien von Feldtypen, die berücksichtigt werden müssen:
  
    
    

- **Andere Feldtypen als RichHtmlField** Die Seitenfelder, aus denen ein Seitenlayout besteht, entsprechen dem Inhaltstyp für dieses Seitenlayout. Ein Seitenfeld kann vielen Typen entsprechen, z. B. einer einzelnen Textzeile (TextField) oder mehreren Textzeilen (NoteField). Als Designer können Sie Formatvorlagen für alle diese Seitenfelder auf dieselbe Weise anwenden, indem Sie Formatvorlagen direkt auf das Seitenfeld im Seitenlayout anwenden.
    
  
- **RichHtmlField** Das Rich-HTML-Feldsteuerelement (das auch als Publishing-HTML-Feld bezeichnet wird) ist eins der leistungsstärksten und am häufigsten verwendete Steuerelemente in Seitenlayouts. Standardmäßig verwenden Inhaltsautoren in einem Rich-HTML-Feld das Menüband zum Formatieren und Anwenden von Formatvorlagen auf Inhalte sowie zum Einfügen von Tabellen, Medien wie Bilder und Videos sowie Webparts. Dieser Feldtyp ist hilfreich, wenn Sie Inhaltsautoren die Freiheit geben möchten, Inhalte innerhalb der Parameter hinzuzufügen und zu formatieren, die Sie steuern können. Sie können ein RichHtmlField auf zwei Arten steuern:
    
  - **Erstellen eines benutzerdefinierten Stylesheets** Standardmäßig stammen die Formatvorlagen, die auf dem Menüband eines RichHtmlField verfügbar sind, aus einem Stylesheet namens HtmlEditorStyles.css. Sie können die Eigenschaft **PrefixStyleSheet** für diesen Codeausschnitt konfigurieren, damit auf dem Menüband Ihre eigenen benutzerdefinierten Formatvorlagen für Inhaltsautoren angezeigt werden.
    
  
  - **Konfigurieren der Allow-Eigenschaften** Ein Codeausschnitt für ein RichHtmlField hat 28 verfügbare Eigenschaften, die mit **Allow** beginnen, und Sie können diese Eigenschaften verwenden, um bestimmte Befehle oder Gruppen von Befehlen auf dem Menüband nicht für Inhaltsautoren verfügbar zu machen. Wenn Sie z. B. die Eigenschaft **AllowFontsMenu** auf **False** festlegen, können Autoren Schriftartmenü auf dem Menüband nicht verwenden, um zu ändern, welche Schriftart auf Text angewendet wird. Stattdessen können sie nur die von Ihnen angegebenen CSS-Formatvorlagen verwenden.
    
  
Für alle Arten von Seitenfeldern, einschließlich RichHtmlField, bestimmt der Designer, wie der Inhalt formatiert wird. Sie können RichHtmlField verwenden, um Inhaltsautoren die Freiheit zu geben, attraktive Inhalte einzufügen und Formatvorlagen anzuwenden. Sie behalten dennoch die ultimative Kontrolle darüber, welche Inhalte hinzugefügt und welche Formatvorlagen angewendet werden können.
  
    
    

## Anwenden von Formatvorlagen auf andere Seitenfelder als RichHtmlField
<a name="Applying"> </a>

Mit einem Seitenfeld-Steuerelement definieren Sie die Formate des Inhalts. Autoren können einer Seite Inhalte hinzufügen, doch der Designer steuert, wie diese Inhalte mittels CSS gerendert werden, die auf diese Steuerelemente angewendet werden.
  
    
    
Im HTML-Seitenlayout ist jedes Seitenfeld in ein **<div>**-Tag eingeschlossen. Zum Anwenden einer Formatvorlage auf ein Seitenfeld können Sie einfach eine Formatvorlage zu **<div>** hinzufügen, z. B. `<div style="font-weight:bold"`. Aber das allgemeinere und hilfreichere Szenario ist, ein **id** zu **<div>** für jedes Seitenfeld im Seitenlayout hinzuzufügen und dann die **id** als Auswahl für Formatvorlagen zu verwenden, die sich in einem externen Stylesheet befinden. Auf diese Weise können Sie, wenn Sie mehrere Gerätekanäle haben und jeder Kanal über ein eigenes Stylesheet verfügt, verschiedene Formatvorlagen für jedes Seitenfeld für jeden Kanal anwenden. Das folgende Seitenfeld vom Typ TextField (auch als „mehrere Textzeilen" bezeichnet) hat z. B. möglicherweise nur ein **id**-Attribut für das **<div>**-Tag.
  
    
    



```HTML

<div id="ShortSummaryPageField">
<!--CS: Start Page Field: ShortSummary Snippet-->
<!--SPM:<%@Register Tagprefix="PageFieldNoteField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<PageFieldNoteField:NoteField FieldName="a5249942-2dc5-4917-85e2-661d019ad548" runat="server">-->
<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">ShortSummary</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field">ShortSummary field value.</div></div></div><!--PE: End of READ-ONLY PREVIEW-->
<!--ME:</PageFieldNoteField:NoteField>-->
<!--CE: End Page Field: ShortSummary Snippet-->
</div>
```

Weitere Informationen dazu, wo Formatvorlagen und Formatvorlagenverweise für ein Seitenlayout eingefügt werden sollen, finden Sie unter  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
  
    
    

## Deaktivieren von Optionen auf dem Menüband eines RichHtmlField
<a name="Disabling"> </a>

Wenn Inhaltsautoren eine Seite erstellen oder bearbeiten und dann Inhalt zu einem RichHtmlField mit einem Browser hinzufügen, können sie die Befehle auf dem Menüband für dieses Feld verwenden, um es zu formatieren, eine Formatvorlage anzuwenden oder attraktive Inhalte und Medien hinzuzufügen. 
  
    
    
Im Codeausschnittkatalog können Sie die Eigenschaften für ein Seitenfeld vom Typ RichHtmlField so konfigurieren, dass bestimmte Befehle oder Gruppen von Befehlen auf dem Menüband nicht für Autoren verfügbar sind. Wenn Sie z. B. die Eigenschaft **AllowFontSizesMenu** auf **False** festlegen, können Sie die **Font Size**-Gruppe auf dem Menüband deaktivieren. Durch Festlegen der Eigenschaft **AllowFonts** auf **False** können Sie die gesamte Gruppe **Schriftart** auf dem Menüband deaktivieren.
  
    
    
Wenn Sie diese Eigenschaften im Codeausschnittkatalog konfiguriert haben und dann den Codeausschnitt aktualisieren, werden die Eigenschaften im Codeausschnittmarkup innerhalb des  `<!--MS:>`-Kommentars angezeigt.
  
    
    



```HTML

<div data-name="Page Field: ArticleBody">
<!--CS: Start Page Field: ArticleBody Snippet-->
<!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<PageFieldRichHtmlField:RichHtmlField runat="server" AllowFonts="False" FieldName="db3168db-8778-4fb6-a48f-57f598497388">-->
<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div id="ctl02_label" style="display:none">ArticleBody</div><div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label"><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">ArticleBody</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field">ArticleBody field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div></div></div></div>
<!--PE: End of READ-ONLY PREVIEW-->
<!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
<!--CE: End Page Field: ArticleBody Snippet-->
</div>
```


> **HINWEIS**
> Wenn Sie **AllowFonts** auf **False** festlegen, können Inhaltsautoren weiterhin Tastenkombinationen wie STRG + B (Fett) zum Formatieren von Text verwenden. Um zu verhindern, dass Autoren beliebige Formatvorlagen zu Text hinzufügen, können Sie **AllowTextMarkup** auf **False** festlegen. Wenn Inhaltsautoren mit dieser Einstellung versuchen, Inhalte zu speichern, die auf Text angewendete Formatvorlagen enthalten, gibt der HTML-Editor im Browser einen Fehler zurück und fordert den Autor auf, das ungültige Markup zu entfernen.
  
    
    

Ein RichHtmlField-Seitenfeld enthält 28 verschiedene **Allow**-Eigenschaften. Weitere Informationen dazu, was die jeweiligen Eigenschaften steuern, finden Sie unter  [RichHtmlField-Eigenschaften](http://msdn.microsoft.com/de-de/library/microsoft.sharepoint.publishing.webcontrols.richhtmlfield_properties) Weitere Informationen zum Hinzufügen und Konfigurieren von Codeausschnitten finden Sie unter [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md).
  
    
    

## Steuern der in einem RichHtmlField verfügbaren Formatvorlagen
<a name="Controlling"> </a>

In einem RichHtmlField können Inhaltsautoren Optionen auf dem Menüband verwenden, um Inhalte zu formatieren. Diese Formatierungsoptionen werden mithilfe von CSS implementiert, und diese Formatvorlagen sind in einem SharePoint-Stylesheet namens HtmlEditorStyles.css definiert, das sich auf dem Server an einem der folgenden Speicherorte befindet:
  
    
    

- C:\\Programme\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\STYLES 
    
  
- C:\\Programme\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\FEATURES\\PublishingLayouts\\en-us
    
  
Da das RichHtmlField im Browser CSS verwendet, um die Formatvorlagen zu implementieren, können Sie Ihre eigenen Formatvorlagen erstellen, die konsistent mit dem Branding Ihrer Website sind, und dann diese Formatvorlagen für Inhaltsautoren auf dem Menüband verfügbar machen. Wenn Sie geringfügige Änderungen an den Standardformatvorlagen vornehmen möchten, können Sie eine vorhandene Formatvorlage aus HtmlEditorStyles.css in das Stylesheet kopieren, auf das vom Seitenlayout verwiesen wird, und dann diese Formatvorlage bearbeiten, indem Sie die CSS-Eigenschaften und -Werte (jedoch nicht die Auswahl) ändern. Sie können Standardformatvorlagen auch auf dem Menüband ausblenden, indem Sie sie in Ihr Stylesheet kopieren und anschließend  `display:none` festlegen.
  
    
    
Zum Implementieren benutzerdefinierter Formatvorlagen können Sie auch ein Stylesheet von Grund auf neu erstellen, indem Sie die Eigenschaft **PrefixStyleSheet** für den RichHtmlField-Codeausschnitt ändern. Standardmäßig ist diese Eigenschaft auf **ms-rte** festgelegt, und die Formatvorlagen im Standardstylesheet HtmlEditorStyles.css beginnen jeweils mit dem folgenden Präfix - z. B.:
  
    
    



```HTML

H1. ms-rteElement-H1
{
-ms-name:"Heading 1";
-ms-element:"true";
}
```

Wenn Sie den Wert der Eigenschaft **PrefixStyleSheet** ändern, sind keine der vorhandenen **ms-rte**-Formatvorlagen im Rich-HTML-Editor verfügbar, und nur erstellte Formatvorlagen, die das neue Präfix verwenden, stehen für Inhaltsautoren zur Verfügung. Das bedeutet, dass Sie, wenn Sie einige der Standardformatvorlagen verwenden möchten, diese in Ihr Stylesheet kopieren und ändern müssen, dass sie das neue Präfix verwenden.
  
    
    

> **HINWEIS**
> Die Eigenschaft **PrefixStyleSheet** wird für jedes RichHtmlField-Seitenfeld definiert, aber mehrere Seitenfelder können denselben Wert für diese Eigenschaft verwenden. Wenn also mehrere Seitenlayouts auf dasselbe Stylesheet verweisen, können mehrere RichHtmlFields in diesen Seitenlayouts dasselbe Formatvorlagenpräfix haben und auf dieselben Formatvorlagen verweisen.
  
    
    


### So definieren Sie eine neue Liste von Formatvorlagen für ein RichHtmlField


1. Wechseln Sie zu Ihrer Veröffentlichungswebsite.
    
  
2. Wählen Sie in der rechten oberen Ecke der Seite **Einstellungen** und dann **Entwurfs-Manager**.
    
  
3. Wählen Sie im Entwurfs-Manager im linken Navigationsbereich **Seitenlayouts bearbeiten** aus.
    
  
4. Wählen Sie das Seitenlayout aus, auf dem sich das RichHtmlField-Seitenfeld befinden soll.
    
  
5. Wählen Sie in der oberen rechten Ecke der serverseitigen Vorschau **Codeausschnittkatalog** aus.
    
  
6. Wählen Sie auf dem Menüband **Seitenfelder** und dann ein Seitenfeld vom Typ **RichHtmlField** aus.
    
  
7. Erweitern Sie im Eigenschaftenraster den Abschnitt **Verschiedenes**, und ändern Sie die Eigenschaft **PrefixStyleSheet** auf einen anderen Wert als **ms-rte** - z. B. auf **customstyle**.
    
    > **WICHTIG**
      > Dieser Wert muss in Kleinbuchstaben eingegeben werden. 
8. Wählen Sie **Aktualisieren** aus.
    
  
9. Wählen Sie auf der linken Seite des Codeausschnittkatalogs **In die Zwischenablage kopieren** aus.
    
  
10. Öffnen Sie im zugeordneten Netzlaufwerk auf Ihrem Computer das HTML-Seitenlayout in Ihrem HTML-Editor.
    
    > **HINWEIS**
      > Weitere Informationen finden Sie unter  [Gewusst wie: Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md). 
11. Fügen Sie im HTML-Seitenlayout den HTML-Codeausschnitt in **PlaceHolderMain** ein.
    
  
12. Speichern Sie das HTML-Seitenlayout. Die Änderungen an der HTML-Datei werden mit dem zugehörigen ASPX-Seitenlayout synchronisiert.
    
    Wenn ein Inhaltsautor an diesem Punkt eine Seite auf der Basis dieses Seitenlayouts erstellt oder bearbeitet, sind keine Formatvorlagen auf dem Menüband des HTML-Editors verfügbar, da dieses bestimmte Seitenfeld nur Formatvorlagen verwendet, die mit dem neuen Präfix **customstyle** beginnen, aber diese Formatvorlagen wurden noch nicht definiert.
    
  
13. Navigieren Sie auf dem Server zum folgenden Speicherort, und öffnen Sie HtmlEditorStyles.css:
    
    C:\\Programme\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\STYLES
    
    Es ist nützlich, die Standardformatvorlagen anzuzeigen, zu verstehen, wie sie geschrieben werden, und möglicherweise einige davon wiederzuverwenden, indem Sie sie in Ihre Stylesheet kopieren und dann ändern. Wenn Sie dies tun, ersetzen Sie das Standard- **ms Rte** -Präfix durch Ihr eigenes Präfix.
    
    > **WICHTIG**
      > Ändern Sie nicht das Standardstylesheet HtmlEditorStyles.css. Dieses Stylesheet stellt die Formatvorlagen für jedes RichHtmlField in der Farm bereit. Darüber hinaus wird diese Datei möglicherweise durch Dienstupdates oder ein Upgrade überschrieben, sodass alle Änderungen verloren gehen. 
14. Erstellen Sie in einem Stylesheet eine Liste der neuen Formatvorlagen, die mit dem neuen Präfix beginnen.
    
    Wenn beispielsweise **customstyle** das neue Präfix ist, enthält Ihr Stylesheet möglicherweise die folgende Formatvorlage.
    


  ```HTML
  
H2.customstyleElement-H2
{
-ms-name:"Heading 2";
-ms-element:"true";
}
customstyleElement-H2
{
font-weight: bold;
font-family: Cambria;
font-size: 16pt;
} 

  ```


    Aus Gründen der Übersichtlichkeit werden der Klassenname und der Namen der Formatvorlage, der auf dem Menüband angezeigt wird, separat von Eigenschaften der Formatvorlage definiert. In diesem Beispiel ist **H2** die Elementauswahl für die Formatvorlage und **customstyleElement-H2** ist der Klassenname der Formatvorlage. Der Klassenname besteht aus zwei Teilen: **customstyle** ist das Präfix, das Sie für dieses Seitenfeld angegeben haben, und **Element** gibt an, dass diese Formatvorlage im Abschnitt **Seitenelemente** des Katalogs **Formatvorlagen** auf dem Menüband im HTML-Editor angezeigt wird. Die Eigenschaft **-ms-name** legt den Anzeigenamen fest, der für Inhaltsautoren im Formatvorlagenkatalog angezeigt wird.
    
    SharePoint ordnet eine Formatvorlage einem Menü oder Befehl auf dem Menüband zu, indem der Klassenname direkt nach dem Präfix analysiert und nach einer der folgenden Zeichenfolgen gesucht wird:
    
  - **Element**: Der Abschnitt „Seitenelemente" des Formatvorlagenkatalogs
    
  
  - **Style**: Der Abschnitt „Textformatvorlagen" des Formatvorlagenkatalogs
    
  
  - **FontSize**: Das Menü „Schriftgrad"
    
  
  - **ThemeFontFace**: Das Menü „Schriftart"
    
  
  - **ForeColor**: Das Menü „Schriftfarbe"
    
  
  - **BackColor**: Das Menü „Hervorhebungsfarbe"
    
  
  - **Image**: Das Menü „Grafik"
    
  
  - **Table**: Das Menü „Tabelle"
    
  
  - **Position**: Die Ausrichten-Schaltflächen in der Gruppe „Absatz"'
    
  

    Weitere Informationen dazu, wo sich Formatvorlagen für ein Seitenlayout befinden sollten, finden Sie unter  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  

## Zusätzliche Ressourcen
<a name="Additional"> </a>


-  [Übersicht über den Entwurfs-Manager in SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md)
    
  

