---
title: Vorgehensweise Einrichten einer Umgebung für die Entwicklung von mobilen Anwendungen für SharePoint
ms.prod: SHAREPOINT
ms.assetid: acaf556d-e20d-478d-8c59-2efd8efb9dcb
---


# Vorgehensweise: Einrichten einer Umgebung für die Entwicklung von mobilen Anwendungen für SharePoint
In diesem Artikel erhalten Sie Informationen zu den Systemanforderungen und zum Konfigurieren einer Entwicklungsumgebung für SharePoint-Mobilitätsprojekte.
Mindestkonfiguration für die Arbeit mit SharePoint-Mobilitätsprojekte erfordert einen Server mit SharePoint 2013 (oder ein Konto SharePoint Online ) und einer Entwicklungsumgebung auf einem separaten Client-Betriebssystem. Installieren von SharePoint 2013 auf Clientbetriebssysteme (beispielsweise Windows 7 ) ist nicht unterstützte und Installieren von erforderlichen Tools für die Entwicklung für Windows Phone wird nicht auf Server-Betriebssystemen (beispielsweise Windows Server 2008 ).
  
    
    


## Windows Phone-Entwicklungsprojekte und SharePoint Server
<a name="SP15Setupmobile_winphone"> </a>

Zum Erstellen und Testen von Windows Phone-apps, die mit SharePoint interagieren, benötigen Sie Zugriff auf einen Server mit SharePoint 2013 oder ein Konto SharePoint Online und benötigen Sie ausreichende Berechtigungen für die Websites und Listen Sie in Ihren Lösungen verwenden möchten. Es wird empfohlen, dass Sie eine Installation von SharePoint Server, der zum Testen und Entwicklung als Zielserver vorgesehen ist verwenden, während Sie Ihre Projekte entwickeln. Verwenden Sie SharePoint Server in einer produktionsumgebung als Zielserver erst nach Ihrer entwickelte Lösung ausreichende Tests unterzogen wurde.
  
    
    
