---
title: Como personalizar layouts de página para um site baseado em catálogo no SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 21d8db99-73b3-4429-b6cb-04e375af9f55
---


# Como personalizar layouts de página para um site baseado em catálogo no SharePoint 2013
Saiba como criar e personalizar layouts da página de categoria e da página de item de catálogo para um site de publicação entre sites do SharePoint Server 2013.
## Pré-requisitos para criação e personalização de layouts da página para um site baseado em catálogos
<a name="bk_prereqs"> </a>

Para seguir as etapas deste exemplo, você deverá ter o seguinte:
  
    
    

- Um editor HTML
    
  
- Um ambiente de publicação entre sites do SharePoint Server 2013
    
  
Para saber mais sobre como configurar um ambiente de publicação entre sites do SharePoint, consulte  [Configurar a publicação entre sites no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj656774.aspx).
  
    
    

### Conceitos fundamentais para saber como criar e personalizar layouts da página para um site baseado em catálogos

A Tabela 1 lista artigos úteis que poderão ajudar você a compreender os conceitos e as etapas envolvidas na criação e na personalização de layouts da página para um site baseado em catálogos.
  
    
    

**Tabela 1. Conceitos fundamentais para a criação e a personalização de layouts da página para um site baseado em catálogos**


|**Título do artigo**|**Descrição**|
|:-----|:-----|
| [Visão geral da publicação entre sites no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj635883.aspx) <br/> |Saiba como usar a publicação entre sites e Web Parts de Pesquisa para criar sites de Internet, intranet e extranet adaptativos do SharePoint.  <br/> |
| [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) <br/> |Saiba como criar layouts da página no SharePoint Server 2013.  <br/> |
| [Como: resolver erros e avisos ao visualizar uma página no SharePoint 2013](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md) <br/> |Sabia como resolver qualquer problema que impeça que a visualização do lado servidor seja renderizada em sua página.  <br/> |
| [Trechos de código do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-snippets.md) <br/> |Saiba como usar trechos de código para adicionar funcionalidade do SharePoint à sua página mestra ou layout da página HTML.  <br/> |
   

## Introdução a layouts da página de categoria e a layouts da página de item de catálogo
<a name="bk_introduction"> </a>

As páginas de categoria e as páginas de item de catálogo são layouts da página que você pode usar par amostrar conteúdo de catálogo estruturado consistentemente em um site. Por padrão, o SharePoint Server 2013 pode criar automaticamente um layout da página de categoria e um layout da página de item de catálogo por conexão de catálogo. As páginas baseadas nesses layouts são criadas na biblioteca Páginas de um site de publicação ao se conectar o site a um catálogo. Para saber mais sobre layouts da página, consulte  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md). Para saber mais sobre recursos específicos de layouts da página de categoria e layouts da página de item de catálogo, consulte  [Visão geral da publicação entre sites no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj635883.aspx).
  
    
    
Por padrão, os layouts da página de categoria e os layouts da página de item de catálogo são criados automaticamente quando você conecta um site de publicação a um catálogo. Você também pode usar o Gerenciador de Design para criar layouts da página de categoria e layouts da página de item de catálogo que poderão ser selecionados na conexão a um site de publicação a um catálogo ou quando o conjunto de termos de navegação for configurado em um site de publicação.
  
    
    

## Criar um layout da página de categoria
<a name="bk_createCategoryPage"> </a>

