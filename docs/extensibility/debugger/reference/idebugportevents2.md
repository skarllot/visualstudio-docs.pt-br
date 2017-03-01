---
title: IDebugPortEvents2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
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
ms.openlocfilehash: 424b8796d0990657a8be67acba7dd8e51902002c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Essa interface notifica um ouvinte (normalmente o depuração Gerenciador de sessão [SDM] ou um mecanismo de depuração) do programa e o processo de criação e destruição em uma porta específica. Essas informações podem ser usadas para apresentar uma exibição em tempo real dos processos e programas em execução na porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface para receber notificações sobre o programa de criação e destruição. Um mecanismo de depuração também pode implementar esta interface para monitorar esses eventos de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Todos os [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces podem ser consultadas por um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>interface.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> O <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>método `IDebugPortEvents2` é chamado no <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>interface para obter um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>interface.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> Finalmente, o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>método no <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>interface é chamada para enviar eventos por meio de [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) método.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra o método de `IDebugPortEvents2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envia os eventos que descrevem a criação e a destruição de processos e programas na porta.|  
  
## <a name="remarks"></a>Comentários  
 `IDebugPortEvents2`também é usado pelo SDM para depurar programas que são executados em um processo que já está sendo depurado.  
  
 Eventos de porta são passados para o SDM por esta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
