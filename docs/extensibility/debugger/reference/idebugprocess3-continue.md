---
title: IDebugProcess3::Continue | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
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
ms.openlocfilehash: 96fbdd970d37e42bbb81c95839d48b925afca848
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua a execução desse processo de um estado parado. Qualquer estado de execução anterior (como uma etapa) é preservado, e o processo começa a ser executada novamente.  
  
> [!NOTE]
>  Esse método deve ser usado em vez de [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread de continuação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado sobre esse processo, independentemente de quantos processos estão sendo depurado ou processo que gerou o evento de interrupção. A implementação deve manter o estado de execução anterior (como uma etapa) e continuar a execução como se ele nunca foi interrompido antes de concluir sua execução anterior. Ou seja, se um thread nesse processo estava fazendo uma operação de failover etapa e foi interrompido porque algum outro processo interrompido e, em seguida, `Continue` foi chamado, o thread deve concluir a operação de failover etapa original.  
  
 **Aviso** envia um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
