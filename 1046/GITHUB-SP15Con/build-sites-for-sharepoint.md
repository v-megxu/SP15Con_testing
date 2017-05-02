---
title: Criar sites para o SharePoint
ms.prod: SHAREPOINT
ms.assetid: 3b372a63-7cdf-462a-abb4-750e611e967d
---


# Criar sites para o SharePoint
Saiba mas sobre o novo modelo de criação e de publicação para sites no SharePoint 2013.
## Introdução à publicação de sites para designers e desenvolvedores no SharePoint
<a name="SP15_BuildSitesForSP2013_IntroToSitePublishing"> </a>

O SharePoint 2013 introduz um modelo de criação e de publicação para criar sites de publicação. Você pode usar sites de publicação para publicar conteúdo na intranet ou em sites da Internet. Os sites de publicação são diferentes de outros tipos de sites do SharePoint, como sites de equipe, principalmente devido à sua finalidade - vários usuários leem conteúdo do site de publicação, mas somente alguns contribuem adicionando, atualizando e excluindo conteúdo de um ou mais conjuntos de sites. Compare esses sites a sites de equipe, onde várias pessoas podem colaborar e contribuir para o conteúdo.
  
    
    
Você pode usar os recursos de publicação de sites do SharePoint 2013 para criar, personalizar e manter sites de publicação que atendam a necessidades comerciais específicas. Se você for um designer profissional com habilidades em HTML, CSS e JavaScript ou um desenvolvedor que escreve aplicativos do SharePoint e usa código .NET personalizado para criar soluções de sites e de farm, você poderá usar recursos de site no SharePoint 2013 para gerenciar todas as fases do ciclo de vida do conteúdo, incluindo:
  
    
    

- **Authoring** e reutilização do conteúdo do site.
    
  
- **Branding** e design da aparência e do comportamento do seu site.
    
  
- **Managing metadata** - você pode criar um sistema de navegação de sites orientado a taxonomia.
    
  
- O conteúdo de **Publishing** suave no conjunto de sites atual ou o conteúdo de publicação em conjuntos de sites - mesmo se estendendo além dos limites do site da intranet e da Internet.
    
  
- **Accessibility** - você pode usar para melhorar a acessibilidade dos seus sites publicados.
    
  
Se você quiser ver um resumo das novidades para designers e desenvolvedores de sites de publicação no SharePoint 2013, confira  [Novidades no desenvolvimento de site do SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md).
  
    
    

## Criação, design e identidade visual no SharePoint
<a name="SP15_BuildSitesForSP2013_AuthoringDesignBranding"> </a>

O SharePoint 2013 oferece uma nova abordagem para o design de sites. O fluxo de trabalho de criação de conteúdo foi revisado de forma que você possa criar conteúdo usando qualquer um deles, e crie um ótimo conteúdo. Para dar uma identidade visual ao seu site sem precisar escrever código .NET personalizado, use o  [Gerenciador de Design](overview-of-design-manager-in-sharepoint-2013.md) para importar elementos de design. Com o Gerenciador de Design, você também poderá criar uma página mestra baseada em HTML para definir o cromado compartilhado por todas as páginas do seu site e criar layouts de página para modelos de design para páginas. Se você optar por escrever código personalizado, poderá usar o servidor .NET, o cliente .NET (CSOM), Silverlight e bibliotecas do JavaScript.
  
    
    
O SharePoint 2013 também oferece uma nova abordagem para conteúdo e criação. O fluxo de trabalho de criação de conteúdo foi revisado de forma que você possa criar conteúdo usando qualquer ferramenta de criação e de identidade visual e criar um ótimo conteúdo. Para dar uma identidade visual a seu site sem precisar escrever código .NET personalizado, use o Gerenciador de Design. Você pode importar elementos de design e criar uma página mestra baseada em HTML para definir os elementos de quadros compartilhados - o cromado - que todas as páginas e layouts de página do seu site compartilham. Se você optar por escrever código personalizado ao criar a identidade visual do seu site, poderá usar bibliotecas de publicação e de taxonomia.
  
    
    

