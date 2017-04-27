---
title: Search-add-ins in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 21682e45-dd78-4f3c-8f1e-cdd48de3bde2
---


# Search-add-ins in SharePoint 2013
Informationen Sie zur Suche SharePoint-Add-Ins und wie Sie Ihre eigene Search-add-ins erstellen können. Die Add-ins, die Sie erstellen können SharePoint-Add-ins Katalog hinzugefügt werden, damit sie in der lokalen Bereitstellung und Office 365 verwendet werden können. Search-add-ins funktionieren nur mit Daten, die im Suchindex gespeichert sind und nicht mit den ursprünglichen Quelldokumenten.
SharePoint-Add-Ins sind eigenständig der Funktionalität, die Erweiterung der Fähigkeiten einer SharePoint-Website. Diese-add-ins zu spezifische Bedürfnissen von Geschäfts- und Endbenutzer durch die Integration von das beste aus dem Web- und SharePoint lösen. Ein Add-In kann verschiedene SharePoint Elemente wie Listen, Remote-Ereignisempfänger, Inhaltstypen, Workflows, benutzerdefinierte Workflowaktivitäten, Websitespalten, Module, im Menü Element benutzerdefinierte Aktionen, Client-Webparts und Suchkonfigurationen enthalten. Weitere Informationen finden Sie unter  [SharePoint-Add-Ins](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx).
  
    
    

