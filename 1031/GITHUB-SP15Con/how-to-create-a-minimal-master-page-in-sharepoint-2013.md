---
title: Vorgehensweise Erstellen eine minimale Gestaltungsvorlage in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 634aa471-07e1-41d6-aa80-27f7ef7e9dc8
---


# Vorgehensweise: Erstellen eine minimale Gestaltungsvorlage in SharePoint 2013
Eine minimale Gestaltungsvorlage enthält nur die Seitenelemente, die zum Rendern der Seite im Browser ordnungsgemäß SharePoint 2013 erforderlich. Mit Entwurfs-Manager können Sie schnell erstellen eine minimale Gestaltungsvorlage ohne zuvor zum Entwerfen und Konvertieren einer HTML-Datei.
## Einführung in die minimale Gestaltungsvorlage
<a name="Introduction"> </a>

Mit Entwurfs-Manager können Sie eine typische HTML-Datei in eine Gestaltungsvorlage SharePoint 2013 konvertieren. Aber, wenn Sie nicht über eine vordefinierte Modell verfügen, Sie können weiterhin schnell starten von Grund auf neu, indem Sie eine minimale Gestaltungsvorlage erstellen. Die minimale Gestaltungsvorlage enthält nur die Seitenelemente, die von SharePoint zum Rendern der Seite im Browser erforderlich.
  
    
    
Wenn Sie eine minimale Gestaltungsvorlage erstellen, erstellt Entwurfs-Manager die Master-Datei und eine verknüpfte HTML-Datei, damit Sie weiterhin mit der HTML-Datei arbeiten können, falls gewünscht. Arbeiten mit einer minimale Gestaltungsvorlage ist genau die gleiche wie das Arbeiten mit einer Gestaltungsvorlage, die Sie von einer HTML-Datei konvertieren. Die HTML-Datei und Gestaltungsvorlage sind verknüpft, sodass diese Änderungen an der zugeordneten Masterseite, wenn Sie bearbeiten und speichern Sie die HTML-Datei synchronisiert werden. Und die HTML-Datei enthält spezielle Arten von Markup, die Synchronisierung mit der möglichen Master-Datei vornehmen. Weitere Informationen über diese Zuordnung und diese Arten von Markup finden Sie unter  [Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md).
  
    
    
Beginnend mit eine minimale Gestaltungsvorlage ist hilfreich, wenn:
  
    
    

- Sie möchten schnell neu starten, und klicken Sie dann erstellen, den Entwurf der HTML-Datei, die die minimale Gestaltungsvorlage anstelle von beginnend mit einem Modell HTML-Datei zugeordnet ist.
    
  
- Sie schnell testen möchten oder Prototyp Designelement, die eine funktionsfähige SharePoint-Gestaltungsvorlage erforderlich sind. Erstellen eine minimale Gestaltungsvorlage erfordern beispielsweise nicht Vorbereiten einer HTML-Datei für die Konvertierung oder Auflösen von Fehlern Preview, die aus Markup, das der HTML-Datei nicht gültig ist. Dies bedeutet, dass Sie sofort mit der serverseitigen Vorschau oder Codeausschnittkatalog arbeiten können.
    
  
- Die Master-Datei direkt entwickelt werden soll. Wenn Sie ein ASP.NET-Entwickler oder SharePoint-Entwickler sind, können Sie eine minimale Gestaltungsvorlage erstellen, entfernen Sie die Zuordnung zwischen der HTML-Datei und die Master-Datei durch Deaktivieren des Kontrollkästchens **Verknüpfte Datei** in den Eigenschaften der HTML-Datei und dann arbeiten direkt mit der Master-Datei.
    
  

## Erstellen Sie eine minimale Gestaltungsvorlage
<a name="CreateMinimalMaster"> </a>


  
    
    

### Erstellen Sie eine minimale Gestaltungsvorlage


1. Navigieren Sie zu Ihrer Veröffentlichungswebsite.
    
  
2. Wählen Sie oben rechts auf der Seite **Einstellungen** und dann **Entwurfs-Manager** aus.
    
  
3. Wählen Sie im Entwurfs-Manager im linken Navigationsbereich **Gestaltungsvorlagen bearbeiten**.
    
  
4. Wählen Sie **erstellen eine minimale Gestaltungsvorlage** aus.
    
  
5. Klicken Sie im Dialogfeld **Erstellen einer Gestaltungsvorlage** Geben Sie einen Namen für die Gestaltungsvorlage, und wählen Sie dann auf **OK**.
    
    Zu diesem Zeitpunkt erstellt SharePoint eine Master-Datei und eine zugeordnete HTML-Datei mit dem gleichen Namen in der Master Page Gallery.
    
    Im Entwurfs-Manager wird Ihre HTML-Datei nun mit der **Konvertierung erfolgreich** angezeigt, in der Spalte Status angezeigt.
    
  