## Sites de publicação, programação do modelo de objeto cliente e o novo modelo de aplicativo do SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingSites"> </a>

Você pode usar o novo modelo de objeto de cliente .NET (CSOM) para desenvolver aplicativos do SharePoint com o modelo de Suplementos do SharePoint. Você pode usar várias das APIs que também estão disponíveis para programação de servidor .NET nos modelos de objeto cliente do .NET, que dão suporte ao desenvolvimento de cliente .NET, Silverlight, JavaScript - e, em alguns casos, do Windows Phone. Algumas ideias para o desenvolvimento de aplicativos para sites incluem pesquisas, aplicativos de gerenciamento de contas, suporte a eCommerce, integração de recursos sociais e de dados externos a sites de publicação, adições de conteúdo terceirizado e aplicativos associados móveis.
  
    
    

## Modelo de página para sites de publicação
<a name="SP15_BuildSitesForSP2013_PageModel"> </a>

O SharePoint 2013 inclui um modelo de página para sites de publicação. O modelo de página inclui páginas mestras, layouts de página e outros componentes que renderizam a estrutura, o conteúdo, a aparência e o comportamento do seu site. Para saber mais, consulte  [Visão geral do modelo de página do SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Páginas mestras e layouts de página
<a name="SP15_BuildSitesForSP2013_MasterAndLayout"> </a>

Uma página mestra é o principal modelo que define os elementos estruturais compartilhados do seu site - o cromado. Todas as páginas do site compartilham esses elementos, que definem as regiões da página que exibe o conteúdo de layout da página.
  
    
    
Os layouts da página são usados por páginas individuais de determinado tipo. Eles são preenchidos com organizações de campos de página. Essas páginas definem elementos individuais na página. As páginas individuais se baseiam em layouts da página e são criadas em seu navegador da Web por código personalizado ou pela forma como os usuários do site preenchem os campos da página. Para saber mais sobre o modelo de página no SharePoint 2013, consulte  [Visão geral do modelo de página do SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
  
    
    

## Controles de renderização do lado cliente
<a name="SP15_BuildSitesForSP2013_ClientSideRendering"> </a>

Todos os novos controles do SharePoint 2013 são renderizados. Os dados são gravados nos controles em uma matriz JSON do lado cliente e você pode exibir conteúdo usando o JavaScript, CSS e modelos. Como um designer ou desenvolvedor, você terá controle sobre a forma como o conteúdo é renderizado na página e pode usar diversas técnicas de design para obter a aparência e os comportamentos desejados nas páginas publicadas usando recursos como a  [Pesquisa de conteúdo da Web Part do SharePoint 2013](content-search-web-part-in-sharepoint-2013.md) e os modelos de exibição.
  
    
    

## Sites e dispositivos móveis
<a name="SP15_BuildSitesForSP2013_SitesAndMobile"> </a>

Os sites de publicação no SharePoint 2013 são otimizados para desenvolvimento móvel. Você pode definir canais para um ou mais dispositivos (canais de dispositivo) e atribuir uma página mestra alternativa para cada canal, dando a ela elementos estruturais exclusivos, ou o cromado. É possível optar por incluir ou excluir partes de qualquer layout de página em um canal e visualizar como o design de canal móvel está progredindo durante o desenvolvimento.
  
    
    

## Metadados e navegação no SharePoint
<a name="SP15_BuildSitesForSP2013_MetadataNav"> </a>

Os recursos de metadados introduzidos no Microsoft SharePoint Server 2010 são aprimorados e estendidos no SharePoint 2013 para melhor desempenho, acesso mais fácil por meio da interface do usuário e navegação orientada a taxonomia - chamada de navegação gerenciada. Você pode usar a navegação gerenciada ou a navegação baseada na estrutura de site do SharePoint - chamada de navegação estruturada - para criar a navegação do seu site. Para saber mais sobre a navegação gerenciada, consulte [Metadados gerenciados e navegação no SharePoint 2013](managed-metadata-and-navigation-in-sharepoint-2013.md) e [Navegação gerenciada no SharePoint 2013](managed-navigation-in-sharepoint-2013.md).
  
    
    

## Conteúdo de publicação no SharePoint
<a name="SP15_BuildSitesForSP2013_PublishingContent"> </a>

O SharePoint 2013 oferece os seguintes recursos de publicação de conteúdo que permitem a você desenvolver sites de publicação que deem suporte a topologias e cenários mais complexos, acessíveis e flexíveis. 
  
    
    

### Catálogos

O SharePoint 2013 introduz catálogos, que você pode usar para publicar conteúdo em conjuntos de sites. Os recursos de publicação entre sites dependem dos catálogos. Você pode usá-los para reutilizar conteúdo em seus site e no limite entre seus sites de intranet e os sites da Internet. Para consultas de pesquisa predefinidas, os catálogos são sinalizados na pesquisa. Você pode expor conteúdo em catálogos em conjuntos de sites usando a  [Pesquisa de conteúdo da Web Part do SharePoint 2013](content-search-web-part-in-sharepoint-2013.md).
  
    
    

### Publicação entre sites

O SharePoint 2013 introduz um recurso de publicação entre sites para reutilizar conteúdo em vários conjuntos de sites. Ele usa recursos de pesquisa internos para habilitar cenários e arquiteturas de publicação. Pela primeira vez, você pode projetar sites entre farms do SharePoint - permitindo que seus sites se estendam para além dos limites entre intranets e a Internet. É possível usar o CSWP para exibir dados de da pesquisa publicados entre sites e conjuntos de sites.
  
    
    

### Variações e sites multilíngue

Você pode usar o recurso de variações no SharePoint 2013 para criar sites multilíngues ou outros sites onde você deseja variar a apresentação do seu conteúdo. O recurso de variações é restrito a um conjunto de sites. Ou seja, você pode criar "variantes" de idioma/localidade de destino de um idioma/localidade de origem como sites atuais no mesmo conjunto de sites do SharePoint. As variações dão suporte a URLs amigáveis e à capacidade de exportar ou de importar conteúdo para tradução por um terceiro no  [formato de arquivo XLIFF](the-xliff-interchange-file-format-in-sharepoint-2013.md). Você pode incluir rótulos, uma página para tradução e replicação, uma variedade de itens de lista (por exemplo, bibliotecas de documentos) e navegação em seus pacotes de exportação.
  
    
    

### Sites acessíveis

Você pode usar o recurso de variações no SharePoint 2013 para criar sites acessíveis ou outros sites em que queira adaptar a apresentação do seu conteúdo para usuários que possuem uma variedade de necessidades de acessibilidade. O SharePoint 2013 fornece um "Modo Mais Acessível", que pode ser ativado abrindo uma página da Web do SharePoint e pressionando a tecla Tab até encontrar o link "Ativar o Modo Mais Acessível". Este recurso recria a página da Web em HTML padrão, tornando-a mais compatível com leitores de tela. Ao assegurar que os usuários poderão pressionar a tecla Tab para focar neste link, você pode criar uma versão mais acessível da sua página da Web do SharePoint. Isso inclui a conversão de menus suspensos baseados em JavaScript para listas de hiperlinks e objetos convertidos em HTML simples para permitir que os leitores de tela entendam o conteúdo. 
  
    
    

## Recursos adicionais
<a name="SP15_BuildSitesForSP2013_AdditionalResources"> </a>


-  [Otimizar a acessibilidade do site do SharePoint](optimize-sharepoint-site-accessibility.md)
    
  
-  [Configurar um ambiente de desenvolvimento geral para o SharePoint 2013](set-up-a-general-development-environment-for-sharepoint-2013.md)
    
  
-  [Novidades no desenvolvimento de site do SharePoint 2013](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [Visão geral de estratégia Download mínimo](minimal-download-strategy-overview.md)
    
  
-  [Modificar componentes do SharePoint do MDS](modify-sharepoint-components-for-mds.md)
    
  
-  [Biblioteca de classes do servidor de Conteúdo e Sites do SharePoint 2013](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)
    
  
-  [Biblioteca de classes de cliente de sites e conteúdo](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx)
    
  

