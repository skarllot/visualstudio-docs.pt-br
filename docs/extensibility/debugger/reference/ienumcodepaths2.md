---
title: IEnumCodePaths2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
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
ms.openlocfilehash: 1f75db6bde59632d7bcfd83233d474cb8f718ab8
ms.lasthandoff: 02/22/2017

---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Essa interface representa uma lista de caminhos de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de caminhos de código.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumCodePaths2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera um número especificado de caminhos de código em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignora um número especificado de caminhos de código em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtém o número de caminhos de código em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Um caminho de código representa uma chamada de função ou ponto de ramificação em um programa. Uma lista de caminhos de código representa o caminho por meio do qual a execução de código foi tomada.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)
