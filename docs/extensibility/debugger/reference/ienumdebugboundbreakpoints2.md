---
title: IEnumDebugBoundBreakpoints2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
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
ms.openlocfilehash: e8665bbf8bcfdab59ea74b898f70b23424c5d694
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Essa interface enumera os pontos de interrupção associados associados a um ponto de interrupção pendente ou ponto de interrupção associada eventos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para pontos de interrupção. Essa interface deve ser implementada, se houver suporte para pontos de interrupção.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O Visual Studio chama:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) obter essa interface que representa uma lista de todos os pontos de interrupção que foram acionadas.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) obter essa interface que representa uma lista de todos os pontos de interrupção que foram ligados.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) obter essa interface que representa uma lista de todos os pontos de interrupção associada a esse ponto de interrupção pendente.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugBoundBreakpoints2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera um número especificado de pontos de interrupção associados em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora um número especificado de pontos de interrupção associada em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtém o número de pontos de interrupção associada em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Visual Studio usa os pontos de interrupção associados representados por esta interface para atualizar a exibição de pontos de interrupção no IDE.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
