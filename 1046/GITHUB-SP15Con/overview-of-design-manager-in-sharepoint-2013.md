---
title: Visão geral do Gerenciador de Design no SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 29834b3f-3815-4347-91d3-296387663114
---


# Visão geral do Gerenciador de Design no SharePoint 2013
Obtenha uma visão geral de como usar o Gerenciador de Design para definir a marca do seu site SharePoint 2013. O Gerenciador de Design é um recurso de publicação que está disponível em sites de publicação no SharePoint Server 2013 e no Office 365. Você também pode usar o Gerenciador de Design para criar a marca do site público no Office 365.
## Introdução ao Gerenciador de Design
<a name="Introduction"> </a>

Se quiser que seu site SharePoint 2013 represente a marca da sua organização e não "se pareça com o SharePoint", você poderá criar um design personalizado e usar o Gerenciador de Design para alcançar esse objetivo. O Gerenciador de Design é um recurso no SharePoint 2013 que facilita a criação de um design totalmente personalizado, design de pixel perfeito, além de usar as ferramentas de design da Web com as quais você já está familiarizado. O Gerenciador de Design é um recurso de publicação que está disponível em sites de publicação no SharePoint Server 2013 e no Office 365. Você também pode usar o Gerenciador de Design para criar a marca do site público no Office 365.
  
    
    
Com o Gerenciador de Design, você pode criar um design visual para seu site usando qualquer ferramenta de design da Web ou editor de HTML que preferir, usando apenas HTML e CSS, e, em seguida, carregar esse design no SharePoint. O Gerenciador de Design é o hub central e a interface onde você gerencia todos os aspectos de um design personalizado.
  
    
    