Ein Search-add-in ist ein SharePoint-Add-In, dass die Suchfunktion verwendet. SharePoint 2013 API für die Suche können Sie in einem Add-in auf Suche um Inhalte zu suchen. Je nach Art der Berechtigungen, die im [Manifest-Add-in](http://msdn.microsoft.com/library/7cd5850f-cbf3-48d2-bcb7-59b8f4ed0e63%28Office.15%29.aspx)einrichten können Sie entweder innerhalb oder außerhalb der Inhalt des Add-Ins suchen. Darüber hinaus können Sie auch ein Search-add-in verwenden zum Verteilen von Suchkonfigurationen aus einer SharePoint Installation in eine andere.
Der Core Entwurf des Search-add-Ins, hängt von der Bereitstellungsmethode, die Sie auswählen. Im folgende Abschnitt werden die verfügbaren Optionen und ihre Vorteile zusammengefasst. Weitere Informationen finden Sie unter  [Auswählen von Mustern für die Entwicklung und das Hosting Ihres Add-Ins für SharePoint](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
  
    
    


## Bereitstellen der Suche-add-ins
<a name="SP15_Deploy_search_apps"> </a>

Es gibt zwei Methoden, um Ihre Suche-add-in bereitstellen:
  
    
    

1. SharePoint gehostet - lokale Bereitstellung. Das Search-add-in wird innerhalb des Unternehmensnetzwerks auf das Unternehmen Servern gehostet. Das Unternehmen Administratoren verwalten das Add-in. In diesem Szenario bietet Flexibilität bei der Bereitstellung und Support, da die Hardware und Software lokal, die Administratoren verwaltet wird.
    
  
2. Vom Anbieter gehostet - alle Server gehostet. Das Search-add-in wird von jedem Anbieter, außerhalb des Kunden sharepointserver gehostet.
    
  

## Add-in-Entwicklung suchumgebung
<a name="SP15_Search_app_dev_environment"> </a>

Um ein Search-add-in zu erstellen, verwenden Sie eine der folgenden zwei Umgebungen:
  
    
    

- Microsoft Visual Studio 2012 oder Microsoft Visual Studio 2013 oder Visual Studio 2015
    
  
- Napa Office 365-Entwicklungstools
    
  
Mit Visual Studio 2013 und höher, können Sie Ihre Suche-add-ins für beide lokalen oder in Office 365 veröffentlichen. Mit Napa können Sie alternativ erstellen und Veröffentlichen von Search-add-ins in Ihrem Browser. Diese Add-Ins können später exportiert und erneut für lokale Kunden gepackt. Weitere Informationen zu den zwei entwicklungsumgebungen und deren Verwendung zum Erstellen von Search-add-ins finden Sie unter  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md) und [Erstellen von Apps für Office und SharePoint mit den Napa Office 365-Entwicklungstools](http://msdn.microsoft.com/library/82a3645c-0911-4926-9176-236ac8d28bdd%28Office.15%29.aspx).
  
    
    

## APIs für Search-add-ins
<a name="SP15_APIs_search_apps"> </a>

Sie können die Breite Palette von APIs suchbezogene bietet, SharePoint für Search-add-ins. Die folgende Tabelle enthält diese APIs und des Speicherorts der ihre Klassenbibliotheken.
  
    
    

**SharePoint-APIs für Search-add-ins**


|**API-Name**|**Klassenbibliothek**|
|:-----|:-----|
|.NET-Clientobjektmodelle (CSOM) <br/> |Microsoft.SharePoint.Client.Search.dll <br/> |
|Silverlight CSOM <br/> |Microsoft.SharePoint.Client.Search.Silverlight.dll <br/> |
|ECMAScript (JavaScript, JScript)-Objektmodell (JSOM) <br/> |SP.search.js <br/> |
|Suche REST-API <br/> |http://Server/_API/Search/Query <br/> |
   

### Codebeispiele

Hier sind einige Codebeispiele, die mithilfe der verschiedenen APIs. Jedes Codebeispiel sendet eine einfache Suche-Abfrage, die das Schlüsselwort "SharePoint " enthält an Suchdienstanwendung (SSA).
  
    
    
 **Client-side Object Model (CSOM)**
  
    
    

  
    
    



```cs

using (ClientContext clientContext = new ClientContext("http://localhost"))
{
    KeywordQuery keywordQuery = new KeywordQuery(clientContext);
    keywordQuery.QueryText = "*";
    SearchExecutor searchExecutor = new SearchExecutor(clientContext);
    ClientResult<ResultTableCollection> results = 
        searchExecutor.ExecuteQuery(keywordQuery);
    clientContext.ExecuteQuery();
}
```

 **JavaScript Object Model (JSOM)**
  
    
    

  
    
    



```

var keywordQuery = new
Microsoft.SharePoint.Client.Search.Query.KeywordQuery(context);
keywordQuery.set_queryText('SharePoint');
var searchExecutor = new Microsoft.SharePoint.Client.Search.Query.SearchExecutor(context);
results = searchExecutor.executeQuery(keywordQuery);
context.executeQueryAsync(onQuerySuccess, onQueryFail);
```

 **REST**
  
    
    

  
    
    
HTTP GET-Anforderung
  
    
    



```HTML

http://mylocalhost/_api/search/query?querytext='SharePoint'
```

HTTP POST-Anforderung
  
    
    



```HTML
{
'__metadata' : {'type' : 'Microsoft.Office.Server.Search.REST.SearchRequest'},
'Querytext' : 'SharePoint'
}
```


## Suche Add-in-Berechtigungen
<a name="SP15_Search_app_permissions"> </a>

Search-Add-ins senden abfrageanforderungen an Suchdienstanwendung (SSA) sowie die Add-ins erforderlich verschiedene Typen von Berechtigungen ordnungsgemäß funktioniert. Sie können diese Berechtigungen über die Add-in-Manifestdatei, konfigurieren, die Bestandteil jedes SharePoint-Add-in ist. Sie können die Add-in-Manifestdatei direkt mit einem Text-Editor ändern oder Sie können es mit Visual Studio oder Napa, ändern, wie in den folgenden Abbildungen gezeigt.
  
    
    

**Abbildung 1: Einrichten von Berechtigungen für Search-add-ins in Visual Studio 2015**

  
    
    

  
    
    
![Berechtigungskonfiguration für Such-App mit Napa](images/SP15_search_apps_permission_Visual_Studio.PNG)
  
    
    

  
    
    

  
    
    

**Abbildung 2: Einrichten von Berechtigungen für Search-add-ins in "Napa" Office 365-Entwicklungstools**

  
    
    

  
    
    
![Berechtigungskonfiguration für Such-App über Napa](images/SP15_search_app_permission_Napa.gif)
  
    
    
Ein SharePoint-Add-In hat eine eigene Identität und ein Sicherheitsprinzipal zugeordnet ist ein Prinzipal-add-inaufgerufen. Wie Benutzer und Gruppen verfügt über ein Principal-Add-in, bestimmte Berechtigungen und Verwaltung von Informationsrechten. Der Prinzipal-Add-in hat Vollzugriff auf das Web-Add-in muss nur auf Ressourcen in der Hostwebsite oder an anderen Standorten außerhalb der Website-Add-Ins wie Websitesammlungen SharePoint Berechtigungen anzufordern. Im Gegensatz zu anderen SharePoint-Add-Ins ein Search-add-in nur auf Benutzerebene sind Berechtigungen erforderlich, als **QueryAsUserIgnoreAppPrincipal**bezeichnet. Mit dieser Berechtigung können Sie die Abfrage des Search-add-Ins basierend auf den Berechtigungen des Benutzers. Dies bedeutet, dass ACLs des Benutzers, dass die Suche, die Ergebnisse zurückgegeben werden, basiert.
  
    
    

### Anfordern von Berechtigungen in der Manifestdatei-Add-in

Die Manifestdatei-Add-in wird im XML-Format und kann direkt bearbeitet werden. Wenn Sie Berechtigungen erhalten möchten, Schreiben Sie eine Anforderung, wie im folgenden Beispiel dargestellt:
  
    
    

```XML

<AppPermissionRequests>
  <AppPermissionRequest Scope="http://sharepoint/search" Right="QueryAsUserIgnoreAppPrincipal" />
</AppPermissionRequests>
```


## Weitere Ressourcen
<a name="SP15_Search_app_addresources"> </a>


-  [SharePoint-Add-Ins](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)
    
  
-  [Auswählen von Mustern für die Entwicklung und das Hosting Ihres Add-Ins für SharePoint](http://msdn.microsoft.com/library/05ce5435-0a03-4ddc-976b-c33b08d03457%28Office.15%29.aspx)
    
  
-  [Add-In-Berechtigungen in SharePoint 2013](http://msdn.microsoft.com/library/5f7a8440-3c09-4cf8-83ec-c236bfa2d6c4%28Office.15%29.aspx)
    
  
-  [Add-In-Autorisierungsrichtlinientypen in SharePoint 2013](http://msdn.microsoft.com/library/124879c7-a746-4c10-96a7-da76ad5327f0%28Office.15%29.aspx)
    
  
-  [Wichtige Aspekte der Architektur und Entwicklungslandschaft von Add-Ins für SharePoint](http://msdn.microsoft.com/library/ae96572b-8f06-4fd3-854f-fc312f7f2d88%28Office.15%29.aspx)
    
  
-  [Hinweise zur App-Manifeststruktur und zum Paket eines SharePoint-Add-Ins](http://msdn.microsoft.com/library/7cd5850f-cbf3-48d2-bcb7-59b8f4ed0e63%28Office.15%29.aspx)
    
  
-  [Hinzufügen von Suchfunktionen für die add-ins für SharePoint](http://blogs.msdn.com/b/officeapps/archive/2013/05/30/add-search-capabilities-to-your-apps-for-sharepoint.aspx)
    
  
-  [Exportieren und Importieren von Konfigurationseinstellungen für Suche in SharePoint 2013](exporting-and-importing-search-configuration-settings-in-sharepoint-2013.md)
    
  
-  [Exportieren und importieren suchkonfigurationseinstellungen in SharePoint Server 2013 (TechNet)](http://technet.microsoft.com/en-us/library/jj871675.aspx)
    
  

