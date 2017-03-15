---
title: "Exceção tratamento (SDK do Visual Studio) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
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
ms.openlocfilehash: a14ebc5e8dee38502998d04b7b40e10b190ba189
ms.lasthandoff: 02/22/2017

---
# <a name="exception-handling-visual-studio-sdk"></a>Exceção tratamento (SDK do Visual Studio)
O exemplo a seguir descreve o processo que ocorre quando as exceções são lançadas.  
  
## <a name="exception-handling-process"></a>Processo de manipulação de exceção  
  
1.  Quando uma exceção é lançada pela primeira vez, mas antes que ela é tratada pelo manipulador de exceção no programa que está sendo depurado, o mecanismo de depuração (DE) envia uma [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) para o Gerenciador de depuração de sessão (SDM) como um evento de parada. O `IDebugExceptionEvent2` é enviada se apenas as definições de exceção (especificada na caixa de diálogo exceções no pacote de depuração) especificam que o usuário deseja parar em notificações de exceção de primeira chance.  
  
2.  As chamadas SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obter a propriedade de exceção.  
  
3.  As chamadas de pacote de depuração [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar as opções para apresentar ao usuário.  
  
4.  O pacote de depuração pede ao usuário como tratar a exceção abrindo uma caixa de diálogo de exceção de primeira chance.  
  
5.  Se o usuário optar por continuar, o SDM chama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Se o método retorna S_OK, chama [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         -ou-  
  
         Se o método retorna S_FALSE, o programa que está sendo depurado recebe uma segunda chance para tratar a exceção.  
  
6.  Se o programa que está sendo depurado não tem nenhum manipulador para uma exceção de segunda chance, envia o DE um `IDebugExceptionEvent2` para o SDM como **EVENT_SYNC_STOP**.  
  
7.  O pacote de depuração pede ao usuário como tratar a exceção abrindo uma caixa de diálogo de exceção de primeira chance.  
  
8.  As chamadas de pacote de depuração [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar as opções para apresentar ao usuário.  
  
9. O pacote de depuração pede ao usuário como tratar a exceção abrindo uma caixa de diálogo de exceção de segunda chance.  
  
10. Se o método retorna S_OK, chama `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos do depurador de chamada](../../extensibility/debugger/calling-debugger-events.md)
