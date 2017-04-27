---
title: Einrichten einer Entwicklungsumgebung für BCS in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: d83c8a43-49dd-47eb-94d4-23aa2cf71a9a
---


# Einrichten einer Entwicklungsumgebung für BCS in SharePoint 2013
Informationen Sie zum Einrichten einer Entwicklungsumgebung für die Entwicklung von Lösungen SharePoint 2013 und SharePoint-Add-Ins mit Business Connectivity Services (BCS).
Sie können die SharePoint 2013 Lösungen und SharePoint-Add-Ins erstellen, mithilfe von BCS auf einem Clientcomputer oder auf einem Servercomputer, abhängig von der Art der Lösung, die Sie erstellen.
  
    
    


## Erstellen von Server-basierte Lösungen und SharePoint-Add-Ins
<a name="SP15SettingupdevenvBCS_server"> </a>

In der Regel wird die Mehrheit der BCS Lösungen und apps in einer Server-Umgebung gehostet werden. Diese Lösungen für Server und apps bieten die größte Maß an Flexibilität mit allen Features von BCS in SharePoint 2013.
  
    
    
Für Server-basierte Lösungen empfiehlt es sich in der Regel die Lösung auf einem lokalen Computer zu entwickeln, auf dem SharePoint 2013 installiert ist, und dann, wenn die Lösung wird erstellt und getestet, Bereitstellen auf den Produktionsserver. Sie können eine Entwicklungsumgebung installieren, auf einer Host-Arbeitsstation oder auf einen oder mehrere virtuelle Computer, auf dem Windows Server 2008 Service Pack 2 ausgeführt werden.
  
    
    

### Einrichten einer Umgebung SharePoint-Add-Ins erstellen

Die Umgebung, die Sie verwenden, für die Entwicklung von apps mit BCS ist die gleichen wie für eine beliebige SharePoint-Add-In entwickeln.
  
    
    
Weitere Informationen zum Installieren der Komponenten von einer Entwicklungsumgebung, einschließlich Betriebssystem, SharePoint 2013, Visual Studio 2012 und Office Developer Tools für Visual Studio 2012, befolgen Sie die Anweisungen in  [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md).
  
    
    

## Erstellen von Client-basierte Lösungen
<a name="SP15SettingupdevenvBCS_client"> </a>

Client-basierter Lösungen aktivieren Office 2013-Clientanwendungen auf die gleichen externen Daten zugreifen, die eine SharePoint 2013 Lösung oder SharePoint-Add-In kann. Hierzu können Sie Code mithilfe von BCS-Clientcache implementieren. Die Clientkomponenten kommunizieren mit BCS über den clientseitigen Code und Clientcache. Dadurch wird die Office-Clientanwendungen mit den umfangreichen Daten, die über externe Inhaltstypen in SharePoint verfügbar sind.
  
    
    
Da diese Lösungen Code nicht erforderlich ist, können Sie SharePoint Designer 2013 und Office 2013 verwenden.
  
    
    

## Zusätzliche Ressourcen
<a name="SP15SettingupdevenvBCS_addresources"> </a>


-  [Einrichten einer lokalen Entwicklungsumgebung für SharePoint-Add-Ins](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)
    
  
-  [Erste Schritte mit den Business Connectivity Services in SharePoint 2013](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Business Connectivity Services in SharePoint 2013](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [Übersicht über die SharePoint 2013-Entwicklung](sharepoint-2013-development-overview.md)
    
  

