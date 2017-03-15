---
title: IDebugCodeContext2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
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
ms.openlocfilehash: 76d9f2b8e39dee6ea8602b74ced88e86fd0d7226
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Essa interface representa a posição inicial de uma instrução de código. A maioria das arquiteturas de tempo de execução de hoje, um contexto de código pode ser pensado como um endereço no fluxo de execução do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração implementa essa interface para relacionar a posição de uma instrução de código para uma posição de documento.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Métodos em interfaces muitos retornam essa interface, geralmente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Ele também é usado extensivamente com a [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interface, bem como informações de resolução de ponto de interrupção.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtém o contexto de documento que corresponde ao contexto do código ativo.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtém as informações de idioma para este contexto de código.|  
  
## <a name="remarks"></a>Comentários  
 A principal diferença entre um `IDebugCodeContext2` interface e uma [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface é que um `IDebugCodeContext2` sempre está alinhado à instrução. Isso significa que uma `IDebugCodeContext2` sempre aponta para o início de uma instrução, enquanto um `IDebugMemoryContext2` podem apontar para qualquer bytes de memória da arquitetura de tempo de execução. `IDebugCodeContext2`é incrementado por instruções em vez do tamanho de armazenamento básico (normalmente bytes).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
