---
title: "Como especificar um local alternativo para atualiza&#231;&#245;es da implanta&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, atualizações"
  - "atualização de implantação, locais alternativos"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar um local alternativo para atualiza&#231;&#245;es da implanta&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode instalar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo inicialmente a partir de um CD ou um compartilhamento de arquivos, mas o aplicativo deve verificar se há atualizações periódicas na Web.  Você pode especificar um local alternativo para atualizações em seu manifesto de implantação para que seu aplicativo possa atualizar próprio da Web após sua instalação inicial.  
  
> [!NOTE]
>  Seu aplicativo deve ser configurado para instalar localmente para usar este recurso.  Para obter mais informações, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Além disso, se você instalar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos da rede, definindo um local alternativo causas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para usar esse local para a instalação inicial e todas as atualizações subseqüentes.  Se você instalar o aplicativo localmente \(por exemplo, de um CD\), a instalação inicial é realizada usando a mídia original e todas as atualizações subseqüentes usarão o local alternativo.  
  
### Especificando um local alternativo para atualizações usando o MageUI.exe \(utilitário baseado em Windows Forms\)  
  
1.  Abrir um.NET Framework prompt de comando e digite:  
  
     **mageui.exe**  
  
2.  Sobre o  **arquivo** menu, escolha  **Abrir** para abrir o manifesto de implantação do seu aplicativo.  
  
3.  Selecione o  **Opções de implantação** guia.  
  
4.  Na caixa de texto chamado  **O local de inicialização**, digite a URL para o diretório que conterá o manifesto de implantação para atualizações de aplicativos.  
  
5.  Salve o manifesto de implantação.  
  
### Especificando um local alternativo para atualizações usando o Mage  
  
1.  Abrir um.NET Framework prompt de comando.  
  
2.  Defina o local de atualização usando o comando a seguir.  Neste exemplo, **HelloWorld.exe.application** é o caminho para seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo, que sempre tem a extensão. Application, e **http:\/\/adatum.com\/Update\/Path** é o URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] irá verificar atualizações do aplicativo.  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  Salve o arquivo.  
  
    > [!NOTE]
    >  Agora, você precisará assinar novamente o arquivo com Mage.  Para obter mais informações, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Segurança do .NET Framework  
 Se você instalar o seu aplicativo de uma mídia off\-line, como um CD, e o computador está on\-line, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] primeiro verifica o URL especificado pela `<deploymentProvider>` marca no manifesto de implantação para determinar se o local de atualização contém uma versão mais recente do aplicativo.  Em caso afirmativo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instala o aplicativo diretamente a partir daí, em vez da partir do diretório de instalação inicial, e o common language runtime \(CLR\) determina a relação de confiança do seu aplicativo usando de nível `<deploymentProvider>`.  Se o computador estiver off\-line, ou `<deploymentProvider>` não pode ser acessado, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalações a partir do CD e o CLR concede confiança com base em um ponto de instalação. para uma instalação do CD, isso significa que seu aplicativo recebe confiança total.  Todas as atualizações subseqüentes herdarão esse nível de confiança.  
  
 Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] os aplicativos que usam `<deploymentProvider>` deve explicitamente declarar as permissões necessárias no manifesto do aplicativo, para que o aplicativo não recebe diferentes níveis de confiança em computadores diferentes.  
  
## Consulte também  
 [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)