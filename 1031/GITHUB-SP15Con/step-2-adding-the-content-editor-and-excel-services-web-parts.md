---
title: Step 2 Adding the Content Editor and Excel Services Web Parts
ms.prod: SHAREPOINT
ms.assetid: c9c66843-fd77-4a0d-a512-d936d15d4429
---


# Step 2: Adding the Content Editor and Excel Services Web Parts

Nachdem Sie eine ECMAScript (JavaScript, JScript)-Textdatei erstellt und an einem vertrauenswürdigen Speicherort gespeichert haben, erstellen Sie im nächsten Schritt eine Webparts-Seite und fügen der Seite das Inhalts-Editor-Webpart und das Excel Services-Webpart hinzu.
  
    
    

Zeigen Sie als nächstes eine Arbeitsmappe mithilfe des Excel Services-Webparts an, das Sie der Seite hinzugefügt haben. 
### So fügen Sie das Inhalts-Editor-Webpart und das Excel Services-Webpart hinzu


1. Erstellen Sie eine neue Webparts-Seite.
    
  
2. Fügen Sie der soeben erstellten Webparts-Seite ein Inhalts-Editor-Webpart hinzu.
    
  
3. Fügen Sie die URL der Textdatei, die Sie in  [Step 1: Creating a ECMAScript Text File](step-1-creating-a-ecmascript-text-file.md) erstellt haben, dem Inhalts-Editor-Webpart hinzu. Fügen Sie dazu die URL für die Textdatei hinzu, die Sie in [Step 1: Creating a ECMAScript Text File](step-1-creating-a-ecmascript-text-file.md) in eine vertrauenswürdige Dokumentbibliothek hochgeladen haben.
    
    Beispiel:
    
     `http://` _meinserver_ `/Docs/Documents/JSOM_FeedToContentEditor.txt`
    
  
4. Fügen Sie der Seite ein Excel Services-Webpart hinzu.
    
  

### So führen Sie das ECMAScript-Beispiel aus


1. Laden Sie eine Arbeitsmappe in eine vertrauenswürdige Dokumentbibliothek hoch. Zeigen Sie mithilfe des Menüs **Freigegebenes Webpart bearbeiten** den Aufgabenbereich des Excel Services-Webparts an. Geben Sie im Abschnitt **Arbeitsmappenanzeige** im Feld **Arbeitsmappe** die URL der Arbeitsmappe ein, die vom Excel Services-Webpart geladen und angezeigt werden soll. Beispiel:
    
     `http://` _meinserver_ `/Docs/Documents/WorkbookToDisplay.xlsx`
    
  
2. Klicken Sie auf verschiedene Zellen, und beobachten Sie, wie der Wert der Zelle im Inhalts-Editor **div** aufgefüllt wird.
    
  

