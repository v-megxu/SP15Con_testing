---
title: CMIS (Content Management Interoperability Services) in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: a1def24c-b2db-4bf9-8d2c-02f5628832f8
---


# CMIS (Content Management Interoperability Services) in SharePoint 2013
In diesem Artikel erfahren Sie mehr über die SharePoint 2013-Implementierung der Version 1.0 des CMIS-Standards (OASIS Content Management Interoperability Services)
## Einführung in CMIS in SharePoint 2013
<a name="SP15CMIS_Intro"> </a>

Die SharePoint Server-Konformität mit Version 1.0 des  [CMIS-Standards (OASIS Content Management Interoperability Services)](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=cmis) ermöglicht die Integration von SharePoint Server-Inhaltsrepositorys und anderen ECM-Repositorys (Enterprise Content Management) in einem Unternehmen. CMIS bietet die Möglichkeit, Informationen über Internetprotokolle zwischen Dokumentsystemen, Herausgebern und Repositorys innerhalb des Unternehmens sowie zwischen Unternehmen zu teilen - all dies in einem anbieterneutralen Format. Der CMIS-Standard unterstützt grundlegende Dokumentverwaltungsvorgänge wie Lesen, Erstellen, Aktualisieren, Löschen sowie Ein- und Auschecken. Der Standard unterstützt außerdem das Verwalten von Dokumentversionen und deren Metadaten. CMIS ist auf jeder lokalen SharePoint 2013-Website verfügbar, nachdem das Feature **Content Management Interoperability Services (CMIS) - Hersteller** im Abschnitt **Websitefeatures verwalten** der **Websiteeinstellungen** aktiviert wurde. In SharePoint 2013 ist der SharePoint-CMIS-Produzent verfügbar, aber standardmäßig auf allen lokalen Websites deaktiviert.
  
    
    
CMIS stellt Interoperabilität zwischen den APIs zur Verfügung, die den Standard unterstützen, ist jedoch kein Ersatz für systemeigene APIs. Die von CMIS unterstützten Objekte überschneiden sich mit Objekten, mit denen SharePoint Server-Entwickler üblicherweise interagieren, darunter auch Dokumente und Ordner. Entwickler, die Anwendungen mit CMIS-Unterstützung erstellen, müssen wahrscheinlich weiterhin benutzerdefinierten SharePoint Server-Code erstellen. Mit CMIS können 60 - 70 Prozent der Entwicklungszeit bei Lösungen eingespart werden, die den Standard implementieren - betrachten Sie es als ein weiteres Tool in der Toolbox für die Entwicklung.
  
    
    

## Eine ausführliche Betrachtung der CMIS-Implementierung in SharePoint 2013
<a name="SP15CMIS_DetailedLook"> </a>

Einige Teile der CMIS-Spezifikation sind obligatorisch, viele andere sind jedoch optional. Viele Anbieter, einschließlich Microsoft, implementieren die obligatorischen Anteile des Standards und einige seiner optionalen Komponenten. Abbildung 1 zeigt in der CMIS 1.0-Spezifikation angegebene Funktionen, die in SharePoint 2013 implementiert sind.
  
    
    
Abbildung 1: In SharePoint 2013 implementierte CMIS 1.0-Funktionen
  
    
    

  
    
    
![CMIS-Funktionen in SharePoint 2013](images/SP15_CMISCapabilities.jpg)
  
    
    
Das CMIS-Datenmodell definiert ein Repository, das die übrigen CMIS-Datentypen enthält, einschließlich Objekttypen, Versionsverwaltung, Dokumente und Ordner sowie Abfragefunktionen.
  
    
    

### CMIS-Repositorys und SharePoint-Dokumentbibliotheken

Das CMIS-Repository ist der Container für den Rest des CMIS-Datenmodells. In SharePoint 2013 entspricht die Dokumentbibliothek dem CMIS-Repository (Listen werden im SharePoint 2013-CMIS-Produzent nicht unterstützt). Der Zugriff auf das Repository ist in der Regel der Startpunkt für eine Clientanwendung. Beispiel: Ziehen Sie eine SharePoint Server-Website in Betracht, die mehrere Dokumentbibliotheken enthält, die den Repositorys in CMIS entsprechen. Die CMIS-Spezifikation beschreibt einen erforderlichen Dienst, **getRepositories**, der in SharePoint Server alle gültigen Repositorys (Dokumentbibliotheken) im aktuellen  [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) -Objekt abruft. Ein Entwickler kann eine Verbindung zu den Repositorys herstellen, indem er entweder den **getRepositories**-Dienst oder den **getRepositoryInfo**-Dienst aufruft. Mit **getRepositoryInfo** wird das vom Entwickler angegebene Repository abgerufen.
  
    
    