Antes de poder criar ou personalizar um layout da página de categoria, recomendamos que você crie uma unidade de rede mapeada que aponte para a **Galeria de Páginas Mestras**. Para saber mais, consulte  [Como: mapear uma unidade de rede para a Galeria de páginas mestras do SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    
A maneira mais simples de criar um layout da página de categoria é permitir que o SharePoint crie o layout da página automaticamente ao conectar o site de publicação a um catálogo e então personalizar o layout da página de categoria para alterar a marcação como exigido pelo design de página. Como alternativa, você pode criar um novo layout da página de categoria desde o início usando o Gerenciador de Design.
  
    
    

### Para personalizar um layout da página de categoria existente criado automaticamente pelo SharePoint


1. Usando o Windows Explorer, abra a unidade de rede mapeada para a Galeria de Páginas Mestras.
    
  
2. Para personalizar um layout da página de categoria, edite o arquivo HTML que reside diretamente no servidor usando um editor HTML para abrir e editar o arquivo HTML na unidade mapeada. Sempre que você salvar o arquivo HTML, todas as alterações serão sincronizadas ao arquivo .aspx associado.
    
  
3. Substitua a marcação dentro do espaço reservado de conteúdo que tem o **id="PlaceHolderMain"** com a marcação que você deseja usar no layout da página.
    
    > **IMPORTANTE**
      > Você deve manter a marcação Trecho de Pesquisa de Conteúdo de forma que a página de categoria possa exibir resultados da pesquisa. 
4. Para configurar e copiar o HTML para todos os trechos que você deseja adicionar à página, siga da etapa 1 à etapa 11 na seção "Inserir um trecho da Galeria de Trechos de Código" de  [Trechos de código do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
5. Faça todas as outras alterações obrigatórias na marcação e então salve o arquivo.
    
  
6. Siga da etapa 9 à etapa 11 da seção "Criar um layout da página" de  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para verificar o status do arquivo, visualizar o layout da página e corrigir todos os erros.
    
  

### Para criar uma layout da página de categoria usando o Gerenciador de Design


1. Siga da etapa 1 à etapa 6 da seção "Criar um layout da página" de  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  
2. Na etapa 7, escolha o tipo de conteúdo **Página de Artigo**.
    
  
3. Escolha **OK**.
    
    Neste ponto, o SharePoint cria um arquivo HTML e um arquivo .aspx com o mesmo nome.
    
    No Gerenciador de Design, seu arquivo HTML aparece com uma coluna **Status**, que mostra um de dois status:
    
  - Erros
    
  
  - **Conversão bem-sucedida**
    
  
4. Usando o Windows Explorer, abra a unidade de rede mapeada para a Galeria de Páginas Mestras.
    
  
5. Para personalizar o layout da página de categoria, edite o arquivo HTML que reside diretamente no servidor usando um editor HTML para abrir e editar o arquivo HTML na unidade mapeada. Sempre que você salvar o arquivo HTML, todas as alterações serão sincronizadas com o arquivo .aspx associado.
    
  
6. Na marca **<head>**, substitua o espaço reservado de conteúdo com **id="PlaceHolderPageTitle"** por:
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

7. Localize o espaço reservado de conteúdo com **id="PlaceHolderPageTitleInTitleArea"** e substitua-o por:
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitleInTitleArea" runat="server">-->
<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

8. Substitua a marcação dentro do espaço reservado de conteúdo com **id="PlaceHolderMain"** pela marcação que você deseja usar no layout da página.
    
  
9. Para configurar e copiar o HTML para o Trecho de Pesquisa de Conteúdo e todos os outros trechos que você deseja adicionar à página, siga da etapa 1 à etapa 11 na seção "Inserir um trecho da Galeria de Trechos de Código" de  [Trechos de código do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
    > **OBSERVAçãO**
      > Ao adicionar o Trecho de Pesquisa de Conteúdo ao layout da página, altere a consulta para usar a fonte dos resultados criada quando você se conectou o site de publicação a um catálogo. Para saber mais, consulte  [Configurar fontes dos resultados para gerenciamento de conteúdo na Web no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj715262.aspx). 
10. Faça todas as outras alterações obrigatórias na marcação e então salve o arquivo.
    
  
11. Siga da etapa 9 à etapa 11 da seção "Criar um layout da página" de  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para verificar o status do arquivo, visualizar o layout da página e corrigir todos os erros.
    
  

## Noções básicas sobre marcação no layout da página de categoria HTML
<a name="bk_CategoryPageMarkup"> </a>

Quando você criar um layout da página, um arquivo .aspx será criado e usado pelo SharePoint, e alguma marcação HTML será adicionada à versão HTML do layout da página. Os layouts da página de categoria têm componentes de marcação adicionados ao layout da página com base no recurso Publicação de Coleção Entre Sites e que são exclusivos de layouts da página de categoria. Quando você editar o layout da página de categoria HTML em seu editor HTML, poderá ser útil compreender algumas dessas marcações.
  
    
    

### Título de página de janela do navegador

O componente que aparece dentro do espaço reservado de conteúdo com **id="PlaceHolderPageTitle"** contém marcação que diz ao SharePoint para usar uma propriedade de termo como o título da página na janela do navegador, em vez de usar o valor de campo de página padrão. O código a seguir mostra a marcação para o título da página da janela do navegador.
  
    
    

```HTML

<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
```


### Título da página

O componente que aparece dentro do espaço reservado de conteúdo com **id="PlaceHolderPageTitleInTitleArea"** contém marcação que diz ao SharePoint para usar uma propriedade de termo como o título da página na página, em vez de usar o trecho **SPTitleBreadcrumb** e o valor do campo de título de página padrão. O código a seguir mostra a marcação para o título da página.
  
    
    

```HTML

<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->"
```


### Trecho de Pesquisa de Conteúdo

Os componentes que aparecem após o trecho de conteúdo de página, dentro do espaço reservado de conteúdo com **id="PlaceHolderMain"**, contêm marcação para um Trecho de Zona de Web Part com quatro zonas de Web Part. A primeira zona de Web Part contém um Trecho de Pesquisa de Conteúdo que exibe uma Web Part de Pesquisa de Conteúdo na página. Esse trecho também contém informações que ajudam a Web Part de Pesquisa de Conteúdo a consultar uma fonte de resultados e a mostrar os resultados na página. As três últimas zonas de Web Part estão vazias. Se você optar por criar seu próprio layout da página de categoria, deverá incluir a marcação para o Trecho de Pesquisa de conteúdo no arquivo HTML para seu layout da página. O código a seguir mostra a marcação para o trecho de Pesquisa de Conteúdo. Substitua  _ResultSourceID_ pelo GUID da fonte de resultados e substitua _CatalogURL_ pela URL do catálogo.
  
    
    

> **OBSERVAçãO**
> Os GUIDs para **ID** e **__WebPartId** são gerados aleatoriamente pelo SharePoint quando os trechos são adicionados ao layout da página.
  
    
    


```HTML
<!--
CS: Start Content Search Snippet-->
<!--SPM:<%@Register Tagprefix="a781102493" Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<a781102493:ContentBySearchWebPart runat="server" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;&amp;#34;,&amp;#34;SourceID&amp;#34;
:&amp;#34;ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;
{'Tag':'{Term.IDWithChildren}','Scope':'CatalogURL'}&amp;#34;}" ResultsPerPage="3" RenderTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Control_ListWithPaging.js" 
ItemTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Item_PictureOnTop.js" SelectedPropertiesJson="[&amp;#34;WorkId&amp;#34;,&amp;#34;Rank&amp;#34;,&amp;#34;Title&amp;#34;,&amp;#34;Author&amp;#34;,&amp;#34;
Size&amp;#34;,&amp;#34;Path&amp;#34;,&amp;#34;Description&amp;#34;,&amp;#34;Write&amp;#34;,&amp;#34;CollapsingStatus&amp;#34;,&amp;#34;
HitHighlightedSummary&amp;#34;,&amp;#34;HitHighlightedProperties&amp;#34;,&amp;#34;ContentClass&amp;#34;,&amp;#34;
PictureThumbnailURL&amp;#34;,&amp;#34;ServerRedirectedURL&amp;#34;,&amp;#34;ServerRedirectedEmbedURL&amp;#34;,&amp;#34;
ServerRedirectedPreviewURL&amp;#34;,&amp;#34;FileExtension&amp;#34;,&amp;#34;ContentTypeId&amp;#34;,&amp;#34;ParentLink&amp;#34;,&amp;#34;
ViewsLifeTime&amp;#34;,&amp;#34;ViewsRecent&amp;#34;,&amp;#34;SectionNames&amp;#34;,&amp;#34;SectionIndexes&amp;#34;,&amp;#34;
SiteLogo&amp;#34;,&amp;#34;SiteDescription&amp;#34;,&amp;#34;deeplinks&amp;#34;,&amp;#34;importance&amp;#34;]" ShouldHideControlWhenEmpty="True" FrameType="None" SuppressWebPartChrome="False" Description="$Resources:Microsoft.Office.Server.Search,CBS_Description;" IsIncluded="True" 
ZoneID="" PartOrder="0" FrameState="Normal" AllowRemove="True" AllowZoneChange="True" 
AllowMinimize="True" AllowConnect="True" AllowEdit="True" AllowHide="True" IsVisible="True" 
DetailLink="" HelpLink="" HelpMode="Modeless" Dir="Default" PartImageSmall="" IsIncludedFilter="" ExportControlledProperties="True" ConnectionID="00000000-0000-0000-0000-000000000000" ID="g_54e35103_6f29_4dd9_b93b_8d4c863834af" ChromeType="None" ExportMode="All" __MarkupType="vsattributemarkup" __WebPartId="54e35103-6f29-4dd9-b93b-8d4c863834af" 
WebPart="true" Height="" Width="" Title="$Resources:cms,WebPartZoneTitle_Dynamic;">-->
<!--ME:</a781102493:ContentBySearchWebPart>-->
<!--CE: End Content Search Snippet-->

```


## Criar um layout da página de item de catálogo
<a name="bk_createCatItemPage"> </a>

Antes de poder criar ou personalizar um layout da página de item de catálogo, recomendamos que você crie uma unidade de rede mapeada que aponte para a Galeria de Páginas Mestras. Para saber mais, consulte  [Como: mapear uma unidade de rede para a Galeria de páginas mestras do SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    
Assim como acontece com o layout da página de categoria, a maneira mais simples de criar um layout da página de item de catálogo é permitir que o SharePoint crie o layout da página automaticamente, quando você conectar o site de publicação a um catálogo e então personalizar o layout da página de item de catálogo existente para adicionar outra marcação exigida pelo design da página. Como alternativa, você pode criar um layout da página de item de catálogo desde o início usando o Gerenciador de Design.
  
    
    

### Para personalizar um layout da página de item de catálogo existente que foi criado automaticamente pelo SharePoint


1. Usando o Windows Explorer, abra a unidade de rede mapeada para a Galeria de Páginas Mestras.
    
  
2. Para personalizar um layout da página de item de catálogo, edite o arquivo HTML que reside diretamente no servidor usando um editor HTML para abrir e editar o arquivo HTML na unidade mapeada. Sempre que você salvar o arquivo HTML, todas as alterações serão sincronizadas como arquivo .aspx associado.
    
  
3. Dentro do espaço reservado para conteúdo com **id="PlaceHolderMain"**, adicione a marcação que você deseja usar no layout da página.
    
  
4. Exclua todos os trechos que você não deseja usar no layout da página e mova os trechos restantes para locais na marcação onde deseja que os valores da propriedade apareçam.
    
    > **CUIDADO**
      > Por padrão, um Trecho de Zona de Web Parts que contenha um Trecho de Reutilização de Item de Catálogo é adicionado ao layout da página. Esse trecho contém o provedor de dados que retorna resultados da consulta usados por todos os outros trechos na página. Recomendamos que você mantenha o Trecho de Reutilização de Item de Catálogo nesse Trecho de Zona de Web Parts (é possível mover o Trecho de Reutilização de Item de Catálogo para fora da Zona de Web Parts e alterar a propriedade que ele exibe. Mas você deve manter o Trecho de Reutilização de Item de Catálogo no layout da página). Para saber mais, consulte  [Campos da página](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields), posteriormente neste artigo. 
5. Para configurar e copiar o trecho de HTML para todos os trechos que você deseja usar na página, siga da etapa 1 à etapa 11 da seção "Inserir um trecho da Galeria de Trechos de Código" de  [Trechos de código do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
6. Faça todas as outras alterações obrigatórias na marcação e então salve o arquivo.
    
  
7. Siga da etapa 9 à etapa 11 da seção "Criar um layout da página" de  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para verificar o status do arquivo, visualizar o layout da página e corrigir todos os erros.
    
  

### Para criar um layout da página de item de catálogo usando o Gerenciador de Design


1. Siga da etapa 1 à etapa 6 da seção "Criar um layout da página" de  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
    
  
2. Na etapa 7, escolha **Catálogo Remoto** e então escolha o catálogo que contém os dados que aparecerão na página.
    
  
3. Escolha **OK**.
    
    Neste ponto, o SharePoint cria um arquivo HTML e um arquivo .aspx com o mesmo nome.
    
    No Gerenciador de Design, seu arquivo HTML aparece com uma coluna **Status**, que mostra um de dois status:
    
  - Erros
    
  
  - **Conversão bem-sucedida**
    
  
4. Usando o Windows Explorer, abra a unidade de rede mapeada para a Galeria de Páginas Mestras.
    
  
5. Para personalizar um layout da página de item de catálogo, edite o arquivo HTML que reside diretamente no servidor usando um editor HTML para abrir e editar o arquivo HTML na unidade mapeada. Sempre que você salvar o arquivo HTML, todas as alterações serão sincronizadas como arquivo .aspx associado.
    
  
6. Dentro do espaço reservado para conteúdo com **id="PlaceHolderMain"**, adicione a marcação que você deseja usar no layout da página.
    
  
7. Exclua todos os trechos que você não deseja usar no layout da página e mova os trechos restantes para locais na marcação onde deseja que os valores da propriedade apareçam.
    
    > **CUIDADO**
      > Por padrão, um Trecho de Zona de Web Parts que contenha um Trecho de Reutilização de Item de Catálogo é adicionado ao layout da página. Esse trecho contém o provedor de dados que retorna resultados da consulta usados por todos os outros trechos na página. Recomendamos que você mantenha o Trecho de Reutilização de Item de Catálogo nesse Trecho de Zona de Web Parts (é possível mover o Trecho de Reutilização de Item de Catálogo para fora da Zona de Web Parts e alterar a propriedade que ele exibe. Mas você deve manter o Trecho de Reutilização de Item de Catálogo no layout da página). Para saber mais, consulte  [Campos da página](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields), posteriormente neste artigo. 
8. Para configurar e copiar o trecho de HTML para todos os trechos que você deseja usar na página, siga da etapa 1 à etapa 11 da seção "Inserir um trecho da Galeria de Trechos de Código" de  [Trechos de código do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  
9. Faça todas as outras alterações obrigatórias na marcação e então salve o arquivo.
    
  
10. Siga da etapa 9 à etapa 11 da seção "Criar um layout da página" de  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md) para verificar o status do arquivo, visualizar o layout da página e corrigir todos os erros.
    
  

## Noções básicas sobre marcação no layout da página de item de catálogo HTML
<a name="bk_CatItemMarkup"> </a>

Quando você criar um layout da página, um arquivo .aspx será criado e usado pelo SharePoint, e alguma marcação HTML será adicionada à versão HTML do layout da página. Os layouts da página de item catálogo têm componentes de marcação adicionados ao layout da página com base no recurso Publicação de Coleção Entre Sites e que são exclusivos de layouts da página de item de catálogo. Quando você editar o layout da página de item de catálogo HTML em seu editor HTML, poderá ser útil compreender algumas dessas marcações.
  
    
    

### Título de página de janela do navegador

O componente que aparece dentro do espaço reservado de conteúdo com **id="PlaceHolderPageTitle"** contém um Trecho de Reutilização de Item de Catálogo que diz ao SharePoint para usar o nome do item de catálogo como o título da página na janela do navegador, em vez de usar o valor de campo de página padrão. O código a seguir mostra a marcação para o título da página da janela do navegador.
  
    
    

> **OBSERVAçãO**
> Os GUIDs para **ID** e **__WebPartId** são gerados aleatoriamente pelo SharePoint quando os trechos são adicionados ao layout da página.
  
    
    


```HTML

<!--CS: [Title] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_863912c1_c849_46dc_8781_2920ee2bc83f" __WebPartId="{863912c1-c849-46dc-8781-2920ee2bc83f}">-->
<!--SPM:<RenderFormat>-->
<!--DC:Renders value from search without any additional formatting.-->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->

```


### Campos da página
<a name="bk_pagefields"> </a>

Os componentes que aparecem dentro do espaço reservado de conteúdo com **id="PlaceHolderMain"** contêm trechos para os campos **Title**, **Page Content** e **Catalog-Item URL**. Você pode excluir qualquer um desses códigos do layout da página. O código a seguir mostra a marcação para esses campos da página.
  
    
    

```HTML

<div>
    <!--CS: Start Page Field: Title Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldTextField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
        <!--MS:<PageFieldTextField:TextField FieldName="fa564e0f-0c70-4ab9-b863-0177e6ddd247" 
runat="server">-->
        <!--ME:</PageFieldTextField:TextField>-->
    <!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Page Field: Title Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Page Content Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldRichHtmlField:RichHtmlField FieldName="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" runat="server">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
            <div id="ctl02_label" style="display:none">Page Content</div>
            <div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label">
                <div align="left" class="ms-formfieldcontainer">
                    <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                        <span class="ms-formfieldlabel" nowrap="nowrap">Page Content</span>
                    </div>
                    <div class="ms-formfieldvaluecontainer">
                        <div class="ms-rtestate-field">Page Content field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
                    </div>
                </div>
            </div>
        <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
    <!--CE: End Page Field: Page Content Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Catalog-Item URL Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldCatalogSourceFieldControl" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl FieldName="75772bbf-0c25-4710-b52c-7b78344ad136" runat="server">-->
    <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
        <div align="left" class="ms-formfieldcontainer">
            <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                <span class="ms-formfieldlabel" nowrap="nowrap">Catalog-Item URL</span>
            </div>
            <div class="ms-formfieldvaluecontainer">
                <a href="http://www.example.com">Link to sample web site.</a>
            </div>
        </div>
    <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl>-->
    <!--CE: End Page Field: Catalog-Item URL Snippet-->
</div>

```

Se o layout da página de item de catálogo tiver sido criado automaticamente quando o site de publicação tiver sido conectado a um catálogo, ou tiver sido criado pela seção de um catálogo remoto durante a criação do layout da página, o layout da página também conterá um Trecho de Zona de Web Part com um Trecho de Reutilização de Item de Catálogo que registra um provedor de dados para a página. O Trecho de Reutilização de Item de Catálogo contém uma propriedade **UseSharedDataProvider**, que está definida como **False**. O Trecho de Zona de Web Part pode ser excluído do layout da página. Mas o Trecho de Reutilização de Item de Catálogo deve ser mantido na marcação do layout da página para a página exibir itens de catálogo. Quando você criar uma página que use esse layout da página, poderá configurar a Web Part para que ela fique oculta quando um usuário exibir a página.
  
    
    

> **IMPORTANTE**
> Se você criar um novo layout da página de item de catálogo e escolher um tipo de conteúdo em vez de um catálogo remoto, deverá incluir um Trecho de Reutilização de Item de Catálogo no layout da página. O código a seguir mostra a marcação para o Trecho de Reutilização de Item de Catálogo como ele aparece dentro do Trecho de Zona de Web Part. Substitua  _ManagedPropertyName_ pelo nome da propriedade gerenciada a ser exibida, substitua _ResultSourceID_ pelo GUID da fonte de resultados e substitua _CatalogURL_ pela URL do catálogo.
  
    
    




```HTML

<div>
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="cc1"  Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
    <!--MS:<WebPartPages:WebPartZone runat="server" Title="&amp;#60;%$Resources:cms,WebPartZoneTitle_Body%&amp;#62;" AllowPersonalization="False" FrameType="TitleBarOnly" ID="Body" Orientation="Vertical">-->
        <!--MS:<ZoneTemplate>-->
            <!--CS: [ManagedPropertyName] Start Catalog-Item Reuse Snippet-->
            <!--DC:To render the search property using a rendering template, change the "UseServerSideRenderFormat" property to "False".-->
            <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" AddSEOPropertiesFromSearch="True" LogAnalyticsViewEvent="True" UseSharedDataProvider="False" OverwriteResultPath="False" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;ListItemID:{URLTOKEN.1}&amp;#34;,&amp;#34;SourceID&amp;#34;:&amp;#34; ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;{&amp;#39;Scope&amp;#39;:&amp;#39;  CatalogURL&amp;#39;,&amp;#39;Tag&amp;#39;:&amp;#39;{Term}&amp;#39;}&amp;#34;}" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;ManagedPropertyName&amp;#34;]" Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" MissingAssembly="Cannot import this Web Part." ID="g_d63eebe7_207f_4e8c_9566_7381acc80cc7" __WebPartId="{d63eebe7-207f-4e8c-9566-7381acc80cc7}">-->
            <!--SPM:<RenderFormat>-->
            <!--DC:Renders value from search without any additional formatting.-->
            <!--SPM:</RenderFormat>-->
            <!--SPM:</cc1:CatalogItemReuseWebPart>-->
        <!--ME:</ZoneTemplate>-->
    <!--ME:</WebPartPages:WebPartZone>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

Se o layout da página de item de catálogo tiver sido criado automaticamente quando o site de publicação tiver sido conectado a um catálogo, ou tiver sido criado pela seleção de um catálogo remoto durante a criação do layout da página, o layout da página também conterá Trechos de Reutilização de Item de Catálogo que corresponderão a propriedades gerenciadas do catálogo no site de criação. Essas propriedades gerenciadas exibem os detalhes para o item de catálogo específico exibido usando o layout da página de item de catálogo. Esses Trechos de Reutilização de Item de Catálogo aparecem fora da zona de Web Part e são renderizados diretamente na página quando um item for escolhido em uma página de categoria. A Tabela 2 lista as propriedades gerenciadas que são automaticamente incluídas no layout da página de item de catálogo.
  
    
    

> **OBSERVAçãO**
> Algumas propriedades gerenciadas só serão incluídas se o catálogo for uma biblioteca Páginas. A coluna **Usada por** da Tabela 2 indica quais propriedades gerenciadas são usadas por uma biblioteca Página e uma lista e quais são usadas somente de uma biblioteca Páginas.
  
    
    


**Tabela 2. Trechos de Reutilização de Item de Catálogo de propriedades gerenciadas padrão**


|**Propriedade gerenciada**|**Descrição**|**Usada por**|
|:-----|:-----|:-----|
|**AuthorOWSUSER** <br/> |O nome do usuário que criou a página.  <br/> |Somente biblioteca de páginas  <br/> |
|**CreatedOWSDATE** <br/> |A data em que o item de página ou de lista foi criado.  <br/> |Biblioteca e lista de páginas  <br/> |
|**EditorOWSUSER** <br/> |O nome do usuário que alterou o item de página ou de lista pela última vez.  <br/> |Biblioteca e lista de páginas  <br/> |
|**ListItemID** <br/> |A ID do item de página ou de lista.  <br/> |Biblioteca e lista de páginas  <br/> |
|**ModifiedOWSDATE** <br/> |A data em que o item de página ou de lista foi alterado pela última vez.  <br/> |Biblioteca e lista de páginas  <br/> |
|**PublishingContactOWSUSER** <br/> |Contato é uma coluna do site criada pelo recurso Publicação. É usado no Tipo de Conteúdo da Página como a pessoa ou o grupo que é a pessoa de contato para a página.  <br/> |Somente biblioteca de páginas  <br/> |
|**PublishingIsFurlPageOWSBOOL** <br/> |Um valor Booliano que indica se a página está associada a uma URL amigável.  <br/> |Somente biblioteca de páginas  <br/> |
|**PublishingPageContentOWSHTML** <br/> |O conteúdo HTML da página.  <br/> |Somente biblioteca de páginas  <br/> |
|**PublishingPageLayoutOWSURLH** <br/> |A URL do layout da página usado para criar a página.  <br/> |Somente biblioteca de páginas  <br/> |
|**Title** <br/> |O título do item de página ou de lista.  <br/> |Biblioteca e lista de páginas  <br/> |
   
As propriedades gerenciadas para colunas personalizadas que você adiciona à biblioteca ou lista Páginas também são incluídas em Trechos de Reutilização de Item de Catálogo. O nome da propriedade gerenciada vai variar com base no tipo de coluna do site usado quando você criar a coluna do site. Para saber mais, consulte  [Propriedades gerenciadas criadas automaticamente no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj613136.aspx) e [Visão geral do esquema de pesquisa no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj219669.aspx).
  
    
    

> **IMPORTANTE**
> A coluna do site **Page Image** em uma biblioteca Páginas é mapeada para a propriedade gerenciada **PublishingImage**. Mas a propriedade gerenciada **PublishingImage** não é automaticamente incluída no layout da página de item de categoria. Para incluir a imagem no seu layout da página, você deverá adicionar um Trecho de Reutilização de Item de Catálogo para a propriedade gerenciada **PublishingImage**. Use o HTML a seguir para adicionar um Trecho de Reutilização de Item de Catálogo para exibir o valor da propriedade gerenciada **PublishingImage** em seu layout da página. Substitua _UniqueID_ por um GUID que seja exclusivo de cada instância do trecho.
  
    
    




```HTML

<div>
<!--CS: [PublishingImage] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingImage&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_UniqueID" __WebPartId="{UniqueID}">-->
<!--SPM:<RenderFormat>-->
<!--SPM:<Format Type="HTML"> -->
<!--SPM:<Picture>-->True<!--SPM:</Picture>-->
<!--SPM:</Format> -->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

Se você criar um novo layout da página de item de catálogo usando o Gerenciador de Design e se escolher um tipo de conteúdo em vez de um catálogo remoto, poderá adicionar Trechos de Reutilização de Item de Catálogo usando a Galeria de Trechos de Código. O código a seguir mostra a marcação para os Trechos de Reutilização de Item de Catálogo para as propriedades gerenciadas **Title**, **PublishingPageContentOWSHTML**, **CreatedOWSDATE** e **owstaxIdPageCategory**.
  
    
    

> **OBSERVAçãO**
> Os GUIDs para **ID** e **__WebPartId** são gerados aleatoriamente pelo SharePoint quando os trechos são adicionados ao layout da página.
  
    
    




```HTML

<div>
    <!--CS: [Title] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_0dc23bb8_8d34_4f9f_8085_5a6ac286cb9e" 
__WebPartId="{0dc23bb8-8d34-4f9f-8085-5a6ac286cb9e}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [PublishingPageContentOWSHTML] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingPageContentOWSHTML&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_25253a49_a9a6_4277_bf9d_416961024cee" 
__WebPartId="{25253a49-a9a6-4277-bf9d-416961024cee}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [CreatedOWSDATE] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;CreatedOWSDATE&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." 
ID="g_4e1f180b_12f8_4e50_84d7_c72b0ee3793f" 
__WebPartId="{4e1f180b-12f8-4e50-84d7-c72b0ee3793f}">-->
    <!--SPM:<RenderFormat>-->
    <!--SPM:<Format Type="DateTime"> -->
    <!--DC:To render Date and Time, change this value to False.-->
    <!--SPM:<DateOnly>-->True<!--SPM:</DateOnly>-->
    <!--SPM:</Format> -->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [owstaxIdPageCategory] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;owstaxIdPageCategory&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_22e39e9d_1b25_42c7_bf2a_7ebca37616d4" 
__WebPartId="{22e39e9d-1b25-42c7-bf2a-7ebca37616d4}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```


## Recursos adicionais
<a name="bk_addresources"> </a>


-  [Desenvolver o design do site do SharePoint 2013](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [Visão geral do Gerenciador de Design no SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [Visão geral do modelo de página do SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [Modelos de exibição do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-display-templates.md)
    
  

