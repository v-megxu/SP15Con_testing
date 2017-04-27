---
title: Gewusst wie Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: bc60ea49-c44e-4531-af62-06b8cf77d35d
---


# Gewusst wie: Erstellen eines externen Inhaltstyps aus einer OData-Quelle in SharePoint 2013
In diesem Artikel erfahren Sie, wie Sie Visual Studio 2012 verwenden, um eine veröffentlichte OData-Quelle zu erkennen und einen wieder verwendbaren externen Inhaltstyp für die Verwendung in Business Connectivity Services (BCS) in SharePoint 2013 zu erstellen.
## Voraussetzungen für das Erstellen von OData-basierten externen Inhaltstypen
<a name="bkmk_Prerequisites"> </a>

Zum Erstellen eines externen Inhaltstyps aus einer Open Data-Protokollquelle (OData) benötigen Sie Folgendes:
  
    
    

- Eine Instanz von SharePoint 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools für Visual Studio 2012
    
  
- Einen veröffentlichten OData-Dienst, der über das Internet verfügbar ist
    
  
Informationen zum Einrichten Ihrer SharePoint-Entwicklungsumgebung finden Sie unter  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

> **HINWEIS**
> SharePoint Designer 2013kann nicht für die automatische Generierung von BDC-Modellen aus einer OData-Quelle verwendet werden. Sie können stattdessen Visual Studio 2012 verwenden. 
  
    
    


### Kernkonzepte für das Arbeiten mit externen OData-Inhaltstypen

Die folgenden Artikel enthalten Informationen zu OData und dem OData-Connector in SharePoint 2013.
  
    
    

**Tabelle 1: Kernkonzeüte für externe OData-Inhaltstypen**


