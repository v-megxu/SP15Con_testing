---
title: Erstellen von Farmlösungen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 96c32f08-ad93-49af-b8d0-9d194a48cc79
---


# Erstellen von Farmlösungen in SharePoint 2013
Übersicht über unsere Dokumentation und die Entwicklung, Verpackung und Bereitstellung von administrativen Erweiterungen für SharePoint 2013 mit Farmlösungen.
## Was sind Farmlösungen?
<a name="WhatAreFarmSolutions"> </a>

SharePoint 2013 verfügt über ein eigenes System für die Installation von Erweiterungen für administrative SharePoint-Funktionen, das sich von anderen Windows-Anwendungen und -Plattformen unterscheidet. Es ist keine MSI-Datei und ClickOnce-Technologie implementiert. Die Assemblys, XML- und andere Dateien in die Erweiterung werden stattdessen in einer einzelnen Datei gebündelt, die Lösungspaket genannt wird. Ein Lösungspaket verfügt über ein CAB-basiertes Format mit einer WSP-Dateierweiterung. Das Paket kann SharePoint-Features und deren untergeordnete Komponenten sowie bestimmte Arten von Komponenten beinhalten, die nicht in Features bereitgestellt werden. Farmadministratoren laden die Pakete an einem farmübergreifenden Speicherort hoch, von wo sie bereitgestellt und die zugehörigen Features aktiviert werden können.
  
    
    
Im Gegensatz zu SharePoint-Add-Ins enthalten Farmlösungen Code, der auf SharePoint-Servern bereitgestellt wird und Aufrufe des SharePoint-Serverobjektmodells ausführen kann. Diese Assemblys werden immer mit voller Vertrauenswürdigkeit ausgeführt. Der Bereich der Features in Farmlösungen kann, neben des Websitebereichs der Features in SharePoint-Add-Ins, die Websitesammlung, Webanwendung oder die gesamte Farm umfassen. Aufgrund dieser Aspekte der Farmlösungen sind Farmadministratoren nur dann zur Installation von diesen bereit, wenn sie von einer bekannten und vertrauenswürdigen Quelle stammen. Aus diesem Grund sollten SharePoint-Erweiterungen, die in erster Linie für die Verwendung durch Endbenutzer entwickelt werden, als SharePoint-Add-Ins, und nicht Farmlösungen, entwickelt werden. Farmlösungen sollten für Anpassungen von SharePoint-Verwaltungsfunktionen wie benutzerdefinierte Zeitgeberaufträge, benutzerdefinierte Windows PowerShell-Cmdlets und Erweiterungen der Zentralverwaltung verwendet werden. Weitere Informationen über die Vorteile der SharePoint-Add-Ins und die Verwendung von Farmlösungen finden Sie unter  [SharePoint-Add-Ins im Vergleich zu SharePoint-Lösungen](sharepoint-add-ins-compared-with-sharepoint-solutions.md).
  
    
    

## Leitfaden für die Dokumentation für Entwickler von Farmlösungen
<a name="Guide"> </a>

Die Entwicklung von Farmlösungen hat sich seit SharePoint 2010geändert. Deshalb sind in diesem Abschnitt Links zum SharePoint 2010 SDK enthalten. Um Verwirrung zu vermeiden, beachten Sie die folgenden Punkte bei der Verwendung des SharePoint 2010 SDK für die Entwicklung für SharePoint 2013:
  
    
    

