---
title: IEnumDebugReferenceInfo2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
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
ms.openlocfilehash: dbe06b9bb2daae2d2847b1f140fcf48741ed4cbb
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Essa interface enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estruturas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para referências a objetos na memória. Esta interface deve ser implementada somente se há suporte para referências.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas do Visual Studio [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugReferenceInfo2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera um número especificado de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estruturas em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignora um número especificado de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estruturas na sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtém o número de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estruturas em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Uma referência é essencialmente um tipo e um endereço, enquanto que uma propriedade é um nome, o tipo e o endereço. Uma referência persiste enquanto o objeto referenciado existe na memória. Consulte [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obter mais detalhes.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
