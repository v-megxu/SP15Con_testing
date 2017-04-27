---
title: SharePoint 2013 Design Manager - Bilddarstellungen
ms.prod: SHAREPOINT
ms.assetid: d08a74c0-5674-4f26-8646-11ea1f081c85
---


# SharePoint 2013 Design Manager - Bilddarstellungen
Erfahren Sie, wie Sie eine Bilddarstellung erstellen, zu einer Seite hinzufügen und zuschneiden. Eine Bilddarstellung definiert die Maße, die zur Anzeige von Bildern auf SharePoint-Veröffentlichungswebsites verwendet werden.
Mit Bilddarstellungen können Sie unterschiedlich große Versionen eines Bilds, die alle auf demselben Quellbild basieren, auf verschiedenen Seiten einer Veröffentlichungswebsite anzeigen. Wenn Sie eine Bilddarstellung erstellen, geben Sie die Breite und/oder die Höhe für alle Bilder an, die diese Bilddarstellung verwenden. Die Bilddarstellungen sind für jedes Bild verfügbar, das in eine Bibliothek der betreffenden Websitesammlung hochgeladen wird. Designer können beispielsweise eine Bilddarstellung zur Anzeige von Miniaturbildern und eine weitere Bilddarstellung zur Anzeige von Bannerbildern erstellen. Wenn ein Bild zu einer Seite hinzugefügt wird, kann der Autor die für das Bild zu verwendende Bilddarstellung angeben. Autoren können die Bilddarstellung außerdem zuschneiden, um den Teil des Bilds anzugeben, der in der Bilddarstellung verwendet werden soll. Beim Rendern der Seite wird die korrekte Bildgröße angezeigt.
  
    
    

Bilddarstellungen ermöglichen es Ihnen, ein einzelnes Bild auf unterschiedliche Weise zu rendern. Ein Bild kann in verschiedenen Größen oder mit unterschiedlichem Zuschnitt dargestellt werden. Bei der erstmaligen Anforderung eines Bilds verwendet SharePoint Server die angegebene Bilddarstellung, um das Bild zu generieren. Wenn ein Benutzer eine SharePoint-Website anzeigt, wird die korrekt dimensionierte Version des Bilds auf den Clientcomputer heruntergeladen. Dadurch wird die Größe der auf den Client heruntergeladenen Datei verringert, sodass sich die Websiteleistung verbessert.
## Voraussetzungen für das Verwalten von Bilddarstellungen
<a name="Prerequisites"> </a>

Da Bilddarstellungen von anderen Features in SharePoint Server 2013 abhängen, müssen Sie sicherstellen, dass Sie alle in diesem Abschnitt aufgeführten Voraussetzungen erfüllen, bevor Sie die Verfahren in diesem Thema durchführen. Zu den Voraussetzungen gehören folgende:
  
    
    