Criar o design visual de um site geralmente se encaixa em um processo maior, que envolve várias pessoas ou organizações. Para um mapa das tarefas de uma perspectiva maior, confira  [Design e identidade visual no SharePoint 2013](http://go.microsoft.com/fwlink/?LinkId=262838)
  
    
    
Em um nível alto, o designer executará as seguintes tarefas:
  
    
    

- Compreender os principais conceitos de design do SharePoint. Para saber mais, confira  [Visão geral do modelo de página do SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md).
    
  
- Criar um modelo de design em HTML e CSS. Criar o design é a habilidade principal de um designer da Web e não está descrita neste artigo.
    
  
- Implementar o design usando o Gerenciador de Design. As seções deste artigo fornecem uma introdução ao Gerenciador de Design e o processo de usar o Gerenciador de Design para implementar um design visual.
    
  

> **OBSERVAçãO**
> Os elementos de design que você pode criar para um site público no SharePoint Online são diferentes dos elementos de design para outros sites de publicação. Além disso, você não pode criar pacotes de design na versão do Gerenciador de Design que está disponível no site público no SharePoint Online. 
  
    
    


## Use o Gerenciador de Design para implementar um design
<a name="Use"> </a>

Quando você usa o Gerenciador de Design, vê uma série de links no lado esquerdo que representam as tarefas de alto nível que você precisa executar. Dependendo de seu design e dos requisitos do seu site, talvez você não precise executar todas essas tarefas e não precise necessariamente realizá-las nesta ordem. Ainda assim, essa sequência é um ponto de partida útil.
  
    
    

### Antes de começar

Antes de poder usar o Gerenciador de Design, você precisa de um design. Você pode criar seu próprio ou usar um modelo de sites prontos. Um "design" é simplesmente um grupo de arquivos que implementam o design visual do seu site, mais comumente:
  
    
    

- Pelo menos um arquivo HTML que será convertido em uma página mestra do SharePoint
    
  
- Um ou mais arquivos CSS
    
  
- Arquivos JavaScript
    
  
- Imagens
    
  
- Outros arquivos de suporte
    
  
À medida que você compõe o seu site em HTML e CSS, provavelmente terá vários arquivos HTML que implementam designs para definir como deseja que as diferentes páginas ou tipos de páginas apareçam. Lembre-se de que apenas um desses arquivos HTML será convertido na página mestra, a menos que você tenha vários canais de dispositivo, onde cada canal tem sua própria página mestra. Confira a seção a seguir. Após usar o Gerenciador de Design para criar outros elementos do site, como layouts de página ou modelos de exibição, você poderá transferir a marcação de suas maquetes de HTML aos arquivos HTML e CSS associados ao modelo de tela ou layout de página.
  
    
    
Antes de começar, você também precisa das permissões do SharePoint necessárias. Para usar o Gerenciador de Design, você deverá ter o nível de permissão de Designer.
  
    
    

### Gerenciar canais de dispositivo

Mesmo antes de criar seu site, considere a quais dispositivos seu site deve se destinar e qual será a experiência do usuário em cada dispositivo. Por exemplo, você talvez queira otimizar o design do seu site para uma determinada classe de smartphones ou tablets.
  
    
    
Dependendo de quais canais você define, poderá desejar vários designs e, portanto, vários arquivos HTML, onde cada arquivo é convertido em uma página mestra separada. Além disso, cada arquivo HTML (e, portanto, cada página mestra) pode fazer referência a seu próprio arquivo CSS. Antes de criar seu site, os canais de dispositivo são uma das primeiras coisas a considerar.
  
    
    
Com os canais de dispositivo, você pode renderizar um único site de publicação de várias maneiras, mapeando diferentes designs para dispositivos diferentes. Cada canal pode ter sua própria página mestra que se vincula a uma folha de estilos que é otimizada para um dispositivo específico. Cada canal especifica as subcadeias de caracteres de agente de usuário para um ou mais dispositivos, como "Windows Phone OS". Essas são as regras que determinam quais dispositivos estão incluídos em cada canal. Em seguida, quando os visitantes navegarem em seu site, cada canal capturará o tráfego para seu dispositivo ou classe de dispositivos especificado, como telefones com Windows, e os visitantes verão seu site em um design otimizado para o dispositivo.
  
    
    
Os canais de dispositivo são criados e armazenados em uma lista do SharePoint na qual a ordem tem importância, porque os canais de dispositivo também têm classificações. Os canais de dispositivo na lista são ordenados de cima para baixo, e as regras de inclusão são processadas nessa ordem. Isso significa que você quer canais de dispositivo com as regras mais específicas no alto. Por exemplo, um canal direcionado para "Windows Phone SO 7.0" deve preceder um canal direcionado para "Windows Phone SO".
  
    
    

### Carregar arquivos de design

Quando você cria um design, pode usar qualquer editor de HTML que preferir e trabalhar com arquivos localmente em seu computador. Mas, eventualmente, você precisará carregar esses arquivos na Galeria de Páginas Mestras do seu site do SharePoint, para poder usar o Gerenciador de Design para converter, visualizar e refinar seu design.
  
    
    
A maneira mais fácil de carregar e continuar a trabalhar em arquivos de design é mapear uma unidade em seu computador para a Galeria de Páginas Mestras do site do SharePoint. Isso conecta uma pasta em seu computador à Galeria de Páginas Mestras, para que você possa trabalhar em arquivos que residem no servidor no SharePoint 2013 como se fossem arquivos locais.
  
    
    
Depois de mapear uma unidade de rede, você poderá carregar seu design no SharePoint simplesmente copiando os arquivos de design para uma pasta na unidade mapeada do seu computador que está conectado ao SharePoint. Após converter seu arquivo HTML a uma página mestra do SharePoint e depois criar layouts de página e exibir modelos que cada um tem seu próprio arquivo HTML associado, você poderá continuar a editar os arquivos HTML associados no editor de HTML no computador. Sempre que você salvar um arquivo na unidade mapeada, o SharePoint sincronizará automaticamente os arquivos em seu computador com a Galeria de Páginas Mestras. Você pode criar sua própria estrutura de pastas na unidade mapeada, e essa estrutura é mantida pelo SharePoint e aparece na Galeria de Páginas Mestras. Você deve manter todos os arquivos relacionados a um design em uma única pasta e copiar essa pasta para a unidade mapeada quando estiver pronto para carregar seu design.
  
    
    
Para saber mais, confira  [Como: mapear uma unidade de rede para a Galeria de páginas mestras do SharePoint 2013](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md).
  
    
    

### Editar página mestras

Criar uma página mestra totalmente com marca que contém todas as funcionalidades do SharePoint que você quer, como navegação e pesquisa, é basicamente um processo de três etapas:
  
    
    

1. Converter um arquivo HTML em uma página mestra do SharePoint.
    
  
2. Visualizar a página mestra e corrigir os problemas.
    
  
3. Adicionar trechos do SharePoint à página mestra.
    
  
Cada uma dessas três etapas é executada em uma página diferente no Gerenciador de Design.
  
    
    

#### Converter um arquivo HTML

O principal recurso do Gerenciador de Design é que ele converte seu design HTML em uma página mestra do SharePoint. Para renderizar com sucesso, uma página mestra do SharePoint deverá conter muitos elementos ASP.NET e elementos que são específicos do SharePoint. Ao converter um arquivo HTML em uma página mestra, o Gerenciador de Design cria um arquivo .master que contém todos esses elementos necessários, para que você não precise conhecê-los. Durante a conversão, algumas marcações de HTML (por exemplo, comentários) também são adicionadas ao seu arquivo HTML original.
  
    
    
Após a conversão, seu arquivo HTML e a página mestra do SharePoint estarão associados, para que, quando você editar e salvar o arquivo HTML na sua unidade mapeada, a página mestra será atualizada automaticamente. No Gerenciador de Design, a página mestra em HTML tem uma propriedade chamada **Arquivo Associado** que determina se as alterações no arquivo HTML estão sincronizadas com o arquivo .master.
  
    
    

> **OBSERVAçãO**
> O Gerenciador de Design também fornece uma opção para iniciar seu design usando uma página mestra mínima. Nesse cenário, você não precisa começar com um design HTML; pode criar uma página mestra em HTML que contém os elementos de página mínimos necessários para renderizar a página mestra corretamente no SharePoint e depois construir o design editando a página mestra em HTML. 
  
    
    


#### Visualizar a página mestra

Além de converter sua página mestra, o Gerenciador de Design fornece uma visualização do lado do servidor (versus a visualização em tempo de design em seu editor de HTML), para que você possa obter uma visualização dinâmica da sua página mestra e corrigir os problemas que podem impedir a página de renderizar. Por exemplo, seu arquivo HTML deve ser compatível com XML, por isso, você talvez precise corrigir problemas de marcação secundários como o fornecimento de marcas de fechamento para todos os elementos. Para corrigir qualquer problema, edite o arquivo HTML, salve-o e, em seguida, atualize a visualização do lado do servidor.
  
    
    
Quando você visualiza uma página mestra, pode usar a opção **Página de visualização de alteração** no canto superior esquerdo para visualizar a página mestra junto com qualquer página existente, ou crie uma nova página para visualizar com ela. Diferentemente a visualização de tempo de design da página mestra HTML em um editor HTML, essa visualização do servidor é uma visualização em tempo real totalmente funcional; portanto, convém editar o arquivo HTML, salvá-lo para que as alterações mais recentes sejam sincronizadas com o arquivo .master associado e atualizar a visualização dinâmica e ver as últimas alterações de design no navegador.
  
    
    

#### Adicionar trechos de código

Depois de converter sua página mestra e visualizá-la com êxito, você estará pronto para adicionar trechos de código à página mestra. Um trecho de código é uma representação de HTML de um componente do SharePoint (como uma caixa de pesquisa ou controle de navegação ou Web Part) que você pode adicionar à sua página mestra. Adicionar trechos de código à sua página mestra é como se cria rapidamente a funcionalidade de intervalo total do SharePoint em sua página mestra. Adicionar trechos de código é basicamente um processo de três etapas:
  
    
    

1. Localize e configure trechos de código na Galeria de Trechos de Código.
    
  
2. Copie trechos de código para sua página mestra em HTML.
    
  
3. Visualize e crie trechos de código usando CSS.
    
    Para saber mais, confira  [Trechos de código do Gerenciador de Design do SharePoint 2013](sharepoint-2013-design-manager-snippets.md).
    
  

#### Localizar e configurar trechos de código na Galeria de Trechos de Código

A Galeria de Trechos de Código é onde você pode ver rapidamente quais componentes estão disponíveis para o tipo de arquivo que você está editando, seja uma página mestra ou layout da página. Na faixa de opções, selecione um trecho de código. Na grade de propriedades no lado direito, você pode configurar as propriedades para essa instância de um trecho de código e escolher **atualização** para atualizar o trecho de código HTML à esquerda.
  
    
    

#### Copiar trechos de código para sua página mestra em HTML

Depois de configurar um trecho de código, você poderá copiá-lo para a área de transferência e colá-lo no ponto certo no seu arquivo HTML. Seu design HTML pode já conter uma maquete ou controles estáticos e, nesse caso, convém excluí-los ou comentá-los quando os substituir por trechos dinâmicos da Galeria de Trechos de Código.
  
    
    

#### Visualizar e criar trechos de código usando CSS

Depois de copiar trechos de código em seu arquivo HTML e salvar as alterações, atualize a visualização do servidor da página mestra para ver como o controle é processado. Os trechos contêm marcação que fornece uma visualização de tempo de design em um editor de HTML, mas a visualização do servidor mostra uma visualização de fidelidade total com dados dinâmicos, por exemplo, um controle de navegação mostrará a estrutura de navegação atual do site com dados dinâmicos da sua fonte de dados.
  
    
    
Por padrão, a maioria dos trechos herdam estilos da folha de estilos principal do SharePoint 2013, corev15.css. Para formatar um trecho de código, você precisará identificar quais estilos são aplicados ao trecho de código e depois substituí-los por CSS personalizado. Para identificar esses estilos padrão, você poderá usar uma ferramenta de navegador, como as ferramentas de desenvolvedor no Internet Explorer. Enquanto exibe a página mestra na visualização do lado do servidor no Internet Explorer, pressione **F12**, escolha **Localizar** e, em seguida, **Selecionar elemento por clique**. Isso permite que você clique no trecho de código e veja exatamente quais estilos deve substituir adicionando CSS a todas as folhas de estilos personalizada às quais sua página mestra se vincula.
  
    
    

### Editar modelos de exibição

Se você estiver usando uma instalação no local do SharePoint Server, poderá usar a Web Part de pesquisa de conteúdo e outras Web Parts orientadas por pesquisa para exibir os resultados de consultas de pesquisa como conteúdo em suas páginas. Web Parts orientadas por pesquisa usam modelos de exibição para duas finalidades principais:
  
    
    

- Para mapear as propriedades gerenciadas que são retornadas em itens de resultado da pesquisa para propriedades que estarão disponíveis para JavaScript, incluindo os JavaScripts personalizados que você escolheu implementar.
    
  
- Para usar HTML e CSS para apresentar e criar o estilo de como essas propriedades são exibidas.
    
  
Com páginas mestras e layouts de página, você pode editar um arquivo HTML associado, mas não o arquivo .master ou .aspx. De maneira semelhante, os modelos de exibição são feitos de um arquivo HTML e um arquivo .js associado, onde você pode editar o arquivo HTML. Cada vez que você salva esse arquivo HTML, o SharePoint atualiza automaticamente o arquivo .js associado.
  
    
    
Quando você deseja criar um modelo de exibição personalizado, deve começar copiando e modificando um dos modelos de exibição existentes. Isso é útil porque os modelos de exibição padrão contêm informações em comentários nos arquivos HTML, e você terá a estrutura de página básica correta e uma estrutura para tarefas básicas, como mapear os campos de entrada.
  
    
    

### Editar layouts de página

O processo de criação de um layout de página é um pouco diferente do processo de criação de uma página mestra. Para uma página mestra, comece com um design HTML, converta-o em uma página mestra do SharePoint e, em seguida, continue a editar o arquivo HTML associado. Mas para um layout de página, primeiro crie o layout de página no Gerenciador de Design, que cria um arquivo .aspx e um arquivo HTML, e edite o arquivo HTML associado da unidade mapeada no editor de HTML. O motivo para usar o Gerenciador de Design para criar um layout de página é para o conjunto correto de campos de página ser adicionado ao layout da página.
  
    
    
Quando você cria um layout de página, seleciona uma página mestra para visualizar o layout da página e seleciona um tipo de conteúdo de Layout de página. Um tipo de conteúdo é um esquema de campos e tipos de dados, e os campos disponíveis no tipo de conteúdo de layout de página determinam quais controles de campo de página estão disponíveis no layout de página que você cria. Você cria um layout de página no navegador primeiro para que os campos de página possam ser adicionados.
  
    
    
Depois que você criar um layout de página com seu arquivo HTML associado, as etapas restantes serão as mesmas que para uma página mestra:
  
    
    

- Visualize o layout de página e corrija os problemas editando e salvando a versão HTML.
    
  
- Adicione trechos de código ao layout de página (configurar, copiar, visualizar, criar o estilo).
    
  
Na Galeria de Trechos de Código, trechos diferentes estão disponíveis para páginas mestras e layouts de página, e a faixa de opções exibe somente os trechos de código que são relevantes para esse tipo de arquivo. Por exemplo, os trechos de código de navegação e caixa de pesquisa estão disponíveis apenas para uma página mestra, enquanto os campos de página só estão disponíveis em um layout de página.
  
    
    
Quando você cria um layout de página, sua tarefa básica é posicionar e criar os estilos dos controles de campo da página que exibirão o conteúdo criado por autores de conteúdo. Os estilos de um layout de página podem residir em qualquer folha de estilos à qual a página mestra se vincula, ou cada layout de página pode se vincular a sua própria folha de estilo específico. Se seu design HTML inclui conteúdo mais adequado para um layout de página do que uma página mestra, você deve transferir esse conteúdo da sua página mestra em HTML e, em seguida, aplicar esses estilos aos controles e elementos corretos do layout da página relevante.
  
    
    
Para saber mais, confira  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md).
  
    
    

