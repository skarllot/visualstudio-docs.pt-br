---
title: IDebugProgram2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
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
ms.openlocfilehash: 24e00197fad2cfedc713f6e0ed26358ad25de222
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2"></a>IDebugProgram2
Essa interface representa um programa que está sendo executado em um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) e um fornecedor de porta personalizada implementam essa interface para representar um programa em um processo. O Gerenciador de sessão de depuração (SDM) também implementa essa interface para fornecer informações para [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento retorna essa interface para um novo programa. Essa interface também é usada como um parâmetro para muitos métodos em várias interfaces.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugProgram2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera os threads em execução nesse programa.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Obtém o nome do programa.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtém o processo que o programa é executado no.|  
|[Encerrar](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Este programa é encerrado.|  
|[Anexar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Anexa a esse programa.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina se um mecanismo de depuração (DE) pode desanexar do programa.|  
|[Desanexar](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Desanexa o depurador desse programa.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Obtém um identificador exclusivo para este programa.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtém propriedades do programa.|  
|[Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua a execução deste programa de um estado parado. Qualquer estado de execução anterior está desmarcado.|  
|[Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua a execução deste programa de um estado parado. Qualquer estado de execução anterior é preservado.|  
|[Etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Executa uma etapa.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Este programa parar na próxima execução de solicitações de tempo um dos seu código de execução de threads.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtém o nome e o identificador do mecanismo de depuração (DE) executando esse programa.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera os contextos de código para uma posição especificada em um arquivo de origem.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Obtém os bytes de memória para este programa.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtém o fluxo de desmontagem para este programa ou parte do programa.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera os módulos que este programa foi carregado e está em execução.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtém a atualização de editar e continuar (ENC) para este programa.<br /><br /> Um mecanismo de depuração personalizado não implementar esse método (sempre deve retornar `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera os caminhos de código deste programa.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Grava um despejo de memória em um arquivo.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Comentários  
 Um programa é um contêiner de thread em execução em uma arquitetura de tempo de execução específica, enquanto um processo é composto de um ou mais programas.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
