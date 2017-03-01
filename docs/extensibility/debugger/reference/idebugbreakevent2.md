---
title: IDebugBreakEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
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
ms.openlocfilehash: 12b3654d70486319b145712ba6a0bcc6af0e67a2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Essa interface informa o Gerenciador de sessão de depuração (SDM) que a interrupção assíncrona foi concluída com êxito.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para oferecer suporte a quebras de usuário em um programa. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface (usa o SDM [QueryInterface](/visual-cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 As chamadas SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando o usuário solicitou o programa que está sendo depurado para ser pausado. Quando o programa foi interrompido com êxito, o DE envia o `IDebugBreakEvent2` evento. Esse evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada fornecida pelo SDM quando anexado a programa que está sendo depurado.  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, um usuário pode selecionar o **interromper tudo** comando o **depurar** menu para interromper um programa que está executando um loop infinito. O SDM diz ao programa para interromper chamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Os envios DE `IDebugBreakEvent2` quando o programa for interrompido por último.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
