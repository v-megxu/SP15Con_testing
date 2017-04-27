---
title: Métadonnées et navigation gérées dans SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: b66d4ec1-a2ef-49cc-8ca5-a6b516bff02e
---


# Métadonnées et navigation gérées dans SharePoint 2013

  
    
    
![Rubrique de présentation conceptuelle](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
Découvrez les fonctionnalités de navigation et de métadonnées gérées d'entreprise dans SharePoint 2013.
## Améliorations des fonctionnalités de métadonnées gérées dans SharePoint 2013 pour les développeurs
<a name="SP15_ManagedMetadataAndNav_ManagedMetadataFeatureEnhancements"> </a>

Vous pouvez utiliser des métadonnées gérées pour créer des taxonomies et des stratégies de marquage qui répondent à des besoins d'entreprise spécifiques et détaillés. Dans SharePoint 2013, l'ensemble d'API de métadonnées gérées de base est développé et amélioré pour prendre en charge davantage de fonctionnalités et de scénarios.
  
    
    

## Prise en charge du modèle objet client .NET (CSOM) pour les API de métadonnées gérées
<a name="SP15_ManagedMetadataAndNav_CSOMSupport"> </a>

Le modèle CSOM SharePoint 2013 prend en charge le développement et la personnalisation de la taxonomie. La taxonomie est disponible dans les modèles de programmation client .NET (CSOM), Silverlight et JavaScript. Le développement avec ce dernier est logiquement semblable au développement avec le modèle de programmation du serveur .NET. Il peut s'avérer utile de développer des solutions CSOM pour prendre en charge des scénarios où la lecture de contenu est plus courante que sa création ou son administration. Vous devez utiliser le modèle CSOM pour activer l'utilisation de la taxonomie dans un scénario dans le cloud comme SharePoint Online ou pour un sous-ensemble de scénarios disponibles en local.
  
    
    
Lorsque vous souhaitez créer un projet CSOM dans Visual Studio utilisant la fonctionnalité de taxonomie, définissez les références suivantes :
  
    
    

- Microsoft.SharePoint.Client.dll
    
  
- Microsoft.SharePoint.Client.Runtime.dll
    
  
- Microsoft.SharePoint.Client.Taxonomy.dll
    
  
Le développement de personnalisations avec CSOM est très semblable au développement de solutions de taxonomie du serveur .NET : vous devez obtenir une référence à l'objet **TaxonomySession** et à l'objet **TermStore**, ainsi qu'aux objets **Group**, **TermSet** et **Term** requis pour la session.
  
    
    

### Exemples de code : opérations de base avec le modèle CSOM de taxonomie
<a name="SP15_ManagedMetadataAndNav_ExampleBasicOperations"> </a>

Vous pouvez utiliser les exemples de code suivants pour effectuer des opérations de base avec le modèle CSOM de taxonomie. Le premier exemple crée un objet **Group**, un objet **TermSet** et des objets **Term**. Le second exemple effectue une itération sur un objet **Group** et écrit son contenu.
  
    
    

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


  
    
    

## Épinglage
<a name="SP15_ManagedMetadataAndNav_Pinning"> </a>

Dans Microsoft SharePoint Server 2010, les utilisateurs peuvent réutiliser les termes (et tous les termes imbriqués sous les termes réutilisés) à d'autres emplacements dans la hiérarchie de termes. Une fois que ces termes ont été réutilisés, ils peuvent être modifiés, et les modifications sont visibles partout où les termes ont été réutilisés. SharePoint 2013 intègre l'épinglage des termes. Un terme épinglé est semblable à un terme réutilisé, sauf qu'il est en lecture seule et ne peut pas être modifié aux emplacements où le terme est réutilisé. Pour obtenir un exemple, reportez-vous à la rubrique  [Comment : utiliser du code aux termes de broche à terme de navigation définit dans SharePoint 2013](how-to-use-code-to-pin-terms-to-navigation-term-sets-in-sharepoint-2013.md).
  
    
    

  
    
    

## Prise en charge du mode Feuille de données pour les types de colonnes de métadonnées gérées
<a name="SP15_ManagedMetadataAndNav_DatasheetViewSupport"> </a>

Dans SharePoint 2013, l'affichage du mode Feuille de données a été modifié. Désormais, la feuille de données utilise une action de double-clic afin d'ouvrir un affichage standard pour la modification de la grille. Vous pouvez désormais modifier les colonnes de métadonnées à l'aide des mêmes fonctionnalités que celles disponibles lorsque vous modifiez des éléments individuels. Cela inclut l'accès à l'ensemble de termes qui se trouve derrière la colonne. Cette fonctionnalité consiste à rendre disponible la fonctionnalité de modification des métadonnées lorsque vous modifiez un élément individuel pour la modification de la feuille de données.
  
    
    

## Navigation gérée
<a name="SP15_ManagedMetadataAndNav_ManagedNav"> </a>

La navigation gérée utilise des fonctionnalités de métadonnées gérées, telles que la possibilité de marquer des éléments avec des termes et de gérer les termes dans un magasin de termes, afin de fournir une navigation dans les sites hautement personnalisée. La navigation structurée, qui dépend de l'infrastructure SharePoint, est toujours disponible dans SharePoint 2013.
  
    
    

## URL conviviales
<a name="SP15_ManagedMetadataAndNav_FriendlyURLs"> </a>

Les URL conviviales sont un format d'URL réduit qui apparaît dans la barre d'adresse de la plupart des pages de publication SharePoint, y compris la page d'accueil de votre site. Elles sont compatibles SEO et apparaissent dans les résultats de la recherche. 
  
    
    

## Prise en charge de nouveaux scénarios
<a name="SP15_ManagedMetadataAndNav_SupportForNewScenarios"> </a>

Un gestionnaire de magasin de termes permet d'améliorer et de développer des modèles d'utilisation des termes en fonction des fonctionnalités de métadonnées gérées plus flexibles et plus puissantes dans :
  
    
    

- Créer un lien vers une autre collection de sites et afficher les termes des autres. Pour rendre votre ensemble de termes disponible pour les autres collections de sites connectées au service de métadonnées gérées, créez un **global term set**. Si vous souhaitez créer un ensemble de termes privé disponible uniquement pour une collection de sites spécifique lorsqu'elle est stockée dans le service de métadonnées gérées, créez un **local term set**. 
    
  
- Interdire l'utilisation de mots clés en dehors d'un ensemble de termes spécifique.
    
  
- Obtenir une prise en charge multilingue supplémentaire, y compris la prise en charge de la traduction automatique et de LCID flexibles. 
    
  

## Scénarios non pris en charge pour l'utilisation des définitions de site personnalisées
<a name="SP15_ManagedMetadataAndNav_UnsupportedScenarios"> </a>


- SharePoint 2013 ne prend pas en charge la création de champs de taxonomie (colonnes de site de métadonnées gérées) de façon déclarative via une définition XML.
    
  
- SharePoint 2013 ne prend pas en charge l'utilisation des champs de taxonomie (colonnes de site de métadonnées gérées) dans les modèles de site.
    
  
- Pour plus d'informations, consultez l'article n° 898631 du support technique de Microsoft :  [Scénarios pris en charge et non pris en charge](http://support2.microsoft.com/default.aspx?scid=kb;FR-FR;898631)
    
  

## Ressources supplémentaires
<a name="SP15_ManagedMetadataAndNav_AdditionalResources"> </a>


-  [Navigation gérée dans SharePoint 2013](managed-navigation-in-sharepoint-2013.md)
    
  
-  [Composant WebPart de recherche de contenu dans SharePoint 2013](content-search-web-part-in-sharepoint-2013.md)
    
  

