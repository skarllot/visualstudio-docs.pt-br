---
title: "Como: coletar dados de desempenho de um Site da Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.url.url"
  - "vsperf.chooseurl"
  - "vs.performance.wizard.asppage"
  - "vsperf.url.ok"
  - "vsperf.url.cancel"
helpviewer_keywords: 
  - "Ferramentas de criação de perfil ASP.NET de criação de perfil"
  - "sites da Web, a criação de perfil de desempenho"
  - "ASP.NET, criação de perfil de desempenho"
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como: coletar dados de desempenho de um Site da Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o **Performance Wizard** para coletar dados de desempenho para um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo Web. Perfil de um aplicativo Web que é aberto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ou você pode criar um perfil um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] site que está localizado no computador local e não está aberta no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  O **Performance Wizard** permite que você adicione dados de interação \(dica\) de camadas, dados de desempenho de JScript ou ambos os dados de criação de perfil coletados. A opção de dica coleta dados de processos do servidor. A criação de perfil do JScript coleta dados de scripts que são executados em um site local ou remoto. Na maioria dos casos, você deve escolher apenas uma das opções.  
  
 Dependendo das configurações de permissões de acesso do usuário que um administrador tornou disponível, um usuário individual pode ou não pode ter a permissão de segurança para criar uma sessão do criador de perfil no computador que hospeda o processo do ASP.NET. Os exemplos a seguir ilustram possíveis diferenças entre os usuários:  
  
-   Alguns usuários podem acessar recursos avançados de criação de perfil quando o administrador configurou o driver e o início do serviço.  
  
-   Os usuários do domínio podem acessar exemplo apenas perfis.  
  
-   Alguns usuários meu negar acesso a criação de perfil para todos os outros usuários.  
  
 Para obter mais informações, consulte [Criação de perfil e segurança do Windows Vista](../profiling/profiling-and-windows-vista-security.md) e as opções de administração no [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Para criar o perfil de um projeto de site da Web  
  
1.  Abra o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projeto Web no [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] ou [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  Sobre o **Analisar** menu, clique em **Launch Performance Wizard**.  
  
3.  Na primeira página do assistente, selecione um método de criação de perfil e, em seguida, clique em **próximo**. Para obter mais informações sobre métodos de criação de perfil, consulte [Noções básicas sobre métodos da criação de perfil](../profiling/understanding-performance-collection-methods.md). Observe que o Visualizador de simultaneidade, método de criação de perfil não está disponível para aplicativos da web.  
  
4.  No **quais aplicativos você gostaria de destino para a criação de perfil?** lista suspensa, certifique\-se de que o projeto atual está selecionado e, em seguida, clique em **próximo**.  
  
5.  Na terceira página do assistente, você pode optar por adicionar camada interação criação de perfil \(dica\), dados do JavaScript em execução em páginas da Web, ou ambos.  
  
    -   Para coletar a interação de camadas, selecione a **Habilitar Tier Interaction Profiling** caixa de seleção.  
  
    -   Para coletar dados do JavaScript em execução nas páginas da Web, selecione o **perfil JavaScript** caixa de seleção.  
  
6.  Clique em **Avançar**.  
  
7.  Na quarta página do assistente, clique em **Concluir**.  
  
8.  Criar uma sessão de desempenho para o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo e o site da Web é iniciado no navegador. Utilizar a funcionalidade de perfil você deseja e, em seguida, feche o navegador.  
  
     O criador de perfil gera o arquivo de dados e exibe a exibição dos dados de resumo de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela principal.  
  
### Para criar o perfil de um site da Web sem abrir um projeto no Visual Studio  
  
1.  Abra [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] ou [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  Sobre o **Analisar** menu, clique em **Launch Performance Wizard**.  
  
3.  Na primeira página do assistente, selecione um método de criação de perfil e, em seguida, clique em **próximo**. Para obter mais informações, consulte [Noções básicas sobre métodos da criação de perfil](../profiling/understanding-performance-collection-methods.md).  
  
4.  Na segunda página do assistente, selecione o **criar o perfil de um aplicativo ASP.NET ou JavaScript** opção e, em seguida, clique em **próximo**.  
  
5.  No **qual URL ou caminho executará seu aplicativo web** caixa na terceira página do assistente, insira a URL para a home page do aplicativo e, em seguida, clique em **próximo**.  
  
    -   Para o site da Web baseado em um servidor \(IIS\), digite uma URL como **http:\/\/localhost\/MySite\/default.aspx**. Isso faz com que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo no computador local na raiz do aplicativo do MySite para criação de perfil e página Default. aspx no site a ser iniciado no Internet Explorer para iniciar a sessão.  
  
    -   Para o site da Web baseado em um arquivo, digite um caminho como arquivo \/ \/ \/**c:\\WebSites\\MySite\\default.aspx.**. Isso faz com que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo localizado em c:\\webSites\\MySite para criação de perfil e a página http:\/\/localhost:nnnn\/MySite\/default.aspx deve ser iniciada no Internet Explorer para iniciar a sessão.  
  
    -   Para sites externos que você deseja coletar dados de JavaScript em, digite a URL, por exemplo, http:\/\/www.contoso.com.  
  
     Para obter mais informações, exiba as páginas de propriedades para um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] binário de destino.  
  
6.  Na terceira página do assistente, você pode optar por adicionar camada interação criação de perfil \(dica\), dados do JavaScript em execução em páginas da Web, ou ambos.  
  
    -   Para coletar a interação de camadas, selecione a **Habilitar Tier Interaction Profiling** caixa de seleção.  
  
    -   Para coletar dados do JavaScript em execução nas páginas da Web, selecione o **perfil JavaScript** caixa de seleção.  
  
7.  Clique em **Avançar**.  
  
8.  Na quarta página do assistente, clique em **Concluir**.  
  
9. Uma sessão de desempenho é criada para o aplicativo ASP.NET e o site da Web é iniciado no navegador. Utilizar a funcionalidade de perfil você deseja e, em seguida, feche o navegador.  
  
     O criador de perfil gera o arquivo de dados e exibe a exibição dos dados de resumo de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela principal.  
  
## Consulte também  
 [Visões gerais](../profiling/overviews-performance-tools.md)   
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Noções básicas sobre valores de dados de instrumentação](../profiling/understanding-instrumentation-data-values.md)   
 [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)