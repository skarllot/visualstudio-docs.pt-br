---
title: IDebugObject | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
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
ms.openlocfilehash: ef8ae792625ca2ba453045fd5a673a6084559791
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface representa um objeto que cria o fichário para encapsular os valores de expressões e símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um avaliador de expressão implementa essa interface para representar um objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é a classe base para todos os objetos que o avaliador de expressão usa expressões analisado. Ele é retornado por uma chamada para o [ligar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método. [QueryInterface](/visual-cpp/atl/queryinterface) obtém as interfaces mais especializadas a partir dessa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugObject`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtém o tamanho do objeto.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtém o valor do objeto consecutivos de bytes.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Define o valor do objeto do consecutivos de bytes.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Define o valor de referência deste objeto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtém o contexto de memória que representa o endereço do valor do objeto.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Cria uma cópia do objeto gerenciado no espaço de endereço do mecanismo de depuração.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testa se este objeto é uma referência nula.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compara um objeto a este.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se este objeto é somente leitura.|  
|[É proxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se o objeto for um proxy transparente.|  
  
## <a name="remarks"></a>Comentários  
 O avaliador de expressão usa essa interface como a classe base para representar objetos em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Ligação](../../../extensibility/debugger/reference/idebugbinder-bind.md)
