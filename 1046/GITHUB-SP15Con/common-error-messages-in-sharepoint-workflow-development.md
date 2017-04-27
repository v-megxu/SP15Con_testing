---
title: Mensagens de erro comuns no desenvolvimento de fluxo de trabalho do SharePoint
ms.prod: SHAREPOINT
ms.assetid: e9bf6878-c722-4b1f-b5b5-b302ae0ea4da
---


# Mensagens de erro comuns no desenvolvimento de fluxo de trabalho do SharePoint
Uma listagem de mensagens de erro comuns que podem ser encontradas durante o desenvolvimento de fluxos de trabalho do SharePoint e orientação para a resolução do problema subjacente.
## Erros comuns no fluxo de trabalho do SharePoint

Embora esta lista não aborde todos os erros possíveis que podem ser encontrados durante o desenvolvimento de fluxos de trabalho do SharePoint, ela aborda os mais prováveis.
  
    
    

-  [Tempo limite atingido durante espera pela conclusão de solicitação de execução de código em área restrita dentro do processo de trabalho](#bkmk_error01)
    
  
-  [Tempo limite atingido durante espera pela conclusão de solicitação no domínio do aplicativo em área restrita](#bkmk_error02)
    
  
-  [O processo de trabalho que estava manipulando esta solicitação foi encerrado porque excedeu o recurso {0}](#bkmk_error03)
    
  
-  [Não foi possível executar este fluxo de trabalho porque uma solução em área restrita encontrou um erro](#bkmk_error04)
    
  
-  [Não foi possível executar este fluxo de trabalho porque a área restrita falhou: não foi possível obter um processo do pool de p](#bkmk_error05)
    
  
-  [Não foi possível executar este fluxo de trabalho porque a área restrita falhou: o processo de trabalho do código em área restrita foi finalizado inesperadamente](#bkmk_error06)
    
  
-  [Não é possível enviar a mensagem de email. Verifique se as configurações de email de saída para o servidor foram definidas corretamente](#bkmk_error07)
    
  
-  [O fluxo de trabalho não conseguiu atualizar o item, possivelmente porque uma ou mais colunas do item exijam um tipo diferente de informação](#bkmk_error08)
    
  
-  [A operação do fluxo de trabalho falhou porque a pesquisa do fluxo de trabalho não encontrou um item correspondente](#bkmk_error09)
    
  
-  [O fluxo de trabalho não conseguiu criar o item de lista porque o nome do arquivo está ausente ou é inválido](#bkmk_error10)
    
  
-  [Falha de Coerção: não foi possível transformar os dados de pesquisa de entrada no tipo solicitado](#bkmk_error11)
    
  
-  [A operação do fluxo de trabalho falhou porque a ação exige o check-out do documento](#bkmk_error12)
    
  
-  [Foram encontrados erros durante a compilação do fluxo de trabalho. Os arquivos do fluxo de trabalho foram salvos mas não podem ser executados. Erro inesperado no servidor que está associando o fluxo de trabalho](#bkmk_error13)
    
  

### Tempo limite atingido durante espera pela conclusão de solicitação de execução de código em área restrita dentro do processo de trabalho
<a name="bkmk_error01"> </a>

Mesmo problema e mesma solução do item abaixo, "Tempo limite atingido durante espera pela conclusão de solicitação no domínio do aplicativo em área restrita".
  
    
    

### Tempo limite atingido durante espera pela conclusão de solicitação no domínio do aplicativo em área restrita
<a name="bkmk_error02"> </a>

Ambos os erros resultam do mesmo problema  exceder o período de tempo limite padrão para a execução da ação do fluxo de trabalho. O período de tempo limite padrão é de 30 segundos.
  
    
    
É possível alterar o valor do tempo limite em instalações locais, mas não é possível alterá-lo em instalações do SharePoint Online. Para evitar esse erro em instalações do SharePoint Online, modifique seu código para limitar ações no processo de trabalho e no domínio do aplicativo a menos de 30 segundos.
  
    
    
Para modificar o período de tempo limite em sua instalação local, execute o comando do Windows PowerShell a seguir. Observe que o código de exemplo redefine o tempo limite para 60 segundos, mas é possível usar outro valor.
  
    
    



```

Add-pssnapin microsoft.sharepoint.powershell
   $userCodeSvc = [Microsoft.SharePoint.Administration.SPUserCodeService]::Local
   #change to 60 second timeout
   $userCodeSvc.WorkerProcessExecutionTimeout = 60 
   $userCodeSvc.Update()
```


### O processo de trabalho que estava manipulando esta solicitação foi encerrado porque excedeu o recurso {0}
<a name="bkmk_error03"> </a>

Na cadeia de conexão do erro, o valor  `{0}` é um espaço reservado para o recurso específico cujo limite foi excedido. Para sanar esse problema, modifique se código para que ele não exceda o limite do recurso. Esses valores de recurso estão documentados em [Limites de uso de recursos em soluções em áreas restritas no SharePoint 2010](http://msdn.microsoft.com/pt-br/library/gg615462%28v=office.14%29.aspx).
  
    
    

### Não foi possível executar este fluxo de trabalho porque uma solução em área restrita encontrou um erro
<a name="bkmk_error04"> </a>

O código do fluxo de trabalho lançou uma exceção sem tratamento. a resolução desse erro exige depuração e revisão do código em área restrita.
  
    
    

### Não foi possível executar este fluxo de trabalho porque a área restrita falhou: não foi possível obter um processo do pool de p
<a name="bkmk_error05"> </a>

Houve um erro em sua configuração de área restrita. Para saber mais sobre a configuração de uma solução de área restrita, consulte  [Soluções de área restrita no SharePoint](http://msdn.microsoft.com/pt-br/library/ee536577%28v=office.14%29.aspx).
  
    
    

### Não foi possível executar este fluxo de trabalho porque a área restrita falhou: o processo de trabalho do código em área restrita foi finalizado inesperadamente
<a name="bkmk_error06"> </a>

Houve um erro em sua configuração de área restrita. Para saber mais sobre a configuração de uma solução de área restrita, consulte  [Soluções de área restrita no SharePoint](http://msdn.microsoft.com/pt-br/library/ee536577%28v=office.14%29.aspx).
  
    
    

### Não é possível enviar a mensagem de email. Verifique se as configurações de email de saída para o servidor foram definidas corretamente
<a name="bkmk_error07"> </a>

Há dois problemas que devem ser observados durante a solução de problemas de email. Nas instalações locais e do SharePoint Online, verifique se todos os endereços nas linhas **Para:** e **Cc:** são endereços de email válidos. Nas instalações locais, verifique se as configurações de email no servidor foram definidas corretamente.
  
    
    
Examine o seguinte para garantir que você configurou corretamente os emails de entrada e de saída.
  
    
    

-  [Guia de implantação do Microsoft SharePoint 2013](http://download.microsoft.com/download/1/F/6/1F6D3BE4-1174-4320-A1D1-C0E2681CCCF3/Deployment-guide-for-SharePoint-2013.pdf)
    
  
-  [Como configurar emails de entrada e de saída no SharePoint Server](http://blogs.msdn.com/b/pareshg/archive/2010/04/23/how-to-configure-incoming-and-outgoing-emails-in-sharepoint-server-2010.aspx)
    
  

### O fluxo de trabalho não conseguiu atualizar o item, possivelmente porque uma ou mais colunas do item exijam um tipo diferente de informação
<a name="bkmk_error08"> </a>

Esse erro normalmente é resultado de uma destas duas situações:
  
    
    

- Um dos campos da lista foi removido ou alterado, mas o fluxo de trabalho não foi atualizado para refletir a alteração e, portanto, está tentando definir um valor para o campo antigo. Marque todas as ações **Atualizar Item de Lista** em seu fluxo de trabalho para garantir que eles estejam definindo os valores apropriados para os campos e que esses campos existam na lista.
    
  
- Há um erro de tipo de dados onde o fluxo de trabalho está tentando definir um valor em um campo no item de lista usando o tipo de dados errado. Confirme se a operação **Retornar Campo como** na pesquisa é do tipo de dados correto.
    
  

### A operação do fluxo de trabalho falhou porque a pesquisa do fluxo de trabalho não encontrou um item correspondente
<a name="bkmk_error09"> </a>

Indica que há um erro na lógica do fluxo de trabalho. Verifique se você está selecionando a lista e o campo corretos em sua pesquisa.
  
    
    

### O fluxo de trabalho não conseguiu criar o item de lista porque o nome do arquivo está ausente ou é inválido
<a name="bkmk_error10"> </a>

Indica que há um erro na lógica do fluxo de trabalho. Verifique se o nome do arquivo inserido no campo **Caminho e Nome** é um nome de arquivo válido. Os motivos comuns para que um nome do arquivo seja inválido incluem uma extensão de arquivo ausente ou incorreta ou uma cadeia de caracteres de arquivo/caminho muito longa e que excede o número de caracteres permitido.
  
    
    

### Falha de Coerção: não foi possível transformar os dados de pesquisa de entrada no tipo solicitado
<a name="bkmk_error11"> </a>

A operação falhou ao converter valores entre tipos de dados incompatíveis (por exemplo, converter uma cadeia de caracteres aleatória em um valor Date/Time). Verifique as configurações de **Retornar Campo como** em sua pesquisa para garantir que ele seja de um tipo de dados válido para os dados esperados.
  
    
    

### A operação do fluxo de trabalho falhou porque a ação exige o check-out do documento
<a name="bkmk_error12"> </a>

É necessário fazer check-out do item usando a ação **Fazer Check-out do Item** antes de usar a ação **Atualizar Item**.
  
    
    

### Foram encontrados erros durante a compilação do fluxo de trabalho. Os arquivos do fluxo de trabalho foram salvos mas não podem ser executados. Erro inesperado no servidor que está associando o fluxo de trabalho
<a name="bkmk_error13"> </a>

Consulte o  [artigo da Base de Dados de Conhecimento do Suporte da Microsoft ID 2557533](https://support.microsoft.com/pt-br/kb/2557533) ( `http://support.microsoft.com/kb/2557533`) para saber mais.
  
    
    

## Recursos adicionais
<a name="bk_addresources"> </a>


-  [Práticas recomendadas de desenvolvimento de fluxo de trabalho do SharePoint](sharepoint-workflow-development-best-practices.md)
    
  
-  [Desenvolver fluxos de trabalho do SharePoint 2013 usando o Visual Studio](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

