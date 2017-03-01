---
title: "Sessão de depuração Manager | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
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
ms.openlocfilehash: 2433bb2927346ef6920bd508bd4ff9803586d806
ms.lasthandoff: 02/22/2017

---
# <a name="session-debug-manager"></a>Gerenciador de sessão de depuração
O Gerenciador de sessão de depuração (SDM) gerencia a qualquer número de mecanismos de depuração (DE) qualquer número de programas em vários processos em qualquer número de máquinas de depuração. Além de ser um multiplexador do mecanismo de depuração, o SDM oferece uma exibição unificada da sessão de depuração ao IDE.  
  
## <a name="session-debug-manager-operation"></a>Operação do Gerenciador de sessão depuração  
 O Gerenciador de sessão de depuração (SDM) gerencia DE. Pode haver mais de um mecanismo de depuração em execução em um computador ao mesmo tempo. Para multiplexar o DEs, o SDM encapsula um número de interfaces do DEs e os expõe ao IDE como uma única interface.  
  
 Para aumentar o desempenho, algumas interfaces não são multiplexadas. Em vez disso, eles são usados diretamente a partir DE, e o SDM não vão chamadas para essas interfaces. Por exemplo, interfaces usadas com memória, código e contextos de documento não são multiplexadas, porque eles se referem a uma instrução específica, memória ou documento em um programa específico depurado por específicos DE. Nenhum outro DE precisa estar envolvido no nível de comunicação.  
  
 Isso não é verdadeiro para todos os contextos. Chamadas para a interface de contexto de avaliação de expressão percorrer o SDM. Durante a avaliação da expressão, o SDM encapsula o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface que dá ao IDE porque quando essa expressão é avaliada, pode envolver vários DEs que está depurando programas no mesmo processo que poderiam ser executados no mesmo thread.  
  
 O SDM normalmente funciona como um mecanismo de delegação, mas ele pode atuar como um mecanismo de difusão. Por exemplo, durante a avaliação da expressão, o SDM funciona como um mecanismo de difusão para notificar o DEs todos os que eles podem executar código em um thread específico. Da mesma forma, quando o SDM recebe um evento de interrupção, ele transmite para todos os programas que devem interromper a execução. Quando uma etapa é chamada, o SDM transmite para todos os programas que eles podem continuar em execução. Pontos de interrupção também são transmitidos para todos os DE.  
  
 O SDM não controla o programa atual, thread ou quadro de pilha. O programa, thread e processo informações são enviadas para o SDM em conjunto com eventos de depuração específicos.  
  
## <a name="see-also"></a>Consulte também  
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
