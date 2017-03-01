---
title: Iniciando um programa | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 23cfd31d3a3fa409fadebaaf50ffceab15bc14e2
ms.lasthandoff: 02/22/2017

---
# <a name="launching-a-program"></a>Iniciando um programa
Os usuários que desejam depurar um programa podem pressionar F5 para executar o depurador do IDE. Isso inicia uma série de eventos que resultar na conexão do IDE para um mecanismo de depuração (DE), por sua vez conectado, ou anexado, o programa da seguinte maneira:  
  
1.  O IDE primeiro chama o pacote do projeto para obter configurações de depuração de projeto ativo da solução. As configurações incluem o diretório inicial, as variáveis de ambiente, a porta na qual o programa será executado e o DE ser usado para criar o programa, se especificado. Essas configurações são passadas para o pacote de depuração.  
  
2.  Se um DE for especificado, o DE chama o sistema operacional para iniciar o programa. Como consequência de iniciar o programa, o ambiente de tempo de execução do programa é carregado. Por exemplo, se um programa é escrito em MSIL, o common language runtime será chamado para executar o programa.  
  
     -ou-  
  
     Se a DE não for especificada, a porta chama o sistema operacional para iniciar o programa, o que faz com que o ambiente de tempo de execução do programa a ser carregado.  
  
    > [!NOTE]
    >  Se for usado um DE iniciar um programa, é provável que o mesmo DE será anexado ao programa.  
  
3.  Dependendo se a porta ou o DE iniciado o programa, o DE ou o ambiente de tempo de execução, em seguida, cria uma descrição do programa ou o nó e notifica a porta que o programa está em execução.  
  
    > [!NOTE]
    >  É recomendável que o ambiente de tempo de execução criar o nó de programa, porque o nó do programa é uma representação leve de um programa que pode ser depurado. Não é necessário para carregar um inteiro DE apenas para criar e registrar um nó de programa. Se o DE é projetado ser executado no processo do IDE, mas nenhum IDE está realmente em execução, precisa haver um componente que pode adicionar um nó de programa para a porta.  
  
 O programa criado recentemente, juntamente com outros programas relacionados ou não relacionados, iniciado ou anexado a partir do mesmo IDE, compor uma sessão de depuração.  
  
 Programaticamente, quando o usuário primeiro pressiona **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]do pacote de depuração chama o pacote de projeto (que é associado com o tipo de programa que está sendo iniciado) por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>método, que por sua vez preenche um <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>estrutura com configurações de depuração do projeto ativo da solução.</xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Essa estrutura é passada de volta para o pacote de depuração por meio de uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> O pacote de depuração instancia o Gerenciador de depuração de sessão (SDM), que inicia o programa sendo mecanismos de depuração qualquer associado e depurado.  
  
 Um dos argumentos passados para o SDM é o GUID da ser usado para iniciar o programa.  
  
 Se o GUID DE não `GUID_NULL`, o SDM cria conjunta DE e, em seguida, chama o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método para iniciar o programa. Por exemplo, se um programa é escrito em código nativo, em seguida, `IDebugEngineLaunch2::LaunchSuspended` provavelmente chamará `CreateProcess` e `ResumeThread` (funções do Win32) para executar o programa.  
  
 Como consequência de iniciar o programa, o ambiente de tempo de execução do programa é carregado. O DE ou o ambiente de tempo de execução cria um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para descrever o programa de interface e passa essa interface para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar a porta que o programa está em execução.  
  
 Se `GUID_NULL` for passado, a porta inicia o programa. Quando o programa estiver em execução, o ambiente de tempo de execução cria um `IDebugProgramNode2` de interface para descrever o programa e o transmite para `IDebugPortNotify2::AddProgramNode`. Isso notifica a porta que o programa está em execução. Em seguida, o SDM anexa o mecanismo de depuração para o programa em execução.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Notificar a porta](../../extensibility/debugger/notifying-the-port.md)  
 Explica o que acontece depois que um programa é iniciado e a porta é notificada.  
  
 [Anexar após uma inicialização](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documentos quando a sessão de depuração está pronta para anexar o DE para o programa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.
