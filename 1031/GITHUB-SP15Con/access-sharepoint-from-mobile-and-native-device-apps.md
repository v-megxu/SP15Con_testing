---
title: Zugreifen auf SharePoint aus mobile und systemeigene Gerät apps
ms.prod: SHAREPOINT
ms.assetid: 42014171-5ee5-421d-9cde-413efc3aecef
---


# Zugreifen auf SharePoint aus mobile und systemeigene Gerät apps
Erfahren Sie, wie SharePoint von mobilen apps und andere apps systemeigene Gerät und von Anwendungen für externe Webdienste zugreifen.
SharePoint-Add-Ins, Farmlösungen und "codeloser" Sandkastenlösungen werden alle Ausführen von in SharePoint, aber apps auf anderen Plattformen können auch SharePoint-Client-APIs zugreifen.
  
    
    


> **WICHTIG**
> To test and debug on any platform, you need a **developer account on Office 365**. More info: [Einrichten einer Entwicklungsumgebung für SharePoint-Add-Ins in Office 365](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx) or [Erstellen einer Entwicklerwebsite in einem vorhandenen Office 365-Abonnement](http://msdn.microsoft.com/library/2ec857d5-dc6f-4cf6-ba45-adc845ef2a25%28Office.15%29.aspx).
  
    
    


## Mobile und native-Gerät nicht-Microsoft-apps

Gerät nicht-Microsoft-apps, einschließlich mobiler apps, **SharePoint REST/OData-APIs für CRUD-Vorgänge zu SharePoint-Daten verwenden**.
  
    
    

- See  [Erste Schritte mit den SharePoint 2013 REST-Dienst](get-to-know-the-sharepoint-2013-rest-service.md) for the basics.
    
  
- See  [REST-API-Referenz für SharePoint 2013](http://msdn.microsoft.com/library/3514e753-19f9-4b41-a1ae-f35c5ffc17d2%28Office.15%29.aspx) for a complete reference.
    
  
For more information about how to create mobile apps for any platform, see  [Erstellen von mobilen Apps für andere Plattformen mit SharePoint 2013](build-mobile-apps-for-other-platforms-using-sharepoint-2013.md).
  
    
    

## Windows Phone-apps, die auf SharePoint zugreifen
<a name="WinPhone"> </a>

Windows Phone-apps können eine der folgenden verwenden:
  
    
    

- Die .NET SharePoint-Objekt mithilfe der clientseitigen Objektmodell (CSOM) Version speziell für Windows Phone-Geräten.
    
  
- Der SharePoint REST/OData-APIs.
    
  
Diese mobilen apps können der Unterstützung von SharePoint für die Microsoft-pushbenachrichtigungsdienst und einen neuen Geolocation-Feldtyp nutzen.
  
    
    
For more about creating Windows Phone apps that access SharePoint, see  [Erstellen von Windows Phone-Apps, die auf SharePoint 2013 zugreifen](build-windows-phone-apps-that-access-sharepoint-2013.md).
  
    
    

## Webanwendungen, die nicht aus SharePoint beginnen
<a name="WinPhone"> </a>

Webanwendungen, die nicht aus SharePoint beginnen sind nicht unbedingt "SharePoint-Add-Ins ", obwohl sie manchmal als SharePoint-Add-Ins im MSDN und andere Dokumentationen gezählt werden. Diese apps enthalten zwischen anderen, Schriftarten, die von der Office 365 app Launcher und Office-Add-Ins ausgeführt werden, sowie alle Webanwendungen, die direkt in einem Browser ausgeführt werden.
  
    
    
Sie können diese apps auf die Plattform ASP.NET oder einen nicht-Microsoft-Stapel erstellen. Wenn Sie Ihre Webanwendung auf einem nicht-Microsoft-Stapel erstellen, werden CRUD-Vorgänge mit der REST/OData-APIs nur als app nicht von Microsoft stammenden Gerät. Bei der Erstellung auf ASP.NET es **dem SharePoint-Clientobjektmodell oder REST/OData-APIs verwenden können**.
  
    
    
These apps **gain authorized access to SharePoint data by using access tokens** that are issued by the Azure Control Service (ACS) in compliance with the OAuth Authentication Code flow. For more, see [OAuth-Ablauf mit Authentifizierungscode für SharePoint-Add-Ins](http://msdn.microsoft.com/library/e89e91c7-ea39-49b9-af5a-7f047a7e2ab7%28Office.15%29.aspx).
  
    
    

