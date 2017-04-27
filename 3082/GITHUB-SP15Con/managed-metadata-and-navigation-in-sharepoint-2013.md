---
title: Navegación y metadatos administrados en SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: b66d4ec1-a2ef-49cc-8ca5-a6b516bff02e
---


# Navegación y metadatos administrados en SharePoint 2013

  
    
    
![Tema de información general conceptual](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
Obtenga información sobre los metadatos administrados empresariales (EMM) y las características de navegación en SharePoint 2013.
## Mejoras de las características de los metadatos administrados en SharePoint 2013 para desarrolladores
<a name="SP15_ManagedMetadataAndNav_ManagedMetadataFeatureEnhancements"> </a>

Puede utilizar metadatos administrados para crear taxonomías y estrategias de etiquetado que satisfagan necesidades empresariales específicas y detalladas. En SharePoint 2013, se ha extendido y mejorado el conjunto básico de API de metadatos administrados para proporcionar más capacidades y compatibilidad con los escenarios.
  
    
    

## Compatibilidad del modelo de objetos de cliente (CSOM) de .NET con las API de metadatos administrados
<a name="SP15_ManagedMetadataAndNav_CSOMSupport"> </a>

El CSOM de SharePoint 2013 admite el desarrollo y la personalización de la taxonomía. La taxonomía está disponible en modelos de programación de clientes .NET (CSOM), Silverlight y JavaScript. Desarrollar con ella tiene una lógica similar a desarrollar con el modelo de programación de servidor de .NET. Puede resultarle útil para desarrollar soluciones de CSOM que sean compatibles con escenarios en los que leer contenido sea más habitual que crearlo o administrarlo. Debe utilizar CSOM para habilitar el uso de la taxonomía en un escenario de nube como SharePoint Online o para un subconjunto de escenarios que estén disponibles de forma local.
  
    
    
Cuando desee crear un nuevo proyecto de CSOM en Visual Studio que use la función de taxonomía, defina las siguientes referencias:
  
    
    

- Microsoft.SharePoint.Client.dll
    
  
- Microsoft.SharePoint.Client.Runtime.dll
    
  
- Microsoft.SharePoint.Client.Taxonomy.dll
    
  
Desarrollar personalizaciones con CSOM es muy similar a desarrollar soluciones de taxonomía de servidor .NET: obtenga una referencia al objeto **TaxonomySession**, el objeto **TermStore**, los objetos **Group**, los objetos **TermSet** y los objetos **Term** necesarios para la sesión.
  
    
    

### Ejemplos de código: operaciones básicas con el CSOM de taxonomía
<a name="SP15_ManagedMetadataAndNav_ExampleBasicOperations"> </a>

Puede utilizar los siguientes ejemplos de código para realizar operaciones básicas con el CSOM de taxonomía. En el primer ejemplo se crea un objeto **Group**, un objeto **TermSet** y varios objetos **Term**. El segundo ejemplo procesa una iteración en un objeto **Group** y escribe su contenido.
  
    
    

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


  
    
    

## Anclaje
<a name="SP15_ManagedMetadataAndNav_Pinning"> </a>

En Microsoft SharePoint Server 2010, los usuarios pueden reutilizar términos (y todos los términos anidados en los términos reutilizados) en otras ubicaciones de la jerarquía de términos. Después de reutilizar estos términos, se podían modificar y los cambios se verían en todos los lugares donde se estaban reutilizando los términos. SharePoint 2013 presenta el anclaje de términos. Un término anclado es similar a un término que se reutiliza, excepto que es de solo lectura y no se puede cambiar en las ubicaciones donde se reutiliza el término. Para obtener un ejemplo, consulte  [Cómo usar el código para fijar términos a conjuntos de términos de navegación en SharePoint 2013](how-to-use-code-to-pin-terms-to-navigation-term-sets-in-sharepoint-2013.md).
  
    
    

  
    
    

## Compatibilidad con la vista Hoja de datos para los tipos de columna de metadatos administrados
<a name="SP15_ManagedMetadataAndNav_DatasheetViewSupport"> </a>

En SharePoint 2013, la funcionalidad de la vista Hoja de datos ha cambiado. Ahora, la hoja de datos utiliza una acción de doble clic para abrir la vista estándar que permite la edición de la cuadrícula. Ahora puede editar las columnas de metadatos usando las mismas características disponibles al editar elementos individuales. Esto incluye el acceso al conjunto de términos que hay detrás de la columna. Esta característica pone la funcionalidad que permite modificar metadatos al editar un elemento individual a disposición de la edición de hoja de datos.
  
    
    

## Navegación administrada
<a name="SP15_ManagedMetadataAndNav_ManagedNav"> </a>

La navegación administrada usa las características de metadatos administrados, como la capacidad de etiquetar elementos con los términos y de administrar términos en un almacén de términos, para proporcionar una navegación del sitio altamente personalizada. La navegación estructurada que depende de la infraestructura de SharePoint también estará disponible en SharePoint 2013.
  
    
    

## Direcciones URL descriptivas
<a name="SP15_ManagedMetadataAndNav_FriendlyURLs"> </a>

Las direcciones URL descriptivas son un formato de dirección URL más corto que se muestra en la barra de direcciones de la mayoría de páginas de publicación de SharePoint, incluida la página principal del sitio. Son direcciones URL adecuadas para SEO y aparecen en los resultados de búsqueda. 
  
    
    

## Compatibilidad con nuevos escenarios
<a name="SP15_ManagedMetadataAndNav_SupportForNewScenarios"> </a>

Un administrador de almacén de términos puede mejorar y expandir modelos de uso de términos basados en una funcionalidad de metadatos administrados más flexible y eficaz en :
  
    
    

- Cree un vínculo a otra colección de sitios y vea los términos de otros. Si desea que su conjunto de términos esté disponible para otras colecciones de sitios conectadas al servicio de metadatos administrados, cree un **global term set**. Si desea crear un conjunto de términos privados que solo esté disponible para una colección de sitios específica cuando se almacene en el servicio de metadatos administrados, cree un **local term set**. 
    
  
- Impida que los usuarios puedan usar palabras clave que no estén contenidas en un conjunto de términos específico.
    
  
- Obtenga compatibilidad multilingüe adicional, incluida la compatibilidad con la traducción automatizada y los LCID flexibles. 
    
  

## Escenarios incompatibles para trabajar con definiciones de sitios personalizadas
<a name="SP15_ManagedMetadataAndNav_UnsupportedScenarios"> </a>


- SharePoint 2013 no admite la creación de campos de taxonomía (columnas de sitios de metadatos administrados) de forma declarativa mediante una definición XML.
    
  
- SharePoint 2013 no admite el uso de campos de taxonomía (columnas de sitios de metadatos administrados) en las plantillas de sitio.
    
  
- Para obtener más información, consulte el artículo de soporte técnico de Microsoft n.º 898631:  [Escenarios admitidos y no admitidos](http://support2.microsoft.com/default.aspx?scid=kb;ES-ES;898631)
    
  

## Recursos adicionales
<a name="SP15_ManagedMetadataAndNav_AdditionalResources"> </a>


-  [Navegación administrada en SharePoint 2013](managed-navigation-in-sharepoint-2013.md)
    
  
-  [Elemento web de búsqueda de contenido en SharePoint 2013](content-search-web-part-in-sharepoint-2013.md)
    
  

