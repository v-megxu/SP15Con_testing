---
title: Benutzerdefinierte Wörtertrennungen in SharePoint Server 2013
ms.prod: SHAREPOINT
ms.assetid: d18b48d4-987c-4228-9932-30d5b30f86a2
---


# Benutzerdefinierte Wörtertrennungen in SharePoint Server 2013
Informationen Sie zu Wortumbruch in SharePoint Server 2013.
Wortumbruch ist eines der wichtigsten natürlicher Sprache Verarbeitung (NLP) Features, mit denen suchen, und Verbessern der Suchergebnisse (oder Rückruf). Worttrennmodule teilen ein Stream-Objekts von Text in einzelne Wörter oder Token, auf denen Sie zusätzliche Language Verarbeitung basieren können. Worttrennmodule sind sprachspezifische. Zusätzlich zur integrierten Worttrennmodule ermöglicht Suche in SharePoint 2013 die Verwendung von benutzerdefinierten Worttrennmodule, damit Benutzer Wortumbruch Verhalten entsprechend ihren Anforderungen optimieren können. Zur Anpassung von Word wörtertrennung unterstützten Sprachen mit einer Liste finden Sie unter  [Unterstützte Sprachen für Word wörtertrennung Anpassungen in SharePoint Server 2013](#SP15_SupportedLanguages) .
  
    
    

Informationen zum Schreiben von einem Worttrennmodul finden Sie in den folgenden Artikeln
-  [Implementieren von einem Worttrennmodul](http://msdn.microsoft.com/en-us/library/ms693186%28v=vs.85%29.aspx)
    
  
-  [IWordBreaker-Schnittstelle](http://msdn.microsoft.com/en-us/library/ms691079%28v=vs.85%29.aspx)
    
  

## So wechseln Sie zu einem benutzerdefinierten Worttrennmodul in SharePoint Server 2013 wie
<a name="SP15wordbreaker_howto"> </a>


> **VORSICHT**
> Wenn Sie vorhandene Worttrennmodule ersetzen, ändern Sie die Registrierung auf eigenes Risiko. Schwerwiegende Probleme können auftreten, wenn Sie die Registrierung nicht ordnungsgemäß mithilfe des Registrierungs-Editor oder mithilfe einer anderen Methode ändern. Diese Probleme erfordern möglicherweise eine Neuinstallation des Betriebssystems. Microsoft kann nicht stellen Sie sicher, dass diese Probleme gelöst werden können. Wechseln zu einem anderen Worttrennmodul möglicherweise auch schwerwiegenden Problemen führen beim Indizieren und Abfragen. Bevor Sie die Registrierung ändern, Sichern Sie die Registrierung, und stellen Sie sicher, dass Sie wissen, wie Sie die Registrierung wiederherstellen, wenn ein Problem auftritt.
  
    
    

Führen Sie die folgenden Schritte aus, ersetzen Sie das vorhandene Worttrennmodul mit einem benutzerdefinierten Worttrennmodul oder ersetzen das vorhandene Worttrennmodul mit einem Worttrennmodul in einer anderen Sprache.
  
    
    

1. Öffnen Sie den Registrierungs-Editor wie folgt:
    
1. Wählen Sie **Start**, und wählen Sie dann **Run**.
    
  
2. Klicken Sie im Dialogfeld **Open** Geben Sie **Regedit**, und wählen Sie dann **OK**.
    
  
2. Wählen Sie im Registrierungs-Editor den folgenden Registrierungsunterschlüssel:
    
    **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Office Server\\15.0\\Search\\Setup\\ContentIndexCommon\\LanguageResources\\Default\\** _language from the list below_
    
  
3. Klicken Sie im rechten Bereich öffnen Sie das Kontextmenü für den Registrierungswert **WBDLLPathOverride**, und wählen Sie **Modify**.
    
  
4. Klicken Sie im Dialogfeld **Edit String** **Value data** Sie im Feld Geben Sie den Pfad zu Ihrer benutzerdefinierten Worttrennmodul DLL-Datei, und wählen Sie dann **OK**. Die neue DLL sollte sich in demselben Pfad wie die vorhandene DLL befinden, die ersetzt wird.
    
  
5. Klicken Sie im rechten Bereich öffnen Sie das Kontextmenü für den Registrierungswert **WBreakerClass**, und wählen Sie **Modify**.
    
  
6. Klicken Sie im Dialogfeld **Edit String** **Value data** Sie im Feld Geben Sie die Klassen-ID der benutzerdefinierten Worttrennmodul, und wählen Sie dann **OK**.
    
  
7. Starten Sie die SharePoint-Suchhostcontroller und SharePoint Server 2013.
    
  
8. Führen Sie eine vollständige erneute Durchforstung.
    
  

## Unterstützte Sprachen für Word wörtertrennung Anpassungen in SharePoint Server 2013
<a name="SP15_SupportedLanguages"> </a>

Die folgenden Sprachen werden für die Anpassung von Word wörtertrennung unterstützt:
  
    
    
Arabisch
  
    
    
Bengali
  
    
    
Bulgarisch
  
    
    
Katalanisch
  
    
    
Chinesisch (Volksrepublik China)
  
    
    
Chinesisch (Taiwan)
  
    
    
Kroatisch
  
    
    
Tschechisch
  
    
    
Dänisch
  
    
    
Niederländisch (Niederländisch)
  
    
    
Englisch (Vereinigte Staaten)
  
    
    
Estnisch
  
    
    
Finnisch
  
    
    
Französisch (Standard)
  
    
    
Deutsch (Standard)
  
    
    
Griechisch
  
    
    
Gudscharati
  
    
    
Hebräisch
  
    
    
Hindi
  
    
    
Ungarisch
  
    
    
Isländisch
  
    
    
Indonesisch
  
    
    
Italienisch (Standard)
  
    
    
Japanisch
  
    
    
Kannada
  
    
    
Kasachisch
  
    
    
Koreanisch
  
    
    
Lettisch
  
    
    
Litauisch
  
    
    
Malaiisch
  
    
    
Malayalam
  
    
    
Marathi
  
    
    
Norwegisch
  
    
    
Polnisch
  
    
    
Portugiesisch (Portugiesisch)
  
    
    
Punjabi
  
    
    
Rumänisch
  
    
    
Russisch
  
    
    
Serbisch (Kyrillisch)
  
    
    
Slowakisch
  
    
    
Slowenisch
  
    
    
Spanisch (Moderne Sortierung)
  
    
    
Schwedisch
  
    
    
Tamil
  
    
    
Telugu
  
    
    
Thailändisch
  
    
    
Türkisch
  
    
    
Ukrainisch
  
    
    
Urdu
  
    
    
Vietnamesisch
  
    
    

## Zusätzliche Ressourcen
<a name="SP15wordbreakers_addresources"> </a>


-  [Konfigurieren der Suche in SharePoint 2013](configure-search-in-sharepoint-2013.md)
    
  
-  [Implementieren von einem Worttrennmodul](http://msdn.microsoft.com/en-us/library/ms693186%28v=vs.85%29.aspx)
    
  
-  [IWordBreaker-Schnittstelle](http://msdn.microsoft.com/en-us/library/ms691079%28v=vs.85%29.aspx)
    
  

