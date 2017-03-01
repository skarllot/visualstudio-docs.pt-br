---
title: IDebugDocument2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
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
ms.openlocfilehash: 45825eb784f23f8f4b352330a652c17e995f9587
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocument2"></a>IDebugDocument2
Essa interface representa um documento de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]geralmente implementa essa interface. Um mecanismo de depuração (DE) também pode implementar esta interface quando ele precisa fornecer o código-fonte e a origem não existir no disco.  Nesses casos, também implementaria o DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) e [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfaces, bem como alguns métodos adicionais sobre o [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfaces.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Métodos de `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, e `IDebugActivateDocumentEvent2` interfaces retornam essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugDocument2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtém o nome do documento em uma das várias formas.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtém o identificador de classe do documento.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é implementada apenas quando o DE fornece o código-fonte. Por exemplo, quando você está depurando o script em uma página HTML, o DE fontes de código-fonte porque a fonte seja baixada ou gerada dinamicamente e não existe como um arquivo de disco. Durante a depuração de linguagens tradicionais, como C++, essa interface não precisa ser implementado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
