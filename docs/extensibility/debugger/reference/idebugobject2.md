---
title: IDebugObject2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
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
ms.openlocfilehash: 439397e439842b6a6c0334846b88e781cc0f1b6e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface fornece informações adicionais sobre um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão implementa essa interface para oferecer suporte a aliases e acesso a informações sobre o objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pode obter essa interface usando [QueryInterface](/visual-cpp/atl/queryinterface). Além disso, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retorna essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface, o `IDebugObject2` interface implementa o seguinte:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtém o campo ou a variável (se houver) que pode ser fazendo a propriedade representada por esse objeto.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtém o objeto de código gerenciado que representa o valor desse objeto.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Cria uma ID exclusiva para esse objeto ou retorna um alias existente.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtém o alias associado ao objeto, se houver.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtém o tipo desse objeto.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se este objeto representa dados de usuário.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se o estado de editar e continuar não é válido.<br /><br /> O avaliador de expressão personalizada não implementar esse método (sempre deve retornar `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Comentários  
 Consulte [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para obter mais informações sobre aliases.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
