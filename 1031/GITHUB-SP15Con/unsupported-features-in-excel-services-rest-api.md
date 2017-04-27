---
title: Nicht unterstützte Features in der REST-API in Excel Services
ms.prod: OFFICE365
ms.assetid: 4139901f-255b-4556-b8c8-3d986a07c587
---


# Nicht unterstützte Features in der REST-API in Excel Services

Die erste Version des Excel Services REST-API unterstützt alle Excel-Features nicht.
  
    
    

 **Hinweis**: der Excel Services REST API gilt für SharePoint 2013 und SharePoint 2016 lokale. Verwenden Sie die Excel REST-APIs, die Teil des Endpunkts [Microsoft Graph](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/excel
) sind online Szenarios.
Es folgt eine partielle Liste einiger wichtiger Features, die derzeit nicht unterstützt werden oder in der REST-API Excel Services arbeiten:
  
    
    


- **Keine unverankerten Diagramme.** Wenn ein Bereich ein Diagramm enthält und Sie den Bereich über REST anfordern, erhalten Sie nur den Bereich.
    
  
- **Keine Sparklines, keine bedingte Formatierung für Symbole.** Derzeit nicht unterstützt.
    
  
- **Keine Pixelperfektion mit EWA.** Das von REST produzierte HTML ist dem von Excel Web Access produzierten HTML sehr ähnlich. Mit der REST-API in Excel Services kann jedoch nicht auf alle CSS-Elemente (Cascading Stylesheets) zugegriffen werden, auf die Excel Web Access Zugriff hat. Die REST-API in Excel Services gibt ein HTML-Fragment zurück. Das HTML-Fragment muss eigenständig sein.
    
  
- **Keine Unterscheidung in Tabellen.** Wenn eine Tabelle als ATOM angefordert wird, kann nicht festgestellt werden, ob es sich bei der Zelle oder den Daten um eine Spaltenüberschrift, eine Summe oder allgemeine Daten handelt. In der Tabelle wird diesbezüglich nämlich keine Unterscheidung gemacht. Alle Tabellenzeilen in der gesamten Tabelle werden gleich behandelt.
    
  
- **URL-Größenbeschränkungen.** Die URL-Größe ist auf etwa 2000 Zeichen begrenzt. Das heißt, wenn in einer Arbeitsmappe sehr viele Parameter vorhanden sind, können Sie möglicherweise nicht alle Parameter festlegen. Dies gilt insbesondere, wenn die Arbeitsmappe tief in der Hierarchie einer Ordnerstruktur angeordnet ist.
    
  
- **Sonderzeichen.** Zeichen wie "?" und "#" werden nicht unterstützt. Um ordnungsgemäß auf Blattnamen zu verweisen, die Sonderzeichen enthalten, gilt die Grundregel "Feststellen, was der Excel-Client macht", wenn Sie in einer Formel auf ein Blatt mit Sonderzeichen verweisen, und diesem Beispiel folgen.
    
  