6. Führen Sie den Link in der Spalte Status eine Vorschau die Datei.
    
    Die Preview-Seite ist eine serverseitige Livevorschau der Masterseite.
    
    Weitere Informationen zur Vorschau der Gestaltungsvorlage mit unterschiedlichen Seiten finden Sie unter  [Vorgehensweise: ändern die Vorschauseite in SharePoint 2013-Design-Manager](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md).
    
    Die Vorschauseite enthält außerdem einen Link **Ausschnitten** in der oberen rechten Ecke. Dieser Link öffnet im Codeausschnittkatalog, wo Sie beginnen können statisch oder Modell Steuerelemente in Ihrem Entwurf mit dynamischen SharePoint-Steuerelemente ersetzen. Weitere Informationen finden Sie unter [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md).
    
    Nach erfolgreicher Vorschau Ihrer Gestaltungsvorlage sehen Sie das **<div>**-Tag, das Ihrer HTML-Datei hinzugefügt wird. Sie müssen ggf. einen Bildlauf nach unten auf der Seite durchführen, um das **<div>**-Tag zu sehen.
    
    Dieses **<div>**-Tag ist der Hauptinhaltsblock. Es befindet sich im Inhaltsplatzhalter **ContentPlaceHolderMain**. Wenn ein Benutzer zur Laufzeit Ihre Website durchstöbert und eine Seite anfordert, wird dieser Inhaltsplatzhalter mit Inhalten aus einem Seitenlayout gefüllt, das Inhalte in einem übereinstimmenden Inhaltsbereich enthält. Sie müssen dieses **<div>**-Tag an der Stelle positionieren, an der Ihre Seitenlayouts in der Gestaltungsvorlage angezeigt werden sollen.
    
  
7. Sie können die HTML-Datei bearbeiten, die sich direkt auf dem Server mit einem HTML-Editor zu öffnen und Bearbeiten von HTML-Datei in ein zugeordnetes Laufwerk befindet. Jedes Mal, wenn Sie die HTML-Datei speichern, werden alle Änderungen mit der zugehörigen Master-Datei synchronisiert. Weitere Informationen finden Sie unter  [Gewusst wie: Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
    
  
8. Nur bei der Master-Datei und nicht die HTML-Datei verwendet wird, müssen Sie die Zuordnung zwischen den beiden Dateien aufteilen. Wählen Sie im Entwurfs-Manager auf der Seite Gestaltungsvorlagen bearbeiten die HTML-Datei, öffnen Sie das Menü **Eigenschaften**, und wählen Sie dann auf **Eigenschaften bearbeiten**. Klicken Sie auf die Registerkarte **Bearbeiten** deaktivieren Sie das Kontrollkästchen **Datei verknüpft ist**, und wählen Sie dann auf **Speichern**.
    
    Informationen zum Unterteilen der Zuordnung können Sie direkt mit der Master-Datei arbeiten und die Änderungen zu speichern, ohne dass sie durch die HTML-Datei vorgenommenen Änderungen überschrieben. Sie können diese Zuordnung zu einem beliebigen Zeitpunkt wiederherstellen. Wenn Sie die Zuordnung wiederherstellen, wird die verknüpfte HTML-Datei mit der Master-Datei synchronisieren und überschreiben.
    
  

## Verstehen der verknüpften HTML-Datei
<a name="UnderstandHTML"> </a>

Wenn Sie eine minimale Gestaltungsvorlage erstellen, eine HTML-Datei wird erstellt, das die Master-Datei zugeordnet ist, und diese HTML-Datei enthält viele Zeilen von Markup, die für die Funktionsweise von SharePoint 2013 spezifisch sind. Sie können die meisten dieses Markup ignorieren, und die meisten davon wird nicht angezeigt im endgültigen Markup Ihrer Website Wenn Sie die Datenquelle im Browser anzeigen, aber dieses Markup ist ein entscheidender Faktor, zum Synchronisieren von Änderungen aus der HTML-Datei an die Master-Datei, SharePoint 2013 tatsächlich verwendet. Jedes Mal, wenn Sie eine Änderung in Ihre HTML-Datei speichern ermöglicht diese SharePoint-Markup für dieselbe Änderung an der Datei zugeordneten Master im Hintergrund vorgenommen werden sollen. Weitere Informationen finden Sie in die Beispielen Markup in  [Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md).
  
    
    

## Zusätzliche Ressourcen
<a name="Additional"> </a>


-  [Übersicht über den Entwurfs-Manager in SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Konvertieren einer HTML-Datei in eine Gestaltungsvorlage in SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Codeausschnitte des SharePoint 2013-Entwurfs-Managers](sharepoint-2013-design-manager-snippets.md)
    
  

