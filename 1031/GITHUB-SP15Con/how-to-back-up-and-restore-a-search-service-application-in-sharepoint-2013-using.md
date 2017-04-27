---
title: Vorgehensweise Sichern und Wiederherstellen eine Suchdienstanwendung in SharePoint 2013 mit VSS
ms.prod: SHAREPOINT
ms.assetid: 87ee28e6-8170-4dba-8c9d-f04ab9e632dc
---


# Vorgehensweise: Sichern und Wiederherstellen eine Suchdienstanwendung in SharePoint 2013 mit VSS
 **Zusammenfassung:** Informationen Sie zum Sichern und Wiederherstellen einer Suchdienstanwendung in SharePoint 2013 mithilfe der Gruppenrichtlinien-Verwaltungskonsole (Volume Shadow Copy Service, VSS).
## Voraussetzungen für das Sichern und Wiederherstellen von SharePoint mit den Volumeschattenkopie-Dienst

Um eine Sicherung und Wiederherstellung-Lösung für SharePoint 2013, müssen Sie verstehen, wie VSS funktioniert und mit der SharePoint-Benutzeroberfläche.
  
    
    

**In Tabelle 1. Kernkonzepte für das Sichern und Wiederherstellen von SharePoint mit den Volumeschattenkopie-Dienst**


