---
title: Como configurar um ambiente para o desenvolvimento de aplicativos móveis para o SharePoint
ms.prod: SHAREPOINT
ms.assetid: acaf556d-e20d-478d-8c59-2efd8efb9dcb
---


# Como configurar um ambiente para o desenvolvimento de aplicativos móveis para o SharePoint
Saiba mais sobre os requisitos do sistema e a configuração de um ambiente de desenvolvimento para projetos de mobilidade do SharePoint.
Uma configuração mínima para o trabalho com projetos de mobilidade do SharePoint exige um servidor executando o SharePoint 2013 (ou uma conta do SharePoint Online) e um ambiente de desenvolvimento em um sistema operacional cliente separado. A instalação do SharePoint 2013 em sistemas operacionais cliente (como o Windows 7) não tem suporte e a instalação das ferramentas necessárias para o desenvolvimento do Windows Phone não tem suporte em sistemas operacionais de servidor (como o Windows Server 2008).
  
    
    


## Os projetos de desenvolvimento do Windows Phone e o SharePoint Server
<a name="SP15Setupmobile_winphone"> </a>

Para criar e testar aplicativos do Windows Phone que interagem com o SharePoint, você precisará de acesso a um servidor executando o SharePoint 2013 ou de uma conta do SharePoint Online e precisará de permissões suficientes nos sites e nas listas que você precisa usar em suas soluções. Recomendamos que você use uma instalação do SharePoint Server que seja dedicada a testes e desenvolvimento como um servidor de destino enquanto desenvolve seus projetos. Use o SharePoint Server em um ambiente de produção como seu servidor de destino somente depois que a sua solução desenvolvida tiver passado por testes suficientes.
  
    
    
