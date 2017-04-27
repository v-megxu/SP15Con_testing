---
title: Verwaltete Metadaten und Navigation in SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: b66d4ec1-a2ef-49cc-8ca5-a6b516bff02e
---


# Verwaltete Metadaten und Navigation in SharePoint 2013

  
    
    
![Konzeptuelles Übersichtsthema](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
Informationen über verwaltete Metadaten von Unternehmen (EMM) und Navigationsfunktionen in SharePoint 2013.
## Funktionsverbesserungen für verwaltete Metadaten in SharePoint 2013 für Entwickler
<a name="SP15_ManagedMetadataAndNav_ManagedMetadataFeatureEnhancements"> </a>

Mit verwalteten Metadaten können Sie Taxonomien erstellen und Strategien markieren, die bestimmten Geschäftsanforderungen entsprechen. In SharePoint 2013 wurde der grundlegende verwaltete Metadaten-API-Satz erweitert und verbessert, um mehr Funktionen bereitzustellen und mehr Szenarien zu unterstützen.
  
    
    

## Unterstützung vom .NET-Clientobjektmodell für verwaltete Metadaten-APIs
<a name="SP15_ManagedMetadataAndNav_CSOMSupport"> </a>

Das SharePoint 2013-Clientobjektmodell unterstützt das Anpassen und Erstellen von Taxonomien. Taxonomie steht im .NET-Clientobjektmodell, in Silverlight und in JavaScript-Programmiermodellen zur Verfügung. Die Entwicklung mit diesem ähnelt der Entwicklung mit dem .NET-Serverprogrammiermodell. Möglicherweise möchten Sie Clientobjektmodell-Lösungen zur Unterstützung von Szenarien entwickeln, in denen das Lesen von Inhalten häufiger auftritt, als das Erstellen oder Verwalten von diesen. Sie müssen das Clientobjektmodell verwenden, um die Verwendung von Taxonomie in einem cloudbasierten Szenario wie SharePoint Online oder für eine Teilmenge von Szenarien zu aktivieren, die lokal verfügbar sind.
  
    
    
Wenn Sie ein neues Clientobjektmodell-Projekt in Visual Studio erstellen möchten, in dem die Taxonomiefunktion verwendet wird, legen Sie die folgenden Verweise fest:
  
    
    

- Microsoft.SharePoint.Client.dll
    
  
- Microsoft.SharePoint.Client.Runtime.dll
    
  
- Microsoft.SharePoint.Client.Taxonomy.dll
    
  
Die Entwicklung von Anpassungen mit dem Clientobjektmodell ähnelt weitestgehend der Entwicklung von .NET-Servertaxonomielösungen: Informationen zum **TaxonomySession**- und **TermStore**-Objekt, zu **Group**-, **TermSet**- und **Term**-Objekten, die für die Sitzung erforderlich sind.
  
    
    

### Codebeispiele: Grundlegende Vorgänge mit dem Taxonomie-Clientobjektmodell
<a name="SP15_ManagedMetadataAndNav_ExampleBasicOperations"> </a>

Mit den folgenden Codebeispielen können Sie grundlegende Vorgänge mit dem Taxonomie-Clientobjektmodell abschließen. Im ersten Beispiel werden ein **Group**- Objekt, ein **TermSet**-Objekt und **Term**-Objekte erstellt. Im zweiten Beispiel wird ein **Group**-Objekt durchlaufen und seine Inhalte werden geschrieben.
  
    
    

```cs

       private void CreateColorsTermSet(string siteUrl)
        {
           ClientContext clientContext = new ClientContext(siteUrl);
 
           TaxonomySession taxonomySession = TaxonomySession.GetTaxonomySession(clientContext);
            clientContext.Load(taxonomySession,
                ts => ts.TermStores.Include(
                    store => store.Name,
                    store => store.Groups.Include(
                        group => group.Name
                        )
                    )
                );
            clientContext.ExecuteQuery();
 
           if( taxonomySession != null )
            {
               TermStore termStore = taxonomySession.GetDefaultSiteCollectionTermStore();
               if (termStore != null)
                {
                   //
                   //  Create group, termset, and terms.
                   //
                   TermGroup myGroup = termStore.CreateGroup("MyGroup",Guid.NewGuid());
                   TermSet myTermSet = myGroup.CreateTermSet("Color",Guid.NewGuid(), 1033);
                    myTermSet.CreateTerm("Red", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Orange", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Yellow", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Green", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Blue", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Purple", 1033,Guid.NewGuid());
 
                    clientContext.ExecuteQuery();
                }
            }
        }
 
       private void DumpTaxonomyItems(string siteUrl)
        {
           ClientContext clientContext = new ClientContext(siteUrl);
 
           //
           // Load up the taxonomy item names.
           //
            TaxonomySession taxonomySession =TaxonomySession.GetTaxonomySession(clientContext);
           TermStore termStore = taxonomySession.GetDefaultSiteCollectionTermStore();
            clientContext.Load(termStore,
                    store => store.Name,
                    store => store.Groups.Include(
                        group => group.Name,
                        group => group.TermSets.Include(
                            termSet => termSet.Name,
                            termSet => termSet.Terms.Include(
                                term => term.Name)
                        )
                    )
            );
            clientContext.ExecuteQuery();
 
 
           //
           //Writes the taxonomy item names.
           //
           if( taxonomySession != null )
            {
               if (termStore != null)
                {
                   foreach( TermGroup groupin termStore.Groups)
                    {
                       Console.WriteLine("Group " + group.Name);
 
                       foreach( TermSet termSetin group.TermSets )
                        {
                           Console.WriteLine("TermSet " + termSet.Name);
 
                            foreach(Term term in termSet.Terms)
                            {
                               //Writes root-level terms only.
                               Console.WriteLine("Term " + term.Name);
                            }
                        }
                    }
                }
            }
 
        }

```


  
    
    

## Anheften
<a name="SP15_ManagedMetadataAndNav_Pinning"> </a>

In Microsoft SharePoint Server 2010konnten Benutzer Ausdrücke (und alle innerhalb des wiederverwendeten Ausdrucks verschachtelten Ausdrücke) an anderen Stellen in der Ausdruckshierarchie wiederverwendet werden. Wenn diese Ausdrücke nach Wiederverwendung geändert wurden, wurden die Änderungen an allen Stellen übernommen, wo diese wiederverwendet wurden. In SharePoint 2013 wurde das Anheften von Ausdrücken eingeführt. Ein angehefteter Ausdruck entspricht einem wiederverwendeten Ausdruck mit der Ausnahme, dass er schreibgeschützt ist und nicht an den Stellen geändert werden kann, an denen er wiederverwendet wird. Ein Beispiel hierzu finden Sie unter  [Vorgehensweise: Verwendung Code Pin Bedingungen Navigation Begriff wird im SharePoint 2013](how-to-use-code-to-pin-terms-to-navigation-term-sets-in-sharepoint-2013.md).
  
    
    

  
    
    

## Unterstützung für die Datenblattansicht für verwaltete Metadaten-Spaltentypen
<a name="SP15_ManagedMetadataAndNav_DatasheetViewSupport"> </a>

In SharePoint 2013 wurde die Datenblatt-Ansichtsfunktion geändert. Die Standardansicht für die Rasterbearbeitung wird nun mit einem Doppelklick auf die Aktion geöffnet werden. Metadatenspalten können mit den gleichen Funktionen wie beim Bearbeiten von einzelnen Elementen bearbeitet werden. Dies umfasst den Zugriff auf den Ausdruckssatz hinter der Spalte. Bei dieser Funktion geht es um Funktionen zur Metadatenänderung, die beim Bearbeiten eines einzelnen Elements für die Datenblattbearbeitung zur Verfügung stehen.
  
    
    

## Verwaltete Navigation
<a name="SP15_ManagedMetadataAndNav_ManagedNav"> </a>

Die verwaltete Navigation umfasst verwaltete Metadatenfunktionen wie das Anheften von Elementen an Ausdrücke und das Verwalten von Ausdrücken in einem Ausdrucksspeicher zur Bereitstellung einer in hohem Maße angepassten Websitenavigation. Die strukturierte Navigation, die von der SharePoint-Infrastruktur abhängt, ist in SharePoint 2013 weiterhin verfügbar.
  
    
    

## Benutzerfreundliche URLs
<a name="SP15_ManagedMetadataAndNav_FriendlyURLs"> </a>

Benutzerfreundliche URLs stellen ein kürzeres URL-Format dar, das in der Adressleiste der meisten SharePoint-Veröffentlichungsseiten angezeigt wird, einschließlich der Willkommensseite Ihrer Website. Sie sind SEO-freundlich und werden in Suchergebnissen angezeigt. 
  
    
    

## Unterstützung für neue Szenarien
<a name="SP15_ManagedMetadataAndNav_SupportForNewScenarios"> </a>

Mit dem Ausdrucksspeicher-Manager können Ausdrucksverwendungsmodelle, die auf flexibleren und leistungsstärkeren verwalteten Metadatenfunktionen in basieren, verbessert und erweitert werden:
  
    
    

- Verweisen auf eine andere Websitesammlung und Anzeigen von Ausdrücken von anderen Benutzern.Wenn Sie Ihren Ausdruckssatz für andere mit dem verwalteten Metadatendienst verknüpften Websitesammlungen zur Verfügung stellen möchten, erstellen Sie ein **global term set**. Wenn Sie einen privaten Ausdruckssatz erstellen möchten, der nur für eine bestimmte Websitesammlung zur Verfügung steht, wenn er im verwalteten Metadatendienst gespeichert ist, erstellen Sie ein **local term set**. 
    
  
- Das Verwenden von Schlüsselwörtern außerhalb eines bestimmten Ausdruckssatzes für Benutzer blockieren.
    
  
- Zusätzliche, mehrsprachige Unterstützung, darunter Unterstützung für automatisierte Übersetzung und flexible LCIDs. 
    
  

## Nicht unterstützte Szenarien für das Arbeiten mit benutzerdefinierten Websitedefinitionen
<a name="SP15_ManagedMetadataAndNav_UnsupportedScenarios"> </a>


- In SharePoint 2013 wird das Erstellen von Taxonomiefeldern (verwalteten Metadaten-Websitespalten) mithilfe einer XML-Definition nicht unterstützt.
    
  
- In SharePoint 2013 wird das Verwenden von Taxonomiefeldern (verwalteten Metadaten-Websitespalten) in Websitevorlagen nicht unterstützt.
    
  
- Weitere Informationen finden Sie im Microsoft Support-Artikel #898631:  [Unterstützte und nicht unterstütze Szenarien](http://support2.microsoft.com/default.aspx?scid=kb;de-de;898631
)
    
  

## Weitere Ressourcen
<a name="SP15_ManagedMetadataAndNav_AdditionalResources"> </a>


-  [Verwaltete Navigation in SharePoint 2013](managed-navigation-in-sharepoint-2013.md)
    
  
-  [Inhaltssuche-Webpart in SharePoint 2013](content-search-web-part-in-sharepoint-2013.md)
    
  

