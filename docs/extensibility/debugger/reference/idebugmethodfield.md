---
title: IDebugMethodField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
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
ms.openlocfilehash: 0717cfca61ee6e03136283a4a5514e25b587de78
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmethodfield"></a>IDebugMethodField
Essa interface descreve um método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface. Essa interface é uma especialização que apresenta um método.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/visual-cpp/atl/queryinterface) para obter essa interface da [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retorna `FIELD_TYPE_METHOD`. Além disso, os métodos [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), e [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), retorne todos os `IDebugMethodField` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Cria um enumerador para os parâmetros do método.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtém o ponteiro "this" do objeto que contém o método.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Cria um enumerador para todas as variáveis locais do método.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Cria um enumerador para variáveis locais selecionados do método.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Determina se um atributo personalizado específico foi definido.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Cria um enumerador para variáveis locais estáticas do método.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Obtém o contêiner global do método.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Cria um enumerador para o tipo de cada argumento necessário para chamar o método.|  
  
## <a name="remarks"></a>Comentários  
 Um método pode conter parâmetros como variáveis locais.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
