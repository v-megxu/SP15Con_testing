---
title: VSS-Anforderer und SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 0b2e5a4e-40f0-4ccf-a21a-7274921f2169
---


# VSS-Anforderer und SharePoint 2013
 **Zusammenfassung:** Informieren Sie sich über die Funktionsweise des Requestors-Systems des Systems Gruppenrichtlinien-Verwaltungskonsole (Volume Shadow Copy Service, VSS) mit Microsoft SharePoint 2013.
VSS in Windows Server kann verwendet werden, um Anwendungen erstellen, die sichern und Wiederherstellen von Microsoft SharePoint Foundation. Der VSS stellt eine Infrastruktur, die Speicherlösung-Management-Programme, Business-Programme und Hardwareanbietern zusammenzuarbeiten erstellen und Verwalten von Schattenkopien können. Für diese Infrastruktur-basierte Lösungen können die Schatten Kopien (oder gespiegelte Kopien) zum Sichern und Wiederherstellen von Datenbanken für eine oder mehrere- SharePoint Foundation .
  
    
    


## VSS-Requestors system

Der VSS koordiniert die Kommunikation zwischen den Requestors (backup-Anwendungen), Autoren (Windows-Anwendungen wie SharePoint Foundation und Microsoft SQL Server) und Anbieter (System, Software oder Hardware Komponenten, die die Schattenkopien erstellen). Zum Sichern von SharePoint Foundationmithilfe des VSS-Features, muss das Sicherungsprogramm ein Volumenschattenkopie-Anforderers enthalten, das SharePoint Foundationkennt. Da das Sicherungsprogramm, das mit Windows Server bereitgestellt ist keine solche Requestors verfügt, müssen Organisationen Sicherung Anwendungen von Drittanbietern verwenden.
  
    
    
Im Hinblick auf die Kompatibilität mit SharePoint Foundation müssen bei auf VSS basierenden Sicherungsanwendungen zwei Basisvoraussetzungen erfüllt sein, damit die Integrität und Wiederherstellbarkeit von Schattenkopiesicherungen sichergestellt ist. Kunden sollten sich von ihren Sicherungsanbietern bestätigen lassen, dass die Sicherungsanwendung die in diesem Thema genannten Kompatibilitätsanforderungen für SharePoint Foundation erfüllt.
  
    
    
Die folgenden SharePoint Foundation-Anforderungen gelten für eine auf Schattenkopien basierende Sicherungsanwendung, um die Integrität und Wiederherstellbarkeit von SharePoint Foundation-Datenbanken sicherzustellen:
  
    
    

- SharePoint Foundation-Datenbanken und Suchindexdateien dürfen ausschließlich über SPF-VSS Writer gesichert werden.
    
  
- Die Integrität des Schattenkopie-Sicherungssatzes muss von der Sicherungsanwendung überprüft werden. Wiederherstellungsvorgänge am ursprünglichen Speicherort dürfen ausschließlich mit SPF-VSS Writer ausgeführt werden.
    
  

## Wiederherstellen

Für die Ausführung einer Wiederherstellung müssen die folgenden Bedingungen erfüllt sein:
  
    
    

- Die folgenden Dienste müssen  *gestartet*  sein:
    
  - SharePoint VSS Writer
    
  
  - Volumeschattenkopie
    
  
  - SharePoint Tracing
    
  
- Die folgenden Dienste müssen  *beendet*  sein:
    
  - SharePoint-Verwaltung
    
  
  - SharePoint-Suche
    
  
  - SharePoint-Timer
    
  
  - SharePoint Server-Suche (wenn SharePoint Server installiert ist)
    
  
- Wenn die gesamte Farm wiederhergestellt wird, müssen SharePoint Foundation und die Internetinformationsdienste (Internet Information Services, IIS) heruntergefahren werden.
    
  
- Wenn nur ausgewählte Webanwendungen oder andere Komponenten wiederhergestellt werden, müssen die Webanwendungen heruntergefahren werden, und die Komponenten können während der Wiederherstellung nicht verwendet werden.
    
  

## Nächste Schritte
<a name="Next"> </a>

Erfahren Sie, wie erstellen und Verwenden eines VSS-Requestors für SharePoint 2013:
  
    
    

-  [Vorgehensweise: Erstellen ein Volumenschattenkopie-Anforderers für die Verwendung mit SharePoint 2013](how-to-create-a-vss-requestor-for-use-with-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Sichern und Wiederherstellen von SharePoint 2013 verwenden eines VSS-Requestors](how-to-back-up-and-restore-sharepoint-2013-using-a-vss-requestor.md)
    
  
-  [Vorgehensweise: Sichern und Wiederherstellen eine Suchdienstanwendung in SharePoint 2013 mit VSS](how-to-back-up-and-restore-a-search-service-application-in-sharepoint-2013-using.md)
    
  

## Weitere Informationsquellen
<a name="bk_addresources"> </a>


-  [Übersicht über SharePoint 2013 und der Volumeschattenkopie-Dienst](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  
-  [Vorgehensweise: Erstellen ein Volumenschattenkopie-Anforderers für die Verwendung mit SharePoint 2013](how-to-create-a-vss-requestor-for-use-with-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Sichern und Wiederherstellen von SharePoint 2013 verwenden eines VSS-Requestors](how-to-back-up-and-restore-sharepoint-2013-using-a-vss-requestor.md)
    
  
-  [Vorgehensweise: Sichern und Wiederherstellen eine Suchdienstanwendung in SharePoint 2013 mit VSS](how-to-back-up-and-restore-a-search-service-application-in-sharepoint-2013-using.md)
    
  

