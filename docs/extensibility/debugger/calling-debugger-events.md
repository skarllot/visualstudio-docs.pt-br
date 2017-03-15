---
title: Chamar eventos do depurador | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
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
ms.openlocfilehash: a61add2f6d96ff6b2c31ca5114c30d4a0a75b038
ms.lasthandoff: 02/22/2017

---
# <a name="calling-debugger-events"></a>Eventos do depurador de chamada
Eventos em sessões de depuração ocorrerem em uma ordem específica.  
  
## <a name="discussion"></a>Discussão  
 Para entender o padrão de chamadas entre o mecanismo de depuração (DE) e o Gerenciador de sessão de depuração (SDM), o código a seguir representa a ordem de chamada dos eventos que ocorrem em uma sessão de depuração típica:  
  
1.  [Anexar e desanexar a um programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Iniciando o depurador](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Encerrar um programa](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Criar um ponto de interrupção](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Quando associa a um ponto de interrupção ou se tornar não associados](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Erros de ponto de interrupção](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Atingindo um ponto de interrupção](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Excluir um ponto de interrupção](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Entrar no modo de interrupção](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Entrar no modo de interrupção](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Avaliação da expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Tratamento de exceções](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Consulte também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
