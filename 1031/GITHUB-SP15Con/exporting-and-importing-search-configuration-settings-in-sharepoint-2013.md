---
title: Exportieren und Importieren von Konfigurationseinstellungen für Suche in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: d00679a3-ffa2-4281-ad8b-70fc2c4a14e2
---


# Exportieren und Importieren von Konfigurationseinstellungen für Suche in SharePoint 2013
Rufen Sie Codebeispiele, die Ihnen zeigen, wie exportieren und importieren angepasster suchkonfigurationseinstellungen. Dazu gehören alle benutzerdefinierten Abfrageregeln, ergebnisquellen, Ergebnistypen, Bewertungsmodelle und Website für die Suche. SharePoint wird diese Funktionalität durch den Namespace  [Microsoft.Office.Server.Search.Portability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.aspx) verfügbar gemacht.Außerdem können Sie die Einstellungen von Websitesammlungen und Websites importieren und Exportieren benutzerdefinierter suchkonfigurationseinstellungen aus einer Suchdienstanwendung (SSA).
> **HINWEIS**
> Sie können nicht importieren benutzerdefinierter suchkonfigurationseinstellungen in eine SSA oder exportieren die Standard-suchkonfigurationseinstellungen.
  
    
    


## Exportieren der Konfiguration für die Suche
<a name="SP15_exporting_search_configuration"> </a>

Der folgende Code veranschaulicht die  [SearchConfigurationPortability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.SearchConfigurationPortability.aspx) verwenden, um Ihre Website suchkonfigurationseinstellungen exportieren. Der Code verwendet eine Beispiel-Website _http://yoursite/sites/publishing1_, die Sie mit Ihrer eigenen Website ersetzen würde.  _fileName_ bezieht sich auf die Datei, in dem die suchkonfigurationseinstellungen gespeichert werden. _owner_ gibt die [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) an dem die suchkonfigurationseinstellungen ermittelt werden.
  
    
    

```

private static void Export(string fileName)
{
    SPSite site = new SPSite("http://yoursite/sites/publishing1");
    SearchConfigurationPortability conf = new SearchConfigurationPortability(site);
    SearchObjectOwner owner = new SearchObjectOwner(SearchObjectLevel.SPWeb, site.OpenWeb());
    var buff = conf.ExportSearchConfiguration(owner);
    File.WriteAllText(fileName, buff);
    site.Close();
}
```


## Import-suchkonfigurationseinstellungen
<a name="SP15_importing_search_configuration"> </a>

Der folgende Code zeigt, wie Sie mithilfe von  [SearchConfigurationPortability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.SearchConfigurationPortability.aspx) suchkonfigurationseinstellungen aus einer Datei importieren, und Ersetzen Sie den vorhandenen für die Suche auf einer angegebenen Website, _http://yoursite/sites/publishing1_.  _fileName_ bezieht sich auf die Datei, in dem die suchkonfigurationseinstellungen gespeichert werden. _owner_ gibt die [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) an dem die suchkonfigurationseinstellungen ermittelt werden.
  
    
    

```cs

private static void Import(string fileName)
{
    SPSite site = new SPSite("http://yoursite/sites/publishing1");
    SearchConfigurationPortability conf = new SearchConfigurationPortability(site);
    SearchObjectOwner owner = new SearchObjectOwner(SearchObjectLevel.SPWeb, site.OpenWeb());
    conf.ImportSearchConfiguration(owner, File.ReadAllText(fileName));
    site.Close();
}

```


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Suche in SharePoint 2013](search-in-sharepoint-2013.md)
    
  
-  [Exportieren und Importieren von benutzerdefinierten Suchkonfigurationseinstellungen in SharePoint Server 2013](http://technet.microsoft.com/de-de/library/jj871675.aspx)
    
  

  
    
    

