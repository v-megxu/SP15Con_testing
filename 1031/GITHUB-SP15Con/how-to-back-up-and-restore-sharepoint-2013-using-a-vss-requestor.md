---
title: Vorgehensweise Sichern und Wiederherstellen von SharePoint 2013 verwenden eines VSS-Requestors
ms.prod: SHAREPOINT
ms.assetid: cab5ba90-bd23-4cec-82d7-529e3f86ba88
---


# Vorgehensweise: Sichern und Wiederherstellen von SharePoint 2013 verwenden eines VSS-Requestors
 **Zusammenfassung:** Informationen Sie zum Sichern und Wiederherstellen von mithilfe eines Gruppenrichtlinien-Verwaltungskonsole (Volume Shadow Copy Service, VSS)-Anforderers für Microsoft SharePoint 2013.
## Sicherung und Wiederherstellung mit der Anforderer

Verwenden Sie das folgende Verfahren zum Sichern und Wiederherstellen von Microsoft SharePoint Foundation -Daten mithilfe des VSS-Requestors.
  
    
    

### Zum Sichern und Wiederherstellen von Daten mithilfe des Requestors


1. Starten Sie den VSS Writer-Dienst von SharePoint Foundation manuell. Öffnen Sie **Verwaltung**, dann **Dienste**, und starten Sie die Dienste **Volumeschattenkopie** und **SharePoint 2010 VSS Writer**.
    
  
2. Registrieren Sie den Writer-Dienst in der Windows-Registrierung durch Ausführen des  `STSADM -o registerwsswriter`-Befehls in einer Systemkonsole. Die ausführbare Datei befindet sich im Verzeichnis **%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\BIN**.
    
  
3. Wiederholen Sie die Schritte 1 und 2 auf allen SharePoint Foundation-Servern.
    
  
4. Verwenden Sie den Requestor, um Daten zu sichern und wiederherzustellen. Sie können entweder Ihren Requestor (wie unter  [Übersicht über den Volumeschattenkopie-Dienst](http://msdn.microsoft.com/de-de/library/aa384649.aspx) beschrieben) oder das Testprogramm BETest (erhältlich im [VSS SDK](http://www.microsoft.com/downloads/details.aspx?familyid=0b4f56e4-0ccc-4626-826a-ed2c4c95c871&amp;displaylang=de-de)) verwenden, um eine Sicherung oder Wiederherstellung aus SharePoint Foundation durchzuführen.
    
  

## Sicherheit beim Ausführen des Volumeschattenkopie-Diensts

Für den Volumeschattenkopie-Dienst (Volume Shadow Copy Service, VSS) gelten besondere Bedingungen für die Konten, unter denen die Writer auf allen Zielserverinstanzen für die Sicherung und Wiederherstellung ausgeführt werden.
  
    
    

- Das ausführende Konto muss die Berechtigung für Aufrufe in VSS haben. Für VSS muss ein VSS Writer standardmäßig ein Mitglied der Gruppe **Administratoren** oder **Sicherungs-Operatoren** auf der Zielserverinstanz sein. Sie können einen Registrierungsschlüssel so konfigurieren, dass andere Konten die Berechtigung zum Zugriff auf VSS haben.
    
  
- Das Konto muss die Berechtigung zum Ausgeben von **BACKUP DATABASE**- und **RESTORE DATABASE**-Befehlen für die Datenbankserver haben.
    
  
- Das Konto muss die Berechtigung zum Öffnen von VDI für SQL Server haben. Dazu muss der Client ein Mitglied der SQL Server-Gruppe **sysadmin** sein.
    
  
- Das Konto muss Abfragen in der **sys.master_files**-Katalogansicht in der Masterdatenbank auf dem Server mit SQL Server ausführen können.
    
  
Außerdem muss der Writer-Dienst, damit er vom SharePoint Foundation-Timerdienst ( **Owstimer.exe**) gehostet wird, unter dem Anwendungspoolkonto der Zentraladministration ausgeführt werden, das in einer einfachen Installation von SharePoint Foundation das Netzwerkdienstkonto ist.
  
    
    
 **Hinweis** Es ist sehr unwahrscheinlich, dass dieses Konto ein Administratorkonto eines lokalen Computers ist, d. h. die Anforderung für VSS nicht erfüllt wird, nach der das verarbeitende Konto als lokales System ausgeführt werden muss.
  
    
    

## Weitere Informationsquellen
<a name="bk_addresources"> </a>


-  [Übersicht über SharePoint 2013 und der Volumeschattenkopie-Dienst](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  