Para saber mais sobre a instalação e a configuração do SharePoint 2013, consulte a documentação da seção  [Produtos do SharePoint](http://technet.microsoft.com/pt-br/library/ee428287.aspx) da Biblioteca do Microsoft TechNet. Para saber mais sobre o uso do SharePoint Online em suas soluções de desenvolvimento, visite a [Central de Recursos do Desenvolvedor do SharePoint Online](http://msdn.microsoft.com/pt-br/sharepoint/gg153540.aspx).
  
    
    
Para os exemplos de código desta documentação, supõe-se que um desenvolvedor trabalhando com o exemplo tenha ou possa obter permissões suficientes em sites e listas do SharePoint para poder adicionar, editar e excluir dados.
  
    
    

## Configurar um ambiente de desenvolvimento cliente para projetos de mobilidade do SharePoint
<a name="SP15Setupmobile_configure"> </a>

Para desenvolver Suplementos do SharePoint a serem usados em dispositivos Windows Phone, você precisará configurar suas ferramentas de desenvolvimento em um computador que esteja executando um sistema operacional cliente, e não um sistema operacional de servidor.
  
    
    

### Configurando o Windows Phone SDK 8.0

Para desenvolver Suplementos do SharePoint a serem usados no Windows Phone 8, você precisará configurar suas ferramentas de desenvolvimento em um computador que esteja executando versões cliente do Windows 8 de 64 bits (x64) ou o Windows 8 Pro. O Emulador do Windows Phone 8 exige o Windows 8 Pro e requer um processador que dê suporte a SLAT (Conversão de Endereços de Segundo Nível).
  
    
    

1. Em um computador com um sistema operacional cliente com suporte, instale o  [Windows Phone SDK 8.0](http://www.microsoft.com/pt-br/download/details.aspx?id=35471). O Windows Phone Software Development Kit (SDK) 8.0 oferece a você as ferramentas de que você precisa para desenvolver aplicativos e jogos para o Windows Phone 8 e o Windows Phone 7.5.
    
    O Windows Phone SDK 8.0 é um ambiente de desenvolvimento com recursos completos a ser usado para criar aplicativos e jogos para o Windows Phone 8.0 e o Windows Phone 7.5. O Windows Phone SDK oferece uma edição autônoma do Visual Studio Express 2012 para o Windows Phone ou trabalha como um suplemento das edições Visual Studio 2012 Professional, Premium ou Ultimate. Com o SDK, você pode usar suas habilidades de programação e o código existentes para criar aplicativos de código gerenciado ou nativo. Além disso, o SDK inclui vários emuladores e as ferramentas adicionais para criação de perfis e testes de seu aplicativo do Windows Phone sob condições do mundo real.
    
    > **OBSERVAçãO**
      > Se o seu computador atender aos requisitos de hardware e de sistema operacional, mas não atender aos requisitos para o Emulador do Windows Phone 8, o Windows Phone SDK 8.0 será instalado e executado. Entretanto, o Emulador do Windows Phone 8 não funcionará e você não conseguirá implantar ou testar aplicativos no Emulador do Windows Phone 8. Para saber mais sobre os requisitos do sistema para a execução do Emulador do Windows Phone, consulte  [Requisitos de instalação e do sistema para o Emulador do Windows Phone](http://msdn.microsoft.com/pt-br/library/ff626524). 
2. Instale o  [SDK do Microsoft SharePoint para Windows Phone 8](http://www.microsoft.com/en-us/download/details.aspx?id=36818).
    
    O SDK do SharePoint para Windows Phone instala dois Silverlight para modelos do Windows Phone (além dos instalados pelo SDK do Windows Phone): o modelo Aplicativo do SharePoint Vazio do Windows Phone e o modelo Aplicativo de Lista do SharePoint do Windows Phone. O SDK também instala bibliotecas CSOM do SharePoint, uma biblioteca de autenticação e modelos de projeto do Windows Phone e agora dá suporte à autenticação NTLM. Você pode usar as APIs e os modelos empacotados para criar aplicativos do Windows Phone 8 no SharePoint 2013.
    
    Adicionalmente, o SDK do SharePoint para Windows Phone instala vários assemblies de tempo de execução de suporte (em  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v8.0\\Libraries` para uma instalação padrão).
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **OBSERVAçãO**
      > No momento, os modelos do SDK do SharePoint para Windows Phone estão disponíveis apenas para projetos C#. 
Para saber mais sobre os modelos do SDK do SharePoint para Windows Phone, consulte  [Visão geral dos modelos de aplicativos do Windows Phone SharePoint 2013 no Visual Studio](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md).
  
    
    

### Configurando o Windows Phone SDK 7.1

Para desenvolver Suplementos do SharePoint a serem usados no Windows Phone 7, você precisará configurar suas ferramentas de desenvolvimento em um computador que esteja executando o Windows 7 (32 bits ou 64 bits) ou o Windows Vista Service Pack 2 (32 bits ou 64 bits). O Windows Phone Software Development Kit (SDK) 7.1 não tem suporte no Windows Server 2008 ou no Windows XP.
  
    
    

1. Em um computador com um sistema operacional cliente com suporte, instale o  [Windows Phone SDK 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=27570).
    
    > **OBSERVAçãO**
      > Uma versão anterior do Windows Phone SDK chamava-se Ferramentas de Desenvolvedor do Windows Phone. 

    O Windows Phone SDK instala o Microsoft Visual Studio 2010 Express para Windows Phone, o Emulador do Windows Phone, XNA Game Studio e o Microsoft Expression Blend for Windows Phone. O Visual Studio 2010 Express for Windows Phone é um ambiente de desenvolvimento adequado para a maioria das soluções do Windows Phone. Você também pode usar o Visual Studio 2010 Professional como seu ambiente de desenvolvimento preferencial, mas ainda é necessário instalar o Windows Phone SDK, que instala os suplementos necessários no Visual Studio (o Windows Phone SDK atualmente não tem suporte para uso com o Visual Studio 2012).
    
    Para saber mais sobre requisitos do sistema adicionais para a instalação do Windows Phone SDK, consulte  [Instalando o Windows Phone SDK](http://msdn.microsoft.com/pt-br/library/ff402530). Para saber mais sobre os requisitos do sistema para a execução do Emulador do Windows Phone, consulte  [Requisitos de instalação e do sistema para o Emulador do Windows Phone](http://msdn.microsoft.com/pt-br/library/ff626524).
    
  
2. Instale o  [SDK do Microsoft SharePoint para Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476).
    
    O SDK do SharePoint para Windows Phone instala dois Silverlight para modelos do Windows Phone (além dos instalados pelo Windows Phone SDK): o modelo Aplicativo do SharePoint vazio do Windows Phone e o modelo Aplicativo de Lista do SharePoint do Windows Phone.
    
    Adicionalmente, o SDK do SharePoint para Windows Phone instala vários assemblies de tempo de execução de suporte (em  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v7.1\\Libraries` para uma instalação padrão).
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **OBSERVAçãO**
      > No momento, os modelos do SDK do SharePoint para Windows Phone estão disponíveis apenas para projetos C#. 
Para saber mais sobre os modelos do SDK do SharePoint para Windows Phone, consulte  [Visão geral dos modelos de aplicativos do Windows Phone SharePoint 2013 no Visual Studio](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md).
  
    
    

## Recursos adicionais
<a name="SP15Setupmobile_addlresources"> </a>


-  [Crie aplicativos do Windows Phone que acessam o SharePoint 2013](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/en-us/download/details.aspx?id=35471)
    
  
-  [SDK do Microsoft SharePoint para Windows Phone 8](http://www.microsoft.com/en-us/download/details.aspx?id=36818)
    
  
-  [Windows Phone SDK 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=27570)
    
  
-  [SDK do Microsoft SharePoint para Windows Phone 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=30476)
    
  

