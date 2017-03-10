---
title: "Como anexar ao script | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "processos, anexando ao script"
  - "depuração remota, anexando ao script"
  - "depuração de script, anexando ao script"
  - "script, anexando a"
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar ao script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico explica como anexar manualmente o depurador do Visual Studio para um arquivo de script para depuração.  
  
### Para anexar a um processo em execução  
  
1.  No menu **Depurar**, escolha **Anexar ao Processo**. \(Se nenhum projeto estiver aberto, escolha **Anexar ao Processo** no menu **Ferramentas**.\)  
  
2.  Na caixa de diálogo **Anexar ao Processo**, procure a lista **Processos Disponíveis** e localize o processo de script ao qual você quer anexar.  Você pode identificar processos de script consultando a coluna **Tipo**.  
  
    1.  Se o processo que você quiser depurar estiver sendo executado em outro computador, você primeiro deverá selecionar o computador remoto.  Para obter mais informações, consulte [How to: Select a Remote Computer](http://msdn.microsoft.com/pt-br/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Se o processo estiver sendo executado em uma conta de usuário diferente, marque a caixa de seleção **Mostrar processos de todos os usuários**.  
  
    3.  Se você estiver conectado por meio da **Conexão de Área de Trabalho Remota**, marque a caixa de seleção **Exibir os Processos em Todas as Sessões**.  
  
3.  Clique no processo ao qual você quer anexar.  
  
4.  Na caixa **Anexar a** , você deverá ver **Código de script** ou **Automático: Código de script**.  Se você encontrar algo além disso, siga estas etapas:  
  
    1.  Clique em **Selecionar**.  
  
    2.  Na caixa de diálogo **Selecionar Tipo de Código**, clique em **Depurar estes tipos de código** e selecione **Script**.  
  
    3.  Clique em **OK**.  
  
5.  Clique em **Anexar**.  
  
     Neste momento, você pode ver um aviso informando que a depuração de scripts está desabilitada no Internet Explorer.  Se isso ocorrer, consulte [Aviso: depuração de script desabilitada](../debugger/warning-script-debugging-disabled.md).  
  
 A lista **Processos Disponíveis** é exibida automaticamente quando você abre a caixa de diálogo **Processos**.  Os processos podem iniciar e parar em segundo plano quando a caixa de diálogo está aberta.  Consequentemente, o conteúdo pode não estar atualizado.  Você pode atualizar a lista a qualquer momento para ver a lista atual de processos pressionando o botão **Atualizar**.  
  
 Você pode estar associado a vários programas enquanto depura, mas somente um programa está ativo no depurador em um determinado momento.  Você pode definir o programa ativo na barra de ferramentas Local de Depuração.  Para obter mais informações, consulte [How to: Set the Current Process](http://msdn.microsoft.com/pt-br/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Todos os comandos de execução no menu **Depurar** afetam o programa ativo.  Você pode interromper qualquer programa depurado na caixa de diálogo Processos. Consulte o [Usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Se você tentar anexar a um processo de propriedade de uma conta de usuário não confiável, aparecerá uma confirmação da caixa de diálogo de aviso de segurança.  Para obter mais informações, consulte [Aviso de segurança: anexar a um processo de propriedade de um usuário não confiável pode ser perigoso. Caso as informações a seguir pareçam suspeitas ou você não tenha certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 Em alguns casos, quando você está depurando em uma sessão dos Serviços de Terminal \(Área de Trabalho Remota\), a lista Processos Disponíveis não exibirá todos os processos disponíveis.  Em [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] ou em versões posteriores, se você estiver executando o Visual Studio como um usuário limitado, a lista de Processos Disponíveis não mostrará os processos que estão em execução na sessão 0, usada para serviços e outros processos de servidor, incluindo w3wp.exe.  Você pode resolver o problema executando o Visual Studio em uma conta de administrador ou executando o Visual Studio de console do servidor em vez de uma sessão de Terminal Services.  Se nenhuma dessas soluções alternativas for possível, uma terceira opção é anexar ao processo digitando vsjitdebugger.exe \-p ProcessId na linha de comando do Windows.  Você pode determinar o ID do processo usando tlist.exe.  Para obter tlist.exe, baixe e instale as Ferramentas de Depuração para o Windows, disponíveis em [Central de Desenvolvimento de Hardware do Windows](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## Consulte também  
 [Depuração de script do lado do cliente](../debugger/client-side-script-debugging.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Aviso de segurança: anexar a um processo de propriedade de um usuário não confiável pode ser perigoso. Caso as informações a seguir pareçam suspeitas ou você não tenha certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Segurança do depurador](../debugger/debugger-security.md)