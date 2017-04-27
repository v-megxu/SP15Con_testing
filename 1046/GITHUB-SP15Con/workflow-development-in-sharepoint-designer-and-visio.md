---
title: Desenvolvimento de fluxos de trabalho no SharePoint Designer e no Visio
ms.prod: SHAREPOINT
ms.assetid: 496780d5-47d6-4a43-bf14-70aefb8d820c
---


# Desenvolvimento de fluxos de trabalho no SharePoint Designer e no Visio
Saiba como usar o Visio 2013 e o SharePoint Designer 2013 para criar e publicar fluxos de trabalho em um site do SharePoint 2013 sem precisar de qualquer código.
## Introdução
<a name="VSSPD_Intro"> </a>

O Visio 2013 e o SharePoint Designer 2013 facilitam a colaboração e a criação de fluxos de trabalho do para analistas de negócios, consultores de processos e profissionais de TI. O Visio Professional 2013 e o Visual Designer no SharePoint Designer 2013 oferecem uma rica representação de fluxos de trabalho em um formato compreensível para programadores e não programadores.
  
    
    

> **OBSERVAçãO**
> Para obter orientação sobre a instalação e a configuração do SharePoint Server 2013 e do servidor do Workflow Manager, consulte  [Configurar fluxos de trabalho no SharePoint Server 2013](http://technet.microsoft.com/pt-br/library/jj658586.aspx). 
  
    
    

Usando o Visio 2013, você pode criar visualmente um fluxo de trabalho do SharePoint, exportar o fluxo de trabalho para o SharePoint Designer 2013 e então publicá-lo em um site do SharePoint. Após a criação de um fluxo de trabalho no Visio 2013, ele deverá ser exportado para o SharePoint Designer 2013. Em seguida, um proprietário de site ou profissional de TI adiciona parâmetros ao fluxo de trabalho usando o editor de texto do fluxo de trabalho ou o novo Visual Workflow Designer, que é um controle ActiveX do Visio 2013 hospedado no SharePoint Designer 2013. Após a conclusão do fluxo de trabalho, ele poderá ser publicado no site do SharePoint.
  
    
    
Isso é ideal para analistas de negócios e consultores de processos que já conheçam os fluxogramas do Visio, porque permite a eles projetar um fluxo de trabalho que represente a lógica de negócios. A pessoa que projetar o fluxo de trabalho poderá se concentrar somente nas necessidades de BI (business intelligence) do fluxo de trabalho, sem precisar ser um especialista em fluxos de trabalho declarativos.
  
    
    

## Sobre a criação de fluxos de trabalho do SharePoint no Visio 2013 e no SharePoint Designer 2013
<a name="VSSPD_About"> </a>

O Visio 2013 inclui um modelo Fluxo de Trabalho do SharePoint 2013, que pode ser usado para criar fluxos de trabalho do SharePoint 2013. O modelo Fluxo de Trabalho do SharePoint 2013 está associado a três estênceis: Ações de Fluxo de Trabalho do SharePoint 2013, Condições de Fluxo de Trabalho do SharePoint 2013 e Terminadores de Fluxo de Trabalho do SharePoint 2013. As formas desses estênceis correspondem a ações e condições específicas que podem ser usadas em um fluxo de trabalho SharePoint 2013. Para criar um fluxo de trabalho, você só precisará arrastar formas para a tela de desenho no Visio 2013 para modelar a lógica de negócios por trás do fluxo de trabalho.
  
    
    

### Estágios, loops e etapas

Agora, os fluxos de trabalho no SharePoint Designer 2013 incluem as noções de estágios, loops eetapas. Os autores de fluxo de trabalho podem agrupar algumas ações e condições individuais como uma única unidade para que o processo seja definido mais claramente. Por exemplo, pode haver um estágio ou uma etapa de Aprovação ou de Comentários sobre a Solicitação. Nesse estágio ou etapa haveria todas as ações necessárias ao processo. O próprio estágio ou etapa poderia ser um nó de um fluxo de trabalho mais longo e poderia permitir que um visualizador visse o status desse estágio como um todo, em vez de um conjunto de ações individuais.
  
    
    
O modelo Fluxo de Trabalho incluído no SharePoint 2013 também usa estágios, loops e etapas como blocos de construção lógicos para a criação de um fluxo de trabalho.Visio 2013. 
  
    
    

> **IMPORTANTE**
> Por causa das diferenças subjacentes entre o modelo Fluxo de Trabalho do Microsoft SharePoint 2010 e do modelo Fluxo de Trabalho do SharePoint 2013, você não pode usar formas de um modelo em um diagrama criado pelo outro. Somente as formas dos estênceis Ações de Fluxo de Trabalho do SharePoint 2013, Condições de Fluxo de Trabalho do SharePoint 2013 e Terminadores de Fluxo de Trabalho do SharePoint 2013 podem ser usados para criar um fluxo de trabalho do SharePoint 2013. 
  
    
    


### Formas de estágio

Um estágio pode conter qualquer número de formas e pode incluir ramificações. Entretanto, só pode haver um caminho de entrada para um estágio (e para uma etapa) e um caminho de saída dele. Todas as ações no fluxo de trabalho deverão estar contidos por um estágio. As formas de estágio são visualizadas usando formas de contêiner. Uma forma Estágio exige que uma forma Entrar e uma Sair sejam adicionadas às bordas do contêiner para definir os caminhos de entrada e de saída do estágio. O Visio 2013 e o Visual Designer no SharePoint Designer 2013 adicionam as formas Entrar e Sair quando você soltar o contêiner pela primeira vez.
  
    
    
Os estágios também têm as seguintes regras:
  
    
    

- Todos os diagramas devem ter pelo menos um estágio. Um estágio, concluído com as formas Entrar, Saída e Iniciar estão presentes como parte do modelo Fluxo de Trabalho padrão do SharePoint 2013.
    
  
- Quando você adicionar um novo estágio à tela de desenho, o Visio 2013 adicionará os conectores Iniciar e Fim quando o estágio for solto.
    
  
- Os estágios não podem ter conectores entrando ou saindo de outras formas que não sejam Entrar e Sair.
    
  
- Os contêineres de estágio não podem ser aninhados. Se quiser aninhar outro subprocesso em um estágio, use uma etapa.
    
  
- Formas Parar Fluxo de Trabalho podem existir em um estágio.
    
  
- Uma forma Iniciar explícita é necessária fora do estágio para o diagrama inteiro. Uma forma Terminar explícita fora do estágio não é obrigatória.
    
  
- No nível superior, o fluxo de trabalho pode conter somente estágios, formas condicionais e terminadores Iniciar e Terminar. Todas as outras formas deverão estar contidas em um estágio.
    
  

### Formas de loop

Os loops são uma série de formas conectadas que serão executadas como um loop, voltando da última forma na série para a primeira, até que uma condição seja satisfeita. 
  
    
    
Assim como os estágios, os loops são representados por uma forma de contêiner que inclui uma forma Entrar e Sair (adicionada quando a forma é solta na tela de desenho). Uma forma Loop também exige que uma forma Entrar e Sair seja adicionada às bordas do contêiner para definir os caminhos de entrada e de saída do loop.
  
    
    
O Visio 2013 e o SharePoint Designer 2013 dão suporte a dois tipos de loops: loop  *n*  vezes e loop até *valor1*  igual a *valor2*  .
  
    
    
Os loops também devem estar em conformidade com as seguintes regras:
  
    
    

- Os loops devem estar em um estágio e os estágios não podem estar em um loop.
    
  
- As etapas podem estar em um loop.
    
  
- Os loops só poderão ter um ponto de entrada e um ponto de saída.
    
  

### Formas de etapa

As etapas representam uma série agrupada de ações sequenciais. As etapas devem estar contidas em um estágio. Uma forma de etapa também deve ter uma forma Entrar e Sair para definir os caminhos de entrada e de saída da forma. Ambas as formas são adicionadas por padrão quando a forma for solta na tela.
  
    
    

## Criando um fluxo de trabalho no Visio 2013
<a name="VSSPD_Creating"> </a>

Todas as formas mestras nos estênceis de Fluxo de Trabalho SharePoint 2013 correspondem a ações, condições e outras construções lógicas em um fluxo de trabalho do SharePoint 2013. Para criar um fluxo de trabalho, você arrastar formas para a tela de desenho, da mesma forma como qualquer outro fluxograma no Visio. Depois de ter concluído a construção do fluxo de trabalho no Visio 2013, salve o fluxo de trabalho antes que o SharePoint Designer 2013 possa abri-lo.
  
    
    
Para abrir o modelo Fluxo de Trabalho do SharePoint 2013 no Visio 2013, faça o seguinte:
  
    
    

### Para abrir o modelo Fluxo de Trabalho do SharePoint 2013 no Visio 2013


1. Abra o Visio 2013.
    
  
2. Escolha **Novo**.
    
  
3. Em **Categorias de Modelo**, escolha **Fluxograma**.
    
  
4. Em **Escolher um Modelo**, escolha **SharePoint 2013 Fluxo de Trabalho** e então escolha **Criar**.
    
    O modelo abre e a tela de desenho é pré-preenchida com formas Iniciar e Estágio. A forma Estágio contém uma forma Entrar e uma Sair, unidas por um único conector.
    
  
Com o modelo Fluxo de Trabalho do SharePoint 2013 aberto, arraste ações, condições e outras formas para a tela de desenho para projetar um fluxo de trabalho. Para saber mais sobre formas individuais e o que elas significam, consulte o artigo  [Formas no modelo de fluxo de trabalho do SharePoint Server 2013 no Visio 2013](shapes-in-the-sharepoint-server-workflow-template-in-visio.md).
  
    
    

> **DICA**
>  Ao projetar um fluxo de trabalho, mantenha as considerações adicionais a seguir em mente:>  Para criar rapidamente um fluxo de trabalho, solte formas de ação e de condição no conector interno contido por novas formas de estágio. O Visio 2013 divide automaticamente o conector em conectores adicionais, mantendo o fluxo de trabalho conectado da forma Entrar para a forma Sair.>  Não use nenhuma forma de um estêncil diferente das Ações do Fluxo de Trabalho do SharePoint 2013, Condições de Fluxo de Trabalho do SharePoint 2013 e Terminadores de Fluxo de Trabalho do SharePoint 2013. Use somente a ferramenta Conector fornecida pelo modelo Fluxo de Trabalho do SharePoint 2013 para adicionar conexões entre as formas. Todas as outras formas de conector não são válidas em um fluxo de trabalho do SharePoint 2013.>  As formas, as etapas e os loops de ação sempre deverão estar contidos em uma forma Estágio. Algumas formas condicionais podem estar fora de um estágio.>  Uma forma Estágio deve ter exatamente uma forma Entrar e uma forma Sair. O subprocesso de fluxo de trabalho contido no estágio deverá começar com a forma Entrar e terminar com a forma Sair.>  Uma forma de condição deve ter dois conectores deixando a forma, um rotulado como "Sim" e o outro rotulado como "Não". Você pode clicar com o botão direito de um conector para escolher **Sim** ou **Não**. >  Um fluxo de trabalho deve ter somente uma forma Iniciar. A forma Iniciar deve estar fora de um estágio.>  Você adiciona texto às formas no fluxo de trabalho, mas o texto da forma não afetará o fluxo de trabalho.
  
    
    


  
    
    
Validar o fluxo de trabalho no Visio 2013 é como validar qualquer outro diagrama conectado: o Visio verifica o diagrama em relação a um conjunto de regras e retorna uma lista de erros encontrados no diagrama. Consulte o artigo  [Como solucionar problemas de erros de validação de fluxo e trabalho do SharePoint Server 2013 no Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md) para saber como resolver problemas de validação.
  
    
    

### Para validar um fluxo de trabalho do SharePoint 2013 no Visio 2013


1. Na guia **Processo**, no grupo **Validação de Diagrama**, escolha **Verificar Diagrama**.
    
  
2. Se qualquer erro for encontrado no fluxo de trabalho, o painel **Problemas** abre abaixo do diagrama. Escolha cada item na lista para selecionar a forma no diagrama que causou o erro.
    
  
3. Resolva cada erro de validação listado na lista **Problemas**. Assim que todos os erros tiverem sido tratados, escolha **Verificar Diagrama** novamente. Para saber mais sobre como resolver problemas de validação no Visio 2013, consulte o artigo [Como solucionar problemas de erros de validação de fluxo e trabalho do SharePoint Server 2013 no Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md).
    
  
4. Se nenhum erro for encontrado no fluxo de trabalho, o Visio exibirá uma mensagem declarando que a validação de diagrama foi concluída e que nenhum problema foi encontrado.
    
  
Depois que o fluxo de trabalho tiver sido validado com êxito no Visio 2013, você poderá salvar o arquivo e importá-lo para o SharePoint Designer 2013. Ao contrário do modelo Fluxo de Trabalho do Microsoft SharePoint 2010, poderá salvar uma cópia do diagrama Fluxo de Trabalho do SharePoint 2013 como o formato de arquivo padrão do Visio 2013 (.vsdx) e o SharePoint Designer 2013 poderá abrir o arquivo. 
  
    
    
Use o procedimento a seguir para salvar um fluxo de trabalho do SharePoint 2013 no Visio 2013 como um arquivo .vsdx do Visio 2013 que pode ser aberto no SharePoint Designer 2013:
  
    
    

### Para salvar um fluxo de trabalho no Visio 2013


1. Escolha **Arquivo** e então escolha **Salvar como**.
    
  
2. Em **Salvar como**, escolha **Salvar** e então escolha **Procurar**.
    
  
3. Na caixa de diálogo **Salvar como**, selecione um local para salvar o arquivo e digite um nome para o arquivo ("Meu Fluxo de Trabalho SP").
    
  
4. Escolha **Salvar**.
    
  

## Personalizando e publicando um fluxo de trabalho no SharePoint Designer 2013
<a name="VSSPD_Customizing"> </a>

Depois de criar a lógica de negócios subjacente para um fluxo de trabalho do SharePoint 2013 no Visio 2013 e de salvar o diagrama, você poderá abrir o arquivo .vsdx do Visio no SharePoint Designer 2013 e começar a ajustar o fluxo de trabalho para seu site do SharePoint 2013. O pacote do arquivo .vsdx contém documentos XML que o SharePoint Designer 2013 pode traduzir em fluxos de trabalho.
  
    
    
Use o procedimento a seguir para abrir um site do SharePoint 2013 no SharePoint Designer 2013.
  
    
    

### Para abrir um site do SharePoint 2013 no SharePoint Designer 2013


1. Abra o SharePoint Designer 2013.
    
  
2. Em **Abrir Site do SharePoint**, escolha **Abrir Site**.
    
  
3. Na caixa de diálogo **Abrir Site**, selecione o site que você deseja abrir.
    
  
4. Escolha **Abrir**.
    
  
Quando o site do SharePoint 2013 estiver aberto, você poderá abrir o diagrama .vsdx do Visio 2013 no SharePoint Designer 2013.
  
    
    

### Para abrir um fluxo de trabalho do Visio Professional 2013 no SharePoint Designer 2013


1. Escolha **Arquivo** e então escolha **Adicionar Item**.
    
  
2. Parar criar um Fluxo de Trabalho de Lista, faça o seguinte:
    
1. Em **Fluxos de Trabalho**, escolha **Fluxo de Trabalho de Lista**.
    
  
2. No painel esquerdo em **Fluxo de Trabalho de Liste**, digite um nome para seu fluxo de trabalho (Meu Primeiro Fluxo de Trabalho do SP2013) e selecione a lista no site em que você deseja publicar o fluxo de trabalho.
    
  
3. Na lista **Escolher a plataforma de fluxo de trabalho para o novo fluxo de trabalho**, selecione **Fluxo de Trabalho do SharePoint 2013**.
    
  
4. Escolha **Criar**.
    
  
3. Para criar um Fluxo de Trabalho de Site, faça o seguinte:
    
1. Em **Fluxos de Trabalho**, escolha **Fluxo de Trabalho de Site**.
    
  
2. No painel esquerdo, em **Fluxo de Trabalho de Site**, digite um nome para seu fluxo de trabalho (Meu Primeiro Fluxo de Trabalho do SP2013).
    
  
3. Na lista **Escolher a plataforma de fluxo de trabalho para o novo fluxo de trabalho**, selecione **Fluxo de Trabalho do SharePoint 2013**.
    
  
4. Escolha **Criar**.
    
  
4. Na guia **Fluxo de Trabalho**, no grupo **Gerenciar**, escolha **Configurações de Fluxo de Trabalho**.
    
  
5. Na guia **Configurações de Fluxo de Trabalho**, no grupo **Gerenciar**, escolha **Importar do Visio.**
    
  
6. Na caixa de diálogo **Importar Fluxo de Trabalho de Desenho do Visio**, navegue até onde o arquivo .vsdx esteja localizado.
    
  
7. Selecione o arquivo que você deseja abrir (Meu Fluxo de Trabalho SP) e então escolha **Abrir**.
    
  
Quando você abrir um arquivo .vsdx no SharePoint Designer 2013, o arquivo será exibido no Visual Designer, um controle ActiveX do Visio hospedado no SharePoint Designer. O diagrama do Visio 2013 mantém todas as formas e o texto da forma criado no Visio. 
  
    
    

> **OBSERVAçãO**
> Para alternar entre o Visual Designer e o Designer Declarativo no SharePoint Designer 2013, na guia **Fluxo de Trabalho**, no grupo **Gerenciar**, escolha **Modos de Exibição**. Esse processo pode demorar alguns instantes, já que o SharePoint Designer 2013 valida o fluxo de trabalho e então converte as informações de fluxo de trabalho de um formato para outro. Durante esse processo, outra validação no nível da forma ocorrerá. Se qualquer erro for detectado no diagrama, os erros serão exibidos em um painel de erro na parte inferior da tela (como acontece no Visio). 
  
    
    

As formas exibidas no Visual Designer também tem Marcas de Ação (mostradas por um ícone de tipo de configurações de fluxo de trabalho no lado esquerdo inferior da forma). Quando você escolher uma Marca de Ação, um menu suspenso exibe os atributos para essa ação ou condição no fluxo de trabalho e a propriedade **Propriedades**. Essas propriedades definirão os valores de parâmetro a serem usados para a ação: de quais listas serão retirados os itens, qual operador de cálculo usar ou para qual endereço de email enviar uma mensagem. Quando você escolher uma propriedade exibida na lista, aparecerá uma caixa de diálogo na qual você poderá personalizar as configurações dessa propriedade. 
  
    
    
Por exemplo, a forma **Enviar um email** tem duas propriedades associadas a ela: **Criar Email** e **Propriedades**. Quando você escolher **Criar Email**, uma caixa de diálogo **Definir Mensagem de Email** aparecerá e você poderá criar a mensagem a ser enviada pela ação. Se você escolher **Propriedades**, uma caixa de diálogo **Propriedades de Enviar um Email** aparecerá e exibirá todos os parâmetros da ação.
  
    
    

> **OBSERVAçãO**
> Para saber mais sobre ações e formas individuais e suas propriedades, consulte os artigos  [Formas no modelo de fluxo de trabalho do SharePoint Server 2013 no Visio 2013](shapes-in-the-sharepoint-server-workflow-template-in-visio.md) e [Referência rápida de ações de fluxo de trabalho (plataforma de Fluxo de Trabalho do SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md). 
  
    
    

Depois de definir as propriedades no fluxo de trabalho e quando estiver pronto para publicar, primeiro você deverá verificar o fluxo de trabalho em busca de erros no SharePoint Designer 2013. Quando você escolher **Publicar** na guia **Visual Designer** na faixa de opções, o SharePoint Designer 2013 verificará automaticamente o fluxo de trabalho em busca de erros. Se quiser, você também poderá iniciar manualmente a verificação de erros.
  
    
    
Use o procedimento a seguir para verificar o fluxo de trabalho do SharePoint 2013 no SharePoint Designer 2013:
  
    
    

### Para verificar manualmente um fluxo de trabalho em busca de erros no SharePoint Designer 2013


1. Na guia **Visual Designer**, no grupo **Salvar**, escolha **Verificar Erros**.
    
  
2. Se qualquer erro for encontrado no fluxo de trabalho, o painel **Questões** abre abaixo da tela do Visual Designer. Escolha cada item na lista para selecionar a ação, a condição, o conector, o terminador ou o contêiner no fluxo de trabalho que causou o erro.
    
  
3. Resolva cada erro de validação apresentado na lista de **Questões**. Assim que todos os erros tiverem sido verificados, escolha **Verificar Erros** novamente.
    
  
4. Se nenhum erro for encontrado no fluxo de trabalho, o SharePoint Designer exibirá uma mensagem declarando que nenhum problema foi encontrado no fluxo de trabalho.
    
  
Depois que o fluxo de trabalho tiver sido verificado e de nenhum erro tiver sido encontrado, você poderá publicar o fluxo de trabalho na lista do SharePoint. Para publicar o fluxo de trabalho do SharePoint Designer 2013, na guia **Visual Designer**, no grupo **Salvar**, escolha **Publicar**. Se ocorrer um erro durante o processo de publicação, o SharePoint Designer 2013 retornará para o Visual Designer e exibirá os erros no painel **Questões**.
  
    
    

## Recursos adicionais
<a name="VSSPD_Additional"> </a>

Para saber mais, consulte os seguintes recursos:
  
    
    

-  [Referência rápida de ações de fluxo de trabalho (plataforma de Fluxo de Trabalho do SharePoint 2013)](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [Formas no modelo de fluxo de trabalho do SharePoint Server 2013 no Visio 2013](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)
    
  
-  [Como solucionar problemas de erros de validação de fluxo e trabalho do SharePoint Server 2013 no Visio 2013](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)
    
  
-  [Criar, importar e exportar fluxos de trabalho do SharePoint no Visio 2010](http://office.microsoft.com/pt-br/visio-help/create-import-and-export-sharepoint-workflows-in-visio-HA101888007.aspx)
    
  
-  [Central de desenvolvedores do SharePoint](http://msdn.microsoft.com/pt-br/sharepoint/default.aspx)
    
  
-  [Central de desenvolvedores do Visio](http://msdn.microsoft.com/pt-br/office/aa905478)
    
  

