---
title: Add-in-bezogenen externen Inhaltstypen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: a34cbbba-dc38-4d3d-b796-d54b5848bdfb
---


# Add-in-bezogenen externen Inhaltstypen in SharePoint 2013
Erfahren Sie mehr über externe Inhaltstypen, die installiert oder auf der Ebene-Add-Ins in SharePoint 2013 ausgelegt sind, und aktivieren Sie reichhaltige SharePoint-Add-Ins mit externen Datenquellen erstellen.
## Übersicht über die add-in-bezogenen externen Inhaltstypen in SharePoint 2013
<a name="Appscopedect_overview"> </a>

In SharePoint 2010 können Sie installieren und Verwenden von externen Inhaltstypen nur auf Farmebene. Daraufhin wird häufig Probleme für Entwickler, da auch für einfache Applications Administrator beteiligten aufgrund der Zugriffsrechte sein, die erforderlich sind musste, um auf Farmebene zu installieren.
  
    
    
In SharePoint 2013 sind Anwendungen im Wesentlichen in mehr autonomen Einheiten mit dem Namen -add-insisoliert. -Add-ins enthalten alle Ressourcen, die sie ausführen müssen. Dieser Ansatz ermöglicht eine aktive Anwendung auf aus anderen Anwendungen isoliert werden. Die Vorteile dieser Architektur sind wie folgt:
  
    
    

- Erstellen Sie add-ins, die an das neue Anwendungsmodell des SharePoint 2013 ausgerichtet werden.
    
  
- Erstellen Sie add-ins, die Zugriff auf externe Daten von SAP, Netflix, und proprietäre und andere Typen von Daten ohne im Zusammenhang mit der mandantenadministrator.
    
  
- Zugriff auf externe Anwendungen wird durch Business Connectivity Services (BCS), beibehalten, die eine konsistente und einheitliche Benutzeroberfläche bereitstellt, die von anderen SharePoint-Anwendungen verwendet werden kann.
    
  
Add-in-bezogenen externe Inhaltstypen ermöglichen den Zugriff auf externe Daten in einer app.
  
    
    

## Erforderliche Komponenten für die Arbeit mit der add-in-bezogenen externen Inhaltstypen
<a name="Appscopedect_Prereq"> </a>

Im folgenden sind die Anforderungen für die Entwicklung von externen Inhaltstypen, die auf der Ebene der Add-in-Bereich haben:
  
    
    

- Visual Studio 2012
    
  
- Office Developer Tools für Visual Studio 2012
    
  
- SharePoint 2013
    
  
Informationen dazu, wie Sie Ihre SharePoint-Entwicklungsumgebung einrichten, finden Sie unter  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

### Add-in-bezogenen externen Inhaltstyp essentials

Tabelle 1 enthält einige wichtige Konzepte, denen Sie mit vertraut beim Arbeiten mit der add-in-bezogenen externen Inhaltstypen sein sollten.
  
    
    

**In Tabelle 1. Kernkonzepte für das Verständnis von add-in-bezogenen externer Inhaltstypen**


