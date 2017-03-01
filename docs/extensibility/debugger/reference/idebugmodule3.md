---
title: IDebugModule3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
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
ms.openlocfilehash: 8295b491ce8ab6af35485686aee4715f0e57470f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmodule3"></a>IDebugModule3
Essa interface representa um módulo que oferece suporte a locais alternativos de símbolos e JustMyCode estados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para oferecer suporte a locais alternativos de símbolos e trabalhar com estados JustMyCode (consulte a [Glossário de depurador do Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) para obter uma definição de "JustMyCode").  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) retorna essa interface. Os envios do [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) da interface do Gerenciador de depuração de sessão (SDM) usando o [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método. Além disso, uma chamada para [QueryInterface](/visual-cpp/atl/queryinterface) em uma [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interface retorna essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Retorna uma lista de caminhos pesquisado símbolos e os resultados da pesquisa de cada caminho.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carrega e inicializa os símbolos do módulo atual.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Sinalizador que retorna Especifica se o módulo representa o código do usuário.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Especifica se o módulo deve ser considerado o código do usuário ou não.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio é o consumidor comum dessa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
