---
title: IDebugProgramEx2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
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
ms.openlocfilehash: d9464091f968753de999926fa0d01d5609a75840
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Essa interface permite que a sessão de depuração manager (SDM) anexar a um programa e obter o nó de programa associado a um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface no mesmo objeto, como o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface para permitir que o SDM anexar a um programa e, ao mesmo tempo permitindo que o fornecedor de porta controlar todas as sessões anexado ao programa. O fornecedor de porta personalizada pode implementar essa interface, se ele escolhe.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 As chamadas SDM [QueryInterface](/visual-cpp/atl/queryinterface) em um `IDebugProgram2` interface para obter essa interface para rastrear as sessões que anexadas a programas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugProgramEx2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Anexar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Anexa um programa para uma sessão.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtém o nó do programa associado a um programa.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é privada entre o SDM e o programa.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
