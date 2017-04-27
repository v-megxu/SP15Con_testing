---
title: Aktualisieren benutzerdefinierter Designs und CSS-Dateien auf SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8d1a4e3a-ae6f-41a5-bd80-3398ba541207
---


# Aktualisieren benutzerdefinierter Designs und CSS-Dateien auf SharePoint 2013
Informationen zu Problemen beim Upgrade von Designanpassungen, z. B. benutzerdefinierten CSS-Dateien und benutzerdefinierten Gestaltungsvorlagen, und zum Aktualisieren von Anpassungen für die Verwendung in SharePoint 2013.
## Einführung in Designanpassungen und aktualisierte SharePoint 2013-Websites
<a name="Intro"> </a>

Die Designerfahrung in SharePoint 2013 wurde neu gestaltet, um den Anpassungsvorgang von Websites durch Änderung des Websitelayouts, der Farbpalette, des Schriftartschemas und des Hintergrundbilds zu vereinfachen. Die Design-Benutzeroberfläche wurde neu gestaltet und enthält nun eine Reihe neuer Dateiformate, die im Zusammenhang mit Designs stehen. Benutzerdefinierte Designs, die in SharePoint 2010 erstellt wurden, können auf SharePoint 2013-Websites nicht verwendet werden. Sie müssen diese neu erstellen. Benutzerdefinierte CSS-Dateien auf SharePoint 2013-Websites müssen möglicherweise aktualisiert werden, damit Sie für neue Gestaltungsvorlagen, Farbmodule und andere Designänderungen verwendet werden können.
  
    
    
Dieser Artikel beschreibt die Probleme, die beim Verwenden benutzerdefinierter SharePoint 2010-Designs, SharePoint 2010 CSS-Dateien und benutzerdefinierter CSS-Dateien mit der neuen Designerfahrung auftreten können. Darüber hinaus werden Änderungen erläutert, die Sie an Ihren benutzerdefinierten SharePoint 2010-Designs, SharePoint 2010 CSS-Dateien und benutzerdefinierten CSS-Dateien vornehmen müssen, um sie auf SharePoint 2013-Websites zu verwenden.
  
    
    

