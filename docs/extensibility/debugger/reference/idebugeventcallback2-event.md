---
title: IDebugEventCallback2::Event | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
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
ms.openlocfilehash: 63d7840e3d0309a2f4267534536f220e46550300
ms.lasthandoff: 02/22/2017

---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envia notificação de eventos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pEngine`  
 [in] Um [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa o mecanismo de depuração (DE) que está enviando esse evento. É necessário um DE preencher esse parâmetro.  
  
 `pProcess`  
 [in] Um [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa o processo no qual o evento ocorre. Esse parâmetro é preenchido pelo Gerenciador de depuração de sessão (SDM). A DE sempre passa um valor nulo para esse parâmetro.  
  
 `pProgram`  
 [in] Um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa em que esse evento ocorre. Para a maioria dos eventos, esse parâmetro não é um valor nulo.  
  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread em que este evento ocorre. Para eventos de parada, esse parâmetro não pode ser um valor nulo como o quadro de pilha é obtido a esse parâmetro.  
  
 `pEvent`  
 [in] Um [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa o evento de depuração.  
  
 `riidEvent`  
 [in] GUID que identifica qual interface de eventos obtidas a `pEvent` parâmetro.  
  
 `dwAttrib`  
 [in] Uma combinação de sinalizadores do [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Ao chamar esse método, o `dwAttrib` parâmetro deve corresponder ao valor retornado do [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) método como é chamado no objeto de evento passado a `pEvent` parâmetro.  
  
 Todos os eventos de depuração são lançados de forma assíncrona, independentemente se um evento em si é assíncrono ou não. Quando a DE chama esse método, o valor de retorno não indica se o evento foi processado, apenas se o evento foi recebido. Na verdade, na maioria das circunstâncias, o evento não foi processado quando este método retorna.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
