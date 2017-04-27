---
title: Vorgehensweise Erstellen ein anspruchsanbieters in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8f3228ca-57fd-4253-a07d-abeb63298c58
---


# Vorgehensweise: Erstellen ein anspruchsanbieters in SharePoint 2013
In diesem Artikel erfahren Sie, wie ein SharePoint 2013-Anspruchsanbieter erstellt und implementiert wird, der die Voraussetzungen für die Steigerung von Ansprüchen und die Auswahl von Ansprüchen erfüllt.
Ein Forderungsanbieter gibt Forderungen heraus und packt Forderungen in Sicherheitstoken. Ein Forderungsanbieter erfüllt zwei Aufgaben: Erweiterung und Auswahl.
  
    
    

Die anspruchserweiterung kann eine Anwendung zusätzliche Ansprüchen Token des Benutzers. Beispielsweise kann mit Windows-basierten Log-in der Active Directory-Verzeichnisdienst aller Sicherheitsgruppen des Benutzers in Windows-Token des Benutzers ergänzen. Mit anspruchsbasierten anmelden kann eine Anwendung Customer Relationship Management (CRM) Rollen aus einer Datenbank CRM ergänzen. Da Sie diese Ansprüche im Token des Benutzers, können Ressourcen gegen diese Ansprüche autorisiert werden. D. h., werden diese Ansprüche verwendet, um festzustellen, ob ein bestimmter Benutzer Zugriff auf bestimmte Ressourcen hat.
Ansprüche können im Auswahlsteuerelement über anspruchsauswahl Personen angezeigt werden. Anspruchsauswahl ermöglicht Ansprüche Offenlegen eine Anwendung in der Personenauswahl, beispielsweise beim Konfigurieren der Sicherheits einer SharePoint-Website oder die SharePoint-Dienst. Diese Funktionalität können Sie suchen, auflösen und benutzerfreundliche Anzeige von Ansprüchen bereitstellen.
  
    
    


> **HINWEIS**
> Eine Personenauswahl mit einer Funktion zur forderungsauswahl wird manchmal als ein forderungsauswahlbezeichnet. Weitere Informationen finden Sie unter  [Personenauswahl und Anspruchsanbietern](http://technet.microsoft.com/en-us/library/gg602063.aspx).
  
    
    

Wenn Sie einen Forderungsanbieter schreiben möchten, müssen Sie zunächst eine Klasse erstellen, die von der **SPClaimProvider**-Klasse abgeleitet ist.
> **TIPP**
> Ein Codebeispiel und Weitere Informationen zu den **SPClaimProvider** -Klasse und deren Member finden Sie unter [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) . Exemplarische Vorgehensweisen, Tipps und Codebeispiele herunter, finden Sie unter [Ansprüche und Sicherheit: technische Artikel und Codebeispiele in MSDN](http://msdn.microsoft.com/library/f773fd4a-53ec-4656-bd08-e6c435e6f103%28Office.15%29.aspx).
  
    
    


## Erforderliche Implementierungen
<a name="SP15_HowToCreateClaimsProvider_ReqImplementations"> </a>

Es folgen die erforderlichen Methoden und Eigenschaften zum Schreiben eines Forderungsanbieters.
  
    
    

### Erforderlich

Die folgende  [Name](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.Name.aspx) -Eigenschaft ist erforderlich. Der Name muss in der Farm eindeutig sein.
  
    
    

```cs

public abstract String Name
      
```


### Erforderlich für die Forderungsauswahl

Forderungen können im **Personenauswahl**-Steuerelement über die Forderungsauswahl angezeigt werden. Die folgenden Methoden in der  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) -Klasse sind erforderlich, wenn Sie die Forderungsauswahl im **Personenauswahl**-Steuerelement implementieren möchten.
  
    
    

```cs

protected abstract void FillSchema(SPProviderSchema schema);
     protected abstract void FillClaimTypes(List<String> claimTypes);
     protected abstract void FillClaimValueTypes(List<String> claimValueTypes);
     protected abstract void FillEntityTypes(List<String> entityTypes);

```


### Erforderlich für die Forderungserweiterung

Wenn Sie zusätzliche Forderungen in das Sicherheitstoken eines Benutzers einschließen, erweitern Sie Forderungen. Wenn Sie Forderungen erweitern möchten, müssen Sie die folgenden Methoden in der  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) -Klasse implementieren.
  
    
    

```cs

public abstract bool SupportsEntityInformation
      protected abstract void FillClaimsForEntity(Uri context, SPClaim entity, List<SPClaim> claims);

```


### Erforderlich zum Anzeigen der Hierarchie im linken Bereich der Forderungsauswahl

Wenn Sie die Hierarchie im linken Bereich der Forderungsauswahl anzeigen möchten, müssen Sie die folgenden Methoden in der  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) -Klasse implementieren.
  
    
    

```cs

public abstract bool SupportsHierarchy
     protected abstract void FillHierarchy(Uri context, String[] entityTypes, String hierarchyNodeID, int numberOfLevels, bool includeEntityData, SPProviderHierarchyTree hierarchy);

```


### Erforderlich für das Auflösen von Forderungen im Eingabesteuerelement der Forderungsauswahl

Wenn Sie Forderungen mithilfe des Eingabesteuerelements der Forderungsauswahl auflösen möchten, müssen Sie die folgenden Methoden in der  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) -Klasse implementieren.
  
    
    

```cs

public abstract bool SupportsResolve
     protected abstract void FillResolve(Uri context, String[] entityTypes, String resolveInput, List<PickerEntity> resolved);
     protected abstract void FillResolve(Uri context, String[] entityTypes, SPClaim resolveInput, List<PickerEntity> resolved);

```


### Erforderlich für die Suche nach Forderungen in der forderungsauswahl

Wenn Sie nach Forderungen in der Forderungsauswahl suchen möchten, müssen Sie die folgende Eigenschaft und Methode in der  [SPClaimProvider](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaimProvider.aspx) -Klasse implementieren.
  
    
    

```cs

public abstract bool SupportsSearch
     protected abstract void FillSearch(Uri context, String[] entityTypes, String searchPattern, String hierarchyNodeID, int maxCount, SPProviderHierarchyTree searchTree);

```


## Nützliche Hilfsmethode
<a name="SP15_HowToCreateClaimsProvider_UsefulHelperMethod"> </a>

Sie können auch eine Hilfsmethode implementieren, die Sie beim Erstellen von  [SPClaim](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaim.aspx) -Objekten unterstützt.
  
    
    

### Nützliche Hilfsmethode zum Erstellen von SPClaim-Objekten

Die folgende Hilfsmethode können Sie implementieren, damit Sie sie beim Erstellen von  [SPClaim](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.Claims.SPClaim.aspx) -Objekten unterstützt.
  
    
    

```cs

protected SPClaim CreateClaim(String claimType, String value, String valueType)
```


## Zusätzliche Ressourcen
<a name="SP15_HowToCreateClaimsProvider_AdditionalResources"> </a>


-  [Anspruchsbasierte Identität in SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Eingehende Ansprüche: Anmelden bei SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)
    
  
-  [Anspruchsanbieter in SharePoint 2013](claims-provider-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: POST eines anspruchsanbieters in SharePoint 2013](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

