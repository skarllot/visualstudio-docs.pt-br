---
title: IDebugPortNotify2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
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
ms.openlocfilehash: a24d4ea93461f856f5d56e5020abd1857ebad45b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Essa interface registra ou cancela o registro de um programa que possa ser depurado com a porta está em execução no.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para oferecer suporte a adição e remoção de programas da porta. Ele geralmente é implementado no mesmo objeto que implementa o [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [QueryInterface](/visual-cpp/atl/queryinterface) sobre o `IDebugPort2` interface retorna essa interface. Além disso, uma chamada para [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) retorna essa interface. Um mecanismo de depuração pode ver essa interface como um parâmetro para [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPortNotify2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra um programa que possa ser depurado com a porta está em execução no.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Cancela o registro de um programa que possa ser depurado da porta está em execução no.|  
  
## <a name="remarks"></a>Comentários  
 A menos que uma porta de depuração tem uma maneira de saber quando os programas são carregados ou descarregados, um fornecedor de porta personalizada deve implementar essa interface. Todos os programas que estão carregados para depuração por meio de uma porta específica são acompanhados usando esta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
