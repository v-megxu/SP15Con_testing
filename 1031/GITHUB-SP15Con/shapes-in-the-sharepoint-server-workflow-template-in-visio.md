---
title: Shapes in der SharePoint Server-Workflowvorlage in Visio
ms.prod: SHAREPOINT
ms.assetid: f35bdf5d-c102-4e2d-8a23-1d2df17155b9
---



# Shapes in der SharePoint Server-Workflowvorlage in Visio
In diesem Artikel erfahren Sie mehr über die Shapes in der SharePoint 2013-Workflowvorlage in Visio 2013.
## Einführung
<a name="VSSPD_Shapes_Intro"> </a>

In diesem Artikel sind die Shapes aufgelistet, die in der SharePoint 2013-Workflowvorlage in Visio 2013 und im Visual Designer in SharePoint Designer 2013 enthalten sind. Wenn die Vorlage geöffnet wird, öffnet auch die Schablonen für SharePoint 2013-Workflowaktionen, SharePoint 2013-Workflowbedingungen und SharePoint 2013-Workflow-Abschlusszeichen. Viele der in den Schablonen aufgeführten Shapes entsprechen bestimmten Aktionen, Bedingungen oder anderen logischen Konstrukten im Declarative Designer zum Erstellen von Workflows in SharePoint Designer 2013.
  
    
    

> **WICHTIG**
> Bei den folgenden Angaben handelt es sich um eine Referenz für Workflowaktionen, die in SharePoint Designer 2013 unterstützt werden. Die meisten dieser Aktionen sind auch in SharePoint Designer 2010 verfügbar, wobei eine der Aktionen (Auf Ereignis in Listenelement warten) in der aktuellen Version überarbeitet und erweitert wurde. In der aktuellen Version wurden 12 neue Aktionen eingeführt, und 25 Aktionen wurden entfernt. (Eine Liste der Aktionen, Bedingungen und Blöcke, die entfernt wurden, finden Sie unter  [Verwendung der Interop-Workflow-Brücke verfügbar Workflowaktionen](workflow-actions-available-using-the-workflow-interop-bridge.md).) 
  
    
    


## Aktions-Shapes
<a name="VSSDP_Actions"> </a>

Die folgende Tabelle enthält eine Liste aller Shapes, die in der SharePoint 2013-Aktionsschablone in der SharePoint 2013-Workflowvorlage in Visio 2013 enthalten sind.
  
    
    

> **HINWEIS**
> Jedes in der folgenden Tabelle aufgelistete Shapes verfügt über die angegebenen Eigenschaften und eine **Properties**-Eigenschaft. 
  
    
    



