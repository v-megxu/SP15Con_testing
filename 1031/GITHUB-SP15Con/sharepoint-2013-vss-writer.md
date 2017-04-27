---
title: SharePoint 2013 VSS Writer
ms.prod: SHAREPOINT
ms.assetid: f83577e4-ebb8-44e5-8dec-a3ca5878b7fd
---


# SharePoint 2013 VSS Writer
 **Zusammenfassung:** Informationen Sie zu den Eigenschaften und Features von der Gruppenrichtlinien-Verwaltungskonsole (Volume Shadow Copy Service, VSS) Writer für Microsoft SharePoint 2013.
Der VSS im Lieferumfang von Windows Server ist die Infrastruktur, die Funktionen der integrierten Shadow-Kopien bereitstellt. Schattenkopien erstellt von VSS ergänzen des Administrators die Speicher Band Archivierung Sicherungslösungen, Bereitstellung von High Fidelity Point-in-Time-Kopien, die erstellt werden können und auf einfache Weise und verbessern, damit helfen, die verschiedene Aspekte der Speicherung und Verwaltung vereinfachen wiederhergestellt. Microsoft SharePoint Foundation verwendet VSS zum Vereinfachen der Sicherung und Wiederherstellungsvorgängen.
  
    
    


## Eigenschaften des Systems

Im folgenden sind die SharePoint Foundation VSS-Lösung Funktionen und Merkmale:
  
    
    

- **Ein einzelner VSS-Verweisschreiber.** Das Schreiben von Daten von Anwendungen zu Sicherungsanwendungen war nie einfach. Zum erfolgreichen Sichern verschiedener Windows-Plattformanwendungen besitzen Sicherungsanwendungen eine sehr große Anzahl von APIs, für die spezifischer Code geschrieben werden muss. Der SharePoint Foundation VSS Writer (nachfolgend "SPF VSS Writer" genannt) ermöglicht das Nutzen des einzelnen Writers zum Sichern von SharePoint Foundation.
    
  
- **Sicherung und Wiederherstellung der vollständigen Farm für den Notfall.** Mit dem SPF VSS Writer kann eine Sicherungsanwendung (Anforderer) auf die VSS-API zugreifen, um einen Sicherungs- oder Wiederherstellungsvorgang für eine gesamte SharePoint Foundation-Farm anzufordern, einschließlich eines Setups in einem einzelnen System oder einer Farmkonfiguration. (Der IIS-Konfigurationsspeicher, bei dem es sich hauptsächlich um die Datei `applicationhost.config` handelt, ist nicht enthalten. Er muss separat gesichert und wiederhergestellt werden.)
    
  
- **Granularität auf Datenbankebene**. Mit dem SPF VSS Writer kann ein Anforderer alle Datenbanken, ein Segment der Datenbanken (Mehrfachauswahl) oder eine einzelne Datenbank (Einzelauswahl) sowohl für Sicherungs- als auch für Wiederherstellungsvorgänge auswählen. Alle Datenbanken mit Ausnahme der Konfigurations- und der Inhaltsdatenbank der Zentraladministration können über den Writer ausgewählt werden. Die Konfigurations- und die Inhaltsdatenbank der Zentraladministration können nur als Teil der ganzen Farm gesichert und wiederhergestellt werden. (Der IIS-Konfigurationsspeicher ist nicht enthalten. Er muss separat gesichert und wiederhergestellt werden.)
    
  
- **Inventur von Datenbanken.** Vor der Sicherung generiert der SPF VSS Writer eine flache Liste der für eine Sicherung in der Farm ausgewählten Datenbanken. Die Liste wird an den Anforderer zurückgegeben, sodass die Sicherung an dem Speicherort ausgeführt werden kann, an dem sich die Datenbank physikalisch befindet.
    
  
- **Farmunterstützung.** Vom Writer wird Unterstützung für die Synchronisierung der Sicherung und Wiederherstellung in einer SharePoint Foundation-Farm auf begrenzte Art und Weise bereitgestellt. Der Anforderer erhält vom Writer eine Liste der Server, Datenbanken und Dateien, die der Farm zugeordnet sind. Der Anforderer ist für das Herstellen einer separaten Verbindung mit jedem Server verantwortlich, um den SPF VSS Writer auf diesem Server zum Generieren der Sicherung oder zum Ausführen des Wiederherstellungsvorgangs aufzurufen.
    
  
- **Sichern von Inhalt ohne Unterbrechung.** Falls eine Datei von einer Anwendung während der Sicherung geändert wird, kann die Datei dadurch beschädigt werden. Mit VSS wird eine rasche Momentaufnahme der Dateien für die Schattenkopie erstellt, während die Anwendung am ursprünglichen Speicherort ohne Unterbrechung weiter ausgeführt wird.
    
  
- **Austauschbare Datenbanksicherung und -wiederherstellung von Drittanbietern.** Mit dem SPF VSS Writer wird die austauschbare/erweiterbare Sicherung für Lösungen von Drittanbietern angeboten, die auf SharePoint Foundation aufbauen. Es sind jedoch nur die Datenbanken im Writer enthalten, die in der Konfigurationsdatenbank registriert sind. Alle weiteren Dateien und nicht registrierten Datenbanken sind nicht enthalten.
    
  
- **Sicherung und Wiederherstellung von Suchindexdateien.** Da Suchindexdateien im Dateisystem gespeichert werden, ist zu ihrer Sicherung ein separater Dateischreiber erforderlich. Zur Lösung dieses Problems enthält SharePoint Foundation einen separaten Suchschreiber, der Suchindexdateien behandelt. Zur Vereinfachung des Sicherns von Anwendungsschreibern deklariert SharePoint Foundation schreiberübergreifende Abhängigkeiten so, dass Suchindexdateien beim Sichern von registrierten Datenbanken in der Farm gesichert oder wiederhergestellt werden.
    
  
- **Vollständiges Rollback.** Der SPF VSS Writer behandelt alle Komponenten in einer SharePoint Foundation-Bereitstellung, einschließlich der Konfigurationsdatenbank und der Inhaltsdatenbanken und der Suchdatenbank und des Suchindexes. Wie bereits zuvor erwähnt, besitzt der Writer auch eine Abhängigkeit vom Suchschreiber, der alle Suchindexdateien für die Sicherung und Wiederherstellung behandelt. Zum Zeitpunkt der Wiederherstellung kann der Writer ein Rollback der gesamten SharePoint Foundation-Bereitstellung durchführen, indem eine vorherige Farmsicherung wiederhergestellt wird. (Der IIS-Konfigurationsspeicher ist nicht enthalten. Er muss separat gesichert und wiederhergestellt werden.)
    
    > **HINWEIS**
      > Wichtige Informationen zur Wiederherstellung finden Sie unter "Wiederherstellung" in  [VSS-Anforderer und SharePoint 2013](vss-requestors-and-sharepoint-2013.md).