> **HINWEIS**
> SharePoint 2010-Designs können auf Websitesammlungen verwendet werden, die im 2010-Modus ausgeführt werden. Weitere Informationen zu den Websitesammlungsmodi finden Sie unter  [Planen der Upgrades von Websitesammlungen in SharePoint 2013](http://technet.microsoft.com/de-de/library/ff191199.aspx) oder [Planen des Upgrades auf SharePoint 2013](https://technet.microsoft.com/de-de/library/cc303429.aspx). 
  
    
    

Weitere Informationen zu Designs finden Sie unter  [Übersicht über Designs für SharePoint 2013](themes-overview-for-sharepoint-2013.md).
  
    
    

## Benutzerdefinierte SharePoint 2010-Designs in SharePoint 2013
<a name="themes"> </a>

Designs wurden in SharePoint 2010 als THMX-Dateien gespeichert. In SharePoint 2013, gibt es im Zusammenhang mit Designs eine Reihe neuer Dateiformate. Farbpaletten und Schriftartschemas werden in separaten XML-Dateien gespeichert (SPCOLOR- und SPFONT-Dateien). 
  
    
    
Sie können kein Upgrade einer THMX-Datei von SharePoint 2010 auf SharePoint 2013 durchführen. Wenn Sie ein benutzerdefiniertes Design auf Ihre SharePoint 2010-Website angewendet haben, bleiben beim Upgrade auf SharePoint 2013, die Designdateien erhalten, das Design wird jedoch nicht mehr auf die Website angewendet und die Website wird auf das Standarddesign zurückgesetzt. Wenn Sie Ihre SharePoint 2010-Designanpassungen auf SharePoint 2013-Websites verwenden möchten, müssen Sie sie mithilfe der Anleitung zur SharePoint 2013-Designerstellung neu erstellen.
  
    
    
Weitere Informationen zum Erstellen von Designanpassungen finden Sie unter  [Vorgehensweise: Bereitstellen eines benutzerdefinierten Designs in SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md) und [Farbpaletten und Schriftarten in SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md). Sie können auch das SharePoint-Farbpalettentool zum Erstellen von SharePoint-Designs verwenden. Sie können  [das SharePoint-Farbpalettentool](http://www.microsoft.com/en-us/download/details.aspx?id=38182) im Microsoft Download Center herunterladen.
  
    
    

> **TIPP**
> Sie können eine THMX-Datei in PowerPoint öffnen, um nachzuschauen, wie die Farben im benutzerdefinierten Design definiert sind, und dann das Farbpalettentool zum erneuten Erstellen der Farben als Farbpalettendatei (SPCOLOR-Datei) verwenden. Eine Farbpalette ist eine Kombination aus Farben, die auf einer SharePoint-Website verwendet werden. 
  
    
    

Sie können auch eins der vorinstallierten der SharePoint 2013-Designs verwenden. Weitere Informationen finden Sie unter  [Auswählen eines Designs für Ihre Veröffentlichungswebsite](http://office.microsoft.com/de-de/office365-sharepoint-online-enterprise-help/choose-a-theme-for-your-publishing-site-HA102891580.aspx?CTT=1) auf Office.com.
  
    
    

## Aktualisieren angepasster Gestaltungsvorlagen
<a name="MasterPages"> </a>

Bei einem Upgrade einer SharePoint 2010-Website auf SharePoint 2013 wird die Website zum Verwenden der Standardgestaltungsvorlage für SharePoint 2013 konfiguriert. Wenn Sie eine benutzerdefinierte Gestaltungsvorlage für Ihre SharePoint 2010-Website verwendet haben, ist die weiterhin auf der Website vorhanden, und Sie können sie auf die SharePoint 2013-Website anwenden. Sie können die SharePoint-Benutzeroberfläche oder die **SPWeb**-Klasse verwenden, um die benutzerdefinierte Gestaltungsvorlage auf die aktualisierte Website anzuwenden. Weitere Informationen zum Ändern von Gestaltungsvorlagen finden Sie unter  [Vorgehensweise: Anwenden einer Gestaltungsvorlage auf eine Website in SharePoint 2013](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md).
  
    
    
Beachten Sie Folgendes, bevor Sie sich zum Anwenden der benutzerdefinierten SharePoint 2010Gestaltungsvorlage auf die aktualisierte SharePoint 2013-Website entscheiden:
  
    
    

- **Wenn die benutzerdefinierte Gestaltungsvorlage von benutzerdefinierten CSS-Dateien abhängig ist:** Beim Anwenden der benutzerdefinierten Gestaltungsvorlage auf die aktualisierte Website, wird die Website auf das standardmäßige 2010-Design zurückgesetzt. Sie können jedoch ein SharePoint 2013-Design auf die Website anwenden.
    
    Wenn Sie die benutzerdefinierte Gestaltungsvorlage und die benutzerdefinierten CSS-Dateien mit der SharePoint 2013-Designerfahrung verwenden möchten, müssen Sie die CSS-Dateien aktualisieren, um die neuen SharePoint 2013-Farbmodule zu verwenden. Wenn Sie über die Design-Benutzeroberfläche auf die benutzerdefinierte Gestaltungsvorlage zugreifen möchten, müssen Sie auch eine Gestaltungsvorlagen-Vorschaudatei erstellen. Weitere Informationen finden Sie unter  [Gewusst wie: Erstellen einer Gestaltungsvorlagen-Vorschaudatei in SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
- **Wenn die benutzerdefinierte Gestaltungsvorlage von SharePoint 2010-CSS-Dateien abhängig ist:** Die CSS-Dateien wurden in SharePoint 2013 im Vergleich zu SharePoint 2010 erheblich geändert. In vielen Fällen müssen Sie die Gestaltungsvorlage für die Verwendung mit den neuen Klassen überarbeiten, bevor Sie erfolgreich auf die aktualisierte Website angewendet werden kann. Weitere Informationen zu CSS-Klassen finden Sie im Abschnitt **Verwenden von Hostweb-CSS-Dateien in Apps für SharePoint** in den [Designrichtlinien für die Benutzerfreundlichkeit von Add-Ins für SharePoint](http://msdn.microsoft.com/library/a4a8f53c-27d7-43dc-b6db-aa7b1f1c7d45%28Office.15%29.aspx).
    
  

## SharePoint 2010-CSS- und benutzerdefinierte CSS-Dateien
<a name="CSS"> </a>

Unveränderte SharePoint 2010-CSS-Dateien und benutzerdefinierte CSS-Dateien können auf SharePoint 2013-Websites nicht verwendet werden. Im Folgenden werden die Änderungen in SharePoint 2013 beschrieben, die für SharePoint 2010-CSS- und benutzerdefinierte CSS-Dateien gelten:
  
    
    

- **Farbmodule**. Die Anzahl der verfügbaren Farbmodule wurde in SharePoint 2013 wesentlich erhöht. Sie müssen die Farbmodule in SharePoint 2010-CSS-Dateien aktualisieren, bevor sie in der neuen Designerfahrung verwendet werden können. Weitere Informationen finden Sie im Abschnitt  [Zuordnen von Farbplätzen](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots) unter [Farbpaletten und Schriftarten in SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md).
    
  
- **Schriftartmodule**. Sie sollten die Liste der verfügbaren Schriftartmodule prüfen und sicherstellen, dass die CSS-Dateien, die Sie in SharePoint 2013 verwenden möchten, die richtigen Schriftartmodule verwenden. Weitere Informationen finden Sie im Abschnitt  [Schriftartenplätze](color-palettes-and-fonts-in-sharepoint-2013.md#fontSlot) unter [Farbpaletten und Schriftarten in SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md).
    
  
- **Neue Anmerkung**. SharePoint 2013 verfügt über eine neue Anmerkung, mit der Sie das Hintergrundbild ersetzen können. Weitere Informationen finden Sie unter  [Gewusst wie: Benutzerdefinierte CSS-Dateien in SharePoint 2013 designfähig gestalten](how-to-make-custom-css-files-themable-in-sharepoint-2013.md).
    
  
- **Neue Klassen**. Möglicherweise müssen Sie die CSS-Dateien für die Verwendung mit den neuen Klassen in SharePoint 2013 aktualisieren. Weitere Informationen zu CSS-Klassen (auch CSS-Formatvorlagen genannt) finden Sie im Abschnitt **Verwenden von Hostweb-CSS-Dateien in Apps für SharePoint** in den [Designrichtlinien für die Benutzerfreundlichkeit von Add-Ins für SharePoint](http://msdn.microsoft.com/library/a4a8f53c-27d7-43dc-b6db-aa7b1f1c7d45%28Office.15%29.aspx).
    
  

## Zusätzliche Ressourcen
<a name="addresources"> </a>


-  [Übersicht über Designs für SharePoint 2013](themes-overview-for-sharepoint-2013.md)
    
  
-  [Gewusst wie: Erstellen einer Gestaltungsvorlagen-Vorschaudatei in SharePoint 2013](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Bereitstellen eines benutzerdefinierten Designs in SharePoint 2013](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [Farbpaletten und Schriftarten in SharePoint 2013](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [SharePoint-Teamblog: Beweisen Sie Stil mit SharePoint-Designs](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 Design Manager - Branding- und Designfunktionen](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

