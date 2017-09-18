---
title: IDebugProgram2::Step | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
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
ms.openlocfilehash: 69e3c379fbe1e8252d820308f64aa1a310932666
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Executa uma etapa.  
  
> [!NOTE]
>  Este método foi preterido. Use o [etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está sendo passado.  
  
 `sk`  
 [in] Um valor a partir de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumeração que especifica o tipo de etapa.  
  
 `step`  
 [in] Um valor a partir de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumeração que especifica a unidade da etapa (por exemplo, pela instrução ou instrução).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Caso haja qualquer sincronização de thread ou a comunicação entre threads, outros threads no programa devem ser executado quando um determinado thread está nivelado.  
  
> [!WARNING]
>  Não enviar um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