- **Eine Veröffentlichungswebsitesammlung** - Die Websitesammlung, der Sie Bilddarstellungen hinzufügen, muss mithilfe des Veröffentlichungsportals oder der Websitesammlungsvorlage des Produktkatalogs erstellt worden sein. Alternativ müssen Veröffentlichungsfeatures in der Websitesammlung aktiviert sein, in der Sie Bilddarstellungen verwenden möchten. Weitere Informationen finden Sie unter [Übersicht über die Veröffentlichung auf Internet-, Intranet und Extranet-Websites](http://technet.microsoft.com/de-de/library/jj635881%28office.15%29.aspx) in der TechNet-Bibliothek.
    
  
- **Ein konfigurierter BLOB-Cache** - Der datenträgerbasierte BLOB-Cache steuert das Zwischenspeichern für Binary Large Objects (BLOBs), wie z. B. häufig verwendete Bild-, Audio- und Videodateien, sowie andere Dateien, die zum Anzeigen von Webseiten verwendet werden, wie z. B. CSS- und JS-Dateien. Der BLOB-Cache muss auf jedem Front-End-Webserver aktiviert werden, auf dem Sie Bilddarstellungen verwenden möchten. Wenn der BLOB-Cache nicht aktiviert ist, wird immer das ursprüngliche Bild verwendet. Weitere Informationen finden Sie unter [Konfigurieren von Cacheeinstellungen für eine Webanwendung](http://technet.microsoft.com/de-de/library/cc770229.aspx) in der TechNet-Bibliothek.
    
  
- **Eine Objektbibliothek (empfohlen)** - Sie können die Objektbibliotheksvorlage verwenden, um eine Bibliothek einzurichten, mit der Sie bequem umfangreiche Medienobjekte wie z. B. Bild-, Audio- oder Videodateien speichern, organisieren und suchen können. Weitere Informationen finden Sie unter [Einrichten einer Objektbibliothek zum Speichern von Bild-, Audio- oder Videodateien](http://office.microsoft.com/de-de/sharepoint-server-help/set-up-an-asset-library-to-store-image-audio-or-video-files-HA102785730.aspx) auf Office.com.
    
  

## Erstellen einer Bilddarstellung
<a name="Create"> </a>

Bei der Erstellung einer Bilddarstellung generiert SharePoint Server 2013 eine eindeutige ID, die diese Bilddarstellung identifiziert. Ein Bild wird nach dem erstmaligen Empfang einer Anforderung der Bilddarstellung durch SharePoint Server generiert.
  
    
    

### So erstellen Sie eine Bilddarstellung


1. Stellen Sie sicher, dass das Benutzerkonto, das dieses Verfahren durchführt, mindestens über Entwurfsberechtigungen für die Website der obersten Ebene der Websitesammlung verfügt.
    
  
2. Wechseln Sie in einem Browser zur Website der obersten Ebene der Veröffentlichungswebsitesammlung.
    
  
3. Klicken Sie auf das Symbol **Einstellungen**. Klicken Sie auf der Seite **Websiteeinstellungen** im Abschnitt **Aussehen und Verhalten** auf **Bilddarstellungen**.
    
    > **HINWEIS**
      > Die Seite "Bilddarstellungen" kann auch über die Standardhomepage der Veröffentlichungswebsite geöffnet werden. Klicken Sie im Abschnitt **Ich bin der visuelle Designer** auf **Bilddarstellungen konfigurieren**. 
4. Klicken Sie auf der Seite **Bilddarstellungen** auf **Neues Element hinzufügen**.
    
  
5. Geben Sie auf der Seite **Neue Bildwiedergabe** in das Feld **Name** einen Namen für die Darstellung ein, z. B.Thumbnail_Small.
    
  
6. Geben Sie in die Textfelder **Breite** und **Höhe** die Breite und Höhe der Darstellung in Pixel ein, und klicken Sie dann auf **Speichern**.
    
  

## Bearbeiten einer Bilddarstellung
<a name="Edit"> </a>

Wenn eine Bilddarstellung bearbeitet wird, werden die neuen Maße bei der nächsten Anforderung des Bilds wirksam. Wenn es ein Bild gibt, das zuvor aus der Bilddarstellung generiert wurde, wird das Bild bei der nächsten Anforderung mit den neuen Maßen erneut generiert.
  
    
    

### So bearbeiten Sie eine Bilddarstellung


1. Stellen Sie sicher, dass das Benutzerkonto, das dieses Verfahren durchführt, mindestens über Entwurfsberechtigungen für die Website der obersten Ebene der Websitesammlung verfügt.
    
  
2. Wechseln Sie in einem Browser zur Website der obersten Ebene der Veröffentlichungswebsitesammlung.
    
  
3. Klicken Sie auf das Symbol **Einstellungen**. Klicken Sie auf der Seite **Websiteeinstellungen** im Abschnitt **Aussehen und Verhalten** auf **Bilddarstellungen**.
    
    > **HINWEIS**
      > Die Seite **Bilddarstellungen** kann auch über die Standardhomepage der Veröffentlichungswebsite geöffnet werden. Klicken Sie im Abschnitt **Ich bin der visuelle Designer** auf **Bilddarstellung konfigurieren**. 
4. Klicken Sie auf der Seite **Bilddarstellungen** auf die Bilddarstellung, die Sie bearbeiten möchten.
    
  
5. Ändern Sie auf der Seite **Bildwiedergabe bearbeiten** den Namen, die Breite oder Höhe der Bilddarstellung.
    
  

## Hinzufügen einer Bilddarstellung
<a name="Add"> </a>

Wenn Sie ein Bild zu einer Seite einer SharePoint-Veröffentlichungswebsite hinzufügen, können Sie die für dieses Bild zu verwendende Bilddarstellung angeben. Wenn die Seite in einem Browser gerendert wird, wird die korrekte Bildgröße angezeigt. Sie können die Bilddarstellung im Rich-Text-Editor, in einem Bildfeldsteuerelement oder in der Bild-URL angeben.
  
    
    

### Angeben der Bilddarstellung mithilfe des Rich-Text-Editors

Wenn ein Bild auf einer Seite eingefügt wird, können Sie die zu verwendende Bilddarstellung angeben, damit die korrekte Bildgröße angezeigt wird, nachdem die Seite gerendert wurde. Die Angabe der Bilddarstellung im Rich-Text-Editor ist nur für Bilder möglich, die in derselben Websitesammlung gespeichert sind, in der sich auch die bearbeitete Seite befindet.
  
    
    

### So geben Sie eine Bilddarstellung mithilfe des Rich-Text-Editors an


1. Klicken Sie auf der Registerkarte **Seite** auf **Bearbeiten**.
    
  
2. Klicken Sie auf das Symbol **Einstellungen** und dann auf **Seite hinzufügen**.
    
  
3. Geben Sie im Fenster **Seite hinzufügen** einen Namen für die Seite ein, und klicken Sie dann auf **Erstellen**.
    
  
4. Positionieren Sie den Mauszeiger im Feld **Seiteninhalt**.
    
  
5. Klicken Sie auf der Registerkarte **Einfügen** auf **Bild** und dann auf **Von SharePoint**.
    
  
6. Suchen Sie das Bild, das Sie zur Seite hinzufügen möchten, wählen Sie es aus, und klicken Sie dann auf **Einfügen**. Das Bild wird in voller Größe angezeigt.
    
  
7. Klicken Sie auf der Registerkarte **Design** in der Gruppe **Auswählen** auf **Formatvariante auswählen**, und wählen Sie dann eine Bilddarstellung aus. Das Bild wird entsprechend der für die Bilddarstellung angegebenen Größe angezeigt.
    
    > **HINWEIS**
      > Der Befehl **Formatvariante auswählen** ist nur für Bilder verfügbar, die in derselben Websitesammlung gespeichert sind wie die aktuell bearbeitete Seite.
8. Wenn Sie die Bilddarstellung zuschneiden möchten, klicken Sie auf **Formatvariante auswählen** und dann auf **Bearbeiten von Formatvarianten**.
    
    Weitere Informationen zum Zuschneiden von Bilddarstellungen finden Sie im Abschnitt  [Zuschneiden einer Bilddarstellung](#Crop) dieses Artikels.
    
  

### Angeben der Bilddarstellung in der Bild-URL

Sie können die Bilddarstellung angeben, indem Sie die Parameter "RenditionID", "Width" oder "Height" zur Bild-URL hinzufügen.
  
    
    
 **RenditionID** - Mit dem Parameter "RenditionID" können Sie die ID der zu verwendenden Bilddarstellung angeben.
  
    
    
 **Width** - Mit dem Parameter "Width" können Sie die Breite der Bilddarstellung in Pixeln angeben. SharePoint Server versucht, eine Bilddarstellung mit der angegebenen Breite zu finden. Als Nächstes versucht SharePoint Server eine Bilddarstellung zu finden, die breiter als die angegebene Breite ist. Wenn mehrere Bilddarstellungen vorhanden sind, die mit diesem Kriterium übereinstimmen, verwendet SharePoint Server die Bilddarstellung, deren Breite der angegebenen am nächsten kommt. Wenn keine Bilddarstellung mit einer Breite vorhanden ist, die größer oder gleich der angegebenen Breite ist, wird das ursprüngliche Bild verwendet.
  
    
    
 **Height** - Mit dem Parameter "Height" können Sie die Höhe der Bilddarstellung in Pixeln angeben. SharePoint Server versucht, eine Bilddarstellung mit der angegebenen Höhe zu finden. Als Nächstes versucht SharePoint Server eine Bilddarstellung zu finden, die höher als die angegebene Höhe ist. Wenn mehrere Bilddarstellungen vorhanden sind, die mit diesem Kriterium übereinstimmen, verwendet SharePoint Server die Bilddarstellung, deren Höhe der angegebenen am nächsten kommt. Wenn keine Bilddarstellung mit einer Höhe vorhanden ist, die größer oder gleich der angegebenen Höhe ist, wird das ursprüngliche Bild verwendet.
  
    
    
 **Width und Height** - Bei Angabe der Parameter "Width" und "Height" versucht SharePoint Server, eine Bilddarstellung mit der angegebenen Breite und Höhe zu finden. Als Nächstes versucht SharePoint Server eine Bilddarstellung zu finden, die dem angegebenen Breiten-/Höhen-Verhältnis am nächsten kommt. Wenn es mehrere Übereinstimmungen gibt, wird die Bilddarstellung mit dem nächstgrößeren Breiten-/Höhen-Verhältnis im Vergleich zur angeforderten Größe ausgewählt.
  
    
    

> **HINWEIS**
> Wenn die Bild-URL die Parameter "RenditionID", "Width" und "Height" enthält, werden die Parameter "Width" und "Height" ignoriert. 
  
    
    

Das folgende Beispiel zeigt die Verwendung des Parameters "RenditionID":
  
    
    



```HTML

<img src="/sites/pub/Assets/Lighthouse.jpg?RenditionID=2" />
```

Das folgende Beispiel zeigt die Verwendung der Parameter "Width" und "Height":
  
    
    



```HTML
<img src="/sites/pub/Assets/Lighthouse.jpg?Width=400&amp;Height=200" />
```


### Angeben der Bilddarstellung im Bildfeldsteuerelement

Ein Entwickler kann die Bilddarstellung angeben, die im Bildfeldsteuerelement verwendet werden soll. Verwenden Sie die **RenditionId**-Eigenschaft, um die ID der Bilddarstellung festzulegen. Weitere Informationen finden Sie unter **RenditionId**.
  
    
    

## Zuschneiden einer Bilddarstellung
<a name="Crop"> </a>

Standardmäßig wird eine Bilddarstellung aus der Mitte des Bilds generiert. Sie können die Bilddarstellung für einzelne Bilder anpassen, indem Sie den Teil des Bilds zuschneiden, den Sie verwenden möchten. Wenn ein Foto beispielsweise ein Leuchtturmmotiv zeigt, die Bilddarstellung jedoch nicht den ganzen Leuchtturm enthält (siehe Abbildung 1), können Sie den ausgewählten Bildbereich so ändern, dass der ganze Leuchtturm angezeigt wird (siehe Abbildung 2). 
  
    
    

**Abbildung 1: Ursprüngliche Bilddarstellung**

  
    
    

  
    
    
![Wiedergabe des Originalbildes](images/ImgRendition_orig.PNG)
  
    
    

**Abbildung 2: Zugeschnittene Bilddarstellung**

  
    
    

  
    
    
![Wiedergabe eines beschnittenen Bildes](images/ImgRendition_crop.PNG)
  
    
    
Eine Bilddarstellung kann in der Objektbibliothek oder auf einer Seite zugeschnitten werden, ohne das ursprüngliche Bild zu ändern. 
  
    
    
Bilddarstellungen können folgendermaßen zugeschnitten werden:
  
    
    

- Designer können eine Bilddarstellung in der Objektbibliothek zuschneiden. Ein Designer möchte beispielsweise angeben, wie ein Bild in der Miniaturbilddarstellung angezeigt wird.
    
  
- Autoren können eine Bilddarstellung zuschneiden, wenn sie ein Bild in eine Seite einfügen. Dadurch können sie das Erscheinungsbild der Seite anpassen. Wenn ein Autor eine Bilddarstellung zuschneidet, wird auch die Bilddarstellung für das Bild geändert. Jedem Benutzer der Bilddarstellung wird das zugeschnittene Bild angezeigt.
    
    > **HINWEIS**
      > Ein Autor kann eine Bilddarstellung nur zuschneiden, wenn das ursprüngliche Bild in einer Bibliothek gespeichert ist, die sich in derselben Websitesammlung befindet wie die aktuell bearbeitete Seite. In websiteübergreifenden Veröffentlichungsszenarios kann ein Autor die Bilddarstellung beispielsweise nur zuschneiden, wenn das Bild in derselben Websitesammlung gespeichert ist wie der Kataloginhalt. Andernfalls muss die Bilddarstellung in der Objektbibliothek zugeschnitten werden. 

### Zuschneiden einer Bilddarstellung in der Objektbibliothek

Designer können eine Bilddarstellung in der Objektbibliothek zuschneiden.
  
    
    

### So schneiden Sie eine Bilddarstellung in der Objektbibliothek zu


1. Vergewissern Sie sich, dass das Benutzerkonto, mit dem dieses Verfahren durchgeführt wird, über Schreibberechtigungen für die Objektbibliothek verfügt, in der sich das Bild befindet.
    
  
2. Wechseln Sie in einem Browser zur Objektbibliothek.
    
  
3. Positionieren Sie den Mauszeiger in der unteren rechten Ecke des Bilds, dessen Darstellung Sie ändern möchten, wählen Sie die angezeigten Ellipsen ( **...**) aus, und klicken Sie dann auf **BEARBEITEN VON FORMATVARIANTEN**.
    
    > **HINWEIS**
      > Sie können die Seite **Bearbeiten von Formatvarianten** auch öffnen, indem Sie den Mauszeiger über dem Vorschaubild in der Objektbibliothek positionieren und dann das Kontrollkästchen aktivieren, das unter dem Vorschaubild angezeigt wird. Klicken Sie dann auf der Registerkarte **Design** auf **Bearbeiten von Formatvarianten**. 

    Die Seite "Bearbeiten von Formatvarianten" zeigt ein Vorschaubild für jede Bilddarstellung an, die in der Websitesammlung definiert ist.
    
  
4. Suchen Sie nach der Bilddarstellung, die Sie ändern möchten, und klicken Sie dann auf **Zu ändernde Formatierung**.
    
  
5. Verwenden Sie im Fenster **Darstellung zuschneiden** das Bildtool, um den Teil des Bilds auszuwählen, den Sie in der Bilddarstellung verwenden möchten.
    
  
6. Wählen Sie **Speichern**.
    
  
Wenn sich das Bild und die aktuell bearbeitete Seite in derselben Websitesammlung befinden, können Sie eine Bilddarstellung auch mithilfe des Rich-Text-Editors zuschneiden.
  
    
    

### Zuschneiden einer Bilddarstellung auf einer Seite

Autoren können eine Bilddarstellung zuschneiden, wenn sie ein Bild in eine Seite einfügen. Dadurch können sie das Erscheinungsbild der Seite anpassen. Wenn ein Autor eine Bilddarstellung zuschneidet, wird auch die Bilddarstellung für das Bild geändert. Jedem Benutzer der Bilddarstellung wird das zugeschnittene Bild angezeigt.
  
    
    

### So schneiden Sie eine Bilddarstellung auf einer Seite zu


1. Vergewissern Sie sich, dass das Benutzerkonto, mit dem dieses Verfahren durchgeführt wird, über Schreibberechtigungen für die Objektbibliothek verfügt, in der sich das Bild befindet.
    
  
2. Wechseln Sie in einem Browser zu der SharePoint-Website, die das Bild enthält.
    
  
3. Klicken Sie auf der Registerkarte **Seite** auf **Bearbeiten**.
    
  
4. Wählen Sie das Bild aus, das Sie zuschneiden möchten.
    
  
5. Klicken Sie auf der Registerkarte **Bild** des Menübands in der Gruppe **Auswählen** auf **Formatvariante auswählen**, und wählen Sie dann **Bearbeiten von Formatvarianten**.
    
    Die Seite **Bearbeiten von Formatvarianten** zeigt ein Vorschaubild für jede Bilddarstellung an, die in der Websitesammlung definiert ist.
    
    > **HINWEIS**
      > Der Befehl **Formatvariante auswählen** ist nur für Bilder verfügbar, die in derselben Websitesammlung gespeichert sind wie die aktuell bearbeitete Seite.
6. Suchen Sie nach der Bilddarstellung, die Sie ändern möchten, und klicken Sie dann auf **Zu ändernde Formatierung**.
    
  
7. Verwenden Sie im Fenster **Darstellung zuschneiden** das Bildtool, um den Teil des Bilds auszuwählen, der in der Bilddarstellung verwendet werden soll.
    
  
8. Wählen Sie **Speichern**.
    
  

## Löschen einer Bilddarstellung
<a name="Delete"> </a>

Wenn eine Bilddarstellung gelöscht wird, wird sie nicht mehr für Bilder generiert. Wenn eine Website die gelöschte Bilddarstellung anfordert, wird das ursprüngliche Bild zurückgegeben.
  
    
    

### So löschen Sie eine Bilddarstellung


1. Stellen Sie sicher, dass das Benutzerkonto, das dieses Verfahren durchführt, mindestens über Entwurfsberechtigungen für die Website der obersten Ebene der Websitesammlung verfügt.
    
  
2. Wechseln Sie in einem Browser zur Website der obersten Ebene der Veröffentlichungswebsitesammlung.
    
  
3. Klicken Sie auf das Symbol **Einstellungen**. Klicken Sie auf der Seite **Websiteeinstellungen** im Abschnitt **Aussehen und Verhalten** auf **Bilddarstellungen**.
    
    > **HINWEIS**
      > Die Seite **Bilddarstellungen** kann auch über die Standardhomepage der Veröffentlichungswebsite geöffnet werden. Klicken Sie im Abschnitt **Ich bin der visuelle Designer** auf **Bilddarstellung konfigurieren**. 
4. Suchen Sie auf der Seite **Bilddarstellungen** nach der Bilddarstellung, die Sie löschen möchten, und klicken Sie dann auf **Löschen**.
    
  

## Weitere Informationsquellen
<a name="Additional"> </a>


-  [Entwickeln des Website-Designs in SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Design Manager - Branding- und Designfunktionen](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  
-  [Erstellen von Websites für SharePoint](build-sites-for-sharepoint.md)
    
  

