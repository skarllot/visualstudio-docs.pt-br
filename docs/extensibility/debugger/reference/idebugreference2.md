---
title: IDebugReference2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
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
ms.openlocfilehash: 35e76f98c2ce72d24b1651eeade091059f40b679
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2"></a>IDebugReference2
Essa interface representa uma referência a uma propriedade de quadro de pilha ou outra propriedade.  
  
> [!NOTE]
>  `IDebugReference2`é reservado para uso futuro e todos os seus métodos devem retornar `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para representar uma referência a um determinado tipo de valor. Por exemplo, o valor pode ser um valor numérico como resultado de uma avaliação de expressão, um contexto de memória usado para exibir a memória ou uma lista de registros e seus valores.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) para obter essa interface. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) e [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) também retornar essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugReference2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtém o [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estrutura que descreve essa referência.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Define o valor dessa referência de uma cadeia de caracteres.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Define o valor dessa referência de outra referência.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera os filhos dessa referência.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtém o pai dessa referência.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtém a referência desta referência mais derivado.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtém os bytes de memória ao qual esta referência se refere.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtém um contexto de memória para essa referência.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtém o tamanho, em bytes, dessa referência.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Define este tipo de referência.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compara essa referência com outra.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse uso de "propriedade" não deve ser confundido com que uma variável de membro de uma classe, significando que embora um `IDebugReference2` pode representar essa entidade.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) representa uma propriedade, enquanto `IDebugReference2` representa uma referência a uma propriedade, normalmente uma referência a um objeto do programa que está sendo depurado.  
  
 A principal diferença entre uma propriedade e uma referência é que uma propriedade se refere a uma instância nomeada de um objeto, enquanto uma referência a uma instância sem nome. Por exemplo, uma propriedade pode fazer referência a um objeto no heap do programa por `"a.b"`. Outra propriedade pode fazer referência ao mesmo objeto como `"c.d"`. A maneira de se referir a essa propriedade requer que `"a.b"` ou `"c.d"` do escopo. Uma referência a esse mesmo objeto é sem nome; o objeto pode ser chamado enquanto a memória para esse objeto é válida.  
  
 Um `IDebugProperty2` interface pode ser pensada como um valor com um nome, um tipo e um endereço. Um `IDebugReference2`, por outro lado, pode ser pensada como um tipo e um endereço.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
