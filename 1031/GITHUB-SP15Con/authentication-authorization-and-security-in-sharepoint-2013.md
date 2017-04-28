---
title: Authentifizierung, Autorisierung und Sicherheit in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 8734790c-eb75-4d78-9604-7cc23b33b693
---


# Authentifizierung, Autorisierung und Sicherheit in SharePoint 2013

## Neuerungen in SharePoint 2013 bei Authentifizierung, Autorisierung und Sicherheit
<a name="SP15_AuthenticationAuthorizationSecurity_WhatsNew"> </a>

Nachfolgend sind einige der optimierten Features von SharePoint 2013 aufgeführt: 
  
    
    

- Benutzeranmeldung
    
  - SharePoint 2013 bietet weiter Unterstützung für den anspruchsbasierten und klassischen Authentifizierungsmodus. Die anspruchsbasierte Authentifizierung ist in SharePoint 2013 die Standardeinstellung. Der klassische Authentifizierungsmodus gilt als überholt und kann nur noch mithilfe von Windows PowerShell verwaltet werden. Für zahlreiche Features in SharePoint 2013 ist der anspruchsbasierte Modus erforderlich. 
    
  
  - Die **MigrateUsers**-Methode in SharePoint 2010 gilt nun als überholt und eignet sich nicht mehr zum ordnungsgemäßen Migrieren von Konten. Verwenden Sie hierzu das neue Windows PowerShell-Cmdlet  `Convert-SPWebApplication`. Weitere Informationen finden Sie unter  [Migrieren von der klassischen Authentifizierung zur anspruchsbasierten Authentifizierung](http://technet.microsoft.com/de-de/library/gg251985.aspx).
    
  
  - Anspruchsanbieter müssen nicht mehr registriert werden. Anspruchstypen müssen jedoch vorab konfiguriert werden. Sie können die Zeichen für den Anspruchstyp wählen, und für Anspruchstypen gibt es keine zwingende Reihenfolge.
    
  
  - SharePoint 2013 verfolgt **FedAuth**-Cookies im neuen verteilten Cachedienst mithilfe von Windows Server AppFabric-Cachefeatures nach.
    
  
  - Es erfolgt eine wesentlich umfangreichere Protokollierung, die Sie bei der Behandlung von Authentifizierungsproblemen unterstützt. 
    
  
- Authentifizierung von Diensten und Apps
    
  - In SharePoint 2013 können Sie nun Apps für SharePoint erstellen. Eine SharePoint-Add-In hat eine eigene Identität und ist einem Sicherheitsprinzipal zugeordnet, der als App-Prinzipal bezeichnet wird. Wie Benutzer und Gruppen verfügt ein App-Prinzipal über bestimmte Berechtigungen und Rechte.
    
  
  - In SharePoint 2013 stellt der Server-zu-Server-Sicherheitstokendienst Zugriffstoken für die Server-zu-Server-Authentifizierung bereit. Der Server-zu-Server-Sicherheitstokendienst gewährt temporären Zugriffstoken Zugriff auf andere Anwendungsdienste, z. B. Exchange Server 2013, Microsoft Lync 2013 und Apps für SharePoint 2013.
    
  

## Authentifizierung und Autorisierung
<a name="SP15_AuthenticationAuthorizationSecurity_AuthenticationAndAuthorization"> </a>

Von SharePoint 2013 wird die Sicherheit für den Benutzerzugriff auf Website-, Listen, Listenordner- oder Bibliotheksordner- und Elementebene unterstützt. Die Sicherheitsverwaltung ist auf allen Ebenen rollenbasiert, sodass eine zusammenhängende Sicherheitsverwaltung in der SharePoint 2013-Plattform mit einer konsistenten rollenbasierten Benutzeroberfläche und einem Objektmodell für das Zuweisen von Berechtigungen für Objekte bereitgestellt wird. Daher implementiert die Sicherheit auf Listenebene, Ordnerebene oder Elementebene dasselbe Benutzermodell wie die Sicherheit auf Websiteebene, sodass das Verwalten von Benutzerrechten und das Gruppieren von Rechten auf einer Website vereinfacht wird. SharePoint 2013 bietet auch Unterstützung für eindeutige Berechtigungen in den Ordnern und Elementen von Listen und Dokumentbibliotheken.
  
    
    

> **HINWEIS**
> Informationen zur Autorisierung im Zusammenhang mit SharePoint-Add-Ins finden Sie unter  [Autorisierung und Authentifizierung für Add-Ins in SharePoint 2013](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx). 
  
    
    

Autorisierung bezieht sich auf den Prozess, mit dem SharePoint 2013 Sicherheit für Websites, Listen, Ordner oder Elemente bereitstellt, indem bestimmt wird, welche Benutzer bestimmte Aktionen auf ein angegebenes Objekt anwenden dürfen. Der Autorisierungsprozess setzt voraus, dass der Benutzer bereits authentifiziert wurde, was sich auf den Prozess bezieht, mit dem SharePoint 2013 den aktuellen Benutzer identifiziert. SharePoint 2013 implementiert nicht sein eigenes System für die Authentifizierung oder Identitätsverwaltung, sondern vertraut stattdessen auf externe Systeme, entweder die Windows-Authentifizierung oder ein anderes System.
  
    
    
In SharePoint 2013 werden die folgenden Typen von Authentifizierung unterstützt:
  
    
    

- **Windows:** Alle Integrationsoptionen in Microsoft-Internetinformationsdienste (Internet Information Services, IIS) und in der Windows-Authentifizierung, einschließlich Standard, Digest, Zertifikate, Windows NT LAN Manager (NTLM) und Kerberos werden unterstützt. Die Windows-Authentifizierung lässt zu, dass IIS die Authentifizierung für SharePoint 2013 durchführt.
    
    Informationen zum Anmelden an SharePoint mithilfe des Windows-Forderungsmodus finden Sie unter  [Eingehende Ansprüche: Anmelden bei SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md).
    
    > **WICHTIG**
    >  Weitere Informationen zum Aussetzen des Identitätswechsels finden Sie unter [Vermeiden des Aussetzens des Identitätswechsels durch den aufrufenden Benutzer](http://msdn.microsoft.com/de-de/library/ff407852.aspx). 
- **ASP.NET-Formulare:** Ein nicht von Windows bereitgestelltes Identitätsverwaltungssystem, das das austauschbare, auf ASP.NET-Formularen basierte Authentifizierungssystem verwendet, wird unterstützt. Mit diesem Modus kann SharePoint 2013 mit einer Vielzahl von Identitätsverwaltungssystemen zusammenarbeiten, einschließlich extern definierter Gruppen oder Rollen wie Lightweight Directory Access-Protokoll (LDAP) und schlanker Datenbankidentitäts-Verwaltungssysteme. Dank der Formularauthentifizierung kann ASP.NET die Authentifizierung für SharePoint 2013 durchführen, wobei häufig eine Umleitung zu einer Anmeldeseite eingeschlossen ist. In SharePoint 2013 werden ASP.NET-Formulare nur bei der anspruchsbasierten Authentifizierung unterstützt. Ein Formularanbieter muss innerhalb einer Webanwendung registriert sein, die für Ansprüche konfiguriert ist.
    
    Informationen zum Anmelden an SharePoint mithilfe der ASP.NET-Mitgliedschaft und zur passiven Anmeldung mit Rollen finden Sie unter  [Eingehende Ansprüche: Anmelden bei SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md).
    
  

> **HINWEIS**
> SharePoint 2013 bietet keine Unterstützung für die Verwendung eines Mitgliedschaftsanbieters, bei dem die Groß- und Kleinschreibung berücksichtigt wird. Für alle Benutzer in der Datenbank wird unabhängig vom Mitgliedschaftsanbieter die SQL-Speicherung verwendet, bei der die Groß- und Kleinschreibung nicht berücksichtigt wird. 
  
    
    


## Anspruchsbasierte Identität und Authentifizierung
<a name="SP15_AuthenticationAuthorizationSecurity_ClaimsBasedIdentity"> </a>

Die anspruchsbasierte Identität ist ein Identitätsmodell in SharePoint 2013. Dieses Identitätsmodell umfasst Features wie die Authentifizierung von Benutzern sowohl von Systemen, die auf Windows basieren, als auch von solchen, die nicht auf Windows basieren, mehrere Authentifizierungstypen, stärkere Authentifizierung in Echtzeit, eine größere Palette an Prinzipaltypen und die Delegierung von Benutzeridentitäten zwischen Anwendungen.
  
    
    
Wenn sich ein Benutzer an SharePoint 2013 anmeldet, wird das Benutzertoken überprüft und anschließend zum Anmelden an SharePoint verwendet. Das Benutzertoken ist ein von einem Anspruchsanbieter ausgegebenes Sicherheitstoken. Die folgenden Anmelde- oder Zugriffsmodi werden angeboten:
  
    
    

- Anmeldung im Windows-Forderungsmodus (Standard)
    
  
- Passiver SAML-Anmeldungsmodus
    
  
- Passive Anmeldung von Mitgliedern und Rollen in ASP.NET
    
  
- Windows-Anmeldung im klassischen Modus (ab dieser Version überholt)
    
  

> **HINWEIS**
> Weitere Informationen zum Anmelden an SharePoint und zu den verschiedenen Anmeldemodi finden Sie unter  [Eingehende Ansprüche: Anmelden bei SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md). 
  
    
    

Wenn Sie Ansprüche unterstützende Anwendungen erstellen, legt der Benutzer der Anwendung eine Identität als eine Gruppe von Ansprüchen vor. Ein Anspruch kann z. B. der Benutzername sein, ein anderer eine E-Mail-Adresse. Der Grundgedanke ist die Konfiguration eines externen Identitätssystems, damit die Anwendung alle benötigten Informationen erhält, um bei jeder Anfrage alles über den Benutzer zu wissen, sowie eine kryptografische Garantie dahingehend zu geben, dass die von der Anwendung empfangenen Identitätsdaten aus einer vertrauenswürdigen Quelle stammen.
  
    
    
Bei diesem Modell ist eine einmalige Anmeldung viel leichter durchzusetzen, und die Anwendung ist nicht mehr für Folgendes verantwortlich:
  
    
    

- Authentifizieren von Benutzern
    
  
- Speichern von Benutzerkonten und Kennwörtern
    
  
- Aufrufen von Unternehmensverzeichnissen zum Nachschlagen von Details zur Benutzeridentität
    
  
- Integrieren in die Identitätssysteme anderer Plattformen oder Unternehmen
    
  
Bei diesem Modell trifft die Anwendung Entscheidungen zur Identität basierend auf den vom Benutzer übermittelten Ansprüchen. Hierbei kann es sich von einer einfachen Anwendungspersonalisierung mit dem Vornamen des Benutzers bis zur Autorisierung des Benutzers für den Zugriff auf hochwertigere Features und Ressourcen in der Anwendung um alles Mögliche handeln.
  
    
    

> **HINWEIS**
> Weitere Informationen zur anspruchsbasierten Identität und zu Anspruchsanbietern finden Sie unter  [Anspruchsbasierte Identität und-Konzepte in SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md) und [Anspruchsanbieter in SharePoint 2013](claims-provider-in-sharepoint-2013.md). 
  
    
    


## Formularbasierte Authentifizierung
<a name="SP15_AuthenticationAuthorizationSecurity_FormsBasedAuthentication"> </a>

Die formularbasierte Authentifizierung stellt eine benutzerdefinierte Identitätsverwaltung in SharePoint 2013 bereit, indem ein Mitgliedschaftsanbieter implementiert wird, der die Schnittstellen zum Identifizieren und Authentifizieren einzelner Benutzer definiert, und ein Rollen-Manager, der die Schnittstellen zum Gruppieren einzelner Benutzer in logische Gruppen und Rollen definiert. In SharePoint 2013 muss ein Mitgliedschaftsanbieter die erforderliche  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx)-Methode implementieren. Wenn ein Benutzername angegeben wird, gibt das Rollenanbietersystem eine Liste der Rollen zurück, zu denen der Benutzer gehört.
  
    
    
Der Mitgliedschaftsanbieter ist für die Überprüfung der Anmeldeinformationen mithilfe der  [System.Web.Security.Membership.ValidateUser](http://msdn.microsoft.com/library/33f4af0b-75c0-4504-b90f-05e742e44a88.aspx)-Methode (nun in SharePoint 2013 erforderlich) verantwortlich. Das tatsächliche Benutzertoken wird jedoch von einem Sicherheitstokendienst (Security Token Service, STS) erstellt. Der STS erstellt das Benutzertoken aus dem vom Mitgliedschaftsanbieter überprüften Benutzernamen und aus der Menge der dem Benutzernamen zugeordneten Gruppenmitgliedschaften, die vom Mitgliedschaftsanbieter bereitgestellt werden.
  
    
    

> **HINWEIS**
> Weitere Informationen zu STS finden Sie unter  [Anspruchsbasierte Identität und-Konzepte in SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md). 
  
    
    

Der Rollen-Manager ist optional. Falls ein benutzerdefiniertes Authentifizierungssystem Gruppen nicht unterstützt, ist auch kein Rollen-Manager erforderlich. SharePoint 2013 unterstützt einen Mitgliedschaftsanbieter und einen Rollen-Manager pro URL-Zone ( [SPUrlZone](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPUrlZone.aspx) ). Den ASP.NET-Formularrollen sind keine inhärenten Rechte zugeordnet. Stattdessen weist SharePoint 2013 den Formularrollen Rechte über seine Richtlinien und Autorisierung zu. In SharePoint 2013 ist die formularbasierte Authentifizierung in das anspruchsbasierte Identitätsmodell integriert. Falls Sie eine zusätzliche Erweiterung benötigen, um die Grenze von einem Rollenanbieter pro URL-Zone zu umgehen, können Sie auf Anspruchsanbieter vertrauen.
  
    
    

> **HINWEIS**
> Weitere Informationen zur anspruchsbasierten Identität und zu Anspruchsanbietern finden Sie unter  [Anspruchsbasierte Identität und-Konzepte in SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md) und [Anspruchsanbieter in SharePoint 2013](claims-provider-in-sharepoint-2013.md). 
  
    
    

Bei der passiven Anmeldung von Mitgliedern und Rollen in ASP.NET erfolgt die Anmeldung durch das Umleiten des Clients an eine Webseite, auf der die ASP.NET-Anmeldesteuerelemente gehostet sind. Nachdem das Identitätsobjekt, das eine Benutzeridentität darstellt, erstellt wurde, konvertiert SharePoint 2013 dies in ein  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) -Objekt (das eine anspruchsbasierte Darstellung eines Benutzers ist).
  
    
    

> **HINWEIS**
> Weitere Informationen zum Anmelden an SharePoint finden Sie unter  [Eingehende Ansprüche: Anmelden bei SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md). 
  
    
    

SharePoint 2013 verwendet die standardmäßige ASP.NET-Rollenanbieterschnittstelle zum Sammeln von Gruppeninformationen zum aktuellen Benutzer. Zum Zweck der Authentifizierung sind Rollen und Gruppen dasselbe: eine Möglichkeit zum Gruppieren von Benutzern in logische Gruppen für die Autorisierung. Jede ASP.NET-Rolle wird als Domänengruppe von SharePoint 2013 behandelt. 
  
    
    
Informationen zum austauschbaren Authentifizierungsframework von ASP.NET finden Sie in der ASP.NET-Dokumentation für Entwickler.
  
    
    

> **HINWEIS**
> Weitere Informationen zur formularbasierten Authentifizierung finden Sie unter  [Formularbasierte Authentifizierung in SharePoint-Produkten und -Technologien (Teil 1): Einführung](http://msdn.microsoft.com/library/e5efd4d7-b369-49f0-a6f7-431d21daff20%28Office.15%29.aspx). 
  
    
    


## Zusätzliche Ressourcen
<a name="SP15_AuthenticationAuthorizationSecurity_AdditionalResources"> </a>


-  [Autorisierung, Benutzer, Gruppen und das Objektmodell in SharePoint 2013](authorization-users-groups-and-the-object-model-in-sharepoint-2013.md)
    
  
-  [Rolle, die Vererbung von, Erhöhung von Berechtigungen und Kennwortänderungen in SharePoint 2013](role-inheritance-elevation-of-privilege-and-password-changes-in-sharepoint-2013.md)
    
  
-  [Anspruchsbasierte Identität in SharePoint 2013](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [Anspruchsbasierte Identität und-Konzepte in SharePoint 2013](claims-based-identity-and-concepts-in-sharepoint-2013.md)
    
  
-  [Konfiguration, Verwaltung und Ressourcen in SharePoint 2013](configuration-administration-and-resources-in-sharepoint-2013.md)
    
  

