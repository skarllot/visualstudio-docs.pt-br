---
title: IDebugCanStopEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
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
ms.openlocfilehash: 584f8f4e6e721b57bf6879acf1c36540f2bf592c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Essa interface é usada para o Gerenciador de sessão de depuração (SDM) que perguntar se parar no local atual do código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para oferecer suporte a percorrer o código-fonte. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface (usa o SDM [QueryInterface](/visual-cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface).  
  
 A implementação dessa interface deve se comunicar a chamada do SDM de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) ao mecanismo de depuração. Por exemplo, isso pode ser feito com uma mensagem publicada em segmento de tratamento de mensagens de depuração do mecanismo ou o objeto que implementa essa interface pode manter uma referência ao mecanismo de depuração e retornar a chamada para o mecanismo de depuração com o sinalizador passado para `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE pode enviar esse método sempre que o DE é solicitado a continuar a execução e o DE é percorrendo o código. Esse evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada fornecida pelo SDM quando anexado a programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugCanStopEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtém o motivo para esse evento.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica se o programa que está sendo depurado deve parar no local do evento (e enviar um evento que descreve o motivo para interromper) ou simplesmente continuar a execução.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtém o contexto do documento que descreve o local desse evento.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtém o contexto de código que descreve o local desse evento.|  
  
## <a name="remarks"></a>Comentários  
 O DE envia essa interface se as etapas de usuário em uma função e DE não encontrar nenhuma informação de depuração ou informações de depuração existem mas a DE não sabe se o código-fonte pode ser exibido para esse local.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