Das CMIS-Repository enthält die anderen von SharePoint Server unterstützten CMIS-Funktionen, einschließlich der von CMIS festgelegten Dokument- und Ordnerobjekttypen, der CMIS-Versionsverwaltungsfunktionen (die die systemeigenen Versionsverwaltungsfunktionen in SharePoint Server spiegeln) und der CMIS-Abfragefunktion, die eine SQL-ähnliche Syntax verwendet, um bestimmte Daten in CMIS-Repositorys abzufragen.
  
    
    

### CMIS-Dokumente, Ordner und andere Objekttypen

CMIS definiert eine Objekttyp-Funktion, die der Idee der Inhaltstypen in SharePoint Server entspricht (insbesondere der  [SPContentType](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPContentType.aspx) -Klasse). Jeder schreibgeschützte CMIS-Objekttyp besteht aus Attributen und Eigenschaftsdefinitionen. Über Attribute wird festgelegt, ob ein Objekt beispielsweise abgefragt werden kann oder ob seine Version angegeben werden kann. CMIS unterstützt Eigenschaftsdefinitionen für Eigenschaften, die äquivalenten Objekttypen in SharePoint 2013 zugeordnet werden, sofern möglich. Beispielsweise verfügt ein Dokumentobjekt oder ein Ordnerobjekt in CMIS möglicherweise über eine **LastModifiedBy**-Eigenschaft, für die die folgende Syntax gilt:  `cmis:LastModifiedBy`. Eine **Author**-Eigenschaft, die mit einem **Document**-Objekt verknüpft ist, wird als  `cmis:Author` erstellt. Der CMIS-Standard definiert vier Objekttypen, die als Basistypen dienen. In Tabelle 1 sind die CMIS-Objekttypen beschrieben, und es ist angegeben, ob sie in SharePoint 2013 unterstützt werden. Außerdem ist ihre entsprechende Funktion in SharePoint aufgeführt, sofern vorhanden.
  
    
    

  
    
    

**Tabelle 1: CMIS-Objekttypwerte und ihre Entsprechungen in SharePoint 2013**


|**CMIS-Objekttyp**|**Unterstützt in SharePoint Server?**|**Entsprechende Funktion in SharePoint 2013**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|Dokument  <br/> |Ja  <br/> |**Document**-Objekte  <br/> |Der CMIS-Dokumentobjekttyp wird direkt dem **Document**-Objekt in SharePoint Server zugeordnet.  <br/> Dokumente weisen Eigenschaften auf und verfügen über einen angehängten Content Stream, sie können eine Versionsangabe enthalten und unterstützen die grundlegenden Vorgänge Erstellen, Lesen, Aktualisieren und Löschen (CRUD).  <br/> |
|Ordner  <br/> |Ja  <br/> | [SPFolder](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder.aspx) -Objekte <br/> |Der CMIS-Ordnerobjekttyp wird direkt dem **SPFolder**-Objekt in SharePoint Server zugeordnet.  <br/> Ordner können Dokumente und andere Ordner enthalten und über einen einzelnen übergeordneten Ordner verfügen. Ordnern können Eigenschaften hinzugefügt werden, und sie unterstützen die gleichen CRUD-Vorgänge, die vom Dokumentobjekttyp unterstützt werden.  <br/> Für CMIS-Ordner kann keine Versionsangabe festgelegt werden.  <br/> |
|Richtlinie  <br/> |Nein  <br/> |Keine  <br/> |Der CMIS-Richtlinienobjekttyp ist nicht gleichbedeutend mit dem Konzept der Richtlinien in SharePoint oder jeglichen im SharePoint-Objektmodell definierten Richtlinienobjekten.  <br/> |
|Beziehung  <br/> |Nein  <br/> |Keine  <br/> |Nicht unterstützt  <br/> |
   

  
    
    
CMIS stellt keine Methoden zum Erstellen, Ändern oder Löschen von Objekttypen zur Verfügung. Entwickler, die einen SharePoint Server-Dokumentobjekttyp oder -Ordnerobjekttyp erstellen, ändern oder löschen möchten, können hierfür das proprietäre SharePoint Server-Objektmodell verwenden.
  
    
    
