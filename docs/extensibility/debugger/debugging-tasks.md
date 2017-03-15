---
title: "Tarefas de depuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 16
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
ms.openlocfilehash: 08f6d64a86982ad7425a2e89815765ce63dbf28c
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-tasks"></a>Tarefas de depuração
Para depurar um programa, ele deve ser iniciado e um mecanismo de depuração (DE) deve ser anexado a ele, senão a DE deve ser anexada a um programa iniciado anteriormente. Depois de conectado, o DE deve gerar determinados eventos de inicialização. Em resposta, o pacote de depuração tenta associar os pontos de interrupção definidos no IDE. Quando o programa atinge um ponto de interrupção associado, para e aguarda a entrada do usuário.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Problemas de segurança](../../extensibility/debugger/security-issues.md)  
 Discute as etapas de segurança necessárias para depurar um programa.  
  
 [Iniciando um programa](../../extensibility/debugger/launching-a-program.md)  
 Fornece instruções passo a passo sobre como especificar um DE, que chama o sistema operacional para iniciar o programa.  
  
 [Anexar diretamente a um programa](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Descreve o processo usado para depurar um programa em um processo que já está em execução.  
  
 [Enviar eventos de inicialização após uma inicialização](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Lista os eventos que ocorrem depois que o DE é anexado ao programa, até que o programa está em seu ponto de entrada principal e está pronto para depuração.  
  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)  
 Explica como o DE envia normalmente um evento de ponto de entrada, um evento de conclusão de carga ou um evento de parada, dependendo das circunstâncias.  
  
 [Pontos de interrupção de ligação](../../extensibility/debugger/binding-breakpoints.md)  
 Descreve como fazer isso, se o usuário define um ponto de interrupção, o IDE Formula a solicitação e solicita que a sessão de depuração para criar o ponto de interrupção.  
  
 [Avaliando expressões](../../extensibility/debugger/evaluating-expressions.md)  
 Explica como as expressões são criadas e o que acontece quando uma expressão é avaliada.  
  
 [Visualizando e exibindo dados](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explica como os visualizadores de tipo e visualizadores personalizados são suportados pelo avaliador de expressão (EE).  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquiteturas de depuração.  
  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)  
 Fornece uma visão geral sobre os componentes de depuração do Visual Studio, que incluem o manipulador de símbolo (SH), EE e DE.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica como o DE simultaneamente opera no código, documentação e contextos de avaliação de expressão. Descreve, para cada um dos três contextos, o local, posição ou avaliação relevante para ele.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