|**Artikeltitel**|**Beschreibung**|
|:-----|:-----|
| [Verwenden von OData-Quellen mit Business Connectivity Services in SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |Erfahren Sie mehr über die ersten Schritte beim Erstellen externer Inhaltstypen auf der Basis von OData-Quellen und wie Sie diese Daten in SharePoint oder Office-Komponenten verwenden.  <br/> |
| [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md) <br/> |Erfahren Sie mehr über externe BCS-Inhaltstypen und Voraussetzungen für deren Erstellung in SharePoint 2013.  <br/> |
   

## Erstellen eines OData-basierten externen Inhaltstyp
<a name="bkmk_CreatingODataECT"> </a>

Die folgenden Schritte zeigen, wie Sie Visual Studio 2012 zum Erstellen eines externen Inhaltstyps auf der Basis einer OData-Quelle verwenden.
  
    
    

### So erstellen Sie ein neues SharePoint-Add-In


1. Erstellen Sie in Visual Studio 2012 ein neues **App für SharePoint 2013**-Projekt, das sich unter dem Knoten **SharePoint 2013-Vorlage** befindet.
    
  
2. Benennen Sie Ihr Projekt, und wählen Sie **OK** aus.
    
  
3. Geben Sie zum Angeben der Einstellungen für SharePoint einen Namen für Ihre App und die URL des SharePoint 2013-Servers ein, den Sie für das Debuggen verwenden.
    
  
4. Wählen Sie **Fertig stellen** aus.
    
  
Nachdem das Projekt erstellt wurde, verwenden Sie das neue Tool für die automatische Generierung für OData-Quellen, und fügen Sie Ihrer App ein BDC-Modell für die OData-Quelle hinzu.
  
    
    

### So fügen Sie ein neues BDC-Modell hinzu


1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Hinzufügen** und **Inhaltstypen für externe Datenquelle** aus.
    
    Damit wird ein Assistent gestartet, der Ihnen hilft, die ausgewählte Datenquelle zu ermitteln und das BDC-Modell zu erstellen.
    
  
2. Auf der ersten Seite des Assistenten wird die URL des Datendiensts ermittelt. Geben Sie auf der Seite **OData-Quelle angeben** die URL des OData-Diensts ein, mit dem Sie eine Verbindung herstellen möchten. Die URL sollte etwa folgendermaßen aussehen: `http://services.odata.org/Northwind/Northwind.svc/`.
    
    > **HINWEIS**
      > Sie zeigen den Northwind-Dienst an, der in der Liste der Produzenten auf der  [Open Data Protocol-Website ](http://www.odata.org/ecosystem#liveservices) verfügbar ist.
3. Wählen Sie einen Namen für die OData-Quelle und dann **Weiter** aus.
    
  
4. Eine Liste von Datenentitäten, die von dem OData-Dienst verfügbar gemacht werden, wird angezeigt. Wählen Sie eine oder mehrere der Entitäten und dann **Fertig stellen** aus.
    
  

### So zeigen Sie die Struktur der Entitäten an


- Beachten Sie, dass Visual Studio einen neuen Ordner namens „Externe Inhaltstypen" erstellt hat. In diesem Ordner finden Sie einen Unterordner mit dem Namen der neuen Datenquelle. Wenn Sie diesen weiter erweitern, sehen Sie ein Element, das die von Ihnen ausgewählte Entität darstellt. Zum Anzeigen einer grafischen Übersicht über die Entitäten und deren Typen öffnen Sie die **ECT**-Datei, die Sie anzeigen möchten.
    
    Sie können auch den XML-Code der Entitäten anzeigen, indem Sie die ECT-Dateien in einem XML-Editor öffnen.
    
  

## Verwenden eines StreamAccessors für die OData-Quelle
<a name="bkmk_UseStreamAccessor"> </a>

Mit dem folgenden Code können Sie auf einen Datenstrom zugreifen, den der OData-Connector verwenden kann.
  
    
    

```cs

/*Invoke  Stream Accessor Method */
        internal void ExecuteStreamAccessorMethod(IEntityInstance entityInstance, string streamAccessorName)
        {
            this.Log.Comment("ExecuteStreamAccessorMethod enter");
            this.Log.Comment("streamAccesor method" + streamAccessorName);
            IStreamableField isf = entityInstance.GetStreamableField(streamAccessorName);
            Stream resStream = isf.GetData();
            using (BinaryReader reader = new BinaryReader(resStream))
            {
                using (FileStream fs = File.Create(@"C:\\" + entityInstance.GetIdentity().GetIdentifierValues()[0] + ".jpg"))
                {
                    int bytesRead = 0;
                    do
                    {
                        int nrBytes = 80 * 1000 * 1000;
                        byte[] streamData = new byte[nrBytes];
                        bytesRead = reader.Read(streamData, 0, nrBytes);
                        this.Log.Comment("Total Bytes Read - " + bytesRead);
                        if (bytesRead > 0)
                        {
                            fs.Write(streamData, 0, bytesRead);
                        }
                    } while (bytesRead > 0);
                }
            }
            isf.Dispose();
            this.Log.Comment("ExecuteStreamAccessorMethod Exit" );
        }
```


## Nächste Schritte
<a name="bkmk_Next"> </a>

Nachdem Sie einen externen Inhaltstyp erstellt haben, können Sie diesen verwenden, um Daten in SharePoint mithilfe der integrierten Objekte (externe Listen, Geschäftsdaten-Webparts oder benutzerdefinierter Code) zur Verfügung zu stellen.
  
    
    
Weitere Informationen finden Sie unter  [Vorgehensweise: Erstellen eine externe Liste mithilfe einer in SharePoint 2013 OData-Datenquelle](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md).
  
    
    

## Zusätzliche Ressourcen
<a name="bkmk_Addres"> </a>


-  [Verwenden von OData-Quellen mit Business Connectivity Services in SharePoint 2013](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Externe Inhaltstypen in SharePoint 2013](external-content-types-in-sharepoint-2013.md)
    
  
-  [Was ist neu in Business Connectivity Services in SharePoint 2013](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  

