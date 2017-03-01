---
title: IDebugPortEx2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
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
ms.openlocfilehash: f0fc8b48fecd72a5280ad83a33546949fcbba809
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportex2"></a>IDebugPortEx2
Essa interface permite que a sessão de depuração (SDM) do Gerenciador controle de programas e processos em execução em uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface no mesmo objeto que implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 As chamadas SDM [QueryInterface](/visual-cpp/atl/queryinterface) sobre o `IDebugPort2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPortEx2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Um arquivo executável é iniciado.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Retoma a execução de um processo.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se um processo pode ser encerrado.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Finaliza um processo.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtém a ID do processo da porta em si.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtém um programa associado a um nó de programa.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é normalmente privada entre o SDM e o fornecedor de porta personalizada.  
  
 Se desejar, um mecanismo de depuração (DE) pode procurar essa interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface passado para [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e usar [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) para iniciar o programa. No entanto, não é um requisito, e a DE pode fazer tudo o que ele precisa fazer para iniciar o programa de solicitação.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
