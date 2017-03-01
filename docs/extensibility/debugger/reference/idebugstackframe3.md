---
title: IDebugStackFrame3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
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
ms.openlocfilehash: ddef1ae4e4535a0d883669855c5a8ba58d20c28f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Essa interface estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para manipular exceções interceptadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface no mesmo objeto que implementa o [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interface para oferecer suporte a exceções interceptadas.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em um `IDebugStackFrame2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Lida com uma exceção para o quadro de pilha atual antes de qualquer tratamento de exceção regular.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retorna um contexto de código se um desenrolamento de pilha ocorrer.|  
  
## <a name="remarks"></a>Comentários  
 Uma exceção interceptada significa que um depurador pode processar uma exceção antes de quaisquer rotinas de tratamento de exceção normais são chamadas pelo tempo de execução. Interceptar uma exceção essencialmente significa fazer com que o tempo de execução fingir que há presente mesmo quando não há um manipulador de exceção.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) é chamado durante todos os eventos de retorno de chamada de exceção normal (a única exceção a isso é se você estiver depurando código de modo misto (gerenciado e código não gerenciado), caso em que a exceção não pode ser interceptada durante o retorno de chamada de última chance). Se o DE implementar `IDebugStackFrame3`, ou o DE retorna um erro de IDebugStackFrame3::`InterceptCurrentException` (como `E_NOTIMPL`), em seguida, o depurador irá lidar com a exceção normalmente.  
  
 Ao interceptar uma exceção, o depurador pode permitir que o usuário fazer alterações no estado do programa que está sendo depurado e, em seguida, continuar a execução no ponto onde a exceção foi lançada.  
  
> [!NOTE]
>  Exceções interceptadas são permitidas apenas em código gerenciado, ou seja, em um programa que está sendo executado sob o tempo de execução do CLR (Common Language).  
  
 Um mecanismo de depuração indica que ele oferece suporte a exceções interceptando definindo "metricExceptions" com um valor de 1 em tempo de execução usando o `SetMetric` função. Para obter mais informações, consulte [SDK auxiliares para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