- Im SharePoint 2010 SDK wird häufig auf „Sandkastenlösungen" verwiesen. Sandkastenlösungen mit benutzerdefiniertem Code sind in SharePoint 2013 veraltet. Sandkastenlösungen „ohne Code" werden weiterhin verwendet.
    
  
- Unsere Empfehlung, Farmlösungenin erster Linie für administrative Erweiterungen zu verwenden, gilt nicht in SharePoint 2010. Aus diesem Grund beziehen sich möglicherweise viele Beispiele und andere Dokumentationen im SharePoint 2010 SDK auf Endbenutzer-Erweiterungen, die als Farmlösungen bereitgestellt werden.
    
  
- Die Begriffe „serverseitig" oder „Servercode" im SharePoint 2010 SDK beziehen sich auf den Code, der das SharePoint-Serverobjektmodell aufruft. Diese Begriffe beziehen sich  *nicht*  auf den Code, der auf Remote-Webservern ausgeführt wird (d. h. Webservern außerhalb der SharePoint-Farm). Der Code, der SharePoint von Remote-Webservern aufruft, verwendet sowohl in SharePoint 2010 als auch in SharePoint 2013, immer eins der SharePoint- *Client*  objektmodelle. Im SharePoint 2010 SDK, wird diese Art von Code „clientseitiger" Code oder „Clientcode" genannt.
    
  
- Die Assemblys in einer Farmlösung in SharePoint 2010 können mit CAS-Richtlinien (Custom Access Security, CAS) bereitgestellt werden. Solche Richtlinien werden in SharePoint 2013 ignoriert; alle Assemblys in Farmlösungen in SharePoint 2013 werden mit voller Vertrauenswürdigkeit ausgeführt.
    
  

### Verpackung und Bereitstellung

Die Grundlagen der Verpackung, Installation, Aktualisierung und Lokalisierung in Farmlösungen werden unter  [Übersicht über Lösungen](http://msdn.microsoft.com/library/1983cab9-4b29-494a-a62a-0f8e83908744%28Office.15%29.aspx) und [Farmlösungen](http://msdn.microsoft.com/library/845f7524-b9ff-412b-aa29-3afacda91100%28Office.15%29.aspx) erläutert. Die Entwicklung bestimmter SharePoint-Komponenten für die Integration in einer Farmlösung wird in den entsprechenden Artikeln zum SharePoint 2010 SDK beschrieben. Die meisten Komponenten in einer Farmlösung sollten in einem oder mehreren benutzerdefinierten SharePoint-Features eingeschlossen werden. Informationen zum Entwerfen und Erstellen von Features finden Sie unter [Verwenden von Features](http://msdn.microsoft.com/library/ce5f5ce5-1429-439e-9261-2c4ba9788cc1%28Office.15%29.aspx) im SharePoint 2010 SDK.
  
    
    

### Administrative Erweiterungen

Eine Anleitung zum Erweitern der Verwaltungsfunktionen in einer SharePoint-Farm finden Sie unter  [SharePoint Foundation-Administration](http://msdn.microsoft.com/library/cdcc1b8a-4144-446f-b471-03d4a754a8ab%28Office.15%29.aspx) im SharePoint 2010 SDK. Dort sind Erläuterungen zur Erweiterung der Zentraladministration, Erstellen von benutzerdefinierten Windows PowerShell-Cmdlets, Anpassen von Upgrades und Migration, Anpassung von Backups und Anpassen der SharePoint-Ereignisprotokollierung enthalten. In einem Abschnitt wird die Anpassung der SharePoint-Farmintegrität und des Leistungsmesssystems erläutert. Anweisungen zum Erstellen eines benutzerdefinierten Zeitgeberauftrags finden Sie unter [Gewusst wie: Ausführen von Code auf allen Webservern](http://msdn.microsoft.com/library/1bbb11b4-a342-4bed-9e7a-b8b13edd0ccc%28Office.15%29.aspx).
  
    
    

## Inhalt dieses Abschnitts
<a name="Guide"> </a>

Die Themen in diesem Abschnitt beschreiben die  *Änderungen*  bei der Entwicklung von SharePoint-Lösungen.
  
    
    

-  [Vorgehensweise: Anpassen eines Feldtyps mithilfe vom clientseitigem Rendering](how-to-customize-a-field-type-using-client-side-rendering.md)
    
  
-  [URLs und Token in SharePoint 2013](urls-and-tokens-in-sharepoint-2013.md)
    
  
-  [Virtuelle Verzeichnisse in SharePoint 2013-Lösungen](virtual-directories-in-sharepoint-2013-solutions.md)
    
  

## Zusätzliche Ressourcen
<a name="SP15buildfarm_addlresources"> </a>


-  [Programmiermodelle in SharePoint 2013](programming-models-in-sharepoint-2013.md)
    
  