|**Artikel**|**Beschreibung**|
|:-----|:-----|
| [Volumeschattenkopie-Dienst](http://msdn.microsoft.com/en-us/library/windows/desktop/bb968832%28v=vs.85%29.aspx) und seine untergeordneten Artikel. <br/> |Informationen Sie zu den VSS und zum Programmieren dafür. <br/> |
| [SharePoint Foundation und der Volumeschattenkopie-Dienst](http://msdn.microsoft.com/library/adae101a-078e-40b9-9cfa-db2cfb10270a%28Office.15%29.aspx) und seine untergeordneten Artikel. <br/> |Allgemeine Informationen und Vorgehensweisen schrittweise Verfahren zum Sichern und Wiederherstellen von SharePoint 2013 Daten mit der VSS und der SharePoint-Benutzeroberfläche mit VSS an. <br/> |
   

## Verwenden Sie den Volumeschattenkopie-Dienst zum Sichern und Wiederherstellen einer Suchdienstanwendung
<a name="Use"> </a>

Die folgenden Verfahren dienen zur Unterstützung der Entwickler Erstellen einer Sichern/Wiederherstellen der Anwendung, die die VSS verwendet Wenn Sie die IT-Experten finden Anweisungen zum Sichern oder Wiederherstellen einer Suchdienstanwendung SharePoint 2013 haben, finden Sie unter  [Sichern und Wiederherstellen von SharePoint 2013](http://technet.microsoft.com/en-us/library/ee662536.aspx).
  
    
    
 **Erforderliche:** Herunterladen und Installieren von [Microsoft Windows SDK für Windows 7 und .NET Framework 4](http://www.microsoft.com/en-us/download/details.aspx?id=8279) mit dem Server mit der Suchdienstanwendung (SSA) und auf jedem Server mit einer Suchkomponente Index. Unter anderem wird dies `C:\\Program Files\\Microsoft SDKs\\Windows\\v7.1\\Bin\\x64\\vsstools`vshadow.exe und betest.exe installieren.
  
    
    

> **TIPP**
> Ausführliche Informationen zu den in diesem Artikel erwähnten Windows PowerShell-Cmdlets finden Sie unter  [Windows PowerShell für SharePoint 2013 Reference](http://technet.microsoft.com/en-us/library/ee890108.aspx).
  
    
    


### Registrieren die SharePoint-VSS Writer und Vorbereiten der Server für das Sichern und Wiederherstellen


- Registrieren Sie die SharePoint-VSS-Writer mit beiden Methoden:
    
  - Öffnen Sie **Dienste** in **Verwaltung**, und starten Sie den **SharePoint VSS Writer**-Dienst.
    
  
  - Öffnen Sie eine Befehlskonsole und führen Sie  `stsadm.exe -o registerwsswriter` aus. Dienstprogramm Stsadm befindet sich im %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ BIN. Stellen Sie sicher, dass der Dienst **Dienste** in **Verwaltung** ausgeführt wird.
    
  

### So sichern Sie eine SharePoint-Suchdienstanwendung mit VSS


1. Rufen Sie VSS-Metadaten  `vshadow.exe -wm > writers.txt` an der Befehlszeile ausführen, auf jedem Server, die eine Indexkomponente enthält und auch auf dem Computer, auf der SQL Server ausgeführt wird, wo sich die Suchdatenbanken befinden. Die erstellte Datei writers.txt enthält alle VSS Writer-Server zugeordnet. Verwenden Sie diese Datei in den nächsten Schritten, um Manifestdateien für die Suchdienstanwendung (SSA) und den Suchindex zu generieren.
    
  
2. Führen Sie diese Schritte zum Erstellen eines Manifests für die SSA auf dem Computer, auf dem SQL Server ausgeführt wird, wo sich die Suchdatenbanken befinden.
    
1. Erstellen Sie eine XML-Datei, und fügen Sie die folgenden:
    
  ```XML
  
<BETest>
  <Writer writerid="SharePoint Services Writer ID">
    <Component logicalPath="PathSSA" componentName="SearchAppOffice" />
    <Component logicalPath="PathC" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="PathA" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="PathL" componentName="SearchAppOffice_LinksStore" />
  </Writer>
  <Writer writerid="SQL Server Writer ID">
    <Component logicalPath="PathDbSSA" componentName="SearchAppOffice" />
    <Component logicalPath="PathDbC" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="PathDbA" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="PathDbL" componentName="SearchAppOffice_LinksStore" />
  </Writer>
</BETest>

  ```

2. Ersetzen Sie die 10 Platzhalter in der Datei durch die entsprechenden Werte aus der writer.txt-Datei, die Sie im ersten Schritt generiert. Anhand der folgenden Tabelle als Leitfaden.
    
    > **HINWEIS**
      > In der rechten Spalte ist  _SSA_ selbst ein Platzhalter für den Namen der Suchdienstanwendung.

   **In Tabelle 2. SSA Manifestdatei Platzhalter und Werten aus writers.txt**


|**Platzhalter**|**Wo befindet sich die Informationen im writers.txt.**|
|:-----|:-----|
| _SharePoint Services Writer ID_ <br/> |Die WriterId-GUID angezeigt, unter dem Eintrag "SharePoint Services-Writer" <br/> |
| _PathSSA_ <br/> |Der logische Path-Eintrag mit dem Namen der Suchdienstanwendung in den Eintrag "SharePoint Services-Writer" aufgeführt <br/> |
| _PathC_ <br/> |Der logische Path-Eintrag aufgelistet, für die Komponente mit dem Namen" _SSA__CrawlStore" im "SharePoint Services-Writer"-Eintrag <br/> |
| _PathA_ <br/> |Der logische Path-Eintrag aufgelistet, für die Komponente mit dem Namen" _SSA_ _AnalyticsReportingStore" im "SharePoint Services-Writer"-Eintrag <br/> |
| _PathL_ <br/> |Der logische Path-Eintrag aufgelistet, für die Komponente mit dem Namen" _SSA__LinksStore" im "SharePoint Services-Writer"-Eintrag <br/> |
| _SQL Server Writer ID_ <br/> |Die WriterId-GUID angezeigt, unter dem Eintrag "SqlServerWriter" <br/> |
| _PathDbSSA_ <br/> |Der logische Path-Eintrag für die Komponente mit dem Namen der Suchdienstanwendung in der Eintrag "SqlServerWriter" aufgeführt <br/> |
| _PathDbC_ <br/> |Der logische Path-Eintrag für die Komponente mit dem Namen" _SSA__CrawlStore" in den Eintrag "SqlServerWriter" aufgeführt <br/> |
| _PathDbA_ <br/> |Der logische Path-Eintrag für die Komponente mit dem Namen" _SSA__AnalyticsReportingStore" in den Eintrag "SqlServerWriter" aufgeführt <br/> |
| _PathDbL_ <br/> |Der logische Path-Eintrag für die Komponente mit dem Namen" _SSA__LinksStore" in den Eintrag "SqlServerWriter" aufgeführt <br/> |
   

    Dies ist die Manifestdatei SSA. Ein Beispiel einer abgeschlossenen SSA-Manifestdatei finden Sie unter  [Beispiel-Manifestdateien](#Examples).
    
  
3. Befolgen Sie diese Schritte zum Erstellen eines Manifests für die Suche Indexdateien. Wiederholen Sie diese Schritte auf jedem Server, der eine Indexkomponente hat.
    
1. Erstellen Sie eine XML-Datei, und fügen Sie die folgenden:
    
  ```XML
  
<BETest>
   <Writer writerid="SharePoint Services Writer ID">
      <Component logicalPath="PathIndex" componentName="NameIndex" />
   </Writer>
   <Writer writerid="OSearch15 Writer ID">
      <Component logicalPath="PathOSearch15" componentName="IndexComponentGroup" />
   </Writer>    
</BETest>
  ```

2. Ersetzen Sie die sechs Platzhalter in der Datei durch die entsprechenden Werte aus der writer.txt-Datei, die Sie im ersten Schritt generiert. Anhand der folgenden Tabelle als Leitfaden.
    
   **Tabelle 3. Search Index Manifestdatei Platzhalter und Werten aus writer.txt**


|**Platzhalter**|**Wo die Informationen im writers.txt befindet**|
|:-----|:-----|
| _SharePoint Services Writer ID_ <br/> |Die WriterId-GUID angezeigt, unter dem Eintrag "SharePoint Services-Writer" <br/> |
| _PathIndex_ <br/> |Der logische Path-Eintrag aufgelistet, die für die Komponente, deren Namen mit "IndexComponentGroup" in den Eintrag "SharePoint Services-Writer" beginnt <br/> |
| _NameIndex_ <br/> |Den Eintrag aufgeführt, die für die Komponente, deren Namen mit "IndexComponentGroup" in den Eintrag "SharePoint Services-Writer" beginnt <br/> |
| _OSearch15 Writer ID_ <br/> |Die WriterId-GUID angezeigt, unter dem Eintrag "OSearch15 VSS Writer" <br/> |
| _PathOSearch15_ <br/> |Der logische Path-Eintrag aufgelistet, die für die Komponente, deren Namen mit "IndexComponentGroup" in den Eintrag "OSearch15 VSS Writer" beginnt. Es ist normalerweise leer. <br/> |
| _IndexComponentGroup_ <br/> |Den Eintrag aufgeführt, die für die Komponente, deren Namen mit "IndexComponentGroup" in den Eintrag "OSearch15 VSS Writer" beginnt <br/> |
   

    Dies ist die Manifestdatei für die Suche Index. Ein Beispiel eines ausgefüllten Suchindex-Manifestdatei, finden Sie unter  [Beispiel-Manifestdateien](#Examples).
    
  
4. (Optional) Notieren Sie die Größe der **IndexComponent** Ordner auf jedem Server, die eine Indexkomponente enthält. Sie können diese Informationen später so überprüfen Sie die Sicherung verwenden.
    
  
5. Öffnen Sie bei jedem Server in der Farm die SharePoint-Verwaltungsshell, und führen Sie die folgenden Zeilen, wobei  _name of search service application_ die SSA ist, die Sie sichern möchten. Lassen Sie das Fenster SharePoint-Verwaltungsshell geöffnet danach.
    
  ```
  
$ssa = Get-SpenterpriseSearchServiceApplication -Identity "name of search service application"
Suspend-SPEnterpriseSearchServiceApplication -Identity $ssa
  ```

6. Führen Sie Sicherungen der SSA Datenbanken und der Index folgende Schritte aus:
    
1. Führen Sie auf dem Server mit den Datenbanken SSA den folgenden Befehl an der Befehlszeile aus, wobei  _destination backup folder_ ist der vollständige Pfad des Ordners für die Sicherungsdateien, _backup log file_ ist der vollständige Pfad und Namen der Protokolldatei der Sicherung und _SSA manifest file_ ist der Pfad und Dateiname der Manifestdatei SSA.
    
  ```
  
betest.exe /v /b /d "destination backup folder" /s "backup log file" /x "SSA manifest file"
  ```

2. Führen Sie auf dem Server mit dem open SharePoint-Verwaltungsshell-Fenster die folgende Zeile, wobei  _topology file name_ den vollständigen Pfad und Namen der exportierten Datei, die die Topologieinformationen enthält. Sie verwenden diese Datei in der Wiederherstellungsvorgang für die SSA.
    
  ```
  Export-SPEnterpriseSearchTopology -SearchApplication $ssa -Filename "topology file name"
  ```

3. Stellen Sie sicher, dass die Datei erstellt wird.
    
  
4. Führen Sie auf jedem Server, der eine Indexkomponente verfügt folgenden Befehl an der Befehlszeile aus, wobei  _destination backup folder_ ist der vollständige Pfad des Ordners für die Sicherungsdateien, _backup log file_ ist der vollständige Pfad und Namen der Protokolldatei der Sicherung und _index manifest file_ ist der Pfad und Dateiname des Manifests Index.
    
  ```
  betest.exe /v /b /d "destination backup folder" /s "backup log file" /x "index manifest file"
  ```

5. (Optional) Prüfen Sie die Index-Ordner, die gesichert wurde. Stellen Sie sicher, dass Ordnernamen und Größen mit den im vorherigen Schritt aufgezeichnet werden soll.
    
  

### Wiederherstellen eine SharePoint-Suchdienstanwendung mit VSS


1. Öffnen Sie bei jedem Server in der Farm die SharePoint-Verwaltungsshell, und führen Sie die folgenden Zeilen, um die vorhandene Suchdienstanwendung und Stellvertreter, wobei  _name of search service application_ die SSA aus, die Sie wiederherstellen möchten und _name of proxy_ ist seine Anwendungsproxy zu entfernen. Hinweis: Diese _name of SSA proxy_ normalerweise identisch mit den Namen der SSA mit dem Wort "Proxy" Ende hinzugefügten ist. Die Option `RemoveData` wird sichergestellt, dass die Suchdatenbanken entfernt werden.
    
  ```
  $ssa = Get-SPEnterpriseSearchServiceApplication -Identity "name of search service application"
Remove-SPEnterpriseSearchServiceApplication -Identity $ssa -RemoveData
Remove-SPEnterpriseSearchServiceApplicationProxy -Identity "name of SSA proxy"
  ```

2. Führen Sie auf dem gleichen Server Folgendes an der Befehlszeile zum Wiederherstellen der Datenbanken SSA where  _destination backup folder_ ist der vollständige Pfad des Ordners für die Sicherungsdateien, _backup log file_ ist der vollständige Pfad und Namen der Protokolldatei der Sicherung und _SSA manifest file_ ist der Pfad und Dateiname der Manifestdatei SSA.
    
  ```
  
betest.exe /v /r /d "destination backup folder" /s "backup log file" /x SSA_manifest_file
  ```

3. Öffnen Sie auf dem gleichen Server ein SharePoint-Verwaltungsshell, und führen Sie die folgenden Zeilen, um die SSA wiederherzustellen, wobei  _application pool name_ ist der Name des neuen Pools, _domain\\user_ ist der Domänenname des Benutzers, der der zu verwendenden Anwendungspool als von in der Ereignisprotokollen, _name of the search service application_ ist der Name der SSA und _topology_file_name_ ist der Pfad und Name der Aufschlüsselung-Datei, die Sie erstellt haben, wenn die SSA gesichert wurde.
    
    > **TIPP**
      > Dieser Code erstellt eine neue Identität des Anwendungspools, um die wiederhergestellten SSA ausgeführt, aber Sie können auch ein vorhandenes Konto verwenden, mit dem Cmdlet **Get-SPServiceApplicationPool**.

  ```
  $applicationPool = New-SPServiceApplicationPool -name "application pool name" -account "domain\\user"
Restore-SPEnterpriseSearchServiceApplication -Name "name of the search service application" -ApplicationPool $applicationPool -TopologyFile "topology_file_name" -KeepId
  ```

4. Erstellen Sie einen Proxy für die SSA mit den folgenden Cmdlets. Es wird empfohlen, dass Sie die gleichen Werte für  _name of the search service application_ und _name of SSA proxy_ verwenden, wie Sie in Schritt 1 verwendet.
    
  ```
  
$ssa = Get-SpenterpriseSearchServiceApplication -Identity "name of search service application"
New-SPEnterpriseSearchServiceApplicationProxy -Name "name of SSA proxy" -SearchApplication $ssa
  ```

5. (Optional) Stellen Sie sicher, dass die SSA und dessen Proxy vorhanden sind, indem **Zentraladministration** öffnen. Wählen Sie **Dienstanwendungen verwalten**, und stellen Sie sicher, dass die SSA und dessen Proxy aufgeführt sind.
    
  
6. (Optional) Klicken Sie auf die SSA in der Liste der Dienste, und klicken Sie dann auf der Seite, die geöffnet wird, überprüfen Sie, ob die **Suchtopologie**-Tabelle der Aufschlüsselung gesucht, die Sie in den Sicherungsvorgang exportiert haben. (Sie können auch die Topologie mit dem Cmdlet **Get-SPEnterpriseSearchStatus**überprüfen.)
    
  
7. Stellen Sie die Indexdateien mit dem folgenden Verfahren **auf allen Servern mit indexkomponenten** wieder her.
    
1. Beenden Sie den Hostcontroller service entweder in **Verwaltung > Dienste**, oder indem Sie das folgende Cmdlet in SharePoint-Verwaltungsshell ausführen:
    
  ```
  
stop-service SPSearchHostController
  ```

2. Führen Sie auf den gleichen Servern folgenden Befehl an der Befehlszeile aus, wobei  _index manifest file_ der Pfad und Dateiname des Manifests Index ist, die Sie in den Sicherungsvorgang erstellt haben.
    
  ```
  betest.exe /v /r /d "destination backup folder" /s "backup log file" /x "index manifest file"
  ```

3. (Optional) Stellen Sie sicher, dass die Ordnernamen und Größen übereinstimmen, die Sie in den Sicherungsvorgang aufgezeichnet.
    
  
4. Benennen Sie für jede Indexkomponente Daten unter den Datenordner, indem Sie folgende Schritte:
    
1. Führen Sie das folgende Cmdlet in SharePoint-Verwaltungsshell.
    
  ```
  Get-SPEnterpriseSearchVssDataPath
  ```

2. Tragen Sie anhand der Ausgabe des Cmdlets den letzten Teil der einzelnen GUID. Beispielsweise ist eine Zeile der Ausgabe  `IndexComponentGroup_e255918b-6ab0-4d7c-8049-720b2744c62f`, zeichnen Sie 720b2744c62f auf.
    
  
3. Navigieren Sie zu  `C:\\Program Files\\Microsoft Office Servers\\15.0\\Data\\Office Server\\Applications\\Search\\Nodes\\24488A\\IndexComponentN\\storage\\data`, wobei  *N*  die Anzahl der eine Indexkomponente ist, im **Datei-Explorer** (oder **Windows-Explorer** unter Windows Server 2008).
    
  
4. Jeder dieser Ordner ist einen Unterordner, deren Namen mit "SP", gefolgt von 12 hex-Ziffern, gefolgt von einer Version Zahl beginnt. Benennen Sie für jede der folgenden Unterordner, bei denen die 12 hex-Ziffern eines der Endung GUID übereinstimmen, die Sie im vorherigen Schritt notiert haben den Unterordner in Importindex. Im als fortlaufendes Beispiel würden Sie die Unterordner  `SP720b2744c62f.1.I.1.0` inImportindexumbenennen.
    
  
5. Neustart der Hostcontroller service entweder in **Verwaltung > Dienste**, oder indem Sie das folgende Cmdlet in SharePoint-Verwaltungsshell ausführen:
    
  ```
  start-service SPSearchHostController
  ```

6. Stellen Sie sicher, dass die Index Daten Ordnernamen wieder auf den vorherigen Namen wiederhergestellt haben. (In der als fortlaufendes Beispiel wäre "" SP720b2744c62f.1.I.1.0 ".)
    
  
8. (Optional) Stellen Sie sicher, dass die Größe der **IndexComponent** Ordner die Größen entsprechen, die Sie in den Sicherungsvorgang notiert haben.
    
  
9. Starten Sie die SSA neu.
    
  
10. Führen Sie das folgende Cmdlet in SharePoint-Verwaltungsshell, um sicherzustellen, dass der Suchdienst für die Anwendung ordnungsgemäß ausgeführt wird, auf den betroffenen Servern:
    
  ```
  Get-SPEnterpriseSearchStatus
  ```

11. Stellen Sie sicher, dass Zuführung und für neue Dokumente durchsuchen funktioniert. Überprüfen Sie die Größe des Indexes beispielsweise mithilfe der Abfrage "Größe > = 0". Außerdem ein neues Dokument hinzufügen, und stellen Sie sicher, dass es durchsuchbar ist.
    
  

## Beispiel-Manifestdateien
<a name="Examples"> </a>

 **Manifestdatei SSA**
  
    
    

```XML
<BETest>
  <Writer writerid="da452614-4858-5e53-a512-38aab25c61ad">
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\2e1f9435-d714-4bcb-be8d-ae1214e2ea22" componentName="SearchAppOffice" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\b8bb09b8-a823-43b0-a131-7bd5464f91fb" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\20c0c0b5-2086-4b16-8ce8-2cecb5186ebe" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\15004c47-21ca-441e-80fe-9e068ef4ad14" componentName="SearchAppOffice_LinksStore" />
  </Writer>
  <Writer writerid="a65faa63-5ea8-4ebc-9dbd-a0c4db26912a">
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_LinksStore" />
  </Writer>
</BETest>

```

 **Index-Manifestdatei**
  
    
    



```XML

<BETest>
  <Writer writerid="da452614-4858-5e53-a512-38aab25c61ad">
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\cfbddb07-2409-4b3d-997b-ee1b936c3dbd" componentName="IndexComponentGroup_3bca1050-c15a-4987-93dc-8f911d35a0ba" />
  </Writer>
  <Writer writerid="0ff1ce15-0201-0000-0000-000000000000">
    <Component logicalPath="" componentName="IndexComponentGroup_3bca1050-c15a-4987-93dc-8f911d35a0ba" />
  </Writer>
</BETest>
```


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [SharePoint Foundation und der Volumeschattenkopie-Dienst](http://msdn.microsoft.com/library/adae101a-078e-40b9-9cfa-db2cfb10270a%28Office.15%29.aspx)
    
  

