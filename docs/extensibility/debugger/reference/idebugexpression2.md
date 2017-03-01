---
title: IDebugExpression2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
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
ms.openlocfilehash: f630949bb8e0371cb5a268f8c0c4bac2664f2539
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpression2"></a>IDebugExpression2
Essa interface representa um pronto de expressão analisada por associação e avaliar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma expressão analisada pronta para ser avaliada.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retorna essa interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retorna o [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Essas interfaces são acessíveis somente quando o programa que está sendo depurado foi pausado e um quadro de pilha está disponível.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugExpression2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia essa expressão assíncrona.|  
|[Anular](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação da expressão assíncrona.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia essa expressão de forma síncrona.|  
  
## <a name="remarks"></a>Comentários  
 Quando um programa foi interrompido, o Gerenciador de sessão de depuração (SDM) obtém um quadro de pilha de com uma chamada para [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Em seguida, chama o SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter o [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Isso é seguido por uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para criar o `IDebugExpression2` interface, que representa a expressão analisada pronta para ser avaliada.  
  
 O SDM chama o [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , na verdade, a expressão é avaliada e produz um valor.  
  
 Em uma implementação do `IDebugExpressionContext2::ParseText`, o DE usa COM `CoCreateInstance` função instanciar um avaliador de expressão e obter um [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface (consulte o exemplo de `IDebugExpressionEvaluator` interface). Em seguida, chama o DE [analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obter um [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Essa interface é usada na implementação do `IDebugExpression2::EvaluateSync` e `IDebugExpression2::EvaluateAsync` para realizar a avaliação.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
