---
title: Step 4 Building and Testing the Application
ms.prod: SHAREPOINT
ms.assetid: f2feeecb-1b4c-4049-be4e-11d414f13d9f
---


# Step 4: Building and Testing the Application

In diesem Schritt erstellen und testen Sie die Anwendung. In Visual Studio stehen mehrere Methoden zum Erstellen und Ausführen einer Konsolenanwendung in der IDE zur Verfügung. Dazu gehören:
  
    
    


- Starten ohne Debuggen (STRG+F5)
    
  
- Starten (F5)
    
  

## Erstellen, Ausführen und Debuggen der Anwendung


### So erstellen Sie die Anwendung und führen sie aus


1. Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**, oder drücken Sie STRG+F5. Dadurch wird sichergestellt, dass das Konsolenfenster nach der Ausführung des Programms geöffnet bleibt.
    
  
2. Die folgende Ausgabe wird in der Konsole angezeigt.
    
    > **HINWEIS**
      > Die angezeigten Werte hängen von den Werten ab, die Sie in der Arbeitsmappe, der Sitzungs-ID usw. verwenden.

  ```
  
The Credential is: System.Net.SystemNetworkCredential
Total rows in range: 18
Value in range is: 4245.955129
  ```

3. Drücken Sie eine beliebige Taste, um **SampleApplication.exe** zu schließen.
    
  

### Ausnahme "Datei nicht gefunden"


1. Wenn der bereitgestellte Pfad zu der Arbeitsmappe falsch ist, wird die Ausnahme "Datei nicht gefunden" ausgelöst, die durch folgenden Code abgefangen wird:
    
  ```cs
  
catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As SoapException
Console.WriteLine("SOAP Exception Message: {0}", e.Message)
End Try
  ```

2. Die folgende Ausgabe wird für die SOAP-Ausnahme in der Konsole angezeigt:
    
  ```
  
SOAP Exception Message: The file you selected could not be found. Check the spelling of the file name and verify that the location is correct.

  ```


### Ausnahme "Der Index liegt außerhalb des gültigen Bereichs"


1. Wenn Sie versuchen, einen Wert außerhalb des Bereichs abzurufen, erhalten Sie eine **System.IndexOutOfRangeException**-Ausnahme. Die folgende Ausgabe wird in der Konsole angezeigt:
    
  ```
  
The Credential is: System.Net.SystemNetworkCredential
The sessionID is : 64.28e58e90-b757-4658-b1c4-890ad68ef6cbRmqR4IINXfkMeOJRG8Iq0Y
27tVk=110.33d3R6fqv7tr2jPyYiPwRu|!@en-US|en-US|+0480#0000-10-00-05T02:00:00:0000
#+0000#0000-04-00-01T02:00:00:0000#-0060
Total rows in range: 18
  ```

2. Anschließend erhalten Sie eine unbehandelte Ausnahme mit folgender Meldung:
    
  ```
  
An unhandled exception of type 'System.IndexOutOfRangeException' occurred in SampleApplication.exe
Additional information: Index was outside the bounds of the array.
  ```

3. Sie können die obige unbehandelte Ausnahme behandeln, indem Sie nach dem **catch**-Block für die SOAP-Ausnahme einen weiteren **catch**-Block zum Abfangen der Ausnahme hinzufügen, wie im Folgenden gezeigt:
    
  ```cs
  
catch (Exception e)
{
    Console.WriteLine("Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As Exception
Console.WriteLine("Exception Message: {0}", e.Message)
End Try
  ```


### So führen Sie die Anwendung durch Drücken von F5 aus


1. Sie können die Anwendung ausführen, indem Sie im Menü **Debuggen** auf **Starten** klicken, oder indem Sie F5 drücken. Damit sichergestellt ist, dass das Konsolenfenster nach Ausführung des Programms geöffnet bleibt, können Sie am Ende des Codes (nach dem **catch**-Block) die folgende Codezeile hinzufügen:
    
  ```cs
  
Console.ReadLine();
  ```


  ```VB.net
  Console.ReadLine()
  ```

2. Drücken Sie eine beliebige Taste, um **SampleApplication.exe** zu schließen.
    
  

## Siehe auch


#### Konzepte


  
    
    
 [Accessing the SOAP API](accessing-the-soap-api.md)
#### Weitere Ressourcen


  
    
    
 [Step 1: Creating the Web Service Client Project](step-1-creating-the-web-service-client-project.md)
  
    
    
 [Step 2: Adding a Web Reference](step-2-adding-a-web-reference.md)
  
    
    
 [Step 3: Accessing the Web Service](step-3-accessing-the-web-service.md)
  
    
    
 [Walkthrough: Developing a Custom Application Using Excel Web Services](walkthrough-developing-a-custom-application-using-excel-web-services.md)
  
    
    
 [How to: Trust Workbook Locations Using Script](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)