|**Shape in Visio 2013 und SharePoint Designer 2013 Visual Designer**|**Aktion im SharePoint Designer 2013 Declarative Designer**|**Eigenschaften im SharePoint Designer 2013 Visual Designer**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|Kommentar hinzufügen  <br/> |**Kommentar hinzufügen** <br/> |**Kommentar** <br/> |Ermöglicht Ihnen, im Workflow-Designer zu Referenzzwecken informative Kommentare zu hinterlassen. Dies ist besonders hilfreich, wenn andere Benutzer an diesem Workflow mitarbeiten.  <br/> |
|Zeit zum Datum hinzufügen  <br/> |**Zeit zum Datum hinzufügen** <br/> |**Monate** <br/> **Tage** <br/> **Stunden** <br/> **Minuten** <br/> **Datum** <br/> **Ausgabe** <br/> |Fügt einem Datum eine bestimmte Uhrzeit in Minuten, Stunden, Tagen oder Monaten hinzu und speichert den Ausgabewert als Variable. Das Datum kann ein aktuelles Datum, ein bestimmtes Datum oder ein Nachschlagewert sein. Der Wert "Aktuelles Datum" gibt Mitternacht (UTC) zurück.  <br/> |
|Aufgabe zuweisen  <br/> |**Aufgabe zuweisen** <br/> |**Aufgabeneinstellungen** <br/> **Ergebnis des Vorgangs** <br/> **Aufgabenelement-ID** <br/> |Weist einem Benutzer eine Workflowaufgabe zu und erstellt ein Fälligkeitsdatum für den Abschluss der Aufgabe.  <br/> |
|HTTP-Webdienst aufrufen  <br/> |**HTTP-Webdienst aufrufen** <br/> |**HTTP-Anforderung** <br/> **Parameter** <br/> **Antwortinhaltsvariable** <br/> **Antwortkopfzeilenvariable** <br/> **Antwortcodevariable** <br/> |Fungiert als Methodenaufruf eines HTTP-Webdiensts.  <br/> > **HINWEIS**> Der aktuelle Build unterstützt nur SharePoint-Aufrufe **anonymer** HTTP-Dienste und diese nur mit **string**-Parametern und -Rückgabetypen. Außerdem werden keine zusammengesetzten XML-Elemente unterstützt. Beachten Sie auch, dass zurzeit nur die klassische Form von ASMX unterstützt wird. Der WCG-Dienst wird nicht unterstützt.           |
|Element einchecken  <br/> |**Element einchecken** <br/> |**Element** <br/> **Kommentar** <br/> |Checkt ein ausgechecktes Element ein. Sie können nur Elemente aus einer Dokumentbibliothek einchecken.  <br/> > **VORSICHT**> Der Workflow stürzt ab, wenn Sie versuchen, ein nicht ausgechecktes Element einzuchecken.           |
|Element auschecken  <br/> |**Element auschecken** <br/> |**Element** <br/> |Checkt ein Element aus. Der Workflow prüft, ob das Element eingecheckt ist, bevor er ein Dokument auscheckt. Sie können nur Elemente aus einer Bibliothek in Ihrer Website auschecken.  <br/> > **VORSICHT**> Der Workflow stürzt ab, wenn Sie versuchen, ein nicht eingechecktes Element auszuchecken.           |
|Dokument kopieren  <br/> |**Dokument kopieren** <br/> |**Dokument** <br/> **Bibliothek** <br/> |Kopiert ein Dokument aus der aktuellen Liste in eine andere Dokumentbibliotheksliste.  <br/> |
|Elemente im Wörterbuch zählen  <br/> |**Elemente im Wörterbuch zählen** <br/> |**Wörterbuch** <br/> **Ausgabevariable** <br/> |Zählt die Anzahl der Elemente in einer Wörterbuchvariablen.  <br/> |
|Projekt aus dem aktuellen Element erstellen  <br/> |**Projekt aus dem aktuellen Element erstellen** <br/> |**Enterprise-Projekttyp** <br/> |Erstellt auf Basis des aktuellen Elements auf der PWA-Website der SharePoint-Farm ein neues Projekt.  <br/> |
|Listenelement erstellen  <br/> |**Listenelement erstellen** <br/> |**Element** <br/> **Ausgabevariable** <br/> |Erstellt in der von Ihnen angegebenen Liste ein neues Listenelement. Sie können die Felder und Werte im neuen Element angeben. Sie können diese Aktion verwenden, wenn Sie ein neues Element mit bestimmten Informationen erstellen möchten.  <br/> |
|Element löschen  <br/> |**Element löschen** <br/> |**Element** <br/> |Löscht ein Element.  <br/> > **HINWEIS**> Diese Aktion wird auf dem Computer beendet, auf dem das Workflow-Manager-Workflowmodul ausgeführt wird. Sie gibt eine **System.InvalidOperationException**-Ausnahme aus. Es gibt keine Umgehungslösung.           |
|Auschecken verwerfen  <br/> |**Auschecken des Elements verwerfen** <br/> |**Element** <br/> |Verwirft die Änderungen und checkt das Element wieder ein, wenn ein Element ausgecheckt wurde und Änderungen daran vorgenommen wurden.  <br/> > **VORSICHT**> Der Workflow stürzt ab, wenn Sie versuchen, ein nicht ausgechecktes Element einzuchecken.           |
|Berechnung ausführen  <br/> |**Berechnung ausführen** <br/> |**LinkerOperand** <br/> **Operator** <br/> **RechterOperand** <br/> **Bis** <br/> |Führt eine arithmetische Berechnung durch und speichert den Ausgabewert in einer Variablen.  <br/> > **HINWEIS**> Bei SharePoint 2013 unterstützt diese Aktion nur den numerischen Typ **Double**. Ganzzahlen werden nicht unterstützt. Die Verwendung des Operators "+" (Verkettung) bei Zeichenfolgen wird nicht unterstützt.           |
|Teilzeichenfolge ab Ende der Zeichenfolge extrahieren  <br/> |**Teilzeichenfolge ab dem Ende der Zeichenfolge extrahieren** <br/> |**Anzahl der Zeichen** <br/> **Zeichenfolge** <br/> **Ausgabe** <br/> |Kopiert eine bestimmte Anzahl von Zeichen, beginnend am Ende einer Zeichenfolge, und speichert die Ausgabe in einer Variablen  <br/> |
|Teilzeichenfolge ab Index der Zeichenfolge extrahieren  <br/> |**Teilzeichenfolge ab Index der Zeichenfolge extrahieren** <br/> |**Zeichenfolge** <br/> **Index** <br/> **Ausgabe** <br/> |Kopiert eine Teilzeichenfolge, beginnend bei einem angegebenen Index in der Zeichenfolge, und speichert den Wert in einer Variablen.  <br/> > **HINWEIS**> Beachten Sie, dass Werte in SharePoint Designer 2010 mit 1 beginnend indiziert wurden, auch wenn der Indexwert im vorhandenen Build (Technical Preview) von SharePoint Designer nullbasiert ist.           |
|Teilzeichenfolge ab Anfang der Zeichenfolge extrahieren  <br/> |**Teilzeichenfolge ab Anfang der Zeichenfolge extrahieren** <br/> |**Anzahl der Zeichen** <br/> **Zeichenfolge** <br/> **Ausgabe** <br/> |Kopiert eine bestimmte Anzahl von Zeichen, beginnend am Anfang einer Zeichenfolge, und speichert die Ausgabe in einer Variablen  <br/> |
|Teilzeichenfolge der Zeichenfolge anhand des Index mit bestimmter Länge extrahieren  <br/> |**Teilzeichenfolge der Zeichenfolge anhand des Index mit bestimmter Länge extrahieren** <br/> |**Zeichenfolge** <br/> **Index** <br/> **Anzahl der Zeichen** <br/> **Ausgabe** <br/> |Kopiert eine aus einer bestimmten Anzahl von Zeichen bestehende Teilzeichenfolge heraus, beginnend bei einem angegebenen Index in der Zeichenfolge, und speichert den Wert in einer Variablen.  <br/> > **HINWEIS**> Beachten Sie, dass Werte in SharePoint Designer 2010 mit 1 beginnend indiziert wurden, auch wenn der Indexwert im vorhandenen Build (Technical Preview) von SharePoint Designer nullbasiert ist.           |
|Intervall zwischen Datumsangaben suchen  <br/> |**Intervall zwischen Datumsangaben suchen** <br/> |**Einheiten** <br/> **Startdatum** <br/> **Enddatum** <br/> **Ausgabe** <br/> |Berechnet das Zeitintervall zwischen zwei Datumsangaben in Minuten, Stunden oder Tagen und speichert die Ausgabe in einer Variablen.  <br/> |
|Teilzeichenfolge in Zeichenfolge suchen  <br/> |**Teilzeichenfolge in Zeichenfolge suchen** <br/> |**Teilzeichenfolge** <br/> **Zeichenfolge** <br/> **Ausgabe** <br/> |Sucht eine bestimmte Teilzeichenfolge in einer Zeichenfolge und gibt den Index der Startposition der Teilzeichenfolge zurück.  <br/> |
|Element aus Wörterbuch abrufen  <br/> |**Element aus Wörterbuch abrufen** <br/> |**Elementname des Pfads** <br/> **Wörterbuch** <br/> **Ausgabevariable** <br/> |Gibt ein bestimmtes Element aus einer Wörterbuchvariable zurück.  <br/> |
|In Verlaufsliste protokollieren  <br/> |**In Verlaufsliste protokollieren** <br/> |**Nachricht** <br/> |Schreibt eine Nachricht aus einer Liste vordefinierter Nachrichtenelemente in die Workflowverlaufsliste.  <br/> |
|Für Dauer anhalten  <br/> |**Für Dauer anhalten** <br/> |**Tage** <br/> **Stunden** <br/> **Minuten** <br/> |Hält die Ausführung eines Workflows für ein in Tagen, Stunden und Minuten angegebenes Zeitintervall an.  <br/> |
|Bis Datum anhalten  <br/> |**Bis Datum anhalten** <br/> |**Datum** <br/> |Hält die Ausführung eines Workflows bis zu einem angegebenen Datum-/Uhrzeitwert an.  <br/> |
|Teilzeichenfolge in Zeichenfolge ersetzen  <br/> |**Teilzeichenfolge in Zeichenfolge ersetzen** <br/> |**Suchzeichenfolge** <br/> **Ersetzungszeichenfolge** <br/> **Zeichenfolge** <br/> **Ausgabe** <br/> |Ersetzt eine bestimmte Teilzeichenfolge durch eine andere Teilzeichenfolge,  <br/> |
|E-Mail senden  <br/> |**E-Mail senden** <br/> |**E-Mail** <br/> |Sendet bei Auftreten eines bestimmten Workflowereignisses automatisch eine E-Mail, die eine vordefinierte Nachricht an einen Benutzer oder eine Gruppe enthält.  <br/> > **WICHTIG**> Wenn die Website nicht der Liste vertrauenswürdiger Websites hinzugefügt wurde, werden E-Mails an den Junk-E-Mail-Ordner von Outlook weitergeleitet.           |
|Feld in aktuellem Element festlegen  <br/> |**Feld in aktuellem Element festlegen** <br/> |**Feld** <br/> **Wert** <br/> |Legt ein Feld im aktuellen Element auf einen Wert fest.  <br/> |
|Den Zeitbereich des Felds "Datum/Uhrzeit" festlegen  <br/> |**Den Zeitbereich des Felds "Datum/Uhrzeit" festlegen** <br/> |**Stunden** <br/> **Minuten** <br/> **Datum** <br/> **Ausgabe** <br/> |Erstellt einen Zeitstempel und speichert den Ausgabewert in einer Variablen. Sie können die Uhrzeit in Stunden und Minuten festlegen und ein aktuelles Datum, ein bestimmtes Datum oder einen Nachschlagewert festlegen.  <br/> |
|Workflowstatus festlegen  <br/> |**Workflowstatus festlegen** <br/> |**Status** <br/> |Legt den Status des Workflows fest.  <br/> |
|Workflowvariable festlegen  <br/> |**Workflowvariable festlegen** <br/> |**Variable** <br/> **Wert** <br/> |Legt eine Workflowvariable auf einen Wert fest. Sie können diese Aktion auch verwenden, wenn der Workflow einer Variablen Daten zuweisen soll.  <br/> |
|Listenworkflow starten  <br/> |**Listenworkflow starten** <br/> |**Zuordnungsname** <br/> **Eingaben** <br/> **Element** <br/> |Startet einen SharePoint 2010-Listenworkflow.  <br/> > **HINWEIS**>  Der Workflow zum Starten einer Liste weist die folgenden Probleme auf:>  Das Feld für Zuweisungstypen kann nicht als Parameter verwendet werden, wenn der 2010-Workflow eine TaskProcess-Aktion enthält.>  Wenn an den gleichen 2010-Workflow mehrere Aufrufe gerichtet werden, führt dies zu mehreren Datenquellen in der 2013-Workflownachschlagefunktion. Diese Datenquellen sind alle gleich.>  Variablennamen dürfen in 2013 keine Sonderzeichen wie "?" und "#" enthalten. Wenn ein 2010-Workflow Sonderzeichen enthält, werden diese im 2013-Workflow in Hexadezimalcode umgewandelt.          |
|Website-Workflow starten  <br/> |**Website-Workflow starten** <br/> |**Zuordnungsname** <br/> **Parameter** <br/> |Startet einen SharePoint 2010-Website-Workflow.  <br/> > **HINWEIS**>  Der Workflow zum Starten einer Liste weist die folgenden Probleme auf:>  Das Feld für Zuweisungstypen kann nicht als Parameter verwendet werden, wenn der 2010-Workflow eine TaskProcess-Aktion enthält.>  Wenn an den gleichen 2010-Workflow mehrere Aufrufe gerichtet werden, führt dies zu mehreren Datenquellen in der 2013-Workflownachschlagefunktion. Diese Datenquellen sind alle gleich.>  Variablennamen dürfen in 2013 keine Sonderzeichen wie "?" und "#" enthalten. Wenn ein 2010-Workflow Sonderzeichen enthält, werden diese im 2013-Workflow in Hexadezimalcode umgewandelt.          |
|Aufgabenprozess starten  <br/> |**Aufgabenprozess starten** <br/> |**Prozesseinstellungen** <br/> **Prozessergebnis** <br/> |Erstellt Aufgaben für mehrere Benutzer und lässt zu, dass die Aufgaben einen benutzerdefinierten Prozess durchlaufen.  <br/> |
|Dokument übersetzen  <br/> |**Dokument übersetzen** <br/> |**Dokument** <br/> **Sprache** <br/> **Dokumentbibliothek** <br/> |Übersetzt ein Dokument in eine bestimmte Sprache.  <br/> > **HINWEIS**> Eine vorkonfigurierte maschinelle Übersetzungsdienstanwendung ist erforderlich.           |
|Zeichenfolge kürzen  <br/> |**Zeichenfolge kürzen** <br/> |**Zeichenfolge** <br/> **Ausgabe** <br/> |Entfernt Leerzeichen am Beginn und Ende einer Zeichenfolge,  <br/> |
|Listenelement aktualisieren  <br/> |**Listenelement aktualisieren** <br/> |**Element** <br/> |Aktualisiert ein Listenelement. Sie können die Felder und die neuen Werte in diesen Feldern angeben.  <br/> |
|Auf Ereignis in Listenelement warten  <br/> |**Auf Ereignis in Listenelement warten** <br/> | Document.SelectionChanged **-Ereignis** <br/> **Verknüpftes Element** <br/> |[Verbesserte Version der Office 2010-Aktion.] Hält die aktuelle Instanz des Workflows an und wartet auf ein angegebenes Listenelementereignis. Diese Aktion überwacht zwei Ereignisse: **ItemUpdated** und **ItemAdded**.  <br/> |
|Auf Feldänderung warten  <br/> |**Auf Feldänderung warten** <br/> |**Feld** <br/> **Wert** <br/> |Wartet, bis ein Feld im aktuellen Element einem bestimmten Wert entspricht.  <br/> |
|Projektfeld festlegen  <br/> |**Projektfeld festlegen** <br/> |**Feld** <br/> **Wert** <br/> |Legt für ein bestimmtes Feld auf Project Server einen Wert fest.  <br/> > **HINWEIS**> Für diese Aktion muss das Projekt zuerst eingecheckt werden. Wenn das Projekt nicht eingecheckt ist, wird der Workflow beendet, und Benutzer können das Projekt in Project Web App nicht öffnen.           |
|Status der Projektstufe festlegen  <br/> |**Status der Projektstufe festlegen** <br/> |**Stufenstatus** <br/> **Stufeninformationen** <br/> |Legt den Status der Projektstufe fest.  <br/> > **HINWEIS**> Wenn das aktuelle Projekt ausgecheckt ist, tritt eine Ausnahme auf.           |
|Statusfeld in Ideenliste festlegen  <br/> |**Statusfeld in Ideenliste festlegen** <br/> |**Status** <br/> |Aktualisiert den Status für das ursprüngliche Listenelement, das mit dem aktuellen Projekt verknüpft ist.  <br/> |
|Auf Projektereignis warten  <br/> |**Auf Projektereignis warten** <br/> |**Ereignisname** <br/> |Wartet auf ein bestimmtes Projektereignis.  <br/> |
   