- **Synchronisierung von Datenbanken nach der Wiederherstellung.** Zur Sicherstellung, dass alle Datenbanken nach Abschluss eines Wiederherstellungsvorgangs mit der Farm synchronisiert werden, wird jede Datenbank automatisch nach der Wiederherstellung getrennt und wieder mit der Farm verbunden. Administratoren müssen keine zusätzlichen Verfahren ausführen, um die wiederhergestellten Datenbanken erneut zu synchronisieren.
    
  

> **WICHTIG**
> Wenn Sie in Ihrer SharePoint Foundation-Farm SQL-Aliase verwenden, um eine Verbindung mit dem Computer mit SQL Server herzustellen, müssen Sie die SQL Server-Clientverbindungskomponenten auf den Farmservern installieren, damit der SPF-VSS-Writer für die Sicherung/Wiederherstellung verwendet werden kann. Zu den Komponenten gehören der SQL WMI-Anbieter für die Konfigurationsverwaltung, den der SPF-VSS-Writer benötigt, um SQL-Aliase in den ordnungsgemäßen SQL Server aufzulösen. Verwaltungstools wie SQL Management Studio müssen nicht installiert werden. Sie müssen die Installationsquelle (z. B. eine Daten-DVD) verwenden, mit deren Hilfe Sie das vollständige SQL Server-Produkt installieren würden. (Verwenden Sie nicht die gesonderte eigenständige Version der Clientkomponenten, da diese Version nicht den SQL WMI-Anbieter enthält.) Wählen Sie eine benutzerdefinierte Installation und nur die zu installierenden Clientkomponenten aus.
  
    
    


## Vom SPF VSS Writer ausgeführte Funktionen

Vom SPF VSS Writer werden die folgenden Funktionen ausgeführt:
  
    
    

1. Erstellt SharePoint Foundation-Komponenten.
    
  - Generiert eine vollständige Liste aller Komponenten in der SharePoint Foundation-Farm.
    
  
  - Er muss nicht an den Sicherungsprozess oder Wiederherstellungsprozess gebunden sein.
    
  

![SharePoint und Volumeschattenkopie-Dienst](images/99376713-6a54-4d88-9b05-068578169506.gif)
  

  

  
2. Sichert Farm oder Datenbank.
    
  - Fordert eine SharePoint Foundation-Sicherung (Farm/Datenbank) über VSS an.
    
  

![SharePoint und Volumeschattenkopie-Dienst](images/97765b6d-51e9-4d07-8b5d-3e93c0508b16.gif)
  

  

  
3. Stellt eine Farm oder Datenbank wieder her.
    
  - Fordert eine SharePoint Foundation-Wiederherstellung (Farm/Datenbank) über VSS an.
    
  
  - Implementiert **postRestore()** zum Synchronisieren von Websitetabellen.
    
  

![SharePoint und Volumeschattenkopie-Dienst](images/b86ecdb8-88a7-4407-af86-07d2442235dc.gif)
  

  

  

## Nächste Schritte
<a name="Next"> </a>

Erfahren Sie, wie erstellen und Verwenden eines VSS-Requestors für SharePoint 2013:
  
    
    

-  [VSS-Anforderer und SharePoint 2013](vss-requestors-and-sharepoint-2013.md)
    
  

## Weitere Informationsquellen
<a name="bk_addresources"> </a>


-  [Übersicht über SharePoint 2013 und der Volumeschattenkopie-Dienst](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  