### Criar temas e visuais compostos

No site público no Office 365, mas não nas instalações locais do SharePoint Server 2013, o Gerenciador de Design tem a opção de criar temas e visuais compostos. Um tema é um conjunto de fontes e cores que podem ser aplicadas a um design personalizado (ou seja, uma página mestra). Temas são definidos nos arquivos .xml que você carrega na galeria de temas. Se você quiser que uma página mestra personalizada seja habilitada para tema, é necessário adicionar marcação especial à página mestra que o SharePoint reconhece e usa para inserir elementos de tema como fontes e cores.
  
    
    
Uma aparência composta é apenas uma associação entre uma imagem de fundo, um tema (ou seja, fontes e cores) e um design (ou seja, uma página mestra). Uma aparência composta usa elementos de design predefinidos, como temas, imagens de plano de fundo e páginas mestras, e permite que sejam usados em muitas combinações diferentes, para que o site público tenha muitas outras opções de personalização.
  
    
    

### Publicar e aplicar design

A maioria dos ativos usados pelo seu design, como imagens, HTML, CSS e arquivos de JavaScript residirão na Galeria de Páginas Mestras. A Galeria de Páginas Mestras é uma biblioteca de documentos do SharePoint que, por padrão, tem controle de versão ativado, o que cria versões principais e secundárias (rascunho) cada vez que você edita um arquivo.
  
    
    