## Bedingungs-Shapes
<a name="VSSPD_Conditions"> </a>

Die folgende Tabelle enthält eine Liste aller Shapes, die in der SharePoint 2013-Bedingungsschablone in der SharePoint 2013-Workflowvorlage enthalten sind.
  
    
    


|**Shape in Visio 2013 und SharePoint Designer 2013 Visual Designer**|**Aktion im SharePoint Designer 2013 Declarative Designer**|**Eigenschaften im SharePoint Designer 2013 Visual Designer**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|Wenn ein beliebiger Wert gleich dem Wert ist  <br/> |**Wenn ein beliebiger Wert gleich dem Wert ist** <br/> |**Wert** <br/> **Operand** <br/> **Wert** <br/> |Vergleicht zwei Werte. Sie können angeben, ob die Werte gleich oder nicht gleich sein sollen.  <br/> |
|Person ist ein gültiger SharePoint-Benutzer  <br/> |**Person ist ein gültiger SharePoint-Benutzer** <br/> |**Benutzer** <br/> |Überprüft, ob ein bestimmter Benutzer ein registrierter Benutzer oder ein Mitglied einer Gruppe auf der SharePoint-Website ist.  <br/> |
|Projektstufe überspringen  <br/> |**Projektstufe überspringen** <br/> |NV  <br/> |Diese Bedingung prüft, ob das Feature zum Überspringen der Stufe auf dem Server für die aktuelle Workflowinstanz aktiviert wurde.  <br/> |
   

