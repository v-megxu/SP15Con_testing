---
title: Erstellen von Diensten-Hybrid-apps für SharePoint
ms.prod: SHAREPOINT
ms.assetid: 311f036e-3442-4497-b35e-442b665462d3
---


# Erstellen von Diensten-Hybrid-apps für SharePoint
Informationen Sie zu den Prozess der entwickeln und Bereitstellen von apps für SharePoint 2013-Diensten hybridlösungen.
## Hybridkonnektivität in SharePoint 2013 und SharePoint Online
<a name="bk_hybridconnectivity"> </a>

Als Unternehmen mit SharePoint Online zu verschieben, benötigen sie eine Möglichkeit, große Mengen von proprietäre Daten sichere verfügbar zu machen. Um diese Herausforderung zu lösen, SharePoint 2013 hybridkonnektivität eingeführt.
  
    
    
"Übertragen" Business Connectivity Services (BCS) Hybrid-Konnektivität kann SharePoint 2013 Nutzen von Daten, die lokal, innerhalb Unternehmensfirewalls, und verschiedene Formen der Authentifizierung gesichert. Mit hybride Connectivity Funktionen können SharePoint Online diese Daten sicher über das Internet zugreifen als wäre es im gleichen internen Netzwerk. Nachdem hybridkonnektivität konfiguriert wurde, können Benutzer mit Daten arbeiten, die innerhalb des Unternehmens-Infrastruktur gesichert wird. Sie können zugreifen und bearbeiten die Daten entsprechend den Berechtigungen, die ihnen in SharePoint 2013 gewährt wurden.
  
    
    
