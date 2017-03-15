---
title: IDebugModule2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
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
ms.openlocfilehash: 4f27b9417136c856862726978051de0ee766e99f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmodule2"></a>IDebugModule2
Essa interface representa um módulo — ou seja, uma unidade executável de um programa — como uma DLL.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar um módulo e fornecer acesso a informações sobre o módulo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retorna essa interface. Os envios do [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) da interface do Gerenciador de depuração de sessão (SDM) usando o [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.  
  
 Essa interface também pode ser retornada em uma [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura (que é retornado por uma chamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Próximo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) também retorna essa interface ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) retorna o [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugModule2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtém o [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que descreve esse módulo.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO. NÃO USE. Recarrega os símbolos do módulo.|  
  
## <a name="remarks"></a>Comentários  
 Informações de módulo podem ser exibidas no **módulos** janela do IDE.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
