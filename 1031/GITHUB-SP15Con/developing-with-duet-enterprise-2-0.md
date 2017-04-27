---
title: Bei der Entwicklung mit Duet Enterprise 2.0
ms.prod: SHAREPOINT
ms.assetid: c3ef38aa-559e-4832-95c7-75e222c77624
---


# Bei der Entwicklung mit Duet Enterprise 2.0

## Übersicht
<a name="Overview"> </a>

Duet Enterprise 2.0 ist die neueste Version einer gemeinsamen Initiative zwischen Microsoft- und SAP, SharePoint-Benutzern die Möglichkeit zum Arbeiten mit Daten aus SAP-Systemen zu ermöglichen. Komponenten von SAP sowie SharePoint 2013 und SharePoint Online kombiniert. Es ermöglicht Entwicklern die Möglichkeit zum Erstellen von Komponenten, die Benutzern ermöglichen, Daten aus SAP-Systemen in der vertrauten SharePoint-Umgebung zu bringen.
  
    
    

## Features von Duet Enterprise 2.0
<a name="Overview"> </a>

Wenn ordnungsgemäß installiert und konfiguriert ist, wird Duet Enterprise 2.0 folgende Features zu ermöglichen:
  
    
    

- Sie können mit Daten in SAP-Systemen in SharePoint mithilfe von Geschäftsdaten-Webparts, externe Listen und benutzerdefinierten Komponenten arbeiten.
    
  
- Verwenden von SAP-Daten in SharePoint 2013 ohne Code mithilfe der integrierte Komponenten.
    
  
- Verwenden von SAP-Systeme innerhalb einer app, die Berichte.
    
  
- Verwenden Sie spezielle Webparts zum Hinzufügen von SAP-Informationen zu SharePoint-Seiten mit Duet Enterprise 2.0 installiert
    
  
- Verwenden von SAP-Workflow in einer app.
    
  
- Entwickler können mithilfe der clientseitigen JavaScript zum interagieren mit SAP externe Daten verwenden.
    
  
- Sichern Sie Daten mithilfe von OAuth zur Authentifizierung.
    
  

## Einrichten der Entwicklungsumgebung
<a name="SettingUp"> </a>

Entwickeln von SharePoint-Add-Ins mit Duet Enterprise 2.0, ist in den meisten Fällen genau gleicht dem standard SharePoint-Add-Ins erstellen. Sie können entweder die browserbasierte Napa Office 365-Entwicklungstools Tools zum Erstellen und bereitstellen, oder können Sie Visual Studio zum Erweitern Ihrer apps und im Rahmen der Visual Studio-IDE robuste arbeiten.
  
    
    

## Hinzufügen von externen Inhaltstypen
<a name="AddingECT"> </a>

Um die externen Daten, die diese auf dem SAP-System zugreifen zu können, müssen Sie einen externen Inhaltstyp hinzuzufügen. Da SAP-Daten über OData-Endpunkte verfügbar gemacht werden, können die automatische Generierung Tools in Visual Studio installiert auf  [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md) verwendet werden, die auf der Ebene der app ausgelegt ist.
  
    
    
Führen Sie die folgenden Schritte aus, um einen externen Inhaltstyp zu erstellen:
  
    
    

### Erstellen eines externen Inhaltstyps aus einem SAP-OData-Endpunkt


1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Hinzufügen** und **Inhaltstypen für externe Datenquelle** aus.
    
  
2. Geben Sie auf der Seite **OData-Quelle anzugeben** die URL der Duet Enterprise-Workflow-Dienst.
    
  
3. Wählen Sie einen Namen für die OData-Quelle.
    
  
4. Wählen Sie die Entitäten, die erforderlich sind.
    
  
5. Wählen Sie **Fertig stellen** aus.
    
  
Visual Studio erstellt einen neuen Ordner mit dem Namen externer Inhaltstypen Sie das neu erstellte BDC-Modell finden.
  
    
    

## Konfigurieren des BDC-Modells
<a name="ConfiguringProject"> </a>

Stellen Sie das Projekt für die Verwendung der wichtigste wird die **ODataExtensionProvider** -Eigenschaft des BDC-Modells hinzugefügt. Diese Eigenschaft definiert den Erweiterung-Anbieter, der BCS mit den SAP-Erweiterungen für das Erstellen von app-Code benötigt bereitstellt.
  
    
    
In diesem Beispiel werden die Eigenschaften gezeigt, das BDC-Modell hinzugefügt:
  
    
    



```XML

<LobSystem Type="OData" Name="LOB_SYSTEM_NAME">
                     <Properties>
                          <Property Name="ODataServiceMetadataUrl" Type="System.String">
                               https://<DUET_METADATA_URL>:443/sap/opu/odata/sap/ 
                               ZANDY_PO_HEADER_SRV/$metadata</Property>
                          <Property Name="ODataServicesVersion" Type="System.String">2.0</Property>
                          <Property Name="ODataExtensionProvider" Type="System.String"> 
                               OBA.Server.Canary.ObaOdataServerExtensionProvider, 
                               OBA.Server.SSOProvider, 
                               Version=15.0.0.0, 
                               Culture=neutral, 
                               PublicKeyToken=71e9bce111e9429c</Property>
                          <Property Name="TraceHeader" Type="System.String">SAP-PASSPORT</Property>
                     </Properties>

```


## Entwickeln von benutzerdefinierten apps mithilfe von Duet Starter services
<a name="UsingDuetStarterServices"> </a>

Duet Enterprise 2.0 installiert mehrere Starter Services im Dateisystem auf dem Server SharePoint 2013. Die Dateien befinden sich in einer Standardinstallation unter C:\\Program c:\\programme\\duet Enterprise\\2.0\\Solutions\\Starter Services. Dazu gehören:
  
    
    

- OBACustomerWorkspace
    
  
- OBAOrderToCash
    
  
- OBAPortal
    
  
- OBAProductCenter
    
  
Jede dieser Lösungen enthält WSP-Dateien, Lösung und andere unterstützenden Dateien benötigt, sie zu implementieren.
  
    
    
Diese Lösungen werden kann, finden Sie unter Was mit Duet Enterprise 2.0 ausgeführt werden können und was die Entwicklung Muster sind, aber nicht für die Verwendung in SharePoint-Add-Ins unterstützt werden.
  
    
    

## Zusätzliche Ressourcen
<a name="ConNavExample_resources"> </a>


-  [Duet Enterprise für Microsoft SharePoint und SAP Server 2.0](http://technet.microsoft.com/en-us/library/ff972436.aspx)
    
  
-  [Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [Visual Studio Developer Center](http://msdn.microsoft.com/en-us/vstudio/default)
    
  
-  [Office-Entwicklung mit Visual Studio](http://msdn.microsoft.com/en-us/office/hh133430)
    
  

