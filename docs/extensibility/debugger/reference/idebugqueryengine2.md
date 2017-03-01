---
title: IDebugQueryEngine2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
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
ms.openlocfilehash: c3ebaf258d63162f36a536b598b4f8bf5eac42eb
ms.lasthandoff: 02/22/2017

---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Essa interface permite que a sessão de depuração manager (SDM) recuperar uma interface que representa o mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface nos objetos que implementam as interfaces DE mais comuns (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), e [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) para permitir acesso ao [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface DE si mesmo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em uma interface DE típico para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugQueryEngine2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtém uma interface de mecanismo (DE) de depuração personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, essa interface é implementada no objeto que implementa o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) de interface para oferecer suporte a causalidade ordenada percorrendo funções; isto é, quando o depurador está saindo de uma função, a função seguinte para executar pode não ser uma função em outro thread, mas a função anterior na pilha completamente. Para obter uma definição de "causalidade", consulte o [Glossário de depurador do Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
