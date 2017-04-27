---
title: Accessing the SOAP API
keywords: soap
f1_keywords:
- soap
ms.prod: OFFICE365
ms.assetid: 36e8e3d5-83ac-4bd3-b556-1af132add3eb
---


# Accessing the SOAP API

Excel Web Services verwendet SOAP (Simple Object Access-Protokoll) über HTTP und dient als Kommunikationsschnittstelle zwischen Clientprogrammen und Excel Services. Der Webdienst besteht aus Methoden und einer Reihe komplexer Objekte, mit denen Sie auf die gesamten Funktionen von Excel Web Services zugreifen können. Zum Aufrufen dieses Diensts müssen Sie Web Services Description Language (WSDL) von Excel Web Services verwenden.
  
    
    


## Verwenden von WSDL

Für den erfolgreichen Aufruf eines Webdiensts müssen Sie wissen, wie auf den Dienst zugegriffen wird, welche Vorgänge von dem Dienst unterstützt werden, welche Parameter von dem Dienst erwartet werden und was von dem Dienst zurückgegeben wird. WSDL stellt diese Informationen in einem XML-Dokument bereit, das von einem Computer gelesen oder verarbeitet werden kann.
  
    
    
Der Zugriff auf WSDL für den Endpunkt von Excel Web Services erfolgt über  `ExcelServices.asmx?wsdl`. WSDL kann von Development Kits verwendet werden, die SOAP und Webdienste unterstützen, wie z. B. das Microsoft .NET Framework SDK.
  
    
    
Im folgenden Beispiel wird das Format der URL zur WSDL-Datei von Excel Web Services gezeigt:
  
    
    
 `http://<server>/<customsite>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
Wenn keine benutzerdefinierte Website vorhanden ist, kann temporär die folgende URL verwendet werden:
  
    
    
 `http://<server>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
Es wird empfohlen, eine benutzerdefinierte Website zu erstellen und dann die URL, die die benutzerdefinierte Website enthält, im URL-Format zu verwenden.
  
    
    
In der folgenden Tabelle werden die einzelnen Elemente in der URL beschrieben.
  
    
    


|****URL element****|****Description****|
|:-----|:-----|
| _server_ <br/> |Der Name des Servers, auf dem Microsoft SharePoint Server 2010 bereitgestellt wird. <br/> |
| _customsite_ <br/> |Eine benutzerdefinierte SharePoint Server 2010-Website, die vom Serveradministrator erstellt wird. <br/> |
| _<endpointname>.asmx_ <br/> |Der Name des Webdienstendpunkts. Für Excel Web Services ist dies  `ExcelService.asmx`. <br/> |
   
Weitere Informationen zum WSDL-Format finden Sie in der WSDL-Spezifikation des World Wide Web Consortium (W3C) unter **http://www.w3.org/TR/wsdl**.
  
    
    

## Siehe auch


#### Weitere Ressourcen


  
    
    
 [Step 1: Creating the Web Service Client Project](step-1-creating-the-web-service-client-project.md)
  
    
    
 [Step 2: Adding a Web Reference](step-2-adding-a-web-reference.md)
  
    
    
 [Step 3: Accessing the Web Service](step-3-accessing-the-web-service.md)
  
    
    
 [Step 4: Building and Testing the Application](step-4-building-and-testing-the-application.md)
  
    
    
 [Walkthrough: Developing a Custom Application Using Excel Web Services](walkthrough-developing-a-custom-application-using-excel-web-services.md)