Eine vollständige Beschreibung der Vorgehensweise zum Konfigurieren einer hybridlösung arbeiten finden Sie unter  [Hybrid für SharePoint Server 2013](http://technet.microsoft.com/en-us/library/jj838715.aspx). Diese Artikelreihe führt Sie durch die gesamte erforderliche Konfigurieren von Datenquellen, Reverseproxys, Suche, Sicherheit, Netzwerke und alles, was sonst noch benötigt, um die End-to-End-Szenario einzurichten.
  
    
    

> **VORSICHT**
> Um eine SharePoint-hybridumgebung konfigurieren, benötigen Sie eine Kombination von Experten Fähigkeiten und erhebliche praktische Erfahrung mit SharePoint Server 2013, SharePoint Online, und verwandte Produkte und -Technologien. Es wird empfohlen, dass Sie ausschließlich zu Microsoft Consulting Services technische Anleitungen und während der Entwurf und Bereitstellung Ihrer hybridumgebung unterstützen.> Weitere Informationen finden Sie unter  [Microsoft Services](http://www.microsoft.com/en-us/microsoftservices/deploy.aspx).
  
    
    

Damit Sie eine app erstellen können, die Daten aus einer internen Datenquelle über BCS und die Verbindung Hybrid nutzt, wird in diesem Artikel davon ausgegangen, dass Sie die Verfahren zum Konfigurieren der hybridumgebung bereits durchgeführt haben.
  
    
    

## Konnektivität-Hybrid-apps erstellen
<a name="bkmk_CreatingHybridConnectivityApps"> </a>

Erstellen einer hybriden SharePoint-Add-In ist im Wesentlichen das Erstellen eine beliebige SharePoint-Add-In.
  
    
    
Führen Sie diese Schritte zum Erstellen einer Hybrid-app:
  
    
    

-  [Vorbereiten der Datenquelle](#bkmk_PrepareDataSource)
    
  
-  [Erstellen einer SharePoint-Add-In](#bkmk_CreateAnApp)
    
  
-  [Erstellen eines externen Inhaltstyps](#bkmk_CreateECT)
    
  
-  [Bereitstellen der Hybrid-app](#bkmk_DeployHybridApp)
    
  

### Vorbereiten der Datenquelle
<a name="bkmk_PrepareDataSource"> </a>

In den meisten Fällen, die Datenquelle bereits vorhanden ist und eine beliebige Anzahl von Geschäftsanwendungen bedient. Diese Daten können jedoch nur innerhalb der Unternehmens Sicherheitsinfrastruktur zur Verfügung sein. Wenn Ihre Daten auf einem Server befindet sich innerhalb des Unternehmens-Firewall vorhanden, oder mit anderen Mitteln geschützt ist, besteht der nächste Schritt auf Daten, BCS, verfügbar machen, die auch innerhalb der Firewall gespeichert ist. Ein Netzwerkgerät ist so konfiguriert, dass um Anrufe von SharePoint Online an der internen SharePoint-Farm zu übersetzen. Dieses Gerät wird als "Reverseproxy" bezeichnet und ermöglicht die SharePoint-Add-In in der Cloud Aufruf von BCS befindet sich innerhalb der Firewall befinden. BCS behandelt die Datenkonnektivität von dort aus.
  
    
    
Diese Daten zum BCS zur Verfügung zu stellen, sollten Sie es als einer OData-Quelle verfügbar machen. Zu diesem Zweck erstellen eine Website von Internetinformationsdienste (Internet Information Services, IIS), die als host für den Dienst und ermöglichen die Kommunikation mit der Datenquelle über OData und Representational State Transfer (REST) Endpunkte BCS.
  
    
    
Um einen OData-Endpunkt zu erstellen, müssen Sie diese Schritte für die Erstellung einer Datendienst Windows Communication Foundation (WCF).
  
    
    

### Erstellen ein WCF-Datendiensts


1. Erstellen eine IIS-Website mit mindestens Microsoft .NET Framework 4. Sichern Sie die Website mithilfe der Standardauthentifizierung.
    
    > **HINWEIS**
      > Es ist nicht erforderlich für SharePoint auf diesem Server installiert werden soll. Tatsächlich empfiehlt sich aus Gründen der Einfachheit und Leistung, wenn SharePoint nicht auf dem Server installiert ist, die den WCF-Dienst gehostet wird.
2. Erstellen Sie ein neues Projekt im Visual Studio 2012 mithilfe der Vorlage **Leere ASP.NET-Webanwendung**.
    
  
3. Fügen Sie im **Projektmappen-Explorer** ein neues **ADO.NET Entitätsdatenmodell** hinzu.
    
  
4. Wählen Sie im **Entity Data Model Wizard** die **aus Datenbank generieren**.
    
  
5. Wählen Sie eine vorhandene Verbindung aus, oder erstellen Sie einen neuen Anwendungspool.
    
  
6. Geben Sie die URL und die Verknüpfung Security-Informationen.
    
  
7. Wählen Sie die Elemente, die im Modell enthalten sein sollen, und wählen Sie **Fertig stellen**.
    
  
8. Fügen Sie im **Projektmappen-Explorer** erneut einen neuen **WCF Data Service** mithilfe der Visual Studio-Vorlage.
    
  
9. Nennen Sie den Data-Dienst, und wählen Sie **Weiter**.
    
    Zu diesem Zeitpunkt das Entitätsmodell erstellt werden, und die resultierenden Klassen werden in Ihrem Projekt enthalten sein.
    
  
10. Set Sicherheitsmodell für die Personen, und Ersetzen Sie die  `/* TODO: put your data source class name here */` durch den Klassennamen der Entität erstellt Sie die soeben erstellte und Angeben der Entitäten, die Sie Berechtigungen erteilen möchten.
    
  
Ein vollständiges Lernprogramm dafür, wie Sie dies einrichten finden Sie hier:
  
    
    

-  [Erste Schritte mit OData-Teil 1: Erstellen einer OData-Dienst](http://msdn.microsoft.com/en-us/data/gg601462)
    
  
-  [Schnellstart (WCF Data Services)](http://msdn.microsoft.com/en-us/library/cc668796.aspx)
    
  

### Erstellen einer SharePoint-Add-In
<a name="bkmk_CreateAnApp"> </a>

Einer der Annahmen, die wir hier machen ist, dass Sie Ihre app innerhalb der Unternehmensfirewall entwickeln. Dies stellt ein Szenario mit einem Entwickler arbeiten für ein Unternehmen einen Computer hinter den Schutz der Sicherheitsinfrastruktur, entwickeln und Testen der app, bis es bereitgestellt werden kann vor würde. Dies vereinfacht das Herstellen einer Verbindung mit der Datenquelle aus Visual Studio und Office Developer Tools für Visual Studio 2013 verwendet, um den externen Inhaltstyp im nächsten Schritt automatisch zu generieren.
  
    
    

### Zum Erstellen einer neuen app


1. Öffnen Sie Visual Studio 2012 auf Ihrem Entwicklungscomputer, die Office Developer Tools für Visual Studio 2013 und SharePoint 2013 installiert hat.
    
  
2. Erstellen Sie eine neue app für SharePoint.
    
  
3. Geben Sie den Namen der app, die lokale SharePoint-URL, die zum Testen Ihrer Website gehostet wird und wie Sie die app gehostet werden soll. Wählen Sie auf **Fertig stellen**.
    
  

### Erstellen eines externen Inhaltstyps
<a name="bkmk_CreateECT"> </a>

Um dem Projekt eine BDC-Modell oder externen Inhaltstyp hinzuzufügen, die folgenden Schritte aus.
  
    
    

### So fügen Sie einen externen Inhaltstyp hinzu


1. Mit dem neuen Projekt weiterhin öffnen Sie, öffnen Sie das Kontextmenü für die Lösung, und wählen Sie **Hinzufügen** und **Inhaltstypen für eine externe Datenquelle**.
    
  
2. Die erste Seite des Assistenten wird verwendet, um die URL des Datendiensts anzugeben. Geben Sie die URL des OData-Diensts, die Sie mit verbinden möchten, klicken Sie auf der Seite **OData-Quelle anzugeben**. Die URL sollte etwa folgendermaßen aussehen: **http://services.odata.org/Northwind/Northwind.svc/**.
    
  
3. Wählen Sie einen Namen für die OData-Quelle und dann **Weiter** aus.
    
  
4. Es wird eine Liste der Datenentitäten, die vom OData-Dienst verfügbar gemacht werden angezeigt. Stellen Sie sicher, dass das Kontrollkästchen **Listeninstanzen für die ausgewählten Datenentitäten erstellen** ausgewählt ist.
    
  
5. Wählen Sie eine oder mehrere Entitäten, und wählen Sie **Fertig stellen**.
    
  
6. Schritte vor der Bereitstellung Letztes ist die URL in der Datei neu erstellten externen Inhaltstyp zu ändern.
    
    Öffnen Sie die .ect-Datei in einem XML-Editor.
    
  
7. Ändern Sie die  `ODataServiceMetadataUrl` -Eigenschaft auf die URL auf dem ermöglicht den Zugriff über den Reverseproxy geleitet.
    
  
8. Ändern Sie die  `ODataServiceUrl` -Eigenschaft mit der URL, die über den Reverseproxy Zugriff zulässt.
    
  
Informationen zum Hinzufügen eines OData-basierten externen Inhaltstyps finden Sie unter  [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md).
  
    
    

### Bereitstellen der Hybrid-app
<a name="bkmk_DeployHybridApp"> </a>

Wenn Ihre app bereitgestellt wird, können Sie eine Reihe von Auswahlmöglichkeiten. Sie können direkt an eines Mandanten mit F5-Bereitstellung bereitstellen oder Sie können mithilfe der Features zum Veröffentlichen von Visual Studio zum Erstellen einer Datei am Seitenrand packen. Diese Datei kann, der mandantenadministrator SharePoint Online zugewiesen und hochgeladen werden.
  
    
    
Informationen zum Bereitstellen von SharePoint-Add-Ins finden Sie unter den folgenden:
  
    
    

-  [Bereitstellen und Installieren von SharePoint-Add-Ins: Methoden und Optionen](http://msdn.microsoft.com/library/d15a74a7-3c10-485a-9885-7ef11aaa0d90%28Office.15%29.aspx)
    
  
-  [Veröffentlichen von SharePoint-Add-Ins mithilfe von Visual Studio](http://msdn.microsoft.com/library/8137d0fa-52e2-4771-8639-60af80f693bb%28Office.15%29.aspx)
    
  
Außerdem können Sie die BDCM-Datei für den externen Inhaltstyp erstellt und zu extrahieren, die auf jeder Ebene oberhalb der app verwendet werden. Dies ist in  [Vorgehensweise: Konvertieren ein Add-in-bezogenen externes Inhaltstyps in mandantenbereichsbezogenen](how-to-convert-an-add-in-scoped-external-content-type-to-tenant-scoped.md)veranschaulicht.
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Hybridlösung für SharePoint Server 2013](http://technet.microsoft.com/en-us/library/jj838715.aspx)
    
  
-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Veröffentlichen von SharePoint-Add-Ins mithilfe von Visual Studio](http://msdn.microsoft.com/library/8137d0fa-52e2-4771-8639-60af80f693bb%28Office.15%29.aspx)
    
  

