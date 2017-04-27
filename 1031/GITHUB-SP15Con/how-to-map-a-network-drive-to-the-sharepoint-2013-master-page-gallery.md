---
title: Gewusst wie Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog
ms.prod: SHAREPOINT
ms.assetid: 7d416f6e-2471-4d03-97ae-4e8d907784c6
---


# Gewusst wie: Zuordnen eines Netzlaufwerks zum SharePoint 2013-Gestaltungsvorlagenkatalog
In diesem Artikel erfahren Sie, wie Sie dem Gestaltungsvorlagenkatalog ein Netzlaufwerk zuordnen, damit Sie den Entwurfs-Manager zum Hochladen von Designdateien in SharePoint Server 2013 verwenden können.
Sie können mit einem beliebigen Webdesigntools oder HTML-Editor ein visuelles Design für Ihre Website erstellen und das Design anschließend mit dem Entwurfs-Manager in SharePoint importieren. Hierzu müssen Sie sicherstellen, dass die Dateien vom Designtool im Gestaltungsvorlagenkatalog der Website speichert, da dies der Speicherort ist, an dem SharePoint nach den Dateien sucht. Es wird empfohlen, dem Gestaltungsvorlagenkatalog ein Netzlaufwerk zuzuordnen, um das Speichern von Dateien am richtigen Speicherort zu erleichtern.
  
    
    

Suchen Sie zunächst den Speicherort des Gestaltungsvorlagenkatalogs.
### So suchen Sie den Speicherort des Gestaltungsvorlagenkatalogs


1. Starten Sie den Entwurfs-Manager auf der Website, für die Sie ein Design erstellen. (Wählen Sie z. B. im Menü **Einstellungen** die Option **Entwurfs-Manager**.)
    
    > **WICHTIG**
      > Wenn Ihre Website in SharePoint Online gehostet ist, achten Sie darauf, beim Anmelden bei der Website unter Verwendung Ihrer Office 365-Anmeldeinformationen das Kontrollkästchen **Angemeldet bleiben** zu aktivieren. Weitere Informationen finden Sie unter [Konfiguration und Problembehandlung für zugeordnete Netzlaufwerke, die eine Verbindung mit SharePoint Online-Websites in Office 365 für Unternehmen herstellen](http://support.microsoft.com/kb/2616712). 
2. Wählen Sie in der nummerierten Liste die Option **Designdateien hochladen** aus.
    
  
3. Die Seite "Entwurfs-Manager: Designdateien hochladen" enthält den Speicherort des Gestaltungsvorlagenkatalogs. Der Speicherort endet vermutlich mit  `/_catalogs/masterpage/`. Dies ist der Speicherort, dem Sie ein Netzlaufwerk zuordnen.
    
  
4. Notieren Sie sich den Speicherort des Gestaltungsvorlagenkatalogs, oder kopieren Sie ihn in die Zwischenablage.
    
  
Ordnen Sie auf dem Computer, auf dem das Designtool oder der HTML-Editor ausgeführt wird, dem soeben kopierten Speicherort ein Netzlaufwerk zu. Das Verfahren zum Zuordnen von Netzwerklaufwerken unterscheidet sich je nach Betriebssystem des Computers:
- Führen Sie für einen Computer unter Windows 8 die Schritte aus, die in der Windows 8-Version des Artikels  [Erstellen einer Verknüpfung (Zuordnung) mit einem Netzlaufwerk](http://windows.microsoft.com/de-de/windows-8/create-shortcut-to-map-network-drive) beschrieben werden.
    
  
- Führen Sie für einen Computer unter Windows 7 die Schritte aus, die in der Windows 7-Version des Artikels  [Erstellen einer Verknüpfung (Zuordnung) mit einem Netzlaufwerk](http://windows.microsoft.com/de-DE/windows7/Create-a-shortcut-to-map-a-network-drive) beschrieben werden.
    
  
- Führen Sie für einen Computer unter Windows Vista die Schritte aus, die in der -Version des Artikels  [Erstellen einer Verknüpfung (Zuordnung) mit einem Netzlaufwerk](http://windows.microsoft.com/de-DE/windows-vista/Create-a-shortcut-to-map-a-network-drive) beschrieben werden.
    
  
- Führen Sie auf einem Computer unter Windows XP die im Artikel  [Verbinden und Trennen eines Netzlaufwerks in Windows XP](http://support.microsoft.com/kb/308582) beschriebenen Schritte aus.
    
  
- ** *Wenn auf dem Computer ein anderes Betriebssystem ausgeführt wird, befolgen Sie die Anweisungen zum Erstellen einer Verknüpfung zu einem neuen Speicherort für das jeweilige Betriebssystem.* ** Möglicherweise müssen Sie andere Anmeldeinformationen angeben, um eine Verbindung mit der SharePoint-Website herzustellen, und möglicherweise müssen Sie angeben, dass die Verbindung bei jeder Anmeldung beim Computer wiederhergestellt werden soll.
    
  

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Vorgehensweise: Anwenden einer Gestaltungsvorlage auf eine Website in SharePoint 2013](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)
    
  
-  [Entwickeln des Website-Designs in SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013-Design-Manager-Gerätekanäle](sharepoint-2013-design-manager-device-channels.md)
    
  
-  [Vorgehensweise: ändern die Vorschauseite in SharePoint 2013-Design-Manager](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [SharePoint 2013 Design Manager - Bilddarstellungen](sharepoint-2013-design-manager-image-renditions.md)
    
  

