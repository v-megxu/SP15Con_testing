---
title: Eingehende Ansprüche Anmelden bei SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 08c687aa-e485-4269-aea8-4333da3588a5
---


# Eingehende Ansprüche: Anmelden bei SharePoint 2013

## Anmelden bei SharePoint

Wenn sich ein Benutzer bei SharePoint Server anmeldet, wird sein Token geprüft und anschließend für die Anmeldung bei SharePoint verwendet. Bei dem Token handelt es sich um ein von einem Forderungsanbieter bereitgestelltes Sicherheitstoken. 
  
    
    

> **HINWEIS**
> Informationen zur forderungsbasierten Authentifizierung für eine einzelne SharePoint-Farm sowie zur farmübergreifenden SharePoint-Forderungsauthentifizierung finden Sie im TechNet unter  [Planen der Forderungsauthentifizierung ](http://technet.microsoft.com/de-de/library/cc262350.aspx). 
  
    
    


### Anmeldung im Windows-Forderungsmodus

Bei der Anmeldung im Windows-Forderungsmodus erfolgt die Anmeldung mit einer Negotiate-Abfrage der integrierten Windows-Authentifizierung (NTLM/Kerberos). Nach der Erstellung des  [WindowsIdentity](https://msdn.microsoft.com/library/System.Security.Principal.WindowsIdentity.aspx) -Objekts (das einen Windows-Benutzer repräsentiert) wird allerdings von SharePoint Server das [WindowsIdentity](https://msdn.microsoft.com/library/System.Security.Principal.WindowsIdentity.aspx) -Objekt in ein [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) -Objekt konvertiert (das eine forderungsbasierte Darstellung eines Benutzers repräsentiert).
  
    
    
SharePoint Server führt dann eine Forderungsaugmentation durch und verarbeitet das resultierende Token, das von SharePoint Server ausgestellt wird. Das bedeutet, dass einige Features (z. B. die Mehrinstanzenunterstützung für Dienstanwendungen und benutzerdefinierte Forderungsanbieter) in SharePoint Server funktionieren, obwohl die Clients davon ausgehen, dass sich SharePoint Server im systemeigenen Windows-Anmeldungsmodus befindet. Die Anmeldung im Windows-Forderungsmodus ist die Werksvorgabe für SharePoint Server. 
  
    
    
Alle Forderungsanmeldungstypen nutzen die passive Anmeldung. Die passive Anmeldung erfolgt über eine Windows-Abfrage, allerdings über eine eigene Anmeldeseite, die über eine 302-Umleitung aufgerufen wird. Dieser Modus ist nützlich, wenn mehrere Anmeldemethoden aktiviert sind und der Benutzer unter mehreren unterstützten Forderungsanbietern wählen muss. Win32-Clients müssen die formularbasierte Authentifizierung in Office-Clients unterstützen. Einige Office-Clients folgen einem anderen Protokoll.
  
    
    

### Passiver SAML-Anmeldungsmodus

Bei der passiven SAML-Anmeldung (Security Assertion Markup Language) wird der Client (z. B. eine Webseite) bei der Benutzeranmeldung an den festgelegten Forderungsanbieter (z. B. den Windows Live ID-Forderungsanbieter) umgeleitet. Nach der Authentifizierung des Benutzers durch den Forderungsanbieter wird das vom Forderungsanbieter vorgelegte SAML-Token von SharePoint Server übernommen und verarbeitet, anschließend werden die Forderungen augmentiert. 
  
    
    
Bei SAML-basierten Forderungsanbietern wie dem Forderungsanbieter der Active Directory-Verbunddienste und dem Windows Live ID-Forderungsanbieter wird nur die Anmeldung im passiven SAML-Anmeldungsmodus unterstützt. Die passive SAML-Anmeldung ist das Onlineidentitätsmodell von SharePoint. 
  
    
    

> **HINWEIS**
> Die passive SAML-Anmeldung beschreibt den Anmeldungsprozess. Wenn die Anmeldung für eine Webanwendung konfigurationsgemäß Token von einem vertrauenswürdigen Anmeldeanbieter akzeptiert, wird dieser Anmeldungstyp als passive SAML-Anmeldung bezeichnet. Ein vertrauenswürdiger Anmeldeanbieter ist ein externer (außerhalb von SharePoint befindlicher) Sicherheitstokendienst, der von SharePoint als vertrauenswürdig eingestuft wird. 
  
    
    

Win32-Clients müssen die formularbasierte Authentifizierung in Office-Clients unterstützen. 
  
    
    

### Passive Anmeldung von Mitgliedern und Rollen in ASP.NET

Bei der passiven Anmeldung von Mitgliedern und Rollen in ASP.NET erfolgt die Anmeldung durch das Umleiten des Clients an eine Webseite, auf der die ASP.NET-Anmeldesteuerelemente gehostet sind. Nachdem das Identitätsobjekt, das eine Benutzeridentität darstellt, erstellt wurde, konvertiert SharePoint Server dies in ein  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) -Objekt (das eine anspruchsbasierte Darstellung eines Benutzers ist).
  
    
    
SharePoint Server führt dann eine Forderungsaugmentation durch. Win32-Clients müssen die formularbasierte Authentifizierung in Office-Clients unterstützen.
  
    
    

### Anmeldung im klassischen Windows-Modus

Die Anmeldung im klassischen Windows-Modus wird in dieser Version nicht mehr unterstützt. Bei der Anmeldung im klassischen Windows-Modus erfolgt die Anmeldung mit einer Negotiate-Abfrage der integrierten Windows-Authentifizierung (NTLM/Kerberos). Es gibt keine Forderungsaugmentation, deshalb funktionieren einige Features (z. B. die Mehrinstanzenunterstützung für Dienstanwendungen und benutzerdefinierte Forderungsanbieter), wenn sich ein Benutzer in diesem Modus anmeldet. 
  
    
    
Einige Dienstanwendungen erfordern möglicherweise auch den Anspruchsmodus für einige Features.
  
    
    

### Anonymer Zugriff

Sie können den anonymen Zugriff für eine Webanwendung aktivieren. Die Administratoren der Websites innerhalb der Webanwendung können den anonymen Zugriff gestatten. Wenn anonyme Benutzer auf geschützte Ressourcen zugreifen möchten, können sie auf eine Anmeldeschaltfläche klicken, um ihre Anmeldeinformationen zu übertragen. 
  
    
    
SharePoint Server führt dann eine Forderungsaugmentation durch. Win32-Clients müssen die formularbasierte Authentifizierung in Office-Clients unterstützen.
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Anspruchsbasierte Identität in SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Anspruchsanbieter in SharePoint 2013](claims-provider-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: Erstellen ein anspruchsanbieters in SharePoint 2013](how-to-create-a-claims-provider-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: POST eines anspruchsanbieters in SharePoint 2013](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

