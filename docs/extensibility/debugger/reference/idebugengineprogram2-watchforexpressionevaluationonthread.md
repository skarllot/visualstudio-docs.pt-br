---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
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
ms.openlocfilehash: bc90f3f42fc4cc4a3f0de62b0e1de0130748ad0a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Permite (ou não) a avaliação de expressão para ocorrer em determinado thread, mesmo se o programa foi interrompido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pOriginatingProgram`  
 [in] Um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa que está avaliando uma expressão.  
  
 `dwTid`  
 [in] Especifica o identificador do segmento.  
  
 `dwEvalFlags`  
 [in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que especificam como a avaliação deve ser executada.  
  
 `pExprCallback`  
 [in] Um [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto a ser usado para enviar eventos de depuração que ocorrem durante a avaliação da expressão.  
  
 `fWatch`  
 [in] Se diferente de zero (`TRUE`), permite a avaliação da expressão no thread identificado por `dwTid`; caso contrário, zero (`FALSE`) não permite a avaliação da expressão nesse segmento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quando o Gerenciador de sessão de depuração (SDM) solicita um programa, identificado pelo `pOriginatingProgram` parâmetro, para avaliar uma expressão, ele notifica todos os outros programas anexados ao chamar esse método.  
  
 Avaliação de expressão em um programa pode fazer com que o código seja executado em outro, devido a avaliação da função ou avaliação de qualquer `IDispatch` propriedades. Por isso, esse método permite a avaliação de expressão executar e concluir o mesmo que o thread pode ser interrompido neste programa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
