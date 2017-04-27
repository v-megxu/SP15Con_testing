---
title: Accès à l'API SOAP
keywords: soap
f1_keywords:
- soap
ms.prod: OFFICE365
ms.assetid: 36e8e3d5-83ac-4bd3-b556-1af132add3eb
---


# Accès à l'API SOAP

Excel Web Services utilise le protocole SOAP (Simple Object Access Protocol) sur HTTP et sert d'interface de communication entre les programmes clients et Excel Services. Le service Web se compose de méthodes et d'un ensemble d'objets de type complexe que vous pouvez utiliser pour accéder aux fonctionnalités complètes d'Excel Web Services. Pour appeler le service, vous devez faire référence au format WSDL (Web Services Description Language) d'Excel Web Services.
  
    
    


## Référence au format WSDL

Pour appeler un service Web avec succès, vous devez savoir comment accéder au service, quelles sont les opérations prises en charge par le service, quels sont les paramètres attendus par le service et quelles sont les données renvoyées par le service. Le format WSDL fournit ces informations dans un document XML qui peut être lu ou traité par un ordinateur.
  
    
    
Le format WSDL du point de terminaison des Excel Web Services est accessible via  `ExcelServices.asmx?wsdl`. Le format WSDL peut être utilisé par les kits de développement qui prennent en charge le protocole SOAP et les services Web, par exemple le Kit de développement Microsoft .NET Framework SDK.
  
    
    
L'exemple suivant illustre le format de l'URL du fichier WSDL des Excel Web Services :
  
    
    
 `http://<server>/<customsite>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
Si vous n'avez pas de site personnalisé, vous pouvez utiliser temporairement l'URL suivante :
  
    
    
 `http://<server>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
Il est recommandé de créer un site personnalisé, puis d'utiliser l'URL incluant le site personnalisé dans le format de l'URL.
  
    
    
Le tableau suivant décrit chaque élément de l'URL.
  
    
    


|****URL element****|****Description****|
|:-----|:-----|
| _server_ <br/> |Nom du serveur sur lequel Microsoft SharePoint Server 2010 est déployé.  <br/> |
| _customsite_ <br/> |Site SharePoint Server 2010 personnalisé créé par l'administrateur du serveur.  <br/> |
| _<endpointname>.asmx_ <br/> |Nom du point de terminaison du service Web. Pour les Excel Web Services, il s'agit de  `ExcelService.asmx`.  <br/> |
   
Pour plus d'informations sur le format WSDL, voir la spécification WSDL du W3C (World Wide Web Consortium) à l'adresse suivante : http://www.w3.org/TR/wsdl.
  
    
    

## Voir aussi


#### Autres ressources


  
    
    
 [Étape 1 : création du projet de client de service Web](step-1-creating-the-web-service-client-project.md)
  
    
    
 [Étape 2 : ajout d'une référence Web](step-2-adding-a-web-reference.md)
  
    
    
 [Étape 3: accès au service Web](step-3-accessing-the-web-service.md)
  
    
    
 [Étape 4 : création et test de l'application](step-4-building-and-testing-the-application.md)
  
    
    
 [Procédure pas à pas : développement d'une application personnalisée à l'aide des services Web Excel](walkthrough-developing-a-custom-application-using-excel-web-services.md)
