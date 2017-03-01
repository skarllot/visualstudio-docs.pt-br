---
title: IDebugDisassemblyStream2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
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
ms.openlocfilehash: 2026792aa24907b69670a30305faa3662d127805
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Essa interface representa um fluxo de instruções.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um mecanismo de depuração implementa essa interface para oferecer suporte a desmontagem do código do programa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para o [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método retorna essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugDisassemblyStream2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Leitura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lê a partir da posição atual no fluxo de desmontagem de instruções.|  
|[Busca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Move o ponteiro de leitura no fluxo de desmontagem um determinado número de instruções em relação a uma posição especificada.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Retorna um identificador de local do código de um contexto de código em particular.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Retorna um objeto de contexto de código correspondente a um identificador de local de código especificada.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Retorna um identificador de local do código que representa o local atual do código.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtém o documento de origem associado a este fluxo de desmontagem.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtém o escopo deste fluxo de desmontagem.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtém o tamanho deste fluxo de desmontagem.|  
  
## <a name="remarks"></a>Comentários  
 O fluxo de desmontagem pode ser criado para representar o espaço de endereço inteiro ou apenas uma função ou módulo dentro do espaço. Cada instrução é representada por um [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura retornada por uma chamada para o [leitura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