Informationen zur Installation und Konfiguration von SharePoint 2013 finden Sie in die Dokumentation in der  [SharePoint-Produkte](http://technet.microsoft.com/en-us/library/ee428287.aspx) -Abschnitt der Microsoft TechNet Library. Informationen zur Verwendung von SharePoint Online Ihre Entwicklung von Lösungen finden Sie auf der [SharePoint Online-Entwicklerressourcencenter](http://msdn.microsoft.com/en-us/sharepoint/gg153540.aspx).
  
    
    
Die Codebeispiele in dieser Dokumentation wird davon ausgegangen, dass ein Entwickler mit dem Beispiel hat oder erhalten Sie über ausreichende Berechtigungen für SharePoint-Websites und Listen werden sollen, hinzufügen, bearbeiten und Löschen von Daten.
  
    
    

## Konfigurieren einer Client-Entwicklungsumgebung für Mobilität von SharePoint-Projekten
<a name="SP15Setupmobile_configure"> </a>

Informationen zum Entwickeln von SharePoint-Add-Ins für die Verwendung auf Windows Phone-Geräten, müssen Sie Ihre Entwicklungstools auf einem Computer einrichten, die einem Clientbetriebssystem nicht auf einem Server-Betriebssystem ausgeführt wird.
  
    
    

### Konfigurieren von Windows Phone SDK 8.0

Informationen zum Entwickeln von SharePoint-Add-Ins für die Verwendung auf Windows Phone 8, müssen Sie Ihre Entwicklungstools auf einem Computer einrichten, die Clientversionen Windows 8 64-Bit (X 64) oder Windows 8 Pro ausgeführt wird. Windows Phone 8-Emulator erfordert Windows 8 Pro und erfordert einen Prozessor, der Second Level Address Translation (SLAT) unterstützt.
  
    
    

1. Installieren Sie auf einem Computer mit einem unterstützten Client-Betriebssystem  [Windows Phone SDK 8.0](http://www.microsoft.com/en-us/download/details.aspx?id=35471). Die Windows Phone Software Development Kit (SDK) 8.0 enthält die Tools, die Sie zum Entwickeln von apps und Spiele für Windows Phone 8 und Windows Phone 7.5 benötigen.
    
    Die Windows Phone SDK 8.0 ist eine voll funktionsfähige Entwicklungsumgebung zum Erstellen von apps und Spiele für Windows Phone 8.0 und Windows Phone 7.5 verwenden. Windows Phone SDK bietet eine eigenständige Version von Visual Studio Express 2012 für Windows Phone oder als ein Add-in auf Visual Studio 2012 Professional, Premium oder Ultimate Edition funktioniert. Mit dem SDK können Sie Ihre vorhandenen programming Fähigkeiten und Code verwenden, verwalteten oder systemeigenen Code apps erstellen. Das SDK enthält darüber hinaus mehrere Emulatoren und weitere Tools für das Profil erstellen und Testen Ihrer Windows Phone-app unter Umständen Praxis.
    
    > **HINWEIS**
      > Wenn der Computer die Hardware und Betriebssystem erfüllt, jedoch nicht die Anforderungen für die Windows Phone 8-Emulator erfüllt, wird die Windows Phone SDK 8.0 installieren und ausführen. Allerdings Windows Phone 8-Emulator ist nicht funktionsfähig, und Sie werden nicht in der Lage, bereitstellen oder Testen von apps auf dem Windows Phone 8-Emulator. Informationen zu den Systemanforderungen für die Ausführung der Windows Phone-Emulator finden Sie unter  [Setup und System Requirements für Windows Phone-Emulator](http://msdn.microsoft.com/en-us/library/ff626524).
2. Installieren Sie  [Microsoft SharePoint SDK für Windows Phone 8](http://www.microsoft.com/en-us/download/details.aspx?id=36818).
    
    SharePoint SDK für Windows Phone installiert zwei Silverlight für Windows Phone-Vorlagen (neben von Windows Phone SDK installiert): die Vorlage Windows Phone leeres SharePoint-Anwendung und die Vorlage Windows Phone SharePoint List Application. Das SDK auch installiert, SharePoint-CSOM-Bibliotheken, eine Authentifizierungsbibliothek und Windows Phone-Projektvorlagen und es nun die NTLM-Authentifizierung unterstützt. Die gebündelten-APIs und Vorlagen können Sie um Windows Phone 8 Applications gegen SharePoint 2013 zu erstellen.
    
    Darüber hinaus wird im SharePoint SDK für Windows Phone mehrere unterstützenden Laufzeit-Assemblys (in  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v8.0\\Libraries` für eine Standardinstallation) installiert.
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **HINWEIS**
      > Die Vorlagen im SharePoint SDK für Windows Phone stehen derzeit für C#-Projekte nur aus.
Weitere Informationen zu den im SharePoint SDK für Windows Phone-Vorlagen finden Sie unter  [Überblick über Anwendungsvorlagen für Windows Phone SharePoint 2013 in Visual Studio](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md).
  
    
    

### Konfigurieren von Windows Phone SDK 7.1

Informationen zum Entwickeln von SharePoint-Add-Ins für die Verwendung auf Windows Phone 7, müssen Sie richten Sie Ihre Entwicklungstools auf einem Computer mit Windows 7 (32-Bit oder 64-Bit) oder Windows Vista Service Pack 2 (32-Bit oder 64-Bit). Die Windows Phone Software Development Kit (SDK) 7.1 wird nicht auf Windows Server 2008 oder in Windows XP unterstützt.
  
    
    

1. Installieren Sie auf einem Computer mit einem unterstützten Client-Betriebssystem  [Windows Phone SDK 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=27570).
    
    > **HINWEIS**
      > Eine frühere Version von Windows Phone SDK hieß Windows Phone-Entwicklertools.

    Windows Phone SDK installiert Microsoft Visual Studio 2010 Express für Windows Phone, die Windows Phone-Emulator, XNA Spiel Studio und Microsoft Expression Blend für Windows Phone. Visual Studio 2010 Express For Windows Phone ist eine geeignete Entwicklungsumgebung für die meisten Windows Phone-Lösungen. Sie können auch Visual Studio 2010 Professional als Ihre bevorzugten Entwicklungsumgebung, aber noch Windows Phone SDK, installieren Sie die Visual Studio die erforderliche add-ins installiert werden müssen. (Windows Phone SDK wird nicht aktuell für die Verwendung mit Visual Studio 2012 unterstützt.)
    
    Informationen zu zusätzlichen Systemanforderungen und Anweisungen für die Installation von Windows Phone SDK finden Sie unter  [Installieren von Windows Phone SDK](http://msdn.microsoft.com/en-us/library/ff402530). Informationen zu den Systemanforderungen für die Ausführung der Windows Phone-Emulator finden Sie unter  [Setup und System Requirements für Windows Phone-Emulator](http://msdn.microsoft.com/en-us/library/ff626524).
    
  
2. Installieren Sie  [Microsoft SharePoint SDK für Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476).
    
    SharePoint SDK für Windows Phone installiert zwei Silverlight für Windows Phone-Vorlagen (neben von Windows Phone SDK installiert): die Vorlage Windows Phone leeres SharePoint-Anwendung und die Vorlage Windows Phone SharePoint List Application.
    
    Darüber hinaus wird im SharePoint SDK für Windows Phone mehrere unterstützenden Laufzeit-Assemblys (in  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v7.1\\Libraries` für eine Standardinstallation) installiert.
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **HINWEIS**
      > Die Vorlagen im SharePoint SDK für Windows Phone stehen derzeit für C#-Projekte nur aus.
Weitere Informationen zu den im SharePoint SDK für Windows Phone-Vorlagen finden Sie unter  [Überblick über Anwendungsvorlagen für Windows Phone SharePoint 2013 in Visual Studio](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md).
  
    
    

## Zusätzliche Ressourcen
<a name="SP15Setupmobile_addlresources"> </a>


-  [Erstellen von Windows Phone-Apps, die auf SharePoint 2013 zugreifen](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/en-us/download/details.aspx?id=35471)
    
  
-  [Microsoft SharePoint SDK für Windows Phone 8](http://www.microsoft.com/en-us/download/details.aspx?id=36818)
    
  
-  [Windows Phone SDK 7.1](http://www.microsoft.com/de-de/download/details.aspx?id=27570)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476)
    
  

