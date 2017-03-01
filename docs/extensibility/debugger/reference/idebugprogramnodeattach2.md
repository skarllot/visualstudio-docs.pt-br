---
title: IDebugProgramNodeAttach2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
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
ms.openlocfilehash: 76953904c7ca5dc38f6a4fda5d3c45cfe43ded90
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que um nó de programa ser notificado de uma tentativa de anexar o programa associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada na mesma classe que implementa o [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface para receber uma notificação de uma operação de anexação e oferecem a oportunidade de cancelar a operação de anexação.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obter essa interface chamando o `QueryInterface` método em uma [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto. O [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método deve ser chamado antes de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método para dar ao nó de programa a oportunidade de interromper o processo de conexão.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Anexa o programa associado ou adia o processo de conexão para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é a alternativa preferida para preterido [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) método. Todos os mecanismos de depuração são sempre carregados com o `CoCreateInstance` function, ou seja, eles são instanciados fora do espaço de endereço do programa que está sendo depurado.  
  
 Se uma implementação anterior do `IDebugProgramNode2::Attach_V7` método foi simplesmente definindo a `GUID` do programa que está sendo depurado, em seguida, apenas o [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método precisa ser implementado.  
  
 Se uma implementação anterior do `IDebugProgramNode2::Attach_V7` método usado a interface de retorno de chamada que foi fornecida, em seguida, essa funcionalidade precisa ser movido para uma implementação do [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método e o `IDebugProgramNodeAttach2` interface não precisa ser implementado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
