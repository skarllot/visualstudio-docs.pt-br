---
title: IDebugStackFrame2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
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
ms.openlocfilehash: d980d5febf0099c5bb5e2a6692113a1f2d80d70a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Essa interface representa um quadro de pilha única em uma pilha de chamada em um thread específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar um quadro de pilha.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para recuperar um [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface. Chamar [próximo](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) para recuperar um [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura que contém o `IDebugStackFrame2` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugStackFrame2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtém o contexto de código para este quadro de pilhas.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtém o contexto de documento para este quadro de pilhas.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtém o nome da estrutura de pilhas.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtém uma descrição da estrutura de pilhas.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtém uma representação depende do computador do intervalo de endereços físicos associados a um quadro de pilha.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtém um contexto de avaliação para fazer a avaliação da expressão dentro do contexto atual de um quadro de pilha e thread.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtém o idioma associado a um quadro de pilha.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtém uma descrição das propriedades associadas a um quadro de pilha.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Cria um enumerador para a pilha de propriedades do quadro.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtém o thread associado a um quadro de pilha.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é obtida somente quando o programa que está sendo depurado foi interrompido no ponto de interrupção (seja causada por um ponto de interrupção do conjunto de usuários ou uma exceção). A partir dessa interface, um contexto de expressão pode ser obtido para avaliar expressões, uma lista de registros pode ser retornada ou a pilha de chamadas pode ser obtida e examinada.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)
