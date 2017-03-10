---
title: "Depurar aplicativos de 64 bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], 64 bits"
  - "depuração de 64 bits"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar aplicativos de 64 bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode depurar um aplicativo de 64 bits que está em execução no computador local ou em um computador remoto.  
  
 Para depurar um aplicativo de 64 bits em execução em um computador remoto, consulte [Depuração remota](../debugger/remote-debugging.md).  
  
 Para depurar aplicativos de 64 bits localmente, o Visual Studio usa um processo de trabalho de 64 bits \(msvsmon.exe\) para executar as operações de nível baixo que não podem ser feitas dentro do processo do Visual Studio de 32 bits.  
  
 Não há suporte para a depuração de modo misto para processos de 64 bits que usam o .NET Framework versão 3.5 ou anterior.  
  
## Depurar um aplicativo de 64 bits  
 Tentar depurar um aplicativo de 64 bits:  
  
1.  Crie uma solução do Visual Studio, por exemplo um console aplicativo c\#.  
  
2.  Defina a configuração de 64 bits usando o Configuration Manager. Para obter mais informações, consulte [Como configurar projetos para destinar plataformas](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  Neste ponto, a versão de 64 bits do depurador remoto \(msvsmon.exe\) inicia. Ele é executado, contanto que a solução com a configuração de 64 bits é aberta.  
  
4.  Inicie a depuração. Você deve ter a mesma experiência que com uma configuração de 32 bits. Se você receber erros, consulte a seção de solução de problemas abaixo.  
  
## Solucionando problemas de depuração de 64 bits  
 Você verá um erro: "uma operação de depuração de 64 bits está demorando mais do que o esperado." Nesse caso, o Visual Studio enviou uma solicitação para a versão de 64 bits do msvsmon.exe e levou muito tempo para o resultado dessa solicitação voltar.  
  
 Há duas causas principais para este erro:  
  
-   Você tem o software de segurança de rede instalado no computador que fez a pilha de rede não é confiável e ele descartado pacotes ultrapassou localhost. Tente desabilitar todos os softwares de segurança de rede e veja se isso resolve. Nesse caso, de relatório para o fornecedor do software de segurança de rede que o software estiver interferindo com o tráfego de localhost.  
  
-   Você está executando em um problema de suspensão ou de desempenho com o Visual Studio. Se o problema ocorrer regularmente, você pode coletar despejos do Visual Studio \(devenv.exe\) e o processo de trabalho \(msvsmon.exe\) e enviá\-los à Microsoft. Para obter informações sobre como relatar um problema, consulte [Como relatar um problema com o Visual Studio](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md).  
  
## Consulte também  
 [Aplicativos de 64 bits](../Topic/64-bit%20Applications.md)   
 [Configurando programas para 64 bits](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Suporte de 64 bits IDE do Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Usar arquivos de despejo para depurar falhas e travamentos de aplicativo](../debugger/using-dump-files.md)   
 [Depuração remota](../debugger/remote-debugging.md)