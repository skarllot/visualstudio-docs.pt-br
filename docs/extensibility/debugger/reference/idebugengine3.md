---
title: IDebugEngine3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
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
ms.openlocfilehash: 293517b87b57e905e5807fa9e3f07a47d4cead4c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3"></a>IDebugEngine3
Representa um mecanismo de depuração única (DE) que controla a depuração de um ou mais módulos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por um DE personalizado (se ele dá suporte a símbolos) para habilitar o estado de JustMyCode. Essa interface deve ser implementada por DE se ele dá suporte a símbolos e JustMyCode.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada, o Gerenciador de sessão de depuração (SDM) para passar opções de usuário para locais de onde carregar símbolos. Ele também é chamado para definir o GUID do mecanismo de quando ela é instanciada (esse GUID com base nas métricas de momento do mecanismo de registro). O SDM também chama essa interface para definir o estado de JustMyCode e definir todas as exceções conhecidas pelo depurador para um estado especificado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), o `IDebugEngine3` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Define o caminho ou caminhos que o DE será usado para procurar símbolos de depuração.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carrega os símbolos para todos os módulos que ainda não teve seus símbolos carregados.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informa o DE sobre as informações de JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Define o GUID DE métricas.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Defina todas as exceções pendente no momento para um estado especificado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
