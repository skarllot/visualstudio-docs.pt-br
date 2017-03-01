---
title: IEnumDebugAddresses | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
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
ms.openlocfilehash: 236b142c780b0245ce5c953eb448708cb4187e91
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Essa interface representa uma coleção de objetos que implementam o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelo provedor de símbolo para fornecer conjuntos de objetos que implementam o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Observe que isso não é uma enumeração COM padrão devido à presença do [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) método.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é retornada por [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface implementa os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera o próximo conjunto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objetos a partir da enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignora um número especificado de entradas.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Redefine a enumeração para a primeira entrada.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera uma cópia da enumeração atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera o número de entradas na enumeração.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é normalmente usada pelo mecanismo de depuração para ajudar a determinar o endereço apropriado para dar ao avaliador de expressão.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
