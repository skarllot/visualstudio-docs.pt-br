---
title: "Pontos de interrupção de associação | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
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
ms.openlocfilehash: 98c976560652dc58a7cac4ea6aa64f1f893eeb18
ms.lasthandoff: 02/22/2017

---
# <a name="binding-breakpoints"></a>Pontos de interrupção de ligação
Se o usuário define um ponto de interrupção, talvez, pressionando F9, o IDE Formula a solicitação e solicita que a sessão de depuração para criar o ponto de interrupção.  
  
## <a name="setting-a-breakpoint"></a>Definindo um ponto de interrupção  
 Definindo um ponto de interrupção é um processo de duas etapas, porque o código ou os dados afetados pela interrupção podem ainda não estejam disponíveis. Primeiro, o ponto de interrupção deve ser descrito e em seguida, como códigos ou dados se torna disponíveis, ele deve ser associado a esse código ou dados, da seguinte maneira:  
  
1.  O ponto de interrupção foi solicitado dos mecanismos de depuração relevantes (DEs) e, em seguida, o ponto de interrupção está vinculado no código ou dados assim que possível.  
  
2.  A solicitação de ponto de interrupção é enviada para a sessão de depuração, que envia a todos os DEs relevantes. Qualquer DE que escolhe para lidar com o ponto de interrupção cria um correspondente pendentes ponto de interrupção.  
  
3.  A sessão de depuração coleta os pontos de interrupção pendentes e as envia para o pacote de depuração (o componente de depuração do Visual Studio).  
  
4.  O pacote de depuração solicita que a sessão de depuração para associar o ponto de interrupção pendente no código ou dados. A sessão de depuração envia essa solicitação para todos os DEs relevantes.  
  
5.  Se o DE é capaz de associar o ponto de interrupção, ele enviará que um ponto de interrupção associado a eventos para a sessão de depuração. Caso contrário, ele envia um evento de erro do ponto de interrupção em vez disso.  
  
## <a name="pending-breakpoints"></a>Pontos de interrupção pendentes  
 Um ponto de interrupção pendente pode vincular a vários locais de código. Por exemplo, uma linha de código-fonte para um modelo de C++ pode vincular a cada sequência de código gerada a partir do modelo. A sessão de depuração pode usar um evento associado do ponto de interrupção para enumerar os contextos de código associados a um ponto de interrupção no momento em que o evento foi enviado. Mais contextos de código podem ser vinculados posteriormente, para o DE possam enviar que vários ponto de interrupção associada eventos para cada solicitação de associação. No entanto, a DE deve enviar somente um evento de erro de ponto de interrupção por solicitação de associação.  
  
## <a name="implementation"></a>Implementação  
 Programaticamente, o pacote de depuração chama a depuração de sessão Gerenciador (SDM) e concede a ele um [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interface que encapsula um [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) estrutura, que descreve o ponto de interrupção a ser definido. Embora os pontos de interrupção de muitas formas, eles resolvem, por fim, para um contexto de código ou dados.  
  
 O SDM passa essa chamada para cada relevantes DE chamando seu [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método. Se escolher o DE lidar com o ponto de interrupção, ele cria e retorna um [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface. O SDM coleta essas interfaces e passa de volta para o pacote de depuração como um único `IDebugPendingBreakpoint2` interface.  
  
 Até aqui, nenhum evento foi gerado.  
  
 O pacote de depuração tenta associar o ponto de interrupção pendente no código ou dados chamando [ligar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que é implementado por DE.  
  
 Se o ponto de interrupção está associado, o DE envia um [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interface de eventos para o pacote de depuração. O pacote de depuração usa essa interface para enumerar todos os contextos de código (ou o contexto de dados único) associado ao ponto de interrupção chamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que retorna um ou mais [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaces. O [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interface retorna um [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interface, e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) retorna um [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) união que contém o contexto de código ou dados.  
  
 Se o DE é incapaz de ligar o ponto de interrupção, ele envia um único [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interface de eventos para o pacote de depuração. O pacote de depuração recupera o tipo de erro (erro ou aviso) e uma mensagem informativa chamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido por [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Isso retorna um [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) estrutura que contém o tipo de erro e a mensagem.  
  
 Se um DE lida com um ponto de interrupção, mas não é possível vinculá-lo, ele retornará um erro de tipo `BPET_TYPE_ERROR`. O pacote de depuração responde exibindo uma caixa de diálogo de erro e o IDE coloca um glifo de exclamação dentro de glifo de ponto de interrupção à esquerda da linha do código-fonte.  
  
 Se um DE lida com um ponto de interrupção, não é possível vincular a ele, mas algum outro DE poderá associá-lo, ele retorna um aviso. O IDE responde colocando um glifo de ponto dentro de glifo de ponto de interrupção à esquerda da linha do código-fonte.  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
