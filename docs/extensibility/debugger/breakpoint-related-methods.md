---
title: "Métodos de ponto de interrupção | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
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
ms.openlocfilehash: c44e26359bfd6cee4f78d7c9c892c5e4c4761d1b
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoint-related-methods"></a>Métodos de ponto de interrupção
Um mecanismo de depuração (DE) deve oferecer suporte a configuração de pontos de interrupção. Depuração do Visual Studio suporta os seguintes tipos de pontos de interrupção:  
  
-   Associado  
  
     Solicitado por meio da interface do usuário e associar com êxito para um local de código especificada  
  
-   Pendente  
  
     Solicitado pela interface do usuário, mas instruções não ainda ligadas a real  
  
## <a name="discussion"></a>Discussão  
 Por exemplo, um ponto de interrupção pendente ocorre quando as instruções ainda não foram carregadas. Quando o código é carregado, pendentes tente pontos de interrupção para associar ao código no local indicado, ou seja, para inserir instruções de interrupção no código. Eventos são enviados para o Gerenciador de sessão de depuração (SDM) para indicar a associação com êxito, ou para notificar que havia erros de ligação.  
  
 Um ponto de interrupção pendente também gerencia sua própria lista interna de pontos de interrupção vinculados correspondentes. Uma pendente ponto de interrupção pode causar a inserção de muitos pontos de interrupção no código. Depuração da interface do usuário do Visual Studio mostra uma exibição de árvore dos pontos de interrupção pendentes e suas respectivas associadas a pontos de interrupção.  
  
 Criação e uso de pontos de interrupção pendentes exigem a implementação do [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método, bem como os seguintes métodos de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaces.  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se um especificado pendentes ponto de interrupção pode vincular a um local de código.|  
|[Ligação](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa um especificado pendentes ponto de interrupção em um ou mais locais de código.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtém o estado de um ponto de interrupção pendente.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtém a solicitação de ponto de interrupção usada para criar um ponto de interrupção pendente.|  
|[Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna o estado habilitado do ponto de interrupção pendente.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos os pontos de interrupção associados de um ponto de interrupção pendente.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos os pontos de interrupção de erro que resultam de um ponto de interrupção pendente.|  
|[Excluir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Exclui todos os pontos de interrupção associados dele e um ponto de interrupção pendente.|  
  
 Para enumerar os pontos de interrupção associados e os pontos de interrupção de erro, você deve implementar todos os métodos de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Pontos de interrupção que se vincular a um código pendentes local exigir a implementação dos seguintes [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de interrupção pendente que contém um ponto de interrupção.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtém o estado de um ponto de interrupção associado.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de ponto de interrupção que descreve um ponto de interrupção.|  
|[Habilitar](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita ou desabilita um ponto de interrupção.|  
|[Excluir](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Exclui um ponto de interrupção associado.|  
  
 Resolução e solicitação de informações exigem a implementação dos seguintes [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtém o tipo do ponto de interrupção representado por uma resolução.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtém as informações de resolução de ponto de interrupção que descreve um ponto de interrupção.|  
  
 Resolução de erros que podem ocorrer durante a associação exige a implementação dos seguintes [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de interrupção pendente que contém um ponto de interrupção de erro.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de erro do ponto de interrupção que descreve um ponto de interrupção de erro.|  
  
 Resolução de erros que podem ocorrer durante a associação também requer os seguintes métodos de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtém o tipo de um ponto de interrupção.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtém as informações de resolução de um ponto de interrupção.|  
  
 Exibindo o código-fonte em um ponto de interrupção exige que você implementar os métodos de [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/ou os métodos de [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
