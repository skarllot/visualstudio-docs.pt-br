---
title: IEnumDebugPortSuppliers2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
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
ms.openlocfilehash: a0b945bc0499c4a220f793c38ef42ef7065562b4
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Essa interface enumera os fornecedores de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O Visual Studio implementa essa interface para representar uma lista de fornecedores de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) para obter uma lista de fornecedores de porta.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugPortSuppliers2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Recupera um número especificado de fornecedores de porta em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignora um número especificado de fornecedores de porta em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Obtém o número de fornecedores de porta em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de depuração normalmente não precisa obter essa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
