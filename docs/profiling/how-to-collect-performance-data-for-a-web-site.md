---
title: Como coletar dados de desempenho de um site da Web | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 5bdc6cc6f2073ee017c3ffa2147e0fd3bcf5b128
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Como coletar dados de desempenho de um site da Web
Você pode usar o **Assistente de Desempenho** para coletar dados de desempenho para um aplicativo Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. É possível criar o perfil de um aplicativo Web que esteja aberto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou criar um perfil de um site da Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que está localizado no computador local e não aberto no IDE do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  O **Assistente de Desempenho** permite que você adicione dados de interação de camadas (TIP), dados de desempenho de JScript ou ambos os dados de criação de perfil coletados. A opção TIP coleta dados de processos do servidor. A criação de perfil do JScript coleta dados de scripts que são executados em um site da Web local ou remoto. Na maioria dos casos, você deve escolher apenas uma das opções.  
  
 Dependendo das configurações de Permissões de Acesso do Usuário que um administrador tenha disponibilizado, um usuário individual pode ter ou não a permissão de segurança para criar uma sessão de criador de perfil no computador que hospeda o processo ASP.NET. Os exemplos a seguir ilustram possíveis diferenças entre os usuários:  
  
-   Alguns usuários podem acessar recursos de criação de perfil avançados quando o Administrador tiver configurado o início do driver e do serviço.  
  
-   Os usuários do domínio podem acessar apenas as amostras de criação de perfil.  
  
-   Alguns usuários podem negar acesso à criação de perfil para todos os outros usuários.  
  
 Para obter mais informações, consulte [Criação de perfil e segurança do Windows Vista](../profiling/profiling-and-windows-vista-security.md) e as opções de administração em [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Para criar o perfil de um projeto de site da Web  
  
1.  Abra o projeto Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] em [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] ou [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  No menu **Analisar**, clique em **Iniciar o Assistente de Desempenho**.  
  
3.  Na primeira página do assistente, selecione um método de criação de perfil e, em seguida, clique em **Avançar**. Para obter mais informações sobre métodos de criação de perfil, consulte [Noções básicas sobre métodos de coleta de desempenho](../profiling/understanding-performance-collection-methods.md). Observe que o método de criação de perfil do visualizador de simultaneidade não está disponível para aplicativos Web.  
  
4.  Na lista suspensa **Qual aplicativo você deseja direcionar para a criação de perfil?**, certifique-se de que o projeto atual esteja selecionado e, em seguida, clique em **Avançar**.  
  
5.  Na terceira página do assistente, você pode adicionar dados de criação de perfil de interação de camada (TIP), dados do JavaScript em execução nas páginas da Web ou ambos.  
  
    -   Para coletar a interação da camada, selecione a caixa de seleção **Habilitar Criação de Perfil de Interação de Camada**.  
  
    -   Para coletar dados do JavaScript em execução nas páginas da Web, selecione a caixa de seleção **Criar perfil de JavaScript**.  
  
6.  Clique em **Avançar**.  
  
7.  Na quarta página do assistente, clique em **Concluir**.  
  
8.  Uma sessão de desempenho é criada para o aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e o site da Web é iniciado no navegador. Execute a funcionalidade para qual deseja criar o perfil e, em seguida, feche o navegador.  
  
     O criador de perfil gera o arquivo de dados e demonstra a exibição dos dados de Resumo na janela principal do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Para criar o perfil de um site da Web sem abrir um projeto no Visual Studio  
  
1.  Abra [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] ou [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  No menu **Analisar**, clique em **Iniciar o Assistente de Desempenho**.  
  
3.  Na primeira página do assistente, selecione um método de criação de perfil e, em seguida, clique em **Avançar**. Para obter mais informações, consulte [Noções Básicas sobre Métodos de Coleta de Desempenho](../profiling/understanding-performance-collection-methods.md).  
  
4.  Na segunda página do assistente, selecione a opção **Criar Perfil de um aplicativo ASP.NET ou JavaScript** e, em seguida, clique em **Avançar**.  
  
5.  Na caixa **Qual URL ou Caminho executará seu aplicativo Web** na terceira página do assistente, insira a URL para a home page do aplicativo e, em seguida, clique em **Avançar**.  
  
    -   Para o site da Web baseado em um servidor (IIS), digite uma URL como **http://localhost/MySite/default.aspx**. Isso faz com que o aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no computador local na raiz do aplicativo do MySite tenha seu perfil criado e a página default.aspx nesse site seja iniciada no Internet Explorer para iniciar a sessão.  
  
    -   Para um site da Web baseado em um arquivo, digite um caminho como file///**c:\WebSites\MySite\default.aspx**. Isso faz com que o aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] localizado em c:\webSites\MySite tenha seu perfil criado e a página http://localhost:nnnn/MySite/default.aspx seja iniciada no Internet Explorer para iniciar a sessão.  
  
    -   Para sites externos sobre os quais deseja coletar dados de JavaScript, digite a URL, por exemplo, http://www.contoso.com.  
  
     Para obter mais informações, exiba as páginas de propriedades para um binário de destino de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
6.  Na terceira página do assistente, você pode adicionar dados de criação de perfil de interação de camada (TIP), dados do JavaScript em execução nas páginas da Web ou ambos.  
  
    -   Para coletar a interação da camada, selecione a caixa de seleção **Habilitar Criação de Perfil de Interação de Camada**.  
  
    -   Para coletar dados do JavaScript em execução nas páginas da Web, selecione a caixa de seleção **Criar perfil de JavaScript**.  
  
7.  Clique em **Avançar**.  
  
8.  Na quarta página do assistente, clique em **Concluir**.  
  
9. Uma sessão de desempenho é criada para o aplicativo ASP.NET e o site da Web é iniciado no navegador. Execute a funcionalidade para qual deseja criar o perfil e, em seguida, feche o navegador.  
  
     O criador de perfil gera o arquivo de dados e demonstra a exibição dos dados de Resumo na janela principal do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Visões gerais](../profiling/overviews-performance-tools.md)   
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Noções Básicas sobre Valores de Dados de Instrumentação](../profiling/understanding-instrumentation-data-values.md)   
 [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)
