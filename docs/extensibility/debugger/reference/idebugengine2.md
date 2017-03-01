---
title: IDebugEngine2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
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
ms.openlocfilehash: 881cb6e0c1aed32c8c60ef25404458aa5f150f71
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine2"></a>IDebugEngine2
Essa interface representa um mecanismo de depuração (DE). Ele é usado para gerenciar vários aspectos de uma sessão de depuração, desde a criação de pontos de interrupção para definir e apagar exceções.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por um DE personalizados para gerenciar a depuração de programas. Esta interface deve ser implementada por DE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada, o Gerenciador de sessão de depuração (SDM) para gerenciar a sessão de depuração, incluindo gerenciamento de exceções, criando pontos de interrupção e respondendo a eventos síncronos enviados pelo DE.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugEngine2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Cria um enumerador para todos os programas que estão sendo depurado por um DE.|  
|[Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Anexa um DE um programa.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Cria um ponto de interrupção pendente DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica como o DE deve tratar de uma determinada exceção.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Remove a exceção especificada para que ele não é tratado pelo mecanismo de depuração.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Remove a lista de exceções, que o IDE tiver definido para um idioma ou a arquitetura de tempo de execução específica.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtém o GUID DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a DE que o programa especificado foi encerrado atypically e que o DE deve limpar todas as referências para o programa e enviar um programa destruir o evento.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chamado pelo SDM para indicar que um evento de depuração síncrono, anteriormente enviado, DE para o SDM foi recebido e processado.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Define a localidade de.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Define a raiz do registro atualmente em uso por DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Define uma métrica.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicitações que todos os programas que estão sendo depurados por este DE parar a execução da próxima vez que um de seus threads tentará executar.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
