---
title: Mithilfe des Cmdlets Kopplung Register-SPWorkflowService
ms.prod: SHAREPOINT
ms.assetid: 91fca6c2-60ca-4177-8560-2b310dac0e2c
---



# Mithilfe des Cmdlets Kopplung Register-SPWorkflowService
Erfahren Sie, wie das Cmdlet **Register-SPWorkflowService** zu erfolgreich Paar SharePoint Server 2013 mit Workflow-Manager verwenden.
Installieren und Konfigurieren von Microsoft SharePoint Server 2013 zur Unterstützung der Workflowentwicklung erfordert "Paarung" Ihrer Installationen von SharePoint Server 2013 und Workflow-Manager. In den meisten Szenarien wird diese Paarung problemlos mithilfe Cmdlet **Register-SPWorkflowService**, die in der SharePoint-Installation enthalten ist.
  
    
    

Dieses Cmdlet ist wichtiger, nicht für jede paarungs Szenario hilfreich. **Register-SPWorkflowService** ist nur in den folgenden paarungs Szenarien hilfreich:
- Einem Servercomputer Farm, auf dem SharePoint Server 2013 und Workflow-Manager auf dem Server im Feld gemeinsame befinden.
    
  
- Drei Computern Serverfarm, wo sich SharePoint Server 2013 und Workflow-Manager auf allen drei Computern gemeinsame befinden. (Fügen Sie hinzu, dass ein vierter Computer ist, muss auf einem separaten Computer sein, Suche und Workflow-Manager HA ist erforderlich. Wenn letztere erforderlich ist, muss es auf allen drei Computern installiert sein.
    
  
- Farm mit drei Computern SharePoint Server 2013 gepaart mit einer Serverfarm nicht-co-befindet sich Workflow-Manager.
    
  
Beachten Sie außerdem, dass diese **Register-SPWorkflowService** die Anmeldeinformationen des aktuellen Benutzers verwendet werden.
## Cmdlet-Entwurf


****


|**Detail**|**Beschreibung**|
|:-----|:-----|
|Verb <br/> |Registrieren <br/> |
|Name <br/> |SPWorkflowService <br/> |
|Beschreibung <br/> |-Paare eine sps15short-Farm mit einer Workflow-Manager Farm aus. Sie müssen dieses Cmdlet einmal pro Farm ausführen. Bevor Sie das Cmdlet ausführen, müssen Sie im Zertifikatspeicher des Computers und SharePoint-Zertifikatspeicher Stammzertifikat der Zertifizierungsstelle installieren. Verwenden Sie hierzu das Cmdlet **New-SPTrustedRootAuthority**. (Siehe unten). <br/> |
|Ausgabetyp <br/> |Keine. <br/> |
|Syntax <br/> | `Register-SPWorkflowService -SPSite <URI or GUID representing an SPSite object> -WorkflowHostUri <workflow service endpoint URL> -ScopeName <string> [-PartitionMode] [-AllowOAuthHttp] [-Force]` <br/> |
   

## Cmdlet-Parameter



|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|SPSite          (erforderlich) <br/> |**SPSitePipeBind** <br/> |Die URL einer Websitesammlung langfristig in der SharePoint Server-Farm, die als paarungs Endpunkt fungiert. Informationen für die Bildung wird von dieser URL abgeleitet. <br/> |
|WorkflowHostUri          (Required) <br/> |String <br/> |Die URL des Endpunkts Workflow-Manager für die Verbindung. Ermöglicht es dem Workflowhost URI zusammen mit der Portnummer. <br/> |
|ScopeName <br/> |String <br/> |Der Name, der vom Workflowdienst zum Identifizieren der kombinierte SharePoint Server Farm verwendet werden. Der Standardwert ist "SharePoint". Sie müssen nur diesen Parameter angeben, wenn Sie mehrere SharePoint-Serverfarmen zu einer Farm Workflow-Manager Kopplung möchten. <br/> |
|PartitionMode <br/> |SwitchParameter <br/> |Verwenden Sie diesen Parameter nur für SharePoint-Farm mit mehreren Mandanten. Die partitionsmodus wird pro SharePoint-Dienst angegeben. Beachten Sie, dass Sie mehrmandantenfähigkeit in einer SharePoint-Farm erstellen können, nachdem dieses Cmdlet ausgeführt wird. aus diesem Grund kann nicht mit dem Cmdlet dieser Parameterwert implizit aus dem bestehenden Zustand der SharePoint-Farm abzuleiten. <br/> |
|AllowOAuthHttp <br/> |SwitchParameter <br/> |Ermöglicht Exchange OAuth und Metadaten über HTTP. Dies ist nützlich, testen, aber nicht in den Produktionsmodus versetzen. Verwenden Sie diese nur, wenn SharePoint zur Unterstützung von HTTP konfiguriert ist. Es ist nicht erforderlich, dass die Workflow-Manager für die Verwendung von HTTP konfiguriert werden. <br/> |
|Force <br/> |SwitchParameter <br/> |Erzwingt das Erstellen des Bereichs mit  _ScopeName_ -Parameter oder einen vorhandenen Bereich entspricht der gleichen _ScopeName_aktualisiert. Wenn nicht angegeben und des Umfangs mit der gleiche Namen vorhanden ist, wird das Cmdlet wird ein Fehler ausgelöst. <br/> |
   

## Beispiel


```

PS> Register-SPWorkflowService -SPSite "https://myserver/mysitecollection" -WorkflowHostUri "http://workflow.example.com:12291" -ScopeName "SharePoint2" -PartitionMode -AllowOAuthHttp  -Force
```


## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>


-  [Installieren und Konfigurieren von Workflows für SharePoint Server 2013](http://technet.microsoft.com/en-us/library/jj658588.aspx)
    
  
-  [Video Series: Installieren und Konfigurieren von Workflows in SharePoint Server 2013](http://technet.microsoft.com/en-us/library/dn201724.aspx)
    
  
-  [Workflow-Manager 1.0](http://msdn.microsoft.com/en-us/library/jj193528%28Azure.10%29)
    
  
