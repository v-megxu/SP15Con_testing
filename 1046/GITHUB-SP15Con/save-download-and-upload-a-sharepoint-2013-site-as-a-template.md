---
title: Salvar, baixar e carregar um site do SharePoint 2013 como um modelo
ms.prod: SHAREPOINT
ms.assetid: 2e637172-ddac-4a70-bd77-55a1645a3db1
---


# Salvar, baixar e carregar um site do SharePoint 2013 como um modelo
Saiba como projetar e criar aplicativos robustos usando modelos de site do SharePoint.
Você pode projetar e criar aplicativos robustos do SharePoint 2013 que incluem um valioso conjunto de fontes de dados, exibições e formulários voltados para o cliente, fluxos de trabalho altamente personalizados e mais. Depois de criar seu site de solução de negócios, você poderá começar a usá-lo imediatamente em seu ambiente do SharePoint. Ou pode transformar sua solução em um modelo e implantá-la em outro ambiente, disponibilizá-la para usuários para que eles possam criar novos sites a partir dela ou enviá-la para desenvolvimento adicional no Visual Studio.
  
    
    


## O que é um modelo de site do SharePoint?
<a name="bkmk_WhatIsTemplate"> </a>

Os modelos de site do SharePoint são definições pré-compiladas projetadas de acordo com uma necessidade comercial em particular. Você pode usar esses modelos como estão para criar seu próprio site do SharePoint e então personalizar o site o quanto desejar. Provavelmente, você já conhece os modelos de site padrão, como o Site de Equipe, o Site de Projeto e o Site de Comunidades.
  
    
    
Além dos modelos padrão, você pode criar seu próprio modelo de site com base em um site criado e personalizado. Esse é um recurso poderoso que permite a você criar uma solução personalizada e então compartilhar a solução com seus colegas, com a organização ou com outras organizações. Também é possível empacotar o site e abri-lo em outro ambiente ou aplicativo, como o Visual Studio, e também personalizá-lo ali.
  
    
    
Transformar seu site personalizado ou sua solução de negócios em um modelo é um recurso extremamente útil e muito poderoso. Depois de começar a empacotar sua solução como um modelo, você começa a perceber o potencial do SharePoint como uma plataforma para aplicativos de negócios. A opção de modelo de site torna tudo isso possível.
  
    
    
Quando você salva seu site como um modelo, cria um Web Solution Package, ou WSP. Um WSP é um arquivo CAB que usa o manifesto de solução. A solução criada é armazenada na galeria de soluções para o conjunto de sites do SharePoint. Depois de salvar o modelo, um arquivo de solução (.wsp) é criado e armazenado na galeria de soluções onde você pode baixar e ativar a solução.
  
    
    

> **OBSERVAçãO**
> O WSP criado é uma solução de usuário de confiança parcial com o mesmo formato declarativo de uma solução de confiança total do SharePoint. Entretanto, ele não dá suporte a todos os tipos de elementos de recurso com suporte das soluções de confiança total. 
  
    
    


### O que é salvo em um modelo?

Quando você salva um site do SharePoint como um modelo, está salvando a estrutura geral do site  suas listas e bibliotecas, exibições e formulários e fluxos de trabalho. Além desses componentes, você pode incluir o conteúdo do site no modelo; por exemplo, os documentos armazenados nas bibliotecas de documentos. Isso poderia ser útil para fornecer conteúdo de exemplo para usuários para começar. Considere que isso também pode aumentar o tamanho do modelo além do limite de modelo de site padrão de 50 MB.
  
    
    
A maioria dos objetos em um site é incluída e tem suporte no modelo. Entretanto, há vários objetos e recursos sem suporte. 
  
    
    

