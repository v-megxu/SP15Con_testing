---
title: Erweitern Sie das festem Format Exportfeature in Word Automation Services
ms.prod: SHAREPOINT
ms.assetid: d8375505-432e-438e-971b-221a1d9bb601
---


# Erweitern Sie das festem Format Exportfeature in Word Automation Services
Erweitern Sie Word Automation Services in Microsoft Office 2013 ersetzen Sie die Bibliothek, die von der Funktion zum Exportieren in feste Formate verwendet.
## Einführung in die Word-Datei Konvertierung Service mit festem Format export feature

In diesem Artikel wird beschrieben, wie so erweitern Sie das Feature exportieren in feste Formate von Word Automation Services zu verschiedenen exportieren in feste Formate-DLLs verwenden, sodass Drittanbieter-Entwickler von Microsoft bereitgestellte ersetzen können. Dieser Mechanismus ist erforderlich und des Office-Clients mit festem Format Erweiterbarkeit COM-Schnittstelle erweitert. Weitere Informationen finden Sie unter  [Extending the Office 2007 Fixed-Format Export Feature](http://msdn.microsoft.com/en-us/library/aa338206.aspx).
  
    
    

## Ermittlung

Word Automation Services können Drittanbieter-Entwickler ersetzen Sie einen oder beide der Ausgaben mit festem Format unterstützt:
  
    
    

- PDF
    
  
- XPS
    
  
Um jedes Format zu ersetzen, muss die DLL im gleichen Verzeichnis befindet wie der Hauptbibliothek (Sword.dll) für Word Automation Services gefunden werden (Installationspfad: << Install Root >> \\WebServices\\ConversionService\\Bin\\Converter\\), und müssen den bestimmten Dateinamen in Tabelle 1 angegeben haben.
  
    
    

**In Tabelle 1. Dateinamen mit festem Format exportieren DLLs**


|**Format**|**Dateiname**|
|:-----|:-----|
|PDF <br/> |Renderpdf.dll <br/> |
|XPS <br/> |Renderxps.dll <br/> |
   

## Initialisierung

Eine Methode mit der folgenden Signatur muss die DLL-Datei exportiert werden.
  
    
    

```

HRESULT HrGetDocExporter (
IMsoDocExporter **ppimde,
IMsoServerFileManagerSite *psfms,
PFNKeepAlive pfnKeepAlive
)
```

Die Funktion erfordert die DLL zwei Schnittstellen und einer Methodenzeiger, die im folgenden Abschnitt beschrieben bereitgestellt.
  
    
    
Wenn die Funktion Fehler zurückgibt wird der Dienst nicht auf die Microsoft bereitgestellten Exporter (engl.) zurückgreifen. Stattdessen meldet der Dienst die Konvertierung als fehlgeschlagen ist.
  
    
    

## IMsoDocExporter

Die **IMsoDocExporter** -Schnittstelle ist identisch mit der vorhandenen-Schnittstelle auf MSDN dokumentiert. Weitere Informationen finden Sie unter [Extending the Office 2007 Fixed-Format Export Feature](http://msdn.microsoft.com/en-us/library/aa338206.aspx). Wenn die frühere Methode Erfolg zurückgegeben wird, werden diese Schnittstelle die Konvertierung durchgeführt.
  
    
    
Über die Anforderungen in der oben genannten Artikel beschrieben wird müssen Entwickler von DLLs exportieren in feste Formate Beachten Sie, dass der Dienst den bereitgestellten **IMsoDocExporter** in einem anderen Thread von der Anrufen kann, auf dem der Dienst **HrGetDocExporter**bezeichnet. Die DLL muss dies ohne den Anruf wieder an der Thread, **HrGetDocExporter**, aufgerufen, da der Dienst wird ein Nachrichtensystem nicht ausgeführt, und der gemarshallte Anruf nie erhalten über (was eine hängen und weitere Fehler) gemarshallt behandeln können.
  
    
    

## IMsoServerFileManagerSite

Die IMsoServerFileManagerSite-Schnittstelle wird wie folgt definiert.
  
    
    

```

#undef  INTERFACE
#define INTERFACE  IMsoServerFileManagerSite
DECLARE_INTERFACE(IMsoServerFileManagerSite)
{
STDMETHOD_(BOOL, FGetHandle) (const WCHAR *pwzFileName, HANDLE *phFile, BOOL fRead, BOOL fWrite) PURE;
STDMETHOD_(BOOL, FCloseHandle) (HANDLE hFile) PURE;
};
```

Diese Schnittstelle stellt die folgenden Methoden.
  
    
    

**In Tabelle 2. Methoden verfügbar gemacht werden, die von der IMsoServerFileManagerSite-Schnittstelle**

|||
|:-----|:-----|
|Methode <br/> |Beschreibung <br/> |
|**FGetHandle** <br/> |Ruft ein Dateihandle ab. <br/> |
|**FCloseHandle** <br/> |Gibt ein Dateihandle frei. <br/> |
   
Diese Schnittstelle erbt nicht von **IUnknown**. Die DLL-Datei exportieren in feste Formate darf entsprechend, einen Verweis auf dieses für die Lebensdauer bleiben.
  
    
    

### FGetHandle

Das mit festem Format exportieren DLL-Aufrufe dieser Funktion zum Abrufen des Dateihandles zum Schreiben in. Es muss nicht versuchen Sie zum Öffnen von Dateien über einen anderen Mechanismus, da der Dienst in einer stark eingeschränkten Umgebung ohne Zugriff auf die meisten Stellen im Dateisystem ausgeführt wird.
  
    
    

```

BOOL FGetHandle (
const WCHAR *pwzFile,
HANDLE *phFile,
BOOL fRead,
BOOL fWrite
)
```


**Tabelle 3. FGetHandle-Parameter**

|||
|:-----|:-----|
|Parameter <br/> |Beschreibung <br/> |
|**pwzFile** <br/> |Gibt den Namen der Datei, das mit festem Format exportieren DLL öffnen möchte. Dies muss keinen vollständigen Dateipfad - müssen sie nur einen Dateinamen ein (beispielsweise Output.pdf) angeben. <br/> |
|**phFile** <br/> |Gibt das Handle für die angegebene Datei an, ob die Datei erfolgreich geöffnet wird. Das Exportieren in feste Formate DLL können Sie dieses HANDLE in normalen Dateivorgänge, bis es geschlossen wird durch Aufrufen der **FCloseHandle** -Methode. <br/> |
|**fRead** <br/> |Gibt an, ob die Datei mit Lesezugriff geöffnet werden. <br/> |
|**fWrite** <br/> |Gibt an, ob die Datei mit Schreibzugriff geöffnet werden. Diese Funktion gibt true, um Erfolg anzuzeigen und FALSE, um Fehler anzuzeigen. <br/> |
   

### FCloseHandle

Das Exportieren in feste Formate DLL ruft diese Funktion um, die durch Aufrufen der Methode **FGetHandle** dateikennungen zu schließen.
  
    
    

```

BOOL FCloseHandle (
HANDLE phFile,
)
```

Der  *PhFile*  -Parameter gibt das Handle für die Datei geschlossen wird. Wenn der durch diese Methode zurückgegebene Wert 0 ist, einem fehlgeschlagenen Vorgang. Alle anderen Werte geben bei Erfolg.
  
    
    

## PFNKeepAlive

Wenn die DLL-Datei exportieren in feste Formate aktiv ist, müssen sie die Funktion **KeepAlive** in regelmäßigen Abständen (vom Administrator konfigurierbar) aufrufen, um zu verhindern, dass den Dienst aus, unter der Voraussetzung, dass die DLL-Datei exportieren in feste Formate reagiert und Beenden des Prozesses.
  
    
    
 `typedef void (*PFNKeepAlive)(void)`
  
    
    

## Zusätzliche Ressourcen
<a name="bk_addresources"> </a>

Weitere Informationen finden Sie in den folgenden Ressourcen:
  
    
    

-  [Erweitern Sie das Office 2007-Format Export Feature](http://msdn.microsoft.com/en-us/library/office/aa338206%28v=office.12%29.aspx)
    
  