## Abschlusszeichen-Shapes
<a name="VSSPD_Terminators"> </a>

Die folgende Tabelle enthält eine Liste aller Shapes, die in der SharePoint 2013-Abschlusszeichen-Schablone in der SharePoint 2013-Workflowvorlage enthalten sind.
  
    
    


|**Shape in Visio 2013 und SharePoint Designer 2013 Visual Designer**|**Aktion im SharePoint Designer 2013 Declarative Designer**|**Eigenschaften im SharePoint Designer 2013 Visual Designer**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|Anfang  <br/> |NV  <br/> |NV  <br/> |Startet den Workflow. Jedes SharePoint 2013-Workflowdiagramm darf nur ein Anfangs-Shape enthalten.  <br/> |
|Stufe  <br/> |**Stufe** <br/> |NV  <br/> |Enthält eine beliebige Anzahl von Shapes und kann ggf. Verzweigungen enthalten. Alle Aktionen im Workflow müssen in einer Stufe enthalten sein. Stufen-Shapes werden mithilfe von Container-Shapes visualisiert. Ein Stufen-Shape erfordert, dass ein Eingabe-Shape und eine Ausgangs-Shape an den Kanten des Containers hinzugefügt werden, um die Pfade innerhalb und außerhalb der Stufe zu definieren.  <br/> Weitere Informationen finden Sie im Abschnitt "Phasen, Schleifen und Schritte" im Artikel  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Schritt  <br/> |**Schritt** <br/> |NV  <br/> |Stellt eine gruppierte Reihe aufeinanderfolgender Aktionen dar. Schritte müssen in einer Stufe enthalten sein. Ein Schritt-Shape muss auch über ein Eingabe- und ein Ausgangs-Shape verfügen. Diese werden hinzugefügt, wenn das Shape im Zeichenbereich abgelegt wird.  <br/> Weitere Informationen finden Sie im Abschnitt "Phasen, Schleifen und Schritte" im Artikel  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Einfache Stufe  <br/> |**Stufe** <br/> |NV  <br/> |Fügt neue Stufen auf der oberen Ebene des Workflows in der Phasenansicht in Visio 2013 hinzu.  <br/> |
|Schleife n-mal  <br/> |**Schleife n-mal** <br/> |**Schleifenanzahl** <br/> |Definiert eine Reihe verbundener Shapes, die als Schleife ausgeführt werden, wobei so oft vom letzten Shape in der Reihe wieder zum ersten gewechselt wird, bis die Schleife eine festgelegte Anzahl von Malen ausgeführt wurde. Ebenso wie Stufen werden Schleifen durch ein Container-Shape dargestellt, das ein Eingabe- und ein Ausgangs-Shape enthält.  <br/> Weitere Informationen finden Sie im Abschnitt "Phasen, Schleifen und Schritte" im Artikel  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md).  <br/> |
|Schleife mit Bedingung  <br/> |**Schleife mit Bedingung** <br/> |**Schleifenanzahl** <br/> |Die Schleife wird ausgeführt, bis eine bestimmte Bedingungen erfüllt ist.  <br/> |
|Parallele Aktion starten  <br/> |**Paralleler Block** <br/> |NV  <br/> ||
|Parallele Aktion beenden  <br/> |**Paralleler Block** <br/> |NV  <br/> ||
   

## Zusätzliche Ressourcen
<a name="VSSPD_Additional"> </a>


-  [Workflowentwicklung in SharePoint Designer und Visio](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [Kurzübersicht zu Workflowaktionen (SharePoint 2013-Workflowplattform)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Leitfaden für Shapes in SharePoint-Workflowvorlagen](http://office.microsoft.com/de-de/visio-help/sharepoint-workflow-template-shapes-guide-HA101903894.aspx)
    
  
-  [SharePoint Developer Center](http://msdn.microsoft.com/de-de/sharepoint/default.aspx)
    
  
-  [Visio Developer Center](http://msdn.microsoft.com/de-de/office/aa905478)
    
  