- **Com suporte** Listas, bibliotecas, listas externas, conexões de fonte de dados, exibições de lista e exibições de dados, formulários personalizados, fluxos de trabalho, tipos de conteúdo, ações personalizadas, navegação, páginas de site, páginas mestras, módulos e modelos da Web.
    
  
- **Sem suporte** Permissões personalizadas, instâncias de fluxo de trabalho em execução, histórico de versão de item de lista, tarefas de fluxo de trabalho associadas com fluxos de trabalho em execução, valores de campo de pessoas ou de grupo, valores de campo de taxonomia, páginas de publicação e sites de publicação, Meus Sites, recursos grampeados, Suplementos do SharePoint e receptores de evento remoto.
    
    > **OBSERVAçãO**
      > Para sites de publicação, você pode usar modelos de definição de site. Para saber mais, consulte  [Recursos adicionais](save-download-and-upload-a-sharepoint-2013-site-as-a-template.md#bkmk_additionalresources) no final deste tópico.

### O que você pode fazer com modelos do SharePoint?

Salvar um site como um modelo é um recurso poderoso porque oferece diferentes usos de sites personalizados. Estes são os benefícios imediatos que você obtém do salvamento de um site como um modelo:
  
    
    

- **Implantar soluções imediatamente** Salve e ative o modelo na galeria de soluções e permita que outros funcionários criem novos sites a partir do modelo. Você pode selecioná-lo e então criar um novo site a partir dele, que herdará os componentes do site, sua estrutura, fluxos de trabalho e mais. Você não precisa que o Visual Studio crie sua solução e é necessário acessar o servidor diretamente e executar comandos de administrador de servidor. Basta salvar o site como um modelo, ativá-lo e pronto.
    
  
- **Portabilidade** Além de implantar uma solução personalizada em seu ambiente, você poderá baixar o arquivo .wsp, colocá-lo em funcionamento e implantá-lo em outro ambiente do SharePoint. Toda a personalização do seu site é convenientemente armazenada em um arquivo.
    
  
- **Extensibilidade** Assim como acontece com um Web Solution Package, você pode abrir seu site personalizado no Visual Studio, execute personalização de desenvolvimento adicional para o modelo e então implante-o no SharePoint. O desenvolvimento de sites do SharePoint, como resultado, pode passar por um ciclo de vida da solução (desenvolvimento, preparação e produção) que inclui o SharePoint Designer 2013, o Visual Studio e o navegador.
    
  
À medida que você começará a criar sites personalizados no SharePoint, descobrirá ainda mais benefícios de transformar seu site em uma solução que possa se tornar portável em sua organização. As etapas básicas para o trabalho com modelos de site são as seguintes:
  
    
    

- Salvar um site como um modelo para a galeria de soluções.
    
  
- Baixar o modelo de site da galeria de soluções para um arquivo .wsp.
    
  
- Carregue o arquivo .wsp na galeria de soluções.
    
  
Depois de adicionar um modelo de site à galeria de soluções e que o modelo for ativado, na próxima vez em que um site ou subsite for criado, o modelo estará disponível para seleção na guia **Personalizado** da seção **Seleção de Modelo** na página **Novo Site do SharePoint**.
  
    
    

## Salvar um site como um modelo para a galeria de soluções
<a name="bkmk_SaveTemplate"> </a>


1. Navegue até o site de nível superior do seu conjunto de sites.
    
  
2. Clique em **Configurações** e então clique em **Configurações do Site**.
    
  
3. Na seção **Ações do Site**, clique em **Salvar site como modelo**.
    
  
4. Especifique um nome a ser usado para o arquivo de modelo na caixa **Nome do arquivo**.
    
  
5. Especifique um nome e uma descrição para o modelo nas caixas **Nome do modelo** e **Descrição do modelo**.
    
  
6. Para incluir o conteúdo do site no modelo de site, selecione a caixa **Incluir Conteúdo**.
    
    > **OBSERVAçãO**
      > A inclusão do conteúdo do site pode aumentar o tamanho do modelo significativamente. O limite de tamanho padrão para um modelo de site é de 50 MB, mas pode ser menor em sua organização. Você sempre poderá excluir o conteúdo e então copiar o que for necessário mais tarde para o novo site. Ou você pode aumentar o limite de tamanho. Por exemplo, para aumentar o limite até o máximo permitido, use a sintaxe do comando Stsadm a seguir. >  `stsadm -o setproperty -pn max-template-document-size -pv 524288000`
7. Clique em **OK** para salvar o modelo.
    
    Se todos os componentes do site forem válidos, o modelo será criado e você verá uma mensagem que diz "Operação Concluída com Êxito".
    
  
8. Siga um destes procedimentos:
    
  - Para voltar para seu site, clique em **OK**.
    
  
  - Para ir diretamente para o modelo de site, clique em **Galeria de Soluções**.
    
  

## Baixar o modelo de site da galeria de soluções para um arquivo
<a name="bkmk_DownloadTemplate"> </a>


1. Navegue até o site de nível superior do seu conjunto de sites.
    
  
2. Clique em **Configurações** e então clique em **Configurações do Site**.
    
  
3. Na seção **Galerias de Web Designer**, clique em **Soluções**.
    
  
4. Se for necessário ativar a solução, selecione-a e, no grupo **Comandos**, clique em **Ativar**. Em seguida, na tela **Confirmação de Ativação de Solução**, no grupo **Comandos**, clique em **Ativar**.
    
  
5. Para baixar a solução, clique em seu nome na galeria de soluções e clique em **Salvar**. Em seguida, na caixa de diálogo **Salvar como**, navegue até o local onde deseja salvar a solução, clique em **Salvar** e, em seguida, clique em **Fechar**.
    
  

## Carregar o arquivo do modelo de site para uma galeria de soluções
<a name="bkmk_UploadTemplate"> </a>


1. Navegue até o site de nível superior do seu conjunto de sites.
    
  
2. Clique em **Configurações** e então clique em **Configurações do Site**.
    
  
3. Na seção **Galerias de Web Designer**, clique em **Soluções**.
    
  
4. Para carregar a solução, no grupo **Comandos**, clique em **Upload** e, então, na caixa de diálogo **Adicionar um Documento**, clique em **Procurar**. Em seguida, na caixa de diálogo **Escolher Arquivo para Upload**, localize o arquivo, selecione-o, clique em **Abrir** e então clique em **OK**.
    
  
5. Para ativar a solução, na tela de confirmação de ativação de solução, no grupo **Comandos**, clique em **Ativar**.
    
  

## Recursos adicionais
<a name="bkmk_additionalresources"> </a>


-  [Tipos de site: modelos da Web e definições de site](http://msdn.microsoft.com/pt-br/library/ms434313.aspx)
    
  
-  [Noções básicas sobre como empacotar e implantar um fluxo de trabalho no SharePoint 2013](http://msdn.microsoft.com/pt-br/library/jj819316%28v=office.15%29.aspx)
    
  
-  [Criar soluções de farm no SharePoint 2013](http://msdn.microsoft.com/pt-br/library/jj163902%28v=office.15%29.aspx)
    
  
-  [Copiar e mover listas usando modelos de lista](http://office.com/redir/HA101782479.aspx)
    
  
-  [Copiar ou mover uma biblioteca usando um modelo de biblioteca](http://office.com/redir/HA101814157.aspx)
    
  
-  [Copiar ou mover arquivos de biblioteca usando o Windows Explorer](http://office.com/redir/HA101811182.aspx)
    
  