|**Artikel**|**Beschreibung**|
|:-----|:-----|
| [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |Erfahren Sie, wie BCS externen Inhaltstypen erstellen. <br/> |
| [SharePoint-Add-Ins](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |In diesem Artikel erfahren Sie mehr über das neue Add-In-Modell in SharePoint 2013, das Sie zur Erstellung von Add-Ins verwenden können, die einfache, benutzerfreundliche Lösungen für Endanwender darstellen. <br/> |
| [Erste Schritte beim Erstellen von von SharePoint gehosteten SharePoint-Add-Ins](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx) <br/> |Informationen Sie zur Erstellung eines einfachen SharePoint-Hosting add-Ins mithilfe der Office Developer Tools für Visual Studio 2012. <br/> |
   

## Was können Sie mit der add-in-bezogenen externen Inhaltstypen?
<a name="Appscopedect_Tasks"> </a>

Der Hauptgrund für das Hinzufügen eines Add-in-bezogenen externen Inhaltstyps ist für den Zugriff auf externe Daten aus einer einzelnen-Add-in. Hiermit können Sie folgende Aktionen ausführen:
  
    
    

- Einschränken des Zugriffs auf externe Inhaltstypen zu einer bestimmten app.
    
  
- Bereitstellen von externen Inhaltstypen in einer app.
    
  

### Erstellen von add-in-bezogenen externen Inhaltstypen
<a name="Appscopedect_createect"> </a>

Das Konzept eines Katalogs dateibasierten Metadaten wurde in SharePoint 2010 eingeführt. Es können Sie angeben, dass eine Datei mit dem XML benötigt, um externe Inhaltstypen zu definieren. Diese Datei in eine WSP-Paket bereitgestellt werden kann und bezieht sich nur auf die Anwendung, der sie für ausgelegt ist. Mithilfe dieser Metadatendatei können externe Inhaltstypen auf die-Add-in-Ebene beschränkt.
  
    
    
In SharePoint 2013 wurde **SPListDataSource** geändert, um eine Eigenschaft hinzuzufügen, die den Bereich der Anwendung angibt.
  
    
    
Diese Klasse dient als die Brücke zwischen **SPList** und einer externen Liste. Verwenden Sie die zugeordneten **SPList** Entitätsfelder und Daten abgerufen. Eine Instanz des **SPListDataSource** aus der **HasExternalDataSource** -Eigenschaft abrufen. Wenn **HasExternalDataSource** nicht null ist, ist das **SPList** -Objekt Daten außerhalb SharePoint 2013.
  
    
    
Wenn Sie einen Add-in-bezogenen externen Inhaltstyp hinzufügen möchten, ist diese Eigenschaft auf **Add-in**festgelegt.
  
    
    
Die **MetadataCatalogFileName** -Eigenschaft wird verwendet, um die BDC-Modelldatei zu definieren, die die Definition des externen Inhaltstyps enthält. Diese Eigenschaft kann deklarativ oder programmgesteuert definiert werden, aber nicht in der SharePoint-Benutzeroberfläche (UI).
  
    
    
Im folgenden Beispiel wird veranschaulicht, wie die **MetadataCatalogFileName** -Eigenschaft deklarativ festgelegt.
  
    
    



```XML

<DataSource>
  <Property Name="Entity" Value="Customer" />
  <Property Name="EntityNamespace" Value="SAP" />
  <Property Name="LobSystemInstanceName" Value="SAPClient1" />
  <Property Name="SpecificFinder" Value="ReadCustomer" />
  <Property Name=" MetadataCatalogFileName" Value="BDCMetadata.bdcm" />
</DataSource>
```


> **HINWEIS**
> Websiteadministratoren können, mit dem App-bezogenen Kampagnentyp add-ins installiert, aber nur Websitesammlungsadministratoren können Erteilen von Berechtigungen für Apps für BCS-Verbindungen verwenden.
  
    
    


### Bereitstellen eines Add-in-bezogenen externen Inhaltstyps in einer benutzerdefinierten Funktion in eine WSP-Datei
<a name="Appscopedect_deployect"> </a>

Sie können ein BDC-Modell in eine WSP-Datei für die Bereitstellung einschließen. Im folgenden Beispiel wird veranschaulicht, wie ein BDC-Modell in der app werden soll.
  
    
    

```XML

<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <BdcModel Path="BDCMetadata.bdcm">
  </BdcModel>
</Elements>

```


> **WICHTIG**
> Nur ein BDC-Modelldatei kann pro-add-ins eingeschlossen werden. In diesem Beispiel wird der Dateiname BDCMetadata.bdcm ist, kann die Modelldatei einen beliebigen Namen Ihrer Wahl, solange der Dateiname, die entspricht sich im **Path** -Attribut des BDC-Modelldatei tatsächlich entsprechen.
  
    
    


> **HINWEIS**
> Nur Open Data Protocol (OData) Verbindungen sind für add-in-bezogenen externen Inhaltstypen zulässig.
  
    
    


### Festlegen von Anmeldeinformationen für ein externes system
<a name="Appscopedect_deployect"> </a>

Um Daten für eine sichere externe System zugreifen zu können, müssen Sie das BDC-Modell mit den entsprechenden Anmeldeinformationen konfigurieren.
  
    
    
Im folgenden Beispiel wird gezeigt, wie durch Bearbeiten der Datei "Elements.xml" der app Sicherheitsanmeldeinformationen für ein externes System add-in-bezogenen externen Inhaltstypen festgelegt.
  
    
    



```XML

<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <BdcModel Path="BDCMetadata.bdcm">
    <LobSystem Name="SAP">
       <LobSystemInstance Name="SAPInst" RequireCredentials="true" CredentialsDescription="Credentials to connect to SAP"/>
    </LobSystem>
    <LobSystem Name="SQL">
       <LobSystemInstance Name="App Database" DataSource="SQL-Azure" RequireCredentials="true" />
    </LobSystem>
  </BdcModel>
</Elements>

```


## Inhalt dieses Abschnitts
<a name="Appscopedect_inthissection"> </a>


-  [Vorgehensweise: erstellen ein Add-in-bezogenen externes Inhaltstyps in SharePoint 2013](how-to-create-an-add-in-scoped-external-content-type-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Zugriff auf externe Daten mit REST in der SharePoint 2013](how-to-access-external-data-with-rest-in-sharepoint-2013.md)
    
  

## Zusätzliche Ressourcen
<a name="Appscopedect_Addres"> </a>


-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Business Connectivity Services-Programmierreferenz für SharePoint 2013](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint-Add-Ins](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [Externe Ereignisse und Warnungen in SharePoint 2013](external-events-and-alerts-in-sharepoint-2013.md)
    
  
-  [Was ist neu in Business Connectivity Services in SharePoint 2013](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Erste Schritte mit den Business Connectivity Services in SharePoint 2013](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

