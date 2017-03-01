---
title: IDebugContainerField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
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
ms.openlocfilehash: 7cf087725f8cfcb8ba53da739706ededcddb61c4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Essa interface representa um símbolo ou um tipo que é um contêiner para outros símbolos ou tipos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Essa interface também é a classe base para todas as interfaces que representam contêineres.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Muitos métodos em interfaces muitos retornam essa interface. Como esta é uma classe base para todos os contêineres, interfaces mais especializadas pode ser obtido usando a partir dessa interface [QueryInterface](/visual-cpp/atl/queryinterface). Essas interfaces incluem [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Cria um enumerador para os campos do contêiner.|  
  
## <a name="remarks"></a>Comentários  
 Matrizes (contêineres para variáveis), classes (recipientes de métodos e variáveis) e métodos (contêineres para parâmetros e variáveis locais) são exemplos de contêineres.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
