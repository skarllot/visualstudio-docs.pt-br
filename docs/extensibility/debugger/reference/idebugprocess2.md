---
title: IDebugProcess2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
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
ms.openlocfilehash: c6607eb78e73d3f542e35146f79d216ab99cde15
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocess2"></a>IDebugProcess2
Essa interface representa um processo em execução em uma porta. Se a porta é a porta local, em seguida, `IDebugProcess2` normalmente representa um processo físico na máquina local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por um fornecedor de porta personalizada para gerenciar programas como um grupo. Esta interface deve ser implementada pelo fornecedor de porta.  
  
 Um mecanismo de depuração também implementa essa interface se houver suporte para iniciar um programa por meio de [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada principalmente pelo Gerenciador de depuração de sessão (SDM) para interagir com um grupo de programas identificados neste processo.  
  
 Chamar [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obter essa interface. Essa interface também é retornada ao chamar `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugProcess2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtém uma descrição do processo.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera os programas que estão contidos nesse processo.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtém o título, o nome amigável ou o nome de arquivo do processo.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtém a instância de um computador servidor, que esse processo está em execução no.|  
|[Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Encerra o processo.|  
|[Anexar](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Anexa ao processo.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se o SDM poderá desanexar o processo.|  
|[Desanexar](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Desanexa o depurador do processo.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtém o identificador de processo do sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtém um identificador exclusivo para esse processo.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [SUBSTITUÍDO]|Obtém o nome da sessão que é o processo de depuração.<br /><br /> [SUBSTITUÍDO. DEVE SEMPRE RETORNAR `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera os threads em execução no processo.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicita que o próximo programa executando código em parar este processo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtém a porta que esse processo está em execução no.|  
  
## <a name="remarks"></a>Comentários  
 Um `IDebugProcess2` contém um ou mais [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaces.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
