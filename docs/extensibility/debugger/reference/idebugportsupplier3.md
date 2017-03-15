---
title: IDebugPortSupplier3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
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
ms.openlocfilehash: 40482875e97030a819a5ba1f042f82bb7f888ef4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Essa interface permite que um chamador determinar se um fornecedor de porta pode preservar portas (gravá-los em disco) entre invocações do depurador e, em seguida, obter uma lista dessas portas preservados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para oferecer suporte a persistência ou salvar informações de porta para o disco. Esta interface deve ser implementada no mesmo objeto, como o [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/visual-cpp/atl/queryinterface) sobre o `IDebugPortSupplier2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados do [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface, essa interface oferece suporte a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retorna se o fornecedor de porta pode persistir portas (gravando-los em disco) entre invocações do depurador.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retorna um objeto que pode ser usado para enumerar todas as portas que foram gravadas no disco pelo fornecedor porta.|  
  
## <a name="remarks"></a>Comentários  
 Se um fornecedor de porta pode persistir portas entre invocações, ele deve implementar essa interface. Portas devem ser carregadas quando o fornecedor de porta é instanciado e gravado em disco quando o fornecedor de porta é destruído.  
  
 Normalmente, um mecanismo de depuração não interage com um fornecedor de porta e não terá nenhum uso para essa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
