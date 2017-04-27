---
title: Inhaltssuche-Webpart in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 6fb4bf41-0846-4dca-ad9e-906afdfd3d2b
---


# Inhaltssuche-Webpart in SharePoint 2013

  
    
    
![Konzeptuelles Übersichtsthema](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
Informationen zum Inhaltssuche-Webpart (CSWP) in SharePoint 2013.
## Einführung in das Inhaltssuche-Webpart (CSWP)
<a name="SP15_CSWP_IntroducingCSWP"> </a>

Das Inhaltssuche-Webpart (Content Search Web Part, CSWP) wurde in SharePoint 2013 eingeführt. Es verwendet verschiedene Optionen für die Formatierung, um dynamische Inhalte auf SharePoint-Seiten anzuzeigen.
  
    
    

## Funktionsweise des Inhaltssuche-Webparts
<a name="SP15_CSWP_HowCSWPWorks"> </a>

Das Inhaltssuche-Webpart zeigt Suchergebnisse in einer Weise an, die Sie einfach formatieren können. Jedem Inhaltssuche-Webpart ist eine Suchabfrage zugeordnet, für die die Ergebnisse angezeigt werden.
  
    
    
Sie können Anzeigevorlagen verwenden, um die Darstellung der Suchergebnisse auf der Seite zu ändern. Anzeigevorlagen sind HTML- und JavaScript-Codeausschnitte zum Rendern der von SharePoint zurückgegebenen Informationen. Die anzuzeigenden Informationen werden im JSON-Format in die Seite eingefügt. 
  
    
    

## Gründe für die Verwendung des Inhaltssuche-Webparts (CSWP) oder des Webparts für Inhaltsabfragen (CQWP)
<a name="SP15_CSWP_WhenToUseCSWPorCQWP"> </a>

Das Inhaltssuche-Webpart kann beliebige Inhalte aus dem Suchindex zurückgeben. Verwenden Sie es auf Ihren SharePoint 2013-Websites, wenn Sie eine Verbindung mit einem Suchdienst herstellen und indizierte Suchergebnisse auf Ihren Seiten zurückgeben möchten. 
  
    
    
Das Inhaltssuche-Webpart gibt Inhalte zurück, die so aktuell sind wie die letzte Durchforstung Ihrer Inhalte. Wenn Sie häufig Durchforstungen ausführen, ist der vom Inhaltssuche-Webpart zurückgegebene Inhalt aktueller, als wenn Sie nur selten Durchforstungen ausführen. Wenn aktuelle Inhalte oder die aktualisierte Version der Inhalte angezeigt werden sollen, verwenden Sie stattdessen das Webpart für Inhaltsabfragen (Content Query Web Part, CQWP).
  
    
    
Bei der Suche werden nur die Hauptversionen von Inhalten durchforstet, niemals die Nebenversionen. Wenn Sie die Nebenversionen von Inhalten anzeigen möchten, verwenden Sie dazu ein Webpart für Inhaltsabfragen.
  
    
    
Einige Websitesammlungsadministratoren markieren Websites, die nicht indiziert werden sollen. So markierte Inhalte ist nicht in einem Inhaltssuche-Webpart verfügbar. Wenn Sie Ergebnisse aus einer Website zurückgeben möchten, die als nicht indizierbar gekennzeichnet ist, verwenden Sie das Webpart für Inhaltsabfragen.
  
    
    

## Weitere Ressourcen
<a name="SP15_CSWP_AdditionalResources"> </a>


-  [Verwaltete Navigation in SharePoint 2013](managed-navigation-in-sharepoint-2013.md)
    
  
-  [What's new in SharePoint 2013-Suche für Entwickler](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

