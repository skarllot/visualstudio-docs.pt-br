---
title: "Como instalar o criador de perfil aut&#244;nomo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ferramentas de desempenho, instalando criador de perfil autônomo"
  - "ferramentas de criação de perfil, criador de perfil autônomo"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como instalar o criador de perfil aut&#244;nomo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profiler fornece um autônomo baseado em linha de comando que pode ser executado sem instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  Essa situação acontece quando um computador não pode ou não ter um ambiente de desenvolvimento instalado.  Por exemplo, você não deve instalar um ambiente de desenvolvimento em um servidor Web de produção.  
  
> [!NOTE]
>  Quando você estiver usando o profiler autônomo para coletar dados de desempenho do site ASP.NET, a ferramenta de linha [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) é recomendada sobre a ferramenta de [VSPerfCmd](../profiling/vsperfcmd.md) .  
  
### Para instalar o profiler autônoma  
  
1.  Localize o instalador autônomo do perfil vs\_profiler.exe \(\) na mídia de instalação de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no diretório que inclui \\ caminho do profiler e execute\-o.  
  
2.  Adicionar os caminhos para vsintr.exe e msdis150.dll ao caminho do sistema.  
  
    > [!NOTE]
    >  Na instalação padrão de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vsinstr.exe e msdis150.dll são localizados em \\ arquivos de programas \\ microsoft Visual Studio 10 \\ tools \\ de equipe ferramentas de desempenho.  
  
3.  No prompt de comando, digite **VSInstr**.  
  
    > [!NOTE]
    >  Se as informações de uso para vsinstr.exe é exibida, tudo está configurado corretamente.  Se ocorrer um erro que indica vsinstr.exe ou uma de suas dependências não for encontrado, verifique se você tem os caminhos adequadamente configurados como descrito na etapa 2.  
  
4.  Configurar o servidor do símbolo definindo sua variável de **\_NT\_SYMBOL\_PATH** a **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols**  
  
5.  Depois que você configurar o servidor do símbolo usando variáveis de ambiente do, execute as ferramentas do profiler de linha de comando em um novo prompt de comando.  Isso permite que os novos variáveis de ambiente entrem em vigor.  Na janela do prompt de comando, digite o seguinte comando:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Para obter instruções detalhadas sobre como configurar o pacote do servidor do símbolo, consulte [Como fazer referência a informações de símbolo do Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Use a ferramenta de [VSPerfReport](../profiling/vsperfreport.md) para serializar os símbolos no arquivo de dados de perfil .vsp \(\).  Use as opções de **VSPerfReport \/summary:all \/packsymbols** .  Se você não tiver os símbolos inseridos em seu arquivo de dados, certifique\-se de que a variável de ambiente de \_NT\_SYMBOL\_PATH definido.  
  
## Consulte também  
 [Criando perfil a partir da linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Instruções passo a passo: criação de perfil de linha de comando usando amostragem](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [Instruções passo a passo: criação de perfil de linha de comando usando instrumentação](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Como fazer referência a informações de símbolo do Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)