---
title: Vorgehensweise durchforsten zugeordneter externe Inhaltstypen in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 187ec42e-f749-4e22-abef-1df604143063
---


# Vorgehensweise: durchforsten zugeordneter externe Inhaltstypen in SharePoint 2013
In diesem Artikel lernen Sie die suchspezifischen Eigenschaften im Business Data Connectivity (BDC)-Dienst-Metadatenmodell für das Durchforsten von Zuordnungen und die verschiedenen Benutzerumgebungen kennen, die Sie aktivieren können.
## Durchforsten des zugeordneten externen Inhaltstyps
<a name="HowToCrawlAssociations_CrawlingAssociatedExternalTypes"> </a>

Microsoft Business Connectivity Services (BCS) können Sie zwei verwandte externe Inhaltstypen, verknüpfen, der dann Sie verwandten externen Inhalte abgerufen werden sollen können. Beispielsweise können Sie externen Inhalte von zwei SQL Server Datenbank Datenbanktabellen basierenden externen Inhaltstypen abgerufen werden, die auf Fremdschlüsseln basieren. Dieses Konzept der Verknüpfung von zwei verwandte externer Inhaltstypen wird als eine  *Zuordnung*  bezeichnet. Weitere Informationen zu Zuordnungen finden Sie unter [Hinzufügen von Zuordnungen zwischen externen Inhaltstypen](http://msdn.microsoft.com/library/791e95ab-9b3c-413b-be12-bd0e59962c93%28Office.15%29.aspx).
  
    
    
Im Kontext von Suche Connector Framework wird der externe quellinhaltstyp eines Association-Elements als den externen Inhaltstyp für das übergeordnete bezeichnet. Der Crawler Suche kann durchforstet werden externe Inhaltstypen, die das übergeordnete Element auf zwei Arten zugeordnet sind: als Anlagen oder als untergeordnete Elemente. Diese Zuordnungen externer Inhaltstypen wirken sich auf Folgendes:
  
    
    

- Benutzerumgebung
    
  
- Inkrementelle Durchforstungen
    
  
- Verarbeitung des Löschens von Durchforstungen
    
  

### Auswirkungen auf die Benutzerumgebung durch Zuordnungen externer Inhaltstypen

Ein untergeordneter Inhaltstyp hat ein eigene Suchergebnis-URL und Profilseite, nachdem die Profilseite erstellt wurde. Die Suchergebnis-URL ist die URL, die angezeigt wird, wenn der Benutzer in den Daten des untergeordneten externen Inhaltstyps einen Begriff sucht.
  
    
    
Der externe Inhaltstyp einer Anlage hat keine eigene Suchergebnis-URL. Wenn der Benutzer im externen Element **Anlage** einen Begriff sucht, wird stattdessen die URL für den übergeordneten externen Inhaltstyp angezeigt. Sie können diese URL auf die Profilseiten-URL des übergeordneten Inhaltstyps festlegen. Die Profilseite für den übergeordneten externen Inhaltstyp enthält alle Felder des externen Inhaltstyps **Anlage**, die vom Zuordnungsnavigator zur Verfügung gestellt werden.
  
    
    

### Auswirkungen auf inkrementelle Durchforstungen durch Zuordnungen externer Inhaltstypen

Untergeordnete externe Elemente werden erneut durchforstet und für zeitstempelbasierte inkrementelle Durchforstungen aktualisiert werden, wenn der Zeitstempel des untergeordneten externen Elements ändert.
  
    
    
Für externe Inhaltstypen vom Typ **Anlage** wird der Zeitstempel des übergeordneten externen Elements als Zeitstempel des externen Elements **Anlage** interpretiert. Änderungen am externen Element **Anlage** werden bei einer inkrementellen Durchforstung nur berücksichtigt, wenn sich der Zeitstempel des übergeordneten externen Elements ändert.
  
    
    

### Auswirkungen auf die Verarbeitung des Löschens von Durchforstungen durch Zuordnungen externer Inhaltstypen

Bei der Verarbeitung des Löschens Wenn des übergeordneten externen Inhaltstyps aus dem Index gelöscht wird, löscht der Crawler Suche die zugeordnete Anlage externe Inhaltstypen und untergeordnete externe Inhaltstypen aus dem Index.
  
    
    

## Durchforsten des zugeordneten externen Inhaltstyps "Anlagen"
<a name="HowToCrawlAssociations_CrawlingAttachments"> </a>

Fügen Sie zum Markieren einer Zuordnung, dass sie als Anlage durchforstet wird, die **AttachmentAccessor**-Eigenschaft wie folgt der Instanz der **Association**-Methode hinzu.
  
    
    

```XML

<Association Name="AttachmentsNavigate Association" Type="AssociationNavigator" ...>
    <Properties>
        <Property Name="ForeignFieldMappings" Type="System.String">....... </Property>
        <Property Name="AttachmentAccessor" Type="System.String">x</Property>
    </Properties>
    <SourceEntity Namespace="ParentExternalContentType" Name="Parent" />
    <DestinationEntity Namespace="AttachmentExternalContentType" Name="Attachment External Content Type" />
</Association>
```


> **HINWEIS**
> Sie können einen beliebigen Wert für die **AttachmentAccessor** -Eigenschaft angeben. Dieser Wert wird von Suche nicht überprüfen.
  
    
    


## Durchforsten zugeordneter externer Inhaltstypen als untergeordnete externe Inhaltstypen
<a name="HowToCrawlAssociations_CrawlingChildExternalTypes"> </a>

Fügen Sie zum Markieren einer Zuordnung, dass sie als untergeordneter Inhaltstyp durchforstet wird, die **DirectoryLink**-Eigenschaft wie folgt der Instanz der **Association**-Methode hinzu.
  
    
    

```XML

<Association Name="ChildrenNavigator Association" Type="AssociationNavigator" ...>
    <Properties>
        <Property Name="DirectoryLink" Type="System.String">x</Property>
    </Properties>
    <SourceEntity Namespace="ParentExternalContentType" Name="Parent" />
    <DestinationEntity Namespace="ChildExternalContentType" Name="Child External Content Type" />
</Association>
```


> **HINWEIS**
> Sie können einen beliebigen Wert für die **DirectoryLink** -Eigenschaft angeben. Dieser Wert wird von Suche nicht überprüfen.
  
    
    


## Zusätzliche Ressourcen
<a name="SP15crawlects_addlresources"> </a>


-  [Connector Framework für die Suche in SharePoint 2013](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [Hinzufügen von Zuordnungen zwischen externen Inhaltstypen](http://msdn.microsoft.com/library/791e95ab-9b3c-413b-be12-bd0e59962c93%28Office.15%29.aspx)
    
  
-  [Association-Element in MethodInstances (BDCMetadata-Schema)](http://msdn.microsoft.com/library/9659a1f5-1b12-03ef-f9e3-5c9904cc5dd0%28Office.15%29.aspx)
    
  
-  [Step 4 (Optional): Define Associations](http://msdn.microsoft.com/library/6bc55f46-459a-4986-8744-8c6c5f45097b%28Office.15%29.aspx)
    
  