Antes de aplicar o design em um site, primeiro você precisa publicar uma versão principal de cada arquivo ou ativo usado pelo seu design. Se você estiver criando o seu site em um ambiente de teste, deverá desativar o controle de versão para a Galeria de Páginas Mestras, para que você não precise se lembrar de publicar todos os arquivos antes de visualizar o site. Mas isso não é uma prática recomendada, se você estiver criando um site ao vivo.
  
    
    
Depois de publicar todos os arquivos de design, você estará pronto para aplicar o design, atribuindo suas páginas mestras concluídas ao seu site. Cada site pode ter uma página mestra diferente atribuída a cada canal de dispositivo, e esta página do Gerenciador de Design é onde você aplica uma página mestra a um canal.
  
    
    

### Criar um pacote de design

Um pacote de design é uma maneira fácil de coletar todos os arquivos e ativos usados pelo seu design, exportá-los de um site, importá-los para outro site e aplicar o design ao novo site. Se você implementa e refine seu design em um conjunto de sites de teste e quiser implantá-lo em um conjunto de sites ao vivo, poderá usar um pacote de design para transferir seu design.
  
    
    
Um pacote de design é um arquivo .wsp, um arquivo de solução do SharePoint, que é basicamente um tipo especial de arquivo .cab. Quando você cria ou importa um pacote de design, o arquivo .wsp é armazenado na Galeria de soluções. Após importar um pacote de design, o pacote é ativado automaticamente. Se as páginas mestras e os layouts de página foram publicados antes de terem sido empacotados, e se as páginas mestras foram atribuídas a canais de dispositivo antes de terem sido empacotadas, o design será automaticamente aplicado ao site quando o pacote de design for implantado. Caso contrário, para aplicar o design ao novo site, você só precisará publicar os arquivos de design e aplicar as páginas mestras por canal de dispositivo.
  
    
    

> **OBSERVAçãO**
> Pacotes de design não estão disponíveis no site público no Office 365. Para implementar um design totalmente personalizado com o Gerenciador de Design, você poderá convidar um designer em seu site, concedendo temporariamente a essa pessoa o nível de permissão de Designer. 
  
    
    


## Recursos adicionais
<a name="Additional"> </a>


-  [Visão geral do modelo de página do SharePoint 2013](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [Como: converter um arquivo HTML em uma página mestra no SharePoint 2013](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [Tutorial: criar um layout de página no SharePoint 2013](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  

