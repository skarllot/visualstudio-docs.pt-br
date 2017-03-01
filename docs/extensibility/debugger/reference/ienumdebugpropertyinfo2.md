---
title: IEnumDebugPropertyInfo2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
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
ms.openlocfilehash: fc1d8df92d93ae1f34920e7416b2db14eedb4547
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Essa interface enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar as informações para uma determinada propriedade.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obter essa interface que representa os filhos de uma propriedade específica. Chamar [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para obter essa interface que representa as propriedades de um quadro de pilhas específico.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugPropertyInfo2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera um número especificado de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignora um número especificado de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtém o número de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, uma propriedade é uma hierarquia de informações que podem incluir um nome, valor, endereço e tipo, bem como quaisquer outras informações apropriadas para o quadro de pilha ou objeto de propriedade associada. Consulte [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para obter mais detalhes.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