Abbildung 2 zeigt Beispielbeziehungen, die zwischen CMIS-Dokument- und -Ordnerobjekttypen bestehen können. In der Abbildung werden Bezeichnungen verwendet, die möglicherweise in einem SharePoint Server-Dokumentverwaltungsszenario zu finden sind. Beispiel: Ein CMIS-Objekttyp namens **cmis:folder** ist einem Objekttyp namens **cmis:documentset** übergeordnet. Der **cmis:documentset**-Objekttyp kann, muss jedoch nicht, Dokumentobjekte enthalten, die in einem  [DocumentSet](https://msdn.microsoft.com/library/Microsoft.Office.DocumentManagement.DocumentSets.DocumentSet.aspx) -Objekt organisiert sind.
  
    
    
Der CMIS-Dokumentobjekttyp unterstützt zudem Beziehungen zwischen übergeordneten und untergeordneten Elementen, wie hier gezeigt. Dabei ist der **cmis:document**-Objekttyp den **cmis:specification**-, **cmis:report**- und **cmis:image**-Dokumentobjekttypen übergeordnet. Es ist möglich, diese Dokumente in SharePoint Server-Dokumentenmappen zu organisieren, CMIS definiert ein solches Konstrukt jedoch nicht. Stattdessen erkennt CMIS einzelne Objekte als Dokumentobjekttyp oder Ordnerobjekttyp oder als eine Teilmenge eines dieser beiden Objekttypen.
  
    
    
Abbildung 2: Beispiele des CMIS-Dokumentobjekttyps und des -Ordnerobjekttyps
  
    
    

  
    
    
![Beispiele für CMIS-Objekttypen in SharePoint 2013](images/SP15_CMISObjectTypeExamples.png)
  
    
    

  
    
    

  
    
    

### CMIS-Abfrage in SharePoint 2013

Die Abfrage ist ein optionaler Bestandteil der CMIS-Spezifikation, die SharePoint Server unterstützt. Bei der CMIS-Abfrage wird eine vereinfachte SQL-ähnliche Syntax verwendet. Jede Abfrage in CMIS ist einem Repository zugeordnet, sodass alle Abfrageergebnisse aus dem einzelnen Repository zurückgegeben werden, dem die Abfrage zugeordnet ist. Bei der Ausführung mehrerer Abfragen in mehreren Repositorys werden Ergebnisse aus einem Repository für jede ausgeführte Abfrage wiedergegeben. Dies führt dazu, dass Ergebnisse aus mehreren Repositorys zurückgegeben werden. Tabelle 2 enthält einige Beispiele für grundlegende CMIS-Abfrageanweisungen.
  
    
    

  
    
    

**Tabelle 2: CMIS-Abfragesyntax - Beispiele**


|**CMIS-Abfrageanweisung**|**Beschreibung**|
|:-----|:-----|
| `SELECT * FROM cmis:document` <br/> |Wählt alle Dokumente im Repository aus.  <br/> |
| `SELECT cmis:name, cmis:author FROM cmis:document WHERE cmis:author='Tina Makovec'` <br/> |Wählt den Namen und den Autor jedes Dokuments im Repository aus, bei dem der Name des Autors Tina Makovec ist.  <br/> |
| `SELECT * FROM cmis:document WHERE CONTAINS('4Q13')` <br/> |Dies ist ein Beispiel für eine Volltextsuche mithilfe von CONTAINS. Diese Abfrage gibt alle Dokumente im Repository zurück, die das Wort 4Q13 enthalten. <br/> |
   

  
    
    
SharePoint Server unterstützt keine Verknüpfungen. Bei der CMIS 1.0-Spezifikation hingegen ist dies der Fall. Nicht-SharePoint-CMIS-Repositorys können Verknüpfungen in ihrer CMIS-Abfrageimplementierung unterstützen. Alle Repositorys, die die CMIS-Abfrage unterstützen, unterstützen die Sortierung, die Auswahl der zurückzugebenden Eigenschaften und Paging.
  
    
    

### CMIS-Versionsverwaltung und SharePoint-Versionsverwaltung

Die CMIS-Versionsverwaltung ist identisch mit der Versionsverwaltung für Dokumente in SharePoint Server. Haupt- und Nebenversionen sowie Ein- und Auscheckvorgänge werden in CMIS nur für Dokumente unterstützt.
  
    
    
Ordner können keine Versionsangabe enthalten.
  
    
    

### CMIS-Änderungsprotokollunterstützung

CMIS beinhaltet ein Änderungsprotokollkonzept. CMIS-Änderungsprotokolle unterstützen grundlegende Erstellungs-, Aktualisierungs- und Löschereignisse, die an eine Objekt-ID und Eigenschaften gebunden sind. Die Eigenschaften werden ausgelöst, wenn ein Erstellungs-, Aktualisierungs- oder Löschereignis eintritt. Das Änderungsprotokoll unterstützt Paging, sodass Entwickler ihr eigenes Änderungsprotokoll dort speichern können, wo sie möchten.
  
    
    

## Authentifizierung und CMIS in SharePoint 2013
<a name="SP15CMIS_Authentication"> </a>

Standardmäßig unterstützt SharePoint Server die Authentifizierung für Anonymous AuthN, Basic AuthN, NTLM AuthN, Digest AuthN, Kerberos-Protokollübergang/Eingeschränkte Delegierung, Windows-Forderungen, Claims MultiAuth, and Forderungen/gemischter Modus.
  
    
    
Inbound OAuth wird nicht unterstützt.
  
    
    

## Der CMIS-Produzent in SharePoint 2013
<a name="SP15CMIS_CMISProducer"> </a>

Der CMIS-Produzent ist standardmäßig in SharePoint Server für lokale Bereitstellungen verfügbar. Der Prozent erstellt CMIS-konforme Endpunkte, mit denen CMIS-konforme Verbraucherwebdienste zusammenarbeiten können. CMIS-Unterstützung das Feature CMIS-Produzent sind für alle lokalen SharePoint Server-Implementierungen verfügbar, bei denen das Feature CMIS-Produzent aktiviert ist. CMIS wird in SharePoint Online nicht unterstützt.
  
    
    

## CMIS-Szenarien und Anwendungsideen
<a name="SP15CMIS_Scenarios"> </a>

Mit den CMIS-Funktionen in SharePoint 2013 können Entwickler Anwendungen erstellen, die CMIS-konforme Daten aus SharePoint Server und anderen CMIS-konformen Anwendungen einschließen. Da es sich bei CMIS um ein anbieterneutrales Format handelt, können Entwickler Code erstellen, der CMIS-konforme Endpunkte erzeugt, die mit CMIS-konformen Endverbraucheranwendungen geteilt werden können, ohne dass Code für die API der systemeigenen Anwendung erstellt werden muss. Beispielsweise kann der standardmäßige CMIS-Produzent von SharePoint 2013 ein CMIS-Repository (zum Beispiel eine SharePoint Server-Dokumentbibliothek) mit der Bildbearbeitungsanwendung eines anderen Anbieters teilen. Ein Benutzer kann eine Bilddatei öffnen, die im CMIS-Repository des Produzenten der Bildbearbeitungsanwendung gespeichert ist, und sie von der Bildbearbeitungsanwendung aus in SharePoint Server auschecken. Nachdem der Benutzer Änderungen durchgeführt und gespeichert hat, kann er von der Bildbearbeitungsanwendung aus die neueste Version in die SharePoint Server-Dokumentbibliothek einchecken. Da die CMIS-Spezifikation die Versionsverwaltung, was Haupt- und Nebenversionen angeht, auf die gleiche Weise definiert wie SharePoint, speichert der Benutzer der Bildbearbeitungsanwendung Änderungen in einer Version im CMIS-Repository mithilfe einer Versionsverwaltungslogik, die mit der Logik in SharePoint Server identisch ist.
  
    
    
Ziehen Sie beim Erstellen einer App Code in Erwägung, mit dem ein Verzeichnis implementiert wird, das alle Parameter initialisiert. Die Parameter werden zur Authentifizierung bei Repositorys verwendet und geben beispielsweise folgende Daten an: eine Bindung, die verwendet wird (zum Beispiel REST, AtomPub, SOAP), die URL des Servers für den Zugriff auf den REST-Endpunkt, den Benutzernamen, das Kennwort und die Klasse des Authentifizierungsanbieters (zum Beispiel Basic AuthN). Nachdem die Parameter eingerichtet wurden, kann der Entwickler über den **getRepositories**-Aufruf eine Verbindung zu jedem Repository herstellen. 
  
    
    
CMIS unterstützt die Entwicklung einer breiten Palette von Anwendungen, die Daten von mehreren CMIS-Produzenten verarbeiten. CMIS wurde zur Unterstützung von Szenarien konzipiert, auf die Unternehmen in der Regel treffen, wenn sie Inhalte über mehrere Inhaltsverwaltungssysteme hinweg in umfassenden Hybridumgebungen verwalten. Dazu zählen: 
  
    
    

- Datenmigration zu und von Inhaltsverwaltungssystemen in einem Unternehmen
    
  
- Grafische Benutzeroberflächen (GUIs) in Apps, die Daten aus mehreren Inhaltsrepositorys lesen
    
  
- Ein SharePoint-Webpart, das CMIS verwendet, um ein Rollup persönlicher Daten aus mehreren älteren Inhaltsverwaltungssystemen in einem Unternehmen auszuführen
    
  
- Eine mobile Anwendung, die von einem beliebigen ECM-System aus auf Dokumente zugreifen kann
    
  
- Eine Bildbearbeitungsanwendung, die Dateien in einem CMIS-Repository mit aktivierten ECM-Funktionen, wie beispielsweise der Möglichkeit, Dateien ein- und auszuschecken, speichert
    
  
- Ein Branchensystem (LOB, Line-of-Business), das Berichtsdaten in ein ECM-Repository exportiert
    
  
- Eine App zur Genehmigung von Verträgen, die Elemente der SharePoint-Benutzeroberfläche zur Verwaltung eines zentralen Genehmigungsprozesses nutzt, während die Möglichkeit bestehen bleibt, den Vertrag in verschiedenen Systemen zu veröffentlichen
    
  

### Beispiel: Contoso Finances-App

Erwägen Sie als App ein SharePoint Server-Webpart, das Daten von mehreren CMIS-Datenanbietern verarbeitet - die Contoso Finances-App. Die Contoso Finances-App sammelt Finanzdaten und ordnet diese in Tabellen an und verteilt diese Daten dann über drei Server: einen IBM-Server, einen Server, auf dem SharePoint Server ausgeführt wird, und einen internen Contoso-Server. Die SharePoint Server-App nutzt ein Webpart, um Daten aus allen drei Datenquellen innerhalb einer beliebigen SharePoint Server-Seite anzuzeigen. Die App benötigt keinen benutzerdefinierten Code, der für eine Implementierung des CMIS-Repository (der SharePoint Server-Dokumentbibliothek) spezifisch ist.
  
    
    

## CMIS und das SharePoint-Objektmodell
<a name="SP15CMIS_ObjectModel"> </a>

Das SharePoint-Objektmodell bietet Entwicklern zahlreiche Optionen für Erweiterungen, die nicht von CMIS unterstützt werden, einschließlich APIs zur Verwaltung von Objekttypen, Verwaltung der Website oder Repositoryspalten, Abfragen, die für SharePoint spezifische Schlüsselwörter und Syntax verwenden, Communitytags und Zugriffssteuerungseinträge (ACE). 
  
    
    
Die SharePoint Server-Implementierung von CMIS verwendet die  [BlockedFileExtensions](https://msdn.microsoft.com/library/Microsoft.SharePoint.Administration.SPWebApplication.BlockedFileExtensions.aspx) -Eigenschaft, um eine Liste der Dateierweiterungen abzurufen, die nicht auf Websites in der Webanwendung hochgeladen oder von diesen heruntergeladen werden können. CMIS respektiert die [von SharePoint standardmäßig blockierten Dateitypen](http://technet.microsoft.com/de-de/library/cc262496.aspx).
  
    
    
Entwickler können CMIS-Clients in jeder Sprache erstellen. Beispielsweise kann ein SharePoint-Entwickler das clientseitige .NET-Objektmodell (CSOM) oder das JavaScript-Objektmodell (JSOM) verwenden, um einen Client zu erstellen. Ein Entwickler kann auch serverseitigen Code verwenden, um eine SharePoint-Anwendung zu entwickeln, die automatisch auf Microsoft Azure gehostet oder auf einem beliebigen Server, einschließlich Internet Information Services (IIS) oder Microsoft Azure von Anbieter gehostet ist.
  
    
    

## Suche und Zusammenarbeit mit Open Source-CMIS-Implementierungen
<a name="SP15CMIS_OpenSource"> </a>

Es gibt viele Open Source-Projekte, die mit der SharePoint 2013-Implementierung des CMIS 1.0-Standards getestet werden können. Beispiele sind das  [Apache Chemistry-Projekt](http://chemistry.apache.org) und das [Open CMIS-Projekt](http://chemistry.apache.org/java/opencmis.mdl), die beide Client- und Server-CMIS-Implementierungen mit Java testen, das Projekt  [DotCMIS](http://chemistry.apache.org/dotnet/dotcmis.mdl) für .NET-Clients, das Projekt [cmislib, eine CMIS-Clientbibliothek für Python](http://code.google.com/p/cmislib/) und das Projekt [phpclient, eine CMIS-Clientbibliothek für PHP](http://chemistry.apache.org/php/phpclient.mdl).
  
    
    
Die  [CMIS Workbench](http://chemistry.apache.org/java/developing/tools/dev-tools-workbench.mdl) ist eine CMIS-Desktopclientanwendung für Entwickler, die die Navigation in CMIS-Repositorys und interaktive Tests von CMIS-Entwicklungsprojekten für Open CMIS unterstützt. Die Workbench ist über Systemeigenschaften konfigurierbar. Wenn sie das Anmeldedialogfeld für Experten verwenden, können Entwickler auch weitere Eigenschaften konfigurieren.
  
    
    

## CMIS 1.1-Features
<a name="SP15CMIS_Features"> </a>

CMIS 1.1 wird in SharePoint 2013 nicht unterstützt. Die neuere Version der CMIS-Spezifikation enthält jedoch einige neue Features, bei denen es sich lohnt, sie kennenzulernen. Dabei sind die Folgenden hervorzuheben:
  
    
    

- **Type mutability**: Eine Funktion zum Erstellen und Ändern von Inhaltstypen
    
  
- **Repository features**: Eine Funktion zum Erweitern des **getRepositoryInfo**-Diensts zum Veröffentlichen einer Liste der Erweiterungen für die unterstützten Standards
    
  
- **Retention and hold**: Dienste, mit denen festgelegt werden kann, das ein Dokument für einen bestimmten Zeitraum oder unbeschränkte Zeit nicht gelöscht wird
    
  
- **Browser binding**: Eine neue optionale Bindung, die speziell zur Unterstützung von Anwendungen konzipiert wurde, die in einem Webbrowser ausgeführt werden. Die Bindung nutzt JSON anstelle von XML und verwendet stets die HTTP GET- und POST-Befehle
    
  
- **Secondary object types**: Benannte Eigenschaftssätze, die dynamisch in CMIS-Projekten hinzugefügt bzw. daraus entfernt werden können.
    
  
- **cmis:item type**: Neuer Datenmodelltyp der obersten Ebene für Repositorys, die Objekttypen über CMIS verfügbar machen müssen, die bezüglich Dokument-, Ordner- oder Richtlinienobjekttypen nicht in die Definition des CMIS-Modells passen
    
  
- **Bulk update properties**: Methode zur Unterstützung von Masseneigenschaftsupdates für eine Reihe von Objekten in einem einzelnen Dienstaufruf
    
  
- **Append to a stream**: Unterstützung beim Anfügen an einen Content Stream. Dieses Feature bietet Clients die Möglichkeit, sehr große Uploads von Dokumentinhalten in viele kleinere Aufrufe zu unterteilen.
    
  

## Zusätzliche Ressourcen
<a name="SP15CMIS_AdditionalResources"> </a>


-  [Hinzufügen von SharePoint 2013-Funktionen](add-sharepoint-2013-capabilities.md)
    
  
-  [Verwalten von gesperrten Dateitypen in SharePoint 2013](http://technet.microsoft.com/de-de/library/cc262496.aspx)
    
  
-  [OASIS Content Management Interoperability Specification (CMIS) Version 1.0](http://docs.oasis-open.org/cmis/CMIS/v1.0/os/cmis-spec-v1.0.mdl)
    
  
-  [OASIS Content Management Interoperability Specification (CMIS) Version 1.1](http://docs.oasis-open.org/cmis/CMIS/v1.1/cs01/CMIS-v1.1-cs01.mdl) (in SharePoint 2013 nicht unterstützt)
    
  

  
    
    

