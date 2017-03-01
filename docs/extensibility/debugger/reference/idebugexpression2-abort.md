---
title: IDebugExpression2::Abort | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
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
ms.openlocfilehash: e393ab9474c65d1065762c7a32ee3661bdef94de
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Esse método cancela a avaliação da expressão assíncrona como iniciado por uma chamada para o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```c#  
int Abort();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quando a avaliação da expressão assíncrona é cancelada, não enviado um [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) evento para o retorno de chamada do evento transmitido para o [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
