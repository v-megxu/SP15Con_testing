---
title: Vorgehensweise Legen Sie die Bing Maps-Taste auf Ordnerebene Web und Farm in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 507ed9de-c349-44b5-b182-e838795dd862
---


# Vorgehensweise: Legen Sie die Bing Maps-Taste auf Ordnerebene Web und Farm in SharePoint 2013

  
    
    
![Thema mit Anleitung](images/mod_icon_howto.png)
  
    
    

  
    
    

  
    
    
In diesem Artikel erfahren Sie, wie Sie den Bing Maps-Schlüssel programmgesteuert auf der Web- und der Farmebene mithilfe des SharePoint 2013-Clientobjektmodells und von Windows PowerShell festlegen, um die Bing Maps-Funktionen in SharePoint-Listen sowie standortbasierten Web-Apps und mobilen Apps zu aktivieren.

  
    
    


## Erforderliche Komponenten für die Festlegung des Bing Maps-Schlüssels
<a name="SP15Bing_prereq"> </a>

Zum Ausführen der Schritte in diesem Beispiel sollten Sie über Folgendes verfügen:
  
    
    

- SharePoint 2013, mit Administratorrechten.
    
  
- Ein gültiger Bing Maps-Schlüssel, die Sie von der  [Bing Maps-Kontocenter](https://www.bingmapsportal.com/)erhalten können.
    
    > **WICHTIG**
      > Bitte beachten Sie, dass Sie für Benutzer von der Anwendung für die Einhaltung von Ausdrücken und Vorschriften für Ihre Verwendung von Bing Maps-Schlüssel und alle erforderlichen Angaben verantwortlich sind hinsichtlich Daten an den Bing Maps-Dienst weitergeleitet.

## Codebeispiel: Legen Sie den Bing Maps-Schlüssel Farm oder Web-Ebene
<a name="SP15Setbing_farm"> </a>

Ebene der Farm oder Web kann der Bing Maps-Schlüssel festgelegt werden. Um den Bing Maps-Schlüssel auf Farmebene festgelegt, benötigen Sie Administratorrechte auf dem Server; Sie können den Schlüssel dann mithilfe der SharePoint 2013-Verwaltungsshell hinzufügen. Um den Bing Maps-Schlüssel auf der Ebene der Webserver festzulegen, Schreiben Sie eine Konsolenanwendung, die das SharePoint-Clientobjektmodell verwendet.
  
    
    

> **TIPP**
> Der Bing Maps-Schlüssel auf der Ebene Webserver festgelegt hat höhere Rangfolge als der Bing Maps-Schlüssels auf Farmebene festgelegt.
  
    
    


### So legen Sie den Bing Maps-Schlüssel auf Farmebene mithilfe von Windows PowerShell fest


1. Melden Sie sich an den SharePoint-Server als Administrator, und öffnen Sie die SharePoint 2013-Verwaltungsshell.
    
  
2. Führen Sie den folgenden Befehl aus:
    
     `Set-SPBingMapsKey -BingKey "<Enter a valid Bing Maps key>"`
    
    Der Bing Maps-Schlüssel wird nun auf der Farmebene in SharePoint Server 2013 festgelegt.
    
    > **HINWEIS**
      > Wenn Sie Windows PowerShell verwenden, kann nur auf Farmebene der Bing Maps-Schlüssel festgelegt werden. Wenn Sie den Bing Maps-Schlüssel auf der Ebene der Webserver festlegen möchten, können Sie den Schlüssel programmgesteuert, wie im folgenden Abschnitt festlegen.

### Farm oder Web-Ebene mit dem Objektmodell den Bing Maps-Schlüssel festgelegt


1. Starten Sie Visual Studio.
    
  
2. Wählen Sie auf der Menüleiste **Datei**, **Neues Projekt** aus. Das Dialogfeld **Neues Projekt** wird geöffnet.
    
  
3. Klicken Sie im Dialogfeld **Neues Projekt** wählen Sie **c#** im Feld **Installierte Vorlagen**, und wählen Sie dann die Vorlage **Konsolenanwendung**.
    
  
4. Benennen Sie dem Projekt, und wählen Sie dann auf die Schaltfläche **OK**.
    
  
5. Visual Studio erstellt das Projekt. Fügen Sie einen Verweis auf die folgenden Assemblys hinzu, und wählen Sie **OK**.
    
  - Microsoft.SharePoint.Client.dll
    
  
  - Microsoft.SharePoint.Client.Runtime.dll
    
  
6. Fügen Sie eine Richtlinie **using** in der Standard-cs-Datei wie folgt.
    
     `using Microsoft.SharePoint.Client;`
    
  
7. Fügen Sie der Main-Methode in der Datei den folgenden Code.
    
  ```cs
  
class Program
    {
        static void Main(string[] args)
        {
            SetBingMapsKey();
            Console.WriteLine("Bing Maps set successfully");
        }
     static private void SetBingMapsKey()
        {

            ClientContext context = new ClientContext("<Site Url>");
            Web web = context.Web;
            web.AllProperties["BING_MAPS_KEY"] = "<Valid Bing Maps Key>"
            web.Update();
            context.ExecuteQuery();
        }    
    }

  ```

8. Ersetzen Sie die < Website-Url > und  _<Valid Bing Maps Key>_ durch gültige Werte.
    
  
9. Legen Sie das Zielframework in den Projekteigenschaften als .NET Framework 4.0, und führen Sie das Beispiel.
    
  
10. Der Schlüssel sollte jetzt auf der Ebene der Webserver festgelegt werden.
    
  

## Nächste Schritte
<a name="SP15Bing_nextsteps"> </a>

Weitere Informationen zum Arbeiten mit Standort- und Karten-Funktionalität in SharePoint 2013, finden Sie in der folgenden:
  
    
    

-  [Vorgehensweise: Hinzufügen einer Geolocation-Spalte einer Liste in SharePoint 2013 programmgesteuert](how-to-add-a-geolocation-column-to-a-list-programmatically-in-sharepoint-2013.md)
    
  
-  [Vorgehensweise: erweitern den Geolocation-Feldtyp verwenden clientseitiges Rendering](how-to-extend-the-geolocation-field-type-using-client-side-rendering.md)
    
  

