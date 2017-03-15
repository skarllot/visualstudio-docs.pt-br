---
title: IEnumDebugPorts2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
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
ms.openlocfilehash: 2400b1b737f89e68ec5019eecb50d76d294912d2
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Essa interface enumera as portas de um fornecedor de porta ou da máquina.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para representar uma lista de portas criado pelo fornecedor. O Visual Studio implementa essa interface para oferecer suporte a seu próprio fornecedor de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) para obter essa interface que representa uma lista de portas criada pelo fornecedor de porta. Chamar [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) para obter essa interface que representa uma lista de portas que foram salvos em disco.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugPorts2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera um número especificado de portas em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignora um número especificado de portas em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtém o número de portas em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Visual Studio usa essa interface para ajudar a preencher uma lista de portas usadas para anexar a processos.  
  
 Um mecanismo de depuração normalmente não usa essa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
