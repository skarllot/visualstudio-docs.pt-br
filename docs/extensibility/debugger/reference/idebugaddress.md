---
title: IDebugAddress | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
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
ms.openlocfilehash: c3d96947ca29d8ef36bfdebb12fd0ba89ac3ea0a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugaddress"></a>IDebugAddress
Essa interface representa o endereço de um item. Ele é retornado pelo manipulador de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface para representar um endereço de um objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Muitos métodos em interfaces muitos retornam essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera um [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura que descreve um objeto e seu local.|  
  
## <a name="remarks"></a>Comentários  
 O provedor de símbolo retorna essa interface para representar um objeto e seu local em um escopo específico (por exemplo, função, método ou classe). Essa interface é retornada do e passada para diversos métodos do provedor de símbolo e expressão avaliador. Normalmente, o provedor de símbolo é a única entidade que precisa interpretar o conteúdo desta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
