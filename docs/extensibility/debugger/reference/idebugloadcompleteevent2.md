---
title: IDebugLoadCompleteEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugLoadCompleteEvent2
helpviewer_keywords:
- IDebugLoadCompleteEvent2
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
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
ms.openlocfilehash: 8025fb9fd0df097744da9a7600633f7a720401d7
ms.lasthandoff: 02/22/2017

---
# <a name="idebugloadcompleteevent2"></a>IDebugLoadCompleteEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando um programa é carregado, mas antes que qualquer código é executado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugLoadCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para informar que o programa foi carregado com êxito. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. O SDM usa [QueryInterface](/visual-cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para relatar que o programa foi carregado com êxito. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando anexado a programa que está sendo depurado.  
  
## <a name="remarks"></a>Comentários  
 Esse evento é um evento de parada e deve ter o `EVENT_STOPPING` o sinalizador será definido nos atributos de evento.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
